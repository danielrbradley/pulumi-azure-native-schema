A private endpoint connection
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Approve or reject a private endpoint connection with a given name.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnection = new AzureNative.Sql.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        PrivateEndpointConnectionName = "private-endpoint-connection-name",
        PrivateLinkServiceConnectionState = new AzureNative.Sql.Inputs.PrivateLinkServiceConnectionStatePropertyArgs
        {
            Description = "Approved by johndoe@contoso.com",
            Status = "Approved",
        },
        ResourceGroupName = "Default",
        ServerName = "test-svr",
    });

});


```

```go
package main

import (
	sql "github.com/pulumi/pulumi-azure-native-sdk/sql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := sql.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &sql.PrivateEndpointConnectionArgs{
			PrivateEndpointConnectionName: pulumi.String("private-endpoint-connection-name"),
			PrivateLinkServiceConnectionState: &sql.PrivateLinkServiceConnectionStatePropertyArgs{
				Description: pulumi.String("Approved by johndoe@contoso.com"),
				Status:      pulumi.String("Approved"),
			},
			ResourceGroupName: pulumi.String("Default"),
			ServerName:        pulumi.String("test-svr"),
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
import com.pulumi.azurenative.sql.PrivateEndpointConnection;
import com.pulumi.azurenative.sql.PrivateEndpointConnectionArgs;
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
            .privateEndpointConnectionName("private-endpoint-connection-name")
            .privateLinkServiceConnectionState(Map.ofEntries(
                Map.entry("description", "Approved by johndoe@contoso.com"),
                Map.entry("status", "Approved")
            ))
            .resourceGroupName("Default")
            .serverName("test-svr")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.sql.PrivateEndpointConnection("privateEndpointConnection", {
    privateEndpointConnectionName: "private-endpoint-connection-name",
    privateLinkServiceConnectionState: {
        description: "Approved by johndoe@contoso.com",
        status: "Approved",
    },
    resourceGroupName: "Default",
    serverName: "test-svr",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.sql.PrivateEndpointConnection("privateEndpointConnection",
    private_endpoint_connection_name="private-endpoint-connection-name",
    private_link_service_connection_state=azure_native.sql.PrivateLinkServiceConnectionStatePropertyArgs(
        description="Approved by johndoe@contoso.com",
        status="Approved",
    ),
    resource_group_name="Default",
    server_name="test-svr")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:sql:PrivateEndpointConnection
    properties:
      privateEndpointConnectionName: private-endpoint-connection-name
      privateLinkServiceConnectionState:
        description: Approved by johndoe@contoso.com
        status: Approved
      resourceGroupName: Default
      serverName: test-svr

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:PrivateEndpointConnection private-endpoint-connection-name /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/servers/test-svr/privateEndpointConnections/private-endpoint-connection-name 
```
