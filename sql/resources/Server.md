An Azure SQL Database server.
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create server
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var server = new AzureNative.Sql.Server("server", new()
    {
        AdministratorLogin = "dummylogin",
        AdministratorLoginPassword = "PLACEHOLDER",
        Administrators = new AzureNative.Sql.Inputs.ServerExternalAdministratorArgs
        {
            AzureADOnlyAuthentication = true,
            Login = "bob@contoso.com",
            PrincipalType = "User",
            Sid = "00000011-1111-2222-2222-123456789111",
            TenantId = "00000011-1111-2222-2222-123456789111",
        },
        Location = "Japan East",
        PublicNetworkAccess = "Enabled",
        ResourceGroupName = "sqlcrudtest-7398",
        RestrictOutboundNetworkAccess = "Enabled",
        ServerName = "sqlcrudtest-4645",
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
		_, err := sql.NewServer(ctx, "server", &sql.ServerArgs{
			AdministratorLogin:         pulumi.String("dummylogin"),
			AdministratorLoginPassword: pulumi.String("PLACEHOLDER"),
			Administrators: &sql.ServerExternalAdministratorArgs{
				AzureADOnlyAuthentication: pulumi.Bool(true),
				Login:                     pulumi.String("bob@contoso.com"),
				PrincipalType:             pulumi.String("User"),
				Sid:                       pulumi.String("00000011-1111-2222-2222-123456789111"),
				TenantId:                  pulumi.String("00000011-1111-2222-2222-123456789111"),
			},
			Location:                      pulumi.String("Japan East"),
			PublicNetworkAccess:           pulumi.String("Enabled"),
			ResourceGroupName:             pulumi.String("sqlcrudtest-7398"),
			RestrictOutboundNetworkAccess: pulumi.String("Enabled"),
			ServerName:                    pulumi.String("sqlcrudtest-4645"),
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
import com.pulumi.azurenative.sql.Server;
import com.pulumi.azurenative.sql.ServerArgs;
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
        var server = new Server("server", ServerArgs.builder()        
            .administratorLogin("dummylogin")
            .administratorLoginPassword("PLACEHOLDER")
            .administrators(Map.ofEntries(
                Map.entry("azureADOnlyAuthentication", true),
                Map.entry("login", "bob@contoso.com"),
                Map.entry("principalType", "User"),
                Map.entry("sid", "00000011-1111-2222-2222-123456789111"),
                Map.entry("tenantId", "00000011-1111-2222-2222-123456789111")
            ))
            .location("Japan East")
            .publicNetworkAccess("Enabled")
            .resourceGroupName("sqlcrudtest-7398")
            .restrictOutboundNetworkAccess("Enabled")
            .serverName("sqlcrudtest-4645")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const server = new azure_native.sql.Server("server", {
    administratorLogin: "dummylogin",
    administratorLoginPassword: "PLACEHOLDER",
    administrators: {
        azureADOnlyAuthentication: true,
        login: "bob@contoso.com",
        principalType: "User",
        sid: "00000011-1111-2222-2222-123456789111",
        tenantId: "00000011-1111-2222-2222-123456789111",
    },
    location: "Japan East",
    publicNetworkAccess: "Enabled",
    resourceGroupName: "sqlcrudtest-7398",
    restrictOutboundNetworkAccess: "Enabled",
    serverName: "sqlcrudtest-4645",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

server = azure_native.sql.Server("server",
    administrator_login="dummylogin",
    administrator_login_password="PLACEHOLDER",
    administrators=azure_native.sql.ServerExternalAdministratorArgs(
        azure_ad_only_authentication=True,
        login="bob@contoso.com",
        principal_type="User",
        sid="00000011-1111-2222-2222-123456789111",
        tenant_id="00000011-1111-2222-2222-123456789111",
    ),
    location="Japan East",
    public_network_access="Enabled",
    resource_group_name="sqlcrudtest-7398",
    restrict_outbound_network_access="Enabled",
    server_name="sqlcrudtest-4645")

```

```yaml
resources:
  server:
    type: azure-native:sql:Server
    properties:
      administratorLogin: dummylogin
      administratorLoginPassword: PLACEHOLDER
      administrators:
        azureADOnlyAuthentication: true
        login: bob@contoso.com
        principalType: User
        sid: 00000011-1111-2222-2222-123456789111
        tenantId: 00000011-1111-2222-2222-123456789111
      location: Japan East
      publicNetworkAccess: Enabled
      resourceGroupName: sqlcrudtest-7398
      restrictOutboundNetworkAccess: Enabled
      serverName: sqlcrudtest-4645

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:Server sqlcrudtest-4645 /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/sqlcrudtest-7398/providers/Microsoft.Sql/servers/sqlcrudtest-4645 
```
