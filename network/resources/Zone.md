Describes a DNS zone.
API Version: 2018-05-01.
Previous API Version: 2018-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create zone
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var zone = new AzureNative.Network.Zone("zone", new()
    {
        Location = "Global",
        ResourceGroupName = "rg1",
        Tags = 
        {
            { "key1", "value1" },
        },
        ZoneName = "zone1",
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
		_, err := network.NewZone(ctx, "zone", &network.ZoneArgs{
			Location:          pulumi.String("Global"),
			ResourceGroupName: pulumi.String("rg1"),
			Tags: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			ZoneName: pulumi.String("zone1"),
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
import com.pulumi.azurenative.network.Zone;
import com.pulumi.azurenative.network.ZoneArgs;
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
        var zone = new Zone("zone", ZoneArgs.builder()        
            .location("Global")
            .resourceGroupName("rg1")
            .tags(Map.of("key1", "value1"))
            .zoneName("zone1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const zone = new azure_native.network.Zone("zone", {
    location: "Global",
    resourceGroupName: "rg1",
    tags: {
        key1: "value1",
    },
    zoneName: "zone1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

zone = azure_native.network.Zone("zone",
    location="Global",
    resource_group_name="rg1",
    tags={
        "key1": "value1",
    },
    zone_name="zone1")

```

```yaml
resources:
  zone:
    type: azure-native:network:Zone
    properties:
      location: Global
      resourceGroupName: rg1
      tags:
        key1: value1
      zoneName: zone1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:Zone zone1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/dnsZones/zone1 
```
