An Azure SQL Database sync member.
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a new sync member
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var syncMember = new AzureNative.Sql.SyncMember("syncMember", new()
    {
        DatabaseName = "syncgroupcrud-4328",
        DatabaseType = "AzureSqlDatabase",
        ResourceGroupName = "syncgroupcrud-65440",
        ServerName = "syncgroupcrud-8475",
        SyncDirection = "Bidirectional",
        SyncGroupName = "syncgroupcrud-3187",
        SyncMemberAzureDatabaseResourceId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/syncgroupcrud-65440/providers/Microsoft.Sql/servers/syncgroupcrud-8475/databases/syncgroupcrud-4328",
        SyncMemberName = "syncmembercrud-4879",
        UsePrivateLinkConnection = true,
        UserName = "myUser",
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
		_, err := sql.NewSyncMember(ctx, "syncMember", &sql.SyncMemberArgs{
			DatabaseName:                      pulumi.String("syncgroupcrud-4328"),
			DatabaseType:                      pulumi.String("AzureSqlDatabase"),
			ResourceGroupName:                 pulumi.String("syncgroupcrud-65440"),
			ServerName:                        pulumi.String("syncgroupcrud-8475"),
			SyncDirection:                     pulumi.String("Bidirectional"),
			SyncGroupName:                     pulumi.String("syncgroupcrud-3187"),
			SyncMemberAzureDatabaseResourceId: pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/syncgroupcrud-65440/providers/Microsoft.Sql/servers/syncgroupcrud-8475/databases/syncgroupcrud-4328"),
			SyncMemberName:                    pulumi.String("syncmembercrud-4879"),
			UsePrivateLinkConnection:          pulumi.Bool(true),
			UserName:                          pulumi.String("myUser"),
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
import com.pulumi.azurenative.sql.SyncMember;
import com.pulumi.azurenative.sql.SyncMemberArgs;
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
        var syncMember = new SyncMember("syncMember", SyncMemberArgs.builder()        
            .databaseName("syncgroupcrud-4328")
            .databaseType("AzureSqlDatabase")
            .resourceGroupName("syncgroupcrud-65440")
            .serverName("syncgroupcrud-8475")
            .syncDirection("Bidirectional")
            .syncGroupName("syncgroupcrud-3187")
            .syncMemberAzureDatabaseResourceId("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/syncgroupcrud-65440/providers/Microsoft.Sql/servers/syncgroupcrud-8475/databases/syncgroupcrud-4328")
            .syncMemberName("syncmembercrud-4879")
            .usePrivateLinkConnection(true)
            .userName("myUser")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const syncMember = new azure_native.sql.SyncMember("syncMember", {
    databaseName: "syncgroupcrud-4328",
    databaseType: "AzureSqlDatabase",
    resourceGroupName: "syncgroupcrud-65440",
    serverName: "syncgroupcrud-8475",
    syncDirection: "Bidirectional",
    syncGroupName: "syncgroupcrud-3187",
    syncMemberAzureDatabaseResourceId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/syncgroupcrud-65440/providers/Microsoft.Sql/servers/syncgroupcrud-8475/databases/syncgroupcrud-4328",
    syncMemberName: "syncmembercrud-4879",
    usePrivateLinkConnection: true,
    userName: "myUser",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sync_member = azure_native.sql.SyncMember("syncMember",
    database_name="syncgroupcrud-4328",
    database_type="AzureSqlDatabase",
    resource_group_name="syncgroupcrud-65440",
    server_name="syncgroupcrud-8475",
    sync_direction="Bidirectional",
    sync_group_name="syncgroupcrud-3187",
    sync_member_azure_database_resource_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/syncgroupcrud-65440/providers/Microsoft.Sql/servers/syncgroupcrud-8475/databases/syncgroupcrud-4328",
    sync_member_name="syncmembercrud-4879",
    use_private_link_connection=True,
    user_name="myUser")

```

```yaml
resources:
  syncMember:
    type: azure-native:sql:SyncMember
    properties:
      databaseName: syncgroupcrud-4328
      databaseType: AzureSqlDatabase
      resourceGroupName: syncgroupcrud-65440
      serverName: syncgroupcrud-8475
      syncDirection: Bidirectional
      syncGroupName: syncgroupcrud-3187
      syncMemberAzureDatabaseResourceId: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/syncgroupcrud-65440/providers/Microsoft.Sql/servers/syncgroupcrud-8475/databases/syncgroupcrud-4328
      syncMemberName: syncmembercrud-4879
      usePrivateLinkConnection: true
      userName: myUser

```

{{% /example %}}
{{% example %}}
### Update a sync member
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var syncMember = new AzureNative.Sql.SyncMember("syncMember", new()
    {
        DatabaseName = "syncgroupcrud-7421",
        DatabaseType = "AzureSqlDatabase",
        ResourceGroupName = "syncgroupcrud-65440",
        ServerName = "syncgroupcrud-3379.database.windows.net",
        SyncDirection = "Bidirectional",
        SyncGroupName = "syncgroupcrud-3187",
        SyncMemberAzureDatabaseResourceId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/syncgroupcrud-65440/providers/Microsoft.Sql/servers/syncgroupcrud-8475/databases/syncgroupcrud-4328",
        SyncMemberName = "syncmembercrud-4879",
        UsePrivateLinkConnection = true,
        UserName = "myUser",
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
		_, err := sql.NewSyncMember(ctx, "syncMember", &sql.SyncMemberArgs{
			DatabaseName:                      pulumi.String("syncgroupcrud-7421"),
			DatabaseType:                      pulumi.String("AzureSqlDatabase"),
			ResourceGroupName:                 pulumi.String("syncgroupcrud-65440"),
			ServerName:                        pulumi.String("syncgroupcrud-3379.database.windows.net"),
			SyncDirection:                     pulumi.String("Bidirectional"),
			SyncGroupName:                     pulumi.String("syncgroupcrud-3187"),
			SyncMemberAzureDatabaseResourceId: pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/syncgroupcrud-65440/providers/Microsoft.Sql/servers/syncgroupcrud-8475/databases/syncgroupcrud-4328"),
			SyncMemberName:                    pulumi.String("syncmembercrud-4879"),
			UsePrivateLinkConnection:          pulumi.Bool(true),
			UserName:                          pulumi.String("myUser"),
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
import com.pulumi.azurenative.sql.SyncMember;
import com.pulumi.azurenative.sql.SyncMemberArgs;
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
        var syncMember = new SyncMember("syncMember", SyncMemberArgs.builder()        
            .databaseName("syncgroupcrud-7421")
            .databaseType("AzureSqlDatabase")
            .resourceGroupName("syncgroupcrud-65440")
            .serverName("syncgroupcrud-3379.database.windows.net")
            .syncDirection("Bidirectional")
            .syncGroupName("syncgroupcrud-3187")
            .syncMemberAzureDatabaseResourceId("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/syncgroupcrud-65440/providers/Microsoft.Sql/servers/syncgroupcrud-8475/databases/syncgroupcrud-4328")
            .syncMemberName("syncmembercrud-4879")
            .usePrivateLinkConnection(true)
            .userName("myUser")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const syncMember = new azure_native.sql.SyncMember("syncMember", {
    databaseName: "syncgroupcrud-7421",
    databaseType: "AzureSqlDatabase",
    resourceGroupName: "syncgroupcrud-65440",
    serverName: "syncgroupcrud-3379.database.windows.net",
    syncDirection: "Bidirectional",
    syncGroupName: "syncgroupcrud-3187",
    syncMemberAzureDatabaseResourceId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/syncgroupcrud-65440/providers/Microsoft.Sql/servers/syncgroupcrud-8475/databases/syncgroupcrud-4328",
    syncMemberName: "syncmembercrud-4879",
    usePrivateLinkConnection: true,
    userName: "myUser",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sync_member = azure_native.sql.SyncMember("syncMember",
    database_name="syncgroupcrud-7421",
    database_type="AzureSqlDatabase",
    resource_group_name="syncgroupcrud-65440",
    server_name="syncgroupcrud-3379.database.windows.net",
    sync_direction="Bidirectional",
    sync_group_name="syncgroupcrud-3187",
    sync_member_azure_database_resource_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/syncgroupcrud-65440/providers/Microsoft.Sql/servers/syncgroupcrud-8475/databases/syncgroupcrud-4328",
    sync_member_name="syncmembercrud-4879",
    use_private_link_connection=True,
    user_name="myUser")

```

```yaml
resources:
  syncMember:
    type: azure-native:sql:SyncMember
    properties:
      databaseName: syncgroupcrud-7421
      databaseType: AzureSqlDatabase
      resourceGroupName: syncgroupcrud-65440
      serverName: syncgroupcrud-3379.database.windows.net
      syncDirection: Bidirectional
      syncGroupName: syncgroupcrud-3187
      syncMemberAzureDatabaseResourceId: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/syncgroupcrud-65440/providers/Microsoft.Sql/servers/syncgroupcrud-8475/databases/syncgroupcrud-4328
      syncMemberName: syncmembercrud-4879
      usePrivateLinkConnection: true
      userName: myUser

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:SyncMember syncmembercrud-4879 /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/syncgroupcrud-65440/providers/Microsoft.Sql/servers/syncgroupcrud-8475/databases/syncgroupcrud-4328/syncGroups/syncgroupcrud-3187/syncMembers/syncmembercrud-4879 
```
