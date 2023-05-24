Interface endpoint resource.
API Version: 2019-02-01.

{{% examples %}}
## Example Usage
{{% example %}}
### Create interface endpoint
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var interfaceEndpoint = new AzureNative.Network.InterfaceEndpoint("interfaceEndpoint", new()
    {
        EndpointService = new AzureNative.Network.Inputs.EndpointServiceArgs
        {
            Id = "/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Provider/resourceType/resourceName",
        },
        Fqdn = "uniqueIdentifier.fqdn.windows.net",
        InterfaceEndpointName = "testIe",
        ResourceGroupName = "rg1",
        Subnet = new AzureNative.Network.Inputs.SubnetArgs
        {
            Id = "/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet",
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
		_, err := network.NewInterfaceEndpoint(ctx, "interfaceEndpoint", &network.InterfaceEndpointArgs{
			EndpointService: &network.EndpointServiceArgs{
				Id: pulumi.String("/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Provider/resourceType/resourceName"),
			},
			Fqdn:                  pulumi.String("uniqueIdentifier.fqdn.windows.net"),
			InterfaceEndpointName: pulumi.String("testIe"),
			ResourceGroupName:     pulumi.String("rg1"),
			Subnet: &network.SubnetTypeArgs{
				Id: pulumi.String("/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet"),
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
import com.pulumi.azurenative.network.InterfaceEndpoint;
import com.pulumi.azurenative.network.InterfaceEndpointArgs;
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
        var interfaceEndpoint = new InterfaceEndpoint("interfaceEndpoint", InterfaceEndpointArgs.builder()        
            .endpointService(Map.of("id", "/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Provider/resourceType/resourceName"))
            .fqdn("uniqueIdentifier.fqdn.windows.net")
            .interfaceEndpointName("testIe")
            .resourceGroupName("rg1")
            .subnet(Map.of("id", "/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const interfaceEndpoint = new azure_native.network.InterfaceEndpoint("interfaceEndpoint", {
    endpointService: {
        id: "/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Provider/resourceType/resourceName",
    },
    fqdn: "uniqueIdentifier.fqdn.windows.net",
    interfaceEndpointName: "testIe",
    resourceGroupName: "rg1",
    subnet: {
        id: "/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

interface_endpoint = azure_native.network.InterfaceEndpoint("interfaceEndpoint",
    endpoint_service=azure_native.network.EndpointServiceArgs(
        id="/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Provider/resourceType/resourceName",
    ),
    fqdn="uniqueIdentifier.fqdn.windows.net",
    interface_endpoint_name="testIe",
    resource_group_name="rg1",
    subnet=azure_native.network.SubnetArgs(
        id="/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet",
    ))

```

```yaml
resources:
  interfaceEndpoint:
    type: azure-native:network:InterfaceEndpoint
    properties:
      endpointService:
        id: /subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Provider/resourceType/resourceName
      fqdn: uniqueIdentifier.fqdn.windows.net
      interfaceEndpointName: testIe
      resourceGroupName: rg1
      subnet:
        id: /subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:InterfaceEndpoint testIe /subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/interfaceEndpoints/testIe 
```
