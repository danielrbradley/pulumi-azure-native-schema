Route resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create route
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var route = new AzureNative.Network.Route("route", new()
    {
        AddressPrefix = "10.0.3.0/24",
        NextHopType = "VirtualNetworkGateway",
        ResourceGroupName = "rg1",
        RouteName = "route1",
        RouteTableName = "testrt",
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
		_, err := network.NewRoute(ctx, "route", &network.RouteArgs{
			AddressPrefix:     pulumi.String("10.0.3.0/24"),
			NextHopType:       pulumi.String("VirtualNetworkGateway"),
			ResourceGroupName: pulumi.String("rg1"),
			RouteName:         pulumi.String("route1"),
			RouteTableName:    pulumi.String("testrt"),
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
import com.pulumi.azurenative.network.Route;
import com.pulumi.azurenative.network.RouteArgs;
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
        var route = new Route("route", RouteArgs.builder()        
            .addressPrefix("10.0.3.0/24")
            .nextHopType("VirtualNetworkGateway")
            .resourceGroupName("rg1")
            .routeName("route1")
            .routeTableName("testrt")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const route = new azure_native.network.Route("route", {
    addressPrefix: "10.0.3.0/24",
    nextHopType: "VirtualNetworkGateway",
    resourceGroupName: "rg1",
    routeName: "route1",
    routeTableName: "testrt",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

route = azure_native.network.Route("route",
    address_prefix="10.0.3.0/24",
    next_hop_type="VirtualNetworkGateway",
    resource_group_name="rg1",
    route_name="route1",
    route_table_name="testrt")

```

```yaml
resources:
  route:
    type: azure-native:network:Route
    properties:
      addressPrefix: 10.0.3.0/24
      nextHopType: VirtualNetworkGateway
      resourceGroupName: rg1
      routeName: route1
      routeTableName: testrt

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:Route route1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/routeTables/testrt/routes/route1 
```
