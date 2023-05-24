Single Event Hubs Cluster resource in List or Get operations.
API Version: 2021-11-01.
Previous API Version: 2018-01-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ClusterPut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cluster = new AzureNative.EventHub.Cluster("cluster", new()
    {
        ClusterName = "testCluster",
        Location = "South Central US",
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.EventHub.Inputs.ClusterSkuArgs
        {
            Capacity = 1,
            Name = "Dedicated",
        },
        Tags = 
        {
            { "tag1", "value1" },
            { "tag2", "value2" },
        },
    });

});


```

```go
package main

import (
	eventhub "github.com/pulumi/pulumi-azure-native-sdk/eventhub"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := eventhub.NewCluster(ctx, "cluster", &eventhub.ClusterArgs{
			ClusterName:       pulumi.String("testCluster"),
			Location:          pulumi.String("South Central US"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			Sku: &eventhub.ClusterSkuArgs{
				Capacity: pulumi.Int(1),
				Name:     pulumi.String("Dedicated"),
			},
			Tags: pulumi.StringMap{
				"tag1": pulumi.String("value1"),
				"tag2": pulumi.String("value2"),
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
import com.pulumi.azurenative.eventhub.Cluster;
import com.pulumi.azurenative.eventhub.ClusterArgs;
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
            .clusterName("testCluster")
            .location("South Central US")
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 1),
                Map.entry("name", "Dedicated")
            ))
            .tags(Map.ofEntries(
                Map.entry("tag1", "value1"),
                Map.entry("tag2", "value2")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cluster = new azure_native.eventhub.Cluster("cluster", {
    clusterName: "testCluster",
    location: "South Central US",
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 1,
        name: "Dedicated",
    },
    tags: {
        tag1: "value1",
        tag2: "value2",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cluster = azure_native.eventhub.Cluster("cluster",
    cluster_name="testCluster",
    location="South Central US",
    resource_group_name="myResourceGroup",
    sku=azure_native.eventhub.ClusterSkuArgs(
        capacity=1,
        name="Dedicated",
    ),
    tags={
        "tag1": "value1",
        "tag2": "value2",
    })

```

```yaml
resources:
  cluster:
    type: azure-native:eventhub:Cluster
    properties:
      clusterName: testCluster
      location: South Central US
      resourceGroupName: myResourceGroup
      sku:
        capacity: 1
        name: Dedicated
      tags:
        tag1: value1
        tag2: value2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:eventhub:Cluster testCluster /subscriptions/5f750a97-50d9-4e36-8081-c9ee4c0210d4/resourceGroups/myResourceGroup/providers/Microsoft.EventHub/clusters/testCluster 
```
