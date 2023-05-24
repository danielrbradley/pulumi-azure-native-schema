The policy definition.
API Version: 2021-06-01.
Previous API Version: 2020-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a policy definition at management group level
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var policyDefinitionAtManagementGroup = new AzureNative.Authorization.PolicyDefinitionAtManagementGroup("policyDefinitionAtManagementGroup", new()
    {
        Description = "Force resource names to begin with given 'prefix' and/or end with given 'suffix'",
        DisplayName = "Enforce resource naming convention",
        ManagementGroupId = "MyManagementGroup",
        Metadata = 
        {
            { "category", "Naming" },
        },
        Mode = "All",
        Parameters = 
        {
            { "prefix", new AzureNative.Authorization.Inputs.ParameterDefinitionsValueArgs
            {
                Metadata = new AzureNative.Authorization.Inputs.ParameterDefinitionsValueMetadataArgs
                {
                    Description = "Resource name prefix",
                    DisplayName = "Prefix",
                },
                Type = "String",
            } },
            { "suffix", new AzureNative.Authorization.Inputs.ParameterDefinitionsValueArgs
            {
                Metadata = new AzureNative.Authorization.Inputs.ParameterDefinitionsValueMetadataArgs
                {
                    Description = "Resource name suffix",
                    DisplayName = "Suffix",
                },
                Type = "String",
            } },
        },
        PolicyDefinitionName = "ResourceNaming",
        PolicyRule = 
        {
            { "if", 
            {
                { "not", 
                {
                    { "field", "name" },
                    { "like", "[concat(parameters('prefix'), '*', parameters('suffix'))]" },
                } },
            } },
            { "then", 
            {
                { "effect", "deny" },
            } },
        },
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
		_, err := authorization.NewPolicyDefinitionAtManagementGroup(ctx, "policyDefinitionAtManagementGroup", &authorization.PolicyDefinitionAtManagementGroupArgs{
			Description:       pulumi.String("Force resource names to begin with given 'prefix' and/or end with given 'suffix'"),
			DisplayName:       pulumi.String("Enforce resource naming convention"),
			ManagementGroupId: pulumi.String("MyManagementGroup"),
			Metadata: pulumi.Any{
				Category: "Naming",
			},
			Mode: pulumi.String("All"),
			Parameters: authorization.ParameterDefinitionsValueMap{
				"prefix": &authorization.ParameterDefinitionsValueArgs{
					Metadata: &authorization.ParameterDefinitionsValueMetadataArgs{
						Description: pulumi.String("Resource name prefix"),
						DisplayName: pulumi.String("Prefix"),
					},
					Type: pulumi.String("String"),
				},
				"suffix": &authorization.ParameterDefinitionsValueArgs{
					Metadata: &authorization.ParameterDefinitionsValueMetadataArgs{
						Description: pulumi.String("Resource name suffix"),
						DisplayName: pulumi.String("Suffix"),
					},
					Type: pulumi.String("String"),
				},
			},
			PolicyDefinitionName: pulumi.String("ResourceNaming"),
			PolicyRule: pulumi.Any{
				If: map[string]interface{}{
					"not": map[string]interface{}{
						"field": "name",
						"like":  "[concat(parameters('prefix'), '*', parameters('suffix'))]",
					},
				},
				Then: map[string]interface{}{
					"effect": "deny",
				},
			},
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
import com.pulumi.azurenative.authorization.PolicyDefinitionAtManagementGroup;
import com.pulumi.azurenative.authorization.PolicyDefinitionAtManagementGroupArgs;
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
        var policyDefinitionAtManagementGroup = new PolicyDefinitionAtManagementGroup("policyDefinitionAtManagementGroup", PolicyDefinitionAtManagementGroupArgs.builder()        
            .description("Force resource names to begin with given 'prefix' and/or end with given 'suffix'")
            .displayName("Enforce resource naming convention")
            .managementGroupId("MyManagementGroup")
            .metadata(Map.of("category", "Naming"))
            .mode("All")
            .parameters(Map.ofEntries(
                Map.entry("prefix", Map.ofEntries(
                    Map.entry("metadata", Map.ofEntries(
                        Map.entry("description", "Resource name prefix"),
                        Map.entry("displayName", "Prefix")
                    )),
                    Map.entry("type", "String")
                )),
                Map.entry("suffix", Map.ofEntries(
                    Map.entry("metadata", Map.ofEntries(
                        Map.entry("description", "Resource name suffix"),
                        Map.entry("displayName", "Suffix")
                    )),
                    Map.entry("type", "String")
                ))
            ))
            .policyDefinitionName("ResourceNaming")
            .policyRule(Map.ofEntries(
                Map.entry("if", Map.of("not", Map.ofEntries(
                    Map.entry("field", "name"),
                    Map.entry("like", "[concat(parameters('prefix'), '*', parameters('suffix'))]")
                ))),
                Map.entry("then", Map.of("effect", "deny"))
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const policyDefinitionAtManagementGroup = new azure_native.authorization.PolicyDefinitionAtManagementGroup("policyDefinitionAtManagementGroup", {
    description: "Force resource names to begin with given 'prefix' and/or end with given 'suffix'",
    displayName: "Enforce resource naming convention",
    managementGroupId: "MyManagementGroup",
    metadata: {
        category: "Naming",
    },
    mode: "All",
    parameters: {
        prefix: {
            metadata: {
                description: "Resource name prefix",
                displayName: "Prefix",
            },
            type: "String",
        },
        suffix: {
            metadata: {
                description: "Resource name suffix",
                displayName: "Suffix",
            },
            type: "String",
        },
    },
    policyDefinitionName: "ResourceNaming",
    policyRule: {
        "if": {
            not: {
                field: "name",
                like: "[concat(parameters('prefix'), '*', parameters('suffix'))]",
            },
        },
        then: {
            effect: "deny",
        },
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

policy_definition_at_management_group = azure_native.authorization.PolicyDefinitionAtManagementGroup("policyDefinitionAtManagementGroup",
    description="Force resource names to begin with given 'prefix' and/or end with given 'suffix'",
    display_name="Enforce resource naming convention",
    management_group_id="MyManagementGroup",
    metadata={
        "category": "Naming",
    },
    mode="All",
    parameters={
        "prefix": azure_native.authorization.ParameterDefinitionsValueArgs(
            metadata=azure_native.authorization.ParameterDefinitionsValueMetadataArgs(
                description="Resource name prefix",
                display_name="Prefix",
            ),
            type="String",
        ),
        "suffix": azure_native.authorization.ParameterDefinitionsValueArgs(
            metadata=azure_native.authorization.ParameterDefinitionsValueMetadataArgs(
                description="Resource name suffix",
                display_name="Suffix",
            ),
            type="String",
        ),
    },
    policy_definition_name="ResourceNaming",
    policy_rule={
        "if": {
            "not": {
                "field": "name",
                "like": "[concat(parameters('prefix'), '*', parameters('suffix'))]",
            },
        },
        "then": {
            "effect": "deny",
        },
    })

```

```yaml
resources:
  policyDefinitionAtManagementGroup:
    type: azure-native:authorization:PolicyDefinitionAtManagementGroup
    properties:
      description: Force resource names to begin with given 'prefix' and/or end with given 'suffix'
      displayName: Enforce resource naming convention
      managementGroupId: MyManagementGroup
      metadata:
        category: Naming
      mode: All
      parameters:
        prefix:
          metadata:
            description: Resource name prefix
            displayName: Prefix
          type: String
        suffix:
          metadata:
            description: Resource name suffix
            displayName: Suffix
          type: String
      policyDefinitionName: ResourceNaming
      policyRule:
        if:
          not:
            field: name
            like: '[concat(parameters(''prefix''), ''*'', parameters(''suffix''))]'
        then:
          effect: deny

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:authorization:PolicyDefinitionAtManagementGroup ResourceNaming /providers/Microsoft.Management/managementgroups/MyManagementGroup/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming 
```
