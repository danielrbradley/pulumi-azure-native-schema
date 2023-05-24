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
    var periodicTimerEventTrigger = new AzureNative.DataBoxEdge.PeriodicTimerEventTrigger("periodicTimerEventTrigger", new()
    {
        DeviceName = "testedgedevice",
        Name = "trigger1",
        ResourceGroupName = "GroupForEdgeAutomation",
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
		_, err := databoxedge.NewPeriodicTimerEventTrigger(ctx, "periodicTimerEventTrigger", &databoxedge.PeriodicTimerEventTriggerArgs{
			DeviceName:        pulumi.String("testedgedevice"),
			Name:              pulumi.String("trigger1"),
			ResourceGroupName: pulumi.String("GroupForEdgeAutomation"),
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
import com.pulumi.azurenative.databoxedge.PeriodicTimerEventTrigger;
import com.pulumi.azurenative.databoxedge.PeriodicTimerEventTriggerArgs;
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
        var periodicTimerEventTrigger = new PeriodicTimerEventTrigger("periodicTimerEventTrigger", PeriodicTimerEventTriggerArgs.builder()        
            .deviceName("testedgedevice")
            .name("trigger1")
            .resourceGroupName("GroupForEdgeAutomation")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const periodicTimerEventTrigger = new azure_native.databoxedge.PeriodicTimerEventTrigger("periodicTimerEventTrigger", {
    deviceName: "testedgedevice",
    name: "trigger1",
    resourceGroupName: "GroupForEdgeAutomation",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

periodic_timer_event_trigger = azure_native.databoxedge.PeriodicTimerEventTrigger("periodicTimerEventTrigger",
    device_name="testedgedevice",
    name="trigger1",
    resource_group_name="GroupForEdgeAutomation")

```

```yaml
resources:
  periodicTimerEventTrigger:
    type: azure-native:databoxedge:PeriodicTimerEventTrigger
    properties:
      deviceName: testedgedevice
      name: trigger1
      resourceGroupName: GroupForEdgeAutomation

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:databoxedge:PeriodicTimerEventTrigger trigger1 /subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/triggers/trigger1 
```
