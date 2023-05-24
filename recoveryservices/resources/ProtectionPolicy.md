Base class for backup policy. Workload-specific backup policies are derived from this class.
API Version: 2023-02-01.
Previous API Version: 2021-02-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or Update Daily Azure Storage Protection Policy
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var protectionPolicy = new AzureNative.RecoveryServices.ProtectionPolicy("protectionPolicy", new()
    {
        PolicyName = "dailyPolicy2",
        Properties = new AzureNative.RecoveryServices.Inputs.AzureFileShareProtectionPolicyArgs
        {
            BackupManagementType = "AzureStorage",
            RetentionPolicy = new AzureNative.RecoveryServices.Inputs.LongTermRetentionPolicyArgs
            {
                DailySchedule = new AzureNative.RecoveryServices.Inputs.DailyRetentionScheduleArgs
                {
                    RetentionDuration = new AzureNative.RecoveryServices.Inputs.RetentionDurationArgs
                    {
                        Count = 5,
                        DurationType = "Days",
                    },
                    RetentionTimes = new[]
                    {
                        "2021-09-29T08:00:00.000Z",
                    },
                },
                MonthlySchedule = new AzureNative.RecoveryServices.Inputs.MonthlyRetentionScheduleArgs
                {
                    RetentionDuration = new AzureNative.RecoveryServices.Inputs.RetentionDurationArgs
                    {
                        Count = 60,
                        DurationType = "Months",
                    },
                    RetentionScheduleFormatType = "Weekly",
                    RetentionScheduleWeekly = new AzureNative.RecoveryServices.Inputs.WeeklyRetentionFormatArgs
                    {
                        DaysOfTheWeek = new[]
                        {
                            AzureNative.RecoveryServices.DayOfWeek.Sunday,
                        },
                        WeeksOfTheMonth = new[]
                        {
                            AzureNative.RecoveryServices.WeekOfMonth.First,
                        },
                    },
                    RetentionTimes = new[]
                    {
                        "2021-09-29T08:00:00.000Z",
                    },
                },
                RetentionPolicyType = "LongTermRetentionPolicy",
                WeeklySchedule = new AzureNative.RecoveryServices.Inputs.WeeklyRetentionScheduleArgs
                {
                    DaysOfTheWeek = new[]
                    {
                        AzureNative.RecoveryServices.DayOfWeek.Sunday,
                    },
                    RetentionDuration = new AzureNative.RecoveryServices.Inputs.RetentionDurationArgs
                    {
                        Count = 12,
                        DurationType = "Weeks",
                    },
                    RetentionTimes = new[]
                    {
                        "2021-09-29T08:00:00.000Z",
                    },
                },
                YearlySchedule = new AzureNative.RecoveryServices.Inputs.YearlyRetentionScheduleArgs
                {
                    MonthsOfYear = new[]
                    {
                        AzureNative.RecoveryServices.MonthOfYear.January,
                    },
                    RetentionDuration = new AzureNative.RecoveryServices.Inputs.RetentionDurationArgs
                    {
                        Count = 10,
                        DurationType = "Years",
                    },
                    RetentionScheduleFormatType = "Weekly",
                    RetentionScheduleWeekly = new AzureNative.RecoveryServices.Inputs.WeeklyRetentionFormatArgs
                    {
                        DaysOfTheWeek = new[]
                        {
                            AzureNative.RecoveryServices.DayOfWeek.Sunday,
                        },
                        WeeksOfTheMonth = new[]
                        {
                            AzureNative.RecoveryServices.WeekOfMonth.First,
                        },
                    },
                    RetentionTimes = new[]
                    {
                        "2021-09-29T08:00:00.000Z",
                    },
                },
            },
            SchedulePolicy = new AzureNative.RecoveryServices.Inputs.SimpleSchedulePolicyArgs
            {
                SchedulePolicyType = "SimpleSchedulePolicy",
                ScheduleRunFrequency = "Daily",
                ScheduleRunTimes = new[]
                {
                    "2021-09-29T08:00:00.000Z",
                },
            },
            TimeZone = "UTC",
            WorkLoadType = "AzureFileShare",
        },
        ResourceGroupName = "SwaggerTestRg",
        VaultName = "swaggertestvault",
    });

});


```

```go
package main

import (
	recoveryservices "github.com/pulumi/pulumi-azure-native-sdk/recoveryservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := recoveryservices.NewProtectionPolicy(ctx, "protectionPolicy", &recoveryservices.ProtectionPolicyArgs{
			PolicyName: pulumi.String("dailyPolicy2"),
			Properties: recoveryservices.AzureFileShareProtectionPolicy{
				BackupManagementType: "AzureStorage",
				RetentionPolicy: recoveryservices.LongTermRetentionPolicy{
					DailySchedule: recoveryservices.DailyRetentionSchedule{
						RetentionDuration: recoveryservices.RetentionDuration{
							Count:        5,
							DurationType: "Days",
						},
						RetentionTimes: []string{
							"2021-09-29T08:00:00.000Z",
						},
					},
					MonthlySchedule: recoveryservices.MonthlyRetentionSchedule{
						RetentionDuration: recoveryservices.RetentionDuration{
							Count:        60,
							DurationType: "Months",
						},
						RetentionScheduleFormatType: "Weekly",
						RetentionScheduleWeekly: recoveryservices.WeeklyRetentionFormat{
							DaysOfTheWeek: []recoveryservices.DayOfWeek{
								recoveryservices.DayOfWeekSunday,
							},
							WeeksOfTheMonth: []recoveryservices.WeekOfMonth{
								recoveryservices.WeekOfMonthFirst,
							},
						},
						RetentionTimes: []string{
							"2021-09-29T08:00:00.000Z",
						},
					},
					RetentionPolicyType: "LongTermRetentionPolicy",
					WeeklySchedule: recoveryservices.WeeklyRetentionSchedule{
						DaysOfTheWeek: []recoveryservices.DayOfWeek{
							recoveryservices.DayOfWeekSunday,
						},
						RetentionDuration: recoveryservices.RetentionDuration{
							Count:        12,
							DurationType: "Weeks",
						},
						RetentionTimes: []string{
							"2021-09-29T08:00:00.000Z",
						},
					},
					YearlySchedule: recoveryservices.YearlyRetentionSchedule{
						MonthsOfYear: []recoveryservices.MonthOfYear{
							recoveryservices.MonthOfYearJanuary,
						},
						RetentionDuration: recoveryservices.RetentionDuration{
							Count:        10,
							DurationType: "Years",
						},
						RetentionScheduleFormatType: "Weekly",
						RetentionScheduleWeekly: recoveryservices.WeeklyRetentionFormat{
							DaysOfTheWeek: []recoveryservices.DayOfWeek{
								recoveryservices.DayOfWeekSunday,
							},
							WeeksOfTheMonth: []recoveryservices.WeekOfMonth{
								recoveryservices.WeekOfMonthFirst,
							},
						},
						RetentionTimes: []string{
							"2021-09-29T08:00:00.000Z",
						},
					},
				},
				SchedulePolicy: recoveryservices.SimpleSchedulePolicy{
					SchedulePolicyType:   "SimpleSchedulePolicy",
					ScheduleRunFrequency: "Daily",
					ScheduleRunTimes: []string{
						"2021-09-29T08:00:00.000Z",
					},
				},
				TimeZone:     "UTC",
				WorkLoadType: "AzureFileShare",
			},
			ResourceGroupName: pulumi.String("SwaggerTestRg"),
			VaultName:         pulumi.String("swaggertestvault"),
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
import com.pulumi.azurenative.recoveryservices.ProtectionPolicy;
import com.pulumi.azurenative.recoveryservices.ProtectionPolicyArgs;
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
        var protectionPolicy = new ProtectionPolicy("protectionPolicy", ProtectionPolicyArgs.builder()        
            .policyName("dailyPolicy2")
            .properties(Map.ofEntries(
                Map.entry("backupManagementType", "AzureStorage"),
                Map.entry("retentionPolicy", Map.ofEntries(
                    Map.entry("dailySchedule", Map.ofEntries(
                        Map.entry("retentionDuration", Map.ofEntries(
                            Map.entry("count", 5),
                            Map.entry("durationType", "Days")
                        )),
                        Map.entry("retentionTimes", "2021-09-29T08:00:00.000Z")
                    )),
                    Map.entry("monthlySchedule", Map.ofEntries(
                        Map.entry("retentionDuration", Map.ofEntries(
                            Map.entry("count", 60),
                            Map.entry("durationType", "Months")
                        )),
                        Map.entry("retentionScheduleFormatType", "Weekly"),
                        Map.entry("retentionScheduleWeekly", Map.ofEntries(
                            Map.entry("daysOfTheWeek", "Sunday"),
                            Map.entry("weeksOfTheMonth", "First")
                        )),
                        Map.entry("retentionTimes", "2021-09-29T08:00:00.000Z")
                    )),
                    Map.entry("retentionPolicyType", "LongTermRetentionPolicy"),
                    Map.entry("weeklySchedule", Map.ofEntries(
                        Map.entry("daysOfTheWeek", "Sunday"),
                        Map.entry("retentionDuration", Map.ofEntries(
                            Map.entry("count", 12),
                            Map.entry("durationType", "Weeks")
                        )),
                        Map.entry("retentionTimes", "2021-09-29T08:00:00.000Z")
                    )),
                    Map.entry("yearlySchedule", Map.ofEntries(
                        Map.entry("monthsOfYear", "January"),
                        Map.entry("retentionDuration", Map.ofEntries(
                            Map.entry("count", 10),
                            Map.entry("durationType", "Years")
                        )),
                        Map.entry("retentionScheduleFormatType", "Weekly"),
                        Map.entry("retentionScheduleWeekly", Map.ofEntries(
                            Map.entry("daysOfTheWeek", "Sunday"),
                            Map.entry("weeksOfTheMonth", "First")
                        )),
                        Map.entry("retentionTimes", "2021-09-29T08:00:00.000Z")
                    ))
                )),
                Map.entry("schedulePolicy", Map.ofEntries(
                    Map.entry("schedulePolicyType", "SimpleSchedulePolicy"),
                    Map.entry("scheduleRunFrequency", "Daily"),
                    Map.entry("scheduleRunTimes", "2021-09-29T08:00:00.000Z")
                )),
                Map.entry("timeZone", "UTC"),
                Map.entry("workLoadType", "AzureFileShare")
            ))
            .resourceGroupName("SwaggerTestRg")
            .vaultName("swaggertestvault")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const protectionPolicy = new azure_native.recoveryservices.ProtectionPolicy("protectionPolicy", {
    policyName: "dailyPolicy2",
    properties: {
        backupManagementType: "AzureStorage",
        retentionPolicy: {
            dailySchedule: {
                retentionDuration: {
                    count: 5,
                    durationType: "Days",
                },
                retentionTimes: ["2021-09-29T08:00:00.000Z"],
            },
            monthlySchedule: {
                retentionDuration: {
                    count: 60,
                    durationType: "Months",
                },
                retentionScheduleFormatType: "Weekly",
                retentionScheduleWeekly: {
                    daysOfTheWeek: [azure_native.recoveryservices.DayOfWeek.Sunday],
                    weeksOfTheMonth: [azure_native.recoveryservices.WeekOfMonth.First],
                },
                retentionTimes: ["2021-09-29T08:00:00.000Z"],
            },
            retentionPolicyType: "LongTermRetentionPolicy",
            weeklySchedule: {
                daysOfTheWeek: [azure_native.recoveryservices.DayOfWeek.Sunday],
                retentionDuration: {
                    count: 12,
                    durationType: "Weeks",
                },
                retentionTimes: ["2021-09-29T08:00:00.000Z"],
            },
            yearlySchedule: {
                monthsOfYear: [azure_native.recoveryservices.MonthOfYear.January],
                retentionDuration: {
                    count: 10,
                    durationType: "Years",
                },
                retentionScheduleFormatType: "Weekly",
                retentionScheduleWeekly: {
                    daysOfTheWeek: [azure_native.recoveryservices.DayOfWeek.Sunday],
                    weeksOfTheMonth: [azure_native.recoveryservices.WeekOfMonth.First],
                },
                retentionTimes: ["2021-09-29T08:00:00.000Z"],
            },
        },
        schedulePolicy: {
            schedulePolicyType: "SimpleSchedulePolicy",
            scheduleRunFrequency: "Daily",
            scheduleRunTimes: ["2021-09-29T08:00:00.000Z"],
        },
        timeZone: "UTC",
        workLoadType: "AzureFileShare",
    },
    resourceGroupName: "SwaggerTestRg",
    vaultName: "swaggertestvault",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

protection_policy = azure_native.recoveryservices.ProtectionPolicy("protectionPolicy",
    policy_name="dailyPolicy2",
    properties=azure_native.recoveryservices.AzureFileShareProtectionPolicyArgs(
        backup_management_type="AzureStorage",
        retention_policy=azure_native.recoveryservices.LongTermRetentionPolicyArgs(
            daily_schedule=azure_native.recoveryservices.DailyRetentionScheduleArgs(
                retention_duration=azure_native.recoveryservices.RetentionDurationArgs(
                    count=5,
                    duration_type="Days",
                ),
                retention_times=["2021-09-29T08:00:00.000Z"],
            ),
            monthly_schedule=azure_native.recoveryservices.MonthlyRetentionScheduleArgs(
                retention_duration=azure_native.recoveryservices.RetentionDurationArgs(
                    count=60,
                    duration_type="Months",
                ),
                retention_schedule_format_type="Weekly",
                retention_schedule_weekly=azure_native.recoveryservices.WeeklyRetentionFormatArgs(
                    days_of_the_week=[azure_native.recoveryservices.DayOfWeek.SUNDAY],
                    weeks_of_the_month=[azure_native.recoveryservices.WeekOfMonth.FIRST],
                ),
                retention_times=["2021-09-29T08:00:00.000Z"],
            ),
            retention_policy_type="LongTermRetentionPolicy",
            weekly_schedule=azure_native.recoveryservices.WeeklyRetentionScheduleArgs(
                days_of_the_week=[azure_native.recoveryservices.DayOfWeek.SUNDAY],
                retention_duration=azure_native.recoveryservices.RetentionDurationArgs(
                    count=12,
                    duration_type="Weeks",
                ),
                retention_times=["2021-09-29T08:00:00.000Z"],
            ),
            yearly_schedule=azure_native.recoveryservices.YearlyRetentionScheduleArgs(
                months_of_year=[azure_native.recoveryservices.MonthOfYear.JANUARY],
                retention_duration=azure_native.recoveryservices.RetentionDurationArgs(
                    count=10,
                    duration_type="Years",
                ),
                retention_schedule_format_type="Weekly",
                retention_schedule_weekly=azure_native.recoveryservices.WeeklyRetentionFormatArgs(
                    days_of_the_week=[azure_native.recoveryservices.DayOfWeek.SUNDAY],
                    weeks_of_the_month=[azure_native.recoveryservices.WeekOfMonth.FIRST],
                ),
                retention_times=["2021-09-29T08:00:00.000Z"],
            ),
        ),
        schedule_policy=azure_native.recoveryservices.SimpleSchedulePolicyArgs(
            schedule_policy_type="SimpleSchedulePolicy",
            schedule_run_frequency="Daily",
            schedule_run_times=["2021-09-29T08:00:00.000Z"],
        ),
        time_zone="UTC",
        work_load_type="AzureFileShare",
    ),
    resource_group_name="SwaggerTestRg",
    vault_name="swaggertestvault")

```

```yaml
resources:
  protectionPolicy:
    type: azure-native:recoveryservices:ProtectionPolicy
    properties:
      policyName: dailyPolicy2
      properties:
        backupManagementType: AzureStorage
        retentionPolicy:
          dailySchedule:
            retentionDuration:
              count: 5
              durationType: Days
            retentionTimes:
              - 2021-09-29T08:00:00.000Z
          monthlySchedule:
            retentionDuration:
              count: 60
              durationType: Months
            retentionScheduleFormatType: Weekly
            retentionScheduleWeekly:
              daysOfTheWeek:
                - Sunday
              weeksOfTheMonth:
                - First
            retentionTimes:
              - 2021-09-29T08:00:00.000Z
          retentionPolicyType: LongTermRetentionPolicy
          weeklySchedule:
            daysOfTheWeek:
              - Sunday
            retentionDuration:
              count: 12
              durationType: Weeks
            retentionTimes:
              - 2021-09-29T08:00:00.000Z
          yearlySchedule:
            monthsOfYear:
              - January
            retentionDuration:
              count: 10
              durationType: Years
            retentionScheduleFormatType: Weekly
            retentionScheduleWeekly:
              daysOfTheWeek:
                - Sunday
              weeksOfTheMonth:
                - First
            retentionTimes:
              - 2021-09-29T08:00:00.000Z
        schedulePolicy:
          schedulePolicyType: SimpleSchedulePolicy
          scheduleRunFrequency: Daily
          scheduleRunTimes:
            - 2021-09-29T08:00:00.000Z
        timeZone: UTC
        workLoadType: AzureFileShare
      resourceGroupName: SwaggerTestRg
      vaultName: swaggertestvault

```

{{% /example %}}
{{% example %}}
### Create or Update Enhanced Azure Vm Protection Policy with Hourly backup
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var protectionPolicy = new AzureNative.RecoveryServices.ProtectionPolicy("protectionPolicy", new()
    {
        PolicyName = "v2-daily-sample",
        Properties = new AzureNative.RecoveryServices.Inputs.AzureIaaSVMProtectionPolicyArgs
        {
            BackupManagementType = "AzureIaasVM",
            InstantRpRetentionRangeInDays = 30,
            PolicyType = "V2",
            RetentionPolicy = new AzureNative.RecoveryServices.Inputs.LongTermRetentionPolicyArgs
            {
                DailySchedule = new AzureNative.RecoveryServices.Inputs.DailyRetentionScheduleArgs
                {
                    RetentionDuration = new AzureNative.RecoveryServices.Inputs.RetentionDurationArgs
                    {
                        Count = 180,
                        DurationType = "Days",
                    },
                    RetentionTimes = new[]
                    {
                        "2021-12-17T08:00:00+00:00",
                    },
                },
                MonthlySchedule = new AzureNative.RecoveryServices.Inputs.MonthlyRetentionScheduleArgs
                {
                    RetentionDuration = new AzureNative.RecoveryServices.Inputs.RetentionDurationArgs
                    {
                        Count = 60,
                        DurationType = "Months",
                    },
                    RetentionScheduleFormatType = "Weekly",
                    RetentionScheduleWeekly = new AzureNative.RecoveryServices.Inputs.WeeklyRetentionFormatArgs
                    {
                        DaysOfTheWeek = new[]
                        {
                            AzureNative.RecoveryServices.DayOfWeek.Sunday,
                        },
                        WeeksOfTheMonth = new[]
                        {
                            AzureNative.RecoveryServices.WeekOfMonth.First,
                        },
                    },
                    RetentionTimes = new[]
                    {
                        "2021-12-17T08:00:00+00:00",
                    },
                },
                RetentionPolicyType = "LongTermRetentionPolicy",
                WeeklySchedule = new AzureNative.RecoveryServices.Inputs.WeeklyRetentionScheduleArgs
                {
                    DaysOfTheWeek = new[]
                    {
                        AzureNative.RecoveryServices.DayOfWeek.Sunday,
                    },
                    RetentionDuration = new AzureNative.RecoveryServices.Inputs.RetentionDurationArgs
                    {
                        Count = 12,
                        DurationType = "Weeks",
                    },
                    RetentionTimes = new[]
                    {
                        "2021-12-17T08:00:00+00:00",
                    },
                },
                YearlySchedule = new AzureNative.RecoveryServices.Inputs.YearlyRetentionScheduleArgs
                {
                    MonthsOfYear = new[]
                    {
                        AzureNative.RecoveryServices.MonthOfYear.January,
                    },
                    RetentionDuration = new AzureNative.RecoveryServices.Inputs.RetentionDurationArgs
                    {
                        Count = 10,
                        DurationType = "Years",
                    },
                    RetentionScheduleFormatType = "Weekly",
                    RetentionScheduleWeekly = new AzureNative.RecoveryServices.Inputs.WeeklyRetentionFormatArgs
                    {
                        DaysOfTheWeek = new[]
                        {
                            AzureNative.RecoveryServices.DayOfWeek.Sunday,
                        },
                        WeeksOfTheMonth = new[]
                        {
                            AzureNative.RecoveryServices.WeekOfMonth.First,
                        },
                    },
                    RetentionTimes = new[]
                    {
                        "2021-12-17T08:00:00+00:00",
                    },
                },
            },
            SchedulePolicy = new AzureNative.RecoveryServices.Inputs.SimpleSchedulePolicyV2Args
            {
                HourlySchedule = new AzureNative.RecoveryServices.Inputs.HourlyScheduleArgs
                {
                    Interval = 4,
                    ScheduleWindowDuration = 16,
                    ScheduleWindowStartTime = "2021-12-17T08:00:00Z",
                },
                SchedulePolicyType = "SimpleSchedulePolicyV2",
                ScheduleRunFrequency = "Hourly",
            },
            TimeZone = "India Standard Time",
        },
        ResourceGroupName = "SwaggerTestRg",
        VaultName = "NetSDKTestRsVault",
    });

});


```

```go
package main

import (
	recoveryservices "github.com/pulumi/pulumi-azure-native-sdk/recoveryservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := recoveryservices.NewProtectionPolicy(ctx, "protectionPolicy", &recoveryservices.ProtectionPolicyArgs{
			PolicyName: pulumi.String("v2-daily-sample"),
			Properties: recoveryservices.AzureIaaSVMProtectionPolicy{
				BackupManagementType:          "AzureIaasVM",
				InstantRpRetentionRangeInDays: 30,
				PolicyType:                    "V2",
				RetentionPolicy: recoveryservices.LongTermRetentionPolicy{
					DailySchedule: recoveryservices.DailyRetentionSchedule{
						RetentionDuration: recoveryservices.RetentionDuration{
							Count:        180,
							DurationType: "Days",
						},
						RetentionTimes: []string{
							"2021-12-17T08:00:00+00:00",
						},
					},
					MonthlySchedule: recoveryservices.MonthlyRetentionSchedule{
						RetentionDuration: recoveryservices.RetentionDuration{
							Count:        60,
							DurationType: "Months",
						},
						RetentionScheduleFormatType: "Weekly",
						RetentionScheduleWeekly: recoveryservices.WeeklyRetentionFormat{
							DaysOfTheWeek: []recoveryservices.DayOfWeek{
								recoveryservices.DayOfWeekSunday,
							},
							WeeksOfTheMonth: []recoveryservices.WeekOfMonth{
								recoveryservices.WeekOfMonthFirst,
							},
						},
						RetentionTimes: []string{
							"2021-12-17T08:00:00+00:00",
						},
					},
					RetentionPolicyType: "LongTermRetentionPolicy",
					WeeklySchedule: recoveryservices.WeeklyRetentionSchedule{
						DaysOfTheWeek: []recoveryservices.DayOfWeek{
							recoveryservices.DayOfWeekSunday,
						},
						RetentionDuration: recoveryservices.RetentionDuration{
							Count:        12,
							DurationType: "Weeks",
						},
						RetentionTimes: []string{
							"2021-12-17T08:00:00+00:00",
						},
					},
					YearlySchedule: recoveryservices.YearlyRetentionSchedule{
						MonthsOfYear: []recoveryservices.MonthOfYear{
							recoveryservices.MonthOfYearJanuary,
						},
						RetentionDuration: recoveryservices.RetentionDuration{
							Count:        10,
							DurationType: "Years",
						},
						RetentionScheduleFormatType: "Weekly",
						RetentionScheduleWeekly: recoveryservices.WeeklyRetentionFormat{
							DaysOfTheWeek: []recoveryservices.DayOfWeek{
								recoveryservices.DayOfWeekSunday,
							},
							WeeksOfTheMonth: []recoveryservices.WeekOfMonth{
								recoveryservices.WeekOfMonthFirst,
							},
						},
						RetentionTimes: []string{
							"2021-12-17T08:00:00+00:00",
						},
					},
				},
				SchedulePolicy: recoveryservices.SimpleSchedulePolicyV2{
					HourlySchedule: recoveryservices.HourlySchedule{
						Interval:                4,
						ScheduleWindowDuration:  16,
						ScheduleWindowStartTime: "2021-12-17T08:00:00Z",
					},
					SchedulePolicyType:   "SimpleSchedulePolicyV2",
					ScheduleRunFrequency: "Hourly",
				},
				TimeZone: "India Standard Time",
			},
			ResourceGroupName: pulumi.String("SwaggerTestRg"),
			VaultName:         pulumi.String("NetSDKTestRsVault"),
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
import com.pulumi.azurenative.recoveryservices.ProtectionPolicy;
import com.pulumi.azurenative.recoveryservices.ProtectionPolicyArgs;
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
        var protectionPolicy = new ProtectionPolicy("protectionPolicy", ProtectionPolicyArgs.builder()        
            .policyName("v2-daily-sample")
            .properties(Map.ofEntries(
                Map.entry("backupManagementType", "AzureIaasVM"),
                Map.entry("instantRpRetentionRangeInDays", 30),
                Map.entry("policyType", "V2"),
                Map.entry("retentionPolicy", Map.ofEntries(
                    Map.entry("dailySchedule", Map.ofEntries(
                        Map.entry("retentionDuration", Map.ofEntries(
                            Map.entry("count", 180),
                            Map.entry("durationType", "Days")
                        )),
                        Map.entry("retentionTimes", "2021-12-17T08:00:00+00:00")
                    )),
                    Map.entry("monthlySchedule", Map.ofEntries(
                        Map.entry("retentionDuration", Map.ofEntries(
                            Map.entry("count", 60),
                            Map.entry("durationType", "Months")
                        )),
                        Map.entry("retentionScheduleFormatType", "Weekly"),
                        Map.entry("retentionScheduleWeekly", Map.ofEntries(
                            Map.entry("daysOfTheWeek", "Sunday"),
                            Map.entry("weeksOfTheMonth", "First")
                        )),
                        Map.entry("retentionTimes", "2021-12-17T08:00:00+00:00")
                    )),
                    Map.entry("retentionPolicyType", "LongTermRetentionPolicy"),
                    Map.entry("weeklySchedule", Map.ofEntries(
                        Map.entry("daysOfTheWeek", "Sunday"),
                        Map.entry("retentionDuration", Map.ofEntries(
                            Map.entry("count", 12),
                            Map.entry("durationType", "Weeks")
                        )),
                        Map.entry("retentionTimes", "2021-12-17T08:00:00+00:00")
                    )),
                    Map.entry("yearlySchedule", Map.ofEntries(
                        Map.entry("monthsOfYear", "January"),
                        Map.entry("retentionDuration", Map.ofEntries(
                            Map.entry("count", 10),
                            Map.entry("durationType", "Years")
                        )),
                        Map.entry("retentionScheduleFormatType", "Weekly"),
                        Map.entry("retentionScheduleWeekly", Map.ofEntries(
                            Map.entry("daysOfTheWeek", "Sunday"),
                            Map.entry("weeksOfTheMonth", "First")
                        )),
                        Map.entry("retentionTimes", "2021-12-17T08:00:00+00:00")
                    ))
                )),
                Map.entry("schedulePolicy", Map.ofEntries(
                    Map.entry("hourlySchedule", Map.ofEntries(
                        Map.entry("interval", 4),
                        Map.entry("scheduleWindowDuration", 16),
                        Map.entry("scheduleWindowStartTime", "2021-12-17T08:00:00Z")
                    )),
                    Map.entry("schedulePolicyType", "SimpleSchedulePolicyV2"),
                    Map.entry("scheduleRunFrequency", "Hourly")
                )),
                Map.entry("timeZone", "India Standard Time")
            ))
            .resourceGroupName("SwaggerTestRg")
            .vaultName("NetSDKTestRsVault")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const protectionPolicy = new azure_native.recoveryservices.ProtectionPolicy("protectionPolicy", {
    policyName: "v2-daily-sample",
    properties: {
        backupManagementType: "AzureIaasVM",
        instantRpRetentionRangeInDays: 30,
        policyType: "V2",
        retentionPolicy: {
            dailySchedule: {
                retentionDuration: {
                    count: 180,
                    durationType: "Days",
                },
                retentionTimes: ["2021-12-17T08:00:00+00:00"],
            },
            monthlySchedule: {
                retentionDuration: {
                    count: 60,
                    durationType: "Months",
                },
                retentionScheduleFormatType: "Weekly",
                retentionScheduleWeekly: {
                    daysOfTheWeek: [azure_native.recoveryservices.DayOfWeek.Sunday],
                    weeksOfTheMonth: [azure_native.recoveryservices.WeekOfMonth.First],
                },
                retentionTimes: ["2021-12-17T08:00:00+00:00"],
            },
            retentionPolicyType: "LongTermRetentionPolicy",
            weeklySchedule: {
                daysOfTheWeek: [azure_native.recoveryservices.DayOfWeek.Sunday],
                retentionDuration: {
                    count: 12,
                    durationType: "Weeks",
                },
                retentionTimes: ["2021-12-17T08:00:00+00:00"],
            },
            yearlySchedule: {
                monthsOfYear: [azure_native.recoveryservices.MonthOfYear.January],
                retentionDuration: {
                    count: 10,
                    durationType: "Years",
                },
                retentionScheduleFormatType: "Weekly",
                retentionScheduleWeekly: {
                    daysOfTheWeek: [azure_native.recoveryservices.DayOfWeek.Sunday],
                    weeksOfTheMonth: [azure_native.recoveryservices.WeekOfMonth.First],
                },
                retentionTimes: ["2021-12-17T08:00:00+00:00"],
            },
        },
        schedulePolicy: {
            hourlySchedule: {
                interval: 4,
                scheduleWindowDuration: 16,
                scheduleWindowStartTime: "2021-12-17T08:00:00Z",
            },
            schedulePolicyType: "SimpleSchedulePolicyV2",
            scheduleRunFrequency: "Hourly",
        },
        timeZone: "India Standard Time",
    },
    resourceGroupName: "SwaggerTestRg",
    vaultName: "NetSDKTestRsVault",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

protection_policy = azure_native.recoveryservices.ProtectionPolicy("protectionPolicy",
    policy_name="v2-daily-sample",
    properties=azure_native.recoveryservices.AzureIaaSVMProtectionPolicyArgs(
        backup_management_type="AzureIaasVM",
        instant_rp_retention_range_in_days=30,
        policy_type="V2",
        retention_policy=azure_native.recoveryservices.LongTermRetentionPolicyArgs(
            daily_schedule=azure_native.recoveryservices.DailyRetentionScheduleArgs(
                retention_duration=azure_native.recoveryservices.RetentionDurationArgs(
                    count=180,
                    duration_type="Days",
                ),
                retention_times=["2021-12-17T08:00:00+00:00"],
            ),
            monthly_schedule=azure_native.recoveryservices.MonthlyRetentionScheduleArgs(
                retention_duration=azure_native.recoveryservices.RetentionDurationArgs(
                    count=60,
                    duration_type="Months",
                ),
                retention_schedule_format_type="Weekly",
                retention_schedule_weekly=azure_native.recoveryservices.WeeklyRetentionFormatArgs(
                    days_of_the_week=[azure_native.recoveryservices.DayOfWeek.SUNDAY],
                    weeks_of_the_month=[azure_native.recoveryservices.WeekOfMonth.FIRST],
                ),
                retention_times=["2021-12-17T08:00:00+00:00"],
            ),
            retention_policy_type="LongTermRetentionPolicy",
            weekly_schedule=azure_native.recoveryservices.WeeklyRetentionScheduleArgs(
                days_of_the_week=[azure_native.recoveryservices.DayOfWeek.SUNDAY],
                retention_duration=azure_native.recoveryservices.RetentionDurationArgs(
                    count=12,
                    duration_type="Weeks",
                ),
                retention_times=["2021-12-17T08:00:00+00:00"],
            ),
            yearly_schedule=azure_native.recoveryservices.YearlyRetentionScheduleArgs(
                months_of_year=[azure_native.recoveryservices.MonthOfYear.JANUARY],
                retention_duration=azure_native.recoveryservices.RetentionDurationArgs(
                    count=10,
                    duration_type="Years",
                ),
                retention_schedule_format_type="Weekly",
                retention_schedule_weekly=azure_native.recoveryservices.WeeklyRetentionFormatArgs(
                    days_of_the_week=[azure_native.recoveryservices.DayOfWeek.SUNDAY],
                    weeks_of_the_month=[azure_native.recoveryservices.WeekOfMonth.FIRST],
                ),
                retention_times=["2021-12-17T08:00:00+00:00"],
            ),
        ),
        schedule_policy=azure_native.recoveryservices.SimpleSchedulePolicyV2Args(
            hourly_schedule=azure_native.recoveryservices.HourlyScheduleArgs(
                interval=4,
                schedule_window_duration=16,
                schedule_window_start_time="2021-12-17T08:00:00Z",
            ),
            schedule_policy_type="SimpleSchedulePolicyV2",
            schedule_run_frequency="Hourly",
        ),
        time_zone="India Standard Time",
    ),
    resource_group_name="SwaggerTestRg",
    vault_name="NetSDKTestRsVault")

```

```yaml
resources:
  protectionPolicy:
    type: azure-native:recoveryservices:ProtectionPolicy
    properties:
      policyName: v2-daily-sample
      properties:
        backupManagementType: AzureIaasVM
        instantRpRetentionRangeInDays: 30
        policyType: V2
        retentionPolicy:
          dailySchedule:
            retentionDuration:
              count: 180
              durationType: Days
            retentionTimes:
              - 2021-12-17T08:00:00+00:00
          monthlySchedule:
            retentionDuration:
              count: 60
              durationType: Months
            retentionScheduleFormatType: Weekly
            retentionScheduleWeekly:
              daysOfTheWeek:
                - Sunday
              weeksOfTheMonth:
                - First
            retentionTimes:
              - 2021-12-17T08:00:00+00:00
          retentionPolicyType: LongTermRetentionPolicy
          weeklySchedule:
            daysOfTheWeek:
              - Sunday
            retentionDuration:
              count: 12
              durationType: Weeks
            retentionTimes:
              - 2021-12-17T08:00:00+00:00
          yearlySchedule:
            monthsOfYear:
              - January
            retentionDuration:
              count: 10
              durationType: Years
            retentionScheduleFormatType: Weekly
            retentionScheduleWeekly:
              daysOfTheWeek:
                - Sunday
              weeksOfTheMonth:
                - First
            retentionTimes:
              - 2021-12-17T08:00:00+00:00
        schedulePolicy:
          hourlySchedule:
            interval: 4
            scheduleWindowDuration: 16
            scheduleWindowStartTime: 2021-12-17T08:00:00Z
          schedulePolicyType: SimpleSchedulePolicyV2
          scheduleRunFrequency: Hourly
        timeZone: India Standard Time
      resourceGroupName: SwaggerTestRg
      vaultName: NetSDKTestRsVault

```

{{% /example %}}
{{% example %}}
### Create or Update Enhanced Azure Vm Protection Policy with daily backup
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var protectionPolicy = new AzureNative.RecoveryServices.ProtectionPolicy("protectionPolicy", new()
    {
        PolicyName = "v2-daily-sample",
        Properties = new AzureNative.RecoveryServices.Inputs.AzureIaaSVMProtectionPolicyArgs
        {
            BackupManagementType = "AzureIaasVM",
            InstantRpRetentionRangeInDays = 30,
            PolicyType = "V2",
            RetentionPolicy = new AzureNative.RecoveryServices.Inputs.LongTermRetentionPolicyArgs
            {
                DailySchedule = new AzureNative.RecoveryServices.Inputs.DailyRetentionScheduleArgs
                {
                    RetentionDuration = new AzureNative.RecoveryServices.Inputs.RetentionDurationArgs
                    {
                        Count = 180,
                        DurationType = "Days",
                    },
                    RetentionTimes = new[]
                    {
                        "2021-12-17T08:00:00+00:00",
                    },
                },
                MonthlySchedule = new AzureNative.RecoveryServices.Inputs.MonthlyRetentionScheduleArgs
                {
                    RetentionDuration = new AzureNative.RecoveryServices.Inputs.RetentionDurationArgs
                    {
                        Count = 60,
                        DurationType = "Months",
                    },
                    RetentionScheduleFormatType = "Weekly",
                    RetentionScheduleWeekly = new AzureNative.RecoveryServices.Inputs.WeeklyRetentionFormatArgs
                    {
                        DaysOfTheWeek = new[]
                        {
                            AzureNative.RecoveryServices.DayOfWeek.Sunday,
                        },
                        WeeksOfTheMonth = new[]
                        {
                            AzureNative.RecoveryServices.WeekOfMonth.First,
                        },
                    },
                    RetentionTimes = new[]
                    {
                        "2021-12-17T08:00:00+00:00",
                    },
                },
                RetentionPolicyType = "LongTermRetentionPolicy",
                WeeklySchedule = new AzureNative.RecoveryServices.Inputs.WeeklyRetentionScheduleArgs
                {
                    DaysOfTheWeek = new[]
                    {
                        AzureNative.RecoveryServices.DayOfWeek.Sunday,
                    },
                    RetentionDuration = new AzureNative.RecoveryServices.Inputs.RetentionDurationArgs
                    {
                        Count = 12,
                        DurationType = "Weeks",
                    },
                    RetentionTimes = new[]
                    {
                        "2021-12-17T08:00:00+00:00",
                    },
                },
                YearlySchedule = new AzureNative.RecoveryServices.Inputs.YearlyRetentionScheduleArgs
                {
                    MonthsOfYear = new[]
                    {
                        AzureNative.RecoveryServices.MonthOfYear.January,
                    },
                    RetentionDuration = new AzureNative.RecoveryServices.Inputs.RetentionDurationArgs
                    {
                        Count = 10,
                        DurationType = "Years",
                    },
                    RetentionScheduleFormatType = "Weekly",
                    RetentionScheduleWeekly = new AzureNative.RecoveryServices.Inputs.WeeklyRetentionFormatArgs
                    {
                        DaysOfTheWeek = new[]
                        {
                            AzureNative.RecoveryServices.DayOfWeek.Sunday,
                        },
                        WeeksOfTheMonth = new[]
                        {
                            AzureNative.RecoveryServices.WeekOfMonth.First,
                        },
                    },
                    RetentionTimes = new[]
                    {
                        "2021-12-17T08:00:00+00:00",
                    },
                },
            },
            SchedulePolicy = new AzureNative.RecoveryServices.Inputs.SimpleSchedulePolicyV2Args
            {
                DailySchedule = new AzureNative.RecoveryServices.Inputs.DailyScheduleArgs
                {
                    ScheduleRunTimes = new[]
                    {
                        "2018-01-24T10:00:00Z",
                    },
                },
                SchedulePolicyType = "SimpleSchedulePolicyV2",
                ScheduleRunFrequency = "Daily",
            },
            TimeZone = "India Standard Time",
        },
        ResourceGroupName = "SwaggerTestRg",
        VaultName = "NetSDKTestRsVault",
    });

});


```

```go
package main

import (
	recoveryservices "github.com/pulumi/pulumi-azure-native-sdk/recoveryservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := recoveryservices.NewProtectionPolicy(ctx, "protectionPolicy", &recoveryservices.ProtectionPolicyArgs{
			PolicyName: pulumi.String("v2-daily-sample"),
			Properties: recoveryservices.AzureIaaSVMProtectionPolicy{
				BackupManagementType:          "AzureIaasVM",
				InstantRpRetentionRangeInDays: 30,
				PolicyType:                    "V2",
				RetentionPolicy: recoveryservices.LongTermRetentionPolicy{
					DailySchedule: recoveryservices.DailyRetentionSchedule{
						RetentionDuration: recoveryservices.RetentionDuration{
							Count:        180,
							DurationType: "Days",
						},
						RetentionTimes: []string{
							"2021-12-17T08:00:00+00:00",
						},
					},
					MonthlySchedule: recoveryservices.MonthlyRetentionSchedule{
						RetentionDuration: recoveryservices.RetentionDuration{
							Count:        60,
							DurationType: "Months",
						},
						RetentionScheduleFormatType: "Weekly",
						RetentionScheduleWeekly: recoveryservices.WeeklyRetentionFormat{
							DaysOfTheWeek: []recoveryservices.DayOfWeek{
								recoveryservices.DayOfWeekSunday,
							},
							WeeksOfTheMonth: []recoveryservices.WeekOfMonth{
								recoveryservices.WeekOfMonthFirst,
							},
						},
						RetentionTimes: []string{
							"2021-12-17T08:00:00+00:00",
						},
					},
					RetentionPolicyType: "LongTermRetentionPolicy",
					WeeklySchedule: recoveryservices.WeeklyRetentionSchedule{
						DaysOfTheWeek: []recoveryservices.DayOfWeek{
							recoveryservices.DayOfWeekSunday,
						},
						RetentionDuration: recoveryservices.RetentionDuration{
							Count:        12,
							DurationType: "Weeks",
						},
						RetentionTimes: []string{
							"2021-12-17T08:00:00+00:00",
						},
					},
					YearlySchedule: recoveryservices.YearlyRetentionSchedule{
						MonthsOfYear: []recoveryservices.MonthOfYear{
							recoveryservices.MonthOfYearJanuary,
						},
						RetentionDuration: recoveryservices.RetentionDuration{
							Count:        10,
							DurationType: "Years",
						},
						RetentionScheduleFormatType: "Weekly",
						RetentionScheduleWeekly: recoveryservices.WeeklyRetentionFormat{
							DaysOfTheWeek: []recoveryservices.DayOfWeek{
								recoveryservices.DayOfWeekSunday,
							},
							WeeksOfTheMonth: []recoveryservices.WeekOfMonth{
								recoveryservices.WeekOfMonthFirst,
							},
						},
						RetentionTimes: []string{
							"2021-12-17T08:00:00+00:00",
						},
					},
				},
				SchedulePolicy: recoveryservices.SimpleSchedulePolicyV2{
					DailySchedule: recoveryservices.DailySchedule{
						ScheduleRunTimes: []string{
							"2018-01-24T10:00:00Z",
						},
					},
					SchedulePolicyType:   "SimpleSchedulePolicyV2",
					ScheduleRunFrequency: "Daily",
				},
				TimeZone: "India Standard Time",
			},
			ResourceGroupName: pulumi.String("SwaggerTestRg"),
			VaultName:         pulumi.String("NetSDKTestRsVault"),
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
import com.pulumi.azurenative.recoveryservices.ProtectionPolicy;
import com.pulumi.azurenative.recoveryservices.ProtectionPolicyArgs;
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
        var protectionPolicy = new ProtectionPolicy("protectionPolicy", ProtectionPolicyArgs.builder()        
            .policyName("v2-daily-sample")
            .properties(Map.ofEntries(
                Map.entry("backupManagementType", "AzureIaasVM"),
                Map.entry("instantRpRetentionRangeInDays", 30),
                Map.entry("policyType", "V2"),
                Map.entry("retentionPolicy", Map.ofEntries(
                    Map.entry("dailySchedule", Map.ofEntries(
                        Map.entry("retentionDuration", Map.ofEntries(
                            Map.entry("count", 180),
                            Map.entry("durationType", "Days")
                        )),
                        Map.entry("retentionTimes", "2021-12-17T08:00:00+00:00")
                    )),
                    Map.entry("monthlySchedule", Map.ofEntries(
                        Map.entry("retentionDuration", Map.ofEntries(
                            Map.entry("count", 60),
                            Map.entry("durationType", "Months")
                        )),
                        Map.entry("retentionScheduleFormatType", "Weekly"),
                        Map.entry("retentionScheduleWeekly", Map.ofEntries(
                            Map.entry("daysOfTheWeek", "Sunday"),
                            Map.entry("weeksOfTheMonth", "First")
                        )),
                        Map.entry("retentionTimes", "2021-12-17T08:00:00+00:00")
                    )),
                    Map.entry("retentionPolicyType", "LongTermRetentionPolicy"),
                    Map.entry("weeklySchedule", Map.ofEntries(
                        Map.entry("daysOfTheWeek", "Sunday"),
                        Map.entry("retentionDuration", Map.ofEntries(
                            Map.entry("count", 12),
                            Map.entry("durationType", "Weeks")
                        )),
                        Map.entry("retentionTimes", "2021-12-17T08:00:00+00:00")
                    )),
                    Map.entry("yearlySchedule", Map.ofEntries(
                        Map.entry("monthsOfYear", "January"),
                        Map.entry("retentionDuration", Map.ofEntries(
                            Map.entry("count", 10),
                            Map.entry("durationType", "Years")
                        )),
                        Map.entry("retentionScheduleFormatType", "Weekly"),
                        Map.entry("retentionScheduleWeekly", Map.ofEntries(
                            Map.entry("daysOfTheWeek", "Sunday"),
                            Map.entry("weeksOfTheMonth", "First")
                        )),
                        Map.entry("retentionTimes", "2021-12-17T08:00:00+00:00")
                    ))
                )),
                Map.entry("schedulePolicy", Map.ofEntries(
                    Map.entry("dailySchedule", Map.of("scheduleRunTimes", "2018-01-24T10:00:00Z")),
                    Map.entry("schedulePolicyType", "SimpleSchedulePolicyV2"),
                    Map.entry("scheduleRunFrequency", "Daily")
                )),
                Map.entry("timeZone", "India Standard Time")
            ))
            .resourceGroupName("SwaggerTestRg")
            .vaultName("NetSDKTestRsVault")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const protectionPolicy = new azure_native.recoveryservices.ProtectionPolicy("protectionPolicy", {
    policyName: "v2-daily-sample",
    properties: {
        backupManagementType: "AzureIaasVM",
        instantRpRetentionRangeInDays: 30,
        policyType: "V2",
        retentionPolicy: {
            dailySchedule: {
                retentionDuration: {
                    count: 180,
                    durationType: "Days",
                },
                retentionTimes: ["2021-12-17T08:00:00+00:00"],
            },
            monthlySchedule: {
                retentionDuration: {
                    count: 60,
                    durationType: "Months",
                },
                retentionScheduleFormatType: "Weekly",
                retentionScheduleWeekly: {
                    daysOfTheWeek: [azure_native.recoveryservices.DayOfWeek.Sunday],
                    weeksOfTheMonth: [azure_native.recoveryservices.WeekOfMonth.First],
                },
                retentionTimes: ["2021-12-17T08:00:00+00:00"],
            },
            retentionPolicyType: "LongTermRetentionPolicy",
            weeklySchedule: {
                daysOfTheWeek: [azure_native.recoveryservices.DayOfWeek.Sunday],
                retentionDuration: {
                    count: 12,
                    durationType: "Weeks",
                },
                retentionTimes: ["2021-12-17T08:00:00+00:00"],
            },
            yearlySchedule: {
                monthsOfYear: [azure_native.recoveryservices.MonthOfYear.January],
                retentionDuration: {
                    count: 10,
                    durationType: "Years",
                },
                retentionScheduleFormatType: "Weekly",
                retentionScheduleWeekly: {
                    daysOfTheWeek: [azure_native.recoveryservices.DayOfWeek.Sunday],
                    weeksOfTheMonth: [azure_native.recoveryservices.WeekOfMonth.First],
                },
                retentionTimes: ["2021-12-17T08:00:00+00:00"],
            },
        },
        schedulePolicy: {
            dailySchedule: {
                scheduleRunTimes: ["2018-01-24T10:00:00Z"],
            },
            schedulePolicyType: "SimpleSchedulePolicyV2",
            scheduleRunFrequency: "Daily",
        },
        timeZone: "India Standard Time",
    },
    resourceGroupName: "SwaggerTestRg",
    vaultName: "NetSDKTestRsVault",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

protection_policy = azure_native.recoveryservices.ProtectionPolicy("protectionPolicy",
    policy_name="v2-daily-sample",
    properties=azure_native.recoveryservices.AzureIaaSVMProtectionPolicyArgs(
        backup_management_type="AzureIaasVM",
        instant_rp_retention_range_in_days=30,
        policy_type="V2",
        retention_policy=azure_native.recoveryservices.LongTermRetentionPolicyArgs(
            daily_schedule=azure_native.recoveryservices.DailyRetentionScheduleArgs(
                retention_duration=azure_native.recoveryservices.RetentionDurationArgs(
                    count=180,
                    duration_type="Days",
                ),
                retention_times=["2021-12-17T08:00:00+00:00"],
            ),
            monthly_schedule=azure_native.recoveryservices.MonthlyRetentionScheduleArgs(
                retention_duration=azure_native.recoveryservices.RetentionDurationArgs(
                    count=60,
                    duration_type="Months",
                ),
                retention_schedule_format_type="Weekly",
                retention_schedule_weekly=azure_native.recoveryservices.WeeklyRetentionFormatArgs(
                    days_of_the_week=[azure_native.recoveryservices.DayOfWeek.SUNDAY],
                    weeks_of_the_month=[azure_native.recoveryservices.WeekOfMonth.FIRST],
                ),
                retention_times=["2021-12-17T08:00:00+00:00"],
            ),
            retention_policy_type="LongTermRetentionPolicy",
            weekly_schedule=azure_native.recoveryservices.WeeklyRetentionScheduleArgs(
                days_of_the_week=[azure_native.recoveryservices.DayOfWeek.SUNDAY],
                retention_duration=azure_native.recoveryservices.RetentionDurationArgs(
                    count=12,
                    duration_type="Weeks",
                ),
                retention_times=["2021-12-17T08:00:00+00:00"],
            ),
            yearly_schedule=azure_native.recoveryservices.YearlyRetentionScheduleArgs(
                months_of_year=[azure_native.recoveryservices.MonthOfYear.JANUARY],
                retention_duration=azure_native.recoveryservices.RetentionDurationArgs(
                    count=10,
                    duration_type="Years",
                ),
                retention_schedule_format_type="Weekly",
                retention_schedule_weekly=azure_native.recoveryservices.WeeklyRetentionFormatArgs(
                    days_of_the_week=[azure_native.recoveryservices.DayOfWeek.SUNDAY],
                    weeks_of_the_month=[azure_native.recoveryservices.WeekOfMonth.FIRST],
                ),
                retention_times=["2021-12-17T08:00:00+00:00"],
            ),
        ),
        schedule_policy=azure_native.recoveryservices.SimpleSchedulePolicyV2Args(
            daily_schedule=azure_native.recoveryservices.DailyScheduleArgs(
                schedule_run_times=["2018-01-24T10:00:00Z"],
            ),
            schedule_policy_type="SimpleSchedulePolicyV2",
            schedule_run_frequency="Daily",
        ),
        time_zone="India Standard Time",
    ),
    resource_group_name="SwaggerTestRg",
    vault_name="NetSDKTestRsVault")

```

```yaml
resources:
  protectionPolicy:
    type: azure-native:recoveryservices:ProtectionPolicy
    properties:
      policyName: v2-daily-sample
      properties:
        backupManagementType: AzureIaasVM
        instantRpRetentionRangeInDays: 30
        policyType: V2
        retentionPolicy:
          dailySchedule:
            retentionDuration:
              count: 180
              durationType: Days
            retentionTimes:
              - 2021-12-17T08:00:00+00:00
          monthlySchedule:
            retentionDuration:
              count: 60
              durationType: Months
            retentionScheduleFormatType: Weekly
            retentionScheduleWeekly:
              daysOfTheWeek:
                - Sunday
              weeksOfTheMonth:
                - First
            retentionTimes:
              - 2021-12-17T08:00:00+00:00
          retentionPolicyType: LongTermRetentionPolicy
          weeklySchedule:
            daysOfTheWeek:
              - Sunday
            retentionDuration:
              count: 12
              durationType: Weeks
            retentionTimes:
              - 2021-12-17T08:00:00+00:00
          yearlySchedule:
            monthsOfYear:
              - January
            retentionDuration:
              count: 10
              durationType: Years
            retentionScheduleFormatType: Weekly
            retentionScheduleWeekly:
              daysOfTheWeek:
                - Sunday
              weeksOfTheMonth:
                - First
            retentionTimes:
              - 2021-12-17T08:00:00+00:00
        schedulePolicy:
          dailySchedule:
            scheduleRunTimes:
              - 2018-01-24T10:00:00Z
          schedulePolicyType: SimpleSchedulePolicyV2
          scheduleRunFrequency: Daily
        timeZone: India Standard Time
      resourceGroupName: SwaggerTestRg
      vaultName: NetSDKTestRsVault

```

{{% /example %}}
{{% example %}}
### Create or Update Full Azure Vm Protection Policy
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var protectionPolicy = new AzureNative.RecoveryServices.ProtectionPolicy("protectionPolicy", new()
    {
        PolicyName = "testPolicy1",
        Properties = new AzureNative.RecoveryServices.Inputs.AzureIaaSVMProtectionPolicyArgs
        {
            BackupManagementType = "AzureIaasVM",
            RetentionPolicy = new AzureNative.RecoveryServices.Inputs.LongTermRetentionPolicyArgs
            {
                MonthlySchedule = new AzureNative.RecoveryServices.Inputs.MonthlyRetentionScheduleArgs
                {
                    RetentionDuration = new AzureNative.RecoveryServices.Inputs.RetentionDurationArgs
                    {
                        Count = 2,
                        DurationType = "Months",
                    },
                    RetentionScheduleFormatType = "Weekly",
                    RetentionScheduleWeekly = new AzureNative.RecoveryServices.Inputs.WeeklyRetentionFormatArgs
                    {
                        DaysOfTheWeek = new[]
                        {
                            AzureNative.RecoveryServices.DayOfWeek.Wednesday,
                            AzureNative.RecoveryServices.DayOfWeek.Thursday,
                        },
                        WeeksOfTheMonth = new[]
                        {
                            AzureNative.RecoveryServices.WeekOfMonth.First,
                            AzureNative.RecoveryServices.WeekOfMonth.Third,
                        },
                    },
                    RetentionTimes = new[]
                    {
                        "2018-01-24T10:00:00Z",
                    },
                },
                RetentionPolicyType = "LongTermRetentionPolicy",
                WeeklySchedule = new AzureNative.RecoveryServices.Inputs.WeeklyRetentionScheduleArgs
                {
                    DaysOfTheWeek = new[]
                    {
                        AzureNative.RecoveryServices.DayOfWeek.Monday,
                        AzureNative.RecoveryServices.DayOfWeek.Wednesday,
                        AzureNative.RecoveryServices.DayOfWeek.Thursday,
                    },
                    RetentionDuration = new AzureNative.RecoveryServices.Inputs.RetentionDurationArgs
                    {
                        Count = 1,
                        DurationType = "Weeks",
                    },
                    RetentionTimes = new[]
                    {
                        "2018-01-24T10:00:00Z",
                    },
                },
                YearlySchedule = new AzureNative.RecoveryServices.Inputs.YearlyRetentionScheduleArgs
                {
                    MonthsOfYear = new[]
                    {
                        AzureNative.RecoveryServices.MonthOfYear.February,
                        AzureNative.RecoveryServices.MonthOfYear.November,
                    },
                    RetentionDuration = new AzureNative.RecoveryServices.Inputs.RetentionDurationArgs
                    {
                        Count = 4,
                        DurationType = "Years",
                    },
                    RetentionScheduleFormatType = "Weekly",
                    RetentionScheduleWeekly = new AzureNative.RecoveryServices.Inputs.WeeklyRetentionFormatArgs
                    {
                        DaysOfTheWeek = new[]
                        {
                            AzureNative.RecoveryServices.DayOfWeek.Monday,
                            AzureNative.RecoveryServices.DayOfWeek.Thursday,
                        },
                        WeeksOfTheMonth = new[]
                        {
                            AzureNative.RecoveryServices.WeekOfMonth.Fourth,
                        },
                    },
                    RetentionTimes = new[]
                    {
                        "2018-01-24T10:00:00Z",
                    },
                },
            },
            SchedulePolicy = new AzureNative.RecoveryServices.Inputs.SimpleSchedulePolicyArgs
            {
                SchedulePolicyType = "SimpleSchedulePolicy",
                ScheduleRunDays = new[]
                {
                    AzureNative.RecoveryServices.DayOfWeek.Monday,
                    AzureNative.RecoveryServices.DayOfWeek.Wednesday,
                    AzureNative.RecoveryServices.DayOfWeek.Thursday,
                },
                ScheduleRunFrequency = "Weekly",
                ScheduleRunTimes = new[]
                {
                    "2018-01-24T10:00:00Z",
                },
            },
            TimeZone = "Pacific Standard Time",
        },
        ResourceGroupName = "SwaggerTestRg",
        VaultName = "NetSDKTestRsVault",
    });

});


```

```go
package main

import (
	recoveryservices "github.com/pulumi/pulumi-azure-native-sdk/recoveryservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := recoveryservices.NewProtectionPolicy(ctx, "protectionPolicy", &recoveryservices.ProtectionPolicyArgs{
			PolicyName: pulumi.String("testPolicy1"),
			Properties: recoveryservices.AzureIaaSVMProtectionPolicy{
				BackupManagementType: "AzureIaasVM",
				RetentionPolicy: recoveryservices.LongTermRetentionPolicy{
					MonthlySchedule: recoveryservices.MonthlyRetentionSchedule{
						RetentionDuration: recoveryservices.RetentionDuration{
							Count:        2,
							DurationType: "Months",
						},
						RetentionScheduleFormatType: "Weekly",
						RetentionScheduleWeekly: recoveryservices.WeeklyRetentionFormat{
							DaysOfTheWeek: []recoveryservices.DayOfWeek{
								recoveryservices.DayOfWeekWednesday,
								recoveryservices.DayOfWeekThursday,
							},
							WeeksOfTheMonth: []recoveryservices.WeekOfMonth{
								recoveryservices.WeekOfMonthFirst,
								recoveryservices.WeekOfMonthThird,
							},
						},
						RetentionTimes: []string{
							"2018-01-24T10:00:00Z",
						},
					},
					RetentionPolicyType: "LongTermRetentionPolicy",
					WeeklySchedule: recoveryservices.WeeklyRetentionSchedule{
						DaysOfTheWeek: []recoveryservices.DayOfWeek{
							recoveryservices.DayOfWeekMonday,
							recoveryservices.DayOfWeekWednesday,
							recoveryservices.DayOfWeekThursday,
						},
						RetentionDuration: recoveryservices.RetentionDuration{
							Count:        1,
							DurationType: "Weeks",
						},
						RetentionTimes: []string{
							"2018-01-24T10:00:00Z",
						},
					},
					YearlySchedule: recoveryservices.YearlyRetentionSchedule{
						MonthsOfYear: []recoveryservices.MonthOfYear{
							recoveryservices.MonthOfYearFebruary,
							recoveryservices.MonthOfYearNovember,
						},
						RetentionDuration: recoveryservices.RetentionDuration{
							Count:        4,
							DurationType: "Years",
						},
						RetentionScheduleFormatType: "Weekly",
						RetentionScheduleWeekly: recoveryservices.WeeklyRetentionFormat{
							DaysOfTheWeek: []recoveryservices.DayOfWeek{
								recoveryservices.DayOfWeekMonday,
								recoveryservices.DayOfWeekThursday,
							},
							WeeksOfTheMonth: []recoveryservices.WeekOfMonth{
								recoveryservices.WeekOfMonthFourth,
							},
						},
						RetentionTimes: []string{
							"2018-01-24T10:00:00Z",
						},
					},
				},
				SchedulePolicy: recoveryservices.SimpleSchedulePolicy{
					SchedulePolicyType: "SimpleSchedulePolicy",
					ScheduleRunDays: []recoveryservices.DayOfWeek{
						recoveryservices.DayOfWeekMonday,
						recoveryservices.DayOfWeekWednesday,
						recoveryservices.DayOfWeekThursday,
					},
					ScheduleRunFrequency: "Weekly",
					ScheduleRunTimes: []string{
						"2018-01-24T10:00:00Z",
					},
				},
				TimeZone: "Pacific Standard Time",
			},
			ResourceGroupName: pulumi.String("SwaggerTestRg"),
			VaultName:         pulumi.String("NetSDKTestRsVault"),
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
import com.pulumi.azurenative.recoveryservices.ProtectionPolicy;
import com.pulumi.azurenative.recoveryservices.ProtectionPolicyArgs;
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
        var protectionPolicy = new ProtectionPolicy("protectionPolicy", ProtectionPolicyArgs.builder()        
            .policyName("testPolicy1")
            .properties(Map.ofEntries(
                Map.entry("backupManagementType", "AzureIaasVM"),
                Map.entry("retentionPolicy", Map.ofEntries(
                    Map.entry("monthlySchedule", Map.ofEntries(
                        Map.entry("retentionDuration", Map.ofEntries(
                            Map.entry("count", 2),
                            Map.entry("durationType", "Months")
                        )),
                        Map.entry("retentionScheduleFormatType", "Weekly"),
                        Map.entry("retentionScheduleWeekly", Map.ofEntries(
                            Map.entry("daysOfTheWeek",                             
                                "Wednesday",
                                "Thursday"),
                            Map.entry("weeksOfTheMonth",                             
                                "First",
                                "Third")
                        )),
                        Map.entry("retentionTimes", "2018-01-24T10:00:00Z")
                    )),
                    Map.entry("retentionPolicyType", "LongTermRetentionPolicy"),
                    Map.entry("weeklySchedule", Map.ofEntries(
                        Map.entry("daysOfTheWeek",                         
                            "Monday",
                            "Wednesday",
                            "Thursday"),
                        Map.entry("retentionDuration", Map.ofEntries(
                            Map.entry("count", 1),
                            Map.entry("durationType", "Weeks")
                        )),
                        Map.entry("retentionTimes", "2018-01-24T10:00:00Z")
                    )),
                    Map.entry("yearlySchedule", Map.ofEntries(
                        Map.entry("monthsOfYear",                         
                            "February",
                            "November"),
                        Map.entry("retentionDuration", Map.ofEntries(
                            Map.entry("count", 4),
                            Map.entry("durationType", "Years")
                        )),
                        Map.entry("retentionScheduleFormatType", "Weekly"),
                        Map.entry("retentionScheduleWeekly", Map.ofEntries(
                            Map.entry("daysOfTheWeek",                             
                                "Monday",
                                "Thursday"),
                            Map.entry("weeksOfTheMonth", "Fourth")
                        )),
                        Map.entry("retentionTimes", "2018-01-24T10:00:00Z")
                    ))
                )),
                Map.entry("schedulePolicy", Map.ofEntries(
                    Map.entry("schedulePolicyType", "SimpleSchedulePolicy"),
                    Map.entry("scheduleRunDays",                     
                        "Monday",
                        "Wednesday",
                        "Thursday"),
                    Map.entry("scheduleRunFrequency", "Weekly"),
                    Map.entry("scheduleRunTimes", "2018-01-24T10:00:00Z")
                )),
                Map.entry("timeZone", "Pacific Standard Time")
            ))
            .resourceGroupName("SwaggerTestRg")
            .vaultName("NetSDKTestRsVault")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const protectionPolicy = new azure_native.recoveryservices.ProtectionPolicy("protectionPolicy", {
    policyName: "testPolicy1",
    properties: {
        backupManagementType: "AzureIaasVM",
        retentionPolicy: {
            monthlySchedule: {
                retentionDuration: {
                    count: 2,
                    durationType: "Months",
                },
                retentionScheduleFormatType: "Weekly",
                retentionScheduleWeekly: {
                    daysOfTheWeek: [
                        azure_native.recoveryservices.DayOfWeek.Wednesday,
                        azure_native.recoveryservices.DayOfWeek.Thursday,
                    ],
                    weeksOfTheMonth: [
                        azure_native.recoveryservices.WeekOfMonth.First,
                        azure_native.recoveryservices.WeekOfMonth.Third,
                    ],
                },
                retentionTimes: ["2018-01-24T10:00:00Z"],
            },
            retentionPolicyType: "LongTermRetentionPolicy",
            weeklySchedule: {
                daysOfTheWeek: [
                    azure_native.recoveryservices.DayOfWeek.Monday,
                    azure_native.recoveryservices.DayOfWeek.Wednesday,
                    azure_native.recoveryservices.DayOfWeek.Thursday,
                ],
                retentionDuration: {
                    count: 1,
                    durationType: "Weeks",
                },
                retentionTimes: ["2018-01-24T10:00:00Z"],
            },
            yearlySchedule: {
                monthsOfYear: [
                    azure_native.recoveryservices.MonthOfYear.February,
                    azure_native.recoveryservices.MonthOfYear.November,
                ],
                retentionDuration: {
                    count: 4,
                    durationType: "Years",
                },
                retentionScheduleFormatType: "Weekly",
                retentionScheduleWeekly: {
                    daysOfTheWeek: [
                        azure_native.recoveryservices.DayOfWeek.Monday,
                        azure_native.recoveryservices.DayOfWeek.Thursday,
                    ],
                    weeksOfTheMonth: [azure_native.recoveryservices.WeekOfMonth.Fourth],
                },
                retentionTimes: ["2018-01-24T10:00:00Z"],
            },
        },
        schedulePolicy: {
            schedulePolicyType: "SimpleSchedulePolicy",
            scheduleRunDays: [
                azure_native.recoveryservices.DayOfWeek.Monday,
                azure_native.recoveryservices.DayOfWeek.Wednesday,
                azure_native.recoveryservices.DayOfWeek.Thursday,
            ],
            scheduleRunFrequency: "Weekly",
            scheduleRunTimes: ["2018-01-24T10:00:00Z"],
        },
        timeZone: "Pacific Standard Time",
    },
    resourceGroupName: "SwaggerTestRg",
    vaultName: "NetSDKTestRsVault",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

protection_policy = azure_native.recoveryservices.ProtectionPolicy("protectionPolicy",
    policy_name="testPolicy1",
    properties=azure_native.recoveryservices.AzureIaaSVMProtectionPolicyArgs(
        backup_management_type="AzureIaasVM",
        retention_policy=azure_native.recoveryservices.LongTermRetentionPolicyArgs(
            monthly_schedule=azure_native.recoveryservices.MonthlyRetentionScheduleArgs(
                retention_duration=azure_native.recoveryservices.RetentionDurationArgs(
                    count=2,
                    duration_type="Months",
                ),
                retention_schedule_format_type="Weekly",
                retention_schedule_weekly=azure_native.recoveryservices.WeeklyRetentionFormatArgs(
                    days_of_the_week=[
                        azure_native.recoveryservices.DayOfWeek.WEDNESDAY,
                        azure_native.recoveryservices.DayOfWeek.THURSDAY,
                    ],
                    weeks_of_the_month=[
                        azure_native.recoveryservices.WeekOfMonth.FIRST,
                        azure_native.recoveryservices.WeekOfMonth.THIRD,
                    ],
                ),
                retention_times=["2018-01-24T10:00:00Z"],
            ),
            retention_policy_type="LongTermRetentionPolicy",
            weekly_schedule=azure_native.recoveryservices.WeeklyRetentionScheduleArgs(
                days_of_the_week=[
                    azure_native.recoveryservices.DayOfWeek.MONDAY,
                    azure_native.recoveryservices.DayOfWeek.WEDNESDAY,
                    azure_native.recoveryservices.DayOfWeek.THURSDAY,
                ],
                retention_duration=azure_native.recoveryservices.RetentionDurationArgs(
                    count=1,
                    duration_type="Weeks",
                ),
                retention_times=["2018-01-24T10:00:00Z"],
            ),
            yearly_schedule=azure_native.recoveryservices.YearlyRetentionScheduleArgs(
                months_of_year=[
                    azure_native.recoveryservices.MonthOfYear.FEBRUARY,
                    azure_native.recoveryservices.MonthOfYear.NOVEMBER,
                ],
                retention_duration=azure_native.recoveryservices.RetentionDurationArgs(
                    count=4,
                    duration_type="Years",
                ),
                retention_schedule_format_type="Weekly",
                retention_schedule_weekly=azure_native.recoveryservices.WeeklyRetentionFormatArgs(
                    days_of_the_week=[
                        azure_native.recoveryservices.DayOfWeek.MONDAY,
                        azure_native.recoveryservices.DayOfWeek.THURSDAY,
                    ],
                    weeks_of_the_month=[azure_native.recoveryservices.WeekOfMonth.FOURTH],
                ),
                retention_times=["2018-01-24T10:00:00Z"],
            ),
        ),
        schedule_policy=azure_native.recoveryservices.SimpleSchedulePolicyArgs(
            schedule_policy_type="SimpleSchedulePolicy",
            schedule_run_days=[
                azure_native.recoveryservices.DayOfWeek.MONDAY,
                azure_native.recoveryservices.DayOfWeek.WEDNESDAY,
                azure_native.recoveryservices.DayOfWeek.THURSDAY,
            ],
            schedule_run_frequency="Weekly",
            schedule_run_times=["2018-01-24T10:00:00Z"],
        ),
        time_zone="Pacific Standard Time",
    ),
    resource_group_name="SwaggerTestRg",
    vault_name="NetSDKTestRsVault")

```

```yaml
resources:
  protectionPolicy:
    type: azure-native:recoveryservices:ProtectionPolicy
    properties:
      policyName: testPolicy1
      properties:
        backupManagementType: AzureIaasVM
        retentionPolicy:
          monthlySchedule:
            retentionDuration:
              count: 2
              durationType: Months
            retentionScheduleFormatType: Weekly
            retentionScheduleWeekly:
              daysOfTheWeek:
                - Wednesday
                - Thursday
              weeksOfTheMonth:
                - First
                - Third
            retentionTimes:
              - 2018-01-24T10:00:00Z
          retentionPolicyType: LongTermRetentionPolicy
          weeklySchedule:
            daysOfTheWeek:
              - Monday
              - Wednesday
              - Thursday
            retentionDuration:
              count: 1
              durationType: Weeks
            retentionTimes:
              - 2018-01-24T10:00:00Z
          yearlySchedule:
            monthsOfYear:
              - February
              - November
            retentionDuration:
              count: 4
              durationType: Years
            retentionScheduleFormatType: Weekly
            retentionScheduleWeekly:
              daysOfTheWeek:
                - Monday
                - Thursday
              weeksOfTheMonth:
                - Fourth
            retentionTimes:
              - 2018-01-24T10:00:00Z
        schedulePolicy:
          schedulePolicyType: SimpleSchedulePolicy
          scheduleRunDays:
            - Monday
            - Wednesday
            - Thursday
          scheduleRunFrequency: Weekly
          scheduleRunTimes:
            - 2018-01-24T10:00:00Z
        timeZone: Pacific Standard Time
      resourceGroupName: SwaggerTestRg
      vaultName: NetSDKTestRsVault

```

{{% /example %}}
{{% example %}}
### Create or Update Full Azure Workload Protection Policy
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var protectionPolicy = new AzureNative.RecoveryServices.ProtectionPolicy("protectionPolicy", new()
    {
        PolicyName = "testPolicy1",
        Properties = new AzureNative.RecoveryServices.Inputs.AzureVmWorkloadProtectionPolicyArgs
        {
            BackupManagementType = "AzureWorkload",
            Settings = new AzureNative.RecoveryServices.Inputs.SettingsArgs
            {
                Issqlcompression = false,
                TimeZone = "Pacific Standard Time",
            },
            SubProtectionPolicy = new[]
            {
                new AzureNative.RecoveryServices.Inputs.SubProtectionPolicyArgs
                {
                    PolicyType = "Full",
                    RetentionPolicy = new AzureNative.RecoveryServices.Inputs.LongTermRetentionPolicyArgs
                    {
                        MonthlySchedule = new AzureNative.RecoveryServices.Inputs.MonthlyRetentionScheduleArgs
                        {
                            RetentionDuration = new AzureNative.RecoveryServices.Inputs.RetentionDurationArgs
                            {
                                Count = 1,
                                DurationType = "Months",
                            },
                            RetentionScheduleFormatType = "Weekly",
                            RetentionScheduleWeekly = new AzureNative.RecoveryServices.Inputs.WeeklyRetentionFormatArgs
                            {
                                DaysOfTheWeek = new[]
                                {
                                    AzureNative.RecoveryServices.DayOfWeek.Sunday,
                                },
                                WeeksOfTheMonth = new[]
                                {
                                    AzureNative.RecoveryServices.WeekOfMonth.Second,
                                },
                            },
                            RetentionTimes = new[]
                            {
                                "2018-01-24T10:00:00Z",
                            },
                        },
                        RetentionPolicyType = "LongTermRetentionPolicy",
                        WeeklySchedule = new AzureNative.RecoveryServices.Inputs.WeeklyRetentionScheduleArgs
                        {
                            DaysOfTheWeek = new[]
                            {
                                AzureNative.RecoveryServices.DayOfWeek.Sunday,
                                AzureNative.RecoveryServices.DayOfWeek.Tuesday,
                            },
                            RetentionDuration = new AzureNative.RecoveryServices.Inputs.RetentionDurationArgs
                            {
                                Count = 2,
                                DurationType = "Weeks",
                            },
                            RetentionTimes = new[]
                            {
                                "2018-01-24T10:00:00Z",
                            },
                        },
                        YearlySchedule = new AzureNative.RecoveryServices.Inputs.YearlyRetentionScheduleArgs
                        {
                            MonthsOfYear = new[]
                            {
                                AzureNative.RecoveryServices.MonthOfYear.January,
                                AzureNative.RecoveryServices.MonthOfYear.June,
                                AzureNative.RecoveryServices.MonthOfYear.December,
                            },
                            RetentionDuration = new AzureNative.RecoveryServices.Inputs.RetentionDurationArgs
                            {
                                Count = 1,
                                DurationType = "Years",
                            },
                            RetentionScheduleFormatType = "Weekly",
                            RetentionScheduleWeekly = new AzureNative.RecoveryServices.Inputs.WeeklyRetentionFormatArgs
                            {
                                DaysOfTheWeek = new[]
                                {
                                    AzureNative.RecoveryServices.DayOfWeek.Sunday,
                                },
                                WeeksOfTheMonth = new[]
                                {
                                    AzureNative.RecoveryServices.WeekOfMonth.Last,
                                },
                            },
                            RetentionTimes = new[]
                            {
                                "2018-01-24T10:00:00Z",
                            },
                        },
                    },
                    SchedulePolicy = new AzureNative.RecoveryServices.Inputs.SimpleSchedulePolicyArgs
                    {
                        SchedulePolicyType = "SimpleSchedulePolicy",
                        ScheduleRunDays = new[]
                        {
                            AzureNative.RecoveryServices.DayOfWeek.Sunday,
                            AzureNative.RecoveryServices.DayOfWeek.Tuesday,
                        },
                        ScheduleRunFrequency = "Weekly",
                        ScheduleRunTimes = new[]
                        {
                            "2018-01-24T10:00:00Z",
                        },
                    },
                },
                new AzureNative.RecoveryServices.Inputs.SubProtectionPolicyArgs
                {
                    PolicyType = "Differential",
                    RetentionPolicy = new AzureNative.RecoveryServices.Inputs.SimpleRetentionPolicyArgs
                    {
                        RetentionDuration = new AzureNative.RecoveryServices.Inputs.RetentionDurationArgs
                        {
                            Count = 8,
                            DurationType = "Days",
                        },
                        RetentionPolicyType = "SimpleRetentionPolicy",
                    },
                    SchedulePolicy = new AzureNative.RecoveryServices.Inputs.SimpleSchedulePolicyArgs
                    {
                        SchedulePolicyType = "SimpleSchedulePolicy",
                        ScheduleRunDays = new[]
                        {
                            AzureNative.RecoveryServices.DayOfWeek.Friday,
                        },
                        ScheduleRunFrequency = "Weekly",
                        ScheduleRunTimes = new[]
                        {
                            "2018-01-24T10:00:00Z",
                        },
                    },
                },
                new AzureNative.RecoveryServices.Inputs.SubProtectionPolicyArgs
                {
                    PolicyType = "Log",
                    RetentionPolicy = new AzureNative.RecoveryServices.Inputs.SimpleRetentionPolicyArgs
                    {
                        RetentionDuration = new AzureNative.RecoveryServices.Inputs.RetentionDurationArgs
                        {
                            Count = 7,
                            DurationType = "Days",
                        },
                        RetentionPolicyType = "SimpleRetentionPolicy",
                    },
                    SchedulePolicy = new AzureNative.RecoveryServices.Inputs.LogSchedulePolicyArgs
                    {
                        ScheduleFrequencyInMins = 60,
                        SchedulePolicyType = "LogSchedulePolicy",
                    },
                },
            },
            WorkLoadType = "SQLDataBase",
        },
        ResourceGroupName = "SwaggerTestRg",
        VaultName = "NetSDKTestRsVault",
    });

});


```

```go
package main

import (
	recoveryservices "github.com/pulumi/pulumi-azure-native-sdk/recoveryservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := recoveryservices.NewProtectionPolicy(ctx, "protectionPolicy", &recoveryservices.ProtectionPolicyArgs{
			PolicyName: pulumi.String("testPolicy1"),
			Properties: recoveryservices.AzureVmWorkloadProtectionPolicy{
				BackupManagementType: "AzureWorkload",
				Settings: recoveryservices.Settings{
					Issqlcompression: false,
					TimeZone:         "Pacific Standard Time",
				},
				SubProtectionPolicy: []recoveryservices.SubProtectionPolicy{
					{
						PolicyType: "Full",
						RetentionPolicy: {
							MonthlySchedule: {
								RetentionDuration: {
									Count:        1,
									DurationType: "Months",
								},
								RetentionScheduleFormatType: "Weekly",
								RetentionScheduleWeekly: {
									DaysOfTheWeek: []recoveryservices.DayOfWeek{
										recoveryservices.DayOfWeekSunday,
									},
									WeeksOfTheMonth: []recoveryservices.WeekOfMonth{
										recoveryservices.WeekOfMonthSecond,
									},
								},
								RetentionTimes: []string{
									"2018-01-24T10:00:00Z",
								},
							},
							RetentionPolicyType: "LongTermRetentionPolicy",
							WeeklySchedule: {
								DaysOfTheWeek: []recoveryservices.DayOfWeek{
									recoveryservices.DayOfWeekSunday,
									recoveryservices.DayOfWeekTuesday,
								},
								RetentionDuration: {
									Count:        2,
									DurationType: "Weeks",
								},
								RetentionTimes: []string{
									"2018-01-24T10:00:00Z",
								},
							},
							YearlySchedule: {
								MonthsOfYear: []recoveryservices.MonthOfYear{
									recoveryservices.MonthOfYearJanuary,
									recoveryservices.MonthOfYearJune,
									recoveryservices.MonthOfYearDecember,
								},
								RetentionDuration: {
									Count:        1,
									DurationType: "Years",
								},
								RetentionScheduleFormatType: "Weekly",
								RetentionScheduleWeekly: {
									DaysOfTheWeek: []recoveryservices.DayOfWeek{
										recoveryservices.DayOfWeekSunday,
									},
									WeeksOfTheMonth: []recoveryservices.WeekOfMonth{
										recoveryservices.WeekOfMonthLast,
									},
								},
								RetentionTimes: []string{
									"2018-01-24T10:00:00Z",
								},
							},
						},
						SchedulePolicy: {
							SchedulePolicyType: "SimpleSchedulePolicy",
							ScheduleRunDays: []recoveryservices.DayOfWeek{
								recoveryservices.DayOfWeekSunday,
								recoveryservices.DayOfWeekTuesday,
							},
							ScheduleRunFrequency: "Weekly",
							ScheduleRunTimes: []string{
								"2018-01-24T10:00:00Z",
							},
						},
					},
					{
						PolicyType: "Differential",
						RetentionPolicy: {
							RetentionDuration: {
								Count:        8,
								DurationType: "Days",
							},
							RetentionPolicyType: "SimpleRetentionPolicy",
						},
						SchedulePolicy: {
							SchedulePolicyType: "SimpleSchedulePolicy",
							ScheduleRunDays: []recoveryservices.DayOfWeek{
								recoveryservices.DayOfWeekFriday,
							},
							ScheduleRunFrequency: "Weekly",
							ScheduleRunTimes: []string{
								"2018-01-24T10:00:00Z",
							},
						},
					},
					{
						PolicyType: "Log",
						RetentionPolicy: {
							RetentionDuration: {
								Count:        7,
								DurationType: "Days",
							},
							RetentionPolicyType: "SimpleRetentionPolicy",
						},
						SchedulePolicy: {
							ScheduleFrequencyInMins: 60,
							SchedulePolicyType:      "LogSchedulePolicy",
						},
					},
				},
				WorkLoadType: "SQLDataBase",
			},
			ResourceGroupName: pulumi.String("SwaggerTestRg"),
			VaultName:         pulumi.String("NetSDKTestRsVault"),
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
import com.pulumi.azurenative.recoveryservices.ProtectionPolicy;
import com.pulumi.azurenative.recoveryservices.ProtectionPolicyArgs;
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
        var protectionPolicy = new ProtectionPolicy("protectionPolicy", ProtectionPolicyArgs.builder()        
            .policyName("testPolicy1")
            .properties(Map.ofEntries(
                Map.entry("backupManagementType", "AzureWorkload"),
                Map.entry("settings", Map.ofEntries(
                    Map.entry("issqlcompression", false),
                    Map.entry("timeZone", "Pacific Standard Time")
                )),
                Map.entry("subProtectionPolicy",                 
                    Map.ofEntries(
                        Map.entry("policyType", "Full"),
                        Map.entry("retentionPolicy", Map.ofEntries(
                            Map.entry("monthlySchedule", Map.ofEntries(
                                Map.entry("retentionDuration", Map.ofEntries(
                                    Map.entry("count", 1),
                                    Map.entry("durationType", "Months")
                                )),
                                Map.entry("retentionScheduleFormatType", "Weekly"),
                                Map.entry("retentionScheduleWeekly", Map.ofEntries(
                                    Map.entry("daysOfTheWeek", "Sunday"),
                                    Map.entry("weeksOfTheMonth", "Second")
                                )),
                                Map.entry("retentionTimes", "2018-01-24T10:00:00Z")
                            )),
                            Map.entry("retentionPolicyType", "LongTermRetentionPolicy"),
                            Map.entry("weeklySchedule", Map.ofEntries(
                                Map.entry("daysOfTheWeek",                                 
                                    "Sunday",
                                    "Tuesday"),
                                Map.entry("retentionDuration", Map.ofEntries(
                                    Map.entry("count", 2),
                                    Map.entry("durationType", "Weeks")
                                )),
                                Map.entry("retentionTimes", "2018-01-24T10:00:00Z")
                            )),
                            Map.entry("yearlySchedule", Map.ofEntries(
                                Map.entry("monthsOfYear",                                 
                                    "January",
                                    "June",
                                    "December"),
                                Map.entry("retentionDuration", Map.ofEntries(
                                    Map.entry("count", 1),
                                    Map.entry("durationType", "Years")
                                )),
                                Map.entry("retentionScheduleFormatType", "Weekly"),
                                Map.entry("retentionScheduleWeekly", Map.ofEntries(
                                    Map.entry("daysOfTheWeek", "Sunday"),
                                    Map.entry("weeksOfTheMonth", "Last")
                                )),
                                Map.entry("retentionTimes", "2018-01-24T10:00:00Z")
                            ))
                        )),
                        Map.entry("schedulePolicy", Map.ofEntries(
                            Map.entry("schedulePolicyType", "SimpleSchedulePolicy"),
                            Map.entry("scheduleRunDays",                             
                                "Sunday",
                                "Tuesday"),
                            Map.entry("scheduleRunFrequency", "Weekly"),
                            Map.entry("scheduleRunTimes", "2018-01-24T10:00:00Z")
                        ))
                    ),
                    Map.ofEntries(
                        Map.entry("policyType", "Differential"),
                        Map.entry("retentionPolicy", Map.ofEntries(
                            Map.entry("retentionDuration", Map.ofEntries(
                                Map.entry("count", 8),
                                Map.entry("durationType", "Days")
                            )),
                            Map.entry("retentionPolicyType", "SimpleRetentionPolicy")
                        )),
                        Map.entry("schedulePolicy", Map.ofEntries(
                            Map.entry("schedulePolicyType", "SimpleSchedulePolicy"),
                            Map.entry("scheduleRunDays", "Friday"),
                            Map.entry("scheduleRunFrequency", "Weekly"),
                            Map.entry("scheduleRunTimes", "2018-01-24T10:00:00Z")
                        ))
                    ),
                    Map.ofEntries(
                        Map.entry("policyType", "Log"),
                        Map.entry("retentionPolicy", Map.ofEntries(
                            Map.entry("retentionDuration", Map.ofEntries(
                                Map.entry("count", 7),
                                Map.entry("durationType", "Days")
                            )),
                            Map.entry("retentionPolicyType", "SimpleRetentionPolicy")
                        )),
                        Map.entry("schedulePolicy", Map.ofEntries(
                            Map.entry("scheduleFrequencyInMins", 60),
                            Map.entry("schedulePolicyType", "LogSchedulePolicy")
                        ))
                    )),
                Map.entry("workLoadType", "SQLDataBase")
            ))
            .resourceGroupName("SwaggerTestRg")
            .vaultName("NetSDKTestRsVault")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const protectionPolicy = new azure_native.recoveryservices.ProtectionPolicy("protectionPolicy", {
    policyName: "testPolicy1",
    properties: {
        backupManagementType: "AzureWorkload",
        settings: {
            issqlcompression: false,
            timeZone: "Pacific Standard Time",
        },
        subProtectionPolicy: [
            {
                policyType: "Full",
                retentionPolicy: {
                    monthlySchedule: {
                        retentionDuration: {
                            count: 1,
                            durationType: "Months",
                        },
                        retentionScheduleFormatType: "Weekly",
                        retentionScheduleWeekly: {
                            daysOfTheWeek: [azure_native.recoveryservices.DayOfWeek.Sunday],
                            weeksOfTheMonth: [azure_native.recoveryservices.WeekOfMonth.Second],
                        },
                        retentionTimes: ["2018-01-24T10:00:00Z"],
                    },
                    retentionPolicyType: "LongTermRetentionPolicy",
                    weeklySchedule: {
                        daysOfTheWeek: [
                            azure_native.recoveryservices.DayOfWeek.Sunday,
                            azure_native.recoveryservices.DayOfWeek.Tuesday,
                        ],
                        retentionDuration: {
                            count: 2,
                            durationType: "Weeks",
                        },
                        retentionTimes: ["2018-01-24T10:00:00Z"],
                    },
                    yearlySchedule: {
                        monthsOfYear: [
                            azure_native.recoveryservices.MonthOfYear.January,
                            azure_native.recoveryservices.MonthOfYear.June,
                            azure_native.recoveryservices.MonthOfYear.December,
                        ],
                        retentionDuration: {
                            count: 1,
                            durationType: "Years",
                        },
                        retentionScheduleFormatType: "Weekly",
                        retentionScheduleWeekly: {
                            daysOfTheWeek: [azure_native.recoveryservices.DayOfWeek.Sunday],
                            weeksOfTheMonth: [azure_native.recoveryservices.WeekOfMonth.Last],
                        },
                        retentionTimes: ["2018-01-24T10:00:00Z"],
                    },
                },
                schedulePolicy: {
                    schedulePolicyType: "SimpleSchedulePolicy",
                    scheduleRunDays: [
                        azure_native.recoveryservices.DayOfWeek.Sunday,
                        azure_native.recoveryservices.DayOfWeek.Tuesday,
                    ],
                    scheduleRunFrequency: "Weekly",
                    scheduleRunTimes: ["2018-01-24T10:00:00Z"],
                },
            },
            {
                policyType: "Differential",
                retentionPolicy: {
                    retentionDuration: {
                        count: 8,
                        durationType: "Days",
                    },
                    retentionPolicyType: "SimpleRetentionPolicy",
                },
                schedulePolicy: {
                    schedulePolicyType: "SimpleSchedulePolicy",
                    scheduleRunDays: [azure_native.recoveryservices.DayOfWeek.Friday],
                    scheduleRunFrequency: "Weekly",
                    scheduleRunTimes: ["2018-01-24T10:00:00Z"],
                },
            },
            {
                policyType: "Log",
                retentionPolicy: {
                    retentionDuration: {
                        count: 7,
                        durationType: "Days",
                    },
                    retentionPolicyType: "SimpleRetentionPolicy",
                },
                schedulePolicy: {
                    scheduleFrequencyInMins: 60,
                    schedulePolicyType: "LogSchedulePolicy",
                },
            },
        ],
        workLoadType: "SQLDataBase",
    },
    resourceGroupName: "SwaggerTestRg",
    vaultName: "NetSDKTestRsVault",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

protection_policy = azure_native.recoveryservices.ProtectionPolicy("protectionPolicy",
    policy_name="testPolicy1",
    properties=azure_native.recoveryservices.AzureVmWorkloadProtectionPolicyArgs(
        backup_management_type="AzureWorkload",
        settings=azure_native.recoveryservices.SettingsArgs(
            issqlcompression=False,
            time_zone="Pacific Standard Time",
        ),
        sub_protection_policy=[
            azure_native.recoveryservices.SubProtectionPolicyArgs(
                policy_type="Full",
                retention_policy=azure_native.recoveryservices.LongTermRetentionPolicyArgs(
                    monthly_schedule=azure_native.recoveryservices.MonthlyRetentionScheduleArgs(
                        retention_duration=azure_native.recoveryservices.RetentionDurationArgs(
                            count=1,
                            duration_type="Months",
                        ),
                        retention_schedule_format_type="Weekly",
                        retention_schedule_weekly=azure_native.recoveryservices.WeeklyRetentionFormatArgs(
                            days_of_the_week=[azure_native.recoveryservices.DayOfWeek.SUNDAY],
                            weeks_of_the_month=[azure_native.recoveryservices.WeekOfMonth.SECOND],
                        ),
                        retention_times=["2018-01-24T10:00:00Z"],
                    ),
                    retention_policy_type="LongTermRetentionPolicy",
                    weekly_schedule=azure_native.recoveryservices.WeeklyRetentionScheduleArgs(
                        days_of_the_week=[
                            azure_native.recoveryservices.DayOfWeek.SUNDAY,
                            azure_native.recoveryservices.DayOfWeek.TUESDAY,
                        ],
                        retention_duration=azure_native.recoveryservices.RetentionDurationArgs(
                            count=2,
                            duration_type="Weeks",
                        ),
                        retention_times=["2018-01-24T10:00:00Z"],
                    ),
                    yearly_schedule=azure_native.recoveryservices.YearlyRetentionScheduleArgs(
                        months_of_year=[
                            azure_native.recoveryservices.MonthOfYear.JANUARY,
                            azure_native.recoveryservices.MonthOfYear.JUNE,
                            azure_native.recoveryservices.MonthOfYear.DECEMBER,
                        ],
                        retention_duration=azure_native.recoveryservices.RetentionDurationArgs(
                            count=1,
                            duration_type="Years",
                        ),
                        retention_schedule_format_type="Weekly",
                        retention_schedule_weekly=azure_native.recoveryservices.WeeklyRetentionFormatArgs(
                            days_of_the_week=[azure_native.recoveryservices.DayOfWeek.SUNDAY],
                            weeks_of_the_month=[azure_native.recoveryservices.WeekOfMonth.LAST],
                        ),
                        retention_times=["2018-01-24T10:00:00Z"],
                    ),
                ),
                schedule_policy=azure_native.recoveryservices.SimpleSchedulePolicyArgs(
                    schedule_policy_type="SimpleSchedulePolicy",
                    schedule_run_days=[
                        azure_native.recoveryservices.DayOfWeek.SUNDAY,
                        azure_native.recoveryservices.DayOfWeek.TUESDAY,
                    ],
                    schedule_run_frequency="Weekly",
                    schedule_run_times=["2018-01-24T10:00:00Z"],
                ),
            ),
            azure_native.recoveryservices.SubProtectionPolicyArgs(
                policy_type="Differential",
                retention_policy=azure_native.recoveryservices.SimpleRetentionPolicyArgs(
                    retention_duration=azure_native.recoveryservices.RetentionDurationArgs(
                        count=8,
                        duration_type="Days",
                    ),
                    retention_policy_type="SimpleRetentionPolicy",
                ),
                schedule_policy=azure_native.recoveryservices.SimpleSchedulePolicyArgs(
                    schedule_policy_type="SimpleSchedulePolicy",
                    schedule_run_days=[azure_native.recoveryservices.DayOfWeek.FRIDAY],
                    schedule_run_frequency="Weekly",
                    schedule_run_times=["2018-01-24T10:00:00Z"],
                ),
            ),
            azure_native.recoveryservices.SubProtectionPolicyArgs(
                policy_type="Log",
                retention_policy=azure_native.recoveryservices.SimpleRetentionPolicyArgs(
                    retention_duration=azure_native.recoveryservices.RetentionDurationArgs(
                        count=7,
                        duration_type="Days",
                    ),
                    retention_policy_type="SimpleRetentionPolicy",
                ),
                schedule_policy=azure_native.recoveryservices.LogSchedulePolicyArgs(
                    schedule_frequency_in_mins=60,
                    schedule_policy_type="LogSchedulePolicy",
                ),
            ),
        ],
        work_load_type="SQLDataBase",
    ),
    resource_group_name="SwaggerTestRg",
    vault_name="NetSDKTestRsVault")

```

```yaml
resources:
  protectionPolicy:
    type: azure-native:recoveryservices:ProtectionPolicy
    properties:
      policyName: testPolicy1
      properties:
        backupManagementType: AzureWorkload
        settings:
          issqlcompression: false
          timeZone: Pacific Standard Time
        subProtectionPolicy:
          - policyType: Full
            retentionPolicy:
              monthlySchedule:
                retentionDuration:
                  count: 1
                  durationType: Months
                retentionScheduleFormatType: Weekly
                retentionScheduleWeekly:
                  daysOfTheWeek:
                    - Sunday
                  weeksOfTheMonth:
                    - Second
                retentionTimes:
                  - 2018-01-24T10:00:00Z
              retentionPolicyType: LongTermRetentionPolicy
              weeklySchedule:
                daysOfTheWeek:
                  - Sunday
                  - Tuesday
                retentionDuration:
                  count: 2
                  durationType: Weeks
                retentionTimes:
                  - 2018-01-24T10:00:00Z
              yearlySchedule:
                monthsOfYear:
                  - January
                  - June
                  - December
                retentionDuration:
                  count: 1
                  durationType: Years
                retentionScheduleFormatType: Weekly
                retentionScheduleWeekly:
                  daysOfTheWeek:
                    - Sunday
                  weeksOfTheMonth:
                    - Last
                retentionTimes:
                  - 2018-01-24T10:00:00Z
            schedulePolicy:
              schedulePolicyType: SimpleSchedulePolicy
              scheduleRunDays:
                - Sunday
                - Tuesday
              scheduleRunFrequency: Weekly
              scheduleRunTimes:
                - 2018-01-24T10:00:00Z
          - policyType: Differential
            retentionPolicy:
              retentionDuration:
                count: 8
                durationType: Days
              retentionPolicyType: SimpleRetentionPolicy
            schedulePolicy:
              schedulePolicyType: SimpleSchedulePolicy
              scheduleRunDays:
                - Friday
              scheduleRunFrequency: Weekly
              scheduleRunTimes:
                - 2018-01-24T10:00:00Z
          - policyType: Log
            retentionPolicy:
              retentionDuration:
                count: 7
                durationType: Days
              retentionPolicyType: SimpleRetentionPolicy
            schedulePolicy:
              scheduleFrequencyInMins: 60
              schedulePolicyType: LogSchedulePolicy
        workLoadType: SQLDataBase
      resourceGroupName: SwaggerTestRg
      vaultName: NetSDKTestRsVault

```

{{% /example %}}
{{% example %}}
### Create or Update Hourly Azure Storage Protection Policy
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var protectionPolicy = new AzureNative.RecoveryServices.ProtectionPolicy("protectionPolicy", new()
    {
        PolicyName = "newPolicy2",
        Properties = new AzureNative.RecoveryServices.Inputs.AzureFileShareProtectionPolicyArgs
        {
            BackupManagementType = "AzureStorage",
            RetentionPolicy = new AzureNative.RecoveryServices.Inputs.LongTermRetentionPolicyArgs
            {
                DailySchedule = new AzureNative.RecoveryServices.Inputs.DailyRetentionScheduleArgs
                {
                    RetentionDuration = new AzureNative.RecoveryServices.Inputs.RetentionDurationArgs
                    {
                        Count = 5,
                        DurationType = "Days",
                    },
                },
                MonthlySchedule = new AzureNative.RecoveryServices.Inputs.MonthlyRetentionScheduleArgs
                {
                    RetentionDuration = new AzureNative.RecoveryServices.Inputs.RetentionDurationArgs
                    {
                        Count = 60,
                        DurationType = "Months",
                    },
                    RetentionScheduleFormatType = "Weekly",
                    RetentionScheduleWeekly = new AzureNative.RecoveryServices.Inputs.WeeklyRetentionFormatArgs
                    {
                        DaysOfTheWeek = new[]
                        {
                            AzureNative.RecoveryServices.DayOfWeek.Sunday,
                        },
                        WeeksOfTheMonth = new[]
                        {
                            AzureNative.RecoveryServices.WeekOfMonth.First,
                        },
                    },
                },
                RetentionPolicyType = "LongTermRetentionPolicy",
                WeeklySchedule = new AzureNative.RecoveryServices.Inputs.WeeklyRetentionScheduleArgs
                {
                    DaysOfTheWeek = new[]
                    {
                        AzureNative.RecoveryServices.DayOfWeek.Sunday,
                    },
                    RetentionDuration = new AzureNative.RecoveryServices.Inputs.RetentionDurationArgs
                    {
                        Count = 12,
                        DurationType = "Weeks",
                    },
                },
                YearlySchedule = new AzureNative.RecoveryServices.Inputs.YearlyRetentionScheduleArgs
                {
                    MonthsOfYear = new[]
                    {
                        AzureNative.RecoveryServices.MonthOfYear.January,
                    },
                    RetentionDuration = new AzureNative.RecoveryServices.Inputs.RetentionDurationArgs
                    {
                        Count = 10,
                        DurationType = "Years",
                    },
                    RetentionScheduleFormatType = "Weekly",
                    RetentionScheduleWeekly = new AzureNative.RecoveryServices.Inputs.WeeklyRetentionFormatArgs
                    {
                        DaysOfTheWeek = new[]
                        {
                            AzureNative.RecoveryServices.DayOfWeek.Sunday,
                        },
                        WeeksOfTheMonth = new[]
                        {
                            AzureNative.RecoveryServices.WeekOfMonth.First,
                        },
                    },
                },
            },
            SchedulePolicy = new AzureNative.RecoveryServices.Inputs.SimpleSchedulePolicyArgs
            {
                HourlySchedule = new AzureNative.RecoveryServices.Inputs.HourlyScheduleArgs
                {
                    Interval = 4,
                    ScheduleWindowDuration = 12,
                    ScheduleWindowStartTime = "2021-09-29T08:00:00.000Z",
                },
                SchedulePolicyType = "SimpleSchedulePolicy",
                ScheduleRunFrequency = "Hourly",
            },
            TimeZone = "UTC",
            WorkLoadType = "AzureFileShare",
        },
        ResourceGroupName = "SwaggerTestRg",
        VaultName = "swaggertestvault",
    });

});


```

```go
package main

import (
	recoveryservices "github.com/pulumi/pulumi-azure-native-sdk/recoveryservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := recoveryservices.NewProtectionPolicy(ctx, "protectionPolicy", &recoveryservices.ProtectionPolicyArgs{
			PolicyName: pulumi.String("newPolicy2"),
			Properties: recoveryservices.AzureFileShareProtectionPolicy{
				BackupManagementType: "AzureStorage",
				RetentionPolicy: recoveryservices.LongTermRetentionPolicy{
					DailySchedule: recoveryservices.DailyRetentionSchedule{
						RetentionDuration: recoveryservices.RetentionDuration{
							Count:        5,
							DurationType: "Days",
						},
					},
					MonthlySchedule: recoveryservices.MonthlyRetentionSchedule{
						RetentionDuration: recoveryservices.RetentionDuration{
							Count:        60,
							DurationType: "Months",
						},
						RetentionScheduleFormatType: "Weekly",
						RetentionScheduleWeekly: recoveryservices.WeeklyRetentionFormat{
							DaysOfTheWeek: []recoveryservices.DayOfWeek{
								recoveryservices.DayOfWeekSunday,
							},
							WeeksOfTheMonth: []recoveryservices.WeekOfMonth{
								recoveryservices.WeekOfMonthFirst,
							},
						},
					},
					RetentionPolicyType: "LongTermRetentionPolicy",
					WeeklySchedule: recoveryservices.WeeklyRetentionSchedule{
						DaysOfTheWeek: []recoveryservices.DayOfWeek{
							recoveryservices.DayOfWeekSunday,
						},
						RetentionDuration: recoveryservices.RetentionDuration{
							Count:        12,
							DurationType: "Weeks",
						},
					},
					YearlySchedule: recoveryservices.YearlyRetentionSchedule{
						MonthsOfYear: []recoveryservices.MonthOfYear{
							recoveryservices.MonthOfYearJanuary,
						},
						RetentionDuration: recoveryservices.RetentionDuration{
							Count:        10,
							DurationType: "Years",
						},
						RetentionScheduleFormatType: "Weekly",
						RetentionScheduleWeekly: recoveryservices.WeeklyRetentionFormat{
							DaysOfTheWeek: []recoveryservices.DayOfWeek{
								recoveryservices.DayOfWeekSunday,
							},
							WeeksOfTheMonth: []recoveryservices.WeekOfMonth{
								recoveryservices.WeekOfMonthFirst,
							},
						},
					},
				},
				SchedulePolicy: recoveryservices.SimpleSchedulePolicy{
					HourlySchedule: recoveryservices.HourlySchedule{
						Interval:                4,
						ScheduleWindowDuration:  12,
						ScheduleWindowStartTime: "2021-09-29T08:00:00.000Z",
					},
					SchedulePolicyType:   "SimpleSchedulePolicy",
					ScheduleRunFrequency: "Hourly",
				},
				TimeZone:     "UTC",
				WorkLoadType: "AzureFileShare",
			},
			ResourceGroupName: pulumi.String("SwaggerTestRg"),
			VaultName:         pulumi.String("swaggertestvault"),
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
import com.pulumi.azurenative.recoveryservices.ProtectionPolicy;
import com.pulumi.azurenative.recoveryservices.ProtectionPolicyArgs;
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
        var protectionPolicy = new ProtectionPolicy("protectionPolicy", ProtectionPolicyArgs.builder()        
            .policyName("newPolicy2")
            .properties(Map.ofEntries(
                Map.entry("backupManagementType", "AzureStorage"),
                Map.entry("retentionPolicy", Map.ofEntries(
                    Map.entry("dailySchedule", Map.of("retentionDuration", Map.ofEntries(
                        Map.entry("count", 5),
                        Map.entry("durationType", "Days")
                    ))),
                    Map.entry("monthlySchedule", Map.ofEntries(
                        Map.entry("retentionDuration", Map.ofEntries(
                            Map.entry("count", 60),
                            Map.entry("durationType", "Months")
                        )),
                        Map.entry("retentionScheduleFormatType", "Weekly"),
                        Map.entry("retentionScheduleWeekly", Map.ofEntries(
                            Map.entry("daysOfTheWeek", "Sunday"),
                            Map.entry("weeksOfTheMonth", "First")
                        ))
                    )),
                    Map.entry("retentionPolicyType", "LongTermRetentionPolicy"),
                    Map.entry("weeklySchedule", Map.ofEntries(
                        Map.entry("daysOfTheWeek", "Sunday"),
                        Map.entry("retentionDuration", Map.ofEntries(
                            Map.entry("count", 12),
                            Map.entry("durationType", "Weeks")
                        ))
                    )),
                    Map.entry("yearlySchedule", Map.ofEntries(
                        Map.entry("monthsOfYear", "January"),
                        Map.entry("retentionDuration", Map.ofEntries(
                            Map.entry("count", 10),
                            Map.entry("durationType", "Years")
                        )),
                        Map.entry("retentionScheduleFormatType", "Weekly"),
                        Map.entry("retentionScheduleWeekly", Map.ofEntries(
                            Map.entry("daysOfTheWeek", "Sunday"),
                            Map.entry("weeksOfTheMonth", "First")
                        ))
                    ))
                )),
                Map.entry("schedulePolicy", Map.ofEntries(
                    Map.entry("hourlySchedule", Map.ofEntries(
                        Map.entry("interval", 4),
                        Map.entry("scheduleWindowDuration", 12),
                        Map.entry("scheduleWindowStartTime", "2021-09-29T08:00:00.000Z")
                    )),
                    Map.entry("schedulePolicyType", "SimpleSchedulePolicy"),
                    Map.entry("scheduleRunFrequency", "Hourly")
                )),
                Map.entry("timeZone", "UTC"),
                Map.entry("workLoadType", "AzureFileShare")
            ))
            .resourceGroupName("SwaggerTestRg")
            .vaultName("swaggertestvault")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const protectionPolicy = new azure_native.recoveryservices.ProtectionPolicy("protectionPolicy", {
    policyName: "newPolicy2",
    properties: {
        backupManagementType: "AzureStorage",
        retentionPolicy: {
            dailySchedule: {
                retentionDuration: {
                    count: 5,
                    durationType: "Days",
                },
            },
            monthlySchedule: {
                retentionDuration: {
                    count: 60,
                    durationType: "Months",
                },
                retentionScheduleFormatType: "Weekly",
                retentionScheduleWeekly: {
                    daysOfTheWeek: [azure_native.recoveryservices.DayOfWeek.Sunday],
                    weeksOfTheMonth: [azure_native.recoveryservices.WeekOfMonth.First],
                },
            },
            retentionPolicyType: "LongTermRetentionPolicy",
            weeklySchedule: {
                daysOfTheWeek: [azure_native.recoveryservices.DayOfWeek.Sunday],
                retentionDuration: {
                    count: 12,
                    durationType: "Weeks",
                },
            },
            yearlySchedule: {
                monthsOfYear: [azure_native.recoveryservices.MonthOfYear.January],
                retentionDuration: {
                    count: 10,
                    durationType: "Years",
                },
                retentionScheduleFormatType: "Weekly",
                retentionScheduleWeekly: {
                    daysOfTheWeek: [azure_native.recoveryservices.DayOfWeek.Sunday],
                    weeksOfTheMonth: [azure_native.recoveryservices.WeekOfMonth.First],
                },
            },
        },
        schedulePolicy: {
            hourlySchedule: {
                interval: 4,
                scheduleWindowDuration: 12,
                scheduleWindowStartTime: "2021-09-29T08:00:00.000Z",
            },
            schedulePolicyType: "SimpleSchedulePolicy",
            scheduleRunFrequency: "Hourly",
        },
        timeZone: "UTC",
        workLoadType: "AzureFileShare",
    },
    resourceGroupName: "SwaggerTestRg",
    vaultName: "swaggertestvault",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

protection_policy = azure_native.recoveryservices.ProtectionPolicy("protectionPolicy",
    policy_name="newPolicy2",
    properties=azure_native.recoveryservices.AzureFileShareProtectionPolicyArgs(
        backup_management_type="AzureStorage",
        retention_policy=azure_native.recoveryservices.LongTermRetentionPolicyArgs(
            daily_schedule=azure_native.recoveryservices.DailyRetentionScheduleArgs(
                retention_duration=azure_native.recoveryservices.RetentionDurationArgs(
                    count=5,
                    duration_type="Days",
                ),
            ),
            monthly_schedule=azure_native.recoveryservices.MonthlyRetentionScheduleArgs(
                retention_duration=azure_native.recoveryservices.RetentionDurationArgs(
                    count=60,
                    duration_type="Months",
                ),
                retention_schedule_format_type="Weekly",
                retention_schedule_weekly=azure_native.recoveryservices.WeeklyRetentionFormatArgs(
                    days_of_the_week=[azure_native.recoveryservices.DayOfWeek.SUNDAY],
                    weeks_of_the_month=[azure_native.recoveryservices.WeekOfMonth.FIRST],
                ),
            ),
            retention_policy_type="LongTermRetentionPolicy",
            weekly_schedule=azure_native.recoveryservices.WeeklyRetentionScheduleArgs(
                days_of_the_week=[azure_native.recoveryservices.DayOfWeek.SUNDAY],
                retention_duration=azure_native.recoveryservices.RetentionDurationArgs(
                    count=12,
                    duration_type="Weeks",
                ),
            ),
            yearly_schedule=azure_native.recoveryservices.YearlyRetentionScheduleArgs(
                months_of_year=[azure_native.recoveryservices.MonthOfYear.JANUARY],
                retention_duration=azure_native.recoveryservices.RetentionDurationArgs(
                    count=10,
                    duration_type="Years",
                ),
                retention_schedule_format_type="Weekly",
                retention_schedule_weekly=azure_native.recoveryservices.WeeklyRetentionFormatArgs(
                    days_of_the_week=[azure_native.recoveryservices.DayOfWeek.SUNDAY],
                    weeks_of_the_month=[azure_native.recoveryservices.WeekOfMonth.FIRST],
                ),
            ),
        ),
        schedule_policy=azure_native.recoveryservices.SimpleSchedulePolicyArgs(
            hourly_schedule=azure_native.recoveryservices.HourlyScheduleArgs(
                interval=4,
                schedule_window_duration=12,
                schedule_window_start_time="2021-09-29T08:00:00.000Z",
            ),
            schedule_policy_type="SimpleSchedulePolicy",
            schedule_run_frequency="Hourly",
        ),
        time_zone="UTC",
        work_load_type="AzureFileShare",
    ),
    resource_group_name="SwaggerTestRg",
    vault_name="swaggertestvault")

```

```yaml
resources:
  protectionPolicy:
    type: azure-native:recoveryservices:ProtectionPolicy
    properties:
      policyName: newPolicy2
      properties:
        backupManagementType: AzureStorage
        retentionPolicy:
          dailySchedule:
            retentionDuration:
              count: 5
              durationType: Days
          monthlySchedule:
            retentionDuration:
              count: 60
              durationType: Months
            retentionScheduleFormatType: Weekly
            retentionScheduleWeekly:
              daysOfTheWeek:
                - Sunday
              weeksOfTheMonth:
                - First
          retentionPolicyType: LongTermRetentionPolicy
          weeklySchedule:
            daysOfTheWeek:
              - Sunday
            retentionDuration:
              count: 12
              durationType: Weeks
          yearlySchedule:
            monthsOfYear:
              - January
            retentionDuration:
              count: 10
              durationType: Years
            retentionScheduleFormatType: Weekly
            retentionScheduleWeekly:
              daysOfTheWeek:
                - Sunday
              weeksOfTheMonth:
                - First
        schedulePolicy:
          hourlySchedule:
            interval: 4
            scheduleWindowDuration: 12
            scheduleWindowStartTime: 2021-09-29T08:00:00.000Z
          schedulePolicyType: SimpleSchedulePolicy
          scheduleRunFrequency: Hourly
        timeZone: UTC
        workLoadType: AzureFileShare
      resourceGroupName: SwaggerTestRg
      vaultName: swaggertestvault

```

{{% /example %}}
{{% example %}}
### Create or Update Simple Azure Vm Protection Policy
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var protectionPolicy = new AzureNative.RecoveryServices.ProtectionPolicy("protectionPolicy", new()
    {
        PolicyName = "testPolicy1",
        Properties = new AzureNative.RecoveryServices.Inputs.AzureIaaSVMProtectionPolicyArgs
        {
            BackupManagementType = "AzureIaasVM",
            RetentionPolicy = new AzureNative.RecoveryServices.Inputs.LongTermRetentionPolicyArgs
            {
                DailySchedule = new AzureNative.RecoveryServices.Inputs.DailyRetentionScheduleArgs
                {
                    RetentionDuration = new AzureNative.RecoveryServices.Inputs.RetentionDurationArgs
                    {
                        Count = 1,
                        DurationType = "Days",
                    },
                    RetentionTimes = new[]
                    {
                        "2018-01-24T02:00:00Z",
                    },
                },
                RetentionPolicyType = "LongTermRetentionPolicy",
            },
            SchedulePolicy = new AzureNative.RecoveryServices.Inputs.SimpleSchedulePolicyArgs
            {
                SchedulePolicyType = "SimpleSchedulePolicy",
                ScheduleRunFrequency = "Daily",
                ScheduleRunTimes = new[]
                {
                    "2018-01-24T02:00:00Z",
                },
            },
            TimeZone = "Pacific Standard Time",
        },
        ResourceGroupName = "SwaggerTestRg",
        VaultName = "NetSDKTestRsVault",
    });

});


```

```go
package main

import (
	recoveryservices "github.com/pulumi/pulumi-azure-native-sdk/recoveryservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := recoveryservices.NewProtectionPolicy(ctx, "protectionPolicy", &recoveryservices.ProtectionPolicyArgs{
			PolicyName: pulumi.String("testPolicy1"),
			Properties: recoveryservices.AzureIaaSVMProtectionPolicy{
				BackupManagementType: "AzureIaasVM",
				RetentionPolicy: recoveryservices.LongTermRetentionPolicy{
					DailySchedule: recoveryservices.DailyRetentionSchedule{
						RetentionDuration: recoveryservices.RetentionDuration{
							Count:        1,
							DurationType: "Days",
						},
						RetentionTimes: []string{
							"2018-01-24T02:00:00Z",
						},
					},
					RetentionPolicyType: "LongTermRetentionPolicy",
				},
				SchedulePolicy: recoveryservices.SimpleSchedulePolicy{
					SchedulePolicyType:   "SimpleSchedulePolicy",
					ScheduleRunFrequency: "Daily",
					ScheduleRunTimes: []string{
						"2018-01-24T02:00:00Z",
					},
				},
				TimeZone: "Pacific Standard Time",
			},
			ResourceGroupName: pulumi.String("SwaggerTestRg"),
			VaultName:         pulumi.String("NetSDKTestRsVault"),
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
import com.pulumi.azurenative.recoveryservices.ProtectionPolicy;
import com.pulumi.azurenative.recoveryservices.ProtectionPolicyArgs;
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
        var protectionPolicy = new ProtectionPolicy("protectionPolicy", ProtectionPolicyArgs.builder()        
            .policyName("testPolicy1")
            .properties(Map.ofEntries(
                Map.entry("backupManagementType", "AzureIaasVM"),
                Map.entry("retentionPolicy", Map.ofEntries(
                    Map.entry("dailySchedule", Map.ofEntries(
                        Map.entry("retentionDuration", Map.ofEntries(
                            Map.entry("count", 1),
                            Map.entry("durationType", "Days")
                        )),
                        Map.entry("retentionTimes", "2018-01-24T02:00:00Z")
                    )),
                    Map.entry("retentionPolicyType", "LongTermRetentionPolicy")
                )),
                Map.entry("schedulePolicy", Map.ofEntries(
                    Map.entry("schedulePolicyType", "SimpleSchedulePolicy"),
                    Map.entry("scheduleRunFrequency", "Daily"),
                    Map.entry("scheduleRunTimes", "2018-01-24T02:00:00Z")
                )),
                Map.entry("timeZone", "Pacific Standard Time")
            ))
            .resourceGroupName("SwaggerTestRg")
            .vaultName("NetSDKTestRsVault")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const protectionPolicy = new azure_native.recoveryservices.ProtectionPolicy("protectionPolicy", {
    policyName: "testPolicy1",
    properties: {
        backupManagementType: "AzureIaasVM",
        retentionPolicy: {
            dailySchedule: {
                retentionDuration: {
                    count: 1,
                    durationType: "Days",
                },
                retentionTimes: ["2018-01-24T02:00:00Z"],
            },
            retentionPolicyType: "LongTermRetentionPolicy",
        },
        schedulePolicy: {
            schedulePolicyType: "SimpleSchedulePolicy",
            scheduleRunFrequency: "Daily",
            scheduleRunTimes: ["2018-01-24T02:00:00Z"],
        },
        timeZone: "Pacific Standard Time",
    },
    resourceGroupName: "SwaggerTestRg",
    vaultName: "NetSDKTestRsVault",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

protection_policy = azure_native.recoveryservices.ProtectionPolicy("protectionPolicy",
    policy_name="testPolicy1",
    properties=azure_native.recoveryservices.AzureIaaSVMProtectionPolicyArgs(
        backup_management_type="AzureIaasVM",
        retention_policy=azure_native.recoveryservices.LongTermRetentionPolicyArgs(
            daily_schedule=azure_native.recoveryservices.DailyRetentionScheduleArgs(
                retention_duration=azure_native.recoveryservices.RetentionDurationArgs(
                    count=1,
                    duration_type="Days",
                ),
                retention_times=["2018-01-24T02:00:00Z"],
            ),
            retention_policy_type="LongTermRetentionPolicy",
        ),
        schedule_policy=azure_native.recoveryservices.SimpleSchedulePolicyArgs(
            schedule_policy_type="SimpleSchedulePolicy",
            schedule_run_frequency="Daily",
            schedule_run_times=["2018-01-24T02:00:00Z"],
        ),
        time_zone="Pacific Standard Time",
    ),
    resource_group_name="SwaggerTestRg",
    vault_name="NetSDKTestRsVault")

```

```yaml
resources:
  protectionPolicy:
    type: azure-native:recoveryservices:ProtectionPolicy
    properties:
      policyName: testPolicy1
      properties:
        backupManagementType: AzureIaasVM
        retentionPolicy:
          dailySchedule:
            retentionDuration:
              count: 1
              durationType: Days
            retentionTimes:
              - 2018-01-24T02:00:00Z
          retentionPolicyType: LongTermRetentionPolicy
        schedulePolicy:
          schedulePolicyType: SimpleSchedulePolicy
          scheduleRunFrequency: Daily
          scheduleRunTimes:
            - 2018-01-24T02:00:00Z
        timeZone: Pacific Standard Time
      resourceGroupName: SwaggerTestRg
      vaultName: NetSDKTestRsVault

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:recoveryservices:ProtectionPolicy testPolicy1 /Subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/SwaggerTestRg/providers/Microsoft.RecoveryServices/vaults/NetSDKTestRsVault/backupPolicies/testPolicy1 
```
