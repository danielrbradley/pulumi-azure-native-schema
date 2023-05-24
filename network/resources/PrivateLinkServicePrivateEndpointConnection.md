PrivateEndpointConnection resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### approve or reject private end point connection for a private link service
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateLinkServicePrivateEndpointConnection = new AzureNative.Network.PrivateLinkServicePrivateEndpointConnection("privateLinkServicePrivateEndpointConnection", new()
    {
        Name = "testPlePeConnection",
        PeConnectionName = "testPlePeConnection",
        PrivateLinkServiceConnectionState = new AzureNative.Network.Inputs.PrivateLinkServiceConnectionStateArgs
        {
            Description = "approved it for some reason.",
            Status = "Approved",
        },
        ResourceGroupName = "rg1",
        ServiceName = "testPls",
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
		_, err := network.NewPrivateLinkServicePrivateEndpointConnection(ctx, "privateLinkServicePrivateEndpointConnection", &network.PrivateLinkServicePrivateEndpointConnectionArgs{
			Name:             pulumi.String("testPlePeConnection"),
			PeConnectionName: pulumi.String("testPlePeConnection"),
			PrivateLinkServiceConnectionState: &network.PrivateLinkServiceConnectionStateArgs{
				Description: pulumi.String("approved it for some reason."),
				Status:      pulumi.String("Approved"),
			},
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("testPls"),
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
import com.pulumi.azurenative.network.PrivateLinkServicePrivateEndpointConnection;
import com.pulumi.azurenative.network.PrivateLinkServicePrivateEndpointConnectionArgs;
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
        var privateLinkServicePrivateEndpointConnection = new PrivateLinkServicePrivateEndpointConnection("privateLinkServicePrivateEndpointConnection", PrivateLinkServicePrivateEndpointConnectionArgs.builder()        
            .name("testPlePeConnection")
            .peConnectionName("testPlePeConnection")
            .privateLinkServiceConnectionState(Map.ofEntries(
                Map.entry("description", "approved it for some reason."),
                Map.entry("status", "Approved")
            ))
            .resourceGroupName("rg1")
            .serviceName("testPls")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateLinkServicePrivateEndpointConnection = new azure_native.network.PrivateLinkServicePrivateEndpointConnection("privateLinkServicePrivateEndpointConnection", {
    name: "testPlePeConnection",
    peConnectionName: "testPlePeConnection",
    privateLinkServiceConnectionState: {
        description: "approved it for some reason.",
        status: "Approved",
    },
    resourceGroupName: "rg1",
    serviceName: "testPls",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_link_service_private_endpoint_connection = azure_native.network.PrivateLinkServicePrivateEndpointConnection("privateLinkServicePrivateEndpointConnection",
    name="testPlePeConnection",
    pe_connection_name="testPlePeConnection",
    private_link_service_connection_state=azure_native.network.PrivateLinkServiceConnectionStateArgs(
        description="approved it for some reason.",
        status="Approved",
    ),
    resource_group_name="rg1",
    service_name="testPls")

```

```yaml
resources:
  privateLinkServicePrivateEndpointConnection:
    type: azure-native:network:PrivateLinkServicePrivateEndpointConnection
    properties:
      name: testPlePeConnection
      peConnectionName: testPlePeConnection
      privateLinkServiceConnectionState:
        description: approved it for some reason.
        status: Approved
      resourceGroupName: rg1
      serviceName: testPls

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:PrivateLinkServicePrivateEndpointConnection testPlePeConnection /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Network/privateLinkServices/{serviceName}/privateEndpointConnections/{peConnectionName} 
```
