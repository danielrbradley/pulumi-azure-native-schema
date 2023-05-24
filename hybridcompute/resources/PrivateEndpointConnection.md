A private endpoint connection
API Version: 2022-11-10.
Previous API Version: 2021-03-25-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Approve or reject a private endpoint connection with a given name.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnection = new AzureNative.HybridCompute.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        PrivateEndpointConnectionName = "private-endpoint-connection-name",
        Properties = new AzureNative.HybridCompute.Inputs.PrivateEndpointConnectionPropertiesArgs
        {
            PrivateLinkServiceConnectionState = new AzureNative.HybridCompute.Inputs.PrivateLinkServiceConnectionStatePropertyArgs
            {
                Description = "Approved by johndoe@contoso.com",
                Status = "Approved",
            },
        },
        ResourceGroupName = "myResourceGroup",
        ScopeName = "myPrivateLinkScope",
    });

});


```

```go
package main

import (
	hybridcompute "github.com/pulumi/pulumi-azure-native-sdk/hybridcompute"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := hybridcompute.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &hybridcompute.PrivateEndpointConnectionArgs{
			PrivateEndpointConnectionName: pulumi.String("private-endpoint-connection-name"),
			Properties: hybridcompute.PrivateEndpointConnectionPropertiesResponse{
				PrivateLinkServiceConnectionState: &hybridcompute.PrivateLinkServiceConnectionStatePropertyArgs{
					Description: pulumi.String("Approved by johndoe@contoso.com"),
					Status:      pulumi.String("Approved"),
				},
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
			ScopeName:         pulumi.String("myPrivateLinkScope"),
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
import com.pulumi.azurenative.hybridcompute.PrivateEndpointConnection;
import com.pulumi.azurenative.hybridcompute.PrivateEndpointConnectionArgs;
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
            .privateEndpointConnectionName("private-endpoint-connection-name")
            .properties(Map.of("privateLinkServiceConnectionState", Map.ofEntries(
                Map.entry("description", "Approved by johndoe@contoso.com"),
                Map.entry("status", "Approved")
            )))
            .resourceGroupName("myResourceGroup")
            .scopeName("myPrivateLinkScope")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.hybridcompute.PrivateEndpointConnection("privateEndpointConnection", {
    privateEndpointConnectionName: "private-endpoint-connection-name",
    properties: {
        privateLinkServiceConnectionState: {
            description: "Approved by johndoe@contoso.com",
            status: "Approved",
        },
    },
    resourceGroupName: "myResourceGroup",
    scopeName: "myPrivateLinkScope",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.hybridcompute.PrivateEndpointConnection("privateEndpointConnection",
    private_endpoint_connection_name="private-endpoint-connection-name",
    properties=azure_native.hybridcompute.PrivateEndpointConnectionPropertiesResponseArgs(
        private_link_service_connection_state=azure_native.hybridcompute.PrivateLinkServiceConnectionStatePropertyArgs(
            description="Approved by johndoe@contoso.com",
            status="Approved",
        ),
    ),
    resource_group_name="myResourceGroup",
    scope_name="myPrivateLinkScope")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:hybridcompute:PrivateEndpointConnection
    properties:
      privateEndpointConnectionName: private-endpoint-connection-name
      properties:
        privateLinkServiceConnectionState:
          description: Approved by johndoe@contoso.com
          status: Approved
      resourceGroupName: myResourceGroup
      scopeName: myPrivateLinkScope

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:hybridcompute:PrivateEndpointConnection private-endpoint-connection-name /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/myResourceGroup/providers/Microsoft.HybridCompute/privateLinkScopes/myPrivateLinkScope/privateEndpointConnections/private-endpoint-connection-name 
```
