Trigger details.
API Version: 2022-03-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### TriggerPut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var fileEventTrigger = new AzureNative.DataBoxEdge.FileEventTrigger("fileEventTrigger", new()
    {
        CustomContextTag = "CustomContextTags-1235346475",
        DeviceName = "testedgedevice",
        Kind = "FileEvent",
        Name = "trigger1",
        ResourceGroupName = "GroupForEdgeAutomation",
        SinkInfo = new AzureNative.DataBoxEdge.Inputs.RoleSinkInfoArgs
        {
            RoleId = "/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/roles/role1",
        },
        SourceInfo = new AzureNative.DataBoxEdge.Inputs.FileSourceInfoArgs
        {
            ShareId = "/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/shares/share1",
        },
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
		_, err := databoxedge.NewFileEventTrigger(ctx, "fileEventTrigger", &databoxedge.FileEventTriggerArgs{
			CustomContextTag:  pulumi.String("CustomContextTags-1235346475"),
			DeviceName:        pulumi.String("testedgedevice"),
			Kind:              pulumi.String("FileEvent"),
			Name:              pulumi.String("trigger1"),
			ResourceGroupName: pulumi.String("GroupForEdgeAutomation"),
			SinkInfo: &databoxedge.RoleSinkInfoArgs{
				RoleId: pulumi.String("/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/roles/role1"),
			},
			SourceInfo: &databoxedge.FileSourceInfoArgs{
				ShareId: pulumi.String("/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/shares/share1"),
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
import com.pulumi.azurenative.databoxedge.FileEventTrigger;
import com.pulumi.azurenative.databoxedge.FileEventTriggerArgs;
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
        var fileEventTrigger = new FileEventTrigger("fileEventTrigger", FileEventTriggerArgs.builder()        
            .customContextTag("CustomContextTags-1235346475")
            .deviceName("testedgedevice")
            .kind("FileEvent")
            .name("trigger1")
            .resourceGroupName("GroupForEdgeAutomation")
            .sinkInfo(Map.of("roleId", "/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/roles/role1"))
            .sourceInfo(Map.of("shareId", "/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/shares/share1"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const fileEventTrigger = new azure_native.databoxedge.FileEventTrigger("fileEventTrigger", {
    customContextTag: "CustomContextTags-1235346475",
    deviceName: "testedgedevice",
    kind: "FileEvent",
    name: "trigger1",
    resourceGroupName: "GroupForEdgeAutomation",
    sinkInfo: {
        roleId: "/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/roles/role1",
    },
    sourceInfo: {
        shareId: "/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/shares/share1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

file_event_trigger = azure_native.databoxedge.FileEventTrigger("fileEventTrigger",
    custom_context_tag="CustomContextTags-1235346475",
    device_name="testedgedevice",
    kind="FileEvent",
    name="trigger1",
    resource_group_name="GroupForEdgeAutomation",
    sink_info=azure_native.databoxedge.RoleSinkInfoArgs(
        role_id="/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/roles/role1",
    ),
    source_info=azure_native.databoxedge.FileSourceInfoArgs(
        share_id="/subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/shares/share1",
    ))

```

```yaml
resources:
  fileEventTrigger:
    type: azure-native:databoxedge:FileEventTrigger
    properties:
      customContextTag: CustomContextTags-1235346475
      deviceName: testedgedevice
      kind: FileEvent
      name: trigger1
      resourceGroupName: GroupForEdgeAutomation
      sinkInfo:
        roleId: /subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/roles/role1
      sourceInfo:
        shareId: /subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/shares/share1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:databoxedge:FileEventTrigger trigger1 /subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/triggers/trigger1 
```
