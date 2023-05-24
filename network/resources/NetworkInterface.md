A network interface in a resource group.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create network interface
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var networkInterface = new AzureNative.Network.NetworkInterface("networkInterface", new()
    {
        DisableTcpStateTracking = true,
        EnableAcceleratedNetworking = true,
        IpConfigurations = new[]
        {
            new AzureNative.Network.Inputs.NetworkInterfaceIPConfigurationArgs
            {
                Name = "ipconfig1",
                PublicIPAddress = new AzureNative.Network.Inputs.PublicIPAddressArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/test-ip",
                },
                Subnet = new AzureNative.Network.Inputs.SubnetArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/rg1-vnet/subnets/default",
                },
            },
        },
        Location = "eastus",
        NetworkInterfaceName = "test-nic",
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
		_, err := network.NewNetworkInterface(ctx, "networkInterface", &network.NetworkInterfaceArgs{
			DisableTcpStateTracking:     pulumi.Bool(true),
			EnableAcceleratedNetworking: pulumi.Bool(true),
			IpConfigurations: []network.NetworkInterfaceIPConfigurationArgs{
				{
					Name: pulumi.String("ipconfig1"),
					PublicIPAddress: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/test-ip"),
					},
					Subnet: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/rg1-vnet/subnets/default"),
					},
				},
			},
			Location:             pulumi.String("eastus"),
			NetworkInterfaceName: pulumi.String("test-nic"),
			ResourceGroupName:    pulumi.String("rg1"),
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
import com.pulumi.azurenative.network.NetworkInterface;
import com.pulumi.azurenative.network.NetworkInterfaceArgs;
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
        var networkInterface = new NetworkInterface("networkInterface", NetworkInterfaceArgs.builder()        
            .disableTcpStateTracking(true)
            .enableAcceleratedNetworking(true)
            .ipConfigurations(Map.ofEntries(
                Map.entry("name", "ipconfig1"),
                Map.entry("publicIPAddress", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/test-ip")),
                Map.entry("subnet", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/rg1-vnet/subnets/default"))
            ))
            .location("eastus")
            .networkInterfaceName("test-nic")
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const networkInterface = new azure_native.network.NetworkInterface("networkInterface", {
    disableTcpStateTracking: true,
    enableAcceleratedNetworking: true,
    ipConfigurations: [{
        name: "ipconfig1",
        publicIPAddress: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/test-ip",
        },
        subnet: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/rg1-vnet/subnets/default",
        },
    }],
    location: "eastus",
    networkInterfaceName: "test-nic",
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

network_interface = azure_native.network.NetworkInterface("networkInterface",
    disable_tcp_state_tracking=True,
    enable_accelerated_networking=True,
    ip_configurations=[azure_native.network.NetworkInterfaceIPConfigurationArgs(
        name="ipconfig1",
        public_ip_address=azure_native.network.PublicIPAddressArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/test-ip",
        ),
        subnet=azure_native.network.SubnetArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/rg1-vnet/subnets/default",
        ),
    )],
    location="eastus",
    network_interface_name="test-nic",
    resource_group_name="rg1")

```

```yaml
resources:
  networkInterface:
    type: azure-native:network:NetworkInterface
    properties:
      disableTcpStateTracking: true
      enableAcceleratedNetworking: true
      ipConfigurations:
        - name: ipconfig1
          publicIPAddress:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/test-ip
          subnet:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/rg1-vnet/subnets/default
      location: eastus
      networkInterfaceName: test-nic
      resourceGroupName: rg1

```

{{% /example %}}
{{% example %}}
### Create network interface with Gateway Load Balancer Consumer configured
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var networkInterface = new AzureNative.Network.NetworkInterface("networkInterface", new()
    {
        EnableAcceleratedNetworking = true,
        IpConfigurations = new[]
        {
            new AzureNative.Network.Inputs.NetworkInterfaceIPConfigurationArgs
            {
                GatewayLoadBalancer = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb-provider",
                },
                Name = "ipconfig1",
                PublicIPAddress = new AzureNative.Network.Inputs.PublicIPAddressArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/test-ip",
                },
                Subnet = new AzureNative.Network.Inputs.SubnetArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/rg1-vnet/subnets/default",
                },
            },
        },
        Location = "eastus",
        NetworkInterfaceName = "test-nic",
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
		_, err := network.NewNetworkInterface(ctx, "networkInterface", &network.NetworkInterfaceArgs{
			EnableAcceleratedNetworking: pulumi.Bool(true),
			IpConfigurations: []network.NetworkInterfaceIPConfigurationArgs{
				{
					GatewayLoadBalancer: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb-provider"),
					},
					Name: pulumi.String("ipconfig1"),
					PublicIPAddress: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/test-ip"),
					},
					Subnet: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/rg1-vnet/subnets/default"),
					},
				},
			},
			Location:             pulumi.String("eastus"),
			NetworkInterfaceName: pulumi.String("test-nic"),
			ResourceGroupName:    pulumi.String("rg1"),
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
import com.pulumi.azurenative.network.NetworkInterface;
import com.pulumi.azurenative.network.NetworkInterfaceArgs;
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
        var networkInterface = new NetworkInterface("networkInterface", NetworkInterfaceArgs.builder()        
            .enableAcceleratedNetworking(true)
            .ipConfigurations(Map.ofEntries(
                Map.entry("gatewayLoadBalancer", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb-provider")),
                Map.entry("name", "ipconfig1"),
                Map.entry("publicIPAddress", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/test-ip")),
                Map.entry("subnet", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/rg1-vnet/subnets/default"))
            ))
            .location("eastus")
            .networkInterfaceName("test-nic")
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const networkInterface = new azure_native.network.NetworkInterface("networkInterface", {
    enableAcceleratedNetworking: true,
    ipConfigurations: [{
        gatewayLoadBalancer: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb-provider",
        },
        name: "ipconfig1",
        publicIPAddress: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/test-ip",
        },
        subnet: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/rg1-vnet/subnets/default",
        },
    }],
    location: "eastus",
    networkInterfaceName: "test-nic",
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

network_interface = azure_native.network.NetworkInterface("networkInterface",
    enable_accelerated_networking=True,
    ip_configurations=[azure_native.network.NetworkInterfaceIPConfigurationArgs(
        gateway_load_balancer=azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb-provider",
        ),
        name="ipconfig1",
        public_ip_address=azure_native.network.PublicIPAddressArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/test-ip",
        ),
        subnet=azure_native.network.SubnetArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/rg1-vnet/subnets/default",
        ),
    )],
    location="eastus",
    network_interface_name="test-nic",
    resource_group_name="rg1")

```

```yaml
resources:
  networkInterface:
    type: azure-native:network:NetworkInterface
    properties:
      enableAcceleratedNetworking: true
      ipConfigurations:
        - gatewayLoadBalancer:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb-provider
          name: ipconfig1
          publicIPAddress:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/test-ip
          subnet:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/rg1-vnet/subnets/default
      location: eastus
      networkInterfaceName: test-nic
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:NetworkInterface test-nic /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/networkInterfaces/test-nic 
```
