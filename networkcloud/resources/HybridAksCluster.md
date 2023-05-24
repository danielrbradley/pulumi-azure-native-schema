The details are specific to the Network Cloud use of the Hybrid AKS cluster.
API Version: 2022-12-12-preview.
Previous API Version: 2022-12-12-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update Hybrid AKS provisioned cluster data
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var hybridAksCluster = new AzureNative.NetworkCloud.HybridAksCluster("hybridAksCluster", new()
    {
        AssociatedNetworkIds = new[]
        {
            "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/l3Networks/l3NetworkName",
        },
        ControlPlaneCount = 4,
        ExtendedLocation = new AzureNative.NetworkCloud.Inputs.ExtendedLocationArgs
        {
            Name = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName",
            Type = "CustomLocation",
        },
        HybridAksClusterName = "hybridAksClusterName",
        HybridAksProvisionedClusterId = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.HybridContainerService/provisionedClusters/hybridAksClusterName",
        Location = "location",
        ResourceGroupName = "resourceGroupName",
        Tags = 
        {
            { "key1", "myvalue1" },
            { "key2", "myvalue2" },
        },
        WorkerCount = 8,
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
		_, err := networkcloud.NewHybridAksCluster(ctx, "hybridAksCluster", &networkcloud.HybridAksClusterArgs{
			AssociatedNetworkIds: pulumi.StringArray{
				pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/l3Networks/l3NetworkName"),
			},
			ControlPlaneCount: pulumi.Float64(4),
			ExtendedLocation: &networkcloud.ExtendedLocationArgs{
				Name: pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName"),
				Type: pulumi.String("CustomLocation"),
			},
			HybridAksClusterName:          pulumi.String("hybridAksClusterName"),
			HybridAksProvisionedClusterId: pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.HybridContainerService/provisionedClusters/hybridAksClusterName"),
			Location:                      pulumi.String("location"),
			ResourceGroupName:             pulumi.String("resourceGroupName"),
			Tags: pulumi.StringMap{
				"key1": pulumi.String("myvalue1"),
				"key2": pulumi.String("myvalue2"),
			},
			WorkerCount: pulumi.Float64(8),
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
import com.pulumi.azurenative.networkcloud.HybridAksCluster;
import com.pulumi.azurenative.networkcloud.HybridAksClusterArgs;
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
        var hybridAksCluster = new HybridAksCluster("hybridAksCluster", HybridAksClusterArgs.builder()        
            .associatedNetworkIds("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/l3Networks/l3NetworkName")
            .controlPlaneCount(4)
            .extendedLocation(Map.ofEntries(
                Map.entry("name", "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName"),
                Map.entry("type", "CustomLocation")
            ))
            .hybridAksClusterName("hybridAksClusterName")
            .hybridAksProvisionedClusterId("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.HybridContainerService/provisionedClusters/hybridAksClusterName")
            .location("location")
            .resourceGroupName("resourceGroupName")
            .tags(Map.ofEntries(
                Map.entry("key1", "myvalue1"),
                Map.entry("key2", "myvalue2")
            ))
            .workerCount(8)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const hybridAksCluster = new azure_native.networkcloud.HybridAksCluster("hybridAksCluster", {
    associatedNetworkIds: ["/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/l3Networks/l3NetworkName"],
    controlPlaneCount: 4,
    extendedLocation: {
        name: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName",
        type: "CustomLocation",
    },
    hybridAksClusterName: "hybridAksClusterName",
    hybridAksProvisionedClusterId: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.HybridContainerService/provisionedClusters/hybridAksClusterName",
    location: "location",
    resourceGroupName: "resourceGroupName",
    tags: {
        key1: "myvalue1",
        key2: "myvalue2",
    },
    workerCount: 8,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

hybrid_aks_cluster = azure_native.networkcloud.HybridAksCluster("hybridAksCluster",
    associated_network_ids=["/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/l3Networks/l3NetworkName"],
    control_plane_count=4,
    extended_location=azure_native.networkcloud.ExtendedLocationArgs(
        name="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName",
        type="CustomLocation",
    ),
    hybrid_aks_cluster_name="hybridAksClusterName",
    hybrid_aks_provisioned_cluster_id="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.HybridContainerService/provisionedClusters/hybridAksClusterName",
    location="location",
    resource_group_name="resourceGroupName",
    tags={
        "key1": "myvalue1",
        "key2": "myvalue2",
    },
    worker_count=8)

```

```yaml
resources:
  hybridAksCluster:
    type: azure-native:networkcloud:HybridAksCluster
    properties:
      associatedNetworkIds:
        - /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/l3Networks/l3NetworkName
      controlPlaneCount: 4
      extendedLocation:
        name: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName
        type: CustomLocation
      hybridAksClusterName: hybridAksClusterName
      hybridAksProvisionedClusterId: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.HybridContainerService/provisionedClusters/hybridAksClusterName
      location: location
      resourceGroupName: resourceGroupName
      tags:
        key1: myvalue1
        key2: myvalue2
      workerCount: 8

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:networkcloud:HybridAksCluster HybridAksClusterName /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/hybridAksClusters/hybridAksClusterName 
```
