A schedule.
API Version: 2018-09-15.
Previous API Version: 2018-09-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Schedules_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var schedule = new AzureNative.DevTestLab.Schedule("schedule", new()
    {
        DailyRecurrence = new AzureNative.DevTestLab.Inputs.DayDetailsArgs
        {
            Time = "{timeOfTheDayTheScheduleWillOccurEveryDay}",
        },
        HourlyRecurrence = new AzureNative.DevTestLab.Inputs.HourDetailsArgs
        {
            Minute = 30,
        },
        LabName = "{labName}",
        Location = "{location}",
        Name = "{scheduleName}",
        NotificationSettings = new AzureNative.DevTestLab.Inputs.NotificationSettingsArgs
        {
            EmailRecipient = "{email}",
            NotificationLocale = "EN",
            Status = "{Enabled|Disabled}",
            TimeInMinutes = 15,
            WebhookUrl = "{webhookUrl}",
        },
        ResourceGroupName = "resourceGroupName",
        Status = "{Enabled|Disabled}",
        Tags = 
        {
            { "tagName1", "tagValue1" },
        },
        TargetResourceId = "/subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}",
        TaskType = "{myLabVmTaskType}",
        TimeZoneId = "Pacific Standard Time",
        WeeklyRecurrence = new AzureNative.DevTestLab.Inputs.WeekDetailsArgs
        {
            Time = "{timeOfTheDayTheScheduleWillOccurOnThoseDays}",
            Weekdays = new[]
            {
                "Monday",
                "Wednesday",
                "Friday",
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
		_, err := devtestlab.NewSchedule(ctx, "schedule", &devtestlab.ScheduleArgs{
			DailyRecurrence: &devtestlab.DayDetailsArgs{
				Time: pulumi.String("{timeOfTheDayTheScheduleWillOccurEveryDay}"),
			},
			HourlyRecurrence: &devtestlab.HourDetailsArgs{
				Minute: pulumi.Int(30),
			},
			LabName:  pulumi.String("{labName}"),
			Location: pulumi.String("{location}"),
			Name:     pulumi.String("{scheduleName}"),
			NotificationSettings: &devtestlab.NotificationSettingsArgs{
				EmailRecipient:     pulumi.String("{email}"),
				NotificationLocale: pulumi.String("EN"),
				Status:             pulumi.String("{Enabled|Disabled}"),
				TimeInMinutes:      pulumi.Int(15),
				WebhookUrl:         pulumi.String("{webhookUrl}"),
			},
			ResourceGroupName: pulumi.String("resourceGroupName"),
			Status:            pulumi.String("{Enabled|Disabled}"),
			Tags: pulumi.StringMap{
				"tagName1": pulumi.String("tagValue1"),
			},
			TargetResourceId: pulumi.String("/subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}"),
			TaskType:         pulumi.String("{myLabVmTaskType}"),
			TimeZoneId:       pulumi.String("Pacific Standard Time"),
			WeeklyRecurrence: &devtestlab.WeekDetailsArgs{
				Time: pulumi.String("{timeOfTheDayTheScheduleWillOccurOnThoseDays}"),
				Weekdays: pulumi.StringArray{
					pulumi.String("Monday"),
					pulumi.String("Wednesday"),
					pulumi.String("Friday"),
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
import com.pulumi.azurenative.devtestlab.Schedule;
import com.pulumi.azurenative.devtestlab.ScheduleArgs;
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
            .dailyRecurrence(Map.of("time", "{timeOfTheDayTheScheduleWillOccurEveryDay}"))
            .hourlyRecurrence(Map.of("minute", 30))
            .labName("{labName}")
            .location("{location}")
            .name("{scheduleName}")
            .notificationSettings(Map.ofEntries(
                Map.entry("emailRecipient", "{email}"),
                Map.entry("notificationLocale", "EN"),
                Map.entry("status", "{Enabled|Disabled}"),
                Map.entry("timeInMinutes", 15),
                Map.entry("webhookUrl", "{webhookUrl}")
            ))
            .resourceGroupName("resourceGroupName")
            .status("{Enabled|Disabled}")
            .tags(Map.of("tagName1", "tagValue1"))
            .targetResourceId("/subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}")
            .taskType("{myLabVmTaskType}")
            .timeZoneId("Pacific Standard Time")
            .weeklyRecurrence(Map.ofEntries(
                Map.entry("time", "{timeOfTheDayTheScheduleWillOccurOnThoseDays}"),
                Map.entry("weekdays",                 
                    "Monday",
                    "Wednesday",
                    "Friday")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const schedule = new azure_native.devtestlab.Schedule("schedule", {
    dailyRecurrence: {
        time: "{timeOfTheDayTheScheduleWillOccurEveryDay}",
    },
    hourlyRecurrence: {
        minute: 30,
    },
    labName: "{labName}",
    location: "{location}",
    name: "{scheduleName}",
    notificationSettings: {
        emailRecipient: "{email}",
        notificationLocale: "EN",
        status: "{Enabled|Disabled}",
        timeInMinutes: 15,
        webhookUrl: "{webhookUrl}",
    },
    resourceGroupName: "resourceGroupName",
    status: "{Enabled|Disabled}",
    tags: {
        tagName1: "tagValue1",
    },
    targetResourceId: "/subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}",
    taskType: "{myLabVmTaskType}",
    timeZoneId: "Pacific Standard Time",
    weeklyRecurrence: {
        time: "{timeOfTheDayTheScheduleWillOccurOnThoseDays}",
        weekdays: [
            "Monday",
            "Wednesday",
            "Friday",
        ],
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

schedule = azure_native.devtestlab.Schedule("schedule",
    daily_recurrence=azure_native.devtestlab.DayDetailsArgs(
        time="{timeOfTheDayTheScheduleWillOccurEveryDay}",
    ),
    hourly_recurrence=azure_native.devtestlab.HourDetailsArgs(
        minute=30,
    ),
    lab_name="{labName}",
    location="{location}",
    name="{scheduleName}",
    notification_settings=azure_native.devtestlab.NotificationSettingsArgs(
        email_recipient="{email}",
        notification_locale="EN",
        status="{Enabled|Disabled}",
        time_in_minutes=15,
        webhook_url="{webhookUrl}",
    ),
    resource_group_name="resourceGroupName",
    status="{Enabled|Disabled}",
    tags={
        "tagName1": "tagValue1",
    },
    target_resource_id="/subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}",
    task_type="{myLabVmTaskType}",
    time_zone_id="Pacific Standard Time",
    weekly_recurrence=azure_native.devtestlab.WeekDetailsArgs(
        time="{timeOfTheDayTheScheduleWillOccurOnThoseDays}",
        weekdays=[
            "Monday",
            "Wednesday",
            "Friday",
        ],
    ))

```

```yaml
resources:
  schedule:
    type: azure-native:devtestlab:Schedule
    properties:
      dailyRecurrence:
        time: '{timeOfTheDayTheScheduleWillOccurEveryDay}'
      hourlyRecurrence:
        minute: 30
      labName: '{labName}'
      location: '{location}'
      name: '{scheduleName}'
      notificationSettings:
        emailRecipient: '{email}'
        notificationLocale: EN
        status: '{Enabled|Disabled}'
        timeInMinutes: 15
        webhookUrl: '{webhookUrl}'
      resourceGroupName: resourceGroupName
      status: '{Enabled|Disabled}'
      tags:
        tagName1: tagValue1
      targetResourceId: /subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}
      taskType: '{myLabVmTaskType}'
      timeZoneId: Pacific Standard Time
      weeklyRecurrence:
        time: '{timeOfTheDayTheScheduleWillOccurOnThoseDays}'
        weekdays:
          - Monday
          - Wednesday
          - Friday

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devtestlab:Schedule {scheduleName} /subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}/schedules/{scheduleName} 
```
