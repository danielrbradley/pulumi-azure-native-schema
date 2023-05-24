The RouteMap child resource of a Virtual hub.
API Version: 2022-09-01.

{{% examples %}}
## Example Usage
{{% example %}}
### RouteMapPut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var routeMap = new AzureNative.Network.RouteMap("routeMap", new()
    {
        AssociatedInboundConnections = new[]
        {
            "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/expressRouteGateways/exrGateway1/expressRouteConnections/exrConn1",
        },
        AssociatedOutboundConnections = new[] {},
        ResourceGroupName = "rg1",
        RouteMapName = "routeMap1",
        Rules = new[]
        {
            new AzureNative.Network.Inputs.RouteMapRuleArgs
            {
                Actions = new[]
                {
                    new AzureNative.Network.Inputs.ActionArgs
                    {
                        Parameters = new[]
                        {
                            new AzureNative.Network.Inputs.ParameterArgs
                            {
                                AsPath = new[]
                                {
                                    "22334",
                                },
                                Community = new[] {},
                                RoutePrefix = new[] {},
                            },
                        },
                        Type = "Add",
                    },
                },
                MatchCriteria = new[]
                {
                    new AzureNative.Network.Inputs.CriterionArgs
                    {
                        AsPath = new[] {},
                        Community = new[] {},
                        MatchCondition = "Contains",
                        RoutePrefix = new[]
                        {
                            "10.0.0.0/8",
                        },
                    },
                },
                Name = "rule1",
                NextStepIfMatched = "Continue",
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
		_, err := network.NewRouteMap(ctx, "routeMap", &network.RouteMapArgs{
			AssociatedInboundConnections: pulumi.StringArray{
				pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/expressRouteGateways/exrGateway1/expressRouteConnections/exrConn1"),
			},
			AssociatedOutboundConnections: pulumi.StringArray{},
			ResourceGroupName:             pulumi.String("rg1"),
			RouteMapName:                  pulumi.String("routeMap1"),
			Rules: []network.RouteMapRuleArgs{
				{
					Actions: network.ActionArray{
						{
							Parameters: network.ParameterArray{
								{
									AsPath: pulumi.StringArray{
										pulumi.String("22334"),
									},
									Community:   pulumi.StringArray{},
									RoutePrefix: pulumi.StringArray{},
								},
							},
							Type: pulumi.String("Add"),
						},
					},
					MatchCriteria: network.CriterionArray{
						{
							AsPath:         pulumi.StringArray{},
							Community:      pulumi.StringArray{},
							MatchCondition: pulumi.String("Contains"),
							RoutePrefix: pulumi.StringArray{
								pulumi.String("10.0.0.0/8"),
							},
						},
					},
					Name:              pulumi.String("rule1"),
					NextStepIfMatched: pulumi.String("Continue"),
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
import com.pulumi.azurenative.network.RouteMap;
import com.pulumi.azurenative.network.RouteMapArgs;
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
        var routeMap = new RouteMap("routeMap", RouteMapArgs.builder()        
            .associatedInboundConnections("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/expressRouteGateways/exrGateway1/expressRouteConnections/exrConn1")
            .associatedOutboundConnections()
            .resourceGroupName("rg1")
            .routeMapName("routeMap1")
            .rules(Map.ofEntries(
                Map.entry("actions", Map.ofEntries(
                    Map.entry("parameters", Map.ofEntries(
                        Map.entry("asPath", "22334"),
                        Map.entry("community", ),
                        Map.entry("routePrefix", )
                    )),
                    Map.entry("type", "Add")
                )),
                Map.entry("matchCriteria", Map.ofEntries(
                    Map.entry("asPath", ),
                    Map.entry("community", ),
                    Map.entry("matchCondition", "Contains"),
                    Map.entry("routePrefix", "10.0.0.0/8")
                )),
                Map.entry("name", "rule1"),
                Map.entry("nextStepIfMatched", "Continue")
            ))
            .virtualHubName("virtualHub1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const routeMap = new azure_native.network.RouteMap("routeMap", {
    associatedInboundConnections: ["/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/expressRouteGateways/exrGateway1/expressRouteConnections/exrConn1"],
    associatedOutboundConnections: [],
    resourceGroupName: "rg1",
    routeMapName: "routeMap1",
    rules: [{
        actions: [{
            parameters: [{
                asPath: ["22334"],
                community: [],
                routePrefix: [],
            }],
            type: "Add",
        }],
        matchCriteria: [{
            asPath: [],
            community: [],
            matchCondition: "Contains",
            routePrefix: ["10.0.0.0/8"],
        }],
        name: "rule1",
        nextStepIfMatched: "Continue",
    }],
    virtualHubName: "virtualHub1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

route_map = azure_native.network.RouteMap("routeMap",
    associated_inbound_connections=["/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/expressRouteGateways/exrGateway1/expressRouteConnections/exrConn1"],
    associated_outbound_connections=[],
    resource_group_name="rg1",
    route_map_name="routeMap1",
    rules=[{
        "actions": [{
            "parameters": [azure_native.network.ParameterArgs(
                as_path=["22334"],
                community=[],
                route_prefix=[],
            )],
            "type": "Add",
        }],
        "matchCriteria": [azure_native.network.CriterionArgs(
            as_path=[],
            community=[],
            match_condition="Contains",
            route_prefix=["10.0.0.0/8"],
        )],
        "name": "rule1",
        "nextStepIfMatched": "Continue",
    }],
    virtual_hub_name="virtualHub1")

```

```yaml
resources:
  routeMap:
    type: azure-native:network:RouteMap
    properties:
      associatedInboundConnections:
        - /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/expressRouteGateways/exrGateway1/expressRouteConnections/exrConn1
      associatedOutboundConnections: []
      resourceGroupName: rg1
      routeMapName: routeMap1
      rules:
        - actions:
            - parameters:
                - asPath:
                    - '22334'
                  community: []
                  routePrefix: []
              type: Add
          matchCriteria:
            - asPath: []
              community: []
              matchCondition: Contains
              routePrefix:
                - 10.0.0.0/8
          name: rule1
          nextStepIfMatched: Continue
      virtualHubName: virtualHub1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:RouteMap routeMap1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/routeMaps/routeMap1 
```
