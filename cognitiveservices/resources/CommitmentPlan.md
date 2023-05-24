Cognitive Services account commitment plan.
API Version: 2022-12-01.
Previous API Version: 2021-10-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Commitment Plan
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var commitmentPlan = new AzureNative.CognitiveServices.CommitmentPlan("commitmentPlan", new()
    {
        CommitmentPlanName = "commitmentPlanName",
        Kind = "SpeechServices",
        Location = "West US",
        Properties = new AzureNative.CognitiveServices.Inputs.CommitmentPlanPropertiesArgs
        {
            AutoRenew = true,
            Current = new AzureNative.CognitiveServices.Inputs.CommitmentPeriodArgs
            {
                Tier = "T1",
            },
            HostingModel = "Web",
            PlanType = "STT",
        },
        ResourceGroupName = "resourceGroupName",
        Sku = new AzureNative.CognitiveServices.Inputs.SkuArgs
        {
            Name = "S0",
        },
    });

});


```

```go
package main

import (
	cognitiveservices "github.com/pulumi/pulumi-azure-native-sdk/cognitiveservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := cognitiveservices.NewCommitmentPlan(ctx, "commitmentPlan", &cognitiveservices.CommitmentPlanArgs{
			CommitmentPlanName: pulumi.String("commitmentPlanName"),
			Kind:               pulumi.String("SpeechServices"),
			Location:           pulumi.String("West US"),
			Properties: cognitiveservices.CommitmentPlanPropertiesResponse{
				AutoRenew: pulumi.Bool(true),
				Current: &cognitiveservices.CommitmentPeriodArgs{
					Tier: pulumi.String("T1"),
				},
				HostingModel: pulumi.String("Web"),
				PlanType:     pulumi.String("STT"),
			},
			ResourceGroupName: pulumi.String("resourceGroupName"),
			Sku: &cognitiveservices.SkuArgs{
				Name: pulumi.String("S0"),
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
import com.pulumi.azurenative.cognitiveservices.CommitmentPlan;
import com.pulumi.azurenative.cognitiveservices.CommitmentPlanArgs;
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
        var commitmentPlan = new CommitmentPlan("commitmentPlan", CommitmentPlanArgs.builder()        
            .commitmentPlanName("commitmentPlanName")
            .kind("SpeechServices")
            .location("West US")
            .properties(Map.ofEntries(
                Map.entry("autoRenew", true),
                Map.entry("current", Map.of("tier", "T1")),
                Map.entry("hostingModel", "Web"),
                Map.entry("planType", "STT")
            ))
            .resourceGroupName("resourceGroupName")
            .sku(Map.of("name", "S0"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const commitmentPlan = new azure_native.cognitiveservices.CommitmentPlan("commitmentPlan", {
    commitmentPlanName: "commitmentPlanName",
    kind: "SpeechServices",
    location: "West US",
    properties: {
        autoRenew: true,
        current: {
            tier: "T1",
        },
        hostingModel: "Web",
        planType: "STT",
    },
    resourceGroupName: "resourceGroupName",
    sku: {
        name: "S0",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

commitment_plan = azure_native.cognitiveservices.CommitmentPlan("commitmentPlan",
    commitment_plan_name="commitmentPlanName",
    kind="SpeechServices",
    location="West US",
    properties=azure_native.cognitiveservices.CommitmentPlanPropertiesResponseArgs(
        auto_renew=True,
        current=azure_native.cognitiveservices.CommitmentPeriodArgs(
            tier="T1",
        ),
        hosting_model="Web",
        plan_type="STT",
    ),
    resource_group_name="resourceGroupName",
    sku=azure_native.cognitiveservices.SkuArgs(
        name="S0",
    ))

```

```yaml
resources:
  commitmentPlan:
    type: azure-native:cognitiveservices:CommitmentPlan
    properties:
      commitmentPlanName: commitmentPlanName
      kind: SpeechServices
      location: West US
      properties:
        autoRenew: true
        current:
          tier: T1
        hostingModel: Web
        planType: STT
      resourceGroupName: resourceGroupName
      sku:
        name: S0

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:cognitiveservices:CommitmentPlan commitmentPlanName /subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/resourceGroups/resourceGroupName/providers/Microsoft.CognitiveServices/commitmentPlans/commitmentPlanName 
```
