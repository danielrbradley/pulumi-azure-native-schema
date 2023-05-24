Azure Resource Manager resource envelope.
API Version: 2022-10-01.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateOrUpdate Environment Version.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var environmentVersion = new AzureNative.MachineLearningServices.EnvironmentVersion("environmentVersion", new()
    {
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
import com.pulumi.azurenative.machinelearningservices.EnvironmentVersion;
import com.pulumi.azurenative.machinelearningservices.EnvironmentVersionArgs;
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
        var environmentVersion = new EnvironmentVersion("environmentVersion", EnvironmentVersionArgs.builder()        
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

const environmentVersion = new azure_native.machinelearningservices.EnvironmentVersion("environmentVersion", {
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
    name: "string",
    resourceGroupName: "test-rg",
    version: "string",
    workspaceName: "my-aml-workspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

environment_version = azure_native.machinelearningservices.EnvironmentVersion("environmentVersion",
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
    name="string",
    resource_group_name="test-rg",
    version="string",
    workspace_name="my-aml-workspace")

```

```yaml
resources:
  environmentVersion:
    type: azure-native:machinelearningservices:EnvironmentVersion
    properties:
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
$ pulumi import azure-native:machinelearningservices:EnvironmentVersion string string 
```
