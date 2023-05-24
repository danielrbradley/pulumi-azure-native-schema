A SQL server.
API Version: 2019-07-24-preview.
Previous API Version: 2019-07-24-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates or updates a SQL Server in a Registration group.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sqlServer = new AzureNative.AzureData.SqlServer("sqlServer", new()
    {
        Cores = 8,
        Edition = "Latin",
        PropertyBag = "",
        RegistrationID = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.AzureData/SqlServerRegistrations/testsqlregistration",
        ResourceGroupName = "testrg",
        SqlServerName = "testsqlserver",
        SqlServerRegistrationName = "testsqlregistration",
        Version = "2008",
    });

});


```

```go
package main

import (
	azuredata "github.com/pulumi/pulumi-azure-native-sdk/azuredata"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := azuredata.NewSqlServer(ctx, "sqlServer", &azuredata.SqlServerArgs{
			Cores:                     pulumi.Int(8),
			Edition:                   pulumi.String("Latin"),
			PropertyBag:               pulumi.String(""),
			RegistrationID:            pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.AzureData/SqlServerRegistrations/testsqlregistration"),
			ResourceGroupName:         pulumi.String("testrg"),
			SqlServerName:             pulumi.String("testsqlserver"),
			SqlServerRegistrationName: pulumi.String("testsqlregistration"),
			Version:                   pulumi.String("2008"),
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
import com.pulumi.azurenative.azuredata.SqlServer;
import com.pulumi.azurenative.azuredata.SqlServerArgs;
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
        var sqlServer = new SqlServer("sqlServer", SqlServerArgs.builder()        
            .cores(8)
            .edition("Latin")
            .propertyBag("")
            .registrationID("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.AzureData/SqlServerRegistrations/testsqlregistration")
            .resourceGroupName("testrg")
            .sqlServerName("testsqlserver")
            .sqlServerRegistrationName("testsqlregistration")
            .version("2008")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sqlServer = new azure_native.azuredata.SqlServer("sqlServer", {
    cores: 8,
    edition: "Latin",
    propertyBag: "",
    registrationID: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.AzureData/SqlServerRegistrations/testsqlregistration",
    resourceGroupName: "testrg",
    sqlServerName: "testsqlserver",
    sqlServerRegistrationName: "testsqlregistration",
    version: "2008",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sql_server = azure_native.azuredata.SqlServer("sqlServer",
    cores=8,
    edition="Latin",
    property_bag="",
    registration_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.AzureData/SqlServerRegistrations/testsqlregistration",
    resource_group_name="testrg",
    sql_server_name="testsqlserver",
    sql_server_registration_name="testsqlregistration",
    version="2008")

```

```yaml
resources:
  sqlServer:
    type: azure-native:azuredata:SqlServer
    properties:
      cores: 8
      edition: Latin
      propertyBag:
      registrationID: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.AzureData/SqlServerRegistrations/testsqlregistration
      resourceGroupName: testrg
      sqlServerName: testsqlserver
      sqlServerRegistrationName: testsqlregistration
      version: '2008'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:azuredata:SqlServer testsqlserver /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.AzureData/SqlServerRegistrations/testsqlregistration/sqlServers/testsqlserver 
```
