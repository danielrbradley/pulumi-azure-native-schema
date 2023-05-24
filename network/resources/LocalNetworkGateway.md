A common class for general resource information.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateLocalNetworkGateway
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var localNetworkGateway = new AzureNative.Network.LocalNetworkGateway("localNetworkGateway", new()
    {
        Fqdn = "site1.contoso.com",
        GatewayIpAddress = "11.12.13.14",
        LocalNetworkAddressSpace = new AzureNative.Network.Inputs.AddressSpaceArgs
        {
            AddressPrefixes = new[]
            {
                "10.1.0.0/16",
            },
        },
        LocalNetworkGatewayName = "localgw",
        Location = "Central US",
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
		_, err := network.NewLocalNetworkGateway(ctx, "localNetworkGateway", &network.LocalNetworkGatewayArgs{
			Fqdn:             pulumi.String("site1.contoso.com"),
			GatewayIpAddress: pulumi.String("11.12.13.14"),
			LocalNetworkAddressSpace: &network.AddressSpaceArgs{
				AddressPrefixes: pulumi.StringArray{
					pulumi.String("10.1.0.0/16"),
				},
			},
			LocalNetworkGatewayName: pulumi.String("localgw"),
			Location:                pulumi.String("Central US"),
			ResourceGroupName:       pulumi.String("rg1"),
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
import com.pulumi.azurenative.network.LocalNetworkGateway;
import com.pulumi.azurenative.network.LocalNetworkGatewayArgs;
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
        var localNetworkGateway = new LocalNetworkGateway("localNetworkGateway", LocalNetworkGatewayArgs.builder()        
            .fqdn("site1.contoso.com")
            .gatewayIpAddress("11.12.13.14")
            .localNetworkAddressSpace(Map.of("addressPrefixes", "10.1.0.0/16"))
            .localNetworkGatewayName("localgw")
            .location("Central US")
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const localNetworkGateway = new azure_native.network.LocalNetworkGateway("localNetworkGateway", {
    fqdn: "site1.contoso.com",
    gatewayIpAddress: "11.12.13.14",
    localNetworkAddressSpace: {
        addressPrefixes: ["10.1.0.0/16"],
    },
    localNetworkGatewayName: "localgw",
    location: "Central US",
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

local_network_gateway = azure_native.network.LocalNetworkGateway("localNetworkGateway",
    fqdn="site1.contoso.com",
    gateway_ip_address="11.12.13.14",
    local_network_address_space=azure_native.network.AddressSpaceArgs(
        address_prefixes=["10.1.0.0/16"],
    ),
    local_network_gateway_name="localgw",
    location="Central US",
    resource_group_name="rg1")

```

```yaml
resources:
  localNetworkGateway:
    type: azure-native:network:LocalNetworkGateway
    properties:
      fqdn: site1.contoso.com
      gatewayIpAddress: 11.12.13.14
      localNetworkAddressSpace:
        addressPrefixes:
          - 10.1.0.0/16
      localNetworkGatewayName: localgw
      location: Central US
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:LocalNetworkGateway localgw /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/localNetworkGateways/localgw 
```
