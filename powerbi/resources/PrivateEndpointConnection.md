
API Version: 2020-06-01.
Previous API Version: 2020-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Updates status of private endpoint connection
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnection = new AzureNative.PowerBI.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        AzureResourceName = "azureResourceName",
        PrivateEndpoint = new AzureNative.PowerBI.Inputs.PrivateEndpointArgs
        {
            Id = "/subscriptions/a0020869-4d28-422a-89f4-c2413130d73c/resourceGroups/resourceGroup/providers/Microsoft.Network/privateEndpoints/myPrivateEndpointName",
        },
        PrivateEndpointName = "myPrivateEndpointName",
        PrivateLinkServiceConnectionState = new AzureNative.PowerBI.Inputs.ConnectionStateArgs
        {
            ActionsRequired = "None",
            Description = "",
            Status = "Approved ",
        },
        ResourceGroupName = "resourceGroup",
    });

});


```

```go
package main

import (
	powerbi "github.com/pulumi/pulumi-azure-native-sdk/powerbi"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := powerbi.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &powerbi.PrivateEndpointConnectionArgs{
			AzureResourceName: pulumi.String("azureResourceName"),
			PrivateEndpoint: &powerbi.PrivateEndpointArgs{
				Id: pulumi.String("/subscriptions/a0020869-4d28-422a-89f4-c2413130d73c/resourceGroups/resourceGroup/providers/Microsoft.Network/privateEndpoints/myPrivateEndpointName"),
			},
			PrivateEndpointName: pulumi.String("myPrivateEndpointName"),
			PrivateLinkServiceConnectionState: &powerbi.ConnectionStateArgs{
				ActionsRequired: pulumi.String("None"),
				Description:     pulumi.String(""),
				Status:          pulumi.String("Approved "),
			},
			ResourceGroupName: pulumi.String("resourceGroup"),
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
import com.pulumi.azurenative.powerbi.PrivateEndpointConnection;
import com.pulumi.azurenative.powerbi.PrivateEndpointConnectionArgs;
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
            .azureResourceName("azureResourceName")
            .privateEndpoint(Map.of("id", "/subscriptions/a0020869-4d28-422a-89f4-c2413130d73c/resourceGroups/resourceGroup/providers/Microsoft.Network/privateEndpoints/myPrivateEndpointName"))
            .privateEndpointName("myPrivateEndpointName")
            .privateLinkServiceConnectionState(Map.ofEntries(
                Map.entry("actionsRequired", "None"),
                Map.entry("description", ""),
                Map.entry("status", "Approved ")
            ))
            .resourceGroupName("resourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.powerbi.PrivateEndpointConnection("privateEndpointConnection", {
    azureResourceName: "azureResourceName",
    privateEndpoint: {
        id: "/subscriptions/a0020869-4d28-422a-89f4-c2413130d73c/resourceGroups/resourceGroup/providers/Microsoft.Network/privateEndpoints/myPrivateEndpointName",
    },
    privateEndpointName: "myPrivateEndpointName",
    privateLinkServiceConnectionState: {
        actionsRequired: "None",
        description: "",
        status: "Approved ",
    },
    resourceGroupName: "resourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.powerbi.PrivateEndpointConnection("privateEndpointConnection",
    azure_resource_name="azureResourceName",
    private_endpoint=azure_native.powerbi.PrivateEndpointArgs(
        id="/subscriptions/a0020869-4d28-422a-89f4-c2413130d73c/resourceGroups/resourceGroup/providers/Microsoft.Network/privateEndpoints/myPrivateEndpointName",
    ),
    private_endpoint_name="myPrivateEndpointName",
    private_link_service_connection_state=azure_native.powerbi.ConnectionStateArgs(
        actions_required="None",
        description="",
        status="Approved ",
    ),
    resource_group_name="resourceGroup")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:powerbi:PrivateEndpointConnection
    properties:
      azureResourceName: azureResourceName
      privateEndpoint:
        id: /subscriptions/a0020869-4d28-422a-89f4-c2413130d73c/resourceGroups/resourceGroup/providers/Microsoft.Network/privateEndpoints/myPrivateEndpointName
      privateEndpointName: myPrivateEndpointName
      privateLinkServiceConnectionState:
        actionsRequired: None
        description:
        status: 'Approved '
      resourceGroupName: resourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:powerbi:PrivateEndpointConnection myPrivateEndpointName.58ffb8de-89ad-41eb-9f8f-de0a7db9d721 /subscriptions/a0020869-4d28-422a-89f4-c2413130d73c/resourceGroups/resourceGroup/providers/Microsoft.PowerBI/privateLinkServicesForPowerBI/azureResourceName/privateEndpointConnections/myPrivateEndpointName.58ffb8de-89ad-41eb-9f8f-de0a7db9d721 
```
