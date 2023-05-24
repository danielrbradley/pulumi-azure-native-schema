A global reach connection resource
API Version: 2022-05-01.
Previous API Version: 2020-07-17-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### GlobalReachConnections_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var globalReachConnection = new AzureNative.AVS.GlobalReachConnection("globalReachConnection", new()
    {
        AuthorizationKey = "01010101-0101-0101-0101-010101010101",
        GlobalReachConnectionName = "connection1",
        PeerExpressRouteCircuit = "/subscriptions/12341234-1234-1234-1234-123412341234/resourceGroups/mygroup/providers/Microsoft.Network/expressRouteCircuits/mypeer",
        PrivateCloudName = "cloud1",
        ResourceGroupName = "group1",
    });

});


```

```go
package main

import (
	avs "github.com/pulumi/pulumi-azure-native-sdk/avs"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := avs.NewGlobalReachConnection(ctx, "globalReachConnection", &avs.GlobalReachConnectionArgs{
			AuthorizationKey:          pulumi.String("01010101-0101-0101-0101-010101010101"),
			GlobalReachConnectionName: pulumi.String("connection1"),
			PeerExpressRouteCircuit:   pulumi.String("/subscriptions/12341234-1234-1234-1234-123412341234/resourceGroups/mygroup/providers/Microsoft.Network/expressRouteCircuits/mypeer"),
			PrivateCloudName:          pulumi.String("cloud1"),
			ResourceGroupName:         pulumi.String("group1"),
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
import com.pulumi.azurenative.avs.GlobalReachConnection;
import com.pulumi.azurenative.avs.GlobalReachConnectionArgs;
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
        var globalReachConnection = new GlobalReachConnection("globalReachConnection", GlobalReachConnectionArgs.builder()        
            .authorizationKey("01010101-0101-0101-0101-010101010101")
            .globalReachConnectionName("connection1")
            .peerExpressRouteCircuit("/subscriptions/12341234-1234-1234-1234-123412341234/resourceGroups/mygroup/providers/Microsoft.Network/expressRouteCircuits/mypeer")
            .privateCloudName("cloud1")
            .resourceGroupName("group1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const globalReachConnection = new azure_native.avs.GlobalReachConnection("globalReachConnection", {
    authorizationKey: "01010101-0101-0101-0101-010101010101",
    globalReachConnectionName: "connection1",
    peerExpressRouteCircuit: "/subscriptions/12341234-1234-1234-1234-123412341234/resourceGroups/mygroup/providers/Microsoft.Network/expressRouteCircuits/mypeer",
    privateCloudName: "cloud1",
    resourceGroupName: "group1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

global_reach_connection = azure_native.avs.GlobalReachConnection("globalReachConnection",
    authorization_key="01010101-0101-0101-0101-010101010101",
    global_reach_connection_name="connection1",
    peer_express_route_circuit="/subscriptions/12341234-1234-1234-1234-123412341234/resourceGroups/mygroup/providers/Microsoft.Network/expressRouteCircuits/mypeer",
    private_cloud_name="cloud1",
    resource_group_name="group1")

```

```yaml
resources:
  globalReachConnection:
    type: azure-native:avs:GlobalReachConnection
    properties:
      authorizationKey: 01010101-0101-0101-0101-010101010101
      globalReachConnectionName: connection1
      peerExpressRouteCircuit: /subscriptions/12341234-1234-1234-1234-123412341234/resourceGroups/mygroup/providers/Microsoft.Network/expressRouteCircuits/mypeer
      privateCloudName: cloud1
      resourceGroupName: group1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:avs:GlobalReachConnection connection1 /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/group1/providers/Microsoft.AVS/privateClouds/cloud1/globalReachConnections/connection1 
```
