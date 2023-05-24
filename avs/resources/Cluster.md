A cluster resource
API Version: 2022-05-01.
Previous API Version: 2020-03-20. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Clusters_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cluster = new AzureNative.AVS.Cluster("cluster", new()
    {
        ClusterName = "cluster1",
        ClusterSize = 3,
        PrivateCloudName = "cloud1",
        ResourceGroupName = "group1",
        Sku = new AzureNative.AVS.Inputs.SkuArgs
        {
            Name = "AV20",
        },
    });

});


```

```go
package main

import (
	avs "github.com/pulumi/pulumi-azure-native-sdk/avs"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := avs.NewCluster(ctx, "cluster", &avs.ClusterArgs{
			ClusterName:       pulumi.String("cluster1"),
			ClusterSize:       pulumi.Int(3),
			PrivateCloudName:  pulumi.String("cloud1"),
			ResourceGroupName: pulumi.String("group1"),
			Sku: &avs.SkuArgs{
				Name: pulumi.String("AV20"),
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
import com.pulumi.azurenative.avs.Cluster;
import com.pulumi.azurenative.avs.ClusterArgs;
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
            .clusterName("cluster1")
            .clusterSize(3)
            .privateCloudName("cloud1")
            .resourceGroupName("group1")
            .sku(Map.of("name", "AV20"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cluster = new azure_native.avs.Cluster("cluster", {
    clusterName: "cluster1",
    clusterSize: 3,
    privateCloudName: "cloud1",
    resourceGroupName: "group1",
    sku: {
        name: "AV20",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cluster = azure_native.avs.Cluster("cluster",
    cluster_name="cluster1",
    cluster_size=3,
    private_cloud_name="cloud1",
    resource_group_name="group1",
    sku=azure_native.avs.SkuArgs(
        name="AV20",
    ))

```

```yaml
resources:
  cluster:
    type: azure-native:avs:Cluster
    properties:
      clusterName: cluster1
      clusterSize: 3
      privateCloudName: cloud1
      resourceGroupName: group1
      sku:
        name: AV20

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:avs:Cluster cluster1 /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/group1/providers/Microsoft.AVS/privateClouds/cloud1/clusters/cluster1 
```
