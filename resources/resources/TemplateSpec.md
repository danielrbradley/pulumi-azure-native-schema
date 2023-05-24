Template Spec object.
API Version: 2022-02-01.
Previous API Version: 2022-02-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### TemplateSpecsCreateUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var templateSpec = new AzureNative.Resources.TemplateSpec("templateSpec", new()
    {
        Description = "A very simple Template Spec",
        Location = "eastus",
        ResourceGroupName = "templateSpecRG",
        TemplateSpecName = "simpleTemplateSpec",
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
		_, err := resources.NewTemplateSpec(ctx, "templateSpec", &resources.TemplateSpecArgs{
			Description:       pulumi.String("A very simple Template Spec"),
			Location:          pulumi.String("eastus"),
			ResourceGroupName: pulumi.String("templateSpecRG"),
			TemplateSpecName:  pulumi.String("simpleTemplateSpec"),
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
import com.pulumi.azurenative.resources.TemplateSpec;
import com.pulumi.azurenative.resources.TemplateSpecArgs;
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
        var templateSpec = new TemplateSpec("templateSpec", TemplateSpecArgs.builder()        
            .description("A very simple Template Spec")
            .location("eastus")
            .resourceGroupName("templateSpecRG")
            .templateSpecName("simpleTemplateSpec")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const templateSpec = new azure_native.resources.TemplateSpec("templateSpec", {
    description: "A very simple Template Spec",
    location: "eastus",
    resourceGroupName: "templateSpecRG",
    templateSpecName: "simpleTemplateSpec",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

template_spec = azure_native.resources.TemplateSpec("templateSpec",
    description="A very simple Template Spec",
    location="eastus",
    resource_group_name="templateSpecRG",
    template_spec_name="simpleTemplateSpec")

```

```yaml
resources:
  templateSpec:
    type: azure-native:resources:TemplateSpec
    properties:
      description: A very simple Template Spec
      location: eastus
      resourceGroupName: templateSpecRG
      templateSpecName: simpleTemplateSpec

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:resources:TemplateSpec simpleTemplateSpec /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/templateSpecRG/providers/Microsoft.Resources/templateSpecs/simpleTemplateSpec 
```
