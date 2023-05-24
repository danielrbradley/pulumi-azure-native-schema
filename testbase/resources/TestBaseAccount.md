The Test Base Account resource.
API Version: 2022-04-01-preview.
Previous API Version: 2022-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### TestBaseAccountCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var testBaseAccount = new AzureNative.TestBase.TestBaseAccount("testBaseAccount", new()
    {
        Location = "westus",
        ResourceGroupName = "contoso-rg1",
        Sku = new AzureNative.TestBase.Inputs.TestBaseAccountSKUArgs
        {
            Name = "S0",
            Tier = "Standard",
        },
        TestBaseAccountName = "contoso-testBaseAccount1",
    });

});


```

```go
package main

import (
	testbase "github.com/pulumi/pulumi-azure-native-sdk/testbase"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := testbase.NewTestBaseAccount(ctx, "testBaseAccount", &testbase.TestBaseAccountArgs{
			Location:          pulumi.String("westus"),
			ResourceGroupName: pulumi.String("contoso-rg1"),
			Sku: &testbase.TestBaseAccountSKUArgs{
				Name: pulumi.String("S0"),
				Tier: pulumi.String("Standard"),
			},
			TestBaseAccountName: pulumi.String("contoso-testBaseAccount1"),
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
import com.pulumi.azurenative.testbase.TestBaseAccount;
import com.pulumi.azurenative.testbase.TestBaseAccountArgs;
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
        var testBaseAccount = new TestBaseAccount("testBaseAccount", TestBaseAccountArgs.builder()        
            .location("westus")
            .resourceGroupName("contoso-rg1")
            .sku(Map.ofEntries(
                Map.entry("name", "S0"),
                Map.entry("tier", "Standard")
            ))
            .testBaseAccountName("contoso-testBaseAccount1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const testBaseAccount = new azure_native.testbase.TestBaseAccount("testBaseAccount", {
    location: "westus",
    resourceGroupName: "contoso-rg1",
    sku: {
        name: "S0",
        tier: "Standard",
    },
    testBaseAccountName: "contoso-testBaseAccount1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

test_base_account = azure_native.testbase.TestBaseAccount("testBaseAccount",
    location="westus",
    resource_group_name="contoso-rg1",
    sku=azure_native.testbase.TestBaseAccountSKUArgs(
        name="S0",
        tier="Standard",
    ),
    test_base_account_name="contoso-testBaseAccount1")

```

```yaml
resources:
  testBaseAccount:
    type: azure-native:testbase:TestBaseAccount
    properties:
      location: westus
      resourceGroupName: contoso-rg1
      sku:
        name: S0
        tier: Standard
      testBaseAccountName: contoso-testBaseAccount1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:testbase:TestBaseAccount contoso-testBaseAccount1 /subscriptions/subscription-id/resourceGroups/contoso-rg1/providers/Microsoft.TestBase/testBaseAccounts/contoso-testBaseAccount1 
```
