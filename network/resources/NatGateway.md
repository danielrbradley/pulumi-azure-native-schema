Nat Gateway resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create nat gateway
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var natGateway = new AzureNative.Network.NatGateway("natGateway", new()
    {
        Location = "westus",
        NatGatewayName = "test-natgateway",
        PublicIpAddresses = new[]
        {
            new AzureNative.Network.Inputs.SubResourceArgs
            {
                Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/PublicIpAddress1",
            },
        },
        PublicIpPrefixes = new[]
        {
            new AzureNative.Network.Inputs.SubResourceArgs
            {
                Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPPrefixes/PublicIpPrefix1",
            },
        },
        ResourceGroupName = "rg1",
        Sku = new AzureNative.Network.Inputs.NatGatewaySkuArgs
        {
            Name = "Standard",
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
		_, err := network.NewNatGateway(ctx, "natGateway", &network.NatGatewayArgs{
			Location:       pulumi.String("westus"),
			NatGatewayName: pulumi.String("test-natgateway"),
			PublicIpAddresses: []network.SubResourceArgs{
				{
					Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/PublicIpAddress1"),
				},
			},
			PublicIpPrefixes: []network.SubResourceArgs{
				{
					Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPPrefixes/PublicIpPrefix1"),
				},
			},
			ResourceGroupName: pulumi.String("rg1"),
			Sku: &network.NatGatewaySkuArgs{
				Name: pulumi.String("Standard"),
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
import com.pulumi.azurenative.network.NatGateway;
import com.pulumi.azurenative.network.NatGatewayArgs;
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
        var natGateway = new NatGateway("natGateway", NatGatewayArgs.builder()        
            .location("westus")
            .natGatewayName("test-natgateway")
            .publicIpAddresses(Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/PublicIpAddress1"))
            .publicIpPrefixes(Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPPrefixes/PublicIpPrefix1"))
            .resourceGroupName("rg1")
            .sku(Map.of("name", "Standard"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const natGateway = new azure_native.network.NatGateway("natGateway", {
    location: "westus",
    natGatewayName: "test-natgateway",
    publicIpAddresses: [{
        id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/PublicIpAddress1",
    }],
    publicIpPrefixes: [{
        id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPPrefixes/PublicIpPrefix1",
    }],
    resourceGroupName: "rg1",
    sku: {
        name: "Standard",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

nat_gateway = azure_native.network.NatGateway("natGateway",
    location="westus",
    nat_gateway_name="test-natgateway",
    public_ip_addresses=[azure_native.network.SubResourceArgs(
        id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/PublicIpAddress1",
    )],
    public_ip_prefixes=[azure_native.network.SubResourceArgs(
        id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPPrefixes/PublicIpPrefix1",
    )],
    resource_group_name="rg1",
    sku=azure_native.network.NatGatewaySkuArgs(
        name="Standard",
    ))

```

```yaml
resources:
  natGateway:
    type: azure-native:network:NatGateway
    properties:
      location: westus
      natGatewayName: test-natgateway
      publicIpAddresses:
        - id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/PublicIpAddress1
      publicIpPrefixes:
        - id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPPrefixes/PublicIpPrefix1
      resourceGroupName: rg1
      sku:
        name: Standard

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:NatGateway test-natGateway /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/natGateways/test-natGateway 
```
