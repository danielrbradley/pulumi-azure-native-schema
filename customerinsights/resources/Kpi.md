The KPI resource format.
API Version: 2017-04-26.
Previous API Version: 2017-04-26. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Kpi_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var kpi = new AzureNative.CustomerInsights.Kpi("kpi", new()
    {
        Aliases = new[]
        {
            new AzureNative.CustomerInsights.Inputs.KpiAliasArgs
            {
                AliasName = "alias",
                Expression = "Id+4",
            },
        },
        CalculationWindow = AzureNative.CustomerInsights.CalculationWindowTypes.Day,
        Description = 
        {
            { "en-us", "Kpi Description" },
        },
        DisplayName = 
        {
            { "en-us", "Kpi DisplayName" },
        },
        EntityType = AzureNative.CustomerInsights.EntityTypes.Profile,
        EntityTypeName = "testProfile2327128",
        Expression = "SavingAccountBalance",
        Function = AzureNative.CustomerInsights.KpiFunctions.Sum,
        GroupBy = new[]
        {
            "SavingAccountBalance",
        },
        HubName = "sdkTestHub",
        KpiName = "kpiTest45453647",
        ResourceGroupName = "TestHubRG",
        ThresHolds = new AzureNative.CustomerInsights.Inputs.KpiThresholdsArgs
        {
            IncreasingKpi = true,
            LowerLimit = 5,
            UpperLimit = 50,
        },
        Unit = "unit",
    });

});


```

```go
package main

import (
	customerinsights "github.com/pulumi/pulumi-azure-native-sdk/customerinsights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := customerinsights.NewKpi(ctx, "kpi", &customerinsights.KpiArgs{
			Aliases: []customerinsights.KpiAliasArgs{
				{
					AliasName:  pulumi.String("alias"),
					Expression: pulumi.String("Id+4"),
				},
			},
			CalculationWindow: customerinsights.CalculationWindowTypesDay,
			Description: pulumi.StringMap{
				"en-us": pulumi.String("Kpi Description"),
			},
			DisplayName: pulumi.StringMap{
				"en-us": pulumi.String("Kpi DisplayName"),
			},
			EntityType:     customerinsights.EntityTypesProfile,
			EntityTypeName: pulumi.String("testProfile2327128"),
			Expression:     pulumi.String("SavingAccountBalance"),
			Function:       customerinsights.KpiFunctionsSum,
			GroupBy: pulumi.StringArray{
				pulumi.String("SavingAccountBalance"),
			},
			HubName:           pulumi.String("sdkTestHub"),
			KpiName:           pulumi.String("kpiTest45453647"),
			ResourceGroupName: pulumi.String("TestHubRG"),
			ThresHolds: &customerinsights.KpiThresholdsArgs{
				IncreasingKpi: pulumi.Bool(true),
				LowerLimit:    pulumi.Float64(5),
				UpperLimit:    pulumi.Float64(50),
			},
			Unit: pulumi.String("unit"),
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
import com.pulumi.azurenative.customerinsights.Kpi;
import com.pulumi.azurenative.customerinsights.KpiArgs;
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
        var kpi = new Kpi("kpi", KpiArgs.builder()        
            .aliases(Map.ofEntries(
                Map.entry("aliasName", "alias"),
                Map.entry("expression", "Id+4")
            ))
            .calculationWindow("Day")
            .description(Map.of("en-us", "Kpi Description"))
            .displayName(Map.of("en-us", "Kpi DisplayName"))
            .entityType("Profile")
            .entityTypeName("testProfile2327128")
            .expression("SavingAccountBalance")
            .function("Sum")
            .groupBy("SavingAccountBalance")
            .hubName("sdkTestHub")
            .kpiName("kpiTest45453647")
            .resourceGroupName("TestHubRG")
            .thresHolds(Map.ofEntries(
                Map.entry("increasingKpi", true),
                Map.entry("lowerLimit", 5),
                Map.entry("upperLimit", 50)
            ))
            .unit("unit")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const kpi = new azure_native.customerinsights.Kpi("kpi", {
    aliases: [{
        aliasName: "alias",
        expression: "Id+4",
    }],
    calculationWindow: azure_native.customerinsights.CalculationWindowTypes.Day,
    description: {
        "en-us": "Kpi Description",
    },
    displayName: {
        "en-us": "Kpi DisplayName",
    },
    entityType: azure_native.customerinsights.EntityTypes.Profile,
    entityTypeName: "testProfile2327128",
    expression: "SavingAccountBalance",
    "function": azure_native.customerinsights.KpiFunctions.Sum,
    groupBy: ["SavingAccountBalance"],
    hubName: "sdkTestHub",
    kpiName: "kpiTest45453647",
    resourceGroupName: "TestHubRG",
    thresHolds: {
        increasingKpi: true,
        lowerLimit: 5,
        upperLimit: 50,
    },
    unit: "unit",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

kpi = azure_native.customerinsights.Kpi("kpi",
    aliases=[azure_native.customerinsights.KpiAliasArgs(
        alias_name="alias",
        expression="Id+4",
    )],
    calculation_window=azure_native.customerinsights.CalculationWindowTypes.DAY,
    description={
        "en-us": "Kpi Description",
    },
    display_name={
        "en-us": "Kpi DisplayName",
    },
    entity_type=azure_native.customerinsights.EntityTypes.PROFILE,
    entity_type_name="testProfile2327128",
    expression="SavingAccountBalance",
    function=azure_native.customerinsights.KpiFunctions.SUM,
    group_by=["SavingAccountBalance"],
    hub_name="sdkTestHub",
    kpi_name="kpiTest45453647",
    resource_group_name="TestHubRG",
    thres_holds=azure_native.customerinsights.KpiThresholdsArgs(
        increasing_kpi=True,
        lower_limit=5,
        upper_limit=50,
    ),
    unit="unit")

```

```yaml
resources:
  kpi:
    type: azure-native:customerinsights:Kpi
    properties:
      aliases:
        - aliasName: alias
          expression: Id+4
      calculationWindow: Day
      description:
        en-us: Kpi Description
      displayName:
        en-us: Kpi DisplayName
      entityType: Profile
      entityTypeName: testProfile2327128
      expression: SavingAccountBalance
      function: Sum
      groupBy:
        - SavingAccountBalance
      hubName: sdkTestHub
      kpiName: kpiTest45453647
      resourceGroupName: TestHubRG
      thresHolds:
        increasingKpi: true
        lowerLimit: 5
        upperLimit: 50
      unit: unit

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:customerinsights:Kpi sdkTestHub/kpiTest45453647 /subscriptions/c909e979-ef71-4def-a970-bc7c154db8c5/resourceGroups/TestHubRG/providers/Microsoft.CustomerInsights/hubs/sdkTestHub/kpi/kpiTest45453647 
```
