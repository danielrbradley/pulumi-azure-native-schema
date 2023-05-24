Peerings in a virtual network resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create peering
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualNetworkPeering = new AzureNative.Network.VirtualNetworkPeering("virtualNetworkPeering", new()
    {
        AllowForwardedTraffic = true,
        AllowGatewayTransit = false,
        AllowVirtualNetworkAccess = true,
        RemoteVirtualNetwork = new AzureNative.Network.Inputs.SubResourceArgs
        {
            Id = "/subscriptions/subid/resourceGroups/peerTest/providers/Microsoft.Network/virtualNetworks/vnet2",
        },
        ResourceGroupName = "peerTest",
        UseRemoteGateways = false,
        VirtualNetworkName = "vnet1",
        VirtualNetworkPeeringName = "peer",
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
		_, err := network.NewVirtualNetworkPeering(ctx, "virtualNetworkPeering", &network.VirtualNetworkPeeringArgs{
			AllowForwardedTraffic:     pulumi.Bool(true),
			AllowGatewayTransit:       pulumi.Bool(false),
			AllowVirtualNetworkAccess: pulumi.Bool(true),
			RemoteVirtualNetwork: &network.SubResourceArgs{
				Id: pulumi.String("/subscriptions/subid/resourceGroups/peerTest/providers/Microsoft.Network/virtualNetworks/vnet2"),
			},
			ResourceGroupName:         pulumi.String("peerTest"),
			UseRemoteGateways:         pulumi.Bool(false),
			VirtualNetworkName:        pulumi.String("vnet1"),
			VirtualNetworkPeeringName: pulumi.String("peer"),
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
import com.pulumi.azurenative.network.VirtualNetworkPeering;
import com.pulumi.azurenative.network.VirtualNetworkPeeringArgs;
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
        var virtualNetworkPeering = new VirtualNetworkPeering("virtualNetworkPeering", VirtualNetworkPeeringArgs.builder()        
            .allowForwardedTraffic(true)
            .allowGatewayTransit(false)
            .allowVirtualNetworkAccess(true)
            .remoteVirtualNetwork(Map.of("id", "/subscriptions/subid/resourceGroups/peerTest/providers/Microsoft.Network/virtualNetworks/vnet2"))
            .resourceGroupName("peerTest")
            .useRemoteGateways(false)
            .virtualNetworkName("vnet1")
            .virtualNetworkPeeringName("peer")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualNetworkPeering = new azure_native.network.VirtualNetworkPeering("virtualNetworkPeering", {
    allowForwardedTraffic: true,
    allowGatewayTransit: false,
    allowVirtualNetworkAccess: true,
    remoteVirtualNetwork: {
        id: "/subscriptions/subid/resourceGroups/peerTest/providers/Microsoft.Network/virtualNetworks/vnet2",
    },
    resourceGroupName: "peerTest",
    useRemoteGateways: false,
    virtualNetworkName: "vnet1",
    virtualNetworkPeeringName: "peer",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_network_peering = azure_native.network.VirtualNetworkPeering("virtualNetworkPeering",
    allow_forwarded_traffic=True,
    allow_gateway_transit=False,
    allow_virtual_network_access=True,
    remote_virtual_network=azure_native.network.SubResourceArgs(
        id="/subscriptions/subid/resourceGroups/peerTest/providers/Microsoft.Network/virtualNetworks/vnet2",
    ),
    resource_group_name="peerTest",
    use_remote_gateways=False,
    virtual_network_name="vnet1",
    virtual_network_peering_name="peer")

```

```yaml
resources:
  virtualNetworkPeering:
    type: azure-native:network:VirtualNetworkPeering
    properties:
      allowForwardedTraffic: true
      allowGatewayTransit: false
      allowVirtualNetworkAccess: true
      remoteVirtualNetwork:
        id: /subscriptions/subid/resourceGroups/peerTest/providers/Microsoft.Network/virtualNetworks/vnet2
      resourceGroupName: peerTest
      useRemoteGateways: false
      virtualNetworkName: vnet1
      virtualNetworkPeeringName: peer

```

{{% /example %}}
{{% example %}}
### Create peering with remote virtual network encryption
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualNetworkPeering = new AzureNative.Network.VirtualNetworkPeering("virtualNetworkPeering", new()
    {
        AllowForwardedTraffic = true,
        AllowGatewayTransit = false,
        AllowVirtualNetworkAccess = true,
        RemoteVirtualNetwork = new AzureNative.Network.Inputs.SubResourceArgs
        {
            Id = "/subscriptions/subid/resourceGroups/peerTest/providers/Microsoft.Network/virtualNetworks/vnet2",
        },
        ResourceGroupName = "peerTest",
        UseRemoteGateways = false,
        VirtualNetworkName = "vnet1",
        VirtualNetworkPeeringName = "peer",
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
		_, err := network.NewVirtualNetworkPeering(ctx, "virtualNetworkPeering", &network.VirtualNetworkPeeringArgs{
			AllowForwardedTraffic:     pulumi.Bool(true),
			AllowGatewayTransit:       pulumi.Bool(false),
			AllowVirtualNetworkAccess: pulumi.Bool(true),
			RemoteVirtualNetwork: &network.SubResourceArgs{
				Id: pulumi.String("/subscriptions/subid/resourceGroups/peerTest/providers/Microsoft.Network/virtualNetworks/vnet2"),
			},
			ResourceGroupName:         pulumi.String("peerTest"),
			UseRemoteGateways:         pulumi.Bool(false),
			VirtualNetworkName:        pulumi.String("vnet1"),
			VirtualNetworkPeeringName: pulumi.String("peer"),
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
import com.pulumi.azurenative.network.VirtualNetworkPeering;
import com.pulumi.azurenative.network.VirtualNetworkPeeringArgs;
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
        var virtualNetworkPeering = new VirtualNetworkPeering("virtualNetworkPeering", VirtualNetworkPeeringArgs.builder()        
            .allowForwardedTraffic(true)
            .allowGatewayTransit(false)
            .allowVirtualNetworkAccess(true)
            .remoteVirtualNetwork(Map.of("id", "/subscriptions/subid/resourceGroups/peerTest/providers/Microsoft.Network/virtualNetworks/vnet2"))
            .resourceGroupName("peerTest")
            .useRemoteGateways(false)
            .virtualNetworkName("vnet1")
            .virtualNetworkPeeringName("peer")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualNetworkPeering = new azure_native.network.VirtualNetworkPeering("virtualNetworkPeering", {
    allowForwardedTraffic: true,
    allowGatewayTransit: false,
    allowVirtualNetworkAccess: true,
    remoteVirtualNetwork: {
        id: "/subscriptions/subid/resourceGroups/peerTest/providers/Microsoft.Network/virtualNetworks/vnet2",
    },
    resourceGroupName: "peerTest",
    useRemoteGateways: false,
    virtualNetworkName: "vnet1",
    virtualNetworkPeeringName: "peer",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_network_peering = azure_native.network.VirtualNetworkPeering("virtualNetworkPeering",
    allow_forwarded_traffic=True,
    allow_gateway_transit=False,
    allow_virtual_network_access=True,
    remote_virtual_network=azure_native.network.SubResourceArgs(
        id="/subscriptions/subid/resourceGroups/peerTest/providers/Microsoft.Network/virtualNetworks/vnet2",
    ),
    resource_group_name="peerTest",
    use_remote_gateways=False,
    virtual_network_name="vnet1",
    virtual_network_peering_name="peer")

```

```yaml
resources:
  virtualNetworkPeering:
    type: azure-native:network:VirtualNetworkPeering
    properties:
      allowForwardedTraffic: true
      allowGatewayTransit: false
      allowVirtualNetworkAccess: true
      remoteVirtualNetwork:
        id: /subscriptions/subid/resourceGroups/peerTest/providers/Microsoft.Network/virtualNetworks/vnet2
      resourceGroupName: peerTest
      useRemoteGateways: false
      virtualNetworkName: vnet1
      virtualNetworkPeeringName: peer

```

{{% /example %}}
{{% example %}}
### Sync Peering
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualNetworkPeering = new AzureNative.Network.VirtualNetworkPeering("virtualNetworkPeering", new()
    {
        AllowForwardedTraffic = true,
        AllowGatewayTransit = false,
        AllowVirtualNetworkAccess = true,
        RemoteVirtualNetwork = new AzureNative.Network.Inputs.SubResourceArgs
        {
            Id = "/subscriptions/subid/resourceGroups/peerTest/providers/Microsoft.Network/virtualNetworks/vnet2",
        },
        ResourceGroupName = "peerTest",
        SyncRemoteAddressSpace = "true",
        UseRemoteGateways = false,
        VirtualNetworkName = "vnet1",
        VirtualNetworkPeeringName = "peer",
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
		_, err := network.NewVirtualNetworkPeering(ctx, "virtualNetworkPeering", &network.VirtualNetworkPeeringArgs{
			AllowForwardedTraffic:     pulumi.Bool(true),
			AllowGatewayTransit:       pulumi.Bool(false),
			AllowVirtualNetworkAccess: pulumi.Bool(true),
			RemoteVirtualNetwork: &network.SubResourceArgs{
				Id: pulumi.String("/subscriptions/subid/resourceGroups/peerTest/providers/Microsoft.Network/virtualNetworks/vnet2"),
			},
			ResourceGroupName:         pulumi.String("peerTest"),
			SyncRemoteAddressSpace:    pulumi.String("true"),
			UseRemoteGateways:         pulumi.Bool(false),
			VirtualNetworkName:        pulumi.String("vnet1"),
			VirtualNetworkPeeringName: pulumi.String("peer"),
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
import com.pulumi.azurenative.network.VirtualNetworkPeering;
import com.pulumi.azurenative.network.VirtualNetworkPeeringArgs;
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
        var virtualNetworkPeering = new VirtualNetworkPeering("virtualNetworkPeering", VirtualNetworkPeeringArgs.builder()        
            .allowForwardedTraffic(true)
            .allowGatewayTransit(false)
            .allowVirtualNetworkAccess(true)
            .remoteVirtualNetwork(Map.of("id", "/subscriptions/subid/resourceGroups/peerTest/providers/Microsoft.Network/virtualNetworks/vnet2"))
            .resourceGroupName("peerTest")
            .syncRemoteAddressSpace("true")
            .useRemoteGateways(false)
            .virtualNetworkName("vnet1")
            .virtualNetworkPeeringName("peer")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualNetworkPeering = new azure_native.network.VirtualNetworkPeering("virtualNetworkPeering", {
    allowForwardedTraffic: true,
    allowGatewayTransit: false,
    allowVirtualNetworkAccess: true,
    remoteVirtualNetwork: {
        id: "/subscriptions/subid/resourceGroups/peerTest/providers/Microsoft.Network/virtualNetworks/vnet2",
    },
    resourceGroupName: "peerTest",
    syncRemoteAddressSpace: "true",
    useRemoteGateways: false,
    virtualNetworkName: "vnet1",
    virtualNetworkPeeringName: "peer",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_network_peering = azure_native.network.VirtualNetworkPeering("virtualNetworkPeering",
    allow_forwarded_traffic=True,
    allow_gateway_transit=False,
    allow_virtual_network_access=True,
    remote_virtual_network=azure_native.network.SubResourceArgs(
        id="/subscriptions/subid/resourceGroups/peerTest/providers/Microsoft.Network/virtualNetworks/vnet2",
    ),
    resource_group_name="peerTest",
    sync_remote_address_space="true",
    use_remote_gateways=False,
    virtual_network_name="vnet1",
    virtual_network_peering_name="peer")

```

```yaml
resources:
  virtualNetworkPeering:
    type: azure-native:network:VirtualNetworkPeering
    properties:
      allowForwardedTraffic: true
      allowGatewayTransit: false
      allowVirtualNetworkAccess: true
      remoteVirtualNetwork:
        id: /subscriptions/subid/resourceGroups/peerTest/providers/Microsoft.Network/virtualNetworks/vnet2
      resourceGroupName: peerTest
      syncRemoteAddressSpace: 'true'
      useRemoteGateways: false
      virtualNetworkName: vnet1
      virtualNetworkPeeringName: peer

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:VirtualNetworkPeering peer /subscriptions/subid/resourceGroups/peerTest/providers/Microsoft.Network/virtualNetworks/vnet1/virtualNetworkPeerings/peer 
```
