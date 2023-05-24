The private endpoint connection of a Digital Twin.
API Version: 2023-01-31.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Update the status of a private endpoint connection with the given name
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnection = new AzureNative.DigitalTwins.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        PrivateEndpointConnectionName = "myPrivateConnection",
        Properties = new AzureNative.DigitalTwins.Inputs.ConnectionPropertiesArgs
        {
            PrivateLinkServiceConnectionState = new AzureNative.DigitalTwins.Inputs.ConnectionPropertiesPrivateLinkServiceConnectionStateArgs
            {
                Description = "Approved by johndoe@company.com.",
                Status = "Approved",
            },
        },
        ResourceGroupName = "resRg",
        ResourceName = "myDigitalTwinsService",
    });

});


```

```go
package main

import (
	digitaltwins "github.com/pulumi/pulumi-azure-native-sdk/digitaltwins"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := digitaltwins.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &digitaltwins.PrivateEndpointConnectionArgs{
			PrivateEndpointConnectionName: pulumi.String("myPrivateConnection"),
			Properties: digitaltwins.ConnectionPropertiesResponse{
				PrivateLinkServiceConnectionState: &digitaltwins.ConnectionPropertiesPrivateLinkServiceConnectionStateArgs{
					Description: pulumi.String("Approved by johndoe@company.com."),
					Status:      pulumi.String("Approved"),
				},
			},
			ResourceGroupName: pulumi.String("resRg"),
			ResourceName:      pulumi.String("myDigitalTwinsService"),
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
import com.pulumi.azurenative.digitaltwins.PrivateEndpointConnection;
import com.pulumi.azurenative.digitaltwins.PrivateEndpointConnectionArgs;
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
            .privateEndpointConnectionName("myPrivateConnection")
            .properties(Map.of("privateLinkServiceConnectionState", Map.ofEntries(
                Map.entry("description", "Approved by johndoe@company.com."),
                Map.entry("status", "Approved")
            )))
            .resourceGroupName("resRg")
            .resourceName("myDigitalTwinsService")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.digitaltwins.PrivateEndpointConnection("privateEndpointConnection", {
    privateEndpointConnectionName: "myPrivateConnection",
    properties: {
        privateLinkServiceConnectionState: {
            description: "Approved by johndoe@company.com.",
            status: "Approved",
        },
    },
    resourceGroupName: "resRg",
    resourceName: "myDigitalTwinsService",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.digitaltwins.PrivateEndpointConnection("privateEndpointConnection",
    private_endpoint_connection_name="myPrivateConnection",
    properties=azure_native.digitaltwins.ConnectionPropertiesResponseArgs(
        private_link_service_connection_state=azure_native.digitaltwins.ConnectionPropertiesPrivateLinkServiceConnectionStateArgs(
            description="Approved by johndoe@company.com.",
            status="Approved",
        ),
    ),
    resource_group_name="resRg",
    resource_name_="myDigitalTwinsService")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:digitaltwins:PrivateEndpointConnection
    properties:
      privateEndpointConnectionName: myPrivateConnection
      properties:
        privateLinkServiceConnectionState:
          description: Approved by johndoe@company.com.
          status: Approved
      resourceGroupName: resRg
      resourceName: myDigitalTwinsService

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:digitaltwins:PrivateEndpointConnection myPrivateConnection /subscriptions/50016170-c839-41ba-a724-51e9df440b9e/resourcegroups/resRg/providers/Microsoft.DigitalTwins/digitalTwinsInstances/myDigitalTwinsService/privateEndpointConnections/myPrivateConnection 
```
