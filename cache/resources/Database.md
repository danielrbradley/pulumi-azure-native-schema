Describes a database on the RedisEnterprise cluster
API Version: 2022-01-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### RedisEnterpriseDatabasesCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var database = new AzureNative.Cache.Database("database", new()
    {
        ClientProtocol = "Encrypted",
        ClusterName = "cache1",
        ClusteringPolicy = "EnterpriseCluster",
        DatabaseName = "default",
        EvictionPolicy = "AllKeysLRU",
        Modules = new[]
        {
            new AzureNative.Cache.Inputs.ModuleArgs
            {
                Args = "ERROR_RATE 0.00 INITIAL_SIZE 400",
                Name = "RedisBloom",
            },
            new AzureNative.Cache.Inputs.ModuleArgs
            {
                Args = "RETENTION_POLICY 20",
                Name = "RedisTimeSeries",
            },
            new AzureNative.Cache.Inputs.ModuleArgs
            {
                Name = "RediSearch",
            },
        },
        Persistence = new AzureNative.Cache.Inputs.PersistenceArgs
        {
            AofEnabled = true,
            AofFrequency = "1s",
        },
        Port = 10000,
        ResourceGroupName = "rg1",
    });

});


```

```go
package main

import (
	cache "github.com/pulumi/pulumi-azure-native-sdk/cache"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := cache.NewDatabase(ctx, "database", &cache.DatabaseArgs{
			ClientProtocol:   pulumi.String("Encrypted"),
			ClusterName:      pulumi.String("cache1"),
			ClusteringPolicy: pulumi.String("EnterpriseCluster"),
			DatabaseName:     pulumi.String("default"),
			EvictionPolicy:   pulumi.String("AllKeysLRU"),
			Modules: []cache.ModuleArgs{
				{
					Args: pulumi.String("ERROR_RATE 0.00 INITIAL_SIZE 400"),
					Name: pulumi.String("RedisBloom"),
				},
				{
					Args: pulumi.String("RETENTION_POLICY 20"),
					Name: pulumi.String("RedisTimeSeries"),
				},
				{
					Name: pulumi.String("RediSearch"),
				},
			},
			Persistence: &cache.PersistenceArgs{
				AofEnabled:   pulumi.Bool(true),
				AofFrequency: pulumi.String("1s"),
			},
			Port:              pulumi.Int(10000),
			ResourceGroupName: pulumi.String("rg1"),
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
import com.pulumi.azurenative.cache.Database;
import com.pulumi.azurenative.cache.DatabaseArgs;
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
        var database = new Database("database", DatabaseArgs.builder()        
            .clientProtocol("Encrypted")
            .clusterName("cache1")
            .clusteringPolicy("EnterpriseCluster")
            .databaseName("default")
            .evictionPolicy("AllKeysLRU")
            .modules(            
                Map.ofEntries(
                    Map.entry("args", "ERROR_RATE 0.00 INITIAL_SIZE 400"),
                    Map.entry("name", "RedisBloom")
                ),
                Map.ofEntries(
                    Map.entry("args", "RETENTION_POLICY 20"),
                    Map.entry("name", "RedisTimeSeries")
                ),
                Map.of("name", "RediSearch"))
            .persistence(Map.ofEntries(
                Map.entry("aofEnabled", true),
                Map.entry("aofFrequency", "1s")
            ))
            .port(10000)
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const database = new azure_native.cache.Database("database", {
    clientProtocol: "Encrypted",
    clusterName: "cache1",
    clusteringPolicy: "EnterpriseCluster",
    databaseName: "default",
    evictionPolicy: "AllKeysLRU",
    modules: [
        {
            args: "ERROR_RATE 0.00 INITIAL_SIZE 400",
            name: "RedisBloom",
        },
        {
            args: "RETENTION_POLICY 20",
            name: "RedisTimeSeries",
        },
        {
            name: "RediSearch",
        },
    ],
    persistence: {
        aofEnabled: true,
        aofFrequency: "1s",
    },
    port: 10000,
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

database = azure_native.cache.Database("database",
    client_protocol="Encrypted",
    cluster_name="cache1",
    clustering_policy="EnterpriseCluster",
    database_name="default",
    eviction_policy="AllKeysLRU",
    modules=[
        azure_native.cache.ModuleArgs(
            args="ERROR_RATE 0.00 INITIAL_SIZE 400",
            name="RedisBloom",
        ),
        azure_native.cache.ModuleArgs(
            args="RETENTION_POLICY 20",
            name="RedisTimeSeries",
        ),
        azure_native.cache.ModuleArgs(
            name="RediSearch",
        ),
    ],
    persistence=azure_native.cache.PersistenceArgs(
        aof_enabled=True,
        aof_frequency="1s",
    ),
    port=10000,
    resource_group_name="rg1")

```

```yaml
resources:
  database:
    type: azure-native:cache:Database
    properties:
      clientProtocol: Encrypted
      clusterName: cache1
      clusteringPolicy: EnterpriseCluster
      databaseName: default
      evictionPolicy: AllKeysLRU
      modules:
        - args: ERROR_RATE 0.00 INITIAL_SIZE 400
          name: RedisBloom
        - args: RETENTION_POLICY 20
          name: RedisTimeSeries
        - name: RediSearch
      persistence:
        aofEnabled: true
        aofFrequency: 1s
      port: 10000
      resourceGroupName: rg1

```

{{% /example %}}
{{% example %}}
### RedisEnterpriseDatabasesCreate With Active Geo Replication
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var database = new AzureNative.Cache.Database("database", new()
    {
        ClientProtocol = "Encrypted",
        ClusterName = "cache1",
        ClusteringPolicy = "EnterpriseCluster",
        DatabaseName = "default",
        EvictionPolicy = "NoEviction",
        GeoReplication = new AzureNative.Cache.Inputs.DatabasePropertiesGeoReplicationArgs
        {
            GroupNickname = "groupName",
            LinkedDatabases = new[]
            {
                new AzureNative.Cache.Inputs.LinkedDatabaseArgs
                {
                    Id = "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Cache/redisEnterprise/cache1/databases/default",
                },
                new AzureNative.Cache.Inputs.LinkedDatabaseArgs
                {
                    Id = "/subscriptions/subid2/resourceGroups/rg2/providers/Microsoft.Cache/redisEnterprise/cache2/databases/default",
                },
            },
        },
        Port = 10000,
        ResourceGroupName = "rg1",
    });

});


```

```go
package main

import (
	cache "github.com/pulumi/pulumi-azure-native-sdk/cache"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := cache.NewDatabase(ctx, "database", &cache.DatabaseArgs{
			ClientProtocol:   pulumi.String("Encrypted"),
			ClusterName:      pulumi.String("cache1"),
			ClusteringPolicy: pulumi.String("EnterpriseCluster"),
			DatabaseName:     pulumi.String("default"),
			EvictionPolicy:   pulumi.String("NoEviction"),
			GeoReplication: cache.DatabasePropertiesResponseGeoReplication{
				GroupNickname: pulumi.String("groupName"),
				LinkedDatabases: cache.LinkedDatabaseArray{
					&cache.LinkedDatabaseArgs{
						Id: pulumi.String("/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Cache/redisEnterprise/cache1/databases/default"),
					},
					&cache.LinkedDatabaseArgs{
						Id: pulumi.String("/subscriptions/subid2/resourceGroups/rg2/providers/Microsoft.Cache/redisEnterprise/cache2/databases/default"),
					},
				},
			},
			Port:              pulumi.Int(10000),
			ResourceGroupName: pulumi.String("rg1"),
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
import com.pulumi.azurenative.cache.Database;
import com.pulumi.azurenative.cache.DatabaseArgs;
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
        var database = new Database("database", DatabaseArgs.builder()        
            .clientProtocol("Encrypted")
            .clusterName("cache1")
            .clusteringPolicy("EnterpriseCluster")
            .databaseName("default")
            .evictionPolicy("NoEviction")
            .geoReplication(Map.ofEntries(
                Map.entry("groupNickname", "groupName"),
                Map.entry("linkedDatabases",                 
                    Map.of("id", "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Cache/redisEnterprise/cache1/databases/default"),
                    Map.of("id", "/subscriptions/subid2/resourceGroups/rg2/providers/Microsoft.Cache/redisEnterprise/cache2/databases/default"))
            ))
            .port(10000)
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const database = new azure_native.cache.Database("database", {
    clientProtocol: "Encrypted",
    clusterName: "cache1",
    clusteringPolicy: "EnterpriseCluster",
    databaseName: "default",
    evictionPolicy: "NoEviction",
    geoReplication: {
        groupNickname: "groupName",
        linkedDatabases: [
            {
                id: "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Cache/redisEnterprise/cache1/databases/default",
            },
            {
                id: "/subscriptions/subid2/resourceGroups/rg2/providers/Microsoft.Cache/redisEnterprise/cache2/databases/default",
            },
        ],
    },
    port: 10000,
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

database = azure_native.cache.Database("database",
    client_protocol="Encrypted",
    cluster_name="cache1",
    clustering_policy="EnterpriseCluster",
    database_name="default",
    eviction_policy="NoEviction",
    geo_replication=azure_native.cache.DatabasePropertiesResponseGeoReplicationArgs(
        group_nickname="groupName",
        linked_databases=[
            azure_native.cache.LinkedDatabaseArgs(
                id="/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Cache/redisEnterprise/cache1/databases/default",
            ),
            azure_native.cache.LinkedDatabaseArgs(
                id="/subscriptions/subid2/resourceGroups/rg2/providers/Microsoft.Cache/redisEnterprise/cache2/databases/default",
            ),
        ],
    ),
    port=10000,
    resource_group_name="rg1")

```

```yaml
resources:
  database:
    type: azure-native:cache:Database
    properties:
      clientProtocol: Encrypted
      clusterName: cache1
      clusteringPolicy: EnterpriseCluster
      databaseName: default
      evictionPolicy: NoEviction
      geoReplication:
        groupNickname: groupName
        linkedDatabases:
          - id: /subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Cache/redisEnterprise/cache1/databases/default
          - id: /subscriptions/subid2/resourceGroups/rg2/providers/Microsoft.Cache/redisEnterprise/cache2/databases/default
      port: 10000
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:cache:Database cache1/default /subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Cache/redisEnterprise/cache1/databases/default 
```
