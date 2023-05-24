The extended info of the manager.
API Version: 2017-06-01.
Previous API Version: 2017-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ManagersCreateExtendedInfo
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managerExtendedInfo = new AzureNative.StorSimple.ManagerExtendedInfo("managerExtendedInfo", new()
    {
        Algorithm = "None",
        IntegrityKey = "BIl+RHqO8PZ6DRvuXTTK7g==",
        ManagerName = "ManagerForSDKTest2",
        ResourceGroupName = "ResourceGroupForSDKTest",
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
		_, err := storsimple.NewManagerExtendedInfo(ctx, "managerExtendedInfo", &storsimple.ManagerExtendedInfoArgs{
			Algorithm:         pulumi.String("None"),
			IntegrityKey:      pulumi.String("BIl+RHqO8PZ6DRvuXTTK7g=="),
			ManagerName:       pulumi.String("ManagerForSDKTest2"),
			ResourceGroupName: pulumi.String("ResourceGroupForSDKTest"),
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
import com.pulumi.azurenative.storsimple.ManagerExtendedInfo;
import com.pulumi.azurenative.storsimple.ManagerExtendedInfoArgs;
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
        var managerExtendedInfo = new ManagerExtendedInfo("managerExtendedInfo", ManagerExtendedInfoArgs.builder()        
            .algorithm("None")
            .integrityKey("BIl+RHqO8PZ6DRvuXTTK7g==")
            .managerName("ManagerForSDKTest2")
            .resourceGroupName("ResourceGroupForSDKTest")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managerExtendedInfo = new azure_native.storsimple.ManagerExtendedInfo("managerExtendedInfo", {
    algorithm: "None",
    integrityKey: "BIl+RHqO8PZ6DRvuXTTK7g==",
    managerName: "ManagerForSDKTest2",
    resourceGroupName: "ResourceGroupForSDKTest",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

manager_extended_info = azure_native.storsimple.ManagerExtendedInfo("managerExtendedInfo",
    algorithm="None",
    integrity_key="BIl+RHqO8PZ6DRvuXTTK7g==",
    manager_name="ManagerForSDKTest2",
    resource_group_name="ResourceGroupForSDKTest")

```

```yaml
resources:
  managerExtendedInfo:
    type: azure-native:storsimple:ManagerExtendedInfo
    properties:
      algorithm: None
      integrityKey: BIl+RHqO8PZ6DRvuXTTK7g==
      managerName: ManagerForSDKTest2
      resourceGroupName: ResourceGroupForSDKTest

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:storsimple:ManagerExtendedInfo vaultExtendedInfo /subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.StorSimple/Managers/ManagerForSDKTest2extendedInformation/vaultExtendedInfo 
```
