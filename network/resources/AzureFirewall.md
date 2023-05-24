Azure Firewall resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Azure Firewall
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var azureFirewall = new AzureNative.Network.AzureFirewall("azureFirewall", new()
    {
        ApplicationRuleCollections = new[]
        {
            new AzureNative.Network.Inputs.AzureFirewallApplicationRuleCollectionArgs
            {
                Action = new AzureNative.Network.Inputs.AzureFirewallRCActionArgs
                {
                    Type = "Deny",
                },
                Name = "apprulecoll",
                Priority = 110,
                Rules = new[]
                {
                    new AzureNative.Network.Inputs.AzureFirewallApplicationRuleArgs
                    {
                        Description = "Deny inbound rule",
                        Name = "rule1",
                        Protocols = new[]
                        {
                            new AzureNative.Network.Inputs.AzureFirewallApplicationRuleProtocolArgs
                            {
                                Port = 443,
                                ProtocolType = "Https",
                            },
                        },
                        SourceAddresses = new[]
                        {
                            "216.58.216.164",
                            "10.0.0.0/24",
                        },
                        TargetFqdns = new[]
                        {
                            "www.test.com",
                        },
                    },
                },
            },
        },
        AzureFirewallName = "azurefirewall",
        IpConfigurations = new[]
        {
            new AzureNative.Network.Inputs.AzureFirewallIPConfigurationArgs
            {
                Name = "azureFirewallIpConfiguration",
                PublicIPAddress = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName",
                },
                Subnet = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallSubnet",
                },
            },
        },
        Location = "West US",
        NatRuleCollections = new[]
        {
            new AzureNative.Network.Inputs.AzureFirewallNatRuleCollectionArgs
            {
                Action = new AzureNative.Network.Inputs.AzureFirewallNatRCActionArgs
                {
                    Type = "Dnat",
                },
                Name = "natrulecoll",
                Priority = 112,
                Rules = new[]
                {
                    new AzureNative.Network.Inputs.AzureFirewallNatRuleArgs
                    {
                        Description = "D-NAT all outbound web traffic for inspection",
                        DestinationAddresses = new[]
                        {
                            "1.2.3.4",
                        },
                        DestinationPorts = new[]
                        {
                            "443",
                        },
                        Name = "DNAT-HTTPS-traffic",
                        Protocols = new[]
                        {
                            "TCP",
                        },
                        SourceAddresses = new[]
                        {
                            "*",
                        },
                        TranslatedAddress = "1.2.3.5",
                        TranslatedPort = "8443",
                    },
                    new AzureNative.Network.Inputs.AzureFirewallNatRuleArgs
                    {
                        Description = "D-NAT all inbound web traffic for inspection",
                        DestinationAddresses = new[]
                        {
                            "1.2.3.4",
                        },
                        DestinationPorts = new[]
                        {
                            "80",
                        },
                        Name = "DNAT-HTTP-traffic-With-FQDN",
                        Protocols = new[]
                        {
                            "TCP",
                        },
                        SourceAddresses = new[]
                        {
                            "*",
                        },
                        TranslatedFqdn = "internalhttpserver",
                        TranslatedPort = "880",
                    },
                },
            },
        },
        NetworkRuleCollections = new[]
        {
            new AzureNative.Network.Inputs.AzureFirewallNetworkRuleCollectionArgs
            {
                Action = new AzureNative.Network.Inputs.AzureFirewallRCActionArgs
                {
                    Type = "Deny",
                },
                Name = "netrulecoll",
                Priority = 112,
                Rules = new[]
                {
                    new AzureNative.Network.Inputs.AzureFirewallNetworkRuleArgs
                    {
                        Description = "Block traffic based on source IPs and ports",
                        DestinationAddresses = new[]
                        {
                            "*",
                        },
                        DestinationPorts = new[]
                        {
                            "443-444",
                            "8443",
                        },
                        Name = "L4-traffic",
                        Protocols = new[]
                        {
                            "TCP",
                        },
                        SourceAddresses = new[]
                        {
                            "192.168.1.1-192.168.1.12",
                            "10.1.4.12-10.1.4.255",
                        },
                    },
                    new AzureNative.Network.Inputs.AzureFirewallNetworkRuleArgs
                    {
                        Description = "Block traffic based on source IPs and ports to amazon",
                        DestinationFqdns = new[]
                        {
                            "www.amazon.com",
                        },
                        DestinationPorts = new[]
                        {
                            "443-444",
                            "8443",
                        },
                        Name = "L4-traffic-with-FQDN",
                        Protocols = new[]
                        {
                            "TCP",
                        },
                        SourceAddresses = new[]
                        {
                            "10.2.4.12-10.2.4.255",
                        },
                    },
                },
            },
        },
        ResourceGroupName = "rg1",
        Sku = new AzureNative.Network.Inputs.AzureFirewallSkuArgs
        {
            Name = "AZFW_VNet",
            Tier = "Standard",
        },
        Tags = 
        {
            { "key1", "value1" },
        },
        ThreatIntelMode = "Alert",
        Zones = new[] {},
    });

});


```

```go
package main

import (
	network "github.com/pulumi/pulumi-azure-native-sdk/network"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := network.NewAzureFirewall(ctx, "azureFirewall", &network.AzureFirewallArgs{
			ApplicationRuleCollections: []network.AzureFirewallApplicationRuleCollectionArgs{
				{
					Action: {
						Type: pulumi.String("Deny"),
					},
					Name:     pulumi.String("apprulecoll"),
					Priority: pulumi.Int(110),
					Rules: network.AzureFirewallApplicationRuleArray{
						{
							Description: pulumi.String("Deny inbound rule"),
							Name:        pulumi.String("rule1"),
							Protocols: network.AzureFirewallApplicationRuleProtocolArray{
								{
									Port:         pulumi.Int(443),
									ProtocolType: pulumi.String("Https"),
								},
							},
							SourceAddresses: pulumi.StringArray{
								pulumi.String("216.58.216.164"),
								pulumi.String("10.0.0.0/24"),
							},
							TargetFqdns: pulumi.StringArray{
								pulumi.String("www.test.com"),
							},
						},
					},
				},
			},
			AzureFirewallName: pulumi.String("azurefirewall"),
			IpConfigurations: []network.AzureFirewallIPConfigurationArgs{
				{
					Name: pulumi.String("azureFirewallIpConfiguration"),
					PublicIPAddress: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName"),
					},
					Subnet: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallSubnet"),
					},
				},
			},
			Location: pulumi.String("West US"),
			NatRuleCollections: []network.AzureFirewallNatRuleCollectionArgs{
				{
					Action: {
						Type: pulumi.String("Dnat"),
					},
					Name:     pulumi.String("natrulecoll"),
					Priority: pulumi.Int(112),
					Rules: network.AzureFirewallNatRuleArray{
						{
							Description: pulumi.String("D-NAT all outbound web traffic for inspection"),
							DestinationAddresses: pulumi.StringArray{
								pulumi.String("1.2.3.4"),
							},
							DestinationPorts: pulumi.StringArray{
								pulumi.String("443"),
							},
							Name: pulumi.String("DNAT-HTTPS-traffic"),
							Protocols: pulumi.StringArray{
								pulumi.String("TCP"),
							},
							SourceAddresses: pulumi.StringArray{
								pulumi.String("*"),
							},
							TranslatedAddress: pulumi.String("1.2.3.5"),
							TranslatedPort:    pulumi.String("8443"),
						},
						{
							Description: pulumi.String("D-NAT all inbound web traffic for inspection"),
							DestinationAddresses: pulumi.StringArray{
								pulumi.String("1.2.3.4"),
							},
							DestinationPorts: pulumi.StringArray{
								pulumi.String("80"),
							},
							Name: pulumi.String("DNAT-HTTP-traffic-With-FQDN"),
							Protocols: pulumi.StringArray{
								pulumi.String("TCP"),
							},
							SourceAddresses: pulumi.StringArray{
								pulumi.String("*"),
							},
							TranslatedFqdn: pulumi.String("internalhttpserver"),
							TranslatedPort: pulumi.String("880"),
						},
					},
				},
			},
			NetworkRuleCollections: []network.AzureFirewallNetworkRuleCollectionArgs{
				{
					Action: {
						Type: pulumi.String("Deny"),
					},
					Name:     pulumi.String("netrulecoll"),
					Priority: pulumi.Int(112),
					Rules: network.AzureFirewallNetworkRuleArray{
						{
							Description: pulumi.String("Block traffic based on source IPs and ports"),
							DestinationAddresses: pulumi.StringArray{
								pulumi.String("*"),
							},
							DestinationPorts: pulumi.StringArray{
								pulumi.String("443-444"),
								pulumi.String("8443"),
							},
							Name: pulumi.String("L4-traffic"),
							Protocols: pulumi.StringArray{
								pulumi.String("TCP"),
							},
							SourceAddresses: pulumi.StringArray{
								pulumi.String("192.168.1.1-192.168.1.12"),
								pulumi.String("10.1.4.12-10.1.4.255"),
							},
						},
						{
							Description: pulumi.String("Block traffic based on source IPs and ports to amazon"),
							DestinationFqdns: pulumi.StringArray{
								pulumi.String("www.amazon.com"),
							},
							DestinationPorts: pulumi.StringArray{
								pulumi.String("443-444"),
								pulumi.String("8443"),
							},
							Name: pulumi.String("L4-traffic-with-FQDN"),
							Protocols: pulumi.StringArray{
								pulumi.String("TCP"),
							},
							SourceAddresses: pulumi.StringArray{
								pulumi.String("10.2.4.12-10.2.4.255"),
							},
						},
					},
				},
			},
			ResourceGroupName: pulumi.String("rg1"),
			Sku: &network.AzureFirewallSkuArgs{
				Name: pulumi.String("AZFW_VNet"),
				Tier: pulumi.String("Standard"),
			},
			Tags: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			ThreatIntelMode: pulumi.String("Alert"),
			Zones:           pulumi.StringArray{},
		})
		if err != nil {
			return err
		}
		return nil
	})
}

```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.network.AzureFirewall;
import com.pulumi.azurenative.network.AzureFirewallArgs;
import java.util.List;
import java.util.ArrayList;
import java.util.Map;
import java.io.File;
import java.nio.file.Files;
import java.nio.file.Paths;

public class App {
    public static void main(String[] args) {
        Pulumi.run(App::stack);
    }

    public static void stack(Context ctx) {
        var azureFirewall = new AzureFirewall("azureFirewall", AzureFirewallArgs.builder()        
            .applicationRuleCollections(Map.ofEntries(
                Map.entry("action", Map.of("type", "Deny")),
                Map.entry("name", "apprulecoll"),
                Map.entry("priority", 110),
                Map.entry("rules", Map.ofEntries(
                    Map.entry("description", "Deny inbound rule"),
                    Map.entry("name", "rule1"),
                    Map.entry("protocols", Map.ofEntries(
                        Map.entry("port", 443),
                        Map.entry("protocolType", "Https")
                    )),
                    Map.entry("sourceAddresses",                     
                        "216.58.216.164",
                        "10.0.0.0/24"),
                    Map.entry("targetFqdns", "www.test.com")
                ))
            ))
            .azureFirewallName("azurefirewall")
            .ipConfigurations(Map.ofEntries(
                Map.entry("name", "azureFirewallIpConfiguration"),
                Map.entry("publicIPAddress", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName")),
                Map.entry("subnet", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallSubnet"))
            ))
            .location("West US")
            .natRuleCollections(Map.ofEntries(
                Map.entry("action", Map.of("type", "Dnat")),
                Map.entry("name", "natrulecoll"),
                Map.entry("priority", 112),
                Map.entry("rules",                 
                    Map.ofEntries(
                        Map.entry("description", "D-NAT all outbound web traffic for inspection"),
                        Map.entry("destinationAddresses", "1.2.3.4"),
                        Map.entry("destinationPorts", "443"),
                        Map.entry("name", "DNAT-HTTPS-traffic"),
                        Map.entry("protocols", "TCP"),
                        Map.entry("sourceAddresses", "*"),
                        Map.entry("translatedAddress", "1.2.3.5"),
                        Map.entry("translatedPort", "8443")
                    ),
                    Map.ofEntries(
                        Map.entry("description", "D-NAT all inbound web traffic for inspection"),
                        Map.entry("destinationAddresses", "1.2.3.4"),
                        Map.entry("destinationPorts", "80"),
                        Map.entry("name", "DNAT-HTTP-traffic-With-FQDN"),
                        Map.entry("protocols", "TCP"),
                        Map.entry("sourceAddresses", "*"),
                        Map.entry("translatedFqdn", "internalhttpserver"),
                        Map.entry("translatedPort", "880")
                    ))
            ))
            .networkRuleCollections(Map.ofEntries(
                Map.entry("action", Map.of("type", "Deny")),
                Map.entry("name", "netrulecoll"),
                Map.entry("priority", 112),
                Map.entry("rules",                 
                    Map.ofEntries(
                        Map.entry("description", "Block traffic based on source IPs and ports"),
                        Map.entry("destinationAddresses", "*"),
                        Map.entry("destinationPorts",                         
                            "443-444",
                            "8443"),
                        Map.entry("name", "L4-traffic"),
                        Map.entry("protocols", "TCP"),
                        Map.entry("sourceAddresses",                         
                            "192.168.1.1-192.168.1.12",
                            "10.1.4.12-10.1.4.255")
                    ),
                    Map.ofEntries(
                        Map.entry("description", "Block traffic based on source IPs and ports to amazon"),
                        Map.entry("destinationFqdns", "www.amazon.com"),
                        Map.entry("destinationPorts",                         
                            "443-444",
                            "8443"),
                        Map.entry("name", "L4-traffic-with-FQDN"),
                        Map.entry("protocols", "TCP"),
                        Map.entry("sourceAddresses", "10.2.4.12-10.2.4.255")
                    ))
            ))
            .resourceGroupName("rg1")
            .sku(Map.ofEntries(
                Map.entry("name", "AZFW_VNet"),
                Map.entry("tier", "Standard")
            ))
            .tags(Map.of("key1", "value1"))
            .threatIntelMode("Alert")
            .zones()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const azureFirewall = new azure_native.network.AzureFirewall("azureFirewall", {
    applicationRuleCollections: [{
        action: {
            type: "Deny",
        },
        name: "apprulecoll",
        priority: 110,
        rules: [{
            description: "Deny inbound rule",
            name: "rule1",
            protocols: [{
                port: 443,
                protocolType: "Https",
            }],
            sourceAddresses: [
                "216.58.216.164",
                "10.0.0.0/24",
            ],
            targetFqdns: ["www.test.com"],
        }],
    }],
    azureFirewallName: "azurefirewall",
    ipConfigurations: [{
        name: "azureFirewallIpConfiguration",
        publicIPAddress: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName",
        },
        subnet: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallSubnet",
        },
    }],
    location: "West US",
    natRuleCollections: [{
        action: {
            type: "Dnat",
        },
        name: "natrulecoll",
        priority: 112,
        rules: [
            {
                description: "D-NAT all outbound web traffic for inspection",
                destinationAddresses: ["1.2.3.4"],
                destinationPorts: ["443"],
                name: "DNAT-HTTPS-traffic",
                protocols: ["TCP"],
                sourceAddresses: ["*"],
                translatedAddress: "1.2.3.5",
                translatedPort: "8443",
            },
            {
                description: "D-NAT all inbound web traffic for inspection",
                destinationAddresses: ["1.2.3.4"],
                destinationPorts: ["80"],
                name: "DNAT-HTTP-traffic-With-FQDN",
                protocols: ["TCP"],
                sourceAddresses: ["*"],
                translatedFqdn: "internalhttpserver",
                translatedPort: "880",
            },
        ],
    }],
    networkRuleCollections: [{
        action: {
            type: "Deny",
        },
        name: "netrulecoll",
        priority: 112,
        rules: [
            {
                description: "Block traffic based on source IPs and ports",
                destinationAddresses: ["*"],
                destinationPorts: [
                    "443-444",
                    "8443",
                ],
                name: "L4-traffic",
                protocols: ["TCP"],
                sourceAddresses: [
                    "192.168.1.1-192.168.1.12",
                    "10.1.4.12-10.1.4.255",
                ],
            },
            {
                description: "Block traffic based on source IPs and ports to amazon",
                destinationFqdns: ["www.amazon.com"],
                destinationPorts: [
                    "443-444",
                    "8443",
                ],
                name: "L4-traffic-with-FQDN",
                protocols: ["TCP"],
                sourceAddresses: ["10.2.4.12-10.2.4.255"],
            },
        ],
    }],
    resourceGroupName: "rg1",
    sku: {
        name: "AZFW_VNet",
        tier: "Standard",
    },
    tags: {
        key1: "value1",
    },
    threatIntelMode: "Alert",
    zones: [],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

azure_firewall = azure_native.network.AzureFirewall("azureFirewall",
    application_rule_collections=[{
        "action": azure_native.network.AzureFirewallRCActionArgs(
            type="Deny",
        ),
        "name": "apprulecoll",
        "priority": 110,
        "rules": [{
            "description": "Deny inbound rule",
            "name": "rule1",
            "protocols": [azure_native.network.AzureFirewallApplicationRuleProtocolArgs(
                port=443,
                protocol_type="Https",
            )],
            "sourceAddresses": [
                "216.58.216.164",
                "10.0.0.0/24",
            ],
            "targetFqdns": ["www.test.com"],
        }],
    }],
    azure_firewall_name="azurefirewall",
    ip_configurations=[{
        "name": "azureFirewallIpConfiguration",
        "publicIPAddress": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName",
        ),
        "subnet": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallSubnet",
        ),
    }],
    location="West US",
    nat_rule_collections=[{
        "action": azure_native.network.AzureFirewallNatRCActionArgs(
            type="Dnat",
        ),
        "name": "natrulecoll",
        "priority": 112,
        "rules": [
            azure_native.network.AzureFirewallNatRuleArgs(
                description="D-NAT all outbound web traffic for inspection",
                destination_addresses=["1.2.3.4"],
                destination_ports=["443"],
                name="DNAT-HTTPS-traffic",
                protocols=["TCP"],
                source_addresses=["*"],
                translated_address="1.2.3.5",
                translated_port="8443",
            ),
            azure_native.network.AzureFirewallNatRuleArgs(
                description="D-NAT all inbound web traffic for inspection",
                destination_addresses=["1.2.3.4"],
                destination_ports=["80"],
                name="DNAT-HTTP-traffic-With-FQDN",
                protocols=["TCP"],
                source_addresses=["*"],
                translated_fqdn="internalhttpserver",
                translated_port="880",
            ),
        ],
    }],
    network_rule_collections=[{
        "action": azure_native.network.AzureFirewallRCActionArgs(
            type="Deny",
        ),
        "name": "netrulecoll",
        "priority": 112,
        "rules": [
            azure_native.network.AzureFirewallNetworkRuleArgs(
                description="Block traffic based on source IPs and ports",
                destination_addresses=["*"],
                destination_ports=[
                    "443-444",
                    "8443",
                ],
                name="L4-traffic",
                protocols=["TCP"],
                source_addresses=[
                    "192.168.1.1-192.168.1.12",
                    "10.1.4.12-10.1.4.255",
                ],
            ),
            azure_native.network.AzureFirewallNetworkRuleArgs(
                description="Block traffic based on source IPs and ports to amazon",
                destination_fqdns=["www.amazon.com"],
                destination_ports=[
                    "443-444",
                    "8443",
                ],
                name="L4-traffic-with-FQDN",
                protocols=["TCP"],
                source_addresses=["10.2.4.12-10.2.4.255"],
            ),
        ],
    }],
    resource_group_name="rg1",
    sku=azure_native.network.AzureFirewallSkuArgs(
        name="AZFW_VNet",
        tier="Standard",
    ),
    tags={
        "key1": "value1",
    },
    threat_intel_mode="Alert",
    zones=[])

```

```yaml
resources:
  azureFirewall:
    type: azure-native:network:AzureFirewall
    properties:
      applicationRuleCollections:
        - action:
            type: Deny
          name: apprulecoll
          priority: 110
          rules:
            - description: Deny inbound rule
              name: rule1
              protocols:
                - port: 443
                  protocolType: Https
              sourceAddresses:
                - 216.58.216.164
                - 10.0.0.0/24
              targetFqdns:
                - www.test.com
      azureFirewallName: azurefirewall
      ipConfigurations:
        - name: azureFirewallIpConfiguration
          publicIPAddress:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName
          subnet:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallSubnet
      location: West US
      natRuleCollections:
        - action:
            type: Dnat
          name: natrulecoll
          priority: 112
          rules:
            - description: D-NAT all outbound web traffic for inspection
              destinationAddresses:
                - 1.2.3.4
              destinationPorts:
                - '443'
              name: DNAT-HTTPS-traffic
              protocols:
                - TCP
              sourceAddresses:
                - '*'
              translatedAddress: 1.2.3.5
              translatedPort: '8443'
            - description: D-NAT all inbound web traffic for inspection
              destinationAddresses:
                - 1.2.3.4
              destinationPorts:
                - '80'
              name: DNAT-HTTP-traffic-With-FQDN
              protocols:
                - TCP
              sourceAddresses:
                - '*'
              translatedFqdn: internalhttpserver
              translatedPort: '880'
      networkRuleCollections:
        - action:
            type: Deny
          name: netrulecoll
          priority: 112
          rules:
            - description: Block traffic based on source IPs and ports
              destinationAddresses:
                - '*'
              destinationPorts:
                - 443-444
                - '8443'
              name: L4-traffic
              protocols:
                - TCP
              sourceAddresses:
                - 192.168.1.1-192.168.1.12
                - 10.1.4.12-10.1.4.255
            - description: Block traffic based on source IPs and ports to amazon
              destinationFqdns:
                - www.amazon.com
              destinationPorts:
                - 443-444
                - '8443'
              name: L4-traffic-with-FQDN
              protocols:
                - TCP
              sourceAddresses:
                - 10.2.4.12-10.2.4.255
      resourceGroupName: rg1
      sku:
        name: AZFW_VNet
        tier: Standard
      tags:
        key1: value1
      threatIntelMode: Alert
      zones: []

```

{{% /example %}}
{{% example %}}
### Create Azure Firewall With Additional Properties
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var azureFirewall = new AzureNative.Network.AzureFirewall("azureFirewall", new()
    {
        AdditionalProperties = 
        {
            { "key1", "value1" },
            { "key2", "value2" },
        },
        ApplicationRuleCollections = new[]
        {
            new AzureNative.Network.Inputs.AzureFirewallApplicationRuleCollectionArgs
            {
                Action = new AzureNative.Network.Inputs.AzureFirewallRCActionArgs
                {
                    Type = "Deny",
                },
                Name = "apprulecoll",
                Priority = 110,
                Rules = new[]
                {
                    new AzureNative.Network.Inputs.AzureFirewallApplicationRuleArgs
                    {
                        Description = "Deny inbound rule",
                        Name = "rule1",
                        Protocols = new[]
                        {
                            new AzureNative.Network.Inputs.AzureFirewallApplicationRuleProtocolArgs
                            {
                                Port = 443,
                                ProtocolType = "Https",
                            },
                        },
                        SourceAddresses = new[]
                        {
                            "216.58.216.164",
                            "10.0.0.0/24",
                        },
                        TargetFqdns = new[]
                        {
                            "www.test.com",
                        },
                    },
                },
            },
        },
        AzureFirewallName = "azurefirewall",
        IpConfigurations = new[]
        {
            new AzureNative.Network.Inputs.AzureFirewallIPConfigurationArgs
            {
                Name = "azureFirewallIpConfiguration",
                PublicIPAddress = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName",
                },
                Subnet = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallSubnet",
                },
            },
        },
        Location = "West US",
        NatRuleCollections = new[]
        {
            new AzureNative.Network.Inputs.AzureFirewallNatRuleCollectionArgs
            {
                Action = new AzureNative.Network.Inputs.AzureFirewallNatRCActionArgs
                {
                    Type = "Dnat",
                },
                Name = "natrulecoll",
                Priority = 112,
                Rules = new[]
                {
                    new AzureNative.Network.Inputs.AzureFirewallNatRuleArgs
                    {
                        Description = "D-NAT all outbound web traffic for inspection",
                        DestinationAddresses = new[]
                        {
                            "1.2.3.4",
                        },
                        DestinationPorts = new[]
                        {
                            "443",
                        },
                        Name = "DNAT-HTTPS-traffic",
                        Protocols = new[]
                        {
                            "TCP",
                        },
                        SourceAddresses = new[]
                        {
                            "*",
                        },
                        TranslatedAddress = "1.2.3.5",
                        TranslatedPort = "8443",
                    },
                    new AzureNative.Network.Inputs.AzureFirewallNatRuleArgs
                    {
                        Description = "D-NAT all inbound web traffic for inspection",
                        DestinationAddresses = new[]
                        {
                            "1.2.3.4",
                        },
                        DestinationPorts = new[]
                        {
                            "80",
                        },
                        Name = "DNAT-HTTP-traffic-With-FQDN",
                        Protocols = new[]
                        {
                            "TCP",
                        },
                        SourceAddresses = new[]
                        {
                            "*",
                        },
                        TranslatedFqdn = "internalhttpserver",
                        TranslatedPort = "880",
                    },
                },
            },
        },
        NetworkRuleCollections = new[]
        {
            new AzureNative.Network.Inputs.AzureFirewallNetworkRuleCollectionArgs
            {
                Action = new AzureNative.Network.Inputs.AzureFirewallRCActionArgs
                {
                    Type = "Deny",
                },
                Name = "netrulecoll",
                Priority = 112,
                Rules = new[]
                {
                    new AzureNative.Network.Inputs.AzureFirewallNetworkRuleArgs
                    {
                        Description = "Block traffic based on source IPs and ports",
                        DestinationAddresses = new[]
                        {
                            "*",
                        },
                        DestinationPorts = new[]
                        {
                            "443-444",
                            "8443",
                        },
                        Name = "L4-traffic",
                        Protocols = new[]
                        {
                            "TCP",
                        },
                        SourceAddresses = new[]
                        {
                            "192.168.1.1-192.168.1.12",
                            "10.1.4.12-10.1.4.255",
                        },
                    },
                    new AzureNative.Network.Inputs.AzureFirewallNetworkRuleArgs
                    {
                        Description = "Block traffic based on source IPs and ports to amazon",
                        DestinationFqdns = new[]
                        {
                            "www.amazon.com",
                        },
                        DestinationPorts = new[]
                        {
                            "443-444",
                            "8443",
                        },
                        Name = "L4-traffic-with-FQDN",
                        Protocols = new[]
                        {
                            "TCP",
                        },
                        SourceAddresses = new[]
                        {
                            "10.2.4.12-10.2.4.255",
                        },
                    },
                },
            },
        },
        ResourceGroupName = "rg1",
        Sku = new AzureNative.Network.Inputs.AzureFirewallSkuArgs
        {
            Name = "AZFW_VNet",
            Tier = "Standard",
        },
        Tags = 
        {
            { "key1", "value1" },
        },
        ThreatIntelMode = "Alert",
        Zones = new[] {},
    });

});


```

```go
package main

import (
	network "github.com/pulumi/pulumi-azure-native-sdk/network"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := network.NewAzureFirewall(ctx, "azureFirewall", &network.AzureFirewallArgs{
			AdditionalProperties: pulumi.StringMap{
				"key1": pulumi.String("value1"),
				"key2": pulumi.String("value2"),
			},
			ApplicationRuleCollections: []network.AzureFirewallApplicationRuleCollectionArgs{
				{
					Action: {
						Type: pulumi.String("Deny"),
					},
					Name:     pulumi.String("apprulecoll"),
					Priority: pulumi.Int(110),
					Rules: network.AzureFirewallApplicationRuleArray{
						{
							Description: pulumi.String("Deny inbound rule"),
							Name:        pulumi.String("rule1"),
							Protocols: network.AzureFirewallApplicationRuleProtocolArray{
								{
									Port:         pulumi.Int(443),
									ProtocolType: pulumi.String("Https"),
								},
							},
							SourceAddresses: pulumi.StringArray{
								pulumi.String("216.58.216.164"),
								pulumi.String("10.0.0.0/24"),
							},
							TargetFqdns: pulumi.StringArray{
								pulumi.String("www.test.com"),
							},
						},
					},
				},
			},
			AzureFirewallName: pulumi.String("azurefirewall"),
			IpConfigurations: []network.AzureFirewallIPConfigurationArgs{
				{
					Name: pulumi.String("azureFirewallIpConfiguration"),
					PublicIPAddress: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName"),
					},
					Subnet: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallSubnet"),
					},
				},
			},
			Location: pulumi.String("West US"),
			NatRuleCollections: []network.AzureFirewallNatRuleCollectionArgs{
				{
					Action: {
						Type: pulumi.String("Dnat"),
					},
					Name:     pulumi.String("natrulecoll"),
					Priority: pulumi.Int(112),
					Rules: network.AzureFirewallNatRuleArray{
						{
							Description: pulumi.String("D-NAT all outbound web traffic for inspection"),
							DestinationAddresses: pulumi.StringArray{
								pulumi.String("1.2.3.4"),
							},
							DestinationPorts: pulumi.StringArray{
								pulumi.String("443"),
							},
							Name: pulumi.String("DNAT-HTTPS-traffic"),
							Protocols: pulumi.StringArray{
								pulumi.String("TCP"),
							},
							SourceAddresses: pulumi.StringArray{
								pulumi.String("*"),
							},
							TranslatedAddress: pulumi.String("1.2.3.5"),
							TranslatedPort:    pulumi.String("8443"),
						},
						{
							Description: pulumi.String("D-NAT all inbound web traffic for inspection"),
							DestinationAddresses: pulumi.StringArray{
								pulumi.String("1.2.3.4"),
							},
							DestinationPorts: pulumi.StringArray{
								pulumi.String("80"),
							},
							Name: pulumi.String("DNAT-HTTP-traffic-With-FQDN"),
							Protocols: pulumi.StringArray{
								pulumi.String("TCP"),
							},
							SourceAddresses: pulumi.StringArray{
								pulumi.String("*"),
							},
							TranslatedFqdn: pulumi.String("internalhttpserver"),
							TranslatedPort: pulumi.String("880"),
						},
					},
				},
			},
			NetworkRuleCollections: []network.AzureFirewallNetworkRuleCollectionArgs{
				{
					Action: {
						Type: pulumi.String("Deny"),
					},
					Name:     pulumi.String("netrulecoll"),
					Priority: pulumi.Int(112),
					Rules: network.AzureFirewallNetworkRuleArray{
						{
							Description: pulumi.String("Block traffic based on source IPs and ports"),
							DestinationAddresses: pulumi.StringArray{
								pulumi.String("*"),
							},
							DestinationPorts: pulumi.StringArray{
								pulumi.String("443-444"),
								pulumi.String("8443"),
							},
							Name: pulumi.String("L4-traffic"),
							Protocols: pulumi.StringArray{
								pulumi.String("TCP"),
							},
							SourceAddresses: pulumi.StringArray{
								pulumi.String("192.168.1.1-192.168.1.12"),
								pulumi.String("10.1.4.12-10.1.4.255"),
							},
						},
						{
							Description: pulumi.String("Block traffic based on source IPs and ports to amazon"),
							DestinationFqdns: pulumi.StringArray{
								pulumi.String("www.amazon.com"),
							},
							DestinationPorts: pulumi.StringArray{
								pulumi.String("443-444"),
								pulumi.String("8443"),
							},
							Name: pulumi.String("L4-traffic-with-FQDN"),
							Protocols: pulumi.StringArray{
								pulumi.String("TCP"),
							},
							SourceAddresses: pulumi.StringArray{
								pulumi.String("10.2.4.12-10.2.4.255"),
							},
						},
					},
				},
			},
			ResourceGroupName: pulumi.String("rg1"),
			Sku: &network.AzureFirewallSkuArgs{
				Name: pulumi.String("AZFW_VNet"),
				Tier: pulumi.String("Standard"),
			},
			Tags: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			ThreatIntelMode: pulumi.String("Alert"),
			Zones:           pulumi.StringArray{},
		})
		if err != nil {
			return err
		}
		return nil
	})
}

```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.network.AzureFirewall;
import com.pulumi.azurenative.network.AzureFirewallArgs;
import java.util.List;
import java.util.ArrayList;
import java.util.Map;
import java.io.File;
import java.nio.file.Files;
import java.nio.file.Paths;

public class App {
    public static void main(String[] args) {
        Pulumi.run(App::stack);
    }

    public static void stack(Context ctx) {
        var azureFirewall = new AzureFirewall("azureFirewall", AzureFirewallArgs.builder()        
            .additionalProperties(Map.ofEntries(
                Map.entry("key1", "value1"),
                Map.entry("key2", "value2")
            ))
            .applicationRuleCollections(Map.ofEntries(
                Map.entry("action", Map.of("type", "Deny")),
                Map.entry("name", "apprulecoll"),
                Map.entry("priority", 110),
                Map.entry("rules", Map.ofEntries(
                    Map.entry("description", "Deny inbound rule"),
                    Map.entry("name", "rule1"),
                    Map.entry("protocols", Map.ofEntries(
                        Map.entry("port", 443),
                        Map.entry("protocolType", "Https")
                    )),
                    Map.entry("sourceAddresses",                     
                        "216.58.216.164",
                        "10.0.0.0/24"),
                    Map.entry("targetFqdns", "www.test.com")
                ))
            ))
            .azureFirewallName("azurefirewall")
            .ipConfigurations(Map.ofEntries(
                Map.entry("name", "azureFirewallIpConfiguration"),
                Map.entry("publicIPAddress", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName")),
                Map.entry("subnet", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallSubnet"))
            ))
            .location("West US")
            .natRuleCollections(Map.ofEntries(
                Map.entry("action", Map.of("type", "Dnat")),
                Map.entry("name", "natrulecoll"),
                Map.entry("priority", 112),
                Map.entry("rules",                 
                    Map.ofEntries(
                        Map.entry("description", "D-NAT all outbound web traffic for inspection"),
                        Map.entry("destinationAddresses", "1.2.3.4"),
                        Map.entry("destinationPorts", "443"),
                        Map.entry("name", "DNAT-HTTPS-traffic"),
                        Map.entry("protocols", "TCP"),
                        Map.entry("sourceAddresses", "*"),
                        Map.entry("translatedAddress", "1.2.3.5"),
                        Map.entry("translatedPort", "8443")
                    ),
                    Map.ofEntries(
                        Map.entry("description", "D-NAT all inbound web traffic for inspection"),
                        Map.entry("destinationAddresses", "1.2.3.4"),
                        Map.entry("destinationPorts", "80"),
                        Map.entry("name", "DNAT-HTTP-traffic-With-FQDN"),
                        Map.entry("protocols", "TCP"),
                        Map.entry("sourceAddresses", "*"),
                        Map.entry("translatedFqdn", "internalhttpserver"),
                        Map.entry("translatedPort", "880")
                    ))
            ))
            .networkRuleCollections(Map.ofEntries(
                Map.entry("action", Map.of("type", "Deny")),
                Map.entry("name", "netrulecoll"),
                Map.entry("priority", 112),
                Map.entry("rules",                 
                    Map.ofEntries(
                        Map.entry("description", "Block traffic based on source IPs and ports"),
                        Map.entry("destinationAddresses", "*"),
                        Map.entry("destinationPorts",                         
                            "443-444",
                            "8443"),
                        Map.entry("name", "L4-traffic"),
                        Map.entry("protocols", "TCP"),
                        Map.entry("sourceAddresses",                         
                            "192.168.1.1-192.168.1.12",
                            "10.1.4.12-10.1.4.255")
                    ),
                    Map.ofEntries(
                        Map.entry("description", "Block traffic based on source IPs and ports to amazon"),
                        Map.entry("destinationFqdns", "www.amazon.com"),
                        Map.entry("destinationPorts",                         
                            "443-444",
                            "8443"),
                        Map.entry("name", "L4-traffic-with-FQDN"),
                        Map.entry("protocols", "TCP"),
                        Map.entry("sourceAddresses", "10.2.4.12-10.2.4.255")
                    ))
            ))
            .resourceGroupName("rg1")
            .sku(Map.ofEntries(
                Map.entry("name", "AZFW_VNet"),
                Map.entry("tier", "Standard")
            ))
            .tags(Map.of("key1", "value1"))
            .threatIntelMode("Alert")
            .zones()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const azureFirewall = new azure_native.network.AzureFirewall("azureFirewall", {
    additionalProperties: {
        key1: "value1",
        key2: "value2",
    },
    applicationRuleCollections: [{
        action: {
            type: "Deny",
        },
        name: "apprulecoll",
        priority: 110,
        rules: [{
            description: "Deny inbound rule",
            name: "rule1",
            protocols: [{
                port: 443,
                protocolType: "Https",
            }],
            sourceAddresses: [
                "216.58.216.164",
                "10.0.0.0/24",
            ],
            targetFqdns: ["www.test.com"],
        }],
    }],
    azureFirewallName: "azurefirewall",
    ipConfigurations: [{
        name: "azureFirewallIpConfiguration",
        publicIPAddress: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName",
        },
        subnet: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallSubnet",
        },
    }],
    location: "West US",
    natRuleCollections: [{
        action: {
            type: "Dnat",
        },
        name: "natrulecoll",
        priority: 112,
        rules: [
            {
                description: "D-NAT all outbound web traffic for inspection",
                destinationAddresses: ["1.2.3.4"],
                destinationPorts: ["443"],
                name: "DNAT-HTTPS-traffic",
                protocols: ["TCP"],
                sourceAddresses: ["*"],
                translatedAddress: "1.2.3.5",
                translatedPort: "8443",
            },
            {
                description: "D-NAT all inbound web traffic for inspection",
                destinationAddresses: ["1.2.3.4"],
                destinationPorts: ["80"],
                name: "DNAT-HTTP-traffic-With-FQDN",
                protocols: ["TCP"],
                sourceAddresses: ["*"],
                translatedFqdn: "internalhttpserver",
                translatedPort: "880",
            },
        ],
    }],
    networkRuleCollections: [{
        action: {
            type: "Deny",
        },
        name: "netrulecoll",
        priority: 112,
        rules: [
            {
                description: "Block traffic based on source IPs and ports",
                destinationAddresses: ["*"],
                destinationPorts: [
                    "443-444",
                    "8443",
                ],
                name: "L4-traffic",
                protocols: ["TCP"],
                sourceAddresses: [
                    "192.168.1.1-192.168.1.12",
                    "10.1.4.12-10.1.4.255",
                ],
            },
            {
                description: "Block traffic based on source IPs and ports to amazon",
                destinationFqdns: ["www.amazon.com"],
                destinationPorts: [
                    "443-444",
                    "8443",
                ],
                name: "L4-traffic-with-FQDN",
                protocols: ["TCP"],
                sourceAddresses: ["10.2.4.12-10.2.4.255"],
            },
        ],
    }],
    resourceGroupName: "rg1",
    sku: {
        name: "AZFW_VNet",
        tier: "Standard",
    },
    tags: {
        key1: "value1",
    },
    threatIntelMode: "Alert",
    zones: [],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

azure_firewall = azure_native.network.AzureFirewall("azureFirewall",
    additional_properties={
        "key1": "value1",
        "key2": "value2",
    },
    application_rule_collections=[{
        "action": azure_native.network.AzureFirewallRCActionArgs(
            type="Deny",
        ),
        "name": "apprulecoll",
        "priority": 110,
        "rules": [{
            "description": "Deny inbound rule",
            "name": "rule1",
            "protocols": [azure_native.network.AzureFirewallApplicationRuleProtocolArgs(
                port=443,
                protocol_type="Https",
            )],
            "sourceAddresses": [
                "216.58.216.164",
                "10.0.0.0/24",
            ],
            "targetFqdns": ["www.test.com"],
        }],
    }],
    azure_firewall_name="azurefirewall",
    ip_configurations=[{
        "name": "azureFirewallIpConfiguration",
        "publicIPAddress": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName",
        ),
        "subnet": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallSubnet",
        ),
    }],
    location="West US",
    nat_rule_collections=[{
        "action": azure_native.network.AzureFirewallNatRCActionArgs(
            type="Dnat",
        ),
        "name": "natrulecoll",
        "priority": 112,
        "rules": [
            azure_native.network.AzureFirewallNatRuleArgs(
                description="D-NAT all outbound web traffic for inspection",
                destination_addresses=["1.2.3.4"],
                destination_ports=["443"],
                name="DNAT-HTTPS-traffic",
                protocols=["TCP"],
                source_addresses=["*"],
                translated_address="1.2.3.5",
                translated_port="8443",
            ),
            azure_native.network.AzureFirewallNatRuleArgs(
                description="D-NAT all inbound web traffic for inspection",
                destination_addresses=["1.2.3.4"],
                destination_ports=["80"],
                name="DNAT-HTTP-traffic-With-FQDN",
                protocols=["TCP"],
                source_addresses=["*"],
                translated_fqdn="internalhttpserver",
                translated_port="880",
            ),
        ],
    }],
    network_rule_collections=[{
        "action": azure_native.network.AzureFirewallRCActionArgs(
            type="Deny",
        ),
        "name": "netrulecoll",
        "priority": 112,
        "rules": [
            azure_native.network.AzureFirewallNetworkRuleArgs(
                description="Block traffic based on source IPs and ports",
                destination_addresses=["*"],
                destination_ports=[
                    "443-444",
                    "8443",
                ],
                name="L4-traffic",
                protocols=["TCP"],
                source_addresses=[
                    "192.168.1.1-192.168.1.12",
                    "10.1.4.12-10.1.4.255",
                ],
            ),
            azure_native.network.AzureFirewallNetworkRuleArgs(
                description="Block traffic based on source IPs and ports to amazon",
                destination_fqdns=["www.amazon.com"],
                destination_ports=[
                    "443-444",
                    "8443",
                ],
                name="L4-traffic-with-FQDN",
                protocols=["TCP"],
                source_addresses=["10.2.4.12-10.2.4.255"],
            ),
        ],
    }],
    resource_group_name="rg1",
    sku=azure_native.network.AzureFirewallSkuArgs(
        name="AZFW_VNet",
        tier="Standard",
    ),
    tags={
        "key1": "value1",
    },
    threat_intel_mode="Alert",
    zones=[])

```

```yaml
resources:
  azureFirewall:
    type: azure-native:network:AzureFirewall
    properties:
      additionalProperties:
        key1: value1
        key2: value2
      applicationRuleCollections:
        - action:
            type: Deny
          name: apprulecoll
          priority: 110
          rules:
            - description: Deny inbound rule
              name: rule1
              protocols:
                - port: 443
                  protocolType: Https
              sourceAddresses:
                - 216.58.216.164
                - 10.0.0.0/24
              targetFqdns:
                - www.test.com
      azureFirewallName: azurefirewall
      ipConfigurations:
        - name: azureFirewallIpConfiguration
          publicIPAddress:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName
          subnet:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallSubnet
      location: West US
      natRuleCollections:
        - action:
            type: Dnat
          name: natrulecoll
          priority: 112
          rules:
            - description: D-NAT all outbound web traffic for inspection
              destinationAddresses:
                - 1.2.3.4
              destinationPorts:
                - '443'
              name: DNAT-HTTPS-traffic
              protocols:
                - TCP
              sourceAddresses:
                - '*'
              translatedAddress: 1.2.3.5
              translatedPort: '8443'
            - description: D-NAT all inbound web traffic for inspection
              destinationAddresses:
                - 1.2.3.4
              destinationPorts:
                - '80'
              name: DNAT-HTTP-traffic-With-FQDN
              protocols:
                - TCP
              sourceAddresses:
                - '*'
              translatedFqdn: internalhttpserver
              translatedPort: '880'
      networkRuleCollections:
        - action:
            type: Deny
          name: netrulecoll
          priority: 112
          rules:
            - description: Block traffic based on source IPs and ports
              destinationAddresses:
                - '*'
              destinationPorts:
                - 443-444
                - '8443'
              name: L4-traffic
              protocols:
                - TCP
              sourceAddresses:
                - 192.168.1.1-192.168.1.12
                - 10.1.4.12-10.1.4.255
            - description: Block traffic based on source IPs and ports to amazon
              destinationFqdns:
                - www.amazon.com
              destinationPorts:
                - 443-444
                - '8443'
              name: L4-traffic-with-FQDN
              protocols:
                - TCP
              sourceAddresses:
                - 10.2.4.12-10.2.4.255
      resourceGroupName: rg1
      sku:
        name: AZFW_VNet
        tier: Standard
      tags:
        key1: value1
      threatIntelMode: Alert
      zones: []

```

{{% /example %}}
{{% example %}}
### Create Azure Firewall With IpGroups
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var azureFirewall = new AzureNative.Network.AzureFirewall("azureFirewall", new()
    {
        ApplicationRuleCollections = new[]
        {
            new AzureNative.Network.Inputs.AzureFirewallApplicationRuleCollectionArgs
            {
                Action = new AzureNative.Network.Inputs.AzureFirewallRCActionArgs
                {
                    Type = "Deny",
                },
                Name = "apprulecoll",
                Priority = 110,
                Rules = new[]
                {
                    new AzureNative.Network.Inputs.AzureFirewallApplicationRuleArgs
                    {
                        Description = "Deny inbound rule",
                        Name = "rule1",
                        Protocols = new[]
                        {
                            new AzureNative.Network.Inputs.AzureFirewallApplicationRuleProtocolArgs
                            {
                                Port = 443,
                                ProtocolType = "Https",
                            },
                        },
                        SourceAddresses = new[]
                        {
                            "216.58.216.164",
                            "10.0.0.0/24",
                        },
                        TargetFqdns = new[]
                        {
                            "www.test.com",
                        },
                    },
                },
            },
        },
        AzureFirewallName = "azurefirewall",
        IpConfigurations = new[]
        {
            new AzureNative.Network.Inputs.AzureFirewallIPConfigurationArgs
            {
                Name = "azureFirewallIpConfiguration",
                PublicIPAddress = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName",
                },
                Subnet = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallSubnet",
                },
            },
        },
        Location = "West US",
        NatRuleCollections = new[]
        {
            new AzureNative.Network.Inputs.AzureFirewallNatRuleCollectionArgs
            {
                Action = new AzureNative.Network.Inputs.AzureFirewallNatRCActionArgs
                {
                    Type = "Dnat",
                },
                Name = "natrulecoll",
                Priority = 112,
                Rules = new[]
                {
                    new AzureNative.Network.Inputs.AzureFirewallNatRuleArgs
                    {
                        Description = "D-NAT all outbound web traffic for inspection",
                        DestinationAddresses = new[]
                        {
                            "1.2.3.4",
                        },
                        DestinationPorts = new[]
                        {
                            "443",
                        },
                        Name = "DNAT-HTTPS-traffic",
                        Protocols = new[]
                        {
                            "TCP",
                        },
                        SourceAddresses = new[]
                        {
                            "*",
                        },
                        TranslatedAddress = "1.2.3.5",
                        TranslatedPort = "8443",
                    },
                    new AzureNative.Network.Inputs.AzureFirewallNatRuleArgs
                    {
                        Description = "D-NAT all inbound web traffic for inspection",
                        DestinationAddresses = new[]
                        {
                            "1.2.3.4",
                        },
                        DestinationPorts = new[]
                        {
                            "80",
                        },
                        Name = "DNAT-HTTP-traffic-With-FQDN",
                        Protocols = new[]
                        {
                            "TCP",
                        },
                        SourceAddresses = new[]
                        {
                            "*",
                        },
                        TranslatedFqdn = "internalhttpserver",
                        TranslatedPort = "880",
                    },
                },
            },
        },
        NetworkRuleCollections = new[]
        {
            new AzureNative.Network.Inputs.AzureFirewallNetworkRuleCollectionArgs
            {
                Action = new AzureNative.Network.Inputs.AzureFirewallRCActionArgs
                {
                    Type = "Deny",
                },
                Name = "netrulecoll",
                Priority = 112,
                Rules = new[]
                {
                    new AzureNative.Network.Inputs.AzureFirewallNetworkRuleArgs
                    {
                        Description = "Block traffic based on source IPs and ports",
                        DestinationAddresses = new[]
                        {
                            "*",
                        },
                        DestinationPorts = new[]
                        {
                            "443-444",
                            "8443",
                        },
                        Name = "L4-traffic",
                        Protocols = new[]
                        {
                            "TCP",
                        },
                        SourceAddresses = new[]
                        {
                            "192.168.1.1-192.168.1.12",
                            "10.1.4.12-10.1.4.255",
                        },
                    },
                    new AzureNative.Network.Inputs.AzureFirewallNetworkRuleArgs
                    {
                        Description = "Block traffic based on source IPs and ports to amazon",
                        DestinationFqdns = new[]
                        {
                            "www.amazon.com",
                        },
                        DestinationPorts = new[]
                        {
                            "443-444",
                            "8443",
                        },
                        Name = "L4-traffic-with-FQDN",
                        Protocols = new[]
                        {
                            "TCP",
                        },
                        SourceAddresses = new[]
                        {
                            "10.2.4.12-10.2.4.255",
                        },
                    },
                },
            },
        },
        ResourceGroupName = "rg1",
        Sku = new AzureNative.Network.Inputs.AzureFirewallSkuArgs
        {
            Name = "AZFW_VNet",
            Tier = "Standard",
        },
        Tags = 
        {
            { "key1", "value1" },
        },
        ThreatIntelMode = "Alert",
        Zones = new[] {},
    });

});


```

```go
package main

import (
	network "github.com/pulumi/pulumi-azure-native-sdk/network"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := network.NewAzureFirewall(ctx, "azureFirewall", &network.AzureFirewallArgs{
			ApplicationRuleCollections: []network.AzureFirewallApplicationRuleCollectionArgs{
				{
					Action: {
						Type: pulumi.String("Deny"),
					},
					Name:     pulumi.String("apprulecoll"),
					Priority: pulumi.Int(110),
					Rules: network.AzureFirewallApplicationRuleArray{
						{
							Description: pulumi.String("Deny inbound rule"),
							Name:        pulumi.String("rule1"),
							Protocols: network.AzureFirewallApplicationRuleProtocolArray{
								{
									Port:         pulumi.Int(443),
									ProtocolType: pulumi.String("Https"),
								},
							},
							SourceAddresses: pulumi.StringArray{
								pulumi.String("216.58.216.164"),
								pulumi.String("10.0.0.0/24"),
							},
							TargetFqdns: pulumi.StringArray{
								pulumi.String("www.test.com"),
							},
						},
					},
				},
			},
			AzureFirewallName: pulumi.String("azurefirewall"),
			IpConfigurations: []network.AzureFirewallIPConfigurationArgs{
				{
					Name: pulumi.String("azureFirewallIpConfiguration"),
					PublicIPAddress: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName"),
					},
					Subnet: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallSubnet"),
					},
				},
			},
			Location: pulumi.String("West US"),
			NatRuleCollections: []network.AzureFirewallNatRuleCollectionArgs{
				{
					Action: {
						Type: pulumi.String("Dnat"),
					},
					Name:     pulumi.String("natrulecoll"),
					Priority: pulumi.Int(112),
					Rules: network.AzureFirewallNatRuleArray{
						{
							Description: pulumi.String("D-NAT all outbound web traffic for inspection"),
							DestinationAddresses: pulumi.StringArray{
								pulumi.String("1.2.3.4"),
							},
							DestinationPorts: pulumi.StringArray{
								pulumi.String("443"),
							},
							Name: pulumi.String("DNAT-HTTPS-traffic"),
							Protocols: pulumi.StringArray{
								pulumi.String("TCP"),
							},
							SourceAddresses: pulumi.StringArray{
								pulumi.String("*"),
							},
							TranslatedAddress: pulumi.String("1.2.3.5"),
							TranslatedPort:    pulumi.String("8443"),
						},
						{
							Description: pulumi.String("D-NAT all inbound web traffic for inspection"),
							DestinationAddresses: pulumi.StringArray{
								pulumi.String("1.2.3.4"),
							},
							DestinationPorts: pulumi.StringArray{
								pulumi.String("80"),
							},
							Name: pulumi.String("DNAT-HTTP-traffic-With-FQDN"),
							Protocols: pulumi.StringArray{
								pulumi.String("TCP"),
							},
							SourceAddresses: pulumi.StringArray{
								pulumi.String("*"),
							},
							TranslatedFqdn: pulumi.String("internalhttpserver"),
							TranslatedPort: pulumi.String("880"),
						},
					},
				},
			},
			NetworkRuleCollections: []network.AzureFirewallNetworkRuleCollectionArgs{
				{
					Action: {
						Type: pulumi.String("Deny"),
					},
					Name:     pulumi.String("netrulecoll"),
					Priority: pulumi.Int(112),
					Rules: network.AzureFirewallNetworkRuleArray{
						{
							Description: pulumi.String("Block traffic based on source IPs and ports"),
							DestinationAddresses: pulumi.StringArray{
								pulumi.String("*"),
							},
							DestinationPorts: pulumi.StringArray{
								pulumi.String("443-444"),
								pulumi.String("8443"),
							},
							Name: pulumi.String("L4-traffic"),
							Protocols: pulumi.StringArray{
								pulumi.String("TCP"),
							},
							SourceAddresses: pulumi.StringArray{
								pulumi.String("192.168.1.1-192.168.1.12"),
								pulumi.String("10.1.4.12-10.1.4.255"),
							},
						},
						{
							Description: pulumi.String("Block traffic based on source IPs and ports to amazon"),
							DestinationFqdns: pulumi.StringArray{
								pulumi.String("www.amazon.com"),
							},
							DestinationPorts: pulumi.StringArray{
								pulumi.String("443-444"),
								pulumi.String("8443"),
							},
							Name: pulumi.String("L4-traffic-with-FQDN"),
							Protocols: pulumi.StringArray{
								pulumi.String("TCP"),
							},
							SourceAddresses: pulumi.StringArray{
								pulumi.String("10.2.4.12-10.2.4.255"),
							},
						},
					},
				},
			},
			ResourceGroupName: pulumi.String("rg1"),
			Sku: &network.AzureFirewallSkuArgs{
				Name: pulumi.String("AZFW_VNet"),
				Tier: pulumi.String("Standard"),
			},
			Tags: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			ThreatIntelMode: pulumi.String("Alert"),
			Zones:           pulumi.StringArray{},
		})
		if err != nil {
			return err
		}
		return nil
	})
}

```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.network.AzureFirewall;
import com.pulumi.azurenative.network.AzureFirewallArgs;
import java.util.List;
import java.util.ArrayList;
import java.util.Map;
import java.io.File;
import java.nio.file.Files;
import java.nio.file.Paths;

public class App {
    public static void main(String[] args) {
        Pulumi.run(App::stack);
    }

    public static void stack(Context ctx) {
        var azureFirewall = new AzureFirewall("azureFirewall", AzureFirewallArgs.builder()        
            .applicationRuleCollections(Map.ofEntries(
                Map.entry("action", Map.of("type", "Deny")),
                Map.entry("name", "apprulecoll"),
                Map.entry("priority", 110),
                Map.entry("rules", Map.ofEntries(
                    Map.entry("description", "Deny inbound rule"),
                    Map.entry("name", "rule1"),
                    Map.entry("protocols", Map.ofEntries(
                        Map.entry("port", 443),
                        Map.entry("protocolType", "Https")
                    )),
                    Map.entry("sourceAddresses",                     
                        "216.58.216.164",
                        "10.0.0.0/24"),
                    Map.entry("targetFqdns", "www.test.com")
                ))
            ))
            .azureFirewallName("azurefirewall")
            .ipConfigurations(Map.ofEntries(
                Map.entry("name", "azureFirewallIpConfiguration"),
                Map.entry("publicIPAddress", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName")),
                Map.entry("subnet", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallSubnet"))
            ))
            .location("West US")
            .natRuleCollections(Map.ofEntries(
                Map.entry("action", Map.of("type", "Dnat")),
                Map.entry("name", "natrulecoll"),
                Map.entry("priority", 112),
                Map.entry("rules",                 
                    Map.ofEntries(
                        Map.entry("description", "D-NAT all outbound web traffic for inspection"),
                        Map.entry("destinationAddresses", "1.2.3.4"),
                        Map.entry("destinationPorts", "443"),
                        Map.entry("name", "DNAT-HTTPS-traffic"),
                        Map.entry("protocols", "TCP"),
                        Map.entry("sourceAddresses", "*"),
                        Map.entry("translatedAddress", "1.2.3.5"),
                        Map.entry("translatedPort", "8443")
                    ),
                    Map.ofEntries(
                        Map.entry("description", "D-NAT all inbound web traffic for inspection"),
                        Map.entry("destinationAddresses", "1.2.3.4"),
                        Map.entry("destinationPorts", "80"),
                        Map.entry("name", "DNAT-HTTP-traffic-With-FQDN"),
                        Map.entry("protocols", "TCP"),
                        Map.entry("sourceAddresses", "*"),
                        Map.entry("translatedFqdn", "internalhttpserver"),
                        Map.entry("translatedPort", "880")
                    ))
            ))
            .networkRuleCollections(Map.ofEntries(
                Map.entry("action", Map.of("type", "Deny")),
                Map.entry("name", "netrulecoll"),
                Map.entry("priority", 112),
                Map.entry("rules",                 
                    Map.ofEntries(
                        Map.entry("description", "Block traffic based on source IPs and ports"),
                        Map.entry("destinationAddresses", "*"),
                        Map.entry("destinationPorts",                         
                            "443-444",
                            "8443"),
                        Map.entry("name", "L4-traffic"),
                        Map.entry("protocols", "TCP"),
                        Map.entry("sourceAddresses",                         
                            "192.168.1.1-192.168.1.12",
                            "10.1.4.12-10.1.4.255")
                    ),
                    Map.ofEntries(
                        Map.entry("description", "Block traffic based on source IPs and ports to amazon"),
                        Map.entry("destinationFqdns", "www.amazon.com"),
                        Map.entry("destinationPorts",                         
                            "443-444",
                            "8443"),
                        Map.entry("name", "L4-traffic-with-FQDN"),
                        Map.entry("protocols", "TCP"),
                        Map.entry("sourceAddresses", "10.2.4.12-10.2.4.255")
                    ))
            ))
            .resourceGroupName("rg1")
            .sku(Map.ofEntries(
                Map.entry("name", "AZFW_VNet"),
                Map.entry("tier", "Standard")
            ))
            .tags(Map.of("key1", "value1"))
            .threatIntelMode("Alert")
            .zones()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const azureFirewall = new azure_native.network.AzureFirewall("azureFirewall", {
    applicationRuleCollections: [{
        action: {
            type: "Deny",
        },
        name: "apprulecoll",
        priority: 110,
        rules: [{
            description: "Deny inbound rule",
            name: "rule1",
            protocols: [{
                port: 443,
                protocolType: "Https",
            }],
            sourceAddresses: [
                "216.58.216.164",
                "10.0.0.0/24",
            ],
            targetFqdns: ["www.test.com"],
        }],
    }],
    azureFirewallName: "azurefirewall",
    ipConfigurations: [{
        name: "azureFirewallIpConfiguration",
        publicIPAddress: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName",
        },
        subnet: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallSubnet",
        },
    }],
    location: "West US",
    natRuleCollections: [{
        action: {
            type: "Dnat",
        },
        name: "natrulecoll",
        priority: 112,
        rules: [
            {
                description: "D-NAT all outbound web traffic for inspection",
                destinationAddresses: ["1.2.3.4"],
                destinationPorts: ["443"],
                name: "DNAT-HTTPS-traffic",
                protocols: ["TCP"],
                sourceAddresses: ["*"],
                translatedAddress: "1.2.3.5",
                translatedPort: "8443",
            },
            {
                description: "D-NAT all inbound web traffic for inspection",
                destinationAddresses: ["1.2.3.4"],
                destinationPorts: ["80"],
                name: "DNAT-HTTP-traffic-With-FQDN",
                protocols: ["TCP"],
                sourceAddresses: ["*"],
                translatedFqdn: "internalhttpserver",
                translatedPort: "880",
            },
        ],
    }],
    networkRuleCollections: [{
        action: {
            type: "Deny",
        },
        name: "netrulecoll",
        priority: 112,
        rules: [
            {
                description: "Block traffic based on source IPs and ports",
                destinationAddresses: ["*"],
                destinationPorts: [
                    "443-444",
                    "8443",
                ],
                name: "L4-traffic",
                protocols: ["TCP"],
                sourceAddresses: [
                    "192.168.1.1-192.168.1.12",
                    "10.1.4.12-10.1.4.255",
                ],
            },
            {
                description: "Block traffic based on source IPs and ports to amazon",
                destinationFqdns: ["www.amazon.com"],
                destinationPorts: [
                    "443-444",
                    "8443",
                ],
                name: "L4-traffic-with-FQDN",
                protocols: ["TCP"],
                sourceAddresses: ["10.2.4.12-10.2.4.255"],
            },
        ],
    }],
    resourceGroupName: "rg1",
    sku: {
        name: "AZFW_VNet",
        tier: "Standard",
    },
    tags: {
        key1: "value1",
    },
    threatIntelMode: "Alert",
    zones: [],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

azure_firewall = azure_native.network.AzureFirewall("azureFirewall",
    application_rule_collections=[{
        "action": azure_native.network.AzureFirewallRCActionArgs(
            type="Deny",
        ),
        "name": "apprulecoll",
        "priority": 110,
        "rules": [{
            "description": "Deny inbound rule",
            "name": "rule1",
            "protocols": [azure_native.network.AzureFirewallApplicationRuleProtocolArgs(
                port=443,
                protocol_type="Https",
            )],
            "sourceAddresses": [
                "216.58.216.164",
                "10.0.0.0/24",
            ],
            "targetFqdns": ["www.test.com"],
        }],
    }],
    azure_firewall_name="azurefirewall",
    ip_configurations=[{
        "name": "azureFirewallIpConfiguration",
        "publicIPAddress": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName",
        ),
        "subnet": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallSubnet",
        ),
    }],
    location="West US",
    nat_rule_collections=[{
        "action": azure_native.network.AzureFirewallNatRCActionArgs(
            type="Dnat",
        ),
        "name": "natrulecoll",
        "priority": 112,
        "rules": [
            azure_native.network.AzureFirewallNatRuleArgs(
                description="D-NAT all outbound web traffic for inspection",
                destination_addresses=["1.2.3.4"],
                destination_ports=["443"],
                name="DNAT-HTTPS-traffic",
                protocols=["TCP"],
                source_addresses=["*"],
                translated_address="1.2.3.5",
                translated_port="8443",
            ),
            azure_native.network.AzureFirewallNatRuleArgs(
                description="D-NAT all inbound web traffic for inspection",
                destination_addresses=["1.2.3.4"],
                destination_ports=["80"],
                name="DNAT-HTTP-traffic-With-FQDN",
                protocols=["TCP"],
                source_addresses=["*"],
                translated_fqdn="internalhttpserver",
                translated_port="880",
            ),
        ],
    }],
    network_rule_collections=[{
        "action": azure_native.network.AzureFirewallRCActionArgs(
            type="Deny",
        ),
        "name": "netrulecoll",
        "priority": 112,
        "rules": [
            azure_native.network.AzureFirewallNetworkRuleArgs(
                description="Block traffic based on source IPs and ports",
                destination_addresses=["*"],
                destination_ports=[
                    "443-444",
                    "8443",
                ],
                name="L4-traffic",
                protocols=["TCP"],
                source_addresses=[
                    "192.168.1.1-192.168.1.12",
                    "10.1.4.12-10.1.4.255",
                ],
            ),
            azure_native.network.AzureFirewallNetworkRuleArgs(
                description="Block traffic based on source IPs and ports to amazon",
                destination_fqdns=["www.amazon.com"],
                destination_ports=[
                    "443-444",
                    "8443",
                ],
                name="L4-traffic-with-FQDN",
                protocols=["TCP"],
                source_addresses=["10.2.4.12-10.2.4.255"],
            ),
        ],
    }],
    resource_group_name="rg1",
    sku=azure_native.network.AzureFirewallSkuArgs(
        name="AZFW_VNet",
        tier="Standard",
    ),
    tags={
        "key1": "value1",
    },
    threat_intel_mode="Alert",
    zones=[])

```

```yaml
resources:
  azureFirewall:
    type: azure-native:network:AzureFirewall
    properties:
      applicationRuleCollections:
        - action:
            type: Deny
          name: apprulecoll
          priority: 110
          rules:
            - description: Deny inbound rule
              name: rule1
              protocols:
                - port: 443
                  protocolType: Https
              sourceAddresses:
                - 216.58.216.164
                - 10.0.0.0/24
              targetFqdns:
                - www.test.com
      azureFirewallName: azurefirewall
      ipConfigurations:
        - name: azureFirewallIpConfiguration
          publicIPAddress:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName
          subnet:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallSubnet
      location: West US
      natRuleCollections:
        - action:
            type: Dnat
          name: natrulecoll
          priority: 112
          rules:
            - description: D-NAT all outbound web traffic for inspection
              destinationAddresses:
                - 1.2.3.4
              destinationPorts:
                - '443'
              name: DNAT-HTTPS-traffic
              protocols:
                - TCP
              sourceAddresses:
                - '*'
              translatedAddress: 1.2.3.5
              translatedPort: '8443'
            - description: D-NAT all inbound web traffic for inspection
              destinationAddresses:
                - 1.2.3.4
              destinationPorts:
                - '80'
              name: DNAT-HTTP-traffic-With-FQDN
              protocols:
                - TCP
              sourceAddresses:
                - '*'
              translatedFqdn: internalhttpserver
              translatedPort: '880'
      networkRuleCollections:
        - action:
            type: Deny
          name: netrulecoll
          priority: 112
          rules:
            - description: Block traffic based on source IPs and ports
              destinationAddresses:
                - '*'
              destinationPorts:
                - 443-444
                - '8443'
              name: L4-traffic
              protocols:
                - TCP
              sourceAddresses:
                - 192.168.1.1-192.168.1.12
                - 10.1.4.12-10.1.4.255
            - description: Block traffic based on source IPs and ports to amazon
              destinationFqdns:
                - www.amazon.com
              destinationPorts:
                - 443-444
                - '8443'
              name: L4-traffic-with-FQDN
              protocols:
                - TCP
              sourceAddresses:
                - 10.2.4.12-10.2.4.255
      resourceGroupName: rg1
      sku:
        name: AZFW_VNet
        tier: Standard
      tags:
        key1: value1
      threatIntelMode: Alert
      zones: []

```

{{% /example %}}
{{% example %}}
### Create Azure Firewall With Zones
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var azureFirewall = new AzureNative.Network.AzureFirewall("azureFirewall", new()
    {
        ApplicationRuleCollections = new[]
        {
            new AzureNative.Network.Inputs.AzureFirewallApplicationRuleCollectionArgs
            {
                Action = new AzureNative.Network.Inputs.AzureFirewallRCActionArgs
                {
                    Type = "Deny",
                },
                Name = "apprulecoll",
                Priority = 110,
                Rules = new[]
                {
                    new AzureNative.Network.Inputs.AzureFirewallApplicationRuleArgs
                    {
                        Description = "Deny inbound rule",
                        Name = "rule1",
                        Protocols = new[]
                        {
                            new AzureNative.Network.Inputs.AzureFirewallApplicationRuleProtocolArgs
                            {
                                Port = 443,
                                ProtocolType = "Https",
                            },
                        },
                        SourceAddresses = new[]
                        {
                            "216.58.216.164",
                            "10.0.0.0/24",
                        },
                        TargetFqdns = new[]
                        {
                            "www.test.com",
                        },
                    },
                },
            },
        },
        AzureFirewallName = "azurefirewall",
        IpConfigurations = new[]
        {
            new AzureNative.Network.Inputs.AzureFirewallIPConfigurationArgs
            {
                Name = "azureFirewallIpConfiguration",
                PublicIPAddress = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName",
                },
                Subnet = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallSubnet",
                },
            },
        },
        Location = "West US 2",
        NatRuleCollections = new[]
        {
            new AzureNative.Network.Inputs.AzureFirewallNatRuleCollectionArgs
            {
                Action = new AzureNative.Network.Inputs.AzureFirewallNatRCActionArgs
                {
                    Type = "Dnat",
                },
                Name = "natrulecoll",
                Priority = 112,
                Rules = new[]
                {
                    new AzureNative.Network.Inputs.AzureFirewallNatRuleArgs
                    {
                        Description = "D-NAT all outbound web traffic for inspection",
                        DestinationAddresses = new[]
                        {
                            "1.2.3.4",
                        },
                        DestinationPorts = new[]
                        {
                            "443",
                        },
                        Name = "DNAT-HTTPS-traffic",
                        Protocols = new[]
                        {
                            "TCP",
                        },
                        SourceAddresses = new[]
                        {
                            "*",
                        },
                        TranslatedAddress = "1.2.3.5",
                        TranslatedPort = "8443",
                    },
                    new AzureNative.Network.Inputs.AzureFirewallNatRuleArgs
                    {
                        Description = "D-NAT all inbound web traffic for inspection",
                        DestinationAddresses = new[]
                        {
                            "1.2.3.4",
                        },
                        DestinationPorts = new[]
                        {
                            "80",
                        },
                        Name = "DNAT-HTTP-traffic-With-FQDN",
                        Protocols = new[]
                        {
                            "TCP",
                        },
                        SourceAddresses = new[]
                        {
                            "*",
                        },
                        TranslatedFqdn = "internalhttpserver",
                        TranslatedPort = "880",
                    },
                },
            },
        },
        NetworkRuleCollections = new[]
        {
            new AzureNative.Network.Inputs.AzureFirewallNetworkRuleCollectionArgs
            {
                Action = new AzureNative.Network.Inputs.AzureFirewallRCActionArgs
                {
                    Type = "Deny",
                },
                Name = "netrulecoll",
                Priority = 112,
                Rules = new[]
                {
                    new AzureNative.Network.Inputs.AzureFirewallNetworkRuleArgs
                    {
                        Description = "Block traffic based on source IPs and ports",
                        DestinationAddresses = new[]
                        {
                            "*",
                        },
                        DestinationPorts = new[]
                        {
                            "443-444",
                            "8443",
                        },
                        Name = "L4-traffic",
                        Protocols = new[]
                        {
                            "TCP",
                        },
                        SourceAddresses = new[]
                        {
                            "192.168.1.1-192.168.1.12",
                            "10.1.4.12-10.1.4.255",
                        },
                    },
                    new AzureNative.Network.Inputs.AzureFirewallNetworkRuleArgs
                    {
                        Description = "Block traffic based on source IPs and ports to amazon",
                        DestinationFqdns = new[]
                        {
                            "www.amazon.com",
                        },
                        DestinationPorts = new[]
                        {
                            "443-444",
                            "8443",
                        },
                        Name = "L4-traffic-with-FQDN",
                        Protocols = new[]
                        {
                            "TCP",
                        },
                        SourceAddresses = new[]
                        {
                            "10.2.4.12-10.2.4.255",
                        },
                    },
                },
            },
        },
        ResourceGroupName = "rg1",
        Sku = new AzureNative.Network.Inputs.AzureFirewallSkuArgs
        {
            Name = "AZFW_VNet",
            Tier = "Standard",
        },
        Tags = 
        {
            { "key1", "value1" },
        },
        ThreatIntelMode = "Alert",
        Zones = new[]
        {
            "1",
            "2",
            "3",
        },
    });

});


```

```go
package main

import (
	network "github.com/pulumi/pulumi-azure-native-sdk/network"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := network.NewAzureFirewall(ctx, "azureFirewall", &network.AzureFirewallArgs{
			ApplicationRuleCollections: []network.AzureFirewallApplicationRuleCollectionArgs{
				{
					Action: {
						Type: pulumi.String("Deny"),
					},
					Name:     pulumi.String("apprulecoll"),
					Priority: pulumi.Int(110),
					Rules: network.AzureFirewallApplicationRuleArray{
						{
							Description: pulumi.String("Deny inbound rule"),
							Name:        pulumi.String("rule1"),
							Protocols: network.AzureFirewallApplicationRuleProtocolArray{
								{
									Port:         pulumi.Int(443),
									ProtocolType: pulumi.String("Https"),
								},
							},
							SourceAddresses: pulumi.StringArray{
								pulumi.String("216.58.216.164"),
								pulumi.String("10.0.0.0/24"),
							},
							TargetFqdns: pulumi.StringArray{
								pulumi.String("www.test.com"),
							},
						},
					},
				},
			},
			AzureFirewallName: pulumi.String("azurefirewall"),
			IpConfigurations: []network.AzureFirewallIPConfigurationArgs{
				{
					Name: pulumi.String("azureFirewallIpConfiguration"),
					PublicIPAddress: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName"),
					},
					Subnet: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallSubnet"),
					},
				},
			},
			Location: pulumi.String("West US 2"),
			NatRuleCollections: []network.AzureFirewallNatRuleCollectionArgs{
				{
					Action: {
						Type: pulumi.String("Dnat"),
					},
					Name:     pulumi.String("natrulecoll"),
					Priority: pulumi.Int(112),
					Rules: network.AzureFirewallNatRuleArray{
						{
							Description: pulumi.String("D-NAT all outbound web traffic for inspection"),
							DestinationAddresses: pulumi.StringArray{
								pulumi.String("1.2.3.4"),
							},
							DestinationPorts: pulumi.StringArray{
								pulumi.String("443"),
							},
							Name: pulumi.String("DNAT-HTTPS-traffic"),
							Protocols: pulumi.StringArray{
								pulumi.String("TCP"),
							},
							SourceAddresses: pulumi.StringArray{
								pulumi.String("*"),
							},
							TranslatedAddress: pulumi.String("1.2.3.5"),
							TranslatedPort:    pulumi.String("8443"),
						},
						{
							Description: pulumi.String("D-NAT all inbound web traffic for inspection"),
							DestinationAddresses: pulumi.StringArray{
								pulumi.String("1.2.3.4"),
							},
							DestinationPorts: pulumi.StringArray{
								pulumi.String("80"),
							},
							Name: pulumi.String("DNAT-HTTP-traffic-With-FQDN"),
							Protocols: pulumi.StringArray{
								pulumi.String("TCP"),
							},
							SourceAddresses: pulumi.StringArray{
								pulumi.String("*"),
							},
							TranslatedFqdn: pulumi.String("internalhttpserver"),
							TranslatedPort: pulumi.String("880"),
						},
					},
				},
			},
			NetworkRuleCollections: []network.AzureFirewallNetworkRuleCollectionArgs{
				{
					Action: {
						Type: pulumi.String("Deny"),
					},
					Name:     pulumi.String("netrulecoll"),
					Priority: pulumi.Int(112),
					Rules: network.AzureFirewallNetworkRuleArray{
						{
							Description: pulumi.String("Block traffic based on source IPs and ports"),
							DestinationAddresses: pulumi.StringArray{
								pulumi.String("*"),
							},
							DestinationPorts: pulumi.StringArray{
								pulumi.String("443-444"),
								pulumi.String("8443"),
							},
							Name: pulumi.String("L4-traffic"),
							Protocols: pulumi.StringArray{
								pulumi.String("TCP"),
							},
							SourceAddresses: pulumi.StringArray{
								pulumi.String("192.168.1.1-192.168.1.12"),
								pulumi.String("10.1.4.12-10.1.4.255"),
							},
						},
						{
							Description: pulumi.String("Block traffic based on source IPs and ports to amazon"),
							DestinationFqdns: pulumi.StringArray{
								pulumi.String("www.amazon.com"),
							},
							DestinationPorts: pulumi.StringArray{
								pulumi.String("443-444"),
								pulumi.String("8443"),
							},
							Name: pulumi.String("L4-traffic-with-FQDN"),
							Protocols: pulumi.StringArray{
								pulumi.String("TCP"),
							},
							SourceAddresses: pulumi.StringArray{
								pulumi.String("10.2.4.12-10.2.4.255"),
							},
						},
					},
				},
			},
			ResourceGroupName: pulumi.String("rg1"),
			Sku: &network.AzureFirewallSkuArgs{
				Name: pulumi.String("AZFW_VNet"),
				Tier: pulumi.String("Standard"),
			},
			Tags: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			ThreatIntelMode: pulumi.String("Alert"),
			Zones: pulumi.StringArray{
				pulumi.String("1"),
				pulumi.String("2"),
				pulumi.String("3"),
			},
		})
		if err != nil {
			return err
		}
		return nil
	})
}

```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.network.AzureFirewall;
import com.pulumi.azurenative.network.AzureFirewallArgs;
import java.util.List;
import java.util.ArrayList;
import java.util.Map;
import java.io.File;
import java.nio.file.Files;
import java.nio.file.Paths;

public class App {
    public static void main(String[] args) {
        Pulumi.run(App::stack);
    }

    public static void stack(Context ctx) {
        var azureFirewall = new AzureFirewall("azureFirewall", AzureFirewallArgs.builder()        
            .applicationRuleCollections(Map.ofEntries(
                Map.entry("action", Map.of("type", "Deny")),
                Map.entry("name", "apprulecoll"),
                Map.entry("priority", 110),
                Map.entry("rules", Map.ofEntries(
                    Map.entry("description", "Deny inbound rule"),
                    Map.entry("name", "rule1"),
                    Map.entry("protocols", Map.ofEntries(
                        Map.entry("port", 443),
                        Map.entry("protocolType", "Https")
                    )),
                    Map.entry("sourceAddresses",                     
                        "216.58.216.164",
                        "10.0.0.0/24"),
                    Map.entry("targetFqdns", "www.test.com")
                ))
            ))
            .azureFirewallName("azurefirewall")
            .ipConfigurations(Map.ofEntries(
                Map.entry("name", "azureFirewallIpConfiguration"),
                Map.entry("publicIPAddress", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName")),
                Map.entry("subnet", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallSubnet"))
            ))
            .location("West US 2")
            .natRuleCollections(Map.ofEntries(
                Map.entry("action", Map.of("type", "Dnat")),
                Map.entry("name", "natrulecoll"),
                Map.entry("priority", 112),
                Map.entry("rules",                 
                    Map.ofEntries(
                        Map.entry("description", "D-NAT all outbound web traffic for inspection"),
                        Map.entry("destinationAddresses", "1.2.3.4"),
                        Map.entry("destinationPorts", "443"),
                        Map.entry("name", "DNAT-HTTPS-traffic"),
                        Map.entry("protocols", "TCP"),
                        Map.entry("sourceAddresses", "*"),
                        Map.entry("translatedAddress", "1.2.3.5"),
                        Map.entry("translatedPort", "8443")
                    ),
                    Map.ofEntries(
                        Map.entry("description", "D-NAT all inbound web traffic for inspection"),
                        Map.entry("destinationAddresses", "1.2.3.4"),
                        Map.entry("destinationPorts", "80"),
                        Map.entry("name", "DNAT-HTTP-traffic-With-FQDN"),
                        Map.entry("protocols", "TCP"),
                        Map.entry("sourceAddresses", "*"),
                        Map.entry("translatedFqdn", "internalhttpserver"),
                        Map.entry("translatedPort", "880")
                    ))
            ))
            .networkRuleCollections(Map.ofEntries(
                Map.entry("action", Map.of("type", "Deny")),
                Map.entry("name", "netrulecoll"),
                Map.entry("priority", 112),
                Map.entry("rules",                 
                    Map.ofEntries(
                        Map.entry("description", "Block traffic based on source IPs and ports"),
                        Map.entry("destinationAddresses", "*"),
                        Map.entry("destinationPorts",                         
                            "443-444",
                            "8443"),
                        Map.entry("name", "L4-traffic"),
                        Map.entry("protocols", "TCP"),
                        Map.entry("sourceAddresses",                         
                            "192.168.1.1-192.168.1.12",
                            "10.1.4.12-10.1.4.255")
                    ),
                    Map.ofEntries(
                        Map.entry("description", "Block traffic based on source IPs and ports to amazon"),
                        Map.entry("destinationFqdns", "www.amazon.com"),
                        Map.entry("destinationPorts",                         
                            "443-444",
                            "8443"),
                        Map.entry("name", "L4-traffic-with-FQDN"),
                        Map.entry("protocols", "TCP"),
                        Map.entry("sourceAddresses", "10.2.4.12-10.2.4.255")
                    ))
            ))
            .resourceGroupName("rg1")
            .sku(Map.ofEntries(
                Map.entry("name", "AZFW_VNet"),
                Map.entry("tier", "Standard")
            ))
            .tags(Map.of("key1", "value1"))
            .threatIntelMode("Alert")
            .zones(            
                "1",
                "2",
                "3")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const azureFirewall = new azure_native.network.AzureFirewall("azureFirewall", {
    applicationRuleCollections: [{
        action: {
            type: "Deny",
        },
        name: "apprulecoll",
        priority: 110,
        rules: [{
            description: "Deny inbound rule",
            name: "rule1",
            protocols: [{
                port: 443,
                protocolType: "Https",
            }],
            sourceAddresses: [
                "216.58.216.164",
                "10.0.0.0/24",
            ],
            targetFqdns: ["www.test.com"],
        }],
    }],
    azureFirewallName: "azurefirewall",
    ipConfigurations: [{
        name: "azureFirewallIpConfiguration",
        publicIPAddress: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName",
        },
        subnet: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallSubnet",
        },
    }],
    location: "West US 2",
    natRuleCollections: [{
        action: {
            type: "Dnat",
        },
        name: "natrulecoll",
        priority: 112,
        rules: [
            {
                description: "D-NAT all outbound web traffic for inspection",
                destinationAddresses: ["1.2.3.4"],
                destinationPorts: ["443"],
                name: "DNAT-HTTPS-traffic",
                protocols: ["TCP"],
                sourceAddresses: ["*"],
                translatedAddress: "1.2.3.5",
                translatedPort: "8443",
            },
            {
                description: "D-NAT all inbound web traffic for inspection",
                destinationAddresses: ["1.2.3.4"],
                destinationPorts: ["80"],
                name: "DNAT-HTTP-traffic-With-FQDN",
                protocols: ["TCP"],
                sourceAddresses: ["*"],
                translatedFqdn: "internalhttpserver",
                translatedPort: "880",
            },
        ],
    }],
    networkRuleCollections: [{
        action: {
            type: "Deny",
        },
        name: "netrulecoll",
        priority: 112,
        rules: [
            {
                description: "Block traffic based on source IPs and ports",
                destinationAddresses: ["*"],
                destinationPorts: [
                    "443-444",
                    "8443",
                ],
                name: "L4-traffic",
                protocols: ["TCP"],
                sourceAddresses: [
                    "192.168.1.1-192.168.1.12",
                    "10.1.4.12-10.1.4.255",
                ],
            },
            {
                description: "Block traffic based on source IPs and ports to amazon",
                destinationFqdns: ["www.amazon.com"],
                destinationPorts: [
                    "443-444",
                    "8443",
                ],
                name: "L4-traffic-with-FQDN",
                protocols: ["TCP"],
                sourceAddresses: ["10.2.4.12-10.2.4.255"],
            },
        ],
    }],
    resourceGroupName: "rg1",
    sku: {
        name: "AZFW_VNet",
        tier: "Standard",
    },
    tags: {
        key1: "value1",
    },
    threatIntelMode: "Alert",
    zones: [
        "1",
        "2",
        "3",
    ],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

azure_firewall = azure_native.network.AzureFirewall("azureFirewall",
    application_rule_collections=[{
        "action": azure_native.network.AzureFirewallRCActionArgs(
            type="Deny",
        ),
        "name": "apprulecoll",
        "priority": 110,
        "rules": [{
            "description": "Deny inbound rule",
            "name": "rule1",
            "protocols": [azure_native.network.AzureFirewallApplicationRuleProtocolArgs(
                port=443,
                protocol_type="Https",
            )],
            "sourceAddresses": [
                "216.58.216.164",
                "10.0.0.0/24",
            ],
            "targetFqdns": ["www.test.com"],
        }],
    }],
    azure_firewall_name="azurefirewall",
    ip_configurations=[{
        "name": "azureFirewallIpConfiguration",
        "publicIPAddress": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName",
        ),
        "subnet": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallSubnet",
        ),
    }],
    location="West US 2",
    nat_rule_collections=[{
        "action": azure_native.network.AzureFirewallNatRCActionArgs(
            type="Dnat",
        ),
        "name": "natrulecoll",
        "priority": 112,
        "rules": [
            azure_native.network.AzureFirewallNatRuleArgs(
                description="D-NAT all outbound web traffic for inspection",
                destination_addresses=["1.2.3.4"],
                destination_ports=["443"],
                name="DNAT-HTTPS-traffic",
                protocols=["TCP"],
                source_addresses=["*"],
                translated_address="1.2.3.5",
                translated_port="8443",
            ),
            azure_native.network.AzureFirewallNatRuleArgs(
                description="D-NAT all inbound web traffic for inspection",
                destination_addresses=["1.2.3.4"],
                destination_ports=["80"],
                name="DNAT-HTTP-traffic-With-FQDN",
                protocols=["TCP"],
                source_addresses=["*"],
                translated_fqdn="internalhttpserver",
                translated_port="880",
            ),
        ],
    }],
    network_rule_collections=[{
        "action": azure_native.network.AzureFirewallRCActionArgs(
            type="Deny",
        ),
        "name": "netrulecoll",
        "priority": 112,
        "rules": [
            azure_native.network.AzureFirewallNetworkRuleArgs(
                description="Block traffic based on source IPs and ports",
                destination_addresses=["*"],
                destination_ports=[
                    "443-444",
                    "8443",
                ],
                name="L4-traffic",
                protocols=["TCP"],
                source_addresses=[
                    "192.168.1.1-192.168.1.12",
                    "10.1.4.12-10.1.4.255",
                ],
            ),
            azure_native.network.AzureFirewallNetworkRuleArgs(
                description="Block traffic based on source IPs and ports to amazon",
                destination_fqdns=["www.amazon.com"],
                destination_ports=[
                    "443-444",
                    "8443",
                ],
                name="L4-traffic-with-FQDN",
                protocols=["TCP"],
                source_addresses=["10.2.4.12-10.2.4.255"],
            ),
        ],
    }],
    resource_group_name="rg1",
    sku=azure_native.network.AzureFirewallSkuArgs(
        name="AZFW_VNet",
        tier="Standard",
    ),
    tags={
        "key1": "value1",
    },
    threat_intel_mode="Alert",
    zones=[
        "1",
        "2",
        "3",
    ])

```

```yaml
resources:
  azureFirewall:
    type: azure-native:network:AzureFirewall
    properties:
      applicationRuleCollections:
        - action:
            type: Deny
          name: apprulecoll
          priority: 110
          rules:
            - description: Deny inbound rule
              name: rule1
              protocols:
                - port: 443
                  protocolType: Https
              sourceAddresses:
                - 216.58.216.164
                - 10.0.0.0/24
              targetFqdns:
                - www.test.com
      azureFirewallName: azurefirewall
      ipConfigurations:
        - name: azureFirewallIpConfiguration
          publicIPAddress:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName
          subnet:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallSubnet
      location: West US 2
      natRuleCollections:
        - action:
            type: Dnat
          name: natrulecoll
          priority: 112
          rules:
            - description: D-NAT all outbound web traffic for inspection
              destinationAddresses:
                - 1.2.3.4
              destinationPorts:
                - '443'
              name: DNAT-HTTPS-traffic
              protocols:
                - TCP
              sourceAddresses:
                - '*'
              translatedAddress: 1.2.3.5
              translatedPort: '8443'
            - description: D-NAT all inbound web traffic for inspection
              destinationAddresses:
                - 1.2.3.4
              destinationPorts:
                - '80'
              name: DNAT-HTTP-traffic-With-FQDN
              protocols:
                - TCP
              sourceAddresses:
                - '*'
              translatedFqdn: internalhttpserver
              translatedPort: '880'
      networkRuleCollections:
        - action:
            type: Deny
          name: netrulecoll
          priority: 112
          rules:
            - description: Block traffic based on source IPs and ports
              destinationAddresses:
                - '*'
              destinationPorts:
                - 443-444
                - '8443'
              name: L4-traffic
              protocols:
                - TCP
              sourceAddresses:
                - 192.168.1.1-192.168.1.12
                - 10.1.4.12-10.1.4.255
            - description: Block traffic based on source IPs and ports to amazon
              destinationFqdns:
                - www.amazon.com
              destinationPorts:
                - 443-444
                - '8443'
              name: L4-traffic-with-FQDN
              protocols:
                - TCP
              sourceAddresses:
                - 10.2.4.12-10.2.4.255
      resourceGroupName: rg1
      sku:
        name: AZFW_VNet
        tier: Standard
      tags:
        key1: value1
      threatIntelMode: Alert
      zones:
        - '1'
        - '2'
        - '3'

```

{{% /example %}}
{{% example %}}
### Create Azure Firewall With management subnet
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var azureFirewall = new AzureNative.Network.AzureFirewall("azureFirewall", new()
    {
        ApplicationRuleCollections = new[]
        {
            new AzureNative.Network.Inputs.AzureFirewallApplicationRuleCollectionArgs
            {
                Action = new AzureNative.Network.Inputs.AzureFirewallRCActionArgs
                {
                    Type = "Deny",
                },
                Name = "apprulecoll",
                Priority = 110,
                Rules = new[]
                {
                    new AzureNative.Network.Inputs.AzureFirewallApplicationRuleArgs
                    {
                        Description = "Deny inbound rule",
                        Name = "rule1",
                        Protocols = new[]
                        {
                            new AzureNative.Network.Inputs.AzureFirewallApplicationRuleProtocolArgs
                            {
                                Port = 443,
                                ProtocolType = "Https",
                            },
                        },
                        SourceAddresses = new[]
                        {
                            "216.58.216.164",
                            "10.0.0.0/24",
                        },
                        TargetFqdns = new[]
                        {
                            "www.test.com",
                        },
                    },
                },
            },
        },
        AzureFirewallName = "azurefirewall",
        IpConfigurations = new[]
        {
            new AzureNative.Network.Inputs.AzureFirewallIPConfigurationArgs
            {
                Name = "azureFirewallIpConfiguration",
                PublicIPAddress = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName",
                },
                Subnet = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallSubnet",
                },
            },
        },
        Location = "West US",
        ManagementIpConfiguration = new AzureNative.Network.Inputs.AzureFirewallIPConfigurationArgs
        {
            Name = "azureFirewallMgmtIpConfiguration",
            PublicIPAddress = new AzureNative.Network.Inputs.SubResourceArgs
            {
                Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/managementPipName",
            },
            Subnet = new AzureNative.Network.Inputs.SubResourceArgs
            {
                Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallManagementSubnet",
            },
        },
        NatRuleCollections = new[]
        {
            new AzureNative.Network.Inputs.AzureFirewallNatRuleCollectionArgs
            {
                Action = new AzureNative.Network.Inputs.AzureFirewallNatRCActionArgs
                {
                    Type = "Dnat",
                },
                Name = "natrulecoll",
                Priority = 112,
                Rules = new[]
                {
                    new AzureNative.Network.Inputs.AzureFirewallNatRuleArgs
                    {
                        Description = "D-NAT all outbound web traffic for inspection",
                        DestinationAddresses = new[]
                        {
                            "1.2.3.4",
                        },
                        DestinationPorts = new[]
                        {
                            "443",
                        },
                        Name = "DNAT-HTTPS-traffic",
                        Protocols = new[]
                        {
                            "TCP",
                        },
                        SourceAddresses = new[]
                        {
                            "*",
                        },
                        TranslatedAddress = "1.2.3.5",
                        TranslatedPort = "8443",
                    },
                    new AzureNative.Network.Inputs.AzureFirewallNatRuleArgs
                    {
                        Description = "D-NAT all inbound web traffic for inspection",
                        DestinationAddresses = new[]
                        {
                            "1.2.3.4",
                        },
                        DestinationPorts = new[]
                        {
                            "80",
                        },
                        Name = "DNAT-HTTP-traffic-With-FQDN",
                        Protocols = new[]
                        {
                            "TCP",
                        },
                        SourceAddresses = new[]
                        {
                            "*",
                        },
                        TranslatedFqdn = "internalhttpserver",
                        TranslatedPort = "880",
                    },
                },
            },
        },
        NetworkRuleCollections = new[]
        {
            new AzureNative.Network.Inputs.AzureFirewallNetworkRuleCollectionArgs
            {
                Action = new AzureNative.Network.Inputs.AzureFirewallRCActionArgs
                {
                    Type = "Deny",
                },
                Name = "netrulecoll",
                Priority = 112,
                Rules = new[]
                {
                    new AzureNative.Network.Inputs.AzureFirewallNetworkRuleArgs
                    {
                        Description = "Block traffic based on source IPs and ports",
                        DestinationAddresses = new[]
                        {
                            "*",
                        },
                        DestinationPorts = new[]
                        {
                            "443-444",
                            "8443",
                        },
                        Name = "L4-traffic",
                        Protocols = new[]
                        {
                            "TCP",
                        },
                        SourceAddresses = new[]
                        {
                            "192.168.1.1-192.168.1.12",
                            "10.1.4.12-10.1.4.255",
                        },
                    },
                    new AzureNative.Network.Inputs.AzureFirewallNetworkRuleArgs
                    {
                        Description = "Block traffic based on source IPs and ports to amazon",
                        DestinationFqdns = new[]
                        {
                            "www.amazon.com",
                        },
                        DestinationPorts = new[]
                        {
                            "443-444",
                            "8443",
                        },
                        Name = "L4-traffic-with-FQDN",
                        Protocols = new[]
                        {
                            "TCP",
                        },
                        SourceAddresses = new[]
                        {
                            "10.2.4.12-10.2.4.255",
                        },
                    },
                },
            },
        },
        ResourceGroupName = "rg1",
        Sku = new AzureNative.Network.Inputs.AzureFirewallSkuArgs
        {
            Name = "AZFW_VNet",
            Tier = "Standard",
        },
        Tags = 
        {
            { "key1", "value1" },
        },
        ThreatIntelMode = "Alert",
        Zones = new[] {},
    });

});


```

```go
package main

import (
	network "github.com/pulumi/pulumi-azure-native-sdk/network"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := network.NewAzureFirewall(ctx, "azureFirewall", &network.AzureFirewallArgs{
			ApplicationRuleCollections: []network.AzureFirewallApplicationRuleCollectionArgs{
				{
					Action: {
						Type: pulumi.String("Deny"),
					},
					Name:     pulumi.String("apprulecoll"),
					Priority: pulumi.Int(110),
					Rules: network.AzureFirewallApplicationRuleArray{
						{
							Description: pulumi.String("Deny inbound rule"),
							Name:        pulumi.String("rule1"),
							Protocols: network.AzureFirewallApplicationRuleProtocolArray{
								{
									Port:         pulumi.Int(443),
									ProtocolType: pulumi.String("Https"),
								},
							},
							SourceAddresses: pulumi.StringArray{
								pulumi.String("216.58.216.164"),
								pulumi.String("10.0.0.0/24"),
							},
							TargetFqdns: pulumi.StringArray{
								pulumi.String("www.test.com"),
							},
						},
					},
				},
			},
			AzureFirewallName: pulumi.String("azurefirewall"),
			IpConfigurations: []network.AzureFirewallIPConfigurationArgs{
				{
					Name: pulumi.String("azureFirewallIpConfiguration"),
					PublicIPAddress: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName"),
					},
					Subnet: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallSubnet"),
					},
				},
			},
			Location: pulumi.String("West US"),
			ManagementIpConfiguration: network.AzureFirewallIPConfigurationResponse{
				Name: pulumi.String("azureFirewallMgmtIpConfiguration"),
				PublicIPAddress: &network.SubResourceArgs{
					Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/managementPipName"),
				},
				Subnet: &network.SubResourceArgs{
					Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallManagementSubnet"),
				},
			},
			NatRuleCollections: []network.AzureFirewallNatRuleCollectionArgs{
				{
					Action: {
						Type: pulumi.String("Dnat"),
					},
					Name:     pulumi.String("natrulecoll"),
					Priority: pulumi.Int(112),
					Rules: network.AzureFirewallNatRuleArray{
						{
							Description: pulumi.String("D-NAT all outbound web traffic for inspection"),
							DestinationAddresses: pulumi.StringArray{
								pulumi.String("1.2.3.4"),
							},
							DestinationPorts: pulumi.StringArray{
								pulumi.String("443"),
							},
							Name: pulumi.String("DNAT-HTTPS-traffic"),
							Protocols: pulumi.StringArray{
								pulumi.String("TCP"),
							},
							SourceAddresses: pulumi.StringArray{
								pulumi.String("*"),
							},
							TranslatedAddress: pulumi.String("1.2.3.5"),
							TranslatedPort:    pulumi.String("8443"),
						},
						{
							Description: pulumi.String("D-NAT all inbound web traffic for inspection"),
							DestinationAddresses: pulumi.StringArray{
								pulumi.String("1.2.3.4"),
							},
							DestinationPorts: pulumi.StringArray{
								pulumi.String("80"),
							},
							Name: pulumi.String("DNAT-HTTP-traffic-With-FQDN"),
							Protocols: pulumi.StringArray{
								pulumi.String("TCP"),
							},
							SourceAddresses: pulumi.StringArray{
								pulumi.String("*"),
							},
							TranslatedFqdn: pulumi.String("internalhttpserver"),
							TranslatedPort: pulumi.String("880"),
						},
					},
				},
			},
			NetworkRuleCollections: []network.AzureFirewallNetworkRuleCollectionArgs{
				{
					Action: {
						Type: pulumi.String("Deny"),
					},
					Name:     pulumi.String("netrulecoll"),
					Priority: pulumi.Int(112),
					Rules: network.AzureFirewallNetworkRuleArray{
						{
							Description: pulumi.String("Block traffic based on source IPs and ports"),
							DestinationAddresses: pulumi.StringArray{
								pulumi.String("*"),
							},
							DestinationPorts: pulumi.StringArray{
								pulumi.String("443-444"),
								pulumi.String("8443"),
							},
							Name: pulumi.String("L4-traffic"),
							Protocols: pulumi.StringArray{
								pulumi.String("TCP"),
							},
							SourceAddresses: pulumi.StringArray{
								pulumi.String("192.168.1.1-192.168.1.12"),
								pulumi.String("10.1.4.12-10.1.4.255"),
							},
						},
						{
							Description: pulumi.String("Block traffic based on source IPs and ports to amazon"),
							DestinationFqdns: pulumi.StringArray{
								pulumi.String("www.amazon.com"),
							},
							DestinationPorts: pulumi.StringArray{
								pulumi.String("443-444"),
								pulumi.String("8443"),
							},
							Name: pulumi.String("L4-traffic-with-FQDN"),
							Protocols: pulumi.StringArray{
								pulumi.String("TCP"),
							},
							SourceAddresses: pulumi.StringArray{
								pulumi.String("10.2.4.12-10.2.4.255"),
							},
						},
					},
				},
			},
			ResourceGroupName: pulumi.String("rg1"),
			Sku: &network.AzureFirewallSkuArgs{
				Name: pulumi.String("AZFW_VNet"),
				Tier: pulumi.String("Standard"),
			},
			Tags: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			ThreatIntelMode: pulumi.String("Alert"),
			Zones:           pulumi.StringArray{},
		})
		if err != nil {
			return err
		}
		return nil
	})
}

```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.network.AzureFirewall;
import com.pulumi.azurenative.network.AzureFirewallArgs;
import java.util.List;
import java.util.ArrayList;
import java.util.Map;
import java.io.File;
import java.nio.file.Files;
import java.nio.file.Paths;

public class App {
    public static void main(String[] args) {
        Pulumi.run(App::stack);
    }

    public static void stack(Context ctx) {
        var azureFirewall = new AzureFirewall("azureFirewall", AzureFirewallArgs.builder()        
            .applicationRuleCollections(Map.ofEntries(
                Map.entry("action", Map.of("type", "Deny")),
                Map.entry("name", "apprulecoll"),
                Map.entry("priority", 110),
                Map.entry("rules", Map.ofEntries(
                    Map.entry("description", "Deny inbound rule"),
                    Map.entry("name", "rule1"),
                    Map.entry("protocols", Map.ofEntries(
                        Map.entry("port", 443),
                        Map.entry("protocolType", "Https")
                    )),
                    Map.entry("sourceAddresses",                     
                        "216.58.216.164",
                        "10.0.0.0/24"),
                    Map.entry("targetFqdns", "www.test.com")
                ))
            ))
            .azureFirewallName("azurefirewall")
            .ipConfigurations(Map.ofEntries(
                Map.entry("name", "azureFirewallIpConfiguration"),
                Map.entry("publicIPAddress", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName")),
                Map.entry("subnet", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallSubnet"))
            ))
            .location("West US")
            .managementIpConfiguration(Map.ofEntries(
                Map.entry("name", "azureFirewallMgmtIpConfiguration"),
                Map.entry("publicIPAddress", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/managementPipName")),
                Map.entry("subnet", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallManagementSubnet"))
            ))
            .natRuleCollections(Map.ofEntries(
                Map.entry("action", Map.of("type", "Dnat")),
                Map.entry("name", "natrulecoll"),
                Map.entry("priority", 112),
                Map.entry("rules",                 
                    Map.ofEntries(
                        Map.entry("description", "D-NAT all outbound web traffic for inspection"),
                        Map.entry("destinationAddresses", "1.2.3.4"),
                        Map.entry("destinationPorts", "443"),
                        Map.entry("name", "DNAT-HTTPS-traffic"),
                        Map.entry("protocols", "TCP"),
                        Map.entry("sourceAddresses", "*"),
                        Map.entry("translatedAddress", "1.2.3.5"),
                        Map.entry("translatedPort", "8443")
                    ),
                    Map.ofEntries(
                        Map.entry("description", "D-NAT all inbound web traffic for inspection"),
                        Map.entry("destinationAddresses", "1.2.3.4"),
                        Map.entry("destinationPorts", "80"),
                        Map.entry("name", "DNAT-HTTP-traffic-With-FQDN"),
                        Map.entry("protocols", "TCP"),
                        Map.entry("sourceAddresses", "*"),
                        Map.entry("translatedFqdn", "internalhttpserver"),
                        Map.entry("translatedPort", "880")
                    ))
            ))
            .networkRuleCollections(Map.ofEntries(
                Map.entry("action", Map.of("type", "Deny")),
                Map.entry("name", "netrulecoll"),
                Map.entry("priority", 112),
                Map.entry("rules",                 
                    Map.ofEntries(
                        Map.entry("description", "Block traffic based on source IPs and ports"),
                        Map.entry("destinationAddresses", "*"),
                        Map.entry("destinationPorts",                         
                            "443-444",
                            "8443"),
                        Map.entry("name", "L4-traffic"),
                        Map.entry("protocols", "TCP"),
                        Map.entry("sourceAddresses",                         
                            "192.168.1.1-192.168.1.12",
                            "10.1.4.12-10.1.4.255")
                    ),
                    Map.ofEntries(
                        Map.entry("description", "Block traffic based on source IPs and ports to amazon"),
                        Map.entry("destinationFqdns", "www.amazon.com"),
                        Map.entry("destinationPorts",                         
                            "443-444",
                            "8443"),
                        Map.entry("name", "L4-traffic-with-FQDN"),
                        Map.entry("protocols", "TCP"),
                        Map.entry("sourceAddresses", "10.2.4.12-10.2.4.255")
                    ))
            ))
            .resourceGroupName("rg1")
            .sku(Map.ofEntries(
                Map.entry("name", "AZFW_VNet"),
                Map.entry("tier", "Standard")
            ))
            .tags(Map.of("key1", "value1"))
            .threatIntelMode("Alert")
            .zones()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const azureFirewall = new azure_native.network.AzureFirewall("azureFirewall", {
    applicationRuleCollections: [{
        action: {
            type: "Deny",
        },
        name: "apprulecoll",
        priority: 110,
        rules: [{
            description: "Deny inbound rule",
            name: "rule1",
            protocols: [{
                port: 443,
                protocolType: "Https",
            }],
            sourceAddresses: [
                "216.58.216.164",
                "10.0.0.0/24",
            ],
            targetFqdns: ["www.test.com"],
        }],
    }],
    azureFirewallName: "azurefirewall",
    ipConfigurations: [{
        name: "azureFirewallIpConfiguration",
        publicIPAddress: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName",
        },
        subnet: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallSubnet",
        },
    }],
    location: "West US",
    managementIpConfiguration: {
        name: "azureFirewallMgmtIpConfiguration",
        publicIPAddress: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/managementPipName",
        },
        subnet: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallManagementSubnet",
        },
    },
    natRuleCollections: [{
        action: {
            type: "Dnat",
        },
        name: "natrulecoll",
        priority: 112,
        rules: [
            {
                description: "D-NAT all outbound web traffic for inspection",
                destinationAddresses: ["1.2.3.4"],
                destinationPorts: ["443"],
                name: "DNAT-HTTPS-traffic",
                protocols: ["TCP"],
                sourceAddresses: ["*"],
                translatedAddress: "1.2.3.5",
                translatedPort: "8443",
            },
            {
                description: "D-NAT all inbound web traffic for inspection",
                destinationAddresses: ["1.2.3.4"],
                destinationPorts: ["80"],
                name: "DNAT-HTTP-traffic-With-FQDN",
                protocols: ["TCP"],
                sourceAddresses: ["*"],
                translatedFqdn: "internalhttpserver",
                translatedPort: "880",
            },
        ],
    }],
    networkRuleCollections: [{
        action: {
            type: "Deny",
        },
        name: "netrulecoll",
        priority: 112,
        rules: [
            {
                description: "Block traffic based on source IPs and ports",
                destinationAddresses: ["*"],
                destinationPorts: [
                    "443-444",
                    "8443",
                ],
                name: "L4-traffic",
                protocols: ["TCP"],
                sourceAddresses: [
                    "192.168.1.1-192.168.1.12",
                    "10.1.4.12-10.1.4.255",
                ],
            },
            {
                description: "Block traffic based on source IPs and ports to amazon",
                destinationFqdns: ["www.amazon.com"],
                destinationPorts: [
                    "443-444",
                    "8443",
                ],
                name: "L4-traffic-with-FQDN",
                protocols: ["TCP"],
                sourceAddresses: ["10.2.4.12-10.2.4.255"],
            },
        ],
    }],
    resourceGroupName: "rg1",
    sku: {
        name: "AZFW_VNet",
        tier: "Standard",
    },
    tags: {
        key1: "value1",
    },
    threatIntelMode: "Alert",
    zones: [],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

azure_firewall = azure_native.network.AzureFirewall("azureFirewall",
    application_rule_collections=[{
        "action": azure_native.network.AzureFirewallRCActionArgs(
            type="Deny",
        ),
        "name": "apprulecoll",
        "priority": 110,
        "rules": [{
            "description": "Deny inbound rule",
            "name": "rule1",
            "protocols": [azure_native.network.AzureFirewallApplicationRuleProtocolArgs(
                port=443,
                protocol_type="Https",
            )],
            "sourceAddresses": [
                "216.58.216.164",
                "10.0.0.0/24",
            ],
            "targetFqdns": ["www.test.com"],
        }],
    }],
    azure_firewall_name="azurefirewall",
    ip_configurations=[{
        "name": "azureFirewallIpConfiguration",
        "publicIPAddress": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName",
        ),
        "subnet": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallSubnet",
        ),
    }],
    location="West US",
    management_ip_configuration=azure_native.network.AzureFirewallIPConfigurationResponseArgs(
        name="azureFirewallMgmtIpConfiguration",
        public_ip_address=azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/managementPipName",
        ),
        subnet=azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallManagementSubnet",
        ),
    ),
    nat_rule_collections=[{
        "action": azure_native.network.AzureFirewallNatRCActionArgs(
            type="Dnat",
        ),
        "name": "natrulecoll",
        "priority": 112,
        "rules": [
            azure_native.network.AzureFirewallNatRuleArgs(
                description="D-NAT all outbound web traffic for inspection",
                destination_addresses=["1.2.3.4"],
                destination_ports=["443"],
                name="DNAT-HTTPS-traffic",
                protocols=["TCP"],
                source_addresses=["*"],
                translated_address="1.2.3.5",
                translated_port="8443",
            ),
            azure_native.network.AzureFirewallNatRuleArgs(
                description="D-NAT all inbound web traffic for inspection",
                destination_addresses=["1.2.3.4"],
                destination_ports=["80"],
                name="DNAT-HTTP-traffic-With-FQDN",
                protocols=["TCP"],
                source_addresses=["*"],
                translated_fqdn="internalhttpserver",
                translated_port="880",
            ),
        ],
    }],
    network_rule_collections=[{
        "action": azure_native.network.AzureFirewallRCActionArgs(
            type="Deny",
        ),
        "name": "netrulecoll",
        "priority": 112,
        "rules": [
            azure_native.network.AzureFirewallNetworkRuleArgs(
                description="Block traffic based on source IPs and ports",
                destination_addresses=["*"],
                destination_ports=[
                    "443-444",
                    "8443",
                ],
                name="L4-traffic",
                protocols=["TCP"],
                source_addresses=[
                    "192.168.1.1-192.168.1.12",
                    "10.1.4.12-10.1.4.255",
                ],
            ),
            azure_native.network.AzureFirewallNetworkRuleArgs(
                description="Block traffic based on source IPs and ports to amazon",
                destination_fqdns=["www.amazon.com"],
                destination_ports=[
                    "443-444",
                    "8443",
                ],
                name="L4-traffic-with-FQDN",
                protocols=["TCP"],
                source_addresses=["10.2.4.12-10.2.4.255"],
            ),
        ],
    }],
    resource_group_name="rg1",
    sku=azure_native.network.AzureFirewallSkuArgs(
        name="AZFW_VNet",
        tier="Standard",
    ),
    tags={
        "key1": "value1",
    },
    threat_intel_mode="Alert",
    zones=[])

```

```yaml
resources:
  azureFirewall:
    type: azure-native:network:AzureFirewall
    properties:
      applicationRuleCollections:
        - action:
            type: Deny
          name: apprulecoll
          priority: 110
          rules:
            - description: Deny inbound rule
              name: rule1
              protocols:
                - port: 443
                  protocolType: Https
              sourceAddresses:
                - 216.58.216.164
                - 10.0.0.0/24
              targetFqdns:
                - www.test.com
      azureFirewallName: azurefirewall
      ipConfigurations:
        - name: azureFirewallIpConfiguration
          publicIPAddress:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName
          subnet:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallSubnet
      location: West US
      managementIpConfiguration:
        name: azureFirewallMgmtIpConfiguration
        publicIPAddress:
          id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/managementPipName
        subnet:
          id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/AzureFirewallManagementSubnet
      natRuleCollections:
        - action:
            type: Dnat
          name: natrulecoll
          priority: 112
          rules:
            - description: D-NAT all outbound web traffic for inspection
              destinationAddresses:
                - 1.2.3.4
              destinationPorts:
                - '443'
              name: DNAT-HTTPS-traffic
              protocols:
                - TCP
              sourceAddresses:
                - '*'
              translatedAddress: 1.2.3.5
              translatedPort: '8443'
            - description: D-NAT all inbound web traffic for inspection
              destinationAddresses:
                - 1.2.3.4
              destinationPorts:
                - '80'
              name: DNAT-HTTP-traffic-With-FQDN
              protocols:
                - TCP
              sourceAddresses:
                - '*'
              translatedFqdn: internalhttpserver
              translatedPort: '880'
      networkRuleCollections:
        - action:
            type: Deny
          name: netrulecoll
          priority: 112
          rules:
            - description: Block traffic based on source IPs and ports
              destinationAddresses:
                - '*'
              destinationPorts:
                - 443-444
                - '8443'
              name: L4-traffic
              protocols:
                - TCP
              sourceAddresses:
                - 192.168.1.1-192.168.1.12
                - 10.1.4.12-10.1.4.255
            - description: Block traffic based on source IPs and ports to amazon
              destinationFqdns:
                - www.amazon.com
              destinationPorts:
                - 443-444
                - '8443'
              name: L4-traffic-with-FQDN
              protocols:
                - TCP
              sourceAddresses:
                - 10.2.4.12-10.2.4.255
      resourceGroupName: rg1
      sku:
        name: AZFW_VNet
        tier: Standard
      tags:
        key1: value1
      threatIntelMode: Alert
      zones: []

```

{{% /example %}}
{{% example %}}
### Create Azure Firewall in virtual Hub
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var azureFirewall = new AzureNative.Network.AzureFirewall("azureFirewall", new()
    {
        AzureFirewallName = "azurefirewall",
        FirewallPolicy = new AzureNative.Network.Inputs.SubResourceArgs
        {
            Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/firewallPolicies/policy1",
        },
        HubIPAddresses = new AzureNative.Network.Inputs.HubIPAddressesArgs
        {
            PublicIPs = new AzureNative.Network.Inputs.HubPublicIPAddressesArgs
            {
                Addresses = new[] {},
                Count = 1,
            },
        },
        Location = "West US",
        ResourceGroupName = "rg1",
        Sku = new AzureNative.Network.Inputs.AzureFirewallSkuArgs
        {
            Name = "AZFW_Hub",
            Tier = "Standard",
        },
        Tags = 
        {
            { "key1", "value1" },
        },
        ThreatIntelMode = "Alert",
        VirtualHub = new AzureNative.Network.Inputs.SubResourceArgs
        {
            Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1",
        },
        Zones = new[] {},
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.network.AzureFirewall;
import com.pulumi.azurenative.network.AzureFirewallArgs;
import java.util.List;
import java.util.ArrayList;
import java.util.Map;
import java.io.File;
import java.nio.file.Files;
import java.nio.file.Paths;

public class App {
    public static void main(String[] args) {
        Pulumi.run(App::stack);
    }

    public static void stack(Context ctx) {
        var azureFirewall = new AzureFirewall("azureFirewall", AzureFirewallArgs.builder()        
            .azureFirewallName("azurefirewall")
            .firewallPolicy(Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/firewallPolicies/policy1"))
            .hubIPAddresses(Map.of("publicIPs", Map.ofEntries(
                Map.entry("addresses", ),
                Map.entry("count", 1)
            )))
            .location("West US")
            .resourceGroupName("rg1")
            .sku(Map.ofEntries(
                Map.entry("name", "AZFW_Hub"),
                Map.entry("tier", "Standard")
            ))
            .tags(Map.of("key1", "value1"))
            .threatIntelMode("Alert")
            .virtualHub(Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1"))
            .zones()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const azureFirewall = new azure_native.network.AzureFirewall("azureFirewall", {
    azureFirewallName: "azurefirewall",
    firewallPolicy: {
        id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/firewallPolicies/policy1",
    },
    hubIPAddresses: {
        publicIPs: {
            addresses: [],
            count: 1,
        },
    },
    location: "West US",
    resourceGroupName: "rg1",
    sku: {
        name: "AZFW_Hub",
        tier: "Standard",
    },
    tags: {
        key1: "value1",
    },
    threatIntelMode: "Alert",
    virtualHub: {
        id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1",
    },
    zones: [],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

azure_firewall = azure_native.network.AzureFirewall("azureFirewall",
    azure_firewall_name="azurefirewall",
    firewall_policy=azure_native.network.SubResourceArgs(
        id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/firewallPolicies/policy1",
    ),
    hub_ip_addresses=azure_native.network.HubIPAddressesResponseArgs(
        public_ips={
            "addresses": [],
            "count": 1,
        },
    ),
    location="West US",
    resource_group_name="rg1",
    sku=azure_native.network.AzureFirewallSkuArgs(
        name="AZFW_Hub",
        tier="Standard",
    ),
    tags={
        "key1": "value1",
    },
    threat_intel_mode="Alert",
    virtual_hub=azure_native.network.SubResourceArgs(
        id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1",
    ),
    zones=[])

```

```yaml
resources:
  azureFirewall:
    type: azure-native:network:AzureFirewall
    properties:
      azureFirewallName: azurefirewall
      firewallPolicy:
        id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/firewallPolicies/policy1
      hubIPAddresses:
        publicIPs:
          addresses: []
          count: 1
      location: West US
      resourceGroupName: rg1
      sku:
        name: AZFW_Hub
        tier: Standard
      tags:
        key1: value1
      threatIntelMode: Alert
      virtualHub:
        id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1
      zones: []

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:AzureFirewall azurefirewall /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/azureFirewalls/azurefirewall 
```
