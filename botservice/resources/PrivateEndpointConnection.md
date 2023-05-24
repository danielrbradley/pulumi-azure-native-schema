The Private Endpoint Connection resource.
API Version: 2022-09-15.
Previous API Version: 2021-05-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Put Private Endpoint Connection
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnection = new AzureNative.BotService.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        PrivateEndpointConnectionName = "{privateEndpointConnectionName}",
        PrivateLinkServiceConnectionState = new AzureNative.BotService.Inputs.PrivateLinkServiceConnectionStateArgs
        {
            Description = "Auto-Approved",
            Status = "Approved",
        },
        ResourceGroupName = "res7687",
        ResourceName = "sto9699",
    });

});


```

```go
package main

import (
	botservice "github.com/pulumi/pulumi-azure-native-sdk/botservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := botservice.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &botservice.PrivateEndpointConnectionArgs{
			PrivateEndpointConnectionName: pulumi.String("{privateEndpointConnectionName}"),
			PrivateLinkServiceConnectionState: &botservice.PrivateLinkServiceConnectionStateArgs{
				Description: pulumi.String("Auto-Approved"),
				Status:      pulumi.String("Approved"),
			},
			ResourceGroupName: pulumi.String("res7687"),
			ResourceName:      pulumi.String("sto9699"),
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
import com.pulumi.azurenative.botservice.PrivateEndpointConnection;
import com.pulumi.azurenative.botservice.PrivateEndpointConnectionArgs;
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
            .privateEndpointConnectionName("{privateEndpointConnectionName}")
            .privateLinkServiceConnectionState(Map.ofEntries(
                Map.entry("description", "Auto-Approved"),
                Map.entry("status", "Approved")
            ))
            .resourceGroupName("res7687")
            .resourceName("sto9699")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.botservice.PrivateEndpointConnection("privateEndpointConnection", {
    privateEndpointConnectionName: "{privateEndpointConnectionName}",
    privateLinkServiceConnectionState: {
        description: "Auto-Approved",
        status: "Approved",
    },
    resourceGroupName: "res7687",
    resourceName: "sto9699",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.botservice.PrivateEndpointConnection("privateEndpointConnection",
    private_endpoint_connection_name="{privateEndpointConnectionName}",
    private_link_service_connection_state=azure_native.botservice.PrivateLinkServiceConnectionStateArgs(
        description="Auto-Approved",
        status="Approved",
    ),
    resource_group_name="res7687",
    resource_name_="sto9699")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:botservice:PrivateEndpointConnection
    properties:
      privateEndpointConnectionName: '{privateEndpointConnectionName}'
      privateLinkServiceConnectionState:
        description: Auto-Approved
        status: Approved
      resourceGroupName: res7687
      resourceName: sto9699

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:botservice:PrivateEndpointConnection {privateEndpointConnectionName} /subscriptions/{subscription-id}/resourceGroups/res7231/providers/Microsoft.BotService/botServices/sto288/privateEndpointConnections/{privateEndpointConnectionName} 
```
