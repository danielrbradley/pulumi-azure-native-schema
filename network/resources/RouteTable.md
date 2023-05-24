Route table resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create route table
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var routeTable = new AzureNative.Network.RouteTable("routeTable", new()
    {
        Location = "westus",
        ResourceGroupName = "rg1",
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
		_, err := network.NewRouteTable(ctx, "routeTable", &network.RouteTableArgs{
			Location:          pulumi.String("westus"),
			ResourceGroupName: pulumi.String("rg1"),
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
import com.pulumi.azurenative.network.RouteTable;
import com.pulumi.azurenative.network.RouteTableArgs;
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
        var routeTable = new RouteTable("routeTable", RouteTableArgs.builder()        
            .location("westus")
            .resourceGroupName("rg1")
            .routeTableName("testrt")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const routeTable = new azure_native.network.RouteTable("routeTable", {
    location: "westus",
    resourceGroupName: "rg1",
    routeTableName: "testrt",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

route_table = azure_native.network.RouteTable("routeTable",
    location="westus",
    resource_group_name="rg1",
    route_table_name="testrt")

```

```yaml
resources:
  routeTable:
    type: azure-native:network:RouteTable
    properties:
      location: westus
      resourceGroupName: rg1
      routeTableName: testrt

```

{{% /example %}}
{{% example %}}
### Create route table with route
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var routeTable = new AzureNative.Network.RouteTable("routeTable", new()
    {
        DisableBgpRoutePropagation = true,
        Location = "westus",
        ResourceGroupName = "rg1",
        RouteTableName = "testrt",
        Routes = new[]
        {
            new AzureNative.Network.Inputs.RouteArgs
            {
                AddressPrefix = "10.0.3.0/24",
                Name = "route1",
                NextHopType = "VirtualNetworkGateway",
            },
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
		_, err := network.NewRouteTable(ctx, "routeTable", &network.RouteTableArgs{
			DisableBgpRoutePropagation: pulumi.Bool(true),
			Location:                   pulumi.String("westus"),
			ResourceGroupName:          pulumi.String("rg1"),
			RouteTableName:             pulumi.String("testrt"),
			Routes: []network.RouteTypeArgs{
				{
					AddressPrefix: pulumi.String("10.0.3.0/24"),
					Name:          pulumi.String("route1"),
					NextHopType:   pulumi.String("VirtualNetworkGateway"),
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
import com.pulumi.azurenative.network.RouteTable;
import com.pulumi.azurenative.network.RouteTableArgs;
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
        var routeTable = new RouteTable("routeTable", RouteTableArgs.builder()        
            .disableBgpRoutePropagation(true)
            .location("westus")
            .resourceGroupName("rg1")
            .routeTableName("testrt")
            .routes(Map.ofEntries(
                Map.entry("addressPrefix", "10.0.3.0/24"),
                Map.entry("name", "route1"),
                Map.entry("nextHopType", "VirtualNetworkGateway")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const routeTable = new azure_native.network.RouteTable("routeTable", {
    disableBgpRoutePropagation: true,
    location: "westus",
    resourceGroupName: "rg1",
    routeTableName: "testrt",
    routes: [{
        addressPrefix: "10.0.3.0/24",
        name: "route1",
        nextHopType: "VirtualNetworkGateway",
    }],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

route_table = azure_native.network.RouteTable("routeTable",
    disable_bgp_route_propagation=True,
    location="westus",
    resource_group_name="rg1",
    route_table_name="testrt",
    routes=[azure_native.network.RouteArgs(
        address_prefix="10.0.3.0/24",
        name="route1",
        next_hop_type="VirtualNetworkGateway",
    )])

```

```yaml
resources:
  routeTable:
    type: azure-native:network:RouteTable
    properties:
      disableBgpRoutePropagation: true
      location: westus
      resourceGroupName: rg1
      routeTableName: testrt
      routes:
        - addressPrefix: 10.0.3.0/24
          name: route1
          nextHopType: VirtualNetworkGateway

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:RouteTable testrt /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/routeTables/testrt 
```
