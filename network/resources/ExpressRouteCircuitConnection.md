Express Route Circuit Connection in an ExpressRouteCircuitPeering resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ExpressRouteCircuitConnectionCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var expressRouteCircuitConnection = new AzureNative.Network.ExpressRouteCircuitConnection("expressRouteCircuitConnection", new()
    {
        AddressPrefix = "10.0.0.0/29",
        AuthorizationKey = "946a1918-b7a2-4917-b43c-8c4cdaee006a",
        CircuitName = "ExpressRouteARMCircuitA",
        ConnectionName = "circuitConnectionUSAUS",
        ExpressRouteCircuitPeering = new AzureNative.Network.Inputs.SubResourceArgs
        {
            Id = "/subscriptions/subid1/resourceGroups/dedharcktinit/providers/Microsoft.Network/expressRouteCircuits/dedharcktlocal/peerings/AzurePrivatePeering",
        },
        Ipv6CircuitConnectionConfig = new AzureNative.Network.Inputs.Ipv6CircuitConnectionConfigArgs
        {
            AddressPrefix = "aa:bb::/125",
        },
        PeerExpressRouteCircuitPeering = new AzureNative.Network.Inputs.SubResourceArgs
        {
            Id = "/subscriptions/subid2/resourceGroups/dedharcktpeer/providers/Microsoft.Network/expressRouteCircuits/dedharcktremote/peerings/AzurePrivatePeering",
        },
        PeeringName = "AzurePrivatePeering",
        ResourceGroupName = "rg1",
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
		_, err := network.NewExpressRouteCircuitConnection(ctx, "expressRouteCircuitConnection", &network.ExpressRouteCircuitConnectionArgs{
			AddressPrefix:    pulumi.String("10.0.0.0/29"),
			AuthorizationKey: pulumi.String("946a1918-b7a2-4917-b43c-8c4cdaee006a"),
			CircuitName:      pulumi.String("ExpressRouteARMCircuitA"),
			ConnectionName:   pulumi.String("circuitConnectionUSAUS"),
			ExpressRouteCircuitPeering: &network.SubResourceArgs{
				Id: pulumi.String("/subscriptions/subid1/resourceGroups/dedharcktinit/providers/Microsoft.Network/expressRouteCircuits/dedharcktlocal/peerings/AzurePrivatePeering"),
			},
			Ipv6CircuitConnectionConfig: &network.Ipv6CircuitConnectionConfigArgs{
				AddressPrefix: pulumi.String("aa:bb::/125"),
			},
			PeerExpressRouteCircuitPeering: &network.SubResourceArgs{
				Id: pulumi.String("/subscriptions/subid2/resourceGroups/dedharcktpeer/providers/Microsoft.Network/expressRouteCircuits/dedharcktremote/peerings/AzurePrivatePeering"),
			},
			PeeringName:       pulumi.String("AzurePrivatePeering"),
			ResourceGroupName: pulumi.String("rg1"),
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
import com.pulumi.azurenative.network.ExpressRouteCircuitConnection;
import com.pulumi.azurenative.network.ExpressRouteCircuitConnectionArgs;
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
        var expressRouteCircuitConnection = new ExpressRouteCircuitConnection("expressRouteCircuitConnection", ExpressRouteCircuitConnectionArgs.builder()        
            .addressPrefix("10.0.0.0/29")
            .authorizationKey("946a1918-b7a2-4917-b43c-8c4cdaee006a")
            .circuitName("ExpressRouteARMCircuitA")
            .connectionName("circuitConnectionUSAUS")
            .expressRouteCircuitPeering(Map.of("id", "/subscriptions/subid1/resourceGroups/dedharcktinit/providers/Microsoft.Network/expressRouteCircuits/dedharcktlocal/peerings/AzurePrivatePeering"))
            .ipv6CircuitConnectionConfig(Map.of("addressPrefix", "aa:bb::/125"))
            .peerExpressRouteCircuitPeering(Map.of("id", "/subscriptions/subid2/resourceGroups/dedharcktpeer/providers/Microsoft.Network/expressRouteCircuits/dedharcktremote/peerings/AzurePrivatePeering"))
            .peeringName("AzurePrivatePeering")
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const expressRouteCircuitConnection = new azure_native.network.ExpressRouteCircuitConnection("expressRouteCircuitConnection", {
    addressPrefix: "10.0.0.0/29",
    authorizationKey: "946a1918-b7a2-4917-b43c-8c4cdaee006a",
    circuitName: "ExpressRouteARMCircuitA",
    connectionName: "circuitConnectionUSAUS",
    expressRouteCircuitPeering: {
        id: "/subscriptions/subid1/resourceGroups/dedharcktinit/providers/Microsoft.Network/expressRouteCircuits/dedharcktlocal/peerings/AzurePrivatePeering",
    },
    ipv6CircuitConnectionConfig: {
        addressPrefix: "aa:bb::/125",
    },
    peerExpressRouteCircuitPeering: {
        id: "/subscriptions/subid2/resourceGroups/dedharcktpeer/providers/Microsoft.Network/expressRouteCircuits/dedharcktremote/peerings/AzurePrivatePeering",
    },
    peeringName: "AzurePrivatePeering",
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

express_route_circuit_connection = azure_native.network.ExpressRouteCircuitConnection("expressRouteCircuitConnection",
    address_prefix="10.0.0.0/29",
    authorization_key="946a1918-b7a2-4917-b43c-8c4cdaee006a",
    circuit_name="ExpressRouteARMCircuitA",
    connection_name="circuitConnectionUSAUS",
    express_route_circuit_peering=azure_native.network.SubResourceArgs(
        id="/subscriptions/subid1/resourceGroups/dedharcktinit/providers/Microsoft.Network/expressRouteCircuits/dedharcktlocal/peerings/AzurePrivatePeering",
    ),
    ipv6_circuit_connection_config=azure_native.network.Ipv6CircuitConnectionConfigArgs(
        address_prefix="aa:bb::/125",
    ),
    peer_express_route_circuit_peering=azure_native.network.SubResourceArgs(
        id="/subscriptions/subid2/resourceGroups/dedharcktpeer/providers/Microsoft.Network/expressRouteCircuits/dedharcktremote/peerings/AzurePrivatePeering",
    ),
    peering_name="AzurePrivatePeering",
    resource_group_name="rg1")

```

```yaml
resources:
  expressRouteCircuitConnection:
    type: azure-native:network:ExpressRouteCircuitConnection
    properties:
      addressPrefix: 10.0.0.0/29
      authorizationKey: 946a1918-b7a2-4917-b43c-8c4cdaee006a
      circuitName: ExpressRouteARMCircuitA
      connectionName: circuitConnectionUSAUS
      expressRouteCircuitPeering:
        id: /subscriptions/subid1/resourceGroups/dedharcktinit/providers/Microsoft.Network/expressRouteCircuits/dedharcktlocal/peerings/AzurePrivatePeering
      ipv6CircuitConnectionConfig:
        addressPrefix: aa:bb::/125
      peerExpressRouteCircuitPeering:
        id: /subscriptions/subid2/resourceGroups/dedharcktpeer/providers/Microsoft.Network/expressRouteCircuits/dedharcktremote/peerings/AzurePrivatePeering
      peeringName: AzurePrivatePeering
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:ExpressRouteCircuitConnection circuitConnectionUSAUS /subscriptions/subid1/resourceGroups/dedharcktinit/providers/Microsoft.Network/expressRouteCircuits/ExpressRouteARMCircuitA/peerings/AzurePrivatePeering/connections/circuitConnectionUSAUS 
```
