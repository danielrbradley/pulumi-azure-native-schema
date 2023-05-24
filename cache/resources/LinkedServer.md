Response to put/get linked server (with properties) for Redis cache.
API Version: 2022-06-01.
Previous API Version: 2020-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### LinkedServer_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var linkedServer = new AzureNative.Cache.LinkedServer("linkedServer", new()
    {
        LinkedRedisCacheId = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Cache/Redis/cache2",
        LinkedRedisCacheLocation = "West US",
        LinkedServerName = "cache2",
        Name = "cache1",
        ResourceGroupName = "rg1",
        ServerRole = AzureNative.Cache.ReplicationRole.Secondary,
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
		_, err := cache.NewLinkedServer(ctx, "linkedServer", &cache.LinkedServerArgs{
			LinkedRedisCacheId:       pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Cache/Redis/cache2"),
			LinkedRedisCacheLocation: pulumi.String("West US"),
			LinkedServerName:         pulumi.String("cache2"),
			Name:                     pulumi.String("cache1"),
			ResourceGroupName:        pulumi.String("rg1"),
			ServerRole:               cache.ReplicationRoleSecondary,
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
import com.pulumi.azurenative.cache.LinkedServer;
import com.pulumi.azurenative.cache.LinkedServerArgs;
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
        var linkedServer = new LinkedServer("linkedServer", LinkedServerArgs.builder()        
            .linkedRedisCacheId("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Cache/Redis/cache2")
            .linkedRedisCacheLocation("West US")
            .linkedServerName("cache2")
            .name("cache1")
            .resourceGroupName("rg1")
            .serverRole("Secondary")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const linkedServer = new azure_native.cache.LinkedServer("linkedServer", {
    linkedRedisCacheId: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Cache/Redis/cache2",
    linkedRedisCacheLocation: "West US",
    linkedServerName: "cache2",
    name: "cache1",
    resourceGroupName: "rg1",
    serverRole: azure_native.cache.ReplicationRole.Secondary,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

linked_server = azure_native.cache.LinkedServer("linkedServer",
    linked_redis_cache_id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Cache/Redis/cache2",
    linked_redis_cache_location="West US",
    linked_server_name="cache2",
    name="cache1",
    resource_group_name="rg1",
    server_role=azure_native.cache.ReplicationRole.SECONDARY)

```

```yaml
resources:
  linkedServer:
    type: azure-native:cache:LinkedServer
    properties:
      linkedRedisCacheId: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Cache/Redis/cache2
      linkedRedisCacheLocation: West US
      linkedServerName: cache2
      name: cache1
      resourceGroupName: rg1
      serverRole: Secondary

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:cache:LinkedServer cache2 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Cache/Redis/cache1/linkedServers/cache2 
```
