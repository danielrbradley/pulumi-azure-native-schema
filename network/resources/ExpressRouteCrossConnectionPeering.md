Peering in an ExpressRoute Cross Connection resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ExpressRouteCrossConnectionBgpPeeringCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var expressRouteCrossConnectionPeering = new AzureNative.Network.ExpressRouteCrossConnectionPeering("expressRouteCrossConnectionPeering", new()
    {
        CrossConnectionName = "<circuitServiceKey>",
        Ipv6PeeringConfig = new AzureNative.Network.Inputs.Ipv6ExpressRouteCircuitPeeringConfigArgs
        {
            PrimaryPeerAddressPrefix = "3FFE:FFFF:0:CD30::/126",
            SecondaryPeerAddressPrefix = "3FFE:FFFF:0:CD30::4/126",
        },
        PeerASN = 200,
        PeeringName = "AzurePrivatePeering",
        PrimaryPeerAddressPrefix = "192.168.16.252/30",
        ResourceGroupName = "CrossConnection-SiliconValley",
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
		_, err := network.NewExpressRouteCrossConnectionPeering(ctx, "expressRouteCrossConnectionPeering", &network.ExpressRouteCrossConnectionPeeringArgs{
			CrossConnectionName: pulumi.String("<circuitServiceKey>"),
			Ipv6PeeringConfig: &network.Ipv6ExpressRouteCircuitPeeringConfigArgs{
				PrimaryPeerAddressPrefix:   pulumi.String("3FFE:FFFF:0:CD30::/126"),
				SecondaryPeerAddressPrefix: pulumi.String("3FFE:FFFF:0:CD30::4/126"),
			},
			PeerASN:                    pulumi.Float64(200),
			PeeringName:                pulumi.String("AzurePrivatePeering"),
			PrimaryPeerAddressPrefix:   pulumi.String("192.168.16.252/30"),
			ResourceGroupName:          pulumi.String("CrossConnection-SiliconValley"),
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
import com.pulumi.azurenative.network.ExpressRouteCrossConnectionPeering;
import com.pulumi.azurenative.network.ExpressRouteCrossConnectionPeeringArgs;
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
        var expressRouteCrossConnectionPeering = new ExpressRouteCrossConnectionPeering("expressRouteCrossConnectionPeering", ExpressRouteCrossConnectionPeeringArgs.builder()        
            .crossConnectionName("<circuitServiceKey>")
            .ipv6PeeringConfig(Map.ofEntries(
                Map.entry("primaryPeerAddressPrefix", "3FFE:FFFF:0:CD30::/126"),
                Map.entry("secondaryPeerAddressPrefix", "3FFE:FFFF:0:CD30::4/126")
            ))
            .peerASN(200)
            .peeringName("AzurePrivatePeering")
            .primaryPeerAddressPrefix("192.168.16.252/30")
            .resourceGroupName("CrossConnection-SiliconValley")
            .secondaryPeerAddressPrefix("192.168.18.252/30")
            .vlanId(200)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const expressRouteCrossConnectionPeering = new azure_native.network.ExpressRouteCrossConnectionPeering("expressRouteCrossConnectionPeering", {
    crossConnectionName: "<circuitServiceKey>",
    ipv6PeeringConfig: {
        primaryPeerAddressPrefix: "3FFE:FFFF:0:CD30::/126",
        secondaryPeerAddressPrefix: "3FFE:FFFF:0:CD30::4/126",
    },
    peerASN: 200,
    peeringName: "AzurePrivatePeering",
    primaryPeerAddressPrefix: "192.168.16.252/30",
    resourceGroupName: "CrossConnection-SiliconValley",
    secondaryPeerAddressPrefix: "192.168.18.252/30",
    vlanId: 200,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

express_route_cross_connection_peering = azure_native.network.ExpressRouteCrossConnectionPeering("expressRouteCrossConnectionPeering",
    cross_connection_name="<circuitServiceKey>",
    ipv6_peering_config=azure_native.network.Ipv6ExpressRouteCircuitPeeringConfigArgs(
        primary_peer_address_prefix="3FFE:FFFF:0:CD30::/126",
        secondary_peer_address_prefix="3FFE:FFFF:0:CD30::4/126",
    ),
    peer_asn=200,
    peering_name="AzurePrivatePeering",
    primary_peer_address_prefix="192.168.16.252/30",
    resource_group_name="CrossConnection-SiliconValley",
    secondary_peer_address_prefix="192.168.18.252/30",
    vlan_id=200)

```

```yaml
resources:
  expressRouteCrossConnectionPeering:
    type: azure-native:network:ExpressRouteCrossConnectionPeering
    properties:
      crossConnectionName: <circuitServiceKey>
      ipv6PeeringConfig:
        primaryPeerAddressPrefix: 3FFE:FFFF:0:CD30::/126
        secondaryPeerAddressPrefix: 3FFE:FFFF:0:CD30::4/126
      peerASN: 200
      peeringName: AzurePrivatePeering
      primaryPeerAddressPrefix: 192.168.16.252/30
      resourceGroupName: CrossConnection-SiliconValley
      secondaryPeerAddressPrefix: 192.168.18.252/30
      vlanId: 200

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:ExpressRouteCrossConnectionPeering AzurePrivatePeering /subscriptions/subid/resourceGroups/CrossConnection-Boydton1DC/providers/Microsoft.Network/expressRouteCrossConnections/<circuitServiceKey>/peerings/AzurePrivatePeering 
```
