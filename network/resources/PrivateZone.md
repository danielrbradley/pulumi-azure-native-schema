Describes a Private DNS zone.
API Version: 2020-06-01.
Previous API Version: 2020-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PUT Private DNS Zone
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateZone = new AzureNative.Network.PrivateZone("privateZone", new()
    {
        Location = "Global",
        PrivateZoneName = "privatezone1.com",
        ResourceGroupName = "resourceGroup1",
        Tags = 
        {
            { "key1", "value1" },
        },
    });

});


```

```go
package main

import (
	network "github.com/pulumi/pulumi-azure-native-sdk/network"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := network.NewPrivateZone(ctx, "privateZone", &network.PrivateZoneArgs{
			Location:          pulumi.String("Global"),
			PrivateZoneName:   pulumi.String("privatezone1.com"),
			ResourceGroupName: pulumi.String("resourceGroup1"),
			Tags: pulumi.StringMap{
				"key1": pulumi.String("value1"),
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
import com.pulumi.azurenative.network.PrivateZone;
import com.pulumi.azurenative.network.PrivateZoneArgs;
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
        var privateZone = new PrivateZone("privateZone", PrivateZoneArgs.builder()        
            .location("Global")
            .privateZoneName("privatezone1.com")
            .resourceGroupName("resourceGroup1")
            .tags(Map.of("key1", "value1"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateZone = new azure_native.network.PrivateZone("privateZone", {
    location: "Global",
    privateZoneName: "privatezone1.com",
    resourceGroupName: "resourceGroup1",
    tags: {
        key1: "value1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_zone = azure_native.network.PrivateZone("privateZone",
    location="Global",
    private_zone_name="privatezone1.com",
    resource_group_name="resourceGroup1",
    tags={
        "key1": "value1",
    })

```

```yaml
resources:
  privateZone:
    type: azure-native:network:PrivateZone
    properties:
      location: Global
      privateZoneName: privatezone1.com
      resourceGroupName: resourceGroup1
      tags:
        key1: value1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:PrivateZone privatezone1.com /subscriptions/subscriptionId/resourceGroups/resourceGroup1/providers/Microsoft.Network/privateDnsZones/privatezone1.com 
```
