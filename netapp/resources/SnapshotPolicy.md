Snapshot policy information
API Version: 2022-09-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### SnapshotPolicies_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var snapshotPolicy = new AzureNative.NetApp.SnapshotPolicy("snapshotPolicy", new()
    {
        AccountName = "account1",
        DailySchedule = new AzureNative.NetApp.Inputs.DailyScheduleArgs
        {
            Hour = 14,
            Minute = 30,
            SnapshotsToKeep = 4,
        },
        Enabled = true,
        HourlySchedule = new AzureNative.NetApp.Inputs.HourlyScheduleArgs
        {
            Minute = 50,
            SnapshotsToKeep = 2,
        },
        Location = "eastus",
        MonthlySchedule = new AzureNative.NetApp.Inputs.MonthlyScheduleArgs
        {
            DaysOfMonth = "10,11,12",
            Hour = 14,
            Minute = 15,
            SnapshotsToKeep = 5,
        },
        ResourceGroupName = "myRG",
        SnapshotPolicyName = "snapshotPolicyName",
        WeeklySchedule = new AzureNative.NetApp.Inputs.WeeklyScheduleArgs
        {
            Day = "Wednesday",
            Hour = 14,
            Minute = 45,
            SnapshotsToKeep = 3,
        },
    });

});


```

```go
package main

import (
	netapp "github.com/pulumi/pulumi-azure-native-sdk/netapp"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := netapp.NewSnapshotPolicy(ctx, "snapshotPolicy", &netapp.SnapshotPolicyArgs{
			AccountName: pulumi.String("account1"),
			DailySchedule: &netapp.DailyScheduleArgs{
				Hour:            pulumi.Int(14),
				Minute:          pulumi.Int(30),
				SnapshotsToKeep: pulumi.Int(4),
			},
			Enabled: pulumi.Bool(true),
			HourlySchedule: &netapp.HourlyScheduleArgs{
				Minute:          pulumi.Int(50),
				SnapshotsToKeep: pulumi.Int(2),
			},
			Location: pulumi.String("eastus"),
			MonthlySchedule: &netapp.MonthlyScheduleArgs{
				DaysOfMonth:     pulumi.String("10,11,12"),
				Hour:            pulumi.Int(14),
				Minute:          pulumi.Int(15),
				SnapshotsToKeep: pulumi.Int(5),
			},
			ResourceGroupName:  pulumi.String("myRG"),
			SnapshotPolicyName: pulumi.String("snapshotPolicyName"),
			WeeklySchedule: &netapp.WeeklyScheduleArgs{
				Day:             pulumi.String("Wednesday"),
				Hour:            pulumi.Int(14),
				Minute:          pulumi.Int(45),
				SnapshotsToKeep: pulumi.Int(3),
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
import com.pulumi.azurenative.netapp.SnapshotPolicy;
import com.pulumi.azurenative.netapp.SnapshotPolicyArgs;
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
        var snapshotPolicy = new SnapshotPolicy("snapshotPolicy", SnapshotPolicyArgs.builder()        
            .accountName("account1")
            .dailySchedule(Map.ofEntries(
                Map.entry("hour", 14),
                Map.entry("minute", 30),
                Map.entry("snapshotsToKeep", 4)
            ))
            .enabled(true)
            .hourlySchedule(Map.ofEntries(
                Map.entry("minute", 50),
                Map.entry("snapshotsToKeep", 2)
            ))
            .location("eastus")
            .monthlySchedule(Map.ofEntries(
                Map.entry("daysOfMonth", "10,11,12"),
                Map.entry("hour", 14),
                Map.entry("minute", 15),
                Map.entry("snapshotsToKeep", 5)
            ))
            .resourceGroupName("myRG")
            .snapshotPolicyName("snapshotPolicyName")
            .weeklySchedule(Map.ofEntries(
                Map.entry("day", "Wednesday"),
                Map.entry("hour", 14),
                Map.entry("minute", 45),
                Map.entry("snapshotsToKeep", 3)
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const snapshotPolicy = new azure_native.netapp.SnapshotPolicy("snapshotPolicy", {
    accountName: "account1",
    dailySchedule: {
        hour: 14,
        minute: 30,
        snapshotsToKeep: 4,
    },
    enabled: true,
    hourlySchedule: {
        minute: 50,
        snapshotsToKeep: 2,
    },
    location: "eastus",
    monthlySchedule: {
        daysOfMonth: "10,11,12",
        hour: 14,
        minute: 15,
        snapshotsToKeep: 5,
    },
    resourceGroupName: "myRG",
    snapshotPolicyName: "snapshotPolicyName",
    weeklySchedule: {
        day: "Wednesday",
        hour: 14,
        minute: 45,
        snapshotsToKeep: 3,
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

snapshot_policy = azure_native.netapp.SnapshotPolicy("snapshotPolicy",
    account_name="account1",
    daily_schedule=azure_native.netapp.DailyScheduleArgs(
        hour=14,
        minute=30,
        snapshots_to_keep=4,
    ),
    enabled=True,
    hourly_schedule=azure_native.netapp.HourlyScheduleArgs(
        minute=50,
        snapshots_to_keep=2,
    ),
    location="eastus",
    monthly_schedule=azure_native.netapp.MonthlyScheduleArgs(
        days_of_month="10,11,12",
        hour=14,
        minute=15,
        snapshots_to_keep=5,
    ),
    resource_group_name="myRG",
    snapshot_policy_name="snapshotPolicyName",
    weekly_schedule=azure_native.netapp.WeeklyScheduleArgs(
        day="Wednesday",
        hour=14,
        minute=45,
        snapshots_to_keep=3,
    ))

```

```yaml
resources:
  snapshotPolicy:
    type: azure-native:netapp:SnapshotPolicy
    properties:
      accountName: account1
      dailySchedule:
        hour: 14
        minute: 30
        snapshotsToKeep: 4
      enabled: true
      hourlySchedule:
        minute: 50
        snapshotsToKeep: 2
      location: eastus
      monthlySchedule:
        daysOfMonth: 10,11,12
        hour: 14
        minute: 15
        snapshotsToKeep: 5
      resourceGroupName: myRG
      snapshotPolicyName: snapshotPolicyName
      weeklySchedule:
        day: Wednesday
        hour: 14
        minute: 45
        snapshotsToKeep: 3

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:netapp:SnapshotPolicy account1/snapshotPolicy1 /subscriptions/D633CC2E-722B-4AE1-B636-BBD9E4C60ED9/resourceGroups/myRG/providers/Microsoft.NetApp/netAppAccounts/account1/snapshotPolicies/snapshotPolicy1 
```
