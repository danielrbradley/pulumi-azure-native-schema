The policy definition.
API Version: 2021-06-01.
Previous API Version: 2020-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a policy definition
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var policyDefinition = new AzureNative.Authorization.PolicyDefinition("policyDefinition", new()
    {
        Description = "Force resource names to begin with given 'prefix' and/or end with given 'suffix'",
        DisplayName = "Enforce resource naming convention",
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
		_, err := authorization.NewPolicyDefinition(ctx, "policyDefinition", &authorization.PolicyDefinitionArgs{
			Description: pulumi.String("Force resource names to begin with given 'prefix' and/or end with given 'suffix'"),
			DisplayName: pulumi.String("Enforce resource naming convention"),
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
import com.pulumi.azurenative.authorization.PolicyDefinition;
import com.pulumi.azurenative.authorization.PolicyDefinitionArgs;
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
        var policyDefinition = new PolicyDefinition("policyDefinition", PolicyDefinitionArgs.builder()        
            .description("Force resource names to begin with given 'prefix' and/or end with given 'suffix'")
            .displayName("Enforce resource naming convention")
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

const policyDefinition = new azure_native.authorization.PolicyDefinition("policyDefinition", {
    description: "Force resource names to begin with given 'prefix' and/or end with given 'suffix'",
    displayName: "Enforce resource naming convention",
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

policy_definition = azure_native.authorization.PolicyDefinition("policyDefinition",
    description="Force resource names to begin with given 'prefix' and/or end with given 'suffix'",
    display_name="Enforce resource naming convention",
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
  policyDefinition:
    type: azure-native:authorization:PolicyDefinition
    properties:
      description: Force resource names to begin with given 'prefix' and/or end with given 'suffix'
      displayName: Enforce resource naming convention
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
{{% example %}}
### Create or update a policy definition with advanced parameters
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var policyDefinition = new AzureNative.Authorization.PolicyDefinition("policyDefinition", new()
    {
        Description = "Audit enabling of logs and retain them up to a year. This enables recreation of activity trails for investigation purposes when a security incident occurs or your network is compromised",
        DisplayName = "Event Hubs should have diagnostic logging enabled",
        Metadata = 
        {
            { "category", "Event Hub" },
        },
        Mode = "Indexed",
        Parameters = 
        {
            { "requiredRetentionDays", new AzureNative.Authorization.Inputs.ParameterDefinitionsValueArgs
            {
                AllowedValues = new[]
                {
                    0,
                    30,
                    90,
                    180,
                    365,
                },
                DefaultValue = 365,
                Metadata = new AzureNative.Authorization.Inputs.ParameterDefinitionsValueMetadataArgs
                {
                    Description = "The required diagnostic logs retention in days",
                    DisplayName = "Required retention (days)",
                },
                Type = "Integer",
            } },
        },
        PolicyDefinitionName = "EventHubDiagnosticLogs",
        PolicyRule = 
        {
            { "if", 
            {
                { "equals", "Microsoft.EventHub/namespaces" },
                { "field", "type" },
            } },
            { "then", 
            {
                { "details", 
                {
                    { "existenceCondition", 
                    {
                        { "allOf", new[]
                        {
                            
                            {
                                { "equals", "true" },
                                { "field", "Microsoft.Insights/diagnosticSettings/logs[*].retentionPolicy.enabled" },
                            },
                            
                            {
                                { "equals", "[parameters('requiredRetentionDays')]" },
                                { "field", "Microsoft.Insights/diagnosticSettings/logs[*].retentionPolicy.days" },
                            },
                        } },
                    } },
                    { "type", "Microsoft.Insights/diagnosticSettings" },
                } },
                { "effect", "AuditIfNotExists" },
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
		_, err := authorization.NewPolicyDefinition(ctx, "policyDefinition", &authorization.PolicyDefinitionArgs{
			Description: pulumi.String("Audit enabling of logs and retain them up to a year. This enables recreation of activity trails for investigation purposes when a security incident occurs or your network is compromised"),
			DisplayName: pulumi.String("Event Hubs should have diagnostic logging enabled"),
			Metadata: pulumi.Any{
				Category: "Event Hub",
			},
			Mode: pulumi.String("Indexed"),
			Parameters: authorization.ParameterDefinitionsValueMap{
				"requiredRetentionDays": &authorization.ParameterDefinitionsValueArgs{
					AllowedValues: pulumi.AnyArray{
						pulumi.Any(0),
						pulumi.Any(30),
						pulumi.Any(90),
						pulumi.Any(180),
						pulumi.Any(365),
					},
					DefaultValue: pulumi.Any(365),
					Metadata: &authorization.ParameterDefinitionsValueMetadataArgs{
						Description: pulumi.String("The required diagnostic logs retention in days"),
						DisplayName: pulumi.String("Required retention (days)"),
					},
					Type: pulumi.String("Integer"),
				},
			},
			PolicyDefinitionName: pulumi.String("EventHubDiagnosticLogs"),
			PolicyRule: pulumi.Any{
				If: map[string]interface{}{
					"equals": "Microsoft.EventHub/namespaces",
					"field":  "type",
				},
				Then: map[string]interface{}{
					"details": map[string]interface{}{
						"existenceCondition": map[string]interface{}{
							"allOf": []map[string]interface{}{
								map[string]interface{}{
									"equals": "true",
									"field":  "Microsoft.Insights/diagnosticSettings/logs[*].retentionPolicy.enabled",
								},
								map[string]interface{}{
									"equals": "[parameters('requiredRetentionDays')]",
									"field":  "Microsoft.Insights/diagnosticSettings/logs[*].retentionPolicy.days",
								},
							},
						},
						"type": "Microsoft.Insights/diagnosticSettings",
					},
					"effect": "AuditIfNotExists",
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
import com.pulumi.azurenative.authorization.PolicyDefinition;
import com.pulumi.azurenative.authorization.PolicyDefinitionArgs;
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
        var policyDefinition = new PolicyDefinition("policyDefinition", PolicyDefinitionArgs.builder()        
            .description("Audit enabling of logs and retain them up to a year. This enables recreation of activity trails for investigation purposes when a security incident occurs or your network is compromised")
            .displayName("Event Hubs should have diagnostic logging enabled")
            .metadata(Map.of("category", "Event Hub"))
            .mode("Indexed")
            .parameters(Map.of("requiredRetentionDays", Map.ofEntries(
                Map.entry("allowedValues",                 
                    0,
                    30,
                    90,
                    180,
                    365),
                Map.entry("defaultValue", 365),
                Map.entry("metadata", Map.ofEntries(
                    Map.entry("description", "The required diagnostic logs retention in days"),
                    Map.entry("displayName", "Required retention (days)")
                )),
                Map.entry("type", "Integer")
            )))
            .policyDefinitionName("EventHubDiagnosticLogs")
            .policyRule(Map.ofEntries(
                Map.entry("if", Map.ofEntries(
                    Map.entry("equals", "Microsoft.EventHub/namespaces"),
                    Map.entry("field", "type")
                )),
                Map.entry("then", Map.ofEntries(
                    Map.entry("details", Map.ofEntries(
                        Map.entry("existenceCondition", Map.of("allOf",                         
                            Map.ofEntries(
                                Map.entry("equals", "true"),
                                Map.entry("field", "Microsoft.Insights/diagnosticSettings/logs[*].retentionPolicy.enabled")
                            ),
                            Map.ofEntries(
                                Map.entry("equals", "[parameters('requiredRetentionDays')]"),
                                Map.entry("field", "Microsoft.Insights/diagnosticSettings/logs[*].retentionPolicy.days")
                            ))),
                        Map.entry("type", "Microsoft.Insights/diagnosticSettings")
                    )),
                    Map.entry("effect", "AuditIfNotExists")
                ))
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const policyDefinition = new azure_native.authorization.PolicyDefinition("policyDefinition", {
    description: "Audit enabling of logs and retain them up to a year. This enables recreation of activity trails for investigation purposes when a security incident occurs or your network is compromised",
    displayName: "Event Hubs should have diagnostic logging enabled",
    metadata: {
        category: "Event Hub",
    },
    mode: "Indexed",
    parameters: {
        requiredRetentionDays: {
            allowedValues: [
                0,
                30,
                90,
                180,
                365,
            ],
            defaultValue: 365,
            metadata: {
                description: "The required diagnostic logs retention in days",
                displayName: "Required retention (days)",
            },
            type: "Integer",
        },
    },
    policyDefinitionName: "EventHubDiagnosticLogs",
    policyRule: {
        "if": {
            equals: "Microsoft.EventHub/namespaces",
            field: "type",
        },
        then: {
            details: {
                existenceCondition: {
                    allOf: [
                        {
                            equals: "true",
                            field: "Microsoft.Insights/diagnosticSettings/logs[*].retentionPolicy.enabled",
                        },
                        {
                            equals: "[parameters('requiredRetentionDays')]",
                            field: "Microsoft.Insights/diagnosticSettings/logs[*].retentionPolicy.days",
                        },
                    ],
                },
                type: "Microsoft.Insights/diagnosticSettings",
            },
            effect: "AuditIfNotExists",
        },
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

policy_definition = azure_native.authorization.PolicyDefinition("policyDefinition",
    description="Audit enabling of logs and retain them up to a year. This enables recreation of activity trails for investigation purposes when a security incident occurs or your network is compromised",
    display_name="Event Hubs should have diagnostic logging enabled",
    metadata={
        "category": "Event Hub",
    },
    mode="Indexed",
    parameters={
        "requiredRetentionDays": azure_native.authorization.ParameterDefinitionsValueArgs(
            allowed_values=[
                0,
                30,
                90,
                180,
                365,
            ],
            default_value=365,
            metadata=azure_native.authorization.ParameterDefinitionsValueMetadataArgs(
                description="The required diagnostic logs retention in days",
                display_name="Required retention (days)",
            ),
            type="Integer",
        ),
    },
    policy_definition_name="EventHubDiagnosticLogs",
    policy_rule={
        "if": {
            "equals": "Microsoft.EventHub/namespaces",
            "field": "type",
        },
        "then": {
            "details": {
                "existenceCondition": {
                    "allOf": [
                        {
                            "equals": "true",
                            "field": "Microsoft.Insights/diagnosticSettings/logs[*].retentionPolicy.enabled",
                        },
                        {
                            "equals": "[parameters('requiredRetentionDays')]",
                            "field": "Microsoft.Insights/diagnosticSettings/logs[*].retentionPolicy.days",
                        },
                    ],
                },
                "type": "Microsoft.Insights/diagnosticSettings",
            },
            "effect": "AuditIfNotExists",
        },
    })

```

```yaml
resources:
  policyDefinition:
    type: azure-native:authorization:PolicyDefinition
    properties:
      description: Audit enabling of logs and retain them up to a year. This enables recreation of activity trails for investigation purposes when a security incident occurs or your network is compromised
      displayName: Event Hubs should have diagnostic logging enabled
      metadata:
        category: Event Hub
      mode: Indexed
      parameters:
        requiredRetentionDays:
          allowedValues:
            - 0
            - 30
            - 90
            - 180
            - 365
          defaultValue: 365
          metadata:
            description: The required diagnostic logs retention in days
            displayName: Required retention (days)
          type: Integer
      policyDefinitionName: EventHubDiagnosticLogs
      policyRule:
        if:
          equals: Microsoft.EventHub/namespaces
          field: type
        then:
          details:
            existenceCondition:
              allOf:
                - equals: 'true'
                  field: Microsoft.Insights/diagnosticSettings/logs[*].retentionPolicy.enabled
                - equals: '[parameters(''requiredRetentionDays'')]'
                  field: Microsoft.Insights/diagnosticSettings/logs[*].retentionPolicy.days
            type: Microsoft.Insights/diagnosticSettings
          effect: AuditIfNotExists

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:authorization:PolicyDefinition ResourceNaming /subscriptions/ae640e6b-ba3e-4256-9d62-2993eecfa6f2/providers/Microsoft.Authorization/policyDefinitions/ResourceNaming 
```
