Private Endpoint connection on an application gateway.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Update Application Gateway Private Endpoint Connection
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var applicationGatewayPrivateEndpointConnection = new AzureNative.Network.ApplicationGatewayPrivateEndpointConnection("applicationGatewayPrivateEndpointConnection", new()
    {
        ApplicationGatewayName = "appgw",
        ConnectionName = "connection1",
        Name = "connection1",
        PrivateLinkServiceConnectionState = new AzureNative.Network.Inputs.PrivateLinkServiceConnectionStateArgs
        {
            Description = "approved it for some reason.",
            Status = "Approved",
        },
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
		_, err := network.NewApplicationGatewayPrivateEndpointConnection(ctx, "applicationGatewayPrivateEndpointConnection", &network.ApplicationGatewayPrivateEndpointConnectionArgs{
			ApplicationGatewayName: pulumi.String("appgw"),
			ConnectionName:         pulumi.String("connection1"),
			Name:                   pulumi.String("connection1"),
			PrivateLinkServiceConnectionState: &network.PrivateLinkServiceConnectionStateArgs{
				Description: pulumi.String("approved it for some reason."),
				Status:      pulumi.String("Approved"),
			},
			ResourceGroupName: pulumi.String("rg1"),
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
import com.pulumi.azurenative.network.ApplicationGatewayPrivateEndpointConnection;
import com.pulumi.azurenative.network.ApplicationGatewayPrivateEndpointConnectionArgs;
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
        var applicationGatewayPrivateEndpointConnection = new ApplicationGatewayPrivateEndpointConnection("applicationGatewayPrivateEndpointConnection", ApplicationGatewayPrivateEndpointConnectionArgs.builder()        
            .applicationGatewayName("appgw")
            .connectionName("connection1")
            .name("connection1")
            .privateLinkServiceConnectionState(Map.ofEntries(
                Map.entry("description", "approved it for some reason."),
                Map.entry("status", "Approved")
            ))
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const applicationGatewayPrivateEndpointConnection = new azure_native.network.ApplicationGatewayPrivateEndpointConnection("applicationGatewayPrivateEndpointConnection", {
    applicationGatewayName: "appgw",
    connectionName: "connection1",
    name: "connection1",
    privateLinkServiceConnectionState: {
        description: "approved it for some reason.",
        status: "Approved",
    },
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

application_gateway_private_endpoint_connection = azure_native.network.ApplicationGatewayPrivateEndpointConnection("applicationGatewayPrivateEndpointConnection",
    application_gateway_name="appgw",
    connection_name="connection1",
    name="connection1",
    private_link_service_connection_state=azure_native.network.PrivateLinkServiceConnectionStateArgs(
        description="approved it for some reason.",
        status="Approved",
    ),
    resource_group_name="rg1")

```

```yaml
resources:
  applicationGatewayPrivateEndpointConnection:
    type: azure-native:network:ApplicationGatewayPrivateEndpointConnection
    properties:
      applicationGatewayName: appgw
      connectionName: connection1
      name: connection1
      privateLinkServiceConnectionState:
        description: approved it for some reason.
        status: Approved
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:ApplicationGatewayPrivateEndpointConnection testPlePeConnection /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Network/applicationGateways/{applicationGatewayName}/privateEndpointConnections/{connectionName} 
```
