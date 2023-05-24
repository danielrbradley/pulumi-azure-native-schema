Virtual Appliance Site resource.
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
    var virtualHubBgpConnection = new AzureNative.Network.VirtualHubBgpConnection("virtualHubBgpConnection", new()
    {
        ConnectionName = "conn1",
        HubVirtualNetworkConnection = new AzureNative.Network.Inputs.SubResourceArgs
        {
            Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1/hubVirtualNetworkConnections/hubVnetConn1",
        },
        PeerAsn = 20000,
        PeerIp = "192.168.1.5",
        ResourceGroupName = "rg1",
        VirtualHubName = "hub1",
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
		_, err := network.NewVirtualHubBgpConnection(ctx, "virtualHubBgpConnection", &network.VirtualHubBgpConnectionArgs{
			ConnectionName: pulumi.String("conn1"),
			HubVirtualNetworkConnection: &network.SubResourceArgs{
				Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1/hubVirtualNetworkConnections/hubVnetConn1"),
			},
			PeerAsn:           pulumi.Float64(20000),
			PeerIp:            pulumi.String("192.168.1.5"),
			ResourceGroupName: pulumi.String("rg1"),
			VirtualHubName:    pulumi.String("hub1"),
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
import com.pulumi.azurenative.network.VirtualHubBgpConnection;
import com.pulumi.azurenative.network.VirtualHubBgpConnectionArgs;
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
        var virtualHubBgpConnection = new VirtualHubBgpConnection("virtualHubBgpConnection", VirtualHubBgpConnectionArgs.builder()        
            .connectionName("conn1")
            .hubVirtualNetworkConnection(Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1/hubVirtualNetworkConnections/hubVnetConn1"))
            .peerAsn(20000)
            .peerIp("192.168.1.5")
            .resourceGroupName("rg1")
            .virtualHubName("hub1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualHubBgpConnection = new azure_native.network.VirtualHubBgpConnection("virtualHubBgpConnection", {
    connectionName: "conn1",
    hubVirtualNetworkConnection: {
        id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1/hubVirtualNetworkConnections/hubVnetConn1",
    },
    peerAsn: 20000,
    peerIp: "192.168.1.5",
    resourceGroupName: "rg1",
    virtualHubName: "hub1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_hub_bgp_connection = azure_native.network.VirtualHubBgpConnection("virtualHubBgpConnection",
    connection_name="conn1",
    hub_virtual_network_connection=azure_native.network.SubResourceArgs(
        id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1/hubVirtualNetworkConnections/hubVnetConn1",
    ),
    peer_asn=20000,
    peer_ip="192.168.1.5",
    resource_group_name="rg1",
    virtual_hub_name="hub1")

```

```yaml
resources:
  virtualHubBgpConnection:
    type: azure-native:network:VirtualHubBgpConnection
    properties:
      connectionName: conn1
      hubVirtualNetworkConnection:
        id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1/hubVirtualNetworkConnections/hubVnetConn1
      peerAsn: 20000
      peerIp: 192.168.1.5
      resourceGroupName: rg1
      virtualHubName: hub1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:VirtualHubBgpConnection conn1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1/bgpConnections/conn1 
```
