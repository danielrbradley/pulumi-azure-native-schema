Properties of the PrivateEndpointConnection.
API Version: 2021-11-01.
Previous API Version: 2018-01-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### NameSpacePrivateEndPointConnectionCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnection = new AzureNative.EventHub.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        NamespaceName = "sdk-Namespace-2924",
        PrivateEndpoint = new AzureNative.EventHub.Inputs.PrivateEndpointArgs
        {
            Id = "/subscriptions/dbedb4e0-40e6-4145-81f3-f1314c150774/resourceGroups/SDK-EventHub-8396/providers/Microsoft.Network/privateEndpoints/sdk-Namespace-2847",
        },
        PrivateEndpointConnectionName = "privateEndpointConnectionName",
        PrivateLinkServiceConnectionState = new AzureNative.EventHub.Inputs.ConnectionStateArgs
        {
            Description = "testing",
            Status = "Rejected",
        },
        ProvisioningState = "Succeeded",
        ResourceGroupName = "ArunMonocle",
    });

});


```

```go
package main

import (
	eventhub "github.com/pulumi/pulumi-azure-native-sdk/eventhub"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := eventhub.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &eventhub.PrivateEndpointConnectionArgs{
			NamespaceName: pulumi.String("sdk-Namespace-2924"),
			PrivateEndpoint: &eventhub.PrivateEndpointArgs{
				Id: pulumi.String("/subscriptions/dbedb4e0-40e6-4145-81f3-f1314c150774/resourceGroups/SDK-EventHub-8396/providers/Microsoft.Network/privateEndpoints/sdk-Namespace-2847"),
			},
			PrivateEndpointConnectionName: pulumi.String("privateEndpointConnectionName"),
			PrivateLinkServiceConnectionState: &eventhub.ConnectionStateArgs{
				Description: pulumi.String("testing"),
				Status:      pulumi.String("Rejected"),
			},
			ProvisioningState: pulumi.String("Succeeded"),
			ResourceGroupName: pulumi.String("ArunMonocle"),
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
import com.pulumi.azurenative.eventhub.PrivateEndpointConnection;
import com.pulumi.azurenative.eventhub.PrivateEndpointConnectionArgs;
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
        var privateEndpointConnection = new PrivateEndpointConnection("privateEndpointConnection", PrivateEndpointConnectionArgs.builder()        
            .namespaceName("sdk-Namespace-2924")
            .privateEndpoint(Map.of("id", "/subscriptions/dbedb4e0-40e6-4145-81f3-f1314c150774/resourceGroups/SDK-EventHub-8396/providers/Microsoft.Network/privateEndpoints/sdk-Namespace-2847"))
            .privateEndpointConnectionName("privateEndpointConnectionName")
            .privateLinkServiceConnectionState(Map.ofEntries(
                Map.entry("description", "testing"),
                Map.entry("status", "Rejected")
            ))
            .provisioningState("Succeeded")
            .resourceGroupName("ArunMonocle")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.eventhub.PrivateEndpointConnection("privateEndpointConnection", {
    namespaceName: "sdk-Namespace-2924",
    privateEndpoint: {
        id: "/subscriptions/dbedb4e0-40e6-4145-81f3-f1314c150774/resourceGroups/SDK-EventHub-8396/providers/Microsoft.Network/privateEndpoints/sdk-Namespace-2847",
    },
    privateEndpointConnectionName: "privateEndpointConnectionName",
    privateLinkServiceConnectionState: {
        description: "testing",
        status: "Rejected",
    },
    provisioningState: "Succeeded",
    resourceGroupName: "ArunMonocle",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.eventhub.PrivateEndpointConnection("privateEndpointConnection",
    namespace_name="sdk-Namespace-2924",
    private_endpoint=azure_native.eventhub.PrivateEndpointArgs(
        id="/subscriptions/dbedb4e0-40e6-4145-81f3-f1314c150774/resourceGroups/SDK-EventHub-8396/providers/Microsoft.Network/privateEndpoints/sdk-Namespace-2847",
    ),
    private_endpoint_connection_name="privateEndpointConnectionName",
    private_link_service_connection_state=azure_native.eventhub.ConnectionStateArgs(
        description="testing",
        status="Rejected",
    ),
    provisioning_state="Succeeded",
    resource_group_name="ArunMonocle")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:eventhub:PrivateEndpointConnection
    properties:
      namespaceName: sdk-Namespace-2924
      privateEndpoint:
        id: /subscriptions/dbedb4e0-40e6-4145-81f3-f1314c150774/resourceGroups/SDK-EventHub-8396/providers/Microsoft.Network/privateEndpoints/sdk-Namespace-2847
      privateEndpointConnectionName: privateEndpointConnectionName
      privateLinkServiceConnectionState:
        description: testing
        status: Rejected
      provisioningState: Succeeded
      resourceGroupName: ArunMonocle

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:eventhub:PrivateEndpointConnection 928c44d5-b7c6-423b-b6fa-811e0c27b3e0 /subscriptions/dbedb4e0-40e6-4145-81f3-f1314c150774/resourceGroups/SDK-EventHub-4794/providers/Microsoft.EventHub/namespaces/sdk-Namespace-5828/privateEndpointConnections/928c44d5-b7c6-423b-b6fa-811e0c27b3e0 
```
