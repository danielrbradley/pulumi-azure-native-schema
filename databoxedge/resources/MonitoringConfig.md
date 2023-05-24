The metric setting details for the role
API Version: 2022-03-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PutMonitoringConfig
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var monitoringConfig = new AzureNative.DataBoxEdge.MonitoringConfig("monitoringConfig", new()
    {
        DeviceName = "testedgedevice",
        MetricConfigurations = new[]
        {
            new AzureNative.DataBoxEdge.Inputs.MetricConfigurationArgs
            {
                CounterSets = new[]
                {
                    new AzureNative.DataBoxEdge.Inputs.MetricCounterSetArgs
                    {
                        Counters = new[]
                        {
                            new AzureNative.DataBoxEdge.Inputs.MetricCounterArgs
                            {
                                Name = "test",
                            },
                        },
                    },
                },
                MdmAccount = "test",
                MetricNameSpace = "test",
                ResourceId = "test",
            },
        },
        ResourceGroupName = "GroupForEdgeAutomation",
        RoleName = "testrole",
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
		_, err := databoxedge.NewMonitoringConfig(ctx, "monitoringConfig", &databoxedge.MonitoringConfigArgs{
			DeviceName: pulumi.String("testedgedevice"),
			MetricConfigurations: []databoxedge.MetricConfigurationArgs{
				{
					CounterSets: databoxedge.MetricCounterSetArray{
						{
							Counters: databoxedge.MetricCounterArray{
								{
									Name: pulumi.String("test"),
								},
							},
						},
					},
					MdmAccount:      pulumi.String("test"),
					MetricNameSpace: pulumi.String("test"),
					ResourceId:      pulumi.String("test"),
				},
			},
			ResourceGroupName: pulumi.String("GroupForEdgeAutomation"),
			RoleName:          pulumi.String("testrole"),
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
import com.pulumi.azurenative.databoxedge.MonitoringConfig;
import com.pulumi.azurenative.databoxedge.MonitoringConfigArgs;
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
        var monitoringConfig = new MonitoringConfig("monitoringConfig", MonitoringConfigArgs.builder()        
            .deviceName("testedgedevice")
            .metricConfigurations(Map.ofEntries(
                Map.entry("counterSets", Map.of("counters", Map.of("name", "test"))),
                Map.entry("mdmAccount", "test"),
                Map.entry("metricNameSpace", "test"),
                Map.entry("resourceId", "test")
            ))
            .resourceGroupName("GroupForEdgeAutomation")
            .roleName("testrole")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const monitoringConfig = new azure_native.databoxedge.MonitoringConfig("monitoringConfig", {
    deviceName: "testedgedevice",
    metricConfigurations: [{
        counterSets: [{
            counters: [{
                name: "test",
            }],
        }],
        mdmAccount: "test",
        metricNameSpace: "test",
        resourceId: "test",
    }],
    resourceGroupName: "GroupForEdgeAutomation",
    roleName: "testrole",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

monitoring_config = azure_native.databoxedge.MonitoringConfig("monitoringConfig",
    device_name="testedgedevice",
    metric_configurations=[{
        "counterSets": [{
            "counters": [azure_native.databoxedge.MetricCounterArgs(
                name="test",
            )],
        }],
        "mdmAccount": "test",
        "metricNameSpace": "test",
        "resourceId": "test",
    }],
    resource_group_name="GroupForEdgeAutomation",
    role_name="testrole")

```

```yaml
resources:
  monitoringConfig:
    type: azure-native:databoxedge:MonitoringConfig
    properties:
      deviceName: testedgedevice
      metricConfigurations:
        - counterSets:
            - counters:
                - name: test
          mdmAccount: test
          metricNameSpace: test
          resourceId: test
      resourceGroupName: GroupForEdgeAutomation
      roleName: testrole

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:databoxedge:MonitoringConfig myresource1 /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/{deviceName}/roles/{roleName}/monitoringConfig/default 
```
