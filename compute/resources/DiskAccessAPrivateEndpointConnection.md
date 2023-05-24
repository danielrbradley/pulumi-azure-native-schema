The Private Endpoint Connection resource.
API Version: 2022-07-02.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Approve a Private Endpoint Connection under a disk access resource.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var diskAccessAPrivateEndpointConnection = new AzureNative.Compute.DiskAccessAPrivateEndpointConnection("diskAccessAPrivateEndpointConnection", new()
    {
        DiskAccessName = "myDiskAccess",
        PrivateEndpointConnectionName = "myPrivateEndpointConnection",
        PrivateLinkServiceConnectionState = new AzureNative.Compute.Inputs.PrivateLinkServiceConnectionStateArgs
        {
            Description = "Approving myPrivateEndpointConnection",
            Status = "Approved",
        },
        ResourceGroupName = "myResourceGroup",
    });

});


```

```go
package main

import (
	compute "github.com/pulumi/pulumi-azure-native-sdk/compute"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := compute.NewDiskAccessAPrivateEndpointConnection(ctx, "diskAccessAPrivateEndpointConnection", &compute.DiskAccessAPrivateEndpointConnectionArgs{
			DiskAccessName:                pulumi.String("myDiskAccess"),
			PrivateEndpointConnectionName: pulumi.String("myPrivateEndpointConnection"),
			PrivateLinkServiceConnectionState: &compute.PrivateLinkServiceConnectionStateArgs{
				Description: pulumi.String("Approving myPrivateEndpointConnection"),
				Status:      pulumi.String("Approved"),
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.compute.DiskAccessAPrivateEndpointConnection;
import com.pulumi.azurenative.compute.DiskAccessAPrivateEndpointConnectionArgs;
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
        var diskAccessAPrivateEndpointConnection = new DiskAccessAPrivateEndpointConnection("diskAccessAPrivateEndpointConnection", DiskAccessAPrivateEndpointConnectionArgs.builder()        
            .diskAccessName("myDiskAccess")
            .privateEndpointConnectionName("myPrivateEndpointConnection")
            .privateLinkServiceConnectionState(Map.ofEntries(
                Map.entry("description", "Approving myPrivateEndpointConnection"),
                Map.entry("status", "Approved")
            ))
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const diskAccessAPrivateEndpointConnection = new azure_native.compute.DiskAccessAPrivateEndpointConnection("diskAccessAPrivateEndpointConnection", {
    diskAccessName: "myDiskAccess",
    privateEndpointConnectionName: "myPrivateEndpointConnection",
    privateLinkServiceConnectionState: {
        description: "Approving myPrivateEndpointConnection",
        status: "Approved",
    },
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

disk_access_a_private_endpoint_connection = azure_native.compute.DiskAccessAPrivateEndpointConnection("diskAccessAPrivateEndpointConnection",
    disk_access_name="myDiskAccess",
    private_endpoint_connection_name="myPrivateEndpointConnection",
    private_link_service_connection_state=azure_native.compute.PrivateLinkServiceConnectionStateArgs(
        description="Approving myPrivateEndpointConnection",
        status="Approved",
    ),
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  diskAccessAPrivateEndpointConnection:
    type: azure-native:compute:DiskAccessAPrivateEndpointConnection
    properties:
      diskAccessName: myDiskAccess
      privateEndpointConnectionName: myPrivateEndpointConnection
      privateLinkServiceConnectionState:
        description: Approving myPrivateEndpointConnection
        status: Approved
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:compute:DiskAccessAPrivateEndpointConnection myPrivateEndpointConnectionName /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskAccesses/myDiskAccess/privateEndpoinConnections/myPrivateEndpointConnectionName 
```
