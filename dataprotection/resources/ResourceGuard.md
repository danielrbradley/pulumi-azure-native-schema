
API Version: 2023-01-01.
Previous API Version: 2021-10-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create ResourceGuard
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var resourceGuard = new AzureNative.DataProtection.ResourceGuard("resourceGuard", new()
    {
        Location = "WestUS",
        ResourceGroupName = "SampleResourceGroup",
        ResourceGuardsName = "swaggerExample",
        Tags = 
        {
            { "key1", "val1" },
        },
    });

});


```

```go
package main

import (
	dataprotection "github.com/pulumi/pulumi-azure-native-sdk/dataprotection"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := dataprotection.NewResourceGuard(ctx, "resourceGuard", &dataprotection.ResourceGuardArgs{
			Location:           pulumi.String("WestUS"),
			ResourceGroupName:  pulumi.String("SampleResourceGroup"),
			ResourceGuardsName: pulumi.String("swaggerExample"),
			Tags: pulumi.StringMap{
				"key1": pulumi.String("val1"),
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
import com.pulumi.azurenative.dataprotection.ResourceGuard;
import com.pulumi.azurenative.dataprotection.ResourceGuardArgs;
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
        var resourceGuard = new ResourceGuard("resourceGuard", ResourceGuardArgs.builder()        
            .location("WestUS")
            .resourceGroupName("SampleResourceGroup")
            .resourceGuardsName("swaggerExample")
            .tags(Map.of("key1", "val1"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const resourceGuard = new azure_native.dataprotection.ResourceGuard("resourceGuard", {
    location: "WestUS",
    resourceGroupName: "SampleResourceGroup",
    resourceGuardsName: "swaggerExample",
    tags: {
        key1: "val1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

resource_guard = azure_native.dataprotection.ResourceGuard("resourceGuard",
    location="WestUS",
    resource_group_name="SampleResourceGroup",
    resource_guards_name="swaggerExample",
    tags={
        "key1": "val1",
    })

```

```yaml
resources:
  resourceGuard:
    type: azure-native:dataprotection:ResourceGuard
    properties:
      location: WestUS
      resourceGroupName: SampleResourceGroup
      resourceGuardsName: swaggerExample
      tags:
        key1: val1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:dataprotection:ResourceGuard VaultGuardTestNew /subscriptions/c999d45b-944f-418c-a0d8-c3fcfd1802c8/resourceGroups/vaultguardRGNew/providers/Microsoft.DataProtection/resourceGuards/VaultGuardTestNew 
```
