Template Spec Version object.
API Version: 2022-02-01.
Previous API Version: 2022-02-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### TemplateSpecVersionsCreateUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var templateSpecVersion = new AzureNative.Resources.TemplateSpecVersion("templateSpecVersion", new()
    {
        Description = "This is version v1.0 of our template content",
        Location = "eastus",
        MainTemplate = 
        {
            { "$schema", "http://schema.management.azure.com/schemas/2015-01-01/deploymentTemplate.json#" },
            { "contentVersion", "1.0.0.0" },
            { "parameters", null },
            { "resources", new[] {} },
        },
        ResourceGroupName = "templateSpecRG",
        TemplateSpecName = "simpleTemplateSpec",
        TemplateSpecVersion = "v1.0",
    });

});


```

```go
package main

import (
	resources "github.com/pulumi/pulumi-azure-native-sdk/resources"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := resources.NewTemplateSpecVersion(ctx, "templateSpecVersion", &resources.TemplateSpecVersionArgs{
			Description: pulumi.String("This is version v1.0 of our template content"),
			Location:    pulumi.String("eastus"),
			MainTemplate: pulumi.Any{
				Schema:         "http://schema.management.azure.com/schemas/2015-01-01/deploymentTemplate.json#",
				ContentVersion: "1.0.0.0",
				Parameters:     nil,
				Resources:      []interface{}{},
			},
			ResourceGroupName:   pulumi.String("templateSpecRG"),
			TemplateSpecName:    pulumi.String("simpleTemplateSpec"),
			TemplateSpecVersion: pulumi.String("v1.0"),
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
import com.pulumi.azurenative.resources.TemplateSpecVersion;
import com.pulumi.azurenative.resources.TemplateSpecVersionArgs;
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
        var templateSpecVersion = new TemplateSpecVersion("templateSpecVersion", TemplateSpecVersionArgs.builder()        
            .description("This is version v1.0 of our template content")
            .location("eastus")
            .mainTemplate(Map.ofEntries(
                Map.entry("$schema", "http://schema.management.azure.com/schemas/2015-01-01/deploymentTemplate.json#"),
                Map.entry("contentVersion", "1.0.0.0"),
                Map.entry("parameters", ),
                Map.entry("resources", )
            ))
            .resourceGroupName("templateSpecRG")
            .templateSpecName("simpleTemplateSpec")
            .templateSpecVersion("v1.0")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const templateSpecVersion = new azure_native.resources.TemplateSpecVersion("templateSpecVersion", {
    description: "This is version v1.0 of our template content",
    location: "eastus",
    mainTemplate: {
        $schema: "http://schema.management.azure.com/schemas/2015-01-01/deploymentTemplate.json#",
        contentVersion: "1.0.0.0",
        parameters: {},
        resources: [],
    },
    resourceGroupName: "templateSpecRG",
    templateSpecName: "simpleTemplateSpec",
    templateSpecVersion: "v1.0",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

template_spec_version = azure_native.resources.TemplateSpecVersion("templateSpecVersion",
    description="This is version v1.0 of our template content",
    location="eastus",
    main_template={
        "$schema": "http://schema.management.azure.com/schemas/2015-01-01/deploymentTemplate.json#",
        "contentVersion": "1.0.0.0",
        "parameters": {},
        "resources": [],
    },
    resource_group_name="templateSpecRG",
    template_spec_name="simpleTemplateSpec",
    template_spec_version="v1.0")

```

```yaml
resources:
  templateSpecVersion:
    type: azure-native:resources:TemplateSpecVersion
    properties:
      description: This is version v1.0 of our template content
      location: eastus
      mainTemplate:
        $schema: http://schema.management.azure.com/schemas/2015-01-01/deploymentTemplate.json#
        contentVersion: 1.0.0.0
        parameters: {}
        resources: []
      resourceGroupName: templateSpecRG
      templateSpecName: simpleTemplateSpec
      templateSpecVersion: v1.0

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:resources:TemplateSpecVersion v1.0 /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/templateSpecRG/providers/Microsoft.Resources/templateSpecs/simpleTemplateSpec/versions/v1.0 
```
