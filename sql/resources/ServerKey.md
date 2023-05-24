A server key.
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates or updates a server key
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var serverKey = new AzureNative.Sql.ServerKey("serverKey", new()
    {
        KeyName = "someVault_someKey_01234567890123456789012345678901",
        ResourceGroupName = "sqlcrudtest-7398",
        ServerKeyType = "AzureKeyVault",
        ServerName = "sqlcrudtest-4645",
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
		_, err := sql.NewServerKey(ctx, "serverKey", &sql.ServerKeyArgs{
			KeyName:           pulumi.String("someVault_someKey_01234567890123456789012345678901"),
			ResourceGroupName: pulumi.String("sqlcrudtest-7398"),
			ServerKeyType:     pulumi.String("AzureKeyVault"),
			ServerName:        pulumi.String("sqlcrudtest-4645"),
			Uri:               pulumi.String("https://someVault.vault.azure.net/keys/someKey/01234567890123456789012345678901"),
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
import com.pulumi.azurenative.sql.ServerKey;
import com.pulumi.azurenative.sql.ServerKeyArgs;
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
        var serverKey = new ServerKey("serverKey", ServerKeyArgs.builder()        
            .keyName("someVault_someKey_01234567890123456789012345678901")
            .resourceGroupName("sqlcrudtest-7398")
            .serverKeyType("AzureKeyVault")
            .serverName("sqlcrudtest-4645")
            .uri("https://someVault.vault.azure.net/keys/someKey/01234567890123456789012345678901")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const serverKey = new azure_native.sql.ServerKey("serverKey", {
    keyName: "someVault_someKey_01234567890123456789012345678901",
    resourceGroupName: "sqlcrudtest-7398",
    serverKeyType: "AzureKeyVault",
    serverName: "sqlcrudtest-4645",
    uri: "https://someVault.vault.azure.net/keys/someKey/01234567890123456789012345678901",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

server_key = azure_native.sql.ServerKey("serverKey",
    key_name="someVault_someKey_01234567890123456789012345678901",
    resource_group_name="sqlcrudtest-7398",
    server_key_type="AzureKeyVault",
    server_name="sqlcrudtest-4645",
    uri="https://someVault.vault.azure.net/keys/someKey/01234567890123456789012345678901")

```

```yaml
resources:
  serverKey:
    type: azure-native:sql:ServerKey
    properties:
      keyName: someVault_someKey_01234567890123456789012345678901
      resourceGroupName: sqlcrudtest-7398
      serverKeyType: AzureKeyVault
      serverName: sqlcrudtest-4645
      uri: https://someVault.vault.azure.net/keys/someKey/01234567890123456789012345678901

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:ServerKey sqlcrudtest-4645 /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/sqlcrudtest-7398/providers/Microsoft.Sql/servers/sqlcrudtest-4645/keys/someVault_someKey_01234567890123456789012345678901 
```
