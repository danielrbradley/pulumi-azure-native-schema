Lab details.
API Version: 2021-12-01-preview.
Previous API Version: 2021-12-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateLab
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var lab = new AzureNative.Education.Lab("lab", new()
    {
        BillingAccountName = "{billingAccountName}",
        BillingProfileName = "{billingProfileName}",
        BudgetPerStudent = new AzureNative.Education.Inputs.AmountArgs
        {
            Currency = "USD",
            Value = 100,
        },
        Description = "example lab description",
        DisplayName = "example lab",
        ExpirationDate = "2021-12-09T22:11:29.422Z",
        InvoiceSectionName = "{invoiceSectionName}",
    });

});


```

```go
package main

import (
	education "github.com/pulumi/pulumi-azure-native-sdk/education"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := education.NewLab(ctx, "lab", &education.LabArgs{
			BillingAccountName: pulumi.String("{billingAccountName}"),
			BillingProfileName: pulumi.String("{billingProfileName}"),
			BudgetPerStudent: &education.AmountArgs{
				Currency: pulumi.String("USD"),
				Value:    pulumi.Float64(100),
			},
			Description:        pulumi.String("example lab description"),
			DisplayName:        pulumi.String("example lab"),
			ExpirationDate:     pulumi.String("2021-12-09T22:11:29.422Z"),
			InvoiceSectionName: pulumi.String("{invoiceSectionName}"),
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
import com.pulumi.azurenative.education.Lab;
import com.pulumi.azurenative.education.LabArgs;
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
        var lab = new Lab("lab", LabArgs.builder()        
            .billingAccountName("{billingAccountName}")
            .billingProfileName("{billingProfileName}")
            .budgetPerStudent(Map.ofEntries(
                Map.entry("currency", "USD"),
                Map.entry("value", 100)
            ))
            .description("example lab description")
            .displayName("example lab")
            .expirationDate("2021-12-09T22:11:29.422Z")
            .invoiceSectionName("{invoiceSectionName}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const lab = new azure_native.education.Lab("lab", {
    billingAccountName: "{billingAccountName}",
    billingProfileName: "{billingProfileName}",
    budgetPerStudent: {
        currency: "USD",
        value: 100,
    },
    description: "example lab description",
    displayName: "example lab",
    expirationDate: "2021-12-09T22:11:29.422Z",
    invoiceSectionName: "{invoiceSectionName}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

lab = azure_native.education.Lab("lab",
    billing_account_name="{billingAccountName}",
    billing_profile_name="{billingProfileName}",
    budget_per_student=azure_native.education.AmountArgs(
        currency="USD",
        value=100,
    ),
    description="example lab description",
    display_name="example lab",
    expiration_date="2021-12-09T22:11:29.422Z",
    invoice_section_name="{invoiceSectionName}")

```

```yaml
resources:
  lab:
    type: azure-native:education:Lab
    properties:
      billingAccountName: '{billingAccountName}'
      billingProfileName: '{billingProfileName}'
      budgetPerStudent:
        currency: USD
        value: 100
      description: example lab description
      displayName: example lab
      expirationDate: 2021-12-09T22:11:29.422Z
      invoiceSectionName: '{invoiceSectionName}'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:education:Lab default /providers/Microsoft.Billing/billingAccounts/{billingAccountName}/billingProfiles/{billingProfileName}/invoiceSections/{invoiceSectionName}/providers/Microsoft.Education/labs/default 
```
