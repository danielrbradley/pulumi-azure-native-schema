Represents a ScalingPlanPooledSchedule definition.
API Version: 2022-09-09.
Previous API Version: 2022-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ScalingPlanPooledSchedules_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var scalingPlanPooledSchedule = new AzureNative.DesktopVirtualization.ScalingPlanPooledSchedule("scalingPlanPooledSchedule", new()
    {
        DaysOfWeek = new[]
        {
            "Monday",
            "Tuesday",
            "Wednesday",
            "Thursday",
            "Friday",
        },
        OffPeakLoadBalancingAlgorithm = "DepthFirst",
        OffPeakStartTime = new AzureNative.DesktopVirtualization.Inputs.TimeArgs
        {
            Hour = 20,
            Minute = 0,
        },
        PeakLoadBalancingAlgorithm = "BreadthFirst",
        PeakStartTime = new AzureNative.DesktopVirtualization.Inputs.TimeArgs
        {
            Hour = 8,
            Minute = 0,
        },
        RampDownCapacityThresholdPct = 50,
        RampDownForceLogoffUsers = true,
        RampDownLoadBalancingAlgorithm = "DepthFirst",
        RampDownMinimumHostsPct = 20,
        RampDownNotificationMessage = "message",
        RampDownStartTime = new AzureNative.DesktopVirtualization.Inputs.TimeArgs
        {
            Hour = 18,
            Minute = 0,
        },
        RampDownWaitTimeMinutes = 30,
        RampUpCapacityThresholdPct = 80,
        RampUpLoadBalancingAlgorithm = "DepthFirst",
        RampUpMinimumHostsPct = 20,
        RampUpStartTime = new AzureNative.DesktopVirtualization.Inputs.TimeArgs
        {
            Hour = 6,
            Minute = 0,
        },
        ResourceGroupName = "resourceGroup1",
        ScalingPlanName = "scalingPlan1",
        ScalingPlanScheduleName = "scalingPlanScheduleWeekdays1",
    });

});


```

```go
package main

import (
	desktopvirtualization "github.com/pulumi/pulumi-azure-native-sdk/desktopvirtualization"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := desktopvirtualization.NewScalingPlanPooledSchedule(ctx, "scalingPlanPooledSchedule", &desktopvirtualization.ScalingPlanPooledScheduleArgs{
			DaysOfWeek: pulumi.StringArray{
				pulumi.String("Monday"),
				pulumi.String("Tuesday"),
				pulumi.String("Wednesday"),
				pulumi.String("Thursday"),
				pulumi.String("Friday"),
			},
			OffPeakLoadBalancingAlgorithm: pulumi.String("DepthFirst"),
			OffPeakStartTime: &desktopvirtualization.TimeArgs{
				Hour:   pulumi.Int(20),
				Minute: pulumi.Int(0),
			},
			PeakLoadBalancingAlgorithm: pulumi.String("BreadthFirst"),
			PeakStartTime: &desktopvirtualization.TimeArgs{
				Hour:   pulumi.Int(8),
				Minute: pulumi.Int(0),
			},
			RampDownCapacityThresholdPct:   pulumi.Int(50),
			RampDownForceLogoffUsers:       pulumi.Bool(true),
			RampDownLoadBalancingAlgorithm: pulumi.String("DepthFirst"),
			RampDownMinimumHostsPct:        pulumi.Int(20),
			RampDownNotificationMessage:    pulumi.String("message"),
			RampDownStartTime: &desktopvirtualization.TimeArgs{
				Hour:   pulumi.Int(18),
				Minute: pulumi.Int(0),
			},
			RampDownWaitTimeMinutes:      pulumi.Int(30),
			RampUpCapacityThresholdPct:   pulumi.Int(80),
			RampUpLoadBalancingAlgorithm: pulumi.String("DepthFirst"),
			RampUpMinimumHostsPct:        pulumi.Int(20),
			RampUpStartTime: &desktopvirtualization.TimeArgs{
				Hour:   pulumi.Int(6),
				Minute: pulumi.Int(0),
			},
			ResourceGroupName:       pulumi.String("resourceGroup1"),
			ScalingPlanName:         pulumi.String("scalingPlan1"),
			ScalingPlanScheduleName: pulumi.String("scalingPlanScheduleWeekdays1"),
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
import com.pulumi.azurenative.desktopvirtualization.ScalingPlanPooledSchedule;
import com.pulumi.azurenative.desktopvirtualization.ScalingPlanPooledScheduleArgs;
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
        var scalingPlanPooledSchedule = new ScalingPlanPooledSchedule("scalingPlanPooledSchedule", ScalingPlanPooledScheduleArgs.builder()        
            .daysOfWeek(            
                "Monday",
                "Tuesday",
                "Wednesday",
                "Thursday",
                "Friday")
            .offPeakLoadBalancingAlgorithm("DepthFirst")
            .offPeakStartTime(Map.ofEntries(
                Map.entry("hour", 20),
                Map.entry("minute", 0)
            ))
            .peakLoadBalancingAlgorithm("BreadthFirst")
            .peakStartTime(Map.ofEntries(
                Map.entry("hour", 8),
                Map.entry("minute", 0)
            ))
            .rampDownCapacityThresholdPct(50)
            .rampDownForceLogoffUsers(true)
            .rampDownLoadBalancingAlgorithm("DepthFirst")
            .rampDownMinimumHostsPct(20)
            .rampDownNotificationMessage("message")
            .rampDownStartTime(Map.ofEntries(
                Map.entry("hour", 18),
                Map.entry("minute", 0)
            ))
            .rampDownWaitTimeMinutes(30)
            .rampUpCapacityThresholdPct(80)
            .rampUpLoadBalancingAlgorithm("DepthFirst")
            .rampUpMinimumHostsPct(20)
            .rampUpStartTime(Map.ofEntries(
                Map.entry("hour", 6),
                Map.entry("minute", 0)
            ))
            .resourceGroupName("resourceGroup1")
            .scalingPlanName("scalingPlan1")
            .scalingPlanScheduleName("scalingPlanScheduleWeekdays1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const scalingPlanPooledSchedule = new azure_native.desktopvirtualization.ScalingPlanPooledSchedule("scalingPlanPooledSchedule", {
    daysOfWeek: [
        "Monday",
        "Tuesday",
        "Wednesday",
        "Thursday",
        "Friday",
    ],
    offPeakLoadBalancingAlgorithm: "DepthFirst",
    offPeakStartTime: {
        hour: 20,
        minute: 0,
    },
    peakLoadBalancingAlgorithm: "BreadthFirst",
    peakStartTime: {
        hour: 8,
        minute: 0,
    },
    rampDownCapacityThresholdPct: 50,
    rampDownForceLogoffUsers: true,
    rampDownLoadBalancingAlgorithm: "DepthFirst",
    rampDownMinimumHostsPct: 20,
    rampDownNotificationMessage: "message",
    rampDownStartTime: {
        hour: 18,
        minute: 0,
    },
    rampDownWaitTimeMinutes: 30,
    rampUpCapacityThresholdPct: 80,
    rampUpLoadBalancingAlgorithm: "DepthFirst",
    rampUpMinimumHostsPct: 20,
    rampUpStartTime: {
        hour: 6,
        minute: 0,
    },
    resourceGroupName: "resourceGroup1",
    scalingPlanName: "scalingPlan1",
    scalingPlanScheduleName: "scalingPlanScheduleWeekdays1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

scaling_plan_pooled_schedule = azure_native.desktopvirtualization.ScalingPlanPooledSchedule("scalingPlanPooledSchedule",
    days_of_week=[
        "Monday",
        "Tuesday",
        "Wednesday",
        "Thursday",
        "Friday",
    ],
    off_peak_load_balancing_algorithm="DepthFirst",
    off_peak_start_time=azure_native.desktopvirtualization.TimeArgs(
        hour=20,
        minute=0,
    ),
    peak_load_balancing_algorithm="BreadthFirst",
    peak_start_time=azure_native.desktopvirtualization.TimeArgs(
        hour=8,
        minute=0,
    ),
    ramp_down_capacity_threshold_pct=50,
    ramp_down_force_logoff_users=True,
    ramp_down_load_balancing_algorithm="DepthFirst",
    ramp_down_minimum_hosts_pct=20,
    ramp_down_notification_message="message",
    ramp_down_start_time=azure_native.desktopvirtualization.TimeArgs(
        hour=18,
        minute=0,
    ),
    ramp_down_wait_time_minutes=30,
    ramp_up_capacity_threshold_pct=80,
    ramp_up_load_balancing_algorithm="DepthFirst",
    ramp_up_minimum_hosts_pct=20,
    ramp_up_start_time=azure_native.desktopvirtualization.TimeArgs(
        hour=6,
        minute=0,
    ),
    resource_group_name="resourceGroup1",
    scaling_plan_name="scalingPlan1",
    scaling_plan_schedule_name="scalingPlanScheduleWeekdays1")

```

```yaml
resources:
  scalingPlanPooledSchedule:
    type: azure-native:desktopvirtualization:ScalingPlanPooledSchedule
    properties:
      daysOfWeek:
        - Monday
        - Tuesday
        - Wednesday
        - Thursday
        - Friday
      offPeakLoadBalancingAlgorithm: DepthFirst
      offPeakStartTime:
        hour: 20
        minute: 0
      peakLoadBalancingAlgorithm: BreadthFirst
      peakStartTime:
        hour: 8
        minute: 0
      rampDownCapacityThresholdPct: 50
      rampDownForceLogoffUsers: true
      rampDownLoadBalancingAlgorithm: DepthFirst
      rampDownMinimumHostsPct: 20
      rampDownNotificationMessage: message
      rampDownStartTime:
        hour: 18
        minute: 0
      rampDownWaitTimeMinutes: 30
      rampUpCapacityThresholdPct: 80
      rampUpLoadBalancingAlgorithm: DepthFirst
      rampUpMinimumHostsPct: 20
      rampUpStartTime:
        hour: 6
        minute: 0
      resourceGroupName: resourceGroup1
      scalingPlanName: scalingPlan1
      scalingPlanScheduleName: scalingPlanScheduleWeekdays1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:desktopvirtualization:ScalingPlanPooledSchedule scalingPlanScheduleWeekdays1 /subscriptions/daefabc0-95b4-48b3-b645-8a753a63c4fa/resourceGroups/resourceGroup1/providers/Microsoft.DesktopVirtualization/scalingPlans/scalingPlan1/pooledSchedules/scalingPlanScheduleWeekdays1 
```
