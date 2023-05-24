Network watcher in a resource group.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create network watcher
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var networkWatcher = new AzureNative.Network.NetworkWatcher("networkWatcher", new()
    {
        Location = "eastus",
        NetworkWatcherName = "nw1",
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
		_, err := network.NewNetworkWatcher(ctx, "networkWatcher", &network.NetworkWatcherArgs{
			Location:           pulumi.String("eastus"),
			NetworkWatcherName: pulumi.String("nw1"),
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
import com.pulumi.azurenative.network.NetworkWatcher;
import com.pulumi.azurenative.network.NetworkWatcherArgs;
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
        var networkWatcher = new NetworkWatcher("networkWatcher", NetworkWatcherArgs.builder()        
            .location("eastus")
            .networkWatcherName("nw1")
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const networkWatcher = new azure_native.network.NetworkWatcher("networkWatcher", {
    location: "eastus",
    networkWatcherName: "nw1",
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

network_watcher = azure_native.network.NetworkWatcher("networkWatcher",
    location="eastus",
    network_watcher_name="nw1",
    resource_group_name="rg1")

```

```yaml
resources:
  networkWatcher:
    type: azure-native:network:NetworkWatcher
    properties:
      location: eastus
      networkWatcherName: nw1
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:NetworkWatcher nw1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/networkWatchers/nw1 
```
