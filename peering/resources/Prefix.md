The peering service prefix class.
API Version: 2022-10-01.
Previous API Version: 2021-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a prefix for the peering service
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var prefix = new AzureNative.Peering.Prefix("prefix", new()
    {
        PeeringServiceName = "peeringServiceName",
        PeeringServicePrefixKey = "00000000-0000-0000-0000-000000000000",
        Prefix = "192.168.1.0/24",
        PrefixName = "peeringServicePrefixName",
        ResourceGroupName = "rgName",
    });

});


```

```go
package main

import (
	peering "github.com/pulumi/pulumi-azure-native-sdk/peering"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := peering.NewPrefix(ctx, "prefix", &peering.PrefixArgs{
			PeeringServiceName:      pulumi.String("peeringServiceName"),
			PeeringServicePrefixKey: pulumi.String("00000000-0000-0000-0000-000000000000"),
			Prefix:                  pulumi.String("192.168.1.0/24"),
			PrefixName:              pulumi.String("peeringServicePrefixName"),
			ResourceGroupName:       pulumi.String("rgName"),
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
import com.pulumi.azurenative.peering.Prefix;
import com.pulumi.azurenative.peering.PrefixArgs;
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
        var prefix = new Prefix("prefix", PrefixArgs.builder()        
            .peeringServiceName("peeringServiceName")
            .peeringServicePrefixKey("00000000-0000-0000-0000-000000000000")
            .prefix("192.168.1.0/24")
            .prefixName("peeringServicePrefixName")
            .resourceGroupName("rgName")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const prefix = new azure_native.peering.Prefix("prefix", {
    peeringServiceName: "peeringServiceName",
    peeringServicePrefixKey: "00000000-0000-0000-0000-000000000000",
    prefix: "192.168.1.0/24",
    prefixName: "peeringServicePrefixName",
    resourceGroupName: "rgName",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

prefix = azure_native.peering.Prefix("prefix",
    peering_service_name="peeringServiceName",
    peering_service_prefix_key="00000000-0000-0000-0000-000000000000",
    prefix="192.168.1.0/24",
    prefix_name="peeringServicePrefixName",
    resource_group_name="rgName")

```

```yaml
resources:
  prefix:
    type: azure-native:peering:Prefix
    properties:
      peeringServiceName: peeringServiceName
      peeringServicePrefixKey: 00000000-0000-0000-0000-000000000000
      prefix: 192.168.1.0/24
      prefixName: peeringServicePrefixName
      resourceGroupName: rgName

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:peering:Prefix peeringServicePrefixName /subscriptions/subId/resourceGroups/rgName/providers/Microsoft.Peering/peeringServices/peeringServiceName/prefixes/peeringServicePrefixName 
```
