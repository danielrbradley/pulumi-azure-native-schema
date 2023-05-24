The server encryption protector.
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Update the encryption protector to key vault
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var encryptionProtector = new AzureNative.Sql.EncryptionProtector("encryptionProtector", new()
    {
        AutoRotationEnabled = false,
        EncryptionProtectorName = "current",
        ResourceGroupName = "sqlcrudtest-7398",
        ServerKeyName = "someVault_someKey_01234567890123456789012345678901",
        ServerKeyType = "AzureKeyVault",
        ServerName = "sqlcrudtest-4645",
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
		_, err := sql.NewEncryptionProtector(ctx, "encryptionProtector", &sql.EncryptionProtectorArgs{
			AutoRotationEnabled:     pulumi.Bool(false),
			EncryptionProtectorName: pulumi.String("current"),
			ResourceGroupName:       pulumi.String("sqlcrudtest-7398"),
			ServerKeyName:           pulumi.String("someVault_someKey_01234567890123456789012345678901"),
			ServerKeyType:           pulumi.String("AzureKeyVault"),
			ServerName:              pulumi.String("sqlcrudtest-4645"),
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
import com.pulumi.azurenative.sql.EncryptionProtector;
import com.pulumi.azurenative.sql.EncryptionProtectorArgs;
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
        var encryptionProtector = new EncryptionProtector("encryptionProtector", EncryptionProtectorArgs.builder()        
            .autoRotationEnabled(false)
            .encryptionProtectorName("current")
            .resourceGroupName("sqlcrudtest-7398")
            .serverKeyName("someVault_someKey_01234567890123456789012345678901")
            .serverKeyType("AzureKeyVault")
            .serverName("sqlcrudtest-4645")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const encryptionProtector = new azure_native.sql.EncryptionProtector("encryptionProtector", {
    autoRotationEnabled: false,
    encryptionProtectorName: "current",
    resourceGroupName: "sqlcrudtest-7398",
    serverKeyName: "someVault_someKey_01234567890123456789012345678901",
    serverKeyType: "AzureKeyVault",
    serverName: "sqlcrudtest-4645",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

encryption_protector = azure_native.sql.EncryptionProtector("encryptionProtector",
    auto_rotation_enabled=False,
    encryption_protector_name="current",
    resource_group_name="sqlcrudtest-7398",
    server_key_name="someVault_someKey_01234567890123456789012345678901",
    server_key_type="AzureKeyVault",
    server_name="sqlcrudtest-4645")

```

```yaml
resources:
  encryptionProtector:
    type: azure-native:sql:EncryptionProtector
    properties:
      autoRotationEnabled: false
      encryptionProtectorName: current
      resourceGroupName: sqlcrudtest-7398
      serverKeyName: someVault_someKey_01234567890123456789012345678901
      serverKeyType: AzureKeyVault
      serverName: sqlcrudtest-4645

```

{{% /example %}}
{{% example %}}
### Update the encryption protector to service managed
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var encryptionProtector = new AzureNative.Sql.EncryptionProtector("encryptionProtector", new()
    {
        EncryptionProtectorName = "current",
        ResourceGroupName = "sqlcrudtest-7398",
        ServerKeyName = "ServiceManaged",
        ServerKeyType = "ServiceManaged",
        ServerName = "sqlcrudtest-4645",
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
		_, err := sql.NewEncryptionProtector(ctx, "encryptionProtector", &sql.EncryptionProtectorArgs{
			EncryptionProtectorName: pulumi.String("current"),
			ResourceGroupName:       pulumi.String("sqlcrudtest-7398"),
			ServerKeyName:           pulumi.String("ServiceManaged"),
			ServerKeyType:           pulumi.String("ServiceManaged"),
			ServerName:              pulumi.String("sqlcrudtest-4645"),
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
import com.pulumi.azurenative.sql.EncryptionProtector;
import com.pulumi.azurenative.sql.EncryptionProtectorArgs;
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
        var encryptionProtector = new EncryptionProtector("encryptionProtector", EncryptionProtectorArgs.builder()        
            .encryptionProtectorName("current")
            .resourceGroupName("sqlcrudtest-7398")
            .serverKeyName("ServiceManaged")
            .serverKeyType("ServiceManaged")
            .serverName("sqlcrudtest-4645")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const encryptionProtector = new azure_native.sql.EncryptionProtector("encryptionProtector", {
    encryptionProtectorName: "current",
    resourceGroupName: "sqlcrudtest-7398",
    serverKeyName: "ServiceManaged",
    serverKeyType: "ServiceManaged",
    serverName: "sqlcrudtest-4645",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

encryption_protector = azure_native.sql.EncryptionProtector("encryptionProtector",
    encryption_protector_name="current",
    resource_group_name="sqlcrudtest-7398",
    server_key_name="ServiceManaged",
    server_key_type="ServiceManaged",
    server_name="sqlcrudtest-4645")

```

```yaml
resources:
  encryptionProtector:
    type: azure-native:sql:EncryptionProtector
    properties:
      encryptionProtectorName: current
      resourceGroupName: sqlcrudtest-7398
      serverKeyName: ServiceManaged
      serverKeyType: ServiceManaged
      serverName: sqlcrudtest-4645

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:EncryptionProtector current /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/sqlcrudtest-7398/providers/Microsoft.Sql/servers/sqlcrudtest-4645/encryptionProtector/current 
```
