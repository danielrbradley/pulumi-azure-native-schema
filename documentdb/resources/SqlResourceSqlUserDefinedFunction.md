An Azure Cosmos DB userDefinedFunction.
API Version: 2022-11-15.
Previous API Version: 2021-03-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CosmosDBSqlUserDefinedFunctionCreateUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sqlResourceSqlUserDefinedFunction = new AzureNative.DocumentDB.SqlResourceSqlUserDefinedFunction("sqlResourceSqlUserDefinedFunction", new()
    {
        AccountName = "ddb1",
        ContainerName = "containerName",
        DatabaseName = "databaseName",
        Options = null,
        Resource = new AzureNative.DocumentDB.Inputs.SqlUserDefinedFunctionResourceArgs
        {
            Body = "body",
            Id = "userDefinedFunctionName",
        },
        ResourceGroupName = "rg1",
        UserDefinedFunctionName = "userDefinedFunctionName",
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
		_, err := documentdb.NewSqlResourceSqlUserDefinedFunction(ctx, "sqlResourceSqlUserDefinedFunction", &documentdb.SqlResourceSqlUserDefinedFunctionArgs{
			AccountName:   pulumi.String("ddb1"),
			ContainerName: pulumi.String("containerName"),
			DatabaseName:  pulumi.String("databaseName"),
			Options:       nil,
			Resource: &documentdb.SqlUserDefinedFunctionResourceArgs{
				Body: pulumi.String("body"),
				Id:   pulumi.String("userDefinedFunctionName"),
			},
			ResourceGroupName:       pulumi.String("rg1"),
			UserDefinedFunctionName: pulumi.String("userDefinedFunctionName"),
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
import com.pulumi.azurenative.documentdb.SqlResourceSqlUserDefinedFunction;
import com.pulumi.azurenative.documentdb.SqlResourceSqlUserDefinedFunctionArgs;
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
        var sqlResourceSqlUserDefinedFunction = new SqlResourceSqlUserDefinedFunction("sqlResourceSqlUserDefinedFunction", SqlResourceSqlUserDefinedFunctionArgs.builder()        
            .accountName("ddb1")
            .containerName("containerName")
            .databaseName("databaseName")
            .options()
            .resource(Map.ofEntries(
                Map.entry("body", "body"),
                Map.entry("id", "userDefinedFunctionName")
            ))
            .resourceGroupName("rg1")
            .userDefinedFunctionName("userDefinedFunctionName")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sqlResourceSqlUserDefinedFunction = new azure_native.documentdb.SqlResourceSqlUserDefinedFunction("sqlResourceSqlUserDefinedFunction", {
    accountName: "ddb1",
    containerName: "containerName",
    databaseName: "databaseName",
    options: {},
    resource: {
        body: "body",
        id: "userDefinedFunctionName",
    },
    resourceGroupName: "rg1",
    userDefinedFunctionName: "userDefinedFunctionName",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sql_resource_sql_user_defined_function = azure_native.documentdb.SqlResourceSqlUserDefinedFunction("sqlResourceSqlUserDefinedFunction",
    account_name="ddb1",
    container_name="containerName",
    database_name="databaseName",
    options=azure_native.documentdb.CreateUpdateOptionsArgs(),
    resource=azure_native.documentdb.SqlUserDefinedFunctionResourceArgs(
        body="body",
        id="userDefinedFunctionName",
    ),
    resource_group_name="rg1",
    user_defined_function_name="userDefinedFunctionName")

```

```yaml
resources:
  sqlResourceSqlUserDefinedFunction:
    type: azure-native:documentdb:SqlResourceSqlUserDefinedFunction
    properties:
      accountName: ddb1
      containerName: containerName
      databaseName: databaseName
      options: {}
      resource:
        body: body
        id: userDefinedFunctionName
      resourceGroupName: rg1
      userDefinedFunctionName: userDefinedFunctionName

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:documentdb:SqlResourceSqlUserDefinedFunction userDefinedFunctionName /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.DocumentDB/databaseAccounts/ddb1/sqlDatabases/databaseName/sqlContainers/containerName/sqlUserDefinedFunctions/userDefinedFunctionName 
```
