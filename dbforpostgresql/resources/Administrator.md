Represents an Active Directory administrator.
API Version: 2022-12-01.

{{% examples %}}
## Example Usage
{{% example %}}
### Adds an Active DIrectory Administrator for the server
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var administrator = new AzureNative.DBforPostgreSQL.Administrator("administrator", new()
    {
        ObjectId = "oooooooo-oooo-oooo-oooo-oooooooooooo",
        PrincipalName = "testuser1@microsoft.com",
        PrincipalType = "User",
        ResourceGroupName = "testrg",
        ServerName = "testserver",
        TenantId = "tttttttt-tttt-tttt-tttt-tttttttttttt",
    });

});


```

```go
package main

import (
	dbforpostgresql "github.com/pulumi/pulumi-azure-native-sdk/dbforpostgresql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := dbforpostgresql.NewAdministrator(ctx, "administrator", &dbforpostgresql.AdministratorArgs{
			ObjectId:          pulumi.String("oooooooo-oooo-oooo-oooo-oooooooooooo"),
			PrincipalName:     pulumi.String("testuser1@microsoft.com"),
			PrincipalType:     pulumi.String("User"),
			ResourceGroupName: pulumi.String("testrg"),
			ServerName:        pulumi.String("testserver"),
			TenantId:          pulumi.String("tttttttt-tttt-tttt-tttt-tttttttttttt"),
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
import com.pulumi.azurenative.dbforpostgresql.Administrator;
import com.pulumi.azurenative.dbforpostgresql.AdministratorArgs;
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
        var administrator = new Administrator("administrator", AdministratorArgs.builder()        
            .objectId("oooooooo-oooo-oooo-oooo-oooooooooooo")
            .principalName("testuser1@microsoft.com")
            .principalType("User")
            .resourceGroupName("testrg")
            .serverName("testserver")
            .tenantId("tttttttt-tttt-tttt-tttt-tttttttttttt")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const administrator = new azure_native.dbforpostgresql.Administrator("administrator", {
    objectId: "oooooooo-oooo-oooo-oooo-oooooooooooo",
    principalName: "testuser1@microsoft.com",
    principalType: "User",
    resourceGroupName: "testrg",
    serverName: "testserver",
    tenantId: "tttttttt-tttt-tttt-tttt-tttttttttttt",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

administrator = azure_native.dbforpostgresql.Administrator("administrator",
    object_id="oooooooo-oooo-oooo-oooo-oooooooooooo",
    principal_name="testuser1@microsoft.com",
    principal_type="User",
    resource_group_name="testrg",
    server_name="testserver",
    tenant_id="tttttttt-tttt-tttt-tttt-tttttttttttt")

```

```yaml
resources:
  administrator:
    type: azure-native:dbforpostgresql:Administrator
    properties:
      objectId: oooooooo-oooo-oooo-oooo-oooooooooooo
      principalName: testuser1@microsoft.com
      principalType: User
      resourceGroupName: testrg
      serverName: testserver
      tenantId: tttttttt-tttt-tttt-tttt-tttttttttttt

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:dbforpostgresql:Administrator testuser1@microsoft.com /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.DBforPostgreSQL/flexibleServers/testserver/administrators/oooooooo-oooo-oooo-oooo-oooooooooooo 
```
