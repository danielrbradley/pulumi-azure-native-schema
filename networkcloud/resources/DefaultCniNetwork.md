
API Version: 2022-12-12-preview.
Previous API Version: 2022-12-12-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update default CNI network
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var defaultCniNetwork = new AzureNative.NetworkCloud.DefaultCniNetwork("defaultCniNetwork", new()
    {
        CniBgpConfiguration = new AzureNative.NetworkCloud.Inputs.CniBgpConfigurationArgs
        {
            BgpPeers = new[]
            {
                new AzureNative.NetworkCloud.Inputs.BgpPeerArgs
                {
                    AsNumber = 64497,
                    PeerIp = "203.0.113.254",
                },
            },
            CommunityAdvertisements = new[]
            {
                new AzureNative.NetworkCloud.Inputs.CommunityAdvertisementArgs
                {
                    Communities = new[]
                    {
                        "64512:100",
                    },
                    SubnetPrefix = "192.0.2.0/27",
                },
            },
            ServiceExternalPrefixes = new[]
            {
                "192.0.2.0/28",
            },
            ServiceLoadBalancerPrefixes = new[]
            {
                "192.0.2.16/28",
            },
        },
        DefaultCniNetworkName = "defaultCniNetworkName",
        ExtendedLocation = new AzureNative.NetworkCloud.Inputs.ExtendedLocationArgs
        {
            Name = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName",
            Type = "CustomLocation",
        },
        IpAllocationType = "DualStack",
        Ipv4ConnectedPrefix = "203.0.113.0/24",
        Ipv6ConnectedPrefix = "2001:db8:0:3::/64",
        L3IsolationDomainId = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/l3IsolationDomains/l3IsolationDomainName",
        Location = "location",
        ResourceGroupName = "resourceGroupName",
        Tags = 
        {
            { "key1", "myvalue1" },
            { "key2", "myvalue2" },
        },
        Vlan = 12,
    });

});


```

```go
package main

import (
	networkcloud "github.com/pulumi/pulumi-azure-native-sdk/networkcloud"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := networkcloud.NewDefaultCniNetwork(ctx, "defaultCniNetwork", &networkcloud.DefaultCniNetworkArgs{
			CniBgpConfiguration: networkcloud.CniBgpConfigurationResponse{
				BgpPeers: networkcloud.BgpPeerArray{
					&networkcloud.BgpPeerArgs{
						AsNumber: pulumi.Float64(64497),
						PeerIp:   pulumi.String("203.0.113.254"),
					},
				},
				CommunityAdvertisements: networkcloud.CommunityAdvertisementArray{
					&networkcloud.CommunityAdvertisementArgs{
						Communities: pulumi.StringArray{
							pulumi.String("64512:100"),
						},
						SubnetPrefix: pulumi.String("192.0.2.0/27"),
					},
				},
				ServiceExternalPrefixes: pulumi.StringArray{
					pulumi.String("192.0.2.0/28"),
				},
				ServiceLoadBalancerPrefixes: pulumi.StringArray{
					pulumi.String("192.0.2.16/28"),
				},
			},
			DefaultCniNetworkName: pulumi.String("defaultCniNetworkName"),
			ExtendedLocation: &networkcloud.ExtendedLocationArgs{
				Name: pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName"),
				Type: pulumi.String("CustomLocation"),
			},
			IpAllocationType:    pulumi.String("DualStack"),
			Ipv4ConnectedPrefix: pulumi.String("203.0.113.0/24"),
			Ipv6ConnectedPrefix: pulumi.String("2001:db8:0:3::/64"),
			L3IsolationDomainId: pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/l3IsolationDomains/l3IsolationDomainName"),
			Location:            pulumi.String("location"),
			ResourceGroupName:   pulumi.String("resourceGroupName"),
			Tags: pulumi.StringMap{
				"key1": pulumi.String("myvalue1"),
				"key2": pulumi.String("myvalue2"),
			},
			Vlan: pulumi.Float64(12),
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
import com.pulumi.azurenative.networkcloud.DefaultCniNetwork;
import com.pulumi.azurenative.networkcloud.DefaultCniNetworkArgs;
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
        var defaultCniNetwork = new DefaultCniNetwork("defaultCniNetwork", DefaultCniNetworkArgs.builder()        
            .cniBgpConfiguration(Map.ofEntries(
                Map.entry("bgpPeers", Map.ofEntries(
                    Map.entry("asNumber", 64497),
                    Map.entry("peerIp", "203.0.113.254")
                )),
                Map.entry("communityAdvertisements", Map.ofEntries(
                    Map.entry("communities", "64512:100"),
                    Map.entry("subnetPrefix", "192.0.2.0/27")
                )),
                Map.entry("serviceExternalPrefixes", "192.0.2.0/28"),
                Map.entry("serviceLoadBalancerPrefixes", "192.0.2.16/28")
            ))
            .defaultCniNetworkName("defaultCniNetworkName")
            .extendedLocation(Map.ofEntries(
                Map.entry("name", "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName"),
                Map.entry("type", "CustomLocation")
            ))
            .ipAllocationType("DualStack")
            .ipv4ConnectedPrefix("203.0.113.0/24")
            .ipv6ConnectedPrefix("2001:db8:0:3::/64")
            .l3IsolationDomainId("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/l3IsolationDomains/l3IsolationDomainName")
            .location("location")
            .resourceGroupName("resourceGroupName")
            .tags(Map.ofEntries(
                Map.entry("key1", "myvalue1"),
                Map.entry("key2", "myvalue2")
            ))
            .vlan(12)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const defaultCniNetwork = new azure_native.networkcloud.DefaultCniNetwork("defaultCniNetwork", {
    cniBgpConfiguration: {
        bgpPeers: [{
            asNumber: 64497,
            peerIp: "203.0.113.254",
        }],
        communityAdvertisements: [{
            communities: ["64512:100"],
            subnetPrefix: "192.0.2.0/27",
        }],
        serviceExternalPrefixes: ["192.0.2.0/28"],
        serviceLoadBalancerPrefixes: ["192.0.2.16/28"],
    },
    defaultCniNetworkName: "defaultCniNetworkName",
    extendedLocation: {
        name: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName",
        type: "CustomLocation",
    },
    ipAllocationType: "DualStack",
    ipv4ConnectedPrefix: "203.0.113.0/24",
    ipv6ConnectedPrefix: "2001:db8:0:3::/64",
    l3IsolationDomainId: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/l3IsolationDomains/l3IsolationDomainName",
    location: "location",
    resourceGroupName: "resourceGroupName",
    tags: {
        key1: "myvalue1",
        key2: "myvalue2",
    },
    vlan: 12,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

default_cni_network = azure_native.networkcloud.DefaultCniNetwork("defaultCniNetwork",
    cni_bgp_configuration=azure_native.networkcloud.CniBgpConfigurationResponseArgs(
        bgp_peers=[azure_native.networkcloud.BgpPeerArgs(
            as_number=64497,
            peer_ip="203.0.113.254",
        )],
        community_advertisements=[azure_native.networkcloud.CommunityAdvertisementArgs(
            communities=["64512:100"],
            subnet_prefix="192.0.2.0/27",
        )],
        service_external_prefixes=["192.0.2.0/28"],
        service_load_balancer_prefixes=["192.0.2.16/28"],
    ),
    default_cni_network_name="defaultCniNetworkName",
    extended_location=azure_native.networkcloud.ExtendedLocationArgs(
        name="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName",
        type="CustomLocation",
    ),
    ip_allocation_type="DualStack",
    ipv4_connected_prefix="203.0.113.0/24",
    ipv6_connected_prefix="2001:db8:0:3::/64",
    l3_isolation_domain_id="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/l3IsolationDomains/l3IsolationDomainName",
    location="location",
    resource_group_name="resourceGroupName",
    tags={
        "key1": "myvalue1",
        "key2": "myvalue2",
    },
    vlan=12)

```

```yaml
resources:
  defaultCniNetwork:
    type: azure-native:networkcloud:DefaultCniNetwork
    properties:
      cniBgpConfiguration:
        bgpPeers:
          - asNumber: 64497
            peerIp: 203.0.113.254
        communityAdvertisements:
          - communities:
              - 64512:100
            subnetPrefix: 192.0.2.0/27
        serviceExternalPrefixes:
          - 192.0.2.0/28
        serviceLoadBalancerPrefixes:
          - 192.0.2.16/28
      defaultCniNetworkName: defaultCniNetworkName
      extendedLocation:
        name: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName
        type: CustomLocation
      ipAllocationType: DualStack
      ipv4ConnectedPrefix: 203.0.113.0/24
      ipv6ConnectedPrefix: 2001:db8:0:3::/64
      l3IsolationDomainId: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/l3IsolationDomains/l3IsolationDomainName
      location: location
      resourceGroupName: resourceGroupName
      tags:
        key1: myvalue1
        key2: myvalue2
      vlan: 12

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:networkcloud:DefaultCniNetwork defaultcniNetworkName /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/defaultcniNetworks/defaultcniNetworkName 
```
