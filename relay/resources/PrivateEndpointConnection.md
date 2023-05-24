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
    var privateEndpointConnection = new AzureNative.Relay.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        NamespaceName = "example-RelayNamespace-5849",
        PrivateEndpoint = new AzureNative.Relay.Inputs.PrivateEndpointArgs
        {
            Id = "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/resourcegroup/providers/Microsoft.Network/privateEndpoints/ali-relay-pve-1",
        },
        PrivateEndpointConnectionName = "{privateEndpointConnection name}",
        PrivateLinkServiceConnectionState = new AzureNative.Relay.Inputs.ConnectionStateArgs
        {
            Description = "You may pass",
            Status = "Approved",
        },
        ResourceGroupName = "resourcegroup",
    });

});


```

```go
package main

import (
	relay "github.com/pulumi/pulumi-azure-native-sdk/relay"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := relay.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &relay.PrivateEndpointConnectionArgs{
			NamespaceName: pulumi.String("example-RelayNamespace-5849"),
			PrivateEndpoint: &relay.PrivateEndpointArgs{
				Id: pulumi.String("/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/resourcegroup/providers/Microsoft.Network/privateEndpoints/ali-relay-pve-1"),
			},
			PrivateEndpointConnectionName: pulumi.String("{privateEndpointConnection name}"),
			PrivateLinkServiceConnectionState: &relay.ConnectionStateArgs{
				Description: pulumi.String("You may pass"),
				Status:      pulumi.String("Approved"),
			},
			ResourceGroupName: pulumi.String("resourcegroup"),
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
import com.pulumi.azurenative.relay.PrivateEndpointConnection;
import com.pulumi.azurenative.relay.PrivateEndpointConnectionArgs;
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
            .namespaceName("example-RelayNamespace-5849")
            .privateEndpoint(Map.of("id", "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/resourcegroup/providers/Microsoft.Network/privateEndpoints/ali-relay-pve-1"))
            .privateEndpointConnectionName("{privateEndpointConnection name}")
            .privateLinkServiceConnectionState(Map.ofEntries(
                Map.entry("description", "You may pass"),
                Map.entry("status", "Approved")
            ))
            .resourceGroupName("resourcegroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.relay.PrivateEndpointConnection("privateEndpointConnection", {
    namespaceName: "example-RelayNamespace-5849",
    privateEndpoint: {
        id: "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/resourcegroup/providers/Microsoft.Network/privateEndpoints/ali-relay-pve-1",
    },
    privateEndpointConnectionName: "{privateEndpointConnection name}",
    privateLinkServiceConnectionState: {
        description: "You may pass",
        status: "Approved",
    },
    resourceGroupName: "resourcegroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.relay.PrivateEndpointConnection("privateEndpointConnection",
    namespace_name="example-RelayNamespace-5849",
    private_endpoint=azure_native.relay.PrivateEndpointArgs(
        id="/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/resourcegroup/providers/Microsoft.Network/privateEndpoints/ali-relay-pve-1",
    ),
    private_endpoint_connection_name="{privateEndpointConnection name}",
    private_link_service_connection_state=azure_native.relay.ConnectionStateArgs(
        description="You may pass",
        status="Approved",
    ),
    resource_group_name="resourcegroup")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:relay:PrivateEndpointConnection
    properties:
      namespaceName: example-RelayNamespace-5849
      privateEndpoint:
        id: /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/resourcegroup/providers/Microsoft.Network/privateEndpoints/ali-relay-pve-1
      privateEndpointConnectionName: '{privateEndpointConnection name}'
      privateLinkServiceConnectionState:
        description: You may pass
        status: Approved
      resourceGroupName: resourcegroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:relay:PrivateEndpointConnection {privateEndpointConnection name} /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/alitest/providers/Microsoft.Relay/namespaces/relay-private-endpoint-test/privateEndpointConnections/{privateEndpointConnection name} 
```
