The top level Log Analytics cluster resource container.
API Version: 2021-06-01.
Previous API Version: 2020-10-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ClustersCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cluster = new AzureNative.OperationalInsights.Cluster("cluster", new()
    {
        ClusterName = "oiautorest6685",
        Location = "australiasoutheast",
        ResourceGroupName = "oiautorest6685",
        Sku = new AzureNative.OperationalInsights.Inputs.ClusterSkuArgs
        {
            Capacity = 1000,
            Name = "CapacityReservation",
        },
        Tags = 
        {
            { "tag1", "val1" },
        },
    });

});


```

```go
package main

import (
	operationalinsights "github.com/pulumi/pulumi-azure-native-sdk/operationalinsights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := operationalinsights.NewCluster(ctx, "cluster", &operationalinsights.ClusterArgs{
			ClusterName:       pulumi.String("oiautorest6685"),
			Location:          pulumi.String("australiasoutheast"),
			ResourceGroupName: pulumi.String("oiautorest6685"),
			Sku: &operationalinsights.ClusterSkuArgs{
				Capacity: pulumi.Float64(1000),
				Name:     pulumi.String("CapacityReservation"),
			},
			Tags: pulumi.StringMap{
				"tag1": pulumi.String("val1"),
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
import com.pulumi.azurenative.operationalinsights.Cluster;
import com.pulumi.azurenative.operationalinsights.ClusterArgs;
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
            .clusterName("oiautorest6685")
            .location("australiasoutheast")
            .resourceGroupName("oiautorest6685")
            .sku(Map.ofEntries(
                Map.entry("capacity", 1000),
                Map.entry("name", "CapacityReservation")
            ))
            .tags(Map.of("tag1", "val1"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cluster = new azure_native.operationalinsights.Cluster("cluster", {
    clusterName: "oiautorest6685",
    location: "australiasoutheast",
    resourceGroupName: "oiautorest6685",
    sku: {
        capacity: 1000,
        name: "CapacityReservation",
    },
    tags: {
        tag1: "val1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cluster = azure_native.operationalinsights.Cluster("cluster",
    cluster_name="oiautorest6685",
    location="australiasoutheast",
    resource_group_name="oiautorest6685",
    sku=azure_native.operationalinsights.ClusterSkuArgs(
        capacity=1000,
        name="CapacityReservation",
    ),
    tags={
        "tag1": "val1",
    })

```

```yaml
resources:
  cluster:
    type: azure-native:operationalinsights:Cluster
    properties:
      clusterName: oiautorest6685
      location: australiasoutheast
      resourceGroupName: oiautorest6685
      sku:
        capacity: 1000
        name: CapacityReservation
      tags:
        tag1: val1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:operationalinsights:Cluster oiautorest6685 /subscriptions/594038b5-1093-476e-a366-482775671c11/resourcegroups/oiautorest6685/providers/microsoft.operationalinsights/clusters/oiautorest6685 
```
