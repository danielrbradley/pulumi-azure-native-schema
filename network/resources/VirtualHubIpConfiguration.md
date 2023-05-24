IpConfigurations.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### VirtualHubIpConfigurationPut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualHubIpConfiguration = new AzureNative.Network.VirtualHubIpConfiguration("virtualHubIpConfiguration", new()
    {
        IpConfigName = "ipconfig1",
        ResourceGroupName = "rg1",
        Subnet = new AzureNative.Network.Inputs.SubnetArgs
        {
            Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet1/subnets/subnet1",
        },
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
		_, err := network.NewVirtualHubIpConfiguration(ctx, "virtualHubIpConfiguration", &network.VirtualHubIpConfigurationArgs{
			IpConfigName:      pulumi.String("ipconfig1"),
			ResourceGroupName: pulumi.String("rg1"),
			Subnet: &network.SubnetTypeArgs{
				Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet1/subnets/subnet1"),
			},
			VirtualHubName: pulumi.String("hub1"),
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
import com.pulumi.azurenative.network.VirtualHubIpConfiguration;
import com.pulumi.azurenative.network.VirtualHubIpConfigurationArgs;
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
        var virtualHubIpConfiguration = new VirtualHubIpConfiguration("virtualHubIpConfiguration", VirtualHubIpConfigurationArgs.builder()        
            .ipConfigName("ipconfig1")
            .resourceGroupName("rg1")
            .subnet(Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet1/subnets/subnet1"))
            .virtualHubName("hub1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualHubIpConfiguration = new azure_native.network.VirtualHubIpConfiguration("virtualHubIpConfiguration", {
    ipConfigName: "ipconfig1",
    resourceGroupName: "rg1",
    subnet: {
        id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet1/subnets/subnet1",
    },
    virtualHubName: "hub1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_hub_ip_configuration = azure_native.network.VirtualHubIpConfiguration("virtualHubIpConfiguration",
    ip_config_name="ipconfig1",
    resource_group_name="rg1",
    subnet=azure_native.network.SubnetArgs(
        id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet1/subnets/subnet1",
    ),
    virtual_hub_name="hub1")

```

```yaml
resources:
  virtualHubIpConfiguration:
    type: azure-native:network:VirtualHubIpConfiguration
    properties:
      ipConfigName: ipconfig1
      resourceGroupName: rg1
      subnet:
        id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet1/subnets/subnet1
      virtualHubName: hub1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:VirtualHubIpConfiguration ipconfig1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1/ipConfigurations/ipconfig1 
```
