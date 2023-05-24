Defines the InternalNetwork item.
API Version: 2023-02-01-preview.
Previous API Version: 2023-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### InternalNetworks_Create_MaximumSet_Gen
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var internalNetwork = new AzureNative.ManagedNetworkFabric.InternalNetwork("internalNetwork", new()
    {
        BgpConfiguration = new AzureNative.ManagedNetworkFabric.Inputs.InternalNetworkPatchablePropertiesBgpConfigurationArgs
        {
            AllowAS = 1,
            AllowASOverride = "Enable",
            DefaultRouteOriginate = "True",
            Ipv4ListenRangePrefixes = new[]
            {
                "10.1.0.0/25",
            },
            Ipv4NeighborAddress = new[]
            {
                new AzureNative.ManagedNetworkFabric.Inputs.InternalNetworkPatchablePropertiesIpv4NeighborAddressArgs
                {
                    Address = "10.1.0.0",
                },
            },
            Ipv6ListenRangePrefixes = new[]
            {
                "2fff::/66",
            },
            Ipv6NeighborAddress = new[]
            {
                new AzureNative.ManagedNetworkFabric.Inputs.InternalNetworkPatchablePropertiesIpv6NeighborAddressArgs
                {
                    Address = "2fff::",
                },
            },
            PeerASN = 6,
        },
        ConnectedIPv4Subnets = new[]
        {
            new AzureNative.ManagedNetworkFabric.Inputs.InternalNetworkPatchablePropertiesConnectedIPv4SubnetsArgs
            {
                Prefix = "10.0.0.0/24",
            },
        },
        ConnectedIPv6Subnets = new[]
        {
            new AzureNative.ManagedNetworkFabric.Inputs.InternalNetworkPatchablePropertiesConnectedIPv6SubnetsArgs
            {
                Prefix = "3FFE:FFFF:0:CD30::a0/29",
            },
        },
        ExportRoutePolicyId = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName2",
        ImportRoutePolicyId = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName1",
        InternalNetworkName = "example-internalnetwork",
        L3IsolationDomainName = "example-l3domain",
        Mtu = 1500,
        ResourceGroupName = "resourceGroupName",
        StaticRouteConfiguration = new AzureNative.ManagedNetworkFabric.Inputs.InternalNetworkPatchablePropertiesStaticRouteConfigurationArgs
        {
            Ipv4Routes = new[]
            {
                new AzureNative.ManagedNetworkFabric.Inputs.InternalNetworkPatchablePropertiesIpv4RoutesArgs
                {
                    NextHop = new[]
                    {
                        "10.0.0.1",
                    },
                    Prefix = "10.1.0.0/24",
                },
            },
            Ipv6Routes = new[]
            {
                new AzureNative.ManagedNetworkFabric.Inputs.InternalNetworkPatchablePropertiesIpv6RoutesArgs
                {
                    NextHop = new[]
                    {
                        "2ffe::1",
                    },
                    Prefix = "2fff::/64",
                },
            },
        },
        VlanId = 501,
    });

});


```

```go
package main

import (
	managednetworkfabric "github.com/pulumi/pulumi-azure-native-sdk/managednetworkfabric"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := managednetworkfabric.NewInternalNetwork(ctx, "internalNetwork", &managednetworkfabric.InternalNetworkArgs{
			BgpConfiguration: managednetworkfabric.InternalNetworkPatchablePropertiesResponseBgpConfiguration{
				AllowAS:               pulumi.Int(1),
				AllowASOverride:       pulumi.String("Enable"),
				DefaultRouteOriginate: pulumi.String("True"),
				Ipv4ListenRangePrefixes: pulumi.StringArray{
					pulumi.String("10.1.0.0/25"),
				},
				Ipv4NeighborAddress: managednetworkfabric.InternalNetworkPatchablePropertiesIpv4NeighborAddressArray{
					&managednetworkfabric.InternalNetworkPatchablePropertiesIpv4NeighborAddressArgs{
						Address: pulumi.String("10.1.0.0"),
					},
				},
				Ipv6ListenRangePrefixes: pulumi.StringArray{
					pulumi.String("2fff::/66"),
				},
				Ipv6NeighborAddress: managednetworkfabric.InternalNetworkPatchablePropertiesIpv6NeighborAddressArray{
					&managednetworkfabric.InternalNetworkPatchablePropertiesIpv6NeighborAddressArgs{
						Address: pulumi.String("2fff::"),
					},
				},
				PeerASN: pulumi.Int(6),
			},
			ConnectedIPv4Subnets: []managednetworkfabric.InternalNetworkPatchablePropertiesConnectedIPv4SubnetsArgs{
				{
					Prefix: pulumi.String("10.0.0.0/24"),
				},
			},
			ConnectedIPv6Subnets: []managednetworkfabric.InternalNetworkPatchablePropertiesConnectedIPv6SubnetsArgs{
				{
					Prefix: pulumi.String("3FFE:FFFF:0:CD30::a0/29"),
				},
			},
			ExportRoutePolicyId:   pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName2"),
			ImportRoutePolicyId:   pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName1"),
			InternalNetworkName:   pulumi.String("example-internalnetwork"),
			L3IsolationDomainName: pulumi.String("example-l3domain"),
			Mtu:                   pulumi.Int(1500),
			ResourceGroupName:     pulumi.String("resourceGroupName"),
			StaticRouteConfiguration: managednetworkfabric.InternalNetworkPatchablePropertiesResponseStaticRouteConfiguration{
				Ipv4Routes: managednetworkfabric.InternalNetworkPatchablePropertiesIpv4RoutesArray{
					&managednetworkfabric.InternalNetworkPatchablePropertiesIpv4RoutesArgs{
						NextHop: pulumi.StringArray{
							pulumi.String("10.0.0.1"),
						},
						Prefix: pulumi.String("10.1.0.0/24"),
					},
				},
				Ipv6Routes: managednetworkfabric.InternalNetworkPatchablePropertiesIpv6RoutesArray{
					&managednetworkfabric.InternalNetworkPatchablePropertiesIpv6RoutesArgs{
						NextHop: pulumi.StringArray{
							pulumi.String("2ffe::1"),
						},
						Prefix: pulumi.String("2fff::/64"),
					},
				},
			},
			VlanId: pulumi.Int(501),
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
import com.pulumi.azurenative.managednetworkfabric.InternalNetwork;
import com.pulumi.azurenative.managednetworkfabric.InternalNetworkArgs;
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
        var internalNetwork = new InternalNetwork("internalNetwork", InternalNetworkArgs.builder()        
            .bgpConfiguration(Map.ofEntries(
                Map.entry("allowAS", 1),
                Map.entry("allowASOverride", "Enable"),
                Map.entry("defaultRouteOriginate", "True"),
                Map.entry("ipv4ListenRangePrefixes", "10.1.0.0/25"),
                Map.entry("ipv4NeighborAddress", Map.of("address", "10.1.0.0")),
                Map.entry("ipv6ListenRangePrefixes", "2fff::/66"),
                Map.entry("ipv6NeighborAddress", Map.of("address", "2fff::")),
                Map.entry("peerASN", 6)
            ))
            .connectedIPv4Subnets(Map.of("prefix", "10.0.0.0/24"))
            .connectedIPv6Subnets(Map.of("prefix", "3FFE:FFFF:0:CD30::a0/29"))
            .exportRoutePolicyId("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName2")
            .importRoutePolicyId("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName1")
            .internalNetworkName("example-internalnetwork")
            .l3IsolationDomainName("example-l3domain")
            .mtu(1500)
            .resourceGroupName("resourceGroupName")
            .staticRouteConfiguration(Map.ofEntries(
                Map.entry("ipv4Routes", Map.ofEntries(
                    Map.entry("nextHop", "10.0.0.1"),
                    Map.entry("prefix", "10.1.0.0/24")
                )),
                Map.entry("ipv6Routes", Map.ofEntries(
                    Map.entry("nextHop", "2ffe::1"),
                    Map.entry("prefix", "2fff::/64")
                ))
            ))
            .vlanId(501)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const internalNetwork = new azure_native.managednetworkfabric.InternalNetwork("internalNetwork", {
    bgpConfiguration: {
        allowAS: 1,
        allowASOverride: "Enable",
        defaultRouteOriginate: "True",
        ipv4ListenRangePrefixes: ["10.1.0.0/25"],
        ipv4NeighborAddress: [{
            address: "10.1.0.0",
        }],
        ipv6ListenRangePrefixes: ["2fff::/66"],
        ipv6NeighborAddress: [{
            address: "2fff::",
        }],
        peerASN: 6,
    },
    connectedIPv4Subnets: [{
        prefix: "10.0.0.0/24",
    }],
    connectedIPv6Subnets: [{
        prefix: "3FFE:FFFF:0:CD30::a0/29",
    }],
    exportRoutePolicyId: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName2",
    importRoutePolicyId: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName1",
    internalNetworkName: "example-internalnetwork",
    l3IsolationDomainName: "example-l3domain",
    mtu: 1500,
    resourceGroupName: "resourceGroupName",
    staticRouteConfiguration: {
        ipv4Routes: [{
            nextHop: ["10.0.0.1"],
            prefix: "10.1.0.0/24",
        }],
        ipv6Routes: [{
            nextHop: ["2ffe::1"],
            prefix: "2fff::/64",
        }],
    },
    vlanId: 501,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

internal_network = azure_native.managednetworkfabric.InternalNetwork("internalNetwork",
    bgp_configuration=azure_native.managednetworkfabric.InternalNetworkPatchablePropertiesResponseBgpConfigurationArgs(
        allow_as=1,
        allow_as_override="Enable",
        default_route_originate="True",
        ipv4_listen_range_prefixes=["10.1.0.0/25"],
        ipv4_neighbor_address=[azure_native.managednetworkfabric.InternalNetworkPatchablePropertiesIpv4NeighborAddressArgs(
            address="10.1.0.0",
        )],
        ipv6_listen_range_prefixes=["2fff::/66"],
        ipv6_neighbor_address=[azure_native.managednetworkfabric.InternalNetworkPatchablePropertiesIpv6NeighborAddressArgs(
            address="2fff::",
        )],
        peer_asn=6,
    ),
    connected_i_pv4_subnets=[azure_native.managednetworkfabric.InternalNetworkPatchablePropertiesConnectedIPv4SubnetsArgs(
        prefix="10.0.0.0/24",
    )],
    connected_i_pv6_subnets=[azure_native.managednetworkfabric.InternalNetworkPatchablePropertiesConnectedIPv6SubnetsArgs(
        prefix="3FFE:FFFF:0:CD30::a0/29",
    )],
    export_route_policy_id="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName2",
    import_route_policy_id="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName1",
    internal_network_name="example-internalnetwork",
    l3_isolation_domain_name="example-l3domain",
    mtu=1500,
    resource_group_name="resourceGroupName",
    static_route_configuration=azure_native.managednetworkfabric.InternalNetworkPatchablePropertiesResponseStaticRouteConfigurationArgs(
        ipv4_routes=[azure_native.managednetworkfabric.InternalNetworkPatchablePropertiesIpv4RoutesArgs(
            next_hop=["10.0.0.1"],
            prefix="10.1.0.0/24",
        )],
        ipv6_routes=[azure_native.managednetworkfabric.InternalNetworkPatchablePropertiesIpv6RoutesArgs(
            next_hop=["2ffe::1"],
            prefix="2fff::/64",
        )],
    ),
    vlan_id=501)

```

```yaml
resources:
  internalNetwork:
    type: azure-native:managednetworkfabric:InternalNetwork
    properties:
      bgpConfiguration:
        allowAS: 1
        allowASOverride: Enable
        defaultRouteOriginate: True
        ipv4ListenRangePrefixes:
          - 10.1.0.0/25
        ipv4NeighborAddress:
          - address: 10.1.0.0
        ipv6ListenRangePrefixes:
          - 2fff::/66
        ipv6NeighborAddress:
          - address: '2fff::'
        peerASN: 6
      connectedIPv4Subnets:
        - prefix: 10.0.0.0/24
      connectedIPv6Subnets:
        - prefix: 3FFE:FFFF:0:CD30::a0/29
      exportRoutePolicyId: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName2
      importRoutePolicyId: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/routePolicies/routePolicyName1
      internalNetworkName: example-internalnetwork
      l3IsolationDomainName: example-l3domain
      mtu: 1500
      resourceGroupName: resourceGroupName
      staticRouteConfiguration:
        ipv4Routes:
          - nextHop:
              - 10.0.0.1
            prefix: 10.1.0.0/24
        ipv6Routes:
          - nextHop:
              - 2ffe::1
            prefix: 2fff::/64
      vlanId: 501

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:managednetworkfabric:InternalNetwork example-externalnetwork /subscriptions/xxxxxx/resourceGroups/resourcegroupname/providers/Microsoft.ManagedNetworkFabric/example-l3domain/externalNetworks/example-externalnetwork 
```
