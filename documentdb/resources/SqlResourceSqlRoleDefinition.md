An Azure Cosmos DB SQL Role Definition.
API Version: 2022-11-15.
Previous API Version: 2021-03-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CosmosDBSqlRoleDefinitionCreateUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sqlResourceSqlRoleDefinition = new AzureNative.DocumentDB.SqlResourceSqlRoleDefinition("sqlResourceSqlRoleDefinition", new()
    {
        AccountName = "myAccountName",
        AssignableScopes = new[]
        {
            "/subscriptions/mySubscriptionId/resourceGroups/myResourceGroupName/providers/Microsoft.DocumentDB/databaseAccounts/myAccountName/dbs/sales",
            "/subscriptions/mySubscriptionId/resourceGroups/myResourceGroupName/providers/Microsoft.DocumentDB/databaseAccounts/myAccountName/dbs/purchases",
        },
        Permissions = new[]
        {
            new AzureNative.DocumentDB.Inputs.PermissionArgs
            {
                DataActions = new[]
                {
                    "Microsoft.DocumentDB/databaseAccounts/sqlDatabases/containers/items/create",
                    "Microsoft.DocumentDB/databaseAccounts/sqlDatabases/containers/items/read",
                },
                NotDataActions = new[] {},
            },
        },
        ResourceGroupName = "myResourceGroupName",
        RoleDefinitionId = "myRoleDefinitionId",
        RoleName = "myRoleName",
        Type = AzureNative.DocumentDB.RoleDefinitionType.CustomRole,
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
		_, err := documentdb.NewSqlResourceSqlRoleDefinition(ctx, "sqlResourceSqlRoleDefinition", &documentdb.SqlResourceSqlRoleDefinitionArgs{
			AccountName: pulumi.String("myAccountName"),
			AssignableScopes: pulumi.StringArray{
				pulumi.String("/subscriptions/mySubscriptionId/resourceGroups/myResourceGroupName/providers/Microsoft.DocumentDB/databaseAccounts/myAccountName/dbs/sales"),
				pulumi.String("/subscriptions/mySubscriptionId/resourceGroups/myResourceGroupName/providers/Microsoft.DocumentDB/databaseAccounts/myAccountName/dbs/purchases"),
			},
			Permissions: []documentdb.PermissionArgs{
				{
					DataActions: pulumi.StringArray{
						pulumi.String("Microsoft.DocumentDB/databaseAccounts/sqlDatabases/containers/items/create"),
						pulumi.String("Microsoft.DocumentDB/databaseAccounts/sqlDatabases/containers/items/read"),
					},
					NotDataActions: pulumi.StringArray{},
				},
			},
			ResourceGroupName: pulumi.String("myResourceGroupName"),
			RoleDefinitionId:  pulumi.String("myRoleDefinitionId"),
			RoleName:          pulumi.String("myRoleName"),
			Type:              documentdb.RoleDefinitionTypeCustomRole,
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
import com.pulumi.azurenative.documentdb.SqlResourceSqlRoleDefinition;
import com.pulumi.azurenative.documentdb.SqlResourceSqlRoleDefinitionArgs;
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
        var sqlResourceSqlRoleDefinition = new SqlResourceSqlRoleDefinition("sqlResourceSqlRoleDefinition", SqlResourceSqlRoleDefinitionArgs.builder()        
            .accountName("myAccountName")
            .assignableScopes(            
                "/subscriptions/mySubscriptionId/resourceGroups/myResourceGroupName/providers/Microsoft.DocumentDB/databaseAccounts/myAccountName/dbs/sales",
                "/subscriptions/mySubscriptionId/resourceGroups/myResourceGroupName/providers/Microsoft.DocumentDB/databaseAccounts/myAccountName/dbs/purchases")
            .permissions(Map.ofEntries(
                Map.entry("dataActions",                 
                    "Microsoft.DocumentDB/databaseAccounts/sqlDatabases/containers/items/create",
                    "Microsoft.DocumentDB/databaseAccounts/sqlDatabases/containers/items/read"),
                Map.entry("notDataActions", )
            ))
            .resourceGroupName("myResourceGroupName")
            .roleDefinitionId("myRoleDefinitionId")
            .roleName("myRoleName")
            .type("CustomRole")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sqlResourceSqlRoleDefinition = new azure_native.documentdb.SqlResourceSqlRoleDefinition("sqlResourceSqlRoleDefinition", {
    accountName: "myAccountName",
    assignableScopes: [
        "/subscriptions/mySubscriptionId/resourceGroups/myResourceGroupName/providers/Microsoft.DocumentDB/databaseAccounts/myAccountName/dbs/sales",
        "/subscriptions/mySubscriptionId/resourceGroups/myResourceGroupName/providers/Microsoft.DocumentDB/databaseAccounts/myAccountName/dbs/purchases",
    ],
    permissions: [{
        dataActions: [
            "Microsoft.DocumentDB/databaseAccounts/sqlDatabases/containers/items/create",
            "Microsoft.DocumentDB/databaseAccounts/sqlDatabases/containers/items/read",
        ],
        notDataActions: [],
    }],
    resourceGroupName: "myResourceGroupName",
    roleDefinitionId: "myRoleDefinitionId",
    roleName: "myRoleName",
    type: azure_native.documentdb.RoleDefinitionType.CustomRole,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sql_resource_sql_role_definition = azure_native.documentdb.SqlResourceSqlRoleDefinition("sqlResourceSqlRoleDefinition",
    account_name="myAccountName",
    assignable_scopes=[
        "/subscriptions/mySubscriptionId/resourceGroups/myResourceGroupName/providers/Microsoft.DocumentDB/databaseAccounts/myAccountName/dbs/sales",
        "/subscriptions/mySubscriptionId/resourceGroups/myResourceGroupName/providers/Microsoft.DocumentDB/databaseAccounts/myAccountName/dbs/purchases",
    ],
    permissions=[azure_native.documentdb.PermissionArgs(
        data_actions=[
            "Microsoft.DocumentDB/databaseAccounts/sqlDatabases/containers/items/create",
            "Microsoft.DocumentDB/databaseAccounts/sqlDatabases/containers/items/read",
        ],
        not_data_actions=[],
    )],
    resource_group_name="myResourceGroupName",
    role_definition_id="myRoleDefinitionId",
    role_name="myRoleName",
    type=azure_native.documentdb.RoleDefinitionType.CUSTOM_ROLE)

```

```yaml
resources:
  sqlResourceSqlRoleDefinition:
    type: azure-native:documentdb:SqlResourceSqlRoleDefinition
    properties:
      accountName: myAccountName
      assignableScopes:
        - /subscriptions/mySubscriptionId/resourceGroups/myResourceGroupName/providers/Microsoft.DocumentDB/databaseAccounts/myAccountName/dbs/sales
        - /subscriptions/mySubscriptionId/resourceGroups/myResourceGroupName/providers/Microsoft.DocumentDB/databaseAccounts/myAccountName/dbs/purchases
      permissions:
        - dataActions:
            - Microsoft.DocumentDB/databaseAccounts/sqlDatabases/containers/items/create
            - Microsoft.DocumentDB/databaseAccounts/sqlDatabases/containers/items/read
          notDataActions: []
      resourceGroupName: myResourceGroupName
      roleDefinitionId: myRoleDefinitionId
      roleName: myRoleName
      type: CustomRole

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:documentdb:SqlResourceSqlRoleDefinition myRoleDefinitionId /subscriptions/mySubscriptionId/resourceGroups/myResourceGroupName/providers/Microsoft.DocumentDB/databaseAccounts/myAccountName/sqlRoleDefinitions/myRoleDefinitionId 
```
