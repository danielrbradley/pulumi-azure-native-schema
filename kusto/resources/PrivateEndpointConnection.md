A private endpoint connection
API Version: 2022-12-29.
Previous API Version: 2021-08-27. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

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
    var privateEndpointConnection = new AzureNative.Kusto.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        ClusterName = "kustoclusterrptest4",
        PrivateEndpointConnectionName = "privateEndpointTest",
        PrivateLinkServiceConnectionState = new AzureNative.Kusto.Inputs.PrivateLinkServiceConnectionStatePropertyArgs
        {
            Description = "Approved by johndoe@contoso.com",
            Status = "Approved",
        },
        ResourceGroupName = "kustorptest",
    });

});


```

```go
package main

import (
	kusto "github.com/pulumi/pulumi-azure-native-sdk/kusto"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := kusto.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &kusto.PrivateEndpointConnectionArgs{
			ClusterName:                   pulumi.String("kustoclusterrptest4"),
			PrivateEndpointConnectionName: pulumi.String("privateEndpointTest"),
			PrivateLinkServiceConnectionState: &kusto.PrivateLinkServiceConnectionStatePropertyArgs{
				Description: pulumi.String("Approved by johndoe@contoso.com"),
				Status:      pulumi.String("Approved"),
			},
			ResourceGroupName: pulumi.String("kustorptest"),
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
import com.pulumi.azurenative.kusto.PrivateEndpointConnection;
import com.pulumi.azurenative.kusto.PrivateEndpointConnectionArgs;
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
            .clusterName("kustoclusterrptest4")
            .privateEndpointConnectionName("privateEndpointTest")
            .privateLinkServiceConnectionState(Map.ofEntries(
                Map.entry("description", "Approved by johndoe@contoso.com"),
                Map.entry("status", "Approved")
            ))
            .resourceGroupName("kustorptest")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.kusto.PrivateEndpointConnection("privateEndpointConnection", {
    clusterName: "kustoclusterrptest4",
    privateEndpointConnectionName: "privateEndpointTest",
    privateLinkServiceConnectionState: {
        description: "Approved by johndoe@contoso.com",
        status: "Approved",
    },
    resourceGroupName: "kustorptest",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.kusto.PrivateEndpointConnection("privateEndpointConnection",
    cluster_name="kustoclusterrptest4",
    private_endpoint_connection_name="privateEndpointTest",
    private_link_service_connection_state=azure_native.kusto.PrivateLinkServiceConnectionStatePropertyArgs(
        description="Approved by johndoe@contoso.com",
        status="Approved",
    ),
    resource_group_name="kustorptest")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:kusto:PrivateEndpointConnection
    properties:
      clusterName: kustoclusterrptest4
      privateEndpointConnectionName: privateEndpointTest
      privateLinkServiceConnectionState:
        description: Approved by johndoe@contoso.com
        status: Approved
      resourceGroupName: kustorptest

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:kusto:PrivateEndpointConnection privateEndpointTest /subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.Kusto/Clusters/KustoClusterRPTest4/privateEndpointConnections/privateEndpointTest 
```
