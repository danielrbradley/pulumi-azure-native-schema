Arc Sql Server Availability Group
API Version: 2023-03-15-preview.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a Arc Sql Server availability group.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sqlServerAvailabilityGroup = new AzureNative.AzureArcData.SqlServerAvailabilityGroup("sqlServerAvailabilityGroup", new()
    {
        Location = "southeastasia",
        Properties = new AzureNative.AzureArcData.Inputs.SqlServerAvailabilityGroupResourcePropertiesArgs
        {
            AvailabilityGroupId = "00000000-1111-2222-3333-444444444444",
            AvailabilityGroupName = "testAG",
            Configure = new AzureNative.AzureArcData.Inputs.AvailabilityGroupConfigureArgs
            {
                AvailabilityModeDesc = "SYNCHRONOUS_COMMIT",
                BackupPriority = 50,
                EndpointUrl = "TCP://mytest60-0.mytest60-svc:5022",
                FailoverModeDesc = "EXTERNAL",
                PrimaryRoleAllowConnectionsDesc = "ALL",
                SecondaryRoleAllowConnectionsDesc = "ALL",
                SeedingModeDesc = "AUTOMATIC",
                SessionTimeout = 10,
            },
            State = new AzureNative.AzureArcData.Inputs.AvailabilityGroupStateArgs
            {
                AvailabilityGroupReplicaRole = "SECONDARY",
                ConnectedStateDesc = "CONNECTED",
                LastConnectErrorDescription = "",
                LastConnectErrorTimestamp = "2022-05-05T16:26:33.883Z",
                OperationalStateDesc = "ONLINE",
                RecoveryHealthDesc = "ONLINE_IN_PROGRESS",
                SynchronizationHealthDesc = "HEALTHY",
            },
        },
        ResourceGroupName = "testrg",
        SqlAvailabilityGroupName = "testAG",
        SqlServerInstanceName = "testSqlServerInstance",
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
		_, err := azurearcdata.NewSqlServerAvailabilityGroup(ctx, "sqlServerAvailabilityGroup", &azurearcdata.SqlServerAvailabilityGroupArgs{
			Location: pulumi.String("southeastasia"),
			Properties: azurearcdata.SqlServerAvailabilityGroupResourcePropertiesResponse{
				AvailabilityGroupId:   pulumi.String("00000000-1111-2222-3333-444444444444"),
				AvailabilityGroupName: pulumi.String("testAG"),
				Configure: &azurearcdata.AvailabilityGroupConfigureArgs{
					AvailabilityModeDesc:              pulumi.String("SYNCHRONOUS_COMMIT"),
					BackupPriority:                    pulumi.Int(50),
					EndpointUrl:                       pulumi.String("TCP://mytest60-0.mytest60-svc:5022"),
					FailoverModeDesc:                  pulumi.String("EXTERNAL"),
					PrimaryRoleAllowConnectionsDesc:   pulumi.String("ALL"),
					SecondaryRoleAllowConnectionsDesc: pulumi.String("ALL"),
					SeedingModeDesc:                   pulumi.String("AUTOMATIC"),
					SessionTimeout:                    pulumi.Int(10),
				},
				State: &azurearcdata.AvailabilityGroupStateArgs{
					AvailabilityGroupReplicaRole: pulumi.String("SECONDARY"),
					ConnectedStateDesc:           pulumi.String("CONNECTED"),
					LastConnectErrorDescription:  pulumi.String(""),
					LastConnectErrorTimestamp:    pulumi.String("2022-05-05T16:26:33.883Z"),
					OperationalStateDesc:         pulumi.String("ONLINE"),
					RecoveryHealthDesc:           pulumi.String("ONLINE_IN_PROGRESS"),
					SynchronizationHealthDesc:    pulumi.String("HEALTHY"),
				},
			},
			ResourceGroupName:        pulumi.String("testrg"),
			SqlAvailabilityGroupName: pulumi.String("testAG"),
			SqlServerInstanceName:    pulumi.String("testSqlServerInstance"),
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
import com.pulumi.azurenative.azurearcdata.SqlServerAvailabilityGroup;
import com.pulumi.azurenative.azurearcdata.SqlServerAvailabilityGroupArgs;
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
        var sqlServerAvailabilityGroup = new SqlServerAvailabilityGroup("sqlServerAvailabilityGroup", SqlServerAvailabilityGroupArgs.builder()        
            .location("southeastasia")
            .properties(Map.ofEntries(
                Map.entry("availabilityGroupId", "00000000-1111-2222-3333-444444444444"),
                Map.entry("availabilityGroupName", "testAG"),
                Map.entry("configure", Map.ofEntries(
                    Map.entry("availabilityModeDesc", "SYNCHRONOUS_COMMIT"),
                    Map.entry("backupPriority", 50),
                    Map.entry("endpointUrl", "TCP://mytest60-0.mytest60-svc:5022"),
                    Map.entry("failoverModeDesc", "EXTERNAL"),
                    Map.entry("primaryRoleAllowConnectionsDesc", "ALL"),
                    Map.entry("secondaryRoleAllowConnectionsDesc", "ALL"),
                    Map.entry("seedingModeDesc", "AUTOMATIC"),
                    Map.entry("sessionTimeout", 10)
                )),
                Map.entry("state", Map.ofEntries(
                    Map.entry("availabilityGroupReplicaRole", "SECONDARY"),
                    Map.entry("connectedStateDesc", "CONNECTED"),
                    Map.entry("lastConnectErrorDescription", ""),
                    Map.entry("lastConnectErrorTimestamp", "2022-05-05T16:26:33.883Z"),
                    Map.entry("operationalStateDesc", "ONLINE"),
                    Map.entry("recoveryHealthDesc", "ONLINE_IN_PROGRESS"),
                    Map.entry("synchronizationHealthDesc", "HEALTHY")
                ))
            ))
            .resourceGroupName("testrg")
            .sqlAvailabilityGroupName("testAG")
            .sqlServerInstanceName("testSqlServerInstance")
            .tags(Map.of("mytag", "myval"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sqlServerAvailabilityGroup = new azure_native.azurearcdata.SqlServerAvailabilityGroup("sqlServerAvailabilityGroup", {
    location: "southeastasia",
    properties: {
        availabilityGroupId: "00000000-1111-2222-3333-444444444444",
        availabilityGroupName: "testAG",
        configure: {
            availabilityModeDesc: "SYNCHRONOUS_COMMIT",
            backupPriority: 50,
            endpointUrl: "TCP://mytest60-0.mytest60-svc:5022",
            failoverModeDesc: "EXTERNAL",
            primaryRoleAllowConnectionsDesc: "ALL",
            secondaryRoleAllowConnectionsDesc: "ALL",
            seedingModeDesc: "AUTOMATIC",
            sessionTimeout: 10,
        },
        state: {
            availabilityGroupReplicaRole: "SECONDARY",
            connectedStateDesc: "CONNECTED",
            lastConnectErrorDescription: "",
            lastConnectErrorTimestamp: "2022-05-05T16:26:33.883Z",
            operationalStateDesc: "ONLINE",
            recoveryHealthDesc: "ONLINE_IN_PROGRESS",
            synchronizationHealthDesc: "HEALTHY",
        },
    },
    resourceGroupName: "testrg",
    sqlAvailabilityGroupName: "testAG",
    sqlServerInstanceName: "testSqlServerInstance",
    tags: {
        mytag: "myval",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sql_server_availability_group = azure_native.azurearcdata.SqlServerAvailabilityGroup("sqlServerAvailabilityGroup",
    location="southeastasia",
    properties=azure_native.azurearcdata.SqlServerAvailabilityGroupResourcePropertiesResponseArgs(
        availability_group_id="00000000-1111-2222-3333-444444444444",
        availability_group_name="testAG",
        configure=azure_native.azurearcdata.AvailabilityGroupConfigureArgs(
            availability_mode_desc="SYNCHRONOUS_COMMIT",
            backup_priority=50,
            endpoint_url="TCP://mytest60-0.mytest60-svc:5022",
            failover_mode_desc="EXTERNAL",
            primary_role_allow_connections_desc="ALL",
            secondary_role_allow_connections_desc="ALL",
            seeding_mode_desc="AUTOMATIC",
            session_timeout=10,
        ),
        state=azure_native.azurearcdata.AvailabilityGroupStateArgs(
            availability_group_replica_role="SECONDARY",
            connected_state_desc="CONNECTED",
            last_connect_error_description="",
            last_connect_error_timestamp="2022-05-05T16:26:33.883Z",
            operational_state_desc="ONLINE",
            recovery_health_desc="ONLINE_IN_PROGRESS",
            synchronization_health_desc="HEALTHY",
        ),
    ),
    resource_group_name="testrg",
    sql_availability_group_name="testAG",
    sql_server_instance_name="testSqlServerInstance",
    tags={
        "mytag": "myval",
    })

```

```yaml
resources:
  sqlServerAvailabilityGroup:
    type: azure-native:azurearcdata:SqlServerAvailabilityGroup
    properties:
      location: southeastasia
      properties:
        availabilityGroupId: 00000000-1111-2222-3333-444444444444
        availabilityGroupName: testAG
        configure:
          availabilityModeDesc: SYNCHRONOUS_COMMIT
          backupPriority: 50
          endpointUrl: TCP://mytest60-0.mytest60-svc:5022
          failoverModeDesc: EXTERNAL
          primaryRoleAllowConnectionsDesc: ALL
          secondaryRoleAllowConnectionsDesc: ALL
          seedingModeDesc: AUTOMATIC
          sessionTimeout: 10
        state:
          availabilityGroupReplicaRole: SECONDARY
          connectedStateDesc: CONNECTED
          lastConnectErrorDescription:
          lastConnectErrorTimestamp: 2022-05-05T16:26:33.883Z
          operationalStateDesc: ONLINE
          recoveryHealthDesc: ONLINE_IN_PROGRESS
          synchronizationHealthDesc: HEALTHY
      resourceGroupName: testrg
      sqlAvailabilityGroupName: testAG
      sqlServerInstanceName: testSqlServerInstance
      tags:
        mytag: myval

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:azurearcdata:SqlServerAvailabilityGroup testAG /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.AzureArcData/sqlServerInstances/testSqlServerInstance/sqlAvailabilityGroups/testAG 
```
