The Private Endpoint Connection resource.
API Version: 2022-09-01.
Previous API Version: 2021-02-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### StorageAccountPutPrivateEndpointConnection
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnection = new AzureNative.Storage.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        AccountName = "sto9699",
        PrivateEndpointConnectionName = "{privateEndpointConnectionName}",
        PrivateLinkServiceConnectionState = new AzureNative.Storage.Inputs.PrivateLinkServiceConnectionStateArgs
        {
            Description = "Auto-Approved",
            Status = "Approved",
        },
        ResourceGroupName = "res7687",
    });

});


```

```go
package main

import (
	storage "github.com/pulumi/pulumi-azure-native-sdk/storage"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := storage.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &storage.PrivateEndpointConnectionArgs{
			AccountName:                   pulumi.String("sto9699"),
			PrivateEndpointConnectionName: pulumi.String("{privateEndpointConnectionName}"),
			PrivateLinkServiceConnectionState: &storage.PrivateLinkServiceConnectionStateArgs{
				Description: pulumi.String("Auto-Approved"),
				Status:      pulumi.String("Approved"),
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
import com.pulumi.azurenative.storage.PrivateEndpointConnection;
import com.pulumi.azurenative.storage.PrivateEndpointConnectionArgs;
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
            .privateLinkServiceConnectionState(Map.ofEntries(
                Map.entry("description", "Auto-Approved"),
                Map.entry("status", "Approved")
            ))
            .resourceGroupName("res7687")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.storage.PrivateEndpointConnection("privateEndpointConnection", {
    accountName: "sto9699",
    privateEndpointConnectionName: "{privateEndpointConnectionName}",
    privateLinkServiceConnectionState: {
        description: "Auto-Approved",
        status: "Approved",
    },
    resourceGroupName: "res7687",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.storage.PrivateEndpointConnection("privateEndpointConnection",
    account_name="sto9699",
    private_endpoint_connection_name="{privateEndpointConnectionName}",
    private_link_service_connection_state=azure_native.storage.PrivateLinkServiceConnectionStateArgs(
        description="Auto-Approved",
        status="Approved",
    ),
    resource_group_name="res7687")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:storage:PrivateEndpointConnection
    properties:
      accountName: sto9699
      privateEndpointConnectionName: '{privateEndpointConnectionName}'
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
$ pulumi import azure-native:storage:PrivateEndpointConnection {privateEndpointConnectionName} /subscriptions/{subscription-id}/resourceGroups/res7231/providers/Microsoft.Storage/storageAccounts/sto288/privateEndpointConnections/{privateEndpointConnectionName} 
```
