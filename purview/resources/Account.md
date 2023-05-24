Account resource
API Version: 2021-07-01.
Previous API Version: 2020-12-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Accounts_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var account = new AzureNative.Purview.Account("account", new()
    {
        AccountName = "account1",
        Location = "West US 2",
        ManagedResourceGroupName = "custom-rgname",
        ResourceGroupName = "SampleResourceGroup",
    });

});


```

```go
package main

import (
	purview "github.com/pulumi/pulumi-azure-native-sdk/purview"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := purview.NewAccount(ctx, "account", &purview.AccountArgs{
			AccountName:              pulumi.String("account1"),
			Location:                 pulumi.String("West US 2"),
			ManagedResourceGroupName: pulumi.String("custom-rgname"),
			ResourceGroupName:        pulumi.String("SampleResourceGroup"),
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
import com.pulumi.azurenative.purview.Account;
import com.pulumi.azurenative.purview.AccountArgs;
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
            .accountName("account1")
            .location("West US 2")
            .managedResourceGroupName("custom-rgname")
            .resourceGroupName("SampleResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const account = new azure_native.purview.Account("account", {
    accountName: "account1",
    location: "West US 2",
    managedResourceGroupName: "custom-rgname",
    resourceGroupName: "SampleResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

account = azure_native.purview.Account("account",
    account_name="account1",
    location="West US 2",
    managed_resource_group_name="custom-rgname",
    resource_group_name="SampleResourceGroup")

```

```yaml
resources:
  account:
    type: azure-native:purview:Account
    properties:
      accountName: account1
      location: West US 2
      managedResourceGroupName: custom-rgname
      resourceGroupName: SampleResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:purview:Account account1 /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/SampleResourceGroup/providers/Microsoft.Purview/accounts/account1 
```
