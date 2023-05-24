Scheduled action definition.
API Version: 2022-10-01.
Previous API Version: 2022-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateOrUpdatePrivateScheduledAction
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var scheduledAction = new AzureNative.CostManagement.ScheduledAction("scheduledAction", new()
    {
        DisplayName = "Monthly Cost By Resource",
        Kind = "Email",
        Name = "monthlyCostByResource",
        Notification = new AzureNative.CostManagement.Inputs.NotificationPropertiesArgs
        {
            Subject = "Cost by resource this month",
            To = new[]
            {
                "user@gmail.com",
                "team@gmail.com",
            },
        },
        Schedule = new AzureNative.CostManagement.Inputs.SchedulePropertiesArgs
        {
            DaysOfWeek = new[]
            {
                "Monday",
            },
            EndDate = "2021-06-19T22:21:51.1287144Z",
            Frequency = "Monthly",
            HourOfDay = 10,
            StartDate = "2020-06-19T22:21:51.1287144Z",
            WeeksOfMonth = new[]
            {
                "First",
                "Third",
            },
        },
        Status = "Enabled",
        ViewId = "/providers/Microsoft.CostManagement/views/swaggerExample",
    });

});


```

```go
package main

import (
	costmanagement "github.com/pulumi/pulumi-azure-native-sdk/costmanagement"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := costmanagement.NewScheduledAction(ctx, "scheduledAction", &costmanagement.ScheduledActionArgs{
			DisplayName: pulumi.String("Monthly Cost By Resource"),
			Kind:        pulumi.String("Email"),
			Name:        pulumi.String("monthlyCostByResource"),
			Notification: &costmanagement.NotificationPropertiesArgs{
				Subject: pulumi.String("Cost by resource this month"),
				To: pulumi.StringArray{
					pulumi.String("user@gmail.com"),
					pulumi.String("team@gmail.com"),
				},
			},
			Schedule: &costmanagement.SchedulePropertiesArgs{
				DaysOfWeek: pulumi.StringArray{
					pulumi.String("Monday"),
				},
				EndDate:   pulumi.String("2021-06-19T22:21:51.1287144Z"),
				Frequency: pulumi.String("Monthly"),
				HourOfDay: pulumi.Int(10),
				StartDate: pulumi.String("2020-06-19T22:21:51.1287144Z"),
				WeeksOfMonth: pulumi.StringArray{
					pulumi.String("First"),
					pulumi.String("Third"),
				},
			},
			Status: pulumi.String("Enabled"),
			ViewId: pulumi.String("/providers/Microsoft.CostManagement/views/swaggerExample"),
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
import com.pulumi.azurenative.costmanagement.ScheduledAction;
import com.pulumi.azurenative.costmanagement.ScheduledActionArgs;
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
        var scheduledAction = new ScheduledAction("scheduledAction", ScheduledActionArgs.builder()        
            .displayName("Monthly Cost By Resource")
            .kind("Email")
            .name("monthlyCostByResource")
            .notification(Map.ofEntries(
                Map.entry("subject", "Cost by resource this month"),
                Map.entry("to",                 
                    "user@gmail.com",
                    "team@gmail.com")
            ))
            .schedule(Map.ofEntries(
                Map.entry("daysOfWeek", "Monday"),
                Map.entry("endDate", "2021-06-19T22:21:51.1287144Z"),
                Map.entry("frequency", "Monthly"),
                Map.entry("hourOfDay", 10),
                Map.entry("startDate", "2020-06-19T22:21:51.1287144Z"),
                Map.entry("weeksOfMonth",                 
                    "First",
                    "Third")
            ))
            .status("Enabled")
            .viewId("/providers/Microsoft.CostManagement/views/swaggerExample")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const scheduledAction = new azure_native.costmanagement.ScheduledAction("scheduledAction", {
    displayName: "Monthly Cost By Resource",
    kind: "Email",
    name: "monthlyCostByResource",
    notification: {
        subject: "Cost by resource this month",
        to: [
            "user@gmail.com",
            "team@gmail.com",
        ],
    },
    schedule: {
        daysOfWeek: ["Monday"],
        endDate: "2021-06-19T22:21:51.1287144Z",
        frequency: "Monthly",
        hourOfDay: 10,
        startDate: "2020-06-19T22:21:51.1287144Z",
        weeksOfMonth: [
            "First",
            "Third",
        ],
    },
    status: "Enabled",
    viewId: "/providers/Microsoft.CostManagement/views/swaggerExample",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

scheduled_action = azure_native.costmanagement.ScheduledAction("scheduledAction",
    display_name="Monthly Cost By Resource",
    kind="Email",
    name="monthlyCostByResource",
    notification=azure_native.costmanagement.NotificationPropertiesArgs(
        subject="Cost by resource this month",
        to=[
            "user@gmail.com",
            "team@gmail.com",
        ],
    ),
    schedule=azure_native.costmanagement.SchedulePropertiesArgs(
        days_of_week=["Monday"],
        end_date="2021-06-19T22:21:51.1287144Z",
        frequency="Monthly",
        hour_of_day=10,
        start_date="2020-06-19T22:21:51.1287144Z",
        weeks_of_month=[
            "First",
            "Third",
        ],
    ),
    status="Enabled",
    view_id="/providers/Microsoft.CostManagement/views/swaggerExample")

```

```yaml
resources:
  scheduledAction:
    type: azure-native:costmanagement:ScheduledAction
    properties:
      displayName: Monthly Cost By Resource
      kind: Email
      name: monthlyCostByResource
      notification:
        subject: Cost by resource this month
        to:
          - user@gmail.com
          - team@gmail.com
      schedule:
        daysOfWeek:
          - Monday
        endDate: 2021-06-19T22:21:51.1287144Z
        frequency: Monthly
        hourOfDay: 10
        startDate: 2020-06-19T22:21:51.1287144Z
        weeksOfMonth:
          - First
          - Third
      status: Enabled
      viewId: /providers/Microsoft.CostManagement/views/swaggerExample

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:costmanagement:ScheduledAction monthlyCostByResource providers/Microsoft.CostManagement/scheduledActions/monthlyCostByResource 
```
