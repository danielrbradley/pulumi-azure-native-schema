Represents a scaling plan definition.
API Version: 2022-09-09.
Previous API Version: 2021-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ScalingPlans_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var scalingPlan = new AzureNative.DesktopVirtualization.ScalingPlan("scalingPlan", new()
    {
        Description = "Description of Scaling Plan",
        ExclusionTag = "value",
        FriendlyName = "Scaling Plan 1",
        HostPoolReferences = new[]
        {
            new AzureNative.DesktopVirtualization.Inputs.ScalingHostPoolReferenceArgs
            {
                HostPoolArmPath = "/subscriptions/daefabc0-95b4-48b3-b645-8a753a63c4fa/resourceGroups/resourceGroup1/providers/Microsoft.DesktopVirtualization/hostPools/hostPool1",
                ScalingPlanEnabled = true,
            },
        },
        HostPoolType = "Pooled",
        Location = "centralus",
        ResourceGroupName = "resourceGroup1",
        ScalingPlanName = "scalingPlan1",
        Schedules = new[]
        {
            new AzureNative.DesktopVirtualization.Inputs.ScalingScheduleArgs
            {
                DaysOfWeek = new[]
                {
                    "Monday",
                    "Tuesday",
                    "Wednesday",
                    "Thursday",
                    "Friday",
                },
                Name = "schedule1",
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
            },
        },
        Tags = 
        {
            { "tag1", "value1" },
            { "tag2", "value2" },
        },
        TimeZone = "Central Standard Time",
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
		_, err := desktopvirtualization.NewScalingPlan(ctx, "scalingPlan", &desktopvirtualization.ScalingPlanArgs{
			Description:  pulumi.String("Description of Scaling Plan"),
			ExclusionTag: pulumi.String("value"),
			FriendlyName: pulumi.String("Scaling Plan 1"),
			HostPoolReferences: []desktopvirtualization.ScalingHostPoolReferenceArgs{
				{
					HostPoolArmPath:    pulumi.String("/subscriptions/daefabc0-95b4-48b3-b645-8a753a63c4fa/resourceGroups/resourceGroup1/providers/Microsoft.DesktopVirtualization/hostPools/hostPool1"),
					ScalingPlanEnabled: pulumi.Bool(true),
				},
			},
			HostPoolType:      pulumi.String("Pooled"),
			Location:          pulumi.String("centralus"),
			ResourceGroupName: pulumi.String("resourceGroup1"),
			ScalingPlanName:   pulumi.String("scalingPlan1"),
			Schedules: []desktopvirtualization.ScalingScheduleArgs{
				{
					DaysOfWeek: pulumi.StringArray{
						pulumi.String("Monday"),
						pulumi.String("Tuesday"),
						pulumi.String("Wednesday"),
						pulumi.String("Thursday"),
						pulumi.String("Friday"),
					},
					Name:                          pulumi.String("schedule1"),
					OffPeakLoadBalancingAlgorithm: pulumi.String("DepthFirst"),
					OffPeakStartTime: {
						Hour:   pulumi.Int(20),
						Minute: pulumi.Int(0),
					},
					PeakLoadBalancingAlgorithm: pulumi.String("BreadthFirst"),
					PeakStartTime: {
						Hour:   pulumi.Int(8),
						Minute: pulumi.Int(0),
					},
					RampDownCapacityThresholdPct:   pulumi.Int(50),
					RampDownForceLogoffUsers:       pulumi.Bool(true),
					RampDownLoadBalancingAlgorithm: pulumi.String("DepthFirst"),
					RampDownMinimumHostsPct:        pulumi.Int(20),
					RampDownNotificationMessage:    pulumi.String("message"),
					RampDownStartTime: {
						Hour:   pulumi.Int(18),
						Minute: pulumi.Int(0),
					},
					RampDownWaitTimeMinutes:      pulumi.Int(30),
					RampUpCapacityThresholdPct:   pulumi.Int(80),
					RampUpLoadBalancingAlgorithm: pulumi.String("DepthFirst"),
					RampUpMinimumHostsPct:        pulumi.Int(20),
					RampUpStartTime: {
						Hour:   pulumi.Int(6),
						Minute: pulumi.Int(0),
					},
				},
			},
			Tags: pulumi.StringMap{
				"tag1": pulumi.String("value1"),
				"tag2": pulumi.String("value2"),
			},
			TimeZone: pulumi.String("Central Standard Time"),
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
import com.pulumi.azurenative.desktopvirtualization.ScalingPlan;
import com.pulumi.azurenative.desktopvirtualization.ScalingPlanArgs;
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
        var scalingPlan = new ScalingPlan("scalingPlan", ScalingPlanArgs.builder()        
            .description("Description of Scaling Plan")
            .exclusionTag("value")
            .friendlyName("Scaling Plan 1")
            .hostPoolReferences(Map.ofEntries(
                Map.entry("hostPoolArmPath", "/subscriptions/daefabc0-95b4-48b3-b645-8a753a63c4fa/resourceGroups/resourceGroup1/providers/Microsoft.DesktopVirtualization/hostPools/hostPool1"),
                Map.entry("scalingPlanEnabled", true)
            ))
            .hostPoolType("Pooled")
            .location("centralus")
            .resourceGroupName("resourceGroup1")
            .scalingPlanName("scalingPlan1")
            .schedules(Map.ofEntries(
                Map.entry("daysOfWeek",                 
                    "Monday",
                    "Tuesday",
                    "Wednesday",
                    "Thursday",
                    "Friday"),
                Map.entry("name", "schedule1"),
                Map.entry("offPeakLoadBalancingAlgorithm", "DepthFirst"),
                Map.entry("offPeakStartTime", Map.ofEntries(
                    Map.entry("hour", 20),
                    Map.entry("minute", 0)
                )),
                Map.entry("peakLoadBalancingAlgorithm", "BreadthFirst"),
                Map.entry("peakStartTime", Map.ofEntries(
                    Map.entry("hour", 8),
                    Map.entry("minute", 0)
                )),
                Map.entry("rampDownCapacityThresholdPct", 50),
                Map.entry("rampDownForceLogoffUsers", true),
                Map.entry("rampDownLoadBalancingAlgorithm", "DepthFirst"),
                Map.entry("rampDownMinimumHostsPct", 20),
                Map.entry("rampDownNotificationMessage", "message"),
                Map.entry("rampDownStartTime", Map.ofEntries(
                    Map.entry("hour", 18),
                    Map.entry("minute", 0)
                )),
                Map.entry("rampDownWaitTimeMinutes", 30),
                Map.entry("rampUpCapacityThresholdPct", 80),
                Map.entry("rampUpLoadBalancingAlgorithm", "DepthFirst"),
                Map.entry("rampUpMinimumHostsPct", 20),
                Map.entry("rampUpStartTime", Map.ofEntries(
                    Map.entry("hour", 6),
                    Map.entry("minute", 0)
                ))
            ))
            .tags(Map.ofEntries(
                Map.entry("tag1", "value1"),
                Map.entry("tag2", "value2")
            ))
            .timeZone("Central Standard Time")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const scalingPlan = new azure_native.desktopvirtualization.ScalingPlan("scalingPlan", {
    description: "Description of Scaling Plan",
    exclusionTag: "value",
    friendlyName: "Scaling Plan 1",
    hostPoolReferences: [{
        hostPoolArmPath: "/subscriptions/daefabc0-95b4-48b3-b645-8a753a63c4fa/resourceGroups/resourceGroup1/providers/Microsoft.DesktopVirtualization/hostPools/hostPool1",
        scalingPlanEnabled: true,
    }],
    hostPoolType: "Pooled",
    location: "centralus",
    resourceGroupName: "resourceGroup1",
    scalingPlanName: "scalingPlan1",
    schedules: [{
        daysOfWeek: [
            "Monday",
            "Tuesday",
            "Wednesday",
            "Thursday",
            "Friday",
        ],
        name: "schedule1",
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
    }],
    tags: {
        tag1: "value1",
        tag2: "value2",
    },
    timeZone: "Central Standard Time",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

scaling_plan = azure_native.desktopvirtualization.ScalingPlan("scalingPlan",
    description="Description of Scaling Plan",
    exclusion_tag="value",
    friendly_name="Scaling Plan 1",
    host_pool_references=[azure_native.desktopvirtualization.ScalingHostPoolReferenceArgs(
        host_pool_arm_path="/subscriptions/daefabc0-95b4-48b3-b645-8a753a63c4fa/resourceGroups/resourceGroup1/providers/Microsoft.DesktopVirtualization/hostPools/hostPool1",
        scaling_plan_enabled=True,
    )],
    host_pool_type="Pooled",
    location="centralus",
    resource_group_name="resourceGroup1",
    scaling_plan_name="scalingPlan1",
    schedules=[{
        "daysOfWeek": [
            "Monday",
            "Tuesday",
            "Wednesday",
            "Thursday",
            "Friday",
        ],
        "name": "schedule1",
        "offPeakLoadBalancingAlgorithm": "DepthFirst",
        "offPeakStartTime": azure_native.desktopvirtualization.TimeArgs(
            hour=20,
            minute=0,
        ),
        "peakLoadBalancingAlgorithm": "BreadthFirst",
        "peakStartTime": azure_native.desktopvirtualization.TimeArgs(
            hour=8,
            minute=0,
        ),
        "rampDownCapacityThresholdPct": 50,
        "rampDownForceLogoffUsers": True,
        "rampDownLoadBalancingAlgorithm": "DepthFirst",
        "rampDownMinimumHostsPct": 20,
        "rampDownNotificationMessage": "message",
        "rampDownStartTime": azure_native.desktopvirtualization.TimeArgs(
            hour=18,
            minute=0,
        ),
        "rampDownWaitTimeMinutes": 30,
        "rampUpCapacityThresholdPct": 80,
        "rampUpLoadBalancingAlgorithm": "DepthFirst",
        "rampUpMinimumHostsPct": 20,
        "rampUpStartTime": azure_native.desktopvirtualization.TimeArgs(
            hour=6,
            minute=0,
        ),
    }],
    tags={
        "tag1": "value1",
        "tag2": "value2",
    },
    time_zone="Central Standard Time")

```

```yaml
resources:
  scalingPlan:
    type: azure-native:desktopvirtualization:ScalingPlan
    properties:
      description: Description of Scaling Plan
      exclusionTag: value
      friendlyName: Scaling Plan 1
      hostPoolReferences:
        - hostPoolArmPath: /subscriptions/daefabc0-95b4-48b3-b645-8a753a63c4fa/resourceGroups/resourceGroup1/providers/Microsoft.DesktopVirtualization/hostPools/hostPool1
          scalingPlanEnabled: true
      hostPoolType: Pooled
      location: centralus
      resourceGroupName: resourceGroup1
      scalingPlanName: scalingPlan1
      schedules:
        - daysOfWeek:
            - Monday
            - Tuesday
            - Wednesday
            - Thursday
            - Friday
          name: schedule1
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
      tags:
        tag1: value1
        tag2: value2
      timeZone: Central Standard Time

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:desktopvirtualization:ScalingPlan scalingPlan1 /subscriptions/daefabc0-95b4-48b3-b645-8a753a63c4fa/resourceGroups/resourceGroup1/providers/Microsoft.DesktopVirtualization/scalingPlans/scalingPlan1 
```
