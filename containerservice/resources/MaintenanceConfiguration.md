See [planned maintenance](https://docs.microsoft.com/azure/aks/planned-maintenance) for more information about planned maintenance.
API Version: 2023-01-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create/Update Maintenance Configuration
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var maintenanceConfiguration = new AzureNative.ContainerService.MaintenanceConfiguration("maintenanceConfiguration", new()
    {
        ConfigName = "default",
        NotAllowedTime = new[]
        {
            new AzureNative.ContainerService.Inputs.TimeSpanArgs
            {
                End = "2020-11-30T12:00:00Z",
                Start = "2020-11-26T03:00:00Z",
            },
        },
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        TimeInWeek = new[]
        {
            new AzureNative.ContainerService.Inputs.TimeInWeekArgs
            {
                Day = "Monday",
                HourSlots = new[]
                {
                    1,
                    2,
                },
            },
        },
    });

});


```

```go
package main

import (
	containerservice "github.com/pulumi/pulumi-azure-native-sdk/containerservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := containerservice.NewMaintenanceConfiguration(ctx, "maintenanceConfiguration", &containerservice.MaintenanceConfigurationArgs{
			ConfigName: pulumi.String("default"),
			NotAllowedTime: []containerservice.TimeSpanArgs{
				{
					End:   pulumi.String("2020-11-30T12:00:00Z"),
					Start: pulumi.String("2020-11-26T03:00:00Z"),
				},
			},
			ResourceGroupName: pulumi.String("rg1"),
			ResourceName:      pulumi.String("clustername1"),
			TimeInWeek: []containerservice.TimeInWeekArgs{
				{
					Day: pulumi.String("Monday"),
					HourSlots: pulumi.IntArray{
						pulumi.Int(1),
						pulumi.Int(2),
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
import com.pulumi.azurenative.containerservice.MaintenanceConfiguration;
import com.pulumi.azurenative.containerservice.MaintenanceConfigurationArgs;
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
        var maintenanceConfiguration = new MaintenanceConfiguration("maintenanceConfiguration", MaintenanceConfigurationArgs.builder()        
            .configName("default")
            .notAllowedTime(Map.ofEntries(
                Map.entry("end", "2020-11-30T12:00:00Z"),
                Map.entry("start", "2020-11-26T03:00:00Z")
            ))
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .timeInWeek(Map.ofEntries(
                Map.entry("day", "Monday"),
                Map.entry("hourSlots",                 
                    1,
                    2)
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const maintenanceConfiguration = new azure_native.containerservice.MaintenanceConfiguration("maintenanceConfiguration", {
    configName: "default",
    notAllowedTime: [{
        end: "2020-11-30T12:00:00Z",
        start: "2020-11-26T03:00:00Z",
    }],
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    timeInWeek: [{
        day: "Monday",
        hourSlots: [
            1,
            2,
        ],
    }],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

maintenance_configuration = azure_native.containerservice.MaintenanceConfiguration("maintenanceConfiguration",
    config_name="default",
    not_allowed_time=[azure_native.containerservice.TimeSpanArgs(
        end="2020-11-30T12:00:00Z",
        start="2020-11-26T03:00:00Z",
    )],
    resource_group_name="rg1",
    resource_name_="clustername1",
    time_in_week=[azure_native.containerservice.TimeInWeekArgs(
        day="Monday",
        hour_slots=[
            1,
            2,
        ],
    )])

```

```yaml
resources:
  maintenanceConfiguration:
    type: azure-native:containerservice:MaintenanceConfiguration
    properties:
      configName: default
      notAllowedTime:
        - end: 2020-11-30T12:00:00Z
          start: 2020-11-26T03:00:00Z
      resourceGroupName: rg1
      resourceName: clustername1
      timeInWeek:
        - day: Monday
          hourSlots:
            - 1
            - 2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:containerservice:MaintenanceConfiguration default /subscriptions/subid1/resourcegroups/rg1/providers/Microsoft.ContainerService/managedClusters/clustername1/maintenanceConfigurations/default 
```
