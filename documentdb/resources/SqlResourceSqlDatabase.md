An Azure Cosmos DB SQL database.
API Version: 2022-11-15.
Previous API Version: 2021-03-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CosmosDBSqlDatabaseCreateUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sqlResourceSqlDatabase = new AzureNative.DocumentDB.SqlResourceSqlDatabase("sqlResourceSqlDatabase", new()
    {
        AccountName = "ddb1",
        DatabaseName = "databaseName",
        Location = "West US",
        Options = null,
        Resource = new AzureNative.DocumentDB.Inputs.SqlDatabaseResourceArgs
        {
            Id = "databaseName",
        },
        ResourceGroupName = "rg1",
        Tags = null,
    });

});


```

```go
package main

import (
	documentdb "github.com/pulumi/pulumi-azure-native-sdk/documentdb"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := documentdb.NewSqlResourceSqlDatabase(ctx, "sqlResourceSqlDatabase", &documentdb.SqlResourceSqlDatabaseArgs{
			AccountName:  pulumi.String("ddb1"),
			DatabaseName: pulumi.String("databaseName"),
			Location:     pulumi.String("West US"),
			Options:      nil,
			Resource: &documentdb.SqlDatabaseResourceArgs{
				Id: pulumi.String("databaseName"),
			},
			ResourceGroupName: pulumi.String("rg1"),
			Tags:              nil,
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
import com.pulumi.azurenative.documentdb.SqlResourceSqlDatabase;
import com.pulumi.azurenative.documentdb.SqlResourceSqlDatabaseArgs;
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
        var sqlResourceSqlDatabase = new SqlResourceSqlDatabase("sqlResourceSqlDatabase", SqlResourceSqlDatabaseArgs.builder()        
            .accountName("ddb1")
            .databaseName("databaseName")
            .location("West US")
            .options()
            .resource(Map.of("id", "databaseName"))
            .resourceGroupName("rg1")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sqlResourceSqlDatabase = new azure_native.documentdb.SqlResourceSqlDatabase("sqlResourceSqlDatabase", {
    accountName: "ddb1",
    databaseName: "databaseName",
    location: "West US",
    options: {},
    resource: {
        id: "databaseName",
    },
    resourceGroupName: "rg1",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sql_resource_sql_database = azure_native.documentdb.SqlResourceSqlDatabase("sqlResourceSqlDatabase",
    account_name="ddb1",
    database_name="databaseName",
    location="West US",
    options=azure_native.documentdb.CreateUpdateOptionsArgs(),
    resource=azure_native.documentdb.SqlDatabaseResourceArgs(
        id="databaseName",
    ),
    resource_group_name="rg1",
    tags={})

```

```yaml
resources:
  sqlResourceSqlDatabase:
    type: azure-native:documentdb:SqlResourceSqlDatabase
    properties:
      accountName: ddb1
      databaseName: databaseName
      location: West US
      options: {}
      resource:
        id: databaseName
      resourceGroupName: rg1
      tags: {}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:documentdb:SqlResourceSqlDatabase databaseName /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.DocumentDB/databaseAccounts/ddb1/sqlDatabases/databaseName 
```
