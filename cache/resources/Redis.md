A single Redis item in List or Get Operation.
API Version: 2022-06-01.
Previous API Version: 2020-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### RedisCacheCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var redis = new AzureNative.Cache.Redis("redis", new()
    {
        EnableNonSslPort = true,
        Location = "West US",
        MinimumTlsVersion = "1.2",
        Name = "cache1",
        RedisConfiguration = new AzureNative.Cache.Inputs.RedisCommonPropertiesRedisConfigurationArgs
        {
            MaxmemoryPolicy = "allkeys-lru",
        },
        RedisVersion = "4",
        ReplicasPerPrimary = 2,
        ResourceGroupName = "rg1",
        ShardCount = 2,
        Sku = new AzureNative.Cache.Inputs.SkuArgs
        {
            Capacity = 1,
            Family = "P",
            Name = "Premium",
        },
        StaticIP = "192.168.0.5",
        SubnetId = "/subscriptions/subid/resourceGroups/rg2/providers/Microsoft.Network/virtualNetworks/network1/subnets/subnet1",
        Zones = new[]
        {
            "1",
        },
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
		_, err := cache.NewRedis(ctx, "redis", &cache.RedisArgs{
			EnableNonSslPort:  pulumi.Bool(true),
			Location:          pulumi.String("West US"),
			MinimumTlsVersion: pulumi.String("1.2"),
			Name:              pulumi.String("cache1"),
			RedisConfiguration: &cache.RedisCommonPropertiesRedisConfigurationArgs{
				MaxmemoryPolicy: pulumi.String("allkeys-lru"),
			},
			RedisVersion:       pulumi.String("4"),
			ReplicasPerPrimary: pulumi.Int(2),
			ResourceGroupName:  pulumi.String("rg1"),
			ShardCount:         pulumi.Int(2),
			Sku: &cache.SkuArgs{
				Capacity: pulumi.Int(1),
				Family:   pulumi.String("P"),
				Name:     pulumi.String("Premium"),
			},
			StaticIP: pulumi.String("192.168.0.5"),
			SubnetId: pulumi.String("/subscriptions/subid/resourceGroups/rg2/providers/Microsoft.Network/virtualNetworks/network1/subnets/subnet1"),
			Zones: pulumi.StringArray{
				pulumi.String("1"),
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
import com.pulumi.azurenative.cache.Redis;
import com.pulumi.azurenative.cache.RedisArgs;
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
        var redis = new Redis("redis", RedisArgs.builder()        
            .enableNonSslPort(true)
            .location("West US")
            .minimumTlsVersion("1.2")
            .name("cache1")
            .redisConfiguration(Map.of("maxmemoryPolicy", "allkeys-lru"))
            .redisVersion("4")
            .replicasPerPrimary(2)
            .resourceGroupName("rg1")
            .shardCount(2)
            .sku(Map.ofEntries(
                Map.entry("capacity", 1),
                Map.entry("family", "P"),
                Map.entry("name", "Premium")
            ))
            .staticIP("192.168.0.5")
            .subnetId("/subscriptions/subid/resourceGroups/rg2/providers/Microsoft.Network/virtualNetworks/network1/subnets/subnet1")
            .zones("1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const redis = new azure_native.cache.Redis("redis", {
    enableNonSslPort: true,
    location: "West US",
    minimumTlsVersion: "1.2",
    name: "cache1",
    redisConfiguration: {
        maxmemoryPolicy: "allkeys-lru",
    },
    redisVersion: "4",
    replicasPerPrimary: 2,
    resourceGroupName: "rg1",
    shardCount: 2,
    sku: {
        capacity: 1,
        family: "P",
        name: "Premium",
    },
    staticIP: "192.168.0.5",
    subnetId: "/subscriptions/subid/resourceGroups/rg2/providers/Microsoft.Network/virtualNetworks/network1/subnets/subnet1",
    zones: ["1"],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

redis = azure_native.cache.Redis("redis",
    enable_non_ssl_port=True,
    location="West US",
    minimum_tls_version="1.2",
    name="cache1",
    redis_configuration=azure_native.cache.RedisCommonPropertiesRedisConfigurationArgs(
        maxmemory_policy="allkeys-lru",
    ),
    redis_version="4",
    replicas_per_primary=2,
    resource_group_name="rg1",
    shard_count=2,
    sku=azure_native.cache.SkuArgs(
        capacity=1,
        family="P",
        name="Premium",
    ),
    static_ip="192.168.0.5",
    subnet_id="/subscriptions/subid/resourceGroups/rg2/providers/Microsoft.Network/virtualNetworks/network1/subnets/subnet1",
    zones=["1"])

```

```yaml
resources:
  redis:
    type: azure-native:cache:Redis
    properties:
      enableNonSslPort: true
      location: West US
      minimumTlsVersion: '1.2'
      name: cache1
      redisConfiguration:
        maxmemoryPolicy: allkeys-lru
      redisVersion: '4'
      replicasPerPrimary: 2
      resourceGroupName: rg1
      shardCount: 2
      sku:
        capacity: 1
        family: P
        name: Premium
      staticIP: 192.168.0.5
      subnetId: /subscriptions/subid/resourceGroups/rg2/providers/Microsoft.Network/virtualNetworks/network1/subnets/subnet1
      zones:
        - '1'

```

{{% /example %}}
{{% example %}}
### RedisCacheCreateDefaultVersion
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var redis = new AzureNative.Cache.Redis("redis", new()
    {
        EnableNonSslPort = true,
        Location = "West US",
        MinimumTlsVersion = "1.2",
        Name = "cache1",
        RedisConfiguration = new AzureNative.Cache.Inputs.RedisCommonPropertiesRedisConfigurationArgs
        {
            MaxmemoryPolicy = "allkeys-lru",
        },
        ReplicasPerPrimary = 2,
        ResourceGroupName = "rg1",
        ShardCount = 2,
        Sku = new AzureNative.Cache.Inputs.SkuArgs
        {
            Capacity = 1,
            Family = "P",
            Name = "Premium",
        },
        StaticIP = "192.168.0.5",
        SubnetId = "/subscriptions/subid/resourceGroups/rg2/providers/Microsoft.Network/virtualNetworks/network1/subnets/subnet1",
        Zones = new[]
        {
            "1",
        },
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
		_, err := cache.NewRedis(ctx, "redis", &cache.RedisArgs{
			EnableNonSslPort:  pulumi.Bool(true),
			Location:          pulumi.String("West US"),
			MinimumTlsVersion: pulumi.String("1.2"),
			Name:              pulumi.String("cache1"),
			RedisConfiguration: &cache.RedisCommonPropertiesRedisConfigurationArgs{
				MaxmemoryPolicy: pulumi.String("allkeys-lru"),
			},
			ReplicasPerPrimary: pulumi.Int(2),
			ResourceGroupName:  pulumi.String("rg1"),
			ShardCount:         pulumi.Int(2),
			Sku: &cache.SkuArgs{
				Capacity: pulumi.Int(1),
				Family:   pulumi.String("P"),
				Name:     pulumi.String("Premium"),
			},
			StaticIP: pulumi.String("192.168.0.5"),
			SubnetId: pulumi.String("/subscriptions/subid/resourceGroups/rg2/providers/Microsoft.Network/virtualNetworks/network1/subnets/subnet1"),
			Zones: pulumi.StringArray{
				pulumi.String("1"),
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
import com.pulumi.azurenative.cache.Redis;
import com.pulumi.azurenative.cache.RedisArgs;
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
        var redis = new Redis("redis", RedisArgs.builder()        
            .enableNonSslPort(true)
            .location("West US")
            .minimumTlsVersion("1.2")
            .name("cache1")
            .redisConfiguration(Map.of("maxmemoryPolicy", "allkeys-lru"))
            .replicasPerPrimary(2)
            .resourceGroupName("rg1")
            .shardCount(2)
            .sku(Map.ofEntries(
                Map.entry("capacity", 1),
                Map.entry("family", "P"),
                Map.entry("name", "Premium")
            ))
            .staticIP("192.168.0.5")
            .subnetId("/subscriptions/subid/resourceGroups/rg2/providers/Microsoft.Network/virtualNetworks/network1/subnets/subnet1")
            .zones("1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const redis = new azure_native.cache.Redis("redis", {
    enableNonSslPort: true,
    location: "West US",
    minimumTlsVersion: "1.2",
    name: "cache1",
    redisConfiguration: {
        maxmemoryPolicy: "allkeys-lru",
    },
    replicasPerPrimary: 2,
    resourceGroupName: "rg1",
    shardCount: 2,
    sku: {
        capacity: 1,
        family: "P",
        name: "Premium",
    },
    staticIP: "192.168.0.5",
    subnetId: "/subscriptions/subid/resourceGroups/rg2/providers/Microsoft.Network/virtualNetworks/network1/subnets/subnet1",
    zones: ["1"],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

redis = azure_native.cache.Redis("redis",
    enable_non_ssl_port=True,
    location="West US",
    minimum_tls_version="1.2",
    name="cache1",
    redis_configuration=azure_native.cache.RedisCommonPropertiesRedisConfigurationArgs(
        maxmemory_policy="allkeys-lru",
    ),
    replicas_per_primary=2,
    resource_group_name="rg1",
    shard_count=2,
    sku=azure_native.cache.SkuArgs(
        capacity=1,
        family="P",
        name="Premium",
    ),
    static_ip="192.168.0.5",
    subnet_id="/subscriptions/subid/resourceGroups/rg2/providers/Microsoft.Network/virtualNetworks/network1/subnets/subnet1",
    zones=["1"])

```

```yaml
resources:
  redis:
    type: azure-native:cache:Redis
    properties:
      enableNonSslPort: true
      location: West US
      minimumTlsVersion: '1.2'
      name: cache1
      redisConfiguration:
        maxmemoryPolicy: allkeys-lru
      replicasPerPrimary: 2
      resourceGroupName: rg1
      shardCount: 2
      sku:
        capacity: 1
        family: P
        name: Premium
      staticIP: 192.168.0.5
      subnetId: /subscriptions/subid/resourceGroups/rg2/providers/Microsoft.Network/virtualNetworks/network1/subnets/subnet1
      zones:
        - '1'

```

{{% /example %}}
{{% example %}}
### RedisCacheCreateLatestVersion
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var redis = new AzureNative.Cache.Redis("redis", new()
    {
        EnableNonSslPort = true,
        Location = "West US",
        MinimumTlsVersion = "1.2",
        Name = "cache1",
        RedisConfiguration = new AzureNative.Cache.Inputs.RedisCommonPropertiesRedisConfigurationArgs
        {
            MaxmemoryPolicy = "allkeys-lru",
        },
        RedisVersion = "Latest",
        ReplicasPerPrimary = 2,
        ResourceGroupName = "rg1",
        ShardCount = 2,
        Sku = new AzureNative.Cache.Inputs.SkuArgs
        {
            Capacity = 1,
            Family = "P",
            Name = "Premium",
        },
        StaticIP = "192.168.0.5",
        SubnetId = "/subscriptions/subid/resourceGroups/rg2/providers/Microsoft.Network/virtualNetworks/network1/subnets/subnet1",
        Zones = new[]
        {
            "1",
        },
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
		_, err := cache.NewRedis(ctx, "redis", &cache.RedisArgs{
			EnableNonSslPort:  pulumi.Bool(true),
			Location:          pulumi.String("West US"),
			MinimumTlsVersion: pulumi.String("1.2"),
			Name:              pulumi.String("cache1"),
			RedisConfiguration: &cache.RedisCommonPropertiesRedisConfigurationArgs{
				MaxmemoryPolicy: pulumi.String("allkeys-lru"),
			},
			RedisVersion:       pulumi.String("Latest"),
			ReplicasPerPrimary: pulumi.Int(2),
			ResourceGroupName:  pulumi.String("rg1"),
			ShardCount:         pulumi.Int(2),
			Sku: &cache.SkuArgs{
				Capacity: pulumi.Int(1),
				Family:   pulumi.String("P"),
				Name:     pulumi.String("Premium"),
			},
			StaticIP: pulumi.String("192.168.0.5"),
			SubnetId: pulumi.String("/subscriptions/subid/resourceGroups/rg2/providers/Microsoft.Network/virtualNetworks/network1/subnets/subnet1"),
			Zones: pulumi.StringArray{
				pulumi.String("1"),
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
import com.pulumi.azurenative.cache.Redis;
import com.pulumi.azurenative.cache.RedisArgs;
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
        var redis = new Redis("redis", RedisArgs.builder()        
            .enableNonSslPort(true)
            .location("West US")
            .minimumTlsVersion("1.2")
            .name("cache1")
            .redisConfiguration(Map.of("maxmemoryPolicy", "allkeys-lru"))
            .redisVersion("Latest")
            .replicasPerPrimary(2)
            .resourceGroupName("rg1")
            .shardCount(2)
            .sku(Map.ofEntries(
                Map.entry("capacity", 1),
                Map.entry("family", "P"),
                Map.entry("name", "Premium")
            ))
            .staticIP("192.168.0.5")
            .subnetId("/subscriptions/subid/resourceGroups/rg2/providers/Microsoft.Network/virtualNetworks/network1/subnets/subnet1")
            .zones("1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const redis = new azure_native.cache.Redis("redis", {
    enableNonSslPort: true,
    location: "West US",
    minimumTlsVersion: "1.2",
    name: "cache1",
    redisConfiguration: {
        maxmemoryPolicy: "allkeys-lru",
    },
    redisVersion: "Latest",
    replicasPerPrimary: 2,
    resourceGroupName: "rg1",
    shardCount: 2,
    sku: {
        capacity: 1,
        family: "P",
        name: "Premium",
    },
    staticIP: "192.168.0.5",
    subnetId: "/subscriptions/subid/resourceGroups/rg2/providers/Microsoft.Network/virtualNetworks/network1/subnets/subnet1",
    zones: ["1"],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

redis = azure_native.cache.Redis("redis",
    enable_non_ssl_port=True,
    location="West US",
    minimum_tls_version="1.2",
    name="cache1",
    redis_configuration=azure_native.cache.RedisCommonPropertiesRedisConfigurationArgs(
        maxmemory_policy="allkeys-lru",
    ),
    redis_version="Latest",
    replicas_per_primary=2,
    resource_group_name="rg1",
    shard_count=2,
    sku=azure_native.cache.SkuArgs(
        capacity=1,
        family="P",
        name="Premium",
    ),
    static_ip="192.168.0.5",
    subnet_id="/subscriptions/subid/resourceGroups/rg2/providers/Microsoft.Network/virtualNetworks/network1/subnets/subnet1",
    zones=["1"])

```

```yaml
resources:
  redis:
    type: azure-native:cache:Redis
    properties:
      enableNonSslPort: true
      location: West US
      minimumTlsVersion: '1.2'
      name: cache1
      redisConfiguration:
        maxmemoryPolicy: allkeys-lru
      redisVersion: Latest
      replicasPerPrimary: 2
      resourceGroupName: rg1
      shardCount: 2
      sku:
        capacity: 1
        family: P
        name: Premium
      staticIP: 192.168.0.5
      subnetId: /subscriptions/subid/resourceGroups/rg2/providers/Microsoft.Network/virtualNetworks/network1/subnets/subnet1
      zones:
        - '1'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:cache:Redis cache1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Cache/Redis/cache1 
```
