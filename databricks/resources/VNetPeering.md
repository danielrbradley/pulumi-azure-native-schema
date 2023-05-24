Peerings in a VirtualNetwork resource
API Version: 2023-02-01.
Previous API Version: 2018-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create vNet Peering for Workspace
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var vNetPeering = new AzureNative.Databricks.VNetPeering("vNetPeering", new()
    {
        AllowForwardedTraffic = false,
        AllowGatewayTransit = false,
        AllowVirtualNetworkAccess = true,
        PeeringName = "vNetPeeringTest",
        RemoteVirtualNetwork = new AzureNative.Databricks.Inputs.VirtualNetworkPeeringPropertiesFormatRemoteVirtualNetworkArgs
        {
            Id = "/subscriptions/0140911e-1040-48da-8bc9-b99fb3dd88a6/resourceGroups/subramantest/providers/Microsoft.Network/virtualNetworks/subramanvnet",
        },
        ResourceGroupName = "rg",
        UseRemoteGateways = false,
        WorkspaceName = "myWorkspace",
    });

});


```

```go
package main

import (
	databricks "github.com/pulumi/pulumi-azure-native-sdk/databricks"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := databricks.NewVNetPeering(ctx, "vNetPeering", &databricks.VNetPeeringArgs{
			AllowForwardedTraffic:     pulumi.Bool(false),
			AllowGatewayTransit:       pulumi.Bool(false),
			AllowVirtualNetworkAccess: pulumi.Bool(true),
			PeeringName:               pulumi.String("vNetPeeringTest"),
			RemoteVirtualNetwork: &databricks.VirtualNetworkPeeringPropertiesFormatRemoteVirtualNetworkArgs{
				Id: pulumi.String("/subscriptions/0140911e-1040-48da-8bc9-b99fb3dd88a6/resourceGroups/subramantest/providers/Microsoft.Network/virtualNetworks/subramanvnet"),
			},
			ResourceGroupName: pulumi.String("rg"),
			UseRemoteGateways: pulumi.Bool(false),
			WorkspaceName:     pulumi.String("myWorkspace"),
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
import com.pulumi.azurenative.databricks.VNetPeering;
import com.pulumi.azurenative.databricks.VNetPeeringArgs;
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
        var vNetPeering = new VNetPeering("vNetPeering", VNetPeeringArgs.builder()        
            .allowForwardedTraffic(false)
            .allowGatewayTransit(false)
            .allowVirtualNetworkAccess(true)
            .peeringName("vNetPeeringTest")
            .remoteVirtualNetwork(Map.of("id", "/subscriptions/0140911e-1040-48da-8bc9-b99fb3dd88a6/resourceGroups/subramantest/providers/Microsoft.Network/virtualNetworks/subramanvnet"))
            .resourceGroupName("rg")
            .useRemoteGateways(false)
            .workspaceName("myWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const vNetPeering = new azure_native.databricks.VNetPeering("vNetPeering", {
    allowForwardedTraffic: false,
    allowGatewayTransit: false,
    allowVirtualNetworkAccess: true,
    peeringName: "vNetPeeringTest",
    remoteVirtualNetwork: {
        id: "/subscriptions/0140911e-1040-48da-8bc9-b99fb3dd88a6/resourceGroups/subramantest/providers/Microsoft.Network/virtualNetworks/subramanvnet",
    },
    resourceGroupName: "rg",
    useRemoteGateways: false,
    workspaceName: "myWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

v_net_peering = azure_native.databricks.VNetPeering("vNetPeering",
    allow_forwarded_traffic=False,
    allow_gateway_transit=False,
    allow_virtual_network_access=True,
    peering_name="vNetPeeringTest",
    remote_virtual_network=azure_native.databricks.VirtualNetworkPeeringPropertiesFormatRemoteVirtualNetworkArgs(
        id="/subscriptions/0140911e-1040-48da-8bc9-b99fb3dd88a6/resourceGroups/subramantest/providers/Microsoft.Network/virtualNetworks/subramanvnet",
    ),
    resource_group_name="rg",
    use_remote_gateways=False,
    workspace_name="myWorkspace")

```

```yaml
resources:
  vNetPeering:
    type: azure-native:databricks:VNetPeering
    properties:
      allowForwardedTraffic: false
      allowGatewayTransit: false
      allowVirtualNetworkAccess: true
      peeringName: vNetPeeringTest
      remoteVirtualNetwork:
        id: /subscriptions/0140911e-1040-48da-8bc9-b99fb3dd88a6/resourceGroups/subramantest/providers/Microsoft.Network/virtualNetworks/subramanvnet
      resourceGroupName: rg
      useRemoteGateways: false
      workspaceName: myWorkspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:databricks:VNetPeering vNetPeeringTest /subscriptions/0140911e-1040-48da-8bc9-b99fb3dd88a6/resourceGroups/subramantest/providers/Microsoft.Databricks/workspaces/adbworkspace/virtualNetworkPeerings/vNetPeeringTest 
```
