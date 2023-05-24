Azure Resource Manager resource envelope.
API Version: 2022-10-01.
Previous API Version: 2021-03-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateOrUpdate Code Version.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var codeVersion = new AzureNative.MachineLearningServices.CodeVersion("codeVersion", new()
    {
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
		_, err := machinelearningservices.NewCodeVersion(ctx, "codeVersion", &machinelearningservices.CodeVersionArgs{
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
import com.pulumi.azurenative.machinelearningservices.CodeVersion;
import com.pulumi.azurenative.machinelearningservices.CodeVersionArgs;
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
        var codeVersion = new CodeVersion("codeVersion", CodeVersionArgs.builder()        
            .codeVersionProperties(Map.ofEntries(
                Map.entry("codeUri", "https://blobStorage/folderName"),
                Map.entry("description", "string"),
                Map.entry("isAnonymous", false),
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

const codeVersion = new azure_native.machinelearningservices.CodeVersion("codeVersion", {
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
    name: "string",
    resourceGroupName: "test-rg",
    version: "string",
    workspaceName: "my-aml-workspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

code_version = azure_native.machinelearningservices.CodeVersion("codeVersion",
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
    name="string",
    resource_group_name="test-rg",
    version="string",
    workspace_name="my-aml-workspace")

```

```yaml
resources:
  codeVersion:
    type: azure-native:machinelearningservices:CodeVersion
    properties:
      codeVersionProperties:
        codeUri: https://blobStorage/folderName
        description: string
        isAnonymous: false
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
$ pulumi import azure-native:machinelearningservices:CodeVersion string string 
```
