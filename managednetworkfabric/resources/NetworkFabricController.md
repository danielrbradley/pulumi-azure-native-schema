The NetworkFabricController resource definition.
API Version: 2023-02-01-preview.
Previous API Version: 2023-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### NetworkFabricControllers_Create_MaximumSet_Gen
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var networkFabricController = new AzureNative.ManagedNetworkFabric.NetworkFabricController("networkFabricController", new()
    {
        Annotation = "lab 1",
        InfrastructureExpressRouteConnections = new[]
        {
            new AzureNative.ManagedNetworkFabric.Inputs.ExpressRouteConnectionInformationArgs
            {
                ExpressRouteAuthorizationKey = "xxxxxxx",
                ExpressRouteCircuitId = "/subscriptions/xxxxx/resourceGroups/resourceGroupName/providers/Microsoft.Network/expressRouteCircuits/expressRouteCircuitName",
            },
        },
        Ipv4AddressSpace = "172.253.0.0/19",
        Location = "eastus",
        ManagedResourceGroupConfiguration = new AzureNative.ManagedNetworkFabric.Inputs.NetworkFabricControllerPropertiesManagedResourceGroupConfigurationArgs
        {
            Location = "eastus",
            Name = "managedResourceGroupName",
        },
        NetworkFabricControllerName = "NetworkControllerName",
        ResourceGroupName = "resourceGroupName",
        WorkloadExpressRouteConnections = new[]
        {
            new AzureNative.ManagedNetworkFabric.Inputs.ExpressRouteConnectionInformationArgs
            {
                ExpressRouteAuthorizationKey = "xxxxx",
                ExpressRouteCircuitId = "/subscriptions/xxxxx/resourceGroups/resourceGroupName/providers/Microsoft.Network/expressRouteCircuits/expressRouteCircuitName",
            },
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
		_, err := managednetworkfabric.NewNetworkFabricController(ctx, "networkFabricController", &managednetworkfabric.NetworkFabricControllerArgs{
			Annotation: pulumi.String("lab 1"),
			InfrastructureExpressRouteConnections: []managednetworkfabric.ExpressRouteConnectionInformationArgs{
				{
					ExpressRouteAuthorizationKey: pulumi.String("xxxxxxx"),
					ExpressRouteCircuitId:        pulumi.String("/subscriptions/xxxxx/resourceGroups/resourceGroupName/providers/Microsoft.Network/expressRouteCircuits/expressRouteCircuitName"),
				},
			},
			Ipv4AddressSpace: pulumi.String("172.253.0.0/19"),
			Location:         pulumi.String("eastus"),
			ManagedResourceGroupConfiguration: &managednetworkfabric.NetworkFabricControllerPropertiesManagedResourceGroupConfigurationArgs{
				Location: pulumi.String("eastus"),
				Name:     pulumi.String("managedResourceGroupName"),
			},
			NetworkFabricControllerName: pulumi.String("NetworkControllerName"),
			ResourceGroupName:           pulumi.String("resourceGroupName"),
			WorkloadExpressRouteConnections: []managednetworkfabric.ExpressRouteConnectionInformationArgs{
				{
					ExpressRouteAuthorizationKey: pulumi.String("xxxxx"),
					ExpressRouteCircuitId:        pulumi.String("/subscriptions/xxxxx/resourceGroups/resourceGroupName/providers/Microsoft.Network/expressRouteCircuits/expressRouteCircuitName"),
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
import com.pulumi.azurenative.managednetworkfabric.NetworkFabricController;
import com.pulumi.azurenative.managednetworkfabric.NetworkFabricControllerArgs;
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
        var networkFabricController = new NetworkFabricController("networkFabricController", NetworkFabricControllerArgs.builder()        
            .annotation("lab 1")
            .infrastructureExpressRouteConnections(Map.ofEntries(
                Map.entry("expressRouteAuthorizationKey", "xxxxxxx"),
                Map.entry("expressRouteCircuitId", "/subscriptions/xxxxx/resourceGroups/resourceGroupName/providers/Microsoft.Network/expressRouteCircuits/expressRouteCircuitName")
            ))
            .ipv4AddressSpace("172.253.0.0/19")
            .location("eastus")
            .managedResourceGroupConfiguration(Map.ofEntries(
                Map.entry("location", "eastus"),
                Map.entry("name", "managedResourceGroupName")
            ))
            .networkFabricControllerName("NetworkControllerName")
            .resourceGroupName("resourceGroupName")
            .workloadExpressRouteConnections(Map.ofEntries(
                Map.entry("expressRouteAuthorizationKey", "xxxxx"),
                Map.entry("expressRouteCircuitId", "/subscriptions/xxxxx/resourceGroups/resourceGroupName/providers/Microsoft.Network/expressRouteCircuits/expressRouteCircuitName")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const networkFabricController = new azure_native.managednetworkfabric.NetworkFabricController("networkFabricController", {
    annotation: "lab 1",
    infrastructureExpressRouteConnections: [{
        expressRouteAuthorizationKey: "xxxxxxx",
        expressRouteCircuitId: "/subscriptions/xxxxx/resourceGroups/resourceGroupName/providers/Microsoft.Network/expressRouteCircuits/expressRouteCircuitName",
    }],
    ipv4AddressSpace: "172.253.0.0/19",
    location: "eastus",
    managedResourceGroupConfiguration: {
        location: "eastus",
        name: "managedResourceGroupName",
    },
    networkFabricControllerName: "NetworkControllerName",
    resourceGroupName: "resourceGroupName",
    workloadExpressRouteConnections: [{
        expressRouteAuthorizationKey: "xxxxx",
        expressRouteCircuitId: "/subscriptions/xxxxx/resourceGroups/resourceGroupName/providers/Microsoft.Network/expressRouteCircuits/expressRouteCircuitName",
    }],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

network_fabric_controller = azure_native.managednetworkfabric.NetworkFabricController("networkFabricController",
    annotation="lab 1",
    infrastructure_express_route_connections=[azure_native.managednetworkfabric.ExpressRouteConnectionInformationArgs(
        express_route_authorization_key="xxxxxxx",
        express_route_circuit_id="/subscriptions/xxxxx/resourceGroups/resourceGroupName/providers/Microsoft.Network/expressRouteCircuits/expressRouteCircuitName",
    )],
    ipv4_address_space="172.253.0.0/19",
    location="eastus",
    managed_resource_group_configuration=azure_native.managednetworkfabric.NetworkFabricControllerPropertiesManagedResourceGroupConfigurationArgs(
        location="eastus",
        name="managedResourceGroupName",
    ),
    network_fabric_controller_name="NetworkControllerName",
    resource_group_name="resourceGroupName",
    workload_express_route_connections=[azure_native.managednetworkfabric.ExpressRouteConnectionInformationArgs(
        express_route_authorization_key="xxxxx",
        express_route_circuit_id="/subscriptions/xxxxx/resourceGroups/resourceGroupName/providers/Microsoft.Network/expressRouteCircuits/expressRouteCircuitName",
    )])

```

```yaml
resources:
  networkFabricController:
    type: azure-native:managednetworkfabric:NetworkFabricController
    properties:
      annotation: lab 1
      infrastructureExpressRouteConnections:
        - expressRouteAuthorizationKey: xxxxxxx
          expressRouteCircuitId: /subscriptions/xxxxx/resourceGroups/resourceGroupName/providers/Microsoft.Network/expressRouteCircuits/expressRouteCircuitName
      ipv4AddressSpace: 172.253.0.0/19
      location: eastus
      managedResourceGroupConfiguration:
        location: eastus
        name: managedResourceGroupName
      networkFabricControllerName: NetworkControllerName
      resourceGroupName: resourceGroupName
      workloadExpressRouteConnections:
        - expressRouteAuthorizationKey: xxxxx
          expressRouteCircuitId: /subscriptions/xxxxx/resourceGroups/resourceGroupName/providers/Microsoft.Network/expressRouteCircuits/expressRouteCircuitName

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:managednetworkfabric:NetworkFabricController NetworkFabricName /subscriptions/xxxxx/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkFabricControllers/networkFabricControllerName 
```
