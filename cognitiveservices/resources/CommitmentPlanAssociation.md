The commitment plan association.
API Version: 2022-12-01.

{{% examples %}}
## Example Usage
{{% example %}}
### PutCommitmentPlan
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var commitmentPlanAssociation = new AzureNative.CognitiveServices.CommitmentPlanAssociation("commitmentPlanAssociation", new()
    {
        AccountId = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.CognitiveServices/accounts/accountName",
        CommitmentPlanAssociationName = "commitmentPlanAssociationName",
        CommitmentPlanName = "commitmentPlanName",
        ResourceGroupName = "resourceGroupName",
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
		_, err := cognitiveservices.NewCommitmentPlanAssociation(ctx, "commitmentPlanAssociation", &cognitiveservices.CommitmentPlanAssociationArgs{
			AccountId:                     pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.CognitiveServices/accounts/accountName"),
			CommitmentPlanAssociationName: pulumi.String("commitmentPlanAssociationName"),
			CommitmentPlanName:            pulumi.String("commitmentPlanName"),
			ResourceGroupName:             pulumi.String("resourceGroupName"),
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
import com.pulumi.azurenative.cognitiveservices.CommitmentPlanAssociation;
import com.pulumi.azurenative.cognitiveservices.CommitmentPlanAssociationArgs;
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
        var commitmentPlanAssociation = new CommitmentPlanAssociation("commitmentPlanAssociation", CommitmentPlanAssociationArgs.builder()        
            .accountId("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.CognitiveServices/accounts/accountName")
            .commitmentPlanAssociationName("commitmentPlanAssociationName")
            .commitmentPlanName("commitmentPlanName")
            .resourceGroupName("resourceGroupName")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const commitmentPlanAssociation = new azure_native.cognitiveservices.CommitmentPlanAssociation("commitmentPlanAssociation", {
    accountId: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.CognitiveServices/accounts/accountName",
    commitmentPlanAssociationName: "commitmentPlanAssociationName",
    commitmentPlanName: "commitmentPlanName",
    resourceGroupName: "resourceGroupName",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

commitment_plan_association = azure_native.cognitiveservices.CommitmentPlanAssociation("commitmentPlanAssociation",
    account_id="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.CognitiveServices/accounts/accountName",
    commitment_plan_association_name="commitmentPlanAssociationName",
    commitment_plan_name="commitmentPlanName",
    resource_group_name="resourceGroupName")

```

```yaml
resources:
  commitmentPlanAssociation:
    type: azure-native:cognitiveservices:CommitmentPlanAssociation
    properties:
      accountId: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.CognitiveServices/accounts/accountName
      commitmentPlanAssociationName: commitmentPlanAssociationName
      commitmentPlanName: commitmentPlanName
      resourceGroupName: resourceGroupName

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:cognitiveservices:CommitmentPlanAssociation commitmentPlanAssociationName /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.CognitiveServices/commitmentPlans/commitmentPlanName/accountAssociations/commitmentPlanAssociationName 
```
