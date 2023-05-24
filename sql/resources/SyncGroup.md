An Azure SQL Database sync group.
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a sync group
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var syncGroup = new AzureNative.Sql.SyncGroup("syncGroup", new()
    {
        ConflictResolutionPolicy = "HubWin",
        DatabaseName = "syncgroupcrud-4328",
        HubDatabaseUserName = "hubUser",
        Interval = -1,
        ResourceGroupName = "syncgroupcrud-65440",
        ServerName = "syncgroupcrud-8475",
        SyncDatabaseId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/syncgroupcrud-3521/providers/Microsoft.Sql/servers/syncgroupcrud-8475/databases/syncgroupcrud-4328",
        SyncGroupName = "syncgroupcrud-3187",
        UsePrivateLinkConnection = true,
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
		_, err := sql.NewSyncGroup(ctx, "syncGroup", &sql.SyncGroupArgs{
			ConflictResolutionPolicy: pulumi.String("HubWin"),
			DatabaseName:             pulumi.String("syncgroupcrud-4328"),
			HubDatabaseUserName:      pulumi.String("hubUser"),
			Interval:                 -1,
			ResourceGroupName:        pulumi.String("syncgroupcrud-65440"),
			ServerName:               pulumi.String("syncgroupcrud-8475"),
			SyncDatabaseId:           pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/syncgroupcrud-3521/providers/Microsoft.Sql/servers/syncgroupcrud-8475/databases/syncgroupcrud-4328"),
			SyncGroupName:            pulumi.String("syncgroupcrud-3187"),
			UsePrivateLinkConnection: pulumi.Bool(true),
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
import com.pulumi.azurenative.sql.SyncGroup;
import com.pulumi.azurenative.sql.SyncGroupArgs;
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
        var syncGroup = new SyncGroup("syncGroup", SyncGroupArgs.builder()        
            .conflictResolutionPolicy("HubWin")
            .databaseName("syncgroupcrud-4328")
            .hubDatabaseUserName("hubUser")
            .interval("TODO: GenUnaryOpExpression")
            .resourceGroupName("syncgroupcrud-65440")
            .serverName("syncgroupcrud-8475")
            .syncDatabaseId("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/syncgroupcrud-3521/providers/Microsoft.Sql/servers/syncgroupcrud-8475/databases/syncgroupcrud-4328")
            .syncGroupName("syncgroupcrud-3187")
            .usePrivateLinkConnection(true)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const syncGroup = new azure_native.sql.SyncGroup("syncGroup", {
    conflictResolutionPolicy: "HubWin",
    databaseName: "syncgroupcrud-4328",
    hubDatabaseUserName: "hubUser",
    interval: -1,
    resourceGroupName: "syncgroupcrud-65440",
    serverName: "syncgroupcrud-8475",
    syncDatabaseId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/syncgroupcrud-3521/providers/Microsoft.Sql/servers/syncgroupcrud-8475/databases/syncgroupcrud-4328",
    syncGroupName: "syncgroupcrud-3187",
    usePrivateLinkConnection: true,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sync_group = azure_native.sql.SyncGroup("syncGroup",
    conflict_resolution_policy="HubWin",
    database_name="syncgroupcrud-4328",
    hub_database_user_name="hubUser",
    interval=-1,
    resource_group_name="syncgroupcrud-65440",
    server_name="syncgroupcrud-8475",
    sync_database_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/syncgroupcrud-3521/providers/Microsoft.Sql/servers/syncgroupcrud-8475/databases/syncgroupcrud-4328",
    sync_group_name="syncgroupcrud-3187",
    use_private_link_connection=True)

```

```yaml

```

{{% /example %}}
{{% example %}}
### Update a sync group
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var syncGroup = new AzureNative.Sql.SyncGroup("syncGroup", new()
    {
        ConflictResolutionPolicy = "HubWin",
        DatabaseName = "syncgroupcrud-4328",
        HubDatabaseUserName = "hubUser",
        Interval = -1,
        ResourceGroupName = "syncgroupcrud-65440",
        ServerName = "syncgroupcrud-8475",
        SyncDatabaseId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/syncgroupcrud-3521/providers/Microsoft.Sql/servers/syncgroupcrud-8475/databases/syncgroupcrud-4328",
        SyncGroupName = "syncgroupcrud-3187",
        UsePrivateLinkConnection = true,
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
		_, err := sql.NewSyncGroup(ctx, "syncGroup", &sql.SyncGroupArgs{
			ConflictResolutionPolicy: pulumi.String("HubWin"),
			DatabaseName:             pulumi.String("syncgroupcrud-4328"),
			HubDatabaseUserName:      pulumi.String("hubUser"),
			Interval:                 -1,
			ResourceGroupName:        pulumi.String("syncgroupcrud-65440"),
			ServerName:               pulumi.String("syncgroupcrud-8475"),
			SyncDatabaseId:           pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/syncgroupcrud-3521/providers/Microsoft.Sql/servers/syncgroupcrud-8475/databases/syncgroupcrud-4328"),
			SyncGroupName:            pulumi.String("syncgroupcrud-3187"),
			UsePrivateLinkConnection: pulumi.Bool(true),
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
import com.pulumi.azurenative.sql.SyncGroup;
import com.pulumi.azurenative.sql.SyncGroupArgs;
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
        var syncGroup = new SyncGroup("syncGroup", SyncGroupArgs.builder()        
            .conflictResolutionPolicy("HubWin")
            .databaseName("syncgroupcrud-4328")
            .hubDatabaseUserName("hubUser")
            .interval("TODO: GenUnaryOpExpression")
            .resourceGroupName("syncgroupcrud-65440")
            .serverName("syncgroupcrud-8475")
            .syncDatabaseId("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/syncgroupcrud-3521/providers/Microsoft.Sql/servers/syncgroupcrud-8475/databases/syncgroupcrud-4328")
            .syncGroupName("syncgroupcrud-3187")
            .usePrivateLinkConnection(true)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const syncGroup = new azure_native.sql.SyncGroup("syncGroup", {
    conflictResolutionPolicy: "HubWin",
    databaseName: "syncgroupcrud-4328",
    hubDatabaseUserName: "hubUser",
    interval: -1,
    resourceGroupName: "syncgroupcrud-65440",
    serverName: "syncgroupcrud-8475",
    syncDatabaseId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/syncgroupcrud-3521/providers/Microsoft.Sql/servers/syncgroupcrud-8475/databases/syncgroupcrud-4328",
    syncGroupName: "syncgroupcrud-3187",
    usePrivateLinkConnection: true,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sync_group = azure_native.sql.SyncGroup("syncGroup",
    conflict_resolution_policy="HubWin",
    database_name="syncgroupcrud-4328",
    hub_database_user_name="hubUser",
    interval=-1,
    resource_group_name="syncgroupcrud-65440",
    server_name="syncgroupcrud-8475",
    sync_database_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/syncgroupcrud-3521/providers/Microsoft.Sql/servers/syncgroupcrud-8475/databases/syncgroupcrud-4328",
    sync_group_name="syncgroupcrud-3187",
    use_private_link_connection=True)

```

```yaml

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:SyncGroup syncgroupcrud-3187 /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/syncgroupcrud-3521/providers/Microsoft.Sql/servers/syncgroupcrud-8475/databases/syncgroupcrud-4328/syncGroups/syncgroupcrud-3187 
```
