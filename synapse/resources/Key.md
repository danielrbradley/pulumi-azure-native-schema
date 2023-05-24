A workspace key
API Version: 2021-06-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a workspace key
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var key = new AzureNative.Synapse.Key("key", new()
    {
        IsActiveCMK = true,
        KeyName = "somekey",
        KeyVaultUrl = "https://vault.azure.net/keys/somesecret",
        ResourceGroupName = "ExampleResourceGroup",
        WorkspaceName = "ExampleWorkspace",
    });

});


```

```go
package main

import (
	synapse "github.com/pulumi/pulumi-azure-native-sdk/synapse"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := synapse.NewKey(ctx, "key", &synapse.KeyArgs{
			IsActiveCMK:       pulumi.Bool(true),
			KeyName:           pulumi.String("somekey"),
			KeyVaultUrl:       pulumi.String("https://vault.azure.net/keys/somesecret"),
			ResourceGroupName: pulumi.String("ExampleResourceGroup"),
			WorkspaceName:     pulumi.String("ExampleWorkspace"),
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
import com.pulumi.azurenative.synapse.Key;
import com.pulumi.azurenative.synapse.KeyArgs;
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
            .isActiveCMK(true)
            .keyName("somekey")
            .keyVaultUrl("https://vault.azure.net/keys/somesecret")
            .resourceGroupName("ExampleResourceGroup")
            .workspaceName("ExampleWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const key = new azure_native.synapse.Key("key", {
    isActiveCMK: true,
    keyName: "somekey",
    keyVaultUrl: "https://vault.azure.net/keys/somesecret",
    resourceGroupName: "ExampleResourceGroup",
    workspaceName: "ExampleWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

key = azure_native.synapse.Key("key",
    is_active_cmk=True,
    key_name="somekey",
    key_vault_url="https://vault.azure.net/keys/somesecret",
    resource_group_name="ExampleResourceGroup",
    workspace_name="ExampleWorkspace")

```

```yaml
resources:
  key:
    type: azure-native:synapse:Key
    properties:
      isActiveCMK: true
      keyName: somekey
      keyVaultUrl: https://vault.azure.net/keys/somesecret
      resourceGroupName: ExampleResourceGroup
      workspaceName: ExampleWorkspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:synapse:Key somekey /subscriptions/01234567-89ab-4def-0123-456789abcdef/resourceGroups/ExampleResourceGroup/providers/Microsoft.Synapse/workspaces/ExampleWorkspace/keys/somekey 
```
