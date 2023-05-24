An Azure Cosmos DB Role Assignment
API Version: 2022-11-15.
Previous API Version: 2021-03-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CosmosDBSqlRoleAssignmentCreateUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sqlResourceSqlRoleAssignment = new AzureNative.DocumentDB.SqlResourceSqlRoleAssignment("sqlResourceSqlRoleAssignment", new()
    {
        AccountName = "myAccountName",
        PrincipalId = "myPrincipalId",
        ResourceGroupName = "myResourceGroupName",
        RoleAssignmentId = "myRoleAssignmentId",
        RoleDefinitionId = "/subscriptions/mySubscriptionId/resourceGroups/myResourceGroupName/providers/Microsoft.DocumentDB/databaseAccounts/myAccountName/sqlRoleDefinitions/myRoleDefinitionId",
        Scope = "/subscriptions/mySubscriptionId/resourceGroups/myResourceGroupName/providers/Microsoft.DocumentDB/databaseAccounts/myAccountName/dbs/purchases/colls/redmond-purchases",
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
		_, err := documentdb.NewSqlResourceSqlRoleAssignment(ctx, "sqlResourceSqlRoleAssignment", &documentdb.SqlResourceSqlRoleAssignmentArgs{
			AccountName:       pulumi.String("myAccountName"),
			PrincipalId:       pulumi.String("myPrincipalId"),
			ResourceGroupName: pulumi.String("myResourceGroupName"),
			RoleAssignmentId:  pulumi.String("myRoleAssignmentId"),
			RoleDefinitionId:  pulumi.String("/subscriptions/mySubscriptionId/resourceGroups/myResourceGroupName/providers/Microsoft.DocumentDB/databaseAccounts/myAccountName/sqlRoleDefinitions/myRoleDefinitionId"),
			Scope:             pulumi.String("/subscriptions/mySubscriptionId/resourceGroups/myResourceGroupName/providers/Microsoft.DocumentDB/databaseAccounts/myAccountName/dbs/purchases/colls/redmond-purchases"),
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
import com.pulumi.azurenative.documentdb.SqlResourceSqlRoleAssignment;
import com.pulumi.azurenative.documentdb.SqlResourceSqlRoleAssignmentArgs;
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
        var sqlResourceSqlRoleAssignment = new SqlResourceSqlRoleAssignment("sqlResourceSqlRoleAssignment", SqlResourceSqlRoleAssignmentArgs.builder()        
            .accountName("myAccountName")
            .principalId("myPrincipalId")
            .resourceGroupName("myResourceGroupName")
            .roleAssignmentId("myRoleAssignmentId")
            .roleDefinitionId("/subscriptions/mySubscriptionId/resourceGroups/myResourceGroupName/providers/Microsoft.DocumentDB/databaseAccounts/myAccountName/sqlRoleDefinitions/myRoleDefinitionId")
            .scope("/subscriptions/mySubscriptionId/resourceGroups/myResourceGroupName/providers/Microsoft.DocumentDB/databaseAccounts/myAccountName/dbs/purchases/colls/redmond-purchases")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sqlResourceSqlRoleAssignment = new azure_native.documentdb.SqlResourceSqlRoleAssignment("sqlResourceSqlRoleAssignment", {
    accountName: "myAccountName",
    principalId: "myPrincipalId",
    resourceGroupName: "myResourceGroupName",
    roleAssignmentId: "myRoleAssignmentId",
    roleDefinitionId: "/subscriptions/mySubscriptionId/resourceGroups/myResourceGroupName/providers/Microsoft.DocumentDB/databaseAccounts/myAccountName/sqlRoleDefinitions/myRoleDefinitionId",
    scope: "/subscriptions/mySubscriptionId/resourceGroups/myResourceGroupName/providers/Microsoft.DocumentDB/databaseAccounts/myAccountName/dbs/purchases/colls/redmond-purchases",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sql_resource_sql_role_assignment = azure_native.documentdb.SqlResourceSqlRoleAssignment("sqlResourceSqlRoleAssignment",
    account_name="myAccountName",
    principal_id="myPrincipalId",
    resource_group_name="myResourceGroupName",
    role_assignment_id="myRoleAssignmentId",
    role_definition_id="/subscriptions/mySubscriptionId/resourceGroups/myResourceGroupName/providers/Microsoft.DocumentDB/databaseAccounts/myAccountName/sqlRoleDefinitions/myRoleDefinitionId",
    scope="/subscriptions/mySubscriptionId/resourceGroups/myResourceGroupName/providers/Microsoft.DocumentDB/databaseAccounts/myAccountName/dbs/purchases/colls/redmond-purchases")

```

```yaml
resources:
  sqlResourceSqlRoleAssignment:
    type: azure-native:documentdb:SqlResourceSqlRoleAssignment
    properties:
      accountName: myAccountName
      principalId: myPrincipalId
      resourceGroupName: myResourceGroupName
      roleAssignmentId: myRoleAssignmentId
      roleDefinitionId: /subscriptions/mySubscriptionId/resourceGroups/myResourceGroupName/providers/Microsoft.DocumentDB/databaseAccounts/myAccountName/sqlRoleDefinitions/myRoleDefinitionId
      scope: /subscriptions/mySubscriptionId/resourceGroups/myResourceGroupName/providers/Microsoft.DocumentDB/databaseAccounts/myAccountName/dbs/purchases/colls/redmond-purchases

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:documentdb:SqlResourceSqlRoleAssignment myRoleAssignmentId /subscriptions/mySubscriptionId/resourceGroups/myResourceGroupName/providers/Microsoft.DocumentDB/databaseAccounts/myAccountName/sqlRoleAssignments/myRoleAssignmentId 
```
