The integration account.
API Version: 2019-05-01.
Previous API Version: 2019-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update an integration account
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var integrationAccount = new AzureNative.Logic.IntegrationAccount("integrationAccount", new()
    {
        IntegrationAccountName = "testIntegrationAccount",
        Location = "westus",
        ResourceGroupName = "testResourceGroup",
        Sku = new AzureNative.Logic.Inputs.IntegrationAccountSkuArgs
        {
            Name = "Standard",
        },
    });

});


```

```go
package main

import (
	logic "github.com/pulumi/pulumi-azure-native-sdk/logic"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := logic.NewIntegrationAccount(ctx, "integrationAccount", &logic.IntegrationAccountArgs{
			IntegrationAccountName: pulumi.String("testIntegrationAccount"),
			Location:               pulumi.String("westus"),
			ResourceGroupName:      pulumi.String("testResourceGroup"),
			Sku: &logic.IntegrationAccountSkuArgs{
				Name: pulumi.String("Standard"),
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
import com.pulumi.azurenative.logic.IntegrationAccount;
import com.pulumi.azurenative.logic.IntegrationAccountArgs;
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
        var integrationAccount = new IntegrationAccount("integrationAccount", IntegrationAccountArgs.builder()        
            .integrationAccountName("testIntegrationAccount")
            .location("westus")
            .resourceGroupName("testResourceGroup")
            .sku(Map.of("name", "Standard"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const integrationAccount = new azure_native.logic.IntegrationAccount("integrationAccount", {
    integrationAccountName: "testIntegrationAccount",
    location: "westus",
    resourceGroupName: "testResourceGroup",
    sku: {
        name: "Standard",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

integration_account = azure_native.logic.IntegrationAccount("integrationAccount",
    integration_account_name="testIntegrationAccount",
    location="westus",
    resource_group_name="testResourceGroup",
    sku=azure_native.logic.IntegrationAccountSkuArgs(
        name="Standard",
    ))

```

```yaml
resources:
  integrationAccount:
    type: azure-native:logic:IntegrationAccount
    properties:
      integrationAccountName: testIntegrationAccount
      location: westus
      resourceGroupName: testResourceGroup
      sku:
        name: Standard

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:logic:IntegrationAccount testIntegrationAccount /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testResourceGroup/providers/Microsoft.Logic/integrationAccounts/testIntegrationAccount 
```
