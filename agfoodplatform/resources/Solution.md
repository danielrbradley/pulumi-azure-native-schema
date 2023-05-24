Solution resource.
API Version: 2021-09-01-preview.

{{% examples %}}
## Example Usage
{{% example %}}
### Solutions_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var solution = new AzureNative.AgFoodPlatform.Solution("solution", new()
    {
        FarmBeatsResourceName = "examples-farmbeatsResourceName",
        Properties = new AzureNative.AgFoodPlatform.Inputs.SolutionPropertiesArgs
        {
            MarketplacePublisherId = "publisherId",
            OfferId = "offerId",
            PlanId = "planId",
            SaasSubscriptionId = "123",
            SaasSubscriptionName = "name",
            TermId = "termId",
        },
        ResourceGroupName = "examples-rg",
        SolutionId = "abc.partner",
    });

});


```

```go
package main

import (
	agfoodplatform "github.com/pulumi/pulumi-azure-native-sdk/agfoodplatform"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := agfoodplatform.NewSolution(ctx, "solution", &agfoodplatform.SolutionArgs{
			FarmBeatsResourceName: pulumi.String("examples-farmbeatsResourceName"),
			Properties: &agfoodplatform.SolutionPropertiesArgs{
				MarketplacePublisherId: pulumi.String("publisherId"),
				OfferId:                pulumi.String("offerId"),
				PlanId:                 pulumi.String("planId"),
				SaasSubscriptionId:     pulumi.String("123"),
				SaasSubscriptionName:   pulumi.String("name"),
				TermId:                 pulumi.String("termId"),
			},
			ResourceGroupName: pulumi.String("examples-rg"),
			SolutionId:        pulumi.String("abc.partner"),
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
import com.pulumi.azurenative.agfoodplatform.Solution;
import com.pulumi.azurenative.agfoodplatform.SolutionArgs;
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
        var solution = new Solution("solution", SolutionArgs.builder()        
            .farmBeatsResourceName("examples-farmbeatsResourceName")
            .properties(Map.ofEntries(
                Map.entry("marketplacePublisherId", "publisherId"),
                Map.entry("offerId", "offerId"),
                Map.entry("planId", "planId"),
                Map.entry("saasSubscriptionId", "123"),
                Map.entry("saasSubscriptionName", "name"),
                Map.entry("termId", "termId")
            ))
            .resourceGroupName("examples-rg")
            .solutionId("abc.partner")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const solution = new azure_native.agfoodplatform.Solution("solution", {
    farmBeatsResourceName: "examples-farmbeatsResourceName",
    properties: {
        marketplacePublisherId: "publisherId",
        offerId: "offerId",
        planId: "planId",
        saasSubscriptionId: "123",
        saasSubscriptionName: "name",
        termId: "termId",
    },
    resourceGroupName: "examples-rg",
    solutionId: "abc.partner",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

solution = azure_native.agfoodplatform.Solution("solution",
    farm_beats_resource_name="examples-farmbeatsResourceName",
    properties=azure_native.agfoodplatform.SolutionPropertiesArgs(
        marketplace_publisher_id="publisherId",
        offer_id="offerId",
        plan_id="planId",
        saas_subscription_id="123",
        saas_subscription_name="name",
        term_id="termId",
    ),
    resource_group_name="examples-rg",
    solution_id="abc.partner")

```

```yaml
resources:
  solution:
    type: azure-native:agfoodplatform:Solution
    properties:
      farmBeatsResourceName: examples-farmbeatsResourceName
      properties:
        marketplacePublisherId: publisherId
        offerId: offerId
        planId: planId
        saasSubscriptionId: '123'
        saasSubscriptionName: name
        termId: termId
      resourceGroupName: examples-rg
      solutionId: abc.partner

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:agfoodplatform:Solution string /subscriptions/ff57165d-e71f-4a0e-8e9b-3cd461dc0f38/resourceGroups/bugbash-instances-westus2/providers/Microsoft.AgFoodPlatform/farmBeats/bb-df-wus2-1/solutions/string 
```
