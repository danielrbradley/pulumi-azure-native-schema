The metric alert resource.
API Version: 2018-03-01.
Previous API Version: 2018-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a dynamic alert rule for Multiple Resources
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var metricAlert = new AzureNative.Insights.MetricAlert("metricAlert", new()
    {
        Actions = new[]
        {
            new AzureNative.Insights.Inputs.MetricAlertActionArgs
            {
                ActionGroupId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2",
                WebHookProperties = 
                {
                    { "key11", "value11" },
                    { "key12", "value12" },
                },
            },
        },
        AutoMitigate = true,
        Criteria = new AzureNative.Insights.Inputs.MetricAlertMultipleResourceMultipleMetricCriteriaArgs
        {
            AllOf = new[]
            {
                new AzureNative.Insights.Inputs.DynamicMetricCriteriaArgs
                {
                    AlertSensitivity = "Medium",
                    CriterionType = "DynamicThresholdCriterion",
                    Dimensions = new[] {},
                    FailingPeriods = new AzureNative.Insights.Inputs.DynamicThresholdFailingPeriodsArgs
                    {
                        MinFailingPeriodsToAlert = 4,
                        NumberOfEvaluationPeriods = 4,
                    },
                    MetricName = "Percentage CPU",
                    MetricNamespace = "microsoft.compute/virtualmachines",
                    Name = "High_CPU_80",
                    Operator = "GreaterOrLessThan",
                    TimeAggregation = "Average",
                },
            },
            OdataType = "Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria",
        },
        Description = "This is the description of the rule1",
        Enabled = true,
        EvaluationFrequency = "PT1M",
        Location = "global",
        ResourceGroupName = "gigtest",
        RuleName = "MetricAlertOnMultipleResources",
        Scopes = new[]
        {
            "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme1",
            "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme2",
        },
        Severity = 3,
        Tags = null,
        TargetResourceRegion = "southcentralus",
        TargetResourceType = "Microsoft.Compute/virtualMachines",
        WindowSize = "PT15M",
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
		_, err := insights.NewMetricAlert(ctx, "metricAlert", &insights.MetricAlertArgs{
			Actions: []insights.MetricAlertActionArgs{
				{
					ActionGroupId: pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2"),
					WebHookProperties: {
						"key11": pulumi.String("value11"),
						"key12": pulumi.String("value12"),
					},
				},
			},
			AutoMitigate: pulumi.Bool(true),
			Criteria: insights.MetricAlertMultipleResourceMultipleMetricCriteria{
				AllOf: []interface{}{
					insights.DynamicMetricCriteria{
						AlertSensitivity: "Medium",
						CriterionType:    "DynamicThresholdCriterion",
						Dimensions:       []insights.MetricDimension{},
						FailingPeriods: insights.DynamicThresholdFailingPeriods{
							MinFailingPeriodsToAlert:  4,
							NumberOfEvaluationPeriods: 4,
						},
						MetricName:      "Percentage CPU",
						MetricNamespace: "microsoft.compute/virtualmachines",
						Name:            "High_CPU_80",
						Operator:        "GreaterOrLessThan",
						TimeAggregation: "Average",
					},
				},
				OdataType: "Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria",
			},
			Description:         pulumi.String("This is the description of the rule1"),
			Enabled:             pulumi.Bool(true),
			EvaluationFrequency: pulumi.String("PT1M"),
			Location:            pulumi.String("global"),
			ResourceGroupName:   pulumi.String("gigtest"),
			RuleName:            pulumi.String("MetricAlertOnMultipleResources"),
			Scopes: pulumi.StringArray{
				pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme1"),
				pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme2"),
			},
			Severity:             pulumi.Int(3),
			Tags:                 nil,
			TargetResourceRegion: pulumi.String("southcentralus"),
			TargetResourceType:   pulumi.String("Microsoft.Compute/virtualMachines"),
			WindowSize:           pulumi.String("PT15M"),
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
import com.pulumi.azurenative.insights.MetricAlert;
import com.pulumi.azurenative.insights.MetricAlertArgs;
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
        var metricAlert = new MetricAlert("metricAlert", MetricAlertArgs.builder()        
            .actions(Map.ofEntries(
                Map.entry("actionGroupId", "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2"),
                Map.entry("webHookProperties", Map.ofEntries(
                    Map.entry("key11", "value11"),
                    Map.entry("key12", "value12")
                ))
            ))
            .autoMitigate(true)
            .criteria(Map.ofEntries(
                Map.entry("allOf", Map.ofEntries(
                    Map.entry("alertSensitivity", "Medium"),
                    Map.entry("criterionType", "DynamicThresholdCriterion"),
                    Map.entry("dimensions", ),
                    Map.entry("failingPeriods", Map.ofEntries(
                        Map.entry("minFailingPeriodsToAlert", 4),
                        Map.entry("numberOfEvaluationPeriods", 4)
                    )),
                    Map.entry("metricName", "Percentage CPU"),
                    Map.entry("metricNamespace", "microsoft.compute/virtualmachines"),
                    Map.entry("name", "High_CPU_80"),
                    Map.entry("operator", "GreaterOrLessThan"),
                    Map.entry("timeAggregation", "Average")
                )),
                Map.entry("odataType", "Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria")
            ))
            .description("This is the description of the rule1")
            .enabled(true)
            .evaluationFrequency("PT1M")
            .location("global")
            .resourceGroupName("gigtest")
            .ruleName("MetricAlertOnMultipleResources")
            .scopes(            
                "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme1",
                "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme2")
            .severity(3)
            .tags()
            .targetResourceRegion("southcentralus")
            .targetResourceType("Microsoft.Compute/virtualMachines")
            .windowSize("PT15M")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const metricAlert = new azure_native.insights.MetricAlert("metricAlert", {
    actions: [{
        actionGroupId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2",
        webHookProperties: {
            key11: "value11",
            key12: "value12",
        },
    }],
    autoMitigate: true,
    criteria: {
        allOf: [{
            alertSensitivity: "Medium",
            criterionType: "DynamicThresholdCriterion",
            dimensions: [],
            failingPeriods: {
                minFailingPeriodsToAlert: 4,
                numberOfEvaluationPeriods: 4,
            },
            metricName: "Percentage CPU",
            metricNamespace: "microsoft.compute/virtualmachines",
            name: "High_CPU_80",
            operator: "GreaterOrLessThan",
            timeAggregation: "Average",
        }],
        odataType: "Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria",
    },
    description: "This is the description of the rule1",
    enabled: true,
    evaluationFrequency: "PT1M",
    location: "global",
    resourceGroupName: "gigtest",
    ruleName: "MetricAlertOnMultipleResources",
    scopes: [
        "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme1",
        "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme2",
    ],
    severity: 3,
    tags: {},
    targetResourceRegion: "southcentralus",
    targetResourceType: "Microsoft.Compute/virtualMachines",
    windowSize: "PT15M",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

metric_alert = azure_native.insights.MetricAlert("metricAlert",
    actions=[azure_native.insights.MetricAlertActionArgs(
        action_group_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2",
        web_hook_properties={
            "key11": "value11",
            "key12": "value12",
        },
    )],
    auto_mitigate=True,
    criteria=azure_native.insights.MetricAlertMultipleResourceMultipleMetricCriteriaArgs(
        all_of=[azure_native.insights.DynamicMetricCriteriaArgs(
            alert_sensitivity="Medium",
            criterion_type="DynamicThresholdCriterion",
            dimensions=[],
            failing_periods=azure_native.insights.DynamicThresholdFailingPeriodsArgs(
                min_failing_periods_to_alert=4,
                number_of_evaluation_periods=4,
            ),
            metric_name="Percentage CPU",
            metric_namespace="microsoft.compute/virtualmachines",
            name="High_CPU_80",
            operator="GreaterOrLessThan",
            time_aggregation="Average",
        )],
        odata_type="Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria",
    ),
    description="This is the description of the rule1",
    enabled=True,
    evaluation_frequency="PT1M",
    location="global",
    resource_group_name="gigtest",
    rule_name="MetricAlertOnMultipleResources",
    scopes=[
        "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme1",
        "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme2",
    ],
    severity=3,
    tags={},
    target_resource_region="southcentralus",
    target_resource_type="Microsoft.Compute/virtualMachines",
    window_size="PT15M")

```

```yaml
resources:
  metricAlert:
    type: azure-native:insights:MetricAlert
    properties:
      actions:
        - actionGroupId: /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2
          webHookProperties:
            key11: value11
            key12: value12
      autoMitigate: true
      criteria:
        allOf:
          - alertSensitivity: Medium
            criterionType: DynamicThresholdCriterion
            dimensions: []
            failingPeriods:
              minFailingPeriodsToAlert: 4
              numberOfEvaluationPeriods: 4
            metricName: Percentage CPU
            metricNamespace: microsoft.compute/virtualmachines
            name: High_CPU_80
            operator: GreaterOrLessThan
            timeAggregation: Average
        odataType: Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria
      description: This is the description of the rule1
      enabled: true
      evaluationFrequency: PT1M
      location: global
      resourceGroupName: gigtest
      ruleName: MetricAlertOnMultipleResources
      scopes:
        - /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme1
        - /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme2
      severity: 3
      tags: {}
      targetResourceRegion: southcentralus
      targetResourceType: Microsoft.Compute/virtualMachines
      windowSize: PT15M

```

{{% /example %}}
{{% example %}}
### Create or update a dynamic alert rule for Single Resource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var metricAlert = new AzureNative.Insights.MetricAlert("metricAlert", new()
    {
        Actions = new[]
        {
            new AzureNative.Insights.Inputs.MetricAlertActionArgs
            {
                ActionGroupId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2",
                WebHookProperties = 
                {
                    { "key11", "value11" },
                    { "key12", "value12" },
                },
            },
        },
        AutoMitigate = true,
        Criteria = new AzureNative.Insights.Inputs.MetricAlertMultipleResourceMultipleMetricCriteriaArgs
        {
            AllOf = new[]
            {
                new AzureNative.Insights.Inputs.DynamicMetricCriteriaArgs
                {
                    AlertSensitivity = "Medium",
                    CriterionType = "DynamicThresholdCriterion",
                    Dimensions = new[] {},
                    FailingPeriods = new AzureNative.Insights.Inputs.DynamicThresholdFailingPeriodsArgs
                    {
                        MinFailingPeriodsToAlert = 4,
                        NumberOfEvaluationPeriods = 4,
                    },
                    IgnoreDataBefore = "2019-04-04T21:00:00.000Z",
                    MetricName = "Percentage CPU",
                    MetricNamespace = "microsoft.compute/virtualmachines",
                    Name = "High_CPU_80",
                    Operator = "GreaterOrLessThan",
                    TimeAggregation = "Average",
                },
            },
            OdataType = "Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria",
        },
        Description = "This is the description of the rule1",
        Enabled = true,
        EvaluationFrequency = "PT1M",
        Location = "global",
        ResourceGroupName = "gigtest",
        RuleName = "chiricutin",
        Scopes = new[]
        {
            "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme",
        },
        Severity = 3,
        Tags = null,
        WindowSize = "PT15M",
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
		_, err := insights.NewMetricAlert(ctx, "metricAlert", &insights.MetricAlertArgs{
			Actions: []insights.MetricAlertActionArgs{
				{
					ActionGroupId: pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2"),
					WebHookProperties: {
						"key11": pulumi.String("value11"),
						"key12": pulumi.String("value12"),
					},
				},
			},
			AutoMitigate: pulumi.Bool(true),
			Criteria: insights.MetricAlertMultipleResourceMultipleMetricCriteria{
				AllOf: []interface{}{
					insights.DynamicMetricCriteria{
						AlertSensitivity: "Medium",
						CriterionType:    "DynamicThresholdCriterion",
						Dimensions:       []insights.MetricDimension{},
						FailingPeriods: insights.DynamicThresholdFailingPeriods{
							MinFailingPeriodsToAlert:  4,
							NumberOfEvaluationPeriods: 4,
						},
						IgnoreDataBefore: "2019-04-04T21:00:00.000Z",
						MetricName:       "Percentage CPU",
						MetricNamespace:  "microsoft.compute/virtualmachines",
						Name:             "High_CPU_80",
						Operator:         "GreaterOrLessThan",
						TimeAggregation:  "Average",
					},
				},
				OdataType: "Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria",
			},
			Description:         pulumi.String("This is the description of the rule1"),
			Enabled:             pulumi.Bool(true),
			EvaluationFrequency: pulumi.String("PT1M"),
			Location:            pulumi.String("global"),
			ResourceGroupName:   pulumi.String("gigtest"),
			RuleName:            pulumi.String("chiricutin"),
			Scopes: pulumi.StringArray{
				pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme"),
			},
			Severity:   pulumi.Int(3),
			Tags:       nil,
			WindowSize: pulumi.String("PT15M"),
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
import com.pulumi.azurenative.insights.MetricAlert;
import com.pulumi.azurenative.insights.MetricAlertArgs;
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
        var metricAlert = new MetricAlert("metricAlert", MetricAlertArgs.builder()        
            .actions(Map.ofEntries(
                Map.entry("actionGroupId", "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2"),
                Map.entry("webHookProperties", Map.ofEntries(
                    Map.entry("key11", "value11"),
                    Map.entry("key12", "value12")
                ))
            ))
            .autoMitigate(true)
            .criteria(Map.ofEntries(
                Map.entry("allOf", Map.ofEntries(
                    Map.entry("alertSensitivity", "Medium"),
                    Map.entry("criterionType", "DynamicThresholdCriterion"),
                    Map.entry("dimensions", ),
                    Map.entry("failingPeriods", Map.ofEntries(
                        Map.entry("minFailingPeriodsToAlert", 4),
                        Map.entry("numberOfEvaluationPeriods", 4)
                    )),
                    Map.entry("ignoreDataBefore", "2019-04-04T21:00:00.000Z"),
                    Map.entry("metricName", "Percentage CPU"),
                    Map.entry("metricNamespace", "microsoft.compute/virtualmachines"),
                    Map.entry("name", "High_CPU_80"),
                    Map.entry("operator", "GreaterOrLessThan"),
                    Map.entry("timeAggregation", "Average")
                )),
                Map.entry("odataType", "Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria")
            ))
            .description("This is the description of the rule1")
            .enabled(true)
            .evaluationFrequency("PT1M")
            .location("global")
            .resourceGroupName("gigtest")
            .ruleName("chiricutin")
            .scopes("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme")
            .severity(3)
            .tags()
            .windowSize("PT15M")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const metricAlert = new azure_native.insights.MetricAlert("metricAlert", {
    actions: [{
        actionGroupId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2",
        webHookProperties: {
            key11: "value11",
            key12: "value12",
        },
    }],
    autoMitigate: true,
    criteria: {
        allOf: [{
            alertSensitivity: "Medium",
            criterionType: "DynamicThresholdCriterion",
            dimensions: [],
            failingPeriods: {
                minFailingPeriodsToAlert: 4,
                numberOfEvaluationPeriods: 4,
            },
            ignoreDataBefore: "2019-04-04T21:00:00.000Z",
            metricName: "Percentage CPU",
            metricNamespace: "microsoft.compute/virtualmachines",
            name: "High_CPU_80",
            operator: "GreaterOrLessThan",
            timeAggregation: "Average",
        }],
        odataType: "Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria",
    },
    description: "This is the description of the rule1",
    enabled: true,
    evaluationFrequency: "PT1M",
    location: "global",
    resourceGroupName: "gigtest",
    ruleName: "chiricutin",
    scopes: ["/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme"],
    severity: 3,
    tags: {},
    windowSize: "PT15M",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

metric_alert = azure_native.insights.MetricAlert("metricAlert",
    actions=[azure_native.insights.MetricAlertActionArgs(
        action_group_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2",
        web_hook_properties={
            "key11": "value11",
            "key12": "value12",
        },
    )],
    auto_mitigate=True,
    criteria=azure_native.insights.MetricAlertMultipleResourceMultipleMetricCriteriaArgs(
        all_of=[azure_native.insights.DynamicMetricCriteriaArgs(
            alert_sensitivity="Medium",
            criterion_type="DynamicThresholdCriterion",
            dimensions=[],
            failing_periods=azure_native.insights.DynamicThresholdFailingPeriodsArgs(
                min_failing_periods_to_alert=4,
                number_of_evaluation_periods=4,
            ),
            ignore_data_before="2019-04-04T21:00:00.000Z",
            metric_name="Percentage CPU",
            metric_namespace="microsoft.compute/virtualmachines",
            name="High_CPU_80",
            operator="GreaterOrLessThan",
            time_aggregation="Average",
        )],
        odata_type="Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria",
    ),
    description="This is the description of the rule1",
    enabled=True,
    evaluation_frequency="PT1M",
    location="global",
    resource_group_name="gigtest",
    rule_name="chiricutin",
    scopes=["/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme"],
    severity=3,
    tags={},
    window_size="PT15M")

```

```yaml
resources:
  metricAlert:
    type: azure-native:insights:MetricAlert
    properties:
      actions:
        - actionGroupId: /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2
          webHookProperties:
            key11: value11
            key12: value12
      autoMitigate: true
      criteria:
        allOf:
          - alertSensitivity: Medium
            criterionType: DynamicThresholdCriterion
            dimensions: []
            failingPeriods:
              minFailingPeriodsToAlert: 4
              numberOfEvaluationPeriods: 4
            ignoreDataBefore: 2019-04-04T21:00:00.000Z
            metricName: Percentage CPU
            metricNamespace: microsoft.compute/virtualmachines
            name: High_CPU_80
            operator: GreaterOrLessThan
            timeAggregation: Average
        odataType: Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria
      description: This is the description of the rule1
      enabled: true
      evaluationFrequency: PT1M
      location: global
      resourceGroupName: gigtest
      ruleName: chiricutin
      scopes:
        - /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme
      severity: 3
      tags: {}
      windowSize: PT15M

```

{{% /example %}}
{{% example %}}
### Create or update a web test alert rule
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var metricAlert = new AzureNative.Insights.MetricAlert("metricAlert", new()
    {
        Actions = new[] {},
        Criteria = new AzureNative.Insights.Inputs.WebtestLocationAvailabilityCriteriaArgs
        {
            ComponentId = "/subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/components/webtest-name-example",
            FailedLocationCount = 2,
            OdataType = "Microsoft.Azure.Monitor.WebtestLocationAvailabilityCriteria",
            WebTestId = "/subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/webtests/component-example",
        },
        Description = "Automatically created alert rule for availability test \"component-example\" a",
        Enabled = true,
        EvaluationFrequency = "PT1M",
        Location = "global",
        ResourceGroupName = "rg-example",
        RuleName = "webtest-name-example",
        Scopes = new[]
        {
            "/subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/webtests/component-example",
            "/subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/components/webtest-name-example",
        },
        Severity = 4,
        Tags = 
        {
            { "hidden-link:/subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/components/webtest-name-example", "Resource" },
            { "hidden-link:/subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/webtests/component-example", "Resource" },
        },
        WindowSize = "PT15M",
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
		_, err := insights.NewMetricAlert(ctx, "metricAlert", &insights.MetricAlertArgs{
			Actions: insights.MetricAlertActionArray{},
			Criteria: insights.WebtestLocationAvailabilityCriteria{
				ComponentId:         "/subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/components/webtest-name-example",
				FailedLocationCount: 2,
				OdataType:           "Microsoft.Azure.Monitor.WebtestLocationAvailabilityCriteria",
				WebTestId:           "/subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/webtests/component-example",
			},
			Description:         pulumi.String("Automatically created alert rule for availability test \"component-example\" a"),
			Enabled:             pulumi.Bool(true),
			EvaluationFrequency: pulumi.String("PT1M"),
			Location:            pulumi.String("global"),
			ResourceGroupName:   pulumi.String("rg-example"),
			RuleName:            pulumi.String("webtest-name-example"),
			Scopes: pulumi.StringArray{
				pulumi.String("/subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/webtests/component-example"),
				pulumi.String("/subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/components/webtest-name-example"),
			},
			Severity: pulumi.Int(4),
			Tags: pulumi.StringMap{
				"hidden-link:/subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/components/webtest-name-example": pulumi.String("Resource"),
				"hidden-link:/subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/webtests/component-example":      pulumi.String("Resource"),
			},
			WindowSize: pulumi.String("PT15M"),
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
import com.pulumi.azurenative.insights.MetricAlert;
import com.pulumi.azurenative.insights.MetricAlertArgs;
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
        var metricAlert = new MetricAlert("metricAlert", MetricAlertArgs.builder()        
            .actions()
            .criteria(Map.ofEntries(
                Map.entry("componentId", "/subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/components/webtest-name-example"),
                Map.entry("failedLocationCount", 2),
                Map.entry("odataType", "Microsoft.Azure.Monitor.WebtestLocationAvailabilityCriteria"),
                Map.entry("webTestId", "/subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/webtests/component-example")
            ))
            .description("Automatically created alert rule for availability test \"component-example\" a")
            .enabled(true)
            .evaluationFrequency("PT1M")
            .location("global")
            .resourceGroupName("rg-example")
            .ruleName("webtest-name-example")
            .scopes(            
                "/subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/webtests/component-example",
                "/subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/components/webtest-name-example")
            .severity(4)
            .tags(Map.ofEntries(
                Map.entry("hidden-link:/subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/components/webtest-name-example", "Resource"),
                Map.entry("hidden-link:/subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/webtests/component-example", "Resource")
            ))
            .windowSize("PT15M")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const metricAlert = new azure_native.insights.MetricAlert("metricAlert", {
    actions: [],
    criteria: {
        componentId: "/subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/components/webtest-name-example",
        failedLocationCount: 2,
        odataType: "Microsoft.Azure.Monitor.WebtestLocationAvailabilityCriteria",
        webTestId: "/subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/webtests/component-example",
    },
    description: "Automatically created alert rule for availability test \"component-example\" a",
    enabled: true,
    evaluationFrequency: "PT1M",
    location: "global",
    resourceGroupName: "rg-example",
    ruleName: "webtest-name-example",
    scopes: [
        "/subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/webtests/component-example",
        "/subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/components/webtest-name-example",
    ],
    severity: 4,
    tags: {
        "hidden-link:/subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/components/webtest-name-example": "Resource",
        "hidden-link:/subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/webtests/component-example": "Resource",
    },
    windowSize: "PT15M",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

metric_alert = azure_native.insights.MetricAlert("metricAlert",
    actions=[],
    criteria=azure_native.insights.WebtestLocationAvailabilityCriteriaArgs(
        component_id="/subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/components/webtest-name-example",
        failed_location_count=2,
        odata_type="Microsoft.Azure.Monitor.WebtestLocationAvailabilityCriteria",
        web_test_id="/subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/webtests/component-example",
    ),
    description="Automatically created alert rule for availability test \"component-example\" a",
    enabled=True,
    evaluation_frequency="PT1M",
    location="global",
    resource_group_name="rg-example",
    rule_name="webtest-name-example",
    scopes=[
        "/subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/webtests/component-example",
        "/subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/components/webtest-name-example",
    ],
    severity=4,
    tags={
        "hidden-link:/subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/components/webtest-name-example": "Resource",
        "hidden-link:/subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/webtests/component-example": "Resource",
    },
    window_size="PT15M")

```

```yaml
resources:
  metricAlert:
    type: azure-native:insights:MetricAlert
    properties:
      actions: []
      criteria:
        componentId: /subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/components/webtest-name-example
        failedLocationCount: 2
        odataType: Microsoft.Azure.Monitor.WebtestLocationAvailabilityCriteria
        webTestId: /subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/webtests/component-example
      description: Automatically created alert rule for availability test "component-example" a
      enabled: true
      evaluationFrequency: PT1M
      location: global
      resourceGroupName: rg-example
      ruleName: webtest-name-example
      scopes:
        - /subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/webtests/component-example
        - /subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/components/webtest-name-example
      severity: 4
      tags:
        ? hidden-link:/subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/components/webtest-name-example
        : Resource
        ? hidden-link:/subscriptions/12345678-1234-1234-1234-123456789101/resourcegroups/rg-example/providers/microsoft.insights/webtests/component-example
        : Resource
      windowSize: PT15M

```

{{% /example %}}
{{% example %}}
### Create or update an alert rule for Multiple Resource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var metricAlert = new AzureNative.Insights.MetricAlert("metricAlert", new()
    {
        Actions = new[]
        {
            new AzureNative.Insights.Inputs.MetricAlertActionArgs
            {
                ActionGroupId = "/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2",
                WebHookProperties = 
                {
                    { "key11", "value11" },
                    { "key12", "value12" },
                },
            },
        },
        AutoMitigate = true,
        Criteria = new AzureNative.Insights.Inputs.MetricAlertMultipleResourceMultipleMetricCriteriaArgs
        {
            AllOf = new[]
            {
                new AzureNative.Insights.Inputs.MetricCriteriaArgs
                {
                    CriterionType = "StaticThresholdCriterion",
                    Dimensions = new[] {},
                    MetricName = "Percentage CPU",
                    MetricNamespace = "microsoft.compute/virtualmachines",
                    Name = "High_CPU_80",
                    Operator = "GreaterThan",
                    Threshold = 80.5,
                    TimeAggregation = "Average",
                },
            },
            OdataType = "Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria",
        },
        Description = "This is the description of the rule1",
        Enabled = true,
        EvaluationFrequency = "PT1M",
        Location = "global",
        ResourceGroupName = "gigtest",
        RuleName = "MetricAlertOnMultipleResources",
        Scopes = new[]
        {
            "/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme1",
            "/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme2",
        },
        Severity = 3,
        Tags = null,
        TargetResourceRegion = "southcentralus",
        TargetResourceType = "Microsoft.Compute/virtualMachines",
        WindowSize = "PT15M",
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
		_, err := insights.NewMetricAlert(ctx, "metricAlert", &insights.MetricAlertArgs{
			Actions: []insights.MetricAlertActionArgs{
				{
					ActionGroupId: pulumi.String("/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2"),
					WebHookProperties: {
						"key11": pulumi.String("value11"),
						"key12": pulumi.String("value12"),
					},
				},
			},
			AutoMitigate: pulumi.Bool(true),
			Criteria: insights.MetricAlertMultipleResourceMultipleMetricCriteria{
				AllOf: []interface{}{
					insights.MetricCriteria{
						CriterionType:   "StaticThresholdCriterion",
						Dimensions:      []insights.MetricDimension{},
						MetricName:      "Percentage CPU",
						MetricNamespace: "microsoft.compute/virtualmachines",
						Name:            "High_CPU_80",
						Operator:        "GreaterThan",
						Threshold:       80.5,
						TimeAggregation: "Average",
					},
				},
				OdataType: "Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria",
			},
			Description:         pulumi.String("This is the description of the rule1"),
			Enabled:             pulumi.Bool(true),
			EvaluationFrequency: pulumi.String("PT1M"),
			Location:            pulumi.String("global"),
			ResourceGroupName:   pulumi.String("gigtest"),
			RuleName:            pulumi.String("MetricAlertOnMultipleResources"),
			Scopes: pulumi.StringArray{
				pulumi.String("/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme1"),
				pulumi.String("/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme2"),
			},
			Severity:             pulumi.Int(3),
			Tags:                 nil,
			TargetResourceRegion: pulumi.String("southcentralus"),
			TargetResourceType:   pulumi.String("Microsoft.Compute/virtualMachines"),
			WindowSize:           pulumi.String("PT15M"),
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
import com.pulumi.azurenative.insights.MetricAlert;
import com.pulumi.azurenative.insights.MetricAlertArgs;
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
        var metricAlert = new MetricAlert("metricAlert", MetricAlertArgs.builder()        
            .actions(Map.ofEntries(
                Map.entry("actionGroupId", "/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2"),
                Map.entry("webHookProperties", Map.ofEntries(
                    Map.entry("key11", "value11"),
                    Map.entry("key12", "value12")
                ))
            ))
            .autoMitigate(true)
            .criteria(Map.ofEntries(
                Map.entry("allOf", Map.ofEntries(
                    Map.entry("criterionType", "StaticThresholdCriterion"),
                    Map.entry("dimensions", ),
                    Map.entry("metricName", "Percentage CPU"),
                    Map.entry("metricNamespace", "microsoft.compute/virtualmachines"),
                    Map.entry("name", "High_CPU_80"),
                    Map.entry("operator", "GreaterThan"),
                    Map.entry("threshold", 80.5),
                    Map.entry("timeAggregation", "Average")
                )),
                Map.entry("odataType", "Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria")
            ))
            .description("This is the description of the rule1")
            .enabled(true)
            .evaluationFrequency("PT1M")
            .location("global")
            .resourceGroupName("gigtest")
            .ruleName("MetricAlertOnMultipleResources")
            .scopes(            
                "/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme1",
                "/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme2")
            .severity(3)
            .tags()
            .targetResourceRegion("southcentralus")
            .targetResourceType("Microsoft.Compute/virtualMachines")
            .windowSize("PT15M")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const metricAlert = new azure_native.insights.MetricAlert("metricAlert", {
    actions: [{
        actionGroupId: "/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2",
        webHookProperties: {
            key11: "value11",
            key12: "value12",
        },
    }],
    autoMitigate: true,
    criteria: {
        allOf: [{
            criterionType: "StaticThresholdCriterion",
            dimensions: [],
            metricName: "Percentage CPU",
            metricNamespace: "microsoft.compute/virtualmachines",
            name: "High_CPU_80",
            operator: "GreaterThan",
            threshold: 80.5,
            timeAggregation: "Average",
        }],
        odataType: "Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria",
    },
    description: "This is the description of the rule1",
    enabled: true,
    evaluationFrequency: "PT1M",
    location: "global",
    resourceGroupName: "gigtest",
    ruleName: "MetricAlertOnMultipleResources",
    scopes: [
        "/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme1",
        "/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme2",
    ],
    severity: 3,
    tags: {},
    targetResourceRegion: "southcentralus",
    targetResourceType: "Microsoft.Compute/virtualMachines",
    windowSize: "PT15M",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

metric_alert = azure_native.insights.MetricAlert("metricAlert",
    actions=[azure_native.insights.MetricAlertActionArgs(
        action_group_id="/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2",
        web_hook_properties={
            "key11": "value11",
            "key12": "value12",
        },
    )],
    auto_mitigate=True,
    criteria=azure_native.insights.MetricAlertMultipleResourceMultipleMetricCriteriaArgs(
        all_of=[azure_native.insights.MetricCriteriaArgs(
            criterion_type="StaticThresholdCriterion",
            dimensions=[],
            metric_name="Percentage CPU",
            metric_namespace="microsoft.compute/virtualmachines",
            name="High_CPU_80",
            operator="GreaterThan",
            threshold=80.5,
            time_aggregation="Average",
        )],
        odata_type="Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria",
    ),
    description="This is the description of the rule1",
    enabled=True,
    evaluation_frequency="PT1M",
    location="global",
    resource_group_name="gigtest",
    rule_name="MetricAlertOnMultipleResources",
    scopes=[
        "/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme1",
        "/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme2",
    ],
    severity=3,
    tags={},
    target_resource_region="southcentralus",
    target_resource_type="Microsoft.Compute/virtualMachines",
    window_size="PT15M")

```

```yaml
resources:
  metricAlert:
    type: azure-native:insights:MetricAlert
    properties:
      actions:
        - actionGroupId: /subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2
          webHookProperties:
            key11: value11
            key12: value12
      autoMitigate: true
      criteria:
        allOf:
          - criterionType: StaticThresholdCriterion
            dimensions: []
            metricName: Percentage CPU
            metricNamespace: microsoft.compute/virtualmachines
            name: High_CPU_80
            operator: GreaterThan
            threshold: 80.5
            timeAggregation: Average
        odataType: Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria
      description: This is the description of the rule1
      enabled: true
      evaluationFrequency: PT1M
      location: global
      resourceGroupName: gigtest
      ruleName: MetricAlertOnMultipleResources
      scopes:
        - /subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme1
        - /subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme2
      severity: 3
      tags: {}
      targetResourceRegion: southcentralus
      targetResourceType: Microsoft.Compute/virtualMachines
      windowSize: PT15M

```

{{% /example %}}
{{% example %}}
### Create or update an alert rule for Single Resource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var metricAlert = new AzureNative.Insights.MetricAlert("metricAlert", new()
    {
        Actions = new[]
        {
            new AzureNative.Insights.Inputs.MetricAlertActionArgs
            {
                ActionGroupId = "/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2",
                WebHookProperties = 
                {
                    { "key11", "value11" },
                    { "key12", "value12" },
                },
            },
        },
        AutoMitigate = true,
        Criteria = new AzureNative.Insights.Inputs.MetricAlertSingleResourceMultipleMetricCriteriaArgs
        {
            AllOf = new[]
            {
                new AzureNative.Insights.Inputs.MetricCriteriaArgs
                {
                    CriterionType = "StaticThresholdCriterion",
                    Dimensions = new[] {},
                    MetricName = "\\Processor(_Total)\\% Processor Time",
                    Name = "High_CPU_80",
                    Operator = "GreaterThan",
                    Threshold = 80.5,
                    TimeAggregation = "Average",
                },
            },
            OdataType = "Microsoft.Azure.Monitor.SingleResourceMultipleMetricCriteria",
        },
        Description = "This is the description of the rule1",
        Enabled = true,
        EvaluationFrequency = "Pt1m",
        Location = "global",
        ResourceGroupName = "gigtest",
        RuleName = "chiricutin",
        Scopes = new[]
        {
            "/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme",
        },
        Severity = 3,
        Tags = null,
        WindowSize = "Pt15m",
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
		_, err := insights.NewMetricAlert(ctx, "metricAlert", &insights.MetricAlertArgs{
			Actions: []insights.MetricAlertActionArgs{
				{
					ActionGroupId: pulumi.String("/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2"),
					WebHookProperties: {
						"key11": pulumi.String("value11"),
						"key12": pulumi.String("value12"),
					},
				},
			},
			AutoMitigate: pulumi.Bool(true),
			Criteria: insights.MetricAlertSingleResourceMultipleMetricCriteria{
				AllOf: []insights.MetricCriteria{
					{
						CriterionType:   "StaticThresholdCriterion",
						Dimensions:      []insights.MetricDimension{},
						MetricName:      "\\Processor(_Total)\\% Processor Time",
						Name:            "High_CPU_80",
						Operator:        "GreaterThan",
						Threshold:       80.5,
						TimeAggregation: "Average",
					},
				},
				OdataType: "Microsoft.Azure.Monitor.SingleResourceMultipleMetricCriteria",
			},
			Description:         pulumi.String("This is the description of the rule1"),
			Enabled:             pulumi.Bool(true),
			EvaluationFrequency: pulumi.String("Pt1m"),
			Location:            pulumi.String("global"),
			ResourceGroupName:   pulumi.String("gigtest"),
			RuleName:            pulumi.String("chiricutin"),
			Scopes: pulumi.StringArray{
				pulumi.String("/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme"),
			},
			Severity:   pulumi.Int(3),
			Tags:       nil,
			WindowSize: pulumi.String("Pt15m"),
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
import com.pulumi.azurenative.insights.MetricAlert;
import com.pulumi.azurenative.insights.MetricAlertArgs;
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
        var metricAlert = new MetricAlert("metricAlert", MetricAlertArgs.builder()        
            .actions(Map.ofEntries(
                Map.entry("actionGroupId", "/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2"),
                Map.entry("webHookProperties", Map.ofEntries(
                    Map.entry("key11", "value11"),
                    Map.entry("key12", "value12")
                ))
            ))
            .autoMitigate(true)
            .criteria(Map.ofEntries(
                Map.entry("allOf", Map.ofEntries(
                    Map.entry("criterionType", "StaticThresholdCriterion"),
                    Map.entry("dimensions", ),
                    Map.entry("metricName", "\\Processor(_Total)\\% Processor Time"),
                    Map.entry("name", "High_CPU_80"),
                    Map.entry("operator", "GreaterThan"),
                    Map.entry("threshold", 80.5),
                    Map.entry("timeAggregation", "Average")
                )),
                Map.entry("odataType", "Microsoft.Azure.Monitor.SingleResourceMultipleMetricCriteria")
            ))
            .description("This is the description of the rule1")
            .enabled(true)
            .evaluationFrequency("Pt1m")
            .location("global")
            .resourceGroupName("gigtest")
            .ruleName("chiricutin")
            .scopes("/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme")
            .severity(3)
            .tags()
            .windowSize("Pt15m")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const metricAlert = new azure_native.insights.MetricAlert("metricAlert", {
    actions: [{
        actionGroupId: "/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2",
        webHookProperties: {
            key11: "value11",
            key12: "value12",
        },
    }],
    autoMitigate: true,
    criteria: {
        allOf: [{
            criterionType: "StaticThresholdCriterion",
            dimensions: [],
            metricName: "\\Processor(_Total)\\% Processor Time",
            name: "High_CPU_80",
            operator: "GreaterThan",
            threshold: 80.5,
            timeAggregation: "Average",
        }],
        odataType: "Microsoft.Azure.Monitor.SingleResourceMultipleMetricCriteria",
    },
    description: "This is the description of the rule1",
    enabled: true,
    evaluationFrequency: "Pt1m",
    location: "global",
    resourceGroupName: "gigtest",
    ruleName: "chiricutin",
    scopes: ["/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme"],
    severity: 3,
    tags: {},
    windowSize: "Pt15m",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

metric_alert = azure_native.insights.MetricAlert("metricAlert",
    actions=[azure_native.insights.MetricAlertActionArgs(
        action_group_id="/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2",
        web_hook_properties={
            "key11": "value11",
            "key12": "value12",
        },
    )],
    auto_mitigate=True,
    criteria=azure_native.insights.MetricAlertSingleResourceMultipleMetricCriteriaArgs(
        all_of=[azure_native.insights.MetricCriteriaArgs(
            criterion_type="StaticThresholdCriterion",
            dimensions=[],
            metric_name="\\Processor(_Total)\\% Processor Time",
            name="High_CPU_80",
            operator="GreaterThan",
            threshold=80.5,
            time_aggregation="Average",
        )],
        odata_type="Microsoft.Azure.Monitor.SingleResourceMultipleMetricCriteria",
    ),
    description="This is the description of the rule1",
    enabled=True,
    evaluation_frequency="Pt1m",
    location="global",
    resource_group_name="gigtest",
    rule_name="chiricutin",
    scopes=["/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme"],
    severity=3,
    tags={},
    window_size="Pt15m")

```

```yaml
resources:
  metricAlert:
    type: azure-native:insights:MetricAlert
    properties:
      actions:
        - actionGroupId: /subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2
          webHookProperties:
            key11: value11
            key12: value12
      autoMitigate: true
      criteria:
        allOf:
          - criterionType: StaticThresholdCriterion
            dimensions: []
            metricName: \Processor(_Total)\% Processor Time
            name: High_CPU_80
            operator: GreaterThan
            threshold: 80.5
            timeAggregation: Average
        odataType: Microsoft.Azure.Monitor.SingleResourceMultipleMetricCriteria
      description: This is the description of the rule1
      enabled: true
      evaluationFrequency: Pt1m
      location: global
      resourceGroupName: gigtest
      ruleName: chiricutin
      scopes:
        - /subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest/providers/Microsoft.Compute/virtualMachines/gigwadme
      severity: 3
      tags: {}
      windowSize: Pt15m

```

{{% /example %}}
{{% example %}}
### Create or update an alert rule on Resource group(s)
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var metricAlert = new AzureNative.Insights.MetricAlert("metricAlert", new()
    {
        Actions = new[]
        {
            new AzureNative.Insights.Inputs.MetricAlertActionArgs
            {
                ActionGroupId = "/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2",
                WebHookProperties = 
                {
                    { "key11", "value11" },
                    { "key12", "value12" },
                },
            },
        },
        AutoMitigate = true,
        Criteria = new AzureNative.Insights.Inputs.MetricAlertMultipleResourceMultipleMetricCriteriaArgs
        {
            AllOf = new[]
            {
                new AzureNative.Insights.Inputs.MetricCriteriaArgs
                {
                    CriterionType = "StaticThresholdCriterion",
                    Dimensions = new[] {},
                    MetricName = "Percentage CPU",
                    MetricNamespace = "microsoft.compute/virtualmachines",
                    Name = "High_CPU_80",
                    Operator = "GreaterThan",
                    Threshold = 80.5,
                    TimeAggregation = "Average",
                },
            },
            OdataType = "Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria",
        },
        Description = "This is the description of the rule1",
        Enabled = true,
        EvaluationFrequency = "PT1M",
        Location = "global",
        ResourceGroupName = "gigtest1",
        RuleName = "MetricAlertAtResourceGroupLevel",
        Scopes = new[]
        {
            "/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest1",
            "/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest2",
        },
        Severity = 3,
        Tags = null,
        TargetResourceRegion = "southcentralus",
        TargetResourceType = "Microsoft.Compute/virtualMachines",
        WindowSize = "PT15M",
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
		_, err := insights.NewMetricAlert(ctx, "metricAlert", &insights.MetricAlertArgs{
			Actions: []insights.MetricAlertActionArgs{
				{
					ActionGroupId: pulumi.String("/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2"),
					WebHookProperties: {
						"key11": pulumi.String("value11"),
						"key12": pulumi.String("value12"),
					},
				},
			},
			AutoMitigate: pulumi.Bool(true),
			Criteria: insights.MetricAlertMultipleResourceMultipleMetricCriteria{
				AllOf: []interface{}{
					insights.MetricCriteria{
						CriterionType:   "StaticThresholdCriterion",
						Dimensions:      []insights.MetricDimension{},
						MetricName:      "Percentage CPU",
						MetricNamespace: "microsoft.compute/virtualmachines",
						Name:            "High_CPU_80",
						Operator:        "GreaterThan",
						Threshold:       80.5,
						TimeAggregation: "Average",
					},
				},
				OdataType: "Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria",
			},
			Description:         pulumi.String("This is the description of the rule1"),
			Enabled:             pulumi.Bool(true),
			EvaluationFrequency: pulumi.String("PT1M"),
			Location:            pulumi.String("global"),
			ResourceGroupName:   pulumi.String("gigtest1"),
			RuleName:            pulumi.String("MetricAlertAtResourceGroupLevel"),
			Scopes: pulumi.StringArray{
				pulumi.String("/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest1"),
				pulumi.String("/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest2"),
			},
			Severity:             pulumi.Int(3),
			Tags:                 nil,
			TargetResourceRegion: pulumi.String("southcentralus"),
			TargetResourceType:   pulumi.String("Microsoft.Compute/virtualMachines"),
			WindowSize:           pulumi.String("PT15M"),
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
import com.pulumi.azurenative.insights.MetricAlert;
import com.pulumi.azurenative.insights.MetricAlertArgs;
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
        var metricAlert = new MetricAlert("metricAlert", MetricAlertArgs.builder()        
            .actions(Map.ofEntries(
                Map.entry("actionGroupId", "/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2"),
                Map.entry("webHookProperties", Map.ofEntries(
                    Map.entry("key11", "value11"),
                    Map.entry("key12", "value12")
                ))
            ))
            .autoMitigate(true)
            .criteria(Map.ofEntries(
                Map.entry("allOf", Map.ofEntries(
                    Map.entry("criterionType", "StaticThresholdCriterion"),
                    Map.entry("dimensions", ),
                    Map.entry("metricName", "Percentage CPU"),
                    Map.entry("metricNamespace", "microsoft.compute/virtualmachines"),
                    Map.entry("name", "High_CPU_80"),
                    Map.entry("operator", "GreaterThan"),
                    Map.entry("threshold", 80.5),
                    Map.entry("timeAggregation", "Average")
                )),
                Map.entry("odataType", "Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria")
            ))
            .description("This is the description of the rule1")
            .enabled(true)
            .evaluationFrequency("PT1M")
            .location("global")
            .resourceGroupName("gigtest1")
            .ruleName("MetricAlertAtResourceGroupLevel")
            .scopes(            
                "/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest1",
                "/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest2")
            .severity(3)
            .tags()
            .targetResourceRegion("southcentralus")
            .targetResourceType("Microsoft.Compute/virtualMachines")
            .windowSize("PT15M")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const metricAlert = new azure_native.insights.MetricAlert("metricAlert", {
    actions: [{
        actionGroupId: "/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2",
        webHookProperties: {
            key11: "value11",
            key12: "value12",
        },
    }],
    autoMitigate: true,
    criteria: {
        allOf: [{
            criterionType: "StaticThresholdCriterion",
            dimensions: [],
            metricName: "Percentage CPU",
            metricNamespace: "microsoft.compute/virtualmachines",
            name: "High_CPU_80",
            operator: "GreaterThan",
            threshold: 80.5,
            timeAggregation: "Average",
        }],
        odataType: "Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria",
    },
    description: "This is the description of the rule1",
    enabled: true,
    evaluationFrequency: "PT1M",
    location: "global",
    resourceGroupName: "gigtest1",
    ruleName: "MetricAlertAtResourceGroupLevel",
    scopes: [
        "/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest1",
        "/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest2",
    ],
    severity: 3,
    tags: {},
    targetResourceRegion: "southcentralus",
    targetResourceType: "Microsoft.Compute/virtualMachines",
    windowSize: "PT15M",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

metric_alert = azure_native.insights.MetricAlert("metricAlert",
    actions=[azure_native.insights.MetricAlertActionArgs(
        action_group_id="/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2",
        web_hook_properties={
            "key11": "value11",
            "key12": "value12",
        },
    )],
    auto_mitigate=True,
    criteria=azure_native.insights.MetricAlertMultipleResourceMultipleMetricCriteriaArgs(
        all_of=[azure_native.insights.MetricCriteriaArgs(
            criterion_type="StaticThresholdCriterion",
            dimensions=[],
            metric_name="Percentage CPU",
            metric_namespace="microsoft.compute/virtualmachines",
            name="High_CPU_80",
            operator="GreaterThan",
            threshold=80.5,
            time_aggregation="Average",
        )],
        odata_type="Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria",
    ),
    description="This is the description of the rule1",
    enabled=True,
    evaluation_frequency="PT1M",
    location="global",
    resource_group_name="gigtest1",
    rule_name="MetricAlertAtResourceGroupLevel",
    scopes=[
        "/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest1",
        "/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest2",
    ],
    severity=3,
    tags={},
    target_resource_region="southcentralus",
    target_resource_type="Microsoft.Compute/virtualMachines",
    window_size="PT15M")

```

```yaml
resources:
  metricAlert:
    type: azure-native:insights:MetricAlert
    properties:
      actions:
        - actionGroupId: /subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2
          webHookProperties:
            key11: value11
            key12: value12
      autoMitigate: true
      criteria:
        allOf:
          - criterionType: StaticThresholdCriterion
            dimensions: []
            metricName: Percentage CPU
            metricNamespace: microsoft.compute/virtualmachines
            name: High_CPU_80
            operator: GreaterThan
            threshold: 80.5
            timeAggregation: Average
        odataType: Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria
      description: This is the description of the rule1
      enabled: true
      evaluationFrequency: PT1M
      location: global
      resourceGroupName: gigtest1
      ruleName: MetricAlertAtResourceGroupLevel
      scopes:
        - /subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest1
        - /subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest2
      severity: 3
      tags: {}
      targetResourceRegion: southcentralus
      targetResourceType: Microsoft.Compute/virtualMachines
      windowSize: PT15M

```

{{% /example %}}
{{% example %}}
### Create or update an alert rule on Subscription 
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var metricAlert = new AzureNative.Insights.MetricAlert("metricAlert", new()
    {
        Actions = new[]
        {
            new AzureNative.Insights.Inputs.MetricAlertActionArgs
            {
                ActionGroupId = "/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2",
                WebHookProperties = 
                {
                    { "key11", "value11" },
                    { "key12", "value12" },
                },
            },
        },
        AutoMitigate = true,
        Criteria = new AzureNative.Insights.Inputs.MetricAlertMultipleResourceMultipleMetricCriteriaArgs
        {
            AllOf = new[]
            {
                new AzureNative.Insights.Inputs.MetricCriteriaArgs
                {
                    CriterionType = "StaticThresholdCriterion",
                    Dimensions = new[] {},
                    MetricName = "Percentage CPU",
                    MetricNamespace = "microsoft.compute/virtualmachines",
                    Name = "High_CPU_80",
                    Operator = "GreaterThan",
                    Threshold = 80.5,
                    TimeAggregation = "Average",
                },
            },
            OdataType = "Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria",
        },
        Description = "This is the description of the rule1",
        Enabled = true,
        EvaluationFrequency = "PT1M",
        Location = "global",
        ResourceGroupName = "gigtest",
        RuleName = "MetricAlertAtSubscriptionLevel",
        Scopes = new[]
        {
            "/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7",
        },
        Severity = 3,
        Tags = null,
        TargetResourceRegion = "southcentralus",
        TargetResourceType = "Microsoft.Compute/virtualMachines",
        WindowSize = "PT15M",
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
		_, err := insights.NewMetricAlert(ctx, "metricAlert", &insights.MetricAlertArgs{
			Actions: []insights.MetricAlertActionArgs{
				{
					ActionGroupId: pulumi.String("/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2"),
					WebHookProperties: {
						"key11": pulumi.String("value11"),
						"key12": pulumi.String("value12"),
					},
				},
			},
			AutoMitigate: pulumi.Bool(true),
			Criteria: insights.MetricAlertMultipleResourceMultipleMetricCriteria{
				AllOf: []interface{}{
					insights.MetricCriteria{
						CriterionType:   "StaticThresholdCriterion",
						Dimensions:      []insights.MetricDimension{},
						MetricName:      "Percentage CPU",
						MetricNamespace: "microsoft.compute/virtualmachines",
						Name:            "High_CPU_80",
						Operator:        "GreaterThan",
						Threshold:       80.5,
						TimeAggregation: "Average",
					},
				},
				OdataType: "Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria",
			},
			Description:         pulumi.String("This is the description of the rule1"),
			Enabled:             pulumi.Bool(true),
			EvaluationFrequency: pulumi.String("PT1M"),
			Location:            pulumi.String("global"),
			ResourceGroupName:   pulumi.String("gigtest"),
			RuleName:            pulumi.String("MetricAlertAtSubscriptionLevel"),
			Scopes: pulumi.StringArray{
				pulumi.String("/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7"),
			},
			Severity:             pulumi.Int(3),
			Tags:                 nil,
			TargetResourceRegion: pulumi.String("southcentralus"),
			TargetResourceType:   pulumi.String("Microsoft.Compute/virtualMachines"),
			WindowSize:           pulumi.String("PT15M"),
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
import com.pulumi.azurenative.insights.MetricAlert;
import com.pulumi.azurenative.insights.MetricAlertArgs;
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
        var metricAlert = new MetricAlert("metricAlert", MetricAlertArgs.builder()        
            .actions(Map.ofEntries(
                Map.entry("actionGroupId", "/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2"),
                Map.entry("webHookProperties", Map.ofEntries(
                    Map.entry("key11", "value11"),
                    Map.entry("key12", "value12")
                ))
            ))
            .autoMitigate(true)
            .criteria(Map.ofEntries(
                Map.entry("allOf", Map.ofEntries(
                    Map.entry("criterionType", "StaticThresholdCriterion"),
                    Map.entry("dimensions", ),
                    Map.entry("metricName", "Percentage CPU"),
                    Map.entry("metricNamespace", "microsoft.compute/virtualmachines"),
                    Map.entry("name", "High_CPU_80"),
                    Map.entry("operator", "GreaterThan"),
                    Map.entry("threshold", 80.5),
                    Map.entry("timeAggregation", "Average")
                )),
                Map.entry("odataType", "Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria")
            ))
            .description("This is the description of the rule1")
            .enabled(true)
            .evaluationFrequency("PT1M")
            .location("global")
            .resourceGroupName("gigtest")
            .ruleName("MetricAlertAtSubscriptionLevel")
            .scopes("/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7")
            .severity(3)
            .tags()
            .targetResourceRegion("southcentralus")
            .targetResourceType("Microsoft.Compute/virtualMachines")
            .windowSize("PT15M")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const metricAlert = new azure_native.insights.MetricAlert("metricAlert", {
    actions: [{
        actionGroupId: "/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2",
        webHookProperties: {
            key11: "value11",
            key12: "value12",
        },
    }],
    autoMitigate: true,
    criteria: {
        allOf: [{
            criterionType: "StaticThresholdCriterion",
            dimensions: [],
            metricName: "Percentage CPU",
            metricNamespace: "microsoft.compute/virtualmachines",
            name: "High_CPU_80",
            operator: "GreaterThan",
            threshold: 80.5,
            timeAggregation: "Average",
        }],
        odataType: "Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria",
    },
    description: "This is the description of the rule1",
    enabled: true,
    evaluationFrequency: "PT1M",
    location: "global",
    resourceGroupName: "gigtest",
    ruleName: "MetricAlertAtSubscriptionLevel",
    scopes: ["/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7"],
    severity: 3,
    tags: {},
    targetResourceRegion: "southcentralus",
    targetResourceType: "Microsoft.Compute/virtualMachines",
    windowSize: "PT15M",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

metric_alert = azure_native.insights.MetricAlert("metricAlert",
    actions=[azure_native.insights.MetricAlertActionArgs(
        action_group_id="/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2",
        web_hook_properties={
            "key11": "value11",
            "key12": "value12",
        },
    )],
    auto_mitigate=True,
    criteria=azure_native.insights.MetricAlertMultipleResourceMultipleMetricCriteriaArgs(
        all_of=[azure_native.insights.MetricCriteriaArgs(
            criterion_type="StaticThresholdCriterion",
            dimensions=[],
            metric_name="Percentage CPU",
            metric_namespace="microsoft.compute/virtualmachines",
            name="High_CPU_80",
            operator="GreaterThan",
            threshold=80.5,
            time_aggregation="Average",
        )],
        odata_type="Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria",
    ),
    description="This is the description of the rule1",
    enabled=True,
    evaluation_frequency="PT1M",
    location="global",
    resource_group_name="gigtest",
    rule_name="MetricAlertAtSubscriptionLevel",
    scopes=["/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7"],
    severity=3,
    tags={},
    target_resource_region="southcentralus",
    target_resource_type="Microsoft.Compute/virtualMachines",
    window_size="PT15M")

```

```yaml
resources:
  metricAlert:
    type: azure-native:insights:MetricAlert
    properties:
      actions:
        - actionGroupId: /subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2
          webHookProperties:
            key11: value11
            key12: value12
      autoMitigate: true
      criteria:
        allOf:
          - criterionType: StaticThresholdCriterion
            dimensions: []
            metricName: Percentage CPU
            metricNamespace: microsoft.compute/virtualmachines
            name: High_CPU_80
            operator: GreaterThan
            threshold: 80.5
            timeAggregation: Average
        odataType: Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria
      description: This is the description of the rule1
      enabled: true
      evaluationFrequency: PT1M
      location: global
      resourceGroupName: gigtest
      ruleName: MetricAlertAtSubscriptionLevel
      scopes:
        - /subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7
      severity: 3
      tags: {}
      targetResourceRegion: southcentralus
      targetResourceType: Microsoft.Compute/virtualMachines
      windowSize: PT15M

```

{{% /example %}}
{{% example %}}
### Create or update an alert rules with dimensions
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var metricAlert = new AzureNative.Insights.MetricAlert("metricAlert", new()
    {
        Actions = new[]
        {
            new AzureNative.Insights.Inputs.MetricAlertActionArgs
            {
                ActionGroupId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2",
                WebHookProperties = 
                {
                    { "key11", "value11" },
                    { "key12", "value12" },
                },
            },
        },
        AutoMitigate = true,
        Criteria = new AzureNative.Insights.Inputs.MetricAlertMultipleResourceMultipleMetricCriteriaArgs
        {
            AllOf = new[]
            {
                new AzureNative.Insights.Inputs.MetricCriteriaArgs
                {
                    CriterionType = "StaticThresholdCriterion",
                    Dimensions = new[]
                    {
                        new AzureNative.Insights.Inputs.MetricDimensionArgs
                        {
                            Name = "ActivityName",
                            Operator = "Include",
                            Values = new[]
                            {
                                "*",
                            },
                        },
                        new AzureNative.Insights.Inputs.MetricDimensionArgs
                        {
                            Name = "StatusCode",
                            Operator = "Include",
                            Values = new[]
                            {
                                "200",
                            },
                        },
                    },
                    MetricName = "Availability",
                    MetricNamespace = "Microsoft.KeyVault/vaults",
                    Name = "Metric1",
                    Operator = "GreaterThan",
                    Threshold = 55,
                    TimeAggregation = "Average",
                },
            },
            OdataType = "Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria",
        },
        Description = "This is the description of the rule1",
        Enabled = true,
        EvaluationFrequency = "PT1H",
        Location = "global",
        ResourceGroupName = "gigtest",
        RuleName = "MetricAlertOnMultipleDimensions",
        Scopes = new[]
        {
            "/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest/providers/Microsoft.KeyVault/vaults/keyVaultResource",
        },
        Severity = 3,
        Tags = null,
        WindowSize = "P1D",
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
		_, err := insights.NewMetricAlert(ctx, "metricAlert", &insights.MetricAlertArgs{
			Actions: []insights.MetricAlertActionArgs{
				{
					ActionGroupId: pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2"),
					WebHookProperties: {
						"key11": pulumi.String("value11"),
						"key12": pulumi.String("value12"),
					},
				},
			},
			AutoMitigate: pulumi.Bool(true),
			Criteria: insights.MetricAlertMultipleResourceMultipleMetricCriteria{
				AllOf: []interface{}{
					insights.MetricCriteria{
						CriterionType: "StaticThresholdCriterion",
						Dimensions: []insights.MetricDimension{
							{
								Name:     "ActivityName",
								Operator: "Include",
								Values: []string{
									"*",
								},
							},
							{
								Name:     "StatusCode",
								Operator: "Include",
								Values: []string{
									"200",
								},
							},
						},
						MetricName:      "Availability",
						MetricNamespace: "Microsoft.KeyVault/vaults",
						Name:            "Metric1",
						Operator:        "GreaterThan",
						Threshold:       55,
						TimeAggregation: "Average",
					},
				},
				OdataType: "Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria",
			},
			Description:         pulumi.String("This is the description of the rule1"),
			Enabled:             pulumi.Bool(true),
			EvaluationFrequency: pulumi.String("PT1H"),
			Location:            pulumi.String("global"),
			ResourceGroupName:   pulumi.String("gigtest"),
			RuleName:            pulumi.String("MetricAlertOnMultipleDimensions"),
			Scopes: pulumi.StringArray{
				pulumi.String("/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest/providers/Microsoft.KeyVault/vaults/keyVaultResource"),
			},
			Severity:   pulumi.Int(3),
			Tags:       nil,
			WindowSize: pulumi.String("P1D"),
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
import com.pulumi.azurenative.insights.MetricAlert;
import com.pulumi.azurenative.insights.MetricAlertArgs;
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
        var metricAlert = new MetricAlert("metricAlert", MetricAlertArgs.builder()        
            .actions(Map.ofEntries(
                Map.entry("actionGroupId", "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2"),
                Map.entry("webHookProperties", Map.ofEntries(
                    Map.entry("key11", "value11"),
                    Map.entry("key12", "value12")
                ))
            ))
            .autoMitigate(true)
            .criteria(Map.ofEntries(
                Map.entry("allOf", Map.ofEntries(
                    Map.entry("criterionType", "StaticThresholdCriterion"),
                    Map.entry("dimensions",                     
                        Map.ofEntries(
                            Map.entry("name", "ActivityName"),
                            Map.entry("operator", "Include"),
                            Map.entry("values", "*")
                        ),
                        Map.ofEntries(
                            Map.entry("name", "StatusCode"),
                            Map.entry("operator", "Include"),
                            Map.entry("values", "200")
                        )),
                    Map.entry("metricName", "Availability"),
                    Map.entry("metricNamespace", "Microsoft.KeyVault/vaults"),
                    Map.entry("name", "Metric1"),
                    Map.entry("operator", "GreaterThan"),
                    Map.entry("threshold", 55),
                    Map.entry("timeAggregation", "Average")
                )),
                Map.entry("odataType", "Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria")
            ))
            .description("This is the description of the rule1")
            .enabled(true)
            .evaluationFrequency("PT1H")
            .location("global")
            .resourceGroupName("gigtest")
            .ruleName("MetricAlertOnMultipleDimensions")
            .scopes("/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest/providers/Microsoft.KeyVault/vaults/keyVaultResource")
            .severity(3)
            .tags()
            .windowSize("P1D")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const metricAlert = new azure_native.insights.MetricAlert("metricAlert", {
    actions: [{
        actionGroupId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2",
        webHookProperties: {
            key11: "value11",
            key12: "value12",
        },
    }],
    autoMitigate: true,
    criteria: {
        allOf: [{
            criterionType: "StaticThresholdCriterion",
            dimensions: [
                {
                    name: "ActivityName",
                    operator: "Include",
                    values: ["*"],
                },
                {
                    name: "StatusCode",
                    operator: "Include",
                    values: ["200"],
                },
            ],
            metricName: "Availability",
            metricNamespace: "Microsoft.KeyVault/vaults",
            name: "Metric1",
            operator: "GreaterThan",
            threshold: 55,
            timeAggregation: "Average",
        }],
        odataType: "Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria",
    },
    description: "This is the description of the rule1",
    enabled: true,
    evaluationFrequency: "PT1H",
    location: "global",
    resourceGroupName: "gigtest",
    ruleName: "MetricAlertOnMultipleDimensions",
    scopes: ["/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest/providers/Microsoft.KeyVault/vaults/keyVaultResource"],
    severity: 3,
    tags: {},
    windowSize: "P1D",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

metric_alert = azure_native.insights.MetricAlert("metricAlert",
    actions=[azure_native.insights.MetricAlertActionArgs(
        action_group_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2",
        web_hook_properties={
            "key11": "value11",
            "key12": "value12",
        },
    )],
    auto_mitigate=True,
    criteria=azure_native.insights.MetricAlertMultipleResourceMultipleMetricCriteriaArgs(
        all_of=[azure_native.insights.MetricCriteriaArgs(
            criterion_type="StaticThresholdCriterion",
            dimensions=[
                azure_native.insights.MetricDimensionArgs(
                    name="ActivityName",
                    operator="Include",
                    values=["*"],
                ),
                azure_native.insights.MetricDimensionArgs(
                    name="StatusCode",
                    operator="Include",
                    values=["200"],
                ),
            ],
            metric_name="Availability",
            metric_namespace="Microsoft.KeyVault/vaults",
            name="Metric1",
            operator="GreaterThan",
            threshold=55,
            time_aggregation="Average",
        )],
        odata_type="Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria",
    ),
    description="This is the description of the rule1",
    enabled=True,
    evaluation_frequency="PT1H",
    location="global",
    resource_group_name="gigtest",
    rule_name="MetricAlertOnMultipleDimensions",
    scopes=["/subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest/providers/Microsoft.KeyVault/vaults/keyVaultResource"],
    severity=3,
    tags={},
    window_size="P1D")

```

```yaml
resources:
  metricAlert:
    type: azure-native:insights:MetricAlert
    properties:
      actions:
        - actionGroupId: /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/gigtest/providers/microsoft.insights/actiongroups/group2
          webHookProperties:
            key11: value11
            key12: value12
      autoMitigate: true
      criteria:
        allOf:
          - criterionType: StaticThresholdCriterion
            dimensions:
              - name: ActivityName
                operator: Include
                values:
                  - '*'
              - name: StatusCode
                operator: Include
                values:
                  - '200'
            metricName: Availability
            metricNamespace: Microsoft.KeyVault/vaults
            name: Metric1
            operator: GreaterThan
            threshold: 55
            timeAggregation: Average
        odataType: Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria
      description: This is the description of the rule1
      enabled: true
      evaluationFrequency: PT1H
      location: global
      resourceGroupName: gigtest
      ruleName: MetricAlertOnMultipleDimensions
      scopes:
        - /subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest/providers/Microsoft.KeyVault/vaults/keyVaultResource
      severity: 3
      tags: {}
      windowSize: P1D

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:insights:MetricAlert webtest-name-example /subscriptions/14ddf0c5-77c5-4b53-84f6-e1fa43ad68f7/resourceGroups/gigtest/providers/providers/microsoft.insights/metricalerts/MetricAlertWithDimensions 
```
