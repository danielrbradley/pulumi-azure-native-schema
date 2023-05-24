States and configurations of Cost Analysis.
API Version: 2022-10-01.
Previous API Version: 2019-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ResourceGroupCreateOrUpdateView
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var viewByScope = new AzureNative.CostManagement.ViewByScope("viewByScope", new()
    {
        Accumulated = "true",
        Chart = "Table",
        DataSet = new AzureNative.CostManagement.Inputs.ReportConfigDatasetArgs
        {
            Aggregation = 
            {
                { "totalCost", new AzureNative.CostManagement.Inputs.ReportConfigAggregationArgs
                {
                    Function = "Sum",
                    Name = "PreTaxCost",
                } },
            },
            Granularity = "Daily",
            Grouping = new[] {},
            Sorting = new[]
            {
                new AzureNative.CostManagement.Inputs.ReportConfigSortingArgs
                {
                    Direction = "Ascending",
                    Name = "UsageDate",
                },
            },
        },
        DisplayName = "swagger Example",
        ETag = "\"1d4ff9fe66f1d10\"",
        Kpis = new[]
        {
            new AzureNative.CostManagement.Inputs.KpiPropertiesArgs
            {
                Enabled = true,
                Type = "Forecast",
            },
            new AzureNative.CostManagement.Inputs.KpiPropertiesArgs
            {
                Enabled = true,
                Id = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Consumption/budgets/swaggerDemo",
                Type = "Budget",
            },
        },
        Metric = "ActualCost",
        Pivots = new[]
        {
            new AzureNative.CostManagement.Inputs.PivotPropertiesArgs
            {
                Name = "ServiceName",
                Type = "Dimension",
            },
            new AzureNative.CostManagement.Inputs.PivotPropertiesArgs
            {
                Name = "MeterCategory",
                Type = "Dimension",
            },
            new AzureNative.CostManagement.Inputs.PivotPropertiesArgs
            {
                Name = "swaggerTagKey",
                Type = "TagKey",
            },
        },
        Scope = "subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG",
        Timeframe = "MonthToDate",
        Type = "Usage",
        ViewName = "swaggerExample",
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
		_, err := costmanagement.NewViewByScope(ctx, "viewByScope", &costmanagement.ViewByScopeArgs{
			Accumulated: pulumi.String("true"),
			Chart:       pulumi.String("Table"),
			DataSet: costmanagement.ReportConfigDatasetResponse{
				Aggregation: costmanagement.ReportConfigAggregationMap{
					"totalCost": &costmanagement.ReportConfigAggregationArgs{
						Function: pulumi.String("Sum"),
						Name:     pulumi.String("PreTaxCost"),
					},
				},
				Granularity: pulumi.String("Daily"),
				Grouping:    costmanagement.ReportConfigGroupingArray{},
				Sorting: costmanagement.ReportConfigSortingArray{
					&costmanagement.ReportConfigSortingArgs{
						Direction: pulumi.String("Ascending"),
						Name:      pulumi.String("UsageDate"),
					},
				},
			},
			DisplayName: pulumi.String("swagger Example"),
			ETag:        pulumi.String("\"1d4ff9fe66f1d10\""),
			Kpis: []costmanagement.KpiPropertiesArgs{
				{
					Enabled: pulumi.Bool(true),
					Type:    pulumi.String("Forecast"),
				},
				{
					Enabled: pulumi.Bool(true),
					Id:      pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Consumption/budgets/swaggerDemo"),
					Type:    pulumi.String("Budget"),
				},
			},
			Metric: pulumi.String("ActualCost"),
			Pivots: []costmanagement.PivotPropertiesArgs{
				{
					Name: pulumi.String("ServiceName"),
					Type: pulumi.String("Dimension"),
				},
				{
					Name: pulumi.String("MeterCategory"),
					Type: pulumi.String("Dimension"),
				},
				{
					Name: pulumi.String("swaggerTagKey"),
					Type: pulumi.String("TagKey"),
				},
			},
			Scope:     pulumi.String("subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG"),
			Timeframe: pulumi.String("MonthToDate"),
			Type:      pulumi.String("Usage"),
			ViewName:  pulumi.String("swaggerExample"),
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
import com.pulumi.azurenative.costmanagement.ViewByScope;
import com.pulumi.azurenative.costmanagement.ViewByScopeArgs;
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
        var viewByScope = new ViewByScope("viewByScope", ViewByScopeArgs.builder()        
            .accumulated("true")
            .chart("Table")
            .dataSet(Map.ofEntries(
                Map.entry("aggregation", Map.of("totalCost", Map.ofEntries(
                    Map.entry("function", "Sum"),
                    Map.entry("name", "PreTaxCost")
                ))),
                Map.entry("granularity", "Daily"),
                Map.entry("grouping", ),
                Map.entry("sorting", Map.ofEntries(
                    Map.entry("direction", "Ascending"),
                    Map.entry("name", "UsageDate")
                ))
            ))
            .displayName("swagger Example")
            .eTag("\"1d4ff9fe66f1d10\"")
            .kpis(            
                Map.ofEntries(
                    Map.entry("enabled", true),
                    Map.entry("type", "Forecast")
                ),
                Map.ofEntries(
                    Map.entry("enabled", true),
                    Map.entry("id", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Consumption/budgets/swaggerDemo"),
                    Map.entry("type", "Budget")
                ))
            .metric("ActualCost")
            .pivots(            
                Map.ofEntries(
                    Map.entry("name", "ServiceName"),
                    Map.entry("type", "Dimension")
                ),
                Map.ofEntries(
                    Map.entry("name", "MeterCategory"),
                    Map.entry("type", "Dimension")
                ),
                Map.ofEntries(
                    Map.entry("name", "swaggerTagKey"),
                    Map.entry("type", "TagKey")
                ))
            .scope("subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG")
            .timeframe("MonthToDate")
            .type("Usage")
            .viewName("swaggerExample")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const viewByScope = new azure_native.costmanagement.ViewByScope("viewByScope", {
    accumulated: "true",
    chart: "Table",
    dataSet: {
        aggregation: {
            totalCost: {
                "function": "Sum",
                name: "PreTaxCost",
            },
        },
        granularity: "Daily",
        grouping: [],
        sorting: [{
            direction: "Ascending",
            name: "UsageDate",
        }],
    },
    displayName: "swagger Example",
    eTag: "\"1d4ff9fe66f1d10\"",
    kpis: [
        {
            enabled: true,
            type: "Forecast",
        },
        {
            enabled: true,
            id: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Consumption/budgets/swaggerDemo",
            type: "Budget",
        },
    ],
    metric: "ActualCost",
    pivots: [
        {
            name: "ServiceName",
            type: "Dimension",
        },
        {
            name: "MeterCategory",
            type: "Dimension",
        },
        {
            name: "swaggerTagKey",
            type: "TagKey",
        },
    ],
    scope: "subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG",
    timeframe: "MonthToDate",
    type: "Usage",
    viewName: "swaggerExample",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

view_by_scope = azure_native.costmanagement.ViewByScope("viewByScope",
    accumulated="true",
    chart="Table",
    data_set=azure_native.costmanagement.ReportConfigDatasetResponseArgs(
        aggregation={
            "totalCost": azure_native.costmanagement.ReportConfigAggregationArgs(
                function="Sum",
                name="PreTaxCost",
            ),
        },
        granularity="Daily",
        grouping=[],
        sorting=[azure_native.costmanagement.ReportConfigSortingArgs(
            direction="Ascending",
            name="UsageDate",
        )],
    ),
    display_name="swagger Example",
    e_tag="\"1d4ff9fe66f1d10\"",
    kpis=[
        azure_native.costmanagement.KpiPropertiesArgs(
            enabled=True,
            type="Forecast",
        ),
        azure_native.costmanagement.KpiPropertiesArgs(
            enabled=True,
            id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Consumption/budgets/swaggerDemo",
            type="Budget",
        ),
    ],
    metric="ActualCost",
    pivots=[
        azure_native.costmanagement.PivotPropertiesArgs(
            name="ServiceName",
            type="Dimension",
        ),
        azure_native.costmanagement.PivotPropertiesArgs(
            name="MeterCategory",
            type="Dimension",
        ),
        azure_native.costmanagement.PivotPropertiesArgs(
            name="swaggerTagKey",
            type="TagKey",
        ),
    ],
    scope="subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG",
    timeframe="MonthToDate",
    type="Usage",
    view_name="swaggerExample")

```

```yaml
resources:
  viewByScope:
    type: azure-native:costmanagement:ViewByScope
    properties:
      accumulated: 'true'
      chart: Table
      dataSet:
        aggregation:
          totalCost:
            function: Sum
            name: PreTaxCost
        granularity: Daily
        grouping: []
        sorting:
          - direction: Ascending
            name: UsageDate
      displayName: swagger Example
      eTag: '"1d4ff9fe66f1d10"'
      kpis:
        - enabled: true
          type: Forecast
        - enabled: true
          id: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.Consumption/budgets/swaggerDemo
          type: Budget
      metric: ActualCost
      pivots:
        - name: ServiceName
          type: Dimension
        - name: MeterCategory
          type: Dimension
        - name: swaggerTagKey
          type: TagKey
      scope: subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG
      timeframe: MonthToDate
      type: Usage
      viewName: swaggerExample

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:costmanagement:ViewByScope swaggerExample /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MYDEVTESTRG/providers/Microsoft.CostManagement/views/swaggerExample 
```
