Azure Resource Manager resource envelope.
API Version: 2023-04-01.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateOrUpdate Registry Code Container.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var registryCodeContainer = new AzureNative.MachineLearningServices.RegistryCodeContainer("registryCodeContainer", new()
    {
        CodeContainerProperties = new AzureNative.MachineLearningServices.Inputs.CodeContainerArgs
        {
            Description = "string",
            Tags = 
            {
                { "tag1", "value1" },
                { "tag2", "value2" },
            },
        },
        CodeName = "testContainer",
        RegistryName = "testregistry",
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
		_, err := machinelearningservices.NewRegistryCodeContainer(ctx, "registryCodeContainer", &machinelearningservices.RegistryCodeContainerArgs{
			CodeContainerProperties: &machinelearningservices.CodeContainerTypeArgs{
				Description: pulumi.String("string"),
				Tags: pulumi.StringMap{
					"tag1": pulumi.String("value1"),
					"tag2": pulumi.String("value2"),
				},
			},
			CodeName:          pulumi.String("testContainer"),
			RegistryName:      pulumi.String("testregistry"),
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
import com.pulumi.azurenative.machinelearningservices.RegistryCodeContainer;
import com.pulumi.azurenative.machinelearningservices.RegistryCodeContainerArgs;
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
        var registryCodeContainer = new RegistryCodeContainer("registryCodeContainer", RegistryCodeContainerArgs.builder()        
            .codeContainerProperties(Map.ofEntries(
                Map.entry("description", "string"),
                Map.entry("tags", Map.ofEntries(
                    Map.entry("tag1", "value1"),
                    Map.entry("tag2", "value2")
                ))
            ))
            .codeName("testContainer")
            .registryName("testregistry")
            .resourceGroupName("testrg123")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const registryCodeContainer = new azure_native.machinelearningservices.RegistryCodeContainer("registryCodeContainer", {
    codeContainerProperties: {
        description: "string",
        tags: {
            tag1: "value1",
            tag2: "value2",
        },
    },
    codeName: "testContainer",
    registryName: "testregistry",
    resourceGroupName: "testrg123",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

registry_code_container = azure_native.machinelearningservices.RegistryCodeContainer("registryCodeContainer",
    code_container_properties=azure_native.machinelearningservices.CodeContainerArgs(
        description="string",
        tags={
            "tag1": "value1",
            "tag2": "value2",
        },
    ),
    code_name="testContainer",
    registry_name="testregistry",
    resource_group_name="testrg123")

```

```yaml
resources:
  registryCodeContainer:
    type: azure-native:machinelearningservices:RegistryCodeContainer
    properties:
      codeContainerProperties:
        description: string
        tags:
          tag1: value1
          tag2: value2
      codeName: testContainer
      registryName: testregistry
      resourceGroupName: testrg123

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:machinelearningservices:RegistryCodeContainer testContainer /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg123/providers/Microsoft.MachineLearningServices/registries/testregistry/codes/testContainer 
```
