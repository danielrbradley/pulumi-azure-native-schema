Cache details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateCache
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cache = new AzureNative.ApiManagement.Cache("cache", new()
    {
        CacheId = "c1",
        ConnectionString = "apim.redis.cache.windows.net:6380,password=xc,ssl=True,abortConnect=False",
        Description = "Redis cache instances in West India",
        ResourceGroupName = "rg1",
        ResourceId = "https://management.azure.com/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Cache/redis/apimservice1",
        ServiceName = "apimService1",
        UseFromLocation = "default",
    });

});


```

```go
package main

import (
	apimanagement "github.com/pulumi/pulumi-azure-native-sdk/apimanagement"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := apimanagement.NewCache(ctx, "cache", &apimanagement.CacheArgs{
			CacheId:           pulumi.String("c1"),
			ConnectionString:  pulumi.String("apim.redis.cache.windows.net:6380,password=xc,ssl=True,abortConnect=False"),
			Description:       pulumi.String("Redis cache instances in West India"),
			ResourceGroupName: pulumi.String("rg1"),
			ResourceId:        pulumi.String("https://management.azure.com/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Cache/redis/apimservice1"),
			ServiceName:       pulumi.String("apimService1"),
			UseFromLocation:   pulumi.String("default"),
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
import com.pulumi.azurenative.apimanagement.Cache;
import com.pulumi.azurenative.apimanagement.CacheArgs;
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
        var cache = new Cache("cache", CacheArgs.builder()        
            .cacheId("c1")
            .connectionString("apim.redis.cache.windows.net:6380,password=xc,ssl=True,abortConnect=False")
            .description("Redis cache instances in West India")
            .resourceGroupName("rg1")
            .resourceId("https://management.azure.com/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Cache/redis/apimservice1")
            .serviceName("apimService1")
            .useFromLocation("default")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cache = new azure_native.apimanagement.Cache("cache", {
    cacheId: "c1",
    connectionString: "apim.redis.cache.windows.net:6380,password=xc,ssl=True,abortConnect=False",
    description: "Redis cache instances in West India",
    resourceGroupName: "rg1",
    resourceId: "https://management.azure.com/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Cache/redis/apimservice1",
    serviceName: "apimService1",
    useFromLocation: "default",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cache = azure_native.apimanagement.Cache("cache",
    cache_id="c1",
    connection_string="apim.redis.cache.windows.net:6380,password=xc,ssl=True,abortConnect=False",
    description="Redis cache instances in West India",
    resource_group_name="rg1",
    resource_id="https://management.azure.com/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Cache/redis/apimservice1",
    service_name="apimService1",
    use_from_location="default")

```

```yaml
resources:
  cache:
    type: azure-native:apimanagement:Cache
    properties:
      cacheId: c1
      connectionString: apim.redis.cache.windows.net:6380,password=xc,ssl=True,abortConnect=False
      description: Redis cache instances in West India
      resourceGroupName: rg1
      resourceId: https://management.azure.com/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Cache/redis/apimservice1
      serviceName: apimService1
      useFromLocation: default

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:Cache c1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/caches/c1 
```
