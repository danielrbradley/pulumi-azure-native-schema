RouteTable resource in a virtual hub.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### RouteTablePut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var hubRouteTable = new AzureNative.Network.HubRouteTable("hubRouteTable", new()
    {
        Labels = new[]
        {
            "label1",
            "label2",
        },
        ResourceGroupName = "rg1",
        RouteTableName = "hubRouteTable1",
        Routes = new[]
        {
            new AzureNative.Network.Inputs.HubRouteArgs
            {
                DestinationType = "CIDR",
                Destinations = new[]
                {
                    "10.0.0.0/8",
                    "20.0.0.0/8",
                    "30.0.0.0/8",
                },
                Name = "route1",
                NextHop = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/azureFirewalls/azureFirewall1",
                NextHopType = "ResourceId",
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
		_, err := network.NewHubRouteTable(ctx, "hubRouteTable", &network.HubRouteTableArgs{
			Labels: pulumi.StringArray{
				pulumi.String("label1"),
				pulumi.String("label2"),
			},
			ResourceGroupName: pulumi.String("rg1"),
			RouteTableName:    pulumi.String("hubRouteTable1"),
			Routes: []network.HubRouteArgs{
				{
					DestinationType: pulumi.String("CIDR"),
					Destinations: pulumi.StringArray{
						pulumi.String("10.0.0.0/8"),
						pulumi.String("20.0.0.0/8"),
						pulumi.String("30.0.0.0/8"),
					},
					Name:        pulumi.String("route1"),
					NextHop:     pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/azureFirewalls/azureFirewall1"),
					NextHopType: pulumi.String("ResourceId"),
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
import com.pulumi.azurenative.network.HubRouteTable;
import com.pulumi.azurenative.network.HubRouteTableArgs;
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
        var hubRouteTable = new HubRouteTable("hubRouteTable", HubRouteTableArgs.builder()        
            .labels(            
                "label1",
                "label2")
            .resourceGroupName("rg1")
            .routeTableName("hubRouteTable1")
            .routes(Map.ofEntries(
                Map.entry("destinationType", "CIDR"),
                Map.entry("destinations",                 
                    "10.0.0.0/8",
                    "20.0.0.0/8",
                    "30.0.0.0/8"),
                Map.entry("name", "route1"),
                Map.entry("nextHop", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/azureFirewalls/azureFirewall1"),
                Map.entry("nextHopType", "ResourceId")
            ))
            .virtualHubName("virtualHub1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const hubRouteTable = new azure_native.network.HubRouteTable("hubRouteTable", {
    labels: [
        "label1",
        "label2",
    ],
    resourceGroupName: "rg1",
    routeTableName: "hubRouteTable1",
    routes: [{
        destinationType: "CIDR",
        destinations: [
            "10.0.0.0/8",
            "20.0.0.0/8",
            "30.0.0.0/8",
        ],
        name: "route1",
        nextHop: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/azureFirewalls/azureFirewall1",
        nextHopType: "ResourceId",
    }],
    virtualHubName: "virtualHub1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

hub_route_table = azure_native.network.HubRouteTable("hubRouteTable",
    labels=[
        "label1",
        "label2",
    ],
    resource_group_name="rg1",
    route_table_name="hubRouteTable1",
    routes=[azure_native.network.HubRouteArgs(
        destination_type="CIDR",
        destinations=[
            "10.0.0.0/8",
            "20.0.0.0/8",
            "30.0.0.0/8",
        ],
        name="route1",
        next_hop="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/azureFirewalls/azureFirewall1",
        next_hop_type="ResourceId",
    )],
    virtual_hub_name="virtualHub1")

```

```yaml
resources:
  hubRouteTable:
    type: azure-native:network:HubRouteTable
    properties:
      labels:
        - label1
        - label2
      resourceGroupName: rg1
      routeTableName: hubRouteTable1
      routes:
        - destinationType: CIDR
          destinations:
            - 10.0.0.0/8
            - 20.0.0.0/8
            - 30.0.0.0/8
          name: route1
          nextHop: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/azureFirewalls/azureFirewall1
          nextHopType: ResourceId
      virtualHubName: virtualHub1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:HubRouteTable hubRouteTable1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable1 
```
