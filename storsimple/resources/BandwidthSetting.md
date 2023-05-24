The bandwidth setting.
API Version: 2017-06-01.
Previous API Version: 2017-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### BandwidthSettingsCreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var bandwidthSetting = new AzureNative.StorSimple.BandwidthSetting("bandwidthSetting", new()
    {
        BandwidthSettingName = "BWSForTest",
        ManagerName = "ManagerForSDKTest1",
        ResourceGroupName = "ResourceGroupForSDKTest",
        Schedules = new[]
        {
            new AzureNative.StorSimple.Inputs.BandwidthScheduleArgs
            {
                Days = new[]
                {
                    AzureNative.StorSimple.DayOfWeek.Saturday,
                    AzureNative.StorSimple.DayOfWeek.Sunday,
                },
                RateInMbps = 10,
                Start = new AzureNative.StorSimple.Inputs.TimeArgs
                {
                    Hours = 10,
                    Minutes = 0,
                    Seconds = 0,
                },
                Stop = new AzureNative.StorSimple.Inputs.TimeArgs
                {
                    Hours = 20,
                    Minutes = 0,
                    Seconds = 0,
                },
            },
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
		_, err := storsimple.NewBandwidthSetting(ctx, "bandwidthSetting", &storsimple.BandwidthSettingArgs{
			BandwidthSettingName: pulumi.String("BWSForTest"),
			ManagerName:          pulumi.String("ManagerForSDKTest1"),
			ResourceGroupName:    pulumi.String("ResourceGroupForSDKTest"),
			Schedules: []storsimple.BandwidthScheduleArgs{
				{
					Days: storsimple.DayOfWeekArray{
						storsimple.DayOfWeekSaturday,
						storsimple.DayOfWeekSunday,
					},
					RateInMbps: pulumi.Int(10),
					Start: {
						Hours:   pulumi.Int(10),
						Minutes: pulumi.Int(0),
						Seconds: pulumi.Int(0),
					},
					Stop: {
						Hours:   pulumi.Int(20),
						Minutes: pulumi.Int(0),
						Seconds: pulumi.Int(0),
					},
				},
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
import com.pulumi.azurenative.storsimple.BandwidthSetting;
import com.pulumi.azurenative.storsimple.BandwidthSettingArgs;
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
        var bandwidthSetting = new BandwidthSetting("bandwidthSetting", BandwidthSettingArgs.builder()        
            .bandwidthSettingName("BWSForTest")
            .managerName("ManagerForSDKTest1")
            .resourceGroupName("ResourceGroupForSDKTest")
            .schedules(Map.ofEntries(
                Map.entry("days",                 
                    "Saturday",
                    "Sunday"),
                Map.entry("rateInMbps", 10),
                Map.entry("start", Map.ofEntries(
                    Map.entry("hours", 10),
                    Map.entry("minutes", 0),
                    Map.entry("seconds", 0)
                )),
                Map.entry("stop", Map.ofEntries(
                    Map.entry("hours", 20),
                    Map.entry("minutes", 0),
                    Map.entry("seconds", 0)
                ))
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const bandwidthSetting = new azure_native.storsimple.BandwidthSetting("bandwidthSetting", {
    bandwidthSettingName: "BWSForTest",
    managerName: "ManagerForSDKTest1",
    resourceGroupName: "ResourceGroupForSDKTest",
    schedules: [{
        days: [
            azure_native.storsimple.DayOfWeek.Saturday,
            azure_native.storsimple.DayOfWeek.Sunday,
        ],
        rateInMbps: 10,
        start: {
            hours: 10,
            minutes: 0,
            seconds: 0,
        },
        stop: {
            hours: 20,
            minutes: 0,
            seconds: 0,
        },
    }],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

bandwidth_setting = azure_native.storsimple.BandwidthSetting("bandwidthSetting",
    bandwidth_setting_name="BWSForTest",
    manager_name="ManagerForSDKTest1",
    resource_group_name="ResourceGroupForSDKTest",
    schedules=[{
        "days": [
            azure_native.storsimple.DayOfWeek.SATURDAY,
            azure_native.storsimple.DayOfWeek.SUNDAY,
        ],
        "rateInMbps": 10,
        "start": azure_native.storsimple.TimeArgs(
            hours=10,
            minutes=0,
            seconds=0,
        ),
        "stop": azure_native.storsimple.TimeArgs(
            hours=20,
            minutes=0,
            seconds=0,
        ),
    }])

```

```yaml
resources:
  bandwidthSetting:
    type: azure-native:storsimple:BandwidthSetting
    properties:
      bandwidthSettingName: BWSForTest
      managerName: ManagerForSDKTest1
      resourceGroupName: ResourceGroupForSDKTest
      schedules:
        - days:
            - Saturday
            - Sunday
          rateInMbps: 10
          start:
            hours: 10
            minutes: 0
            seconds: 0
          stop:
            hours: 20
            minutes: 0
            seconds: 0

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:storsimple:BandwidthSetting BWSForTest /subscriptions/4385cf00-2d3a-425a-832f-f4285b1c9dce/resourceGroups/ResourceGroupForSDKTest/providers/Microsoft.StorSimple/managers/ManagerForSDKTest1/bandwidthSettings/BWSForTest 
```
