The Private Endpoint Connection resource.
API Version: 2022-06-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### RedisCachePutPrivateEndpointConnection
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnection = new AzureNative.Cache.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        CacheName = "cachetest01",
        PrivateEndpointConnectionName = "pectest01",
        PrivateLinkServiceConnectionState = new AzureNative.Cache.Inputs.PrivateLinkServiceConnectionStateArgs
        {
            Description = "Auto-Approved",
            Status = "Approved",
        },
        ResourceGroupName = "rgtest01",
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
		_, err := cache.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &cache.PrivateEndpointConnectionArgs{
			CacheName:                     pulumi.String("cachetest01"),
			PrivateEndpointConnectionName: pulumi.String("pectest01"),
			PrivateLinkServiceConnectionState: &cache.PrivateLinkServiceConnectionStateArgs{
				Description: pulumi.String("Auto-Approved"),
				Status:      pulumi.String("Approved"),
			},
			ResourceGroupName: pulumi.String("rgtest01"),
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
import com.pulumi.azurenative.cache.PrivateEndpointConnection;
import com.pulumi.azurenative.cache.PrivateEndpointConnectionArgs;
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
        var privateEndpointConnection = new PrivateEndpointConnection("privateEndpointConnection", PrivateEndpointConnectionArgs.builder()        
            .cacheName("cachetest01")
            .privateEndpointConnectionName("pectest01")
            .privateLinkServiceConnectionState(Map.ofEntries(
                Map.entry("description", "Auto-Approved"),
                Map.entry("status", "Approved")
            ))
            .resourceGroupName("rgtest01")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.cache.PrivateEndpointConnection("privateEndpointConnection", {
    cacheName: "cachetest01",
    privateEndpointConnectionName: "pectest01",
    privateLinkServiceConnectionState: {
        description: "Auto-Approved",
        status: "Approved",
    },
    resourceGroupName: "rgtest01",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.cache.PrivateEndpointConnection("privateEndpointConnection",
    cache_name="cachetest01",
    private_endpoint_connection_name="pectest01",
    private_link_service_connection_state=azure_native.cache.PrivateLinkServiceConnectionStateArgs(
        description="Auto-Approved",
        status="Approved",
    ),
    resource_group_name="rgtest01")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:cache:PrivateEndpointConnection
    properties:
      cacheName: cachetest01
      privateEndpointConnectionName: pectest01
      privateLinkServiceConnectionState:
        description: Auto-Approved
        status: Approved
      resourceGroupName: rgtest01

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:cache:PrivateEndpointConnection pectest01 /subscriptions/{subscriptionId}/resourceGroups/rgtest01/providers/Microsoft.Cache/Redis/cachetest01/privateEndpointConnections/pectest01 
```
