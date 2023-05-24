Role Assignments
API Version: 2022-04-01.
Previous API Version: 2020-10-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create role assignment for resource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var roleAssignment = new AzureNative.Authorization.RoleAssignment("roleAssignment", new()
    {
        PrincipalId = "ce2ce14e-85d7-4629-bdbc-454d0519d987",
        PrincipalType = "User",
        RoleAssignmentName = "05c5a614-a7d6-4502-b150-c2fb455033ff",
        RoleDefinitionId = "/subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2/providers/Microsoft.Authorization/roleDefinitions/0b5fe924-9a61-425c-96af-cfe6e287ca2d",
        Scope = "subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2/resourceGroups/testrg/providers/Microsoft.DocumentDb/databaseAccounts/test-db-account",
    });

});


```

```go
package main

import (
	authorization "github.com/pulumi/pulumi-azure-native-sdk/authorization"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := authorization.NewRoleAssignment(ctx, "roleAssignment", &authorization.RoleAssignmentArgs{
			PrincipalId:        pulumi.String("ce2ce14e-85d7-4629-bdbc-454d0519d987"),
			PrincipalType:      pulumi.String("User"),
			RoleAssignmentName: pulumi.String("05c5a614-a7d6-4502-b150-c2fb455033ff"),
			RoleDefinitionId:   pulumi.String("/subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2/providers/Microsoft.Authorization/roleDefinitions/0b5fe924-9a61-425c-96af-cfe6e287ca2d"),
			Scope:              pulumi.String("subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2/resourceGroups/testrg/providers/Microsoft.DocumentDb/databaseAccounts/test-db-account"),
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
import com.pulumi.azurenative.authorization.RoleAssignment;
import com.pulumi.azurenative.authorization.RoleAssignmentArgs;
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
        var roleAssignment = new RoleAssignment("roleAssignment", RoleAssignmentArgs.builder()        
            .principalId("ce2ce14e-85d7-4629-bdbc-454d0519d987")
            .principalType("User")
            .roleAssignmentName("05c5a614-a7d6-4502-b150-c2fb455033ff")
            .roleDefinitionId("/subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2/providers/Microsoft.Authorization/roleDefinitions/0b5fe924-9a61-425c-96af-cfe6e287ca2d")
            .scope("subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2/resourceGroups/testrg/providers/Microsoft.DocumentDb/databaseAccounts/test-db-account")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const roleAssignment = new azure_native.authorization.RoleAssignment("roleAssignment", {
    principalId: "ce2ce14e-85d7-4629-bdbc-454d0519d987",
    principalType: "User",
    roleAssignmentName: "05c5a614-a7d6-4502-b150-c2fb455033ff",
    roleDefinitionId: "/subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2/providers/Microsoft.Authorization/roleDefinitions/0b5fe924-9a61-425c-96af-cfe6e287ca2d",
    scope: "subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2/resourceGroups/testrg/providers/Microsoft.DocumentDb/databaseAccounts/test-db-account",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

role_assignment = azure_native.authorization.RoleAssignment("roleAssignment",
    principal_id="ce2ce14e-85d7-4629-bdbc-454d0519d987",
    principal_type="User",
    role_assignment_name="05c5a614-a7d6-4502-b150-c2fb455033ff",
    role_definition_id="/subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2/providers/Microsoft.Authorization/roleDefinitions/0b5fe924-9a61-425c-96af-cfe6e287ca2d",
    scope="subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2/resourceGroups/testrg/providers/Microsoft.DocumentDb/databaseAccounts/test-db-account")

```

```yaml
resources:
  roleAssignment:
    type: azure-native:authorization:RoleAssignment
    properties:
      principalId: ce2ce14e-85d7-4629-bdbc-454d0519d987
      principalType: User
      roleAssignmentName: 05c5a614-a7d6-4502-b150-c2fb455033ff
      roleDefinitionId: /subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2/providers/Microsoft.Authorization/roleDefinitions/0b5fe924-9a61-425c-96af-cfe6e287ca2d
      scope: subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2/resourceGroups/testrg/providers/Microsoft.DocumentDb/databaseAccounts/test-db-account

```

{{% /example %}}
{{% example %}}
### Create role assignment for resource group
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var roleAssignment = new AzureNative.Authorization.RoleAssignment("roleAssignment", new()
    {
        PrincipalId = "ce2ce14e-85d7-4629-bdbc-454d0519d987",
        PrincipalType = "User",
        RoleAssignmentName = "05c5a614-a7d6-4502-b150-c2fb455033ff",
        RoleDefinitionId = "/subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2/providers/Microsoft.Authorization/roleDefinitions/0b5fe924-9a61-425c-96af-cfe6e287ca2d",
        Scope = "subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2/resourceGroups/testrg",
    });

});


```

```go
package main

import (
	authorization "github.com/pulumi/pulumi-azure-native-sdk/authorization"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := authorization.NewRoleAssignment(ctx, "roleAssignment", &authorization.RoleAssignmentArgs{
			PrincipalId:        pulumi.String("ce2ce14e-85d7-4629-bdbc-454d0519d987"),
			PrincipalType:      pulumi.String("User"),
			RoleAssignmentName: pulumi.String("05c5a614-a7d6-4502-b150-c2fb455033ff"),
			RoleDefinitionId:   pulumi.String("/subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2/providers/Microsoft.Authorization/roleDefinitions/0b5fe924-9a61-425c-96af-cfe6e287ca2d"),
			Scope:              pulumi.String("subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2/resourceGroups/testrg"),
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
import com.pulumi.azurenative.authorization.RoleAssignment;
import com.pulumi.azurenative.authorization.RoleAssignmentArgs;
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
        var roleAssignment = new RoleAssignment("roleAssignment", RoleAssignmentArgs.builder()        
            .principalId("ce2ce14e-85d7-4629-bdbc-454d0519d987")
            .principalType("User")
            .roleAssignmentName("05c5a614-a7d6-4502-b150-c2fb455033ff")
            .roleDefinitionId("/subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2/providers/Microsoft.Authorization/roleDefinitions/0b5fe924-9a61-425c-96af-cfe6e287ca2d")
            .scope("subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2/resourceGroups/testrg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const roleAssignment = new azure_native.authorization.RoleAssignment("roleAssignment", {
    principalId: "ce2ce14e-85d7-4629-bdbc-454d0519d987",
    principalType: "User",
    roleAssignmentName: "05c5a614-a7d6-4502-b150-c2fb455033ff",
    roleDefinitionId: "/subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2/providers/Microsoft.Authorization/roleDefinitions/0b5fe924-9a61-425c-96af-cfe6e287ca2d",
    scope: "subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2/resourceGroups/testrg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

role_assignment = azure_native.authorization.RoleAssignment("roleAssignment",
    principal_id="ce2ce14e-85d7-4629-bdbc-454d0519d987",
    principal_type="User",
    role_assignment_name="05c5a614-a7d6-4502-b150-c2fb455033ff",
    role_definition_id="/subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2/providers/Microsoft.Authorization/roleDefinitions/0b5fe924-9a61-425c-96af-cfe6e287ca2d",
    scope="subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2/resourceGroups/testrg")

```

```yaml
resources:
  roleAssignment:
    type: azure-native:authorization:RoleAssignment
    properties:
      principalId: ce2ce14e-85d7-4629-bdbc-454d0519d987
      principalType: User
      roleAssignmentName: 05c5a614-a7d6-4502-b150-c2fb455033ff
      roleDefinitionId: /subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2/providers/Microsoft.Authorization/roleDefinitions/0b5fe924-9a61-425c-96af-cfe6e287ca2d
      scope: subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2/resourceGroups/testrg

```

{{% /example %}}
{{% example %}}
### Create role assignment for subscription
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var roleAssignment = new AzureNative.Authorization.RoleAssignment("roleAssignment", new()
    {
        PrincipalId = "ce2ce14e-85d7-4629-bdbc-454d0519d987",
        PrincipalType = "User",
        RoleAssignmentName = "05c5a614-a7d6-4502-b150-c2fb455033ff",
        RoleDefinitionId = "/subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2/providers/Microsoft.Authorization/roleDefinitions/0b5fe924-9a61-425c-96af-cfe6e287ca2d",
        Scope = "subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2",
    });

});


```

```go
package main

import (
	authorization "github.com/pulumi/pulumi-azure-native-sdk/authorization"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := authorization.NewRoleAssignment(ctx, "roleAssignment", &authorization.RoleAssignmentArgs{
			PrincipalId:        pulumi.String("ce2ce14e-85d7-4629-bdbc-454d0519d987"),
			PrincipalType:      pulumi.String("User"),
			RoleAssignmentName: pulumi.String("05c5a614-a7d6-4502-b150-c2fb455033ff"),
			RoleDefinitionId:   pulumi.String("/subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2/providers/Microsoft.Authorization/roleDefinitions/0b5fe924-9a61-425c-96af-cfe6e287ca2d"),
			Scope:              pulumi.String("subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2"),
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
import com.pulumi.azurenative.authorization.RoleAssignment;
import com.pulumi.azurenative.authorization.RoleAssignmentArgs;
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
        var roleAssignment = new RoleAssignment("roleAssignment", RoleAssignmentArgs.builder()        
            .principalId("ce2ce14e-85d7-4629-bdbc-454d0519d987")
            .principalType("User")
            .roleAssignmentName("05c5a614-a7d6-4502-b150-c2fb455033ff")
            .roleDefinitionId("/subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2/providers/Microsoft.Authorization/roleDefinitions/0b5fe924-9a61-425c-96af-cfe6e287ca2d")
            .scope("subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const roleAssignment = new azure_native.authorization.RoleAssignment("roleAssignment", {
    principalId: "ce2ce14e-85d7-4629-bdbc-454d0519d987",
    principalType: "User",
    roleAssignmentName: "05c5a614-a7d6-4502-b150-c2fb455033ff",
    roleDefinitionId: "/subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2/providers/Microsoft.Authorization/roleDefinitions/0b5fe924-9a61-425c-96af-cfe6e287ca2d",
    scope: "subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

role_assignment = azure_native.authorization.RoleAssignment("roleAssignment",
    principal_id="ce2ce14e-85d7-4629-bdbc-454d0519d987",
    principal_type="User",
    role_assignment_name="05c5a614-a7d6-4502-b150-c2fb455033ff",
    role_definition_id="/subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2/providers/Microsoft.Authorization/roleDefinitions/0b5fe924-9a61-425c-96af-cfe6e287ca2d",
    scope="subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2")

```

```yaml
resources:
  roleAssignment:
    type: azure-native:authorization:RoleAssignment
    properties:
      principalId: ce2ce14e-85d7-4629-bdbc-454d0519d987
      principalType: User
      roleAssignmentName: 05c5a614-a7d6-4502-b150-c2fb455033ff
      roleDefinitionId: /subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2/providers/Microsoft.Authorization/roleDefinitions/0b5fe924-9a61-425c-96af-cfe6e287ca2d
      scope: subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:authorization:RoleAssignment 05c5a614-a7d6-4502-b150-c2fb455033ff /subscriptions/a925f2f7-5c63-4b7b-8799-25a5f97bc3b2/providers/Microsoft.Authorization/roleAssignments/05c5a614-a7d6-4502-b150-c2fb455033ff 
```
