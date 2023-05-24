A server trust group.
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create server trust group
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var serverTrustGroup = new AzureNative.Sql.ServerTrustGroup("serverTrustGroup", new()
    {
        GroupMembers = new[]
        {
            new AzureNative.Sql.Inputs.ServerInfoArgs
            {
                ServerId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/managedInstances/managedInstance-1",
            },
            new AzureNative.Sql.Inputs.ServerInfoArgs
            {
                ServerId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/managedInstances/managedInstance-2",
            },
        },
        LocationName = "Japan East",
        ResourceGroupName = "Default",
        ServerTrustGroupName = "server-trust-group-test",
        TrustScopes = new[]
        {
            "GlobalTransactions",
            "ServiceBroker",
        },
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
		_, err := sql.NewServerTrustGroup(ctx, "serverTrustGroup", &sql.ServerTrustGroupArgs{
			GroupMembers: []sql.ServerInfoArgs{
				{
					ServerId: pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/managedInstances/managedInstance-1"),
				},
				{
					ServerId: pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/managedInstances/managedInstance-2"),
				},
			},
			LocationName:         pulumi.String("Japan East"),
			ResourceGroupName:    pulumi.String("Default"),
			ServerTrustGroupName: pulumi.String("server-trust-group-test"),
			TrustScopes: pulumi.StringArray{
				pulumi.String("GlobalTransactions"),
				pulumi.String("ServiceBroker"),
			},
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
import com.pulumi.azurenative.sql.ServerTrustGroup;
import com.pulumi.azurenative.sql.ServerTrustGroupArgs;
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
        var serverTrustGroup = new ServerTrustGroup("serverTrustGroup", ServerTrustGroupArgs.builder()        
            .groupMembers(            
                Map.of("serverId", "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/managedInstances/managedInstance-1"),
                Map.of("serverId", "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/managedInstances/managedInstance-2"))
            .locationName("Japan East")
            .resourceGroupName("Default")
            .serverTrustGroupName("server-trust-group-test")
            .trustScopes(            
                "GlobalTransactions",
                "ServiceBroker")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const serverTrustGroup = new azure_native.sql.ServerTrustGroup("serverTrustGroup", {
    groupMembers: [
        {
            serverId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/managedInstances/managedInstance-1",
        },
        {
            serverId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/managedInstances/managedInstance-2",
        },
    ],
    locationName: "Japan East",
    resourceGroupName: "Default",
    serverTrustGroupName: "server-trust-group-test",
    trustScopes: [
        "GlobalTransactions",
        "ServiceBroker",
    ],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

server_trust_group = azure_native.sql.ServerTrustGroup("serverTrustGroup",
    group_members=[
        azure_native.sql.ServerInfoArgs(
            server_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/managedInstances/managedInstance-1",
        ),
        azure_native.sql.ServerInfoArgs(
            server_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/managedInstances/managedInstance-2",
        ),
    ],
    location_name="Japan East",
    resource_group_name="Default",
    server_trust_group_name="server-trust-group-test",
    trust_scopes=[
        "GlobalTransactions",
        "ServiceBroker",
    ])

```

```yaml
resources:
  serverTrustGroup:
    type: azure-native:sql:ServerTrustGroup
    properties:
      groupMembers:
        - serverId: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/managedInstances/managedInstance-1
        - serverId: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/managedInstances/managedInstance-2
      locationName: Japan East
      resourceGroupName: Default
      serverTrustGroupName: server-trust-group-test
      trustScopes:
        - GlobalTransactions
        - ServiceBroker

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:ServerTrustGroup server-trust-group-test /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/locations/Japan East/serverTrustGroups/server-trust-group-test 
```
