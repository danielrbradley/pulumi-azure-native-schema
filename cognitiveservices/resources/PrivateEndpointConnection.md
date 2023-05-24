The Private Endpoint Connection resource.
API Version: 2022-12-01.
Previous API Version: 2017-04-18. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PutPrivateEndpointConnection
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnection = new AzureNative.CognitiveServices.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        AccountName = "sto9699",
        PrivateEndpointConnectionName = "{privateEndpointConnectionName}",
        Properties = new AzureNative.CognitiveServices.Inputs.PrivateEndpointConnectionPropertiesArgs
        {
            PrivateLinkServiceConnectionState = new AzureNative.CognitiveServices.Inputs.PrivateLinkServiceConnectionStateArgs
            {
                Description = "Auto-Approved",
                Status = "Approved",
            },
        },
        ResourceGroupName = "res7687",
    });

});


```

```go
package main

import (
	cognitiveservices "github.com/pulumi/pulumi-azure-native-sdk/cognitiveservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := cognitiveservices.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &cognitiveservices.PrivateEndpointConnectionArgs{
			AccountName:                   pulumi.String("sto9699"),
			PrivateEndpointConnectionName: pulumi.String("{privateEndpointConnectionName}"),
			Properties: cognitiveservices.PrivateEndpointConnectionPropertiesResponse{
				PrivateLinkServiceConnectionState: &cognitiveservices.PrivateLinkServiceConnectionStateArgs{
					Description: pulumi.String("Auto-Approved"),
					Status:      pulumi.String("Approved"),
				},
			},
			ResourceGroupName: pulumi.String("res7687"),
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
import com.pulumi.azurenative.cognitiveservices.PrivateEndpointConnection;
import com.pulumi.azurenative.cognitiveservices.PrivateEndpointConnectionArgs;
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
            .accountName("sto9699")
            .privateEndpointConnectionName("{privateEndpointConnectionName}")
            .properties(Map.of("privateLinkServiceConnectionState", Map.ofEntries(
                Map.entry("description", "Auto-Approved"),
                Map.entry("status", "Approved")
            )))
            .resourceGroupName("res7687")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.cognitiveservices.PrivateEndpointConnection("privateEndpointConnection", {
    accountName: "sto9699",
    privateEndpointConnectionName: "{privateEndpointConnectionName}",
    properties: {
        privateLinkServiceConnectionState: {
            description: "Auto-Approved",
            status: "Approved",
        },
    },
    resourceGroupName: "res7687",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.cognitiveservices.PrivateEndpointConnection("privateEndpointConnection",
    account_name="sto9699",
    private_endpoint_connection_name="{privateEndpointConnectionName}",
    properties=azure_native.cognitiveservices.PrivateEndpointConnectionPropertiesResponseArgs(
        private_link_service_connection_state=azure_native.cognitiveservices.PrivateLinkServiceConnectionStateArgs(
            description="Auto-Approved",
            status="Approved",
        ),
    ),
    resource_group_name="res7687")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:cognitiveservices:PrivateEndpointConnection
    properties:
      accountName: sto9699
      privateEndpointConnectionName: '{privateEndpointConnectionName}'
      properties:
        privateLinkServiceConnectionState:
          description: Auto-Approved
          status: Approved
      resourceGroupName: res7687

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:cognitiveservices:PrivateEndpointConnection {privateEndpointConnectionName} /subscriptions/{subscription-id}/resourceGroups/res7231/providers/Microsoft.CognitiveServices/accounts/sto288/privateEndpointConnections/{privateEndpointConnectionName} 
```
