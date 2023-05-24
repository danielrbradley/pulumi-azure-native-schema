An Azure Cosmos DB Table.
API Version: 2022-11-15.
Previous API Version: 2021-03-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CosmosDBTableReplace
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var tableResourceTable = new AzureNative.DocumentDB.TableResourceTable("tableResourceTable", new()
    {
        AccountName = "ddb1",
        Location = "West US",
        Options = null,
        Resource = new AzureNative.DocumentDB.Inputs.TableResourceArgs
        {
            Id = "tableName",
        },
        ResourceGroupName = "rg1",
        TableName = "tableName",
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
		_, err := documentdb.NewTableResourceTable(ctx, "tableResourceTable", &documentdb.TableResourceTableArgs{
			AccountName: pulumi.String("ddb1"),
			Location:    pulumi.String("West US"),
			Options:     nil,
			Resource: &documentdb.TableResourceArgs{
				Id: pulumi.String("tableName"),
			},
			ResourceGroupName: pulumi.String("rg1"),
			TableName:         pulumi.String("tableName"),
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
import com.pulumi.azurenative.documentdb.TableResourceTable;
import com.pulumi.azurenative.documentdb.TableResourceTableArgs;
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
        var tableResourceTable = new TableResourceTable("tableResourceTable", TableResourceTableArgs.builder()        
            .accountName("ddb1")
            .location("West US")
            .options()
            .resource(Map.of("id", "tableName"))
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

const tableResourceTable = new azure_native.documentdb.TableResourceTable("tableResourceTable", {
    accountName: "ddb1",
    location: "West US",
    options: {},
    resource: {
        id: "tableName",
    },
    resourceGroupName: "rg1",
    tableName: "tableName",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

table_resource_table = azure_native.documentdb.TableResourceTable("tableResourceTable",
    account_name="ddb1",
    location="West US",
    options=azure_native.documentdb.CreateUpdateOptionsArgs(),
    resource=azure_native.documentdb.TableResourceArgs(
        id="tableName",
    ),
    resource_group_name="rg1",
    table_name="tableName",
    tags={})

```

```yaml
resources:
  tableResourceTable:
    type: azure-native:documentdb:TableResourceTable
    properties:
      accountName: ddb1
      location: West US
      options: {}
      resource:
        id: tableName
      resourceGroupName: rg1
      tableName: tableName
      tags: {}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:documentdb:TableResourceTable tableName /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.DocumentDB/databaseAccounts/ddb1/tables/tableName 
```
