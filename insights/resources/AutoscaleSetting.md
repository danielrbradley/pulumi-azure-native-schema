The autoscale setting resource.
API Version: 2022-10-01.
Previous API Version: 2015-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update an autoscale setting
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var autoscaleSetting = new AzureNative.Insights.AutoscaleSetting("autoscaleSetting", new()
    {
        AutoscaleSettingName = "MySetting",
        Enabled = true,
        Location = "West US",
        Notifications = new[]
        {
            new AzureNative.Insights.Inputs.AutoscaleNotificationArgs
            {
                Email = new AzureNative.Insights.Inputs.EmailNotificationArgs
                {
                    CustomEmails = new[]
                    {
                        "gu@ms.com",
                        "ge@ns.net",
                    },
                    SendToSubscriptionAdministrator = true,
                    SendToSubscriptionCoAdministrators = true,
                },
                Operation = AzureNative.Insights.OperationType.Scale,
                Webhooks = new[]
                {
                    new AzureNative.Insights.Inputs.WebhookNotificationArgs
                    {
                        Properties = null,
                        ServiceUri = "http://myservice.com",
                    },
                },
            },
        },
        PredictiveAutoscalePolicy = new AzureNative.Insights.Inputs.PredictiveAutoscalePolicyArgs
        {
            ScaleMode = AzureNative.Insights.PredictiveAutoscalePolicyScaleMode.Enabled,
        },
        Profiles = new[]
        {
            new AzureNative.Insights.Inputs.AutoscaleProfileArgs
            {
                Capacity = new AzureNative.Insights.Inputs.ScaleCapacityArgs
                {
                    Default = "1",
                    Maximum = "10",
                    Minimum = "1",
                },
                FixedDate = new AzureNative.Insights.Inputs.TimeWindowArgs
                {
                    End = "2015-03-05T14:30:00Z",
                    Start = "2015-03-05T14:00:00Z",
                    TimeZone = "UTC",
                },
                Name = "adios",
                Rules = new[]
                {
                    new AzureNative.Insights.Inputs.ScaleRuleArgs
                    {
                        MetricTrigger = new AzureNative.Insights.Inputs.MetricTriggerArgs
                        {
                            DividePerInstance = false,
                            MetricName = "Percentage CPU",
                            MetricResourceUri = "/subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/TestingMetricsScaleSet/providers/Microsoft.Compute/virtualMachineScaleSets/testingsc",
                            Operator = AzureNative.Insights.ComparisonOperationType.GreaterThan,
                            Statistic = AzureNative.Insights.MetricStatisticType.Average,
                            Threshold = 10,
                            TimeAggregation = AzureNative.Insights.TimeAggregationType.Average,
                            TimeGrain = "PT1M",
                            TimeWindow = "PT5M",
                        },
                        ScaleAction = new AzureNative.Insights.Inputs.ScaleActionArgs
                        {
                            Cooldown = "PT5M",
                            Direction = AzureNative.Insights.ScaleDirection.Increase,
                            Type = AzureNative.Insights.ScaleType.ChangeCount,
                            Value = "1",
                        },
                    },
                    new AzureNative.Insights.Inputs.ScaleRuleArgs
                    {
                        MetricTrigger = new AzureNative.Insights.Inputs.MetricTriggerArgs
                        {
                            DividePerInstance = false,
                            MetricName = "Percentage CPU",
                            MetricResourceUri = "/subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/TestingMetricsScaleSet/providers/Microsoft.Compute/virtualMachineScaleSets/testingsc",
                            Operator = AzureNative.Insights.ComparisonOperationType.GreaterThan,
                            Statistic = AzureNative.Insights.MetricStatisticType.Average,
                            Threshold = 15,
                            TimeAggregation = AzureNative.Insights.TimeAggregationType.Average,
                            TimeGrain = "PT2M",
                            TimeWindow = "PT5M",
                        },
                        ScaleAction = new AzureNative.Insights.Inputs.ScaleActionArgs
                        {
                            Cooldown = "PT6M",
                            Direction = AzureNative.Insights.ScaleDirection.Decrease,
                            Type = AzureNative.Insights.ScaleType.ChangeCount,
                            Value = "2",
                        },
                    },
                },
            },
            new AzureNative.Insights.Inputs.AutoscaleProfileArgs
            {
                Capacity = new AzureNative.Insights.Inputs.ScaleCapacityArgs
                {
                    Default = "1",
                    Maximum = "10",
                    Minimum = "1",
                },
                Name = "saludos",
                Recurrence = new AzureNative.Insights.Inputs.RecurrenceArgs
                {
                    Frequency = AzureNative.Insights.RecurrenceFrequency.Week,
                    Schedule = new AzureNative.Insights.Inputs.RecurrentScheduleArgs
                    {
                        Days = new[]
                        {
                            "1",
                        },
                        Hours = new[]
                        {
                            5,
                        },
                        Minutes = new[]
                        {
                            15,
                        },
                        TimeZone = "UTC",
                    },
                },
                Rules = new[]
                {
                    new AzureNative.Insights.Inputs.ScaleRuleArgs
                    {
                        MetricTrigger = new AzureNative.Insights.Inputs.MetricTriggerArgs
                        {
                            DividePerInstance = false,
                            MetricName = "Percentage CPU",
                            MetricResourceUri = "/subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/TestingMetricsScaleSet/providers/Microsoft.Compute/virtualMachineScaleSets/testingsc",
                            Operator = AzureNative.Insights.ComparisonOperationType.GreaterThan,
                            Statistic = AzureNative.Insights.MetricStatisticType.Average,
                            Threshold = 10,
                            TimeAggregation = AzureNative.Insights.TimeAggregationType.Average,
                            TimeGrain = "PT1M",
                            TimeWindow = "PT5M",
                        },
                        ScaleAction = new AzureNative.Insights.Inputs.ScaleActionArgs
                        {
                            Cooldown = "PT5M",
                            Direction = AzureNative.Insights.ScaleDirection.Increase,
                            Type = AzureNative.Insights.ScaleType.ChangeCount,
                            Value = "1",
                        },
                    },
                    new AzureNative.Insights.Inputs.ScaleRuleArgs
                    {
                        MetricTrigger = new AzureNative.Insights.Inputs.MetricTriggerArgs
                        {
                            DividePerInstance = false,
                            MetricName = "Percentage CPU",
                            MetricResourceUri = "/subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/TestingMetricsScaleSet/providers/Microsoft.Compute/virtualMachineScaleSets/testingsc",
                            Operator = AzureNative.Insights.ComparisonOperationType.GreaterThan,
                            Statistic = AzureNative.Insights.MetricStatisticType.Average,
                            Threshold = 15,
                            TimeAggregation = AzureNative.Insights.TimeAggregationType.Average,
                            TimeGrain = "PT2M",
                            TimeWindow = "PT5M",
                        },
                        ScaleAction = new AzureNative.Insights.Inputs.ScaleActionArgs
                        {
                            Cooldown = "PT6M",
                            Direction = AzureNative.Insights.ScaleDirection.Decrease,
                            Type = AzureNative.Insights.ScaleType.ChangeCount,
                            Value = "2",
                        },
                    },
                },
            },
        },
        ResourceGroupName = "TestingMetricsScaleSet",
        Tags = 
        {
            { "key1", "value1" },
            { "key2", "value2" },
        },
        TargetResourceUri = "/subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/TestingMetricsScaleSet/providers/Microsoft.Compute/virtualMachineScaleSets/testingsc",
    });

});


```

```go
package main

import (
	insights "github.com/pulumi/pulumi-azure-native-sdk/insights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := insights.NewAutoscaleSetting(ctx, "autoscaleSetting", &insights.AutoscaleSettingArgs{
			AutoscaleSettingName: pulumi.String("MySetting"),
			Enabled:              pulumi.Bool(true),
			Location:             pulumi.String("West US"),
			Notifications: []insights.AutoscaleNotificationArgs{
				{
					Email: {
						CustomEmails: pulumi.StringArray{
							pulumi.String("gu@ms.com"),
							pulumi.String("ge@ns.net"),
						},
						SendToSubscriptionAdministrator:    pulumi.Bool(true),
						SendToSubscriptionCoAdministrators: pulumi.Bool(true),
					},
					Operation: insights.OperationTypeScale,
					Webhooks: insights.WebhookNotificationArray{
						{
							Properties: nil,
							ServiceUri: pulumi.String("http://myservice.com"),
						},
					},
				},
			},
			PredictiveAutoscalePolicy: &insights.PredictiveAutoscalePolicyArgs{
				ScaleMode: insights.PredictiveAutoscalePolicyScaleModeEnabled,
			},
			Profiles: []insights.AutoscaleProfileArgs{
				{
					Capacity: {
						Default: pulumi.String("1"),
						Maximum: pulumi.String("10"),
						Minimum: pulumi.String("1"),
					},
					FixedDate: {
						End:      pulumi.String("2015-03-05T14:30:00Z"),
						Start:    pulumi.String("2015-03-05T14:00:00Z"),
						TimeZone: pulumi.String("UTC"),
					},
					Name: pulumi.String("adios"),
					Rules: insights.ScaleRuleArray{
						{
							MetricTrigger: {
								DividePerInstance: pulumi.Bool(false),
								MetricName:        pulumi.String("Percentage CPU"),
								MetricResourceUri: pulumi.String("/subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/TestingMetricsScaleSet/providers/Microsoft.Compute/virtualMachineScaleSets/testingsc"),
								Operator:          insights.ComparisonOperationTypeGreaterThan,
								Statistic:         insights.MetricStatisticTypeAverage,
								Threshold:         pulumi.Float64(10),
								TimeAggregation:   insights.TimeAggregationTypeAverage,
								TimeGrain:         pulumi.String("PT1M"),
								TimeWindow:        pulumi.String("PT5M"),
							},
							ScaleAction: {
								Cooldown:  pulumi.String("PT5M"),
								Direction: insights.ScaleDirectionIncrease,
								Type:      insights.ScaleTypeChangeCount,
								Value:     pulumi.String("1"),
							},
						},
						{
							MetricTrigger: {
								DividePerInstance: pulumi.Bool(false),
								MetricName:        pulumi.String("Percentage CPU"),
								MetricResourceUri: pulumi.String("/subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/TestingMetricsScaleSet/providers/Microsoft.Compute/virtualMachineScaleSets/testingsc"),
								Operator:          insights.ComparisonOperationTypeGreaterThan,
								Statistic:         insights.MetricStatisticTypeAverage,
								Threshold:         pulumi.Float64(15),
								TimeAggregation:   insights.TimeAggregationTypeAverage,
								TimeGrain:         pulumi.String("PT2M"),
								TimeWindow:        pulumi.String("PT5M"),
							},
							ScaleAction: {
								Cooldown:  pulumi.String("PT6M"),
								Direction: insights.ScaleDirectionDecrease,
								Type:      insights.ScaleTypeChangeCount,
								Value:     pulumi.String("2"),
							},
						},
					},
				},
				{
					Capacity: {
						Default: pulumi.String("1"),
						Maximum: pulumi.String("10"),
						Minimum: pulumi.String("1"),
					},
					Name: pulumi.String("saludos"),
					Recurrence: {
						Frequency: insights.RecurrenceFrequencyWeek,
						Schedule: {
							Days: pulumi.StringArray{
								pulumi.String("1"),
							},
							Hours: pulumi.IntArray{
								pulumi.Int(5),
							},
							Minutes: pulumi.IntArray{
								pulumi.Int(15),
							},
							TimeZone: pulumi.String("UTC"),
						},
					},
					Rules: insights.ScaleRuleArray{
						{
							MetricTrigger: {
								DividePerInstance: pulumi.Bool(false),
								MetricName:        pulumi.String("Percentage CPU"),
								MetricResourceUri: pulumi.String("/subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/TestingMetricsScaleSet/providers/Microsoft.Compute/virtualMachineScaleSets/testingsc"),
								Operator:          insights.ComparisonOperationTypeGreaterThan,
								Statistic:         insights.MetricStatisticTypeAverage,
								Threshold:         pulumi.Float64(10),
								TimeAggregation:   insights.TimeAggregationTypeAverage,
								TimeGrain:         pulumi.String("PT1M"),
								TimeWindow:        pulumi.String("PT5M"),
							},
							ScaleAction: {
								Cooldown:  pulumi.String("PT5M"),
								Direction: insights.ScaleDirectionIncrease,
								Type:      insights.ScaleTypeChangeCount,
								Value:     pulumi.String("1"),
							},
						},
						{
							MetricTrigger: {
								DividePerInstance: pulumi.Bool(false),
								MetricName:        pulumi.String("Percentage CPU"),
								MetricResourceUri: pulumi.String("/subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/TestingMetricsScaleSet/providers/Microsoft.Compute/virtualMachineScaleSets/testingsc"),
								Operator:          insights.ComparisonOperationTypeGreaterThan,
								Statistic:         insights.MetricStatisticTypeAverage,
								Threshold:         pulumi.Float64(15),
								TimeAggregation:   insights.TimeAggregationTypeAverage,
								TimeGrain:         pulumi.String("PT2M"),
								TimeWindow:        pulumi.String("PT5M"),
							},
							ScaleAction: {
								Cooldown:  pulumi.String("PT6M"),
								Direction: insights.ScaleDirectionDecrease,
								Type:      insights.ScaleTypeChangeCount,
								Value:     pulumi.String("2"),
							},
						},
					},
				},
			},
			ResourceGroupName: pulumi.String("TestingMetricsScaleSet"),
			Tags: pulumi.StringMap{
				"key1": pulumi.String("value1"),
				"key2": pulumi.String("value2"),
			},
			TargetResourceUri: pulumi.String("/subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/TestingMetricsScaleSet/providers/Microsoft.Compute/virtualMachineScaleSets/testingsc"),
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
import com.pulumi.azurenative.insights.AutoscaleSetting;
import com.pulumi.azurenative.insights.AutoscaleSettingArgs;
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
        var autoscaleSetting = new AutoscaleSetting("autoscaleSetting", AutoscaleSettingArgs.builder()        
            .autoscaleSettingName("MySetting")
            .enabled(true)
            .location("West US")
            .notifications(Map.ofEntries(
                Map.entry("email", Map.ofEntries(
                    Map.entry("customEmails",                     
                        "gu@ms.com",
                        "ge@ns.net"),
                    Map.entry("sendToSubscriptionAdministrator", true),
                    Map.entry("sendToSubscriptionCoAdministrators", true)
                )),
                Map.entry("operation", "Scale"),
                Map.entry("webhooks", Map.ofEntries(
                    Map.entry("properties", ),
                    Map.entry("serviceUri", "http://myservice.com")
                ))
            ))
            .predictiveAutoscalePolicy(Map.of("scaleMode", "Enabled"))
            .profiles(            
                Map.ofEntries(
                    Map.entry("capacity", Map.ofEntries(
                        Map.entry("default", "1"),
                        Map.entry("maximum", "10"),
                        Map.entry("minimum", "1")
                    )),
                    Map.entry("fixedDate", Map.ofEntries(
                        Map.entry("end", "2015-03-05T14:30:00Z"),
                        Map.entry("start", "2015-03-05T14:00:00Z"),
                        Map.entry("timeZone", "UTC")
                    )),
                    Map.entry("name", "adios"),
                    Map.entry("rules",                     
                        Map.ofEntries(
                            Map.entry("metricTrigger", Map.ofEntries(
                                Map.entry("dividePerInstance", false),
                                Map.entry("metricName", "Percentage CPU"),
                                Map.entry("metricResourceUri", "/subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/TestingMetricsScaleSet/providers/Microsoft.Compute/virtualMachineScaleSets/testingsc"),
                                Map.entry("operator", "GreaterThan"),
                                Map.entry("statistic", "Average"),
                                Map.entry("threshold", 10),
                                Map.entry("timeAggregation", "Average"),
                                Map.entry("timeGrain", "PT1M"),
                                Map.entry("timeWindow", "PT5M")
                            )),
                            Map.entry("scaleAction", Map.ofEntries(
                                Map.entry("cooldown", "PT5M"),
                                Map.entry("direction", "Increase"),
                                Map.entry("type", "ChangeCount"),
                                Map.entry("value", "1")
                            ))
                        ),
                        Map.ofEntries(
                            Map.entry("metricTrigger", Map.ofEntries(
                                Map.entry("dividePerInstance", false),
                                Map.entry("metricName", "Percentage CPU"),
                                Map.entry("metricResourceUri", "/subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/TestingMetricsScaleSet/providers/Microsoft.Compute/virtualMachineScaleSets/testingsc"),
                                Map.entry("operator", "GreaterThan"),
                                Map.entry("statistic", "Average"),
                                Map.entry("threshold", 15),
                                Map.entry("timeAggregation", "Average"),
                                Map.entry("timeGrain", "PT2M"),
                                Map.entry("timeWindow", "PT5M")
                            )),
                            Map.entry("scaleAction", Map.ofEntries(
                                Map.entry("cooldown", "PT6M"),
                                Map.entry("direction", "Decrease"),
                                Map.entry("type", "ChangeCount"),
                                Map.entry("value", "2")
                            ))
                        ))
                ),
                Map.ofEntries(
                    Map.entry("capacity", Map.ofEntries(
                        Map.entry("default", "1"),
                        Map.entry("maximum", "10"),
                        Map.entry("minimum", "1")
                    )),
                    Map.entry("name", "saludos"),
                    Map.entry("recurrence", Map.ofEntries(
                        Map.entry("frequency", "Week"),
                        Map.entry("schedule", Map.ofEntries(
                            Map.entry("days", "1"),
                            Map.entry("hours", 5),
                            Map.entry("minutes", 15),
                            Map.entry("timeZone", "UTC")
                        ))
                    )),
                    Map.entry("rules",                     
                        Map.ofEntries(
                            Map.entry("metricTrigger", Map.ofEntries(
                                Map.entry("dividePerInstance", false),
                                Map.entry("metricName", "Percentage CPU"),
                                Map.entry("metricResourceUri", "/subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/TestingMetricsScaleSet/providers/Microsoft.Compute/virtualMachineScaleSets/testingsc"),
                                Map.entry("operator", "GreaterThan"),
                                Map.entry("statistic", "Average"),
                                Map.entry("threshold", 10),
                                Map.entry("timeAggregation", "Average"),
                                Map.entry("timeGrain", "PT1M"),
                                Map.entry("timeWindow", "PT5M")
                            )),
                            Map.entry("scaleAction", Map.ofEntries(
                                Map.entry("cooldown", "PT5M"),
                                Map.entry("direction", "Increase"),
                                Map.entry("type", "ChangeCount"),
                                Map.entry("value", "1")
                            ))
                        ),
                        Map.ofEntries(
                            Map.entry("metricTrigger", Map.ofEntries(
                                Map.entry("dividePerInstance", false),
                                Map.entry("metricName", "Percentage CPU"),
                                Map.entry("metricResourceUri", "/subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/TestingMetricsScaleSet/providers/Microsoft.Compute/virtualMachineScaleSets/testingsc"),
                                Map.entry("operator", "GreaterThan"),
                                Map.entry("statistic", "Average"),
                                Map.entry("threshold", 15),
                                Map.entry("timeAggregation", "Average"),
                                Map.entry("timeGrain", "PT2M"),
                                Map.entry("timeWindow", "PT5M")
                            )),
                            Map.entry("scaleAction", Map.ofEntries(
                                Map.entry("cooldown", "PT6M"),
                                Map.entry("direction", "Decrease"),
                                Map.entry("type", "ChangeCount"),
                                Map.entry("value", "2")
                            ))
                        ))
                ))
            .resourceGroupName("TestingMetricsScaleSet")
            .tags(Map.ofEntries(
                Map.entry("key1", "value1"),
                Map.entry("key2", "value2")
            ))
            .targetResourceUri("/subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/TestingMetricsScaleSet/providers/Microsoft.Compute/virtualMachineScaleSets/testingsc")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const autoscaleSetting = new azure_native.insights.AutoscaleSetting("autoscaleSetting", {
    autoscaleSettingName: "MySetting",
    enabled: true,
    location: "West US",
    notifications: [{
        email: {
            customEmails: [
                "gu@ms.com",
                "ge@ns.net",
            ],
            sendToSubscriptionAdministrator: true,
            sendToSubscriptionCoAdministrators: true,
        },
        operation: azure_native.insights.OperationType.Scale,
        webhooks: [{
            properties: {},
            serviceUri: "http://myservice.com",
        }],
    }],
    predictiveAutoscalePolicy: {
        scaleMode: azure_native.insights.PredictiveAutoscalePolicyScaleMode.Enabled,
    },
    profiles: [
        {
            capacity: {
                "default": "1",
                maximum: "10",
                minimum: "1",
            },
            fixedDate: {
                end: "2015-03-05T14:30:00Z",
                start: "2015-03-05T14:00:00Z",
                timeZone: "UTC",
            },
            name: "adios",
            rules: [
                {
                    metricTrigger: {
                        dividePerInstance: false,
                        metricName: "Percentage CPU",
                        metricResourceUri: "/subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/TestingMetricsScaleSet/providers/Microsoft.Compute/virtualMachineScaleSets/testingsc",
                        operator: azure_native.insights.ComparisonOperationType.GreaterThan,
                        statistic: azure_native.insights.MetricStatisticType.Average,
                        threshold: 10,
                        timeAggregation: azure_native.insights.TimeAggregationType.Average,
                        timeGrain: "PT1M",
                        timeWindow: "PT5M",
                    },
                    scaleAction: {
                        cooldown: "PT5M",
                        direction: azure_native.insights.ScaleDirection.Increase,
                        type: azure_native.insights.ScaleType.ChangeCount,
                        value: "1",
                    },
                },
                {
                    metricTrigger: {
                        dividePerInstance: false,
                        metricName: "Percentage CPU",
                        metricResourceUri: "/subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/TestingMetricsScaleSet/providers/Microsoft.Compute/virtualMachineScaleSets/testingsc",
                        operator: azure_native.insights.ComparisonOperationType.GreaterThan,
                        statistic: azure_native.insights.MetricStatisticType.Average,
                        threshold: 15,
                        timeAggregation: azure_native.insights.TimeAggregationType.Average,
                        timeGrain: "PT2M",
                        timeWindow: "PT5M",
                    },
                    scaleAction: {
                        cooldown: "PT6M",
                        direction: azure_native.insights.ScaleDirection.Decrease,
                        type: azure_native.insights.ScaleType.ChangeCount,
                        value: "2",
                    },
                },
            ],
        },
        {
            capacity: {
                "default": "1",
                maximum: "10",
                minimum: "1",
            },
            name: "saludos",
            recurrence: {
                frequency: azure_native.insights.RecurrenceFrequency.Week,
                schedule: {
                    days: ["1"],
                    hours: [5],
                    minutes: [15],
                    timeZone: "UTC",
                },
            },
            rules: [
                {
                    metricTrigger: {
                        dividePerInstance: false,
                        metricName: "Percentage CPU",
                        metricResourceUri: "/subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/TestingMetricsScaleSet/providers/Microsoft.Compute/virtualMachineScaleSets/testingsc",
                        operator: azure_native.insights.ComparisonOperationType.GreaterThan,
                        statistic: azure_native.insights.MetricStatisticType.Average,
                        threshold: 10,
                        timeAggregation: azure_native.insights.TimeAggregationType.Average,
                        timeGrain: "PT1M",
                        timeWindow: "PT5M",
                    },
                    scaleAction: {
                        cooldown: "PT5M",
                        direction: azure_native.insights.ScaleDirection.Increase,
                        type: azure_native.insights.ScaleType.ChangeCount,
                        value: "1",
                    },
                },
                {
                    metricTrigger: {
                        dividePerInstance: false,
                        metricName: "Percentage CPU",
                        metricResourceUri: "/subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/TestingMetricsScaleSet/providers/Microsoft.Compute/virtualMachineScaleSets/testingsc",
                        operator: azure_native.insights.ComparisonOperationType.GreaterThan,
                        statistic: azure_native.insights.MetricStatisticType.Average,
                        threshold: 15,
                        timeAggregation: azure_native.insights.TimeAggregationType.Average,
                        timeGrain: "PT2M",
                        timeWindow: "PT5M",
                    },
                    scaleAction: {
                        cooldown: "PT6M",
                        direction: azure_native.insights.ScaleDirection.Decrease,
                        type: azure_native.insights.ScaleType.ChangeCount,
                        value: "2",
                    },
                },
            ],
        },
    ],
    resourceGroupName: "TestingMetricsScaleSet",
    tags: {
        key1: "value1",
        key2: "value2",
    },
    targetResourceUri: "/subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/TestingMetricsScaleSet/providers/Microsoft.Compute/virtualMachineScaleSets/testingsc",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

autoscale_setting = azure_native.insights.AutoscaleSetting("autoscaleSetting",
    autoscale_setting_name="MySetting",
    enabled=True,
    location="West US",
    notifications=[{
        "email": azure_native.insights.EmailNotificationArgs(
            custom_emails=[
                "gu@ms.com",
                "ge@ns.net",
            ],
            send_to_subscription_administrator=True,
            send_to_subscription_co_administrators=True,
        ),
        "operation": azure_native.insights.OperationType.SCALE,
        "webhooks": [azure_native.insights.WebhookNotificationArgs(
            properties={},
            service_uri="http://myservice.com",
        )],
    }],
    predictive_autoscale_policy=azure_native.insights.PredictiveAutoscalePolicyArgs(
        scale_mode=azure_native.insights.PredictiveAutoscalePolicyScaleMode.ENABLED,
    ),
    profiles=[
        {
            "capacity": azure_native.insights.ScaleCapacityArgs(
                default="1",
                maximum="10",
                minimum="1",
            ),
            "fixedDate": azure_native.insights.TimeWindowArgs(
                end="2015-03-05T14:30:00Z",
                start="2015-03-05T14:00:00Z",
                time_zone="UTC",
            ),
            "name": "adios",
            "rules": [
                {
                    "metricTrigger": azure_native.insights.MetricTriggerArgs(
                        divide_per_instance=False,
                        metric_name="Percentage CPU",
                        metric_resource_uri="/subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/TestingMetricsScaleSet/providers/Microsoft.Compute/virtualMachineScaleSets/testingsc",
                        operator=azure_native.insights.ComparisonOperationType.GREATER_THAN,
                        statistic=azure_native.insights.MetricStatisticType.AVERAGE,
                        threshold=10,
                        time_aggregation=azure_native.insights.TimeAggregationType.AVERAGE,
                        time_grain="PT1M",
                        time_window="PT5M",
                    ),
                    "scaleAction": azure_native.insights.ScaleActionArgs(
                        cooldown="PT5M",
                        direction=azure_native.insights.ScaleDirection.INCREASE,
                        type=azure_native.insights.ScaleType.CHANGE_COUNT,
                        value="1",
                    ),
                },
                {
                    "metricTrigger": azure_native.insights.MetricTriggerArgs(
                        divide_per_instance=False,
                        metric_name="Percentage CPU",
                        metric_resource_uri="/subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/TestingMetricsScaleSet/providers/Microsoft.Compute/virtualMachineScaleSets/testingsc",
                        operator=azure_native.insights.ComparisonOperationType.GREATER_THAN,
                        statistic=azure_native.insights.MetricStatisticType.AVERAGE,
                        threshold=15,
                        time_aggregation=azure_native.insights.TimeAggregationType.AVERAGE,
                        time_grain="PT2M",
                        time_window="PT5M",
                    ),
                    "scaleAction": azure_native.insights.ScaleActionArgs(
                        cooldown="PT6M",
                        direction=azure_native.insights.ScaleDirection.DECREASE,
                        type=azure_native.insights.ScaleType.CHANGE_COUNT,
                        value="2",
                    ),
                },
            ],
        },
        {
            "capacity": azure_native.insights.ScaleCapacityArgs(
                default="1",
                maximum="10",
                minimum="1",
            ),
            "name": "saludos",
            "recurrence": {
                "frequency": azure_native.insights.RecurrenceFrequency.WEEK,
                "schedule": azure_native.insights.RecurrentScheduleArgs(
                    days=["1"],
                    hours=[5],
                    minutes=[15],
                    time_zone="UTC",
                ),
            },
            "rules": [
                {
                    "metricTrigger": azure_native.insights.MetricTriggerArgs(
                        divide_per_instance=False,
                        metric_name="Percentage CPU",
                        metric_resource_uri="/subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/TestingMetricsScaleSet/providers/Microsoft.Compute/virtualMachineScaleSets/testingsc",
                        operator=azure_native.insights.ComparisonOperationType.GREATER_THAN,
                        statistic=azure_native.insights.MetricStatisticType.AVERAGE,
                        threshold=10,
                        time_aggregation=azure_native.insights.TimeAggregationType.AVERAGE,
                        time_grain="PT1M",
                        time_window="PT5M",
                    ),
                    "scaleAction": azure_native.insights.ScaleActionArgs(
                        cooldown="PT5M",
                        direction=azure_native.insights.ScaleDirection.INCREASE,
                        type=azure_native.insights.ScaleType.CHANGE_COUNT,
                        value="1",
                    ),
                },
                {
                    "metricTrigger": azure_native.insights.MetricTriggerArgs(
                        divide_per_instance=False,
                        metric_name="Percentage CPU",
                        metric_resource_uri="/subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/TestingMetricsScaleSet/providers/Microsoft.Compute/virtualMachineScaleSets/testingsc",
                        operator=azure_native.insights.ComparisonOperationType.GREATER_THAN,
                        statistic=azure_native.insights.MetricStatisticType.AVERAGE,
                        threshold=15,
                        time_aggregation=azure_native.insights.TimeAggregationType.AVERAGE,
                        time_grain="PT2M",
                        time_window="PT5M",
                    ),
                    "scaleAction": azure_native.insights.ScaleActionArgs(
                        cooldown="PT6M",
                        direction=azure_native.insights.ScaleDirection.DECREASE,
                        type=azure_native.insights.ScaleType.CHANGE_COUNT,
                        value="2",
                    ),
                },
            ],
        },
    ],
    resource_group_name="TestingMetricsScaleSet",
    tags={
        "key1": "value1",
        "key2": "value2",
    },
    target_resource_uri="/subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/TestingMetricsScaleSet/providers/Microsoft.Compute/virtualMachineScaleSets/testingsc")

```

```yaml
resources:
  autoscaleSetting:
    type: azure-native:insights:AutoscaleSetting
    properties:
      autoscaleSettingName: MySetting
      enabled: true
      location: West US
      notifications:
        - email:
            customEmails:
              - gu@ms.com
              - ge@ns.net
            sendToSubscriptionAdministrator: true
            sendToSubscriptionCoAdministrators: true
          operation: Scale
          webhooks:
            - properties: {}
              serviceUri: http://myservice.com
      predictiveAutoscalePolicy:
        scaleMode: Enabled
      profiles:
        - capacity:
            default: '1'
            maximum: '10'
            minimum: '1'
          fixedDate:
            end: 2015-03-05T14:30:00Z
            start: 2015-03-05T14:00:00Z
            timeZone: UTC
          name: adios
          rules:
            - metricTrigger:
                dividePerInstance: false
                metricName: Percentage CPU
                metricResourceUri: /subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/TestingMetricsScaleSet/providers/Microsoft.Compute/virtualMachineScaleSets/testingsc
                operator: GreaterThan
                statistic: Average
                threshold: 10
                timeAggregation: Average
                timeGrain: PT1M
                timeWindow: PT5M
              scaleAction:
                cooldown: PT5M
                direction: Increase
                type: ChangeCount
                value: '1'
            - metricTrigger:
                dividePerInstance: false
                metricName: Percentage CPU
                metricResourceUri: /subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/TestingMetricsScaleSet/providers/Microsoft.Compute/virtualMachineScaleSets/testingsc
                operator: GreaterThan
                statistic: Average
                threshold: 15
                timeAggregation: Average
                timeGrain: PT2M
                timeWindow: PT5M
              scaleAction:
                cooldown: PT6M
                direction: Decrease
                type: ChangeCount
                value: '2'
        - capacity:
            default: '1'
            maximum: '10'
            minimum: '1'
          name: saludos
          recurrence:
            frequency: Week
            schedule:
              days:
                - '1'
              hours:
                - 5
              minutes:
                - 15
              timeZone: UTC
          rules:
            - metricTrigger:
                dividePerInstance: false
                metricName: Percentage CPU
                metricResourceUri: /subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/TestingMetricsScaleSet/providers/Microsoft.Compute/virtualMachineScaleSets/testingsc
                operator: GreaterThan
                statistic: Average
                threshold: 10
                timeAggregation: Average
                timeGrain: PT1M
                timeWindow: PT5M
              scaleAction:
                cooldown: PT5M
                direction: Increase
                type: ChangeCount
                value: '1'
            - metricTrigger:
                dividePerInstance: false
                metricName: Percentage CPU
                metricResourceUri: /subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/TestingMetricsScaleSet/providers/Microsoft.Compute/virtualMachineScaleSets/testingsc
                operator: GreaterThan
                statistic: Average
                threshold: 15
                timeAggregation: Average
                timeGrain: PT2M
                timeWindow: PT5M
              scaleAction:
                cooldown: PT6M
                direction: Decrease
                type: ChangeCount
                value: '2'
      resourceGroupName: TestingMetricsScaleSet
      tags:
        key1: value1
        key2: value2
      targetResourceUri: /subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/TestingMetricsScaleSet/providers/Microsoft.Compute/virtualMachineScaleSets/testingsc

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:insights:AutoscaleSetting MySetting /subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/TestingMetricsScaleSet/providers/microsoft.insights/autoscalesettings/MySetting 
```
