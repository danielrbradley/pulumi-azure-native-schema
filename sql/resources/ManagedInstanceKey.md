A managed instance key.
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates or updates a managed instance key
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedInstanceKey = new AzureNative.Sql.ManagedInstanceKey("managedInstanceKey", new()
    {
        KeyName = "someVault_someKey_01234567890123456789012345678901",
        ManagedInstanceName = "sqlcrudtest-4645",
        ResourceGroupName = "sqlcrudtest-7398",
        ServerKeyType = "AzureKeyVault",
        Uri = "https://someVault.vault.azure.net/keys/someKey/01234567890123456789012345678901",
    });

});


```

```go
package main

import (
	sql "github.com/pulumi/pulumi-azure-native-sdk/sql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := sql.NewManagedInstanceKey(ctx, "managedInstanceKey", &sql.ManagedInstanceKeyArgs{
			KeyName:             pulumi.String("someVault_someKey_01234567890123456789012345678901"),
			ManagedInstanceName: pulumi.String("sqlcrudtest-4645"),
			ResourceGroupName:   pulumi.String("sqlcrudtest-7398"),
			ServerKeyType:       pulumi.String("AzureKeyVault"),
			Uri:                 pulumi.String("https://someVault.vault.azure.net/keys/someKey/01234567890123456789012345678901"),
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
import com.pulumi.azurenative.sql.ManagedInstanceKey;
import com.pulumi.azurenative.sql.ManagedInstanceKeyArgs;
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
        var managedInstanceKey = new ManagedInstanceKey("managedInstanceKey", ManagedInstanceKeyArgs.builder()        
            .keyName("someVault_someKey_01234567890123456789012345678901")
            .managedInstanceName("sqlcrudtest-4645")
            .resourceGroupName("sqlcrudtest-7398")
            .serverKeyType("AzureKeyVault")
            .uri("https://someVault.vault.azure.net/keys/someKey/01234567890123456789012345678901")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedInstanceKey = new azure_native.sql.ManagedInstanceKey("managedInstanceKey", {
    keyName: "someVault_someKey_01234567890123456789012345678901",
    managedInstanceName: "sqlcrudtest-4645",
    resourceGroupName: "sqlcrudtest-7398",
    serverKeyType: "AzureKeyVault",
    uri: "https://someVault.vault.azure.net/keys/someKey/01234567890123456789012345678901",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_instance_key = azure_native.sql.ManagedInstanceKey("managedInstanceKey",
    key_name="someVault_someKey_01234567890123456789012345678901",
    managed_instance_name="sqlcrudtest-4645",
    resource_group_name="sqlcrudtest-7398",
    server_key_type="AzureKeyVault",
    uri="https://someVault.vault.azure.net/keys/someKey/01234567890123456789012345678901")

```

```yaml
resources:
  managedInstanceKey:
    type: azure-native:sql:ManagedInstanceKey
    properties:
      keyName: someVault_someKey_01234567890123456789012345678901
      managedInstanceName: sqlcrudtest-4645
      resourceGroupName: sqlcrudtest-7398
      serverKeyType: AzureKeyVault
      uri: https://someVault.vault.azure.net/keys/someKey/01234567890123456789012345678901

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:ManagedInstanceKey sqlcrudtest-4645 /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/sqlcrudtest-7398/providers/Microsoft.Sql/managedInstances/sqlcrudtest-4645/keys/someVault_someKey_01234567890123456789012345678901 
```
