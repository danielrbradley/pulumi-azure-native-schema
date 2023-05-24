The EngagementFabric account
API Version: 2018-09-01-preview.
Previous API Version: 2018-09-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### AccountsCreateOrUpdateExample
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var account = new AzureNative.EngagementFabric.Account("account", new()
    {
        AccountName = "ExampleAccount",
        Location = "WestUS",
        ResourceGroupName = "ExampleRg",
        Sku = new AzureNative.EngagementFabric.Inputs.SKUArgs
        {
            Name = "B1",
        },
    });

});


```

```go
package main

import (
	engagementfabric "github.com/pulumi/pulumi-azure-native-sdk/engagementfabric"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := engagementfabric.NewAccount(ctx, "account", &engagementfabric.AccountArgs{
			AccountName:       pulumi.String("ExampleAccount"),
			Location:          pulumi.String("WestUS"),
			ResourceGroupName: pulumi.String("ExampleRg"),
			Sku: &engagementfabric.SKUArgs{
				Name: pulumi.String("B1"),
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
import com.pulumi.azurenative.engagementfabric.Account;
import com.pulumi.azurenative.engagementfabric.AccountArgs;
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
        var account = new Account("account", AccountArgs.builder()        
            .accountName("ExampleAccount")
            .location("WestUS")
            .resourceGroupName("ExampleRg")
            .sku(Map.of("name", "B1"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const account = new azure_native.engagementfabric.Account("account", {
    accountName: "ExampleAccount",
    location: "WestUS",
    resourceGroupName: "ExampleRg",
    sku: {
        name: "B1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

account = azure_native.engagementfabric.Account("account",
    account_name="ExampleAccount",
    location="WestUS",
    resource_group_name="ExampleRg",
    sku=azure_native.engagementfabric.SKUArgs(
        name="B1",
    ))

```

```yaml
resources:
  account:
    type: azure-native:engagementfabric:Account
    properties:
      accountName: ExampleAccount
      location: WestUS
      resourceGroupName: ExampleRg
      sku:
        name: B1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:engagementfabric:Account ExampleAccount subscriptions/EDBF0095-A524-4A84-95FB-F72DA41AA6A1/resourceGroups/ExampleRg/providers/Microsoft.EngagementFabric/Accounts/ExampleAccount 
```
