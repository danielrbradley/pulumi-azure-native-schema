The Managed Network Peering Policy resource
API Version: 2019-06-01-preview.
Previous API Version: 2019-06-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ManagedNetworkPeeringPoliciesPut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedNetworkPeeringPolicy = new AzureNative.ManagedNetwork.ManagedNetworkPeeringPolicy("managedNetworkPeeringPolicy", new()
    {
        ManagedNetworkName = "myManagedNetwork",
        ManagedNetworkPeeringPolicyName = "myHubAndSpoke",
        Properties = new AzureNative.ManagedNetwork.Inputs.ManagedNetworkPeeringPolicyPropertiesArgs
        {
            Hub = new AzureNative.ManagedNetwork.Inputs.ResourceIdArgs
            {
                Id = "/subscriptionB/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myHubVnet",
            },
            Spokes = new[]
            {
                new AzureNative.ManagedNetwork.Inputs.ResourceIdArgs
                {
                    Id = "/subscriptionB/resourceGroups/myResourceGroup/providers/Microsoft.ManagedNetwork/managedNetworks/myManagedNetwork/managedNetworkGroups/myManagedNetworkGroup1",
                },
            },
            Type = "HubAndSpokeTopology",
        },
        ResourceGroupName = "myResourceGroup",
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
		_, err := managednetwork.NewManagedNetworkPeeringPolicy(ctx, "managedNetworkPeeringPolicy", &managednetwork.ManagedNetworkPeeringPolicyArgs{
			ManagedNetworkName:              pulumi.String("myManagedNetwork"),
			ManagedNetworkPeeringPolicyName: pulumi.String("myHubAndSpoke"),
			Properties: managednetwork.ManagedNetworkPeeringPolicyPropertiesResponse{
				Hub: &managednetwork.ResourceIdArgs{
					Id: pulumi.String("/subscriptionB/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myHubVnet"),
				},
				Spokes: managednetwork.ResourceIdArray{
					&managednetwork.ResourceIdArgs{
						Id: pulumi.String("/subscriptionB/resourceGroups/myResourceGroup/providers/Microsoft.ManagedNetwork/managedNetworks/myManagedNetwork/managedNetworkGroups/myManagedNetworkGroup1"),
					},
				},
				Type: pulumi.String("HubAndSpokeTopology"),
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.managednetwork.ManagedNetworkPeeringPolicy;
import com.pulumi.azurenative.managednetwork.ManagedNetworkPeeringPolicyArgs;
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
        var managedNetworkPeeringPolicy = new ManagedNetworkPeeringPolicy("managedNetworkPeeringPolicy", ManagedNetworkPeeringPolicyArgs.builder()        
            .managedNetworkName("myManagedNetwork")
            .managedNetworkPeeringPolicyName("myHubAndSpoke")
            .properties(Map.ofEntries(
                Map.entry("hub", Map.of("id", "/subscriptionB/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myHubVnet")),
                Map.entry("spokes", Map.of("id", "/subscriptionB/resourceGroups/myResourceGroup/providers/Microsoft.ManagedNetwork/managedNetworks/myManagedNetwork/managedNetworkGroups/myManagedNetworkGroup1")),
                Map.entry("type", "HubAndSpokeTopology")
            ))
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedNetworkPeeringPolicy = new azure_native.managednetwork.ManagedNetworkPeeringPolicy("managedNetworkPeeringPolicy", {
    managedNetworkName: "myManagedNetwork",
    managedNetworkPeeringPolicyName: "myHubAndSpoke",
    properties: {
        hub: {
            id: "/subscriptionB/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myHubVnet",
        },
        spokes: [{
            id: "/subscriptionB/resourceGroups/myResourceGroup/providers/Microsoft.ManagedNetwork/managedNetworks/myManagedNetwork/managedNetworkGroups/myManagedNetworkGroup1",
        }],
        type: "HubAndSpokeTopology",
    },
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_network_peering_policy = azure_native.managednetwork.ManagedNetworkPeeringPolicy("managedNetworkPeeringPolicy",
    managed_network_name="myManagedNetwork",
    managed_network_peering_policy_name="myHubAndSpoke",
    properties=azure_native.managednetwork.ManagedNetworkPeeringPolicyPropertiesResponseArgs(
        hub=azure_native.managednetwork.ResourceIdArgs(
            id="/subscriptionB/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myHubVnet",
        ),
        spokes=[azure_native.managednetwork.ResourceIdArgs(
            id="/subscriptionB/resourceGroups/myResourceGroup/providers/Microsoft.ManagedNetwork/managedNetworks/myManagedNetwork/managedNetworkGroups/myManagedNetworkGroup1",
        )],
        type="HubAndSpokeTopology",
    ),
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  managedNetworkPeeringPolicy:
    type: azure-native:managednetwork:ManagedNetworkPeeringPolicy
    properties:
      managedNetworkName: myManagedNetwork
      managedNetworkPeeringPolicyName: myHubAndSpoke
      properties:
        hub:
          id: /subscriptionB/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myHubVnet
        spokes:
          - id: /subscriptionB/resourceGroups/myResourceGroup/providers/Microsoft.ManagedNetwork/managedNetworks/myManagedNetwork/managedNetworkGroups/myManagedNetworkGroup1
        type: HubAndSpokeTopology
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:managednetwork:ManagedNetworkPeeringPolicy myHubAndSpoke /subscriptionA/resourceGroups/myResourceGroup/providers/Microsoft.ManagedNetwork/managedNetworks/myManagedNetwork/managedNetworkPeeringPolicies/myHubAndSpoke 
```
