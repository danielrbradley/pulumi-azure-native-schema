The policy set definition.
API Version: 2021-06-01.
Previous API Version: 2020-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a policy set definition at management group level
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var policySetDefinitionAtManagementGroup = new AzureNative.Authorization.PolicySetDefinitionAtManagementGroup("policySetDefinitionAtManagementGroup", new()
    {
        Description = "Policies to enforce low cost storage SKUs",
        DisplayName = "Cost Management",
        ManagementGroupId = "MyManagementGroup",
        Metadata = 
        {
            { "category", "Cost Management" },
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
                PolicyDefinitionId = "/providers/Microsoft.Management/managementgroups/MyManagementGroup/providers/Microsoft.Authorization/policyDefinitions/7433c107-6db4-4ad1-b57a-a76dce0154a1",
                PolicyDefinitionReferenceId = "Limit_Skus",
            },
            new AzureNative.Authorization.Inputs.PolicyDefinitionReferenceArgs
            {
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
                PolicyDefinitionId = "/providers/Microsoft.Management/managementgroups/MyManagementGroup/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming",
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
		_, err := authorization.NewPolicySetDefinitionAtManagementGroup(ctx, "policySetDefinitionAtManagementGroup", &authorization.PolicySetDefinitionAtManagementGroupArgs{
			Description:       pulumi.String("Policies to enforce low cost storage SKUs"),
			DisplayName:       pulumi.String("Cost Management"),
			ManagementGroupId: pulumi.String("MyManagementGroup"),
			Metadata: pulumi.Any{
				Category: "Cost Management",
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
					PolicyDefinitionId:          pulumi.String("/providers/Microsoft.Management/managementgroups/MyManagementGroup/providers/Microsoft.Authorization/policyDefinitions/7433c107-6db4-4ad1-b57a-a76dce0154a1"),
					PolicyDefinitionReferenceId: pulumi.String("Limit_Skus"),
				},
				{
					Parameters: {
						"prefix": {
							Value: pulumi.Any("DeptA"),
						},
						"suffix": {
							Value: pulumi.Any("-LC"),
						},
					},
					PolicyDefinitionId:          pulumi.String("/providers/Microsoft.Management/managementgroups/MyManagementGroup/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming"),
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
import com.pulumi.azurenative.authorization.PolicySetDefinitionAtManagementGroup;
import com.pulumi.azurenative.authorization.PolicySetDefinitionAtManagementGroupArgs;
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
        var policySetDefinitionAtManagementGroup = new PolicySetDefinitionAtManagementGroup("policySetDefinitionAtManagementGroup", PolicySetDefinitionAtManagementGroupArgs.builder()        
            .description("Policies to enforce low cost storage SKUs")
            .displayName("Cost Management")
            .managementGroupId("MyManagementGroup")
            .metadata(Map.of("category", "Cost Management"))
            .policyDefinitions(            
                Map.ofEntries(
                    Map.entry("parameters", Map.of("listOfAllowedSKUs", Map.of("value",                     
                        "Standard_GRS",
                        "Standard_LRS"))),
                    Map.entry("policyDefinitionId", "/providers/Microsoft.Management/managementgroups/MyManagementGroup/providers/Microsoft.Authorization/policyDefinitions/7433c107-6db4-4ad1-b57a-a76dce0154a1"),
                    Map.entry("policyDefinitionReferenceId", "Limit_Skus")
                ),
                Map.ofEntries(
                    Map.entry("parameters", Map.ofEntries(
                        Map.entry("prefix", Map.of("value", "DeptA")),
                        Map.entry("suffix", Map.of("value", "-LC"))
                    )),
                    Map.entry("policyDefinitionId", "/providers/Microsoft.Management/managementgroups/MyManagementGroup/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming"),
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

const policySetDefinitionAtManagementGroup = new azure_native.authorization.PolicySetDefinitionAtManagementGroup("policySetDefinitionAtManagementGroup", {
    description: "Policies to enforce low cost storage SKUs",
    displayName: "Cost Management",
    managementGroupId: "MyManagementGroup",
    metadata: {
        category: "Cost Management",
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
            policyDefinitionId: "/providers/Microsoft.Management/managementgroups/MyManagementGroup/providers/Microsoft.Authorization/policyDefinitions/7433c107-6db4-4ad1-b57a-a76dce0154a1",
            policyDefinitionReferenceId: "Limit_Skus",
        },
        {
            parameters: {
                prefix: {
                    value: "DeptA",
                },
                suffix: {
                    value: "-LC",
                },
            },
            policyDefinitionId: "/providers/Microsoft.Management/managementgroups/MyManagementGroup/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming",
            policyDefinitionReferenceId: "Resource_Naming",
        },
    ],
    policySetDefinitionName: "CostManagement",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

policy_set_definition_at_management_group = azure_native.authorization.PolicySetDefinitionAtManagementGroup("policySetDefinitionAtManagementGroup",
    description="Policies to enforce low cost storage SKUs",
    display_name="Cost Management",
    management_group_id="MyManagementGroup",
    metadata={
        "category": "Cost Management",
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
            "policyDefinitionId": "/providers/Microsoft.Management/managementgroups/MyManagementGroup/providers/Microsoft.Authorization/policyDefinitions/7433c107-6db4-4ad1-b57a-a76dce0154a1",
            "policyDefinitionReferenceId": "Limit_Skus",
        },
        {
            "parameters": {
                "prefix": azure_native.authorization.ParameterValuesValueArgs(
                    value="DeptA",
                ),
                "suffix": azure_native.authorization.ParameterValuesValueArgs(
                    value="-LC",
                ),
            },
            "policyDefinitionId": "/providers/Microsoft.Management/managementgroups/MyManagementGroup/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming",
            "policyDefinitionReferenceId": "Resource_Naming",
        },
    ],
    policy_set_definition_name="CostManagement")

```

```yaml
resources:
  policySetDefinitionAtManagementGroup:
    type: azure-native:authorization:PolicySetDefinitionAtManagementGroup
    properties:
      description: Policies to enforce low cost storage SKUs
      displayName: Cost Management
      managementGroupId: MyManagementGroup
      metadata:
        category: Cost Management
      policyDefinitions:
        - parameters:
            listOfAllowedSKUs:
              value:
                - Standard_GRS
                - Standard_LRS
          policyDefinitionId: /providers/Microsoft.Management/managementgroups/MyManagementGroup/providers/Microsoft.Authorization/policyDefinitions/7433c107-6db4-4ad1-b57a-a76dce0154a1
          policyDefinitionReferenceId: Limit_Skus
        - parameters:
            prefix:
              value: DeptA
            suffix:
              value: -LC
          policyDefinitionId: /providers/Microsoft.Management/managementgroups/MyManagementGroup/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming
          policyDefinitionReferenceId: Resource_Naming
      policySetDefinitionName: CostManagement

```

{{% /example %}}
{{% example %}}
### Create or update a policy set definition with groups at management group level
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var policySetDefinitionAtManagementGroup = new AzureNative.Authorization.PolicySetDefinitionAtManagementGroup("policySetDefinitionAtManagementGroup", new()
    {
        Description = "Policies to enforce low cost storage SKUs",
        DisplayName = "Cost Management",
        ManagementGroupId = "MyManagementGroup",
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
		_, err := authorization.NewPolicySetDefinitionAtManagementGroup(ctx, "policySetDefinitionAtManagementGroup", &authorization.PolicySetDefinitionAtManagementGroupArgs{
			Description:       pulumi.String("Policies to enforce low cost storage SKUs"),
			DisplayName:       pulumi.String("Cost Management"),
			ManagementGroupId: pulumi.String("MyManagementGroup"),
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
import com.pulumi.azurenative.authorization.PolicySetDefinitionAtManagementGroup;
import com.pulumi.azurenative.authorization.PolicySetDefinitionAtManagementGroupArgs;
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
        var policySetDefinitionAtManagementGroup = new PolicySetDefinitionAtManagementGroup("policySetDefinitionAtManagementGroup", PolicySetDefinitionAtManagementGroupArgs.builder()        
            .description("Policies to enforce low cost storage SKUs")
            .displayName("Cost Management")
            .managementGroupId("MyManagementGroup")
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

const policySetDefinitionAtManagementGroup = new azure_native.authorization.PolicySetDefinitionAtManagementGroup("policySetDefinitionAtManagementGroup", {
    description: "Policies to enforce low cost storage SKUs",
    displayName: "Cost Management",
    managementGroupId: "MyManagementGroup",
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

policy_set_definition_at_management_group = azure_native.authorization.PolicySetDefinitionAtManagementGroup("policySetDefinitionAtManagementGroup",
    description="Policies to enforce low cost storage SKUs",
    display_name="Cost Management",
    management_group_id="MyManagementGroup",
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
  policySetDefinitionAtManagementGroup:
    type: azure-native:authorization:PolicySetDefinitionAtManagementGroup
    properties:
      description: Policies to enforce low cost storage SKUs
      displayName: Cost Management
      managementGroupId: MyManagementGroup
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
$ pulumi import azure-native:authorization:PolicySetDefinitionAtManagementGroup CostManagement /providers/Microsoft.Management/managementgroups/MyManagementGroup/providers/Microsoft.Authorization/policySetDefinitions/CostManagement 
```
