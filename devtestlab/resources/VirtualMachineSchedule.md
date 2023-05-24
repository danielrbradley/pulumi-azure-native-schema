A schedule.
API Version: 2018-09-15.
Previous API Version: 2018-09-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### VirtualMachineSchedules_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineSchedule = new AzureNative.DevTestLab.VirtualMachineSchedule("virtualMachineSchedule", new()
    {
        DailyRecurrence = new AzureNative.DevTestLab.Inputs.DayDetailsArgs
        {
            Time = "1900",
        },
        HourlyRecurrence = new AzureNative.DevTestLab.Inputs.HourDetailsArgs
        {
            Minute = 30,
        },
        LabName = "{labName}",
        Location = "{location}",
        Name = "LabVmsShutdown",
        NotificationSettings = new AzureNative.DevTestLab.Inputs.NotificationSettingsArgs
        {
            EmailRecipient = "{email}",
            NotificationLocale = "EN",
            Status = "Enabled",
            TimeInMinutes = 30,
            WebhookUrl = "{webhookUrl}",
        },
        ResourceGroupName = "resourceGroupName",
        Status = "Enabled",
        Tags = 
        {
            { "tagName1", "tagValue1" },
        },
        TargetResourceId = "/subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}/virtualMachines/{vmName}",
        TaskType = "LabVmsShutdownTask",
        TimeZoneId = "Pacific Standard Time",
        VirtualMachineName = "{vmName}",
        WeeklyRecurrence = new AzureNative.DevTestLab.Inputs.WeekDetailsArgs
        {
            Time = "1700",
            Weekdays = new[]
            {
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
		_, err := devtestlab.NewVirtualMachineSchedule(ctx, "virtualMachineSchedule", &devtestlab.VirtualMachineScheduleArgs{
			DailyRecurrence: &devtestlab.DayDetailsArgs{
				Time: pulumi.String("1900"),
			},
			HourlyRecurrence: &devtestlab.HourDetailsArgs{
				Minute: pulumi.Int(30),
			},
			LabName:  pulumi.String("{labName}"),
			Location: pulumi.String("{location}"),
			Name:     pulumi.String("LabVmsShutdown"),
			NotificationSettings: &devtestlab.NotificationSettingsArgs{
				EmailRecipient:     pulumi.String("{email}"),
				NotificationLocale: pulumi.String("EN"),
				Status:             pulumi.String("Enabled"),
				TimeInMinutes:      pulumi.Int(30),
				WebhookUrl:         pulumi.String("{webhookUrl}"),
			},
			ResourceGroupName: pulumi.String("resourceGroupName"),
			Status:            pulumi.String("Enabled"),
			Tags: pulumi.StringMap{
				"tagName1": pulumi.String("tagValue1"),
			},
			TargetResourceId:   pulumi.String("/subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}/virtualMachines/{vmName}"),
			TaskType:           pulumi.String("LabVmsShutdownTask"),
			TimeZoneId:         pulumi.String("Pacific Standard Time"),
			VirtualMachineName: pulumi.String("{vmName}"),
			WeeklyRecurrence: &devtestlab.WeekDetailsArgs{
				Time: pulumi.String("1700"),
				Weekdays: pulumi.StringArray{
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
import com.pulumi.azurenative.devtestlab.VirtualMachineSchedule;
import com.pulumi.azurenative.devtestlab.VirtualMachineScheduleArgs;
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
        var virtualMachineSchedule = new VirtualMachineSchedule("virtualMachineSchedule", VirtualMachineScheduleArgs.builder()        
            .dailyRecurrence(Map.of("time", "1900"))
            .hourlyRecurrence(Map.of("minute", 30))
            .labName("{labName}")
            .location("{location}")
            .name("LabVmsShutdown")
            .notificationSettings(Map.ofEntries(
                Map.entry("emailRecipient", "{email}"),
                Map.entry("notificationLocale", "EN"),
                Map.entry("status", "Enabled"),
                Map.entry("timeInMinutes", 30),
                Map.entry("webhookUrl", "{webhookUrl}")
            ))
            .resourceGroupName("resourceGroupName")
            .status("Enabled")
            .tags(Map.of("tagName1", "tagValue1"))
            .targetResourceId("/subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}/virtualMachines/{vmName}")
            .taskType("LabVmsShutdownTask")
            .timeZoneId("Pacific Standard Time")
            .virtualMachineName("{vmName}")
            .weeklyRecurrence(Map.ofEntries(
                Map.entry("time", "1700"),
                Map.entry("weekdays",                 
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

const virtualMachineSchedule = new azure_native.devtestlab.VirtualMachineSchedule("virtualMachineSchedule", {
    dailyRecurrence: {
        time: "1900",
    },
    hourlyRecurrence: {
        minute: 30,
    },
    labName: "{labName}",
    location: "{location}",
    name: "LabVmsShutdown",
    notificationSettings: {
        emailRecipient: "{email}",
        notificationLocale: "EN",
        status: "Enabled",
        timeInMinutes: 30,
        webhookUrl: "{webhookUrl}",
    },
    resourceGroupName: "resourceGroupName",
    status: "Enabled",
    tags: {
        tagName1: "tagValue1",
    },
    targetResourceId: "/subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}/virtualMachines/{vmName}",
    taskType: "LabVmsShutdownTask",
    timeZoneId: "Pacific Standard Time",
    virtualMachineName: "{vmName}",
    weeklyRecurrence: {
        time: "1700",
        weekdays: [
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

virtual_machine_schedule = azure_native.devtestlab.VirtualMachineSchedule("virtualMachineSchedule",
    daily_recurrence=azure_native.devtestlab.DayDetailsArgs(
        time="1900",
    ),
    hourly_recurrence=azure_native.devtestlab.HourDetailsArgs(
        minute=30,
    ),
    lab_name="{labName}",
    location="{location}",
    name="LabVmsShutdown",
    notification_settings=azure_native.devtestlab.NotificationSettingsArgs(
        email_recipient="{email}",
        notification_locale="EN",
        status="Enabled",
        time_in_minutes=30,
        webhook_url="{webhookUrl}",
    ),
    resource_group_name="resourceGroupName",
    status="Enabled",
    tags={
        "tagName1": "tagValue1",
    },
    target_resource_id="/subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}/virtualMachines/{vmName}",
    task_type="LabVmsShutdownTask",
    time_zone_id="Pacific Standard Time",
    virtual_machine_name="{vmName}",
    weekly_recurrence=azure_native.devtestlab.WeekDetailsArgs(
        time="1700",
        weekdays=[
            "Friday",
            "Saturday",
            "Sunday",
        ],
    ))

```

```yaml
resources:
  virtualMachineSchedule:
    type: azure-native:devtestlab:VirtualMachineSchedule
    properties:
      dailyRecurrence:
        time: '1900'
      hourlyRecurrence:
        minute: 30
      labName: '{labName}'
      location: '{location}'
      name: LabVmsShutdown
      notificationSettings:
        emailRecipient: '{email}'
        notificationLocale: EN
        status: Enabled
        timeInMinutes: 30
        webhookUrl: '{webhookUrl}'
      resourceGroupName: resourceGroupName
      status: Enabled
      tags:
        tagName1: tagValue1
      targetResourceId: /subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}/virtualMachines/{vmName}
      taskType: LabVmsShutdownTask
      timeZoneId: Pacific Standard Time
      virtualMachineName: '{vmName}'
      weeklyRecurrence:
        time: '1700'
        weekdays:
          - Friday
          - Saturday
          - Sunday

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devtestlab:VirtualMachineSchedule LabVmsShutdown /subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}/virtualMachines/{vmName}/schedules/LabVmsShutdown 
```
