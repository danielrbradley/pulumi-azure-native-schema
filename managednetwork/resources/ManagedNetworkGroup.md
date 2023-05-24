The Managed Network Group resource
API Version: 2019-06-01-preview.
Previous API Version: 2019-06-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ManagementNetworkGroupsPut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedNetworkGroup = new AzureNative.ManagedNetwork.ManagedNetworkGroup("managedNetworkGroup", new()
    {
        ManagedNetworkGroupName = "myManagedNetworkGroup1",
        ManagedNetworkName = "myManagedNetwork",
        ManagementGroups = new[] {},
        ResourceGroupName = "myResourceGroup",
        Subnets = new[]
        {
            new AzureNative.ManagedNetwork.Inputs.ResourceIdArgs
            {
                Id = "/subscriptionB/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetA/subnets/subnetA",
            },
        },
        Subscriptions = new[] {},
        VirtualNetworks = new[]
        {
            new AzureNative.ManagedNetwork.Inputs.ResourceIdArgs
            {
                Id = "/subscriptionB/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetA",
            },
            new AzureNative.ManagedNetwork.Inputs.ResourceIdArgs
            {
                Id = "/subscriptionB/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetB",
            },
        },
    });

});


```

```go
package main

import (
	managednetwork "github.com/pulumi/pulumi-azure-native-sdk/managednetwork"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := managednetwork.NewManagedNetworkGroup(ctx, "managedNetworkGroup", &managednetwork.ManagedNetworkGroupArgs{
			ManagedNetworkGroupName: pulumi.String("myManagedNetworkGroup1"),
			ManagedNetworkName:      pulumi.String("myManagedNetwork"),
			ManagementGroups:        managednetwork.ResourceIdArray{},
			ResourceGroupName:       pulumi.String("myResourceGroup"),
			Subnets: []managednetwork.ResourceIdArgs{
				{
					Id: pulumi.String("/subscriptionB/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetA/subnets/subnetA"),
				},
			},
			Subscriptions: managednetwork.ResourceIdArray{},
			VirtualNetworks: []managednetwork.ResourceIdArgs{
				{
					Id: pulumi.String("/subscriptionB/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetA"),
				},
				{
					Id: pulumi.String("/subscriptionB/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetB"),
				},
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
import com.pulumi.azurenative.managednetwork.ManagedNetworkGroup;
import com.pulumi.azurenative.managednetwork.ManagedNetworkGroupArgs;
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
        var managedNetworkGroup = new ManagedNetworkGroup("managedNetworkGroup", ManagedNetworkGroupArgs.builder()        
            .managedNetworkGroupName("myManagedNetworkGroup1")
            .managedNetworkName("myManagedNetwork")
            .managementGroups()
            .resourceGroupName("myResourceGroup")
            .subnets(Map.of("id", "/subscriptionB/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetA/subnets/subnetA"))
            .subscriptions()
            .virtualNetworks(            
                Map.of("id", "/subscriptionB/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetA"),
                Map.of("id", "/subscriptionB/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetB"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedNetworkGroup = new azure_native.managednetwork.ManagedNetworkGroup("managedNetworkGroup", {
    managedNetworkGroupName: "myManagedNetworkGroup1",
    managedNetworkName: "myManagedNetwork",
    managementGroups: [],
    resourceGroupName: "myResourceGroup",
    subnets: [{
        id: "/subscriptionB/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetA/subnets/subnetA",
    }],
    subscriptions: [],
    virtualNetworks: [
        {
            id: "/subscriptionB/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetA",
        },
        {
            id: "/subscriptionB/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetB",
        },
    ],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_network_group = azure_native.managednetwork.ManagedNetworkGroup("managedNetworkGroup",
    managed_network_group_name="myManagedNetworkGroup1",
    managed_network_name="myManagedNetwork",
    management_groups=[],
    resource_group_name="myResourceGroup",
    subnets=[azure_native.managednetwork.ResourceIdArgs(
        id="/subscriptionB/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetA/subnets/subnetA",
    )],
    subscriptions=[],
    virtual_networks=[
        azure_native.managednetwork.ResourceIdArgs(
            id="/subscriptionB/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetA",
        ),
        azure_native.managednetwork.ResourceIdArgs(
            id="/subscriptionB/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetB",
        ),
    ])

```

```yaml
resources:
  managedNetworkGroup:
    type: azure-native:managednetwork:ManagedNetworkGroup
    properties:
      managedNetworkGroupName: myManagedNetworkGroup1
      managedNetworkName: myManagedNetwork
      managementGroups: []
      resourceGroupName: myResourceGroup
      subnets:
        - id: /subscriptionB/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetA/subnets/subnetA
      subscriptions: []
      virtualNetworks:
        - id: /subscriptionB/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetA
        - id: /subscriptionB/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetB

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:managednetwork:ManagedNetworkGroup myManagedNetworkGroup1 /subscriptionA/resourceGroups/myResourceGroup/providers/Microsoft.ManagedNetwork/managedNetworks/myManagedNetwork/managedNetworkGroups/myManagedNetworkGroup1 
```
