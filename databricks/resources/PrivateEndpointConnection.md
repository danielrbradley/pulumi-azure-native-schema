The private endpoint connection of a workspace
API Version: 2023-02-01.
Previous API Version: 2022-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Update a private endpoint connection
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnection = new AzureNative.Databricks.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        PrivateEndpointConnectionName = "myWorkspace.23456789-1111-1111-1111-111111111111",
        Properties = new AzureNative.Databricks.Inputs.PrivateEndpointConnectionPropertiesArgs
        {
            PrivateLinkServiceConnectionState = new AzureNative.Databricks.Inputs.PrivateLinkServiceConnectionStateArgs
            {
                Description = "Approved by databricksadmin@contoso.com",
                Status = "Approved",
            },
        },
        ResourceGroupName = "myResourceGroup",
        WorkspaceName = "myWorkspace",
    });

});


```

```go
package main

import (
	databricks "github.com/pulumi/pulumi-azure-native-sdk/databricks"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := databricks.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &databricks.PrivateEndpointConnectionArgs{
			PrivateEndpointConnectionName: pulumi.String("myWorkspace.23456789-1111-1111-1111-111111111111"),
			Properties: databricks.PrivateEndpointConnectionPropertiesResponse{
				PrivateLinkServiceConnectionState: &databricks.PrivateLinkServiceConnectionStateArgs{
					Description: pulumi.String("Approved by databricksadmin@contoso.com"),
					Status:      pulumi.String("Approved"),
				},
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
			WorkspaceName:     pulumi.String("myWorkspace"),
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
import com.pulumi.azurenative.databricks.PrivateEndpointConnection;
import com.pulumi.azurenative.databricks.PrivateEndpointConnectionArgs;
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
            .privateEndpointConnectionName("myWorkspace.23456789-1111-1111-1111-111111111111")
            .properties(Map.of("privateLinkServiceConnectionState", Map.ofEntries(
                Map.entry("description", "Approved by databricksadmin@contoso.com"),
                Map.entry("status", "Approved")
            )))
            .resourceGroupName("myResourceGroup")
            .workspaceName("myWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.databricks.PrivateEndpointConnection("privateEndpointConnection", {
    privateEndpointConnectionName: "myWorkspace.23456789-1111-1111-1111-111111111111",
    properties: {
        privateLinkServiceConnectionState: {
            description: "Approved by databricksadmin@contoso.com",
            status: "Approved",
        },
    },
    resourceGroupName: "myResourceGroup",
    workspaceName: "myWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.databricks.PrivateEndpointConnection("privateEndpointConnection",
    private_endpoint_connection_name="myWorkspace.23456789-1111-1111-1111-111111111111",
    properties=azure_native.databricks.PrivateEndpointConnectionPropertiesResponseArgs(
        private_link_service_connection_state=azure_native.databricks.PrivateLinkServiceConnectionStateArgs(
            description="Approved by databricksadmin@contoso.com",
            status="Approved",
        ),
    ),
    resource_group_name="myResourceGroup",
    workspace_name="myWorkspace")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:databricks:PrivateEndpointConnection
    properties:
      privateEndpointConnectionName: myWorkspace.23456789-1111-1111-1111-111111111111
      properties:
        privateLinkServiceConnectionState:
          description: Approved by databricksadmin@contoso.com
          status: Approved
      resourceGroupName: myResourceGroup
      workspaceName: myWorkspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:databricks:PrivateEndpointConnection myWorkspace.23456789-1111-1111-1111-111111111111 /subscriptions/11111111-1111-1111-1111-111111111111/resourceGroups/myResourceGroup/providers/Microsoft.Databricks/workspaces/myWorkspace/PrivateEndpointConnections/myWorkspace.23456789-1111-1111-1111-111111111111 
```
