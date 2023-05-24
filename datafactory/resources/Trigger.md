Trigger resource type.
API Version: 2018-06-01.
Previous API Version: 2018-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Triggers_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var trigger = new AzureNative.DataFactory.Trigger("trigger", new()
    {
        FactoryName = "exampleFactoryName",
        Properties = new AzureNative.DataFactory.Inputs.ScheduleTriggerArgs
        {
            Pipelines = new[]
            {
                new AzureNative.DataFactory.Inputs.TriggerPipelineReferenceArgs
                {
                    Parameters = 
                    {
                        { "OutputBlobNameList", new[]
                        {
                            "exampleoutput.csv",
                        } },
                    },
                    PipelineReference = new AzureNative.DataFactory.Inputs.PipelineReferenceArgs
                    {
                        ReferenceName = "examplePipeline",
                        Type = "PipelineReference",
                    },
                },
            },
            Recurrence = new AzureNative.DataFactory.Inputs.ScheduleTriggerRecurrenceArgs
            {
                EndTime = "2018-06-16T00:55:13.8441801Z",
                Frequency = "Minute",
                Interval = 4,
                StartTime = "2018-06-16T00:39:13.8441801Z",
                TimeZone = "UTC",
            },
            Type = "ScheduleTrigger",
        },
        ResourceGroupName = "exampleResourceGroup",
        TriggerName = "exampleTrigger",
    });

});


```

```go
package main

import (
	datafactory "github.com/pulumi/pulumi-azure-native-sdk/datafactory"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := datafactory.NewTrigger(ctx, "trigger", &datafactory.TriggerArgs{
			FactoryName: pulumi.String("exampleFactoryName"),
			Properties: datafactory.ScheduleTrigger{
				Pipelines: []datafactory.TriggerPipelineReference{
					{
						Parameters: {
							"OutputBlobNameList": []string{
								"exampleoutput.csv",
							},
						},
						PipelineReference: {
							ReferenceName: "examplePipeline",
							Type:          "PipelineReference",
						},
					},
				},
				Recurrence: datafactory.ScheduleTriggerRecurrence{
					EndTime:   "2018-06-16T00:55:13.8441801Z",
					Frequency: "Minute",
					Interval:  4,
					StartTime: "2018-06-16T00:39:13.8441801Z",
					TimeZone:  "UTC",
				},
				Type: "ScheduleTrigger",
			},
			ResourceGroupName: pulumi.String("exampleResourceGroup"),
			TriggerName:       pulumi.String("exampleTrigger"),
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
import com.pulumi.azurenative.datafactory.Trigger;
import com.pulumi.azurenative.datafactory.TriggerArgs;
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
        var trigger = new Trigger("trigger", TriggerArgs.builder()        
            .factoryName("exampleFactoryName")
            .properties(Map.ofEntries(
                Map.entry("pipelines", Map.ofEntries(
                    Map.entry("parameters", BlobEventsTriggerArgs.builder()
                        .outputBlobNameList("exampleoutput.csv")
                        .build()),
                    Map.entry("pipelineReference", Map.ofEntries(
                        Map.entry("referenceName", "examplePipeline"),
                        Map.entry("type", "PipelineReference")
                    ))
                )),
                Map.entry("recurrence", Map.ofEntries(
                    Map.entry("endTime", "2018-06-16T00:55:13.8441801Z"),
                    Map.entry("frequency", "Minute"),
                    Map.entry("interval", 4),
                    Map.entry("startTime", "2018-06-16T00:39:13.8441801Z"),
                    Map.entry("timeZone", "UTC")
                )),
                Map.entry("type", "ScheduleTrigger")
            ))
            .resourceGroupName("exampleResourceGroup")
            .triggerName("exampleTrigger")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const trigger = new azure_native.datafactory.Trigger("trigger", {
    factoryName: "exampleFactoryName",
    properties: {
        pipelines: [{
            parameters: {
                OutputBlobNameList: ["exampleoutput.csv"],
            },
            pipelineReference: {
                referenceName: "examplePipeline",
                type: "PipelineReference",
            },
        }],
        recurrence: {
            endTime: "2018-06-16T00:55:13.8441801Z",
            frequency: "Minute",
            interval: 4,
            startTime: "2018-06-16T00:39:13.8441801Z",
            timeZone: "UTC",
        },
        type: "ScheduleTrigger",
    },
    resourceGroupName: "exampleResourceGroup",
    triggerName: "exampleTrigger",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

trigger = azure_native.datafactory.Trigger("trigger",
    factory_name="exampleFactoryName",
    properties=azure_native.datafactory.ScheduleTriggerArgs(
        pipelines=[azure_native.datafactory.TriggerPipelineReferenceArgs(
            parameters={
                "OutputBlobNameList": ["exampleoutput.csv"],
            },
            pipeline_reference=azure_native.datafactory.PipelineReferenceArgs(
                reference_name="examplePipeline",
                type="PipelineReference",
            ),
        )],
        recurrence=azure_native.datafactory.ScheduleTriggerRecurrenceArgs(
            end_time="2018-06-16T00:55:13.8441801Z",
            frequency="Minute",
            interval=4,
            start_time="2018-06-16T00:39:13.8441801Z",
            time_zone="UTC",
        ),
        type="ScheduleTrigger",
    ),
    resource_group_name="exampleResourceGroup",
    trigger_name="exampleTrigger")

```

```yaml
resources:
  trigger:
    type: azure-native:datafactory:Trigger
    properties:
      factoryName: exampleFactoryName
      properties:
        pipelines:
          - parameters:
              OutputBlobNameList:
                - exampleoutput.csv
            pipelineReference:
              referenceName: examplePipeline
              type: PipelineReference
        recurrence:
          endTime: 2018-06-16T00:55:13.8441801Z
          frequency: Minute
          interval: 4
          startTime: 2018-06-16T00:39:13.8441801Z
          timeZone: UTC
        type: ScheduleTrigger
      resourceGroupName: exampleResourceGroup
      triggerName: exampleTrigger

```

{{% /example %}}
{{% example %}}
### Triggers_Update
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var trigger = new AzureNative.DataFactory.Trigger("trigger", new()
    {
        FactoryName = "exampleFactoryName",
        Properties = new AzureNative.DataFactory.Inputs.ScheduleTriggerArgs
        {
            Description = "Example description",
            Pipelines = new[]
            {
                new AzureNative.DataFactory.Inputs.TriggerPipelineReferenceArgs
                {
                    Parameters = 
                    {
                        { "OutputBlobNameList", new[]
                        {
                            "exampleoutput.csv",
                        } },
                    },
                    PipelineReference = new AzureNative.DataFactory.Inputs.PipelineReferenceArgs
                    {
                        ReferenceName = "examplePipeline",
                        Type = "PipelineReference",
                    },
                },
            },
            Recurrence = new AzureNative.DataFactory.Inputs.ScheduleTriggerRecurrenceArgs
            {
                EndTime = "2018-06-16T00:55:14.905167Z",
                Frequency = "Minute",
                Interval = 4,
                StartTime = "2018-06-16T00:39:14.905167Z",
                TimeZone = "UTC",
            },
            Type = "ScheduleTrigger",
        },
        ResourceGroupName = "exampleResourceGroup",
        TriggerName = "exampleTrigger",
    });

});


```

```go
package main

import (
	datafactory "github.com/pulumi/pulumi-azure-native-sdk/datafactory"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := datafactory.NewTrigger(ctx, "trigger", &datafactory.TriggerArgs{
			FactoryName: pulumi.String("exampleFactoryName"),
			Properties: datafactory.ScheduleTrigger{
				Description: "Example description",
				Pipelines: []datafactory.TriggerPipelineReference{
					{
						Parameters: {
							"OutputBlobNameList": []string{
								"exampleoutput.csv",
							},
						},
						PipelineReference: {
							ReferenceName: "examplePipeline",
							Type:          "PipelineReference",
						},
					},
				},
				Recurrence: datafactory.ScheduleTriggerRecurrence{
					EndTime:   "2018-06-16T00:55:14.905167Z",
					Frequency: "Minute",
					Interval:  4,
					StartTime: "2018-06-16T00:39:14.905167Z",
					TimeZone:  "UTC",
				},
				Type: "ScheduleTrigger",
			},
			ResourceGroupName: pulumi.String("exampleResourceGroup"),
			TriggerName:       pulumi.String("exampleTrigger"),
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
import com.pulumi.azurenative.datafactory.Trigger;
import com.pulumi.azurenative.datafactory.TriggerArgs;
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
        var trigger = new Trigger("trigger", TriggerArgs.builder()        
            .factoryName("exampleFactoryName")
            .properties(Map.ofEntries(
                Map.entry("description", "Example description"),
                Map.entry("pipelines", Map.ofEntries(
                    Map.entry("parameters", BlobEventsTriggerArgs.builder()
                        .outputBlobNameList("exampleoutput.csv")
                        .build()),
                    Map.entry("pipelineReference", Map.ofEntries(
                        Map.entry("referenceName", "examplePipeline"),
                        Map.entry("type", "PipelineReference")
                    ))
                )),
                Map.entry("recurrence", Map.ofEntries(
                    Map.entry("endTime", "2018-06-16T00:55:14.905167Z"),
                    Map.entry("frequency", "Minute"),
                    Map.entry("interval", 4),
                    Map.entry("startTime", "2018-06-16T00:39:14.905167Z"),
                    Map.entry("timeZone", "UTC")
                )),
                Map.entry("type", "ScheduleTrigger")
            ))
            .resourceGroupName("exampleResourceGroup")
            .triggerName("exampleTrigger")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const trigger = new azure_native.datafactory.Trigger("trigger", {
    factoryName: "exampleFactoryName",
    properties: {
        description: "Example description",
        pipelines: [{
            parameters: {
                OutputBlobNameList: ["exampleoutput.csv"],
            },
            pipelineReference: {
                referenceName: "examplePipeline",
                type: "PipelineReference",
            },
        }],
        recurrence: {
            endTime: "2018-06-16T00:55:14.905167Z",
            frequency: "Minute",
            interval: 4,
            startTime: "2018-06-16T00:39:14.905167Z",
            timeZone: "UTC",
        },
        type: "ScheduleTrigger",
    },
    resourceGroupName: "exampleResourceGroup",
    triggerName: "exampleTrigger",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

trigger = azure_native.datafactory.Trigger("trigger",
    factory_name="exampleFactoryName",
    properties=azure_native.datafactory.ScheduleTriggerArgs(
        description="Example description",
        pipelines=[azure_native.datafactory.TriggerPipelineReferenceArgs(
            parameters={
                "OutputBlobNameList": ["exampleoutput.csv"],
            },
            pipeline_reference=azure_native.datafactory.PipelineReferenceArgs(
                reference_name="examplePipeline",
                type="PipelineReference",
            ),
        )],
        recurrence=azure_native.datafactory.ScheduleTriggerRecurrenceArgs(
            end_time="2018-06-16T00:55:14.905167Z",
            frequency="Minute",
            interval=4,
            start_time="2018-06-16T00:39:14.905167Z",
            time_zone="UTC",
        ),
        type="ScheduleTrigger",
    ),
    resource_group_name="exampleResourceGroup",
    trigger_name="exampleTrigger")

```

```yaml
resources:
  trigger:
    type: azure-native:datafactory:Trigger
    properties:
      factoryName: exampleFactoryName
      properties:
        description: Example description
        pipelines:
          - parameters:
              OutputBlobNameList:
                - exampleoutput.csv
            pipelineReference:
              referenceName: examplePipeline
              type: PipelineReference
        recurrence:
          endTime: 2018-06-16T00:55:14.905167Z
          frequency: Minute
          interval: 4
          startTime: 2018-06-16T00:39:14.905167Z
          timeZone: UTC
        type: ScheduleTrigger
      resourceGroupName: exampleResourceGroup
      triggerName: exampleTrigger

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:datafactory:Trigger exampleTrigger /subscriptions/12345678-1234-1234-1234-12345678abc/resourceGroups/exampleResourceGroup/providers/Microsoft.DataFactory/factories/exampleFactoryName/triggers/exampleTrigger 
```
