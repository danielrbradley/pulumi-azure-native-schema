This type describes a gateway resource.
API Version: 2018-09-01-preview.
Previous API Version: 2018-09-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateOrUpdateGateway
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var gateway = new AzureNative.ServiceFabricMesh.Gateway("gateway", new()
    {
        Description = "Service Fabric Mesh sample gateway.",
        DestinationNetwork = new AzureNative.ServiceFabricMesh.Inputs.NetworkRefArgs
        {
            Name = "helloWorldNetwork",
        },
        GatewayResourceName = "sampleGateway",
        Http = new[]
        {
            new AzureNative.ServiceFabricMesh.Inputs.HttpConfigArgs
            {
                Hosts = new[]
                {
                    new AzureNative.ServiceFabricMesh.Inputs.HttpHostConfigArgs
                    {
                        Name = "contoso.com",
                        Routes = new[]
                        {
                            new AzureNative.ServiceFabricMesh.Inputs.HttpRouteConfigArgs
                            {
                                Destination = new AzureNative.ServiceFabricMesh.Inputs.GatewayDestinationArgs
                                {
                                    ApplicationName = "httpHelloWorldApp",
                                    EndpointName = "indexHttpEndpoint",
                                    ServiceName = "indexService",
                                },
                                Match = new AzureNative.ServiceFabricMesh.Inputs.HttpRouteMatchRuleArgs
                                {
                                    Headers = new[]
                                    {
                                        new AzureNative.ServiceFabricMesh.Inputs.HttpRouteMatchHeaderArgs
                                        {
                                            Name = "accept",
                                            Type = "exact",
                                            Value = "application/json",
                                        },
                                    },
                                    Path = new AzureNative.ServiceFabricMesh.Inputs.HttpRouteMatchPathArgs
                                    {
                                        Rewrite = "/",
                                        Type = "prefix",
                                        Value = "/index",
                                    },
                                },
                                Name = "index",
                            },
                        },
                    },
                },
                Name = "contosoWebsite",
                Port = 8081,
            },
        },
        Location = "EastUS",
        ResourceGroupName = "sbz_demo",
        SourceNetwork = new AzureNative.ServiceFabricMesh.Inputs.NetworkRefArgs
        {
            Name = "Open",
        },
        Tags = null,
        Tcp = new[]
        {
            new AzureNative.ServiceFabricMesh.Inputs.TcpConfigArgs
            {
                Destination = new AzureNative.ServiceFabricMesh.Inputs.GatewayDestinationArgs
                {
                    ApplicationName = "helloWorldApp",
                    EndpointName = "helloWorldListener",
                    ServiceName = "helloWorldService",
                },
                Name = "web",
                Port = 80,
            },
        },
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
		_, err := servicefabricmesh.NewGateway(ctx, "gateway", &servicefabricmesh.GatewayArgs{
			Description: pulumi.String("Service Fabric Mesh sample gateway."),
			DestinationNetwork: &servicefabricmesh.NetworkRefArgs{
				Name: pulumi.String("helloWorldNetwork"),
			},
			GatewayResourceName: pulumi.String("sampleGateway"),
			Http: []servicefabricmesh.HttpConfigArgs{
				{
					Hosts: servicefabricmesh.HttpHostConfigArray{
						{
							Name: pulumi.String("contoso.com"),
							Routes: servicefabricmesh.HttpRouteConfigArray{
								{
									Destination: {
										ApplicationName: pulumi.String("httpHelloWorldApp"),
										EndpointName:    pulumi.String("indexHttpEndpoint"),
										ServiceName:     pulumi.String("indexService"),
									},
									Match: {
										Headers: servicefabricmesh.HttpRouteMatchHeaderArray{
											{
												Name:  pulumi.String("accept"),
												Type:  pulumi.String("exact"),
												Value: pulumi.String("application/json"),
											},
										},
										Path: {
											Rewrite: pulumi.String("/"),
											Type:    pulumi.String("prefix"),
											Value:   pulumi.String("/index"),
										},
									},
									Name: pulumi.String("index"),
								},
							},
						},
					},
					Name: pulumi.String("contosoWebsite"),
					Port: pulumi.Int(8081),
				},
			},
			Location:          pulumi.String("EastUS"),
			ResourceGroupName: pulumi.String("sbz_demo"),
			SourceNetwork: &servicefabricmesh.NetworkRefArgs{
				Name: pulumi.String("Open"),
			},
			Tags: nil,
			Tcp: []servicefabricmesh.TcpConfigArgs{
				{
					Destination: {
						ApplicationName: pulumi.String("helloWorldApp"),
						EndpointName:    pulumi.String("helloWorldListener"),
						ServiceName:     pulumi.String("helloWorldService"),
					},
					Name: pulumi.String("web"),
					Port: pulumi.Int(80),
				},
			},
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
import com.pulumi.azurenative.servicefabricmesh.Gateway;
import com.pulumi.azurenative.servicefabricmesh.GatewayArgs;
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
        var gateway = new Gateway("gateway", GatewayArgs.builder()        
            .description("Service Fabric Mesh sample gateway.")
            .destinationNetwork(Map.of("name", "helloWorldNetwork"))
            .gatewayResourceName("sampleGateway")
            .http(Map.ofEntries(
                Map.entry("hosts", Map.ofEntries(
                    Map.entry("name", "contoso.com"),
                    Map.entry("routes", Map.ofEntries(
                        Map.entry("destination", Map.ofEntries(
                            Map.entry("applicationName", "httpHelloWorldApp"),
                            Map.entry("endpointName", "indexHttpEndpoint"),
                            Map.entry("serviceName", "indexService")
                        )),
                        Map.entry("match", Map.ofEntries(
                            Map.entry("headers", Map.ofEntries(
                                Map.entry("name", "accept"),
                                Map.entry("type", "exact"),
                                Map.entry("value", "application/json")
                            )),
                            Map.entry("path", Map.ofEntries(
                                Map.entry("rewrite", "/"),
                                Map.entry("type", "prefix"),
                                Map.entry("value", "/index")
                            ))
                        )),
                        Map.entry("name", "index")
                    ))
                )),
                Map.entry("name", "contosoWebsite"),
                Map.entry("port", 8081)
            ))
            .location("EastUS")
            .resourceGroupName("sbz_demo")
            .sourceNetwork(Map.of("name", "Open"))
            .tags()
            .tcp(Map.ofEntries(
                Map.entry("destination", Map.ofEntries(
                    Map.entry("applicationName", "helloWorldApp"),
                    Map.entry("endpointName", "helloWorldListener"),
                    Map.entry("serviceName", "helloWorldService")
                )),
                Map.entry("name", "web"),
                Map.entry("port", 80)
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const gateway = new azure_native.servicefabricmesh.Gateway("gateway", {
    description: "Service Fabric Mesh sample gateway.",
    destinationNetwork: {
        name: "helloWorldNetwork",
    },
    gatewayResourceName: "sampleGateway",
    http: [{
        hosts: [{
            name: "contoso.com",
            routes: [{
                destination: {
                    applicationName: "httpHelloWorldApp",
                    endpointName: "indexHttpEndpoint",
                    serviceName: "indexService",
                },
                match: {
                    headers: [{
                        name: "accept",
                        type: "exact",
                        value: "application/json",
                    }],
                    path: {
                        rewrite: "/",
                        type: "prefix",
                        value: "/index",
                    },
                },
                name: "index",
            }],
        }],
        name: "contosoWebsite",
        port: 8081,
    }],
    location: "EastUS",
    resourceGroupName: "sbz_demo",
    sourceNetwork: {
        name: "Open",
    },
    tags: {},
    tcp: [{
        destination: {
            applicationName: "helloWorldApp",
            endpointName: "helloWorldListener",
            serviceName: "helloWorldService",
        },
        name: "web",
        port: 80,
    }],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

gateway = azure_native.servicefabricmesh.Gateway("gateway",
    description="Service Fabric Mesh sample gateway.",
    destination_network=azure_native.servicefabricmesh.NetworkRefArgs(
        name="helloWorldNetwork",
    ),
    gateway_resource_name="sampleGateway",
    http=[{
        "hosts": [{
            "name": "contoso.com",
            "routes": [{
                "destination": azure_native.servicefabricmesh.GatewayDestinationArgs(
                    application_name="httpHelloWorldApp",
                    endpoint_name="indexHttpEndpoint",
                    service_name="indexService",
                ),
                "match": {
                    "headers": [azure_native.servicefabricmesh.HttpRouteMatchHeaderArgs(
                        name="accept",
                        type="exact",
                        value="application/json",
                    )],
                    "path": azure_native.servicefabricmesh.HttpRouteMatchPathArgs(
                        rewrite="/",
                        type="prefix",
                        value="/index",
                    ),
                },
                "name": "index",
            }],
        }],
        "name": "contosoWebsite",
        "port": 8081,
    }],
    location="EastUS",
    resource_group_name="sbz_demo",
    source_network=azure_native.servicefabricmesh.NetworkRefArgs(
        name="Open",
    ),
    tags={},
    tcp=[{
        "destination": azure_native.servicefabricmesh.GatewayDestinationArgs(
            application_name="helloWorldApp",
            endpoint_name="helloWorldListener",
            service_name="helloWorldService",
        ),
        "name": "web",
        "port": 80,
    }])

```

```yaml
resources:
  gateway:
    type: azure-native:servicefabricmesh:Gateway
    properties:
      description: Service Fabric Mesh sample gateway.
      destinationNetwork:
        name: helloWorldNetwork
      gatewayResourceName: sampleGateway
      http:
        - hosts:
            - name: contoso.com
              routes:
                - destination:
                    applicationName: httpHelloWorldApp
                    endpointName: indexHttpEndpoint
                    serviceName: indexService
                  match:
                    headers:
                      - name: accept
                        type: exact
                        value: application/json
                    path:
                      rewrite: /
                      type: prefix
                      value: /index
                  name: index
          name: contosoWebsite
          port: 8081
      location: EastUS
      resourceGroupName: sbz_demo
      sourceNetwork:
        name: Open
      tags: {}
      tcp:
        - destination:
            applicationName: helloWorldApp
            endpointName: helloWorldListener
            serviceName: helloWorldService
          name: web
          port: 80

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:servicefabricmesh:Gateway sampleGateway /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/sbz_demo/providers/Microsoft.ServiceFabricMesh/gateways/sampleGateway 
```
