The Role Assignment resource format.
API Version: 2017-04-26.
Previous API Version: 2017-04-26. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### RoleAssignments_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var roleAssignment = new AzureNative.CustomerInsights.RoleAssignment("roleAssignment", new()
    {
        AssignmentName = "assignmentName8976",
        HubName = "sdkTestHub",
        Principals = new[]
        {
            new AzureNative.CustomerInsights.Inputs.AssignmentPrincipalArgs
            {
                PrincipalId = "4c54c38ffa9b416ba5a6d6c8a20cbe7e",
                PrincipalType = "User",
            },
            new AzureNative.CustomerInsights.Inputs.AssignmentPrincipalArgs
            {
                PrincipalId = "93061d15a5054f2b9948ae25724cf9d5",
                PrincipalType = "User",
            },
        },
        ResourceGroupName = "TestHubRG",
        Role = AzureNative.CustomerInsights.RoleTypes.Admin,
    });

});


```

```go
package main

import (
	customerinsights "github.com/pulumi/pulumi-azure-native-sdk/customerinsights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := customerinsights.NewRoleAssignment(ctx, "roleAssignment", &customerinsights.RoleAssignmentArgs{
			AssignmentName: pulumi.String("assignmentName8976"),
			HubName:        pulumi.String("sdkTestHub"),
			Principals: []customerinsights.AssignmentPrincipalArgs{
				{
					PrincipalId:   pulumi.String("4c54c38ffa9b416ba5a6d6c8a20cbe7e"),
					PrincipalType: pulumi.String("User"),
				},
				{
					PrincipalId:   pulumi.String("93061d15a5054f2b9948ae25724cf9d5"),
					PrincipalType: pulumi.String("User"),
				},
			},
			ResourceGroupName: pulumi.String("TestHubRG"),
			Role:              customerinsights.RoleTypesAdmin,
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
import com.pulumi.azurenative.customerinsights.RoleAssignment;
import com.pulumi.azurenative.customerinsights.RoleAssignmentArgs;
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
            .assignmentName("assignmentName8976")
            .hubName("sdkTestHub")
            .principals(            
                Map.ofEntries(
                    Map.entry("principalId", "4c54c38ffa9b416ba5a6d6c8a20cbe7e"),
                    Map.entry("principalType", "User")
                ),
                Map.ofEntries(
                    Map.entry("principalId", "93061d15a5054f2b9948ae25724cf9d5"),
                    Map.entry("principalType", "User")
                ))
            .resourceGroupName("TestHubRG")
            .role("Admin")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const roleAssignment = new azure_native.customerinsights.RoleAssignment("roleAssignment", {
    assignmentName: "assignmentName8976",
    hubName: "sdkTestHub",
    principals: [
        {
            principalId: "4c54c38ffa9b416ba5a6d6c8a20cbe7e",
            principalType: "User",
        },
        {
            principalId: "93061d15a5054f2b9948ae25724cf9d5",
            principalType: "User",
        },
    ],
    resourceGroupName: "TestHubRG",
    role: azure_native.customerinsights.RoleTypes.Admin,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

role_assignment = azure_native.customerinsights.RoleAssignment("roleAssignment",
    assignment_name="assignmentName8976",
    hub_name="sdkTestHub",
    principals=[
        azure_native.customerinsights.AssignmentPrincipalArgs(
            principal_id="4c54c38ffa9b416ba5a6d6c8a20cbe7e",
            principal_type="User",
        ),
        azure_native.customerinsights.AssignmentPrincipalArgs(
            principal_id="93061d15a5054f2b9948ae25724cf9d5",
            principal_type="User",
        ),
    ],
    resource_group_name="TestHubRG",
    role=azure_native.customerinsights.RoleTypes.ADMIN)

```

```yaml
resources:
  roleAssignment:
    type: azure-native:customerinsights:RoleAssignment
    properties:
      assignmentName: assignmentName8976
      hubName: sdkTestHub
      principals:
        - principalId: 4c54c38ffa9b416ba5a6d6c8a20cbe7e
          principalType: User
        - principalId: 93061d15a5054f2b9948ae25724cf9d5
          principalType: User
      resourceGroupName: TestHubRG
      role: Admin

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:customerinsights:RoleAssignment azSdkTestHub/assignmentName8976 /subscriptions/c909e979-ef71-4def-a970-bc7c154db8c5/resourceGroups/TestHubRG/providers/Microsoft.CustomerInsights/hubs/azSdkTestHub/RoleAssignments/assignmentName8976 
```
