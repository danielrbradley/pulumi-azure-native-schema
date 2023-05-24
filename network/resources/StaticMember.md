StaticMember Item.
API Version: 2022-09-01.
Previous API Version: 2022-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### StaticMemberPut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var staticMember = new AzureNative.Network.StaticMember("staticMember", new()
    {
        NetworkGroupName = "testNetworkGroup",
        NetworkManagerName = "testNetworkManager",
        ResourceGroupName = "rg1",
        ResourceId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroup/rg1/providers/Microsoft.Network/virtualnetworks/vnet1",
        StaticMemberName = "testStaticMember",
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
		_, err := network.NewStaticMember(ctx, "staticMember", &network.StaticMemberArgs{
			NetworkGroupName:   pulumi.String("testNetworkGroup"),
			NetworkManagerName: pulumi.String("testNetworkManager"),
			ResourceGroupName:  pulumi.String("rg1"),
			ResourceId:         pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroup/rg1/providers/Microsoft.Network/virtualnetworks/vnet1"),
			StaticMemberName:   pulumi.String("testStaticMember"),
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
import com.pulumi.azurenative.network.StaticMember;
import com.pulumi.azurenative.network.StaticMemberArgs;
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
        var staticMember = new StaticMember("staticMember", StaticMemberArgs.builder()        
            .networkGroupName("testNetworkGroup")
            .networkManagerName("testNetworkManager")
            .resourceGroupName("rg1")
            .resourceId("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroup/rg1/providers/Microsoft.Network/virtualnetworks/vnet1")
            .staticMemberName("testStaticMember")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const staticMember = new azure_native.network.StaticMember("staticMember", {
    networkGroupName: "testNetworkGroup",
    networkManagerName: "testNetworkManager",
    resourceGroupName: "rg1",
    resourceId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroup/rg1/providers/Microsoft.Network/virtualnetworks/vnet1",
    staticMemberName: "testStaticMember",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

static_member = azure_native.network.StaticMember("staticMember",
    network_group_name="testNetworkGroup",
    network_manager_name="testNetworkManager",
    resource_group_name="rg1",
    resource_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroup/rg1/providers/Microsoft.Network/virtualnetworks/vnet1",
    static_member_name="testStaticMember")

```

```yaml
resources:
  staticMember:
    type: azure-native:network:StaticMember
    properties:
      networkGroupName: testNetworkGroup
      networkManagerName: testNetworkManager
      resourceGroupName: rg1
      resourceId: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroup/rg1/providers/Microsoft.Network/virtualnetworks/vnet1
      staticMemberName: testStaticMember

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:StaticMember testStaticMember /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroup/rg1/providers/Microsoft.Network/networkManagers/testNetworkManager/networkGroups/testNetworkGroup/staticMembers/testStaticMember 
```
