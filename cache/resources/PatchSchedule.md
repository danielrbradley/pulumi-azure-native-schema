Response to put/get patch schedules for Redis cache.
API Version: 2022-06-01.
Previous API Version: 2020-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### RedisCachePatchSchedulesCreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var patchSchedule = new AzureNative.Cache.PatchSchedule("patchSchedule", new()
    {
        Default = "default",
        Name = "cache1",
        ResourceGroupName = "rg1",
        ScheduleEntries = new[]
        {
            new AzureNative.Cache.Inputs.ScheduleEntryArgs
            {
                DayOfWeek = AzureNative.Cache.DayOfWeek.Monday,
                MaintenanceWindow = "PT5H",
                StartHourUtc = 12,
            },
            new AzureNative.Cache.Inputs.ScheduleEntryArgs
            {
                DayOfWeek = AzureNative.Cache.DayOfWeek.Tuesday,
                StartHourUtc = 12,
            },
        },
    });

});


```

```go
package main

import (
	cache "github.com/pulumi/pulumi-azure-native-sdk/cache"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := cache.NewPatchSchedule(ctx, "patchSchedule", &cache.PatchScheduleArgs{
			Default:           pulumi.String("default"),
			Name:              pulumi.String("cache1"),
			ResourceGroupName: pulumi.String("rg1"),
			ScheduleEntries: []cache.ScheduleEntryArgs{
				{
					DayOfWeek:         cache.DayOfWeekMonday,
					MaintenanceWindow: pulumi.String("PT5H"),
					StartHourUtc:      pulumi.Int(12),
				},
				{
					DayOfWeek:    cache.DayOfWeekTuesday,
					StartHourUtc: pulumi.Int(12),
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
import com.pulumi.azurenative.cache.PatchSchedule;
import com.pulumi.azurenative.cache.PatchScheduleArgs;
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
        var patchSchedule = new PatchSchedule("patchSchedule", PatchScheduleArgs.builder()        
            .default_("default")
            .name("cache1")
            .resourceGroupName("rg1")
            .scheduleEntries(            
                Map.ofEntries(
                    Map.entry("dayOfWeek", "Monday"),
                    Map.entry("maintenanceWindow", "PT5H"),
                    Map.entry("startHourUtc", 12)
                ),
                Map.ofEntries(
                    Map.entry("dayOfWeek", "Tuesday"),
                    Map.entry("startHourUtc", 12)
                ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const patchSchedule = new azure_native.cache.PatchSchedule("patchSchedule", {
    "default": "default",
    name: "cache1",
    resourceGroupName: "rg1",
    scheduleEntries: [
        {
            dayOfWeek: azure_native.cache.DayOfWeek.Monday,
            maintenanceWindow: "PT5H",
            startHourUtc: 12,
        },
        {
            dayOfWeek: azure_native.cache.DayOfWeek.Tuesday,
            startHourUtc: 12,
        },
    ],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

patch_schedule = azure_native.cache.PatchSchedule("patchSchedule",
    default="default",
    name="cache1",
    resource_group_name="rg1",
    schedule_entries=[
        azure_native.cache.ScheduleEntryArgs(
            day_of_week=azure_native.cache.DayOfWeek.MONDAY,
            maintenance_window="PT5H",
            start_hour_utc=12,
        ),
        azure_native.cache.ScheduleEntryArgs(
            day_of_week=azure_native.cache.DayOfWeek.TUESDAY,
            start_hour_utc=12,
        ),
    ])

```

```yaml
resources:
  patchSchedule:
    type: azure-native:cache:PatchSchedule
    properties:
      default: default
      name: cache1
      resourceGroupName: rg1
      scheduleEntries:
        - dayOfWeek: Monday
          maintenanceWindow: PT5H
          startHourUtc: 12
        - dayOfWeek: Tuesday
          startHourUtc: 12

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:cache:PatchSchedule cachename1/default /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Cache/Redis/cache1/patchSchedules/default 
```
