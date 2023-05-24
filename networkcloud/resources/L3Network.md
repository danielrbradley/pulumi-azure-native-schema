
API Version: 2022-12-12-preview.
Previous API Version: 2022-12-12-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update L3 network
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var l3Network = new AzureNative.NetworkCloud.L3Network("l3Network", new()
    {
        ExtendedLocation = new AzureNative.NetworkCloud.Inputs.ExtendedLocationArgs
        {
            Name = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName",
            Type = "CustomLocation",
        },
        HybridAksIpamEnabled = "True",
        HybridAksPluginType = "DPDK",
        InterfaceName = "eth0",
        IpAllocationType = "DualStack",
        Ipv4ConnectedPrefix = "198.51.100.0/24",
        Ipv6ConnectedPrefix = "2001:db8::/64",
        L3IsolationDomainId = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/l3IsolationDomains/l3IsolationDomainName",
        L3NetworkName = "l3NetworkName",
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
		_, err := networkcloud.NewL3Network(ctx, "l3Network", &networkcloud.L3NetworkArgs{
			ExtendedLocation: &networkcloud.ExtendedLocationArgs{
				Name: pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName"),
				Type: pulumi.String("CustomLocation"),
			},
			HybridAksIpamEnabled: pulumi.String("True"),
			HybridAksPluginType:  pulumi.String("DPDK"),
			InterfaceName:        pulumi.String("eth0"),
			IpAllocationType:     pulumi.String("DualStack"),
			Ipv4ConnectedPrefix:  pulumi.String("198.51.100.0/24"),
			Ipv6ConnectedPrefix:  pulumi.String("2001:db8::/64"),
			L3IsolationDomainId:  pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/l3IsolationDomains/l3IsolationDomainName"),
			L3NetworkName:        pulumi.String("l3NetworkName"),
			Location:             pulumi.String("location"),
			ResourceGroupName:    pulumi.String("resourceGroupName"),
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
import com.pulumi.azurenative.networkcloud.L3Network;
import com.pulumi.azurenative.networkcloud.L3NetworkArgs;
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
        var l3Network = new L3Network("l3Network", L3NetworkArgs.builder()        
            .extendedLocation(Map.ofEntries(
                Map.entry("name", "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName"),
                Map.entry("type", "CustomLocation")
            ))
            .hybridAksIpamEnabled("True")
            .hybridAksPluginType("DPDK")
            .interfaceName("eth0")
            .ipAllocationType("DualStack")
            .ipv4ConnectedPrefix("198.51.100.0/24")
            .ipv6ConnectedPrefix("2001:db8::/64")
            .l3IsolationDomainId("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/l3IsolationDomains/l3IsolationDomainName")
            .l3NetworkName("l3NetworkName")
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

const l3Network = new azure_native.networkcloud.L3Network("l3Network", {
    extendedLocation: {
        name: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName",
        type: "CustomLocation",
    },
    hybridAksIpamEnabled: "True",
    hybridAksPluginType: "DPDK",
    interfaceName: "eth0",
    ipAllocationType: "DualStack",
    ipv4ConnectedPrefix: "198.51.100.0/24",
    ipv6ConnectedPrefix: "2001:db8::/64",
    l3IsolationDomainId: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/l3IsolationDomains/l3IsolationDomainName",
    l3NetworkName: "l3NetworkName",
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

l3_network = azure_native.networkcloud.L3Network("l3Network",
    extended_location=azure_native.networkcloud.ExtendedLocationArgs(
        name="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName",
        type="CustomLocation",
    ),
    hybrid_aks_ipam_enabled="True",
    hybrid_aks_plugin_type="DPDK",
    interface_name="eth0",
    ip_allocation_type="DualStack",
    ipv4_connected_prefix="198.51.100.0/24",
    ipv6_connected_prefix="2001:db8::/64",
    l3_isolation_domain_id="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/l3IsolationDomains/l3IsolationDomainName",
    l3_network_name="l3NetworkName",
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
  l3Network:
    type: azure-native:networkcloud:L3Network
    properties:
      extendedLocation:
        name: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName
        type: CustomLocation
      hybridAksIpamEnabled: True
      hybridAksPluginType: DPDK
      interfaceName: eth0
      ipAllocationType: DualStack
      ipv4ConnectedPrefix: 198.51.100.0/24
      ipv6ConnectedPrefix: 2001:db8::/64
      l3IsolationDomainId: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/l3IsolationDomains/l3IsolationDomainName
      l3NetworkName: l3NetworkName
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
$ pulumi import azure-native:networkcloud:L3Network l3NetworkName /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/l3Networks/l3NetworkName 
```
