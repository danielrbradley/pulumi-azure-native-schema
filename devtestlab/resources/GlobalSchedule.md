A schedule.
API Version: 2018-09-15.
Previous API Version: 2018-09-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### GlobalSchedules_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var globalSchedule = new AzureNative.DevTestLab.GlobalSchedule("globalSchedule", new()
    {
        Name = "labvmautostart",
        ResourceGroupName = "resourceGroupName",
        Status = "Enabled",
        TaskType = "LabVmsStartupTask",
        TimeZoneId = "Hawaiian Standard Time",
        WeeklyRecurrence = new AzureNative.DevTestLab.Inputs.WeekDetailsArgs
        {
            Time = "0700",
            Weekdays = new[]
            {
                "Monday",
                "Tuesday",
                "Wednesday",
                "Thursday",
                "Friday",
                "Saturday",
            },
        },
    });

});


```

```go
package main

import (
	devtestlab "github.com/pulumi/pulumi-azure-native-sdk/devtestlab"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := devtestlab.NewGlobalSchedule(ctx, "globalSchedule", &devtestlab.GlobalScheduleArgs{
			Name:              pulumi.String("labvmautostart"),
			ResourceGroupName: pulumi.String("resourceGroupName"),
			Status:            pulumi.String("Enabled"),
			TaskType:          pulumi.String("LabVmsStartupTask"),
			TimeZoneId:        pulumi.String("Hawaiian Standard Time"),
			WeeklyRecurrence: &devtestlab.WeekDetailsArgs{
				Time: pulumi.String("0700"),
				Weekdays: pulumi.StringArray{
					pulumi.String("Monday"),
					pulumi.String("Tuesday"),
					pulumi.String("Wednesday"),
					pulumi.String("Thursday"),
					pulumi.String("Friday"),
					pulumi.String("Saturday"),
				},
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
import com.pulumi.azurenative.devtestlab.GlobalSchedule;
import com.pulumi.azurenative.devtestlab.GlobalScheduleArgs;
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
        var globalSchedule = new GlobalSchedule("globalSchedule", GlobalScheduleArgs.builder()        
            .name("labvmautostart")
            .resourceGroupName("resourceGroupName")
            .status("Enabled")
            .taskType("LabVmsStartupTask")
            .timeZoneId("Hawaiian Standard Time")
            .weeklyRecurrence(Map.ofEntries(
                Map.entry("time", "0700"),
                Map.entry("weekdays",                 
                    "Monday",
                    "Tuesday",
                    "Wednesday",
                    "Thursday",
                    "Friday",
                    "Saturday")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const globalSchedule = new azure_native.devtestlab.GlobalSchedule("globalSchedule", {
    name: "labvmautostart",
    resourceGroupName: "resourceGroupName",
    status: "Enabled",
    taskType: "LabVmsStartupTask",
    timeZoneId: "Hawaiian Standard Time",
    weeklyRecurrence: {
        time: "0700",
        weekdays: [
            "Monday",
            "Tuesday",
            "Wednesday",
            "Thursday",
            "Friday",
            "Saturday",
        ],
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

global_schedule = azure_native.devtestlab.GlobalSchedule("globalSchedule",
    name="labvmautostart",
    resource_group_name="resourceGroupName",
    status="Enabled",
    task_type="LabVmsStartupTask",
    time_zone_id="Hawaiian Standard Time",
    weekly_recurrence=azure_native.devtestlab.WeekDetailsArgs(
        time="0700",
        weekdays=[
            "Monday",
            "Tuesday",
            "Wednesday",
            "Thursday",
            "Friday",
            "Saturday",
        ],
    ))

```

```yaml
resources:
  globalSchedule:
    type: azure-native:devtestlab:GlobalSchedule
    properties:
      name: labvmautostart
      resourceGroupName: resourceGroupName
      status: Enabled
      taskType: LabVmsStartupTask
      timeZoneId: Hawaiian Standard Time
      weeklyRecurrence:
        time: '0700'
        weekdays:
          - Monday
          - Tuesday
          - Wednesday
          - Thursday
          - Friday
          - Saturday

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devtestlab:GlobalSchedule LabVmAutoStart /subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}/schedules/labvmautostart 
```
