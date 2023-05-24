Azure Resource Manager resource envelope.
API Version: 2022-10-01.
Previous API Version: 2021-03-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateOrUpdate Data Version Base.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var dataVersion = new AzureNative.MachineLearningServices.DataVersion("dataVersion", new()
    {
        DataVersionBaseProperties = new AzureNative.MachineLearningServices.Inputs.UriFileDataVersionArgs
        {
            DataType = "uri_file",
            DataUri = "string",
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
		_, err := machinelearningservices.NewDataVersion(ctx, "dataVersion", &machinelearningservices.DataVersionArgs{
			DataVersionBaseProperties: machinelearningservices.UriFileDataVersion{
				DataType:    "uri_file",
				DataUri:     "string",
				Description: "string",
				IsAnonymous: false,
				Properties: map[string]interface{}{
					"string": "string",
				},
				Tags: map[string]interface{}{
					"string": "string",
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
import com.pulumi.azurenative.machinelearningservices.DataVersion;
import com.pulumi.azurenative.machinelearningservices.DataVersionArgs;
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
        var dataVersion = new DataVersion("dataVersion", DataVersionArgs.builder()        
            .dataVersionBaseProperties(Map.ofEntries(
                Map.entry("dataType", "uri_file"),
                Map.entry("dataUri", "string"),
                Map.entry("description", "string"),
                Map.entry("isAnonymous", false),
                Map.entry("properties", MLTableDataArgs.builder()
                    .string("string")
                    .build()),
                Map.entry("tags", MLTableDataArgs.builder()
                    .string("string")
                    .build())
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

const dataVersion = new azure_native.machinelearningservices.DataVersion("dataVersion", {
    dataVersionBaseProperties: {
        dataType: "uri_file",
        dataUri: "string",
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

data_version = azure_native.machinelearningservices.DataVersion("dataVersion",
    data_version_base_properties=azure_native.machinelearningservices.UriFileDataVersionArgs(
        data_type="uri_file",
        data_uri="string",
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
  dataVersion:
    type: azure-native:machinelearningservices:DataVersion
    properties:
      dataVersionBaseProperties:
        dataType: uri_file
        dataUri: string
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
$ pulumi import azure-native:machinelearningservices:DataVersion string string 
```
