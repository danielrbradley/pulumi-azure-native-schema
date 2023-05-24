An Azure Cosmos DB Cassandra keyspace.
API Version: 2022-11-15.
Previous API Version: 2021-03-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CosmosDBCassandraKeyspaceCreateUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cassandraResourceCassandraKeyspace = new AzureNative.DocumentDB.CassandraResourceCassandraKeyspace("cassandraResourceCassandraKeyspace", new()
    {
        AccountName = "ddb1",
        KeyspaceName = "keyspaceName",
        Location = "West US",
        Options = null,
        Resource = new AzureNative.DocumentDB.Inputs.CassandraKeyspaceResourceArgs
        {
            Id = "keyspaceName",
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
		_, err := documentdb.NewCassandraResourceCassandraKeyspace(ctx, "cassandraResourceCassandraKeyspace", &documentdb.CassandraResourceCassandraKeyspaceArgs{
			AccountName:  pulumi.String("ddb1"),
			KeyspaceName: pulumi.String("keyspaceName"),
			Location:     pulumi.String("West US"),
			Options:      nil,
			Resource: &documentdb.CassandraKeyspaceResourceArgs{
				Id: pulumi.String("keyspaceName"),
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
import com.pulumi.azurenative.documentdb.CassandraResourceCassandraKeyspace;
import com.pulumi.azurenative.documentdb.CassandraResourceCassandraKeyspaceArgs;
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
        var cassandraResourceCassandraKeyspace = new CassandraResourceCassandraKeyspace("cassandraResourceCassandraKeyspace", CassandraResourceCassandraKeyspaceArgs.builder()        
            .accountName("ddb1")
            .keyspaceName("keyspaceName")
            .location("West US")
            .options()
            .resource(Map.of("id", "keyspaceName"))
            .resourceGroupName("rg1")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cassandraResourceCassandraKeyspace = new azure_native.documentdb.CassandraResourceCassandraKeyspace("cassandraResourceCassandraKeyspace", {
    accountName: "ddb1",
    keyspaceName: "keyspaceName",
    location: "West US",
    options: {},
    resource: {
        id: "keyspaceName",
    },
    resourceGroupName: "rg1",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cassandra_resource_cassandra_keyspace = azure_native.documentdb.CassandraResourceCassandraKeyspace("cassandraResourceCassandraKeyspace",
    account_name="ddb1",
    keyspace_name="keyspaceName",
    location="West US",
    options=azure_native.documentdb.CreateUpdateOptionsArgs(),
    resource=azure_native.documentdb.CassandraKeyspaceResourceArgs(
        id="keyspaceName",
    ),
    resource_group_name="rg1",
    tags={})

```

```yaml
resources:
  cassandraResourceCassandraKeyspace:
    type: azure-native:documentdb:CassandraResourceCassandraKeyspace
    properties:
      accountName: ddb1
      keyspaceName: keyspaceName
      location: West US
      options: {}
      resource:
        id: keyspaceName
      resourceGroupName: rg1
      tags: {}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:documentdb:CassandraResourceCassandraKeyspace keyspaceName /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.DocumentDB/databaseAccounts/ddb1/cassandraKeyspaces/keyspaceName 
```
