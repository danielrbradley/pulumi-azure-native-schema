Blueprint artifact that deploys a Resource Manager template.
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
    var templateArtifact = new AzureNative.Blueprint.TemplateArtifact("templateArtifact", new()
    {
        ArtifactName = "storageTemplate",
        BlueprintName = "simpleBlueprint",
        Kind = "template",
        Parameters = 
        {
            { "storageAccountType", new AzureNative.Blueprint.Inputs.ParameterValueArgs
            {
                Value = "[parameters('storageAccountType')]",
            } },
        },
        ResourceGroup = "storageRG",
        ResourceScope = "providers/Microsoft.Management/managementGroups/ContosoOnlineGroup",
        Template = 
        {
            { "contentVersion", "1.0.0.0" },
            { "outputs", 
            {
                { "storageAccountName", 
                {
                    { "type", "string" },
                    { "value", "[variables('storageAccountName')]" },
                } },
            } },
            { "parameters", 
            {
                { "storageAccountType", 
                {
                    { "allowedValues", new[]
                    {
                        "Standard_LRS",
                        "Standard_GRS",
                        "Standard_ZRS",
                        "Premium_LRS",
                    } },
                    { "defaultValue", "Standard_LRS" },
                    { "metadata", 
                    {
                        { "description", "Storage Account type" },
                    } },
                    { "type", "string" },
                } },
            } },
            { "resources", new[]
            {
                
                {
                    { "apiVersion", "2016-01-01" },
                    { "kind", "Storage" },
                    { "location", "[resourceGroup().location]" },
                    { "name", "[variables('storageAccountName')]" },
                    { "properties", null },
                    { "sku", 
                    {
                        { "name", "[parameters('storageAccountType')]" },
                    } },
                    { "type", "Microsoft.Storage/storageAccounts" },
                },
            } },
            { "variables", 
            {
                { "storageAccountName", "[concat(uniquestring(resourceGroup().id), 'standardsa')]" },
            } },
        },
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
		_, err := blueprint.NewTemplateArtifact(ctx, "templateArtifact", &blueprint.TemplateArtifactArgs{
			ArtifactName:  pulumi.String("storageTemplate"),
			BlueprintName: pulumi.String("simpleBlueprint"),
			Kind:          pulumi.String("template"),
			Parameters: blueprint.ParameterValueMap{
				"storageAccountType": &blueprint.ParameterValueArgs{
					Value: pulumi.Any("[parameters('storageAccountType')]"),
				},
			},
			ResourceGroup: pulumi.String("storageRG"),
			ResourceScope: pulumi.String("providers/Microsoft.Management/managementGroups/ContosoOnlineGroup"),
			Template: pulumi.Any{
				ContentVersion: "1.0.0.0",
				Outputs: map[string]interface{}{
					"storageAccountName": map[string]interface{}{
						"type":  "string",
						"value": "[variables('storageAccountName')]",
					},
				},
				Parameters: map[string]interface{}{
					"storageAccountType": map[string]interface{}{
						"allowedValues": []string{
							"Standard_LRS",
							"Standard_GRS",
							"Standard_ZRS",
							"Premium_LRS",
						},
						"defaultValue": "Standard_LRS",
						"metadata": map[string]interface{}{
							"description": "Storage Account type",
						},
						"type": "string",
					},
				},
				Resources: []map[string]interface{}{
					map[string]interface{}{
						"apiVersion": "2016-01-01",
						"kind":       "Storage",
						"location":   "[resourceGroup().location]",
						"name":       "[variables('storageAccountName')]",
						"properties": nil,
						"sku": map[string]interface{}{
							"name": "[parameters('storageAccountType')]",
						},
						"type": "Microsoft.Storage/storageAccounts",
					},
				},
				Variables: map[string]interface{}{
					"storageAccountName": "[concat(uniquestring(resourceGroup().id), 'standardsa')]",
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
import com.pulumi.azurenative.blueprint.TemplateArtifact;
import com.pulumi.azurenative.blueprint.TemplateArtifactArgs;
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
        var templateArtifact = new TemplateArtifact("templateArtifact", TemplateArtifactArgs.builder()        
            .artifactName("storageTemplate")
            .blueprintName("simpleBlueprint")
            .kind("template")
            .parameters(Map.of("storageAccountType", Map.of("value", "[parameters('storageAccountType')]")))
            .resourceGroup("storageRG")
            .resourceScope("providers/Microsoft.Management/managementGroups/ContosoOnlineGroup")
            .template(Map.ofEntries(
                Map.entry("contentVersion", "1.0.0.0"),
                Map.entry("outputs", Map.of("storageAccountName", Map.ofEntries(
                    Map.entry("type", "string"),
                    Map.entry("value", "[variables('storageAccountName')]")
                ))),
                Map.entry("parameters", Map.of("storageAccountType", Map.ofEntries(
                    Map.entry("allowedValues",                     
                        "Standard_LRS",
                        "Standard_GRS",
                        "Standard_ZRS",
                        "Premium_LRS"),
                    Map.entry("defaultValue", "Standard_LRS"),
                    Map.entry("metadata", Map.of("description", "Storage Account type")),
                    Map.entry("type", "string")
                ))),
                Map.entry("resources", Map.ofEntries(
                    Map.entry("apiVersion", "2016-01-01"),
                    Map.entry("kind", "Storage"),
                    Map.entry("location", "[resourceGroup().location]"),
                    Map.entry("name", "[variables('storageAccountName')]"),
                    Map.entry("properties", ),
                    Map.entry("sku", Map.of("name", "[parameters('storageAccountType')]")),
                    Map.entry("type", "Microsoft.Storage/storageAccounts")
                )),
                Map.entry("variables", Map.of("storageAccountName", "[concat(uniquestring(resourceGroup().id), 'standardsa')]"))
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const templateArtifact = new azure_native.blueprint.TemplateArtifact("templateArtifact", {
    artifactName: "storageTemplate",
    blueprintName: "simpleBlueprint",
    kind: "template",
    parameters: {
        storageAccountType: {
            value: "[parameters('storageAccountType')]",
        },
    },
    resourceGroup: "storageRG",
    resourceScope: "providers/Microsoft.Management/managementGroups/ContosoOnlineGroup",
    template: {
        contentVersion: "1.0.0.0",
        outputs: {
            storageAccountName: {
                type: "string",
                value: "[variables('storageAccountName')]",
            },
        },
        parameters: {
            storageAccountType: {
                allowedValues: [
                    "Standard_LRS",
                    "Standard_GRS",
                    "Standard_ZRS",
                    "Premium_LRS",
                ],
                defaultValue: "Standard_LRS",
                metadata: {
                    description: "Storage Account type",
                },
                type: "string",
            },
        },
        resources: [{
            apiVersion: "2016-01-01",
            kind: "Storage",
            location: "[resourceGroup().location]",
            name: "[variables('storageAccountName')]",
            properties: {},
            sku: {
                name: "[parameters('storageAccountType')]",
            },
            type: "Microsoft.Storage/storageAccounts",
        }],
        variables: {
            storageAccountName: "[concat(uniquestring(resourceGroup().id), 'standardsa')]",
        },
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

template_artifact = azure_native.blueprint.TemplateArtifact("templateArtifact",
    artifact_name="storageTemplate",
    blueprint_name="simpleBlueprint",
    kind="template",
    parameters={
        "storageAccountType": azure_native.blueprint.ParameterValueArgs(
            value="[parameters('storageAccountType')]",
        ),
    },
    resource_group="storageRG",
    resource_scope="providers/Microsoft.Management/managementGroups/ContosoOnlineGroup",
    template={
        "contentVersion": "1.0.0.0",
        "outputs": {
            "storageAccountName": {
                "type": "string",
                "value": "[variables('storageAccountName')]",
            },
        },
        "parameters": {
            "storageAccountType": {
                "allowedValues": [
                    "Standard_LRS",
                    "Standard_GRS",
                    "Standard_ZRS",
                    "Premium_LRS",
                ],
                "defaultValue": "Standard_LRS",
                "metadata": {
                    "description": "Storage Account type",
                },
                "type": "string",
            },
        },
        "resources": [{
            "apiVersion": "2016-01-01",
            "kind": "Storage",
            "location": "[resourceGroup().location]",
            "name": "[variables('storageAccountName')]",
            "properties": {},
            "sku": {
                "name": "[parameters('storageAccountType')]",
            },
            "type": "Microsoft.Storage/storageAccounts",
        }],
        "variables": {
            "storageAccountName": "[concat(uniquestring(resourceGroup().id), 'standardsa')]",
        },
    })

```

```yaml
resources:
  templateArtifact:
    type: azure-native:blueprint:TemplateArtifact
    properties:
      artifactName: storageTemplate
      blueprintName: simpleBlueprint
      kind: template
      parameters:
        storageAccountType:
          value: '[parameters(''storageAccountType'')]'
      resourceGroup: storageRG
      resourceScope: providers/Microsoft.Management/managementGroups/ContosoOnlineGroup
      template:
        contentVersion: 1.0.0.0
        outputs:
          storageAccountName:
            type: string
            value: '[variables(''storageAccountName'')]'
        parameters:
          storageAccountType:
            allowedValues:
              - Standard_LRS
              - Standard_GRS
              - Standard_ZRS
              - Premium_LRS
            defaultValue: Standard_LRS
            metadata:
              description: Storage Account type
            type: string
        resources:
          - apiVersion: 2016-01-01
            kind: Storage
            location: '[resourceGroup().location]'
            name: '[variables(''storageAccountName'')]'
            properties: {}
            sku:
              name: '[parameters(''storageAccountType'')]'
            type: Microsoft.Storage/storageAccounts
        variables:
          storageAccountName: '[concat(uniquestring(resourceGroup().id), ''standardsa'')]'

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
    var templateArtifact = new AzureNative.Blueprint.TemplateArtifact("templateArtifact", new()
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
		_, err := blueprint.NewTemplateArtifact(ctx, "templateArtifact", &blueprint.TemplateArtifactArgs{
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
import com.pulumi.azurenative.blueprint.TemplateArtifact;
import com.pulumi.azurenative.blueprint.TemplateArtifactArgs;
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
        var templateArtifact = new TemplateArtifact("templateArtifact", TemplateArtifactArgs.builder()        
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

const templateArtifact = new azure_native.blueprint.TemplateArtifact("templateArtifact", {
    artifactName: "costCenterPolicy",
    blueprintName: "simpleBlueprint",
    resourceScope: "providers/Microsoft.Management/managementGroups/ContosoOnlineGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

template_artifact = azure_native.blueprint.TemplateArtifact("templateArtifact",
    artifact_name="costCenterPolicy",
    blueprint_name="simpleBlueprint",
    resource_scope="providers/Microsoft.Management/managementGroups/ContosoOnlineGroup")

```

```yaml
resources:
  templateArtifact:
    type: azure-native:blueprint:TemplateArtifact
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
    var templateArtifact = new AzureNative.Blueprint.TemplateArtifact("templateArtifact", new()
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
		_, err := blueprint.NewTemplateArtifact(ctx, "templateArtifact", &blueprint.TemplateArtifactArgs{
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
import com.pulumi.azurenative.blueprint.TemplateArtifact;
import com.pulumi.azurenative.blueprint.TemplateArtifactArgs;
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
        var templateArtifact = new TemplateArtifact("templateArtifact", TemplateArtifactArgs.builder()        
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

const templateArtifact = new azure_native.blueprint.TemplateArtifact("templateArtifact", {
    artifactName: "ownerAssignment",
    blueprintName: "simpleBlueprint",
    resourceScope: "providers/Microsoft.Management/managementGroups/ContosoOnlineGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

template_artifact = azure_native.blueprint.TemplateArtifact("templateArtifact",
    artifact_name="ownerAssignment",
    blueprint_name="simpleBlueprint",
    resource_scope="providers/Microsoft.Management/managementGroups/ContosoOnlineGroup")

```

```yaml
resources:
  templateArtifact:
    type: azure-native:blueprint:TemplateArtifact
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
    var templateArtifact = new AzureNative.Blueprint.TemplateArtifact("templateArtifact", new()
    {
        ArtifactName = "storageTemplate",
        BlueprintName = "simpleBlueprint",
        Kind = "template",
        Parameters = 
        {
            { "storageAccountType", new AzureNative.Blueprint.Inputs.ParameterValueArgs
            {
                Value = "[parameters('storageAccountType')]",
            } },
        },
        ResourceGroup = "storageRG",
        ResourceScope = "subscriptions/00000000-0000-0000-0000-000000000000",
        Template = 
        {
            { "contentVersion", "1.0.0.0" },
            { "outputs", 
            {
                { "storageAccountName", 
                {
                    { "type", "string" },
                    { "value", "[variables('storageAccountName')]" },
                } },
            } },
            { "parameters", 
            {
                { "storageAccountType", 
                {
                    { "allowedValues", new[]
                    {
                        "Standard_LRS",
                        "Standard_GRS",
                        "Standard_ZRS",
                        "Premium_LRS",
                    } },
                    { "defaultValue", "Standard_LRS" },
                    { "metadata", 
                    {
                        { "description", "Storage Account type" },
                    } },
                    { "type", "string" },
                } },
            } },
            { "resources", new[]
            {
                
                {
                    { "apiVersion", "2016-01-01" },
                    { "kind", "Storage" },
                    { "location", "[resourceGroup().location]" },
                    { "name", "[variables('storageAccountName')]" },
                    { "properties", null },
                    { "sku", 
                    {
                        { "name", "[parameters('storageAccountType')]" },
                    } },
                    { "type", "Microsoft.Storage/storageAccounts" },
                },
            } },
            { "variables", 
            {
                { "storageAccountName", "[concat(uniquestring(resourceGroup().id), 'standardsa')]" },
            } },
        },
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
		_, err := blueprint.NewTemplateArtifact(ctx, "templateArtifact", &blueprint.TemplateArtifactArgs{
			ArtifactName:  pulumi.String("storageTemplate"),
			BlueprintName: pulumi.String("simpleBlueprint"),
			Kind:          pulumi.String("template"),
			Parameters: blueprint.ParameterValueMap{
				"storageAccountType": &blueprint.ParameterValueArgs{
					Value: pulumi.Any("[parameters('storageAccountType')]"),
				},
			},
			ResourceGroup: pulumi.String("storageRG"),
			ResourceScope: pulumi.String("subscriptions/00000000-0000-0000-0000-000000000000"),
			Template: pulumi.Any{
				ContentVersion: "1.0.0.0",
				Outputs: map[string]interface{}{
					"storageAccountName": map[string]interface{}{
						"type":  "string",
						"value": "[variables('storageAccountName')]",
					},
				},
				Parameters: map[string]interface{}{
					"storageAccountType": map[string]interface{}{
						"allowedValues": []string{
							"Standard_LRS",
							"Standard_GRS",
							"Standard_ZRS",
							"Premium_LRS",
						},
						"defaultValue": "Standard_LRS",
						"metadata": map[string]interface{}{
							"description": "Storage Account type",
						},
						"type": "string",
					},
				},
				Resources: []map[string]interface{}{
					map[string]interface{}{
						"apiVersion": "2016-01-01",
						"kind":       "Storage",
						"location":   "[resourceGroup().location]",
						"name":       "[variables('storageAccountName')]",
						"properties": nil,
						"sku": map[string]interface{}{
							"name": "[parameters('storageAccountType')]",
						},
						"type": "Microsoft.Storage/storageAccounts",
					},
				},
				Variables: map[string]interface{}{
					"storageAccountName": "[concat(uniquestring(resourceGroup().id), 'standardsa')]",
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
import com.pulumi.azurenative.blueprint.TemplateArtifact;
import com.pulumi.azurenative.blueprint.TemplateArtifactArgs;
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
        var templateArtifact = new TemplateArtifact("templateArtifact", TemplateArtifactArgs.builder()        
            .artifactName("storageTemplate")
            .blueprintName("simpleBlueprint")
            .kind("template")
            .parameters(Map.of("storageAccountType", Map.of("value", "[parameters('storageAccountType')]")))
            .resourceGroup("storageRG")
            .resourceScope("subscriptions/00000000-0000-0000-0000-000000000000")
            .template(Map.ofEntries(
                Map.entry("contentVersion", "1.0.0.0"),
                Map.entry("outputs", Map.of("storageAccountName", Map.ofEntries(
                    Map.entry("type", "string"),
                    Map.entry("value", "[variables('storageAccountName')]")
                ))),
                Map.entry("parameters", Map.of("storageAccountType", Map.ofEntries(
                    Map.entry("allowedValues",                     
                        "Standard_LRS",
                        "Standard_GRS",
                        "Standard_ZRS",
                        "Premium_LRS"),
                    Map.entry("defaultValue", "Standard_LRS"),
                    Map.entry("metadata", Map.of("description", "Storage Account type")),
                    Map.entry("type", "string")
                ))),
                Map.entry("resources", Map.ofEntries(
                    Map.entry("apiVersion", "2016-01-01"),
                    Map.entry("kind", "Storage"),
                    Map.entry("location", "[resourceGroup().location]"),
                    Map.entry("name", "[variables('storageAccountName')]"),
                    Map.entry("properties", ),
                    Map.entry("sku", Map.of("name", "[parameters('storageAccountType')]")),
                    Map.entry("type", "Microsoft.Storage/storageAccounts")
                )),
                Map.entry("variables", Map.of("storageAccountName", "[concat(uniquestring(resourceGroup().id), 'standardsa')]"))
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const templateArtifact = new azure_native.blueprint.TemplateArtifact("templateArtifact", {
    artifactName: "storageTemplate",
    blueprintName: "simpleBlueprint",
    kind: "template",
    parameters: {
        storageAccountType: {
            value: "[parameters('storageAccountType')]",
        },
    },
    resourceGroup: "storageRG",
    resourceScope: "subscriptions/00000000-0000-0000-0000-000000000000",
    template: {
        contentVersion: "1.0.0.0",
        outputs: {
            storageAccountName: {
                type: "string",
                value: "[variables('storageAccountName')]",
            },
        },
        parameters: {
            storageAccountType: {
                allowedValues: [
                    "Standard_LRS",
                    "Standard_GRS",
                    "Standard_ZRS",
                    "Premium_LRS",
                ],
                defaultValue: "Standard_LRS",
                metadata: {
                    description: "Storage Account type",
                },
                type: "string",
            },
        },
        resources: [{
            apiVersion: "2016-01-01",
            kind: "Storage",
            location: "[resourceGroup().location]",
            name: "[variables('storageAccountName')]",
            properties: {},
            sku: {
                name: "[parameters('storageAccountType')]",
            },
            type: "Microsoft.Storage/storageAccounts",
        }],
        variables: {
            storageAccountName: "[concat(uniquestring(resourceGroup().id), 'standardsa')]",
        },
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

template_artifact = azure_native.blueprint.TemplateArtifact("templateArtifact",
    artifact_name="storageTemplate",
    blueprint_name="simpleBlueprint",
    kind="template",
    parameters={
        "storageAccountType": azure_native.blueprint.ParameterValueArgs(
            value="[parameters('storageAccountType')]",
        ),
    },
    resource_group="storageRG",
    resource_scope="subscriptions/00000000-0000-0000-0000-000000000000",
    template={
        "contentVersion": "1.0.0.0",
        "outputs": {
            "storageAccountName": {
                "type": "string",
                "value": "[variables('storageAccountName')]",
            },
        },
        "parameters": {
            "storageAccountType": {
                "allowedValues": [
                    "Standard_LRS",
                    "Standard_GRS",
                    "Standard_ZRS",
                    "Premium_LRS",
                ],
                "defaultValue": "Standard_LRS",
                "metadata": {
                    "description": "Storage Account type",
                },
                "type": "string",
            },
        },
        "resources": [{
            "apiVersion": "2016-01-01",
            "kind": "Storage",
            "location": "[resourceGroup().location]",
            "name": "[variables('storageAccountName')]",
            "properties": {},
            "sku": {
                "name": "[parameters('storageAccountType')]",
            },
            "type": "Microsoft.Storage/storageAccounts",
        }],
        "variables": {
            "storageAccountName": "[concat(uniquestring(resourceGroup().id), 'standardsa')]",
        },
    })

```

```yaml
resources:
  templateArtifact:
    type: azure-native:blueprint:TemplateArtifact
    properties:
      artifactName: storageTemplate
      blueprintName: simpleBlueprint
      kind: template
      parameters:
        storageAccountType:
          value: '[parameters(''storageAccountType'')]'
      resourceGroup: storageRG
      resourceScope: subscriptions/00000000-0000-0000-0000-000000000000
      template:
        contentVersion: 1.0.0.0
        outputs:
          storageAccountName:
            type: string
            value: '[variables(''storageAccountName'')]'
        parameters:
          storageAccountType:
            allowedValues:
              - Standard_LRS
              - Standard_GRS
              - Standard_ZRS
              - Premium_LRS
            defaultValue: Standard_LRS
            metadata:
              description: Storage Account type
            type: string
        resources:
          - apiVersion: 2016-01-01
            kind: Storage
            location: '[resourceGroup().location]'
            name: '[variables(''storageAccountName'')]'
            properties: {}
            sku:
              name: '[parameters(''storageAccountType'')]'
            type: Microsoft.Storage/storageAccounts
        variables:
          storageAccountName: '[concat(uniquestring(resourceGroup().id), ''standardsa'')]'

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
    var templateArtifact = new AzureNative.Blueprint.TemplateArtifact("templateArtifact", new()
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
		_, err := blueprint.NewTemplateArtifact(ctx, "templateArtifact", &blueprint.TemplateArtifactArgs{
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
import com.pulumi.azurenative.blueprint.TemplateArtifact;
import com.pulumi.azurenative.blueprint.TemplateArtifactArgs;
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
        var templateArtifact = new TemplateArtifact("templateArtifact", TemplateArtifactArgs.builder()        
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

const templateArtifact = new azure_native.blueprint.TemplateArtifact("templateArtifact", {
    artifactName: "costCenterPolicy",
    blueprintName: "simpleBlueprint",
    resourceScope: "subscriptions/00000000-0000-0000-0000-000000000000",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

template_artifact = azure_native.blueprint.TemplateArtifact("templateArtifact",
    artifact_name="costCenterPolicy",
    blueprint_name="simpleBlueprint",
    resource_scope="subscriptions/00000000-0000-0000-0000-000000000000")

```

```yaml
resources:
  templateArtifact:
    type: azure-native:blueprint:TemplateArtifact
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
    var templateArtifact = new AzureNative.Blueprint.TemplateArtifact("templateArtifact", new()
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
		_, err := blueprint.NewTemplateArtifact(ctx, "templateArtifact", &blueprint.TemplateArtifactArgs{
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
import com.pulumi.azurenative.blueprint.TemplateArtifact;
import com.pulumi.azurenative.blueprint.TemplateArtifactArgs;
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
        var templateArtifact = new TemplateArtifact("templateArtifact", TemplateArtifactArgs.builder()        
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

const templateArtifact = new azure_native.blueprint.TemplateArtifact("templateArtifact", {
    artifactName: "ownerAssignment",
    blueprintName: "simpleBlueprint",
    resourceScope: "subscriptions/00000000-0000-0000-0000-000000000000",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

template_artifact = azure_native.blueprint.TemplateArtifact("templateArtifact",
    artifact_name="ownerAssignment",
    blueprint_name="simpleBlueprint",
    resource_scope="subscriptions/00000000-0000-0000-0000-000000000000")

```

```yaml
resources:
  templateArtifact:
    type: azure-native:blueprint:TemplateArtifact
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
$ pulumi import azure-native:blueprint:TemplateArtifact ownerAssignment /subscriptions/00000000-0000-0000-0000-000000000000/providers/Microsoft.Blueprint/blueprints/simpleBlueprint/artifacts/ownerAssignment 
```
