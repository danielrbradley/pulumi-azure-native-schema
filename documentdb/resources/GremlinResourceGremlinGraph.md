An Azure Cosmos DB Gremlin graph.
API Version: 2022-11-15.
Previous API Version: 2021-03-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CosmosDBGremlinGraphCreateUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var gremlinResourceGremlinGraph = new AzureNative.DocumentDB.GremlinResourceGremlinGraph("gremlinResourceGremlinGraph", new()
    {
        AccountName = "ddb1",
        DatabaseName = "databaseName",
        GraphName = "graphName",
        Location = "West US",
        Options = null,
        Resource = new AzureNative.DocumentDB.Inputs.GremlinGraphResourceArgs
        {
            ConflictResolutionPolicy = new AzureNative.DocumentDB.Inputs.ConflictResolutionPolicyArgs
            {
                ConflictResolutionPath = "/path",
                Mode = "LastWriterWins",
            },
            DefaultTtl = 100,
            Id = "graphName",
            IndexingPolicy = new AzureNative.DocumentDB.Inputs.IndexingPolicyArgs
            {
                Automatic = true,
                ExcludedPaths = new[] {},
                IncludedPaths = new[]
                {
                    new AzureNative.DocumentDB.Inputs.IncludedPathArgs
                    {
                        Indexes = new[]
                        {
                            new AzureNative.DocumentDB.Inputs.IndexesArgs
                            {
                                DataType = "String",
                                Kind = "Range",
                                Precision = -1,
                            },
                            new AzureNative.DocumentDB.Inputs.IndexesArgs
                            {
                                DataType = "Number",
                                Kind = "Range",
                                Precision = -1,
                            },
                        },
                        Path = "/*",
                    },
                },
                IndexingMode = "consistent",
            },
            PartitionKey = new AzureNative.DocumentDB.Inputs.ContainerPartitionKeyArgs
            {
                Kind = "Hash",
                Paths = new[]
                {
                    "/AccountNumber",
                },
            },
            UniqueKeyPolicy = new AzureNative.DocumentDB.Inputs.UniqueKeyPolicyArgs
            {
                UniqueKeys = new[]
                {
                    new AzureNative.DocumentDB.Inputs.UniqueKeyArgs
                    {
                        Paths = new[]
                        {
                            "/testPath",
                        },
                    },
                },
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
import com.pulumi.azurenative.documentdb.GremlinResourceGremlinGraph;
import com.pulumi.azurenative.documentdb.GremlinResourceGremlinGraphArgs;
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
        var gremlinResourceGremlinGraph = new GremlinResourceGremlinGraph("gremlinResourceGremlinGraph", GremlinResourceGremlinGraphArgs.builder()        
            .accountName("ddb1")
            .databaseName("databaseName")
            .graphName("graphName")
            .location("West US")
            .options()
            .resource(Map.ofEntries(
                Map.entry("conflictResolutionPolicy", Map.ofEntries(
                    Map.entry("conflictResolutionPath", "/path"),
                    Map.entry("mode", "LastWriterWins")
                )),
                Map.entry("defaultTtl", 100),
                Map.entry("id", "graphName"),
                Map.entry("indexingPolicy", Map.ofEntries(
                    Map.entry("automatic", true),
                    Map.entry("excludedPaths", ),
                    Map.entry("includedPaths", Map.ofEntries(
                        Map.entry("indexes",                         
                            Map.ofEntries(
                                Map.entry("dataType", "String"),
                                Map.entry("kind", "Range"),
                                Map.entry("precision", "TODO: GenUnaryOpExpression")
                            ),
                            Map.ofEntries(
                                Map.entry("dataType", "Number"),
                                Map.entry("kind", "Range"),
                                Map.entry("precision", "TODO: GenUnaryOpExpression")
                            )),
                        Map.entry("path", "/*")
                    )),
                    Map.entry("indexingMode", "consistent")
                )),
                Map.entry("partitionKey", Map.ofEntries(
                    Map.entry("kind", "Hash"),
                    Map.entry("paths", "/AccountNumber")
                )),
                Map.entry("uniqueKeyPolicy", Map.of("uniqueKeys", Map.of("paths", "/testPath")))
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

const gremlinResourceGremlinGraph = new azure_native.documentdb.GremlinResourceGremlinGraph("gremlinResourceGremlinGraph", {
    accountName: "ddb1",
    databaseName: "databaseName",
    graphName: "graphName",
    location: "West US",
    options: {},
    resource: {
        conflictResolutionPolicy: {
            conflictResolutionPath: "/path",
            mode: "LastWriterWins",
        },
        defaultTtl: 100,
        id: "graphName",
        indexingPolicy: {
            automatic: true,
            excludedPaths: [],
            includedPaths: [{
                indexes: [
                    {
                        dataType: "String",
                        kind: "Range",
                        precision: -1,
                    },
                    {
                        dataType: "Number",
                        kind: "Range",
                        precision: -1,
                    },
                ],
                path: "/*",
            }],
            indexingMode: "consistent",
        },
        partitionKey: {
            kind: "Hash",
            paths: ["/AccountNumber"],
        },
        uniqueKeyPolicy: {
            uniqueKeys: [{
                paths: ["/testPath"],
            }],
        },
    },
    resourceGroupName: "rg1",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

gremlin_resource_gremlin_graph = azure_native.documentdb.GremlinResourceGremlinGraph("gremlinResourceGremlinGraph",
    account_name="ddb1",
    database_name="databaseName",
    graph_name="graphName",
    location="West US",
    options=azure_native.documentdb.CreateUpdateOptionsArgs(),
    resource=azure_native.documentdb.GremlinGraphGetPropertiesResponseResourceArgs(
        conflict_resolution_policy=azure_native.documentdb.ConflictResolutionPolicyArgs(
            conflict_resolution_path="/path",
            mode="LastWriterWins",
        ),
        default_ttl=100,
        id="graphName",
        indexing_policy={
            "automatic": True,
            "excludedPaths": [],
            "includedPaths": [{
                "indexes": [
                    azure_native.documentdb.IndexesArgs(
                        data_type="String",
                        kind="Range",
                        precision=-1,
                    ),
                    azure_native.documentdb.IndexesArgs(
                        data_type="Number",
                        kind="Range",
                        precision=-1,
                    ),
                ],
                "path": "/*",
            }],
            "indexingMode": "consistent",
        },
        partition_key=azure_native.documentdb.ContainerPartitionKeyArgs(
            kind="Hash",
            paths=["/AccountNumber"],
        ),
        unique_key_policy={
            "uniqueKeys": [azure_native.documentdb.UniqueKeyArgs(
                paths=["/testPath"],
            )],
        },
    ),
    resource_group_name="rg1",
    tags={})

```

```yaml

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:documentdb:GremlinResourceGremlinGraph graphName /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.DocumentDB/databaseAccounts/ddb1/gremlinDatabases/databaseName/gremlinGraphs/graphName 
```
