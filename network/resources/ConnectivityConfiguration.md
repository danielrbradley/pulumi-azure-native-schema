The network manager connectivity configuration resource
API Version: 2022-09-01.
Previous API Version: 2021-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ConnectivityConfigurationsPut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var connectivityConfiguration = new AzureNative.Network.ConnectivityConfiguration("connectivityConfiguration", new()
    {
        AppliesToGroups = new[]
        {
            new AzureNative.Network.Inputs.ConnectivityGroupItemArgs
            {
                GroupConnectivity = "None",
                IsGlobal = "False",
                NetworkGroupId = "subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkManagers/testNetworkManager/networkGroups/group1",
                UseHubGateway = "True",
            },
        },
        ConfigurationName = "myTestConnectivityConfig",
        ConnectivityTopology = "HubAndSpoke",
        DeleteExistingPeering = "True",
        Description = "Sample Configuration",
        Hubs = new[]
        {
            new AzureNative.Network.Inputs.HubArgs
            {
                ResourceId = "subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myTestConnectivityConfig",
                ResourceType = "Microsoft.Network/virtualNetworks",
            },
        },
        IsGlobal = "True",
        NetworkManagerName = "testNetworkManager",
        ResourceGroupName = "myResourceGroup",
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
		_, err := network.NewConnectivityConfiguration(ctx, "connectivityConfiguration", &network.ConnectivityConfigurationArgs{
			AppliesToGroups: []network.ConnectivityGroupItemArgs{
				{
					GroupConnectivity: pulumi.String("None"),
					IsGlobal:          pulumi.String("False"),
					NetworkGroupId:    pulumi.String("subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkManagers/testNetworkManager/networkGroups/group1"),
					UseHubGateway:     pulumi.String("True"),
				},
			},
			ConfigurationName:     pulumi.String("myTestConnectivityConfig"),
			ConnectivityTopology:  pulumi.String("HubAndSpoke"),
			DeleteExistingPeering: pulumi.String("True"),
			Description:           pulumi.String("Sample Configuration"),
			Hubs: []network.HubArgs{
				{
					ResourceId:   pulumi.String("subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myTestConnectivityConfig"),
					ResourceType: pulumi.String("Microsoft.Network/virtualNetworks"),
				},
			},
			IsGlobal:           pulumi.String("True"),
			NetworkManagerName: pulumi.String("testNetworkManager"),
			ResourceGroupName:  pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.network.ConnectivityConfiguration;
import com.pulumi.azurenative.network.ConnectivityConfigurationArgs;
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
        var connectivityConfiguration = new ConnectivityConfiguration("connectivityConfiguration", ConnectivityConfigurationArgs.builder()        
            .appliesToGroups(Map.ofEntries(
                Map.entry("groupConnectivity", "None"),
                Map.entry("isGlobal", "False"),
                Map.entry("networkGroupId", "subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkManagers/testNetworkManager/networkGroups/group1"),
                Map.entry("useHubGateway", "True")
            ))
            .configurationName("myTestConnectivityConfig")
            .connectivityTopology("HubAndSpoke")
            .deleteExistingPeering("True")
            .description("Sample Configuration")
            .hubs(Map.ofEntries(
                Map.entry("resourceId", "subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myTestConnectivityConfig"),
                Map.entry("resourceType", "Microsoft.Network/virtualNetworks")
            ))
            .isGlobal("True")
            .networkManagerName("testNetworkManager")
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const connectivityConfiguration = new azure_native.network.ConnectivityConfiguration("connectivityConfiguration", {
    appliesToGroups: [{
        groupConnectivity: "None",
        isGlobal: "False",
        networkGroupId: "subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkManagers/testNetworkManager/networkGroups/group1",
        useHubGateway: "True",
    }],
    configurationName: "myTestConnectivityConfig",
    connectivityTopology: "HubAndSpoke",
    deleteExistingPeering: "True",
    description: "Sample Configuration",
    hubs: [{
        resourceId: "subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myTestConnectivityConfig",
        resourceType: "Microsoft.Network/virtualNetworks",
    }],
    isGlobal: "True",
    networkManagerName: "testNetworkManager",
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

connectivity_configuration = azure_native.network.ConnectivityConfiguration("connectivityConfiguration",
    applies_to_groups=[azure_native.network.ConnectivityGroupItemArgs(
        group_connectivity="None",
        is_global="False",
        network_group_id="subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkManagers/testNetworkManager/networkGroups/group1",
        use_hub_gateway="True",
    )],
    configuration_name="myTestConnectivityConfig",
    connectivity_topology="HubAndSpoke",
    delete_existing_peering="True",
    description="Sample Configuration",
    hubs=[azure_native.network.HubArgs(
        resource_id="subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myTestConnectivityConfig",
        resource_type="Microsoft.Network/virtualNetworks",
    )],
    is_global="True",
    network_manager_name="testNetworkManager",
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  connectivityConfiguration:
    type: azure-native:network:ConnectivityConfiguration
    properties:
      appliesToGroups:
        - groupConnectivity: None
          isGlobal: False
          networkGroupId: subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkManagers/testNetworkManager/networkGroups/group1
          useHubGateway: True
      configurationName: myTestConnectivityConfig
      connectivityTopology: HubAndSpoke
      deleteExistingPeering: True
      description: Sample Configuration
      hubs:
        - resourceId: subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myTestConnectivityConfig
          resourceType: Microsoft.Network/virtualNetworks
      isGlobal: True
      networkManagerName: testNetworkManager
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:ConnectivityConfiguration myTestConnectivityConfig subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkManagers/testNetworkManager/connectivityConfigurations/myTestConnectivityConfig 
```
