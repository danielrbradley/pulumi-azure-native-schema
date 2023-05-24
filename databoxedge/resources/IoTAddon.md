IoT Addon.
API Version: 2022-03-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PutAddOns
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var ioTAddon = new AzureNative.DataBoxEdge.IoTAddon("ioTAddon", new()
    {
        AddonName = "arcName",
        DeviceName = "testedgedevice",
        ResourceGroupName = "GroupForEdgeAutomation",
        RoleName = "KubernetesRole",
    });

});


```

```go
package main

import (
	databoxedge "github.com/pulumi/pulumi-azure-native-sdk/databoxedge"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := databoxedge.NewIoTAddon(ctx, "ioTAddon", &databoxedge.IoTAddonArgs{
			AddonName:         pulumi.String("arcName"),
			DeviceName:        pulumi.String("testedgedevice"),
			ResourceGroupName: pulumi.String("GroupForEdgeAutomation"),
			RoleName:          pulumi.String("KubernetesRole"),
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
import com.pulumi.azurenative.databoxedge.IoTAddon;
import com.pulumi.azurenative.databoxedge.IoTAddonArgs;
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
        var ioTAddon = new IoTAddon("ioTAddon", IoTAddonArgs.builder()        
            .addonName("arcName")
            .deviceName("testedgedevice")
            .resourceGroupName("GroupForEdgeAutomation")
            .roleName("KubernetesRole")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const ioTAddon = new azure_native.databoxedge.IoTAddon("ioTAddon", {
    addonName: "arcName",
    deviceName: "testedgedevice",
    resourceGroupName: "GroupForEdgeAutomation",
    roleName: "KubernetesRole",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

io_t_addon = azure_native.databoxedge.IoTAddon("ioTAddon",
    addon_name="arcName",
    device_name="testedgedevice",
    resource_group_name="GroupForEdgeAutomation",
    role_name="KubernetesRole")

```

```yaml
resources:
  ioTAddon:
    type: azure-native:databoxedge:IoTAddon
    properties:
      addonName: arcName
      deviceName: testedgedevice
      resourceGroupName: GroupForEdgeAutomation
      roleName: KubernetesRole

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:databoxedge:IoTAddon arcName /subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourcegroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/addonExamples/roles/kubernetesRole/addons/arcName 
```
