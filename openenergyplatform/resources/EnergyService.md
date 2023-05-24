
API Version: 2022-04-04-preview.
Previous API Version: 2022-04-04-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### OepResource_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var energyService = new AzureNative.OpenEnergyPlatform.EnergyService("energyService", new()
    {
        ResourceGroupName = "DummyResourceGroupName",
        ResourceName = "DummyResourceName",
    });

});


```

```go
package main

import (
	openenergyplatform "github.com/pulumi/pulumi-azure-native-sdk/openenergyplatform"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := openenergyplatform.NewEnergyService(ctx, "energyService", &openenergyplatform.EnergyServiceArgs{
			ResourceGroupName: pulumi.String("DummyResourceGroupName"),
			ResourceName:      pulumi.String("DummyResourceName"),
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
import com.pulumi.azurenative.openenergyplatform.EnergyService;
import com.pulumi.azurenative.openenergyplatform.EnergyServiceArgs;
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
        var energyService = new EnergyService("energyService", EnergyServiceArgs.builder()        
            .resourceGroupName("DummyResourceGroupName")
            .resourceName("DummyResourceName")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const energyService = new azure_native.openenergyplatform.EnergyService("energyService", {
    resourceGroupName: "DummyResourceGroupName",
    resourceName: "DummyResourceName",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

energy_service = azure_native.openenergyplatform.EnergyService("energyService",
    resource_group_name="DummyResourceGroupName",
    resource_name_="DummyResourceName")

```

```yaml
resources:
  energyService:
    type: azure-native:openenergyplatform:EnergyService
    properties:
      resourceGroupName: DummyResourceGroupName
      resourceName: DummyResourceName

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:openenergyplatform:EnergyService DummyResourceName /subscriptions/00000000-0000-0000-0000-000000000001/resourceGroups/DummyResourceGroupName/providers/Microsoft.OEP/oepResource/DummyResourceName 
```
