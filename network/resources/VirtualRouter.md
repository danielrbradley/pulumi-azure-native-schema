VirtualRouter Resource.
API Version: 2022-09-01.
Previous API Version: 2022-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create VirtualRouter
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualRouter = new AzureNative.Network.VirtualRouter("virtualRouter", new()
    {
        HostedGateway = new AzureNative.Network.Inputs.SubResourceArgs
        {
            Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vnetGateway",
        },
        Location = "West US",
        ResourceGroupName = "rg1",
        Tags = 
        {
            { "key1", "value1" },
        },
        VirtualRouterName = "virtualRouter",
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
		_, err := network.NewVirtualRouter(ctx, "virtualRouter", &network.VirtualRouterArgs{
			HostedGateway: &network.SubResourceArgs{
				Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vnetGateway"),
			},
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("rg1"),
			Tags: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			VirtualRouterName: pulumi.String("virtualRouter"),
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
import com.pulumi.azurenative.network.VirtualRouter;
import com.pulumi.azurenative.network.VirtualRouterArgs;
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
        var virtualRouter = new VirtualRouter("virtualRouter", VirtualRouterArgs.builder()        
            .hostedGateway(Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vnetGateway"))
            .location("West US")
            .resourceGroupName("rg1")
            .tags(Map.of("key1", "value1"))
            .virtualRouterName("virtualRouter")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualRouter = new azure_native.network.VirtualRouter("virtualRouter", {
    hostedGateway: {
        id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vnetGateway",
    },
    location: "West US",
    resourceGroupName: "rg1",
    tags: {
        key1: "value1",
    },
    virtualRouterName: "virtualRouter",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_router = azure_native.network.VirtualRouter("virtualRouter",
    hosted_gateway=azure_native.network.SubResourceArgs(
        id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vnetGateway",
    ),
    location="West US",
    resource_group_name="rg1",
    tags={
        "key1": "value1",
    },
    virtual_router_name="virtualRouter")

```

```yaml
resources:
  virtualRouter:
    type: azure-native:network:VirtualRouter
    properties:
      hostedGateway:
        id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/vnetGateway
      location: West US
      resourceGroupName: rg1
      tags:
        key1: value1
      virtualRouterName: virtualRouter

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:VirtualRouter virtualRouter /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualRouters/virtualRouter 
```
