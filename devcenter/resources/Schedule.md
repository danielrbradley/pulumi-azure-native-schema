Represents a Schedule to execute a task.
API Version: 2022-11-11-preview.
Previous API Version: 2022-09-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Schedules_CreateDailyShutdownPoolSchedule
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var schedule = new AzureNative.DevCenter.Schedule("schedule", new()
    {
        Frequency = "Daily",
        PoolName = "DevPool",
        ProjectName = "DevProject",
        ResourceGroupName = "rg1",
        ScheduleName = "autoShutdown",
        State = "Enabled",
        Time = "17:30",
        TimeZone = "America/Los_Angeles",
        Type = "StopDevBox",
    });

});


```

```go
package main

import (
	devcenter "github.com/pulumi/pulumi-azure-native-sdk/devcenter"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := devcenter.NewSchedule(ctx, "schedule", &devcenter.ScheduleArgs{
			Frequency:         pulumi.String("Daily"),
			PoolName:          pulumi.String("DevPool"),
			ProjectName:       pulumi.String("DevProject"),
			ResourceGroupName: pulumi.String("rg1"),
			ScheduleName:      pulumi.String("autoShutdown"),
			State:             pulumi.String("Enabled"),
			Time:              pulumi.String("17:30"),
			TimeZone:          pulumi.String("America/Los_Angeles"),
			Type:              pulumi.String("StopDevBox"),
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
import com.pulumi.azurenative.devcenter.Schedule;
import com.pulumi.azurenative.devcenter.ScheduleArgs;
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
        var schedule = new Schedule("schedule", ScheduleArgs.builder()        
            .frequency("Daily")
            .poolName("DevPool")
            .projectName("DevProject")
            .resourceGroupName("rg1")
            .scheduleName("autoShutdown")
            .state("Enabled")
            .time("17:30")
            .timeZone("America/Los_Angeles")
            .type("StopDevBox")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const schedule = new azure_native.devcenter.Schedule("schedule", {
    frequency: "Daily",
    poolName: "DevPool",
    projectName: "DevProject",
    resourceGroupName: "rg1",
    scheduleName: "autoShutdown",
    state: "Enabled",
    time: "17:30",
    timeZone: "America/Los_Angeles",
    type: "StopDevBox",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

schedule = azure_native.devcenter.Schedule("schedule",
    frequency="Daily",
    pool_name="DevPool",
    project_name="DevProject",
    resource_group_name="rg1",
    schedule_name="autoShutdown",
    state="Enabled",
    time="17:30",
    time_zone="America/Los_Angeles",
    type="StopDevBox")

```

```yaml
resources:
  schedule:
    type: azure-native:devcenter:Schedule
    properties:
      frequency: Daily
      poolName: DevPool
      projectName: DevProject
      resourceGroupName: rg1
      scheduleName: autoShutdown
      state: Enabled
      time: 17:30
      timeZone: America/Los_Angeles
      type: StopDevBox

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devcenter:Schedule autoShutdown /subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/rg1/providers/Microsoft.DevCenter/projects/TestProject/pools/DevPool/schedules/autoShutdown 
```
