
API Version: 2022-12-12-preview.
Previous API Version: 2022-12-12-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update trunked network
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var trunkedNetwork = new AzureNative.NetworkCloud.TrunkedNetwork("trunkedNetwork", new()
    {
        ExtendedLocation = new AzureNative.NetworkCloud.Inputs.ExtendedLocationArgs
        {
            Name = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName",
            Type = "CustomLocation",
        },
        HybridAksPluginType = "DPDK",
        InterfaceName = "eth0",
        IsolationDomainIds = new[]
        {
            "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/l2IsolationDomains/l2IsolationDomainName",
            "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/l3IsolationDomains/l3IsolationDomainName",
        },
        Location = "location",
        ResourceGroupName = "resourceGroupName",
        Tags = 
        {
            { "key1", "myvalue1" },
            { "key2", "myvalue2" },
        },
        TrunkedNetworkName = "trunkedNetworkName",
        Vlans = new[]
        {
            12,
            14,
        },
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
		_, err := networkcloud.NewTrunkedNetwork(ctx, "trunkedNetwork", &networkcloud.TrunkedNetworkArgs{
			ExtendedLocation: &networkcloud.ExtendedLocationArgs{
				Name: pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName"),
				Type: pulumi.String("CustomLocation"),
			},
			HybridAksPluginType: pulumi.String("DPDK"),
			InterfaceName:       pulumi.String("eth0"),
			IsolationDomainIds: pulumi.StringArray{
				pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/l2IsolationDomains/l2IsolationDomainName"),
				pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/l3IsolationDomains/l3IsolationDomainName"),
			},
			Location:          pulumi.String("location"),
			ResourceGroupName: pulumi.String("resourceGroupName"),
			Tags: pulumi.StringMap{
				"key1": pulumi.String("myvalue1"),
				"key2": pulumi.String("myvalue2"),
			},
			TrunkedNetworkName: pulumi.String("trunkedNetworkName"),
			Vlans: pulumi.Float64Array{
				pulumi.Float64(12),
				pulumi.Float64(14),
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
import com.pulumi.azurenative.networkcloud.TrunkedNetwork;
import com.pulumi.azurenative.networkcloud.TrunkedNetworkArgs;
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
        var trunkedNetwork = new TrunkedNetwork("trunkedNetwork", TrunkedNetworkArgs.builder()        
            .extendedLocation(Map.ofEntries(
                Map.entry("name", "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName"),
                Map.entry("type", "CustomLocation")
            ))
            .hybridAksPluginType("DPDK")
            .interfaceName("eth0")
            .isolationDomainIds(            
                "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/l2IsolationDomains/l2IsolationDomainName",
                "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/l3IsolationDomains/l3IsolationDomainName")
            .location("location")
            .resourceGroupName("resourceGroupName")
            .tags(Map.ofEntries(
                Map.entry("key1", "myvalue1"),
                Map.entry("key2", "myvalue2")
            ))
            .trunkedNetworkName("trunkedNetworkName")
            .vlans(            
                12,
                14)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const trunkedNetwork = new azure_native.networkcloud.TrunkedNetwork("trunkedNetwork", {
    extendedLocation: {
        name: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName",
        type: "CustomLocation",
    },
    hybridAksPluginType: "DPDK",
    interfaceName: "eth0",
    isolationDomainIds: [
        "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/l2IsolationDomains/l2IsolationDomainName",
        "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/l3IsolationDomains/l3IsolationDomainName",
    ],
    location: "location",
    resourceGroupName: "resourceGroupName",
    tags: {
        key1: "myvalue1",
        key2: "myvalue2",
    },
    trunkedNetworkName: "trunkedNetworkName",
    vlans: [
        12,
        14,
    ],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

trunked_network = azure_native.networkcloud.TrunkedNetwork("trunkedNetwork",
    extended_location=azure_native.networkcloud.ExtendedLocationArgs(
        name="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName",
        type="CustomLocation",
    ),
    hybrid_aks_plugin_type="DPDK",
    interface_name="eth0",
    isolation_domain_ids=[
        "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/l2IsolationDomains/l2IsolationDomainName",
        "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/l3IsolationDomains/l3IsolationDomainName",
    ],
    location="location",
    resource_group_name="resourceGroupName",
    tags={
        "key1": "myvalue1",
        "key2": "myvalue2",
    },
    trunked_network_name="trunkedNetworkName",
    vlans=[
        12,
        14,
    ])

```

```yaml
resources:
  trunkedNetwork:
    type: azure-native:networkcloud:TrunkedNetwork
    properties:
      extendedLocation:
        name: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName
        type: CustomLocation
      hybridAksPluginType: DPDK
      interfaceName: eth0
      isolationDomainIds:
        - /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/l2IsolationDomains/l2IsolationDomainName
        - /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/l3IsolationDomains/l3IsolationDomainName
      location: location
      resourceGroupName: resourceGroupName
      tags:
        key1: myvalue1
        key2: myvalue2
      trunkedNetworkName: trunkedNetworkName
      vlans:
        - 12
        - 14

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:networkcloud:TrunkedNetwork trunkedNetworkName /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/trunkedNetworks/trunkedNetworkName 
```
