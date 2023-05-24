Azure Resource Manager resource envelope.
API Version: 2023-04-01.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateOrUpdate Registry Component Version.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var registryComponentVersion = new AzureNative.MachineLearningServices.RegistryComponentVersion("registryComponentVersion", new()
    {
        ComponentName = "string",
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
        RegistryName = "my-aml-registry",
        ResourceGroupName = "test-rg",
        Version = "string",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.machinelearningservices.RegistryComponentVersion;
import com.pulumi.azurenative.machinelearningservices.RegistryComponentVersionArgs;
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
        var registryComponentVersion = new RegistryComponentVersion("registryComponentVersion", RegistryComponentVersionArgs.builder()        
            .componentName("string")
            .componentVersionProperties(Map.ofEntries(
                Map.entry("componentSpec", Map.of("8ced901b-d826-477d-bfef-329da9672513", null)),
                Map.entry("description", "string"),
                Map.entry("isAnonymous", false),
                Map.entry("properties", Map.of("string", "string")),
                Map.entry("tags", Map.of("string", "string"))
            ))
            .registryName("my-aml-registry")
            .resourceGroupName("test-rg")
            .version("string")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const registryComponentVersion = new azure_native.machinelearningservices.RegistryComponentVersion("registryComponentVersion", {
    componentName: "string",
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
    registryName: "my-aml-registry",
    resourceGroupName: "test-rg",
    version: "string",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

registry_component_version = azure_native.machinelearningservices.RegistryComponentVersion("registryComponentVersion",
    component_name="string",
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
    registry_name="my-aml-registry",
    resource_group_name="test-rg",
    version="string")

```

```yaml
resources:
  registryComponentVersion:
    type: azure-native:machinelearningservices:RegistryComponentVersion
    properties:
      componentName: string
      componentVersionProperties:
        componentSpec:
          8ced901b-d826-477d-bfef-329da9672513: null
        description: string
        isAnonymous: false
        properties:
          string: string
        tags:
          string: string
      registryName: my-aml-registry
      resourceGroupName: test-rg
      version: string

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:machinelearningservices:RegistryComponentVersion string string 
```
