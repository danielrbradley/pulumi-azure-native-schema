Arc Sql Server database
API Version: 2023-03-15-preview.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a Arc Sql Server database.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sqlServerDatabase = new AzureNative.AzureArcData.SqlServerDatabase("sqlServerDatabase", new()
    {
        DatabaseName = "testdb",
        Location = "southeastasia",
        Properties = new AzureNative.AzureArcData.Inputs.SqlServerDatabaseResourcePropertiesArgs
        {
            BackupInformation = new AzureNative.AzureArcData.Inputs.SqlServerDatabaseResourcePropertiesBackupInformationArgs
            {
                LastFullBackup = "2022-05-05T16:26:33.883Z",
                LastLogBackup = "2022-05-10T16:26:33.883Z",
            },
            CollationName = "SQL_Latin1_General_CP1_CI_AS",
            CompatibilityLevel = 150,
            DatabaseCreationDate = "2022-04-05T16:26:33.883Z",
            DatabaseOptions = new AzureNative.AzureArcData.Inputs.SqlServerDatabaseResourcePropertiesDatabaseOptionsArgs
            {
                IsAutoCloseOn = true,
                IsAutoCreateStatsOn = true,
                IsAutoShrinkOn = true,
                IsAutoUpdateStatsOn = true,
                IsEncrypted = true,
                IsMemoryOptimizationEnabled = true,
                IsRemoteDataArchiveEnabled = true,
                IsTrustworthyOn = true,
            },
            IsReadOnly = true,
            RecoveryMode = "Full",
            SizeMB = 150,
            SpaceAvailableMB = 100,
            State = "Online",
        },
        ResourceGroupName = "testrg",
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
		_, err := azurearcdata.NewSqlServerDatabase(ctx, "sqlServerDatabase", &azurearcdata.SqlServerDatabaseArgs{
			DatabaseName: pulumi.String("testdb"),
			Location:     pulumi.String("southeastasia"),
			Properties: azurearcdata.SqlServerDatabaseResourcePropertiesResponse{
				BackupInformation: &azurearcdata.SqlServerDatabaseResourcePropertiesBackupInformationArgs{
					LastFullBackup: pulumi.String("2022-05-05T16:26:33.883Z"),
					LastLogBackup:  pulumi.String("2022-05-10T16:26:33.883Z"),
				},
				CollationName:        pulumi.String("SQL_Latin1_General_CP1_CI_AS"),
				CompatibilityLevel:   pulumi.Int(150),
				DatabaseCreationDate: pulumi.String("2022-04-05T16:26:33.883Z"),
				DatabaseOptions: &azurearcdata.SqlServerDatabaseResourcePropertiesDatabaseOptionsArgs{
					IsAutoCloseOn:               pulumi.Bool(true),
					IsAutoCreateStatsOn:         pulumi.Bool(true),
					IsAutoShrinkOn:              pulumi.Bool(true),
					IsAutoUpdateStatsOn:         pulumi.Bool(true),
					IsEncrypted:                 pulumi.Bool(true),
					IsMemoryOptimizationEnabled: pulumi.Bool(true),
					IsRemoteDataArchiveEnabled:  pulumi.Bool(true),
					IsTrustworthyOn:             pulumi.Bool(true),
				},
				IsReadOnly:       pulumi.Bool(true),
				RecoveryMode:     pulumi.String("Full"),
				SizeMB:           pulumi.Float64(150),
				SpaceAvailableMB: pulumi.Float64(100),
				State:            pulumi.String("Online"),
			},
			ResourceGroupName:     pulumi.String("testrg"),
			SqlServerInstanceName: pulumi.String("testSqlServerInstance"),
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
import com.pulumi.azurenative.azurearcdata.SqlServerDatabase;
import com.pulumi.azurenative.azurearcdata.SqlServerDatabaseArgs;
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
        var sqlServerDatabase = new SqlServerDatabase("sqlServerDatabase", SqlServerDatabaseArgs.builder()        
            .databaseName("testdb")
            .location("southeastasia")
            .properties(Map.ofEntries(
                Map.entry("backupInformation", Map.ofEntries(
                    Map.entry("lastFullBackup", "2022-05-05T16:26:33.883Z"),
                    Map.entry("lastLogBackup", "2022-05-10T16:26:33.883Z")
                )),
                Map.entry("collationName", "SQL_Latin1_General_CP1_CI_AS"),
                Map.entry("compatibilityLevel", 150),
                Map.entry("databaseCreationDate", "2022-04-05T16:26:33.883Z"),
                Map.entry("databaseOptions", Map.ofEntries(
                    Map.entry("isAutoCloseOn", true),
                    Map.entry("isAutoCreateStatsOn", true),
                    Map.entry("isAutoShrinkOn", true),
                    Map.entry("isAutoUpdateStatsOn", true),
                    Map.entry("isEncrypted", true),
                    Map.entry("isMemoryOptimizationEnabled", true),
                    Map.entry("isRemoteDataArchiveEnabled", true),
                    Map.entry("isTrustworthyOn", true)
                )),
                Map.entry("isReadOnly", true),
                Map.entry("recoveryMode", "Full"),
                Map.entry("sizeMB", 150),
                Map.entry("spaceAvailableMB", 100),
                Map.entry("state", "Online")
            ))
            .resourceGroupName("testrg")
            .sqlServerInstanceName("testSqlServerInstance")
            .tags(Map.of("mytag", "myval"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sqlServerDatabase = new azure_native.azurearcdata.SqlServerDatabase("sqlServerDatabase", {
    databaseName: "testdb",
    location: "southeastasia",
    properties: {
        backupInformation: {
            lastFullBackup: "2022-05-05T16:26:33.883Z",
            lastLogBackup: "2022-05-10T16:26:33.883Z",
        },
        collationName: "SQL_Latin1_General_CP1_CI_AS",
        compatibilityLevel: 150,
        databaseCreationDate: "2022-04-05T16:26:33.883Z",
        databaseOptions: {
            isAutoCloseOn: true,
            isAutoCreateStatsOn: true,
            isAutoShrinkOn: true,
            isAutoUpdateStatsOn: true,
            isEncrypted: true,
            isMemoryOptimizationEnabled: true,
            isRemoteDataArchiveEnabled: true,
            isTrustworthyOn: true,
        },
        isReadOnly: true,
        recoveryMode: "Full",
        sizeMB: 150,
        spaceAvailableMB: 100,
        state: "Online",
    },
    resourceGroupName: "testrg",
    sqlServerInstanceName: "testSqlServerInstance",
    tags: {
        mytag: "myval",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sql_server_database = azure_native.azurearcdata.SqlServerDatabase("sqlServerDatabase",
    database_name="testdb",
    location="southeastasia",
    properties=azure_native.azurearcdata.SqlServerDatabaseResourcePropertiesResponseArgs(
        backup_information=azure_native.azurearcdata.SqlServerDatabaseResourcePropertiesBackupInformationArgs(
            last_full_backup="2022-05-05T16:26:33.883Z",
            last_log_backup="2022-05-10T16:26:33.883Z",
        ),
        collation_name="SQL_Latin1_General_CP1_CI_AS",
        compatibility_level=150,
        database_creation_date="2022-04-05T16:26:33.883Z",
        database_options=azure_native.azurearcdata.SqlServerDatabaseResourcePropertiesDatabaseOptionsArgs(
            is_auto_close_on=True,
            is_auto_create_stats_on=True,
            is_auto_shrink_on=True,
            is_auto_update_stats_on=True,
            is_encrypted=True,
            is_memory_optimization_enabled=True,
            is_remote_data_archive_enabled=True,
            is_trustworthy_on=True,
        ),
        is_read_only=True,
        recovery_mode="Full",
        size_mb=150,
        space_available_mb=100,
        state="Online",
    ),
    resource_group_name="testrg",
    sql_server_instance_name="testSqlServerInstance",
    tags={
        "mytag": "myval",
    })

```

```yaml
resources:
  sqlServerDatabase:
    type: azure-native:azurearcdata:SqlServerDatabase
    properties:
      databaseName: testdb
      location: southeastasia
      properties:
        backupInformation:
          lastFullBackup: 2022-05-05T16:26:33.883Z
          lastLogBackup: 2022-05-10T16:26:33.883Z
        collationName: SQL_Latin1_General_CP1_CI_AS
        compatibilityLevel: 150
        databaseCreationDate: 2022-04-05T16:26:33.883Z
        databaseOptions:
          isAutoCloseOn: true
          isAutoCreateStatsOn: true
          isAutoShrinkOn: true
          isAutoUpdateStatsOn: true
          isEncrypted: true
          isMemoryOptimizationEnabled: true
          isRemoteDataArchiveEnabled: true
          isTrustworthyOn: true
        isReadOnly: true
        recoveryMode: Full
        sizeMB: 150
        spaceAvailableMB: 100
        state: Online
      resourceGroupName: testrg
      sqlServerInstanceName: testSqlServerInstance
      tags:
        mytag: myval

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:azurearcdata:SqlServerDatabase testdb /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/testrg/providers/Microsoft.AzureArcData/testSqlServerInstance/testsqlManagedInstance/databases/testdb 
```
