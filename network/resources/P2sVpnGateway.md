P2SVpnGateway Resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### P2SVpnGatewayPut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var p2sVpnGateway = new AzureNative.Network.P2sVpnGateway("p2sVpnGateway", new()
    {
        CustomDnsServers = new[]
        {
            "1.1.1.1",
            "2.2.2.2",
        },
        GatewayName = "p2sVpnGateway1",
        IsRoutingPreferenceInternet = false,
        Location = "West US",
        P2SConnectionConfigurations = new[]
        {
            new AzureNative.Network.Inputs.P2SConnectionConfigurationArgs
            {
                Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/p2sVpnGateways/p2sVpnGateway1/p2sConnectionConfigurations/P2SConnectionConfig1",
                Name = "P2SConnectionConfig1",
                RoutingConfiguration = new AzureNative.Network.Inputs.RoutingConfigurationArgs
                {
                    AssociatedRouteTable = new AzureNative.Network.Inputs.SubResourceArgs
                    {
                        Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable1",
                    },
                    PropagatedRouteTables = new AzureNative.Network.Inputs.PropagatedRouteTableArgs
                    {
                        Ids = new[]
                        {
                            new AzureNative.Network.Inputs.SubResourceArgs
                            {
                                Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable1",
                            },
                            new AzureNative.Network.Inputs.SubResourceArgs
                            {
                                Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable2",
                            },
                            new AzureNative.Network.Inputs.SubResourceArgs
                            {
                                Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable3",
                            },
                        },
                        Labels = new[]
                        {
                            "label1",
                            "label2",
                        },
                    },
                    VnetRoutes = new AzureNative.Network.Inputs.VnetRouteArgs
                    {
                        StaticRoutes = new[] {},
                    },
                },
                VpnClientAddressPool = new AzureNative.Network.Inputs.AddressSpaceArgs
                {
                    AddressPrefixes = new[]
                    {
                        "101.3.0.0/16",
                    },
                },
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
        VpnGatewayScaleUnit = 1,
        VpnServerConfiguration = new AzureNative.Network.Inputs.SubResourceArgs
        {
            Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnServerConfigurations/vpnServerConfiguration1",
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
		_, err := network.NewP2sVpnGateway(ctx, "p2sVpnGateway", &network.P2sVpnGatewayArgs{
			CustomDnsServers: pulumi.StringArray{
				pulumi.String("1.1.1.1"),
				pulumi.String("2.2.2.2"),
			},
			GatewayName:                 pulumi.String("p2sVpnGateway1"),
			IsRoutingPreferenceInternet: pulumi.Bool(false),
			Location:                    pulumi.String("West US"),
			P2SConnectionConfigurations: []network.P2SConnectionConfigurationArgs{
				{
					Id:   pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/p2sVpnGateways/p2sVpnGateway1/p2sConnectionConfigurations/P2SConnectionConfig1"),
					Name: pulumi.String("P2SConnectionConfig1"),
					RoutingConfiguration: {
						AssociatedRouteTable: {
							Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable1"),
						},
						PropagatedRouteTables: {
							Ids: network.SubResourceArray{
								{
									Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable1"),
								},
								{
									Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable2"),
								},
								{
									Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable3"),
								},
							},
							Labels: pulumi.StringArray{
								pulumi.String("label1"),
								pulumi.String("label2"),
							},
						},
						VnetRoutes: {
							StaticRoutes: network.StaticRouteArray{},
						},
					},
					VpnClientAddressPool: {
						AddressPrefixes: pulumi.StringArray{
							pulumi.String("101.3.0.0/16"),
						},
					},
				},
			},
			ResourceGroupName: pulumi.String("rg1"),
			Tags: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			VirtualHub: &network.SubResourceArgs{
				Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1"),
			},
			VpnGatewayScaleUnit: pulumi.Int(1),
			VpnServerConfiguration: &network.SubResourceArgs{
				Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnServerConfigurations/vpnServerConfiguration1"),
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
import com.pulumi.azurenative.network.P2sVpnGateway;
import com.pulumi.azurenative.network.P2sVpnGatewayArgs;
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
        var p2sVpnGateway = new P2sVpnGateway("p2sVpnGateway", P2sVpnGatewayArgs.builder()        
            .customDnsServers(            
                "1.1.1.1",
                "2.2.2.2")
            .gatewayName("p2sVpnGateway1")
            .isRoutingPreferenceInternet(false)
            .location("West US")
            .p2SConnectionConfigurations(Map.ofEntries(
                Map.entry("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/p2sVpnGateways/p2sVpnGateway1/p2sConnectionConfigurations/P2SConnectionConfig1"),
                Map.entry("name", "P2SConnectionConfig1"),
                Map.entry("routingConfiguration", Map.ofEntries(
                    Map.entry("associatedRouteTable", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable1")),
                    Map.entry("propagatedRouteTables", Map.ofEntries(
                        Map.entry("ids",                         
                            Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable1"),
                            Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable2"),
                            Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable3")),
                        Map.entry("labels",                         
                            "label1",
                            "label2")
                    )),
                    Map.entry("vnetRoutes", Map.of("staticRoutes", ))
                )),
                Map.entry("vpnClientAddressPool", Map.of("addressPrefixes", "101.3.0.0/16"))
            ))
            .resourceGroupName("rg1")
            .tags(Map.of("key1", "value1"))
            .virtualHub(Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1"))
            .vpnGatewayScaleUnit(1)
            .vpnServerConfiguration(Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnServerConfigurations/vpnServerConfiguration1"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const p2sVpnGateway = new azure_native.network.P2sVpnGateway("p2sVpnGateway", {
    customDnsServers: [
        "1.1.1.1",
        "2.2.2.2",
    ],
    gatewayName: "p2sVpnGateway1",
    isRoutingPreferenceInternet: false,
    location: "West US",
    p2SConnectionConfigurations: [{
        id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/p2sVpnGateways/p2sVpnGateway1/p2sConnectionConfigurations/P2SConnectionConfig1",
        name: "P2SConnectionConfig1",
        routingConfiguration: {
            associatedRouteTable: {
                id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable1",
            },
            propagatedRouteTables: {
                ids: [
                    {
                        id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable1",
                    },
                    {
                        id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable2",
                    },
                    {
                        id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable3",
                    },
                ],
                labels: [
                    "label1",
                    "label2",
                ],
            },
            vnetRoutes: {
                staticRoutes: [],
            },
        },
        vpnClientAddressPool: {
            addressPrefixes: ["101.3.0.0/16"],
        },
    }],
    resourceGroupName: "rg1",
    tags: {
        key1: "value1",
    },
    virtualHub: {
        id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1",
    },
    vpnGatewayScaleUnit: 1,
    vpnServerConfiguration: {
        id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnServerConfigurations/vpnServerConfiguration1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

p2s_vpn_gateway = azure_native.network.P2sVpnGateway("p2sVpnGateway",
    custom_dns_servers=[
        "1.1.1.1",
        "2.2.2.2",
    ],
    gateway_name="p2sVpnGateway1",
    is_routing_preference_internet=False,
    location="West US",
    p2_s_connection_configurations=[{
        "id": "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/p2sVpnGateways/p2sVpnGateway1/p2sConnectionConfigurations/P2SConnectionConfig1",
        "name": "P2SConnectionConfig1",
        "routingConfiguration": {
            "associatedRouteTable": azure_native.network.SubResourceArgs(
                id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable1",
            ),
            "propagatedRouteTables": {
                "ids": [
                    azure_native.network.SubResourceArgs(
                        id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable1",
                    ),
                    azure_native.network.SubResourceArgs(
                        id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable2",
                    ),
                    azure_native.network.SubResourceArgs(
                        id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable3",
                    ),
                ],
                "labels": [
                    "label1",
                    "label2",
                ],
            },
            "vnetRoutes": {
                "staticRoutes": [],
            },
        },
        "vpnClientAddressPool": azure_native.network.AddressSpaceArgs(
            address_prefixes=["101.3.0.0/16"],
        ),
    }],
    resource_group_name="rg1",
    tags={
        "key1": "value1",
    },
    virtual_hub=azure_native.network.SubResourceArgs(
        id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1",
    ),
    vpn_gateway_scale_unit=1,
    vpn_server_configuration=azure_native.network.SubResourceArgs(
        id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnServerConfigurations/vpnServerConfiguration1",
    ))

```

```yaml
resources:
  p2sVpnGateway:
    type: azure-native:network:P2sVpnGateway
    properties:
      customDnsServers:
        - 1.1.1.1
        - 2.2.2.2
      gatewayName: p2sVpnGateway1
      isRoutingPreferenceInternet: false
      location: West US
      p2SConnectionConfigurations:
        - id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/p2sVpnGateways/p2sVpnGateway1/p2sConnectionConfigurations/P2SConnectionConfig1
          name: P2SConnectionConfig1
          routingConfiguration:
            associatedRouteTable:
              id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable1
            propagatedRouteTables:
              ids:
                - id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable1
                - id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable2
                - id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable3
              labels:
                - label1
                - label2
            vnetRoutes:
              staticRoutes: []
          vpnClientAddressPool:
            addressPrefixes:
              - 101.3.0.0/16
      resourceGroupName: rg1
      tags:
        key1: value1
      virtualHub:
        id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1
      vpnGatewayScaleUnit: 1
      vpnServerConfiguration:
        id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnServerConfigurations/vpnServerConfiguration1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:P2sVpnGateway p2sVpnGateway1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/P2SvpnGateways/p2sVpnGateway1 
```
