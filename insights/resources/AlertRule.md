The alert rule resource.
API Version: 2016-03-01.
Previous API Version: 2016-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update an alert rule
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var alertRule = new AzureNative.Insights.AlertRule("alertRule", new()
    {
        Actions = new[] {},
        Condition = new AzureNative.Insights.Inputs.ThresholdRuleConditionArgs
        {
            DataSource = new AzureNative.Insights.Inputs.RuleMetricDataSourceArgs
            {
                MetricName = "Requests",
                OdataType = "Microsoft.Azure.Management.Insights.Models.RuleMetricDataSource",
                ResourceUri = "/subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/Rac46PostSwapRG/providers/Microsoft.Web/sites/leoalerttest",
            },
            OdataType = "Microsoft.Azure.Management.Insights.Models.ThresholdRuleCondition",
            Operator = AzureNative.Insights.ConditionOperator.GreaterThan,
            Threshold = 3,
            TimeAggregation = AzureNative.Insights.TimeAggregationOperator.Total,
            WindowSize = "PT5M",
        },
        Description = "Pura Vida",
        IsEnabled = true,
        Location = "West US",
        Name = "chiricutin",
        ResourceGroupName = "Rac46PostSwapRG",
        RuleName = "chiricutin",
        Tags = null,
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
		_, err := insights.NewAlertRule(ctx, "alertRule", &insights.AlertRuleArgs{
			Actions: pulumi.AnyArray{},
			Condition: insights.ThresholdRuleCondition{
				DataSource: insights.RuleMetricDataSource{
					MetricName:  "Requests",
					OdataType:   "Microsoft.Azure.Management.Insights.Models.RuleMetricDataSource",
					ResourceUri: "/subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/Rac46PostSwapRG/providers/Microsoft.Web/sites/leoalerttest",
				},
				OdataType:       "Microsoft.Azure.Management.Insights.Models.ThresholdRuleCondition",
				Operator:        insights.ConditionOperatorGreaterThan,
				Threshold:       3,
				TimeAggregation: insights.TimeAggregationOperatorTotal,
				WindowSize:      "PT5M",
			},
			Description:       pulumi.String("Pura Vida"),
			IsEnabled:         pulumi.Bool(true),
			Location:          pulumi.String("West US"),
			Name:              pulumi.String("chiricutin"),
			ResourceGroupName: pulumi.String("Rac46PostSwapRG"),
			RuleName:          pulumi.String("chiricutin"),
			Tags:              nil,
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
import com.pulumi.azurenative.insights.AlertRule;
import com.pulumi.azurenative.insights.AlertRuleArgs;
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
        var alertRule = new AlertRule("alertRule", AlertRuleArgs.builder()        
            .actions()
            .condition(Map.ofEntries(
                Map.entry("dataSource", Map.ofEntries(
                    Map.entry("metricName", "Requests"),
                    Map.entry("odataType", "Microsoft.Azure.Management.Insights.Models.RuleMetricDataSource"),
                    Map.entry("resourceUri", "/subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/Rac46PostSwapRG/providers/Microsoft.Web/sites/leoalerttest")
                )),
                Map.entry("odataType", "Microsoft.Azure.Management.Insights.Models.ThresholdRuleCondition"),
                Map.entry("operator", "GreaterThan"),
                Map.entry("threshold", 3),
                Map.entry("timeAggregation", "Total"),
                Map.entry("windowSize", "PT5M")
            ))
            .description("Pura Vida")
            .isEnabled(true)
            .location("West US")
            .name("chiricutin")
            .resourceGroupName("Rac46PostSwapRG")
            .ruleName("chiricutin")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const alertRule = new azure_native.insights.AlertRule("alertRule", {
    actions: [],
    condition: {
        dataSource: {
            metricName: "Requests",
            odataType: "Microsoft.Azure.Management.Insights.Models.RuleMetricDataSource",
            resourceUri: "/subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/Rac46PostSwapRG/providers/Microsoft.Web/sites/leoalerttest",
        },
        odataType: "Microsoft.Azure.Management.Insights.Models.ThresholdRuleCondition",
        operator: azure_native.insights.ConditionOperator.GreaterThan,
        threshold: 3,
        timeAggregation: azure_native.insights.TimeAggregationOperator.Total,
        windowSize: "PT5M",
    },
    description: "Pura Vida",
    isEnabled: true,
    location: "West US",
    name: "chiricutin",
    resourceGroupName: "Rac46PostSwapRG",
    ruleName: "chiricutin",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

alert_rule = azure_native.insights.AlertRule("alertRule",
    actions=[],
    condition=azure_native.insights.ThresholdRuleConditionArgs(
        data_source=azure_native.insights.RuleMetricDataSourceArgs(
            metric_name="Requests",
            odata_type="Microsoft.Azure.Management.Insights.Models.RuleMetricDataSource",
            resource_uri="/subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/Rac46PostSwapRG/providers/Microsoft.Web/sites/leoalerttest",
        ),
        odata_type="Microsoft.Azure.Management.Insights.Models.ThresholdRuleCondition",
        operator=azure_native.insights.ConditionOperator.GREATER_THAN,
        threshold=3,
        time_aggregation=azure_native.insights.TimeAggregationOperator.TOTAL,
        window_size="PT5M",
    ),
    description="Pura Vida",
    is_enabled=True,
    location="West US",
    name="chiricutin",
    resource_group_name="Rac46PostSwapRG",
    rule_name="chiricutin",
    tags={})

```

```yaml
resources:
  alertRule:
    type: azure-native:insights:AlertRule
    properties:
      actions: []
      condition:
        dataSource:
          metricName: Requests
          odataType: Microsoft.Azure.Management.Insights.Models.RuleMetricDataSource
          resourceUri: /subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/Rac46PostSwapRG/providers/Microsoft.Web/sites/leoalerttest
        odataType: Microsoft.Azure.Management.Insights.Models.ThresholdRuleCondition
        operator: GreaterThan
        threshold: 3
        timeAggregation: Total
        windowSize: PT5M
      description: Pura Vida
      isEnabled: true
      location: West US
      name: chiricutin
      resourceGroupName: Rac46PostSwapRG
      ruleName: chiricutin
      tags: {}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:insights:AlertRule chiricutin /subscriptions/b67f7fec-69fc-4974-9099-a26bd6ffeda3/resourceGroups/Rac46PostSwapRG/providers/microsoft.insights/alertrules/chiricutin 
```
