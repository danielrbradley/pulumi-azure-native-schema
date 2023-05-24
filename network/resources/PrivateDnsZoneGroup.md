Private dns zone group resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create private dns zone group
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateDnsZoneGroup = new AzureNative.Network.PrivateDnsZoneGroup("privateDnsZoneGroup", new()
    {
        PrivateDnsZoneConfigs = new[]
        {
            new AzureNative.Network.Inputs.PrivateDnsZoneConfigArgs
            {
                PrivateDnsZoneId = "/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/privateDnsZones/zone1.com",
            },
        },
        PrivateDnsZoneGroupName = "testPdnsgroup",
        PrivateEndpointName = "testPe",
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
		_, err := network.NewPrivateDnsZoneGroup(ctx, "privateDnsZoneGroup", &network.PrivateDnsZoneGroupArgs{
			PrivateDnsZoneConfigs: []network.PrivateDnsZoneConfigArgs{
				{
					PrivateDnsZoneId: pulumi.String("/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/privateDnsZones/zone1.com"),
				},
			},
			PrivateDnsZoneGroupName: pulumi.String("testPdnsgroup"),
			PrivateEndpointName:     pulumi.String("testPe"),
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
import com.pulumi.azurenative.network.PrivateDnsZoneGroup;
import com.pulumi.azurenative.network.PrivateDnsZoneGroupArgs;
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
        var privateDnsZoneGroup = new PrivateDnsZoneGroup("privateDnsZoneGroup", PrivateDnsZoneGroupArgs.builder()        
            .privateDnsZoneConfigs(Map.of("privateDnsZoneId", "/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/privateDnsZones/zone1.com"))
            .privateDnsZoneGroupName("testPdnsgroup")
            .privateEndpointName("testPe")
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateDnsZoneGroup = new azure_native.network.PrivateDnsZoneGroup("privateDnsZoneGroup", {
    privateDnsZoneConfigs: [{
        privateDnsZoneId: "/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/privateDnsZones/zone1.com",
    }],
    privateDnsZoneGroupName: "testPdnsgroup",
    privateEndpointName: "testPe",
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_dns_zone_group = azure_native.network.PrivateDnsZoneGroup("privateDnsZoneGroup",
    private_dns_zone_configs=[azure_native.network.PrivateDnsZoneConfigArgs(
        private_dns_zone_id="/subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/privateDnsZones/zone1.com",
    )],
    private_dns_zone_group_name="testPdnsgroup",
    private_endpoint_name="testPe",
    resource_group_name="rg1")

```

```yaml
resources:
  privateDnsZoneGroup:
    type: azure-native:network:PrivateDnsZoneGroup
    properties:
      privateDnsZoneConfigs:
        - privateDnsZoneId: /subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/privateDnsZones/zone1.com
      privateDnsZoneGroupName: testPdnsgroup
      privateEndpointName: testPe
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:PrivateDnsZoneGroup testPdnsgroup /subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/privateLinkServices/testPe/privateDnsZoneGroups/testPdnsgroup 
```
