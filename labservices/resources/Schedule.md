Schedule for automatically turning virtual machines in a lab on and off at specified times.
API Version: 2022-08-01.
Previous API Version: 2021-10-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### putSchedule
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var schedule = new AzureNative.LabServices.Schedule("schedule", new()
    {
        LabName = "testlab",
        Notes = "Schedule 1 for students",
        RecurrencePattern = new AzureNative.LabServices.Inputs.RecurrencePatternArgs
        {
            ExpirationDate = "2020-08-14T23:59:59Z",
            Frequency = AzureNative.LabServices.RecurrenceFrequency.Daily,
            Interval = 2,
        },
        ResourceGroupName = "testrg123",
        ScheduleName = "schedule1",
        StartAt = "2020-05-26T12:00:00Z",
        StopAt = "2020-05-26T18:00:00Z",
        TimeZoneId = "America/Los_Angeles",
    });

});


```

```go
package main

import (
	labservices "github.com/pulumi/pulumi-azure-native-sdk/labservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := labservices.NewSchedule(ctx, "schedule", &labservices.ScheduleArgs{
			LabName: pulumi.String("testlab"),
			Notes:   pulumi.String("Schedule 1 for students"),
			RecurrencePattern: &labservices.RecurrencePatternArgs{
				ExpirationDate: pulumi.String("2020-08-14T23:59:59Z"),
				Frequency:      labservices.RecurrenceFrequencyDaily,
				Interval:       pulumi.Int(2),
			},
			ResourceGroupName: pulumi.String("testrg123"),
			ScheduleName:      pulumi.String("schedule1"),
			StartAt:           pulumi.String("2020-05-26T12:00:00Z"),
			StopAt:            pulumi.String("2020-05-26T18:00:00Z"),
			TimeZoneId:        pulumi.String("America/Los_Angeles"),
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
import com.pulumi.azurenative.labservices.Schedule;
import com.pulumi.azurenative.labservices.ScheduleArgs;
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
            .labName("testlab")
            .notes("Schedule 1 for students")
            .recurrencePattern(Map.ofEntries(
                Map.entry("expirationDate", "2020-08-14T23:59:59Z"),
                Map.entry("frequency", "Daily"),
                Map.entry("interval", 2)
            ))
            .resourceGroupName("testrg123")
            .scheduleName("schedule1")
            .startAt("2020-05-26T12:00:00Z")
            .stopAt("2020-05-26T18:00:00Z")
            .timeZoneId("America/Los_Angeles")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const schedule = new azure_native.labservices.Schedule("schedule", {
    labName: "testlab",
    notes: "Schedule 1 for students",
    recurrencePattern: {
        expirationDate: "2020-08-14T23:59:59Z",
        frequency: azure_native.labservices.RecurrenceFrequency.Daily,
        interval: 2,
    },
    resourceGroupName: "testrg123",
    scheduleName: "schedule1",
    startAt: "2020-05-26T12:00:00Z",
    stopAt: "2020-05-26T18:00:00Z",
    timeZoneId: "America/Los_Angeles",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

schedule = azure_native.labservices.Schedule("schedule",
    lab_name="testlab",
    notes="Schedule 1 for students",
    recurrence_pattern=azure_native.labservices.RecurrencePatternArgs(
        expiration_date="2020-08-14T23:59:59Z",
        frequency=azure_native.labservices.RecurrenceFrequency.DAILY,
        interval=2,
    ),
    resource_group_name="testrg123",
    schedule_name="schedule1",
    start_at="2020-05-26T12:00:00Z",
    stop_at="2020-05-26T18:00:00Z",
    time_zone_id="America/Los_Angeles")

```

```yaml
resources:
  schedule:
    type: azure-native:labservices:Schedule
    properties:
      labName: testlab
      notes: Schedule 1 for students
      recurrencePattern:
        expirationDate: 2020-08-14T23:59:59Z
        frequency: Daily
        interval: 2
      resourceGroupName: testrg123
      scheduleName: schedule1
      startAt: 2020-05-26T12:00:00Z
      stopAt: 2020-05-26T18:00:00Z
      timeZoneId: America/Los_Angeles

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:labservices:Schedule schedule1 /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.LabServices/labs/testlab/schedules/schedule1 
```
