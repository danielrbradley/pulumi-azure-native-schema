Container App.
API Version: 2022-09-01.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or Update Container App
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var containerApp = new AzureNative.Web.ContainerApp("containerApp", new()
    {
        Configuration = new AzureNative.Web.Inputs.ConfigurationArgs
        {
            Ingress = new AzureNative.Web.Inputs.IngressArgs
            {
                External = true,
                TargetPort = 3000,
            },
        },
        Kind = "containerApp",
        KubeEnvironmentId = "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/rg/providers/Microsoft.Web/kubeEnvironments/demokube",
        Location = "East US",
        Name = "testcontainerApp0",
        ResourceGroupName = "rg",
        Template = new AzureNative.Web.Inputs.TemplateArgs
        {
            Containers = new[]
            {
                new AzureNative.Web.Inputs.ContainerArgs
                {
                    Image = "repo/testcontainerApp0:v1",
                    Name = "testcontainerApp0",
                },
            },
            Dapr = new AzureNative.Web.Inputs.DaprArgs
            {
                AppPort = 3000,
                Enabled = true,
            },
            Scale = new AzureNative.Web.Inputs.ScaleArgs
            {
                MaxReplicas = 5,
                MinReplicas = 1,
                Rules = new[]
                {
                    new AzureNative.Web.Inputs.ScaleRuleArgs
                    {
                        Custom = new AzureNative.Web.Inputs.CustomScaleRuleArgs
                        {
                            Metadata = 
                            {
                                { "concurrentRequests", "50" },
                            },
                            Type = "http",
                        },
                        Name = "httpscalingrule",
                    },
                },
            },
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.web.ContainerApp;
import com.pulumi.azurenative.web.ContainerAppArgs;
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
        var containerApp = new ContainerApp("containerApp", ContainerAppArgs.builder()        
            .configuration(Map.of("ingress", Map.ofEntries(
                Map.entry("external", true),
                Map.entry("targetPort", 3000)
            )))
            .kind("containerApp")
            .kubeEnvironmentId("/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/rg/providers/Microsoft.Web/kubeEnvironments/demokube")
            .location("East US")
            .name("testcontainerApp0")
            .resourceGroupName("rg")
            .template(Map.ofEntries(
                Map.entry("containers", Map.ofEntries(
                    Map.entry("image", "repo/testcontainerApp0:v1"),
                    Map.entry("name", "testcontainerApp0")
                )),
                Map.entry("dapr", Map.ofEntries(
                    Map.entry("appPort", 3000),
                    Map.entry("enabled", true)
                )),
                Map.entry("scale", Map.ofEntries(
                    Map.entry("maxReplicas", 5),
                    Map.entry("minReplicas", 1),
                    Map.entry("rules", Map.ofEntries(
                        Map.entry("custom", Map.ofEntries(
                            Map.entry("metadata", Map.of("concurrentRequests", "50")),
                            Map.entry("type", "http")
                        )),
                        Map.entry("name", "httpscalingrule")
                    ))
                ))
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const containerApp = new azure_native.web.ContainerApp("containerApp", {
    configuration: {
        ingress: {
            external: true,
            targetPort: 3000,
        },
    },
    kind: "containerApp",
    kubeEnvironmentId: "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/rg/providers/Microsoft.Web/kubeEnvironments/demokube",
    location: "East US",
    name: "testcontainerApp0",
    resourceGroupName: "rg",
    template: {
        containers: [{
            image: "repo/testcontainerApp0:v1",
            name: "testcontainerApp0",
        }],
        dapr: {
            appPort: 3000,
            enabled: true,
        },
        scale: {
            maxReplicas: 5,
            minReplicas: 1,
            rules: [{
                custom: {
                    metadata: {
                        concurrentRequests: "50",
                    },
                    type: "http",
                },
                name: "httpscalingrule",
            }],
        },
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

container_app = azure_native.web.ContainerApp("containerApp",
    configuration=azure_native.web.ConfigurationResponseArgs(
        ingress=azure_native.web.IngressArgs(
            external=True,
            target_port=3000,
        ),
    ),
    kind="containerApp",
    kube_environment_id="/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/rg/providers/Microsoft.Web/kubeEnvironments/demokube",
    location="East US",
    name="testcontainerApp0",
    resource_group_name="rg",
    template=azure_native.web.TemplateResponseArgs(
        containers=[azure_native.web.ContainerArgs(
            image="repo/testcontainerApp0:v1",
            name="testcontainerApp0",
        )],
        dapr=azure_native.web.DaprArgs(
            app_port=3000,
            enabled=True,
        ),
        scale={
            "maxReplicas": 5,
            "minReplicas": 1,
            "rules": [{
                "custom": azure_native.web.CustomScaleRuleArgs(
                    metadata={
                        "concurrentRequests": "50",
                    },
                    type="http",
                ),
                "name": "httpscalingrule",
            }],
        },
    ))

```

```yaml
resources:
  containerApp:
    type: azure-native:web:ContainerApp
    properties:
      configuration:
        ingress:
          external: true
          targetPort: 3000
      kind: containerApp
      kubeEnvironmentId: /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/rg/providers/Microsoft.Web/kubeEnvironments/demokube
      location: East US
      name: testcontainerApp0
      resourceGroupName: rg
      template:
        containers:
          - image: repo/testcontainerApp0:v1
            name: testcontainerApp0
        dapr:
          appPort: 3000
          enabled: true
        scale:
          maxReplicas: 5
          minReplicas: 1
          rules:
            - custom:
                metadata:
                  concurrentRequests: '50'
                type: http
              name: httpscalingrule

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:web:ContainerApp testcontainerApp0 /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/rg/providers/Microsoft.Web/containerApps/testcontainerApp0 
```
