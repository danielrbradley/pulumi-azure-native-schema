Azure Resource Manager resource envelope.
API Version: 2023-04-01.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateOrUpdate Registry Code Version.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var registryCodeVersion = new AzureNative.MachineLearningServices.RegistryCodeVersion("registryCodeVersion", new()
    {
        CodeName = "string",
        CodeVersionProperties = new AzureNative.MachineLearningServices.Inputs.CodeVersionArgs
        {
            CodeUri = "https://blobStorage/folderName",
            Description = "string",
            IsAnonymous = false,
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
		_, err := machinelearningservices.NewRegistryCodeVersion(ctx, "registryCodeVersion", &machinelearningservices.RegistryCodeVersionArgs{
			CodeName: pulumi.String("string"),
			CodeVersionProperties: &machinelearningservices.CodeVersionTypeArgs{
				CodeUri:     pulumi.String("https://blobStorage/folderName"),
				Description: pulumi.String("string"),
				IsAnonymous: pulumi.Bool(false),
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
import com.pulumi.azurenative.machinelearningservices.RegistryCodeVersion;
import com.pulumi.azurenative.machinelearningservices.RegistryCodeVersionArgs;
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
        var registryCodeVersion = new RegistryCodeVersion("registryCodeVersion", RegistryCodeVersionArgs.builder()        
            .codeName("string")
            .codeVersionProperties(Map.ofEntries(
                Map.entry("codeUri", "https://blobStorage/folderName"),
                Map.entry("description", "string"),
                Map.entry("isAnonymous", false),
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

const registryCodeVersion = new azure_native.machinelearningservices.RegistryCodeVersion("registryCodeVersion", {
    codeName: "string",
    codeVersionProperties: {
        codeUri: "https://blobStorage/folderName",
        description: "string",
        isAnonymous: false,
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

registry_code_version = azure_native.machinelearningservices.RegistryCodeVersion("registryCodeVersion",
    code_name="string",
    code_version_properties=azure_native.machinelearningservices.CodeVersionArgs(
        code_uri="https://blobStorage/folderName",
        description="string",
        is_anonymous=False,
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
  registryCodeVersion:
    type: azure-native:machinelearningservices:RegistryCodeVersion
    properties:
      codeName: string
      codeVersionProperties:
        codeUri: https://blobStorage/folderName
        description: string
        isAnonymous: false
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
$ pulumi import azure-native:machinelearningservices:RegistryCodeVersion string string 
```
