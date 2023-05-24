The NetworkRack resource definition.
API Version: 2023-02-01-preview.
Previous API Version: 2023-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### NetworkRacks_Create_MaximumSet_Gen
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var networkRack = new AzureNative.ManagedNetworkFabric.NetworkRack("networkRack", new()
    {
        Annotation = "null",
        Location = "eastus",
        NetworkFabricId = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkFabrics/networkFabricName",
        NetworkRackName = "networkRackName",
        NetworkRackSku = "RackSKU",
        ResourceGroupName = "resourceGroupName",
        Tags = 
        {
            { "keyID", "keyValue" },
        },
    });

});


```

```go
package main

import (
	managednetworkfabric "github.com/pulumi/pulumi-azure-native-sdk/managednetworkfabric"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := managednetworkfabric.NewNetworkRack(ctx, "networkRack", &managednetworkfabric.NetworkRackArgs{
			Annotation:        pulumi.String("null"),
			Location:          pulumi.String("eastus"),
			NetworkFabricId:   pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkFabrics/networkFabricName"),
			NetworkRackName:   pulumi.String("networkRackName"),
			NetworkRackSku:    pulumi.String("RackSKU"),
			ResourceGroupName: pulumi.String("resourceGroupName"),
			Tags: pulumi.StringMap{
				"keyID": pulumi.String("keyValue"),
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
import com.pulumi.azurenative.managednetworkfabric.NetworkRack;
import com.pulumi.azurenative.managednetworkfabric.NetworkRackArgs;
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
        var networkRack = new NetworkRack("networkRack", NetworkRackArgs.builder()        
            .annotation("null")
            .location("eastus")
            .networkFabricId("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkFabrics/networkFabricName")
            .networkRackName("networkRackName")
            .networkRackSku("RackSKU")
            .resourceGroupName("resourceGroupName")
            .tags(Map.of("keyID", "keyValue"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const networkRack = new azure_native.managednetworkfabric.NetworkRack("networkRack", {
    annotation: "null",
    location: "eastus",
    networkFabricId: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkFabrics/networkFabricName",
    networkRackName: "networkRackName",
    networkRackSku: "RackSKU",
    resourceGroupName: "resourceGroupName",
    tags: {
        keyID: "keyValue",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

network_rack = azure_native.managednetworkfabric.NetworkRack("networkRack",
    annotation="null",
    location="eastus",
    network_fabric_id="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkFabrics/networkFabricName",
    network_rack_name="networkRackName",
    network_rack_sku="RackSKU",
    resource_group_name="resourceGroupName",
    tags={
        "keyID": "keyValue",
    })

```

```yaml
resources:
  networkRack:
    type: azure-native:managednetworkfabric:NetworkRack
    properties:
      annotation: null
      location: eastus
      networkFabricId: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkFabrics/networkFabricName
      networkRackName: networkRackName
      networkRackSku: RackSKU
      resourceGroupName: resourceGroupName
      tags:
        keyID: keyValue

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:managednetworkfabric:NetworkRack networkRackName /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkRacks/networkRackName 
```
