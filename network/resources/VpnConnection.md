VpnConnection Resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### VpnConnectionPut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var vpnConnection = new AzureNative.Network.VpnConnection("vpnConnection", new()
    {
        ConnectionName = "vpnConnection1",
        GatewayName = "gateway1",
        RemoteVpnSite = new AzureNative.Network.Inputs.SubResourceArgs
        {
            Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnSites/vpnSite1",
        },
        ResourceGroupName = "rg1",
        RoutingConfiguration = new AzureNative.Network.Inputs.RoutingConfigurationArgs
        {
            AssociatedRouteTable = new AzureNative.Network.Inputs.SubResourceArgs
            {
                Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable1",
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
                        Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable1",
                    },
                    new AzureNative.Network.Inputs.SubResourceArgs
                    {
                        Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable2",
                    },
                    new AzureNative.Network.Inputs.SubResourceArgs
                    {
                        Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable3",
                    },
                },
                Labels = new[]
                {
                    "label1",
                    "label2",
                },
            },
        },
        TrafficSelectorPolicies = new[] {},
        VpnLinkConnections = new[]
        {
            new AzureNative.Network.Inputs.VpnSiteLinkConnectionArgs
            {
                ConnectionBandwidth = 200,
                Name = "Connection-Link1",
                SharedKey = "key",
                UsePolicyBasedTrafficSelectors = false,
                VpnConnectionProtocolType = "IKEv2",
                VpnLinkConnectionMode = "Default",
                VpnSiteLink = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnSites/vpnSite1/vpnSiteLinks/siteLink1",
                },
            },
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.network.VpnConnection;
import com.pulumi.azurenative.network.VpnConnectionArgs;
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
        var vpnConnection = new VpnConnection("vpnConnection", VpnConnectionArgs.builder()        
            .connectionName("vpnConnection1")
            .gatewayName("gateway1")
            .remoteVpnSite(Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnSites/vpnSite1"))
            .resourceGroupName("rg1")
            .routingConfiguration(Map.ofEntries(
                Map.entry("associatedRouteTable", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable1")),
                Map.entry("inboundRouteMap", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/routeMaps/routeMap1")),
                Map.entry("outboundRouteMap", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/routeMaps/routeMap2")),
                Map.entry("propagatedRouteTables", Map.ofEntries(
                    Map.entry("ids",                     
                        Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable1"),
                        Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable2"),
                        Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable3")),
                    Map.entry("labels",                     
                        "label1",
                        "label2")
                ))
            ))
            .trafficSelectorPolicies()
            .vpnLinkConnections(Map.ofEntries(
                Map.entry("connectionBandwidth", 200),
                Map.entry("name", "Connection-Link1"),
                Map.entry("sharedKey", "key"),
                Map.entry("usePolicyBasedTrafficSelectors", false),
                Map.entry("vpnConnectionProtocolType", "IKEv2"),
                Map.entry("vpnLinkConnectionMode", "Default"),
                Map.entry("vpnSiteLink", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnSites/vpnSite1/vpnSiteLinks/siteLink1"))
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const vpnConnection = new azure_native.network.VpnConnection("vpnConnection", {
    connectionName: "vpnConnection1",
    gatewayName: "gateway1",
    remoteVpnSite: {
        id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnSites/vpnSite1",
    },
    resourceGroupName: "rg1",
    routingConfiguration: {
        associatedRouteTable: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable1",
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
                    id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable1",
                },
                {
                    id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable2",
                },
                {
                    id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable3",
                },
            ],
            labels: [
                "label1",
                "label2",
            ],
        },
    },
    trafficSelectorPolicies: [],
    vpnLinkConnections: [{
        connectionBandwidth: 200,
        name: "Connection-Link1",
        sharedKey: "key",
        usePolicyBasedTrafficSelectors: false,
        vpnConnectionProtocolType: "IKEv2",
        vpnLinkConnectionMode: "Default",
        vpnSiteLink: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnSites/vpnSite1/vpnSiteLinks/siteLink1",
        },
    }],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

vpn_connection = azure_native.network.VpnConnection("vpnConnection",
    connection_name="vpnConnection1",
    gateway_name="gateway1",
    remote_vpn_site=azure_native.network.SubResourceArgs(
        id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnSites/vpnSite1",
    ),
    resource_group_name="rg1",
    routing_configuration=azure_native.network.RoutingConfigurationResponseArgs(
        associated_route_table=azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable1",
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
                    id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable1",
                ),
                azure_native.network.SubResourceArgs(
                    id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable2",
                ),
                azure_native.network.SubResourceArgs(
                    id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable3",
                ),
            ],
            "labels": [
                "label1",
                "label2",
            ],
        },
    ),
    traffic_selector_policies=[],
    vpn_link_connections=[{
        "connectionBandwidth": 200,
        "name": "Connection-Link1",
        "sharedKey": "key",
        "usePolicyBasedTrafficSelectors": False,
        "vpnConnectionProtocolType": "IKEv2",
        "vpnLinkConnectionMode": "Default",
        "vpnSiteLink": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnSites/vpnSite1/vpnSiteLinks/siteLink1",
        ),
    }])

```

```yaml
resources:
  vpnConnection:
    type: azure-native:network:VpnConnection
    properties:
      connectionName: vpnConnection1
      gatewayName: gateway1
      remoteVpnSite:
        id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnSites/vpnSite1
      resourceGroupName: rg1
      routingConfiguration:
        associatedRouteTable:
          id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable1
        inboundRouteMap:
          id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/routeMaps/routeMap1
        outboundRouteMap:
          id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/routeMaps/routeMap2
        propagatedRouteTables:
          ids:
            - id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable1
            - id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable2
            - id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1/hubRouteTables/hubRouteTable3
          labels:
            - label1
            - label2
      trafficSelectorPolicies: []
      vpnLinkConnections:
        - connectionBandwidth: 200
          name: Connection-Link1
          sharedKey: key
          usePolicyBasedTrafficSelectors: false
          vpnConnectionProtocolType: IKEv2
          vpnLinkConnectionMode: Default
          vpnSiteLink:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnSites/vpnSite1/vpnSiteLinks/siteLink1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:VpnConnection vpnConnection1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnGateways/gateway1/vpnConnections/vpnConnection1 
```
