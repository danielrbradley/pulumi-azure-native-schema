The private endpoint connection resource.
API Version: 2022-11-08.
Previous API Version: 2018-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Approves or Rejects a Private Endpoint Connection with a given name.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnection = new AzureNative.DBforPostgreSQL.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        ClusterName = "testcluster",
        PrivateEndpointConnectionName = "private-endpoint-connection-name",
        PrivateLinkServiceConnectionState = new AzureNative.DBforPostgreSQL.Inputs.PrivateLinkServiceConnectionStateArgs
        {
            Description = "Approved by johndoe@contoso.com",
            Status = "Approved",
        },
        ResourceGroupName = "TestGroup",
    });

});


```

```go
package main

import (
	dbforpostgresql "github.com/pulumi/pulumi-azure-native-sdk/dbforpostgresql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := dbforpostgresql.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &dbforpostgresql.PrivateEndpointConnectionArgs{
			ClusterName:                   pulumi.String("testcluster"),
			PrivateEndpointConnectionName: pulumi.String("private-endpoint-connection-name"),
			PrivateLinkServiceConnectionState: &dbforpostgresql.PrivateLinkServiceConnectionStateArgs{
				Description: pulumi.String("Approved by johndoe@contoso.com"),
				Status:      pulumi.String("Approved"),
			},
			ResourceGroupName: pulumi.String("TestGroup"),
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
import com.pulumi.azurenative.dbforpostgresql.PrivateEndpointConnection;
import com.pulumi.azurenative.dbforpostgresql.PrivateEndpointConnectionArgs;
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
            .clusterName("testcluster")
            .privateEndpointConnectionName("private-endpoint-connection-name")
            .privateLinkServiceConnectionState(Map.ofEntries(
                Map.entry("description", "Approved by johndoe@contoso.com"),
                Map.entry("status", "Approved")
            ))
            .resourceGroupName("TestGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.dbforpostgresql.PrivateEndpointConnection("privateEndpointConnection", {
    clusterName: "testcluster",
    privateEndpointConnectionName: "private-endpoint-connection-name",
    privateLinkServiceConnectionState: {
        description: "Approved by johndoe@contoso.com",
        status: "Approved",
    },
    resourceGroupName: "TestGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.dbforpostgresql.PrivateEndpointConnection("privateEndpointConnection",
    cluster_name="testcluster",
    private_endpoint_connection_name="private-endpoint-connection-name",
    private_link_service_connection_state=azure_native.dbforpostgresql.PrivateLinkServiceConnectionStateArgs(
        description="Approved by johndoe@contoso.com",
        status="Approved",
    ),
    resource_group_name="TestGroup")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:dbforpostgresql:PrivateEndpointConnection
    properties:
      clusterName: testcluster
      privateEndpointConnectionName: private-endpoint-connection-name
      privateLinkServiceConnectionState:
        description: Approved by johndoe@contoso.com
        status: Approved
      resourceGroupName: TestGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:dbforpostgresql:PrivateEndpointConnection private-endpoint-connection-name /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/TestResourceGroup/providers/Microsoft.DBforPostgreSQL/serverGroupsv2/testcluster/privateEndpointConnections/private-endpoint-connection-name 
```
