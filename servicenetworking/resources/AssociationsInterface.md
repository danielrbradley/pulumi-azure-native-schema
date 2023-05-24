Association Subresource of Traffic Controller
API Version: 2022-10-01-preview.
Previous API Version: 2022-10-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Put Association
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var associationsInterface = new AzureNative.ServiceNetworking.AssociationsInterface("associationsInterface", new()
    {
        AssociationName = "as1",
        AssociationType = AzureNative.ServiceNetworking.AssociationType.Subnets,
        Location = "NorthCentralUS",
        ResourceGroupName = "rg1",
        Subnet = new AzureNative.ServiceNetworking.Inputs.AssociationSubnetArgs
        {
            Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet-tc/subnets/tc-subnet",
        },
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
		_, err := servicenetworking.NewAssociationsInterface(ctx, "associationsInterface", &servicenetworking.AssociationsInterfaceArgs{
			AssociationName:   pulumi.String("as1"),
			AssociationType:   servicenetworking.AssociationTypeSubnets,
			Location:          pulumi.String("NorthCentralUS"),
			ResourceGroupName: pulumi.String("rg1"),
			Subnet: &servicenetworking.AssociationSubnetArgs{
				Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet-tc/subnets/tc-subnet"),
			},
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
import com.pulumi.azurenative.servicenetworking.AssociationsInterface;
import com.pulumi.azurenative.servicenetworking.AssociationsInterfaceArgs;
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
        var associationsInterface = new AssociationsInterface("associationsInterface", AssociationsInterfaceArgs.builder()        
            .associationName("as1")
            .associationType("subnets")
            .location("NorthCentralUS")
            .resourceGroupName("rg1")
            .subnet(Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet-tc/subnets/tc-subnet"))
            .trafficControllerName("tc1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const associationsInterface = new azure_native.servicenetworking.AssociationsInterface("associationsInterface", {
    associationName: "as1",
    associationType: azure_native.servicenetworking.AssociationType.Subnets,
    location: "NorthCentralUS",
    resourceGroupName: "rg1",
    subnet: {
        id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet-tc/subnets/tc-subnet",
    },
    trafficControllerName: "tc1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

associations_interface = azure_native.servicenetworking.AssociationsInterface("associationsInterface",
    association_name="as1",
    association_type=azure_native.servicenetworking.AssociationType.SUBNETS,
    location="NorthCentralUS",
    resource_group_name="rg1",
    subnet=azure_native.servicenetworking.AssociationSubnetArgs(
        id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet-tc/subnets/tc-subnet",
    ),
    traffic_controller_name="tc1")

```

```yaml
resources:
  associationsInterface:
    type: azure-native:servicenetworking:AssociationsInterface
    properties:
      associationName: as1
      associationType: subnets
      location: NorthCentralUS
      resourceGroupName: rg1
      subnet:
        id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnet-tc/subnets/tc-subnet
      trafficControllerName: tc1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:servicenetworking:AssociationsInterface associatedvnet-1 /subscriptions/subid/resourcegroups/rg1/providers/Microsoft.ServiceNetworking/trafficControllers/tc1/associations/as1 
```
