A logical database transparent data encryption state.
API Version: 2021-11-01.
Previous API Version: 2014-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Update a database's Transparent Data Encryption state with minimal parameters
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var transparentDataEncryption = new AzureNative.Sql.TransparentDataEncryption("transparentDataEncryption", new()
    {
        DatabaseName = "testdb",
        ResourceGroupName = "securitytde-42-rg",
        ServerName = "securitytde-42",
        State = AzureNative.Sql.TransparentDataEncryptionState.Enabled,
        TdeName = "current",
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
		_, err := sql.NewTransparentDataEncryption(ctx, "transparentDataEncryption", &sql.TransparentDataEncryptionArgs{
			DatabaseName:      pulumi.String("testdb"),
			ResourceGroupName: pulumi.String("securitytde-42-rg"),
			ServerName:        pulumi.String("securitytde-42"),
			State:             sql.TransparentDataEncryptionStateEnabled,
			TdeName:           pulumi.String("current"),
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
import com.pulumi.azurenative.sql.TransparentDataEncryption;
import com.pulumi.azurenative.sql.TransparentDataEncryptionArgs;
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
        var transparentDataEncryption = new TransparentDataEncryption("transparentDataEncryption", TransparentDataEncryptionArgs.builder()        
            .databaseName("testdb")
            .resourceGroupName("securitytde-42-rg")
            .serverName("securitytde-42")
            .state("Enabled")
            .tdeName("current")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const transparentDataEncryption = new azure_native.sql.TransparentDataEncryption("transparentDataEncryption", {
    databaseName: "testdb",
    resourceGroupName: "securitytde-42-rg",
    serverName: "securitytde-42",
    state: azure_native.sql.TransparentDataEncryptionState.Enabled,
    tdeName: "current",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

transparent_data_encryption = azure_native.sql.TransparentDataEncryption("transparentDataEncryption",
    database_name="testdb",
    resource_group_name="securitytde-42-rg",
    server_name="securitytde-42",
    state=azure_native.sql.TransparentDataEncryptionState.ENABLED,
    tde_name="current")

```

```yaml
resources:
  transparentDataEncryption:
    type: azure-native:sql:TransparentDataEncryption
    properties:
      databaseName: testdb
      resourceGroupName: securitytde-42-rg
      serverName: securitytde-42
      state: Enabled
      tdeName: current

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:TransparentDataEncryption current /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/securitytde-42-rg/providers/Microsoft.Sql/servers/securitytde-42/databases/testdb/transparentDataEncryption 
```
