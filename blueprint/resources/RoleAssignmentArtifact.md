Blueprint artifact that applies a Role assignment.
API Version: 2018-11-01-preview.
Previous API Version: 2018-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### MG-ARMTemplateArtifact
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var roleAssignmentArtifact = new AzureNative.Blueprint.RoleAssignmentArtifact("roleAssignmentArtifact", new()
    {
        ArtifactName = "storageTemplate",
        BlueprintName = "simpleBlueprint",
        ResourceScope = "providers/Microsoft.Management/managementGroups/ContosoOnlineGroup",
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
		_, err := blueprint.NewRoleAssignmentArtifact(ctx, "roleAssignmentArtifact", &blueprint.RoleAssignmentArtifactArgs{
			ArtifactName:  pulumi.String("storageTemplate"),
			BlueprintName: pulumi.String("simpleBlueprint"),
			ResourceScope: pulumi.String("providers/Microsoft.Management/managementGroups/ContosoOnlineGroup"),
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
import com.pulumi.azurenative.blueprint.RoleAssignmentArtifact;
import com.pulumi.azurenative.blueprint.RoleAssignmentArtifactArgs;
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
        var roleAssignmentArtifact = new RoleAssignmentArtifact("roleAssignmentArtifact", RoleAssignmentArtifactArgs.builder()        
            .artifactName("storageTemplate")
            .blueprintName("simpleBlueprint")
            .resourceScope("providers/Microsoft.Management/managementGroups/ContosoOnlineGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const roleAssignmentArtifact = new azure_native.blueprint.RoleAssignmentArtifact("roleAssignmentArtifact", {
    artifactName: "storageTemplate",
    blueprintName: "simpleBlueprint",
    resourceScope: "providers/Microsoft.Management/managementGroups/ContosoOnlineGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

role_assignment_artifact = azure_native.blueprint.RoleAssignmentArtifact("roleAssignmentArtifact",
    artifact_name="storageTemplate",
    blueprint_name="simpleBlueprint",
    resource_scope="providers/Microsoft.Management/managementGroups/ContosoOnlineGroup")

```

```yaml
resources:
  roleAssignmentArtifact:
    type: azure-native:blueprint:RoleAssignmentArtifact
    properties:
      artifactName: storageTemplate
      blueprintName: simpleBlueprint
      resourceScope: providers/Microsoft.Management/managementGroups/ContosoOnlineGroup

```

{{% /example %}}
{{% example %}}
### MG-PolicyAssignmentArtifact
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var roleAssignmentArtifact = new AzureNative.Blueprint.RoleAssignmentArtifact("roleAssignmentArtifact", new()
    {
        ArtifactName = "costCenterPolicy",
        BlueprintName = "simpleBlueprint",
        ResourceScope = "providers/Microsoft.Management/managementGroups/ContosoOnlineGroup",
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
		_, err := blueprint.NewRoleAssignmentArtifact(ctx, "roleAssignmentArtifact", &blueprint.RoleAssignmentArtifactArgs{
			ArtifactName:  pulumi.String("costCenterPolicy"),
			BlueprintName: pulumi.String("simpleBlueprint"),
			ResourceScope: pulumi.String("providers/Microsoft.Management/managementGroups/ContosoOnlineGroup"),
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
import com.pulumi.azurenative.blueprint.RoleAssignmentArtifact;
import com.pulumi.azurenative.blueprint.RoleAssignmentArtifactArgs;
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
        var roleAssignmentArtifact = new RoleAssignmentArtifact("roleAssignmentArtifact", RoleAssignmentArtifactArgs.builder()        
            .artifactName("costCenterPolicy")
            .blueprintName("simpleBlueprint")
            .resourceScope("providers/Microsoft.Management/managementGroups/ContosoOnlineGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const roleAssignmentArtifact = new azure_native.blueprint.RoleAssignmentArtifact("roleAssignmentArtifact", {
    artifactName: "costCenterPolicy",
    blueprintName: "simpleBlueprint",
    resourceScope: "providers/Microsoft.Management/managementGroups/ContosoOnlineGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

role_assignment_artifact = azure_native.blueprint.RoleAssignmentArtifact("roleAssignmentArtifact",
    artifact_name="costCenterPolicy",
    blueprint_name="simpleBlueprint",
    resource_scope="providers/Microsoft.Management/managementGroups/ContosoOnlineGroup")

```

```yaml
resources:
  roleAssignmentArtifact:
    type: azure-native:blueprint:RoleAssignmentArtifact
    properties:
      artifactName: costCenterPolicy
      blueprintName: simpleBlueprint
      resourceScope: providers/Microsoft.Management/managementGroups/ContosoOnlineGroup

```

{{% /example %}}
{{% example %}}
### MG-RoleAssignmentArtifact
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var roleAssignmentArtifact = new AzureNative.Blueprint.RoleAssignmentArtifact("roleAssignmentArtifact", new()
    {
        ArtifactName = "ownerAssignment",
        BlueprintName = "simpleBlueprint",
        DisplayName = "enforce owners of given subscription",
        Kind = "roleAssignment",
        PrincipalIds = "[parameters('owners')]",
        ResourceScope = "providers/Microsoft.Management/managementGroups/ContosoOnlineGroup",
        RoleDefinitionId = "/providers/Microsoft.Authorization/roleDefinitions/acdd72a7-3385-48ef-bd42-f606fba81ae7",
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
		_, err := blueprint.NewRoleAssignmentArtifact(ctx, "roleAssignmentArtifact", &blueprint.RoleAssignmentArtifactArgs{
			ArtifactName:     pulumi.String("ownerAssignment"),
			BlueprintName:    pulumi.String("simpleBlueprint"),
			DisplayName:      pulumi.String("enforce owners of given subscription"),
			Kind:             pulumi.String("roleAssignment"),
			PrincipalIds:     pulumi.Any("[parameters('owners')]"),
			ResourceScope:    pulumi.String("providers/Microsoft.Management/managementGroups/ContosoOnlineGroup"),
			RoleDefinitionId: pulumi.String("/providers/Microsoft.Authorization/roleDefinitions/acdd72a7-3385-48ef-bd42-f606fba81ae7"),
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
import com.pulumi.azurenative.blueprint.RoleAssignmentArtifact;
import com.pulumi.azurenative.blueprint.RoleAssignmentArtifactArgs;
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
        var roleAssignmentArtifact = new RoleAssignmentArtifact("roleAssignmentArtifact", RoleAssignmentArtifactArgs.builder()        
            .artifactName("ownerAssignment")
            .blueprintName("simpleBlueprint")
            .displayName("enforce owners of given subscription")
            .kind("roleAssignment")
            .principalIds("[parameters('owners')]")
            .resourceScope("providers/Microsoft.Management/managementGroups/ContosoOnlineGroup")
            .roleDefinitionId("/providers/Microsoft.Authorization/roleDefinitions/acdd72a7-3385-48ef-bd42-f606fba81ae7")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const roleAssignmentArtifact = new azure_native.blueprint.RoleAssignmentArtifact("roleAssignmentArtifact", {
    artifactName: "ownerAssignment",
    blueprintName: "simpleBlueprint",
    displayName: "enforce owners of given subscription",
    kind: "roleAssignment",
    principalIds: "[parameters('owners')]",
    resourceScope: "providers/Microsoft.Management/managementGroups/ContosoOnlineGroup",
    roleDefinitionId: "/providers/Microsoft.Authorization/roleDefinitions/acdd72a7-3385-48ef-bd42-f606fba81ae7",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

role_assignment_artifact = azure_native.blueprint.RoleAssignmentArtifact("roleAssignmentArtifact",
    artifact_name="ownerAssignment",
    blueprint_name="simpleBlueprint",
    display_name="enforce owners of given subscription",
    kind="roleAssignment",
    principal_ids="[parameters('owners')]",
    resource_scope="providers/Microsoft.Management/managementGroups/ContosoOnlineGroup",
    role_definition_id="/providers/Microsoft.Authorization/roleDefinitions/acdd72a7-3385-48ef-bd42-f606fba81ae7")

```

```yaml
resources:
  roleAssignmentArtifact:
    type: azure-native:blueprint:RoleAssignmentArtifact
    properties:
      artifactName: ownerAssignment
      blueprintName: simpleBlueprint
      displayName: enforce owners of given subscription
      kind: roleAssignment
      principalIds: '[parameters(''owners'')]'
      resourceScope: providers/Microsoft.Management/managementGroups/ContosoOnlineGroup
      roleDefinitionId: /providers/Microsoft.Authorization/roleDefinitions/acdd72a7-3385-48ef-bd42-f606fba81ae7

```

{{% /example %}}
{{% example %}}
### Sub-ARMTemplateArtifact
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var roleAssignmentArtifact = new AzureNative.Blueprint.RoleAssignmentArtifact("roleAssignmentArtifact", new()
    {
        ArtifactName = "storageTemplate",
        BlueprintName = "simpleBlueprint",
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
		_, err := blueprint.NewRoleAssignmentArtifact(ctx, "roleAssignmentArtifact", &blueprint.RoleAssignmentArtifactArgs{
			ArtifactName:  pulumi.String("storageTemplate"),
			BlueprintName: pulumi.String("simpleBlueprint"),
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
import com.pulumi.azurenative.blueprint.RoleAssignmentArtifact;
import com.pulumi.azurenative.blueprint.RoleAssignmentArtifactArgs;
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
        var roleAssignmentArtifact = new RoleAssignmentArtifact("roleAssignmentArtifact", RoleAssignmentArtifactArgs.builder()        
            .artifactName("storageTemplate")
            .blueprintName("simpleBlueprint")
            .resourceScope("subscriptions/00000000-0000-0000-0000-000000000000")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const roleAssignmentArtifact = new azure_native.blueprint.RoleAssignmentArtifact("roleAssignmentArtifact", {
    artifactName: "storageTemplate",
    blueprintName: "simpleBlueprint",
    resourceScope: "subscriptions/00000000-0000-0000-0000-000000000000",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

role_assignment_artifact = azure_native.blueprint.RoleAssignmentArtifact("roleAssignmentArtifact",
    artifact_name="storageTemplate",
    blueprint_name="simpleBlueprint",
    resource_scope="subscriptions/00000000-0000-0000-0000-000000000000")

```

```yaml
resources:
  roleAssignmentArtifact:
    type: azure-native:blueprint:RoleAssignmentArtifact
    properties:
      artifactName: storageTemplate
      blueprintName: simpleBlueprint
      resourceScope: subscriptions/00000000-0000-0000-0000-000000000000

```

{{% /example %}}
{{% example %}}
### Sub-PolicyAssignmentArtifact
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var roleAssignmentArtifact = new AzureNative.Blueprint.RoleAssignmentArtifact("roleAssignmentArtifact", new()
    {
        ArtifactName = "costCenterPolicy",
        BlueprintName = "simpleBlueprint",
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
		_, err := blueprint.NewRoleAssignmentArtifact(ctx, "roleAssignmentArtifact", &blueprint.RoleAssignmentArtifactArgs{
			ArtifactName:  pulumi.String("costCenterPolicy"),
			BlueprintName: pulumi.String("simpleBlueprint"),
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
import com.pulumi.azurenative.blueprint.RoleAssignmentArtifact;
import com.pulumi.azurenative.blueprint.RoleAssignmentArtifactArgs;
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
        var roleAssignmentArtifact = new RoleAssignmentArtifact("roleAssignmentArtifact", RoleAssignmentArtifactArgs.builder()        
            .artifactName("costCenterPolicy")
            .blueprintName("simpleBlueprint")
            .resourceScope("subscriptions/00000000-0000-0000-0000-000000000000")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const roleAssignmentArtifact = new azure_native.blueprint.RoleAssignmentArtifact("roleAssignmentArtifact", {
    artifactName: "costCenterPolicy",
    blueprintName: "simpleBlueprint",
    resourceScope: "subscriptions/00000000-0000-0000-0000-000000000000",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

role_assignment_artifact = azure_native.blueprint.RoleAssignmentArtifact("roleAssignmentArtifact",
    artifact_name="costCenterPolicy",
    blueprint_name="simpleBlueprint",
    resource_scope="subscriptions/00000000-0000-0000-0000-000000000000")

```

```yaml
resources:
  roleAssignmentArtifact:
    type: azure-native:blueprint:RoleAssignmentArtifact
    properties:
      artifactName: costCenterPolicy
      blueprintName: simpleBlueprint
      resourceScope: subscriptions/00000000-0000-0000-0000-000000000000

```

{{% /example %}}
{{% example %}}
### Sub-RoleAssignmentArtifact
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var roleAssignmentArtifact = new AzureNative.Blueprint.RoleAssignmentArtifact("roleAssignmentArtifact", new()
    {
        ArtifactName = "ownerAssignment",
        BlueprintName = "simpleBlueprint",
        DisplayName = "enforce owners of given subscription",
        Kind = "roleAssignment",
        PrincipalIds = "[parameters('owners')]",
        ResourceScope = "subscriptions/00000000-0000-0000-0000-000000000000",
        RoleDefinitionId = "/providers/Microsoft.Authorization/roleDefinitions/acdd72a7-3385-48ef-bd42-f606fba81ae7",
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
		_, err := blueprint.NewRoleAssignmentArtifact(ctx, "roleAssignmentArtifact", &blueprint.RoleAssignmentArtifactArgs{
			ArtifactName:     pulumi.String("ownerAssignment"),
			BlueprintName:    pulumi.String("simpleBlueprint"),
			DisplayName:      pulumi.String("enforce owners of given subscription"),
			Kind:             pulumi.String("roleAssignment"),
			PrincipalIds:     pulumi.Any("[parameters('owners')]"),
			ResourceScope:    pulumi.String("subscriptions/00000000-0000-0000-0000-000000000000"),
			RoleDefinitionId: pulumi.String("/providers/Microsoft.Authorization/roleDefinitions/acdd72a7-3385-48ef-bd42-f606fba81ae7"),
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
import com.pulumi.azurenative.blueprint.RoleAssignmentArtifact;
import com.pulumi.azurenative.blueprint.RoleAssignmentArtifactArgs;
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
        var roleAssignmentArtifact = new RoleAssignmentArtifact("roleAssignmentArtifact", RoleAssignmentArtifactArgs.builder()        
            .artifactName("ownerAssignment")
            .blueprintName("simpleBlueprint")
            .displayName("enforce owners of given subscription")
            .kind("roleAssignment")
            .principalIds("[parameters('owners')]")
            .resourceScope("subscriptions/00000000-0000-0000-0000-000000000000")
            .roleDefinitionId("/providers/Microsoft.Authorization/roleDefinitions/acdd72a7-3385-48ef-bd42-f606fba81ae7")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const roleAssignmentArtifact = new azure_native.blueprint.RoleAssignmentArtifact("roleAssignmentArtifact", {
    artifactName: "ownerAssignment",
    blueprintName: "simpleBlueprint",
    displayName: "enforce owners of given subscription",
    kind: "roleAssignment",
    principalIds: "[parameters('owners')]",
    resourceScope: "subscriptions/00000000-0000-0000-0000-000000000000",
    roleDefinitionId: "/providers/Microsoft.Authorization/roleDefinitions/acdd72a7-3385-48ef-bd42-f606fba81ae7",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

role_assignment_artifact = azure_native.blueprint.RoleAssignmentArtifact("roleAssignmentArtifact",
    artifact_name="ownerAssignment",
    blueprint_name="simpleBlueprint",
    display_name="enforce owners of given subscription",
    kind="roleAssignment",
    principal_ids="[parameters('owners')]",
    resource_scope="subscriptions/00000000-0000-0000-0000-000000000000",
    role_definition_id="/providers/Microsoft.Authorization/roleDefinitions/acdd72a7-3385-48ef-bd42-f606fba81ae7")

```

```yaml
resources:
  roleAssignmentArtifact:
    type: azure-native:blueprint:RoleAssignmentArtifact
    properties:
      artifactName: ownerAssignment
      blueprintName: simpleBlueprint
      displayName: enforce owners of given subscription
      kind: roleAssignment
      principalIds: '[parameters(''owners'')]'
      resourceScope: subscriptions/00000000-0000-0000-0000-000000000000
      roleDefinitionId: /providers/Microsoft.Authorization/roleDefinitions/acdd72a7-3385-48ef-bd42-f606fba81ae7

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:blueprint:RoleAssignmentArtifact ownerAssignment /subscriptions/00000000-0000-0000-0000-000000000000/providers/Microsoft.Blueprint/blueprints/simpleBlueprint/artifacts/ownerAssignment 
```
