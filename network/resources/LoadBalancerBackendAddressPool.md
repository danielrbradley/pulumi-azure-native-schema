Pool of backend IP addresses.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Update load balancer backend pool with backend addresses containing virtual network and  IP address.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var loadBalancerBackendAddressPool = new AzureNative.Network.LoadBalancerBackendAddressPool("loadBalancerBackendAddressPool", new()
    {
        BackendAddressPoolName = "backend",
        LoadBalancerBackendAddresses = new[]
        {
            new AzureNative.Network.Inputs.LoadBalancerBackendAddressArgs
            {
                IpAddress = "10.0.0.4",
                Name = "address1",
                VirtualNetwork = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb",
                },
            },
            new AzureNative.Network.Inputs.LoadBalancerBackendAddressArgs
            {
                IpAddress = "10.0.0.5",
                Name = "address2",
                VirtualNetwork = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb",
                },
            },
        },
        LoadBalancerName = "lb",
        ResourceGroupName = "testrg",
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
		_, err := network.NewLoadBalancerBackendAddressPool(ctx, "loadBalancerBackendAddressPool", &network.LoadBalancerBackendAddressPoolArgs{
			BackendAddressPoolName: pulumi.String("backend"),
			LoadBalancerBackendAddresses: []network.LoadBalancerBackendAddressArgs{
				{
					IpAddress: pulumi.String("10.0.0.4"),
					Name:      pulumi.String("address1"),
					VirtualNetwork: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb"),
					},
				},
				{
					IpAddress: pulumi.String("10.0.0.5"),
					Name:      pulumi.String("address2"),
					VirtualNetwork: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb"),
					},
				},
			},
			LoadBalancerName:  pulumi.String("lb"),
			ResourceGroupName: pulumi.String("testrg"),
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
import com.pulumi.azurenative.network.LoadBalancerBackendAddressPool;
import com.pulumi.azurenative.network.LoadBalancerBackendAddressPoolArgs;
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
        var loadBalancerBackendAddressPool = new LoadBalancerBackendAddressPool("loadBalancerBackendAddressPool", LoadBalancerBackendAddressPoolArgs.builder()        
            .backendAddressPoolName("backend")
            .loadBalancerBackendAddresses(            
                Map.ofEntries(
                    Map.entry("ipAddress", "10.0.0.4"),
                    Map.entry("name", "address1"),
                    Map.entry("virtualNetwork", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb"))
                ),
                Map.ofEntries(
                    Map.entry("ipAddress", "10.0.0.5"),
                    Map.entry("name", "address2"),
                    Map.entry("virtualNetwork", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb"))
                ))
            .loadBalancerName("lb")
            .resourceGroupName("testrg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const loadBalancerBackendAddressPool = new azure_native.network.LoadBalancerBackendAddressPool("loadBalancerBackendAddressPool", {
    backendAddressPoolName: "backend",
    loadBalancerBackendAddresses: [
        {
            ipAddress: "10.0.0.4",
            name: "address1",
            virtualNetwork: {
                id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb",
            },
        },
        {
            ipAddress: "10.0.0.5",
            name: "address2",
            virtualNetwork: {
                id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb",
            },
        },
    ],
    loadBalancerName: "lb",
    resourceGroupName: "testrg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

load_balancer_backend_address_pool = azure_native.network.LoadBalancerBackendAddressPool("loadBalancerBackendAddressPool",
    backend_address_pool_name="backend",
    load_balancer_backend_addresses=[
        {
            "ipAddress": "10.0.0.4",
            "name": "address1",
            "virtualNetwork": azure_native.network.SubResourceArgs(
                id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb",
            ),
        },
        {
            "ipAddress": "10.0.0.5",
            "name": "address2",
            "virtualNetwork": azure_native.network.SubResourceArgs(
                id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb",
            ),
        },
    ],
    load_balancer_name="lb",
    resource_group_name="testrg")

```

```yaml
resources:
  loadBalancerBackendAddressPool:
    type: azure-native:network:LoadBalancerBackendAddressPool
    properties:
      backendAddressPoolName: backend
      loadBalancerBackendAddresses:
        - ipAddress: 10.0.0.4
          name: address1
          virtualNetwork:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb
        - ipAddress: 10.0.0.5
          name: address2
          virtualNetwork:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb
      loadBalancerName: lb
      resourceGroupName: testrg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:LoadBalancerBackendAddressPool backend /subscriptions/subid/resourceGroups/testrg/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/backend 
```
