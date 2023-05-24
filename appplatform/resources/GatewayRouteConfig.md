Spring Cloud Gateway route config resource
API Version: 2022-12-01.
Previous API Version: 2022-01-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### GatewayRouteConfigs_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var gatewayRouteConfig = new AzureNative.AppPlatform.GatewayRouteConfig("gatewayRouteConfig", new()
    {
        GatewayName = "default",
        Properties = new AzureNative.AppPlatform.Inputs.GatewayRouteConfigPropertiesArgs
        {
            AppResourceId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.AppPlatform/Spring/myservice/apps/myApp",
            OpenApi = new AzureNative.AppPlatform.Inputs.GatewayRouteConfigOpenApiPropertiesArgs
            {
                Uri = "https://raw.githubusercontent.com/OAI/OpenAPI-Specification/main/examples/v3.0/petstore.json",
            },
            Protocol = "HTTPS",
            Routes = new[]
            {
                new AzureNative.AppPlatform.Inputs.GatewayApiRouteArgs
                {
                    Filters = new[]
                    {
                        "StripPrefix=2",
                        "RateLimit=1,1s",
                    },
                    Predicates = new[]
                    {
                        "Path=/api5/customer/**",
                    },
                    SsoEnabled = true,
                    Title = "myApp route config",
                },
            },
        },
        ResourceGroupName = "myResourceGroup",
        RouteConfigName = "myRouteConfig",
        ServiceName = "myservice",
    });

});


```

```go
package main

import (
	appplatform "github.com/pulumi/pulumi-azure-native-sdk/appplatform"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := appplatform.NewGatewayRouteConfig(ctx, "gatewayRouteConfig", &appplatform.GatewayRouteConfigArgs{
			GatewayName: pulumi.String("default"),
			Properties: appplatform.GatewayRouteConfigPropertiesResponse{
				AppResourceId: pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.AppPlatform/Spring/myservice/apps/myApp"),
				OpenApi: &appplatform.GatewayRouteConfigOpenApiPropertiesArgs{
					Uri: pulumi.String("https://raw.githubusercontent.com/OAI/OpenAPI-Specification/main/examples/v3.0/petstore.json"),
				},
				Protocol: pulumi.String("HTTPS"),
				Routes: appplatform.GatewayApiRouteArray{
					&appplatform.GatewayApiRouteArgs{
						Filters: pulumi.StringArray{
							pulumi.String("StripPrefix=2"),
							pulumi.String("RateLimit=1,1s"),
						},
						Predicates: pulumi.StringArray{
							pulumi.String("Path=/api5/customer/**"),
						},
						SsoEnabled: pulumi.Bool(true),
						Title:      pulumi.String("myApp route config"),
					},
				},
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
			RouteConfigName:   pulumi.String("myRouteConfig"),
			ServiceName:       pulumi.String("myservice"),
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
import com.pulumi.azurenative.appplatform.GatewayRouteConfig;
import com.pulumi.azurenative.appplatform.GatewayRouteConfigArgs;
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
        var gatewayRouteConfig = new GatewayRouteConfig("gatewayRouteConfig", GatewayRouteConfigArgs.builder()        
            .gatewayName("default")
            .properties(Map.ofEntries(
                Map.entry("appResourceId", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.AppPlatform/Spring/myservice/apps/myApp"),
                Map.entry("openApi", Map.of("uri", "https://raw.githubusercontent.com/OAI/OpenAPI-Specification/main/examples/v3.0/petstore.json")),
                Map.entry("protocol", "HTTPS"),
                Map.entry("routes", Map.ofEntries(
                    Map.entry("filters",                     
                        "StripPrefix=2",
                        "RateLimit=1,1s"),
                    Map.entry("predicates", "Path=/api5/customer/**"),
                    Map.entry("ssoEnabled", true),
                    Map.entry("title", "myApp route config")
                ))
            ))
            .resourceGroupName("myResourceGroup")
            .routeConfigName("myRouteConfig")
            .serviceName("myservice")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const gatewayRouteConfig = new azure_native.appplatform.GatewayRouteConfig("gatewayRouteConfig", {
    gatewayName: "default",
    properties: {
        appResourceId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.AppPlatform/Spring/myservice/apps/myApp",
        openApi: {
            uri: "https://raw.githubusercontent.com/OAI/OpenAPI-Specification/main/examples/v3.0/petstore.json",
        },
        protocol: "HTTPS",
        routes: [{
            filters: [
                "StripPrefix=2",
                "RateLimit=1,1s",
            ],
            predicates: ["Path=/api5/customer/**"],
            ssoEnabled: true,
            title: "myApp route config",
        }],
    },
    resourceGroupName: "myResourceGroup",
    routeConfigName: "myRouteConfig",
    serviceName: "myservice",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

gateway_route_config = azure_native.appplatform.GatewayRouteConfig("gatewayRouteConfig",
    gateway_name="default",
    properties=azure_native.appplatform.GatewayRouteConfigPropertiesResponseArgs(
        app_resource_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.AppPlatform/Spring/myservice/apps/myApp",
        open_api=azure_native.appplatform.GatewayRouteConfigOpenApiPropertiesArgs(
            uri="https://raw.githubusercontent.com/OAI/OpenAPI-Specification/main/examples/v3.0/petstore.json",
        ),
        protocol="HTTPS",
        routes=[azure_native.appplatform.GatewayApiRouteArgs(
            filters=[
                "StripPrefix=2",
                "RateLimit=1,1s",
            ],
            predicates=["Path=/api5/customer/**"],
            sso_enabled=True,
            title="myApp route config",
        )],
    ),
    resource_group_name="myResourceGroup",
    route_config_name="myRouteConfig",
    service_name="myservice")

```

```yaml
resources:
  gatewayRouteConfig:
    type: azure-native:appplatform:GatewayRouteConfig
    properties:
      gatewayName: default
      properties:
        appResourceId: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.AppPlatform/Spring/myservice/apps/myApp
        openApi:
          uri: https://raw.githubusercontent.com/OAI/OpenAPI-Specification/main/examples/v3.0/petstore.json
        protocol: HTTPS
        routes:
          - filters:
              - StripPrefix=2
              - RateLimit=1,1s
            predicates:
              - Path=/api5/customer/**
            ssoEnabled: true
            title: myApp route config
      resourceGroupName: myResourceGroup
      routeConfigName: myRouteConfig
      serviceName: myservice

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:appplatform:GatewayRouteConfig myRouteConfig /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.AppPlatform/Spring/myservice/gateways/default/routeConfigs/myRouteConfig 
```
