The routing intent child resource of a Virtual hub.
API Version: 2022-09-01.
Previous API Version: 2022-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### RouteTablePut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var routingIntent = new AzureNative.Network.RoutingIntent("routingIntent", new()
    {
        ResourceGroupName = "rg1",
        RoutingIntentName = "Intent1",
        RoutingPolicies = new[]
        {
            new AzureNative.Network.Inputs.RoutingPolicyArgs
            {
                Destinations = new[]
                {
                    "Internet",
                },
                Name = "InternetTraffic",
                NextHop = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/azureFirewalls/azfw1",
            },
            new AzureNative.Network.Inputs.RoutingPolicyArgs
            {
                Destinations = new[]
                {
                    "PrivateTraffic",
                },
                Name = "PrivateTrafficPolicy",
                NextHop = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/azureFirewalls/azfw1",
            },
        },
        VirtualHubName = "virtualHub1",
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
		_, err := network.NewRoutingIntent(ctx, "routingIntent", &network.RoutingIntentArgs{
			ResourceGroupName: pulumi.String("rg1"),
			RoutingIntentName: pulumi.String("Intent1"),
			RoutingPolicies: []network.RoutingPolicyArgs{
				{
					Destinations: pulumi.StringArray{
						pulumi.String("Internet"),
					},
					Name:    pulumi.String("InternetTraffic"),
					NextHop: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/azureFirewalls/azfw1"),
				},
				{
					Destinations: pulumi.StringArray{
						pulumi.String("PrivateTraffic"),
					},
					Name:    pulumi.String("PrivateTrafficPolicy"),
					NextHop: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/azureFirewalls/azfw1"),
				},
			},
			VirtualHubName: pulumi.String("virtualHub1"),
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
import com.pulumi.azurenative.network.RoutingIntent;
import com.pulumi.azurenative.network.RoutingIntentArgs;
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
        var routingIntent = new RoutingIntent("routingIntent", RoutingIntentArgs.builder()        
            .resourceGroupName("rg1")
            .routingIntentName("Intent1")
            .routingPolicies(            
                Map.ofEntries(
                    Map.entry("destinations", "Internet"),
                    Map.entry("name", "InternetTraffic"),
                    Map.entry("nextHop", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/azureFirewalls/azfw1")
                ),
                Map.ofEntries(
                    Map.entry("destinations", "PrivateTraffic"),
                    Map.entry("name", "PrivateTrafficPolicy"),
                    Map.entry("nextHop", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/azureFirewalls/azfw1")
                ))
            .virtualHubName("virtualHub1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const routingIntent = new azure_native.network.RoutingIntent("routingIntent", {
    resourceGroupName: "rg1",
    routingIntentName: "Intent1",
    routingPolicies: [
        {
            destinations: ["Internet"],
            name: "InternetTraffic",
            nextHop: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/azureFirewalls/azfw1",
        },
        {
            destinations: ["PrivateTraffic"],
            name: "PrivateTrafficPolicy",
            nextHop: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/azureFirewalls/azfw1",
        },
    ],
    virtualHubName: "virtualHub1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

routing_intent = azure_native.network.RoutingIntent("routingIntent",
    resource_group_name="rg1",
    routing_intent_name="Intent1",
    routing_policies=[
        azure_native.network.RoutingPolicyArgs(
            destinations=["Internet"],
            name="InternetTraffic",
            next_hop="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/azureFirewalls/azfw1",
        ),
        azure_native.network.RoutingPolicyArgs(
            destinations=["PrivateTraffic"],
            name="PrivateTrafficPolicy",
            next_hop="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/azureFirewalls/azfw1",
        ),
    ],
    virtual_hub_name="virtualHub1")

```

```yaml
resources:
  routingIntent:
    type: azure-native:network:RoutingIntent
    properties:
      resourceGroupName: rg1
      routingIntentName: Intent1
      routingPolicies:
        - destinations:
            - Internet
          name: InternetTraffic
          nextHop: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/azureFirewalls/azfw1
        - destinations:
            - PrivateTraffic
          name: PrivateTrafficPolicy
          nextHop: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/azureFirewalls/azfw1
      virtualHubName: virtualHub1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:RoutingIntent Intent1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub1/routingIntent/Intent1 
```
