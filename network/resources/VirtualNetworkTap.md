Virtual Network Tap resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Virtual Network Tap
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualNetworkTap = new AzureNative.Network.VirtualNetworkTap("virtualNetworkTap", new()
    {
        DestinationNetworkInterfaceIPConfiguration = new AzureNative.Network.Inputs.NetworkInterfaceIPConfigurationArgs
        {
            Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/networkInterfaces/testNetworkInterface/ipConfigurations/ipconfig1",
        },
        Location = "centraluseuap",
        ResourceGroupName = "rg1",
        TapName = "test-vtap",
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
		_, err := network.NewVirtualNetworkTap(ctx, "virtualNetworkTap", &network.VirtualNetworkTapArgs{
			DestinationNetworkInterfaceIPConfiguration: &network.NetworkInterfaceIPConfigurationArgs{
				Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/networkInterfaces/testNetworkInterface/ipConfigurations/ipconfig1"),
			},
			Location:          pulumi.String("centraluseuap"),
			ResourceGroupName: pulumi.String("rg1"),
			TapName:           pulumi.String("test-vtap"),
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
import com.pulumi.azurenative.network.VirtualNetworkTap;
import com.pulumi.azurenative.network.VirtualNetworkTapArgs;
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
        var virtualNetworkTap = new VirtualNetworkTap("virtualNetworkTap", VirtualNetworkTapArgs.builder()        
            .destinationNetworkInterfaceIPConfiguration(Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/networkInterfaces/testNetworkInterface/ipConfigurations/ipconfig1"))
            .location("centraluseuap")
            .resourceGroupName("rg1")
            .tapName("test-vtap")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualNetworkTap = new azure_native.network.VirtualNetworkTap("virtualNetworkTap", {
    destinationNetworkInterfaceIPConfiguration: {
        id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/networkInterfaces/testNetworkInterface/ipConfigurations/ipconfig1",
    },
    location: "centraluseuap",
    resourceGroupName: "rg1",
    tapName: "test-vtap",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_network_tap = azure_native.network.VirtualNetworkTap("virtualNetworkTap",
    destination_network_interface_ip_configuration=azure_native.network.NetworkInterfaceIPConfigurationArgs(
        id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/networkInterfaces/testNetworkInterface/ipConfigurations/ipconfig1",
    ),
    location="centraluseuap",
    resource_group_name="rg1",
    tap_name="test-vtap")

```

```yaml
resources:
  virtualNetworkTap:
    type: azure-native:network:VirtualNetworkTap
    properties:
      destinationNetworkInterfaceIPConfiguration:
        id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/networkInterfaces/testNetworkInterface/ipConfigurations/ipconfig1
      location: centraluseuap
      resourceGroupName: rg1
      tapName: test-vtap

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:VirtualNetworkTap testvtap /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkTaps/testvtap 
```
