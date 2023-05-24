Represents a Database.
API Version: 2021-05-01.
Previous API Version: 2017-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a database
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var database = new AzureNative.DBforMySQL.Database("database", new()
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
	dbformysql "github.com/pulumi/pulumi-azure-native-sdk/dbformysql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := dbformysql.NewDatabase(ctx, "database", &dbformysql.DatabaseArgs{
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
import com.pulumi.azurenative.dbformysql.Database;
import com.pulumi.azurenative.dbformysql.DatabaseArgs;
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

const database = new azure_native.dbformysql.Database("database", {
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

database = azure_native.dbformysql.Database("database",
    charset="utf8",
    collation="utf8_general_ci",
    database_name="db1",
    resource_group_name="TestGroup",
    server_name="testserver")

```

```yaml
resources:
  database:
    type: azure-native:dbformysql:Database
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
$ pulumi import azure-native:dbformysql:Database db1 /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/TestGroup/providers/Microsoft.DBforMySQL/flexibleServers/testserver/databases/db1 
```
