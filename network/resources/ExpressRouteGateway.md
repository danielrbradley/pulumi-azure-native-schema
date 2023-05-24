ExpressRoute gateway resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ExpressRouteGatewayCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var expressRouteGateway = new AzureNative.Network.ExpressRouteGateway("expressRouteGateway", new()
    {
        AllowNonVirtualWanTraffic = false,
        AutoScaleConfiguration = new AzureNative.Network.Inputs.ExpressRouteGatewayPropertiesAutoScaleConfigurationArgs
        {
            Bounds = new AzureNative.Network.Inputs.ExpressRouteGatewayPropertiesBoundsArgs
            {
                Min = 3,
            },
        },
        ExpressRouteGatewayName = "gateway-2",
        Location = "westus",
        ResourceGroupName = "resourceGroupName",
        VirtualHub = new AzureNative.Network.Inputs.VirtualHubIdArgs
        {
            Id = "/subscriptions/subid/resourceGroups/resourceGroupId/providers/Microsoft.Network/virtualHubs/virtualHubName",
        },
    });

});


```

```go
package main

import (
	network "github.com/pulumi/pulumi-azure-native-sdk/network"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := network.NewExpressRouteGateway(ctx, "expressRouteGateway", &network.ExpressRouteGatewayArgs{
			AllowNonVirtualWanTraffic: pulumi.Bool(false),
			AutoScaleConfiguration: network.ExpressRouteGatewayPropertiesResponseAutoScaleConfiguration{
				Bounds: &network.ExpressRouteGatewayPropertiesBoundsArgs{
					Min: pulumi.Int(3),
				},
			},
			ExpressRouteGatewayName: pulumi.String("gateway-2"),
			Location:                pulumi.String("westus"),
			ResourceGroupName:       pulumi.String("resourceGroupName"),
			VirtualHub: &network.VirtualHubIdArgs{
				Id: pulumi.String("/subscriptions/subid/resourceGroups/resourceGroupId/providers/Microsoft.Network/virtualHubs/virtualHubName"),
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
import com.pulumi.azurenative.network.ExpressRouteGateway;
import com.pulumi.azurenative.network.ExpressRouteGatewayArgs;
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
        var expressRouteGateway = new ExpressRouteGateway("expressRouteGateway", ExpressRouteGatewayArgs.builder()        
            .allowNonVirtualWanTraffic(false)
            .autoScaleConfiguration(Map.of("bounds", Map.of("min", 3)))
            .expressRouteGatewayName("gateway-2")
            .location("westus")
            .resourceGroupName("resourceGroupName")
            .virtualHub(Map.of("id", "/subscriptions/subid/resourceGroups/resourceGroupId/providers/Microsoft.Network/virtualHubs/virtualHubName"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const expressRouteGateway = new azure_native.network.ExpressRouteGateway("expressRouteGateway", {
    allowNonVirtualWanTraffic: false,
    autoScaleConfiguration: {
        bounds: {
            min: 3,
        },
    },
    expressRouteGatewayName: "gateway-2",
    location: "westus",
    resourceGroupName: "resourceGroupName",
    virtualHub: {
        id: "/subscriptions/subid/resourceGroups/resourceGroupId/providers/Microsoft.Network/virtualHubs/virtualHubName",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

express_route_gateway = azure_native.network.ExpressRouteGateway("expressRouteGateway",
    allow_non_virtual_wan_traffic=False,
    auto_scale_configuration=azure_native.network.ExpressRouteGatewayPropertiesResponseAutoScaleConfigurationArgs(
        bounds=azure_native.network.ExpressRouteGatewayPropertiesBoundsArgs(
            min=3,
        ),
    ),
    express_route_gateway_name="gateway-2",
    location="westus",
    resource_group_name="resourceGroupName",
    virtual_hub=azure_native.network.VirtualHubIdArgs(
        id="/subscriptions/subid/resourceGroups/resourceGroupId/providers/Microsoft.Network/virtualHubs/virtualHubName",
    ))

```

```yaml
resources:
  expressRouteGateway:
    type: azure-native:network:ExpressRouteGateway
    properties:
      allowNonVirtualWanTraffic: false
      autoScaleConfiguration:
        bounds:
          min: 3
      expressRouteGatewayName: gateway-2
      location: westus
      resourceGroupName: resourceGroupName
      virtualHub:
        id: /subscriptions/subid/resourceGroups/resourceGroupId/providers/Microsoft.Network/virtualHubs/virtualHubName

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:ExpressRouteGateway gateway-2 /subscriptions/subid/resourceGroups/resourceGroupName/providers/Microsoft.Network/expressRouteGateways/gateway-2 
```
