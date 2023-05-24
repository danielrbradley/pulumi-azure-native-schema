Describes a hybrid machine.
API Version: 2022-11-10.
Previous API Version: 2020-08-02. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or Update a Machine
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var machine = new AzureNative.HybridCompute.Machine("machine", new()
    {
        ClientPublicKey = "string",
        Identity = new AzureNative.HybridCompute.Inputs.IdentityArgs
        {
            Type = AzureNative.HybridCompute.ResourceIdentityType.SystemAssigned,
        },
        Location = "eastus2euap",
        LocationData = new AzureNative.HybridCompute.Inputs.LocationDataArgs
        {
            Name = "Redmond",
        },
        MachineName = "myMachine",
        ParentClusterResourceId = "{AzureStackHCIResourceId}",
        PrivateLinkScopeResourceId = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.HybridCompute/privateLinkScopes/privateLinkScopeName",
        ResourceGroupName = "myResourceGroup",
        VmId = "b7a098cc-b0b8-46e8-a205-62f301a62a8f",
    });

});


```

```go
package main

import (
	hybridcompute "github.com/pulumi/pulumi-azure-native-sdk/hybridcompute"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := hybridcompute.NewMachine(ctx, "machine", &hybridcompute.MachineArgs{
			ClientPublicKey: pulumi.String("string"),
			Identity: &hybridcompute.IdentityArgs{
				Type: hybridcompute.ResourceIdentityTypeSystemAssigned,
			},
			Location: pulumi.String("eastus2euap"),
			LocationData: &hybridcompute.LocationDataArgs{
				Name: pulumi.String("Redmond"),
			},
			MachineName:                pulumi.String("myMachine"),
			ParentClusterResourceId:    pulumi.String("{AzureStackHCIResourceId}"),
			PrivateLinkScopeResourceId: pulumi.String("/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.HybridCompute/privateLinkScopes/privateLinkScopeName"),
			ResourceGroupName:          pulumi.String("myResourceGroup"),
			VmId:                       pulumi.String("b7a098cc-b0b8-46e8-a205-62f301a62a8f"),
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
import com.pulumi.azurenative.hybridcompute.Machine;
import com.pulumi.azurenative.hybridcompute.MachineArgs;
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
        var machine = new Machine("machine", MachineArgs.builder()        
            .clientPublicKey("string")
            .identity(Map.of("type", "SystemAssigned"))
            .location("eastus2euap")
            .locationData(Map.of("name", "Redmond"))
            .machineName("myMachine")
            .parentClusterResourceId("{AzureStackHCIResourceId}")
            .privateLinkScopeResourceId("/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.HybridCompute/privateLinkScopes/privateLinkScopeName")
            .resourceGroupName("myResourceGroup")
            .vmId("b7a098cc-b0b8-46e8-a205-62f301a62a8f")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const machine = new azure_native.hybridcompute.Machine("machine", {
    clientPublicKey: "string",
    identity: {
        type: azure_native.hybridcompute.ResourceIdentityType.SystemAssigned,
    },
    location: "eastus2euap",
    locationData: {
        name: "Redmond",
    },
    machineName: "myMachine",
    parentClusterResourceId: "{AzureStackHCIResourceId}",
    privateLinkScopeResourceId: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.HybridCompute/privateLinkScopes/privateLinkScopeName",
    resourceGroupName: "myResourceGroup",
    vmId: "b7a098cc-b0b8-46e8-a205-62f301a62a8f",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

machine = azure_native.hybridcompute.Machine("machine",
    client_public_key="string",
    identity=azure_native.hybridcompute.IdentityArgs(
        type=azure_native.hybridcompute.ResourceIdentityType.SYSTEM_ASSIGNED,
    ),
    location="eastus2euap",
    location_data=azure_native.hybridcompute.LocationDataArgs(
        name="Redmond",
    ),
    machine_name="myMachine",
    parent_cluster_resource_id="{AzureStackHCIResourceId}",
    private_link_scope_resource_id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.HybridCompute/privateLinkScopes/privateLinkScopeName",
    resource_group_name="myResourceGroup",
    vm_id="b7a098cc-b0b8-46e8-a205-62f301a62a8f")

```

```yaml
resources:
  machine:
    type: azure-native:hybridcompute:Machine
    properties:
      clientPublicKey: string
      identity:
        type: SystemAssigned
      location: eastus2euap
      locationData:
        name: Redmond
      machineName: myMachine
      parentClusterResourceId: '{AzureStackHCIResourceId}'
      privateLinkScopeResourceId: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.HybridCompute/privateLinkScopes/privateLinkScopeName
      resourceGroupName: myResourceGroup
      vmId: b7a098cc-b0b8-46e8-a205-62f301a62a8f

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:hybridcompute:Machine myMachine /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.HybridCompute/machines/myMachine 
```
