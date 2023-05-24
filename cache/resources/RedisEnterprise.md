Describes the RedisEnterprise cluster
API Version: 2022-01-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### RedisEnterpriseCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var redisEnterprise = new AzureNative.Cache.RedisEnterprise("redisEnterprise", new()
    {
        ClusterName = "cache1",
        Location = "West US",
        MinimumTlsVersion = "1.2",
        ResourceGroupName = "rg1",
        Sku = new AzureNative.Cache.Inputs.EnterpriseSkuArgs
        {
            Capacity = 3,
            Name = "EnterpriseFlash_F300",
        },
        Tags = 
        {
            { "tag1", "value1" },
        },
        Zones = new[]
        {
            "1",
            "2",
            "3",
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
		_, err := cache.NewRedisEnterprise(ctx, "redisEnterprise", &cache.RedisEnterpriseArgs{
			ClusterName:       pulumi.String("cache1"),
			Location:          pulumi.String("West US"),
			MinimumTlsVersion: pulumi.String("1.2"),
			ResourceGroupName: pulumi.String("rg1"),
			Sku: &cache.EnterpriseSkuArgs{
				Capacity: pulumi.Int(3),
				Name:     pulumi.String("EnterpriseFlash_F300"),
			},
			Tags: pulumi.StringMap{
				"tag1": pulumi.String("value1"),
			},
			Zones: pulumi.StringArray{
				pulumi.String("1"),
				pulumi.String("2"),
				pulumi.String("3"),
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
import com.pulumi.azurenative.cache.RedisEnterprise;
import com.pulumi.azurenative.cache.RedisEnterpriseArgs;
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
        var redisEnterprise = new RedisEnterprise("redisEnterprise", RedisEnterpriseArgs.builder()        
            .clusterName("cache1")
            .location("West US")
            .minimumTlsVersion("1.2")
            .resourceGroupName("rg1")
            .sku(Map.ofEntries(
                Map.entry("capacity", 3),
                Map.entry("name", "EnterpriseFlash_F300")
            ))
            .tags(Map.of("tag1", "value1"))
            .zones(            
                "1",
                "2",
                "3")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const redisEnterprise = new azure_native.cache.RedisEnterprise("redisEnterprise", {
    clusterName: "cache1",
    location: "West US",
    minimumTlsVersion: "1.2",
    resourceGroupName: "rg1",
    sku: {
        capacity: 3,
        name: "EnterpriseFlash_F300",
    },
    tags: {
        tag1: "value1",
    },
    zones: [
        "1",
        "2",
        "3",
    ],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

redis_enterprise = azure_native.cache.RedisEnterprise("redisEnterprise",
    cluster_name="cache1",
    location="West US",
    minimum_tls_version="1.2",
    resource_group_name="rg1",
    sku=azure_native.cache.EnterpriseSkuArgs(
        capacity=3,
        name="EnterpriseFlash_F300",
    ),
    tags={
        "tag1": "value1",
    },
    zones=[
        "1",
        "2",
        "3",
    ])

```

```yaml
resources:
  redisEnterprise:
    type: azure-native:cache:RedisEnterprise
    properties:
      clusterName: cache1
      location: West US
      minimumTlsVersion: '1.2'
      resourceGroupName: rg1
      sku:
        capacity: 3
        name: EnterpriseFlash_F300
      tags:
        tag1: value1
      zones:
        - '1'
        - '2'
        - '3'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:cache:RedisEnterprise cache1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Cache/redisEnterprise/cache1 
```
