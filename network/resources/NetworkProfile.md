Network profile resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create network profile defaults
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var networkProfile = new AzureNative.Network.NetworkProfile("networkProfile", new()
    {
        ContainerNetworkInterfaceConfigurations = new[]
        {
            new AzureNative.Network.Inputs.ContainerNetworkInterfaceConfigurationArgs
            {
                IpConfigurations = new[]
                {
                    new AzureNative.Network.Inputs.IPConfigurationProfileArgs
                    {
                        Name = "ipconfig1",
                        Subnet = new AzureNative.Network.Inputs.SubnetArgs
                        {
                            Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/networkProfileVnet/subnets/networkProfileSubnet1",
                        },
                    },
                },
                Name = "eth1",
            },
        },
        Location = "westus",
        NetworkProfileName = "networkProfile1",
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
		_, err := network.NewNetworkProfile(ctx, "networkProfile", &network.NetworkProfileArgs{
			ContainerNetworkInterfaceConfigurations: []network.ContainerNetworkInterfaceConfigurationArgs{
				{
					IpConfigurations: network.IPConfigurationProfileArray{
						{
							Name: pulumi.String("ipconfig1"),
							Subnet: {
								Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/networkProfileVnet/subnets/networkProfileSubnet1"),
							},
						},
					},
					Name: pulumi.String("eth1"),
				},
			},
			Location:           pulumi.String("westus"),
			NetworkProfileName: pulumi.String("networkProfile1"),
			ResourceGroupName:  pulumi.String("rg1"),
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
import com.pulumi.azurenative.network.NetworkProfile;
import com.pulumi.azurenative.network.NetworkProfileArgs;
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
        var networkProfile = new NetworkProfile("networkProfile", NetworkProfileArgs.builder()        
            .containerNetworkInterfaceConfigurations(Map.ofEntries(
                Map.entry("ipConfigurations", Map.ofEntries(
                    Map.entry("name", "ipconfig1"),
                    Map.entry("subnet", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/networkProfileVnet/subnets/networkProfileSubnet1"))
                )),
                Map.entry("name", "eth1")
            ))
            .location("westus")
            .networkProfileName("networkProfile1")
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const networkProfile = new azure_native.network.NetworkProfile("networkProfile", {
    containerNetworkInterfaceConfigurations: [{
        ipConfigurations: [{
            name: "ipconfig1",
            subnet: {
                id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/networkProfileVnet/subnets/networkProfileSubnet1",
            },
        }],
        name: "eth1",
    }],
    location: "westus",
    networkProfileName: "networkProfile1",
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

network_profile = azure_native.network.NetworkProfile("networkProfile",
    container_network_interface_configurations=[{
        "ipConfigurations": [{
            "name": "ipconfig1",
            "subnet": azure_native.network.SubnetArgs(
                id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/networkProfileVnet/subnets/networkProfileSubnet1",
            ),
        }],
        "name": "eth1",
    }],
    location="westus",
    network_profile_name="networkProfile1",
    resource_group_name="rg1")

```

```yaml
resources:
  networkProfile:
    type: azure-native:network:NetworkProfile
    properties:
      containerNetworkInterfaceConfigurations:
        - ipConfigurations:
            - name: ipconfig1
              subnet:
                id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/networkProfileVnet/subnets/networkProfileSubnet1
          name: eth1
      location: westus
      networkProfileName: networkProfile1
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:NetworkProfile networkProfile1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/networkProfiles/networkProfile1 
```
