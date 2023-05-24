Spring Cloud Gateway resource
API Version: 2022-12-01.
Previous API Version: 2022-01-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Gateways_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var gateway = new AzureNative.AppPlatform.Gateway("gateway", new()
    {
        GatewayName = "default",
        Properties = new AzureNative.AppPlatform.Inputs.GatewayPropertiesArgs
        {
            Public = true,
            ResourceRequests = new AzureNative.AppPlatform.Inputs.GatewayResourceRequestsArgs
            {
                Cpu = "1",
                Memory = "1G",
            },
        },
        ResourceGroupName = "myResourceGroup",
        ServiceName = "myservice",
        Sku = new AzureNative.AppPlatform.Inputs.SkuArgs
        {
            Capacity = 2,
            Name = "E0",
            Tier = "Enterprise",
        },
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
		_, err := appplatform.NewGateway(ctx, "gateway", &appplatform.GatewayArgs{
			GatewayName: pulumi.String("default"),
			Properties: appplatform.GatewayPropertiesResponse{
				Public: pulumi.Bool(true),
				ResourceRequests: &appplatform.GatewayResourceRequestsArgs{
					Cpu:    pulumi.String("1"),
					Memory: pulumi.String("1G"),
				},
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
			ServiceName:       pulumi.String("myservice"),
			Sku: &appplatform.SkuArgs{
				Capacity: pulumi.Int(2),
				Name:     pulumi.String("E0"),
				Tier:     pulumi.String("Enterprise"),
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
import com.pulumi.azurenative.appplatform.Gateway;
import com.pulumi.azurenative.appplatform.GatewayArgs;
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
            .gatewayName("default")
            .properties(Map.ofEntries(
                Map.entry("public", true),
                Map.entry("resourceRequests", Map.ofEntries(
                    Map.entry("cpu", "1"),
                    Map.entry("memory", "1G")
                ))
            ))
            .resourceGroupName("myResourceGroup")
            .serviceName("myservice")
            .sku(Map.ofEntries(
                Map.entry("capacity", 2),
                Map.entry("name", "E0"),
                Map.entry("tier", "Enterprise")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const gateway = new azure_native.appplatform.Gateway("gateway", {
    gatewayName: "default",
    properties: {
        "public": true,
        resourceRequests: {
            cpu: "1",
            memory: "1G",
        },
    },
    resourceGroupName: "myResourceGroup",
    serviceName: "myservice",
    sku: {
        capacity: 2,
        name: "E0",
        tier: "Enterprise",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

gateway = azure_native.appplatform.Gateway("gateway",
    gateway_name="default",
    properties=azure_native.appplatform.GatewayPropertiesResponseArgs(
        public=True,
        resource_requests=azure_native.appplatform.GatewayResourceRequestsArgs(
            cpu="1",
            memory="1G",
        ),
    ),
    resource_group_name="myResourceGroup",
    service_name="myservice",
    sku=azure_native.appplatform.SkuArgs(
        capacity=2,
        name="E0",
        tier="Enterprise",
    ))

```

```yaml
resources:
  gateway:
    type: azure-native:appplatform:Gateway
    properties:
      gatewayName: default
      properties:
        public: true
        resourceRequests:
          cpu: '1'
          memory: 1G
      resourceGroupName: myResourceGroup
      serviceName: myservice
      sku:
        capacity: 2
        name: E0
        tier: Enterprise

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:appplatform:Gateway default /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.AppPlatform/Spring/myservice/gateways/default 
```
