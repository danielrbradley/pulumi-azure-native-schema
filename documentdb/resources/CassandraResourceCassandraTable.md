An Azure Cosmos DB Cassandra table.
API Version: 2022-11-15.
Previous API Version: 2021-03-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CosmosDBCassandraTableCreateUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cassandraResourceCassandraTable = new AzureNative.DocumentDB.CassandraResourceCassandraTable("cassandraResourceCassandraTable", new()
    {
        AccountName = "ddb1",
        KeyspaceName = "keyspaceName",
        Location = "West US",
        Options = null,
        Resource = new AzureNative.DocumentDB.Inputs.CassandraTableResourceArgs
        {
            DefaultTtl = 100,
            Id = "tableName",
            Schema = new AzureNative.DocumentDB.Inputs.CassandraSchemaArgs
            {
                ClusterKeys = new[]
                {
                    new AzureNative.DocumentDB.Inputs.ClusterKeyArgs
                    {
                        Name = "columnA",
                        OrderBy = "Asc",
                    },
                },
                Columns = new[]
                {
                    new AzureNative.DocumentDB.Inputs.ColumnArgs
                    {
                        Name = "columnA",
                        Type = "Ascii",
                    },
                },
                PartitionKeys = new[]
                {
                    new AzureNative.DocumentDB.Inputs.CassandraPartitionKeyArgs
                    {
                        Name = "columnA",
                    },
                },
            },
        },
        ResourceGroupName = "rg1",
        TableName = "tableName",
        Tags = null,
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.documentdb.CassandraResourceCassandraTable;
import com.pulumi.azurenative.documentdb.CassandraResourceCassandraTableArgs;
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
        var cassandraResourceCassandraTable = new CassandraResourceCassandraTable("cassandraResourceCassandraTable", CassandraResourceCassandraTableArgs.builder()        
            .accountName("ddb1")
            .keyspaceName("keyspaceName")
            .location("West US")
            .options()
            .resource(Map.ofEntries(
                Map.entry("defaultTtl", 100),
                Map.entry("id", "tableName"),
                Map.entry("schema", Map.ofEntries(
                    Map.entry("clusterKeys", Map.ofEntries(
                        Map.entry("name", "columnA"),
                        Map.entry("orderBy", "Asc")
                    )),
                    Map.entry("columns", Map.ofEntries(
                        Map.entry("name", "columnA"),
                        Map.entry("type", "Ascii")
                    )),
                    Map.entry("partitionKeys", Map.of("name", "columnA"))
                ))
            ))
            .resourceGroupName("rg1")
            .tableName("tableName")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cassandraResourceCassandraTable = new azure_native.documentdb.CassandraResourceCassandraTable("cassandraResourceCassandraTable", {
    accountName: "ddb1",
    keyspaceName: "keyspaceName",
    location: "West US",
    options: {},
    resource: {
        defaultTtl: 100,
        id: "tableName",
        schema: {
            clusterKeys: [{
                name: "columnA",
                orderBy: "Asc",
            }],
            columns: [{
                name: "columnA",
                type: "Ascii",
            }],
            partitionKeys: [{
                name: "columnA",
            }],
        },
    },
    resourceGroupName: "rg1",
    tableName: "tableName",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cassandra_resource_cassandra_table = azure_native.documentdb.CassandraResourceCassandraTable("cassandraResourceCassandraTable",
    account_name="ddb1",
    keyspace_name="keyspaceName",
    location="West US",
    options=azure_native.documentdb.CreateUpdateOptionsArgs(),
    resource=azure_native.documentdb.CassandraTableGetPropertiesResponseResourceArgs(
        default_ttl=100,
        id="tableName",
        schema={
            "clusterKeys": [azure_native.documentdb.ClusterKeyArgs(
                name="columnA",
                order_by="Asc",
            )],
            "columns": [azure_native.documentdb.ColumnArgs(
                name="columnA",
                type="Ascii",
            )],
            "partitionKeys": [azure_native.documentdb.CassandraPartitionKeyArgs(
                name="columnA",
            )],
        },
    ),
    resource_group_name="rg1",
    table_name="tableName",
    tags={})

```

```yaml
resources:
  cassandraResourceCassandraTable:
    type: azure-native:documentdb:CassandraResourceCassandraTable
    properties:
      accountName: ddb1
      keyspaceName: keyspaceName
      location: West US
      options: {}
      resource:
        defaultTtl: 100
        id: tableName
        schema:
          clusterKeys:
            - name: columnA
              orderBy: Asc
          columns:
            - name: columnA
              type: Ascii
          partitionKeys:
            - name: columnA
      resourceGroupName: rg1
      tableName: tableName
      tags: {}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:documentdb:CassandraResourceCassandraTable tableName /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.DocumentDB/databaseAccounts/ddb1/cassandraKeyspaces/keyspaceName/cassandraTables/tableName 
```
