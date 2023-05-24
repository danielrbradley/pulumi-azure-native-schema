A group of job targets.
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a target group with all properties.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var jobTargetGroup = new AzureNative.Sql.JobTargetGroup("jobTargetGroup", new()
    {
        JobAgentName = "agent1",
        Members = new[]
        {
            new AzureNative.Sql.Inputs.JobTargetArgs
            {
                DatabaseName = "database1",
                MembershipType = AzureNative.Sql.JobTargetGroupMembershipType.Exclude,
                ServerName = "server1",
                Type = "SqlDatabase",
            },
            new AzureNative.Sql.Inputs.JobTargetArgs
            {
                MembershipType = AzureNative.Sql.JobTargetGroupMembershipType.Include,
                RefreshCredential = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/testCredential",
                ServerName = "server1",
                Type = "SqlServer",
            },
            new AzureNative.Sql.Inputs.JobTargetArgs
            {
                ElasticPoolName = "pool1",
                MembershipType = AzureNative.Sql.JobTargetGroupMembershipType.Include,
                RefreshCredential = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/testCredential",
                ServerName = "server2",
                Type = "SqlElasticPool",
            },
            new AzureNative.Sql.Inputs.JobTargetArgs
            {
                MembershipType = AzureNative.Sql.JobTargetGroupMembershipType.Include,
                RefreshCredential = "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/testCredential",
                ServerName = "server3",
                ShardMapName = "shardMap1",
                Type = "SqlShardMap",
            },
        },
        ResourceGroupName = "group1",
        ServerName = "server1",
        TargetGroupName = "targetGroup1",
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
		_, err := sql.NewJobTargetGroup(ctx, "jobTargetGroup", &sql.JobTargetGroupArgs{
			JobAgentName: pulumi.String("agent1"),
			Members: []sql.JobTargetArgs{
				{
					DatabaseName:   pulumi.String("database1"),
					MembershipType: sql.JobTargetGroupMembershipTypeExclude,
					ServerName:     pulumi.String("server1"),
					Type:           pulumi.String("SqlDatabase"),
				},
				{
					MembershipType:    sql.JobTargetGroupMembershipTypeInclude,
					RefreshCredential: pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/testCredential"),
					ServerName:        pulumi.String("server1"),
					Type:              pulumi.String("SqlServer"),
				},
				{
					ElasticPoolName:   pulumi.String("pool1"),
					MembershipType:    sql.JobTargetGroupMembershipTypeInclude,
					RefreshCredential: pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/testCredential"),
					ServerName:        pulumi.String("server2"),
					Type:              pulumi.String("SqlElasticPool"),
				},
				{
					MembershipType:    sql.JobTargetGroupMembershipTypeInclude,
					RefreshCredential: pulumi.String("/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/testCredential"),
					ServerName:        pulumi.String("server3"),
					ShardMapName:      pulumi.String("shardMap1"),
					Type:              pulumi.String("SqlShardMap"),
				},
			},
			ResourceGroupName: pulumi.String("group1"),
			ServerName:        pulumi.String("server1"),
			TargetGroupName:   pulumi.String("targetGroup1"),
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
import com.pulumi.azurenative.sql.JobTargetGroup;
import com.pulumi.azurenative.sql.JobTargetGroupArgs;
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
        var jobTargetGroup = new JobTargetGroup("jobTargetGroup", JobTargetGroupArgs.builder()        
            .jobAgentName("agent1")
            .members(            
                Map.ofEntries(
                    Map.entry("databaseName", "database1"),
                    Map.entry("membershipType", "Exclude"),
                    Map.entry("serverName", "server1"),
                    Map.entry("type", "SqlDatabase")
                ),
                Map.ofEntries(
                    Map.entry("membershipType", "Include"),
                    Map.entry("refreshCredential", "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/testCredential"),
                    Map.entry("serverName", "server1"),
                    Map.entry("type", "SqlServer")
                ),
                Map.ofEntries(
                    Map.entry("elasticPoolName", "pool1"),
                    Map.entry("membershipType", "Include"),
                    Map.entry("refreshCredential", "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/testCredential"),
                    Map.entry("serverName", "server2"),
                    Map.entry("type", "SqlElasticPool")
                ),
                Map.ofEntries(
                    Map.entry("membershipType", "Include"),
                    Map.entry("refreshCredential", "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/testCredential"),
                    Map.entry("serverName", "server3"),
                    Map.entry("shardMapName", "shardMap1"),
                    Map.entry("type", "SqlShardMap")
                ))
            .resourceGroupName("group1")
            .serverName("server1")
            .targetGroupName("targetGroup1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const jobTargetGroup = new azure_native.sql.JobTargetGroup("jobTargetGroup", {
    jobAgentName: "agent1",
    members: [
        {
            databaseName: "database1",
            membershipType: azure_native.sql.JobTargetGroupMembershipType.Exclude,
            serverName: "server1",
            type: "SqlDatabase",
        },
        {
            membershipType: azure_native.sql.JobTargetGroupMembershipType.Include,
            refreshCredential: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/testCredential",
            serverName: "server1",
            type: "SqlServer",
        },
        {
            elasticPoolName: "pool1",
            membershipType: azure_native.sql.JobTargetGroupMembershipType.Include,
            refreshCredential: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/testCredential",
            serverName: "server2",
            type: "SqlElasticPool",
        },
        {
            membershipType: azure_native.sql.JobTargetGroupMembershipType.Include,
            refreshCredential: "/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/testCredential",
            serverName: "server3",
            shardMapName: "shardMap1",
            type: "SqlShardMap",
        },
    ],
    resourceGroupName: "group1",
    serverName: "server1",
    targetGroupName: "targetGroup1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

job_target_group = azure_native.sql.JobTargetGroup("jobTargetGroup",
    job_agent_name="agent1",
    members=[
        azure_native.sql.JobTargetArgs(
            database_name="database1",
            membership_type=azure_native.sql.JobTargetGroupMembershipType.EXCLUDE,
            server_name="server1",
            type="SqlDatabase",
        ),
        azure_native.sql.JobTargetArgs(
            membership_type=azure_native.sql.JobTargetGroupMembershipType.INCLUDE,
            refresh_credential="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/testCredential",
            server_name="server1",
            type="SqlServer",
        ),
        azure_native.sql.JobTargetArgs(
            elastic_pool_name="pool1",
            membership_type=azure_native.sql.JobTargetGroupMembershipType.INCLUDE,
            refresh_credential="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/testCredential",
            server_name="server2",
            type="SqlElasticPool",
        ),
        azure_native.sql.JobTargetArgs(
            membership_type=azure_native.sql.JobTargetGroupMembershipType.INCLUDE,
            refresh_credential="/subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/testCredential",
            server_name="server3",
            shard_map_name="shardMap1",
            type="SqlShardMap",
        ),
    ],
    resource_group_name="group1",
    server_name="server1",
    target_group_name="targetGroup1")

```

```yaml
resources:
  jobTargetGroup:
    type: azure-native:sql:JobTargetGroup
    properties:
      jobAgentName: agent1
      members:
        - databaseName: database1
          membershipType: Exclude
          serverName: server1
          type: SqlDatabase
        - membershipType: Include
          refreshCredential: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/testCredential
          serverName: server1
          type: SqlServer
        - elasticPoolName: pool1
          membershipType: Include
          refreshCredential: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/testCredential
          serverName: server2
          type: SqlElasticPool
        - membershipType: Include
          refreshCredential: /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/credentials/testCredential
          serverName: server3
          shardMapName: shardMap1
          type: SqlShardMap
      resourceGroupName: group1
      serverName: server1
      targetGroupName: targetGroup1

```

{{% /example %}}
{{% example %}}
### Create or update a target group with minimal properties.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var jobTargetGroup = new AzureNative.Sql.JobTargetGroup("jobTargetGroup", new()
    {
        JobAgentName = "agent1",
        Members = new[] {},
        ResourceGroupName = "group1",
        ServerName = "server1",
        TargetGroupName = "targetGroup1",
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
		_, err := sql.NewJobTargetGroup(ctx, "jobTargetGroup", &sql.JobTargetGroupArgs{
			JobAgentName:      pulumi.String("agent1"),
			Members:           sql.JobTargetArray{},
			ResourceGroupName: pulumi.String("group1"),
			ServerName:        pulumi.String("server1"),
			TargetGroupName:   pulumi.String("targetGroup1"),
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
import com.pulumi.azurenative.sql.JobTargetGroup;
import com.pulumi.azurenative.sql.JobTargetGroupArgs;
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
        var jobTargetGroup = new JobTargetGroup("jobTargetGroup", JobTargetGroupArgs.builder()        
            .jobAgentName("agent1")
            .members()
            .resourceGroupName("group1")
            .serverName("server1")
            .targetGroupName("targetGroup1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const jobTargetGroup = new azure_native.sql.JobTargetGroup("jobTargetGroup", {
    jobAgentName: "agent1",
    members: [],
    resourceGroupName: "group1",
    serverName: "server1",
    targetGroupName: "targetGroup1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

job_target_group = azure_native.sql.JobTargetGroup("jobTargetGroup",
    job_agent_name="agent1",
    members=[],
    resource_group_name="group1",
    server_name="server1",
    target_group_name="targetGroup1")

```

```yaml
resources:
  jobTargetGroup:
    type: azure-native:sql:JobTargetGroup
    properties:
      jobAgentName: agent1
      members: []
      resourceGroupName: group1
      serverName: server1
      targetGroupName: targetGroup1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:JobTargetGroup targetGroup1 /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/group1/providers/Microsoft.Sql/servers/server1/jobAgents/agent1/targetGroups/targetGroup1 
```
