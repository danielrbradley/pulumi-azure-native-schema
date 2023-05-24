An Azure Cosmos DB User Definition
API Version: 2022-11-15.
Previous API Version: 2021-10-15-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CosmosDBMongoDBUserDefinitionCreateUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var mongoDBResourceMongoUserDefinition = new AzureNative.DocumentDB.MongoDBResourceMongoUserDefinition("mongoDBResourceMongoUserDefinition", new()
    {
        AccountName = "myAccountName",
        CustomData = "My custom data",
        DatabaseName = "sales",
        Mechanisms = "SCRAM-SHA-256",
        MongoUserDefinitionId = "myMongoUserDefinitionId",
        Password = "myPassword",
        ResourceGroupName = "myResourceGroupName",
        Roles = new[]
        {
            new AzureNative.DocumentDB.Inputs.RoleArgs
            {
                Db = "sales",
                Role = "myReadRole",
            },
        },
        UserName = "myUserName",
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
		_, err := documentdb.NewMongoDBResourceMongoUserDefinition(ctx, "mongoDBResourceMongoUserDefinition", &documentdb.MongoDBResourceMongoUserDefinitionArgs{
			AccountName:           pulumi.String("myAccountName"),
			CustomData:            pulumi.String("My custom data"),
			DatabaseName:          pulumi.String("sales"),
			Mechanisms:            pulumi.String("SCRAM-SHA-256"),
			MongoUserDefinitionId: pulumi.String("myMongoUserDefinitionId"),
			Password:              pulumi.String("myPassword"),
			ResourceGroupName:     pulumi.String("myResourceGroupName"),
			Roles: []documentdb.RoleArgs{
				{
					Db:   pulumi.String("sales"),
					Role: pulumi.String("myReadRole"),
				},
			},
			UserName: pulumi.String("myUserName"),
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
import com.pulumi.azurenative.documentdb.MongoDBResourceMongoUserDefinition;
import com.pulumi.azurenative.documentdb.MongoDBResourceMongoUserDefinitionArgs;
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
        var mongoDBResourceMongoUserDefinition = new MongoDBResourceMongoUserDefinition("mongoDBResourceMongoUserDefinition", MongoDBResourceMongoUserDefinitionArgs.builder()        
            .accountName("myAccountName")
            .customData("My custom data")
            .databaseName("sales")
            .mechanisms("SCRAM-SHA-256")
            .mongoUserDefinitionId("myMongoUserDefinitionId")
            .password("myPassword")
            .resourceGroupName("myResourceGroupName")
            .roles(Map.ofEntries(
                Map.entry("db", "sales"),
                Map.entry("role", "myReadRole")
            ))
            .userName("myUserName")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const mongoDBResourceMongoUserDefinition = new azure_native.documentdb.MongoDBResourceMongoUserDefinition("mongoDBResourceMongoUserDefinition", {
    accountName: "myAccountName",
    customData: "My custom data",
    databaseName: "sales",
    mechanisms: "SCRAM-SHA-256",
    mongoUserDefinitionId: "myMongoUserDefinitionId",
    password: "myPassword",
    resourceGroupName: "myResourceGroupName",
    roles: [{
        db: "sales",
        role: "myReadRole",
    }],
    userName: "myUserName",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

mongo_db_resource_mongo_user_definition = azure_native.documentdb.MongoDBResourceMongoUserDefinition("mongoDBResourceMongoUserDefinition",
    account_name="myAccountName",
    custom_data="My custom data",
    database_name="sales",
    mechanisms="SCRAM-SHA-256",
    mongo_user_definition_id="myMongoUserDefinitionId",
    password="myPassword",
    resource_group_name="myResourceGroupName",
    roles=[azure_native.documentdb.RoleArgs(
        db="sales",
        role="myReadRole",
    )],
    user_name="myUserName")

```

```yaml
resources:
  mongoDBResourceMongoUserDefinition:
    type: azure-native:documentdb:MongoDBResourceMongoUserDefinition
    properties:
      accountName: myAccountName
      customData: My custom data
      databaseName: sales
      mechanisms: SCRAM-SHA-256
      mongoUserDefinitionId: myMongoUserDefinitionId
      password: myPassword
      resourceGroupName: myResourceGroupName
      roles:
        - db: sales
          role: myReadRole
      userName: myUserName

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:documentdb:MongoDBResourceMongoUserDefinition myUserName /subscriptions/mySubscriptionId/resourceGroups/myResourceGroupName/providers/Microsoft.DocumentDB/databaseAccounts/myAccountName/mongodbUserDefinitions/myUserId 
```
