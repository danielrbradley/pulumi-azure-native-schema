An Azure Cosmos DB MongoDB collection.
API Version: 2022-11-15.
Previous API Version: 2021-03-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CosmosDBMongoDBCollectionCreateUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var mongoDBResourceMongoDBCollection = new AzureNative.DocumentDB.MongoDBResourceMongoDBCollection("mongoDBResourceMongoDBCollection", new()
    {
        AccountName = "ddb1",
        CollectionName = "collectionName",
        DatabaseName = "databaseName",
        Location = "West US",
        Options = null,
        Resource = new AzureNative.DocumentDB.Inputs.MongoDBCollectionResourceArgs
        {
            Id = "collectionName",
            Indexes = new[]
            {
                new AzureNative.DocumentDB.Inputs.MongoIndexArgs
                {
                    Key = new AzureNative.DocumentDB.Inputs.MongoIndexKeysArgs
                    {
                        Keys = new[]
                        {
                            "_ts",
                        },
                    },
                    Options = new AzureNative.DocumentDB.Inputs.MongoIndexOptionsArgs
                    {
                        ExpireAfterSeconds = 100,
                        Unique = true,
                    },
                },
                new AzureNative.DocumentDB.Inputs.MongoIndexArgs
                {
                    Key = new AzureNative.DocumentDB.Inputs.MongoIndexKeysArgs
                    {
                        Keys = new[]
                        {
                            "_id",
                        },
                    },
                },
            },
            ShardKey = 
            {
                { "testKey", "Hash" },
            },
        },
        ResourceGroupName = "rg1",
        Tags = null,
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.documentdb.MongoDBResourceMongoDBCollection;
import com.pulumi.azurenative.documentdb.MongoDBResourceMongoDBCollectionArgs;
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
        var mongoDBResourceMongoDBCollection = new MongoDBResourceMongoDBCollection("mongoDBResourceMongoDBCollection", MongoDBResourceMongoDBCollectionArgs.builder()        
            .accountName("ddb1")
            .collectionName("collectionName")
            .databaseName("databaseName")
            .location("West US")
            .options()
            .resource(Map.ofEntries(
                Map.entry("id", "collectionName"),
                Map.entry("indexes",                 
                    Map.ofEntries(
                        Map.entry("key", Map.of("keys", "_ts")),
                        Map.entry("options", Map.ofEntries(
                            Map.entry("expireAfterSeconds", 100),
                            Map.entry("unique", true)
                        ))
                    ),
                    Map.of("key", Map.of("keys", "_id"))),
                Map.entry("shardKey", Map.of("testKey", "Hash"))
            ))
            .resourceGroupName("rg1")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const mongoDBResourceMongoDBCollection = new azure_native.documentdb.MongoDBResourceMongoDBCollection("mongoDBResourceMongoDBCollection", {
    accountName: "ddb1",
    collectionName: "collectionName",
    databaseName: "databaseName",
    location: "West US",
    options: {},
    resource: {
        id: "collectionName",
        indexes: [
            {
                key: {
                    keys: ["_ts"],
                },
                options: {
                    expireAfterSeconds: 100,
                    unique: true,
                },
            },
            {
                key: {
                    keys: ["_id"],
                },
            },
        ],
        shardKey: {
            testKey: "Hash",
        },
    },
    resourceGroupName: "rg1",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

mongo_db_resource_mongo_db_collection = azure_native.documentdb.MongoDBResourceMongoDBCollection("mongoDBResourceMongoDBCollection",
    account_name="ddb1",
    collection_name="collectionName",
    database_name="databaseName",
    location="West US",
    options=azure_native.documentdb.CreateUpdateOptionsArgs(),
    resource=azure_native.documentdb.MongoDBCollectionGetPropertiesResponseResourceArgs(
        id="collectionName",
        indexes=[
            {
                "key": azure_native.documentdb.MongoIndexKeysArgs(
                    keys=["_ts"],
                ),
                "options": azure_native.documentdb.MongoIndexOptionsArgs(
                    expire_after_seconds=100,
                    unique=True,
                ),
            },
            {
                "key": azure_native.documentdb.MongoIndexKeysArgs(
                    keys=["_id"],
                ),
            },
        ],
        shard_key={
            "testKey": "Hash",
        },
    ),
    resource_group_name="rg1",
    tags={})

```

```yaml
resources:
  mongoDBResourceMongoDBCollection:
    type: azure-native:documentdb:MongoDBResourceMongoDBCollection
    properties:
      accountName: ddb1
      collectionName: collectionName
      databaseName: databaseName
      location: West US
      options: {}
      resource:
        id: collectionName
        indexes:
          - key:
              keys:
                - _ts
            options:
              expireAfterSeconds: 100
              unique: true
          - key:
              keys:
                - _id
        shardKey:
          testKey: Hash
      resourceGroupName: rg1
      tags: {}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:documentdb:MongoDBResourceMongoDBCollection collectionName /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.DocumentDB/databaseAccounts/ddb1/mongodbDatabases/databaseName/mongodbCollections/collectionName 
```
