An account data transfer object.
API Version: 2021-08-01.
Previous API Version: 2020-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Accounts_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var account = new AzureNative.DataShare.Account("account", new()
    {
        AccountName = "Account1",
        Identity = new AzureNative.DataShare.Inputs.IdentityArgs
        {
            Type = "SystemAssigned",
        },
        Location = "West US 2",
        ResourceGroupName = "SampleResourceGroup",
        Tags = 
        {
            { "tag1", "Red" },
            { "tag2", "White" },
        },
    });

});


```

```go
package main

import (
	datashare "github.com/pulumi/pulumi-azure-native-sdk/datashare"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := datashare.NewAccount(ctx, "account", &datashare.AccountArgs{
			AccountName: pulumi.String("Account1"),
			Identity: &datashare.IdentityArgs{
				Type: pulumi.String("SystemAssigned"),
			},
			Location:          pulumi.String("West US 2"),
			ResourceGroupName: pulumi.String("SampleResourceGroup"),
			Tags: pulumi.StringMap{
				"tag1": pulumi.String("Red"),
				"tag2": pulumi.String("White"),
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
import com.pulumi.azurenative.datashare.Account;
import com.pulumi.azurenative.datashare.AccountArgs;
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
            .accountName("Account1")
            .identity(Map.of("type", "SystemAssigned"))
            .location("West US 2")
            .resourceGroupName("SampleResourceGroup")
            .tags(Map.ofEntries(
                Map.entry("tag1", "Red"),
                Map.entry("tag2", "White")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const account = new azure_native.datashare.Account("account", {
    accountName: "Account1",
    identity: {
        type: "SystemAssigned",
    },
    location: "West US 2",
    resourceGroupName: "SampleResourceGroup",
    tags: {
        tag1: "Red",
        tag2: "White",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

account = azure_native.datashare.Account("account",
    account_name="Account1",
    identity=azure_native.datashare.IdentityArgs(
        type="SystemAssigned",
    ),
    location="West US 2",
    resource_group_name="SampleResourceGroup",
    tags={
        "tag1": "Red",
        "tag2": "White",
    })

```

```yaml
resources:
  account:
    type: azure-native:datashare:Account
    properties:
      accountName: Account1
      identity:
        type: SystemAssigned
      location: West US 2
      resourceGroupName: SampleResourceGroup
      tags:
        tag1: Red
        tag2: White

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:datashare:Account Account1 /subscriptions/433a8dfd-e5d5-4e77-ad86-90acdc75eb1a/resourceGroups/SampleResourceGroup/providers/Microsoft.DataShare/accounts/Account1 
```
