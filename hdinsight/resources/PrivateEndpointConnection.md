The private endpoint connection.
API Version: 2021-06-01.
Previous API Version: 2021-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Approve a private endpoint connection manually.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnection = new AzureNative.HDInsight.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        ClusterName = "cluster1",
        PrivateEndpointConnectionName = "testprivateep.b3bf5fed-9b12-4560-b7d0-2abe1bba07e2",
        PrivateLinkServiceConnectionState = new AzureNative.HDInsight.Inputs.PrivateLinkServiceConnectionStateArgs
        {
            ActionsRequired = "None",
            Description = "update it from pending to approved.",
            Status = "Approved",
        },
        ResourceGroupName = "rg1",
    });

});


```

```go
package main

import (
	hdinsight "github.com/pulumi/pulumi-azure-native-sdk/hdinsight"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := hdinsight.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &hdinsight.PrivateEndpointConnectionArgs{
			ClusterName:                   pulumi.String("cluster1"),
			PrivateEndpointConnectionName: pulumi.String("testprivateep.b3bf5fed-9b12-4560-b7d0-2abe1bba07e2"),
			PrivateLinkServiceConnectionState: &hdinsight.PrivateLinkServiceConnectionStateArgs{
				ActionsRequired: pulumi.String("None"),
				Description:     pulumi.String("update it from pending to approved."),
				Status:          pulumi.String("Approved"),
			},
			ResourceGroupName: pulumi.String("rg1"),
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
import com.pulumi.azurenative.hdinsight.PrivateEndpointConnection;
import com.pulumi.azurenative.hdinsight.PrivateEndpointConnectionArgs;
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
            .clusterName("cluster1")
            .privateEndpointConnectionName("testprivateep.b3bf5fed-9b12-4560-b7d0-2abe1bba07e2")
            .privateLinkServiceConnectionState(Map.ofEntries(
                Map.entry("actionsRequired", "None"),
                Map.entry("description", "update it from pending to approved."),
                Map.entry("status", "Approved")
            ))
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.hdinsight.PrivateEndpointConnection("privateEndpointConnection", {
    clusterName: "cluster1",
    privateEndpointConnectionName: "testprivateep.b3bf5fed-9b12-4560-b7d0-2abe1bba07e2",
    privateLinkServiceConnectionState: {
        actionsRequired: "None",
        description: "update it from pending to approved.",
        status: "Approved",
    },
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.hdinsight.PrivateEndpointConnection("privateEndpointConnection",
    cluster_name="cluster1",
    private_endpoint_connection_name="testprivateep.b3bf5fed-9b12-4560-b7d0-2abe1bba07e2",
    private_link_service_connection_state=azure_native.hdinsight.PrivateLinkServiceConnectionStateArgs(
        actions_required="None",
        description="update it from pending to approved.",
        status="Approved",
    ),
    resource_group_name="rg1")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:hdinsight:PrivateEndpointConnection
    properties:
      clusterName: cluster1
      privateEndpointConnectionName: testprivateep.b3bf5fed-9b12-4560-b7d0-2abe1bba07e2
      privateLinkServiceConnectionState:
        actionsRequired: None
        description: update it from pending to approved.
        status: Approved
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:hdinsight:PrivateEndpointConnection testprivateep.b3bf5fed-9b12-4560-b7d0-2abe1bba07e2 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.HDInsight/clusters/cluster1/privateEndpointConnections/testprivateep.b3bf5fed-9b12-4560-b7d0-2abe1bba07e2 
```
