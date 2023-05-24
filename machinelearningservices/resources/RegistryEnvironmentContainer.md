Azure Resource Manager resource envelope.
API Version: 2023-04-01.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateOrUpdate Registry Environment Container.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var registryEnvironmentContainer = new AzureNative.MachineLearningServices.RegistryEnvironmentContainer("registryEnvironmentContainer", new()
    {
        EnvironmentContainerProperties = new AzureNative.MachineLearningServices.Inputs.EnvironmentContainerArgs
        {
            Description = "string",
            Properties = 
            {
                { "additionalProp1", "string" },
                { "additionalProp2", "string" },
                { "additionalProp3", "string" },
            },
            Tags = 
            {
                { "additionalProp1", "string" },
                { "additionalProp2", "string" },
                { "additionalProp3", "string" },
            },
        },
        EnvironmentName = "testEnvironment",
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
		_, err := machinelearningservices.NewRegistryEnvironmentContainer(ctx, "registryEnvironmentContainer", &machinelearningservices.RegistryEnvironmentContainerArgs{
			EnvironmentContainerProperties: &machinelearningservices.EnvironmentContainerTypeArgs{
				Description: pulumi.String("string"),
				Properties: pulumi.StringMap{
					"additionalProp1": pulumi.String("string"),
					"additionalProp2": pulumi.String("string"),
					"additionalProp3": pulumi.String("string"),
				},
				Tags: pulumi.StringMap{
					"additionalProp1": pulumi.String("string"),
					"additionalProp2": pulumi.String("string"),
					"additionalProp3": pulumi.String("string"),
				},
			},
			EnvironmentName:   pulumi.String("testEnvironment"),
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
import com.pulumi.azurenative.machinelearningservices.RegistryEnvironmentContainer;
import com.pulumi.azurenative.machinelearningservices.RegistryEnvironmentContainerArgs;
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
        var registryEnvironmentContainer = new RegistryEnvironmentContainer("registryEnvironmentContainer", RegistryEnvironmentContainerArgs.builder()        
            .environmentContainerProperties(Map.ofEntries(
                Map.entry("description", "string"),
                Map.entry("properties", Map.ofEntries(
                    Map.entry("additionalProp1", "string"),
                    Map.entry("additionalProp2", "string"),
                    Map.entry("additionalProp3", "string")
                )),
                Map.entry("tags", Map.ofEntries(
                    Map.entry("additionalProp1", "string"),
                    Map.entry("additionalProp2", "string"),
                    Map.entry("additionalProp3", "string")
                ))
            ))
            .environmentName("testEnvironment")
            .registryName("testregistry")
            .resourceGroupName("testrg123")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const registryEnvironmentContainer = new azure_native.machinelearningservices.RegistryEnvironmentContainer("registryEnvironmentContainer", {
    environmentContainerProperties: {
        description: "string",
        properties: {
            additionalProp1: "string",
            additionalProp2: "string",
            additionalProp3: "string",
        },
        tags: {
            additionalProp1: "string",
            additionalProp2: "string",
            additionalProp3: "string",
        },
    },
    environmentName: "testEnvironment",
    registryName: "testregistry",
    resourceGroupName: "testrg123",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

registry_environment_container = azure_native.machinelearningservices.RegistryEnvironmentContainer("registryEnvironmentContainer",
    environment_container_properties=azure_native.machinelearningservices.EnvironmentContainerArgs(
        description="string",
        properties={
            "additionalProp1": "string",
            "additionalProp2": "string",
            "additionalProp3": "string",
        },
        tags={
            "additionalProp1": "string",
            "additionalProp2": "string",
            "additionalProp3": "string",
        },
    ),
    environment_name="testEnvironment",
    registry_name="testregistry",
    resource_group_name="testrg123")

```

```yaml
resources:
  registryEnvironmentContainer:
    type: azure-native:machinelearningservices:RegistryEnvironmentContainer
    properties:
      environmentContainerProperties:
        description: string
        properties:
          additionalProp1: string
          additionalProp2: string
          additionalProp3: string
        tags:
          additionalProp1: string
          additionalProp2: string
          additionalProp3: string
      environmentName: testEnvironment
      registryName: testregistry
      resourceGroupName: testrg123

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:machinelearningservices:RegistryEnvironmentContainer testEnvironment /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg123/providers/Microsoft.MachineLearningServices/registries/testregistry/environments/testEnvironment 
```
