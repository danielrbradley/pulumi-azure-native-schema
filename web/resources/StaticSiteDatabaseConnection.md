Static Site Database Connection resource.
API Version: 2022-09-01.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a database connection for a static site
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var staticSiteDatabaseConnection = new AzureNative.Web.StaticSiteDatabaseConnection("staticSiteDatabaseConnection", new()
    {
        ConnectionIdentity = "SystemAssigned",
        ConnectionString = "AccountEndpoint=https://exampleDatabaseName.documents.azure.com:443/;Database=mydb;",
        DatabaseConnectionName = "default",
        Name = "testStaticSite0",
        Region = "West US 2",
        ResourceGroupName = "rg",
        ResourceId = "/subscription/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/databaseRG/providers/Microsoft.DocumentDB/databaseAccounts/exampleDatabaseName",
    });

});


```

```go
package main

import (
	web "github.com/pulumi/pulumi-azure-native-sdk/web"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := web.NewStaticSiteDatabaseConnection(ctx, "staticSiteDatabaseConnection", &web.StaticSiteDatabaseConnectionArgs{
			ConnectionIdentity:     pulumi.String("SystemAssigned"),
			ConnectionString:       pulumi.String("AccountEndpoint=https://exampleDatabaseName.documents.azure.com:443/;Database=mydb;"),
			DatabaseConnectionName: pulumi.String("default"),
			Name:                   pulumi.String("testStaticSite0"),
			Region:                 pulumi.String("West US 2"),
			ResourceGroupName:      pulumi.String("rg"),
			ResourceId:             pulumi.String("/subscription/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/databaseRG/providers/Microsoft.DocumentDB/databaseAccounts/exampleDatabaseName"),
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
import com.pulumi.azurenative.web.StaticSiteDatabaseConnection;
import com.pulumi.azurenative.web.StaticSiteDatabaseConnectionArgs;
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
        var staticSiteDatabaseConnection = new StaticSiteDatabaseConnection("staticSiteDatabaseConnection", StaticSiteDatabaseConnectionArgs.builder()        
            .connectionIdentity("SystemAssigned")
            .connectionString("AccountEndpoint=https://exampleDatabaseName.documents.azure.com:443/;Database=mydb;")
            .databaseConnectionName("default")
            .name("testStaticSite0")
            .region("West US 2")
            .resourceGroupName("rg")
            .resourceId("/subscription/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/databaseRG/providers/Microsoft.DocumentDB/databaseAccounts/exampleDatabaseName")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const staticSiteDatabaseConnection = new azure_native.web.StaticSiteDatabaseConnection("staticSiteDatabaseConnection", {
    connectionIdentity: "SystemAssigned",
    connectionString: "AccountEndpoint=https://exampleDatabaseName.documents.azure.com:443/;Database=mydb;",
    databaseConnectionName: "default",
    name: "testStaticSite0",
    region: "West US 2",
    resourceGroupName: "rg",
    resourceId: "/subscription/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/databaseRG/providers/Microsoft.DocumentDB/databaseAccounts/exampleDatabaseName",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

static_site_database_connection = azure_native.web.StaticSiteDatabaseConnection("staticSiteDatabaseConnection",
    connection_identity="SystemAssigned",
    connection_string="AccountEndpoint=https://exampleDatabaseName.documents.azure.com:443/;Database=mydb;",
    database_connection_name="default",
    name="testStaticSite0",
    region="West US 2",
    resource_group_name="rg",
    resource_id="/subscription/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/databaseRG/providers/Microsoft.DocumentDB/databaseAccounts/exampleDatabaseName")

```

```yaml
resources:
  staticSiteDatabaseConnection:
    type: azure-native:web:StaticSiteDatabaseConnection
    properties:
      connectionIdentity: SystemAssigned
      connectionString: AccountEndpoint=https://exampleDatabaseName.documents.azure.com:443/;Database=mydb;
      databaseConnectionName: default
      name: testStaticSite0
      region: West US 2
      resourceGroupName: rg
      resourceId: /subscription/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/databaseRG/providers/Microsoft.DocumentDB/databaseAccounts/exampleDatabaseName

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:web:StaticSiteDatabaseConnection default /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/rg/providers/Microsoft.Web/staticSites/testStaticSite0/databaseConnections/default 
```
