Azure Resource Manager resource envelope.
API Version: 2023-04-01.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateOrUpdate Registry Data Container.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var registryDataContainer = new AzureNative.MachineLearningServices.RegistryDataContainer("registryDataContainer", new()
    {
        DataContainerProperties = new AzureNative.MachineLearningServices.Inputs.DataContainerArgs
        {
            DataType = "uri_folder",
            Description = "string",
            IsArchived = false,
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
        RegistryName = "registryName",
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
		_, err := machinelearningservices.NewRegistryDataContainer(ctx, "registryDataContainer", &machinelearningservices.RegistryDataContainerArgs{
			DataContainerProperties: &machinelearningservices.DataContainerTypeArgs{
				DataType:    pulumi.String("uri_folder"),
				Description: pulumi.String("string"),
				IsArchived:  pulumi.Bool(false),
				Properties: pulumi.StringMap{
					"string": pulumi.String("string"),
				},
				Tags: pulumi.StringMap{
					"string": pulumi.String("string"),
				},
			},
			Name:              pulumi.String("string"),
			RegistryName:      pulumi.String("registryName"),
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
import com.pulumi.azurenative.machinelearningservices.RegistryDataContainer;
import com.pulumi.azurenative.machinelearningservices.RegistryDataContainerArgs;
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
        var registryDataContainer = new RegistryDataContainer("registryDataContainer", RegistryDataContainerArgs.builder()        
            .dataContainerProperties(Map.ofEntries(
                Map.entry("dataType", "uri_folder"),
                Map.entry("description", "string"),
                Map.entry("isArchived", false),
                Map.entry("properties", Map.of("string", "string")),
                Map.entry("tags", Map.of("string", "string"))
            ))
            .name("string")
            .registryName("registryName")
            .resourceGroupName("test-rg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const registryDataContainer = new azure_native.machinelearningservices.RegistryDataContainer("registryDataContainer", {
    dataContainerProperties: {
        dataType: "uri_folder",
        description: "string",
        isArchived: false,
        properties: {
            string: "string",
        },
        tags: {
            string: "string",
        },
    },
    name: "string",
    registryName: "registryName",
    resourceGroupName: "test-rg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

registry_data_container = azure_native.machinelearningservices.RegistryDataContainer("registryDataContainer",
    data_container_properties=azure_native.machinelearningservices.DataContainerArgs(
        data_type="uri_folder",
        description="string",
        is_archived=False,
        properties={
            "string": "string",
        },
        tags={
            "string": "string",
        },
    ),
    name="string",
    registry_name="registryName",
    resource_group_name="test-rg")

```

```yaml
resources:
  registryDataContainer:
    type: azure-native:machinelearningservices:RegistryDataContainer
    properties:
      dataContainerProperties:
        dataType: uri_folder
        description: string
        isArchived: false
        properties:
          string: string
        tags:
          string: string
      name: string
      registryName: registryName
      resourceGroupName: test-rg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:machinelearningservices:RegistryDataContainer string string 
```
