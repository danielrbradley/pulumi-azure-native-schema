Represents a blueprint assignment.
API Version: 2018-11-01-preview.
Previous API Version: 2018-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Assignment with system-assigned managed identity at management group scope
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var assignment = new AzureNative.Blueprint.Assignment("assignment", new()
    {
        AssignmentName = "assignSimpleBlueprint",
        BlueprintId = "/providers/Microsoft.Management/managementGroups/ContosoOnlineGroup/providers/Microsoft.Blueprint/blueprints/simpleBlueprint",
        Description = "enforce pre-defined simpleBlueprint to this XXXXXXXX subscription.",
        Identity = new AzureNative.Blueprint.Inputs.ManagedServiceIdentityArgs
        {
            Type = "SystemAssigned",
        },
        Location = "eastus",
        Parameters = 
        {
            { "costCenter", new AzureNative.Blueprint.Inputs.ParameterValueArgs
            {
                Value = "Contoso/Online/Shopping/Production",
            } },
            { "owners", new AzureNative.Blueprint.Inputs.ParameterValueArgs
            {
                Value = new[]
                {
                    "johnDoe@contoso.com",
                    "johnsteam@contoso.com",
                },
            } },
            { "storageAccountType", new AzureNative.Blueprint.Inputs.ParameterValueArgs
            {
                Value = "Standard_LRS",
            } },
        },
        ResourceGroups = 
        {
            { "storageRG", new AzureNative.Blueprint.Inputs.ResourceGroupValueArgs
            {
                Location = "eastus",
                Name = "defaultRG",
            } },
        },
        ResourceScope = "managementGroups/ContosoOnlineGroup",
        Scope = "subscriptions/00000000-0000-0000-0000-000000000000",
    });

});


```

```go
package main

import (
	blueprint "github.com/pulumi/pulumi-azure-native-sdk/blueprint"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := blueprint.NewAssignment(ctx, "assignment", &blueprint.AssignmentArgs{
			AssignmentName: pulumi.String("assignSimpleBlueprint"),
			BlueprintId:    pulumi.String("/providers/Microsoft.Management/managementGroups/ContosoOnlineGroup/providers/Microsoft.Blueprint/blueprints/simpleBlueprint"),
			Description:    pulumi.String("enforce pre-defined simpleBlueprint to this XXXXXXXX subscription."),
			Identity: &blueprint.ManagedServiceIdentityArgs{
				Type: pulumi.String("SystemAssigned"),
			},
			Location: pulumi.String("eastus"),
			Parameters: blueprint.ParameterValueMap{
				"costCenter": &blueprint.ParameterValueArgs{
					Value: pulumi.Any("Contoso/Online/Shopping/Production"),
				},
				"owners": &blueprint.ParameterValueArgs{
					Value: pulumi.Any{
						"johnDoe@contoso.com",
						"johnsteam@contoso.com",
					},
				},
				"storageAccountType": &blueprint.ParameterValueArgs{
					Value: pulumi.Any("Standard_LRS"),
				},
			},
			ResourceGroups: blueprint.ResourceGroupValueMap{
				"storageRG": &blueprint.ResourceGroupValueArgs{
					Location: pulumi.String("eastus"),
					Name:     pulumi.String("defaultRG"),
				},
			},
			ResourceScope: pulumi.String("managementGroups/ContosoOnlineGroup"),
			Scope:         pulumi.String("subscriptions/00000000-0000-0000-0000-000000000000"),
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
import com.pulumi.azurenative.blueprint.Assignment;
import com.pulumi.azurenative.blueprint.AssignmentArgs;
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
        var assignment = new Assignment("assignment", AssignmentArgs.builder()        
            .assignmentName("assignSimpleBlueprint")
            .blueprintId("/providers/Microsoft.Management/managementGroups/ContosoOnlineGroup/providers/Microsoft.Blueprint/blueprints/simpleBlueprint")
            .description("enforce pre-defined simpleBlueprint to this XXXXXXXX subscription.")
            .identity(Map.of("type", "SystemAssigned"))
            .location("eastus")
            .parameters(Map.ofEntries(
                Map.entry("costCenter", Map.of("value", "Contoso/Online/Shopping/Production")),
                Map.entry("owners", Map.of("value",                 
                    "johnDoe@contoso.com",
                    "johnsteam@contoso.com")),
                Map.entry("storageAccountType", Map.of("value", "Standard_LRS"))
            ))
            .resourceGroups(Map.of("storageRG", Map.ofEntries(
                Map.entry("location", "eastus"),
                Map.entry("name", "defaultRG")
            )))
            .resourceScope("managementGroups/ContosoOnlineGroup")
            .scope("subscriptions/00000000-0000-0000-0000-000000000000")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const assignment = new azure_native.blueprint.Assignment("assignment", {
    assignmentName: "assignSimpleBlueprint",
    blueprintId: "/providers/Microsoft.Management/managementGroups/ContosoOnlineGroup/providers/Microsoft.Blueprint/blueprints/simpleBlueprint",
    description: "enforce pre-defined simpleBlueprint to this XXXXXXXX subscription.",
    identity: {
        type: "SystemAssigned",
    },
    location: "eastus",
    parameters: {
        costCenter: {
            value: "Contoso/Online/Shopping/Production",
        },
        owners: {
            value: [
                "johnDoe@contoso.com",
                "johnsteam@contoso.com",
            ],
        },
        storageAccountType: {
            value: "Standard_LRS",
        },
    },
    resourceGroups: {
        storageRG: {
            location: "eastus",
            name: "defaultRG",
        },
    },
    resourceScope: "managementGroups/ContosoOnlineGroup",
    scope: "subscriptions/00000000-0000-0000-0000-000000000000",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

assignment = azure_native.blueprint.Assignment("assignment",
    assignment_name="assignSimpleBlueprint",
    blueprint_id="/providers/Microsoft.Management/managementGroups/ContosoOnlineGroup/providers/Microsoft.Blueprint/blueprints/simpleBlueprint",
    description="enforce pre-defined simpleBlueprint to this XXXXXXXX subscription.",
    identity=azure_native.blueprint.ManagedServiceIdentityArgs(
        type="SystemAssigned",
    ),
    location="eastus",
    parameters={
        "costCenter": azure_native.blueprint.ParameterValueArgs(
            value="Contoso/Online/Shopping/Production",
        ),
        "owners": azure_native.blueprint.ParameterValueArgs(
            value=[
                "johnDoe@contoso.com",
                "johnsteam@contoso.com",
            ],
        ),
        "storageAccountType": azure_native.blueprint.ParameterValueArgs(
            value="Standard_LRS",
        ),
    },
    resource_groups={
        "storageRG": azure_native.blueprint.ResourceGroupValueArgs(
            location="eastus",
            name="defaultRG",
        ),
    },
    resource_scope="managementGroups/ContosoOnlineGroup",
    scope="subscriptions/00000000-0000-0000-0000-000000000000")

```

```yaml
resources:
  assignment:
    type: azure-native:blueprint:Assignment
    properties:
      assignmentName: assignSimpleBlueprint
      blueprintId: /providers/Microsoft.Management/managementGroups/ContosoOnlineGroup/providers/Microsoft.Blueprint/blueprints/simpleBlueprint
      description: enforce pre-defined simpleBlueprint to this XXXXXXXX subscription.
      identity:
        type: SystemAssigned
      location: eastus
      parameters:
        costCenter:
          value: Contoso/Online/Shopping/Production
        owners:
          value:
            - johnDoe@contoso.com
            - johnsteam@contoso.com
        storageAccountType:
          value: Standard_LRS
      resourceGroups:
        storageRG:
          location: eastus
          name: defaultRG
      resourceScope: managementGroups/ContosoOnlineGroup
      scope: subscriptions/00000000-0000-0000-0000-000000000000

```

{{% /example %}}
{{% example %}}
### Assignment with system-assigned managed identity at subscription scope
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var assignment = new AzureNative.Blueprint.Assignment("assignment", new()
    {
        AssignmentName = "assignSimpleBlueprint",
        BlueprintId = "/providers/Microsoft.Management/managementGroups/ContosoOnlineGroup/providers/Microsoft.Blueprint/blueprints/simpleBlueprint",
        Description = "enforce pre-defined simpleBlueprint to this XXXXXXXX subscription.",
        Identity = new AzureNative.Blueprint.Inputs.ManagedServiceIdentityArgs
        {
            Type = "SystemAssigned",
        },
        Location = "eastus",
        Parameters = 
        {
            { "costCenter", new AzureNative.Blueprint.Inputs.ParameterValueArgs
            {
                Value = "Contoso/Online/Shopping/Production",
            } },
            { "owners", new AzureNative.Blueprint.Inputs.ParameterValueArgs
            {
                Value = new[]
                {
                    "johnDoe@contoso.com",
                    "johnsteam@contoso.com",
                },
            } },
            { "storageAccountType", new AzureNative.Blueprint.Inputs.ParameterValueArgs
            {
                Value = "Standard_LRS",
            } },
        },
        ResourceGroups = 
        {
            { "storageRG", new AzureNative.Blueprint.Inputs.ResourceGroupValueArgs
            {
                Location = "eastus",
                Name = "defaultRG",
            } },
        },
        ResourceScope = "subscriptions/00000000-0000-0000-0000-000000000000",
    });

});


```

```go
package main

import (
	blueprint "github.com/pulumi/pulumi-azure-native-sdk/blueprint"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := blueprint.NewAssignment(ctx, "assignment", &blueprint.AssignmentArgs{
			AssignmentName: pulumi.String("assignSimpleBlueprint"),
			BlueprintId:    pulumi.String("/providers/Microsoft.Management/managementGroups/ContosoOnlineGroup/providers/Microsoft.Blueprint/blueprints/simpleBlueprint"),
			Description:    pulumi.String("enforce pre-defined simpleBlueprint to this XXXXXXXX subscription."),
			Identity: &blueprint.ManagedServiceIdentityArgs{
				Type: pulumi.String("SystemAssigned"),
			},
			Location: pulumi.String("eastus"),
			Parameters: blueprint.ParameterValueMap{
				"costCenter": &blueprint.ParameterValueArgs{
					Value: pulumi.Any("Contoso/Online/Shopping/Production"),
				},
				"owners": &blueprint.ParameterValueArgs{
					Value: pulumi.Any{
						"johnDoe@contoso.com",
						"johnsteam@contoso.com",
					},
				},
				"storageAccountType": &blueprint.ParameterValueArgs{
					Value: pulumi.Any("Standard_LRS"),
				},
			},
			ResourceGroups: blueprint.ResourceGroupValueMap{
				"storageRG": &blueprint.ResourceGroupValueArgs{
					Location: pulumi.String("eastus"),
					Name:     pulumi.String("defaultRG"),
				},
			},
			ResourceScope: pulumi.String("subscriptions/00000000-0000-0000-0000-000000000000"),
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
import com.pulumi.azurenative.blueprint.Assignment;
import com.pulumi.azurenative.blueprint.AssignmentArgs;
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
        var assignment = new Assignment("assignment", AssignmentArgs.builder()        
            .assignmentName("assignSimpleBlueprint")
            .blueprintId("/providers/Microsoft.Management/managementGroups/ContosoOnlineGroup/providers/Microsoft.Blueprint/blueprints/simpleBlueprint")
            .description("enforce pre-defined simpleBlueprint to this XXXXXXXX subscription.")
            .identity(Map.of("type", "SystemAssigned"))
            .location("eastus")
            .parameters(Map.ofEntries(
                Map.entry("costCenter", Map.of("value", "Contoso/Online/Shopping/Production")),
                Map.entry("owners", Map.of("value",                 
                    "johnDoe@contoso.com",
                    "johnsteam@contoso.com")),
                Map.entry("storageAccountType", Map.of("value", "Standard_LRS"))
            ))
            .resourceGroups(Map.of("storageRG", Map.ofEntries(
                Map.entry("location", "eastus"),
                Map.entry("name", "defaultRG")
            )))
            .resourceScope("subscriptions/00000000-0000-0000-0000-000000000000")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const assignment = new azure_native.blueprint.Assignment("assignment", {
    assignmentName: "assignSimpleBlueprint",
    blueprintId: "/providers/Microsoft.Management/managementGroups/ContosoOnlineGroup/providers/Microsoft.Blueprint/blueprints/simpleBlueprint",
    description: "enforce pre-defined simpleBlueprint to this XXXXXXXX subscription.",
    identity: {
        type: "SystemAssigned",
    },
    location: "eastus",
    parameters: {
        costCenter: {
            value: "Contoso/Online/Shopping/Production",
        },
        owners: {
            value: [
                "johnDoe@contoso.com",
                "johnsteam@contoso.com",
            ],
        },
        storageAccountType: {
            value: "Standard_LRS",
        },
    },
    resourceGroups: {
        storageRG: {
            location: "eastus",
            name: "defaultRG",
        },
    },
    resourceScope: "subscriptions/00000000-0000-0000-0000-000000000000",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

assignment = azure_native.blueprint.Assignment("assignment",
    assignment_name="assignSimpleBlueprint",
    blueprint_id="/providers/Microsoft.Management/managementGroups/ContosoOnlineGroup/providers/Microsoft.Blueprint/blueprints/simpleBlueprint",
    description="enforce pre-defined simpleBlueprint to this XXXXXXXX subscription.",
    identity=azure_native.blueprint.ManagedServiceIdentityArgs(
        type="SystemAssigned",
    ),
    location="eastus",
    parameters={
        "costCenter": azure_native.blueprint.ParameterValueArgs(
            value="Contoso/Online/Shopping/Production",
        ),
        "owners": azure_native.blueprint.ParameterValueArgs(
            value=[
                "johnDoe@contoso.com",
                "johnsteam@contoso.com",
            ],
        ),
        "storageAccountType": azure_native.blueprint.ParameterValueArgs(
            value="Standard_LRS",
        ),
    },
    resource_groups={
        "storageRG": azure_native.blueprint.ResourceGroupValueArgs(
            location="eastus",
            name="defaultRG",
        ),
    },
    resource_scope="subscriptions/00000000-0000-0000-0000-000000000000")

```

```yaml
resources:
  assignment:
    type: azure-native:blueprint:Assignment
    properties:
      assignmentName: assignSimpleBlueprint
      blueprintId: /providers/Microsoft.Management/managementGroups/ContosoOnlineGroup/providers/Microsoft.Blueprint/blueprints/simpleBlueprint
      description: enforce pre-defined simpleBlueprint to this XXXXXXXX subscription.
      identity:
        type: SystemAssigned
      location: eastus
      parameters:
        costCenter:
          value: Contoso/Online/Shopping/Production
        owners:
          value:
            - johnDoe@contoso.com
            - johnsteam@contoso.com
        storageAccountType:
          value: Standard_LRS
      resourceGroups:
        storageRG:
          location: eastus
          name: defaultRG
      resourceScope: subscriptions/00000000-0000-0000-0000-000000000000

```

{{% /example %}}
{{% example %}}
### Assignment with user-assigned managed identity at management group scope
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var assignment = new AzureNative.Blueprint.Assignment("assignment", new()
    {
        AssignmentName = "assignSimpleBlueprint",
        BlueprintId = "/providers/Microsoft.Management/managementGroups/ContosoOnlineGroup/providers/Microsoft.Blueprint/blueprints/simpleBlueprint",
        Description = "enforce pre-defined simpleBlueprint to this XXXXXXXX subscription.",
        Identity = new AzureNative.Blueprint.Inputs.ManagedServiceIdentityArgs
        {
            Type = "UserAssigned",
            UserAssignedIdentities = 
            {
                { "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/contoso-resource-group/providers/Microsoft.ManagedIdentity/userAssignedIdentities/contoso-identity", null },
            },
        },
        Location = "eastus",
        Parameters = 
        {
            { "costCenter", new AzureNative.Blueprint.Inputs.ParameterValueArgs
            {
                Value = "Contoso/Online/Shopping/Production",
            } },
            { "owners", new AzureNative.Blueprint.Inputs.ParameterValueArgs
            {
                Value = new[]
                {
                    "johnDoe@contoso.com",
                    "johnsteam@contoso.com",
                },
            } },
            { "storageAccountType", new AzureNative.Blueprint.Inputs.ParameterValueArgs
            {
                Value = "Standard_LRS",
            } },
        },
        ResourceGroups = 
        {
            { "storageRG", new AzureNative.Blueprint.Inputs.ResourceGroupValueArgs
            {
                Location = "eastus",
                Name = "defaultRG",
            } },
        },
        ResourceScope = "managementGroups/ContosoOnlineGroup",
        Scope = "subscriptions/00000000-0000-0000-0000-000000000000",
    });

});


```

```go
package main

import (
	blueprint "github.com/pulumi/pulumi-azure-native-sdk/blueprint"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := blueprint.NewAssignment(ctx, "assignment", &blueprint.AssignmentArgs{
			AssignmentName: pulumi.String("assignSimpleBlueprint"),
			BlueprintId:    pulumi.String("/providers/Microsoft.Management/managementGroups/ContosoOnlineGroup/providers/Microsoft.Blueprint/blueprints/simpleBlueprint"),
			Description:    pulumi.String("enforce pre-defined simpleBlueprint to this XXXXXXXX subscription."),
			Identity: blueprint.ManagedServiceIdentityResponse{
				Type: pulumi.String("UserAssigned"),
				UserAssignedIdentities: blueprint.UserAssignedIdentityMap{
					"/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/contoso-resource-group/providers/Microsoft.ManagedIdentity/userAssignedIdentities/contoso-identity": nil,
				},
			},
			Location: pulumi.String("eastus"),
			Parameters: blueprint.ParameterValueMap{
				"costCenter": &blueprint.ParameterValueArgs{
					Value: pulumi.Any("Contoso/Online/Shopping/Production"),
				},
				"owners": &blueprint.ParameterValueArgs{
					Value: pulumi.Any{
						"johnDoe@contoso.com",
						"johnsteam@contoso.com",
					},
				},
				"storageAccountType": &blueprint.ParameterValueArgs{
					Value: pulumi.Any("Standard_LRS"),
				},
			},
			ResourceGroups: blueprint.ResourceGroupValueMap{
				"storageRG": &blueprint.ResourceGroupValueArgs{
					Location: pulumi.String("eastus"),
					Name:     pulumi.String("defaultRG"),
				},
			},
			ResourceScope: pulumi.String("managementGroups/ContosoOnlineGroup"),
			Scope:         pulumi.String("subscriptions/00000000-0000-0000-0000-000000000000"),
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
import com.pulumi.azurenative.blueprint.Assignment;
import com.pulumi.azurenative.blueprint.AssignmentArgs;
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
        var assignment = new Assignment("assignment", AssignmentArgs.builder()        
            .assignmentName("assignSimpleBlueprint")
            .blueprintId("/providers/Microsoft.Management/managementGroups/ContosoOnlineGroup/providers/Microsoft.Blueprint/blueprints/simpleBlueprint")
            .description("enforce pre-defined simpleBlueprint to this XXXXXXXX subscription.")
            .identity(Map.ofEntries(
                Map.entry("type", "UserAssigned"),
                Map.entry("userAssignedIdentities", Map.of("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/contoso-resource-group/providers/Microsoft.ManagedIdentity/userAssignedIdentities/contoso-identity", ))
            ))
            .location("eastus")
            .parameters(Map.ofEntries(
                Map.entry("costCenter", Map.of("value", "Contoso/Online/Shopping/Production")),
                Map.entry("owners", Map.of("value",                 
                    "johnDoe@contoso.com",
                    "johnsteam@contoso.com")),
                Map.entry("storageAccountType", Map.of("value", "Standard_LRS"))
            ))
            .resourceGroups(Map.of("storageRG", Map.ofEntries(
                Map.entry("location", "eastus"),
                Map.entry("name", "defaultRG")
            )))
            .resourceScope("managementGroups/ContosoOnlineGroup")
            .scope("subscriptions/00000000-0000-0000-0000-000000000000")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const assignment = new azure_native.blueprint.Assignment("assignment", {
    assignmentName: "assignSimpleBlueprint",
    blueprintId: "/providers/Microsoft.Management/managementGroups/ContosoOnlineGroup/providers/Microsoft.Blueprint/blueprints/simpleBlueprint",
    description: "enforce pre-defined simpleBlueprint to this XXXXXXXX subscription.",
    identity: {
        type: "UserAssigned",
        userAssignedIdentities: {
            "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/contoso-resource-group/providers/Microsoft.ManagedIdentity/userAssignedIdentities/contoso-identity": {},
        },
    },
    location: "eastus",
    parameters: {
        costCenter: {
            value: "Contoso/Online/Shopping/Production",
        },
        owners: {
            value: [
                "johnDoe@contoso.com",
                "johnsteam@contoso.com",
            ],
        },
        storageAccountType: {
            value: "Standard_LRS",
        },
    },
    resourceGroups: {
        storageRG: {
            location: "eastus",
            name: "defaultRG",
        },
    },
    resourceScope: "managementGroups/ContosoOnlineGroup",
    scope: "subscriptions/00000000-0000-0000-0000-000000000000",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

assignment = azure_native.blueprint.Assignment("assignment",
    assignment_name="assignSimpleBlueprint",
    blueprint_id="/providers/Microsoft.Management/managementGroups/ContosoOnlineGroup/providers/Microsoft.Blueprint/blueprints/simpleBlueprint",
    description="enforce pre-defined simpleBlueprint to this XXXXXXXX subscription.",
    identity=azure_native.blueprint.ManagedServiceIdentityResponseArgs(
        type="UserAssigned",
        user_assigned_identities={
            "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/contoso-resource-group/providers/Microsoft.ManagedIdentity/userAssignedIdentities/contoso-identity": azure_native.blueprint.UserAssignedIdentityArgs(),
        },
    ),
    location="eastus",
    parameters={
        "costCenter": azure_native.blueprint.ParameterValueArgs(
            value="Contoso/Online/Shopping/Production",
        ),
        "owners": azure_native.blueprint.ParameterValueArgs(
            value=[
                "johnDoe@contoso.com",
                "johnsteam@contoso.com",
            ],
        ),
        "storageAccountType": azure_native.blueprint.ParameterValueArgs(
            value="Standard_LRS",
        ),
    },
    resource_groups={
        "storageRG": azure_native.blueprint.ResourceGroupValueArgs(
            location="eastus",
            name="defaultRG",
        ),
    },
    resource_scope="managementGroups/ContosoOnlineGroup",
    scope="subscriptions/00000000-0000-0000-0000-000000000000")

```

```yaml
resources:
  assignment:
    type: azure-native:blueprint:Assignment
    properties:
      assignmentName: assignSimpleBlueprint
      blueprintId: /providers/Microsoft.Management/managementGroups/ContosoOnlineGroup/providers/Microsoft.Blueprint/blueprints/simpleBlueprint
      description: enforce pre-defined simpleBlueprint to this XXXXXXXX subscription.
      identity:
        type: UserAssigned
        userAssignedIdentities:
          ? /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/contoso-resource-group/providers/Microsoft.ManagedIdentity/userAssignedIdentities/contoso-identity
          : {}
      location: eastus
      parameters:
        costCenter:
          value: Contoso/Online/Shopping/Production
        owners:
          value:
            - johnDoe@contoso.com
            - johnsteam@contoso.com
        storageAccountType:
          value: Standard_LRS
      resourceGroups:
        storageRG:
          location: eastus
          name: defaultRG
      resourceScope: managementGroups/ContosoOnlineGroup
      scope: subscriptions/00000000-0000-0000-0000-000000000000

```

{{% /example %}}
{{% example %}}
### Assignment with user-assigned managed identity at subscription scope
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var assignment = new AzureNative.Blueprint.Assignment("assignment", new()
    {
        AssignmentName = "assignSimpleBlueprint",
        BlueprintId = "/providers/Microsoft.Management/managementGroups/ContosoOnlineGroup/providers/Microsoft.Blueprint/blueprints/simpleBlueprint",
        Description = "enforce pre-defined simpleBlueprint to this XXXXXXXX subscription.",
        Identity = new AzureNative.Blueprint.Inputs.ManagedServiceIdentityArgs
        {
            Type = "UserAssigned",
            UserAssignedIdentities = 
            {
                { "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/contoso-resource-group/providers/Microsoft.ManagedIdentity/userAssignedIdentities/contoso-identity", null },
            },
        },
        Location = "eastus",
        Parameters = 
        {
            { "costCenter", new AzureNative.Blueprint.Inputs.ParameterValueArgs
            {
                Value = "Contoso/Online/Shopping/Production",
            } },
            { "owners", new AzureNative.Blueprint.Inputs.ParameterValueArgs
            {
                Value = new[]
                {
                    "johnDoe@contoso.com",
                    "johnsteam@contoso.com",
                },
            } },
            { "storageAccountType", new AzureNative.Blueprint.Inputs.ParameterValueArgs
            {
                Value = "Standard_LRS",
            } },
        },
        ResourceGroups = 
        {
            { "storageRG", new AzureNative.Blueprint.Inputs.ResourceGroupValueArgs
            {
                Location = "eastus",
                Name = "defaultRG",
            } },
        },
        ResourceScope = "subscriptions/00000000-0000-0000-0000-000000000000",
    });

});


```

```go
package main

import (
	blueprint "github.com/pulumi/pulumi-azure-native-sdk/blueprint"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := blueprint.NewAssignment(ctx, "assignment", &blueprint.AssignmentArgs{
			AssignmentName: pulumi.String("assignSimpleBlueprint"),
			BlueprintId:    pulumi.String("/providers/Microsoft.Management/managementGroups/ContosoOnlineGroup/providers/Microsoft.Blueprint/blueprints/simpleBlueprint"),
			Description:    pulumi.String("enforce pre-defined simpleBlueprint to this XXXXXXXX subscription."),
			Identity: blueprint.ManagedServiceIdentityResponse{
				Type: pulumi.String("UserAssigned"),
				UserAssignedIdentities: blueprint.UserAssignedIdentityMap{
					"/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/contoso-resource-group/providers/Microsoft.ManagedIdentity/userAssignedIdentities/contoso-identity": nil,
				},
			},
			Location: pulumi.String("eastus"),
			Parameters: blueprint.ParameterValueMap{
				"costCenter": &blueprint.ParameterValueArgs{
					Value: pulumi.Any("Contoso/Online/Shopping/Production"),
				},
				"owners": &blueprint.ParameterValueArgs{
					Value: pulumi.Any{
						"johnDoe@contoso.com",
						"johnsteam@contoso.com",
					},
				},
				"storageAccountType": &blueprint.ParameterValueArgs{
					Value: pulumi.Any("Standard_LRS"),
				},
			},
			ResourceGroups: blueprint.ResourceGroupValueMap{
				"storageRG": &blueprint.ResourceGroupValueArgs{
					Location: pulumi.String("eastus"),
					Name:     pulumi.String("defaultRG"),
				},
			},
			ResourceScope: pulumi.String("subscriptions/00000000-0000-0000-0000-000000000000"),
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
import com.pulumi.azurenative.blueprint.Assignment;
import com.pulumi.azurenative.blueprint.AssignmentArgs;
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
        var assignment = new Assignment("assignment", AssignmentArgs.builder()        
            .assignmentName("assignSimpleBlueprint")
            .blueprintId("/providers/Microsoft.Management/managementGroups/ContosoOnlineGroup/providers/Microsoft.Blueprint/blueprints/simpleBlueprint")
            .description("enforce pre-defined simpleBlueprint to this XXXXXXXX subscription.")
            .identity(Map.ofEntries(
                Map.entry("type", "UserAssigned"),
                Map.entry("userAssignedIdentities", Map.of("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/contoso-resource-group/providers/Microsoft.ManagedIdentity/userAssignedIdentities/contoso-identity", ))
            ))
            .location("eastus")
            .parameters(Map.ofEntries(
                Map.entry("costCenter", Map.of("value", "Contoso/Online/Shopping/Production")),
                Map.entry("owners", Map.of("value",                 
                    "johnDoe@contoso.com",
                    "johnsteam@contoso.com")),
                Map.entry("storageAccountType", Map.of("value", "Standard_LRS"))
            ))
            .resourceGroups(Map.of("storageRG", Map.ofEntries(
                Map.entry("location", "eastus"),
                Map.entry("name", "defaultRG")
            )))
            .resourceScope("subscriptions/00000000-0000-0000-0000-000000000000")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const assignment = new azure_native.blueprint.Assignment("assignment", {
    assignmentName: "assignSimpleBlueprint",
    blueprintId: "/providers/Microsoft.Management/managementGroups/ContosoOnlineGroup/providers/Microsoft.Blueprint/blueprints/simpleBlueprint",
    description: "enforce pre-defined simpleBlueprint to this XXXXXXXX subscription.",
    identity: {
        type: "UserAssigned",
        userAssignedIdentities: {
            "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/contoso-resource-group/providers/Microsoft.ManagedIdentity/userAssignedIdentities/contoso-identity": {},
        },
    },
    location: "eastus",
    parameters: {
        costCenter: {
            value: "Contoso/Online/Shopping/Production",
        },
        owners: {
            value: [
                "johnDoe@contoso.com",
                "johnsteam@contoso.com",
            ],
        },
        storageAccountType: {
            value: "Standard_LRS",
        },
    },
    resourceGroups: {
        storageRG: {
            location: "eastus",
            name: "defaultRG",
        },
    },
    resourceScope: "subscriptions/00000000-0000-0000-0000-000000000000",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

assignment = azure_native.blueprint.Assignment("assignment",
    assignment_name="assignSimpleBlueprint",
    blueprint_id="/providers/Microsoft.Management/managementGroups/ContosoOnlineGroup/providers/Microsoft.Blueprint/blueprints/simpleBlueprint",
    description="enforce pre-defined simpleBlueprint to this XXXXXXXX subscription.",
    identity=azure_native.blueprint.ManagedServiceIdentityResponseArgs(
        type="UserAssigned",
        user_assigned_identities={
            "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/contoso-resource-group/providers/Microsoft.ManagedIdentity/userAssignedIdentities/contoso-identity": azure_native.blueprint.UserAssignedIdentityArgs(),
        },
    ),
    location="eastus",
    parameters={
        "costCenter": azure_native.blueprint.ParameterValueArgs(
            value="Contoso/Online/Shopping/Production",
        ),
        "owners": azure_native.blueprint.ParameterValueArgs(
            value=[
                "johnDoe@contoso.com",
                "johnsteam@contoso.com",
            ],
        ),
        "storageAccountType": azure_native.blueprint.ParameterValueArgs(
            value="Standard_LRS",
        ),
    },
    resource_groups={
        "storageRG": azure_native.blueprint.ResourceGroupValueArgs(
            location="eastus",
            name="defaultRG",
        ),
    },
    resource_scope="subscriptions/00000000-0000-0000-0000-000000000000")

```

```yaml
resources:
  assignment:
    type: azure-native:blueprint:Assignment
    properties:
      assignmentName: assignSimpleBlueprint
      blueprintId: /providers/Microsoft.Management/managementGroups/ContosoOnlineGroup/providers/Microsoft.Blueprint/blueprints/simpleBlueprint
      description: enforce pre-defined simpleBlueprint to this XXXXXXXX subscription.
      identity:
        type: UserAssigned
        userAssignedIdentities:
          ? /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/contoso-resource-group/providers/Microsoft.ManagedIdentity/userAssignedIdentities/contoso-identity
          : {}
      location: eastus
      parameters:
        costCenter:
          value: Contoso/Online/Shopping/Production
        owners:
          value:
            - johnDoe@contoso.com
            - johnsteam@contoso.com
        storageAccountType:
          value: Standard_LRS
      resourceGroups:
        storageRG:
          location: eastus
          name: defaultRG
      resourceScope: subscriptions/00000000-0000-0000-0000-000000000000

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:blueprint:Assignment assignSimpleBlueprint /subscriptions/00000000-0000-0000-0000-000000000000/providers/Microsoft.Blueprint/blueprintAssignments/assignSimpleBlueprint 
```
