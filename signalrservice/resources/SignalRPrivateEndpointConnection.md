A private endpoint connection to an azure resource
API Version: 2023-02-01.
Previous API Version: 2020-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### SignalRPrivateEndpointConnections_Update
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var signalRPrivateEndpointConnection = new AzureNative.SignalRService.SignalRPrivateEndpointConnection("signalRPrivateEndpointConnection", new()
    {
        PrivateEndpoint = new AzureNative.SignalRService.Inputs.PrivateEndpointArgs
        {
            Id = "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.Network/privateEndpoints/myPrivateEndpoint",
        },
        PrivateEndpointConnectionName = "mysignalrservice.1fa229cd-bf3f-47f0-8c49-afb36723997e",
        PrivateLinkServiceConnectionState = new AzureNative.SignalRService.Inputs.PrivateLinkServiceConnectionStateArgs
        {
            ActionsRequired = "None",
            Status = "Approved",
        },
        ResourceGroupName = "myResourceGroup",
        ResourceName = "mySignalRService",
    });

});


```

```go
package main

import (
	signalrservice "github.com/pulumi/pulumi-azure-native-sdk/signalrservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := signalrservice.NewSignalRPrivateEndpointConnection(ctx, "signalRPrivateEndpointConnection", &signalrservice.SignalRPrivateEndpointConnectionArgs{
			PrivateEndpoint: &signalrservice.PrivateEndpointArgs{
				Id: pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.Network/privateEndpoints/myPrivateEndpoint"),
			},
			PrivateEndpointConnectionName: pulumi.String("mysignalrservice.1fa229cd-bf3f-47f0-8c49-afb36723997e"),
			PrivateLinkServiceConnectionState: &signalrservice.PrivateLinkServiceConnectionStateArgs{
				ActionsRequired: pulumi.String("None"),
				Status:          pulumi.String("Approved"),
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
			ResourceName:      pulumi.String("mySignalRService"),
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
import com.pulumi.azurenative.signalrservice.SignalRPrivateEndpointConnection;
import com.pulumi.azurenative.signalrservice.SignalRPrivateEndpointConnectionArgs;
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
        var signalRPrivateEndpointConnection = new SignalRPrivateEndpointConnection("signalRPrivateEndpointConnection", SignalRPrivateEndpointConnectionArgs.builder()        
            .privateEndpoint(Map.of("id", "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.Network/privateEndpoints/myPrivateEndpoint"))
            .privateEndpointConnectionName("mysignalrservice.1fa229cd-bf3f-47f0-8c49-afb36723997e")
            .privateLinkServiceConnectionState(Map.ofEntries(
                Map.entry("actionsRequired", "None"),
                Map.entry("status", "Approved")
            ))
            .resourceGroupName("myResourceGroup")
            .resourceName("mySignalRService")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const signalRPrivateEndpointConnection = new azure_native.signalrservice.SignalRPrivateEndpointConnection("signalRPrivateEndpointConnection", {
    privateEndpoint: {
        id: "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.Network/privateEndpoints/myPrivateEndpoint",
    },
    privateEndpointConnectionName: "mysignalrservice.1fa229cd-bf3f-47f0-8c49-afb36723997e",
    privateLinkServiceConnectionState: {
        actionsRequired: "None",
        status: "Approved",
    },
    resourceGroupName: "myResourceGroup",
    resourceName: "mySignalRService",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

signal_r_private_endpoint_connection = azure_native.signalrservice.SignalRPrivateEndpointConnection("signalRPrivateEndpointConnection",
    private_endpoint=azure_native.signalrservice.PrivateEndpointArgs(
        id="/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.Network/privateEndpoints/myPrivateEndpoint",
    ),
    private_endpoint_connection_name="mysignalrservice.1fa229cd-bf3f-47f0-8c49-afb36723997e",
    private_link_service_connection_state=azure_native.signalrservice.PrivateLinkServiceConnectionStateArgs(
        actions_required="None",
        status="Approved",
    ),
    resource_group_name="myResourceGroup",
    resource_name_="mySignalRService")

```

```yaml
resources:
  signalRPrivateEndpointConnection:
    type: azure-native:signalrservice:SignalRPrivateEndpointConnection
    properties:
      privateEndpoint:
        id: /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.Network/privateEndpoints/myPrivateEndpoint
      privateEndpointConnectionName: mysignalrservice.1fa229cd-bf3f-47f0-8c49-afb36723997e
      privateLinkServiceConnectionState:
        actionsRequired: None
        status: Approved
      resourceGroupName: myResourceGroup
      resourceName: mySignalRService

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:signalrservice:SignalRPrivateEndpointConnection mysignalrservice.1fa229cd-bf3f-47f0-8c49-afb36723997e /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.SignalRService/SignalR/mySignalRService/privateEndpointConnections/mysignalrservice.1fa229cd-bf3f-47f0-8c49-afb36723997e 
```
