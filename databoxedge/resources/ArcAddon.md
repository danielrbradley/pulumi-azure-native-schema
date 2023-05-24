Arc Addon.
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
    var arcAddon = new AzureNative.DataBoxEdge.ArcAddon("arcAddon", new()
    {
        AddonName = "arcName",
        DeviceName = "testedgedevice",
        Kind = "ArcForKubernetes",
        ResourceGroupName = "GroupForEdgeAutomation",
        ResourceLocation = "EastUS",
        ResourceName = "testedgedevice",
        RoleName = "KubernetesRole",
        SubscriptionId = "4385cf00-2d3a-425a-832f-f4285b1c9dce",
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
		_, err := databoxedge.NewArcAddon(ctx, "arcAddon", &databoxedge.ArcAddonArgs{
			AddonName:         pulumi.String("arcName"),
			DeviceName:        pulumi.String("testedgedevice"),
			Kind:              pulumi.String("ArcForKubernetes"),
			ResourceGroupName: pulumi.String("GroupForEdgeAutomation"),
			ResourceLocation:  pulumi.String("EastUS"),
			ResourceName:      pulumi.String("testedgedevice"),
			RoleName:          pulumi.String("KubernetesRole"),
			SubscriptionId:    pulumi.String("4385cf00-2d3a-425a-832f-f4285b1c9dce"),
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
import com.pulumi.azurenative.databoxedge.ArcAddon;
import com.pulumi.azurenative.databoxedge.ArcAddonArgs;
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
        var arcAddon = new ArcAddon("arcAddon", ArcAddonArgs.builder()        
            .addonName("arcName")
            .deviceName("testedgedevice")
            .kind("ArcForKubernetes")
            .resourceGroupName("GroupForEdgeAutomation")
            .resourceLocation("EastUS")
            .resourceName("testedgedevice")
            .roleName("KubernetesRole")
            .subscriptionId("4385cf00-2d3a-425a-832f-f4285b1c9dce")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const arcAddon = new azure_native.databoxedge.ArcAddon("arcAddon", {
    addonName: "arcName",
    deviceName: "testedgedevice",
    kind: "ArcForKubernetes",
    resourceGroupName: "GroupForEdgeAutomation",
    resourceLocation: "EastUS",
    resourceName: "testedgedevice",
    roleName: "KubernetesRole",
    subscriptionId: "4385cf00-2d3a-425a-832f-f4285b1c9dce",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

arc_addon = azure_native.databoxedge.ArcAddon("arcAddon",
    addon_name="arcName",
    device_name="testedgedevice",
    kind="ArcForKubernetes",
    resource_group_name="GroupForEdgeAutomation",
    resource_location="EastUS",
    resource_name_="testedgedevice",
    role_name="KubernetesRole",
    subscription_id="4385cf00-2d3a-425a-832f-f4285b1c9dce")

```

```yaml
resources:
  arcAddon:
    type: azure-native:databoxedge:ArcAddon
    properties:
      addonName: arcName
      deviceName: testedgedevice
      kind: ArcForKubernetes
      resourceGroupName: GroupForEdgeAutomation
      resourceLocation: EastUS
      resourceName: testedgedevice
      roleName: KubernetesRole
      subscriptionId: 4385cf00-2d3a-425a-832f-f4285b1c9dce

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:databoxedge:ArcAddon arcName /subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourcegroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/addonExamples/roles/kubernetesRole/addons/arcName 
```
