The Managed Network resource
API Version: 2019-06-01-preview.
Previous API Version: 2019-06-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ManagedNetworksPut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedNetwork = new AzureNative.ManagedNetwork.ManagedNetwork("managedNetwork", new()
    {
        Location = "eastus",
        ManagedNetworkName = "myManagedNetwork",
        ResourceGroupName = "myResourceGroup",
        Scope = new AzureNative.ManagedNetwork.Inputs.ScopeArgs
        {
            ManagementGroups = new[]
            {
                new AzureNative.ManagedNetwork.Inputs.ResourceIdArgs
                {
                    Id = "/providers/Microsoft.Management/managementGroups/20000000-0001-0000-0000-000000000000",
                },
                new AzureNative.ManagedNetwork.Inputs.ResourceIdArgs
                {
                    Id = "/providers/Microsoft.Management/managementGroups/20000000-0002-0000-0000-000000000000",
                },
            },
            Subnets = new[]
            {
                new AzureNative.ManagedNetwork.Inputs.ResourceIdArgs
                {
                    Id = "/subscriptions/subscriptionC/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetC/subnets/subnetA",
                },
                new AzureNative.ManagedNetwork.Inputs.ResourceIdArgs
                {
                    Id = "/subscriptions/subscriptionC/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetC/subnets/subnetB",
                },
            },
            Subscriptions = new[]
            {
                new AzureNative.ManagedNetwork.Inputs.ResourceIdArgs
                {
                    Id = "subscriptionA",
                },
                new AzureNative.ManagedNetwork.Inputs.ResourceIdArgs
                {
                    Id = "subscriptionB",
                },
            },
            VirtualNetworks = new[]
            {
                new AzureNative.ManagedNetwork.Inputs.ResourceIdArgs
                {
                    Id = "/subscriptions/subscriptionC/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetA",
                },
                new AzureNative.ManagedNetwork.Inputs.ResourceIdArgs
                {
                    Id = "/subscriptions/subscriptionC/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetB",
                },
            },
        },
        Tags = null,
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
		_, err := managednetwork.NewManagedNetwork(ctx, "managedNetwork", &managednetwork.ManagedNetworkArgs{
			Location:           pulumi.String("eastus"),
			ManagedNetworkName: pulumi.String("myManagedNetwork"),
			ResourceGroupName:  pulumi.String("myResourceGroup"),
			Scope: managednetwork.ScopeResponse{
				ManagementGroups: managednetwork.ResourceIdArray{
					&managednetwork.ResourceIdArgs{
						Id: pulumi.String("/providers/Microsoft.Management/managementGroups/20000000-0001-0000-0000-000000000000"),
					},
					&managednetwork.ResourceIdArgs{
						Id: pulumi.String("/providers/Microsoft.Management/managementGroups/20000000-0002-0000-0000-000000000000"),
					},
				},
				Subnets: managednetwork.ResourceIdArray{
					&managednetwork.ResourceIdArgs{
						Id: pulumi.String("/subscriptions/subscriptionC/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetC/subnets/subnetA"),
					},
					&managednetwork.ResourceIdArgs{
						Id: pulumi.String("/subscriptions/subscriptionC/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetC/subnets/subnetB"),
					},
				},
				Subscriptions: managednetwork.ResourceIdArray{
					&managednetwork.ResourceIdArgs{
						Id: pulumi.String("subscriptionA"),
					},
					&managednetwork.ResourceIdArgs{
						Id: pulumi.String("subscriptionB"),
					},
				},
				VirtualNetworks: managednetwork.ResourceIdArray{
					&managednetwork.ResourceIdArgs{
						Id: pulumi.String("/subscriptions/subscriptionC/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetA"),
					},
					&managednetwork.ResourceIdArgs{
						Id: pulumi.String("/subscriptions/subscriptionC/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetB"),
					},
				},
			},
			Tags: nil,
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
import com.pulumi.azurenative.managednetwork.ManagedNetwork;
import com.pulumi.azurenative.managednetwork.ManagedNetworkArgs;
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
        var managedNetwork = new ManagedNetwork("managedNetwork", ManagedNetworkArgs.builder()        
            .location("eastus")
            .managedNetworkName("myManagedNetwork")
            .resourceGroupName("myResourceGroup")
            .scope(Map.ofEntries(
                Map.entry("managementGroups",                 
                    Map.of("id", "/providers/Microsoft.Management/managementGroups/20000000-0001-0000-0000-000000000000"),
                    Map.of("id", "/providers/Microsoft.Management/managementGroups/20000000-0002-0000-0000-000000000000")),
                Map.entry("subnets",                 
                    Map.of("id", "/subscriptions/subscriptionC/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetC/subnets/subnetA"),
                    Map.of("id", "/subscriptions/subscriptionC/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetC/subnets/subnetB")),
                Map.entry("subscriptions",                 
                    Map.of("id", "subscriptionA"),
                    Map.of("id", "subscriptionB")),
                Map.entry("virtualNetworks",                 
                    Map.of("id", "/subscriptions/subscriptionC/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetA"),
                    Map.of("id", "/subscriptions/subscriptionC/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetB"))
            ))
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedNetwork = new azure_native.managednetwork.ManagedNetwork("managedNetwork", {
    location: "eastus",
    managedNetworkName: "myManagedNetwork",
    resourceGroupName: "myResourceGroup",
    scope: {
        managementGroups: [
            {
                id: "/providers/Microsoft.Management/managementGroups/20000000-0001-0000-0000-000000000000",
            },
            {
                id: "/providers/Microsoft.Management/managementGroups/20000000-0002-0000-0000-000000000000",
            },
        ],
        subnets: [
            {
                id: "/subscriptions/subscriptionC/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetC/subnets/subnetA",
            },
            {
                id: "/subscriptions/subscriptionC/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetC/subnets/subnetB",
            },
        ],
        subscriptions: [
            {
                id: "subscriptionA",
            },
            {
                id: "subscriptionB",
            },
        ],
        virtualNetworks: [
            {
                id: "/subscriptions/subscriptionC/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetA",
            },
            {
                id: "/subscriptions/subscriptionC/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetB",
            },
        ],
    },
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_network = azure_native.managednetwork.ManagedNetwork("managedNetwork",
    location="eastus",
    managed_network_name="myManagedNetwork",
    resource_group_name="myResourceGroup",
    scope=azure_native.managednetwork.ScopeResponseArgs(
        management_groups=[
            azure_native.managednetwork.ResourceIdArgs(
                id="/providers/Microsoft.Management/managementGroups/20000000-0001-0000-0000-000000000000",
            ),
            azure_native.managednetwork.ResourceIdArgs(
                id="/providers/Microsoft.Management/managementGroups/20000000-0002-0000-0000-000000000000",
            ),
        ],
        subnets=[
            azure_native.managednetwork.ResourceIdArgs(
                id="/subscriptions/subscriptionC/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetC/subnets/subnetA",
            ),
            azure_native.managednetwork.ResourceIdArgs(
                id="/subscriptions/subscriptionC/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetC/subnets/subnetB",
            ),
        ],
        subscriptions=[
            azure_native.managednetwork.ResourceIdArgs(
                id="subscriptionA",
            ),
            azure_native.managednetwork.ResourceIdArgs(
                id="subscriptionB",
            ),
        ],
        virtual_networks=[
            azure_native.managednetwork.ResourceIdArgs(
                id="/subscriptions/subscriptionC/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetA",
            ),
            azure_native.managednetwork.ResourceIdArgs(
                id="/subscriptions/subscriptionC/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetB",
            ),
        ],
    ),
    tags={})

```

```yaml
resources:
  managedNetwork:
    type: azure-native:managednetwork:ManagedNetwork
    properties:
      location: eastus
      managedNetworkName: myManagedNetwork
      resourceGroupName: myResourceGroup
      scope:
        managementGroups:
          - id: /providers/Microsoft.Management/managementGroups/20000000-0001-0000-0000-000000000000
          - id: /providers/Microsoft.Management/managementGroups/20000000-0002-0000-0000-000000000000
        subnets:
          - id: /subscriptions/subscriptionC/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetC/subnets/subnetA
          - id: /subscriptions/subscriptionC/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetC/subnets/subnetB
        subscriptions:
          - id: subscriptionA
          - id: subscriptionB
        virtualNetworks:
          - id: /subscriptions/subscriptionC/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetA
          - id: /subscriptions/subscriptionC/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/VnetB
      tags: {}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:managednetwork:ManagedNetwork myManagedNetwork /subscriptions/subscriptionA/resourceGroups/myResourceGroup/providers/Microsoft.ManagedNetwork/managedNetworks/myManagedNetwork 
```
