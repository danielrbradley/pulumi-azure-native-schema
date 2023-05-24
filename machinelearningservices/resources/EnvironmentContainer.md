Azure Resource Manager resource envelope.
API Version: 2022-10-01.
Previous API Version: 2021-03-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateOrUpdate Environment Container.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var environmentContainer = new AzureNative.MachineLearningServices.EnvironmentContainer("environmentContainer", new()
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
        Name = "testEnvironment",
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
		_, err := machinelearningservices.NewEnvironmentContainer(ctx, "environmentContainer", &machinelearningservices.EnvironmentContainerArgs{
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
			Name:              pulumi.String("testEnvironment"),
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
import com.pulumi.azurenative.machinelearningservices.EnvironmentContainer;
import com.pulumi.azurenative.machinelearningservices.EnvironmentContainerArgs;
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
        var environmentContainer = new EnvironmentContainer("environmentContainer", EnvironmentContainerArgs.builder()        
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
            .name("testEnvironment")
            .resourceGroupName("testrg123")
            .workspaceName("testworkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const environmentContainer = new azure_native.machinelearningservices.EnvironmentContainer("environmentContainer", {
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
    name: "testEnvironment",
    resourceGroupName: "testrg123",
    workspaceName: "testworkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

environment_container = azure_native.machinelearningservices.EnvironmentContainer("environmentContainer",
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
    name="testEnvironment",
    resource_group_name="testrg123",
    workspace_name="testworkspace")

```

```yaml
resources:
  environmentContainer:
    type: azure-native:machinelearningservices:EnvironmentContainer
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
      name: testEnvironment
      resourceGroupName: testrg123
      workspaceName: testworkspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:machinelearningservices:EnvironmentContainer testEnvironment /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg123/providers/Microsoft.MachineLearningServices/workspaces/testworkspace/environments/testEnvironment 
```
