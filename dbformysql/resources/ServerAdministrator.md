Represents a and external administrator to be created.
API Version: 2017-12-01.
Previous API Version: 2017-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ServerAdministratorCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var serverAdministrator = new AzureNative.DBforMySQL.ServerAdministrator("serverAdministrator", new()
    {
        AdministratorType = "ActiveDirectory",
        Login = "bob@contoso.com",
        ResourceGroupName = "testrg",
        ServerName = "mysqltestsvc4",
        Sid = "c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c",
        TenantId = "c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c",
    });

});


```

```go
package main

import (
	dbformysql "github.com/pulumi/pulumi-azure-native-sdk/dbformysql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := dbformysql.NewServerAdministrator(ctx, "serverAdministrator", &dbformysql.ServerAdministratorArgs{
			AdministratorType: pulumi.String("ActiveDirectory"),
			Login:             pulumi.String("bob@contoso.com"),
			ResourceGroupName: pulumi.String("testrg"),
			ServerName:        pulumi.String("mysqltestsvc4"),
			Sid:               pulumi.String("c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c"),
			TenantId:          pulumi.String("c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c"),
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
import com.pulumi.azurenative.dbformysql.ServerAdministrator;
import com.pulumi.azurenative.dbformysql.ServerAdministratorArgs;
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
        var serverAdministrator = new ServerAdministrator("serverAdministrator", ServerAdministratorArgs.builder()        
            .administratorType("ActiveDirectory")
            .login("bob@contoso.com")
            .resourceGroupName("testrg")
            .serverName("mysqltestsvc4")
            .sid("c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c")
            .tenantId("c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const serverAdministrator = new azure_native.dbformysql.ServerAdministrator("serverAdministrator", {
    administratorType: "ActiveDirectory",
    login: "bob@contoso.com",
    resourceGroupName: "testrg",
    serverName: "mysqltestsvc4",
    sid: "c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c",
    tenantId: "c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

server_administrator = azure_native.dbformysql.ServerAdministrator("serverAdministrator",
    administrator_type="ActiveDirectory",
    login="bob@contoso.com",
    resource_group_name="testrg",
    server_name="mysqltestsvc4",
    sid="c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c",
    tenant_id="c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c")

```

```yaml
resources:
  serverAdministrator:
    type: azure-native:dbformysql:ServerAdministrator
    properties:
      administratorType: ActiveDirectory
      login: bob@contoso.com
      resourceGroupName: testrg
      serverName: mysqltestsvc4
      sid: c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c
      tenantId: c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:dbformysql:ServerAdministrator activeDirectory /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.DBforMySQL/servers/mysqltestsvc4/administrators/activeDirectory 
```
