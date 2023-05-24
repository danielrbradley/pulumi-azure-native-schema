Represents a Database.
API Version: 2018-06-01.
Previous API Version: 2018-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### DatabaseCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var database = new AzureNative.DBforMariaDB.Database("database", new()
    {
        Charset = "utf8",
        Collation = "utf8_general_ci",
        DatabaseName = "db1",
        ResourceGroupName = "TestGroup",
        ServerName = "testserver",
    });

});


```

```go
package main

import (
	dbformariadb "github.com/pulumi/pulumi-azure-native-sdk/dbformariadb"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := dbformariadb.NewDatabase(ctx, "database", &dbformariadb.DatabaseArgs{
			Charset:           pulumi.String("utf8"),
			Collation:         pulumi.String("utf8_general_ci"),
			DatabaseName:      pulumi.String("db1"),
			ResourceGroupName: pulumi.String("TestGroup"),
			ServerName:        pulumi.String("testserver"),
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
import com.pulumi.azurenative.dbformariadb.Database;
import com.pulumi.azurenative.dbformariadb.DatabaseArgs;
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
        var database = new Database("database", DatabaseArgs.builder()        
            .charset("utf8")
            .collation("utf8_general_ci")
            .databaseName("db1")
            .resourceGroupName("TestGroup")
            .serverName("testserver")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const database = new azure_native.dbformariadb.Database("database", {
    charset: "utf8",
    collation: "utf8_general_ci",
    databaseName: "db1",
    resourceGroupName: "TestGroup",
    serverName: "testserver",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

database = azure_native.dbformariadb.Database("database",
    charset="utf8",
    collation="utf8_general_ci",
    database_name="db1",
    resource_group_name="TestGroup",
    server_name="testserver")

```

```yaml
resources:
  database:
    type: azure-native:dbformariadb:Database
    properties:
      charset: utf8
      collation: utf8_general_ci
      databaseName: db1
      resourceGroupName: TestGroup
      serverName: testserver

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:dbformariadb:Database db1 /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/TestGroup/providers/Microsoft.DBforMariaDB/servers/testserver/databases/db1 
```
