Student details.
API Version: 2021-12-01-preview.
Previous API Version: 2021-12-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Student
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var student = new AzureNative.Education.Student("student", new()
    {
        BillingAccountName = "{billingAccountName}",
        BillingProfileName = "{billingProfileName}",
        Budget = new AzureNative.Education.Inputs.AmountArgs
        {
            Currency = "USD",
            Value = 100,
        },
        Email = "test@contoso.com",
        ExpirationDate = "2021-11-09T22:13:21.795Z",
        FirstName = "test",
        InvoiceSectionName = "{invoiceSectionName}",
        LastName = "user",
        Role = "Student",
        StudentAlias = "{studentAlias}",
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
		_, err := education.NewStudent(ctx, "student", &education.StudentArgs{
			BillingAccountName: pulumi.String("{billingAccountName}"),
			BillingProfileName: pulumi.String("{billingProfileName}"),
			Budget: &education.AmountArgs{
				Currency: pulumi.String("USD"),
				Value:    pulumi.Float64(100),
			},
			Email:              pulumi.String("test@contoso.com"),
			ExpirationDate:     pulumi.String("2021-11-09T22:13:21.795Z"),
			FirstName:          pulumi.String("test"),
			InvoiceSectionName: pulumi.String("{invoiceSectionName}"),
			LastName:           pulumi.String("user"),
			Role:               pulumi.String("Student"),
			StudentAlias:       pulumi.String("{studentAlias}"),
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
import com.pulumi.azurenative.education.Student;
import com.pulumi.azurenative.education.StudentArgs;
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
        var student = new Student("student", StudentArgs.builder()        
            .billingAccountName("{billingAccountName}")
            .billingProfileName("{billingProfileName}")
            .budget(Map.ofEntries(
                Map.entry("currency", "USD"),
                Map.entry("value", 100)
            ))
            .email("test@contoso.com")
            .expirationDate("2021-11-09T22:13:21.795Z")
            .firstName("test")
            .invoiceSectionName("{invoiceSectionName}")
            .lastName("user")
            .role("Student")
            .studentAlias("{studentAlias}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const student = new azure_native.education.Student("student", {
    billingAccountName: "{billingAccountName}",
    billingProfileName: "{billingProfileName}",
    budget: {
        currency: "USD",
        value: 100,
    },
    email: "test@contoso.com",
    expirationDate: "2021-11-09T22:13:21.795Z",
    firstName: "test",
    invoiceSectionName: "{invoiceSectionName}",
    lastName: "user",
    role: "Student",
    studentAlias: "{studentAlias}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

student = azure_native.education.Student("student",
    billing_account_name="{billingAccountName}",
    billing_profile_name="{billingProfileName}",
    budget=azure_native.education.AmountArgs(
        currency="USD",
        value=100,
    ),
    email="test@contoso.com",
    expiration_date="2021-11-09T22:13:21.795Z",
    first_name="test",
    invoice_section_name="{invoiceSectionName}",
    last_name="user",
    role="Student",
    student_alias="{studentAlias}")

```

```yaml
resources:
  student:
    type: azure-native:education:Student
    properties:
      billingAccountName: '{billingAccountName}'
      billingProfileName: '{billingProfileName}'
      budget:
        currency: USD
        value: 100
      email: test@contoso.com
      expirationDate: 2021-11-09T22:13:21.795Z
      firstName: test
      invoiceSectionName: '{invoiceSectionName}'
      lastName: user
      role: Student
      studentAlias: '{studentAlias}'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:education:Student {studentAlias} /providers/Microsoft.Billing/billingAccounts/{billingAccountName}/billingProfiles/{billingProfileName}/invoiceSections/{invoiceSectionName}/providers/Microsoft.Education/labs/default/students/{studentAlias} 
```
