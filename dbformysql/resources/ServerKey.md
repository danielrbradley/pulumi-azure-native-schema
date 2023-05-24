A MySQL Server key.
API Version: 2020-01-01.
Previous API Version: 2020-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates or updates a MySQL Server key
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var serverKey = new AzureNative.DBforMySQL.ServerKey("serverKey", new()
    {
        KeyName = "someVault_someKey_01234567890123456789012345678901",
        ResourceGroupName = "testrg",
        ServerKeyType = "AzureKeyVault",
        ServerName = "testserver",
        Uri = "https://someVault.vault.azure.net/keys/someKey/01234567890123456789012345678901",
    });

});


```

```go
package main

import (
	dbformysql "github.com/pulumi/pulumi-azure-native-sdk/dbformysql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := dbformysql.NewServerKey(ctx, "serverKey", &dbformysql.ServerKeyArgs{
			KeyName:           pulumi.String("someVault_someKey_01234567890123456789012345678901"),
			ResourceGroupName: pulumi.String("testrg"),
			ServerKeyType:     pulumi.String("AzureKeyVault"),
			ServerName:        pulumi.String("testserver"),
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
import com.pulumi.azurenative.dbformysql.ServerKey;
import com.pulumi.azurenative.dbformysql.ServerKeyArgs;
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
            .resourceGroupName("testrg")
            .serverKeyType("AzureKeyVault")
            .serverName("testserver")
            .uri("https://someVault.vault.azure.net/keys/someKey/01234567890123456789012345678901")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const serverKey = new azure_native.dbformysql.ServerKey("serverKey", {
    keyName: "someVault_someKey_01234567890123456789012345678901",
    resourceGroupName: "testrg",
    serverKeyType: "AzureKeyVault",
    serverName: "testserver",
    uri: "https://someVault.vault.azure.net/keys/someKey/01234567890123456789012345678901",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

server_key = azure_native.dbformysql.ServerKey("serverKey",
    key_name="someVault_someKey_01234567890123456789012345678901",
    resource_group_name="testrg",
    server_key_type="AzureKeyVault",
    server_name="testserver",
    uri="https://someVault.vault.azure.net/keys/someKey/01234567890123456789012345678901")

```

```yaml
resources:
  serverKey:
    type: azure-native:dbformysql:ServerKey
    properties:
      keyName: someVault_someKey_01234567890123456789012345678901
      resourceGroupName: testrg
      serverKeyType: AzureKeyVault
      serverName: testserver
      uri: https://someVault.vault.azure.net/keys/someKey/01234567890123456789012345678901

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:dbformysql:ServerKey omeVault_someKey_01234567890123456789012345678901 /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.DBforMySQL/servers/testserver/keys/someVault_someKey_01234567890123456789012345678901 
```
