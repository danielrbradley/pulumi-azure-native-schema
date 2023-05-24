The Private Endpoint Connection resource.
API Version: 2022-10-01.
Previous API Version: 2021-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### WorkspacePutPrivateEndpointConnection
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnection = new AzureNative.MachineLearningServices.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        PrivateEndpointConnectionName = "{privateEndpointConnectionName}",
        PrivateLinkServiceConnectionState = new AzureNative.MachineLearningServices.Inputs.PrivateLinkServiceConnectionStateArgs
        {
            Description = "Auto-Approved",
            Status = "Approved",
        },
        ResourceGroupName = "rg-1234",
        WorkspaceName = "testworkspace",
    });

});


```

```go
package main

import (
	machinelearningservices "github.com/pulumi/pulumi-azure-native-sdk/machinelearningservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := machinelearningservices.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &machinelearningservices.PrivateEndpointConnectionArgs{
			PrivateEndpointConnectionName: pulumi.String("{privateEndpointConnectionName}"),
			PrivateLinkServiceConnectionState: &machinelearningservices.PrivateLinkServiceConnectionStateArgs{
				Description: pulumi.String("Auto-Approved"),
				Status:      pulumi.String("Approved"),
			},
			ResourceGroupName: pulumi.String("rg-1234"),
			WorkspaceName:     pulumi.String("testworkspace"),
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
import com.pulumi.azurenative.machinelearningservices.PrivateEndpointConnection;
import com.pulumi.azurenative.machinelearningservices.PrivateEndpointConnectionArgs;
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
            .resourceGroupName("rg-1234")
            .workspaceName("testworkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.machinelearningservices.PrivateEndpointConnection("privateEndpointConnection", {
    privateEndpointConnectionName: "{privateEndpointConnectionName}",
    privateLinkServiceConnectionState: {
        description: "Auto-Approved",
        status: "Approved",
    },
    resourceGroupName: "rg-1234",
    workspaceName: "testworkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.machinelearningservices.PrivateEndpointConnection("privateEndpointConnection",
    private_endpoint_connection_name="{privateEndpointConnectionName}",
    private_link_service_connection_state=azure_native.machinelearningservices.PrivateLinkServiceConnectionStateArgs(
        description="Auto-Approved",
        status="Approved",
    ),
    resource_group_name="rg-1234",
    workspace_name="testworkspace")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:machinelearningservices:PrivateEndpointConnection
    properties:
      privateEndpointConnectionName: '{privateEndpointConnectionName}'
      privateLinkServiceConnectionState:
        description: Auto-Approved
        status: Approved
      resourceGroupName: rg-1234
      workspaceName: testworkspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:machinelearningservices:PrivateEndpointConnection {privateEndpointConnectionName} /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/rg-1234/providers/Microsoft.MachineLearningServices/workspaces/testworkspace/privateEndpointConnections/{privateEndpointConnectionName} 
```
