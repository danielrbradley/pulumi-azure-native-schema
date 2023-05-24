An object that represents a machine learning team account.
API Version: 2017-05-01-preview.
Previous API Version: 2017-05-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### AccountCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var account = new AzureNative.MachineLearningExperimentation.Account("account", new()
    {
        AccountName = "accountcrud5678",
        KeyVaultId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/accountcrud-1234/providers/Microsoft.KeyVault/vaults/testkv",
        Location = "East US",
        ResourceGroupName = "accountcrud-1234",
        StorageAccount = new AzureNative.MachineLearningExperimentation.Inputs.StorageAccountPropertiesArgs
        {
            AccessKey = "key",
            StorageAccountId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/accountcrud-1234/providers/Microsoft.Storage/storageAccounts/testStorageAccount",
        },
        Tags = 
        {
            { "tagKey1", "TagValue1" },
        },
        VsoAccountId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/accountcrud-1234/providers/microsoft.visualstudio/account/vsotest",
    });

});


```

```go
package main

import (
	machinelearningexperimentation "github.com/pulumi/pulumi-azure-native-sdk/machinelearningexperimentation"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := machinelearningexperimentation.NewAccount(ctx, "account", &machinelearningexperimentation.AccountArgs{
			AccountName:       pulumi.String("accountcrud5678"),
			KeyVaultId:        pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/accountcrud-1234/providers/Microsoft.KeyVault/vaults/testkv"),
			Location:          pulumi.String("East US"),
			ResourceGroupName: pulumi.String("accountcrud-1234"),
			StorageAccount: &machinelearningexperimentation.StorageAccountPropertiesArgs{
				AccessKey:        pulumi.String("key"),
				StorageAccountId: pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/accountcrud-1234/providers/Microsoft.Storage/storageAccounts/testStorageAccount"),
			},
			Tags: pulumi.StringMap{
				"tagKey1": pulumi.String("TagValue1"),
			},
			VsoAccountId: pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/accountcrud-1234/providers/microsoft.visualstudio/account/vsotest"),
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
import com.pulumi.azurenative.machinelearningexperimentation.Account;
import com.pulumi.azurenative.machinelearningexperimentation.AccountArgs;
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
            .accountName("accountcrud5678")
            .keyVaultId("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/accountcrud-1234/providers/Microsoft.KeyVault/vaults/testkv")
            .location("East US")
            .resourceGroupName("accountcrud-1234")
            .storageAccount(Map.ofEntries(
                Map.entry("accessKey", "key"),
                Map.entry("storageAccountId", "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/accountcrud-1234/providers/Microsoft.Storage/storageAccounts/testStorageAccount")
            ))
            .tags(Map.of("tagKey1", "TagValue1"))
            .vsoAccountId("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/accountcrud-1234/providers/microsoft.visualstudio/account/vsotest")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const account = new azure_native.machinelearningexperimentation.Account("account", {
    accountName: "accountcrud5678",
    keyVaultId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/accountcrud-1234/providers/Microsoft.KeyVault/vaults/testkv",
    location: "East US",
    resourceGroupName: "accountcrud-1234",
    storageAccount: {
        accessKey: "key",
        storageAccountId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/accountcrud-1234/providers/Microsoft.Storage/storageAccounts/testStorageAccount",
    },
    tags: {
        tagKey1: "TagValue1",
    },
    vsoAccountId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/accountcrud-1234/providers/microsoft.visualstudio/account/vsotest",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

account = azure_native.machinelearningexperimentation.Account("account",
    account_name="accountcrud5678",
    key_vault_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/accountcrud-1234/providers/Microsoft.KeyVault/vaults/testkv",
    location="East US",
    resource_group_name="accountcrud-1234",
    storage_account=azure_native.machinelearningexperimentation.StorageAccountPropertiesArgs(
        access_key="key",
        storage_account_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/accountcrud-1234/providers/Microsoft.Storage/storageAccounts/testStorageAccount",
    ),
    tags={
        "tagKey1": "TagValue1",
    },
    vso_account_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/accountcrud-1234/providers/microsoft.visualstudio/account/vsotest")

```

```yaml
resources:
  account:
    type: azure-native:machinelearningexperimentation:Account
    properties:
      accountName: accountcrud5678
      keyVaultId: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/accountcrud-1234/providers/Microsoft.KeyVault/vaults/testkv
      location: East US
      resourceGroupName: accountcrud-1234
      storageAccount:
        accessKey: key
        storageAccountId: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/accountcrud-1234/providers/Microsoft.Storage/storageAccounts/testStorageAccount
      tags:
        tagKey1: TagValue1
      vsoAccountId: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/accountcrud-1234/providers/microsoft.visualstudio/account/vsotest

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:machinelearningexperimentation:Account accountcrud5678 /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/accountcrud-1234/providers/Microsoft.MachineLearningExperimentation/accounts/accountcrud5678 
```
