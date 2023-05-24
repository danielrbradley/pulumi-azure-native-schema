Definition of the account.
API Version: 2020-10-30-preview.
Previous API Version: 2020-10-30-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update account
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var account = new AzureNative.PowerPlatform.Account("account", new()
    {
        AccountName = "account",
        Description = "Description of the account.",
        Location = "East US",
        ResourceGroupName = "resourceGroup",
        Tags = 
        {
            { "Organization", "Administration" },
        },
    });

});


```

```go
package main

import (
	powerplatform "github.com/pulumi/pulumi-azure-native-sdk/powerplatform"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := powerplatform.NewAccount(ctx, "account", &powerplatform.AccountArgs{
			AccountName:       pulumi.String("account"),
			Description:       pulumi.String("Description of the account."),
			Location:          pulumi.String("East US"),
			ResourceGroupName: pulumi.String("resourceGroup"),
			Tags: pulumi.StringMap{
				"Organization": pulumi.String("Administration"),
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
import com.pulumi.azurenative.powerplatform.Account;
import com.pulumi.azurenative.powerplatform.AccountArgs;
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
            .accountName("account")
            .description("Description of the account.")
            .location("East US")
            .resourceGroupName("resourceGroup")
            .tags(Map.of("Organization", "Administration"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const account = new azure_native.powerplatform.Account("account", {
    accountName: "account",
    description: "Description of the account.",
    location: "East US",
    resourceGroupName: "resourceGroup",
    tags: {
        Organization: "Administration",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

account = azure_native.powerplatform.Account("account",
    account_name="account",
    description="Description of the account.",
    location="East US",
    resource_group_name="resourceGroup",
    tags={
        "Organization": "Administration",
    })

```

```yaml
resources:
  account:
    type: azure-native:powerplatform:Account
    properties:
      accountName: account
      description: Description of the account.
      location: East US
      resourceGroupName: resourceGroup
      tags:
        Organization: Administration

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:powerplatform:Account account /subscriptions/subid/resourceGroups/resourceGroup/providers/Microsoft.PowerPlatform/accounts/account 
```
