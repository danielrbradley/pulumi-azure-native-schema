KPack Builder resource
API Version: 2022-12-01.
Previous API Version: 2022-01-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### BuildServiceBuilder_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var buildServiceBuilder = new AzureNative.AppPlatform.BuildServiceBuilder("buildServiceBuilder", new()
    {
        BuildServiceName = "default",
        BuilderName = "mybuilder",
        Properties = new AzureNative.AppPlatform.Inputs.BuilderPropertiesArgs
        {
            BuildpackGroups = new[]
            {
                new AzureNative.AppPlatform.Inputs.BuildpacksGroupPropertiesArgs
                {
                    Buildpacks = new[]
                    {
                        new AzureNative.AppPlatform.Inputs.BuildpackPropertiesArgs
                        {
                            Id = "tanzu-buildpacks/java-azure",
                        },
                    },
                    Name = "mix",
                },
            },
            Stack = new AzureNative.AppPlatform.Inputs.StackPropertiesArgs
            {
                Id = "io.buildpacks.stacks.bionic",
                Version = "base",
            },
        },
        ResourceGroupName = "myResourceGroup",
        ServiceName = "myservice",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.appplatform.BuildServiceBuilder;
import com.pulumi.azurenative.appplatform.BuildServiceBuilderArgs;
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
        var buildServiceBuilder = new BuildServiceBuilder("buildServiceBuilder", BuildServiceBuilderArgs.builder()        
            .buildServiceName("default")
            .builderName("mybuilder")
            .properties(Map.ofEntries(
                Map.entry("buildpackGroups", Map.ofEntries(
                    Map.entry("buildpacks", Map.of("id", "tanzu-buildpacks/java-azure")),
                    Map.entry("name", "mix")
                )),
                Map.entry("stack", Map.ofEntries(
                    Map.entry("id", "io.buildpacks.stacks.bionic"),
                    Map.entry("version", "base")
                ))
            ))
            .resourceGroupName("myResourceGroup")
            .serviceName("myservice")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const buildServiceBuilder = new azure_native.appplatform.BuildServiceBuilder("buildServiceBuilder", {
    buildServiceName: "default",
    builderName: "mybuilder",
    properties: {
        buildpackGroups: [{
            buildpacks: [{
                id: "tanzu-buildpacks/java-azure",
            }],
            name: "mix",
        }],
        stack: {
            id: "io.buildpacks.stacks.bionic",
            version: "base",
        },
    },
    resourceGroupName: "myResourceGroup",
    serviceName: "myservice",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

build_service_builder = azure_native.appplatform.BuildServiceBuilder("buildServiceBuilder",
    build_service_name="default",
    builder_name="mybuilder",
    properties=azure_native.appplatform.BuilderPropertiesResponseArgs(
        buildpack_groups=[{
            "buildpacks": [azure_native.appplatform.BuildpackPropertiesArgs(
                id="tanzu-buildpacks/java-azure",
            )],
            "name": "mix",
        }],
        stack=azure_native.appplatform.StackPropertiesArgs(
            id="io.buildpacks.stacks.bionic",
            version="base",
        ),
    ),
    resource_group_name="myResourceGroup",
    service_name="myservice")

```

```yaml
resources:
  buildServiceBuilder:
    type: azure-native:appplatform:BuildServiceBuilder
    properties:
      buildServiceName: default
      builderName: mybuilder
      properties:
        buildpackGroups:
          - buildpacks:
              - id: tanzu-buildpacks/java-azure
            name: mix
        stack:
          id: io.buildpacks.stacks.bionic
          version: base
      resourceGroupName: myResourceGroup
      serviceName: myservice

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:appplatform:BuildServiceBuilder mybuilder /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.AppPlatform/Spring/myservice/buildServices/default/builders/mybuilder 
```
