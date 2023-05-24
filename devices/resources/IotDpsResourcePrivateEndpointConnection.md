The private endpoint connection of a provisioning service
API Version: 2022-12-12.
Previous API Version: 2020-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PrivateEndpointConnection_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var iotDpsResourcePrivateEndpointConnection = new AzureNative.Devices.IotDpsResourcePrivateEndpointConnection("iotDpsResourcePrivateEndpointConnection", new()
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
        ResourceName = "myFirstProvisioningService",
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
		_, err := devices.NewIotDpsResourcePrivateEndpointConnection(ctx, "iotDpsResourcePrivateEndpointConnection", &devices.IotDpsResourcePrivateEndpointConnectionArgs{
			PrivateEndpointConnectionName: pulumi.String("myPrivateEndpointConnection"),
			Properties: devices.PrivateEndpointConnectionPropertiesResponse{
				PrivateLinkServiceConnectionState: &devices.PrivateLinkServiceConnectionStateArgs{
					Description: pulumi.String("Approved by johndoe@contoso.com"),
					Status:      pulumi.String("Approved"),
				},
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
			ResourceName:      pulumi.String("myFirstProvisioningService"),
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
import com.pulumi.azurenative.devices.IotDpsResourcePrivateEndpointConnection;
import com.pulumi.azurenative.devices.IotDpsResourcePrivateEndpointConnectionArgs;
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
        var iotDpsResourcePrivateEndpointConnection = new IotDpsResourcePrivateEndpointConnection("iotDpsResourcePrivateEndpointConnection", IotDpsResourcePrivateEndpointConnectionArgs.builder()        
            .privateEndpointConnectionName("myPrivateEndpointConnection")
            .properties(Map.of("privateLinkServiceConnectionState", Map.ofEntries(
                Map.entry("description", "Approved by johndoe@contoso.com"),
                Map.entry("status", "Approved")
            )))
            .resourceGroupName("myResourceGroup")
            .resourceName("myFirstProvisioningService")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const iotDpsResourcePrivateEndpointConnection = new azure_native.devices.IotDpsResourcePrivateEndpointConnection("iotDpsResourcePrivateEndpointConnection", {
    privateEndpointConnectionName: "myPrivateEndpointConnection",
    properties: {
        privateLinkServiceConnectionState: {
            description: "Approved by johndoe@contoso.com",
            status: "Approved",
        },
    },
    resourceGroupName: "myResourceGroup",
    resourceName: "myFirstProvisioningService",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

iot_dps_resource_private_endpoint_connection = azure_native.devices.IotDpsResourcePrivateEndpointConnection("iotDpsResourcePrivateEndpointConnection",
    private_endpoint_connection_name="myPrivateEndpointConnection",
    properties=azure_native.devices.PrivateEndpointConnectionPropertiesResponseArgs(
        private_link_service_connection_state=azure_native.devices.PrivateLinkServiceConnectionStateArgs(
            description="Approved by johndoe@contoso.com",
            status="Approved",
        ),
    ),
    resource_group_name="myResourceGroup",
    resource_name_="myFirstProvisioningService")

```

```yaml
resources:
  iotDpsResourcePrivateEndpointConnection:
    type: azure-native:devices:IotDpsResourcePrivateEndpointConnection
    properties:
      privateEndpointConnectionName: myPrivateEndpointConnection
      properties:
        privateLinkServiceConnectionState:
          description: Approved by johndoe@contoso.com
          status: Approved
      resourceGroupName: myResourceGroup
      resourceName: myFirstProvisioningService

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devices:IotDpsResourcePrivateEndpointConnection myPrivateEndpointConnection /subscriptions/91d12660-3dec-467a-be2a-213b5544ddc0/resourceGroups/myResourceGroup/providers/Microsoft.Devices/ProvisioningServices/myFirstProvisioningService/PrivateEndpointConnections/myPrivateEndpointConnection 
```
