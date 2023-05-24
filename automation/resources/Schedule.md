Definition of the schedule.
API Version: 2022-08-08.
Previous API Version: 2019-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a schedule
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var schedule = new AzureNative.Automation.Schedule("schedule", new()
    {
        AdvancedSchedule = null,
        AutomationAccountName = "myAutomationAccount33",
        Description = "my description of schedule goes here",
        ExpiryTime = "2017-04-01T17:28:57.2494819Z",
        Frequency = "Hour",
        Interval = 1,
        Name = "mySchedule",
        ResourceGroupName = "rg",
        ScheduleName = "mySchedule",
        StartTime = "2017-03-27T17:28:57.2494819Z",
    });

});


```

```go
package main

import (
	automation "github.com/pulumi/pulumi-azure-native-sdk/automation"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := automation.NewSchedule(ctx, "schedule", &automation.ScheduleArgs{
			AdvancedSchedule:      nil,
			AutomationAccountName: pulumi.String("myAutomationAccount33"),
			Description:           pulumi.String("my description of schedule goes here"),
			ExpiryTime:            pulumi.String("2017-04-01T17:28:57.2494819Z"),
			Frequency:             pulumi.String("Hour"),
			Interval:              pulumi.Any(1),
			Name:                  pulumi.String("mySchedule"),
			ResourceGroupName:     pulumi.String("rg"),
			ScheduleName:          pulumi.String("mySchedule"),
			StartTime:             pulumi.String("2017-03-27T17:28:57.2494819Z"),
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
import com.pulumi.azurenative.automation.Schedule;
import com.pulumi.azurenative.automation.ScheduleArgs;
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
            .advancedSchedule()
            .automationAccountName("myAutomationAccount33")
            .description("my description of schedule goes here")
            .expiryTime("2017-04-01T17:28:57.2494819Z")
            .frequency("Hour")
            .interval(1)
            .name("mySchedule")
            .resourceGroupName("rg")
            .scheduleName("mySchedule")
            .startTime("2017-03-27T17:28:57.2494819Z")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const schedule = new azure_native.automation.Schedule("schedule", {
    advancedSchedule: {},
    automationAccountName: "myAutomationAccount33",
    description: "my description of schedule goes here",
    expiryTime: "2017-04-01T17:28:57.2494819Z",
    frequency: "Hour",
    interval: 1,
    name: "mySchedule",
    resourceGroupName: "rg",
    scheduleName: "mySchedule",
    startTime: "2017-03-27T17:28:57.2494819Z",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

schedule = azure_native.automation.Schedule("schedule",
    advanced_schedule=azure_native.automation.AdvancedScheduleArgs(),
    automation_account_name="myAutomationAccount33",
    description="my description of schedule goes here",
    expiry_time="2017-04-01T17:28:57.2494819Z",
    frequency="Hour",
    interval=1,
    name="mySchedule",
    resource_group_name="rg",
    schedule_name="mySchedule",
    start_time="2017-03-27T17:28:57.2494819Z")

```

```yaml
resources:
  schedule:
    type: azure-native:automation:Schedule
    properties:
      advancedSchedule: {}
      automationAccountName: myAutomationAccount33
      description: my description of schedule goes here
      expiryTime: 2017-04-01T17:28:57.2494819Z
      frequency: Hour
      interval: 1
      name: mySchedule
      resourceGroupName: rg
      scheduleName: mySchedule
      startTime: 2017-03-27T17:28:57.2494819Z

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:automation:Schedule mySchedule /subscriptions/subid/resourceGroups/rg/providers/Microsoft.Automation/automationAccounts/myAutomationAccount33/schedules/mySchedule 
```
