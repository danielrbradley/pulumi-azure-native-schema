The Private Endpoint Connection resource.
API Version: 2023-01-01.
Previous API Version: 2020-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Update private endpoint connection.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnection = new AzureNative.Media.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        AccountName = "contososports",
        Name = "connectionName1",
        PrivateLinkServiceConnectionState = new AzureNative.Media.Inputs.PrivateLinkServiceConnectionStateArgs
        {
            Description = "Test description.",
            Status = "Approved",
        },
        ResourceGroupName = "contosorg",
    });

});


```

```go
package main

import (
	media "github.com/pulumi/pulumi-azure-native-sdk/media"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := media.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &media.PrivateEndpointConnectionArgs{
			AccountName: pulumi.String("contososports"),
			Name:        pulumi.String("connectionName1"),
			PrivateLinkServiceConnectionState: &media.PrivateLinkServiceConnectionStateArgs{
				Description: pulumi.String("Test description."),
				Status:      pulumi.String("Approved"),
			},
			ResourceGroupName: pulumi.String("contosorg"),
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
import com.pulumi.azurenative.media.PrivateEndpointConnection;
import com.pulumi.azurenative.media.PrivateEndpointConnectionArgs;
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
            .accountName("contososports")
            .name("connectionName1")
            .privateLinkServiceConnectionState(Map.ofEntries(
                Map.entry("description", "Test description."),
                Map.entry("status", "Approved")
            ))
            .resourceGroupName("contosorg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.media.PrivateEndpointConnection("privateEndpointConnection", {
    accountName: "contososports",
    name: "connectionName1",
    privateLinkServiceConnectionState: {
        description: "Test description.",
        status: "Approved",
    },
    resourceGroupName: "contosorg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.media.PrivateEndpointConnection("privateEndpointConnection",
    account_name="contososports",
    name="connectionName1",
    private_link_service_connection_state=azure_native.media.PrivateLinkServiceConnectionStateArgs(
        description="Test description.",
        status="Approved",
    ),
    resource_group_name="contosorg")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:media:PrivateEndpointConnection
    properties:
      accountName: contososports
      name: connectionName1
      privateLinkServiceConnectionState:
        description: Test description.
        status: Approved
      resourceGroupName: contosorg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:media:PrivateEndpointConnection connectionName1 /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/fabrikam/providers/Microsoft.Media/mediaservices/contososports/privateEndpointConnections/connectionName1 
```
