The policy set definition.
API Version: 2021-06-01.
Previous API Version: 2020-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a policy set definition
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var policySetDefinition = new AzureNative.Authorization.PolicySetDefinition("policySetDefinition", new()
    {
        Description = "Policies to enforce low cost storage SKUs",
        DisplayName = "Cost Management",
        Metadata = 
        {
            { "category", "Cost Management" },
        },
        Parameters = 
        {
            { "namePrefix", new AzureNative.Authorization.Inputs.ParameterDefinitionsValueArgs
            {
                DefaultValue = "myPrefix",
                Metadata = new AzureNative.Authorization.Inputs.ParameterDefinitionsValueMetadataArgs
                {
                    DisplayName = "Prefix to enforce on resource names",
                },
                Type = "String",
            } },
        },
        PolicyDefinitions = new[]
        {
            new AzureNative.Authorization.Inputs.PolicyDefinitionReferenceArgs
            {
                Parameters = 
                {
                    { "listOfAllowedSKUs", new AzureNative.Authorization.Inputs.ParameterValuesValueArgs
                    {
                        Value = new[]
                        {
                            "Standard_GRS",
                            "Standard_LRS",
                        },
                    } },
                },
                PolicyDefinitionId = "/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/7433c107-6db4-4ad1-b57a-a76dce0154a1",
                PolicyDefinitionReferenceId = "Limit_Skus",
            },
            new AzureNative.Authorization.Inputs.PolicyDefinitionReferenceArgs
            {
                Parameters = 
                {
                    { "prefix", new AzureNative.Authorization.Inputs.ParameterValuesValueArgs
                    {
                        Value = "[parameters('namePrefix')]",
                    } },
                    { "suffix", new AzureNative.Authorization.Inputs.ParameterValuesValueArgs
                    {
                        Value = "-LC",
                    } },
                },
                PolicyDefinitionId = "/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming",
                PolicyDefinitionReferenceId = "Resource_Naming",
            },
        },
        PolicySetDefinitionName = "CostManagement",
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
		_, err := authorization.NewPolicySetDefinition(ctx, "policySetDefinition", &authorization.PolicySetDefinitionArgs{
			Description: pulumi.String("Policies to enforce low cost storage SKUs"),
			DisplayName: pulumi.String("Cost Management"),
			Metadata: pulumi.Any{
				Category: "Cost Management",
			},
			Parameters: authorization.ParameterDefinitionsValueMap{
				"namePrefix": &authorization.ParameterDefinitionsValueArgs{
					DefaultValue: pulumi.Any("myPrefix"),
					Metadata: &authorization.ParameterDefinitionsValueMetadataArgs{
						DisplayName: pulumi.String("Prefix to enforce on resource names"),
					},
					Type: pulumi.String("String"),
				},
			},
			PolicyDefinitions: []authorization.PolicyDefinitionReferenceArgs{
				{
					Parameters: {
						"listOfAllowedSKUs": {
							Value: pulumi.Any{
								"Standard_GRS",
								"Standard_LRS",
							},
						},
					},
					PolicyDefinitionId:          pulumi.String("/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/7433c107-6db4-4ad1-b57a-a76dce0154a1"),
					PolicyDefinitionReferenceId: pulumi.String("Limit_Skus"),
				},
				{
					Parameters: {
						"prefix": {
							Value: pulumi.Any("[parameters('namePrefix')]"),
						},
						"suffix": {
							Value: pulumi.Any("-LC"),
						},
					},
					PolicyDefinitionId:          pulumi.String("/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming"),
					PolicyDefinitionReferenceId: pulumi.String("Resource_Naming"),
				},
			},
			PolicySetDefinitionName: pulumi.String("CostManagement"),
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
import com.pulumi.azurenative.authorization.PolicySetDefinition;
import com.pulumi.azurenative.authorization.PolicySetDefinitionArgs;
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
        var policySetDefinition = new PolicySetDefinition("policySetDefinition", PolicySetDefinitionArgs.builder()        
            .description("Policies to enforce low cost storage SKUs")
            .displayName("Cost Management")
            .metadata(Map.of("category", "Cost Management"))
            .parameters(Map.of("namePrefix", Map.ofEntries(
                Map.entry("defaultValue", "myPrefix"),
                Map.entry("metadata", Map.of("displayName", "Prefix to enforce on resource names")),
                Map.entry("type", "String")
            )))
            .policyDefinitions(            
                Map.ofEntries(
                    Map.entry("parameters", Map.of("listOfAllowedSKUs", Map.of("value",                     
                        "Standard_GRS",
                        "Standard_LRS"))),
                    Map.entry("policyDefinitionId", "/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/7433c107-6db4-4ad1-b57a-a76dce0154a1"),
                    Map.entry("policyDefinitionReferenceId", "Limit_Skus")
                ),
                Map.ofEntries(
                    Map.entry("parameters", Map.ofEntries(
                        Map.entry("prefix", Map.of("value", "[parameters('namePrefix')]")),
                        Map.entry("suffix", Map.of("value", "-LC"))
                    )),
                    Map.entry("policyDefinitionId", "/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming"),
                    Map.entry("policyDefinitionReferenceId", "Resource_Naming")
                ))
            .policySetDefinitionName("CostManagement")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const policySetDefinition = new azure_native.authorization.PolicySetDefinition("policySetDefinition", {
    description: "Policies to enforce low cost storage SKUs",
    displayName: "Cost Management",
    metadata: {
        category: "Cost Management",
    },
    parameters: {
        namePrefix: {
            defaultValue: "myPrefix",
            metadata: {
                displayName: "Prefix to enforce on resource names",
            },
            type: "String",
        },
    },
    policyDefinitions: [
        {
            parameters: {
                listOfAllowedSKUs: {
                    value: [
                        "Standard_GRS",
                        "Standard_LRS",
                    ],
                },
            },
            policyDefinitionId: "/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/7433c107-6db4-4ad1-b57a-a76dce0154a1",
            policyDefinitionReferenceId: "Limit_Skus",
        },
        {
            parameters: {
                prefix: {
                    value: "[parameters('namePrefix')]",
                },
                suffix: {
                    value: "-LC",
                },
            },
            policyDefinitionId: "/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming",
            policyDefinitionReferenceId: "Resource_Naming",
        },
    ],
    policySetDefinitionName: "CostManagement",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

policy_set_definition = azure_native.authorization.PolicySetDefinition("policySetDefinition",
    description="Policies to enforce low cost storage SKUs",
    display_name="Cost Management",
    metadata={
        "category": "Cost Management",
    },
    parameters={
        "namePrefix": azure_native.authorization.ParameterDefinitionsValueArgs(
            default_value="myPrefix",
            metadata=azure_native.authorization.ParameterDefinitionsValueMetadataArgs(
                display_name="Prefix to enforce on resource names",
            ),
            type="String",
        ),
    },
    policy_definitions=[
        {
            "parameters": {
                "listOfAllowedSKUs": azure_native.authorization.ParameterValuesValueArgs(
                    value=[
                        "Standard_GRS",
                        "Standard_LRS",
                    ],
                ),
            },
            "policyDefinitionId": "/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/7433c107-6db4-4ad1-b57a-a76dce0154a1",
            "policyDefinitionReferenceId": "Limit_Skus",
        },
        {
            "parameters": {
                "prefix": azure_native.authorization.ParameterValuesValueArgs(
                    value="[parameters('namePrefix')]",
                ),
                "suffix": azure_native.authorization.ParameterValuesValueArgs(
                    value="-LC",
                ),
            },
            "policyDefinitionId": "/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming",
            "policyDefinitionReferenceId": "Resource_Naming",
        },
    ],
    policy_set_definition_name="CostManagement")

```

```yaml
resources:
  policySetDefinition:
    type: azure-native:authorization:PolicySetDefinition
    properties:
      description: Policies to enforce low cost storage SKUs
      displayName: Cost Management
      metadata:
        category: Cost Management
      parameters:
        namePrefix:
          defaultValue: myPrefix
          metadata:
            displayName: Prefix to enforce on resource names
          type: String
      policyDefinitions:
        - parameters:
            listOfAllowedSKUs:
              value:
                - Standard_GRS
                - Standard_LRS
          policyDefinitionId: /subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/7433c107-6db4-4ad1-b57a-a76dce0154a1
          policyDefinitionReferenceId: Limit_Skus
        - parameters:
            prefix:
              value: '[parameters(''namePrefix'')]'
            suffix:
              value: -LC
          policyDefinitionId: /subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming
          policyDefinitionReferenceId: Resource_Naming
      policySetDefinitionName: CostManagement

```

{{% /example %}}
{{% example %}}
### Create or update a policy set definition with groups
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var policySetDefinition = new AzureNative.Authorization.PolicySetDefinition("policySetDefinition", new()
    {
        Description = "Policies to enforce low cost storage SKUs",
        DisplayName = "Cost Management",
        Metadata = 
        {
            { "category", "Cost Management" },
        },
        PolicyDefinitionGroups = new[]
        {
            new AzureNative.Authorization.Inputs.PolicyDefinitionGroupArgs
            {
                Description = "Policies designed to control spend within a subscription.",
                DisplayName = "Cost Management Policies",
                Name = "CostSaving",
            },
            new AzureNative.Authorization.Inputs.PolicyDefinitionGroupArgs
            {
                Description = "Policies that help enforce resource organization standards within a subscription.",
                DisplayName = "Organizational Policies",
                Name = "Organizational",
            },
        },
        PolicyDefinitions = new[]
        {
            new AzureNative.Authorization.Inputs.PolicyDefinitionReferenceArgs
            {
                GroupNames = new[]
                {
                    "CostSaving",
                },
                Parameters = 
                {
                    { "listOfAllowedSKUs", new AzureNative.Authorization.Inputs.ParameterValuesValueArgs
                    {
                        Value = new[]
                        {
                            "Standard_GRS",
                            "Standard_LRS",
                        },
                    } },
                },
                PolicyDefinitionId = "/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/7433c107-6db4-4ad1-b57a-a76dce0154a1",
                PolicyDefinitionReferenceId = "Limit_Skus",
            },
            new AzureNative.Authorization.Inputs.PolicyDefinitionReferenceArgs
            {
                GroupNames = new[]
                {
                    "Organizational",
                },
                Parameters = 
                {
                    { "prefix", new AzureNative.Authorization.Inputs.ParameterValuesValueArgs
                    {
                        Value = "DeptA",
                    } },
                    { "suffix", new AzureNative.Authorization.Inputs.ParameterValuesValueArgs
                    {
                        Value = "-LC",
                    } },
                },
                PolicyDefinitionId = "/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming",
                PolicyDefinitionReferenceId = "Resource_Naming",
            },
        },
        PolicySetDefinitionName = "CostManagement",
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
		_, err := authorization.NewPolicySetDefinition(ctx, "policySetDefinition", &authorization.PolicySetDefinitionArgs{
			Description: pulumi.String("Policies to enforce low cost storage SKUs"),
			DisplayName: pulumi.String("Cost Management"),
			Metadata: pulumi.Any{
				Category: "Cost Management",
			},
			PolicyDefinitionGroups: []authorization.PolicyDefinitionGroupArgs{
				{
					Description: pulumi.String("Policies designed to control spend within a subscription."),
					DisplayName: pulumi.String("Cost Management Policies"),
					Name:        pulumi.String("CostSaving"),
				},
				{
					Description: pulumi.String("Policies that help enforce resource organization standards within a subscription."),
					DisplayName: pulumi.String("Organizational Policies"),
					Name:        pulumi.String("Organizational"),
				},
			},
			PolicyDefinitions: []authorization.PolicyDefinitionReferenceArgs{
				{
					GroupNames: pulumi.StringArray{
						pulumi.String("CostSaving"),
					},
					Parameters: {
						"listOfAllowedSKUs": {
							Value: pulumi.Any{
								"Standard_GRS",
								"Standard_LRS",
							},
						},
					},
					PolicyDefinitionId:          pulumi.String("/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/7433c107-6db4-4ad1-b57a-a76dce0154a1"),
					PolicyDefinitionReferenceId: pulumi.String("Limit_Skus"),
				},
				{
					GroupNames: pulumi.StringArray{
						pulumi.String("Organizational"),
					},
					Parameters: {
						"prefix": {
							Value: pulumi.Any("DeptA"),
						},
						"suffix": {
							Value: pulumi.Any("-LC"),
						},
					},
					PolicyDefinitionId:          pulumi.String("/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming"),
					PolicyDefinitionReferenceId: pulumi.String("Resource_Naming"),
				},
			},
			PolicySetDefinitionName: pulumi.String("CostManagement"),
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
import com.pulumi.azurenative.authorization.PolicySetDefinition;
import com.pulumi.azurenative.authorization.PolicySetDefinitionArgs;
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
        var policySetDefinition = new PolicySetDefinition("policySetDefinition", PolicySetDefinitionArgs.builder()        
            .description("Policies to enforce low cost storage SKUs")
            .displayName("Cost Management")
            .metadata(Map.of("category", "Cost Management"))
            .policyDefinitionGroups(            
                Map.ofEntries(
                    Map.entry("description", "Policies designed to control spend within a subscription."),
                    Map.entry("displayName", "Cost Management Policies"),
                    Map.entry("name", "CostSaving")
                ),
                Map.ofEntries(
                    Map.entry("description", "Policies that help enforce resource organization standards within a subscription."),
                    Map.entry("displayName", "Organizational Policies"),
                    Map.entry("name", "Organizational")
                ))
            .policyDefinitions(            
                Map.ofEntries(
                    Map.entry("groupNames", "CostSaving"),
                    Map.entry("parameters", Map.of("listOfAllowedSKUs", Map.of("value",                     
                        "Standard_GRS",
                        "Standard_LRS"))),
                    Map.entry("policyDefinitionId", "/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/7433c107-6db4-4ad1-b57a-a76dce0154a1"),
                    Map.entry("policyDefinitionReferenceId", "Limit_Skus")
                ),
                Map.ofEntries(
                    Map.entry("groupNames", "Organizational"),
                    Map.entry("parameters", Map.ofEntries(
                        Map.entry("prefix", Map.of("value", "DeptA")),
                        Map.entry("suffix", Map.of("value", "-LC"))
                    )),
                    Map.entry("policyDefinitionId", "/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming"),
                    Map.entry("policyDefinitionReferenceId", "Resource_Naming")
                ))
            .policySetDefinitionName("CostManagement")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const policySetDefinition = new azure_native.authorization.PolicySetDefinition("policySetDefinition", {
    description: "Policies to enforce low cost storage SKUs",
    displayName: "Cost Management",
    metadata: {
        category: "Cost Management",
    },
    policyDefinitionGroups: [
        {
            description: "Policies designed to control spend within a subscription.",
            displayName: "Cost Management Policies",
            name: "CostSaving",
        },
        {
            description: "Policies that help enforce resource organization standards within a subscription.",
            displayName: "Organizational Policies",
            name: "Organizational",
        },
    ],
    policyDefinitions: [
        {
            groupNames: ["CostSaving"],
            parameters: {
                listOfAllowedSKUs: {
                    value: [
                        "Standard_GRS",
                        "Standard_LRS",
                    ],
                },
            },
            policyDefinitionId: "/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/7433c107-6db4-4ad1-b57a-a76dce0154a1",
            policyDefinitionReferenceId: "Limit_Skus",
        },
        {
            groupNames: ["Organizational"],
            parameters: {
                prefix: {
                    value: "DeptA",
                },
                suffix: {
                    value: "-LC",
                },
            },
            policyDefinitionId: "/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming",
            policyDefinitionReferenceId: "Resource_Naming",
        },
    ],
    policySetDefinitionName: "CostManagement",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

policy_set_definition = azure_native.authorization.PolicySetDefinition("policySetDefinition",
    description="Policies to enforce low cost storage SKUs",
    display_name="Cost Management",
    metadata={
        "category": "Cost Management",
    },
    policy_definition_groups=[
        azure_native.authorization.PolicyDefinitionGroupArgs(
            description="Policies designed to control spend within a subscription.",
            display_name="Cost Management Policies",
            name="CostSaving",
        ),
        azure_native.authorization.PolicyDefinitionGroupArgs(
            description="Policies that help enforce resource organization standards within a subscription.",
            display_name="Organizational Policies",
            name="Organizational",
        ),
    ],
    policy_definitions=[
        {
            "groupNames": ["CostSaving"],
            "parameters": {
                "listOfAllowedSKUs": azure_native.authorization.ParameterValuesValueArgs(
                    value=[
                        "Standard_GRS",
                        "Standard_LRS",
                    ],
                ),
            },
            "policyDefinitionId": "/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/7433c107-6db4-4ad1-b57a-a76dce0154a1",
            "policyDefinitionReferenceId": "Limit_Skus",
        },
        {
            "groupNames": ["Organizational"],
            "parameters": {
                "prefix": azure_native.authorization.ParameterValuesValueArgs(
                    value="DeptA",
                ),
                "suffix": azure_native.authorization.ParameterValuesValueArgs(
                    value="-LC",
                ),
            },
            "policyDefinitionId": "/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming",
            "policyDefinitionReferenceId": "Resource_Naming",
        },
    ],
    policy_set_definition_name="CostManagement")

```

```yaml
resources:
  policySetDefinition:
    type: azure-native:authorization:PolicySetDefinition
    properties:
      description: Policies to enforce low cost storage SKUs
      displayName: Cost Management
      metadata:
        category: Cost Management
      policyDefinitionGroups:
        - description: Policies designed to control spend within a subscription.
          displayName: Cost Management Policies
          name: CostSaving
        - description: Policies that help enforce resource organization standards within a subscription.
          displayName: Organizational Policies
          name: Organizational
      policyDefinitions:
        - groupNames:
            - CostSaving
          parameters:
            listOfAllowedSKUs:
              value:
                - Standard_GRS
                - Standard_LRS
          policyDefinitionId: /subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/7433c107-6db4-4ad1-b57a-a76dce0154a1
          policyDefinitionReferenceId: Limit_Skus
        - groupNames:
            - Organizational
          parameters:
            prefix:
              value: DeptA
            suffix:
              value: -LC
          policyDefinitionId: /subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming
          policyDefinitionReferenceId: Resource_Naming
      policySetDefinitionName: CostManagement

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:authorization:PolicySetDefinition CostManagement /subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policySetDefinitions/CostManagement 
```
