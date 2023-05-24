The Private Endpoint Connection resource.
API Version: 2022-10-01.
Previous API Version: 2020-03-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PrivateEndpointConnectionCreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnection = new AzureNative.DeviceUpdate.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        AccountName = "contoso",
        PrivateEndpointConnectionName = "peexample01",
        PrivateLinkServiceConnectionState = new AzureNative.DeviceUpdate.Inputs.PrivateLinkServiceConnectionStateArgs
        {
            Description = "Auto-Approved",
            Status = "Approved",
        },
        ResourceGroupName = "test-rg",
    });

});


```

```go
package main

import (
	deviceupdate "github.com/pulumi/pulumi-azure-native-sdk/deviceupdate"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := deviceupdate.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &deviceupdate.PrivateEndpointConnectionArgs{
			AccountName:                   pulumi.String("contoso"),
			PrivateEndpointConnectionName: pulumi.String("peexample01"),
			PrivateLinkServiceConnectionState: &deviceupdate.PrivateLinkServiceConnectionStateArgs{
				Description: pulumi.String("Auto-Approved"),
				Status:      pulumi.String("Approved"),
			},
			ResourceGroupName: pulumi.String("test-rg"),
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
import com.pulumi.azurenative.deviceupdate.PrivateEndpointConnection;
import com.pulumi.azurenative.deviceupdate.PrivateEndpointConnectionArgs;
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
            .accountName("contoso")
            .privateEndpointConnectionName("peexample01")
            .privateLinkServiceConnectionState(Map.ofEntries(
                Map.entry("description", "Auto-Approved"),
                Map.entry("status", "Approved")
            ))
            .resourceGroupName("test-rg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.deviceupdate.PrivateEndpointConnection("privateEndpointConnection", {
    accountName: "contoso",
    privateEndpointConnectionName: "peexample01",
    privateLinkServiceConnectionState: {
        description: "Auto-Approved",
        status: "Approved",
    },
    resourceGroupName: "test-rg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.deviceupdate.PrivateEndpointConnection("privateEndpointConnection",
    account_name="contoso",
    private_endpoint_connection_name="peexample01",
    private_link_service_connection_state=azure_native.deviceupdate.PrivateLinkServiceConnectionStateArgs(
        description="Auto-Approved",
        status="Approved",
    ),
    resource_group_name="test-rg")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:deviceupdate:PrivateEndpointConnection
    properties:
      accountName: contoso
      privateEndpointConnectionName: peexample01
      privateLinkServiceConnectionState:
        description: Auto-Approved
        status: Approved
      resourceGroupName: test-rg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:deviceupdate:PrivateEndpointConnection peexample01 /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-rg/providers/Microsoft.DeviceUpdate/accounts/contoso/privateEndpointConnections/peexample01 
```
