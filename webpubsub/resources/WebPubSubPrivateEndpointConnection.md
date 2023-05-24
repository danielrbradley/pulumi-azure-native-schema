A private endpoint connection to an azure resource
API Version: 2023-02-01.
Previous API Version: 2021-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### WebPubSubPrivateEndpointConnections_Update
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var webPubSubPrivateEndpointConnection = new AzureNative.WebPubSub.WebPubSubPrivateEndpointConnection("webPubSubPrivateEndpointConnection", new()
    {
        PrivateEndpoint = new AzureNative.WebPubSub.Inputs.PrivateEndpointArgs
        {
            Id = "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.Network/privateEndpoints/myPrivateEndpoint",
        },
        PrivateEndpointConnectionName = "mywebpubsubservice.1fa229cd-bf3f-47f0-8c49-afb36723997e",
        PrivateLinkServiceConnectionState = new AzureNative.WebPubSub.Inputs.PrivateLinkServiceConnectionStateArgs
        {
            ActionsRequired = "None",
            Status = "Approved",
        },
        ResourceGroupName = "myResourceGroup",
        ResourceName = "myWebPubSubService",
    });

});


```

```go
package main

import (
	webpubsub "github.com/pulumi/pulumi-azure-native-sdk/webpubsub"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := webpubsub.NewWebPubSubPrivateEndpointConnection(ctx, "webPubSubPrivateEndpointConnection", &webpubsub.WebPubSubPrivateEndpointConnectionArgs{
			PrivateEndpoint: &webpubsub.PrivateEndpointArgs{
				Id: pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.Network/privateEndpoints/myPrivateEndpoint"),
			},
			PrivateEndpointConnectionName: pulumi.String("mywebpubsubservice.1fa229cd-bf3f-47f0-8c49-afb36723997e"),
			PrivateLinkServiceConnectionState: &webpubsub.PrivateLinkServiceConnectionStateArgs{
				ActionsRequired: pulumi.String("None"),
				Status:          pulumi.String("Approved"),
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
			ResourceName:      pulumi.String("myWebPubSubService"),
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
import com.pulumi.azurenative.webpubsub.WebPubSubPrivateEndpointConnection;
import com.pulumi.azurenative.webpubsub.WebPubSubPrivateEndpointConnectionArgs;
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
        var webPubSubPrivateEndpointConnection = new WebPubSubPrivateEndpointConnection("webPubSubPrivateEndpointConnection", WebPubSubPrivateEndpointConnectionArgs.builder()        
            .privateEndpoint(Map.of("id", "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.Network/privateEndpoints/myPrivateEndpoint"))
            .privateEndpointConnectionName("mywebpubsubservice.1fa229cd-bf3f-47f0-8c49-afb36723997e")
            .privateLinkServiceConnectionState(Map.ofEntries(
                Map.entry("actionsRequired", "None"),
                Map.entry("status", "Approved")
            ))
            .resourceGroupName("myResourceGroup")
            .resourceName("myWebPubSubService")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const webPubSubPrivateEndpointConnection = new azure_native.webpubsub.WebPubSubPrivateEndpointConnection("webPubSubPrivateEndpointConnection", {
    privateEndpoint: {
        id: "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.Network/privateEndpoints/myPrivateEndpoint",
    },
    privateEndpointConnectionName: "mywebpubsubservice.1fa229cd-bf3f-47f0-8c49-afb36723997e",
    privateLinkServiceConnectionState: {
        actionsRequired: "None",
        status: "Approved",
    },
    resourceGroupName: "myResourceGroup",
    resourceName: "myWebPubSubService",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

web_pub_sub_private_endpoint_connection = azure_native.webpubsub.WebPubSubPrivateEndpointConnection("webPubSubPrivateEndpointConnection",
    private_endpoint=azure_native.webpubsub.PrivateEndpointArgs(
        id="/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.Network/privateEndpoints/myPrivateEndpoint",
    ),
    private_endpoint_connection_name="mywebpubsubservice.1fa229cd-bf3f-47f0-8c49-afb36723997e",
    private_link_service_connection_state=azure_native.webpubsub.PrivateLinkServiceConnectionStateArgs(
        actions_required="None",
        status="Approved",
    ),
    resource_group_name="myResourceGroup",
    resource_name_="myWebPubSubService")

```

```yaml
resources:
  webPubSubPrivateEndpointConnection:
    type: azure-native:webpubsub:WebPubSubPrivateEndpointConnection
    properties:
      privateEndpoint:
        id: /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.Network/privateEndpoints/myPrivateEndpoint
      privateEndpointConnectionName: mywebpubsubservice.1fa229cd-bf3f-47f0-8c49-afb36723997e
      privateLinkServiceConnectionState:
        actionsRequired: None
        status: Approved
      resourceGroupName: myResourceGroup
      resourceName: myWebPubSubService

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:webpubsub:WebPubSubPrivateEndpointConnection mywebpubsubservice.1fa229cd-bf3f-47f0-8c49-afb36723997e /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.SignalRService/WebPubSub/myWebPubSubService/privateEndpointConnections/mywebpubsubservice.1fa229cd-bf3f-47f0-8c49-afb36723997e 
```
