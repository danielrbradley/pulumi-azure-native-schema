A private endpoint connection
API Version: 2021-06-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Approve private endpoint connection
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnection = new AzureNative.Synapse.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        PrivateEndpointConnectionName = "ExamplePrivateEndpointConnection",
        PrivateLinkServiceConnectionState = new AzureNative.Synapse.Inputs.PrivateLinkServiceConnectionStateArgs
        {
            Description = "Approved by abc@example.com",
            Status = "Approved",
        },
        ResourceGroupName = "ExampleResourceGroup",
        WorkspaceName = "ExampleWorkspace",
    });

});


```

```go
package main

import (
	synapse "github.com/pulumi/pulumi-azure-native-sdk/synapse"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := synapse.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &synapse.PrivateEndpointConnectionArgs{
			PrivateEndpointConnectionName: pulumi.String("ExamplePrivateEndpointConnection"),
			PrivateLinkServiceConnectionState: &synapse.PrivateLinkServiceConnectionStateArgs{
				Description: pulumi.String("Approved by abc@example.com"),
				Status:      pulumi.String("Approved"),
			},
			ResourceGroupName: pulumi.String("ExampleResourceGroup"),
			WorkspaceName:     pulumi.String("ExampleWorkspace"),
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
import com.pulumi.azurenative.synapse.PrivateEndpointConnection;
import com.pulumi.azurenative.synapse.PrivateEndpointConnectionArgs;
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
            .privateEndpointConnectionName("ExamplePrivateEndpointConnection")
            .privateLinkServiceConnectionState(Map.ofEntries(
                Map.entry("description", "Approved by abc@example.com"),
                Map.entry("status", "Approved")
            ))
            .resourceGroupName("ExampleResourceGroup")
            .workspaceName("ExampleWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.synapse.PrivateEndpointConnection("privateEndpointConnection", {
    privateEndpointConnectionName: "ExamplePrivateEndpointConnection",
    privateLinkServiceConnectionState: {
        description: "Approved by abc@example.com",
        status: "Approved",
    },
    resourceGroupName: "ExampleResourceGroup",
    workspaceName: "ExampleWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.synapse.PrivateEndpointConnection("privateEndpointConnection",
    private_endpoint_connection_name="ExamplePrivateEndpointConnection",
    private_link_service_connection_state=azure_native.synapse.PrivateLinkServiceConnectionStateArgs(
        description="Approved by abc@example.com",
        status="Approved",
    ),
    resource_group_name="ExampleResourceGroup",
    workspace_name="ExampleWorkspace")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:synapse:PrivateEndpointConnection
    properties:
      privateEndpointConnectionName: ExamplePrivateEndpointConnection
      privateLinkServiceConnectionState:
        description: Approved by abc@example.com
        status: Approved
      resourceGroupName: ExampleResourceGroup
      workspaceName: ExampleWorkspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:synapse:PrivateEndpointConnection sql /subscriptions/01234567-89ab-4def-0123-456789abcdef/resourceGroups/ExampleResourceGroup/providers/Microsoft.Synapse/workspaces/ExampleWorkspace/privateEndpointConnections/ExamplePrivateEndpointConnection 
```
