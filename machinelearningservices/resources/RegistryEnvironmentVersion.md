Azure Resource Manager resource envelope.
API Version: 2023-04-01.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateOrUpdate Registry Environment Version.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var registryEnvironmentVersion = new AzureNative.MachineLearningServices.RegistryEnvironmentVersion("registryEnvironmentVersion", new()
    {
        EnvironmentName = "string",
        EnvironmentVersionProperties = new AzureNative.MachineLearningServices.Inputs.EnvironmentVersionArgs
        {
            Build = new AzureNative.MachineLearningServices.Inputs.BuildContextArgs
            {
                ContextUri = "https://storage-account.blob.core.windows.net/azureml/DockerBuildContext/95ddede6b9b8c4e90472db3acd0a8d28/",
                DockerfilePath = "prod/Dockerfile",
            },
            CondaFile = "string",
            Description = "string",
            Image = "docker.io/tensorflow/serving:latest",
            InferenceConfig = new AzureNative.MachineLearningServices.Inputs.InferenceContainerPropertiesArgs
            {
                LivenessRoute = new AzureNative.MachineLearningServices.Inputs.RouteArgs
                {
                    Path = "string",
                    Port = 1,
                },
                ReadinessRoute = new AzureNative.MachineLearningServices.Inputs.RouteArgs
                {
                    Path = "string",
                    Port = 1,
                },
                ScoringRoute = new AzureNative.MachineLearningServices.Inputs.RouteArgs
                {
                    Path = "string",
                    Port = 1,
                },
            },
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
import com.pulumi.azurenative.machinelearningservices.RegistryEnvironmentVersion;
import com.pulumi.azurenative.machinelearningservices.RegistryEnvironmentVersionArgs;
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
        var registryEnvironmentVersion = new RegistryEnvironmentVersion("registryEnvironmentVersion", RegistryEnvironmentVersionArgs.builder()        
            .environmentName("string")
            .environmentVersionProperties(Map.ofEntries(
                Map.entry("build", Map.ofEntries(
                    Map.entry("contextUri", "https://storage-account.blob.core.windows.net/azureml/DockerBuildContext/95ddede6b9b8c4e90472db3acd0a8d28/"),
                    Map.entry("dockerfilePath", "prod/Dockerfile")
                )),
                Map.entry("condaFile", "string"),
                Map.entry("description", "string"),
                Map.entry("image", "docker.io/tensorflow/serving:latest"),
                Map.entry("inferenceConfig", Map.ofEntries(
                    Map.entry("livenessRoute", Map.ofEntries(
                        Map.entry("path", "string"),
                        Map.entry("port", 1)
                    )),
                    Map.entry("readinessRoute", Map.ofEntries(
                        Map.entry("path", "string"),
                        Map.entry("port", 1)
                    )),
                    Map.entry("scoringRoute", Map.ofEntries(
                        Map.entry("path", "string"),
                        Map.entry("port", 1)
                    ))
                )),
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

const registryEnvironmentVersion = new azure_native.machinelearningservices.RegistryEnvironmentVersion("registryEnvironmentVersion", {
    environmentName: "string",
    environmentVersionProperties: {
        build: {
            contextUri: "https://storage-account.blob.core.windows.net/azureml/DockerBuildContext/95ddede6b9b8c4e90472db3acd0a8d28/",
            dockerfilePath: "prod/Dockerfile",
        },
        condaFile: "string",
        description: "string",
        image: "docker.io/tensorflow/serving:latest",
        inferenceConfig: {
            livenessRoute: {
                path: "string",
                port: 1,
            },
            readinessRoute: {
                path: "string",
                port: 1,
            },
            scoringRoute: {
                path: "string",
                port: 1,
            },
        },
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

registry_environment_version = azure_native.machinelearningservices.RegistryEnvironmentVersion("registryEnvironmentVersion",
    environment_name="string",
    environment_version_properties=azure_native.machinelearningservices.EnvironmentVersionResponseArgs(
        build=azure_native.machinelearningservices.BuildContextArgs(
            context_uri="https://storage-account.blob.core.windows.net/azureml/DockerBuildContext/95ddede6b9b8c4e90472db3acd0a8d28/",
            dockerfile_path="prod/Dockerfile",
        ),
        conda_file="string",
        description="string",
        image="docker.io/tensorflow/serving:latest",
        inference_config={
            "livenessRoute": azure_native.machinelearningservices.RouteArgs(
                path="string",
                port=1,
            ),
            "readinessRoute": azure_native.machinelearningservices.RouteArgs(
                path="string",
                port=1,
            ),
            "scoringRoute": azure_native.machinelearningservices.RouteArgs(
                path="string",
                port=1,
            ),
        },
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
  registryEnvironmentVersion:
    type: azure-native:machinelearningservices:RegistryEnvironmentVersion
    properties:
      environmentName: string
      environmentVersionProperties:
        build:
          contextUri: https://storage-account.blob.core.windows.net/azureml/DockerBuildContext/95ddede6b9b8c4e90472db3acd0a8d28/
          dockerfilePath: prod/Dockerfile
        condaFile: string
        description: string
        image: docker.io/tensorflow/serving:latest
        inferenceConfig:
          livenessRoute:
            path: string
            port: 1
          readinessRoute:
            path: string
            port: 1
          scoringRoute:
            path: string
            port: 1
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
$ pulumi import azure-native:machinelearningservices:RegistryEnvironmentVersion string string 
```
