Azure Resource Manager resource envelope.
API Version: 2022-10-01.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateOrUpdate Schedule.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var schedule = new AzureNative.MachineLearningServices.Schedule("schedule", new()
    {
        Name = "string",
        ResourceGroupName = "test-rg",
        ScheduleProperties = new AzureNative.MachineLearningServices.Inputs.ScheduleArgs
        {
            Action = new AzureNative.MachineLearningServices.Inputs.EndpointScheduleActionArgs
            {
                ActionType = "InvokeBatchEndpoint",
                EndpointInvocationDefinition = 
                {
                    { "9965593e-526f-4b89-bb36-761138cf2794", null },
                },
            },
            Description = "string",
            DisplayName = "string",
            IsEnabled = false,
            Properties = 
            {
                { "string", "string" },
            },
            Tags = 
            {
                { "string", "string" },
            },
            Trigger = new AzureNative.MachineLearningServices.Inputs.CronTriggerArgs
            {
                EndTime = "string",
                Expression = "string",
                StartTime = "string",
                TimeZone = "string",
                TriggerType = "Cron",
            },
        },
        WorkspaceName = "my-aml-workspace",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.machinelearningservices.Schedule;
import com.pulumi.azurenative.machinelearningservices.ScheduleArgs;
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
        var schedule = new Schedule("schedule", ScheduleArgs.builder()        
            .name("string")
            .resourceGroupName("test-rg")
            .scheduleProperties(Map.ofEntries(
                Map.entry("action", Map.ofEntries(
                    Map.entry("actionType", "InvokeBatchEndpoint"),
                    Map.entry("endpointInvocationDefinition", ScheduleArgs.builder()
%!v(PANIC=Format method: interface conversion: model.Expression is *model.TemplateExpression, not *model.LiteralValueExpression))
                    )),
                    Map.entry("description", "string"),
                    Map.entry("displayName", "string"),
                    Map.entry("isEnabled", false),
                    Map.entry("properties", Map.of("string", "string")),
                    Map.entry("tags", Map.of("string", "string")),
                    Map.entry("trigger", Map.ofEntries(
                        Map.entry("endTime", "string"),
                        Map.entry("expression", "string"),
                        Map.entry("startTime", "string"),
                        Map.entry("timeZone", "string"),
                        Map.entry("triggerType", "Cron")
                    ))
                ))
                .workspaceName("my-aml-workspace")
                .build());

        }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const schedule = new azure_native.machinelearningservices.Schedule("schedule", {
    name: "string",
    resourceGroupName: "test-rg",
    scheduleProperties: {
        action: {
            actionType: "InvokeBatchEndpoint",
            endpointInvocationDefinition: {
                "9965593e-526f-4b89-bb36-761138cf2794": undefined,
            },
        },
        description: "string",
        displayName: "string",
        isEnabled: false,
        properties: {
            string: "string",
        },
        tags: {
            string: "string",
        },
        trigger: {
            endTime: "string",
            expression: "string",
            startTime: "string",
            timeZone: "string",
            triggerType: "Cron",
        },
    },
    workspaceName: "my-aml-workspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

schedule = azure_native.machinelearningservices.Schedule("schedule",
    name="string",
    resource_group_name="test-rg",
    schedule_properties=azure_native.machinelearningservices.ScheduleResponseArgs(
        action=azure_native.machinelearningservices.EndpointScheduleActionArgs(
            action_type="InvokeBatchEndpoint",
            endpoint_invocation_definition={
                "9965593e-526f-4b89-bb36-761138cf2794": None,
            },
        ),
        description="string",
        display_name="string",
        is_enabled=False,
        properties={
            "string": "string",
        },
        tags={
            "string": "string",
        },
        trigger=azure_native.machinelearningservices.CronTriggerArgs(
            end_time="string",
            expression="string",
            start_time="string",
            time_zone="string",
            trigger_type="Cron",
        ),
    ),
    workspace_name="my-aml-workspace")

```

```yaml
resources:
  schedule:
    type: azure-native:machinelearningservices:Schedule
    properties:
      name: string
      resourceGroupName: test-rg
      scheduleProperties:
        action:
          actionType: InvokeBatchEndpoint
          endpointInvocationDefinition:
            9965593e-526f-4b89-bb36-761138cf2794: null
        description: string
        displayName: string
        isEnabled: false
        properties:
          string: string
        tags:
          string: string
        trigger:
          endTime: string
          expression: string
          startTime: string
          timeZone: string
          triggerType: Cron
      workspaceName: my-aml-workspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:machinelearningservices:Schedule string string 
```
