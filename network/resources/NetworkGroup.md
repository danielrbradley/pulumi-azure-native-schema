The network group resource
API Version: 2022-09-01.
Previous API Version: 2021-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### NetworkGroupsPut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var networkGroup = new AzureNative.Network.NetworkGroup("networkGroup", new()
    {
        Description = "A sample group",
        NetworkGroupName = "testNetworkGroup",
        NetworkManagerName = "testNetworkManager",
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
		_, err := network.NewNetworkGroup(ctx, "networkGroup", &network.NetworkGroupArgs{
			Description:        pulumi.String("A sample group"),
			NetworkGroupName:   pulumi.String("testNetworkGroup"),
			NetworkManagerName: pulumi.String("testNetworkManager"),
			ResourceGroupName:  pulumi.String("rg1"),
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
import com.pulumi.azurenative.network.NetworkGroup;
import com.pulumi.azurenative.network.NetworkGroupArgs;
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
        var networkGroup = new NetworkGroup("networkGroup", NetworkGroupArgs.builder()        
            .description("A sample group")
            .networkGroupName("testNetworkGroup")
            .networkManagerName("testNetworkManager")
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const networkGroup = new azure_native.network.NetworkGroup("networkGroup", {
    description: "A sample group",
    networkGroupName: "testNetworkGroup",
    networkManagerName: "testNetworkManager",
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

network_group = azure_native.network.NetworkGroup("networkGroup",
    description="A sample group",
    network_group_name="testNetworkGroup",
    network_manager_name="testNetworkManager",
    resource_group_name="rg1")

```

```yaml
resources:
  networkGroup:
    type: azure-native:network:NetworkGroup
    properties:
      description: A sample group
      networkGroupName: testNetworkGroup
      networkManagerName: testNetworkManager
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:NetworkGroup testNetworkGroup /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroup/rg1/providers/Microsoft.Network/networkManagers/testNetworkManager/networkGroups/testNetworkGroup 
```
