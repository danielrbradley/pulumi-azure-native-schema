Role management policy
API Version: 2020-10-01.
Previous API Version: 2020-10-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PutRoleManagementPolicyAssignment
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var roleManagementPolicyAssignment = new AzureNative.Authorization.RoleManagementPolicyAssignment("roleManagementPolicyAssignment", new()
    {
        PolicyId = "/subscriptions/129ff972-28f8-46b8-a726-e497be039368/providers/Microsoft.Authorization/roleManagementPolicies/b959d571-f0b5-4042-88a7-01be6cb22db9",
        RoleDefinitionId = "/subscriptions/129ff972-28f8-46b8-a726-e497be039368/providers/Microsoft.Authorization/roleDefinitions/a1705bd2-3a8f-45a5-8683-466fcfd5cc24",
        RoleManagementPolicyAssignmentName = "b959d571-f0b5-4042-88a7-01be6cb22db9_a1705bd2-3a8f-45a5-8683-466fcfd5cc24",
        Scope = "/subscriptions/129ff972-28f8-46b8-a726-e497be039368",
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
		_, err := authorization.NewRoleManagementPolicyAssignment(ctx, "roleManagementPolicyAssignment", &authorization.RoleManagementPolicyAssignmentArgs{
			PolicyId:                           pulumi.String("/subscriptions/129ff972-28f8-46b8-a726-e497be039368/providers/Microsoft.Authorization/roleManagementPolicies/b959d571-f0b5-4042-88a7-01be6cb22db9"),
			RoleDefinitionId:                   pulumi.String("/subscriptions/129ff972-28f8-46b8-a726-e497be039368/providers/Microsoft.Authorization/roleDefinitions/a1705bd2-3a8f-45a5-8683-466fcfd5cc24"),
			RoleManagementPolicyAssignmentName: pulumi.String("b959d571-f0b5-4042-88a7-01be6cb22db9_a1705bd2-3a8f-45a5-8683-466fcfd5cc24"),
			Scope:                              pulumi.String("/subscriptions/129ff972-28f8-46b8-a726-e497be039368"),
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
import com.pulumi.azurenative.authorization.RoleManagementPolicyAssignment;
import com.pulumi.azurenative.authorization.RoleManagementPolicyAssignmentArgs;
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
        var roleManagementPolicyAssignment = new RoleManagementPolicyAssignment("roleManagementPolicyAssignment", RoleManagementPolicyAssignmentArgs.builder()        
            .policyId("/subscriptions/129ff972-28f8-46b8-a726-e497be039368/providers/Microsoft.Authorization/roleManagementPolicies/b959d571-f0b5-4042-88a7-01be6cb22db9")
            .roleDefinitionId("/subscriptions/129ff972-28f8-46b8-a726-e497be039368/providers/Microsoft.Authorization/roleDefinitions/a1705bd2-3a8f-45a5-8683-466fcfd5cc24")
            .roleManagementPolicyAssignmentName("b959d571-f0b5-4042-88a7-01be6cb22db9_a1705bd2-3a8f-45a5-8683-466fcfd5cc24")
            .scope("/subscriptions/129ff972-28f8-46b8-a726-e497be039368")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const roleManagementPolicyAssignment = new azure_native.authorization.RoleManagementPolicyAssignment("roleManagementPolicyAssignment", {
    policyId: "/subscriptions/129ff972-28f8-46b8-a726-e497be039368/providers/Microsoft.Authorization/roleManagementPolicies/b959d571-f0b5-4042-88a7-01be6cb22db9",
    roleDefinitionId: "/subscriptions/129ff972-28f8-46b8-a726-e497be039368/providers/Microsoft.Authorization/roleDefinitions/a1705bd2-3a8f-45a5-8683-466fcfd5cc24",
    roleManagementPolicyAssignmentName: "b959d571-f0b5-4042-88a7-01be6cb22db9_a1705bd2-3a8f-45a5-8683-466fcfd5cc24",
    scope: "/subscriptions/129ff972-28f8-46b8-a726-e497be039368",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

role_management_policy_assignment = azure_native.authorization.RoleManagementPolicyAssignment("roleManagementPolicyAssignment",
    policy_id="/subscriptions/129ff972-28f8-46b8-a726-e497be039368/providers/Microsoft.Authorization/roleManagementPolicies/b959d571-f0b5-4042-88a7-01be6cb22db9",
    role_definition_id="/subscriptions/129ff972-28f8-46b8-a726-e497be039368/providers/Microsoft.Authorization/roleDefinitions/a1705bd2-3a8f-45a5-8683-466fcfd5cc24",
    role_management_policy_assignment_name="b959d571-f0b5-4042-88a7-01be6cb22db9_a1705bd2-3a8f-45a5-8683-466fcfd5cc24",
    scope="/subscriptions/129ff972-28f8-46b8-a726-e497be039368")

```

```yaml
resources:
  roleManagementPolicyAssignment:
    type: azure-native:authorization:RoleManagementPolicyAssignment
    properties:
      policyId: /subscriptions/129ff972-28f8-46b8-a726-e497be039368/providers/Microsoft.Authorization/roleManagementPolicies/b959d571-f0b5-4042-88a7-01be6cb22db9
      roleDefinitionId: /subscriptions/129ff972-28f8-46b8-a726-e497be039368/providers/Microsoft.Authorization/roleDefinitions/a1705bd2-3a8f-45a5-8683-466fcfd5cc24
      roleManagementPolicyAssignmentName: b959d571-f0b5-4042-88a7-01be6cb22db9_a1705bd2-3a8f-45a5-8683-466fcfd5cc24
      scope: /subscriptions/129ff972-28f8-46b8-a726-e497be039368

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:authorization:RoleManagementPolicyAssignment b959d571-f0b5-4042-88a7-01be6cb22db9_a1705bd2-3a8f-45a5-8683-466fcfd5cc24 /subscriptions/129ff972-28f8-46b8-a726-e497be039368/providers/Microsoft.Authorization/roleManagementPolicyAssignment/b959d571-f0b5-4042-88a7-01be6cb22db9_a1705bd2-3a8f-45a5-8683-466fcfd5cc24 
```
