The Managed Network resource
API Version: 2022-09-01.
Previous API Version: 2021-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Put Network Manager
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var networkManager = new AzureNative.Network.NetworkManager("networkManager", new()
    {
        Description = "My Test Network Manager",
        NetworkManagerName = "TestNetworkManager",
        NetworkManagerScopeAccesses = new[]
        {
            "Connectivity",
        },
        NetworkManagerScopes = new AzureNative.Network.Inputs.NetworkManagerPropertiesNetworkManagerScopesArgs
        {
            ManagementGroups = new[]
            {
                "/Microsoft.Management/testmg",
            },
            Subscriptions = new[]
            {
                "/subscriptions/00000000-0000-0000-0000-000000000000",
            },
        },
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
		_, err := network.NewNetworkManager(ctx, "networkManager", &network.NetworkManagerArgs{
			Description:        pulumi.String("My Test Network Manager"),
			NetworkManagerName: pulumi.String("TestNetworkManager"),
			NetworkManagerScopeAccesses: pulumi.StringArray{
				pulumi.String("Connectivity"),
			},
			NetworkManagerScopes: &network.NetworkManagerPropertiesNetworkManagerScopesArgs{
				ManagementGroups: pulumi.StringArray{
					pulumi.String("/Microsoft.Management/testmg"),
				},
				Subscriptions: pulumi.StringArray{
					pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000"),
				},
			},
			ResourceGroupName: pulumi.String("rg1"),
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
import com.pulumi.azurenative.network.NetworkManager;
import com.pulumi.azurenative.network.NetworkManagerArgs;
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
        var networkManager = new NetworkManager("networkManager", NetworkManagerArgs.builder()        
            .description("My Test Network Manager")
            .networkManagerName("TestNetworkManager")
            .networkManagerScopeAccesses("Connectivity")
            .networkManagerScopes(Map.ofEntries(
                Map.entry("managementGroups", "/Microsoft.Management/testmg"),
                Map.entry("subscriptions", "/subscriptions/00000000-0000-0000-0000-000000000000")
            ))
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const networkManager = new azure_native.network.NetworkManager("networkManager", {
    description: "My Test Network Manager",
    networkManagerName: "TestNetworkManager",
    networkManagerScopeAccesses: ["Connectivity"],
    networkManagerScopes: {
        managementGroups: ["/Microsoft.Management/testmg"],
        subscriptions: ["/subscriptions/00000000-0000-0000-0000-000000000000"],
    },
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

network_manager = azure_native.network.NetworkManager("networkManager",
    description="My Test Network Manager",
    network_manager_name="TestNetworkManager",
    network_manager_scope_accesses=["Connectivity"],
    network_manager_scopes=azure_native.network.NetworkManagerPropertiesNetworkManagerScopesArgs(
        management_groups=["/Microsoft.Management/testmg"],
        subscriptions=["/subscriptions/00000000-0000-0000-0000-000000000000"],
    ),
    resource_group_name="rg1")

```

```yaml
resources:
  networkManager:
    type: azure-native:network:NetworkManager
    properties:
      description: My Test Network Manager
      networkManagerName: TestNetworkManager
      networkManagerScopeAccesses:
        - Connectivity
      networkManagerScopes:
        managementGroups:
          - /Microsoft.Management/testmg
        subscriptions:
          - /subscriptions/00000000-0000-0000-0000-000000000000
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:NetworkManager TestNetworkManager /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroup/rg1/providers/Microsoft.Network/networkManagers/TestNetworkManager 
```
