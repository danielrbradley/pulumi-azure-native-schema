Azure Resource Manager resource envelope.
API Version: 2023-04-01.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateOrUpdate Registry Model Version.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var registryModelVersion = new AzureNative.MachineLearningServices.RegistryModelVersion("registryModelVersion", new()
    {
        ModelName = "string",
        ModelVersionProperties = new AzureNative.MachineLearningServices.Inputs.ModelVersionArgs
        {
            Description = "string",
            Flavors = 
            {
                { "string", new AzureNative.MachineLearningServices.Inputs.FlavorDataArgs
                {
                    Data = 
                    {
                        { "string", "string" },
                    },
                } },
            },
            IsAnonymous = false,
            ModelType = "CustomModel",
            ModelUri = "string",
            Properties = 
            {
                { "string", "string" },
            },
            Tags = 
            {
                { "string", "string" },
            },
        },
        RegistryName = "my-aml-registry",
        ResourceGroupName = "test-rg",
        Version = "string",
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
		_, err := machinelearningservices.NewRegistryModelVersion(ctx, "registryModelVersion", &machinelearningservices.RegistryModelVersionArgs{
			ModelName: pulumi.String("string"),
			ModelVersionProperties: machinelearningservices.ModelVersionResponse{
				Description: pulumi.String("string"),
				Flavors: machinelearningservices.FlavorDataMap{
					"string": &machinelearningservices.FlavorDataArgs{
						Data: pulumi.StringMap{
							"string": pulumi.String("string"),
						},
					},
				},
				IsAnonymous: pulumi.Bool(false),
				ModelType:   pulumi.String("CustomModel"),
				ModelUri:    pulumi.String("string"),
				Properties: pulumi.StringMap{
					"string": pulumi.String("string"),
				},
				Tags: pulumi.StringMap{
					"string": pulumi.String("string"),
				},
			},
			RegistryName:      pulumi.String("my-aml-registry"),
			ResourceGroupName: pulumi.String("test-rg"),
			Version:           pulumi.String("string"),
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
import com.pulumi.azurenative.machinelearningservices.RegistryModelVersion;
import com.pulumi.azurenative.machinelearningservices.RegistryModelVersionArgs;
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
        var registryModelVersion = new RegistryModelVersion("registryModelVersion", RegistryModelVersionArgs.builder()        
            .modelName("string")
            .modelVersionProperties(Map.ofEntries(
                Map.entry("description", "string"),
                Map.entry("flavors", Map.of("string", Map.of("data", Map.of("string", "string")))),
                Map.entry("isAnonymous", false),
                Map.entry("modelType", "CustomModel"),
                Map.entry("modelUri", "string"),
                Map.entry("properties", Map.of("string", "string")),
                Map.entry("tags", Map.of("string", "string"))
            ))
            .registryName("my-aml-registry")
            .resourceGroupName("test-rg")
            .version("string")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const registryModelVersion = new azure_native.machinelearningservices.RegistryModelVersion("registryModelVersion", {
    modelName: "string",
    modelVersionProperties: {
        description: "string",
        flavors: {
            string: {
                data: {
                    string: "string",
                },
            },
        },
        isAnonymous: false,
        modelType: "CustomModel",
        modelUri: "string",
        properties: {
            string: "string",
        },
        tags: {
            string: "string",
        },
    },
    registryName: "my-aml-registry",
    resourceGroupName: "test-rg",
    version: "string",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

registry_model_version = azure_native.machinelearningservices.RegistryModelVersion("registryModelVersion",
    model_name="string",
    model_version_properties=azure_native.machinelearningservices.ModelVersionResponseArgs(
        description="string",
        flavors={
            "string": azure_native.machinelearningservices.FlavorDataArgs(
                data={
                    "string": "string",
                },
            ),
        },
        is_anonymous=False,
        model_type="CustomModel",
        model_uri="string",
        properties={
            "string": "string",
        },
        tags={
            "string": "string",
        },
    ),
    registry_name="my-aml-registry",
    resource_group_name="test-rg",
    version="string")

```

```yaml
resources:
  registryModelVersion:
    type: azure-native:machinelearningservices:RegistryModelVersion
    properties:
      modelName: string
      modelVersionProperties:
        description: string
        flavors:
          string:
            data:
              string: string
        isAnonymous: false
        modelType: CustomModel
        modelUri: string
        properties:
          string: string
        tags:
          string: string
      registryName: my-aml-registry
      resourceGroupName: test-rg
      version: string

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:machinelearningservices:RegistryModelVersion string string 
```
