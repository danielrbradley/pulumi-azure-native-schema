Virtual Router Peering resource.
API Version: 2022-09-01.
Previous API Version: 2022-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Virtual Router Peering
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualRouterPeering = new AzureNative.Network.VirtualRouterPeering("virtualRouterPeering", new()
    {
        PeerAsn = 20000,
        PeerIp = "192.168.1.5",
        PeeringName = "peering1",
        ResourceGroupName = "rg1",
        VirtualRouterName = "virtualRouter",
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
		_, err := network.NewVirtualRouterPeering(ctx, "virtualRouterPeering", &network.VirtualRouterPeeringArgs{
			PeerAsn:           pulumi.Float64(20000),
			PeerIp:            pulumi.String("192.168.1.5"),
			PeeringName:       pulumi.String("peering1"),
			ResourceGroupName: pulumi.String("rg1"),
			VirtualRouterName: pulumi.String("virtualRouter"),
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
import com.pulumi.azurenative.network.VirtualRouterPeering;
import com.pulumi.azurenative.network.VirtualRouterPeeringArgs;
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
        var virtualRouterPeering = new VirtualRouterPeering("virtualRouterPeering", VirtualRouterPeeringArgs.builder()        
            .peerAsn(20000)
            .peerIp("192.168.1.5")
            .peeringName("peering1")
            .resourceGroupName("rg1")
            .virtualRouterName("virtualRouter")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualRouterPeering = new azure_native.network.VirtualRouterPeering("virtualRouterPeering", {
    peerAsn: 20000,
    peerIp: "192.168.1.5",
    peeringName: "peering1",
    resourceGroupName: "rg1",
    virtualRouterName: "virtualRouter",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_router_peering = azure_native.network.VirtualRouterPeering("virtualRouterPeering",
    peer_asn=20000,
    peer_ip="192.168.1.5",
    peering_name="peering1",
    resource_group_name="rg1",
    virtual_router_name="virtualRouter")

```

```yaml
resources:
  virtualRouterPeering:
    type: azure-native:network:VirtualRouterPeering
    properties:
      peerAsn: 20000
      peerIp: 192.168.1.5
      peeringName: peering1
      resourceGroupName: rg1
      virtualRouterName: virtualRouter

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:VirtualRouterPeering peering1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualRouters/virtualRouter/peerings/peering1 
```
