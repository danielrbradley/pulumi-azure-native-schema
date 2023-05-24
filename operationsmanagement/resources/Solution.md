The container for solution.
API Version: 2015-11-01-preview.
Previous API Version: 2015-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### SolutionCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var solution = new AzureNative.OperationsManagement.Solution("solution", new()
    {
        Location = "East US",
        Plan = new AzureNative.OperationsManagement.Inputs.SolutionPlanArgs
        {
            Name = "name1",
            Product = "product1",
            PromotionCode = "promocode1",
            Publisher = "publisher1",
        },
        Properties = new AzureNative.OperationsManagement.Inputs.SolutionPropertiesArgs
        {
            ContainedResources = new[]
            {
                "/subscriptions/sub2/resourceGroups/rg2/providers/provider1/resources/resource1",
                "/subscriptions/sub2/resourceGroups/rg2/providers/provider2/resources/resource2",
            },
            ReferencedResources = new[]
            {
                "/subscriptions/sub2/resourceGroups/rg2/providers/provider1/resources/resource2",
                "/subscriptions/sub2/resourceGroups/rg2/providers/provider2/resources/resource3",
            },
            WorkspaceResourceId = "/subscriptions/sub2/resourceGroups/rg2/providers/Microsoft.OperationalInsights/workspaces/ws1",
        },
        ResourceGroupName = "rg1",
        SolutionName = "solution1",
    });

});


```

```go
package main

import (
	operationsmanagement "github.com/pulumi/pulumi-azure-native-sdk/operationsmanagement"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := operationsmanagement.NewSolution(ctx, "solution", &operationsmanagement.SolutionArgs{
			Location: pulumi.String("East US"),
			Plan: &operationsmanagement.SolutionPlanArgs{
				Name:          pulumi.String("name1"),
				Product:       pulumi.String("product1"),
				PromotionCode: pulumi.String("promocode1"),
				Publisher:     pulumi.String("publisher1"),
			},
			Properties: &operationsmanagement.SolutionPropertiesArgs{
				ContainedResources: pulumi.StringArray{
					pulumi.String("/subscriptions/sub2/resourceGroups/rg2/providers/provider1/resources/resource1"),
					pulumi.String("/subscriptions/sub2/resourceGroups/rg2/providers/provider2/resources/resource2"),
				},
				ReferencedResources: pulumi.StringArray{
					pulumi.String("/subscriptions/sub2/resourceGroups/rg2/providers/provider1/resources/resource2"),
					pulumi.String("/subscriptions/sub2/resourceGroups/rg2/providers/provider2/resources/resource3"),
				},
				WorkspaceResourceId: pulumi.String("/subscriptions/sub2/resourceGroups/rg2/providers/Microsoft.OperationalInsights/workspaces/ws1"),
			},
			ResourceGroupName: pulumi.String("rg1"),
			SolutionName:      pulumi.String("solution1"),
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
import com.pulumi.azurenative.operationsmanagement.Solution;
import com.pulumi.azurenative.operationsmanagement.SolutionArgs;
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
            .location("East US")
            .plan(Map.ofEntries(
                Map.entry("name", "name1"),
                Map.entry("product", "product1"),
                Map.entry("promotionCode", "promocode1"),
                Map.entry("publisher", "publisher1")
            ))
            .properties(Map.ofEntries(
                Map.entry("containedResources",                 
                    "/subscriptions/sub2/resourceGroups/rg2/providers/provider1/resources/resource1",
                    "/subscriptions/sub2/resourceGroups/rg2/providers/provider2/resources/resource2"),
                Map.entry("referencedResources",                 
                    "/subscriptions/sub2/resourceGroups/rg2/providers/provider1/resources/resource2",
                    "/subscriptions/sub2/resourceGroups/rg2/providers/provider2/resources/resource3"),
                Map.entry("workspaceResourceId", "/subscriptions/sub2/resourceGroups/rg2/providers/Microsoft.OperationalInsights/workspaces/ws1")
            ))
            .resourceGroupName("rg1")
            .solutionName("solution1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const solution = new azure_native.operationsmanagement.Solution("solution", {
    location: "East US",
    plan: {
        name: "name1",
        product: "product1",
        promotionCode: "promocode1",
        publisher: "publisher1",
    },
    properties: {
        containedResources: [
            "/subscriptions/sub2/resourceGroups/rg2/providers/provider1/resources/resource1",
            "/subscriptions/sub2/resourceGroups/rg2/providers/provider2/resources/resource2",
        ],
        referencedResources: [
            "/subscriptions/sub2/resourceGroups/rg2/providers/provider1/resources/resource2",
            "/subscriptions/sub2/resourceGroups/rg2/providers/provider2/resources/resource3",
        ],
        workspaceResourceId: "/subscriptions/sub2/resourceGroups/rg2/providers/Microsoft.OperationalInsights/workspaces/ws1",
    },
    resourceGroupName: "rg1",
    solutionName: "solution1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

solution = azure_native.operationsmanagement.Solution("solution",
    location="East US",
    plan=azure_native.operationsmanagement.SolutionPlanArgs(
        name="name1",
        product="product1",
        promotion_code="promocode1",
        publisher="publisher1",
    ),
    properties=azure_native.operationsmanagement.SolutionPropertiesArgs(
        contained_resources=[
            "/subscriptions/sub2/resourceGroups/rg2/providers/provider1/resources/resource1",
            "/subscriptions/sub2/resourceGroups/rg2/providers/provider2/resources/resource2",
        ],
        referenced_resources=[
            "/subscriptions/sub2/resourceGroups/rg2/providers/provider1/resources/resource2",
            "/subscriptions/sub2/resourceGroups/rg2/providers/provider2/resources/resource3",
        ],
        workspace_resource_id="/subscriptions/sub2/resourceGroups/rg2/providers/Microsoft.OperationalInsights/workspaces/ws1",
    ),
    resource_group_name="rg1",
    solution_name="solution1")

```

```yaml
resources:
  solution:
    type: azure-native:operationsmanagement:Solution
    properties:
      location: East US
      plan:
        name: name1
        product: product1
        promotionCode: promocode1
        publisher: publisher1
      properties:
        containedResources:
          - /subscriptions/sub2/resourceGroups/rg2/providers/provider1/resources/resource1
          - /subscriptions/sub2/resourceGroups/rg2/providers/provider2/resources/resource2
        referencedResources:
          - /subscriptions/sub2/resourceGroups/rg2/providers/provider1/resources/resource2
          - /subscriptions/sub2/resourceGroups/rg2/providers/provider2/resources/resource3
        workspaceResourceId: /subscriptions/sub2/resourceGroups/rg2/providers/Microsoft.OperationalInsights/workspaces/ws1
      resourceGroupName: rg1
      solutionName: solution1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:operationsmanagement:Solution solution1 subscriptions/subid/resourcegroups/rg1/providers/Microsoft.OperationsManagement/solutions/solution1 
```
