A node pool snapshot resource.
API Version: 2023-01-01.
Previous API Version: 2021-08-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create/Update Snapshot
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var snapshot = new AzureNative.ContainerService.Snapshot("snapshot", new()
    {
        CreationData = new AzureNative.ContainerService.Inputs.CreationDataArgs
        {
            SourceResourceId = "/subscriptions/subid1/resourcegroups/rg1/providers/Microsoft.ContainerService/managedClusters/cluster1/agentPools/pool0",
        },
        Location = "westus",
        ResourceGroupName = "rg1",
        ResourceName = "snapshot1",
        Tags = 
        {
            { "key1", "val1" },
            { "key2", "val2" },
        },
    });

});


```

```go
package main

import (
	containerservice "github.com/pulumi/pulumi-azure-native-sdk/containerservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := containerservice.NewSnapshot(ctx, "snapshot", &containerservice.SnapshotArgs{
			CreationData: &containerservice.CreationDataArgs{
				SourceResourceId: pulumi.String("/subscriptions/subid1/resourcegroups/rg1/providers/Microsoft.ContainerService/managedClusters/cluster1/agentPools/pool0"),
			},
			Location:          pulumi.String("westus"),
			ResourceGroupName: pulumi.String("rg1"),
			ResourceName:      pulumi.String("snapshot1"),
			Tags: pulumi.StringMap{
				"key1": pulumi.String("val1"),
				"key2": pulumi.String("val2"),
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
import com.pulumi.azurenative.containerservice.Snapshot;
import com.pulumi.azurenative.containerservice.SnapshotArgs;
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
        var snapshot = new Snapshot("snapshot", SnapshotArgs.builder()        
            .creationData(Map.of("sourceResourceId", "/subscriptions/subid1/resourcegroups/rg1/providers/Microsoft.ContainerService/managedClusters/cluster1/agentPools/pool0"))
            .location("westus")
            .resourceGroupName("rg1")
            .resourceName("snapshot1")
            .tags(Map.ofEntries(
                Map.entry("key1", "val1"),
                Map.entry("key2", "val2")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const snapshot = new azure_native.containerservice.Snapshot("snapshot", {
    creationData: {
        sourceResourceId: "/subscriptions/subid1/resourcegroups/rg1/providers/Microsoft.ContainerService/managedClusters/cluster1/agentPools/pool0",
    },
    location: "westus",
    resourceGroupName: "rg1",
    resourceName: "snapshot1",
    tags: {
        key1: "val1",
        key2: "val2",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

snapshot = azure_native.containerservice.Snapshot("snapshot",
    creation_data=azure_native.containerservice.CreationDataArgs(
        source_resource_id="/subscriptions/subid1/resourcegroups/rg1/providers/Microsoft.ContainerService/managedClusters/cluster1/agentPools/pool0",
    ),
    location="westus",
    resource_group_name="rg1",
    resource_name_="snapshot1",
    tags={
        "key1": "val1",
        "key2": "val2",
    })

```

```yaml
resources:
  snapshot:
    type: azure-native:containerservice:Snapshot
    properties:
      creationData:
        sourceResourceId: /subscriptions/subid1/resourcegroups/rg1/providers/Microsoft.ContainerService/managedClusters/cluster1/agentPools/pool0
      location: westus
      resourceGroupName: rg1
      resourceName: snapshot1
      tags:
        key1: val1
        key2: val2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:containerservice:Snapshot snapshot1 /subscriptions/subid1/resourcegroups/rg1/providers/Microsoft.ContainerService/snapshots/snapshot1 
```
