Bastion Host resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Bastion Host
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var bastionHost = new AzureNative.Network.BastionHost("bastionHost", new()
    {
        BastionHostName = "bastionhosttenant",
        IpConfigurations = new[]
        {
            new AzureNative.Network.Inputs.BastionHostIPConfigurationArgs
            {
                Name = "bastionHostIpConfiguration",
                PublicIPAddress = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName",
                },
                Subnet = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/BastionHostSubnet",
                },
            },
        },
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
		_, err := network.NewBastionHost(ctx, "bastionHost", &network.BastionHostArgs{
			BastionHostName: pulumi.String("bastionhosttenant"),
			IpConfigurations: []network.BastionHostIPConfigurationArgs{
				{
					Name: pulumi.String("bastionHostIpConfiguration"),
					PublicIPAddress: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName"),
					},
					Subnet: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/BastionHostSubnet"),
					},
				},
			},
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
import com.pulumi.azurenative.network.BastionHost;
import com.pulumi.azurenative.network.BastionHostArgs;
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
        var bastionHost = new BastionHost("bastionHost", BastionHostArgs.builder()        
            .bastionHostName("bastionhosttenant")
            .ipConfigurations(Map.ofEntries(
                Map.entry("name", "bastionHostIpConfiguration"),
                Map.entry("publicIPAddress", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName")),
                Map.entry("subnet", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/BastionHostSubnet"))
            ))
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const bastionHost = new azure_native.network.BastionHost("bastionHost", {
    bastionHostName: "bastionhosttenant",
    ipConfigurations: [{
        name: "bastionHostIpConfiguration",
        publicIPAddress: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName",
        },
        subnet: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/BastionHostSubnet",
        },
    }],
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

bastion_host = azure_native.network.BastionHost("bastionHost",
    bastion_host_name="bastionhosttenant",
    ip_configurations=[{
        "name": "bastionHostIpConfiguration",
        "publicIPAddress": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName",
        ),
        "subnet": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/BastionHostSubnet",
        ),
    }],
    resource_group_name="rg1")

```

```yaml
resources:
  bastionHost:
    type: azure-native:network:BastionHost
    properties:
      bastionHostName: bastionhosttenant
      ipConfigurations:
        - name: bastionHostIpConfiguration
          publicIPAddress:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pipName
          subnet:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet2/subnets/BastionHostSubnet
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:BastionHost bastionhost /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/bastionHosts/bastionhosttenant' 
```
