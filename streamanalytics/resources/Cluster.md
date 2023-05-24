A Stream Analytics Cluster object
API Version: 2020-03-01.
Previous API Version: 2020-03-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a new cluster
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cluster = new AzureNative.StreamAnalytics.Cluster("cluster", new()
    {
        ClusterName = "An Example Cluster",
        Location = "North US",
        ResourceGroupName = "sjrg",
        Sku = new AzureNative.StreamAnalytics.Inputs.ClusterSkuArgs
        {
            Capacity = 48,
            Name = "Default",
        },
        Tags = 
        {
            { "key", "value" },
        },
    });

});


```

```go
package main

import (
	streamanalytics "github.com/pulumi/pulumi-azure-native-sdk/streamanalytics"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := streamanalytics.NewCluster(ctx, "cluster", &streamanalytics.ClusterArgs{
			ClusterName:       pulumi.String("An Example Cluster"),
			Location:          pulumi.String("North US"),
			ResourceGroupName: pulumi.String("sjrg"),
			Sku: &streamanalytics.ClusterSkuArgs{
				Capacity: pulumi.Int(48),
				Name:     pulumi.String("Default"),
			},
			Tags: pulumi.StringMap{
				"key": pulumi.String("value"),
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
import com.pulumi.azurenative.streamanalytics.Cluster;
import com.pulumi.azurenative.streamanalytics.ClusterArgs;
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
        var cluster = new Cluster("cluster", ClusterArgs.builder()        
            .clusterName("An Example Cluster")
            .location("North US")
            .resourceGroupName("sjrg")
            .sku(Map.ofEntries(
                Map.entry("capacity", 48),
                Map.entry("name", "Default")
            ))
            .tags(Map.of("key", "value"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cluster = new azure_native.streamanalytics.Cluster("cluster", {
    clusterName: "An Example Cluster",
    location: "North US",
    resourceGroupName: "sjrg",
    sku: {
        capacity: 48,
        name: "Default",
    },
    tags: {
        key: "value",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cluster = azure_native.streamanalytics.Cluster("cluster",
    cluster_name="An Example Cluster",
    location="North US",
    resource_group_name="sjrg",
    sku=azure_native.streamanalytics.ClusterSkuArgs(
        capacity=48,
        name="Default",
    ),
    tags={
        "key": "value",
    })

```

```yaml
resources:
  cluster:
    type: azure-native:streamanalytics:Cluster
    properties:
      clusterName: An Example Cluster
      location: North US
      resourceGroupName: sjrg
      sku:
        capacity: 48
        name: Default
      tags:
        key: value

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:streamanalytics:Cluster An Example Cluster /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/sjrg/providers/Microsoft.StreamAnalytics/clusters/AnExampleStreamingCluster 
```
