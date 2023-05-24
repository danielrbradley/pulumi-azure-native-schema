Blueprint artifact that applies a Policy assignment.
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
    var policyAssignmentArtifact = new AzureNative.Blueprint.PolicyAssignmentArtifact("policyAssignmentArtifact", new()
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
		_, err := blueprint.NewPolicyAssignmentArtifact(ctx, "policyAssignmentArtifact", &blueprint.PolicyAssignmentArtifactArgs{
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
import com.pulumi.azurenative.blueprint.PolicyAssignmentArtifact;
import com.pulumi.azurenative.blueprint.PolicyAssignmentArtifactArgs;
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
        var policyAssignmentArtifact = new PolicyAssignmentArtifact("policyAssignmentArtifact", PolicyAssignmentArtifactArgs.builder()        
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

const policyAssignmentArtifact = new azure_native.blueprint.PolicyAssignmentArtifact("policyAssignmentArtifact", {
    artifactName: "storageTemplate",
    blueprintName: "simpleBlueprint",
    resourceScope: "providers/Microsoft.Management/managementGroups/ContosoOnlineGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

policy_assignment_artifact = azure_native.blueprint.PolicyAssignmentArtifact("policyAssignmentArtifact",
    artifact_name="storageTemplate",
    blueprint_name="simpleBlueprint",
    resource_scope="providers/Microsoft.Management/managementGroups/ContosoOnlineGroup")

```

```yaml
resources:
  policyAssignmentArtifact:
    type: azure-native:blueprint:PolicyAssignmentArtifact
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
    var policyAssignmentArtifact = new AzureNative.Blueprint.PolicyAssignmentArtifact("policyAssignmentArtifact", new()
    {
        ArtifactName = "costCenterPolicy",
        BlueprintName = "simpleBlueprint",
        DisplayName = "force costCenter tag on all resources",
        Kind = "policyAssignment",
        Parameters = 
        {
            { "tagName", new AzureNative.Blueprint.Inputs.ParameterValueArgs
            {
                Value = "costCenter",
            } },
            { "tagValue", new AzureNative.Blueprint.Inputs.ParameterValueArgs
            {
                Value = "[parameter('costCenter')]",
            } },
        },
        PolicyDefinitionId = "/providers/Microsoft.Authorization/policyDefinitions/1e30110a-5ceb-460c-a204-c1c3969c6d62",
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
		_, err := blueprint.NewPolicyAssignmentArtifact(ctx, "policyAssignmentArtifact", &blueprint.PolicyAssignmentArtifactArgs{
			ArtifactName:  pulumi.String("costCenterPolicy"),
			BlueprintName: pulumi.String("simpleBlueprint"),
			DisplayName:   pulumi.String("force costCenter tag on all resources"),
			Kind:          pulumi.String("policyAssignment"),
			Parameters: blueprint.ParameterValueMap{
				"tagName": &blueprint.ParameterValueArgs{
					Value: pulumi.Any("costCenter"),
				},
				"tagValue": &blueprint.ParameterValueArgs{
					Value: pulumi.Any("[parameter('costCenter')]"),
				},
			},
			PolicyDefinitionId: pulumi.String("/providers/Microsoft.Authorization/policyDefinitions/1e30110a-5ceb-460c-a204-c1c3969c6d62"),
			ResourceScope:      pulumi.String("providers/Microsoft.Management/managementGroups/ContosoOnlineGroup"),
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
import com.pulumi.azurenative.blueprint.PolicyAssignmentArtifact;
import com.pulumi.azurenative.blueprint.PolicyAssignmentArtifactArgs;
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
        var policyAssignmentArtifact = new PolicyAssignmentArtifact("policyAssignmentArtifact", PolicyAssignmentArtifactArgs.builder()        
            .artifactName("costCenterPolicy")
            .blueprintName("simpleBlueprint")
            .displayName("force costCenter tag on all resources")
            .kind("policyAssignment")
            .parameters(Map.ofEntries(
                Map.entry("tagName", Map.of("value", "costCenter")),
                Map.entry("tagValue", Map.of("value", "[parameter('costCenter')]"))
            ))
            .policyDefinitionId("/providers/Microsoft.Authorization/policyDefinitions/1e30110a-5ceb-460c-a204-c1c3969c6d62")
            .resourceScope("providers/Microsoft.Management/managementGroups/ContosoOnlineGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const policyAssignmentArtifact = new azure_native.blueprint.PolicyAssignmentArtifact("policyAssignmentArtifact", {
    artifactName: "costCenterPolicy",
    blueprintName: "simpleBlueprint",
    displayName: "force costCenter tag on all resources",
    kind: "policyAssignment",
    parameters: {
        tagName: {
            value: "costCenter",
        },
        tagValue: {
            value: "[parameter('costCenter')]",
        },
    },
    policyDefinitionId: "/providers/Microsoft.Authorization/policyDefinitions/1e30110a-5ceb-460c-a204-c1c3969c6d62",
    resourceScope: "providers/Microsoft.Management/managementGroups/ContosoOnlineGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

policy_assignment_artifact = azure_native.blueprint.PolicyAssignmentArtifact("policyAssignmentArtifact",
    artifact_name="costCenterPolicy",
    blueprint_name="simpleBlueprint",
    display_name="force costCenter tag on all resources",
    kind="policyAssignment",
    parameters={
        "tagName": azure_native.blueprint.ParameterValueArgs(
            value="costCenter",
        ),
        "tagValue": azure_native.blueprint.ParameterValueArgs(
            value="[parameter('costCenter')]",
        ),
    },
    policy_definition_id="/providers/Microsoft.Authorization/policyDefinitions/1e30110a-5ceb-460c-a204-c1c3969c6d62",
    resource_scope="providers/Microsoft.Management/managementGroups/ContosoOnlineGroup")

```

```yaml
resources:
  policyAssignmentArtifact:
    type: azure-native:blueprint:PolicyAssignmentArtifact
    properties:
      artifactName: costCenterPolicy
      blueprintName: simpleBlueprint
      displayName: force costCenter tag on all resources
      kind: policyAssignment
      parameters:
        tagName:
          value: costCenter
        tagValue:
          value: '[parameter(''costCenter'')]'
      policyDefinitionId: /providers/Microsoft.Authorization/policyDefinitions/1e30110a-5ceb-460c-a204-c1c3969c6d62
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
    var policyAssignmentArtifact = new AzureNative.Blueprint.PolicyAssignmentArtifact("policyAssignmentArtifact", new()
    {
        ArtifactName = "ownerAssignment",
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
		_, err := blueprint.NewPolicyAssignmentArtifact(ctx, "policyAssignmentArtifact", &blueprint.PolicyAssignmentArtifactArgs{
			ArtifactName:  pulumi.String("ownerAssignment"),
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
import com.pulumi.azurenative.blueprint.PolicyAssignmentArtifact;
import com.pulumi.azurenative.blueprint.PolicyAssignmentArtifactArgs;
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
        var policyAssignmentArtifact = new PolicyAssignmentArtifact("policyAssignmentArtifact", PolicyAssignmentArtifactArgs.builder()        
            .artifactName("ownerAssignment")
            .blueprintName("simpleBlueprint")
            .resourceScope("providers/Microsoft.Management/managementGroups/ContosoOnlineGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const policyAssignmentArtifact = new azure_native.blueprint.PolicyAssignmentArtifact("policyAssignmentArtifact", {
    artifactName: "ownerAssignment",
    blueprintName: "simpleBlueprint",
    resourceScope: "providers/Microsoft.Management/managementGroups/ContosoOnlineGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

policy_assignment_artifact = azure_native.blueprint.PolicyAssignmentArtifact("policyAssignmentArtifact",
    artifact_name="ownerAssignment",
    blueprint_name="simpleBlueprint",
    resource_scope="providers/Microsoft.Management/managementGroups/ContosoOnlineGroup")

```

```yaml
resources:
  policyAssignmentArtifact:
    type: azure-native:blueprint:PolicyAssignmentArtifact
    properties:
      artifactName: ownerAssignment
      blueprintName: simpleBlueprint
      resourceScope: providers/Microsoft.Management/managementGroups/ContosoOnlineGroup

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
    var policyAssignmentArtifact = new AzureNative.Blueprint.PolicyAssignmentArtifact("policyAssignmentArtifact", new()
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
		_, err := blueprint.NewPolicyAssignmentArtifact(ctx, "policyAssignmentArtifact", &blueprint.PolicyAssignmentArtifactArgs{
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
import com.pulumi.azurenative.blueprint.PolicyAssignmentArtifact;
import com.pulumi.azurenative.blueprint.PolicyAssignmentArtifactArgs;
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
        var policyAssignmentArtifact = new PolicyAssignmentArtifact("policyAssignmentArtifact", PolicyAssignmentArtifactArgs.builder()        
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

const policyAssignmentArtifact = new azure_native.blueprint.PolicyAssignmentArtifact("policyAssignmentArtifact", {
    artifactName: "storageTemplate",
    blueprintName: "simpleBlueprint",
    resourceScope: "subscriptions/00000000-0000-0000-0000-000000000000",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

policy_assignment_artifact = azure_native.blueprint.PolicyAssignmentArtifact("policyAssignmentArtifact",
    artifact_name="storageTemplate",
    blueprint_name="simpleBlueprint",
    resource_scope="subscriptions/00000000-0000-0000-0000-000000000000")

```

```yaml
resources:
  policyAssignmentArtifact:
    type: azure-native:blueprint:PolicyAssignmentArtifact
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
    var policyAssignmentArtifact = new AzureNative.Blueprint.PolicyAssignmentArtifact("policyAssignmentArtifact", new()
    {
        ArtifactName = "costCenterPolicy",
        BlueprintName = "simpleBlueprint",
        DisplayName = "force costCenter tag on all resources",
        Kind = "policyAssignment",
        Parameters = 
        {
            { "tagName", new AzureNative.Blueprint.Inputs.ParameterValueArgs
            {
                Value = "costCenter",
            } },
            { "tagValue", new AzureNative.Blueprint.Inputs.ParameterValueArgs
            {
                Value = "[parameter('costCenter')]",
            } },
        },
        PolicyDefinitionId = "/providers/Microsoft.Authorization/policyDefinitions/1e30110a-5ceb-460c-a204-c1c3969c6d62",
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
		_, err := blueprint.NewPolicyAssignmentArtifact(ctx, "policyAssignmentArtifact", &blueprint.PolicyAssignmentArtifactArgs{
			ArtifactName:  pulumi.String("costCenterPolicy"),
			BlueprintName: pulumi.String("simpleBlueprint"),
			DisplayName:   pulumi.String("force costCenter tag on all resources"),
			Kind:          pulumi.String("policyAssignment"),
			Parameters: blueprint.ParameterValueMap{
				"tagName": &blueprint.ParameterValueArgs{
					Value: pulumi.Any("costCenter"),
				},
				"tagValue": &blueprint.ParameterValueArgs{
					Value: pulumi.Any("[parameter('costCenter')]"),
				},
			},
			PolicyDefinitionId: pulumi.String("/providers/Microsoft.Authorization/policyDefinitions/1e30110a-5ceb-460c-a204-c1c3969c6d62"),
			ResourceScope:      pulumi.String("subscriptions/00000000-0000-0000-0000-000000000000"),
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
import com.pulumi.azurenative.blueprint.PolicyAssignmentArtifact;
import com.pulumi.azurenative.blueprint.PolicyAssignmentArtifactArgs;
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
        var policyAssignmentArtifact = new PolicyAssignmentArtifact("policyAssignmentArtifact", PolicyAssignmentArtifactArgs.builder()        
            .artifactName("costCenterPolicy")
            .blueprintName("simpleBlueprint")
            .displayName("force costCenter tag on all resources")
            .kind("policyAssignment")
            .parameters(Map.ofEntries(
                Map.entry("tagName", Map.of("value", "costCenter")),
                Map.entry("tagValue", Map.of("value", "[parameter('costCenter')]"))
            ))
            .policyDefinitionId("/providers/Microsoft.Authorization/policyDefinitions/1e30110a-5ceb-460c-a204-c1c3969c6d62")
            .resourceScope("subscriptions/00000000-0000-0000-0000-000000000000")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const policyAssignmentArtifact = new azure_native.blueprint.PolicyAssignmentArtifact("policyAssignmentArtifact", {
    artifactName: "costCenterPolicy",
    blueprintName: "simpleBlueprint",
    displayName: "force costCenter tag on all resources",
    kind: "policyAssignment",
    parameters: {
        tagName: {
            value: "costCenter",
        },
        tagValue: {
            value: "[parameter('costCenter')]",
        },
    },
    policyDefinitionId: "/providers/Microsoft.Authorization/policyDefinitions/1e30110a-5ceb-460c-a204-c1c3969c6d62",
    resourceScope: "subscriptions/00000000-0000-0000-0000-000000000000",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

policy_assignment_artifact = azure_native.blueprint.PolicyAssignmentArtifact("policyAssignmentArtifact",
    artifact_name="costCenterPolicy",
    blueprint_name="simpleBlueprint",
    display_name="force costCenter tag on all resources",
    kind="policyAssignment",
    parameters={
        "tagName": azure_native.blueprint.ParameterValueArgs(
            value="costCenter",
        ),
        "tagValue": azure_native.blueprint.ParameterValueArgs(
            value="[parameter('costCenter')]",
        ),
    },
    policy_definition_id="/providers/Microsoft.Authorization/policyDefinitions/1e30110a-5ceb-460c-a204-c1c3969c6d62",
    resource_scope="subscriptions/00000000-0000-0000-0000-000000000000")

```

```yaml
resources:
  policyAssignmentArtifact:
    type: azure-native:blueprint:PolicyAssignmentArtifact
    properties:
      artifactName: costCenterPolicy
      blueprintName: simpleBlueprint
      displayName: force costCenter tag on all resources
      kind: policyAssignment
      parameters:
        tagName:
          value: costCenter
        tagValue:
          value: '[parameter(''costCenter'')]'
      policyDefinitionId: /providers/Microsoft.Authorization/policyDefinitions/1e30110a-5ceb-460c-a204-c1c3969c6d62
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
    var policyAssignmentArtifact = new AzureNative.Blueprint.PolicyAssignmentArtifact("policyAssignmentArtifact", new()
    {
        ArtifactName = "ownerAssignment",
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
		_, err := blueprint.NewPolicyAssignmentArtifact(ctx, "policyAssignmentArtifact", &blueprint.PolicyAssignmentArtifactArgs{
			ArtifactName:  pulumi.String("ownerAssignment"),
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
import com.pulumi.azurenative.blueprint.PolicyAssignmentArtifact;
import com.pulumi.azurenative.blueprint.PolicyAssignmentArtifactArgs;
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
        var policyAssignmentArtifact = new PolicyAssignmentArtifact("policyAssignmentArtifact", PolicyAssignmentArtifactArgs.builder()        
            .artifactName("ownerAssignment")
            .blueprintName("simpleBlueprint")
            .resourceScope("subscriptions/00000000-0000-0000-0000-000000000000")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const policyAssignmentArtifact = new azure_native.blueprint.PolicyAssignmentArtifact("policyAssignmentArtifact", {
    artifactName: "ownerAssignment",
    blueprintName: "simpleBlueprint",
    resourceScope: "subscriptions/00000000-0000-0000-0000-000000000000",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

policy_assignment_artifact = azure_native.blueprint.PolicyAssignmentArtifact("policyAssignmentArtifact",
    artifact_name="ownerAssignment",
    blueprint_name="simpleBlueprint",
    resource_scope="subscriptions/00000000-0000-0000-0000-000000000000")

```

```yaml
resources:
  policyAssignmentArtifact:
    type: azure-native:blueprint:PolicyAssignmentArtifact
    properties:
      artifactName: ownerAssignment
      blueprintName: simpleBlueprint
      resourceScope: subscriptions/00000000-0000-0000-0000-000000000000

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:blueprint:PolicyAssignmentArtifact ownerAssignment /subscriptions/00000000-0000-0000-0000-000000000000/providers/Microsoft.Blueprint/blueprints/simpleBlueprint/artifacts/ownerAssignment 
```
