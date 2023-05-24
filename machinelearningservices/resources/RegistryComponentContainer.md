Azure Resource Manager resource envelope.
API Version: 2023-04-01.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateOrUpdate Registry Component Container.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var registryComponentContainer = new AzureNative.MachineLearningServices.RegistryComponentContainer("registryComponentContainer", new()
    {
        ComponentContainerProperties = new AzureNative.MachineLearningServices.Inputs.ComponentContainerArgs
        {
            Description = "string",
            Properties = 
            {
                { "string", "string" },
            },
            Tags = 
            {
                { "string", "string" },
            },
        },
        ComponentName = "string",
        RegistryName = "my-aml-registry",
        ResourceGroupName = "test-rg",
    });

});


```

```go
package main

import (
	machinelearningservices "github.com/pulumi/pulumi-azure-native-sdk/machinelearningservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := machinelearningservices.NewRegistryComponentContainer(ctx, "registryComponentContainer", &machinelearningservices.RegistryComponentContainerArgs{
			ComponentContainerProperties: &machinelearningservices.ComponentContainerTypeArgs{
				Description: pulumi.String("string"),
				Properties: pulumi.StringMap{
					"string": pulumi.String("string"),
				},
				Tags: pulumi.StringMap{
					"string": pulumi.String("string"),
				},
			},
			ComponentName:     pulumi.String("string"),
			RegistryName:      pulumi.String("my-aml-registry"),
			ResourceGroupName: pulumi.String("test-rg"),
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
import com.pulumi.azurenative.machinelearningservices.RegistryComponentContainer;
import com.pulumi.azurenative.machinelearningservices.RegistryComponentContainerArgs;
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
        var registryComponentContainer = new RegistryComponentContainer("registryComponentContainer", RegistryComponentContainerArgs.builder()        
            .componentContainerProperties(Map.ofEntries(
                Map.entry("description", "string"),
                Map.entry("properties", Map.of("string", "string")),
                Map.entry("tags", Map.of("string", "string"))
            ))
            .componentName("string")
            .registryName("my-aml-registry")
            .resourceGroupName("test-rg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const registryComponentContainer = new azure_native.machinelearningservices.RegistryComponentContainer("registryComponentContainer", {
    componentContainerProperties: {
        description: "string",
        properties: {
            string: "string",
        },
        tags: {
            string: "string",
        },
    },
    componentName: "string",
    registryName: "my-aml-registry",
    resourceGroupName: "test-rg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

registry_component_container = azure_native.machinelearningservices.RegistryComponentContainer("registryComponentContainer",
    component_container_properties=azure_native.machinelearningservices.ComponentContainerArgs(
        description="string",
        properties={
            "string": "string",
        },
        tags={
            "string": "string",
        },
    ),
    component_name="string",
    registry_name="my-aml-registry",
    resource_group_name="test-rg")

```

```yaml
resources:
  registryComponentContainer:
    type: azure-native:machinelearningservices:RegistryComponentContainer
    properties:
      componentContainerProperties:
        description: string
        properties:
          string: string
        tags:
          string: string
      componentName: string
      registryName: my-aml-registry
      resourceGroupName: test-rg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:machinelearningservices:RegistryComponentContainer string string 
```
