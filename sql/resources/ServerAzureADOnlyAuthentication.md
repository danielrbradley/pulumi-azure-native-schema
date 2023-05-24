Azure Active Directory only authentication.
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates or updates Azure Active Directory only authentication object.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var serverAzureADOnlyAuthentication = new AzureNative.Sql.ServerAzureADOnlyAuthentication("serverAzureADOnlyAuthentication", new()
    {
        AuthenticationName = "Default",
        AzureADOnlyAuthentication = false,
        ResourceGroupName = "sqlcrudtest-4799",
        ServerName = "sqlcrudtest-6440",
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
		_, err := sql.NewServerAzureADOnlyAuthentication(ctx, "serverAzureADOnlyAuthentication", &sql.ServerAzureADOnlyAuthenticationArgs{
			AuthenticationName:        pulumi.String("Default"),
			AzureADOnlyAuthentication: pulumi.Bool(false),
			ResourceGroupName:         pulumi.String("sqlcrudtest-4799"),
			ServerName:                pulumi.String("sqlcrudtest-6440"),
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
import com.pulumi.azurenative.sql.ServerAzureADOnlyAuthentication;
import com.pulumi.azurenative.sql.ServerAzureADOnlyAuthenticationArgs;
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
        var serverAzureADOnlyAuthentication = new ServerAzureADOnlyAuthentication("serverAzureADOnlyAuthentication", ServerAzureADOnlyAuthenticationArgs.builder()        
            .authenticationName("Default")
            .azureADOnlyAuthentication(false)
            .resourceGroupName("sqlcrudtest-4799")
            .serverName("sqlcrudtest-6440")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const serverAzureADOnlyAuthentication = new azure_native.sql.ServerAzureADOnlyAuthentication("serverAzureADOnlyAuthentication", {
    authenticationName: "Default",
    azureADOnlyAuthentication: false,
    resourceGroupName: "sqlcrudtest-4799",
    serverName: "sqlcrudtest-6440",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

server_azure_ad_only_authentication = azure_native.sql.ServerAzureADOnlyAuthentication("serverAzureADOnlyAuthentication",
    authentication_name="Default",
    azure_ad_only_authentication=False,
    resource_group_name="sqlcrudtest-4799",
    server_name="sqlcrudtest-6440")

```

```yaml
resources:
  serverAzureADOnlyAuthentication:
    type: azure-native:sql:ServerAzureADOnlyAuthentication
    properties:
      authenticationName: Default
      azureADOnlyAuthentication: false
      resourceGroupName: sqlcrudtest-4799
      serverName: sqlcrudtest-6440

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:ServerAzureADOnlyAuthentication Default /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/sqlcrudtest-4799/providers/Microsoft.Sql/servers/sqlcrudtest-6440/azureadonlyauthentications/default 
```
