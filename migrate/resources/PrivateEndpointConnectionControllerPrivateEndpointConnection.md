REST model used to encapsulate the user visible state of a PrivateEndpoint.
API Version: 2020-05-01.

{{% examples %}}
## Example Usage
{{% example %}}
### PrivateEndpointConnection_Put
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnectionControllerPrivateEndpointConnection = new AzureNative.Migrate.PrivateEndpointConnectionControllerPrivateEndpointConnection("privateEndpointConnectionControllerPrivateEndpointConnection", new()
    {
        MigrateProjectName = "proj567",
        PeConnectionName = "proj5675162pe.fdccace0-e303-4a79-80c8-3aa7c1f09cc6",
        Properties = new AzureNative.Migrate.Inputs.ConnectionStateRequestBodyPropertiesArgs
        {
            PrivateLinkServiceConnectionState = new AzureNative.Migrate.Inputs.PrivateLinkServiceConnectionStateArgs
            {
                ActionsRequired = "",
                Status = "Approved",
            },
        },
        ResourceGroupName = "pajindTest1",
    });

});


```

```go
package main

import (
	migrate "github.com/pulumi/pulumi-azure-native-sdk/migrate"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := migrate.NewPrivateEndpointConnectionControllerPrivateEndpointConnection(ctx, "privateEndpointConnectionControllerPrivateEndpointConnection", &migrate.PrivateEndpointConnectionControllerPrivateEndpointConnectionArgs{
			MigrateProjectName: pulumi.String("proj567"),
			PeConnectionName:   pulumi.String("proj5675162pe.fdccace0-e303-4a79-80c8-3aa7c1f09cc6"),
			Properties: migrate.PrivateEndpointConnectionPropertiesResponse{
				PrivateLinkServiceConnectionState: &migrate.PrivateLinkServiceConnectionStateArgs{
					ActionsRequired: pulumi.String(""),
					Status:          pulumi.String("Approved"),
				},
			},
			ResourceGroupName: pulumi.String("pajindTest1"),
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
import com.pulumi.azurenative.migrate.PrivateEndpointConnectionControllerPrivateEndpointConnection;
import com.pulumi.azurenative.migrate.PrivateEndpointConnectionControllerPrivateEndpointConnectionArgs;
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
        var privateEndpointConnectionControllerPrivateEndpointConnection = new PrivateEndpointConnectionControllerPrivateEndpointConnection("privateEndpointConnectionControllerPrivateEndpointConnection", PrivateEndpointConnectionControllerPrivateEndpointConnectionArgs.builder()        
            .migrateProjectName("proj567")
            .peConnectionName("proj5675162pe.fdccace0-e303-4a79-80c8-3aa7c1f09cc6")
            .properties(Map.of("privateLinkServiceConnectionState", Map.ofEntries(
                Map.entry("actionsRequired", ""),
                Map.entry("status", "Approved")
            )))
            .resourceGroupName("pajindTest1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnectionControllerPrivateEndpointConnection = new azure_native.migrate.PrivateEndpointConnectionControllerPrivateEndpointConnection("privateEndpointConnectionControllerPrivateEndpointConnection", {
    migrateProjectName: "proj567",
    peConnectionName: "proj5675162pe.fdccace0-e303-4a79-80c8-3aa7c1f09cc6",
    properties: {
        privateLinkServiceConnectionState: {
            actionsRequired: "",
            status: "Approved",
        },
    },
    resourceGroupName: "pajindTest1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection_controller_private_endpoint_connection = azure_native.migrate.PrivateEndpointConnectionControllerPrivateEndpointConnection("privateEndpointConnectionControllerPrivateEndpointConnection",
    migrate_project_name="proj567",
    pe_connection_name="proj5675162pe.fdccace0-e303-4a79-80c8-3aa7c1f09cc6",
    properties=azure_native.migrate.PrivateEndpointConnectionPropertiesResponseArgs(
        private_link_service_connection_state=azure_native.migrate.PrivateLinkServiceConnectionStateArgs(
            actions_required="",
            status="Approved",
        ),
    ),
    resource_group_name="pajindTest1")

```

```yaml
resources:
  privateEndpointConnectionControllerPrivateEndpointConnection:
    type: azure-native:migrate:PrivateEndpointConnectionControllerPrivateEndpointConnection
    properties:
      migrateProjectName: proj567
      peConnectionName: proj5675162pe.fdccace0-e303-4a79-80c8-3aa7c1f09cc6
      properties:
        privateLinkServiceConnectionState:
          actionsRequired:
          status: Approved
      resourceGroupName: pajindTest1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:migrate:PrivateEndpointConnectionControllerPrivateEndpointConnection proj5675162pe.fdccace0-e303-4a79-80c8-3aa7c1f09cc6 /subscriptions/4bd2aa0f-2bd2-4d67-91a8-5a4533d58600/resourceGroups/pajindTest1/providers/Microsoft.Migrate/MigrateProjects/proj567/privateEndpointConnections/proj5675162pe.fdccace0-e303-4a79-80c8-3aa7c1f09cc6 
```
