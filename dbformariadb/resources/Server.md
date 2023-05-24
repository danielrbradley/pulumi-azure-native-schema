Represents a server.
API Version: 2018-06-01.
Previous API Version: 2018-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a database as a point in time restore
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var server = new AzureNative.DBforMariaDB.Server("server", new()
    {
        Location = "brazilsouth",
        Properties = new AzureNative.DBforMariaDB.Inputs.ServerPropertiesForRestoreArgs
        {
            CreateMode = "PointInTimeRestore",
            RestorePointInTime = "2017-12-14T00:00:37.467Z",
            SourceServerId = "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/SourceResourceGroup/providers/Microsoft.DBforMariaDB/servers/sourceserver",
        },
        ResourceGroupName = "TargetResourceGroup",
        ServerName = "targetserver",
        Sku = new AzureNative.DBforMariaDB.Inputs.SkuArgs
        {
            Capacity = 2,
            Family = "Gen5",
            Name = "GP_Gen5_2",
            Tier = "GeneralPurpose",
        },
        Tags = 
        {
            { "ElasticServer", "1" },
        },
    });

});


```

```go
package main

import (
	dbformariadb "github.com/pulumi/pulumi-azure-native-sdk/dbformariadb"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := dbformariadb.NewServer(ctx, "server", &dbformariadb.ServerArgs{
			Location: pulumi.String("brazilsouth"),
			Properties: dbformariadb.ServerPropertiesForRestore{
				CreateMode:         "PointInTimeRestore",
				RestorePointInTime: "2017-12-14T00:00:37.467Z",
				SourceServerId:     "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/SourceResourceGroup/providers/Microsoft.DBforMariaDB/servers/sourceserver",
			},
			ResourceGroupName: pulumi.String("TargetResourceGroup"),
			ServerName:        pulumi.String("targetserver"),
			Sku: &dbformariadb.SkuArgs{
				Capacity: pulumi.Int(2),
				Family:   pulumi.String("Gen5"),
				Name:     pulumi.String("GP_Gen5_2"),
				Tier:     pulumi.String("GeneralPurpose"),
			},
			Tags: pulumi.StringMap{
				"ElasticServer": pulumi.String("1"),
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
import com.pulumi.azurenative.dbformariadb.Server;
import com.pulumi.azurenative.dbformariadb.ServerArgs;
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
            .location("brazilsouth")
            .properties(Map.ofEntries(
                Map.entry("createMode", "PointInTimeRestore"),
                Map.entry("restorePointInTime", "2017-12-14T00:00:37.467Z"),
                Map.entry("sourceServerId", "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/SourceResourceGroup/providers/Microsoft.DBforMariaDB/servers/sourceserver")
            ))
            .resourceGroupName("TargetResourceGroup")
            .serverName("targetserver")
            .sku(Map.ofEntries(
                Map.entry("capacity", 2),
                Map.entry("family", "Gen5"),
                Map.entry("name", "GP_Gen5_2"),
                Map.entry("tier", "GeneralPurpose")
            ))
            .tags(Map.of("ElasticServer", "1"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const server = new azure_native.dbformariadb.Server("server", {
    location: "brazilsouth",
    properties: {
        createMode: "PointInTimeRestore",
        restorePointInTime: "2017-12-14T00:00:37.467Z",
        sourceServerId: "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/SourceResourceGroup/providers/Microsoft.DBforMariaDB/servers/sourceserver",
    },
    resourceGroupName: "TargetResourceGroup",
    serverName: "targetserver",
    sku: {
        capacity: 2,
        family: "Gen5",
        name: "GP_Gen5_2",
        tier: "GeneralPurpose",
    },
    tags: {
        ElasticServer: "1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

server = azure_native.dbformariadb.Server("server",
    location="brazilsouth",
    properties=azure_native.dbformariadb.ServerPropertiesForRestoreArgs(
        create_mode="PointInTimeRestore",
        restore_point_in_time="2017-12-14T00:00:37.467Z",
        source_server_id="/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/SourceResourceGroup/providers/Microsoft.DBforMariaDB/servers/sourceserver",
    ),
    resource_group_name="TargetResourceGroup",
    server_name="targetserver",
    sku=azure_native.dbformariadb.SkuArgs(
        capacity=2,
        family="Gen5",
        name="GP_Gen5_2",
        tier="GeneralPurpose",
    ),
    tags={
        "ElasticServer": "1",
    })

```

```yaml
resources:
  server:
    type: azure-native:dbformariadb:Server
    properties:
      location: brazilsouth
      properties:
        createMode: PointInTimeRestore
        restorePointInTime: 2017-12-14T00:00:37.467Z
        sourceServerId: /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/SourceResourceGroup/providers/Microsoft.DBforMariaDB/servers/sourceserver
      resourceGroupName: TargetResourceGroup
      serverName: targetserver
      sku:
        capacity: 2
        family: Gen5
        name: GP_Gen5_2
        tier: GeneralPurpose
      tags:
        ElasticServer: '1'

```

{{% /example %}}
{{% example %}}
### Create a new server
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var server = new AzureNative.DBforMariaDB.Server("server", new()
    {
        Location = "westus",
        Properties = new AzureNative.DBforMariaDB.Inputs.ServerPropertiesForDefaultCreateArgs
        {
            AdministratorLogin = "cloudsa",
            AdministratorLoginPassword = "<administratorLoginPassword>",
            CreateMode = "Default",
            MinimalTlsVersion = "TLS1_2",
            SslEnforcement = AzureNative.DBforMariaDB.SslEnforcementEnum.Enabled,
            StorageProfile = new AzureNative.DBforMariaDB.Inputs.StorageProfileArgs
            {
                BackupRetentionDays = 7,
                GeoRedundantBackup = "Enabled",
                StorageMB = 128000,
            },
        },
        ResourceGroupName = "testrg",
        ServerName = "mariadbtestsvc4",
        Sku = new AzureNative.DBforMariaDB.Inputs.SkuArgs
        {
            Capacity = 2,
            Family = "Gen5",
            Name = "GP_Gen5_2",
            Tier = "GeneralPurpose",
        },
        Tags = 
        {
            { "ElasticServer", "1" },
        },
    });

});


```

```go
package main

import (
	dbformariadb "github.com/pulumi/pulumi-azure-native-sdk/dbformariadb"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := dbformariadb.NewServer(ctx, "server", &dbformariadb.ServerArgs{
			Location: pulumi.String("westus"),
			Properties: dbformariadb.ServerPropertiesForDefaultCreate{
				AdministratorLogin:         "cloudsa",
				AdministratorLoginPassword: "<administratorLoginPassword>",
				CreateMode:                 "Default",
				MinimalTlsVersion:          "TLS1_2",
				SslEnforcement:             dbformariadb.SslEnforcementEnumEnabled,
				StorageProfile: dbformariadb.StorageProfile{
					BackupRetentionDays: 7,
					GeoRedundantBackup:  "Enabled",
					StorageMB:           128000,
				},
			},
			ResourceGroupName: pulumi.String("testrg"),
			ServerName:        pulumi.String("mariadbtestsvc4"),
			Sku: &dbformariadb.SkuArgs{
				Capacity: pulumi.Int(2),
				Family:   pulumi.String("Gen5"),
				Name:     pulumi.String("GP_Gen5_2"),
				Tier:     pulumi.String("GeneralPurpose"),
			},
			Tags: pulumi.StringMap{
				"ElasticServer": pulumi.String("1"),
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
import com.pulumi.azurenative.dbformariadb.Server;
import com.pulumi.azurenative.dbformariadb.ServerArgs;
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
            .location("westus")
            .properties(Map.ofEntries(
                Map.entry("administratorLogin", "cloudsa"),
                Map.entry("administratorLoginPassword", "<administratorLoginPassword>"),
                Map.entry("createMode", "Default"),
                Map.entry("minimalTlsVersion", "TLS1_2"),
                Map.entry("sslEnforcement", "Enabled"),
                Map.entry("storageProfile", Map.ofEntries(
                    Map.entry("backupRetentionDays", 7),
                    Map.entry("geoRedundantBackup", "Enabled"),
                    Map.entry("storageMB", 128000)
                ))
            ))
            .resourceGroupName("testrg")
            .serverName("mariadbtestsvc4")
            .sku(Map.ofEntries(
                Map.entry("capacity", 2),
                Map.entry("family", "Gen5"),
                Map.entry("name", "GP_Gen5_2"),
                Map.entry("tier", "GeneralPurpose")
            ))
            .tags(Map.of("ElasticServer", "1"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const server = new azure_native.dbformariadb.Server("server", {
    location: "westus",
    properties: {
        administratorLogin: "cloudsa",
        administratorLoginPassword: "<administratorLoginPassword>",
        createMode: "Default",
        minimalTlsVersion: "TLS1_2",
        sslEnforcement: azure_native.dbformariadb.SslEnforcementEnum.Enabled,
        storageProfile: {
            backupRetentionDays: 7,
            geoRedundantBackup: "Enabled",
            storageMB: 128000,
        },
    },
    resourceGroupName: "testrg",
    serverName: "mariadbtestsvc4",
    sku: {
        capacity: 2,
        family: "Gen5",
        name: "GP_Gen5_2",
        tier: "GeneralPurpose",
    },
    tags: {
        ElasticServer: "1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

server = azure_native.dbformariadb.Server("server",
    location="westus",
    properties=azure_native.dbformariadb.ServerPropertiesForDefaultCreateArgs(
        administrator_login="cloudsa",
        administrator_login_password="<administratorLoginPassword>",
        create_mode="Default",
        minimal_tls_version="TLS1_2",
        ssl_enforcement=azure_native.dbformariadb.SslEnforcementEnum.ENABLED,
        storage_profile=azure_native.dbformariadb.StorageProfileArgs(
            backup_retention_days=7,
            geo_redundant_backup="Enabled",
            storage_mb=128000,
        ),
    ),
    resource_group_name="testrg",
    server_name="mariadbtestsvc4",
    sku=azure_native.dbformariadb.SkuArgs(
        capacity=2,
        family="Gen5",
        name="GP_Gen5_2",
        tier="GeneralPurpose",
    ),
    tags={
        "ElasticServer": "1",
    })

```

```yaml
resources:
  server:
    type: azure-native:dbformariadb:Server
    properties:
      location: westus
      properties:
        administratorLogin: cloudsa
        administratorLoginPassword: <administratorLoginPassword>
        createMode: Default
        minimalTlsVersion: TLS1_2
        sslEnforcement: Enabled
        storageProfile:
          backupRetentionDays: 7
          geoRedundantBackup: Enabled
          storageMB: 128000
      resourceGroupName: testrg
      serverName: mariadbtestsvc4
      sku:
        capacity: 2
        family: Gen5
        name: GP_Gen5_2
        tier: GeneralPurpose
      tags:
        ElasticServer: '1'

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
    var server = new AzureNative.DBforMariaDB.Server("server", new()
    {
        Location = "westus",
        Properties = new AzureNative.DBforMariaDB.Inputs.ServerPropertiesForReplicaArgs
        {
            CreateMode = "Replica",
            SourceServerId = "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/MasterResourceGroup/providers/Microsoft.DBforMariaDB/servers/masterserver",
        },
        ResourceGroupName = "TargetResourceGroup",
        ServerName = "targetserver",
    });

});


```

```go
package main

import (
	dbformariadb "github.com/pulumi/pulumi-azure-native-sdk/dbformariadb"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := dbformariadb.NewServer(ctx, "server", &dbformariadb.ServerArgs{
			Location: pulumi.String("westus"),
			Properties: dbformariadb.ServerPropertiesForReplica{
				CreateMode:     "Replica",
				SourceServerId: "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/MasterResourceGroup/providers/Microsoft.DBforMariaDB/servers/masterserver",
			},
			ResourceGroupName: pulumi.String("TargetResourceGroup"),
			ServerName:        pulumi.String("targetserver"),
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
import com.pulumi.azurenative.dbformariadb.Server;
import com.pulumi.azurenative.dbformariadb.ServerArgs;
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
            .location("westus")
            .properties(Map.ofEntries(
                Map.entry("createMode", "Replica"),
                Map.entry("sourceServerId", "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/MasterResourceGroup/providers/Microsoft.DBforMariaDB/servers/masterserver")
            ))
            .resourceGroupName("TargetResourceGroup")
            .serverName("targetserver")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const server = new azure_native.dbformariadb.Server("server", {
    location: "westus",
    properties: {
        createMode: "Replica",
        sourceServerId: "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/MasterResourceGroup/providers/Microsoft.DBforMariaDB/servers/masterserver",
    },
    resourceGroupName: "TargetResourceGroup",
    serverName: "targetserver",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

server = azure_native.dbformariadb.Server("server",
    location="westus",
    properties=azure_native.dbformariadb.ServerPropertiesForReplicaArgs(
        create_mode="Replica",
        source_server_id="/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/MasterResourceGroup/providers/Microsoft.DBforMariaDB/servers/masterserver",
    ),
    resource_group_name="TargetResourceGroup",
    server_name="targetserver")

```

```yaml
resources:
  server:
    type: azure-native:dbformariadb:Server
    properties:
      location: westus
      properties:
        createMode: Replica
        sourceServerId: /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/MasterResourceGroup/providers/Microsoft.DBforMariaDB/servers/masterserver
      resourceGroupName: TargetResourceGroup
      serverName: targetserver

```

{{% /example %}}
{{% example %}}
### Create a server as a geo restore 
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var server = new AzureNative.DBforMariaDB.Server("server", new()
    {
        Location = "westus",
        Properties = new AzureNative.DBforMariaDB.Inputs.ServerPropertiesForGeoRestoreArgs
        {
            CreateMode = "GeoRestore",
            SourceServerId = "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/SourceResourceGroup/providers/Microsoft.DBforMariaDB/servers/sourceserver",
        },
        ResourceGroupName = "TargetResourceGroup",
        ServerName = "targetserver",
        Sku = new AzureNative.DBforMariaDB.Inputs.SkuArgs
        {
            Capacity = 2,
            Family = "Gen5",
            Name = "GP_Gen5_2",
            Tier = "GeneralPurpose",
        },
        Tags = 
        {
            { "ElasticServer", "1" },
        },
    });

});


```

```go
package main

import (
	dbformariadb "github.com/pulumi/pulumi-azure-native-sdk/dbformariadb"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := dbformariadb.NewServer(ctx, "server", &dbformariadb.ServerArgs{
			Location: pulumi.String("westus"),
			Properties: dbformariadb.ServerPropertiesForGeoRestore{
				CreateMode:     "GeoRestore",
				SourceServerId: "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/SourceResourceGroup/providers/Microsoft.DBforMariaDB/servers/sourceserver",
			},
			ResourceGroupName: pulumi.String("TargetResourceGroup"),
			ServerName:        pulumi.String("targetserver"),
			Sku: &dbformariadb.SkuArgs{
				Capacity: pulumi.Int(2),
				Family:   pulumi.String("Gen5"),
				Name:     pulumi.String("GP_Gen5_2"),
				Tier:     pulumi.String("GeneralPurpose"),
			},
			Tags: pulumi.StringMap{
				"ElasticServer": pulumi.String("1"),
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
import com.pulumi.azurenative.dbformariadb.Server;
import com.pulumi.azurenative.dbformariadb.ServerArgs;
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
            .location("westus")
            .properties(Map.ofEntries(
                Map.entry("createMode", "GeoRestore"),
                Map.entry("sourceServerId", "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/SourceResourceGroup/providers/Microsoft.DBforMariaDB/servers/sourceserver")
            ))
            .resourceGroupName("TargetResourceGroup")
            .serverName("targetserver")
            .sku(Map.ofEntries(
                Map.entry("capacity", 2),
                Map.entry("family", "Gen5"),
                Map.entry("name", "GP_Gen5_2"),
                Map.entry("tier", "GeneralPurpose")
            ))
            .tags(Map.of("ElasticServer", "1"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const server = new azure_native.dbformariadb.Server("server", {
    location: "westus",
    properties: {
        createMode: "GeoRestore",
        sourceServerId: "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/SourceResourceGroup/providers/Microsoft.DBforMariaDB/servers/sourceserver",
    },
    resourceGroupName: "TargetResourceGroup",
    serverName: "targetserver",
    sku: {
        capacity: 2,
        family: "Gen5",
        name: "GP_Gen5_2",
        tier: "GeneralPurpose",
    },
    tags: {
        ElasticServer: "1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

server = azure_native.dbformariadb.Server("server",
    location="westus",
    properties=azure_native.dbformariadb.ServerPropertiesForGeoRestoreArgs(
        create_mode="GeoRestore",
        source_server_id="/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/SourceResourceGroup/providers/Microsoft.DBforMariaDB/servers/sourceserver",
    ),
    resource_group_name="TargetResourceGroup",
    server_name="targetserver",
    sku=azure_native.dbformariadb.SkuArgs(
        capacity=2,
        family="Gen5",
        name="GP_Gen5_2",
        tier="GeneralPurpose",
    ),
    tags={
        "ElasticServer": "1",
    })

```

```yaml
resources:
  server:
    type: azure-native:dbformariadb:Server
    properties:
      location: westus
      properties:
        createMode: GeoRestore
        sourceServerId: /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/SourceResourceGroup/providers/Microsoft.DBforMariaDB/servers/sourceserver
      resourceGroupName: TargetResourceGroup
      serverName: targetserver
      sku:
        capacity: 2
        family: Gen5
        name: GP_Gen5_2
        tier: GeneralPurpose
      tags:
        ElasticServer: '1'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:dbformariadb:Server targetserver /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.DBforMariaDB/servers/targetserver 
```
