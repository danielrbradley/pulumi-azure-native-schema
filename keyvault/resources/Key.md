The key resource.
API Version: 2023-02-01.
Previous API Version: 2019-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a key
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var key = new AzureNative.KeyVault.Key("key", new()
    {
        KeyName = "sample-key-name",
        Properties = new AzureNative.KeyVault.Inputs.KeyPropertiesArgs
        {
            Kty = "RSA",
        },
        ResourceGroupName = "sample-group",
        VaultName = "sample-vault-name",
    });

});


```

```go
package main

import (
	keyvault "github.com/pulumi/pulumi-azure-native-sdk/keyvault"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := keyvault.NewKey(ctx, "key", &keyvault.KeyArgs{
			KeyName: pulumi.String("sample-key-name"),
			Properties: &keyvault.KeyPropertiesArgs{
				Kty: pulumi.String("RSA"),
			},
			ResourceGroupName: pulumi.String("sample-group"),
			VaultName:         pulumi.String("sample-vault-name"),
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
import com.pulumi.azurenative.keyvault.Key;
import com.pulumi.azurenative.keyvault.KeyArgs;
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
        var key = new Key("key", KeyArgs.builder()        
            .keyName("sample-key-name")
            .properties(Map.of("kty", "RSA"))
            .resourceGroupName("sample-group")
            .vaultName("sample-vault-name")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const key = new azure_native.keyvault.Key("key", {
    keyName: "sample-key-name",
    properties: {
        kty: "RSA",
    },
    resourceGroupName: "sample-group",
    vaultName: "sample-vault-name",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

key = azure_native.keyvault.Key("key",
    key_name="sample-key-name",
    properties=azure_native.keyvault.KeyPropertiesArgs(
        kty="RSA",
    ),
    resource_group_name="sample-group",
    vault_name="sample-vault-name")

```

```yaml
resources:
  key:
    type: azure-native:keyvault:Key
    properties:
      keyName: sample-key-name
      properties:
        kty: RSA
      resourceGroupName: sample-group
      vaultName: sample-vault-name

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:keyvault:Key sample-key-name /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/sample-group/providers/Microsoft.KeyVault/vaults/sample-vault-name/keys/sample-key-name 
```
