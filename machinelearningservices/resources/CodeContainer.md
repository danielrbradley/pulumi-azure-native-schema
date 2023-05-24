Azure Resource Manager resource envelope.
API Version: 2022-10-01.
Previous API Version: 2021-03-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateOrUpdate Code Container.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var codeContainer = new AzureNative.MachineLearningServices.CodeContainer("codeContainer", new()
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
        Name = "testContainer",
        ResourceGroupName = "testrg123",
        WorkspaceName = "testworkspace",
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
		_, err := machinelearningservices.NewCodeContainer(ctx, "codeContainer", &machinelearningservices.CodeContainerArgs{
			CodeContainerProperties: &machinelearningservices.CodeContainerTypeArgs{
				Description: pulumi.String("string"),
				Tags: pulumi.StringMap{
					"tag1": pulumi.String("value1"),
					"tag2": pulumi.String("value2"),
				},
			},
			Name:              pulumi.String("testContainer"),
			ResourceGroupName: pulumi.String("testrg123"),
			WorkspaceName:     pulumi.String("testworkspace"),
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
import com.pulumi.azurenative.machinelearningservices.CodeContainer;
import com.pulumi.azurenative.machinelearningservices.CodeContainerArgs;
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
        var codeContainer = new CodeContainer("codeContainer", CodeContainerArgs.builder()        
            .codeContainerProperties(Map.ofEntries(
                Map.entry("description", "string"),
                Map.entry("tags", Map.ofEntries(
                    Map.entry("tag1", "value1"),
                    Map.entry("tag2", "value2")
                ))
            ))
            .name("testContainer")
            .resourceGroupName("testrg123")
            .workspaceName("testworkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const codeContainer = new azure_native.machinelearningservices.CodeContainer("codeContainer", {
    codeContainerProperties: {
        description: "string",
        tags: {
            tag1: "value1",
            tag2: "value2",
        },
    },
    name: "testContainer",
    resourceGroupName: "testrg123",
    workspaceName: "testworkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

code_container = azure_native.machinelearningservices.CodeContainer("codeContainer",
    code_container_properties=azure_native.machinelearningservices.CodeContainerArgs(
        description="string",
        tags={
            "tag1": "value1",
            "tag2": "value2",
        },
    ),
    name="testContainer",
    resource_group_name="testrg123",
    workspace_name="testworkspace")

```

```yaml
resources:
  codeContainer:
    type: azure-native:machinelearningservices:CodeContainer
    properties:
      codeContainerProperties:
        description: string
        tags:
          tag1: value1
          tag2: value2
      name: testContainer
      resourceGroupName: testrg123
      workspaceName: testworkspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:machinelearningservices:CodeContainer testContainer /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg123/providers/Microsoft.MachineLearningServices/workspaces/testworkspace/codes/testContainer 
```
