Azure Resource Manager resource envelope.
API Version: 2022-10-01.
Previous API Version: 2022-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateOrUpdate Component Container.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var componentContainer = new AzureNative.MachineLearningServices.ComponentContainer("componentContainer", new()
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
        Name = "string",
        ResourceGroupName = "test-rg",
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
		_, err := machinelearningservices.NewComponentContainer(ctx, "componentContainer", &machinelearningservices.ComponentContainerArgs{
			ComponentContainerProperties: &machinelearningservices.ComponentContainerTypeArgs{
				Description: pulumi.String("string"),
				Properties: pulumi.StringMap{
					"string": pulumi.String("string"),
				},
				Tags: pulumi.StringMap{
					"string": pulumi.String("string"),
				},
			},
			Name:              pulumi.String("string"),
			ResourceGroupName: pulumi.String("test-rg"),
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
import com.pulumi.azurenative.machinelearningservices.ComponentContainer;
import com.pulumi.azurenative.machinelearningservices.ComponentContainerArgs;
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
        var componentContainer = new ComponentContainer("componentContainer", ComponentContainerArgs.builder()        
            .componentContainerProperties(Map.ofEntries(
                Map.entry("description", "string"),
                Map.entry("properties", Map.of("string", "string")),
                Map.entry("tags", Map.of("string", "string"))
            ))
            .name("string")
            .resourceGroupName("test-rg")
            .workspaceName("my-aml-workspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const componentContainer = new azure_native.machinelearningservices.ComponentContainer("componentContainer", {
    componentContainerProperties: {
        description: "string",
        properties: {
            string: "string",
        },
        tags: {
            string: "string",
        },
    },
    name: "string",
    resourceGroupName: "test-rg",
    workspaceName: "my-aml-workspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

component_container = azure_native.machinelearningservices.ComponentContainer("componentContainer",
    component_container_properties=azure_native.machinelearningservices.ComponentContainerArgs(
        description="string",
        properties={
            "string": "string",
        },
        tags={
            "string": "string",
        },
    ),
    name="string",
    resource_group_name="test-rg",
    workspace_name="my-aml-workspace")

```

```yaml
resources:
  componentContainer:
    type: azure-native:machinelearningservices:ComponentContainer
    properties:
      componentContainerProperties:
        description: string
        properties:
          string: string
        tags:
          string: string
      name: string
      resourceGroupName: test-rg
      workspaceName: my-aml-workspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:machinelearningservices:ComponentContainer string string 
```
