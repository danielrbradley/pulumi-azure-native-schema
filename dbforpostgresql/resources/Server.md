Represents a server.
API Version: 2022-12-01.
Previous API Version: 2017-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a database as a geo-restore in geo-paired location
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var server = new AzureNative.DBforPostgreSQL.Server("server", new()
    {
        CreateMode = "GeoRestore",
        Location = "eastus",
        PointInTimeUTC = "2021-06-27T00:04:59.4078005+00:00",
        ResourceGroupName = "testrg",
        ServerName = "pgtestsvc5geo",
        SourceServerResourceId = "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.DBforPostgreSQL/flexibleServers/sourcepgservername",
    });

});


```

```go
package main

import (
	dbforpostgresql "github.com/pulumi/pulumi-azure-native-sdk/dbforpostgresql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := dbforpostgresql.NewServer(ctx, "server", &dbforpostgresql.ServerArgs{
			CreateMode:             pulumi.String("GeoRestore"),
			Location:               pulumi.String("eastus"),
			PointInTimeUTC:         pulumi.String("2021-06-27T00:04:59.4078005+00:00"),
			ResourceGroupName:      pulumi.String("testrg"),
			ServerName:             pulumi.String("pgtestsvc5geo"),
			SourceServerResourceId: pulumi.String("/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.DBforPostgreSQL/flexibleServers/sourcepgservername"),
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
import com.pulumi.azurenative.dbforpostgresql.Server;
import com.pulumi.azurenative.dbforpostgresql.ServerArgs;
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
            .createMode("GeoRestore")
            .location("eastus")
            .pointInTimeUTC("2021-06-27T00:04:59.4078005+00:00")
            .resourceGroupName("testrg")
            .serverName("pgtestsvc5geo")
            .sourceServerResourceId("/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.DBforPostgreSQL/flexibleServers/sourcepgservername")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const server = new azure_native.dbforpostgresql.Server("server", {
    createMode: "GeoRestore",
    location: "eastus",
    pointInTimeUTC: "2021-06-27T00:04:59.4078005+00:00",
    resourceGroupName: "testrg",
    serverName: "pgtestsvc5geo",
    sourceServerResourceId: "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.DBforPostgreSQL/flexibleServers/sourcepgservername",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

server = azure_native.dbforpostgresql.Server("server",
    create_mode="GeoRestore",
    location="eastus",
    point_in_time_utc="2021-06-27T00:04:59.4078005+00:00",
    resource_group_name="testrg",
    server_name="pgtestsvc5geo",
    source_server_resource_id="/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.DBforPostgreSQL/flexibleServers/sourcepgservername")

```

```yaml
resources:
  server:
    type: azure-native:dbforpostgresql:Server
    properties:
      createMode: GeoRestore
      location: eastus
      pointInTimeUTC: 2021-06-27T00:04:59.4078005+00:00
      resourceGroupName: testrg
      serverName: pgtestsvc5geo
      sourceServerResourceId: /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.DBforPostgreSQL/flexibleServers/sourcepgservername

```

{{% /example %}}
{{% example %}}
### Create a database as a point in time restore
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var server = new AzureNative.DBforPostgreSQL.Server("server", new()
    {
        CreateMode = "PointInTimeRestore",
        Location = "westus",
        PointInTimeUTC = "2021-06-27T00:04:59.4078005+00:00",
        ResourceGroupName = "testrg",
        ServerName = "pgtestsvc5",
        SourceServerResourceId = "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.DBforPostgreSQL/flexibleServers/sourcepgservername",
    });

});


```

```go
package main

import (
	dbforpostgresql "github.com/pulumi/pulumi-azure-native-sdk/dbforpostgresql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := dbforpostgresql.NewServer(ctx, "server", &dbforpostgresql.ServerArgs{
			CreateMode:             pulumi.String("PointInTimeRestore"),
			Location:               pulumi.String("westus"),
			PointInTimeUTC:         pulumi.String("2021-06-27T00:04:59.4078005+00:00"),
			ResourceGroupName:      pulumi.String("testrg"),
			ServerName:             pulumi.String("pgtestsvc5"),
			SourceServerResourceId: pulumi.String("/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.DBforPostgreSQL/flexibleServers/sourcepgservername"),
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
import com.pulumi.azurenative.dbforpostgresql.Server;
import com.pulumi.azurenative.dbforpostgresql.ServerArgs;
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
            .location("westus")
            .pointInTimeUTC("2021-06-27T00:04:59.4078005+00:00")
            .resourceGroupName("testrg")
            .serverName("pgtestsvc5")
            .sourceServerResourceId("/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.DBforPostgreSQL/flexibleServers/sourcepgservername")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const server = new azure_native.dbforpostgresql.Server("server", {
    createMode: "PointInTimeRestore",
    location: "westus",
    pointInTimeUTC: "2021-06-27T00:04:59.4078005+00:00",
    resourceGroupName: "testrg",
    serverName: "pgtestsvc5",
    sourceServerResourceId: "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.DBforPostgreSQL/flexibleServers/sourcepgservername",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

server = azure_native.dbforpostgresql.Server("server",
    create_mode="PointInTimeRestore",
    location="westus",
    point_in_time_utc="2021-06-27T00:04:59.4078005+00:00",
    resource_group_name="testrg",
    server_name="pgtestsvc5",
    source_server_resource_id="/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.DBforPostgreSQL/flexibleServers/sourcepgservername")

```

```yaml
resources:
  server:
    type: azure-native:dbforpostgresql:Server
    properties:
      createMode: PointInTimeRestore
      location: westus
      pointInTimeUTC: 2021-06-27T00:04:59.4078005+00:00
      resourceGroupName: testrg
      serverName: pgtestsvc5
      sourceServerResourceId: /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.DBforPostgreSQL/flexibleServers/sourcepgservername

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
    var server = new AzureNative.DBforPostgreSQL.Server("server", new()
    {
        AdministratorLogin = "cloudsa",
        AdministratorLoginPassword = "password",
        AvailabilityZone = "1",
        Backup = new AzureNative.DBforPostgreSQL.Inputs.BackupArgs
        {
            BackupRetentionDays = 7,
            GeoRedundantBackup = "Disabled",
        },
        CreateMode = "Create",
        HighAvailability = new AzureNative.DBforPostgreSQL.Inputs.HighAvailabilityArgs
        {
            Mode = "ZoneRedundant",
        },
        Location = "westus",
        Network = new AzureNative.DBforPostgreSQL.Inputs.NetworkArgs
        {
            DelegatedSubnetResourceId = "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/test-vnet-subnet",
            PrivateDnsZoneArmResourceId = "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourcegroups/testrg/providers/Microsoft.Network/privateDnsZones/test-private-dns-zone.postgres.database.azure.com",
        },
        ResourceGroupName = "testrg",
        ServerName = "pgtestsvc4",
        Sku = new AzureNative.DBforPostgreSQL.Inputs.SkuArgs
        {
            Name = "Standard_D4s_v3",
            Tier = "GeneralPurpose",
        },
        Storage = new AzureNative.DBforPostgreSQL.Inputs.StorageArgs
        {
            StorageSizeGB = 512,
        },
        Tags = 
        {
            { "ElasticServer", "1" },
        },
        Version = "12",
    });

});


```

```go
package main

import (
	dbforpostgresql "github.com/pulumi/pulumi-azure-native-sdk/dbforpostgresql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := dbforpostgresql.NewServer(ctx, "server", &dbforpostgresql.ServerArgs{
			AdministratorLogin:         pulumi.String("cloudsa"),
			AdministratorLoginPassword: pulumi.String("password"),
			AvailabilityZone:           pulumi.String("1"),
			Backup: &dbforpostgresql.BackupArgs{
				BackupRetentionDays: pulumi.Int(7),
				GeoRedundantBackup:  pulumi.String("Disabled"),
			},
			CreateMode: pulumi.String("Create"),
			HighAvailability: &dbforpostgresql.HighAvailabilityArgs{
				Mode: pulumi.String("ZoneRedundant"),
			},
			Location: pulumi.String("westus"),
			Network: &dbforpostgresql.NetworkArgs{
				DelegatedSubnetResourceId:   pulumi.String("/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/test-vnet-subnet"),
				PrivateDnsZoneArmResourceId: pulumi.String("/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourcegroups/testrg/providers/Microsoft.Network/privateDnsZones/test-private-dns-zone.postgres.database.azure.com"),
			},
			ResourceGroupName: pulumi.String("testrg"),
			ServerName:        pulumi.String("pgtestsvc4"),
			Sku: &dbforpostgresql.SkuArgs{
				Name: pulumi.String("Standard_D4s_v3"),
				Tier: pulumi.String("GeneralPurpose"),
			},
			Storage: &dbforpostgresql.StorageArgs{
				StorageSizeGB: pulumi.Int(512),
			},
			Tags: pulumi.StringMap{
				"ElasticServer": pulumi.String("1"),
			},
			Version: pulumi.String("12"),
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
import com.pulumi.azurenative.dbforpostgresql.Server;
import com.pulumi.azurenative.dbforpostgresql.ServerArgs;
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
            .administratorLoginPassword("password")
            .availabilityZone("1")
            .backup(Map.ofEntries(
                Map.entry("backupRetentionDays", 7),
                Map.entry("geoRedundantBackup", "Disabled")
            ))
            .createMode("Create")
            .highAvailability(Map.of("mode", "ZoneRedundant"))
            .location("westus")
            .network(Map.ofEntries(
                Map.entry("delegatedSubnetResourceId", "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/test-vnet-subnet"),
                Map.entry("privateDnsZoneArmResourceId", "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourcegroups/testrg/providers/Microsoft.Network/privateDnsZones/test-private-dns-zone.postgres.database.azure.com")
            ))
            .resourceGroupName("testrg")
            .serverName("pgtestsvc4")
            .sku(Map.ofEntries(
                Map.entry("name", "Standard_D4s_v3"),
                Map.entry("tier", "GeneralPurpose")
            ))
            .storage(Map.of("storageSizeGB", 512))
            .tags(Map.of("ElasticServer", "1"))
            .version("12")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const server = new azure_native.dbforpostgresql.Server("server", {
    administratorLogin: "cloudsa",
    administratorLoginPassword: "password",
    availabilityZone: "1",
    backup: {
        backupRetentionDays: 7,
        geoRedundantBackup: "Disabled",
    },
    createMode: "Create",
    highAvailability: {
        mode: "ZoneRedundant",
    },
    location: "westus",
    network: {
        delegatedSubnetResourceId: "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/test-vnet-subnet",
        privateDnsZoneArmResourceId: "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourcegroups/testrg/providers/Microsoft.Network/privateDnsZones/test-private-dns-zone.postgres.database.azure.com",
    },
    resourceGroupName: "testrg",
    serverName: "pgtestsvc4",
    sku: {
        name: "Standard_D4s_v3",
        tier: "GeneralPurpose",
    },
    storage: {
        storageSizeGB: 512,
    },
    tags: {
        ElasticServer: "1",
    },
    version: "12",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

server = azure_native.dbforpostgresql.Server("server",
    administrator_login="cloudsa",
    administrator_login_password="password",
    availability_zone="1",
    backup=azure_native.dbforpostgresql.BackupArgs(
        backup_retention_days=7,
        geo_redundant_backup="Disabled",
    ),
    create_mode="Create",
    high_availability=azure_native.dbforpostgresql.HighAvailabilityArgs(
        mode="ZoneRedundant",
    ),
    location="westus",
    network=azure_native.dbforpostgresql.NetworkArgs(
        delegated_subnet_resource_id="/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/test-vnet-subnet",
        private_dns_zone_arm_resource_id="/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourcegroups/testrg/providers/Microsoft.Network/privateDnsZones/test-private-dns-zone.postgres.database.azure.com",
    ),
    resource_group_name="testrg",
    server_name="pgtestsvc4",
    sku=azure_native.dbforpostgresql.SkuArgs(
        name="Standard_D4s_v3",
        tier="GeneralPurpose",
    ),
    storage=azure_native.dbforpostgresql.StorageArgs(
        storage_size_gb=512,
    ),
    tags={
        "ElasticServer": "1",
    },
    version="12")

```

```yaml
resources:
  server:
    type: azure-native:dbforpostgresql:Server
    properties:
      administratorLogin: cloudsa
      administratorLoginPassword: password
      availabilityZone: '1'
      backup:
        backupRetentionDays: 7
        geoRedundantBackup: Disabled
      createMode: Create
      highAvailability:
        mode: ZoneRedundant
      location: westus
      network:
        delegatedSubnetResourceId: /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/test-vnet-subnet
        privateDnsZoneArmResourceId: /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourcegroups/testrg/providers/Microsoft.Network/privateDnsZones/test-private-dns-zone.postgres.database.azure.com
      resourceGroupName: testrg
      serverName: pgtestsvc4
      sku:
        name: Standard_D4s_v3
        tier: GeneralPurpose
      storage:
        storageSizeGB: 512
      tags:
        ElasticServer: '1'
      version: '12'

```

{{% /example %}}
{{% example %}}
### Create a new server with active directory authentication enabled
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var server = new AzureNative.DBforPostgreSQL.Server("server", new()
    {
        AdministratorLogin = "cloudsa",
        AdministratorLoginPassword = "password",
        AuthConfig = new AzureNative.DBforPostgreSQL.Inputs.AuthConfigArgs
        {
            ActiveDirectoryAuth = "Enabled",
            PasswordAuth = "Enabled",
            TenantId = "tttttt-tttt-tttt-tttt-tttttttttttt",
        },
        AvailabilityZone = "1",
        Backup = new AzureNative.DBforPostgreSQL.Inputs.BackupArgs
        {
            BackupRetentionDays = 7,
            GeoRedundantBackup = "Disabled",
        },
        CreateMode = "Create",
        DataEncryption = new AzureNative.DBforPostgreSQL.Inputs.DataEncryptionArgs
        {
            Type = "SystemManaged",
        },
        HighAvailability = new AzureNative.DBforPostgreSQL.Inputs.HighAvailabilityArgs
        {
            Mode = "ZoneRedundant",
        },
        Location = "westus",
        Network = new AzureNative.DBforPostgreSQL.Inputs.NetworkArgs
        {
            DelegatedSubnetResourceId = "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/test-vnet-subnet",
            PrivateDnsZoneArmResourceId = "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourcegroups/testrg/providers/Microsoft.Network/privateDnsZones/test-private-dns-zone.postgres.database.azure.com",
        },
        ResourceGroupName = "testrg",
        ServerName = "pgtestsvc4",
        Sku = new AzureNative.DBforPostgreSQL.Inputs.SkuArgs
        {
            Name = "Standard_D4s_v3",
            Tier = "GeneralPurpose",
        },
        Storage = new AzureNative.DBforPostgreSQL.Inputs.StorageArgs
        {
            StorageSizeGB = 512,
        },
        Tags = 
        {
            { "ElasticServer", "1" },
        },
        Version = "12",
    });

});


```

```go
package main

import (
	dbforpostgresql "github.com/pulumi/pulumi-azure-native-sdk/dbforpostgresql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := dbforpostgresql.NewServer(ctx, "server", &dbforpostgresql.ServerArgs{
			AdministratorLogin:         pulumi.String("cloudsa"),
			AdministratorLoginPassword: pulumi.String("password"),
			AuthConfig: &dbforpostgresql.AuthConfigArgs{
				ActiveDirectoryAuth: pulumi.String("Enabled"),
				PasswordAuth:        pulumi.String("Enabled"),
				TenantId:            pulumi.String("tttttt-tttt-tttt-tttt-tttttttttttt"),
			},
			AvailabilityZone: pulumi.String("1"),
			Backup: &dbforpostgresql.BackupArgs{
				BackupRetentionDays: pulumi.Int(7),
				GeoRedundantBackup:  pulumi.String("Disabled"),
			},
			CreateMode: pulumi.String("Create"),
			DataEncryption: &dbforpostgresql.DataEncryptionArgs{
				Type: pulumi.String("SystemManaged"),
			},
			HighAvailability: &dbforpostgresql.HighAvailabilityArgs{
				Mode: pulumi.String("ZoneRedundant"),
			},
			Location: pulumi.String("westus"),
			Network: &dbforpostgresql.NetworkArgs{
				DelegatedSubnetResourceId:   pulumi.String("/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/test-vnet-subnet"),
				PrivateDnsZoneArmResourceId: pulumi.String("/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourcegroups/testrg/providers/Microsoft.Network/privateDnsZones/test-private-dns-zone.postgres.database.azure.com"),
			},
			ResourceGroupName: pulumi.String("testrg"),
			ServerName:        pulumi.String("pgtestsvc4"),
			Sku: &dbforpostgresql.SkuArgs{
				Name: pulumi.String("Standard_D4s_v3"),
				Tier: pulumi.String("GeneralPurpose"),
			},
			Storage: &dbforpostgresql.StorageArgs{
				StorageSizeGB: pulumi.Int(512),
			},
			Tags: pulumi.StringMap{
				"ElasticServer": pulumi.String("1"),
			},
			Version: pulumi.String("12"),
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
import com.pulumi.azurenative.dbforpostgresql.Server;
import com.pulumi.azurenative.dbforpostgresql.ServerArgs;
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
            .administratorLoginPassword("password")
            .authConfig(Map.ofEntries(
                Map.entry("activeDirectoryAuth", "Enabled"),
                Map.entry("passwordAuth", "Enabled"),
                Map.entry("tenantId", "tttttt-tttt-tttt-tttt-tttttttttttt")
            ))
            .availabilityZone("1")
            .backup(Map.ofEntries(
                Map.entry("backupRetentionDays", 7),
                Map.entry("geoRedundantBackup", "Disabled")
            ))
            .createMode("Create")
            .dataEncryption(Map.of("type", "SystemManaged"))
            .highAvailability(Map.of("mode", "ZoneRedundant"))
            .location("westus")
            .network(Map.ofEntries(
                Map.entry("delegatedSubnetResourceId", "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/test-vnet-subnet"),
                Map.entry("privateDnsZoneArmResourceId", "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourcegroups/testrg/providers/Microsoft.Network/privateDnsZones/test-private-dns-zone.postgres.database.azure.com")
            ))
            .resourceGroupName("testrg")
            .serverName("pgtestsvc4")
            .sku(Map.ofEntries(
                Map.entry("name", "Standard_D4s_v3"),
                Map.entry("tier", "GeneralPurpose")
            ))
            .storage(Map.of("storageSizeGB", 512))
            .tags(Map.of("ElasticServer", "1"))
            .version("12")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const server = new azure_native.dbforpostgresql.Server("server", {
    administratorLogin: "cloudsa",
    administratorLoginPassword: "password",
    authConfig: {
        activeDirectoryAuth: "Enabled",
        passwordAuth: "Enabled",
        tenantId: "tttttt-tttt-tttt-tttt-tttttttttttt",
    },
    availabilityZone: "1",
    backup: {
        backupRetentionDays: 7,
        geoRedundantBackup: "Disabled",
    },
    createMode: "Create",
    dataEncryption: {
        type: "SystemManaged",
    },
    highAvailability: {
        mode: "ZoneRedundant",
    },
    location: "westus",
    network: {
        delegatedSubnetResourceId: "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/test-vnet-subnet",
        privateDnsZoneArmResourceId: "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourcegroups/testrg/providers/Microsoft.Network/privateDnsZones/test-private-dns-zone.postgres.database.azure.com",
    },
    resourceGroupName: "testrg",
    serverName: "pgtestsvc4",
    sku: {
        name: "Standard_D4s_v3",
        tier: "GeneralPurpose",
    },
    storage: {
        storageSizeGB: 512,
    },
    tags: {
        ElasticServer: "1",
    },
    version: "12",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

server = azure_native.dbforpostgresql.Server("server",
    administrator_login="cloudsa",
    administrator_login_password="password",
    auth_config=azure_native.dbforpostgresql.AuthConfigArgs(
        active_directory_auth="Enabled",
        password_auth="Enabled",
        tenant_id="tttttt-tttt-tttt-tttt-tttttttttttt",
    ),
    availability_zone="1",
    backup=azure_native.dbforpostgresql.BackupArgs(
        backup_retention_days=7,
        geo_redundant_backup="Disabled",
    ),
    create_mode="Create",
    data_encryption=azure_native.dbforpostgresql.DataEncryptionArgs(
        type="SystemManaged",
    ),
    high_availability=azure_native.dbforpostgresql.HighAvailabilityArgs(
        mode="ZoneRedundant",
    ),
    location="westus",
    network=azure_native.dbforpostgresql.NetworkArgs(
        delegated_subnet_resource_id="/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/test-vnet-subnet",
        private_dns_zone_arm_resource_id="/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourcegroups/testrg/providers/Microsoft.Network/privateDnsZones/test-private-dns-zone.postgres.database.azure.com",
    ),
    resource_group_name="testrg",
    server_name="pgtestsvc4",
    sku=azure_native.dbforpostgresql.SkuArgs(
        name="Standard_D4s_v3",
        tier="GeneralPurpose",
    ),
    storage=azure_native.dbforpostgresql.StorageArgs(
        storage_size_gb=512,
    ),
    tags={
        "ElasticServer": "1",
    },
    version="12")

```

```yaml
resources:
  server:
    type: azure-native:dbforpostgresql:Server
    properties:
      administratorLogin: cloudsa
      administratorLoginPassword: password
      authConfig:
        activeDirectoryAuth: Enabled
        passwordAuth: Enabled
        tenantId: tttttt-tttt-tttt-tttt-tttttttttttt
      availabilityZone: '1'
      backup:
        backupRetentionDays: 7
        geoRedundantBackup: Disabled
      createMode: Create
      dataEncryption:
        type: SystemManaged
      highAvailability:
        mode: ZoneRedundant
      location: westus
      network:
        delegatedSubnetResourceId: /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/test-vnet-subnet
        privateDnsZoneArmResourceId: /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourcegroups/testrg/providers/Microsoft.Network/privateDnsZones/test-private-dns-zone.postgres.database.azure.com
      resourceGroupName: testrg
      serverName: pgtestsvc4
      sku:
        name: Standard_D4s_v3
        tier: GeneralPurpose
      storage:
        storageSizeGB: 512
      tags:
        ElasticServer: '1'
      version: '12'

```

{{% /example %}}
{{% example %}}
### ServerCreateReplica
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var server = new AzureNative.DBforPostgreSQL.Server("server", new()
    {
        CreateMode = "Replica",
        Location = "westus",
        PointInTimeUTC = "2021-06-27T00:04:59.4078005+00:00",
        ResourceGroupName = "testrg",
        ServerName = "pgtestsvc5rep",
        SourceServerResourceId = "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.DBforPostgreSQL/flexibleServers/sourcepgservername",
    });

});


```

```go
package main

import (
	dbforpostgresql "github.com/pulumi/pulumi-azure-native-sdk/dbforpostgresql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := dbforpostgresql.NewServer(ctx, "server", &dbforpostgresql.ServerArgs{
			CreateMode:             pulumi.String("Replica"),
			Location:               pulumi.String("westus"),
			PointInTimeUTC:         pulumi.String("2021-06-27T00:04:59.4078005+00:00"),
			ResourceGroupName:      pulumi.String("testrg"),
			ServerName:             pulumi.String("pgtestsvc5rep"),
			SourceServerResourceId: pulumi.String("/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.DBforPostgreSQL/flexibleServers/sourcepgservername"),
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
import com.pulumi.azurenative.dbforpostgresql.Server;
import com.pulumi.azurenative.dbforpostgresql.ServerArgs;
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
            .location("westus")
            .pointInTimeUTC("2021-06-27T00:04:59.4078005+00:00")
            .resourceGroupName("testrg")
            .serverName("pgtestsvc5rep")
            .sourceServerResourceId("/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.DBforPostgreSQL/flexibleServers/sourcepgservername")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const server = new azure_native.dbforpostgresql.Server("server", {
    createMode: "Replica",
    location: "westus",
    pointInTimeUTC: "2021-06-27T00:04:59.4078005+00:00",
    resourceGroupName: "testrg",
    serverName: "pgtestsvc5rep",
    sourceServerResourceId: "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.DBforPostgreSQL/flexibleServers/sourcepgservername",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

server = azure_native.dbforpostgresql.Server("server",
    create_mode="Replica",
    location="westus",
    point_in_time_utc="2021-06-27T00:04:59.4078005+00:00",
    resource_group_name="testrg",
    server_name="pgtestsvc5rep",
    source_server_resource_id="/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.DBforPostgreSQL/flexibleServers/sourcepgservername")

```

```yaml
resources:
  server:
    type: azure-native:dbforpostgresql:Server
    properties:
      createMode: Replica
      location: westus
      pointInTimeUTC: 2021-06-27T00:04:59.4078005+00:00
      resourceGroupName: testrg
      serverName: pgtestsvc5rep
      sourceServerResourceId: /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.DBforPostgreSQL/flexibleServers/sourcepgservername

```

{{% /example %}}
{{% example %}}
### ServerCreateWithDataEncryptionEnabled
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var server = new AzureNative.DBforPostgreSQL.Server("server", new()
    {
        AdministratorLogin = "cloudsa",
        AdministratorLoginPassword = "password",
        AvailabilityZone = "1",
        Backup = new AzureNative.DBforPostgreSQL.Inputs.BackupArgs
        {
            BackupRetentionDays = 7,
            GeoRedundantBackup = "Disabled",
        },
        CreateMode = "Create",
        DataEncryption = new AzureNative.DBforPostgreSQL.Inputs.DataEncryptionArgs
        {
            PrimaryKeyURI = "https://test-kv.vault.azure.net/keys/test-key1/77f57315bab34b0189daa113fbc78787",
            PrimaryUserAssignedIdentityId = "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testresourcegroup/providers/Microsoft.ManagedIdentity/userAssignedIdentities/test-usermanagedidentity",
            Type = "AzureKeyVault",
        },
        HighAvailability = new AzureNative.DBforPostgreSQL.Inputs.HighAvailabilityArgs
        {
            Mode = "ZoneRedundant",
        },
        Identity = new AzureNative.DBforPostgreSQL.Inputs.UserAssignedIdentityArgs
        {
            Type = "UserAssigned",
            UserAssignedIdentities = 
            {
                { "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testresourcegroup/providers/Microsoft.ManagedIdentity/userAssignedIdentities/test-usermanagedidentity", null },
            },
        },
        Location = "westus",
        Network = new AzureNative.DBforPostgreSQL.Inputs.NetworkArgs
        {
            DelegatedSubnetResourceId = "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/test-vnet-subnet",
            PrivateDnsZoneArmResourceId = "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourcegroups/testrg/providers/Microsoft.Network/privateDnsZones/test-private-dns-zone.postgres.database.azure.com",
        },
        ResourceGroupName = "testrg",
        ServerName = "pgtestsvc4",
        Sku = new AzureNative.DBforPostgreSQL.Inputs.SkuArgs
        {
            Name = "Standard_D4s_v3",
            Tier = "GeneralPurpose",
        },
        Storage = new AzureNative.DBforPostgreSQL.Inputs.StorageArgs
        {
            StorageSizeGB = 512,
        },
        Tags = 
        {
            { "ElasticServer", "1" },
        },
        Version = "12",
    });

});


```

```go
package main

import (
	dbforpostgresql "github.com/pulumi/pulumi-azure-native-sdk/dbforpostgresql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := dbforpostgresql.NewServer(ctx, "server", &dbforpostgresql.ServerArgs{
			AdministratorLogin:         pulumi.String("cloudsa"),
			AdministratorLoginPassword: pulumi.String("password"),
			AvailabilityZone:           pulumi.String("1"),
			Backup: &dbforpostgresql.BackupArgs{
				BackupRetentionDays: pulumi.Int(7),
				GeoRedundantBackup:  pulumi.String("Disabled"),
			},
			CreateMode: pulumi.String("Create"),
			DataEncryption: &dbforpostgresql.DataEncryptionArgs{
				PrimaryKeyURI:                 pulumi.String("https://test-kv.vault.azure.net/keys/test-key1/77f57315bab34b0189daa113fbc78787"),
				PrimaryUserAssignedIdentityId: pulumi.String("/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testresourcegroup/providers/Microsoft.ManagedIdentity/userAssignedIdentities/test-usermanagedidentity"),
				Type:                          pulumi.String("AzureKeyVault"),
			},
			HighAvailability: &dbforpostgresql.HighAvailabilityArgs{
				Mode: pulumi.String("ZoneRedundant"),
			},
			Identity: dbforpostgresql.UserAssignedIdentityResponse{
				Type: pulumi.String("UserAssigned"),
				UserAssignedIdentities: dbforpostgresql.UserIdentityMap{
					"/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testresourcegroup/providers/Microsoft.ManagedIdentity/userAssignedIdentities/test-usermanagedidentity": nil,
				},
			},
			Location: pulumi.String("westus"),
			Network: &dbforpostgresql.NetworkArgs{
				DelegatedSubnetResourceId:   pulumi.String("/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/test-vnet-subnet"),
				PrivateDnsZoneArmResourceId: pulumi.String("/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourcegroups/testrg/providers/Microsoft.Network/privateDnsZones/test-private-dns-zone.postgres.database.azure.com"),
			},
			ResourceGroupName: pulumi.String("testrg"),
			ServerName:        pulumi.String("pgtestsvc4"),
			Sku: &dbforpostgresql.SkuArgs{
				Name: pulumi.String("Standard_D4s_v3"),
				Tier: pulumi.String("GeneralPurpose"),
			},
			Storage: &dbforpostgresql.StorageArgs{
				StorageSizeGB: pulumi.Int(512),
			},
			Tags: pulumi.StringMap{
				"ElasticServer": pulumi.String("1"),
			},
			Version: pulumi.String("12"),
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
import com.pulumi.azurenative.dbforpostgresql.Server;
import com.pulumi.azurenative.dbforpostgresql.ServerArgs;
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
            .administratorLoginPassword("password")
            .availabilityZone("1")
            .backup(Map.ofEntries(
                Map.entry("backupRetentionDays", 7),
                Map.entry("geoRedundantBackup", "Disabled")
            ))
            .createMode("Create")
            .dataEncryption(Map.ofEntries(
                Map.entry("primaryKeyURI", "https://test-kv.vault.azure.net/keys/test-key1/77f57315bab34b0189daa113fbc78787"),
                Map.entry("primaryUserAssignedIdentityId", "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testresourcegroup/providers/Microsoft.ManagedIdentity/userAssignedIdentities/test-usermanagedidentity"),
                Map.entry("type", "AzureKeyVault")
            ))
            .highAvailability(Map.of("mode", "ZoneRedundant"))
            .identity(Map.ofEntries(
                Map.entry("type", "UserAssigned"),
                Map.entry("userAssignedIdentities", Map.of("/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testresourcegroup/providers/Microsoft.ManagedIdentity/userAssignedIdentities/test-usermanagedidentity", ))
            ))
            .location("westus")
            .network(Map.ofEntries(
                Map.entry("delegatedSubnetResourceId", "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/test-vnet-subnet"),
                Map.entry("privateDnsZoneArmResourceId", "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourcegroups/testrg/providers/Microsoft.Network/privateDnsZones/test-private-dns-zone.postgres.database.azure.com")
            ))
            .resourceGroupName("testrg")
            .serverName("pgtestsvc4")
            .sku(Map.ofEntries(
                Map.entry("name", "Standard_D4s_v3"),
                Map.entry("tier", "GeneralPurpose")
            ))
            .storage(Map.of("storageSizeGB", 512))
            .tags(Map.of("ElasticServer", "1"))
            .version("12")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const server = new azure_native.dbforpostgresql.Server("server", {
    administratorLogin: "cloudsa",
    administratorLoginPassword: "password",
    availabilityZone: "1",
    backup: {
        backupRetentionDays: 7,
        geoRedundantBackup: "Disabled",
    },
    createMode: "Create",
    dataEncryption: {
        primaryKeyURI: "https://test-kv.vault.azure.net/keys/test-key1/77f57315bab34b0189daa113fbc78787",
        primaryUserAssignedIdentityId: "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testresourcegroup/providers/Microsoft.ManagedIdentity/userAssignedIdentities/test-usermanagedidentity",
        type: "AzureKeyVault",
    },
    highAvailability: {
        mode: "ZoneRedundant",
    },
    identity: {
        type: "UserAssigned",
        userAssignedIdentities: {
            "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testresourcegroup/providers/Microsoft.ManagedIdentity/userAssignedIdentities/test-usermanagedidentity": {},
        },
    },
    location: "westus",
    network: {
        delegatedSubnetResourceId: "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/test-vnet-subnet",
        privateDnsZoneArmResourceId: "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourcegroups/testrg/providers/Microsoft.Network/privateDnsZones/test-private-dns-zone.postgres.database.azure.com",
    },
    resourceGroupName: "testrg",
    serverName: "pgtestsvc4",
    sku: {
        name: "Standard_D4s_v3",
        tier: "GeneralPurpose",
    },
    storage: {
        storageSizeGB: 512,
    },
    tags: {
        ElasticServer: "1",
    },
    version: "12",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

server = azure_native.dbforpostgresql.Server("server",
    administrator_login="cloudsa",
    administrator_login_password="password",
    availability_zone="1",
    backup=azure_native.dbforpostgresql.BackupArgs(
        backup_retention_days=7,
        geo_redundant_backup="Disabled",
    ),
    create_mode="Create",
    data_encryption=azure_native.dbforpostgresql.DataEncryptionArgs(
        primary_key_uri="https://test-kv.vault.azure.net/keys/test-key1/77f57315bab34b0189daa113fbc78787",
        primary_user_assigned_identity_id="/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testresourcegroup/providers/Microsoft.ManagedIdentity/userAssignedIdentities/test-usermanagedidentity",
        type="AzureKeyVault",
    ),
    high_availability=azure_native.dbforpostgresql.HighAvailabilityArgs(
        mode="ZoneRedundant",
    ),
    identity=azure_native.dbforpostgresql.UserAssignedIdentityResponseArgs(
        type="UserAssigned",
        user_assigned_identities={
            "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testresourcegroup/providers/Microsoft.ManagedIdentity/userAssignedIdentities/test-usermanagedidentity": azure_native.dbforpostgresql.UserIdentityArgs(),
        },
    ),
    location="westus",
    network=azure_native.dbforpostgresql.NetworkArgs(
        delegated_subnet_resource_id="/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/test-vnet-subnet",
        private_dns_zone_arm_resource_id="/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourcegroups/testrg/providers/Microsoft.Network/privateDnsZones/test-private-dns-zone.postgres.database.azure.com",
    ),
    resource_group_name="testrg",
    server_name="pgtestsvc4",
    sku=azure_native.dbforpostgresql.SkuArgs(
        name="Standard_D4s_v3",
        tier="GeneralPurpose",
    ),
    storage=azure_native.dbforpostgresql.StorageArgs(
        storage_size_gb=512,
    ),
    tags={
        "ElasticServer": "1",
    },
    version="12")

```

```yaml
resources:
  server:
    type: azure-native:dbforpostgresql:Server
    properties:
      administratorLogin: cloudsa
      administratorLoginPassword: password
      availabilityZone: '1'
      backup:
        backupRetentionDays: 7
        geoRedundantBackup: Disabled
      createMode: Create
      dataEncryption:
        primaryKeyURI: https://test-kv.vault.azure.net/keys/test-key1/77f57315bab34b0189daa113fbc78787
        primaryUserAssignedIdentityId: /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testresourcegroup/providers/Microsoft.ManagedIdentity/userAssignedIdentities/test-usermanagedidentity
        type: AzureKeyVault
      highAvailability:
        mode: ZoneRedundant
      identity:
        type: UserAssigned
        userAssignedIdentities:
          ? /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testresourcegroup/providers/Microsoft.ManagedIdentity/userAssignedIdentities/test-usermanagedidentity
          : {}
      location: westus
      network:
        delegatedSubnetResourceId: /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/test-vnet-subnet
        privateDnsZoneArmResourceId: /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourcegroups/testrg/providers/Microsoft.Network/privateDnsZones/test-private-dns-zone.postgres.database.azure.com
      resourceGroupName: testrg
      serverName: pgtestsvc4
      sku:
        name: Standard_D4s_v3
        tier: GeneralPurpose
      storage:
        storageSizeGB: 512
      tags:
        ElasticServer: '1'
      version: '12'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:dbforpostgresql:Server pgtestsvc4 /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.DBforPostgreSQL/flexibleServers/pgtestsvc4 
```
