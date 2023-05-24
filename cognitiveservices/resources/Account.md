Cognitive Services account is an Azure resource representing the provisioned account, it's type, location and SKU.
API Version: 2022-12-01.
Previous API Version: 2017-04-18. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Account
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var account = new AzureNative.CognitiveServices.Account("account", new()
    {
        AccountName = "testCreate1",
        Identity = new AzureNative.CognitiveServices.Inputs.IdentityArgs
        {
            Type = AzureNative.CognitiveServices.ResourceIdentityType.SystemAssigned,
        },
        Kind = "Emotion",
        Location = "West US",
        Properties = new AzureNative.CognitiveServices.Inputs.AccountPropertiesArgs
        {
            Encryption = new AzureNative.CognitiveServices.Inputs.EncryptionArgs
            {
                KeySource = "Microsoft.KeyVault",
                KeyVaultProperties = new AzureNative.CognitiveServices.Inputs.KeyVaultPropertiesArgs
                {
                    KeyName = "KeyName",
                    KeyVaultUri = "https://pltfrmscrts-use-pc-dev.vault.azure.net/",
                    KeyVersion = "891CF236-D241-4738-9462-D506AF493DFA",
                },
            },
            UserOwnedStorage = new[]
            {
                new AzureNative.CognitiveServices.Inputs.UserOwnedStorageArgs
                {
                    ResourceId = "/subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/myStorageAccount",
                },
            },
        },
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.CognitiveServices.Inputs.SkuArgs
        {
            Name = "S0",
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.cognitiveservices.Account;
import com.pulumi.azurenative.cognitiveservices.AccountArgs;
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
            .accountName("testCreate1")
            .identity(Map.of("type", "SystemAssigned"))
            .kind("Emotion")
            .location("West US")
            .properties(Map.ofEntries(
                Map.entry("encryption", Map.ofEntries(
                    Map.entry("keySource", "Microsoft.KeyVault"),
                    Map.entry("keyVaultProperties", Map.ofEntries(
                        Map.entry("keyName", "KeyName"),
                        Map.entry("keyVaultUri", "https://pltfrmscrts-use-pc-dev.vault.azure.net/"),
                        Map.entry("keyVersion", "891CF236-D241-4738-9462-D506AF493DFA")
                    ))
                )),
                Map.entry("userOwnedStorage", Map.of("resourceId", "/subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/myStorageAccount"))
            ))
            .resourceGroupName("myResourceGroup")
            .sku(Map.of("name", "S0"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const account = new azure_native.cognitiveservices.Account("account", {
    accountName: "testCreate1",
    identity: {
        type: azure_native.cognitiveservices.ResourceIdentityType.SystemAssigned,
    },
    kind: "Emotion",
    location: "West US",
    properties: {
        encryption: {
            keySource: "Microsoft.KeyVault",
            keyVaultProperties: {
                keyName: "KeyName",
                keyVaultUri: "https://pltfrmscrts-use-pc-dev.vault.azure.net/",
                keyVersion: "891CF236-D241-4738-9462-D506AF493DFA",
            },
        },
        userOwnedStorage: [{
            resourceId: "/subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/myStorageAccount",
        }],
    },
    resourceGroupName: "myResourceGroup",
    sku: {
        name: "S0",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

account = azure_native.cognitiveservices.Account("account",
    account_name="testCreate1",
    identity=azure_native.cognitiveservices.IdentityArgs(
        type=azure_native.cognitiveservices.ResourceIdentityType.SYSTEM_ASSIGNED,
    ),
    kind="Emotion",
    location="West US",
    properties=azure_native.cognitiveservices.AccountPropertiesResponseArgs(
        encryption={
            "keySource": "Microsoft.KeyVault",
            "keyVaultProperties": azure_native.cognitiveservices.KeyVaultPropertiesArgs(
                key_name="KeyName",
                key_vault_uri="https://pltfrmscrts-use-pc-dev.vault.azure.net/",
                key_version="891CF236-D241-4738-9462-D506AF493DFA",
            ),
        },
        user_owned_storage=[azure_native.cognitiveservices.UserOwnedStorageArgs(
            resource_id="/subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/myStorageAccount",
        )],
    ),
    resource_group_name="myResourceGroup",
    sku=azure_native.cognitiveservices.SkuArgs(
        name="S0",
    ))

```

```yaml
resources:
  account:
    type: azure-native:cognitiveservices:Account
    properties:
      accountName: testCreate1
      identity:
        type: SystemAssigned
      kind: Emotion
      location: West US
      properties:
        encryption:
          keySource: Microsoft.KeyVault
          keyVaultProperties:
            keyName: KeyName
            keyVaultUri: https://pltfrmscrts-use-pc-dev.vault.azure.net/
            keyVersion: 891CF236-D241-4738-9462-D506AF493DFA
        userOwnedStorage:
          - resourceId: /subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/myStorageAccount
      resourceGroupName: myResourceGroup
      sku:
        name: S0

```

{{% /example %}}
{{% example %}}
### Create Account Min
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var account = new AzureNative.CognitiveServices.Account("account", new()
    {
        AccountName = "testCreate1",
        Identity = new AzureNative.CognitiveServices.Inputs.IdentityArgs
        {
            Type = AzureNative.CognitiveServices.ResourceIdentityType.SystemAssigned,
        },
        Kind = "CognitiveServices",
        Location = "West US",
        Properties = null,
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.CognitiveServices.Inputs.SkuArgs
        {
            Name = "S0",
        },
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
		_, err := cognitiveservices.NewAccount(ctx, "account", &cognitiveservices.AccountArgs{
			AccountName: pulumi.String("testCreate1"),
			Identity: &cognitiveservices.IdentityArgs{
				Type: cognitiveservices.ResourceIdentityTypeSystemAssigned,
			},
			Kind:              pulumi.String("CognitiveServices"),
			Location:          pulumi.String("West US"),
			Properties:        nil,
			ResourceGroupName: pulumi.String("myResourceGroup"),
			Sku: &cognitiveservices.SkuArgs{
				Name: pulumi.String("S0"),
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
import com.pulumi.azurenative.cognitiveservices.Account;
import com.pulumi.azurenative.cognitiveservices.AccountArgs;
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
            .accountName("testCreate1")
            .identity(Map.of("type", "SystemAssigned"))
            .kind("CognitiveServices")
            .location("West US")
            .properties()
            .resourceGroupName("myResourceGroup")
            .sku(Map.of("name", "S0"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const account = new azure_native.cognitiveservices.Account("account", {
    accountName: "testCreate1",
    identity: {
        type: azure_native.cognitiveservices.ResourceIdentityType.SystemAssigned,
    },
    kind: "CognitiveServices",
    location: "West US",
    properties: {},
    resourceGroupName: "myResourceGroup",
    sku: {
        name: "S0",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

account = azure_native.cognitiveservices.Account("account",
    account_name="testCreate1",
    identity=azure_native.cognitiveservices.IdentityArgs(
        type=azure_native.cognitiveservices.ResourceIdentityType.SYSTEM_ASSIGNED,
    ),
    kind="CognitiveServices",
    location="West US",
    properties=azure_native.cognitiveservices.AccountPropertiesArgs(),
    resource_group_name="myResourceGroup",
    sku=azure_native.cognitiveservices.SkuArgs(
        name="S0",
    ))

```

```yaml
resources:
  account:
    type: azure-native:cognitiveservices:Account
    properties:
      accountName: testCreate1
      identity:
        type: SystemAssigned
      kind: CognitiveServices
      location: West US
      properties: {}
      resourceGroupName: myResourceGroup
      sku:
        name: S0

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:cognitiveservices:Account testCreate1 /subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/resourceGroups/myResourceGroup/providers/Microsoft.CognitiveServices/accounts/testCreate1 
```
