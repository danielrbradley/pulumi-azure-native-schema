Represents a Blueprint definition.
API Version: 2018-11-01-preview.
Previous API Version: 2018-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ManagementGroupBlueprint
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var blueprint = new AzureNative.Blueprint.Blueprint("blueprint", new()
    {
        BlueprintName = "simpleBlueprint",
        Description = "blueprint contains all artifact kinds {'template', 'rbac', 'policy'}",
        Parameters = 
        {
            { "costCenter", new AzureNative.Blueprint.Inputs.ParameterDefinitionArgs
            {
                DisplayName = "force cost center tag for all resources under given subscription.",
                Type = "string",
            } },
            { "owners", new AzureNative.Blueprint.Inputs.ParameterDefinitionArgs
            {
                DisplayName = "assign owners to subscription along with blueprint assignment.",
                Type = "array",
            } },
            { "storageAccountType", new AzureNative.Blueprint.Inputs.ParameterDefinitionArgs
            {
                DisplayName = "storage account type.",
                Type = "string",
            } },
        },
        ResourceGroups = 
        {
            { "storageRG", new AzureNative.Blueprint.Inputs.ResourceGroupDefinitionArgs
            {
                Description = "Contains storageAccounts that collect all shoebox logs.",
                DisplayName = "storage resource group",
            } },
        },
        ResourceScope = "providers/Microsoft.Management/managementGroups/ContosoOnlineGroup",
        TargetScope = "subscription",
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
		_, err := blueprint.NewBlueprint(ctx, "blueprint", &blueprint.BlueprintArgs{
			BlueprintName: pulumi.String("simpleBlueprint"),
			Description:   pulumi.String("blueprint contains all artifact kinds {'template', 'rbac', 'policy'}"),
			Parameters: blueprint.ParameterDefinitionMap{
				"costCenter": &blueprint.ParameterDefinitionArgs{
					DisplayName: pulumi.String("force cost center tag for all resources under given subscription."),
					Type:        pulumi.String("string"),
				},
				"owners": &blueprint.ParameterDefinitionArgs{
					DisplayName: pulumi.String("assign owners to subscription along with blueprint assignment."),
					Type:        pulumi.String("array"),
				},
				"storageAccountType": &blueprint.ParameterDefinitionArgs{
					DisplayName: pulumi.String("storage account type."),
					Type:        pulumi.String("string"),
				},
			},
			ResourceGroups: blueprint.ResourceGroupDefinitionMap{
				"storageRG": &blueprint.ResourceGroupDefinitionArgs{
					Description: pulumi.String("Contains storageAccounts that collect all shoebox logs."),
					DisplayName: pulumi.String("storage resource group"),
				},
			},
			ResourceScope: pulumi.String("providers/Microsoft.Management/managementGroups/ContosoOnlineGroup"),
			TargetScope:   pulumi.String("subscription"),
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
import com.pulumi.azurenative.blueprint.Blueprint;
import com.pulumi.azurenative.blueprint.BlueprintArgs;
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
        var blueprint = new Blueprint("blueprint", BlueprintArgs.builder()        
            .blueprintName("simpleBlueprint")
            .description("blueprint contains all artifact kinds {'template', 'rbac', 'policy'}")
            .parameters(Map.ofEntries(
                Map.entry("costCenter", Map.ofEntries(
                    Map.entry("displayName", "force cost center tag for all resources under given subscription."),
                    Map.entry("type", "string")
                )),
                Map.entry("owners", Map.ofEntries(
                    Map.entry("displayName", "assign owners to subscription along with blueprint assignment."),
                    Map.entry("type", "array")
                )),
                Map.entry("storageAccountType", Map.ofEntries(
                    Map.entry("displayName", "storage account type."),
                    Map.entry("type", "string")
                ))
            ))
            .resourceGroups(Map.of("storageRG", Map.ofEntries(
                Map.entry("description", "Contains storageAccounts that collect all shoebox logs."),
                Map.entry("displayName", "storage resource group")
            )))
            .resourceScope("providers/Microsoft.Management/managementGroups/ContosoOnlineGroup")
            .targetScope("subscription")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const blueprint = new azure_native.blueprint.Blueprint("blueprint", {
    blueprintName: "simpleBlueprint",
    description: "blueprint contains all artifact kinds {'template', 'rbac', 'policy'}",
    parameters: {
        costCenter: {
            displayName: "force cost center tag for all resources under given subscription.",
            type: "string",
        },
        owners: {
            displayName: "assign owners to subscription along with blueprint assignment.",
            type: "array",
        },
        storageAccountType: {
            displayName: "storage account type.",
            type: "string",
        },
    },
    resourceGroups: {
        storageRG: {
            description: "Contains storageAccounts that collect all shoebox logs.",
            displayName: "storage resource group",
        },
    },
    resourceScope: "providers/Microsoft.Management/managementGroups/ContosoOnlineGroup",
    targetScope: "subscription",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

blueprint = azure_native.blueprint.Blueprint("blueprint",
    blueprint_name="simpleBlueprint",
    description="blueprint contains all artifact kinds {'template', 'rbac', 'policy'}",
    parameters={
        "costCenter": azure_native.blueprint.ParameterDefinitionArgs(
            display_name="force cost center tag for all resources under given subscription.",
            type="string",
        ),
        "owners": azure_native.blueprint.ParameterDefinitionArgs(
            display_name="assign owners to subscription along with blueprint assignment.",
            type="array",
        ),
        "storageAccountType": azure_native.blueprint.ParameterDefinitionArgs(
            display_name="storage account type.",
            type="string",
        ),
    },
    resource_groups={
        "storageRG": azure_native.blueprint.ResourceGroupDefinitionArgs(
            description="Contains storageAccounts that collect all shoebox logs.",
            display_name="storage resource group",
        ),
    },
    resource_scope="providers/Microsoft.Management/managementGroups/ContosoOnlineGroup",
    target_scope="subscription")

```

```yaml
resources:
  blueprint:
    type: azure-native:blueprint:Blueprint
    properties:
      blueprintName: simpleBlueprint
      description: blueprint contains all artifact kinds {'template', 'rbac', 'policy'}
      parameters:
        costCenter:
          displayName: force cost center tag for all resources under given subscription.
          type: string
        owners:
          displayName: assign owners to subscription along with blueprint assignment.
          type: array
        storageAccountType:
          displayName: storage account type.
          type: string
      resourceGroups:
        storageRG:
          description: Contains storageAccounts that collect all shoebox logs.
          displayName: storage resource group
      resourceScope: providers/Microsoft.Management/managementGroups/ContosoOnlineGroup
      targetScope: subscription

```

{{% /example %}}
{{% example %}}
### ResourceGroupWithTags
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var blueprint = new AzureNative.Blueprint.Blueprint("blueprint", new()
    {
        BlueprintName = "simpleBlueprint",
        Description = "An example blueprint containing an RG with two tags.",
        ResourceGroups = 
        {
            { "myRGName", new AzureNative.Blueprint.Inputs.ResourceGroupDefinitionArgs
            {
                DisplayName = "My Resource Group",
                Location = "westus",
                Name = "myRGName",
                Tags = 
                {
                    { "costcenter", "123456" },
                    { "nameOnlyTag", "" },
                },
            } },
        },
        ResourceScope = "providers/Microsoft.Management/managementGroups/{ManagementGroupId}",
        TargetScope = "subscription",
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
		_, err := blueprint.NewBlueprint(ctx, "blueprint", &blueprint.BlueprintArgs{
			BlueprintName: pulumi.String("simpleBlueprint"),
			Description:   pulumi.String("An example blueprint containing an RG with two tags."),
			ResourceGroups: blueprint.ResourceGroupDefinitionMap{
				"myRGName": &blueprint.ResourceGroupDefinitionArgs{
					DisplayName: pulumi.String("My Resource Group"),
					Location:    pulumi.String("westus"),
					Name:        pulumi.String("myRGName"),
					Tags: pulumi.StringMap{
						"costcenter":  pulumi.String("123456"),
						"nameOnlyTag": pulumi.String(""),
					},
				},
			},
			ResourceScope: pulumi.String("providers/Microsoft.Management/managementGroups/{ManagementGroupId}"),
			TargetScope:   pulumi.String("subscription"),
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
import com.pulumi.azurenative.blueprint.Blueprint;
import com.pulumi.azurenative.blueprint.BlueprintArgs;
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
        var blueprint = new Blueprint("blueprint", BlueprintArgs.builder()        
            .blueprintName("simpleBlueprint")
            .description("An example blueprint containing an RG with two tags.")
            .resourceGroups(Map.of("myRGName", Map.ofEntries(
                Map.entry("displayName", "My Resource Group"),
                Map.entry("location", "westus"),
                Map.entry("name", "myRGName"),
                Map.entry("tags", Map.ofEntries(
                    Map.entry("costcenter", "123456"),
                    Map.entry("nameOnlyTag", "")
                ))
            )))
            .resourceScope("providers/Microsoft.Management/managementGroups/{ManagementGroupId}")
            .targetScope("subscription")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const blueprint = new azure_native.blueprint.Blueprint("blueprint", {
    blueprintName: "simpleBlueprint",
    description: "An example blueprint containing an RG with two tags.",
    resourceGroups: {
        myRGName: {
            displayName: "My Resource Group",
            location: "westus",
            name: "myRGName",
            tags: {
                costcenter: "123456",
                nameOnlyTag: "",
            },
        },
    },
    resourceScope: "providers/Microsoft.Management/managementGroups/{ManagementGroupId}",
    targetScope: "subscription",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

blueprint = azure_native.blueprint.Blueprint("blueprint",
    blueprint_name="simpleBlueprint",
    description="An example blueprint containing an RG with two tags.",
    resource_groups={
        "myRGName": azure_native.blueprint.ResourceGroupDefinitionArgs(
            display_name="My Resource Group",
            location="westus",
            name="myRGName",
            tags={
                "costcenter": "123456",
                "nameOnlyTag": "",
            },
        ),
    },
    resource_scope="providers/Microsoft.Management/managementGroups/{ManagementGroupId}",
    target_scope="subscription")

```

```yaml
resources:
  blueprint:
    type: azure-native:blueprint:Blueprint
    properties:
      blueprintName: simpleBlueprint
      description: An example blueprint containing an RG with two tags.
      resourceGroups:
        myRGName:
          displayName: My Resource Group
          location: westus
          name: myRGName
          tags:
            costcenter: '123456'
            nameOnlyTag:
      resourceScope: providers/Microsoft.Management/managementGroups/{ManagementGroupId}
      targetScope: subscription

```

{{% /example %}}
{{% example %}}
### SubscriptionBlueprint
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var blueprint = new AzureNative.Blueprint.Blueprint("blueprint", new()
    {
        BlueprintName = "simpleBlueprint",
        Description = "blueprint contains all artifact kinds {'template', 'rbac', 'policy'}",
        Parameters = 
        {
            { "costCenter", new AzureNative.Blueprint.Inputs.ParameterDefinitionArgs
            {
                DisplayName = "force cost center tag for all resources under given subscription.",
                Type = "string",
            } },
            { "owners", new AzureNative.Blueprint.Inputs.ParameterDefinitionArgs
            {
                DisplayName = "assign owners to subscription along with blueprint assignment.",
                Type = "array",
            } },
            { "storageAccountType", new AzureNative.Blueprint.Inputs.ParameterDefinitionArgs
            {
                DisplayName = "storage account type.",
                Type = "string",
            } },
        },
        ResourceGroups = 
        {
            { "storageRG", new AzureNative.Blueprint.Inputs.ResourceGroupDefinitionArgs
            {
                Description = "Contains storageAccounts that collect all shoebox logs.",
                DisplayName = "storage resource group",
            } },
        },
        ResourceScope = "subscriptions/00000000-0000-0000-0000-000000000000",
        TargetScope = "subscription",
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
		_, err := blueprint.NewBlueprint(ctx, "blueprint", &blueprint.BlueprintArgs{
			BlueprintName: pulumi.String("simpleBlueprint"),
			Description:   pulumi.String("blueprint contains all artifact kinds {'template', 'rbac', 'policy'}"),
			Parameters: blueprint.ParameterDefinitionMap{
				"costCenter": &blueprint.ParameterDefinitionArgs{
					DisplayName: pulumi.String("force cost center tag for all resources under given subscription."),
					Type:        pulumi.String("string"),
				},
				"owners": &blueprint.ParameterDefinitionArgs{
					DisplayName: pulumi.String("assign owners to subscription along with blueprint assignment."),
					Type:        pulumi.String("array"),
				},
				"storageAccountType": &blueprint.ParameterDefinitionArgs{
					DisplayName: pulumi.String("storage account type."),
					Type:        pulumi.String("string"),
				},
			},
			ResourceGroups: blueprint.ResourceGroupDefinitionMap{
				"storageRG": &blueprint.ResourceGroupDefinitionArgs{
					Description: pulumi.String("Contains storageAccounts that collect all shoebox logs."),
					DisplayName: pulumi.String("storage resource group"),
				},
			},
			ResourceScope: pulumi.String("subscriptions/00000000-0000-0000-0000-000000000000"),
			TargetScope:   pulumi.String("subscription"),
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
import com.pulumi.azurenative.blueprint.Blueprint;
import com.pulumi.azurenative.blueprint.BlueprintArgs;
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
        var blueprint = new Blueprint("blueprint", BlueprintArgs.builder()        
            .blueprintName("simpleBlueprint")
            .description("blueprint contains all artifact kinds {'template', 'rbac', 'policy'}")
            .parameters(Map.ofEntries(
                Map.entry("costCenter", Map.ofEntries(
                    Map.entry("displayName", "force cost center tag for all resources under given subscription."),
                    Map.entry("type", "string")
                )),
                Map.entry("owners", Map.ofEntries(
                    Map.entry("displayName", "assign owners to subscription along with blueprint assignment."),
                    Map.entry("type", "array")
                )),
                Map.entry("storageAccountType", Map.ofEntries(
                    Map.entry("displayName", "storage account type."),
                    Map.entry("type", "string")
                ))
            ))
            .resourceGroups(Map.of("storageRG", Map.ofEntries(
                Map.entry("description", "Contains storageAccounts that collect all shoebox logs."),
                Map.entry("displayName", "storage resource group")
            )))
            .resourceScope("subscriptions/00000000-0000-0000-0000-000000000000")
            .targetScope("subscription")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const blueprint = new azure_native.blueprint.Blueprint("blueprint", {
    blueprintName: "simpleBlueprint",
    description: "blueprint contains all artifact kinds {'template', 'rbac', 'policy'}",
    parameters: {
        costCenter: {
            displayName: "force cost center tag for all resources under given subscription.",
            type: "string",
        },
        owners: {
            displayName: "assign owners to subscription along with blueprint assignment.",
            type: "array",
        },
        storageAccountType: {
            displayName: "storage account type.",
            type: "string",
        },
    },
    resourceGroups: {
        storageRG: {
            description: "Contains storageAccounts that collect all shoebox logs.",
            displayName: "storage resource group",
        },
    },
    resourceScope: "subscriptions/00000000-0000-0000-0000-000000000000",
    targetScope: "subscription",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

blueprint = azure_native.blueprint.Blueprint("blueprint",
    blueprint_name="simpleBlueprint",
    description="blueprint contains all artifact kinds {'template', 'rbac', 'policy'}",
    parameters={
        "costCenter": azure_native.blueprint.ParameterDefinitionArgs(
            display_name="force cost center tag for all resources under given subscription.",
            type="string",
        ),
        "owners": azure_native.blueprint.ParameterDefinitionArgs(
            display_name="assign owners to subscription along with blueprint assignment.",
            type="array",
        ),
        "storageAccountType": azure_native.blueprint.ParameterDefinitionArgs(
            display_name="storage account type.",
            type="string",
        ),
    },
    resource_groups={
        "storageRG": azure_native.blueprint.ResourceGroupDefinitionArgs(
            description="Contains storageAccounts that collect all shoebox logs.",
            display_name="storage resource group",
        ),
    },
    resource_scope="subscriptions/00000000-0000-0000-0000-000000000000",
    target_scope="subscription")

```

```yaml
resources:
  blueprint:
    type: azure-native:blueprint:Blueprint
    properties:
      blueprintName: simpleBlueprint
      description: blueprint contains all artifact kinds {'template', 'rbac', 'policy'}
      parameters:
        costCenter:
          displayName: force cost center tag for all resources under given subscription.
          type: string
        owners:
          displayName: assign owners to subscription along with blueprint assignment.
          type: array
        storageAccountType:
          displayName: storage account type.
          type: string
      resourceGroups:
        storageRG:
          description: Contains storageAccounts that collect all shoebox logs.
          displayName: storage resource group
      resourceScope: subscriptions/00000000-0000-0000-0000-000000000000
      targetScope: subscription

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:blueprint:Blueprint simpleBlueprint /subscriptions/00000000-0000-0000-0000-000000000000/providers/Microsoft.Blueprint/blueprints/simpleBlueprint 
```
