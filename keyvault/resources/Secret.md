Resource information with extended details.
API Version: 2023-02-01.
Previous API Version: 2019-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a secret
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var secret = new AzureNative.KeyVault.Secret("secret", new()
    {
        Properties = new AzureNative.KeyVault.Inputs.SecretPropertiesArgs
        {
            Value = "secret-value",
        },
        ResourceGroupName = "sample-group",
        SecretName = "secret-name",
        VaultName = "sample-vault",
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
		_, err := keyvault.NewSecret(ctx, "secret", &keyvault.SecretArgs{
			Properties: &keyvault.SecretPropertiesArgs{
				Value: pulumi.String("secret-value"),
			},
			ResourceGroupName: pulumi.String("sample-group"),
			SecretName:        pulumi.String("secret-name"),
			VaultName:         pulumi.String("sample-vault"),
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
import com.pulumi.azurenative.keyvault.Secret;
import com.pulumi.azurenative.keyvault.SecretArgs;
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
        var secret = new Secret("secret", SecretArgs.builder()        
            .properties(Map.of("value", "secret-value"))
            .resourceGroupName("sample-group")
            .secretName("secret-name")
            .vaultName("sample-vault")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const secret = new azure_native.keyvault.Secret("secret", {
    properties: {
        value: "secret-value",
    },
    resourceGroupName: "sample-group",
    secretName: "secret-name",
    vaultName: "sample-vault",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

secret = azure_native.keyvault.Secret("secret",
    properties=azure_native.keyvault.SecretPropertiesArgs(
        value="secret-value",
    ),
    resource_group_name="sample-group",
    secret_name="secret-name",
    vault_name="sample-vault")

```

```yaml
resources:
  secret:
    type: azure-native:keyvault:Secret
    properties:
      properties:
        value: secret-value
      resourceGroupName: sample-group
      secretName: secret-name
      vaultName: sample-vault

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:keyvault:Secret secret-name /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/sample-group/providers/Microsoft.KeyVault/vaults/sample-vault/secrets/secret-name 
```
