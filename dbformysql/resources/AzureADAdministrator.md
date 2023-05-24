Represents a Administrator.
API Version: 2022-01-01.

{{% examples %}}
## Example Usage
{{% example %}}
### Create an azure ad administrator
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var azureADAdministrator = new AzureNative.DBforMySQL.AzureADAdministrator("azureADAdministrator", new()
    {
        AdministratorName = "ActiveDirectory",
        AdministratorType = "ActiveDirectory",
        IdentityResourceId = "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/test-group/providers/Microsoft.ManagedIdentity/userAssignedIdentities/test-umi",
        Login = "bob@contoso.com",
        ResourceGroupName = "testrg",
        ServerName = "mysqltestsvc4",
        Sid = "c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c",
        TenantId = "c12b7025-bfe2-46c1-b463-993b5e4cd467",
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
		_, err := dbformysql.NewAzureADAdministrator(ctx, "azureADAdministrator", &dbformysql.AzureADAdministratorArgs{
			AdministratorName:  pulumi.String("ActiveDirectory"),
			AdministratorType:  pulumi.String("ActiveDirectory"),
			IdentityResourceId: pulumi.String("/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/test-group/providers/Microsoft.ManagedIdentity/userAssignedIdentities/test-umi"),
			Login:              pulumi.String("bob@contoso.com"),
			ResourceGroupName:  pulumi.String("testrg"),
			ServerName:         pulumi.String("mysqltestsvc4"),
			Sid:                pulumi.String("c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c"),
			TenantId:           pulumi.String("c12b7025-bfe2-46c1-b463-993b5e4cd467"),
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
import com.pulumi.azurenative.dbformysql.AzureADAdministrator;
import com.pulumi.azurenative.dbformysql.AzureADAdministratorArgs;
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
        var azureADAdministrator = new AzureADAdministrator("azureADAdministrator", AzureADAdministratorArgs.builder()        
            .administratorName("ActiveDirectory")
            .administratorType("ActiveDirectory")
            .identityResourceId("/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/test-group/providers/Microsoft.ManagedIdentity/userAssignedIdentities/test-umi")
            .login("bob@contoso.com")
            .resourceGroupName("testrg")
            .serverName("mysqltestsvc4")
            .sid("c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c")
            .tenantId("c12b7025-bfe2-46c1-b463-993b5e4cd467")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const azureADAdministrator = new azure_native.dbformysql.AzureADAdministrator("azureADAdministrator", {
    administratorName: "ActiveDirectory",
    administratorType: "ActiveDirectory",
    identityResourceId: "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/test-group/providers/Microsoft.ManagedIdentity/userAssignedIdentities/test-umi",
    login: "bob@contoso.com",
    resourceGroupName: "testrg",
    serverName: "mysqltestsvc4",
    sid: "c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c",
    tenantId: "c12b7025-bfe2-46c1-b463-993b5e4cd467",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

azure_ad_administrator = azure_native.dbformysql.AzureADAdministrator("azureADAdministrator",
    administrator_name="ActiveDirectory",
    administrator_type="ActiveDirectory",
    identity_resource_id="/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/test-group/providers/Microsoft.ManagedIdentity/userAssignedIdentities/test-umi",
    login="bob@contoso.com",
    resource_group_name="testrg",
    server_name="mysqltestsvc4",
    sid="c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c",
    tenant_id="c12b7025-bfe2-46c1-b463-993b5e4cd467")

```

```yaml
resources:
  azureADAdministrator:
    type: azure-native:dbformysql:AzureADAdministrator
    properties:
      administratorName: ActiveDirectory
      administratorType: ActiveDirectory
      identityResourceId: /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/test-group/providers/Microsoft.ManagedIdentity/userAssignedIdentities/test-umi
      login: bob@contoso.com
      resourceGroupName: testrg
      serverName: mysqltestsvc4
      sid: c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c
      tenantId: c12b7025-bfe2-46c1-b463-993b5e4cd467

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:dbformysql:AzureADAdministrator ActiveDirectory /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.DBforMySQL/flexibleServers/mysqltestsvc4/administrators/ActiveDirectory 
```
