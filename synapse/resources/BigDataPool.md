A Big Data pool
API Version: 2021-06-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a Big Data pool
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var bigDataPool = new AzureNative.Synapse.BigDataPool("bigDataPool", new()
    {
        AutoPause = new AzureNative.Synapse.Inputs.AutoPausePropertiesArgs
        {
            DelayInMinutes = 15,
            Enabled = true,
        },
        AutoScale = new AzureNative.Synapse.Inputs.AutoScalePropertiesArgs
        {
            Enabled = true,
            MaxNodeCount = 50,
            MinNodeCount = 3,
        },
        BigDataPoolName = "ExamplePool",
        DefaultSparkLogFolder = "/logs",
        IsAutotuneEnabled = false,
        LibraryRequirements = new AzureNative.Synapse.Inputs.LibraryRequirementsArgs
        {
            Content = "",
            Filename = "requirements.txt",
        },
        Location = "West US 2",
        NodeCount = 4,
        NodeSize = "Medium",
        NodeSizeFamily = "MemoryOptimized",
        ResourceGroupName = "ExampleResourceGroup",
        SparkEventsFolder = "/events",
        SparkVersion = "3.3",
        Tags = 
        {
            { "key", "value" },
        },
        WorkspaceName = "ExampleWorkspace",
    });

});


```

```go
package main

import (
	synapse "github.com/pulumi/pulumi-azure-native-sdk/synapse"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := synapse.NewBigDataPool(ctx, "bigDataPool", &synapse.BigDataPoolArgs{
			AutoPause: &synapse.AutoPausePropertiesArgs{
				DelayInMinutes: pulumi.Int(15),
				Enabled:        pulumi.Bool(true),
			},
			AutoScale: &synapse.AutoScalePropertiesArgs{
				Enabled:      pulumi.Bool(true),
				MaxNodeCount: pulumi.Int(50),
				MinNodeCount: pulumi.Int(3),
			},
			BigDataPoolName:       pulumi.String("ExamplePool"),
			DefaultSparkLogFolder: pulumi.String("/logs"),
			IsAutotuneEnabled:     pulumi.Bool(false),
			LibraryRequirements: &synapse.LibraryRequirementsArgs{
				Content:  pulumi.String(""),
				Filename: pulumi.String("requirements.txt"),
			},
			Location:          pulumi.String("West US 2"),
			NodeCount:         pulumi.Int(4),
			NodeSize:          pulumi.String("Medium"),
			NodeSizeFamily:    pulumi.String("MemoryOptimized"),
			ResourceGroupName: pulumi.String("ExampleResourceGroup"),
			SparkEventsFolder: pulumi.String("/events"),
			SparkVersion:      pulumi.String("3.3"),
			Tags: pulumi.StringMap{
				"key": pulumi.String("value"),
			},
			WorkspaceName: pulumi.String("ExampleWorkspace"),
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
import com.pulumi.azurenative.synapse.BigDataPool;
import com.pulumi.azurenative.synapse.BigDataPoolArgs;
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
        var bigDataPool = new BigDataPool("bigDataPool", BigDataPoolArgs.builder()        
            .autoPause(Map.ofEntries(
                Map.entry("delayInMinutes", 15),
                Map.entry("enabled", true)
            ))
            .autoScale(Map.ofEntries(
                Map.entry("enabled", true),
                Map.entry("maxNodeCount", 50),
                Map.entry("minNodeCount", 3)
            ))
            .bigDataPoolName("ExamplePool")
            .defaultSparkLogFolder("/logs")
            .isAutotuneEnabled(false)
            .libraryRequirements(Map.ofEntries(
                Map.entry("content", ""),
                Map.entry("filename", "requirements.txt")
            ))
            .location("West US 2")
            .nodeCount(4)
            .nodeSize("Medium")
            .nodeSizeFamily("MemoryOptimized")
            .resourceGroupName("ExampleResourceGroup")
            .sparkEventsFolder("/events")
            .sparkVersion("3.3")
            .tags(Map.of("key", "value"))
            .workspaceName("ExampleWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const bigDataPool = new azure_native.synapse.BigDataPool("bigDataPool", {
    autoPause: {
        delayInMinutes: 15,
        enabled: true,
    },
    autoScale: {
        enabled: true,
        maxNodeCount: 50,
        minNodeCount: 3,
    },
    bigDataPoolName: "ExamplePool",
    defaultSparkLogFolder: "/logs",
    isAutotuneEnabled: false,
    libraryRequirements: {
        content: "",
        filename: "requirements.txt",
    },
    location: "West US 2",
    nodeCount: 4,
    nodeSize: "Medium",
    nodeSizeFamily: "MemoryOptimized",
    resourceGroupName: "ExampleResourceGroup",
    sparkEventsFolder: "/events",
    sparkVersion: "3.3",
    tags: {
        key: "value",
    },
    workspaceName: "ExampleWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

big_data_pool = azure_native.synapse.BigDataPool("bigDataPool",
    auto_pause=azure_native.synapse.AutoPausePropertiesArgs(
        delay_in_minutes=15,
        enabled=True,
    ),
    auto_scale=azure_native.synapse.AutoScalePropertiesArgs(
        enabled=True,
        max_node_count=50,
        min_node_count=3,
    ),
    big_data_pool_name="ExamplePool",
    default_spark_log_folder="/logs",
    is_autotune_enabled=False,
    library_requirements=azure_native.synapse.LibraryRequirementsArgs(
        content="",
        filename="requirements.txt",
    ),
    location="West US 2",
    node_count=4,
    node_size="Medium",
    node_size_family="MemoryOptimized",
    resource_group_name="ExampleResourceGroup",
    spark_events_folder="/events",
    spark_version="3.3",
    tags={
        "key": "value",
    },
    workspace_name="ExampleWorkspace")

```

```yaml
resources:
  bigDataPool:
    type: azure-native:synapse:BigDataPool
    properties:
      autoPause:
        delayInMinutes: 15
        enabled: true
      autoScale:
        enabled: true
        maxNodeCount: 50
        minNodeCount: 3
      bigDataPoolName: ExamplePool
      defaultSparkLogFolder: /logs
      isAutotuneEnabled: false
      libraryRequirements:
        content:
        filename: requirements.txt
      location: West US 2
      nodeCount: 4
      nodeSize: Medium
      nodeSizeFamily: MemoryOptimized
      resourceGroupName: ExampleResourceGroup
      sparkEventsFolder: /events
      sparkVersion: '3.3'
      tags:
        key: value
      workspaceName: ExampleWorkspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:synapse:BigDataPool ExamplePool /subscriptions/01234567-89ab-4def-0123-456789abcdef/resourceGroups/ExampleResourceGroup/providers/Microsoft.Synapse/workspaces/ExampleWorkspace/bigDataPools/ExamplePool 
```
