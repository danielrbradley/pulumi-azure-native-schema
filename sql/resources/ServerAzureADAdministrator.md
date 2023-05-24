Azure Active Directory administrator.
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates or updates an existing Azure Active Directory administrator.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var serverAzureADAdministrator = new AzureNative.Sql.ServerAzureADAdministrator("serverAzureADAdministrator", new()
    {
        AdministratorName = "ActiveDirectory",
        AdministratorType = "ActiveDirectory",
        Login = "bob@contoso.com",
        ResourceGroupName = "sqlcrudtest-4799",
        ServerName = "sqlcrudtest-6440",
        Sid = "c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c",
        TenantId = "c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c",
    });

});


```

```go
package main

import (
	sql "github.com/pulumi/pulumi-azure-native-sdk/sql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := sql.NewServerAzureADAdministrator(ctx, "serverAzureADAdministrator", &sql.ServerAzureADAdministratorArgs{
			AdministratorName: pulumi.String("ActiveDirectory"),
			AdministratorType: pulumi.String("ActiveDirectory"),
			Login:             pulumi.String("bob@contoso.com"),
			ResourceGroupName: pulumi.String("sqlcrudtest-4799"),
			ServerName:        pulumi.String("sqlcrudtest-6440"),
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
import com.pulumi.azurenative.sql.ServerAzureADAdministrator;
import com.pulumi.azurenative.sql.ServerAzureADAdministratorArgs;
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
        var serverAzureADAdministrator = new ServerAzureADAdministrator("serverAzureADAdministrator", ServerAzureADAdministratorArgs.builder()        
            .administratorName("ActiveDirectory")
            .administratorType("ActiveDirectory")
            .login("bob@contoso.com")
            .resourceGroupName("sqlcrudtest-4799")
            .serverName("sqlcrudtest-6440")
            .sid("c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c")
            .tenantId("c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const serverAzureADAdministrator = new azure_native.sql.ServerAzureADAdministrator("serverAzureADAdministrator", {
    administratorName: "ActiveDirectory",
    administratorType: "ActiveDirectory",
    login: "bob@contoso.com",
    resourceGroupName: "sqlcrudtest-4799",
    serverName: "sqlcrudtest-6440",
    sid: "c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c",
    tenantId: "c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

server_azure_ad_administrator = azure_native.sql.ServerAzureADAdministrator("serverAzureADAdministrator",
    administrator_name="ActiveDirectory",
    administrator_type="ActiveDirectory",
    login="bob@contoso.com",
    resource_group_name="sqlcrudtest-4799",
    server_name="sqlcrudtest-6440",
    sid="c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c",
    tenant_id="c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c")

```

```yaml
resources:
  serverAzureADAdministrator:
    type: azure-native:sql:ServerAzureADAdministrator
    properties:
      administratorName: ActiveDirectory
      administratorType: ActiveDirectory
      login: bob@contoso.com
      resourceGroupName: sqlcrudtest-4799
      serverName: sqlcrudtest-6440
      sid: c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c
      tenantId: c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:ServerAzureADAdministrator ActiveDirectory /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/sqlcrudtest-4799/providers/Microsoft.Sql/servers/sqlcrudtest-6440/administrators/ActiveDirectory 
```
