The backup schedule.
API Version: 2017-06-01.
Previous API Version: 2017-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### BackupSchedulesCreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var backupSchedule = new AzureNative.StorSimple.BackupSchedule("backupSchedule", new()
    {
        BackupPolicyName = "BkUpPolicy01ForSDKTest",
        BackupScheduleName = "schedule2",
        BackupType = AzureNative.StorSimple.BackupType.CloudSnapshot,
        DeviceName = "Device05ForSDKTest",
        Kind = AzureNative.StorSimple.Kind.Series8000,
        ManagerName = "ManagerForSDKTest1",
        ResourceGroupName = "ResourceGroupForSDKTest",
        RetentionCount = 1,
        ScheduleRecurrence = new AzureNative.StorSimple.Inputs.ScheduleRecurrenceArgs
        {
            RecurrenceType = AzureNative.StorSimple.RecurrenceType.Weekly,
            RecurrenceValue = 1,
            WeeklyDaysList = new[]
            {
                AzureNative.StorSimple.DayOfWeek.Friday,
                AzureNative.StorSimple.DayOfWeek.Thursday,
                AzureNative.StorSimple.DayOfWeek.Monday,
            },
        },
        ScheduleStatus = AzureNative.StorSimple.ScheduleStatus.Enabled,
        StartTime = "2017-06-24T01:00:00Z",
    });

});


```

```go
package main

import (
	storsimple "github.com/pulumi/pulumi-azure-native-sdk/storsimple"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := storsimple.NewBackupSchedule(ctx, "backupSchedule", &storsimple.BackupScheduleArgs{
			BackupPolicyName:   pulumi.String("BkUpPolicy01ForSDKTest"),
			BackupScheduleName: pulumi.String("schedule2"),
			BackupType:         storsimple.BackupTypeCloudSnapshot,
			DeviceName:         pulumi.String("Device05ForSDKTest"),
			Kind:               storsimple.KindSeries8000,
			ManagerName:        pulumi.String("ManagerForSDKTest1"),
			ResourceGroupName:  pulumi.String("ResourceGroupForSDKTest"),
			RetentionCount:     pulumi.Float64(1),
			ScheduleRecurrence: &storsimple.ScheduleRecurrenceArgs{
				RecurrenceType:  storsimple.RecurrenceTypeWeekly,
				RecurrenceValue: pulumi.Int(1),
				WeeklyDaysList: storsimple.DayOfWeekArray{
					storsimple.DayOfWeekFriday,
					storsimple.DayOfWeekThursday,
					storsimple.DayOfWeekMonday,
				},
			},
			ScheduleStatus: storsimple.ScheduleStatusEnabled,
			StartTime:      pulumi.String("2017-06-24T01:00:00Z"),
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
import com.pulumi.azurenative.storsimple.BackupSchedule;
import com.pulumi.azurenative.storsimple.BackupScheduleArgs;
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
        var backupSchedule = new BackupSchedule("backupSchedule", BackupScheduleArgs.builder()        
            .backupPolicyName("BkUpPolicy01ForSDKTest")
            .backupScheduleName("schedule2")
            .backupType("CloudSnapshot")
            .deviceName("Device05ForSDKTest")
            .kind("Series8000")
            .managerName("ManagerForSDKTest1")
            .resourceGroupName("ResourceGroupForSDKTest")
            .retentionCount(1)
            .scheduleRecurrence(Map.ofEntries(
                Map.entry("recurrenceType", "Weekly"),
                Map.entry("recurrenceValue", 1),
                Map.entry("weeklyDaysList",                 
                    "Friday",
                    "Thursday",
                    "Monday")
            ))
            .scheduleStatus("Enabled")
            .startTime("2017-06-24T01:00:00Z")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const backupSchedule = new azure_native.storsimple.BackupSchedule("backupSchedule", {
    backupPolicyName: "BkUpPolicy01ForSDKTest",
    backupScheduleName: "schedule2",
    backupType: azure_native.storsimple.BackupType.CloudSnapshot,
    deviceName: "Device05ForSDKTest",
    kind: azure_native.storsimple.Kind.Series8000,
    managerName: "ManagerForSDKTest1",
    resourceGroupName: "ResourceGroupForSDKTest",
    retentionCount: 1,
    scheduleRecurrence: {
        recurrenceType: azure_native.storsimple.RecurrenceType.Weekly,
        recurrenceValue: 1,
        weeklyDaysList: [
            azure_native.storsimple.DayOfWeek.Friday,
            azure_native.storsimple.DayOfWeek.Thursday,
            azure_native.storsimple.DayOfWeek.Monday,
        ],
    },
    scheduleStatus: azure_native.storsimple.ScheduleStatus.Enabled,
    startTime: "2017-06-24T01:00:00Z",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

backup_schedule = azure_native.storsimple.BackupSchedule("backupSchedule",
    backup_policy_name="BkUpPolicy01ForSDKTest",
    backup_schedule_name="schedule2",
    backup_type=azure_native.storsimple.BackupType.CLOUD_SNAPSHOT,
    device_name="Device05ForSDKTest",
    kind=azure_native.storsimple.Kind.SERIES8000,
    manager_name="ManagerForSDKTest1",
    resource_group_name="ResourceGroupForSDKTest",
    retention_count=1,
    schedule_recurrence=azure_native.storsimple.ScheduleRecurrenceArgs(
        recurrence_type=azure_native.storsimple.RecurrenceType.WEEKLY,
        recurrence_value=1,
        weekly_days_list=[
            azure_native.storsimple.DayOfWeek.FRIDAY,
            azure_native.storsimple.DayOfWeek.THURSDAY,
            azure_native.storsimple.DayOfWeek.MONDAY,
        ],
    ),
    schedule_status=azure_native.storsimple.ScheduleStatus.ENABLED,
    start_time="2017-06-24T01:00:00Z")

```

```yaml
resources:
  backupSchedule:
    type: azure-native:storsimple:BackupSchedule
    properties:
      backupPolicyName: BkUpPolicy01ForSDKTest
      backupScheduleName: schedule2
      backupType: CloudSnapshot
      deviceName: Device05ForSDKTest
      kind: Series8000
      managerName: ManagerForSDKTest1
      resourceGroupName: ResourceGroupForSDKTest
      retentionCount: 1
      scheduleRecurrence:
        recurrenceType: Weekly
        recurrenceValue: 1
        weeklyDaysList:
          - Friday
          - Thursday
          - Monday
      scheduleStatus: Enabled
      startTime: 2017-06-24T01:00:00Z

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:storsimple:BackupSchedule schedule2 /subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.StorSimple/managers/ManagerForSDKTest1/devices/Device05ForSDKTest/backupPolicies/BkUpPolicy01ForSDKTest/schedules/schedule2 
```
