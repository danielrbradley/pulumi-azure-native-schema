Private Endpoint Connection ARM resource.
API Version: 2018-06-01.
Previous API Version: 2018-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Approves or rejects a private endpoint connection for a factory.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnection = new AzureNative.DataFactory.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        FactoryName = "exampleFactoryName",
        PrivateEndpointConnectionName = "connection",
        Properties = new AzureNative.DataFactory.Inputs.PrivateLinkConnectionApprovalRequestArgs
        {
            PrivateEndpoint = new AzureNative.DataFactory.Inputs.PrivateEndpointArgs
            {
                Id = "/subscriptions/12345678-1234-1234-1234-12345678abc/resourceGroups/exampleResourceGroup/providers/Microsoft.DataFactory/factories/exampleFactoryName/privateEndpoints/myPrivateEndpoint",
            },
            PrivateLinkServiceConnectionState = new AzureNative.DataFactory.Inputs.PrivateLinkConnectionStateArgs
            {
                ActionsRequired = "",
                Description = "Approved by admin.",
                Status = "Approved",
            },
        },
        ResourceGroupName = "exampleResourceGroup",
    });

});


```

```go
package main

import (
	datafactory "github.com/pulumi/pulumi-azure-native-sdk/datafactory"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := datafactory.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &datafactory.PrivateEndpointConnectionArgs{
			FactoryName:                   pulumi.String("exampleFactoryName"),
			PrivateEndpointConnectionName: pulumi.String("connection"),
			Properties: datafactory.RemotePrivateEndpointConnectionResponse{
				PrivateEndpoint: &datafactory.PrivateEndpointArgs{
					Id: pulumi.String("/subscriptions/12345678-1234-1234-1234-12345678abc/resourceGroups/exampleResourceGroup/providers/Microsoft.DataFactory/factories/exampleFactoryName/privateEndpoints/myPrivateEndpoint"),
				},
				PrivateLinkServiceConnectionState: &datafactory.PrivateLinkConnectionStateArgs{
					ActionsRequired: pulumi.String(""),
					Description:     pulumi.String("Approved by admin."),
					Status:          pulumi.String("Approved"),
				},
			},
			ResourceGroupName: pulumi.String("exampleResourceGroup"),
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
import com.pulumi.azurenative.datafactory.PrivateEndpointConnection;
import com.pulumi.azurenative.datafactory.PrivateEndpointConnectionArgs;
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
            .factoryName("exampleFactoryName")
            .privateEndpointConnectionName("connection")
            .properties(Map.ofEntries(
                Map.entry("privateEndpoint", Map.of("id", "/subscriptions/12345678-1234-1234-1234-12345678abc/resourceGroups/exampleResourceGroup/providers/Microsoft.DataFactory/factories/exampleFactoryName/privateEndpoints/myPrivateEndpoint")),
                Map.entry("privateLinkServiceConnectionState", Map.ofEntries(
                    Map.entry("actionsRequired", ""),
                    Map.entry("description", "Approved by admin."),
                    Map.entry("status", "Approved")
                ))
            ))
            .resourceGroupName("exampleResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.datafactory.PrivateEndpointConnection("privateEndpointConnection", {
    factoryName: "exampleFactoryName",
    privateEndpointConnectionName: "connection",
    properties: {
        privateEndpoint: {
            id: "/subscriptions/12345678-1234-1234-1234-12345678abc/resourceGroups/exampleResourceGroup/providers/Microsoft.DataFactory/factories/exampleFactoryName/privateEndpoints/myPrivateEndpoint",
        },
        privateLinkServiceConnectionState: {
            actionsRequired: "",
            description: "Approved by admin.",
            status: "Approved",
        },
    },
    resourceGroupName: "exampleResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.datafactory.PrivateEndpointConnection("privateEndpointConnection",
    factory_name="exampleFactoryName",
    private_endpoint_connection_name="connection",
    properties=azure_native.datafactory.RemotePrivateEndpointConnectionResponseArgs(
        private_endpoint=azure_native.datafactory.PrivateEndpointArgs(
            id="/subscriptions/12345678-1234-1234-1234-12345678abc/resourceGroups/exampleResourceGroup/providers/Microsoft.DataFactory/factories/exampleFactoryName/privateEndpoints/myPrivateEndpoint",
        ),
        private_link_service_connection_state=azure_native.datafactory.PrivateLinkConnectionStateArgs(
            actions_required="",
            description="Approved by admin.",
            status="Approved",
        ),
    ),
    resource_group_name="exampleResourceGroup")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:datafactory:PrivateEndpointConnection
    properties:
      factoryName: exampleFactoryName
      privateEndpointConnectionName: connection
      properties:
        privateEndpoint:
          id: /subscriptions/12345678-1234-1234-1234-12345678abc/resourceGroups/exampleResourceGroup/providers/Microsoft.DataFactory/factories/exampleFactoryName/privateEndpoints/myPrivateEndpoint
        privateLinkServiceConnectionState:
          actionsRequired:
          description: Approved by admin.
          status: Approved
      resourceGroupName: exampleResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:datafactory:PrivateEndpointConnection exampleFactoryName /subscriptions/12345678-1234-1234-1234-12345678abc/resourceGroups/exampleResourceGroup/providers/Microsoft.DataFactory/factories/exampleFactoryName 
```
