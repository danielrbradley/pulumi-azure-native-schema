Azure Resource Manager resource envelope.
API Version: 2022-10-01.
Previous API Version: 2021-03-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateOrUpdate Data Container.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var dataContainer = new AzureNative.MachineLearningServices.DataContainer("dataContainer", new()
    {
        DataContainerProperties = new AzureNative.MachineLearningServices.Inputs.DataContainerArgs
        {
            DataType = "UriFile",
            Description = "string",
            Properties = 
            {
                { "properties1", "value1" },
                { "properties2", "value2" },
            },
            Tags = 
            {
                { "tag1", "value1" },
                { "tag2", "value2" },
            },
        },
        Name = "datacontainer123",
        ResourceGroupName = "testrg123",
        WorkspaceName = "workspace123",
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
		_, err := machinelearningservices.NewDataContainer(ctx, "dataContainer", &machinelearningservices.DataContainerArgs{
			DataContainerProperties: &machinelearningservices.DataContainerTypeArgs{
				DataType:    pulumi.String("UriFile"),
				Description: pulumi.String("string"),
				Properties: pulumi.StringMap{
					"properties1": pulumi.String("value1"),
					"properties2": pulumi.String("value2"),
				},
				Tags: pulumi.StringMap{
					"tag1": pulumi.String("value1"),
					"tag2": pulumi.String("value2"),
				},
			},
			Name:              pulumi.String("datacontainer123"),
			ResourceGroupName: pulumi.String("testrg123"),
			WorkspaceName:     pulumi.String("workspace123"),
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
import com.pulumi.azurenative.machinelearningservices.DataContainer;
import com.pulumi.azurenative.machinelearningservices.DataContainerArgs;
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
        var dataContainer = new DataContainer("dataContainer", DataContainerArgs.builder()        
            .dataContainerProperties(Map.ofEntries(
                Map.entry("dataType", "UriFile"),
                Map.entry("description", "string"),
                Map.entry("properties", Map.ofEntries(
                    Map.entry("properties1", "value1"),
                    Map.entry("properties2", "value2")
                )),
                Map.entry("tags", Map.ofEntries(
                    Map.entry("tag1", "value1"),
                    Map.entry("tag2", "value2")
                ))
            ))
            .name("datacontainer123")
            .resourceGroupName("testrg123")
            .workspaceName("workspace123")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const dataContainer = new azure_native.machinelearningservices.DataContainer("dataContainer", {
    dataContainerProperties: {
        dataType: "UriFile",
        description: "string",
        properties: {
            properties1: "value1",
            properties2: "value2",
        },
        tags: {
            tag1: "value1",
            tag2: "value2",
        },
    },
    name: "datacontainer123",
    resourceGroupName: "testrg123",
    workspaceName: "workspace123",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

data_container = azure_native.machinelearningservices.DataContainer("dataContainer",
    data_container_properties=azure_native.machinelearningservices.DataContainerArgs(
        data_type="UriFile",
        description="string",
        properties={
            "properties1": "value1",
            "properties2": "value2",
        },
        tags={
            "tag1": "value1",
            "tag2": "value2",
        },
    ),
    name="datacontainer123",
    resource_group_name="testrg123",
    workspace_name="workspace123")

```

```yaml
resources:
  dataContainer:
    type: azure-native:machinelearningservices:DataContainer
    properties:
      dataContainerProperties:
        dataType: UriFile
        description: string
        properties:
          properties1: value1
          properties2: value2
        tags:
          tag1: value1
          tag2: value2
      name: datacontainer123
      resourceGroupName: testrg123
      workspaceName: workspace123

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:machinelearningservices:DataContainer datacontainer123 /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg123/providers/Microsoft.MachineLearningServices/workspaces/workspace123/data/datacontainer123 
```
