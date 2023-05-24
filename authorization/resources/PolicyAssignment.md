The policy assignment.
API Version: 2022-06-01.
Previous API Version: 2020-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a policy assignment
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var policyAssignment = new AzureNative.Authorization.PolicyAssignment("policyAssignment", new()
    {
        Description = "Force resource names to begin with given DeptA and end with -LC",
        DisplayName = "Enforce resource naming rules",
        Metadata = 
        {
            { "assignedBy", "Special Someone" },
        },
        NonComplianceMessages = new[]
        {
            new AzureNative.Authorization.Inputs.NonComplianceMessageArgs
            {
                Message = "Resource names must start with 'DeptA' and end with '-LC'.",
            },
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
        PolicyAssignmentName = "EnforceNaming",
        PolicyDefinitionId = "/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming",
        Scope = "subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2",
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
		_, err := authorization.NewPolicyAssignment(ctx, "policyAssignment", &authorization.PolicyAssignmentArgs{
			Description: pulumi.String("Force resource names to begin with given DeptA and end with -LC"),
			DisplayName: pulumi.String("Enforce resource naming rules"),
			Metadata: pulumi.Any{
				AssignedBy: "Special Someone",
			},
			NonComplianceMessages: []authorization.NonComplianceMessageArgs{
				{
					Message: pulumi.String("Resource names must start with 'DeptA' and end with '-LC'."),
				},
			},
			Parameters: authorization.ParameterValuesValueMap{
				"prefix": &authorization.ParameterValuesValueArgs{
					Value: pulumi.Any("DeptA"),
				},
				"suffix": &authorization.ParameterValuesValueArgs{
					Value: pulumi.Any("-LC"),
				},
			},
			PolicyAssignmentName: pulumi.String("EnforceNaming"),
			PolicyDefinitionId:   pulumi.String("/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming"),
			Scope:                pulumi.String("subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2"),
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
import com.pulumi.azurenative.authorization.PolicyAssignment;
import com.pulumi.azurenative.authorization.PolicyAssignmentArgs;
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
        var policyAssignment = new PolicyAssignment("policyAssignment", PolicyAssignmentArgs.builder()        
            .description("Force resource names to begin with given DeptA and end with -LC")
            .displayName("Enforce resource naming rules")
            .metadata(Map.of("assignedBy", "Special Someone"))
            .nonComplianceMessages(Map.of("message", "Resource names must start with 'DeptA' and end with '-LC'."))
            .parameters(Map.ofEntries(
                Map.entry("prefix", Map.of("value", "DeptA")),
                Map.entry("suffix", Map.of("value", "-LC"))
            ))
            .policyAssignmentName("EnforceNaming")
            .policyDefinitionId("/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming")
            .scope("subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const policyAssignment = new azure_native.authorization.PolicyAssignment("policyAssignment", {
    description: "Force resource names to begin with given DeptA and end with -LC",
    displayName: "Enforce resource naming rules",
    metadata: {
        assignedBy: "Special Someone",
    },
    nonComplianceMessages: [{
        message: "Resource names must start with 'DeptA' and end with '-LC'.",
    }],
    parameters: {
        prefix: {
            value: "DeptA",
        },
        suffix: {
            value: "-LC",
        },
    },
    policyAssignmentName: "EnforceNaming",
    policyDefinitionId: "/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming",
    scope: "subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

policy_assignment = azure_native.authorization.PolicyAssignment("policyAssignment",
    description="Force resource names to begin with given DeptA and end with -LC",
    display_name="Enforce resource naming rules",
    metadata={
        "assignedBy": "Special Someone",
    },
    non_compliance_messages=[azure_native.authorization.NonComplianceMessageArgs(
        message="Resource names must start with 'DeptA' and end with '-LC'.",
    )],
    parameters={
        "prefix": azure_native.authorization.ParameterValuesValueArgs(
            value="DeptA",
        ),
        "suffix": azure_native.authorization.ParameterValuesValueArgs(
            value="-LC",
        ),
    },
    policy_assignment_name="EnforceNaming",
    policy_definition_id="/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming",
    scope="subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2")

```

```yaml
resources:
  policyAssignment:
    type: azure-native:authorization:PolicyAssignment
    properties:
      description: Force resource names to begin with given DeptA and end with -LC
      displayName: Enforce resource naming rules
      metadata:
        assignedBy: Special Someone
      nonComplianceMessages:
        - message: Resource names must start with 'DeptA' and end with '-LC'.
      parameters:
        prefix:
          value: DeptA
        suffix:
          value: -LC
      policyAssignmentName: EnforceNaming
      policyDefinitionId: /subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming
      scope: subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2

```

{{% /example %}}
{{% example %}}
### Create or update a policy assignment with a system assigned identity
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var policyAssignment = new AzureNative.Authorization.PolicyAssignment("policyAssignment", new()
    {
        Description = "Force resource names to begin with given DeptA and end with -LC",
        DisplayName = "Enforce resource naming rules",
        EnforcementMode = "Default",
        Identity = new AzureNative.Authorization.Inputs.IdentityArgs
        {
            Type = AzureNative.Authorization.ResourceIdentityType.SystemAssigned,
        },
        Location = "eastus",
        Metadata = 
        {
            { "assignedBy", "Foo Bar" },
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
        PolicyAssignmentName = "EnforceNaming",
        PolicyDefinitionId = "/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming",
        Scope = "subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2",
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
		_, err := authorization.NewPolicyAssignment(ctx, "policyAssignment", &authorization.PolicyAssignmentArgs{
			Description:     pulumi.String("Force resource names to begin with given DeptA and end with -LC"),
			DisplayName:     pulumi.String("Enforce resource naming rules"),
			EnforcementMode: pulumi.String("Default"),
			Identity: &authorization.IdentityArgs{
				Type: authorization.ResourceIdentityTypeSystemAssigned,
			},
			Location: pulumi.String("eastus"),
			Metadata: pulumi.Any{
				AssignedBy: "Foo Bar",
			},
			Parameters: authorization.ParameterValuesValueMap{
				"prefix": &authorization.ParameterValuesValueArgs{
					Value: pulumi.Any("DeptA"),
				},
				"suffix": &authorization.ParameterValuesValueArgs{
					Value: pulumi.Any("-LC"),
				},
			},
			PolicyAssignmentName: pulumi.String("EnforceNaming"),
			PolicyDefinitionId:   pulumi.String("/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming"),
			Scope:                pulumi.String("subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2"),
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
import com.pulumi.azurenative.authorization.PolicyAssignment;
import com.pulumi.azurenative.authorization.PolicyAssignmentArgs;
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
        var policyAssignment = new PolicyAssignment("policyAssignment", PolicyAssignmentArgs.builder()        
            .description("Force resource names to begin with given DeptA and end with -LC")
            .displayName("Enforce resource naming rules")
            .enforcementMode("Default")
            .identity(Map.of("type", "SystemAssigned"))
            .location("eastus")
            .metadata(Map.of("assignedBy", "Foo Bar"))
            .parameters(Map.ofEntries(
                Map.entry("prefix", Map.of("value", "DeptA")),
                Map.entry("suffix", Map.of("value", "-LC"))
            ))
            .policyAssignmentName("EnforceNaming")
            .policyDefinitionId("/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming")
            .scope("subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const policyAssignment = new azure_native.authorization.PolicyAssignment("policyAssignment", {
    description: "Force resource names to begin with given DeptA and end with -LC",
    displayName: "Enforce resource naming rules",
    enforcementMode: "Default",
    identity: {
        type: azure_native.authorization.ResourceIdentityType.SystemAssigned,
    },
    location: "eastus",
    metadata: {
        assignedBy: "Foo Bar",
    },
    parameters: {
        prefix: {
            value: "DeptA",
        },
        suffix: {
            value: "-LC",
        },
    },
    policyAssignmentName: "EnforceNaming",
    policyDefinitionId: "/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming",
    scope: "subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

policy_assignment = azure_native.authorization.PolicyAssignment("policyAssignment",
    description="Force resource names to begin with given DeptA and end with -LC",
    display_name="Enforce resource naming rules",
    enforcement_mode="Default",
    identity=azure_native.authorization.IdentityArgs(
        type=azure_native.authorization.ResourceIdentityType.SYSTEM_ASSIGNED,
    ),
    location="eastus",
    metadata={
        "assignedBy": "Foo Bar",
    },
    parameters={
        "prefix": azure_native.authorization.ParameterValuesValueArgs(
            value="DeptA",
        ),
        "suffix": azure_native.authorization.ParameterValuesValueArgs(
            value="-LC",
        ),
    },
    policy_assignment_name="EnforceNaming",
    policy_definition_id="/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming",
    scope="subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2")

```

```yaml
resources:
  policyAssignment:
    type: azure-native:authorization:PolicyAssignment
    properties:
      description: Force resource names to begin with given DeptA and end with -LC
      displayName: Enforce resource naming rules
      enforcementMode: Default
      identity:
        type: SystemAssigned
      location: eastus
      metadata:
        assignedBy: Foo Bar
      parameters:
        prefix:
          value: DeptA
        suffix:
          value: -LC
      policyAssignmentName: EnforceNaming
      policyDefinitionId: /subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming
      scope: subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2

```

{{% /example %}}
{{% example %}}
### Create or update a policy assignment with multiple non-compliance messages
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var policyAssignment = new AzureNative.Authorization.PolicyAssignment("policyAssignment", new()
    {
        DisplayName = "Enforce security policies",
        NonComplianceMessages = new[]
        {
            new AzureNative.Authorization.Inputs.NonComplianceMessageArgs
            {
                Message = "Resources must comply with all internal security policies. See <internal site URL> for more info.",
            },
            new AzureNative.Authorization.Inputs.NonComplianceMessageArgs
            {
                Message = "Resource names must start with 'DeptA' and end with '-LC'.",
                PolicyDefinitionReferenceId = "10420126870854049575",
            },
            new AzureNative.Authorization.Inputs.NonComplianceMessageArgs
            {
                Message = "Storage accounts must have firewall rules configured.",
                PolicyDefinitionReferenceId = "8572513655450389710",
            },
        },
        PolicyAssignmentName = "securityInitAssignment",
        PolicyDefinitionId = "/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policySetDefinitions/securityInitiative",
        Scope = "subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2",
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
		_, err := authorization.NewPolicyAssignment(ctx, "policyAssignment", &authorization.PolicyAssignmentArgs{
			DisplayName: pulumi.String("Enforce security policies"),
			NonComplianceMessages: []authorization.NonComplianceMessageArgs{
				{
					Message: pulumi.String("Resources must comply with all internal security policies. See <internal site URL> for more info."),
				},
				{
					Message:                     pulumi.String("Resource names must start with 'DeptA' and end with '-LC'."),
					PolicyDefinitionReferenceId: pulumi.String("10420126870854049575"),
				},
				{
					Message:                     pulumi.String("Storage accounts must have firewall rules configured."),
					PolicyDefinitionReferenceId: pulumi.String("8572513655450389710"),
				},
			},
			PolicyAssignmentName: pulumi.String("securityInitAssignment"),
			PolicyDefinitionId:   pulumi.String("/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policySetDefinitions/securityInitiative"),
			Scope:                pulumi.String("subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2"),
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
import com.pulumi.azurenative.authorization.PolicyAssignment;
import com.pulumi.azurenative.authorization.PolicyAssignmentArgs;
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
        var policyAssignment = new PolicyAssignment("policyAssignment", PolicyAssignmentArgs.builder()        
            .displayName("Enforce security policies")
            .nonComplianceMessages(            
                Map.of("message", "Resources must comply with all internal security policies. See <internal site URL> for more info."),
                Map.ofEntries(
                    Map.entry("message", "Resource names must start with 'DeptA' and end with '-LC'."),
                    Map.entry("policyDefinitionReferenceId", "10420126870854049575")
                ),
                Map.ofEntries(
                    Map.entry("message", "Storage accounts must have firewall rules configured."),
                    Map.entry("policyDefinitionReferenceId", "8572513655450389710")
                ))
            .policyAssignmentName("securityInitAssignment")
            .policyDefinitionId("/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policySetDefinitions/securityInitiative")
            .scope("subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const policyAssignment = new azure_native.authorization.PolicyAssignment("policyAssignment", {
    displayName: "Enforce security policies",
    nonComplianceMessages: [
        {
            message: "Resources must comply with all internal security policies. See <internal site URL> for more info.",
        },
        {
            message: "Resource names must start with 'DeptA' and end with '-LC'.",
            policyDefinitionReferenceId: "10420126870854049575",
        },
        {
            message: "Storage accounts must have firewall rules configured.",
            policyDefinitionReferenceId: "8572513655450389710",
        },
    ],
    policyAssignmentName: "securityInitAssignment",
    policyDefinitionId: "/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policySetDefinitions/securityInitiative",
    scope: "subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

policy_assignment = azure_native.authorization.PolicyAssignment("policyAssignment",
    display_name="Enforce security policies",
    non_compliance_messages=[
        azure_native.authorization.NonComplianceMessageArgs(
            message="Resources must comply with all internal security policies. See <internal site URL> for more info.",
        ),
        azure_native.authorization.NonComplianceMessageArgs(
            message="Resource names must start with 'DeptA' and end with '-LC'.",
            policy_definition_reference_id="10420126870854049575",
        ),
        azure_native.authorization.NonComplianceMessageArgs(
            message="Storage accounts must have firewall rules configured.",
            policy_definition_reference_id="8572513655450389710",
        ),
    ],
    policy_assignment_name="securityInitAssignment",
    policy_definition_id="/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policySetDefinitions/securityInitiative",
    scope="subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2")

```

```yaml
resources:
  policyAssignment:
    type: azure-native:authorization:PolicyAssignment
    properties:
      displayName: Enforce security policies
      nonComplianceMessages:
        - message: Resources must comply with all internal security policies. See <internal site URL> for more info.
        - message: Resource names must start with 'DeptA' and end with '-LC'.
          policyDefinitionReferenceId: '10420126870854049575'
        - message: Storage accounts must have firewall rules configured.
          policyDefinitionReferenceId: '8572513655450389710'
      policyAssignmentName: securityInitAssignment
      policyDefinitionId: /subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policySetDefinitions/securityInitiative
      scope: subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2

```

{{% /example %}}
{{% example %}}
### Create or update a policy assignment with overrides
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var policyAssignment = new AzureNative.Authorization.PolicyAssignment("policyAssignment", new()
    {
        Description = "Limit the resource location and resource SKU",
        DisplayName = "Limit the resource location and resource SKU",
        Metadata = 
        {
            { "assignedBy", "Special Someone" },
        },
        Overrides = new[]
        {
            new AzureNative.Authorization.Inputs.OverrideArgs
            {
                Kind = "policyEffect",
                Selectors = new[]
                {
                    new AzureNative.Authorization.Inputs.SelectorArgs
                    {
                        In = new[]
                        {
                            "Limit_Skus",
                            "Limit_Locations",
                        },
                        Kind = "policyDefinitionReferenceId",
                    },
                },
                Value = "Audit",
            },
        },
        PolicyAssignmentName = "CostManagement",
        PolicyDefinitionId = "/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policySetDefinitions/CostManagement",
        Scope = "subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2",
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
		_, err := authorization.NewPolicyAssignment(ctx, "policyAssignment", &authorization.PolicyAssignmentArgs{
			Description: pulumi.String("Limit the resource location and resource SKU"),
			DisplayName: pulumi.String("Limit the resource location and resource SKU"),
			Metadata: pulumi.Any{
				AssignedBy: "Special Someone",
			},
			Overrides: []authorization.OverrideArgs{
				{
					Kind: pulumi.String("policyEffect"),
					Selectors: authorization.SelectorArray{
						{
							In: pulumi.StringArray{
								pulumi.String("Limit_Skus"),
								pulumi.String("Limit_Locations"),
							},
							Kind: pulumi.String("policyDefinitionReferenceId"),
						},
					},
					Value: pulumi.String("Audit"),
				},
			},
			PolicyAssignmentName: pulumi.String("CostManagement"),
			PolicyDefinitionId:   pulumi.String("/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policySetDefinitions/CostManagement"),
			Scope:                pulumi.String("subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2"),
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
import com.pulumi.azurenative.authorization.PolicyAssignment;
import com.pulumi.azurenative.authorization.PolicyAssignmentArgs;
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
        var policyAssignment = new PolicyAssignment("policyAssignment", PolicyAssignmentArgs.builder()        
            .description("Limit the resource location and resource SKU")
            .displayName("Limit the resource location and resource SKU")
            .metadata(Map.of("assignedBy", "Special Someone"))
            .overrides(Map.ofEntries(
                Map.entry("kind", "policyEffect"),
                Map.entry("selectors", Map.ofEntries(
                    Map.entry("in",                     
                        "Limit_Skus",
                        "Limit_Locations"),
                    Map.entry("kind", "policyDefinitionReferenceId")
                )),
                Map.entry("value", "Audit")
            ))
            .policyAssignmentName("CostManagement")
            .policyDefinitionId("/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policySetDefinitions/CostManagement")
            .scope("subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const policyAssignment = new azure_native.authorization.PolicyAssignment("policyAssignment", {
    description: "Limit the resource location and resource SKU",
    displayName: "Limit the resource location and resource SKU",
    metadata: {
        assignedBy: "Special Someone",
    },
    overrides: [{
        kind: "policyEffect",
        selectors: [{
            "in": [
                "Limit_Skus",
                "Limit_Locations",
            ],
            kind: "policyDefinitionReferenceId",
        }],
        value: "Audit",
    }],
    policyAssignmentName: "CostManagement",
    policyDefinitionId: "/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policySetDefinitions/CostManagement",
    scope: "subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

policy_assignment = azure_native.authorization.PolicyAssignment("policyAssignment",
    description="Limit the resource location and resource SKU",
    display_name="Limit the resource location and resource SKU",
    metadata={
        "assignedBy": "Special Someone",
    },
    overrides=[{
        "kind": "policyEffect",
        "selectors": [azure_native.authorization.SelectorArgs(
            in_=[
                "Limit_Skus",
                "Limit_Locations",
            ],
            kind="policyDefinitionReferenceId",
        )],
        "value": "Audit",
    }],
    policy_assignment_name="CostManagement",
    policy_definition_id="/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policySetDefinitions/CostManagement",
    scope="subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2")

```

```yaml
resources:
  policyAssignment:
    type: azure-native:authorization:PolicyAssignment
    properties:
      description: Limit the resource location and resource SKU
      displayName: Limit the resource location and resource SKU
      metadata:
        assignedBy: Special Someone
      overrides:
        - kind: policyEffect
          selectors:
            - in:
                - Limit_Skus
                - Limit_Locations
              kind: policyDefinitionReferenceId
          value: Audit
      policyAssignmentName: CostManagement
      policyDefinitionId: /subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policySetDefinitions/CostManagement
      scope: subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2

```

{{% /example %}}
{{% example %}}
### Create or update a policy assignment with resource selectors
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var policyAssignment = new AzureNative.Authorization.PolicyAssignment("policyAssignment", new()
    {
        Description = "Limit the resource location and resource SKU",
        DisplayName = "Limit the resource location and resource SKU",
        Metadata = 
        {
            { "assignedBy", "Special Someone" },
        },
        PolicyAssignmentName = "CostManagement",
        PolicyDefinitionId = "/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policySetDefinitions/CostManagement",
        ResourceSelectors = new[]
        {
            new AzureNative.Authorization.Inputs.ResourceSelectorArgs
            {
                Name = "SDPRegions",
                Selectors = new[]
                {
                    new AzureNative.Authorization.Inputs.SelectorArgs
                    {
                        In = new[]
                        {
                            "eastus2euap",
                            "centraluseuap",
                        },
                        Kind = "resourceLocation",
                    },
                },
            },
        },
        Scope = "subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2",
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
		_, err := authorization.NewPolicyAssignment(ctx, "policyAssignment", &authorization.PolicyAssignmentArgs{
			Description: pulumi.String("Limit the resource location and resource SKU"),
			DisplayName: pulumi.String("Limit the resource location and resource SKU"),
			Metadata: pulumi.Any{
				AssignedBy: "Special Someone",
			},
			PolicyAssignmentName: pulumi.String("CostManagement"),
			PolicyDefinitionId:   pulumi.String("/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policySetDefinitions/CostManagement"),
			ResourceSelectors: []authorization.ResourceSelectorArgs{
				{
					Name: pulumi.String("SDPRegions"),
					Selectors: authorization.SelectorArray{
						{
							In: pulumi.StringArray{
								pulumi.String("eastus2euap"),
								pulumi.String("centraluseuap"),
							},
							Kind: pulumi.String("resourceLocation"),
						},
					},
				},
			},
			Scope: pulumi.String("subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2"),
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
import com.pulumi.azurenative.authorization.PolicyAssignment;
import com.pulumi.azurenative.authorization.PolicyAssignmentArgs;
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
        var policyAssignment = new PolicyAssignment("policyAssignment", PolicyAssignmentArgs.builder()        
            .description("Limit the resource location and resource SKU")
            .displayName("Limit the resource location and resource SKU")
            .metadata(Map.of("assignedBy", "Special Someone"))
            .policyAssignmentName("CostManagement")
            .policyDefinitionId("/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policySetDefinitions/CostManagement")
            .resourceSelectors(Map.ofEntries(
                Map.entry("name", "SDPRegions"),
                Map.entry("selectors", Map.ofEntries(
                    Map.entry("in",                     
                        "eastus2euap",
                        "centraluseuap"),
                    Map.entry("kind", "resourceLocation")
                ))
            ))
            .scope("subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const policyAssignment = new azure_native.authorization.PolicyAssignment("policyAssignment", {
    description: "Limit the resource location and resource SKU",
    displayName: "Limit the resource location and resource SKU",
    metadata: {
        assignedBy: "Special Someone",
    },
    policyAssignmentName: "CostManagement",
    policyDefinitionId: "/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policySetDefinitions/CostManagement",
    resourceSelectors: [{
        name: "SDPRegions",
        selectors: [{
            "in": [
                "eastus2euap",
                "centraluseuap",
            ],
            kind: "resourceLocation",
        }],
    }],
    scope: "subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

policy_assignment = azure_native.authorization.PolicyAssignment("policyAssignment",
    description="Limit the resource location and resource SKU",
    display_name="Limit the resource location and resource SKU",
    metadata={
        "assignedBy": "Special Someone",
    },
    policy_assignment_name="CostManagement",
    policy_definition_id="/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policySetDefinitions/CostManagement",
    resource_selectors=[{
        "name": "SDPRegions",
        "selectors": [azure_native.authorization.SelectorArgs(
            in_=[
                "eastus2euap",
                "centraluseuap",
            ],
            kind="resourceLocation",
        )],
    }],
    scope="subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2")

```

```yaml
resources:
  policyAssignment:
    type: azure-native:authorization:PolicyAssignment
    properties:
      description: Limit the resource location and resource SKU
      displayName: Limit the resource location and resource SKU
      metadata:
        assignedBy: Special Someone
      policyAssignmentName: CostManagement
      policyDefinitionId: /subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policySetDefinitions/CostManagement
      resourceSelectors:
        - name: SDPRegions
          selectors:
            - in:
                - eastus2euap
                - centraluseuap
              kind: resourceLocation
      scope: subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2

```

{{% /example %}}
{{% example %}}
### Create or update a policy assignment without enforcing policy effect during resource creation or update.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var policyAssignment = new AzureNative.Authorization.PolicyAssignment("policyAssignment", new()
    {
        Description = "Force resource names to begin with given DeptA and end with -LC",
        DisplayName = "Enforce resource naming rules",
        EnforcementMode = "DoNotEnforce",
        Metadata = 
        {
            { "assignedBy", "Special Someone" },
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
        PolicyAssignmentName = "EnforceNaming",
        PolicyDefinitionId = "/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming",
        Scope = "subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2",
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
		_, err := authorization.NewPolicyAssignment(ctx, "policyAssignment", &authorization.PolicyAssignmentArgs{
			Description:     pulumi.String("Force resource names to begin with given DeptA and end with -LC"),
			DisplayName:     pulumi.String("Enforce resource naming rules"),
			EnforcementMode: pulumi.String("DoNotEnforce"),
			Metadata: pulumi.Any{
				AssignedBy: "Special Someone",
			},
			Parameters: authorization.ParameterValuesValueMap{
				"prefix": &authorization.ParameterValuesValueArgs{
					Value: pulumi.Any("DeptA"),
				},
				"suffix": &authorization.ParameterValuesValueArgs{
					Value: pulumi.Any("-LC"),
				},
			},
			PolicyAssignmentName: pulumi.String("EnforceNaming"),
			PolicyDefinitionId:   pulumi.String("/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming"),
			Scope:                pulumi.String("subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2"),
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
import com.pulumi.azurenative.authorization.PolicyAssignment;
import com.pulumi.azurenative.authorization.PolicyAssignmentArgs;
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
        var policyAssignment = new PolicyAssignment("policyAssignment", PolicyAssignmentArgs.builder()        
            .description("Force resource names to begin with given DeptA and end with -LC")
            .displayName("Enforce resource naming rules")
            .enforcementMode("DoNotEnforce")
            .metadata(Map.of("assignedBy", "Special Someone"))
            .parameters(Map.ofEntries(
                Map.entry("prefix", Map.of("value", "DeptA")),
                Map.entry("suffix", Map.of("value", "-LC"))
            ))
            .policyAssignmentName("EnforceNaming")
            .policyDefinitionId("/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming")
            .scope("subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const policyAssignment = new azure_native.authorization.PolicyAssignment("policyAssignment", {
    description: "Force resource names to begin with given DeptA and end with -LC",
    displayName: "Enforce resource naming rules",
    enforcementMode: "DoNotEnforce",
    metadata: {
        assignedBy: "Special Someone",
    },
    parameters: {
        prefix: {
            value: "DeptA",
        },
        suffix: {
            value: "-LC",
        },
    },
    policyAssignmentName: "EnforceNaming",
    policyDefinitionId: "/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming",
    scope: "subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

policy_assignment = azure_native.authorization.PolicyAssignment("policyAssignment",
    description="Force resource names to begin with given DeptA and end with -LC",
    display_name="Enforce resource naming rules",
    enforcement_mode="DoNotEnforce",
    metadata={
        "assignedBy": "Special Someone",
    },
    parameters={
        "prefix": azure_native.authorization.ParameterValuesValueArgs(
            value="DeptA",
        ),
        "suffix": azure_native.authorization.ParameterValuesValueArgs(
            value="-LC",
        ),
    },
    policy_assignment_name="EnforceNaming",
    policy_definition_id="/subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming",
    scope="subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2")

```

```yaml
resources:
  policyAssignment:
    type: azure-native:authorization:PolicyAssignment
    properties:
      description: Force resource names to begin with given DeptA and end with -LC
      displayName: Enforce resource naming rules
      enforcementMode: DoNotEnforce
      metadata:
        assignedBy: Special Someone
      parameters:
        prefix:
          value: DeptA
        suffix:
          value: -LC
      policyAssignmentName: EnforceNaming
      policyDefinitionId: /subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming
      scope: subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:authorization:PolicyAssignment EnforceNaming /subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyAssignments/EnforceNaming 
```
