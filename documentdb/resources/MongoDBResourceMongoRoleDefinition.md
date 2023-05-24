An Azure Cosmos DB Mongo Role Definition.
API Version: 2022-11-15.
Previous API Version: 2021-10-15-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CosmosDBMongoDBRoleDefinitionCreateUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var mongoDBResourceMongoRoleDefinition = new AzureNative.DocumentDB.MongoDBResourceMongoRoleDefinition("mongoDBResourceMongoRoleDefinition", new()
    {
        AccountName = "myAccountName",
        DatabaseName = "sales",
        MongoRoleDefinitionId = "myMongoRoleDefinitionId",
        Privileges = new[]
        {
            new AzureNative.DocumentDB.Inputs.PrivilegeArgs
            {
                Actions = new[]
                {
                    "insert",
                    "find",
                },
                Resource = new AzureNative.DocumentDB.Inputs.PrivilegeResourceArgs
                {
                    Collection = "sales",
                    Db = "sales",
                },
            },
        },
        ResourceGroupName = "myResourceGroupName",
        RoleName = "myRoleName",
        Roles = new[]
        {
            new AzureNative.DocumentDB.Inputs.RoleArgs
            {
                Db = "sales",
                Role = "myInheritedRole",
            },
        },
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
		_, err := documentdb.NewMongoDBResourceMongoRoleDefinition(ctx, "mongoDBResourceMongoRoleDefinition", &documentdb.MongoDBResourceMongoRoleDefinitionArgs{
			AccountName:           pulumi.String("myAccountName"),
			DatabaseName:          pulumi.String("sales"),
			MongoRoleDefinitionId: pulumi.String("myMongoRoleDefinitionId"),
			Privileges: []documentdb.PrivilegeArgs{
				{
					Actions: pulumi.StringArray{
						pulumi.String("insert"),
						pulumi.String("find"),
					},
					Resource: {
						Collection: pulumi.String("sales"),
						Db:         pulumi.String("sales"),
					},
				},
			},
			ResourceGroupName: pulumi.String("myResourceGroupName"),
			RoleName:          pulumi.String("myRoleName"),
			Roles: []documentdb.RoleArgs{
				{
					Db:   pulumi.String("sales"),
					Role: pulumi.String("myInheritedRole"),
				},
			},
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
import com.pulumi.azurenative.documentdb.MongoDBResourceMongoRoleDefinition;
import com.pulumi.azurenative.documentdb.MongoDBResourceMongoRoleDefinitionArgs;
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
        var mongoDBResourceMongoRoleDefinition = new MongoDBResourceMongoRoleDefinition("mongoDBResourceMongoRoleDefinition", MongoDBResourceMongoRoleDefinitionArgs.builder()        
            .accountName("myAccountName")
            .databaseName("sales")
            .mongoRoleDefinitionId("myMongoRoleDefinitionId")
            .privileges(Map.ofEntries(
                Map.entry("actions",                 
                    "insert",
                    "find"),
                Map.entry("resource", Map.ofEntries(
                    Map.entry("collection", "sales"),
                    Map.entry("db", "sales")
                ))
            ))
            .resourceGroupName("myResourceGroupName")
            .roleName("myRoleName")
            .roles(Map.ofEntries(
                Map.entry("db", "sales"),
                Map.entry("role", "myInheritedRole")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const mongoDBResourceMongoRoleDefinition = new azure_native.documentdb.MongoDBResourceMongoRoleDefinition("mongoDBResourceMongoRoleDefinition", {
    accountName: "myAccountName",
    databaseName: "sales",
    mongoRoleDefinitionId: "myMongoRoleDefinitionId",
    privileges: [{
        actions: [
            "insert",
            "find",
        ],
        resource: {
            collection: "sales",
            db: "sales",
        },
    }],
    resourceGroupName: "myResourceGroupName",
    roleName: "myRoleName",
    roles: [{
        db: "sales",
        role: "myInheritedRole",
    }],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

mongo_db_resource_mongo_role_definition = azure_native.documentdb.MongoDBResourceMongoRoleDefinition("mongoDBResourceMongoRoleDefinition",
    account_name="myAccountName",
    database_name="sales",
    mongo_role_definition_id="myMongoRoleDefinitionId",
    privileges=[{
        "actions": [
            "insert",
            "find",
        ],
        "resource": azure_native.documentdb.PrivilegeResourceArgs(
            collection="sales",
            db="sales",
        ),
    }],
    resource_group_name="myResourceGroupName",
    role_name="myRoleName",
    roles=[azure_native.documentdb.RoleArgs(
        db="sales",
        role="myInheritedRole",
    )])

```

```yaml
resources:
  mongoDBResourceMongoRoleDefinition:
    type: azure-native:documentdb:MongoDBResourceMongoRoleDefinition
    properties:
      accountName: myAccountName
      databaseName: sales
      mongoRoleDefinitionId: myMongoRoleDefinitionId
      privileges:
        - actions:
            - insert
            - find
          resource:
            collection: sales
            db: sales
      resourceGroupName: myResourceGroupName
      roleName: myRoleName
      roles:
        - db: sales
          role: myInheritedRole

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:documentdb:MongoDBResourceMongoRoleDefinition myMongoDbRoleDefinitionId /subscriptions/mySubscriptionId/resourceGroups/myResourceGroupName/providers/Microsoft.DocumentDB/databaseAccounts/myAccountName/mongodbRoleDefinitions/myMongoDbRoleDefinitionId 
```
