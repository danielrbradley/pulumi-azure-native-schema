The private endpoint connection of an IotHub
API Version: 2021-07-02.
Previous API Version: 2020-08-31. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PrivateEndpointConnection_Update
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnection = new AzureNative.Devices.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        PrivateEndpointConnectionName = "myPrivateEndpointConnection",
        Properties = new AzureNative.Devices.Inputs.PrivateEndpointConnectionPropertiesArgs
        {
            PrivateLinkServiceConnectionState = new AzureNative.Devices.Inputs.PrivateLinkServiceConnectionStateArgs
            {
                Description = "Approved by johndoe@contoso.com",
                Status = "Approved",
            },
        },
        ResourceGroupName = "myResourceGroup",
        ResourceName = "testHub",
    });

});


```

```go
package main

import (
	devices "github.com/pulumi/pulumi-azure-native-sdk/devices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := devices.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &devices.PrivateEndpointConnectionArgs{
			PrivateEndpointConnectionName: pulumi.String("myPrivateEndpointConnection"),
			Properties: devices.PrivateEndpointConnectionPropertiesResponse{
				PrivateLinkServiceConnectionState: &devices.PrivateLinkServiceConnectionStateArgs{
					Description: pulumi.String("Approved by johndoe@contoso.com"),
					Status:      pulumi.String("Approved"),
				},
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
			ResourceName:      pulumi.String("testHub"),
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
import com.pulumi.azurenative.devices.PrivateEndpointConnection;
import com.pulumi.azurenative.devices.PrivateEndpointConnectionArgs;
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
            .privateEndpointConnectionName("myPrivateEndpointConnection")
            .properties(Map.of("privateLinkServiceConnectionState", Map.ofEntries(
                Map.entry("description", "Approved by johndoe@contoso.com"),
                Map.entry("status", "Approved")
            )))
            .resourceGroupName("myResourceGroup")
            .resourceName("testHub")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.devices.PrivateEndpointConnection("privateEndpointConnection", {
    privateEndpointConnectionName: "myPrivateEndpointConnection",
    properties: {
        privateLinkServiceConnectionState: {
            description: "Approved by johndoe@contoso.com",
            status: "Approved",
        },
    },
    resourceGroupName: "myResourceGroup",
    resourceName: "testHub",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.devices.PrivateEndpointConnection("privateEndpointConnection",
    private_endpoint_connection_name="myPrivateEndpointConnection",
    properties=azure_native.devices.PrivateEndpointConnectionPropertiesResponseArgs(
        private_link_service_connection_state=azure_native.devices.PrivateLinkServiceConnectionStateArgs(
            description="Approved by johndoe@contoso.com",
            status="Approved",
        ),
    ),
    resource_group_name="myResourceGroup",
    resource_name_="testHub")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:devices:PrivateEndpointConnection
    properties:
      privateEndpointConnectionName: myPrivateEndpointConnection
      properties:
        privateLinkServiceConnectionState:
          description: Approved by johndoe@contoso.com
          status: Approved
      resourceGroupName: myResourceGroup
      resourceName: testHub

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devices:PrivateEndpointConnection myPrivateEndpointConnection /subscriptions/91d12660-3dec-467a-be2a-213b5544ddc0/resourceGroups/myResourceGroup/providers/Microsoft.Devices/IotHubs/testHub/PrivateEndpointConnections/myPrivateEndpointConnection 
```
