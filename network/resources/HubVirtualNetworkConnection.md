HubVirtualNetworkConnection Resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### HubVirtualNetworkConnectionPut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var hubVirtualNetworkConnection = new AzureNative.Network.HubVirtualNetworkConnection("hubVirtualNetworkConnection", new()
    {
        ConnectionName = "connection1",
        EnableInternetSecurity = false,
        RemoteVirtualNetwork = new AzureNative.Network.Inputs.SubResourceArgs
        {
            Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/SpokeVnet1",
        },
        ResourceGroupName = "rg1",
        RoutingConfiguration = new AzureNative.Network.Inputs.RoutingConfigurationArgs
        {
            AssociatedRouteTable = new AzureNative.Network.Inputs.SubResourceArgs
            {
                Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable1",
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
                        Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable1",
                    },
                },
                Labels = new[]
                {
                    "label1",
                    "label2",
                },
            },
            VnetRoutes = new AzureNative.Network.Inputs.VnetRouteArgs
            {
                StaticRoutes = new[]
                {
                    new AzureNative.Network.Inputs.StaticRouteArgs
                    {
                        AddressPrefixes = new[]
                        {
                            "10.1.0.0/16",
                            "10.2.0.0/16",
                        },
                        Name = "route1",
                        NextHopIpAddress = "10.0.0.68",
                    },
                    new AzureNative.Network.Inputs.StaticRouteArgs
                    {
                        AddressPrefixes = new[]
                        {
                            "10.3.0.0/16",
                            "10.4.0.0/16",
                        },
                        Name = "route2",
                        NextHopIpAddress = "10.0.0.65",
                    },
                },
                StaticRoutesConfig = new AzureNative.Network.Inputs.StaticRoutesConfigArgs
                {
                    VnetLocalRouteOverrideCriteria = "Equal",
                },
            },
        },
        VirtualHubName = "virtualHub1",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.network.HubVirtualNetworkConnection;
import com.pulumi.azurenative.network.HubVirtualNetworkConnectionArgs;
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
        var hubVirtualNetworkConnection = new HubVirtualNetworkConnection("hubVirtualNetworkConnection", HubVirtualNetworkConnectionArgs.builder()        
            .connectionName("connection1")
            .enableInternetSecurity(false)
            .remoteVirtualNetwork(Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/SpokeVnet1"))
            .resourceGroupName("rg1")
            .routingConfiguration(Map.ofEntries(
                Map.entry("associatedRouteTable", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable1")),
                Map.entry("inboundRouteMap", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/routeMaps/routeMap1")),
                Map.entry("outboundRouteMap", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/routeMaps/routeMap2")),
                Map.entry("propagatedRouteTables", Map.ofEntries(
                    Map.entry("ids", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable1")),
                    Map.entry("labels",                     
                        "label1",
                        "label2")
                )),
                Map.entry("vnetRoutes", Map.ofEntries(
                    Map.entry("staticRoutes",                     
                        Map.ofEntries(
                            Map.entry("addressPrefixes",                             
                                "10.1.0.0/16",
                                "10.2.0.0/16"),
                            Map.entry("name", "route1"),
                            Map.entry("nextHopIpAddress", "10.0.0.68")
                        ),
                        Map.ofEntries(
                            Map.entry("addressPrefixes",                             
                                "10.3.0.0/16",
                                "10.4.0.0/16"),
                            Map.entry("name", "route2"),
                            Map.entry("nextHopIpAddress", "10.0.0.65")
                        )),
                    Map.entry("staticRoutesConfig", Map.of("vnetLocalRouteOverrideCriteria", "Equal"))
                ))
            ))
            .virtualHubName("virtualHub1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const hubVirtualNetworkConnection = new azure_native.network.HubVirtualNetworkConnection("hubVirtualNetworkConnection", {
    connectionName: "connection1",
    enableInternetSecurity: false,
    remoteVirtualNetwork: {
        id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/SpokeVnet1",
    },
    resourceGroupName: "rg1",
    routingConfiguration: {
        associatedRouteTable: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable1",
        },
        inboundRouteMap: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/routeMaps/routeMap1",
        },
        outboundRouteMap: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/routeMaps/routeMap2",
        },
        propagatedRouteTables: {
            ids: [{
                id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable1",
            }],
            labels: [
                "label1",
                "label2",
            ],
        },
        vnetRoutes: {
            staticRoutes: [
                {
                    addressPrefixes: [
                        "10.1.0.0/16",
                        "10.2.0.0/16",
                    ],
                    name: "route1",
                    nextHopIpAddress: "10.0.0.68",
                },
                {
                    addressPrefixes: [
                        "10.3.0.0/16",
                        "10.4.0.0/16",
                    ],
                    name: "route2",
                    nextHopIpAddress: "10.0.0.65",
                },
            ],
            staticRoutesConfig: {
                vnetLocalRouteOverrideCriteria: "Equal",
            },
        },
    },
    virtualHubName: "virtualHub1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

hub_virtual_network_connection = azure_native.network.HubVirtualNetworkConnection("hubVirtualNetworkConnection",
    connection_name="connection1",
    enable_internet_security=False,
    remote_virtual_network=azure_native.network.SubResourceArgs(
        id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/SpokeVnet1",
    ),
    resource_group_name="rg1",
    routing_configuration=azure_native.network.RoutingConfigurationResponseArgs(
        associated_route_table=azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable1",
        ),
        inbound_route_map=azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/routeMaps/routeMap1",
        ),
        outbound_route_map=azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/routeMaps/routeMap2",
        ),
        propagated_route_tables={
            "ids": [azure_native.network.SubResourceArgs(
                id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable1",
            )],
            "labels": [
                "label1",
                "label2",
            ],
        },
        vnet_routes={
            "staticRoutes": [
                azure_native.network.StaticRouteArgs(
                    address_prefixes=[
                        "10.1.0.0/16",
                        "10.2.0.0/16",
                    ],
                    name="route1",
                    next_hop_ip_address="10.0.0.68",
                ),
                azure_native.network.StaticRouteArgs(
                    address_prefixes=[
                        "10.3.0.0/16",
                        "10.4.0.0/16",
                    ],
                    name="route2",
                    next_hop_ip_address="10.0.0.65",
                ),
            ],
            "staticRoutesConfig": azure_native.network.StaticRoutesConfigArgs(
                vnet_local_route_override_criteria="Equal",
            ),
        },
    ),
    virtual_hub_name="virtualHub1")

```

```yaml
resources:
  hubVirtualNetworkConnection:
    type: azure-native:network:HubVirtualNetworkConnection
    properties:
      connectionName: connection1
      enableInternetSecurity: false
      remoteVirtualNetwork:
        id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/SpokeVnet1
      resourceGroupName: rg1
      routingConfiguration:
        associatedRouteTable:
          id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable1
        inboundRouteMap:
          id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/routeMaps/routeMap1
        outboundRouteMap:
          id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/routeMaps/routeMap2
        propagatedRouteTables:
          ids:
            - id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable1
          labels:
            - label1
            - label2
        vnetRoutes:
          staticRoutes:
            - addressPrefixes:
                - 10.1.0.0/16
                - 10.2.0.0/16
              name: route1
              nextHopIpAddress: 10.0.0.68
            - addressPrefixes:
                - 10.3.0.0/16
                - 10.4.0.0/16
              name: route2
              nextHopIpAddress: 10.0.0.65
          staticRoutesConfig:
            vnetLocalRouteOverrideCriteria: Equal
      virtualHubName: virtualHub1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:HubVirtualNetworkConnection connection1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubVirtualNetworkConnections/connection1 
```
