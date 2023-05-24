VirtualHubRouteTableV2 Resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### VirtualHubRouteTableV2Put
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualHubRouteTableV2 = new AzureNative.Network.VirtualHubRouteTableV2("virtualHubRouteTableV2", new()
    {
        AttachedConnections = new[]
        {
            "All_Vnets",
        },
        ResourceGroupName = "rg1",
        RouteTableName = "virtualHubRouteTable1a",
        Routes = new[]
        {
            new AzureNative.Network.Inputs.VirtualHubRouteV2Args
            {
                DestinationType = "CIDR",
                Destinations = new[]
                {
                    "20.10.0.0/16",
                    "20.20.0.0/16",
                },
                NextHopType = "IPAddress",
                NextHops = new[]
                {
                    "10.0.0.68",
                },
            },
            new AzureNative.Network.Inputs.VirtualHubRouteV2Args
            {
                DestinationType = "CIDR",
                Destinations = new[]
                {
                    "0.0.0.0/0",
                },
                NextHopType = "IPAddress",
                NextHops = new[]
                {
                    "10.0.0.68",
                },
            },
        },
        VirtualHubName = "virtualHub1",
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
		_, err := network.NewVirtualHubRouteTableV2(ctx, "virtualHubRouteTableV2", &network.VirtualHubRouteTableV2Args{
			AttachedConnections: pulumi.StringArray{
				pulumi.String("All_Vnets"),
			},
			ResourceGroupName: pulumi.String("rg1"),
			RouteTableName:    pulumi.String("virtualHubRouteTable1a"),
			Routes: []network.VirtualHubRouteV2Args{
				{
					DestinationType: pulumi.String("CIDR"),
					Destinations: pulumi.StringArray{
						pulumi.String("20.10.0.0/16"),
						pulumi.String("20.20.0.0/16"),
					},
					NextHopType: pulumi.String("IPAddress"),
					NextHops: pulumi.StringArray{
						pulumi.String("10.0.0.68"),
					},
				},
				{
					DestinationType: pulumi.String("CIDR"),
					Destinations: pulumi.StringArray{
						pulumi.String("0.0.0.0/0"),
					},
					NextHopType: pulumi.String("IPAddress"),
					NextHops: pulumi.StringArray{
						pulumi.String("10.0.0.68"),
					},
				},
			},
			VirtualHubName: pulumi.String("virtualHub1"),
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
import com.pulumi.azurenative.network.VirtualHubRouteTableV2;
import com.pulumi.azurenative.network.VirtualHubRouteTableV2Args;
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
        var virtualHubRouteTableV2 = new VirtualHubRouteTableV2("virtualHubRouteTableV2", VirtualHubRouteTableV2Args.builder()        
            .attachedConnections("All_Vnets")
            .resourceGroupName("rg1")
            .routeTableName("virtualHubRouteTable1a")
            .routes(            
                Map.ofEntries(
                    Map.entry("destinationType", "CIDR"),
                    Map.entry("destinations",                     
                        "20.10.0.0/16",
                        "20.20.0.0/16"),
                    Map.entry("nextHopType", "IPAddress"),
                    Map.entry("nextHops", "10.0.0.68")
                ),
                Map.ofEntries(
                    Map.entry("destinationType", "CIDR"),
                    Map.entry("destinations", "0.0.0.0/0"),
                    Map.entry("nextHopType", "IPAddress"),
                    Map.entry("nextHops", "10.0.0.68")
                ))
            .virtualHubName("virtualHub1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualHubRouteTableV2 = new azure_native.network.VirtualHubRouteTableV2("virtualHubRouteTableV2", {
    attachedConnections: ["All_Vnets"],
    resourceGroupName: "rg1",
    routeTableName: "virtualHubRouteTable1a",
    routes: [
        {
            destinationType: "CIDR",
            destinations: [
                "20.10.0.0/16",
                "20.20.0.0/16",
            ],
            nextHopType: "IPAddress",
            nextHops: ["10.0.0.68"],
        },
        {
            destinationType: "CIDR",
            destinations: ["0.0.0.0/0"],
            nextHopType: "IPAddress",
            nextHops: ["10.0.0.68"],
        },
    ],
    virtualHubName: "virtualHub1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_hub_route_table_v2 = azure_native.network.VirtualHubRouteTableV2("virtualHubRouteTableV2",
    attached_connections=["All_Vnets"],
    resource_group_name="rg1",
    route_table_name="virtualHubRouteTable1a",
    routes=[
        azure_native.network.VirtualHubRouteV2Args(
            destination_type="CIDR",
            destinations=[
                "20.10.0.0/16",
                "20.20.0.0/16",
            ],
            next_hop_type="IPAddress",
            next_hops=["10.0.0.68"],
        ),
        azure_native.network.VirtualHubRouteV2Args(
            destination_type="CIDR",
            destinations=["0.0.0.0/0"],
            next_hop_type="IPAddress",
            next_hops=["10.0.0.68"],
        ),
    ],
    virtual_hub_name="virtualHub1")

```

```yaml
resources:
  virtualHubRouteTableV2:
    type: azure-native:network:VirtualHubRouteTableV2
    properties:
      attachedConnections:
        - All_Vnets
      resourceGroupName: rg1
      routeTableName: virtualHubRouteTable1a
      routes:
        - destinationType: CIDR
          destinations:
            - 20.10.0.0/16
            - 20.20.0.0/16
          nextHopType: IPAddress
          nextHops:
            - 10.0.0.68
        - destinationType: CIDR
          destinations:
            - 0.0.0.0/0
          nextHopType: IPAddress
          nextHops:
            - 10.0.0.68
      virtualHubName: virtualHub1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:VirtualHubRouteTableV2 virtualHubRouteTable1a /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/routeTables/virtualHubRouteTable1a 
```
