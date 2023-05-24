Workspace active directory administrator
API Version: 2021-06-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

Note: SQL AAD Admin is configured automatically during workspace creation and assigned to the current user. One can't add more admins with this resource unless you manually delete the current SQL AAD Admin.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update workspace active directory admin
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var workspaceSqlAadAdmin = new AzureNative.Synapse.WorkspaceSqlAadAdmin("workspaceSqlAadAdmin", new()
    {
        AdministratorType = "ActiveDirectory",
        Login = "bob@contoso.com",
        ResourceGroupName = "resourceGroup1",
        Sid = "c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c",
        TenantId = "c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c",
        WorkspaceName = "workspace1",
    });

});


```

```go
package main

import (
	synapse "github.com/pulumi/pulumi-azure-native-sdk/synapse"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := synapse.NewWorkspaceSqlAadAdmin(ctx, "workspaceSqlAadAdmin", &synapse.WorkspaceSqlAadAdminArgs{
			AdministratorType: pulumi.String("ActiveDirectory"),
			Login:             pulumi.String("bob@contoso.com"),
			ResourceGroupName: pulumi.String("resourceGroup1"),
			Sid:               pulumi.String("c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c"),
			TenantId:          pulumi.String("c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c"),
			WorkspaceName:     pulumi.String("workspace1"),
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
import com.pulumi.azurenative.synapse.WorkspaceSqlAadAdmin;
import com.pulumi.azurenative.synapse.WorkspaceSqlAadAdminArgs;
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
        var workspaceSqlAadAdmin = new WorkspaceSqlAadAdmin("workspaceSqlAadAdmin", WorkspaceSqlAadAdminArgs.builder()        
            .administratorType("ActiveDirectory")
            .login("bob@contoso.com")
            .resourceGroupName("resourceGroup1")
            .sid("c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c")
            .tenantId("c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c")
            .workspaceName("workspace1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const workspaceSqlAadAdmin = new azure_native.synapse.WorkspaceSqlAadAdmin("workspaceSqlAadAdmin", {
    administratorType: "ActiveDirectory",
    login: "bob@contoso.com",
    resourceGroupName: "resourceGroup1",
    sid: "c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c",
    tenantId: "c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c",
    workspaceName: "workspace1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

workspace_sql_aad_admin = azure_native.synapse.WorkspaceSqlAadAdmin("workspaceSqlAadAdmin",
    administrator_type="ActiveDirectory",
    login="bob@contoso.com",
    resource_group_name="resourceGroup1",
    sid="c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c",
    tenant_id="c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c",
    workspace_name="workspace1")

```

```yaml
resources:
  workspaceSqlAadAdmin:
    type: azure-native:synapse:WorkspaceSqlAadAdmin
    properties:
      administratorType: ActiveDirectory
      login: bob@contoso.com
      resourceGroupName: resourceGroup1
      sid: c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c
      tenantId: c6b82b90-a647-49cb-8a62-0d2d3cb7ac7c
      workspaceName: workspace1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:synapse:WorkspaceSqlAadAdmin activeDirectory /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/resourceGroup1/providers/Microsoft.Synapse/workspaces/workspace1/administrators/activeDirectory 
```
