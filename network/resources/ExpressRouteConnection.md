ExpressRouteConnection resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ExpressRouteConnectionCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var expressRouteConnection = new AzureNative.Network.ExpressRouteConnection("expressRouteConnection", new()
    {
        AuthorizationKey = "authorizationKey",
        ConnectionName = "connectionName",
        ExpressRouteCircuitPeering = new AzureNative.Network.Inputs.ExpressRouteCircuitPeeringIdArgs
        {
            Id = "/subscriptions/subid/resourceGroups/resourceGroupName/providers/Microsoft.Network/expressRouteCircuits/circuitName/peerings/AzurePrivatePeering",
        },
        ExpressRouteGatewayName = "gateway-2",
        Id = "/subscriptions/subid/resourceGroups/resourceGroupName/providers/Microsoft.Network/expressRouteGateways/gateway-2/expressRouteConnections/connectionName",
        Name = "connectionName",
        ResourceGroupName = "resourceGroupName",
        RoutingConfiguration = new AzureNative.Network.Inputs.RoutingConfigurationArgs
        {
            AssociatedRouteTable = new AzureNative.Network.Inputs.SubResourceArgs
            {
                Id = "/subscriptions/subid/resourceGroups/resourceGroupName/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable1",
            },
            InboundRouteMap = new AzureNative.Network.Inputs.SubResourceArgs
            {
                Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/routeMaps/routeMap1",
            },
            OutboundRouteMap = new AzureNative.Network.Inputs.SubResourceArgs
            {
                Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/routeMaps/routeMap2",
            },
            PropagatedRouteTables = new AzureNative.Network.Inputs.PropagatedRouteTableArgs
            {
                Ids = new[]
                {
                    new AzureNative.Network.Inputs.SubResourceArgs
                    {
                        Id = "/subscriptions/subid/resourceGroups/resourceGroupName/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable1",
                    },
                    new AzureNative.Network.Inputs.SubResourceArgs
                    {
                        Id = "/subscriptions/subid/resourceGroups/resourceGroupName/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable2",
                    },
                    new AzureNative.Network.Inputs.SubResourceArgs
                    {
                        Id = "/subscriptions/subid/resourceGroups/resourceGroupName/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable3",
                    },
                },
                Labels = new[]
                {
                    "label1",
                    "label2",
                },
            },
        },
        RoutingWeight = 2,
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.network.ExpressRouteConnection;
import com.pulumi.azurenative.network.ExpressRouteConnectionArgs;
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
        var expressRouteConnection = new ExpressRouteConnection("expressRouteConnection", ExpressRouteConnectionArgs.builder()        
            .authorizationKey("authorizationKey")
            .connectionName("connectionName")
            .expressRouteCircuitPeering(Map.of("id", "/subscriptions/subid/resourceGroups/resourceGroupName/providers/Microsoft.Network/expressRouteCircuits/circuitName/peerings/AzurePrivatePeering"))
            .expressRouteGatewayName("gateway-2")
            .id("/subscriptions/subid/resourceGroups/resourceGroupName/providers/Microsoft.Network/expressRouteGateways/gateway-2/expressRouteConnections/connectionName")
            .name("connectionName")
            .resourceGroupName("resourceGroupName")
            .routingConfiguration(Map.ofEntries(
                Map.entry("associatedRouteTable", Map.of("id", "/subscriptions/subid/resourceGroups/resourceGroupName/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable1")),
                Map.entry("inboundRouteMap", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/routeMaps/routeMap1")),
                Map.entry("outboundRouteMap", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/routeMaps/routeMap2")),
                Map.entry("propagatedRouteTables", Map.ofEntries(
                    Map.entry("ids",                     
                        Map.of("id", "/subscriptions/subid/resourceGroups/resourceGroupName/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable1"),
                        Map.of("id", "/subscriptions/subid/resourceGroups/resourceGroupName/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable2"),
                        Map.of("id", "/subscriptions/subid/resourceGroups/resourceGroupName/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable3")),
                    Map.entry("labels",                     
                        "label1",
                        "label2")
                ))
            ))
            .routingWeight(2)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const expressRouteConnection = new azure_native.network.ExpressRouteConnection("expressRouteConnection", {
    authorizationKey: "authorizationKey",
    connectionName: "connectionName",
    expressRouteCircuitPeering: {
        id: "/subscriptions/subid/resourceGroups/resourceGroupName/providers/Microsoft.Network/expressRouteCircuits/circuitName/peerings/AzurePrivatePeering",
    },
    expressRouteGatewayName: "gateway-2",
    id: "/subscriptions/subid/resourceGroups/resourceGroupName/providers/Microsoft.Network/expressRouteGateways/gateway-2/expressRouteConnections/connectionName",
    name: "connectionName",
    resourceGroupName: "resourceGroupName",
    routingConfiguration: {
        associatedRouteTable: {
            id: "/subscriptions/subid/resourceGroups/resourceGroupName/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable1",
        },
        inboundRouteMap: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/routeMaps/routeMap1",
        },
        outboundRouteMap: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/routeMaps/routeMap2",
        },
        propagatedRouteTables: {
            ids: [
                {
                    id: "/subscriptions/subid/resourceGroups/resourceGroupName/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable1",
                },
                {
                    id: "/subscriptions/subid/resourceGroups/resourceGroupName/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable2",
                },
                {
                    id: "/subscriptions/subid/resourceGroups/resourceGroupName/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable3",
                },
            ],
            labels: [
                "label1",
                "label2",
            ],
        },
    },
    routingWeight: 2,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

express_route_connection = azure_native.network.ExpressRouteConnection("expressRouteConnection",
    authorization_key="authorizationKey",
    connection_name="connectionName",
    express_route_circuit_peering=azure_native.network.ExpressRouteCircuitPeeringIdArgs(
        id="/subscriptions/subid/resourceGroups/resourceGroupName/providers/Microsoft.Network/expressRouteCircuits/circuitName/peerings/AzurePrivatePeering",
    ),
    express_route_gateway_name="gateway-2",
    id="/subscriptions/subid/resourceGroups/resourceGroupName/providers/Microsoft.Network/expressRouteGateways/gateway-2/expressRouteConnections/connectionName",
    name="connectionName",
    resource_group_name="resourceGroupName",
    routing_configuration=azure_native.network.RoutingConfigurationResponseArgs(
        associated_route_table=azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/resourceGroupName/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable1",
        ),
        inbound_route_map=azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/routeMaps/routeMap1",
        ),
        outbound_route_map=azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/routeMaps/routeMap2",
        ),
        propagated_route_tables={
            "ids": [
                azure_native.network.SubResourceArgs(
                    id="/subscriptions/subid/resourceGroups/resourceGroupName/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable1",
                ),
                azure_native.network.SubResourceArgs(
                    id="/subscriptions/subid/resourceGroups/resourceGroupName/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable2",
                ),
                azure_native.network.SubResourceArgs(
                    id="/subscriptions/subid/resourceGroups/resourceGroupName/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable3",
                ),
            ],
            "labels": [
                "label1",
                "label2",
            ],
        },
    ),
    routing_weight=2)

```

```yaml
resources:
  expressRouteConnection:
    type: azure-native:network:ExpressRouteConnection
    properties:
      authorizationKey: authorizationKey
      connectionName: connectionName
      expressRouteCircuitPeering:
        id: /subscriptions/subid/resourceGroups/resourceGroupName/providers/Microsoft.Network/expressRouteCircuits/circuitName/peerings/AzurePrivatePeering
      expressRouteGatewayName: gateway-2
      id: /subscriptions/subid/resourceGroups/resourceGroupName/providers/Microsoft.Network/expressRouteGateways/gateway-2/expressRouteConnections/connectionName
      name: connectionName
      resourceGroupName: resourceGroupName
      routingConfiguration:
        associatedRouteTable:
          id: /subscriptions/subid/resourceGroups/resourceGroupName/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable1
        inboundRouteMap:
          id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/routeMaps/routeMap1
        outboundRouteMap:
          id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/routeMaps/routeMap2
        propagatedRouteTables:
          ids:
            - id: /subscriptions/subid/resourceGroups/resourceGroupName/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable1
            - id: /subscriptions/subid/resourceGroups/resourceGroupName/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable2
            - id: /subscriptions/subid/resourceGroups/resourceGroupName/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable3
          labels:
            - label1
            - label2
      routingWeight: 2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:ExpressRouteConnection connectionName /subscriptions/subid/resourceGroups/resourceGroupName/providers/Microsoft.Network/expressRouteGateways/gateway-2/expressRouteConnections/connectionName 
```
