A failover group.
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create failover group
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var failoverGroup = new AzureNative.Sql.FailoverGroup("failoverGroup", new()
    {
        Databases = new[]
        {
            "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/servers/failover-group-primary-server/databases/testdb-1",
            "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/servers/failover-group-primary-server/databases/testdb-2",
        },
        FailoverGroupName = "failover-group-test-3",
        PartnerServers = new[]
        {
            new AzureNative.Sql.Inputs.PartnerInfoArgs
            {
                Id = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/servers/failover-group-secondary-server",
            },
        },
        ReadOnlyEndpoint = new AzureNative.Sql.Inputs.FailoverGroupReadOnlyEndpointArgs
        {
            FailoverPolicy = "Disabled",
        },
        ReadWriteEndpoint = new AzureNative.Sql.Inputs.FailoverGroupReadWriteEndpointArgs
        {
            FailoverPolicy = "Automatic",
            FailoverWithDataLossGracePeriodMinutes = 480,
        },
        ResourceGroupName = "Default",
        ServerName = "failover-group-primary-server",
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
		_, err := sql.NewFailoverGroup(ctx, "failoverGroup", &sql.FailoverGroupArgs{
			Databases: pulumi.StringArray{
				pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/servers/failover-group-primary-server/databases/testdb-1"),
				pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/servers/failover-group-primary-server/databases/testdb-2"),
			},
			FailoverGroupName: pulumi.String("failover-group-test-3"),
			PartnerServers: []sql.PartnerInfoArgs{
				{
					Id: pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/servers/failover-group-secondary-server"),
				},
			},
			ReadOnlyEndpoint: &sql.FailoverGroupReadOnlyEndpointArgs{
				FailoverPolicy: pulumi.String("Disabled"),
			},
			ReadWriteEndpoint: &sql.FailoverGroupReadWriteEndpointArgs{
				FailoverPolicy:                         pulumi.String("Automatic"),
				FailoverWithDataLossGracePeriodMinutes: pulumi.Int(480),
			},
			ResourceGroupName: pulumi.String("Default"),
			ServerName:        pulumi.String("failover-group-primary-server"),
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
import com.pulumi.azurenative.sql.FailoverGroup;
import com.pulumi.azurenative.sql.FailoverGroupArgs;
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
        var failoverGroup = new FailoverGroup("failoverGroup", FailoverGroupArgs.builder()        
            .databases(            
                "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/servers/failover-group-primary-server/databases/testdb-1",
                "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/servers/failover-group-primary-server/databases/testdb-2")
            .failoverGroupName("failover-group-test-3")
            .partnerServers(Map.of("id", "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/servers/failover-group-secondary-server"))
            .readOnlyEndpoint(Map.of("failoverPolicy", "Disabled"))
            .readWriteEndpoint(Map.ofEntries(
                Map.entry("failoverPolicy", "Automatic"),
                Map.entry("failoverWithDataLossGracePeriodMinutes", 480)
            ))
            .resourceGroupName("Default")
            .serverName("failover-group-primary-server")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const failoverGroup = new azure_native.sql.FailoverGroup("failoverGroup", {
    databases: [
        "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/servers/failover-group-primary-server/databases/testdb-1",
        "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/servers/failover-group-primary-server/databases/testdb-2",
    ],
    failoverGroupName: "failover-group-test-3",
    partnerServers: [{
        id: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/servers/failover-group-secondary-server",
    }],
    readOnlyEndpoint: {
        failoverPolicy: "Disabled",
    },
    readWriteEndpoint: {
        failoverPolicy: "Automatic",
        failoverWithDataLossGracePeriodMinutes: 480,
    },
    resourceGroupName: "Default",
    serverName: "failover-group-primary-server",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

failover_group = azure_native.sql.FailoverGroup("failoverGroup",
    databases=[
        "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/servers/failover-group-primary-server/databases/testdb-1",
        "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/servers/failover-group-primary-server/databases/testdb-2",
    ],
    failover_group_name="failover-group-test-3",
    partner_servers=[azure_native.sql.PartnerInfoArgs(
        id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/servers/failover-group-secondary-server",
    )],
    read_only_endpoint=azure_native.sql.FailoverGroupReadOnlyEndpointArgs(
        failover_policy="Disabled",
    ),
    read_write_endpoint=azure_native.sql.FailoverGroupReadWriteEndpointArgs(
        failover_policy="Automatic",
        failover_with_data_loss_grace_period_minutes=480,
    ),
    resource_group_name="Default",
    server_name="failover-group-primary-server")

```

```yaml
resources:
  failoverGroup:
    type: azure-native:sql:FailoverGroup
    properties:
      databases:
        - /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/servers/failover-group-primary-server/databases/testdb-1
        - /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/servers/failover-group-primary-server/databases/testdb-2
      failoverGroupName: failover-group-test-3
      partnerServers:
        - id: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/servers/failover-group-secondary-server
      readOnlyEndpoint:
        failoverPolicy: Disabled
      readWriteEndpoint:
        failoverPolicy: Automatic
        failoverWithDataLossGracePeriodMinutes: 480
      resourceGroupName: Default
      serverName: failover-group-primary-server

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:FailoverGroup failover-group-test-3 /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default/providers/Microsoft.Sql/servers/failover-group-primary-server/failoverGroups/failover-group-test-3 
```
