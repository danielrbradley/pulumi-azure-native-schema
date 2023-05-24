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
    var managedInstancePrivateEndpointConnection = new AzureNative.Sql.ManagedInstancePrivateEndpointConnection("managedInstancePrivateEndpointConnection", new()
    {
        ManagedInstanceName = "test-cl",
        PrivateEndpointConnectionName = "private-endpoint-connection-name",
        PrivateLinkServiceConnectionState = new AzureNative.Sql.Inputs.ManagedInstancePrivateLinkServiceConnectionStatePropertyArgs
        {
            Description = "Approved by johndoe@contoso.com",
            Status = "Approved",
        },
        ResourceGroupName = "Default",
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
		_, err := sql.NewManagedInstancePrivateEndpointConnection(ctx, "managedInstancePrivateEndpointConnection", &sql.ManagedInstancePrivateEndpointConnectionArgs{
			ManagedInstanceName:           pulumi.String("test-cl"),
			PrivateEndpointConnectionName: pulumi.String("private-endpoint-connection-name"),
			PrivateLinkServiceConnectionState: &sql.ManagedInstancePrivateLinkServiceConnectionStatePropertyArgs{
				Description: pulumi.String("Approved by johndoe@contoso.com"),
				Status:      pulumi.String("Approved"),
			},
			ResourceGroupName: pulumi.String("Default"),
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
import com.pulumi.azurenative.sql.ManagedInstancePrivateEndpointConnection;
import com.pulumi.azurenative.sql.ManagedInstancePrivateEndpointConnectionArgs;
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
        var managedInstancePrivateEndpointConnection = new ManagedInstancePrivateEndpointConnection("managedInstancePrivateEndpointConnection", ManagedInstancePrivateEndpointConnectionArgs.builder()        
            .managedInstanceName("test-cl")
            .privateEndpointConnectionName("private-endpoint-connection-name")
            .privateLinkServiceConnectionState(Map.ofEntries(
                Map.entry("description", "Approved by johndoe@contoso.com"),
                Map.entry("status", "Approved")
            ))
            .resourceGroupName("Default")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedInstancePrivateEndpointConnection = new azure_native.sql.ManagedInstancePrivateEndpointConnection("managedInstancePrivateEndpointConnection", {
    managedInstanceName: "test-cl",
    privateEndpointConnectionName: "private-endpoint-connection-name",
    privateLinkServiceConnectionState: {
        description: "Approved by johndoe@contoso.com",
        status: "Approved",
    },
    resourceGroupName: "Default",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_instance_private_endpoint_connection = azure_native.sql.ManagedInstancePrivateEndpointConnection("managedInstancePrivateEndpointConnection",
    managed_instance_name="test-cl",
    private_endpoint_connection_name="private-endpoint-connection-name",
    private_link_service_connection_state=azure_native.sql.ManagedInstancePrivateLinkServiceConnectionStatePropertyArgs(
        description="Approved by johndoe@contoso.com",
        status="Approved",
    ),
    resource_group_name="Default")

```

```yaml
resources:
  managedInstancePrivateEndpointConnection:
    type: azure-native:sql:ManagedInstancePrivateEndpointConnection
    properties:
      managedInstanceName: test-cl
      privateEndpointConnectionName: private-endpoint-connection-name
      privateLinkServiceConnectionState:
        description: Approved by johndoe@contoso.com
        status: Approved
      resourceGroupName: Default

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:ManagedInstancePrivateEndpointConnection private-endpoint-connection-name /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/managedInstances/test-cl/privateEndpointConnections/private-endpoint-connection-name 
```
