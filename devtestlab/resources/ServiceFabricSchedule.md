A schedule.
API Version: 2018-09-15.
Previous API Version: 2018-09-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ServiceFabricSchedules_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var serviceFabricSchedule = new AzureNative.DevTestLab.ServiceFabricSchedule("serviceFabricSchedule", new()
    {
        DailyRecurrence = new AzureNative.DevTestLab.Inputs.DayDetailsArgs
        {
            Time = "19:00",
        },
        HourlyRecurrence = new AzureNative.DevTestLab.Inputs.HourDetailsArgs
        {
            Minute = 0,
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
            WebhookUrl = "{webhoolUrl}",
        },
        ResourceGroupName = "resourceGroupName",
        ServiceFabricName = "{serviceFrabicName}",
        Status = "{Enabled|Disabled}",
        Tags = 
        {
            { "tagName1", "tagValue1" },
        },
        TargetResourceId = "/subscriptions/{subscriptionId}/resourceGroups/resourceGroupName/providers/Microsoft.DevTestLab/labs/{labName}/users/{uniqueIdentifier}/servicefabrics/{serviceFrabicName}",
        TaskType = "{Unknown|LabVmsShutdownTask|LabVmsStartupTask|LabVmReclamationTask|ComputeVmShutdownTask}",
        TimeZoneId = "Pacific Standard Time",
        UserName = "@me",
        WeeklyRecurrence = new AzureNative.DevTestLab.Inputs.WeekDetailsArgs
        {
            Time = "19:00",
            Weekdays = new[]
            {
                "Monday",
                "Tuesday",
                "Wednesday",
                "Thursday",
                "Friday",
                "Saturday",
                "Sunday",
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
		_, err := devtestlab.NewServiceFabricSchedule(ctx, "serviceFabricSchedule", &devtestlab.ServiceFabricScheduleArgs{
			DailyRecurrence: &devtestlab.DayDetailsArgs{
				Time: pulumi.String("19:00"),
			},
			HourlyRecurrence: &devtestlab.HourDetailsArgs{
				Minute: pulumi.Int(0),
			},
			LabName:  pulumi.String("{labName}"),
			Location: pulumi.String("{location}"),
			Name:     pulumi.String("{scheduleName}"),
			NotificationSettings: &devtestlab.NotificationSettingsArgs{
				EmailRecipient:     pulumi.String("{email}"),
				NotificationLocale: pulumi.String("EN"),
				Status:             pulumi.String("{Enabled|Disabled}"),
				TimeInMinutes:      pulumi.Int(15),
				WebhookUrl:         pulumi.String("{webhoolUrl}"),
			},
			ResourceGroupName: pulumi.String("resourceGroupName"),
			ServiceFabricName: pulumi.String("{serviceFrabicName}"),
			Status:            pulumi.String("{Enabled|Disabled}"),
			Tags: pulumi.StringMap{
				"tagName1": pulumi.String("tagValue1"),
			},
			TargetResourceId: pulumi.String("/subscriptions/{subscriptionId}/resourceGroups/resourceGroupName/providers/Microsoft.DevTestLab/labs/{labName}/users/{uniqueIdentifier}/servicefabrics/{serviceFrabicName}"),
			TaskType:         pulumi.String("{Unknown|LabVmsShutdownTask|LabVmsStartupTask|LabVmReclamationTask|ComputeVmShutdownTask}"),
			TimeZoneId:       pulumi.String("Pacific Standard Time"),
			UserName:         pulumi.String("@me"),
			WeeklyRecurrence: &devtestlab.WeekDetailsArgs{
				Time: pulumi.String("19:00"),
				Weekdays: pulumi.StringArray{
					pulumi.String("Monday"),
					pulumi.String("Tuesday"),
					pulumi.String("Wednesday"),
					pulumi.String("Thursday"),
					pulumi.String("Friday"),
					pulumi.String("Saturday"),
					pulumi.String("Sunday"),
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
import com.pulumi.azurenative.devtestlab.ServiceFabricSchedule;
import com.pulumi.azurenative.devtestlab.ServiceFabricScheduleArgs;
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
        var serviceFabricSchedule = new ServiceFabricSchedule("serviceFabricSchedule", ServiceFabricScheduleArgs.builder()        
            .dailyRecurrence(Map.of("time", "19:00"))
            .hourlyRecurrence(Map.of("minute", 0))
            .labName("{labName}")
            .location("{location}")
            .name("{scheduleName}")
            .notificationSettings(Map.ofEntries(
                Map.entry("emailRecipient", "{email}"),
                Map.entry("notificationLocale", "EN"),
                Map.entry("status", "{Enabled|Disabled}"),
                Map.entry("timeInMinutes", 15),
                Map.entry("webhookUrl", "{webhoolUrl}")
            ))
            .resourceGroupName("resourceGroupName")
            .serviceFabricName("{serviceFrabicName}")
            .status("{Enabled|Disabled}")
            .tags(Map.of("tagName1", "tagValue1"))
            .targetResourceId("/subscriptions/{subscriptionId}/resourceGroups/resourceGroupName/providers/Microsoft.DevTestLab/labs/{labName}/users/{uniqueIdentifier}/servicefabrics/{serviceFrabicName}")
            .taskType("{Unknown|LabVmsShutdownTask|LabVmsStartupTask|LabVmReclamationTask|ComputeVmShutdownTask}")
            .timeZoneId("Pacific Standard Time")
            .userName("@me")
            .weeklyRecurrence(Map.ofEntries(
                Map.entry("time", "19:00"),
                Map.entry("weekdays",                 
                    "Monday",
                    "Tuesday",
                    "Wednesday",
                    "Thursday",
                    "Friday",
                    "Saturday",
                    "Sunday")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const serviceFabricSchedule = new azure_native.devtestlab.ServiceFabricSchedule("serviceFabricSchedule", {
    dailyRecurrence: {
        time: "19:00",
    },
    hourlyRecurrence: {
        minute: 0,
    },
    labName: "{labName}",
    location: "{location}",
    name: "{scheduleName}",
    notificationSettings: {
        emailRecipient: "{email}",
        notificationLocale: "EN",
        status: "{Enabled|Disabled}",
        timeInMinutes: 15,
        webhookUrl: "{webhoolUrl}",
    },
    resourceGroupName: "resourceGroupName",
    serviceFabricName: "{serviceFrabicName}",
    status: "{Enabled|Disabled}",
    tags: {
        tagName1: "tagValue1",
    },
    targetResourceId: "/subscriptions/{subscriptionId}/resourceGroups/resourceGroupName/providers/Microsoft.DevTestLab/labs/{labName}/users/{uniqueIdentifier}/servicefabrics/{serviceFrabicName}",
    taskType: "{Unknown|LabVmsShutdownTask|LabVmsStartupTask|LabVmReclamationTask|ComputeVmShutdownTask}",
    timeZoneId: "Pacific Standard Time",
    userName: "@me",
    weeklyRecurrence: {
        time: "19:00",
        weekdays: [
            "Monday",
            "Tuesday",
            "Wednesday",
            "Thursday",
            "Friday",
            "Saturday",
            "Sunday",
        ],
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service_fabric_schedule = azure_native.devtestlab.ServiceFabricSchedule("serviceFabricSchedule",
    daily_recurrence=azure_native.devtestlab.DayDetailsArgs(
        time="19:00",
    ),
    hourly_recurrence=azure_native.devtestlab.HourDetailsArgs(
        minute=0,
    ),
    lab_name="{labName}",
    location="{location}",
    name="{scheduleName}",
    notification_settings=azure_native.devtestlab.NotificationSettingsArgs(
        email_recipient="{email}",
        notification_locale="EN",
        status="{Enabled|Disabled}",
        time_in_minutes=15,
        webhook_url="{webhoolUrl}",
    ),
    resource_group_name="resourceGroupName",
    service_fabric_name="{serviceFrabicName}",
    status="{Enabled|Disabled}",
    tags={
        "tagName1": "tagValue1",
    },
    target_resource_id="/subscriptions/{subscriptionId}/resourceGroups/resourceGroupName/providers/Microsoft.DevTestLab/labs/{labName}/users/{uniqueIdentifier}/servicefabrics/{serviceFrabicName}",
    task_type="{Unknown|LabVmsShutdownTask|LabVmsStartupTask|LabVmReclamationTask|ComputeVmShutdownTask}",
    time_zone_id="Pacific Standard Time",
    user_name="@me",
    weekly_recurrence=azure_native.devtestlab.WeekDetailsArgs(
        time="19:00",
        weekdays=[
            "Monday",
            "Tuesday",
            "Wednesday",
            "Thursday",
            "Friday",
            "Saturday",
            "Sunday",
        ],
    ))

```

```yaml
resources:
  serviceFabricSchedule:
    type: azure-native:devtestlab:ServiceFabricSchedule
    properties:
      dailyRecurrence:
        time: 19:00
      hourlyRecurrence:
        minute: 0
      labName: '{labName}'
      location: '{location}'
      name: '{scheduleName}'
      notificationSettings:
        emailRecipient: '{email}'
        notificationLocale: EN
        status: '{Enabled|Disabled}'
        timeInMinutes: 15
        webhookUrl: '{webhoolUrl}'
      resourceGroupName: resourceGroupName
      serviceFabricName: '{serviceFrabicName}'
      status: '{Enabled|Disabled}'
      tags:
        tagName1: tagValue1
      targetResourceId: /subscriptions/{subscriptionId}/resourceGroups/resourceGroupName/providers/Microsoft.DevTestLab/labs/{labName}/users/{uniqueIdentifier}/servicefabrics/{serviceFrabicName}
      taskType: '{Unknown|LabVmsShutdownTask|LabVmsStartupTask|LabVmReclamationTask|ComputeVmShutdownTask}'
      timeZoneId: Pacific Standard Time
      userName: '@me'
      weeklyRecurrence:
        time: 19:00
        weekdays:
          - Monday
          - Tuesday
          - Wednesday
          - Thursday
          - Friday
          - Saturday
          - Sunday

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devtestlab:ServiceFabricSchedule {scheduleName} /subscriptions/{subscriptionId}/resourceGroups/resourceGroupName/providers/Microsoft.DevTestLab/labs/{labName}/users/{uniqueIdentifier}/servicefabrics/{serviceFrabicName}/schedules/{scheduleName} 
```
