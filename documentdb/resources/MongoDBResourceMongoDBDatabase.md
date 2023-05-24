An Azure Cosmos DB MongoDB database.
API Version: 2022-11-15.
Previous API Version: 2021-03-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CosmosDBMongoDBDatabaseCreateUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var mongoDBResourceMongoDBDatabase = new AzureNative.DocumentDB.MongoDBResourceMongoDBDatabase("mongoDBResourceMongoDBDatabase", new()
    {
        AccountName = "ddb1",
        DatabaseName = "databaseName",
        Location = "West US",
        Options = null,
        Resource = new AzureNative.DocumentDB.Inputs.MongoDBDatabaseResourceArgs
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
		_, err := documentdb.NewMongoDBResourceMongoDBDatabase(ctx, "mongoDBResourceMongoDBDatabase", &documentdb.MongoDBResourceMongoDBDatabaseArgs{
			AccountName:  pulumi.String("ddb1"),
			DatabaseName: pulumi.String("databaseName"),
			Location:     pulumi.String("West US"),
			Options:      nil,
			Resource: &documentdb.MongoDBDatabaseResourceArgs{
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
import com.pulumi.azurenative.documentdb.MongoDBResourceMongoDBDatabase;
import com.pulumi.azurenative.documentdb.MongoDBResourceMongoDBDatabaseArgs;
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
        var mongoDBResourceMongoDBDatabase = new MongoDBResourceMongoDBDatabase("mongoDBResourceMongoDBDatabase", MongoDBResourceMongoDBDatabaseArgs.builder()        
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

const mongoDBResourceMongoDBDatabase = new azure_native.documentdb.MongoDBResourceMongoDBDatabase("mongoDBResourceMongoDBDatabase", {
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

mongo_db_resource_mongo_db_database = azure_native.documentdb.MongoDBResourceMongoDBDatabase("mongoDBResourceMongoDBDatabase",
    account_name="ddb1",
    database_name="databaseName",
    location="West US",
    options=azure_native.documentdb.CreateUpdateOptionsArgs(),
    resource=azure_native.documentdb.MongoDBDatabaseResourceArgs(
        id="databaseName",
    ),
    resource_group_name="rg1",
    tags={})

```

```yaml
resources:
  mongoDBResourceMongoDBDatabase:
    type: azure-native:documentdb:MongoDBResourceMongoDBDatabase
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
$ pulumi import azure-native:documentdb:MongoDBResourceMongoDBDatabase databaseName /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.DocumentDB/databaseAccounts/ddb1/mongodbDatabases/databaseName 
```
