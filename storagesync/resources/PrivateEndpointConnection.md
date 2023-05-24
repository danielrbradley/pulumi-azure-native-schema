The Private Endpoint Connection resource.
API Version: 2022-06-01.
Previous API Version: 2020-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PrivateEndpointConnections_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnection = new AzureNative.StorageSync.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        PrivateEndpointConnectionName = "{privateEndpointConnectionName}",
        PrivateLinkServiceConnectionState = new AzureNative.StorageSync.Inputs.PrivateLinkServiceConnectionStateArgs
        {
            Description = "Auto-Approved",
            Status = "Approved",
        },
        ResourceGroupName = "res7687",
        StorageSyncServiceName = "sss2527",
    });

});


```

```go
package main

import (
	storagesync "github.com/pulumi/pulumi-azure-native-sdk/storagesync"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := storagesync.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &storagesync.PrivateEndpointConnectionArgs{
			PrivateEndpointConnectionName: pulumi.String("{privateEndpointConnectionName}"),
			PrivateLinkServiceConnectionState: &storagesync.PrivateLinkServiceConnectionStateArgs{
				Description: pulumi.String("Auto-Approved"),
				Status:      pulumi.String("Approved"),
			},
			ResourceGroupName:      pulumi.String("res7687"),
			StorageSyncServiceName: pulumi.String("sss2527"),
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
import com.pulumi.azurenative.storagesync.PrivateEndpointConnection;
import com.pulumi.azurenative.storagesync.PrivateEndpointConnectionArgs;
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
            .storageSyncServiceName("sss2527")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.storagesync.PrivateEndpointConnection("privateEndpointConnection", {
    privateEndpointConnectionName: "{privateEndpointConnectionName}",
    privateLinkServiceConnectionState: {
        description: "Auto-Approved",
        status: "Approved",
    },
    resourceGroupName: "res7687",
    storageSyncServiceName: "sss2527",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.storagesync.PrivateEndpointConnection("privateEndpointConnection",
    private_endpoint_connection_name="{privateEndpointConnectionName}",
    private_link_service_connection_state=azure_native.storagesync.PrivateLinkServiceConnectionStateArgs(
        description="Auto-Approved",
        status="Approved",
    ),
    resource_group_name="res7687",
    storage_sync_service_name="sss2527")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:storagesync:PrivateEndpointConnection
    properties:
      privateEndpointConnectionName: '{privateEndpointConnectionName}'
      privateLinkServiceConnectionState:
        description: Auto-Approved
        status: Approved
      resourceGroupName: res7687
      storageSyncServiceName: sss2527

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:storagesync:PrivateEndpointConnection {privateEndpointConnectionName} /subscriptions/{subscription-id}/resourceGroups/res7231/providers/Microsoft.StorageSync/storageSyncServices/sss2527/privateEndpointConnections/{privateEndpointConnectionName} 
```
