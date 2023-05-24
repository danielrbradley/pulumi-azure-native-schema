The prediction resource format.
API Version: 2017-04-26.
Previous API Version: 2017-04-26. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Predictions_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var prediction = new AzureNative.CustomerInsights.Prediction("prediction", new()
    {
        AutoAnalyze = true,
        Description = 
        {
            { "en-us", "sdktest" },
        },
        DisplayName = 
        {
            { "en-us", "sdktest" },
        },
        Grades = new[] {},
        HubName = "sdkTestHub",
        InvolvedInteractionTypes = new[] {},
        InvolvedKpiTypes = new[] {},
        InvolvedRelationships = new[] {},
        Mappings = new AzureNative.CustomerInsights.Inputs.PredictionMappingsArgs
        {
            Grade = "sdktest_Grade",
            Reason = "sdktest_Reason",
            Score = "sdktest_Score",
        },
        NegativeOutcomeExpression = "Customers.FirstName = 'Mike'",
        PositiveOutcomeExpression = "Customers.FirstName = 'David'",
        PredictionName = "sdktest",
        PrimaryProfileType = "Customers",
        ResourceGroupName = "TestHubRG",
        ScopeExpression = "*",
        ScoreLabel = "score label",
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
		_, err := customerinsights.NewPrediction(ctx, "prediction", &customerinsights.PredictionArgs{
			AutoAnalyze: pulumi.Bool(true),
			Description: pulumi.StringMap{
				"en-us": pulumi.String("sdktest"),
			},
			DisplayName: pulumi.StringMap{
				"en-us": pulumi.String("sdktest"),
			},
			Grades:                   customerinsights.PredictionGradesArray{},
			HubName:                  pulumi.String("sdkTestHub"),
			InvolvedInteractionTypes: pulumi.StringArray{},
			InvolvedKpiTypes:         pulumi.StringArray{},
			InvolvedRelationships:    pulumi.StringArray{},
			Mappings: &customerinsights.PredictionMappingsArgs{
				Grade:  pulumi.String("sdktest_Grade"),
				Reason: pulumi.String("sdktest_Reason"),
				Score:  pulumi.String("sdktest_Score"),
			},
			NegativeOutcomeExpression: pulumi.String("Customers.FirstName = 'Mike'"),
			PositiveOutcomeExpression: pulumi.String("Customers.FirstName = 'David'"),
			PredictionName:            pulumi.String("sdktest"),
			PrimaryProfileType:        pulumi.String("Customers"),
			ResourceGroupName:         pulumi.String("TestHubRG"),
			ScopeExpression:           pulumi.String("*"),
			ScoreLabel:                pulumi.String("score label"),
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
import com.pulumi.azurenative.customerinsights.Prediction;
import com.pulumi.azurenative.customerinsights.PredictionArgs;
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
        var prediction = new Prediction("prediction", PredictionArgs.builder()        
            .autoAnalyze(true)
            .description(Map.of("en-us", "sdktest"))
            .displayName(Map.of("en-us", "sdktest"))
            .grades()
            .hubName("sdkTestHub")
            .involvedInteractionTypes()
            .involvedKpiTypes()
            .involvedRelationships()
            .mappings(Map.ofEntries(
                Map.entry("grade", "sdktest_Grade"),
                Map.entry("reason", "sdktest_Reason"),
                Map.entry("score", "sdktest_Score")
            ))
            .negativeOutcomeExpression("Customers.FirstName = 'Mike'")
            .positiveOutcomeExpression("Customers.FirstName = 'David'")
            .predictionName("sdktest")
            .primaryProfileType("Customers")
            .resourceGroupName("TestHubRG")
            .scopeExpression("*")
            .scoreLabel("score label")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const prediction = new azure_native.customerinsights.Prediction("prediction", {
    autoAnalyze: true,
    description: {
        "en-us": "sdktest",
    },
    displayName: {
        "en-us": "sdktest",
    },
    grades: [],
    hubName: "sdkTestHub",
    involvedInteractionTypes: [],
    involvedKpiTypes: [],
    involvedRelationships: [],
    mappings: {
        grade: "sdktest_Grade",
        reason: "sdktest_Reason",
        score: "sdktest_Score",
    },
    negativeOutcomeExpression: "Customers.FirstName = 'Mike'",
    positiveOutcomeExpression: "Customers.FirstName = 'David'",
    predictionName: "sdktest",
    primaryProfileType: "Customers",
    resourceGroupName: "TestHubRG",
    scopeExpression: "*",
    scoreLabel: "score label",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

prediction = azure_native.customerinsights.Prediction("prediction",
    auto_analyze=True,
    description={
        "en-us": "sdktest",
    },
    display_name={
        "en-us": "sdktest",
    },
    grades=[],
    hub_name="sdkTestHub",
    involved_interaction_types=[],
    involved_kpi_types=[],
    involved_relationships=[],
    mappings=azure_native.customerinsights.PredictionMappingsArgs(
        grade="sdktest_Grade",
        reason="sdktest_Reason",
        score="sdktest_Score",
    ),
    negative_outcome_expression="Customers.FirstName = 'Mike'",
    positive_outcome_expression="Customers.FirstName = 'David'",
    prediction_name="sdktest",
    primary_profile_type="Customers",
    resource_group_name="TestHubRG",
    scope_expression="*",
    score_label="score label")

```

```yaml
resources:
  prediction:
    type: azure-native:customerinsights:Prediction
    properties:
      autoAnalyze: true
      description:
        en-us: sdktest
      displayName:
        en-us: sdktest
      grades: []
      hubName: sdkTestHub
      involvedInteractionTypes: []
      involvedKpiTypes: []
      involvedRelationships: []
      mappings:
        grade: sdktest_Grade
        reason: sdktest_Reason
        score: sdktest_Score
      negativeOutcomeExpression: Customers.FirstName = 'Mike'
      positiveOutcomeExpression: Customers.FirstName = 'David'
      predictionName: sdktest
      primaryProfileType: Customers
      resourceGroupName: TestHubRG
      scopeExpression: '*'
      scoreLabel: score label

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:customerinsights:Prediction sdkTestHub/sdktest /subscriptions/c909e979-ef71-4def-a970-bc7c154db8c5/resourceGroups/TestHubRG/providers/Microsoft.CustomerInsights/hubs/azSdkTestHub/predictions/sdktest 
```
