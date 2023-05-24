NetworkVirtualApplianceConnection resource.
API Version: 2022-11-01.

{{% examples %}}
## Example Usage
{{% example %}}
### NetworkVirtualApplianceConnectionPut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var networkVirtualApplianceConnection = new AzureNative.Network.NetworkVirtualApplianceConnection("networkVirtualApplianceConnection", new()
    {
        Asn = 64512,
        BgpPeerAddress = new[]
        {
            "169.254.16.13",
            "169.254.16.14",
        },
        ConnectionName = "connection1",
        EnableInternetSecurity = false,
        Name = "connection1",
        NetworkVirtualApplianceName = "nva1",
        ResourceGroupName = "rg1",
        RoutingConfiguration = new AzureNative.Network.Inputs.RoutingConfigurationNfvArgs
        {
            AssociatedRouteTable = new AzureNative.Network.Inputs.RoutingConfigurationNfvSubResourceArgs
            {
                ResourceUri = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable1",
            },
            InboundRouteMap = new AzureNative.Network.Inputs.RoutingConfigurationNfvSubResourceArgs
            {
                ResourceUri = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/routeMaps/routeMap1",
            },
            OutboundRouteMap = new AzureNative.Network.Inputs.RoutingConfigurationNfvSubResourceArgs
            {
                ResourceUri = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/routeMaps/routeMap2",
            },
            PropagatedRouteTables = new AzureNative.Network.Inputs.PropagatedRouteTableNfvArgs
            {
                Ids = new[]
                {
                    new AzureNative.Network.Inputs.RoutingConfigurationNfvSubResourceArgs
                    {
                        ResourceUri = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable1",
                    },
                },
                Labels = new[]
                {
                    "label1",
                },
            },
        },
        TunnelIdentifier = 0,
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.network.NetworkVirtualApplianceConnection;
import com.pulumi.azurenative.network.NetworkVirtualApplianceConnectionArgs;
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
        var networkVirtualApplianceConnection = new NetworkVirtualApplianceConnection("networkVirtualApplianceConnection", NetworkVirtualApplianceConnectionArgs.builder()        
            .asn(64512)
            .bgpPeerAddress(            
                "169.254.16.13",
                "169.254.16.14")
            .connectionName("connection1")
            .enableInternetSecurity(false)
            .name("connection1")
            .networkVirtualApplianceName("nva1")
            .resourceGroupName("rg1")
            .routingConfiguration(Map.ofEntries(
                Map.entry("associatedRouteTable", Map.of("resourceUri", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable1")),
                Map.entry("inboundRouteMap", Map.of("resourceUri", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/routeMaps/routeMap1")),
                Map.entry("outboundRouteMap", Map.of("resourceUri", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/routeMaps/routeMap2")),
                Map.entry("propagatedRouteTables", Map.ofEntries(
                    Map.entry("ids", Map.of("resourceUri", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable1")),
                    Map.entry("labels", "label1")
                ))
            ))
            .tunnelIdentifier(0)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const networkVirtualApplianceConnection = new azure_native.network.NetworkVirtualApplianceConnection("networkVirtualApplianceConnection", {
    asn: 64512,
    bgpPeerAddress: [
        "169.254.16.13",
        "169.254.16.14",
    ],
    connectionName: "connection1",
    enableInternetSecurity: false,
    name: "connection1",
    networkVirtualApplianceName: "nva1",
    resourceGroupName: "rg1",
    routingConfiguration: {
        associatedRouteTable: {
            resourceUri: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable1",
        },
        inboundRouteMap: {
            resourceUri: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/routeMaps/routeMap1",
        },
        outboundRouteMap: {
            resourceUri: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/routeMaps/routeMap2",
        },
        propagatedRouteTables: {
            ids: [{
                resourceUri: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable1",
            }],
            labels: ["label1"],
        },
    },
    tunnelIdentifier: 0,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

network_virtual_appliance_connection = azure_native.network.NetworkVirtualApplianceConnection("networkVirtualApplianceConnection",
    asn=64512,
    bgp_peer_address=[
        "169.254.16.13",
        "169.254.16.14",
    ],
    connection_name="connection1",
    enable_internet_security=False,
    name="connection1",
    network_virtual_appliance_name="nva1",
    resource_group_name="rg1",
    routing_configuration=azure_native.network.RoutingConfigurationNfvResponseArgs(
        associated_route_table=azure_native.network.RoutingConfigurationNfvSubResourceArgs(
            resource_uri="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable1",
        ),
        inbound_route_map=azure_native.network.RoutingConfigurationNfvSubResourceArgs(
            resource_uri="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/routeMaps/routeMap1",
        ),
        outbound_route_map=azure_native.network.RoutingConfigurationNfvSubResourceArgs(
            resource_uri="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/routeMaps/routeMap2",
        ),
        propagated_route_tables={
            "ids": [azure_native.network.RoutingConfigurationNfvSubResourceArgs(
                resource_uri="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable1",
            )],
            "labels": ["label1"],
        },
    ),
    tunnel_identifier=0)

```

```yaml
resources:
  networkVirtualApplianceConnection:
    type: azure-native:network:NetworkVirtualApplianceConnection
    properties:
      asn: 64512
      bgpPeerAddress:
        - 169.254.16.13
        - 169.254.16.14
      connectionName: connection1
      enableInternetSecurity: false
      name: connection1
      networkVirtualApplianceName: nva1
      resourceGroupName: rg1
      routingConfiguration:
        associatedRouteTable:
          resourceUri: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable1
        inboundRouteMap:
          resourceUri: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/routeMaps/routeMap1
        outboundRouteMap:
          resourceUri: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/routeMaps/routeMap2
        propagatedRouteTables:
          ids:
            - resourceUri: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/hubRouteTables/hubRouteTable1
          labels:
            - label1
      tunnelIdentifier: 0

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:NetworkVirtualApplianceConnection connection1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/networkVirtualAppliances/nva1/networkVirtualApplianceConnections/connection1 
```
