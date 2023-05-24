Arc Sql Server Availability Group Database
API Version: 2023-03-15-preview.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a Arc availability group database.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sqlAvailabilityGroupDatabase = new AzureNative.AzureArcData.SqlAvailabilityGroupDatabase("sqlAvailabilityGroupDatabase", new()
    {
        Location = "southeastasia",
        Properties = new AzureNative.AzureArcData.Inputs.SqlAvailabilityGroupMultiDatabaseReplicaResourcePropertiesArgs
        {
            GroupDatabaseId = "00000000-1111-2222-3333-444444444444",
            Value = new[]
            {
                new AzureNative.AzureArcData.Inputs.SqlAvailabilityGroupDatabaseReplicaResourcePropertiesArgs
                {
                    DatabaseStateDesc = "ONLINE",
                    IsCommitParticipant = true,
                    IsLocal = true,
                    IsPrimaryReplica = true,
                    IsSuspended = false,
                    ReplicaName = "sqlServer1",
                    SynchronizationHealthDesc = "HEALTHY",
                    SynchronizationStateDesc = "SYNCHRONIZED",
                },
                new AzureNative.AzureArcData.Inputs.SqlAvailabilityGroupDatabaseReplicaResourcePropertiesArgs
                {
                    DatabaseStateDesc = "ONLINE",
                    IsCommitParticipant = true,
                    IsLocal = false,
                    IsPrimaryReplica = false,
                    IsSuspended = false,
                    ReplicaName = "sqlServer2",
                    SynchronizationHealthDesc = "HEALTHY",
                    SynchronizationStateDesc = "SYNCHRONIZED",
                },
            },
        },
        ResourceGroupName = "testrg",
        SqlAvailabilityGroupDatabaseName = "testSqlDatabase",
        SqlAvailabilityGroupName = "testAG",
        Tags = 
        {
            { "mytag", "myval" },
        },
    });

});


```

```go
package main

import (
	azurearcdata "github.com/pulumi/pulumi-azure-native-sdk/azurearcdata"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := azurearcdata.NewSqlAvailabilityGroupDatabase(ctx, "sqlAvailabilityGroupDatabase", &azurearcdata.SqlAvailabilityGroupDatabaseArgs{
			Location: pulumi.String("southeastasia"),
			Properties: azurearcdata.SqlAvailabilityGroupMultiDatabaseReplicaResourcePropertiesResponse{
				GroupDatabaseId: pulumi.String("00000000-1111-2222-3333-444444444444"),
				Value: azurearcdata.SqlAvailabilityGroupDatabaseReplicaResourcePropertiesArray{
					&azurearcdata.SqlAvailabilityGroupDatabaseReplicaResourcePropertiesArgs{
						DatabaseStateDesc:         pulumi.String("ONLINE"),
						IsCommitParticipant:       pulumi.Bool(true),
						IsLocal:                   pulumi.Bool(true),
						IsPrimaryReplica:          pulumi.Bool(true),
						IsSuspended:               pulumi.Bool(false),
						ReplicaName:               pulumi.String("sqlServer1"),
						SynchronizationHealthDesc: pulumi.String("HEALTHY"),
						SynchronizationStateDesc:  pulumi.String("SYNCHRONIZED"),
					},
					&azurearcdata.SqlAvailabilityGroupDatabaseReplicaResourcePropertiesArgs{
						DatabaseStateDesc:         pulumi.String("ONLINE"),
						IsCommitParticipant:       pulumi.Bool(true),
						IsLocal:                   pulumi.Bool(false),
						IsPrimaryReplica:          pulumi.Bool(false),
						IsSuspended:               pulumi.Bool(false),
						ReplicaName:               pulumi.String("sqlServer2"),
						SynchronizationHealthDesc: pulumi.String("HEALTHY"),
						SynchronizationStateDesc:  pulumi.String("SYNCHRONIZED"),
					},
				},
			},
			ResourceGroupName:                pulumi.String("testrg"),
			SqlAvailabilityGroupDatabaseName: pulumi.String("testSqlDatabase"),
			SqlAvailabilityGroupName:         pulumi.String("testAG"),
			Tags: pulumi.StringMap{
				"mytag": pulumi.String("myval"),
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
import com.pulumi.azurenative.azurearcdata.SqlAvailabilityGroupDatabase;
import com.pulumi.azurenative.azurearcdata.SqlAvailabilityGroupDatabaseArgs;
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
        var sqlAvailabilityGroupDatabase = new SqlAvailabilityGroupDatabase("sqlAvailabilityGroupDatabase", SqlAvailabilityGroupDatabaseArgs.builder()        
            .location("southeastasia")
            .properties(Map.ofEntries(
                Map.entry("groupDatabaseId", "00000000-1111-2222-3333-444444444444"),
                Map.entry("value",                 
                    Map.ofEntries(
                        Map.entry("databaseStateDesc", "ONLINE"),
                        Map.entry("isCommitParticipant", true),
                        Map.entry("isLocal", true),
                        Map.entry("isPrimaryReplica", true),
                        Map.entry("isSuspended", false),
                        Map.entry("replicaName", "sqlServer1"),
                        Map.entry("synchronizationHealthDesc", "HEALTHY"),
                        Map.entry("synchronizationStateDesc", "SYNCHRONIZED")
                    ),
                    Map.ofEntries(
                        Map.entry("databaseStateDesc", "ONLINE"),
                        Map.entry("isCommitParticipant", true),
                        Map.entry("isLocal", false),
                        Map.entry("isPrimaryReplica", false),
                        Map.entry("isSuspended", false),
                        Map.entry("replicaName", "sqlServer2"),
                        Map.entry("synchronizationHealthDesc", "HEALTHY"),
                        Map.entry("synchronizationStateDesc", "SYNCHRONIZED")
                    ))
            ))
            .resourceGroupName("testrg")
            .sqlAvailabilityGroupDatabaseName("testSqlDatabase")
            .sqlAvailabilityGroupName("testAG")
            .tags(Map.of("mytag", "myval"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sqlAvailabilityGroupDatabase = new azure_native.azurearcdata.SqlAvailabilityGroupDatabase("sqlAvailabilityGroupDatabase", {
    location: "southeastasia",
    properties: {
        groupDatabaseId: "00000000-1111-2222-3333-444444444444",
        value: [
            {
                databaseStateDesc: "ONLINE",
                isCommitParticipant: true,
                isLocal: true,
                isPrimaryReplica: true,
                isSuspended: false,
                replicaName: "sqlServer1",
                synchronizationHealthDesc: "HEALTHY",
                synchronizationStateDesc: "SYNCHRONIZED",
            },
            {
                databaseStateDesc: "ONLINE",
                isCommitParticipant: true,
                isLocal: false,
                isPrimaryReplica: false,
                isSuspended: false,
                replicaName: "sqlServer2",
                synchronizationHealthDesc: "HEALTHY",
                synchronizationStateDesc: "SYNCHRONIZED",
            },
        ],
    },
    resourceGroupName: "testrg",
    sqlAvailabilityGroupDatabaseName: "testSqlDatabase",
    sqlAvailabilityGroupName: "testAG",
    tags: {
        mytag: "myval",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sql_availability_group_database = azure_native.azurearcdata.SqlAvailabilityGroupDatabase("sqlAvailabilityGroupDatabase",
    location="southeastasia",
    properties=azure_native.azurearcdata.SqlAvailabilityGroupMultiDatabaseReplicaResourcePropertiesResponseArgs(
        group_database_id="00000000-1111-2222-3333-444444444444",
        value=[
            azure_native.azurearcdata.SqlAvailabilityGroupDatabaseReplicaResourcePropertiesArgs(
                database_state_desc="ONLINE",
                is_commit_participant=True,
                is_local=True,
                is_primary_replica=True,
                is_suspended=False,
                replica_name="sqlServer1",
                synchronization_health_desc="HEALTHY",
                synchronization_state_desc="SYNCHRONIZED",
            ),
            azure_native.azurearcdata.SqlAvailabilityGroupDatabaseReplicaResourcePropertiesArgs(
                database_state_desc="ONLINE",
                is_commit_participant=True,
                is_local=False,
                is_primary_replica=False,
                is_suspended=False,
                replica_name="sqlServer2",
                synchronization_health_desc="HEALTHY",
                synchronization_state_desc="SYNCHRONIZED",
            ),
        ],
    ),
    resource_group_name="testrg",
    sql_availability_group_database_name="testSqlDatabase",
    sql_availability_group_name="testAG",
    tags={
        "mytag": "myval",
    })

```

```yaml
resources:
  sqlAvailabilityGroupDatabase:
    type: azure-native:azurearcdata:SqlAvailabilityGroupDatabase
    properties:
      location: southeastasia
      properties:
        groupDatabaseId: 00000000-1111-2222-3333-444444444444
        value:
          - databaseStateDesc: ONLINE
            isCommitParticipant: true
            isLocal: true
            isPrimaryReplica: true
            isSuspended: false
            replicaName: sqlServer1
            synchronizationHealthDesc: HEALTHY
            synchronizationStateDesc: SYNCHRONIZED
          - databaseStateDesc: ONLINE
            isCommitParticipant: true
            isLocal: false
            isPrimaryReplica: false
            isSuspended: false
            replicaName: sqlServer2
            synchronizationHealthDesc: HEALTHY
            synchronizationStateDesc: SYNCHRONIZED
      resourceGroupName: testrg
      sqlAvailabilityGroupDatabaseName: testSqlDatabase
      sqlAvailabilityGroupName: testAG
      tags:
        mytag: myval

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:azurearcdata:SqlAvailabilityGroupDatabase testSqlDatabase /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.AzureArcData/sqlAvailabilityGroups/testsAG/databases/testSqlDatabase 
```
