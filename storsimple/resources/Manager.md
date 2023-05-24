The StorSimple Manager.
API Version: 2017-06-01.
Previous API Version: 2017-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ManagersCreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var manager = new AzureNative.StorSimple.Manager("manager", new()
    {
        CisIntrinsicSettings = new AzureNative.StorSimple.Inputs.ManagerIntrinsicSettingsArgs
        {
            Type = AzureNative.StorSimple.ManagerType.GardaV1,
        },
        Location = "westus",
        ManagerName = "ManagerForSDKTest2",
        ResourceGroupName = "ResourceGroupForSDKTest",
        Sku = new AzureNative.StorSimple.Inputs.ManagerSkuArgs
        {
            Name = AzureNative.StorSimple.ManagerSkuType.Standard,
        },
    });

});


```

```go
package main

import (
	storsimple "github.com/pulumi/pulumi-azure-native-sdk/storsimple"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := storsimple.NewManager(ctx, "manager", &storsimple.ManagerArgs{
			CisIntrinsicSettings: &storsimple.ManagerIntrinsicSettingsArgs{
				Type: storsimple.ManagerTypeGardaV1,
			},
			Location:          pulumi.String("westus"),
			ManagerName:       pulumi.String("ManagerForSDKTest2"),
			ResourceGroupName: pulumi.String("ResourceGroupForSDKTest"),
			Sku: &storsimple.ManagerSkuArgs{
				Name: storsimple.ManagerSkuTypeStandard,
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
import com.pulumi.azurenative.storsimple.Manager;
import com.pulumi.azurenative.storsimple.ManagerArgs;
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
        var manager = new Manager("manager", ManagerArgs.builder()        
            .cisIntrinsicSettings(Map.of("type", "GardaV1"))
            .location("westus")
            .managerName("ManagerForSDKTest2")
            .resourceGroupName("ResourceGroupForSDKTest")
            .sku(Map.of("name", "Standard"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const manager = new azure_native.storsimple.Manager("manager", {
    cisIntrinsicSettings: {
        type: azure_native.storsimple.ManagerType.GardaV1,
    },
    location: "westus",
    managerName: "ManagerForSDKTest2",
    resourceGroupName: "ResourceGroupForSDKTest",
    sku: {
        name: azure_native.storsimple.ManagerSkuType.Standard,
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

manager = azure_native.storsimple.Manager("manager",
    cis_intrinsic_settings=azure_native.storsimple.ManagerIntrinsicSettingsArgs(
        type=azure_native.storsimple.ManagerType.GARDA_V1,
    ),
    location="westus",
    manager_name="ManagerForSDKTest2",
    resource_group_name="ResourceGroupForSDKTest",
    sku=azure_native.storsimple.ManagerSkuArgs(
        name=azure_native.storsimple.ManagerSkuType.STANDARD,
    ))

```

```yaml
resources:
  manager:
    type: azure-native:storsimple:Manager
    properties:
      cisIntrinsicSettings:
        type: GardaV1
      location: westus
      managerName: ManagerForSDKTest2
      resourceGroupName: ResourceGroupForSDKTest
      sku:
        name: Standard

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:storsimple:Manager ManagerForSDKTest2 /subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.StorSimple/Managers/ManagerForSDKTest2 
```
