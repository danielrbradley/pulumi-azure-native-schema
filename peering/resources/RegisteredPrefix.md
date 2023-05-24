The customer's prefix that is registered by the peering service provider.
API Version: 2022-10-01.
Previous API Version: 2021-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a registered prefix for the peering
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var registeredPrefix = new AzureNative.Peering.RegisteredPrefix("registeredPrefix", new()
    {
        PeeringName = "peeringName",
        Prefix = "10.22.20.0/24",
        RegisteredPrefixName = "registeredPrefixName",
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
		_, err := peering.NewRegisteredPrefix(ctx, "registeredPrefix", &peering.RegisteredPrefixArgs{
			PeeringName:          pulumi.String("peeringName"),
			Prefix:               pulumi.String("10.22.20.0/24"),
			RegisteredPrefixName: pulumi.String("registeredPrefixName"),
			ResourceGroupName:    pulumi.String("rgName"),
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
import com.pulumi.azurenative.peering.RegisteredPrefix;
import com.pulumi.azurenative.peering.RegisteredPrefixArgs;
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
        var registeredPrefix = new RegisteredPrefix("registeredPrefix", RegisteredPrefixArgs.builder()        
            .peeringName("peeringName")
            .prefix("10.22.20.0/24")
            .registeredPrefixName("registeredPrefixName")
            .resourceGroupName("rgName")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const registeredPrefix = new azure_native.peering.RegisteredPrefix("registeredPrefix", {
    peeringName: "peeringName",
    prefix: "10.22.20.0/24",
    registeredPrefixName: "registeredPrefixName",
    resourceGroupName: "rgName",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

registered_prefix = azure_native.peering.RegisteredPrefix("registeredPrefix",
    peering_name="peeringName",
    prefix="10.22.20.0/24",
    registered_prefix_name="registeredPrefixName",
    resource_group_name="rgName")

```

```yaml
resources:
  registeredPrefix:
    type: azure-native:peering:RegisteredPrefix
    properties:
      peeringName: peeringName
      prefix: 10.22.20.0/24
      registeredPrefixName: registeredPrefixName
      resourceGroupName: rgName

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:peering:RegisteredPrefix registeredPrefixName /subscriptions/subId/resourceGroups/rgName/providers/Microsoft.Peering/peerings/peeringName/registeredPrefixes/registeredPrefixName 
```
