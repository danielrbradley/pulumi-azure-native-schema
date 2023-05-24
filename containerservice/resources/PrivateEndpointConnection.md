A private endpoint connection
API Version: 2023-01-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Update Private Endpoint Connection
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnection = new AzureNative.ContainerService.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        PrivateEndpointConnectionName = "privateendpointconnection1",
        PrivateLinkServiceConnectionState = new AzureNative.ContainerService.Inputs.PrivateLinkServiceConnectionStateArgs
        {
            Status = "Approved",
        },
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
    });

});


```

```go
package main

import (
	containerservice "github.com/pulumi/pulumi-azure-native-sdk/containerservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := containerservice.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &containerservice.PrivateEndpointConnectionArgs{
			PrivateEndpointConnectionName: pulumi.String("privateendpointconnection1"),
			PrivateLinkServiceConnectionState: &containerservice.PrivateLinkServiceConnectionStateArgs{
				Status: pulumi.String("Approved"),
			},
			ResourceGroupName: pulumi.String("rg1"),
			ResourceName:      pulumi.String("clustername1"),
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
import com.pulumi.azurenative.containerservice.PrivateEndpointConnection;
import com.pulumi.azurenative.containerservice.PrivateEndpointConnectionArgs;
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
            .privateEndpointConnectionName("privateendpointconnection1")
            .privateLinkServiceConnectionState(Map.of("status", "Approved"))
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.containerservice.PrivateEndpointConnection("privateEndpointConnection", {
    privateEndpointConnectionName: "privateendpointconnection1",
    privateLinkServiceConnectionState: {
        status: "Approved",
    },
    resourceGroupName: "rg1",
    resourceName: "clustername1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.containerservice.PrivateEndpointConnection("privateEndpointConnection",
    private_endpoint_connection_name="privateendpointconnection1",
    private_link_service_connection_state=azure_native.containerservice.PrivateLinkServiceConnectionStateArgs(
        status="Approved",
    ),
    resource_group_name="rg1",
    resource_name_="clustername1")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:containerservice:PrivateEndpointConnection
    properties:
      privateEndpointConnectionName: privateendpointconnection1
      privateLinkServiceConnectionState:
        status: Approved
      resourceGroupName: rg1
      resourceName: clustername1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:containerservice:PrivateEndpointConnection privateendpointconnection1 /subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.ContainerService/managedCluster/clustername1/privateEndpointConnections/privateendpointconnection1 
```
