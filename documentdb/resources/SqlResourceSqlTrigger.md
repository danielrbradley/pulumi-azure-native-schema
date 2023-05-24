An Azure Cosmos DB trigger.
API Version: 2022-11-15.
Previous API Version: 2021-03-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CosmosDBSqlTriggerCreateUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sqlResourceSqlTrigger = new AzureNative.DocumentDB.SqlResourceSqlTrigger("sqlResourceSqlTrigger", new()
    {
        AccountName = "ddb1",
        ContainerName = "containerName",
        DatabaseName = "databaseName",
        Options = null,
        Resource = new AzureNative.DocumentDB.Inputs.SqlTriggerResourceArgs
        {
            Body = "body",
            Id = "triggerName",
            TriggerOperation = "triggerOperation",
            TriggerType = "triggerType",
        },
        ResourceGroupName = "rg1",
        TriggerName = "triggerName",
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
		_, err := documentdb.NewSqlResourceSqlTrigger(ctx, "sqlResourceSqlTrigger", &documentdb.SqlResourceSqlTriggerArgs{
			AccountName:   pulumi.String("ddb1"),
			ContainerName: pulumi.String("containerName"),
			DatabaseName:  pulumi.String("databaseName"),
			Options:       nil,
			Resource: &documentdb.SqlTriggerResourceArgs{
				Body:             pulumi.String("body"),
				Id:               pulumi.String("triggerName"),
				TriggerOperation: pulumi.String("triggerOperation"),
				TriggerType:      pulumi.String("triggerType"),
			},
			ResourceGroupName: pulumi.String("rg1"),
			TriggerName:       pulumi.String("triggerName"),
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
import com.pulumi.azurenative.documentdb.SqlResourceSqlTrigger;
import com.pulumi.azurenative.documentdb.SqlResourceSqlTriggerArgs;
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
        var sqlResourceSqlTrigger = new SqlResourceSqlTrigger("sqlResourceSqlTrigger", SqlResourceSqlTriggerArgs.builder()        
            .accountName("ddb1")
            .containerName("containerName")
            .databaseName("databaseName")
            .options()
            .resource(Map.ofEntries(
                Map.entry("body", "body"),
                Map.entry("id", "triggerName"),
                Map.entry("triggerOperation", "triggerOperation"),
                Map.entry("triggerType", "triggerType")
            ))
            .resourceGroupName("rg1")
            .triggerName("triggerName")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sqlResourceSqlTrigger = new azure_native.documentdb.SqlResourceSqlTrigger("sqlResourceSqlTrigger", {
    accountName: "ddb1",
    containerName: "containerName",
    databaseName: "databaseName",
    options: {},
    resource: {
        body: "body",
        id: "triggerName",
        triggerOperation: "triggerOperation",
        triggerType: "triggerType",
    },
    resourceGroupName: "rg1",
    triggerName: "triggerName",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sql_resource_sql_trigger = azure_native.documentdb.SqlResourceSqlTrigger("sqlResourceSqlTrigger",
    account_name="ddb1",
    container_name="containerName",
    database_name="databaseName",
    options=azure_native.documentdb.CreateUpdateOptionsArgs(),
    resource=azure_native.documentdb.SqlTriggerResourceArgs(
        body="body",
        id="triggerName",
        trigger_operation="triggerOperation",
        trigger_type="triggerType",
    ),
    resource_group_name="rg1",
    trigger_name="triggerName")

```

```yaml
resources:
  sqlResourceSqlTrigger:
    type: azure-native:documentdb:SqlResourceSqlTrigger
    properties:
      accountName: ddb1
      containerName: containerName
      databaseName: databaseName
      options: {}
      resource:
        body: body
        id: triggerName
        triggerOperation: triggerOperation
        triggerType: triggerType
      resourceGroupName: rg1
      triggerName: triggerName

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:documentdb:SqlResourceSqlTrigger triggerName /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.DocumentDB/databaseAccounts/ddb1/sqlDatabases/databaseName/sqlContainers/containerName/sqlTriggers/triggerName 
```
