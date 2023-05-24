Frontend Subresource of Traffic Controller.
API Version: 2022-10-01-preview.
Previous API Version: 2022-10-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Put Frontend
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var frontendsInterface = new AzureNative.ServiceNetworking.FrontendsInterface("frontendsInterface", new()
    {
        FrontendName = "fe1",
        IpAddressVersion = AzureNative.ServiceNetworking.FrontendIPAddressVersion.IPv4,
        Location = "NorthCentralUS",
        Mode = AzureNative.ServiceNetworking.FrontendMode.@Public,
        PublicIPAddress = new AzureNative.ServiceNetworking.Inputs.FrontendPropertiesIPAddressArgs
        {
            Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/PublicIP-fe1",
        },
        ResourceGroupName = "rg1",
        TrafficControllerName = "tc1",
    });

});


```

```go
package main

import (
	servicenetworking "github.com/pulumi/pulumi-azure-native-sdk/servicenetworking"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := servicenetworking.NewFrontendsInterface(ctx, "frontendsInterface", &servicenetworking.FrontendsInterfaceArgs{
			FrontendName:     pulumi.String("fe1"),
			IpAddressVersion: servicenetworking.FrontendIPAddressVersionIPv4,
			Location:         pulumi.String("NorthCentralUS"),
			Mode:             servicenetworking.FrontendModePublic,
			PublicIPAddress: &servicenetworking.FrontendPropertiesIPAddressArgs{
				Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/PublicIP-fe1"),
			},
			ResourceGroupName:     pulumi.String("rg1"),
			TrafficControllerName: pulumi.String("tc1"),
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
import com.pulumi.azurenative.servicenetworking.FrontendsInterface;
import com.pulumi.azurenative.servicenetworking.FrontendsInterfaceArgs;
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
        var frontendsInterface = new FrontendsInterface("frontendsInterface", FrontendsInterfaceArgs.builder()        
            .frontendName("fe1")
            .ipAddressVersion("IPv4")
            .location("NorthCentralUS")
            .mode("public")
            .publicIPAddress(Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/PublicIP-fe1"))
            .resourceGroupName("rg1")
            .trafficControllerName("tc1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const frontendsInterface = new azure_native.servicenetworking.FrontendsInterface("frontendsInterface", {
    frontendName: "fe1",
    ipAddressVersion: azure_native.servicenetworking.FrontendIPAddressVersion.IPv4,
    location: "NorthCentralUS",
    mode: azure_native.servicenetworking.FrontendMode.Public,
    publicIPAddress: {
        id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/PublicIP-fe1",
    },
    resourceGroupName: "rg1",
    trafficControllerName: "tc1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

frontends_interface = azure_native.servicenetworking.FrontendsInterface("frontendsInterface",
    frontend_name="fe1",
    ip_address_version=azure_native.servicenetworking.FrontendIPAddressVersion.I_PV4,
    location="NorthCentralUS",
    mode=azure_native.servicenetworking.FrontendMode.PUBLIC,
    public_ip_address=azure_native.servicenetworking.FrontendPropertiesIPAddressArgs(
        id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/PublicIP-fe1",
    ),
    resource_group_name="rg1",
    traffic_controller_name="tc1")

```

```yaml
resources:
  frontendsInterface:
    type: azure-native:servicenetworking:FrontendsInterface
    properties:
      frontendName: fe1
      ipAddressVersion: IPv4
      location: NorthCentralUS
      mode: public
      publicIPAddress:
        id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/PublicIP-fe1
      resourceGroupName: rg1
      trafficControllerName: tc1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:servicenetworking:FrontendsInterface fe1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ServiceNetworking/trafficControllers/tc1/frontends/fe1 
```
