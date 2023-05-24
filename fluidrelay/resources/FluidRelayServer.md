A FluidRelay Server.
API Version: 2022-06-01.
Previous API Version: 2021-03-12-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a Fluid Relay server
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var fluidRelayServer = new AzureNative.FluidRelay.FluidRelayServer("fluidRelayServer", new()
    {
        FluidRelayServerName = "myFluidRelayServer",
        Identity = new AzureNative.FluidRelay.Inputs.IdentityArgs
        {
            Type = AzureNative.FluidRelay.ResourceIdentityType.SystemAssigned,
        },
        Location = "west-us",
        ResourceGroup = "myResourceGroup",
        Storagesku = "basic",
        Tags = 
        {
            { "Category", "sales" },
        },
    });

});


```

```go
package main

import (
	fluidrelay "github.com/pulumi/pulumi-azure-native-sdk/fluidrelay"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := fluidrelay.NewFluidRelayServer(ctx, "fluidRelayServer", &fluidrelay.FluidRelayServerArgs{
			FluidRelayServerName: pulumi.String("myFluidRelayServer"),
			Identity: &fluidrelay.IdentityArgs{
				Type: fluidrelay.ResourceIdentityTypeSystemAssigned,
			},
			Location:      pulumi.String("west-us"),
			ResourceGroup: pulumi.String("myResourceGroup"),
			Storagesku:    pulumi.String("basic"),
			Tags: pulumi.StringMap{
				"Category": pulumi.String("sales"),
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
import com.pulumi.azurenative.fluidrelay.FluidRelayServer;
import com.pulumi.azurenative.fluidrelay.FluidRelayServerArgs;
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
        var fluidRelayServer = new FluidRelayServer("fluidRelayServer", FluidRelayServerArgs.builder()        
            .fluidRelayServerName("myFluidRelayServer")
            .identity(Map.of("type", "SystemAssigned"))
            .location("west-us")
            .resourceGroup("myResourceGroup")
            .storagesku("basic")
            .tags(Map.of("Category", "sales"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const fluidRelayServer = new azure_native.fluidrelay.FluidRelayServer("fluidRelayServer", {
    fluidRelayServerName: "myFluidRelayServer",
    identity: {
        type: azure_native.fluidrelay.ResourceIdentityType.SystemAssigned,
    },
    location: "west-us",
    resourceGroup: "myResourceGroup",
    storagesku: "basic",
    tags: {
        Category: "sales",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

fluid_relay_server = azure_native.fluidrelay.FluidRelayServer("fluidRelayServer",
    fluid_relay_server_name="myFluidRelayServer",
    identity=azure_native.fluidrelay.IdentityArgs(
        type=azure_native.fluidrelay.ResourceIdentityType.SYSTEM_ASSIGNED,
    ),
    location="west-us",
    resource_group="myResourceGroup",
    storagesku="basic",
    tags={
        "Category": "sales",
    })

```

```yaml
resources:
  fluidRelayServer:
    type: azure-native:fluidrelay:FluidRelayServer
    properties:
      fluidRelayServerName: myFluidRelayServer
      identity:
        type: SystemAssigned
      location: west-us
      resourceGroup: myResourceGroup
      storagesku: basic
      tags:
        Category: sales

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:fluidrelay:FluidRelayServer myFluidRelayServer /subscriptions/xxxx-xxxx-xxxx-xxxx/resourceGroups/myResourceGroup/Microsoft.FluidRelay/fluidRelayServers/myFluidRelayServer 
```
