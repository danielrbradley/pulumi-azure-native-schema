configuration associated with SAP Landscape Monitor Dashboard.
API Version: 2023-04-01.

{{% examples %}}
## Example Usage
{{% example %}}
### Create for SAP Landscape monitor Dashboard
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sapLandscapeMonitor = new AzureNative.Workloads.SapLandscapeMonitor("sapLandscapeMonitor", new()
    {
        Grouping = new AzureNative.Workloads.Inputs.SapLandscapeMonitorPropertiesGroupingArgs
        {
            Landscape = new[]
            {
                new AzureNative.Workloads.Inputs.SapLandscapeMonitorSidMappingArgs
                {
                    Name = "Prod",
                    TopSid = new[]
                    {
                        "SID1",
                        "SID2",
                    },
                },
            },
            SapApplication = new[]
            {
                new AzureNative.Workloads.Inputs.SapLandscapeMonitorSidMappingArgs
                {
                    Name = "ERP1",
                    TopSid = new[]
                    {
                        "SID1",
                        "SID2",
                    },
                },
            },
        },
        MonitorName = "mySapMonitor",
        ResourceGroupName = "myResourceGroup",
        TopMetricsThresholds = new[]
        {
            new AzureNative.Workloads.Inputs.SapLandscapeMonitorMetricThresholdsArgs
            {
                Green = 90,
                Name = "Instance Availability",
                Red = 50,
                Yellow = 75,
            },
        },
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewSapLandscapeMonitor(ctx, "sapLandscapeMonitor", &workloads.SapLandscapeMonitorArgs{
			Grouping: workloads.SapLandscapeMonitorPropertiesResponseGrouping{
				Landscape: workloads.SapLandscapeMonitorSidMappingArray{
					&workloads.SapLandscapeMonitorSidMappingArgs{
						Name: pulumi.String("Prod"),
						TopSid: pulumi.StringArray{
							pulumi.String("SID1"),
							pulumi.String("SID2"),
						},
					},
				},
				SapApplication: workloads.SapLandscapeMonitorSidMappingArray{
					&workloads.SapLandscapeMonitorSidMappingArgs{
						Name: pulumi.String("ERP1"),
						TopSid: pulumi.StringArray{
							pulumi.String("SID1"),
							pulumi.String("SID2"),
						},
					},
				},
			},
			MonitorName:       pulumi.String("mySapMonitor"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			TopMetricsThresholds: []workloads.SapLandscapeMonitorMetricThresholdsArgs{
				{
					Green:  pulumi.Float64(90),
					Name:   pulumi.String("Instance Availability"),
					Red:    pulumi.Float64(50),
					Yellow: pulumi.Float64(75),
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
import com.pulumi.azurenative.workloads.SapLandscapeMonitor;
import com.pulumi.azurenative.workloads.SapLandscapeMonitorArgs;
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
        var sapLandscapeMonitor = new SapLandscapeMonitor("sapLandscapeMonitor", SapLandscapeMonitorArgs.builder()        
            .grouping(Map.ofEntries(
                Map.entry("landscape", Map.ofEntries(
                    Map.entry("name", "Prod"),
                    Map.entry("topSid",                     
                        "SID1",
                        "SID2")
                )),
                Map.entry("sapApplication", Map.ofEntries(
                    Map.entry("name", "ERP1"),
                    Map.entry("topSid",                     
                        "SID1",
                        "SID2")
                ))
            ))
            .monitorName("mySapMonitor")
            .resourceGroupName("myResourceGroup")
            .topMetricsThresholds(Map.ofEntries(
                Map.entry("green", 90),
                Map.entry("name", "Instance Availability"),
                Map.entry("red", 50),
                Map.entry("yellow", 75)
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sapLandscapeMonitor = new azure_native.workloads.SapLandscapeMonitor("sapLandscapeMonitor", {
    grouping: {
        landscape: [{
            name: "Prod",
            topSid: [
                "SID1",
                "SID2",
            ],
        }],
        sapApplication: [{
            name: "ERP1",
            topSid: [
                "SID1",
                "SID2",
            ],
        }],
    },
    monitorName: "mySapMonitor",
    resourceGroupName: "myResourceGroup",
    topMetricsThresholds: [{
        green: 90,
        name: "Instance Availability",
        red: 50,
        yellow: 75,
    }],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sap_landscape_monitor = azure_native.workloads.SapLandscapeMonitor("sapLandscapeMonitor",
    grouping=azure_native.workloads.SapLandscapeMonitorPropertiesResponseGroupingArgs(
        landscape=[azure_native.workloads.SapLandscapeMonitorSidMappingArgs(
            name="Prod",
            top_sid=[
                "SID1",
                "SID2",
            ],
        )],
        sap_application=[azure_native.workloads.SapLandscapeMonitorSidMappingArgs(
            name="ERP1",
            top_sid=[
                "SID1",
                "SID2",
            ],
        )],
    ),
    monitor_name="mySapMonitor",
    resource_group_name="myResourceGroup",
    top_metrics_thresholds=[azure_native.workloads.SapLandscapeMonitorMetricThresholdsArgs(
        green=90,
        name="Instance Availability",
        red=50,
        yellow=75,
    )])

```

```yaml
resources:
  sapLandscapeMonitor:
    type: azure-native:workloads:SapLandscapeMonitor
    properties:
      grouping:
        landscape:
          - name: Prod
            topSid:
              - SID1
              - SID2
        sapApplication:
          - name: ERP1
            topSid:
              - SID1
              - SID2
      monitorName: mySapMonitor
      resourceGroupName: myResourceGroup
      topMetricsThresholds:
        - green: 90
          name: Instance Availability
          red: 50
          yellow: 75

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:workloads:SapLandscapeMonitor default /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Workloads/monitors/myMonitor/sapLandscapeMonitor/default 
```
