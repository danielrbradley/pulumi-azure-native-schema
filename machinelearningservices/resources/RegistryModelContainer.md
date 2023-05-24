Azure Resource Manager resource envelope.
API Version: 2023-04-01.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateOrUpdate Registry Model Container.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var registryModelContainer = new AzureNative.MachineLearningServices.RegistryModelContainer("registryModelContainer", new()
    {
        ModelContainerProperties = new AzureNative.MachineLearningServices.Inputs.ModelContainerArgs
        {
            Description = "Model container description",
            Tags = 
            {
                { "tag1", "value1" },
                { "tag2", "value2" },
            },
        },
        ModelName = "testContainer",
        RegistryName = "registry123",
        ResourceGroupName = "testrg123",
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
		_, err := machinelearningservices.NewRegistryModelContainer(ctx, "registryModelContainer", &machinelearningservices.RegistryModelContainerArgs{
			ModelContainerProperties: &machinelearningservices.ModelContainerTypeArgs{
				Description: pulumi.String("Model container description"),
				Tags: pulumi.StringMap{
					"tag1": pulumi.String("value1"),
					"tag2": pulumi.String("value2"),
				},
			},
			ModelName:         pulumi.String("testContainer"),
			RegistryName:      pulumi.String("registry123"),
			ResourceGroupName: pulumi.String("testrg123"),
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
import com.pulumi.azurenative.machinelearningservices.RegistryModelContainer;
import com.pulumi.azurenative.machinelearningservices.RegistryModelContainerArgs;
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
        var registryModelContainer = new RegistryModelContainer("registryModelContainer", RegistryModelContainerArgs.builder()        
            .modelContainerProperties(Map.ofEntries(
                Map.entry("description", "Model container description"),
                Map.entry("tags", Map.ofEntries(
                    Map.entry("tag1", "value1"),
                    Map.entry("tag2", "value2")
                ))
            ))
            .modelName("testContainer")
            .registryName("registry123")
            .resourceGroupName("testrg123")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const registryModelContainer = new azure_native.machinelearningservices.RegistryModelContainer("registryModelContainer", {
    modelContainerProperties: {
        description: "Model container description",
        tags: {
            tag1: "value1",
            tag2: "value2",
        },
    },
    modelName: "testContainer",
    registryName: "registry123",
    resourceGroupName: "testrg123",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

registry_model_container = azure_native.machinelearningservices.RegistryModelContainer("registryModelContainer",
    model_container_properties=azure_native.machinelearningservices.ModelContainerArgs(
        description="Model container description",
        tags={
            "tag1": "value1",
            "tag2": "value2",
        },
    ),
    model_name="testContainer",
    registry_name="registry123",
    resource_group_name="testrg123")

```

```yaml
resources:
  registryModelContainer:
    type: azure-native:machinelearningservices:RegistryModelContainer
    properties:
      modelContainerProperties:
        description: Model container description
        tags:
          tag1: value1
          tag2: value2
      modelName: testContainer
      registryName: registry123
      resourceGroupName: testrg123

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:machinelearningservices:RegistryModelContainer testContainer /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg123/providers/Microsoft.MachineLearningServices/registries/registry123/models/testContainer 
```
