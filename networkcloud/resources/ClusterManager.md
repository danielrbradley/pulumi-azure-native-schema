
API Version: 2022-12-12-preview.
Previous API Version: 2022-12-12-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update cluster manager
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var clusterManager = new AzureNative.NetworkCloud.ClusterManager("clusterManager", new()
    {
        AnalyticsWorkspaceId = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/microsoft.operationalInsights/workspaces/logAnalyticsWorkspaceName",
        ClusterManagerName = "clusterManagerName",
        FabricControllerId = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkFabricControllers/fabricControllerName",
        Location = "location",
        ManagedResourceGroupConfiguration = new AzureNative.NetworkCloud.Inputs.ManagedResourceGroupConfigurationArgs
        {
            Location = "East US",
            Name = "my-managed-rg",
        },
        ResourceGroupName = "resourceGroupName",
        Tags = 
        {
            { "key1", "myvalue1" },
            { "key2", "myvalue2" },
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
		_, err := networkcloud.NewClusterManager(ctx, "clusterManager", &networkcloud.ClusterManagerArgs{
			AnalyticsWorkspaceId: pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/microsoft.operationalInsights/workspaces/logAnalyticsWorkspaceName"),
			ClusterManagerName:   pulumi.String("clusterManagerName"),
			FabricControllerId:   pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkFabricControllers/fabricControllerName"),
			Location:             pulumi.String("location"),
			ManagedResourceGroupConfiguration: &networkcloud.ManagedResourceGroupConfigurationArgs{
				Location: pulumi.String("East US"),
				Name:     pulumi.String("my-managed-rg"),
			},
			ResourceGroupName: pulumi.String("resourceGroupName"),
			Tags: pulumi.StringMap{
				"key1": pulumi.String("myvalue1"),
				"key2": pulumi.String("myvalue2"),
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
import com.pulumi.azurenative.networkcloud.ClusterManager;
import com.pulumi.azurenative.networkcloud.ClusterManagerArgs;
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
        var clusterManager = new ClusterManager("clusterManager", ClusterManagerArgs.builder()        
            .analyticsWorkspaceId("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/microsoft.operationalInsights/workspaces/logAnalyticsWorkspaceName")
            .clusterManagerName("clusterManagerName")
            .fabricControllerId("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkFabricControllers/fabricControllerName")
            .location("location")
            .managedResourceGroupConfiguration(Map.ofEntries(
                Map.entry("location", "East US"),
                Map.entry("name", "my-managed-rg")
            ))
            .resourceGroupName("resourceGroupName")
            .tags(Map.ofEntries(
                Map.entry("key1", "myvalue1"),
                Map.entry("key2", "myvalue2")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const clusterManager = new azure_native.networkcloud.ClusterManager("clusterManager", {
    analyticsWorkspaceId: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/microsoft.operationalInsights/workspaces/logAnalyticsWorkspaceName",
    clusterManagerName: "clusterManagerName",
    fabricControllerId: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkFabricControllers/fabricControllerName",
    location: "location",
    managedResourceGroupConfiguration: {
        location: "East US",
        name: "my-managed-rg",
    },
    resourceGroupName: "resourceGroupName",
    tags: {
        key1: "myvalue1",
        key2: "myvalue2",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cluster_manager = azure_native.networkcloud.ClusterManager("clusterManager",
    analytics_workspace_id="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/microsoft.operationalInsights/workspaces/logAnalyticsWorkspaceName",
    cluster_manager_name="clusterManagerName",
    fabric_controller_id="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkFabricControllers/fabricControllerName",
    location="location",
    managed_resource_group_configuration=azure_native.networkcloud.ManagedResourceGroupConfigurationArgs(
        location="East US",
        name="my-managed-rg",
    ),
    resource_group_name="resourceGroupName",
    tags={
        "key1": "myvalue1",
        "key2": "myvalue2",
    })

```

```yaml
resources:
  clusterManager:
    type: azure-native:networkcloud:ClusterManager
    properties:
      analyticsWorkspaceId: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/microsoft.operationalInsights/workspaces/logAnalyticsWorkspaceName
      clusterManagerName: clusterManagerName
      fabricControllerId: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkFabricControllers/fabricControllerName
      location: location
      managedResourceGroupConfiguration:
        location: East US
        name: my-managed-rg
      resourceGroupName: resourceGroupName
      tags:
        key1: myvalue1
        key2: myvalue2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:networkcloud:ClusterManager clusterManagerName /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/clusterManagers/clusterManagerName 
```
