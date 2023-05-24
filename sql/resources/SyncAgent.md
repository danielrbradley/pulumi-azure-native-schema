An Azure SQL Database sync agent.
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a new sync agent
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var syncAgent = new AzureNative.Sql.SyncAgent("syncAgent", new()
    {
        ResourceGroupName = "syncagentcrud-65440",
        ServerName = "syncagentcrud-8475",
        SyncAgentName = "syncagentcrud-3187",
        SyncDatabaseId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-Onebox/providers/Microsoft.Sql/servers/syncagentcrud-8475/databases/sync",
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
		_, err := sql.NewSyncAgent(ctx, "syncAgent", &sql.SyncAgentArgs{
			ResourceGroupName: pulumi.String("syncagentcrud-65440"),
			ServerName:        pulumi.String("syncagentcrud-8475"),
			SyncAgentName:     pulumi.String("syncagentcrud-3187"),
			SyncDatabaseId:    pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-Onebox/providers/Microsoft.Sql/servers/syncagentcrud-8475/databases/sync"),
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
import com.pulumi.azurenative.sql.SyncAgent;
import com.pulumi.azurenative.sql.SyncAgentArgs;
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
        var syncAgent = new SyncAgent("syncAgent", SyncAgentArgs.builder()        
            .resourceGroupName("syncagentcrud-65440")
            .serverName("syncagentcrud-8475")
            .syncAgentName("syncagentcrud-3187")
            .syncDatabaseId("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-Onebox/providers/Microsoft.Sql/servers/syncagentcrud-8475/databases/sync")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const syncAgent = new azure_native.sql.SyncAgent("syncAgent", {
    resourceGroupName: "syncagentcrud-65440",
    serverName: "syncagentcrud-8475",
    syncAgentName: "syncagentcrud-3187",
    syncDatabaseId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-Onebox/providers/Microsoft.Sql/servers/syncagentcrud-8475/databases/sync",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sync_agent = azure_native.sql.SyncAgent("syncAgent",
    resource_group_name="syncagentcrud-65440",
    server_name="syncagentcrud-8475",
    sync_agent_name="syncagentcrud-3187",
    sync_database_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-Onebox/providers/Microsoft.Sql/servers/syncagentcrud-8475/databases/sync")

```

```yaml
resources:
  syncAgent:
    type: azure-native:sql:SyncAgent
    properties:
      resourceGroupName: syncagentcrud-65440
      serverName: syncagentcrud-8475
      syncAgentName: syncagentcrud-3187
      syncDatabaseId: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-Onebox/providers/Microsoft.Sql/servers/syncagentcrud-8475/databases/sync

```

{{% /example %}}
{{% example %}}
### Update a sync agent
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var syncAgent = new AzureNative.Sql.SyncAgent("syncAgent", new()
    {
        ResourceGroupName = "syncagentcrud-65440",
        ServerName = "syncagentcrud-8475",
        SyncAgentName = "syncagentcrud-3187",
        SyncDatabaseId = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-Onebox/providers/Microsoft.Sql/servers/syncagentcrud-8475/databases/sync",
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
		_, err := sql.NewSyncAgent(ctx, "syncAgent", &sql.SyncAgentArgs{
			ResourceGroupName: pulumi.String("syncagentcrud-65440"),
			ServerName:        pulumi.String("syncagentcrud-8475"),
			SyncAgentName:     pulumi.String("syncagentcrud-3187"),
			SyncDatabaseId:    pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-Onebox/providers/Microsoft.Sql/servers/syncagentcrud-8475/databases/sync"),
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
import com.pulumi.azurenative.sql.SyncAgent;
import com.pulumi.azurenative.sql.SyncAgentArgs;
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
        var syncAgent = new SyncAgent("syncAgent", SyncAgentArgs.builder()        
            .resourceGroupName("syncagentcrud-65440")
            .serverName("syncagentcrud-8475")
            .syncAgentName("syncagentcrud-3187")
            .syncDatabaseId("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-Onebox/providers/Microsoft.Sql/servers/syncagentcrud-8475/databases/sync")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const syncAgent = new azure_native.sql.SyncAgent("syncAgent", {
    resourceGroupName: "syncagentcrud-65440",
    serverName: "syncagentcrud-8475",
    syncAgentName: "syncagentcrud-3187",
    syncDatabaseId: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-Onebox/providers/Microsoft.Sql/servers/syncagentcrud-8475/databases/sync",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sync_agent = azure_native.sql.SyncAgent("syncAgent",
    resource_group_name="syncagentcrud-65440",
    server_name="syncagentcrud-8475",
    sync_agent_name="syncagentcrud-3187",
    sync_database_id="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-Onebox/providers/Microsoft.Sql/servers/syncagentcrud-8475/databases/sync")

```

```yaml
resources:
  syncAgent:
    type: azure-native:sql:SyncAgent
    properties:
      resourceGroupName: syncagentcrud-65440
      serverName: syncagentcrud-8475
      syncAgentName: syncagentcrud-3187
      syncDatabaseId: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-Onebox/providers/Microsoft.Sql/servers/syncagentcrud-8475/databases/sync

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:SyncAgent syncagent /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/Default-SQL-Onebox/providers/Microsoft.Sql/servers/syncagentcrud-8475/syncAgents/syncagentcrud-3187 
```
