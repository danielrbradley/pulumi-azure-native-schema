Azure Resource Manager resource envelope.
API Version: 2022-10-01.
Previous API Version: 2022-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateOrUpdate Component Version.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var componentVersion = new AzureNative.MachineLearningServices.ComponentVersion("componentVersion", new()
    {
        ComponentVersionProperties = new AzureNative.MachineLearningServices.Inputs.ComponentVersionArgs
        {
            ComponentSpec = 
            {
                { "8ced901b-d826-477d-bfef-329da9672513", null },
            },
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

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.machinelearningservices.ComponentVersion;
import com.pulumi.azurenative.machinelearningservices.ComponentVersionArgs;
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
        var componentVersion = new ComponentVersion("componentVersion", ComponentVersionArgs.builder()        
            .componentVersionProperties(Map.ofEntries(
                Map.entry("componentSpec", Map.of("8ced901b-d826-477d-bfef-329da9672513", null)),
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

const componentVersion = new azure_native.machinelearningservices.ComponentVersion("componentVersion", {
    componentVersionProperties: {
        componentSpec: {
            "8ced901b-d826-477d-bfef-329da9672513": undefined,
        },
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

component_version = azure_native.machinelearningservices.ComponentVersion("componentVersion",
    component_version_properties=azure_native.machinelearningservices.ComponentVersionArgs(
        component_spec={
            "8ced901b-d826-477d-bfef-329da9672513": None,
        },
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
  componentVersion:
    type: azure-native:machinelearningservices:ComponentVersion
    properties:
      componentVersionProperties:
        componentSpec:
          8ced901b-d826-477d-bfef-329da9672513: null
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
$ pulumi import azure-native:machinelearningservices:ComponentVersion string string 
```
