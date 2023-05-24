An Azure SQL managed instance administrator.
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create administrator of managed instance
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedInstanceAdministrator = new AzureNative.Sql.ManagedInstanceAdministrator("managedInstanceAdministrator", new()
    {
        AdministratorName = "ActiveDirectory",
        AdministratorType = "ActiveDirectory",
        Login = "bob@contoso.com",
        ManagedInstanceName = "managedInstance",
        ResourceGroupName = "Default-SQL-SouthEastAsia",
        Sid = "44444444-3333-2222-1111-000000000000",
        TenantId = "55555555-4444-3333-2222-111111111111",
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
		_, err := sql.NewManagedInstanceAdministrator(ctx, "managedInstanceAdministrator", &sql.ManagedInstanceAdministratorArgs{
			AdministratorName:   pulumi.String("ActiveDirectory"),
			AdministratorType:   pulumi.String("ActiveDirectory"),
			Login:               pulumi.String("bob@contoso.com"),
			ManagedInstanceName: pulumi.String("managedInstance"),
			ResourceGroupName:   pulumi.String("Default-SQL-SouthEastAsia"),
			Sid:                 pulumi.String("44444444-3333-2222-1111-000000000000"),
			TenantId:            pulumi.String("55555555-4444-3333-2222-111111111111"),
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
import com.pulumi.azurenative.sql.ManagedInstanceAdministrator;
import com.pulumi.azurenative.sql.ManagedInstanceAdministratorArgs;
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
        var managedInstanceAdministrator = new ManagedInstanceAdministrator("managedInstanceAdministrator", ManagedInstanceAdministratorArgs.builder()        
            .administratorName("ActiveDirectory")
            .administratorType("ActiveDirectory")
            .login("bob@contoso.com")
            .managedInstanceName("managedInstance")
            .resourceGroupName("Default-SQL-SouthEastAsia")
            .sid("44444444-3333-2222-1111-000000000000")
            .tenantId("55555555-4444-3333-2222-111111111111")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedInstanceAdministrator = new azure_native.sql.ManagedInstanceAdministrator("managedInstanceAdministrator", {
    administratorName: "ActiveDirectory",
    administratorType: "ActiveDirectory",
    login: "bob@contoso.com",
    managedInstanceName: "managedInstance",
    resourceGroupName: "Default-SQL-SouthEastAsia",
    sid: "44444444-3333-2222-1111-000000000000",
    tenantId: "55555555-4444-3333-2222-111111111111",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_instance_administrator = azure_native.sql.ManagedInstanceAdministrator("managedInstanceAdministrator",
    administrator_name="ActiveDirectory",
    administrator_type="ActiveDirectory",
    login="bob@contoso.com",
    managed_instance_name="managedInstance",
    resource_group_name="Default-SQL-SouthEastAsia",
    sid="44444444-3333-2222-1111-000000000000",
    tenant_id="55555555-4444-3333-2222-111111111111")

```

```yaml
resources:
  managedInstanceAdministrator:
    type: azure-native:sql:ManagedInstanceAdministrator
    properties:
      administratorName: ActiveDirectory
      administratorType: ActiveDirectory
      login: bob@contoso.com
      managedInstanceName: managedInstance
      resourceGroupName: Default-SQL-SouthEastAsia
      sid: 44444444-3333-2222-1111-000000000000
      tenantId: 55555555-4444-3333-2222-111111111111

```

{{% /example %}}
{{% example %}}
### Update administrator of managed instance
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedInstanceAdministrator = new AzureNative.Sql.ManagedInstanceAdministrator("managedInstanceAdministrator", new()
    {
        AdministratorName = "ActiveDirectory",
        AdministratorType = "ActiveDirectory",
        Login = "bob@contoso.com",
        ManagedInstanceName = "managedInstance",
        ResourceGroupName = "Default-SQL-SouthEastAsia",
        Sid = "44444444-3333-2222-1111-000000000000",
        TenantId = "55555555-4444-3333-2222-111111111111",
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
		_, err := sql.NewManagedInstanceAdministrator(ctx, "managedInstanceAdministrator", &sql.ManagedInstanceAdministratorArgs{
			AdministratorName:   pulumi.String("ActiveDirectory"),
			AdministratorType:   pulumi.String("ActiveDirectory"),
			Login:               pulumi.String("bob@contoso.com"),
			ManagedInstanceName: pulumi.String("managedInstance"),
			ResourceGroupName:   pulumi.String("Default-SQL-SouthEastAsia"),
			Sid:                 pulumi.String("44444444-3333-2222-1111-000000000000"),
			TenantId:            pulumi.String("55555555-4444-3333-2222-111111111111"),
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
import com.pulumi.azurenative.sql.ManagedInstanceAdministrator;
import com.pulumi.azurenative.sql.ManagedInstanceAdministratorArgs;
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
        var managedInstanceAdministrator = new ManagedInstanceAdministrator("managedInstanceAdministrator", ManagedInstanceAdministratorArgs.builder()        
            .administratorName("ActiveDirectory")
            .administratorType("ActiveDirectory")
            .login("bob@contoso.com")
            .managedInstanceName("managedInstance")
            .resourceGroupName("Default-SQL-SouthEastAsia")
            .sid("44444444-3333-2222-1111-000000000000")
            .tenantId("55555555-4444-3333-2222-111111111111")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedInstanceAdministrator = new azure_native.sql.ManagedInstanceAdministrator("managedInstanceAdministrator", {
    administratorName: "ActiveDirectory",
    administratorType: "ActiveDirectory",
    login: "bob@contoso.com",
    managedInstanceName: "managedInstance",
    resourceGroupName: "Default-SQL-SouthEastAsia",
    sid: "44444444-3333-2222-1111-000000000000",
    tenantId: "55555555-4444-3333-2222-111111111111",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_instance_administrator = azure_native.sql.ManagedInstanceAdministrator("managedInstanceAdministrator",
    administrator_name="ActiveDirectory",
    administrator_type="ActiveDirectory",
    login="bob@contoso.com",
    managed_instance_name="managedInstance",
    resource_group_name="Default-SQL-SouthEastAsia",
    sid="44444444-3333-2222-1111-000000000000",
    tenant_id="55555555-4444-3333-2222-111111111111")

```

```yaml
resources:
  managedInstanceAdministrator:
    type: azure-native:sql:ManagedInstanceAdministrator
    properties:
      administratorName: ActiveDirectory
      administratorType: ActiveDirectory
      login: bob@contoso.com
      managedInstanceName: managedInstance
      resourceGroupName: Default-SQL-SouthEastAsia
      sid: 44444444-3333-2222-1111-000000000000
      tenantId: 55555555-4444-3333-2222-111111111111

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:ManagedInstanceAdministrator ActiveDirectory /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-SouthEastAsia/providers/Microsoft.Sql/managedInstances/managedInstance/administrators/ActiveDirectory 
```
