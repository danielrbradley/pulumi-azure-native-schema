Peering in an ExpressRouteCircuit resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create ExpressRouteCircuit Peerings
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var expressRouteCircuitPeering = new AzureNative.Network.ExpressRouteCircuitPeering("expressRouteCircuitPeering", new()
    {
        CircuitName = "circuitName",
        PeerASN = 200,
        PeeringName = "AzurePrivatePeering",
        PrimaryPeerAddressPrefix = "192.168.16.252/30",
        ResourceGroupName = "rg1",
        SecondaryPeerAddressPrefix = "192.168.18.252/30",
        VlanId = 200,
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
		_, err := network.NewExpressRouteCircuitPeering(ctx, "expressRouteCircuitPeering", &network.ExpressRouteCircuitPeeringArgs{
			CircuitName:                pulumi.String("circuitName"),
			PeerASN:                    pulumi.Float64(200),
			PeeringName:                pulumi.String("AzurePrivatePeering"),
			PrimaryPeerAddressPrefix:   pulumi.String("192.168.16.252/30"),
			ResourceGroupName:          pulumi.String("rg1"),
			SecondaryPeerAddressPrefix: pulumi.String("192.168.18.252/30"),
			VlanId:                     pulumi.Int(200),
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
import com.pulumi.azurenative.network.ExpressRouteCircuitPeering;
import com.pulumi.azurenative.network.ExpressRouteCircuitPeeringArgs;
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
        var expressRouteCircuitPeering = new ExpressRouteCircuitPeering("expressRouteCircuitPeering", ExpressRouteCircuitPeeringArgs.builder()        
            .circuitName("circuitName")
            .peerASN(200)
            .peeringName("AzurePrivatePeering")
            .primaryPeerAddressPrefix("192.168.16.252/30")
            .resourceGroupName("rg1")
            .secondaryPeerAddressPrefix("192.168.18.252/30")
            .vlanId(200)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const expressRouteCircuitPeering = new azure_native.network.ExpressRouteCircuitPeering("expressRouteCircuitPeering", {
    circuitName: "circuitName",
    peerASN: 200,
    peeringName: "AzurePrivatePeering",
    primaryPeerAddressPrefix: "192.168.16.252/30",
    resourceGroupName: "rg1",
    secondaryPeerAddressPrefix: "192.168.18.252/30",
    vlanId: 200,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

express_route_circuit_peering = azure_native.network.ExpressRouteCircuitPeering("expressRouteCircuitPeering",
    circuit_name="circuitName",
    peer_asn=200,
    peering_name="AzurePrivatePeering",
    primary_peer_address_prefix="192.168.16.252/30",
    resource_group_name="rg1",
    secondary_peer_address_prefix="192.168.18.252/30",
    vlan_id=200)

```

```yaml
resources:
  expressRouteCircuitPeering:
    type: azure-native:network:ExpressRouteCircuitPeering
    properties:
      circuitName: circuitName
      peerASN: 200
      peeringName: AzurePrivatePeering
      primaryPeerAddressPrefix: 192.168.16.252/30
      resourceGroupName: rg1
      secondaryPeerAddressPrefix: 192.168.18.252/30
      vlanId: 200

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:ExpressRouteCircuitPeering AzurePrivatePeering /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/expressRouteCircuits/circuitName/peerings/AzurePrivatePeering 
```
