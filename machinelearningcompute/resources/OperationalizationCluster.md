Instance of an Azure ML Operationalization Cluster resource.
API Version: 2017-08-01-preview.
Previous API Version: 2017-08-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PUT Operationalization Cluster
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var operationalizationCluster = new AzureNative.MachineLearningCompute.OperationalizationCluster("operationalizationCluster", new()
    {
        ClusterName = "myCluster",
        ClusterType = "ACS",
        ContainerService = new AzureNative.MachineLearningCompute.Inputs.AcsClusterPropertiesArgs
        {
            OrchestratorProperties = new AzureNative.MachineLearningCompute.Inputs.KubernetesClusterPropertiesArgs
            {
                ServicePrincipal = new AzureNative.MachineLearningCompute.Inputs.ServicePrincipalPropertiesArgs
                {
                    ClientId = "abcdefghijklmnopqrt",
                    Secret = "<secret>",
                },
            },
            OrchestratorType = "Kubernetes",
        },
        Description = "My Operationalization Cluster",
        GlobalServiceConfiguration = new AzureNative.MachineLearningCompute.Inputs.GlobalServiceConfigurationArgs
        {
            Ssl = new AzureNative.MachineLearningCompute.Inputs.SslConfigurationArgs
            {
                Cert = "afjdklq2131casfakld=",
                Cname = "foo.bar.com",
                Key = "flksdafkldsajf=",
                Status = "Enabled",
            },
        },
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
        Tags = 
        {
            { "key1", "alpha" },
            { "key2", "beta" },
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.machinelearningcompute.OperationalizationCluster;
import com.pulumi.azurenative.machinelearningcompute.OperationalizationClusterArgs;
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
        var operationalizationCluster = new OperationalizationCluster("operationalizationCluster", OperationalizationClusterArgs.builder()        
            .clusterName("myCluster")
            .clusterType("ACS")
            .containerService(Map.ofEntries(
                Map.entry("orchestratorProperties", Map.of("servicePrincipal", Map.ofEntries(
                    Map.entry("clientId", "abcdefghijklmnopqrt"),
                    Map.entry("secret", "<secret>")
                ))),
                Map.entry("orchestratorType", "Kubernetes")
            ))
            .description("My Operationalization Cluster")
            .globalServiceConfiguration(Map.of("ssl", Map.ofEntries(
                Map.entry("cert", "afjdklq2131casfakld="),
                Map.entry("cname", "foo.bar.com"),
                Map.entry("key", "flksdafkldsajf="),
                Map.entry("status", "Enabled")
            )))
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .tags(Map.ofEntries(
                Map.entry("key1", "alpha"),
                Map.entry("key2", "beta")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const operationalizationCluster = new azure_native.machinelearningcompute.OperationalizationCluster("operationalizationCluster", {
    clusterName: "myCluster",
    clusterType: "ACS",
    containerService: {
        orchestratorProperties: {
            servicePrincipal: {
                clientId: "abcdefghijklmnopqrt",
                secret: "<secret>",
            },
        },
        orchestratorType: "Kubernetes",
    },
    description: "My Operationalization Cluster",
    globalServiceConfiguration: {
        ssl: {
            cert: "afjdklq2131casfakld=",
            cname: "foo.bar.com",
            key: "flksdafkldsajf=",
            status: "Enabled",
        },
    },
    location: "West US",
    resourceGroupName: "myResourceGroup",
    tags: {
        key1: "alpha",
        key2: "beta",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

operationalization_cluster = azure_native.machinelearningcompute.OperationalizationCluster("operationalizationCluster",
    cluster_name="myCluster",
    cluster_type="ACS",
    container_service=azure_native.machinelearningcompute.AcsClusterPropertiesResponseArgs(
        orchestrator_properties={
            "servicePrincipal": azure_native.machinelearningcompute.ServicePrincipalPropertiesArgs(
                client_id="abcdefghijklmnopqrt",
                secret="<secret>",
            ),
        },
        orchestrator_type="Kubernetes",
    ),
    description="My Operationalization Cluster",
    global_service_configuration=azure_native.machinelearningcompute.GlobalServiceConfigurationResponseArgs(
        ssl=azure_native.machinelearningcompute.SslConfigurationArgs(
            cert="afjdklq2131casfakld=",
            cname="foo.bar.com",
            key="flksdafkldsajf=",
            status="Enabled",
        ),
    ),
    location="West US",
    resource_group_name="myResourceGroup",
    tags={
        "key1": "alpha",
        "key2": "beta",
    })

```

```yaml
resources:
  operationalizationCluster:
    type: azure-native:machinelearningcompute:OperationalizationCluster
    properties:
      clusterName: myCluster
      clusterType: ACS
      containerService:
        orchestratorProperties:
          servicePrincipal:
            clientId: abcdefghijklmnopqrt
            secret: <secret>
        orchestratorType: Kubernetes
      description: My Operationalization Cluster
      globalServiceConfiguration:
        ssl:
          cert: afjdklq2131casfakld=
          cname: foo.bar.com
          key: flksdafkldsajf=
          status: Enabled
      location: West US
      resourceGroupName: myResourceGroup
      tags:
        key1: alpha
        key2: beta

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:machinelearningcompute:OperationalizationCluster MyCluster /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.MachineLearningCompute/operationalizationClusters/MyCluster 
```
