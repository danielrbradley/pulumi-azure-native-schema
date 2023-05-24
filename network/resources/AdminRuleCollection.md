Defines the admin rule collection.
API Version: 2022-09-01.
Previous API Version: 2021-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or Update an admin rule collection
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var adminRuleCollection = new AzureNative.Network.AdminRuleCollection("adminRuleCollection", new()
    {
        AppliesToGroups = new[]
        {
            new AzureNative.Network.Inputs.NetworkManagerSecurityGroupItemArgs
            {
                NetworkGroupId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/rg1/providers/Microsoft.Network/networkManagers/testNetworkManager/networkGroups/testGroup",
            },
        },
        ConfigurationName = "myTestSecurityConfig",
        Description = "A sample policy",
        NetworkManagerName = "testNetworkManager",
        ResourceGroupName = "rg1",
        RuleCollectionName = "testRuleCollection",
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
		_, err := network.NewAdminRuleCollection(ctx, "adminRuleCollection", &network.AdminRuleCollectionArgs{
			AppliesToGroups: []network.NetworkManagerSecurityGroupItemArgs{
				{
					NetworkGroupId: pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/rg1/providers/Microsoft.Network/networkManagers/testNetworkManager/networkGroups/testGroup"),
				},
			},
			ConfigurationName:  pulumi.String("myTestSecurityConfig"),
			Description:        pulumi.String("A sample policy"),
			NetworkManagerName: pulumi.String("testNetworkManager"),
			ResourceGroupName:  pulumi.String("rg1"),
			RuleCollectionName: pulumi.String("testRuleCollection"),
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
import com.pulumi.azurenative.network.AdminRuleCollection;
import com.pulumi.azurenative.network.AdminRuleCollectionArgs;
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
        var adminRuleCollection = new AdminRuleCollection("adminRuleCollection", AdminRuleCollectionArgs.builder()        
            .appliesToGroups(Map.of("networkGroupId", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/rg1/providers/Microsoft.Network/networkManagers/testNetworkManager/networkGroups/testGroup"))
            .configurationName("myTestSecurityConfig")
            .description("A sample policy")
            .networkManagerName("testNetworkManager")
            .resourceGroupName("rg1")
            .ruleCollectionName("testRuleCollection")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const adminRuleCollection = new azure_native.network.AdminRuleCollection("adminRuleCollection", {
    appliesToGroups: [{
        networkGroupId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/rg1/providers/Microsoft.Network/networkManagers/testNetworkManager/networkGroups/testGroup",
    }],
    configurationName: "myTestSecurityConfig",
    description: "A sample policy",
    networkManagerName: "testNetworkManager",
    resourceGroupName: "rg1",
    ruleCollectionName: "testRuleCollection",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

admin_rule_collection = azure_native.network.AdminRuleCollection("adminRuleCollection",
    applies_to_groups=[azure_native.network.NetworkManagerSecurityGroupItemArgs(
        network_group_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/rg1/providers/Microsoft.Network/networkManagers/testNetworkManager/networkGroups/testGroup",
    )],
    configuration_name="myTestSecurityConfig",
    description="A sample policy",
    network_manager_name="testNetworkManager",
    resource_group_name="rg1",
    rule_collection_name="testRuleCollection")

```

```yaml
resources:
  adminRuleCollection:
    type: azure-native:network:AdminRuleCollection
    properties:
      appliesToGroups:
        - networkGroupId: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/rg1/providers/Microsoft.Network/networkManagers/testNetworkManager/networkGroups/testGroup
      configurationName: myTestSecurityConfig
      description: A sample policy
      networkManagerName: testNetworkManager
      resourceGroupName: rg1
      ruleCollectionName: testRuleCollection

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:AdminRuleCollection myTestSecurityConfig /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/rg1/providers/Microsoft.Network/networkManager/testNetworkManager/securityAdminConfigurations/myTestSecurityConfig/ruleCollections/testRuleCollection 
```
