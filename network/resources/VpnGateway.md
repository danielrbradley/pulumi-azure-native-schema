VpnGateway Resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### VpnGatewayPut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var vpnGateway = new AzureNative.Network.VpnGateway("vpnGateway", new()
    {
        BgpSettings = new AzureNative.Network.Inputs.BgpSettingsArgs
        {
            Asn = 65515,
            BgpPeeringAddresses = new[]
            {
                new AzureNative.Network.Inputs.IPConfigurationBgpPeeringAddressArgs
                {
                    CustomBgpIpAddresses = new[]
                    {
                        "169.254.21.5",
                    },
                    IpconfigurationId = "Instance0",
                },
                new AzureNative.Network.Inputs.IPConfigurationBgpPeeringAddressArgs
                {
                    CustomBgpIpAddresses = new[]
                    {
                        "169.254.21.10",
                    },
                    IpconfigurationId = "Instance1",
                },
            },
            PeerWeight = 0,
        },
        Connections = new[]
        {
            new AzureNative.Network.Inputs.VpnConnectionArgs
            {
                Name = "vpnConnection1",
                RemoteVpnSite = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnSites/vpnSite1",
                },
                VpnLinkConnections = new[]
                {
                    new AzureNative.Network.Inputs.VpnSiteLinkConnectionArgs
                    {
                        ConnectionBandwidth = 200,
                        EgressNatRules = new[]
                        {
                            new AzureNative.Network.Inputs.SubResourceArgs
                            {
                                Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnGateways/gateway1/natRules/nat03",
                            },
                        },
                        Name = "Connection-Link1",
                        SharedKey = "key",
                        VpnConnectionProtocolType = "IKEv2",
                        VpnSiteLink = new AzureNative.Network.Inputs.SubResourceArgs
                        {
                            Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnSites/vpnSite1/vpnSiteLinks/siteLink1",
                        },
                    },
                },
            },
        },
        EnableBgpRouteTranslationForNat = false,
        GatewayName = "gateway1",
        IsRoutingPreferenceInternet = false,
        Location = "westcentralus",
        NatRules = new[]
        {
            new AzureNative.Network.Inputs.VpnGatewayNatRuleArgs
            {
                ExternalMappings = new[]
                {
                    new AzureNative.Network.Inputs.VpnNatRuleMappingArgs
                    {
                        AddressSpace = "192.168.0.0/26",
                    },
                },
                InternalMappings = new[]
                {
                    new AzureNative.Network.Inputs.VpnNatRuleMappingArgs
                    {
                        AddressSpace = "0.0.0.0/26",
                    },
                },
                IpConfigurationId = "",
                Mode = "EgressSnat",
                Name = "nat03",
                Type = "Static",
            },
        },
        ResourceGroupName = "rg1",
        Tags = 
        {
            { "key1", "value1" },
        },
        VirtualHub = new AzureNative.Network.Inputs.SubResourceArgs
        {
            Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1",
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
		_, err := network.NewVpnGateway(ctx, "vpnGateway", &network.VpnGatewayArgs{
			BgpSettings: network.BgpSettingsResponse{
				Asn: pulumi.Float64(65515),
				BgpPeeringAddresses: network.IPConfigurationBgpPeeringAddressArray{
					&network.IPConfigurationBgpPeeringAddressArgs{
						CustomBgpIpAddresses: pulumi.StringArray{
							pulumi.String("169.254.21.5"),
						},
						IpconfigurationId: pulumi.String("Instance0"),
					},
					&network.IPConfigurationBgpPeeringAddressArgs{
						CustomBgpIpAddresses: pulumi.StringArray{
							pulumi.String("169.254.21.10"),
						},
						IpconfigurationId: pulumi.String("Instance1"),
					},
				},
				PeerWeight: pulumi.Int(0),
			},
			Connections: []network.VpnConnectionTypeArgs{
				{
					Name: pulumi.String("vpnConnection1"),
					RemoteVpnSite: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnSites/vpnSite1"),
					},
					VpnLinkConnections: network.VpnSiteLinkConnectionArray{
						{
							ConnectionBandwidth: pulumi.Int(200),
							EgressNatRules: network.SubResourceArray{
								{
									Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnGateways/gateway1/natRules/nat03"),
								},
							},
							Name:                      pulumi.String("Connection-Link1"),
							SharedKey:                 pulumi.String("key"),
							VpnConnectionProtocolType: pulumi.String("IKEv2"),
							VpnSiteLink: {
								Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnSites/vpnSite1/vpnSiteLinks/siteLink1"),
							},
						},
					},
				},
			},
			EnableBgpRouteTranslationForNat: pulumi.Bool(false),
			GatewayName:                     pulumi.String("gateway1"),
			IsRoutingPreferenceInternet:     pulumi.Bool(false),
			Location:                        pulumi.String("westcentralus"),
			NatRules: []network.VpnGatewayNatRuleArgs{
				{
					ExternalMappings: network.VpnNatRuleMappingArray{
						{
							AddressSpace: pulumi.String("192.168.0.0/26"),
						},
					},
					InternalMappings: network.VpnNatRuleMappingArray{
						{
							AddressSpace: pulumi.String("0.0.0.0/26"),
						},
					},
					IpConfigurationId: pulumi.String(""),
					Mode:              pulumi.String("EgressSnat"),
					Name:              pulumi.String("nat03"),
					Type:              pulumi.String("Static"),
				},
			},
			ResourceGroupName: pulumi.String("rg1"),
			Tags: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			VirtualHub: &network.SubResourceArgs{
				Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1"),
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
import com.pulumi.azurenative.network.VpnGateway;
import com.pulumi.azurenative.network.VpnGatewayArgs;
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
        var vpnGateway = new VpnGateway("vpnGateway", VpnGatewayArgs.builder()        
            .bgpSettings(Map.ofEntries(
                Map.entry("asn", 65515),
                Map.entry("bgpPeeringAddresses",                 
                    Map.ofEntries(
                        Map.entry("customBgpIpAddresses", "169.254.21.5"),
                        Map.entry("ipconfigurationId", "Instance0")
                    ),
                    Map.ofEntries(
                        Map.entry("customBgpIpAddresses", "169.254.21.10"),
                        Map.entry("ipconfigurationId", "Instance1")
                    )),
                Map.entry("peerWeight", 0)
            ))
            .connections(Map.ofEntries(
                Map.entry("name", "vpnConnection1"),
                Map.entry("remoteVpnSite", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnSites/vpnSite1")),
                Map.entry("vpnLinkConnections", Map.ofEntries(
                    Map.entry("connectionBandwidth", 200),
                    Map.entry("egressNatRules", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnGateways/gateway1/natRules/nat03")),
                    Map.entry("name", "Connection-Link1"),
                    Map.entry("sharedKey", "key"),
                    Map.entry("vpnConnectionProtocolType", "IKEv2"),
                    Map.entry("vpnSiteLink", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnSites/vpnSite1/vpnSiteLinks/siteLink1"))
                ))
            ))
            .enableBgpRouteTranslationForNat(false)
            .gatewayName("gateway1")
            .isRoutingPreferenceInternet(false)
            .location("westcentralus")
            .natRules(Map.ofEntries(
                Map.entry("externalMappings", Map.of("addressSpace", "192.168.0.0/26")),
                Map.entry("internalMappings", Map.of("addressSpace", "0.0.0.0/26")),
                Map.entry("ipConfigurationId", ""),
                Map.entry("mode", "EgressSnat"),
                Map.entry("name", "nat03"),
                Map.entry("type", "Static")
            ))
            .resourceGroupName("rg1")
            .tags(Map.of("key1", "value1"))
            .virtualHub(Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const vpnGateway = new azure_native.network.VpnGateway("vpnGateway", {
    bgpSettings: {
        asn: 65515,
        bgpPeeringAddresses: [
            {
                customBgpIpAddresses: ["169.254.21.5"],
                ipconfigurationId: "Instance0",
            },
            {
                customBgpIpAddresses: ["169.254.21.10"],
                ipconfigurationId: "Instance1",
            },
        ],
        peerWeight: 0,
    },
    connections: [{
        name: "vpnConnection1",
        remoteVpnSite: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnSites/vpnSite1",
        },
        vpnLinkConnections: [{
            connectionBandwidth: 200,
            egressNatRules: [{
                id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnGateways/gateway1/natRules/nat03",
            }],
            name: "Connection-Link1",
            sharedKey: "key",
            vpnConnectionProtocolType: "IKEv2",
            vpnSiteLink: {
                id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnSites/vpnSite1/vpnSiteLinks/siteLink1",
            },
        }],
    }],
    enableBgpRouteTranslationForNat: false,
    gatewayName: "gateway1",
    isRoutingPreferenceInternet: false,
    location: "westcentralus",
    natRules: [{
        externalMappings: [{
            addressSpace: "192.168.0.0/26",
        }],
        internalMappings: [{
            addressSpace: "0.0.0.0/26",
        }],
        ipConfigurationId: "",
        mode: "EgressSnat",
        name: "nat03",
        type: "Static",
    }],
    resourceGroupName: "rg1",
    tags: {
        key1: "value1",
    },
    virtualHub: {
        id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

vpn_gateway = azure_native.network.VpnGateway("vpnGateway",
    bgp_settings=azure_native.network.BgpSettingsResponseArgs(
        asn=65515,
        bgp_peering_addresses=[
            azure_native.network.IPConfigurationBgpPeeringAddressArgs(
                custom_bgp_ip_addresses=["169.254.21.5"],
                ipconfiguration_id="Instance0",
            ),
            azure_native.network.IPConfigurationBgpPeeringAddressArgs(
                custom_bgp_ip_addresses=["169.254.21.10"],
                ipconfiguration_id="Instance1",
            ),
        ],
        peer_weight=0,
    ),
    connections=[{
        "name": "vpnConnection1",
        "remoteVpnSite": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnSites/vpnSite1",
        ),
        "vpnLinkConnections": [{
            "connectionBandwidth": 200,
            "egressNatRules": [azure_native.network.SubResourceArgs(
                id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnGateways/gateway1/natRules/nat03",
            )],
            "name": "Connection-Link1",
            "sharedKey": "key",
            "vpnConnectionProtocolType": "IKEv2",
            "vpnSiteLink": azure_native.network.SubResourceArgs(
                id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnSites/vpnSite1/vpnSiteLinks/siteLink1",
            ),
        }],
    }],
    enable_bgp_route_translation_for_nat=False,
    gateway_name="gateway1",
    is_routing_preference_internet=False,
    location="westcentralus",
    nat_rules=[{
        "externalMappings": [azure_native.network.VpnNatRuleMappingArgs(
            address_space="192.168.0.0/26",
        )],
        "internalMappings": [azure_native.network.VpnNatRuleMappingArgs(
            address_space="0.0.0.0/26",
        )],
        "ipConfigurationId": "",
        "mode": "EgressSnat",
        "name": "nat03",
        "type": "Static",
    }],
    resource_group_name="rg1",
    tags={
        "key1": "value1",
    },
    virtual_hub=azure_native.network.SubResourceArgs(
        id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1",
    ))

```

```yaml
resources:
  vpnGateway:
    type: azure-native:network:VpnGateway
    properties:
      bgpSettings:
        asn: 65515
        bgpPeeringAddresses:
          - customBgpIpAddresses:
              - 169.254.21.5
            ipconfigurationId: Instance0
          - customBgpIpAddresses:
              - 169.254.21.10
            ipconfigurationId: Instance1
        peerWeight: 0
      connections:
        - name: vpnConnection1
          remoteVpnSite:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnSites/vpnSite1
          vpnLinkConnections:
            - connectionBandwidth: 200
              egressNatRules:
                - id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnGateways/gateway1/natRules/nat03
              name: Connection-Link1
              sharedKey: key
              vpnConnectionProtocolType: IKEv2
              vpnSiteLink:
                id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnSites/vpnSite1/vpnSiteLinks/siteLink1
      enableBgpRouteTranslationForNat: false
      gatewayName: gateway1
      isRoutingPreferenceInternet: false
      location: westcentralus
      natRules:
        - externalMappings:
            - addressSpace: 192.168.0.0/26
          internalMappings:
            - addressSpace: 0.0.0.0/26
          ipConfigurationId:
          mode: EgressSnat
          name: nat03
          type: Static
      resourceGroupName: rg1
      tags:
        key1: value1
      virtualHub:
        id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:VpnGateway gateway1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnGateways/gateway1 
```
