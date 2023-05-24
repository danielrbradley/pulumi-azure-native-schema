The bandwidth schedule details.
API Version: 2022-03-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### BandwidthSchedulePut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var bandwidthSchedule = new AzureNative.DataBoxEdge.BandwidthSchedule("bandwidthSchedule", new()
    {
        Days = new[]
        {
            "Sunday",
            "Monday",
        },
        DeviceName = "testedgedevice",
        Name = "bandwidth-1",
        RateInMbps = 100,
        ResourceGroupName = "GroupForEdgeAutomation",
        Start = "0:0:0",
        Stop = "13:59:0",
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
		_, err := databoxedge.NewBandwidthSchedule(ctx, "bandwidthSchedule", &databoxedge.BandwidthScheduleArgs{
			Days: pulumi.StringArray{
				pulumi.String("Sunday"),
				pulumi.String("Monday"),
			},
			DeviceName:        pulumi.String("testedgedevice"),
			Name:              pulumi.String("bandwidth-1"),
			RateInMbps:        pulumi.Int(100),
			ResourceGroupName: pulumi.String("GroupForEdgeAutomation"),
			Start:             pulumi.String("0:0:0"),
			Stop:              pulumi.String("13:59:0"),
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
import com.pulumi.azurenative.databoxedge.BandwidthSchedule;
import com.pulumi.azurenative.databoxedge.BandwidthScheduleArgs;
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
        var bandwidthSchedule = new BandwidthSchedule("bandwidthSchedule", BandwidthScheduleArgs.builder()        
            .days(            
                "Sunday",
                "Monday")
            .deviceName("testedgedevice")
            .name("bandwidth-1")
            .rateInMbps(100)
            .resourceGroupName("GroupForEdgeAutomation")
            .start("0:0:0")
            .stop("13:59:0")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const bandwidthSchedule = new azure_native.databoxedge.BandwidthSchedule("bandwidthSchedule", {
    days: [
        "Sunday",
        "Monday",
    ],
    deviceName: "testedgedevice",
    name: "bandwidth-1",
    rateInMbps: 100,
    resourceGroupName: "GroupForEdgeAutomation",
    start: "0:0:0",
    stop: "13:59:0",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

bandwidth_schedule = azure_native.databoxedge.BandwidthSchedule("bandwidthSchedule",
    days=[
        "Sunday",
        "Monday",
    ],
    device_name="testedgedevice",
    name="bandwidth-1",
    rate_in_mbps=100,
    resource_group_name="GroupForEdgeAutomation",
    start="0:0:0",
    stop="13:59:0")

```

```yaml
resources:
  bandwidthSchedule:
    type: azure-native:databoxedge:BandwidthSchedule
    properties:
      days:
        - Sunday
        - Monday
      deviceName: testedgedevice
      name: bandwidth-1
      rateInMbps: 100
      resourceGroupName: GroupForEdgeAutomation
      start: 0:0:0
      stop: 13:59:0

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:databoxedge:BandwidthSchedule bandwidth-1 /subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/GroupForEdgeAutomation/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/testedgedevice/bandwidthSchedules/bandwidth-1 
```
