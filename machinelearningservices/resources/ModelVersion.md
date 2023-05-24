Azure Resource Manager resource envelope.
API Version: 2022-10-01.
Previous API Version: 2021-03-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateOrUpdate Model Version.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var modelVersion = new AzureNative.MachineLearningServices.ModelVersion("modelVersion", new()
    {
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
        Name = "string",
        ResourceGroupName = "test-rg",
        Version = "string",
        WorkspaceName = "my-aml-workspace",
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
		_, err := machinelearningservices.NewModelVersion(ctx, "modelVersion", &machinelearningservices.ModelVersionArgs{
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
			Name:              pulumi.String("string"),
			ResourceGroupName: pulumi.String("test-rg"),
			Version:           pulumi.String("string"),
			WorkspaceName:     pulumi.String("my-aml-workspace"),
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
import com.pulumi.azurenative.machinelearningservices.ModelVersion;
import com.pulumi.azurenative.machinelearningservices.ModelVersionArgs;
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
        var modelVersion = new ModelVersion("modelVersion", ModelVersionArgs.builder()        
            .modelVersionProperties(Map.ofEntries(
                Map.entry("description", "string"),
                Map.entry("flavors", Map.of("string", Map.of("data", Map.of("string", "string")))),
                Map.entry("isAnonymous", false),
                Map.entry("modelType", "CustomModel"),
                Map.entry("modelUri", "string"),
                Map.entry("properties", Map.of("string", "string")),
                Map.entry("tags", Map.of("string", "string"))
            ))
            .name("string")
            .resourceGroupName("test-rg")
            .version("string")
            .workspaceName("my-aml-workspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const modelVersion = new azure_native.machinelearningservices.ModelVersion("modelVersion", {
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
    name: "string",
    resourceGroupName: "test-rg",
    version: "string",
    workspaceName: "my-aml-workspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

model_version = azure_native.machinelearningservices.ModelVersion("modelVersion",
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
    name="string",
    resource_group_name="test-rg",
    version="string",
    workspace_name="my-aml-workspace")

```

```yaml
resources:
  modelVersion:
    type: azure-native:machinelearningservices:ModelVersion
    properties:
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
      name: string
      resourceGroupName: test-rg
      version: string
      workspaceName: my-aml-workspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:machinelearningservices:ModelVersion string string 
```
