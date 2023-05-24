The Encryption Scope resource.
API Version: 2022-09-01.
Previous API Version: 2021-02-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### StorageAccountPutEncryptionScope
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var encryptionScope = new AzureNative.Storage.EncryptionScope("encryptionScope", new()
    {
        AccountName = "{storage-account-name}",
        EncryptionScopeName = "{encryption-scope-name}",
        ResourceGroupName = "resource-group-name",
    });

});


```

```go
package main

import (
	storage "github.com/pulumi/pulumi-azure-native-sdk/storage"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := storage.NewEncryptionScope(ctx, "encryptionScope", &storage.EncryptionScopeArgs{
			AccountName:         pulumi.String("{storage-account-name}"),
			EncryptionScopeName: pulumi.String("{encryption-scope-name}"),
			ResourceGroupName:   pulumi.String("resource-group-name"),
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
import com.pulumi.azurenative.storage.EncryptionScope;
import com.pulumi.azurenative.storage.EncryptionScopeArgs;
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
        var encryptionScope = new EncryptionScope("encryptionScope", EncryptionScopeArgs.builder()        
            .accountName("{storage-account-name}")
            .encryptionScopeName("{encryption-scope-name}")
            .resourceGroupName("resource-group-name")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const encryptionScope = new azure_native.storage.EncryptionScope("encryptionScope", {
    accountName: "{storage-account-name}",
    encryptionScopeName: "{encryption-scope-name}",
    resourceGroupName: "resource-group-name",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

encryption_scope = azure_native.storage.EncryptionScope("encryptionScope",
    account_name="{storage-account-name}",
    encryption_scope_name="{encryption-scope-name}",
    resource_group_name="resource-group-name")

```

```yaml
resources:
  encryptionScope:
    type: azure-native:storage:EncryptionScope
    properties:
      accountName: '{storage-account-name}'
      encryptionScopeName: '{encryption-scope-name}'
      resourceGroupName: resource-group-name

```

{{% /example %}}
{{% example %}}
### StorageAccountPutEncryptionScopeWithInfrastructureEncryption
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var encryptionScope = new AzureNative.Storage.EncryptionScope("encryptionScope", new()
    {
        AccountName = "{storage-account-name}",
        EncryptionScopeName = "{encryption-scope-name}",
        RequireInfrastructureEncryption = true,
        ResourceGroupName = "resource-group-name",
    });

});


```

```go
package main

import (
	storage "github.com/pulumi/pulumi-azure-native-sdk/storage"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := storage.NewEncryptionScope(ctx, "encryptionScope", &storage.EncryptionScopeArgs{
			AccountName:                     pulumi.String("{storage-account-name}"),
			EncryptionScopeName:             pulumi.String("{encryption-scope-name}"),
			RequireInfrastructureEncryption: pulumi.Bool(true),
			ResourceGroupName:               pulumi.String("resource-group-name"),
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
import com.pulumi.azurenative.storage.EncryptionScope;
import com.pulumi.azurenative.storage.EncryptionScopeArgs;
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
        var encryptionScope = new EncryptionScope("encryptionScope", EncryptionScopeArgs.builder()        
            .accountName("{storage-account-name}")
            .encryptionScopeName("{encryption-scope-name}")
            .requireInfrastructureEncryption(true)
            .resourceGroupName("resource-group-name")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const encryptionScope = new azure_native.storage.EncryptionScope("encryptionScope", {
    accountName: "{storage-account-name}",
    encryptionScopeName: "{encryption-scope-name}",
    requireInfrastructureEncryption: true,
    resourceGroupName: "resource-group-name",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

encryption_scope = azure_native.storage.EncryptionScope("encryptionScope",
    account_name="{storage-account-name}",
    encryption_scope_name="{encryption-scope-name}",
    require_infrastructure_encryption=True,
    resource_group_name="resource-group-name")

```

```yaml
resources:
  encryptionScope:
    type: azure-native:storage:EncryptionScope
    properties:
      accountName: '{storage-account-name}'
      encryptionScopeName: '{encryption-scope-name}'
      requireInfrastructureEncryption: true
      resourceGroupName: resource-group-name

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:storage:EncryptionScope {encryption-scope-name} /subscriptions/{subscription-id}/resourceGroups/resource-group-name/providers/Microsoft.Storage/storageAccounts/{storage-account-name}/encryptionScopes/{encryption-scope-name} 
```
