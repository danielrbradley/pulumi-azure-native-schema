Tap configuration in a Network Interface.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Network Interface Tap Configurations
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var networkInterfaceTapConfiguration = new AzureNative.Network.NetworkInterfaceTapConfiguration("networkInterfaceTapConfiguration", new()
    {
        NetworkInterfaceName = "mynic",
        ResourceGroupName = "testrg",
        TapConfigurationName = "tapconfiguration1",
        VirtualNetworkTap = new AzureNative.Network.Inputs.VirtualNetworkTapArgs
        {
            Id = "/subscriptions/subid/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworkTaps/testvtap",
        },
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
		_, err := network.NewNetworkInterfaceTapConfiguration(ctx, "networkInterfaceTapConfiguration", &network.NetworkInterfaceTapConfigurationArgs{
			NetworkInterfaceName: pulumi.String("mynic"),
			ResourceGroupName:    pulumi.String("testrg"),
			TapConfigurationName: pulumi.String("tapconfiguration1"),
			VirtualNetworkTap: &network.VirtualNetworkTapTypeArgs{
				Id: pulumi.String("/subscriptions/subid/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworkTaps/testvtap"),
			},
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
import com.pulumi.azurenative.network.NetworkInterfaceTapConfiguration;
import com.pulumi.azurenative.network.NetworkInterfaceTapConfigurationArgs;
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
        var networkInterfaceTapConfiguration = new NetworkInterfaceTapConfiguration("networkInterfaceTapConfiguration", NetworkInterfaceTapConfigurationArgs.builder()        
            .networkInterfaceName("mynic")
            .resourceGroupName("testrg")
            .tapConfigurationName("tapconfiguration1")
            .virtualNetworkTap(Map.of("id", "/subscriptions/subid/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworkTaps/testvtap"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const networkInterfaceTapConfiguration = new azure_native.network.NetworkInterfaceTapConfiguration("networkInterfaceTapConfiguration", {
    networkInterfaceName: "mynic",
    resourceGroupName: "testrg",
    tapConfigurationName: "tapconfiguration1",
    virtualNetworkTap: {
        id: "/subscriptions/subid/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworkTaps/testvtap",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

network_interface_tap_configuration = azure_native.network.NetworkInterfaceTapConfiguration("networkInterfaceTapConfiguration",
    network_interface_name="mynic",
    resource_group_name="testrg",
    tap_configuration_name="tapconfiguration1",
    virtual_network_tap=azure_native.network.VirtualNetworkTapArgs(
        id="/subscriptions/subid/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworkTaps/testvtap",
    ))

```

```yaml
resources:
  networkInterfaceTapConfiguration:
    type: azure-native:network:NetworkInterfaceTapConfiguration
    properties:
      networkInterfaceName: mynic
      resourceGroupName: testrg
      tapConfigurationName: tapconfiguration1
      virtualNetworkTap:
        id: /subscriptions/subid/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworkTaps/testvtap

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:NetworkInterfaceTapConfiguration tapConfiguration1 /subscriptions/subid/resourceGroups/testrg/providers/Microsoft.Network/networkInterfaces/mynic/tapConfigurations/tapConfiguration1 
```
