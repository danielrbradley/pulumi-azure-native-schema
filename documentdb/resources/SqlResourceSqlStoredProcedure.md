An Azure Cosmos DB storedProcedure.
API Version: 2022-11-15.
Previous API Version: 2021-03-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CosmosDBSqlStoredProcedureCreateUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sqlResourceSqlStoredProcedure = new AzureNative.DocumentDB.SqlResourceSqlStoredProcedure("sqlResourceSqlStoredProcedure", new()
    {
        AccountName = "ddb1",
        ContainerName = "containerName",
        DatabaseName = "databaseName",
        Options = null,
        Resource = new AzureNative.DocumentDB.Inputs.SqlStoredProcedureResourceArgs
        {
            Body = "body",
            Id = "storedProcedureName",
        },
        ResourceGroupName = "rg1",
        StoredProcedureName = "storedProcedureName",
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
		_, err := documentdb.NewSqlResourceSqlStoredProcedure(ctx, "sqlResourceSqlStoredProcedure", &documentdb.SqlResourceSqlStoredProcedureArgs{
			AccountName:   pulumi.String("ddb1"),
			ContainerName: pulumi.String("containerName"),
			DatabaseName:  pulumi.String("databaseName"),
			Options:       nil,
			Resource: &documentdb.SqlStoredProcedureResourceArgs{
				Body: pulumi.String("body"),
				Id:   pulumi.String("storedProcedureName"),
			},
			ResourceGroupName:   pulumi.String("rg1"),
			StoredProcedureName: pulumi.String("storedProcedureName"),
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
import com.pulumi.azurenative.documentdb.SqlResourceSqlStoredProcedure;
import com.pulumi.azurenative.documentdb.SqlResourceSqlStoredProcedureArgs;
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
        var sqlResourceSqlStoredProcedure = new SqlResourceSqlStoredProcedure("sqlResourceSqlStoredProcedure", SqlResourceSqlStoredProcedureArgs.builder()        
            .accountName("ddb1")
            .containerName("containerName")
            .databaseName("databaseName")
            .options()
            .resource(Map.ofEntries(
                Map.entry("body", "body"),
                Map.entry("id", "storedProcedureName")
            ))
            .resourceGroupName("rg1")
            .storedProcedureName("storedProcedureName")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sqlResourceSqlStoredProcedure = new azure_native.documentdb.SqlResourceSqlStoredProcedure("sqlResourceSqlStoredProcedure", {
    accountName: "ddb1",
    containerName: "containerName",
    databaseName: "databaseName",
    options: {},
    resource: {
        body: "body",
        id: "storedProcedureName",
    },
    resourceGroupName: "rg1",
    storedProcedureName: "storedProcedureName",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sql_resource_sql_stored_procedure = azure_native.documentdb.SqlResourceSqlStoredProcedure("sqlResourceSqlStoredProcedure",
    account_name="ddb1",
    container_name="containerName",
    database_name="databaseName",
    options=azure_native.documentdb.CreateUpdateOptionsArgs(),
    resource=azure_native.documentdb.SqlStoredProcedureResourceArgs(
        body="body",
        id="storedProcedureName",
    ),
    resource_group_name="rg1",
    stored_procedure_name="storedProcedureName")

```

```yaml
resources:
  sqlResourceSqlStoredProcedure:
    type: azure-native:documentdb:SqlResourceSqlStoredProcedure
    properties:
      accountName: ddb1
      containerName: containerName
      databaseName: databaseName
      options: {}
      resource:
        body: body
        id: storedProcedureName
      resourceGroupName: rg1
      storedProcedureName: storedProcedureName

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:documentdb:SqlResourceSqlStoredProcedure storedProcedureName /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.DocumentDB/databaseAccounts/ddb1/sqlDatabases/databaseName/sqlContainers/containerName/sqlStoredProcedures/storedProcedureName 
```
