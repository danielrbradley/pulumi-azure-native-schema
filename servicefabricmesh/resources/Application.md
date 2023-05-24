This type describes an application resource.
API Version: 2018-09-01-preview.
Previous API Version: 2018-09-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateOrUpdateApplication
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var application = new AzureNative.ServiceFabricMesh.Application("application", new()
    {
        ApplicationResourceName = "sampleApplication",
        Description = "Service Fabric Mesh sample application.",
        Location = "EastUS",
        ResourceGroupName = "sbz_demo",
        Services = new[]
        {
            new AzureNative.ServiceFabricMesh.Inputs.ServiceResourceDescriptionArgs
            {
                CodePackages = new[]
                {
                    new AzureNative.ServiceFabricMesh.Inputs.ContainerCodePackagePropertiesArgs
                    {
                        Endpoints = new[]
                        {
                            new AzureNative.ServiceFabricMesh.Inputs.EndpointPropertiesArgs
                            {
                                Name = "helloWorldListener",
                                Port = 80,
                            },
                        },
                        Image = "seabreeze/sbz-helloworld:1.0-alpine",
                        Name = "helloWorldCode",
                        Resources = new AzureNative.ServiceFabricMesh.Inputs.ResourceRequirementsArgs
                        {
                            Requests = new AzureNative.ServiceFabricMesh.Inputs.ResourceRequestsArgs
                            {
                                Cpu = 1,
                                MemoryInGB = 1,
                            },
                        },
                    },
                },
                Description = "SeaBreeze Hello World Service.",
                Name = "helloWorldService",
                NetworkRefs = new[]
                {
                    new AzureNative.ServiceFabricMesh.Inputs.NetworkRefArgs
                    {
                        EndpointRefs = new[]
                        {
                            new AzureNative.ServiceFabricMesh.Inputs.EndpointRefArgs
                            {
                                Name = "helloWorldListener",
                            },
                        },
                        Name = "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/sbz_demo/providers/Microsoft.ServiceFabricMesh/networks/sampleNetwork",
                    },
                },
                OsType = "Linux",
                ReplicaCount = 1,
            },
        },
        Tags = null,
    });

});


```

```go
package main

import (
	servicefabricmesh "github.com/pulumi/pulumi-azure-native-sdk/servicefabricmesh"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := servicefabricmesh.NewApplication(ctx, "application", &servicefabricmesh.ApplicationArgs{
			ApplicationResourceName: pulumi.String("sampleApplication"),
			Description:             pulumi.String("Service Fabric Mesh sample application."),
			Location:                pulumi.String("EastUS"),
			ResourceGroupName:       pulumi.String("sbz_demo"),
			Services: []servicefabricmesh.ServiceResourceDescriptionArgs{
				{
					CodePackages: []servicefabricmesh.ContainerCodePackagePropertiesArgs{
						{
							Endpoints: servicefabricmesh.EndpointPropertiesArray{
								{
									Name: pulumi.String("helloWorldListener"),
									Port: pulumi.Int(80),
								},
							},
							Image: pulumi.String("seabreeze/sbz-helloworld:1.0-alpine"),
							Name:  pulumi.String("helloWorldCode"),
							Resources: {
								Requests: {
									Cpu:        pulumi.Float64(1),
									MemoryInGB: pulumi.Float64(1),
								},
							},
						},
					},
					Description: pulumi.String("SeaBreeze Hello World Service."),
					Name:        pulumi.String("helloWorldService"),
					NetworkRefs: servicefabricmesh.NetworkRefArray{
						{
							EndpointRefs: servicefabricmesh.EndpointRefArray{
								{
									Name: pulumi.String("helloWorldListener"),
								},
							},
							Name: pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/sbz_demo/providers/Microsoft.ServiceFabricMesh/networks/sampleNetwork"),
						},
					},
					OsType:       pulumi.String("Linux"),
					ReplicaCount: pulumi.Int(1),
				},
			},
			Tags: nil,
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
import com.pulumi.azurenative.servicefabricmesh.Application;
import com.pulumi.azurenative.servicefabricmesh.ApplicationArgs;
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
        var application = new Application("application", ApplicationArgs.builder()        
            .applicationResourceName("sampleApplication")
            .description("Service Fabric Mesh sample application.")
            .location("EastUS")
            .resourceGroupName("sbz_demo")
            .services(Map.ofEntries(
                Map.entry("codePackages", Map.ofEntries(
                    Map.entry("endpoints", Map.ofEntries(
                        Map.entry("name", "helloWorldListener"),
                        Map.entry("port", 80)
                    )),
                    Map.entry("image", "seabreeze/sbz-helloworld:1.0-alpine"),
                    Map.entry("name", "helloWorldCode"),
                    Map.entry("resources", Map.of("requests", Map.ofEntries(
                        Map.entry("cpu", 1),
                        Map.entry("memoryInGB", 1)
                    )))
                )),
                Map.entry("description", "SeaBreeze Hello World Service."),
                Map.entry("name", "helloWorldService"),
                Map.entry("networkRefs", Map.ofEntries(
                    Map.entry("endpointRefs", Map.of("name", "helloWorldListener")),
                    Map.entry("name", "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/sbz_demo/providers/Microsoft.ServiceFabricMesh/networks/sampleNetwork")
                )),
                Map.entry("osType", "Linux"),
                Map.entry("replicaCount", 1)
            ))
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const application = new azure_native.servicefabricmesh.Application("application", {
    applicationResourceName: "sampleApplication",
    description: "Service Fabric Mesh sample application.",
    location: "EastUS",
    resourceGroupName: "sbz_demo",
    services: [{
        codePackages: [{
            endpoints: [{
                name: "helloWorldListener",
                port: 80,
            }],
            image: "seabreeze/sbz-helloworld:1.0-alpine",
            name: "helloWorldCode",
            resources: {
                requests: {
                    cpu: 1,
                    memoryInGB: 1,
                },
            },
        }],
        description: "SeaBreeze Hello World Service.",
        name: "helloWorldService",
        networkRefs: [{
            endpointRefs: [{
                name: "helloWorldListener",
            }],
            name: "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/sbz_demo/providers/Microsoft.ServiceFabricMesh/networks/sampleNetwork",
        }],
        osType: "Linux",
        replicaCount: 1,
    }],
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

application = azure_native.servicefabricmesh.Application("application",
    application_resource_name="sampleApplication",
    description="Service Fabric Mesh sample application.",
    location="EastUS",
    resource_group_name="sbz_demo",
    services=[{
        "codePackages": [{
            "endpoints": [azure_native.servicefabricmesh.EndpointPropertiesArgs(
                name="helloWorldListener",
                port=80,
            )],
            "image": "seabreeze/sbz-helloworld:1.0-alpine",
            "name": "helloWorldCode",
            "resources": {
                "requests": azure_native.servicefabricmesh.ResourceRequestsArgs(
                    cpu=1,
                    memory_in_gb=1,
                ),
            },
        }],
        "description": "SeaBreeze Hello World Service.",
        "name": "helloWorldService",
        "networkRefs": [{
            "endpointRefs": [azure_native.servicefabricmesh.EndpointRefArgs(
                name="helloWorldListener",
            )],
            "name": "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/sbz_demo/providers/Microsoft.ServiceFabricMesh/networks/sampleNetwork",
        }],
        "osType": "Linux",
        "replicaCount": 1,
    }],
    tags={})

```

```yaml
resources:
  application:
    type: azure-native:servicefabricmesh:Application
    properties:
      applicationResourceName: sampleApplication
      description: Service Fabric Mesh sample application.
      location: EastUS
      resourceGroupName: sbz_demo
      services:
        - codePackages:
            - endpoints:
                - name: helloWorldListener
                  port: 80
              image: seabreeze/sbz-helloworld:1.0-alpine
              name: helloWorldCode
              resources:
                requests:
                  cpu: 1
                  memoryInGB: 1
          description: SeaBreeze Hello World Service.
          name: helloWorldService
          networkRefs:
            - endpointRefs:
                - name: helloWorldListener
              name: /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/sbz_demo/providers/Microsoft.ServiceFabricMesh/networks/sampleNetwork
          osType: Linux
          replicaCount: 1
      tags: {}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:servicefabricmesh:Application sampleApplication /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/sbz_demo/providers/Microsoft.ServiceFabricMesh/applications/sampleApplication 
```
