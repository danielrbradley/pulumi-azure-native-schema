Represents a server.
API Version: 2021-05-01.
Previous API Version: 2017-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a new server
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var server = new AzureNative.DBforMySQL.Server("server", new()
    {
        AdministratorLogin = "cloudsa",
        AdministratorLoginPassword = "your_password",
        AvailabilityZone = "1",
        Backup = new AzureNative.DBforMySQL.Inputs.BackupArgs
        {
            BackupRetentionDays = 7,
            GeoRedundantBackup = "Disabled",
        },
        CreateMode = "Default",
        HighAvailability = new AzureNative.DBforMySQL.Inputs.HighAvailabilityArgs
        {
            Mode = "ZoneRedundant",
            StandbyAvailabilityZone = "3",
        },
        Location = "southeastasia",
        ResourceGroupName = "testrg",
        ServerName = "mysqltestserver",
        Sku = new AzureNative.DBforMySQL.Inputs.SkuArgs
        {
            Name = "Standard_D2ds_v4",
            Tier = "GeneralPurpose",
        },
        Storage = new AzureNative.DBforMySQL.Inputs.StorageArgs
        {
            AutoGrow = "Disabled",
            Iops = 600,
            StorageSizeGB = 100,
        },
        Tags = 
        {
            { "num", "1" },
        },
        Version = "5.7",
    });

});


```

```go
package main

import (
	dbformysql "github.com/pulumi/pulumi-azure-native-sdk/dbformysql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := dbformysql.NewServer(ctx, "server", &dbformysql.ServerArgs{
			AdministratorLogin:         pulumi.String("cloudsa"),
			AdministratorLoginPassword: pulumi.String("your_password"),
			AvailabilityZone:           pulumi.String("1"),
			Backup: &dbformysql.BackupArgs{
				BackupRetentionDays: pulumi.Int(7),
				GeoRedundantBackup:  pulumi.String("Disabled"),
			},
			CreateMode: pulumi.String("Default"),
			HighAvailability: &dbformysql.HighAvailabilityArgs{
				Mode:                    pulumi.String("ZoneRedundant"),
				StandbyAvailabilityZone: pulumi.String("3"),
			},
			Location:          pulumi.String("southeastasia"),
			ResourceGroupName: pulumi.String("testrg"),
			ServerName:        pulumi.String("mysqltestserver"),
			Sku: &dbformysql.SkuArgs{
				Name: pulumi.String("Standard_D2ds_v4"),
				Tier: pulumi.String("GeneralPurpose"),
			},
			Storage: &dbformysql.StorageArgs{
				AutoGrow:      pulumi.String("Disabled"),
				Iops:          pulumi.Int(600),
				StorageSizeGB: pulumi.Int(100),
			},
			Tags: pulumi.StringMap{
				"num": pulumi.String("1"),
			},
			Version: pulumi.String("5.7"),
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
import com.pulumi.azurenative.dbformysql.Server;
import com.pulumi.azurenative.dbformysql.ServerArgs;
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
        var server = new Server("server", ServerArgs.builder()        
            .administratorLogin("cloudsa")
            .administratorLoginPassword("your_password")
            .availabilityZone("1")
            .backup(Map.ofEntries(
                Map.entry("backupRetentionDays", 7),
                Map.entry("geoRedundantBackup", "Disabled")
            ))
            .createMode("Default")
            .highAvailability(Map.ofEntries(
                Map.entry("mode", "ZoneRedundant"),
                Map.entry("standbyAvailabilityZone", "3")
            ))
            .location("southeastasia")
            .resourceGroupName("testrg")
            .serverName("mysqltestserver")
            .sku(Map.ofEntries(
                Map.entry("name", "Standard_D2ds_v4"),
                Map.entry("tier", "GeneralPurpose")
            ))
            .storage(Map.ofEntries(
                Map.entry("autoGrow", "Disabled"),
                Map.entry("iops", 600),
                Map.entry("storageSizeGB", 100)
            ))
            .tags(Map.of("num", "1"))
            .version("5.7")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const server = new azure_native.dbformysql.Server("server", {
    administratorLogin: "cloudsa",
    administratorLoginPassword: "your_password",
    availabilityZone: "1",
    backup: {
        backupRetentionDays: 7,
        geoRedundantBackup: "Disabled",
    },
    createMode: "Default",
    highAvailability: {
        mode: "ZoneRedundant",
        standbyAvailabilityZone: "3",
    },
    location: "southeastasia",
    resourceGroupName: "testrg",
    serverName: "mysqltestserver",
    sku: {
        name: "Standard_D2ds_v4",
        tier: "GeneralPurpose",
    },
    storage: {
        autoGrow: "Disabled",
        iops: 600,
        storageSizeGB: 100,
    },
    tags: {
        num: "1",
    },
    version: "5.7",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

server = azure_native.dbformysql.Server("server",
    administrator_login="cloudsa",
    administrator_login_password="your_password",
    availability_zone="1",
    backup=azure_native.dbformysql.BackupArgs(
        backup_retention_days=7,
        geo_redundant_backup="Disabled",
    ),
    create_mode="Default",
    high_availability=azure_native.dbformysql.HighAvailabilityArgs(
        mode="ZoneRedundant",
        standby_availability_zone="3",
    ),
    location="southeastasia",
    resource_group_name="testrg",
    server_name="mysqltestserver",
    sku=azure_native.dbformysql.SkuArgs(
        name="Standard_D2ds_v4",
        tier="GeneralPurpose",
    ),
    storage=azure_native.dbformysql.StorageArgs(
        auto_grow="Disabled",
        iops=600,
        storage_size_gb=100,
    ),
    tags={
        "num": "1",
    },
    version="5.7")

```

```yaml
resources:
  server:
    type: azure-native:dbformysql:Server
    properties:
      administratorLogin: cloudsa
      administratorLoginPassword: your_password
      availabilityZone: '1'
      backup:
        backupRetentionDays: 7
        geoRedundantBackup: Disabled
      createMode: Default
      highAvailability:
        mode: ZoneRedundant
        standbyAvailabilityZone: '3'
      location: southeastasia
      resourceGroupName: testrg
      serverName: mysqltestserver
      sku:
        name: Standard_D2ds_v4
        tier: GeneralPurpose
      storage:
        autoGrow: Disabled
        iops: 600
        storageSizeGB: 100
      tags:
        num: '1'
      version: '5.7'

```

{{% /example %}}
{{% example %}}
### Create a replica server
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var server = new AzureNative.DBforMySQL.Server("server", new()
    {
        CreateMode = "Replica",
        Location = "SoutheastAsia",
        ResourceGroupName = "testgr",
        ServerName = "replica-server",
        SourceServerResourceId = "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testgr/providers/Microsoft.DBforMySQL/flexibleServers/source-server",
    });

});


```

```go
package main

import (
	dbformysql "github.com/pulumi/pulumi-azure-native-sdk/dbformysql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := dbformysql.NewServer(ctx, "server", &dbformysql.ServerArgs{
			CreateMode:             pulumi.String("Replica"),
			Location:               pulumi.String("SoutheastAsia"),
			ResourceGroupName:      pulumi.String("testgr"),
			ServerName:             pulumi.String("replica-server"),
			SourceServerResourceId: pulumi.String("/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testgr/providers/Microsoft.DBforMySQL/flexibleServers/source-server"),
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
import com.pulumi.azurenative.dbformysql.Server;
import com.pulumi.azurenative.dbformysql.ServerArgs;
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
        var server = new Server("server", ServerArgs.builder()        
            .createMode("Replica")
            .location("SoutheastAsia")
            .resourceGroupName("testgr")
            .serverName("replica-server")
            .sourceServerResourceId("/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testgr/providers/Microsoft.DBforMySQL/flexibleServers/source-server")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const server = new azure_native.dbformysql.Server("server", {
    createMode: "Replica",
    location: "SoutheastAsia",
    resourceGroupName: "testgr",
    serverName: "replica-server",
    sourceServerResourceId: "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testgr/providers/Microsoft.DBforMySQL/flexibleServers/source-server",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

server = azure_native.dbformysql.Server("server",
    create_mode="Replica",
    location="SoutheastAsia",
    resource_group_name="testgr",
    server_name="replica-server",
    source_server_resource_id="/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testgr/providers/Microsoft.DBforMySQL/flexibleServers/source-server")

```

```yaml
resources:
  server:
    type: azure-native:dbformysql:Server
    properties:
      createMode: Replica
      location: SoutheastAsia
      resourceGroupName: testgr
      serverName: replica-server
      sourceServerResourceId: /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testgr/providers/Microsoft.DBforMySQL/flexibleServers/source-server

```

{{% /example %}}
{{% example %}}
### Create a server as a point in time restore
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var server = new AzureNative.DBforMySQL.Server("server", new()
    {
        CreateMode = "PointInTimeRestore",
        Location = "SoutheastAsia",
        ResourceGroupName = "TargetResourceGroup",
        RestorePointInTime = "2021-06-24T00:00:37.467Z",
        ServerName = "targetserver",
        Sku = new AzureNative.DBforMySQL.Inputs.SkuArgs
        {
            Name = "Standard_D14_v2",
            Tier = "GeneralPurpose",
        },
        SourceServerResourceId = "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/SourceResourceGroup/providers/Microsoft.DBforMySQL/flexibleServers/sourceserver",
        Tags = 
        {
            { "num", "1" },
        },
    });

});


```

```go
package main

import (
	dbformysql "github.com/pulumi/pulumi-azure-native-sdk/dbformysql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := dbformysql.NewServer(ctx, "server", &dbformysql.ServerArgs{
			CreateMode:         pulumi.String("PointInTimeRestore"),
			Location:           pulumi.String("SoutheastAsia"),
			ResourceGroupName:  pulumi.String("TargetResourceGroup"),
			RestorePointInTime: pulumi.String("2021-06-24T00:00:37.467Z"),
			ServerName:         pulumi.String("targetserver"),
			Sku: &dbformysql.SkuArgs{
				Name: pulumi.String("Standard_D14_v2"),
				Tier: pulumi.String("GeneralPurpose"),
			},
			SourceServerResourceId: pulumi.String("/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/SourceResourceGroup/providers/Microsoft.DBforMySQL/flexibleServers/sourceserver"),
			Tags: pulumi.StringMap{
				"num": pulumi.String("1"),
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
import com.pulumi.azurenative.dbformysql.Server;
import com.pulumi.azurenative.dbformysql.ServerArgs;
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
        var server = new Server("server", ServerArgs.builder()        
            .createMode("PointInTimeRestore")
            .location("SoutheastAsia")
            .resourceGroupName("TargetResourceGroup")
            .restorePointInTime("2021-06-24T00:00:37.467Z")
            .serverName("targetserver")
            .sku(Map.ofEntries(
                Map.entry("name", "Standard_D14_v2"),
                Map.entry("tier", "GeneralPurpose")
            ))
            .sourceServerResourceId("/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/SourceResourceGroup/providers/Microsoft.DBforMySQL/flexibleServers/sourceserver")
            .tags(Map.of("num", "1"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const server = new azure_native.dbformysql.Server("server", {
    createMode: "PointInTimeRestore",
    location: "SoutheastAsia",
    resourceGroupName: "TargetResourceGroup",
    restorePointInTime: "2021-06-24T00:00:37.467Z",
    serverName: "targetserver",
    sku: {
        name: "Standard_D14_v2",
        tier: "GeneralPurpose",
    },
    sourceServerResourceId: "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/SourceResourceGroup/providers/Microsoft.DBforMySQL/flexibleServers/sourceserver",
    tags: {
        num: "1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

server = azure_native.dbformysql.Server("server",
    create_mode="PointInTimeRestore",
    location="SoutheastAsia",
    resource_group_name="TargetResourceGroup",
    restore_point_in_time="2021-06-24T00:00:37.467Z",
    server_name="targetserver",
    sku=azure_native.dbformysql.SkuArgs(
        name="Standard_D14_v2",
        tier="GeneralPurpose",
    ),
    source_server_resource_id="/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/SourceResourceGroup/providers/Microsoft.DBforMySQL/flexibleServers/sourceserver",
    tags={
        "num": "1",
    })

```

```yaml
resources:
  server:
    type: azure-native:dbformysql:Server
    properties:
      createMode: PointInTimeRestore
      location: SoutheastAsia
      resourceGroupName: TargetResourceGroup
      restorePointInTime: 2021-06-24T00:00:37.467Z
      serverName: targetserver
      sku:
        name: Standard_D14_v2
        tier: GeneralPurpose
      sourceServerResourceId: /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/SourceResourceGroup/providers/Microsoft.DBforMySQL/flexibleServers/sourceserver
      tags:
        num: '1'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:dbformysql:Server mysqltestserver /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.DBforMySQL/flexibleServers/mysqltestserver 
```
