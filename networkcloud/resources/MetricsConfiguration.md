
API Version: 2022-12-12-preview.
Previous API Version: 2022-12-12-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Update metrics configuration of cluster
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var metricsConfiguration = new AzureNative.NetworkCloud.MetricsConfiguration("metricsConfiguration", new()
    {
        ClusterName = "clusterName",
        CollectionInterval = 15,
        EnabledMetrics = new[]
        {
            "metric1",
            "metric2",
        },
        ExtendedLocation = new AzureNative.NetworkCloud.Inputs.ExtendedLocationArgs
        {
            Name = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName",
            Type = "CustomLocation",
        },
        Location = "location",
        MetricsConfigurationName = "default",
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
		_, err := networkcloud.NewMetricsConfiguration(ctx, "metricsConfiguration", &networkcloud.MetricsConfigurationArgs{
			ClusterName:        pulumi.String("clusterName"),
			CollectionInterval: pulumi.Float64(15),
			EnabledMetrics: pulumi.StringArray{
				pulumi.String("metric1"),
				pulumi.String("metric2"),
			},
			ExtendedLocation: &networkcloud.ExtendedLocationArgs{
				Name: pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName"),
				Type: pulumi.String("CustomLocation"),
			},
			Location:                 pulumi.String("location"),
			MetricsConfigurationName: pulumi.String("default"),
			ResourceGroupName:        pulumi.String("resourceGroupName"),
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
import com.pulumi.azurenative.networkcloud.MetricsConfiguration;
import com.pulumi.azurenative.networkcloud.MetricsConfigurationArgs;
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
        var metricsConfiguration = new MetricsConfiguration("metricsConfiguration", MetricsConfigurationArgs.builder()        
            .clusterName("clusterName")
            .collectionInterval(15)
            .enabledMetrics(            
                "metric1",
                "metric2")
            .extendedLocation(Map.ofEntries(
                Map.entry("name", "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName"),
                Map.entry("type", "CustomLocation")
            ))
            .location("location")
            .metricsConfigurationName("default")
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

const metricsConfiguration = new azure_native.networkcloud.MetricsConfiguration("metricsConfiguration", {
    clusterName: "clusterName",
    collectionInterval: 15,
    enabledMetrics: [
        "metric1",
        "metric2",
    ],
    extendedLocation: {
        name: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName",
        type: "CustomLocation",
    },
    location: "location",
    metricsConfigurationName: "default",
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

metrics_configuration = azure_native.networkcloud.MetricsConfiguration("metricsConfiguration",
    cluster_name="clusterName",
    collection_interval=15,
    enabled_metrics=[
        "metric1",
        "metric2",
    ],
    extended_location=azure_native.networkcloud.ExtendedLocationArgs(
        name="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName",
        type="CustomLocation",
    ),
    location="location",
    metrics_configuration_name="default",
    resource_group_name="resourceGroupName",
    tags={
        "key1": "myvalue1",
        "key2": "myvalue2",
    })

```

```yaml
resources:
  metricsConfiguration:
    type: azure-native:networkcloud:MetricsConfiguration
    properties:
      clusterName: clusterName
      collectionInterval: 15
      enabledMetrics:
        - metric1
        - metric2
      extendedLocation:
        name: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName
        type: CustomLocation
      location: location
      metricsConfigurationName: default
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
$ pulumi import azure-native:networkcloud:MetricsConfiguration default /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/clusters/clusterName/metricsConfigurations/default 
```
