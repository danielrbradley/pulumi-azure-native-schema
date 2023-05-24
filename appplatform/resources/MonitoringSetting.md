Monitoring Setting resource
API Version: 2022-12-01.
Previous API Version: 2020-07-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### MonitoringSettings_UpdatePut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var monitoringSetting = new AzureNative.AppPlatform.MonitoringSetting("monitoringSetting", new()
    {
        Properties = new AzureNative.AppPlatform.Inputs.MonitoringSettingPropertiesArgs
        {
            AppInsightsInstrumentationKey = "00000000-0000-0000-0000-000000000000",
            AppInsightsSamplingRate = 10,
            TraceEnabled = true,
        },
        ResourceGroupName = "myResourceGroup",
        ServiceName = "myservice",
    });

});


```

```go
package main

import (
	appplatform "github.com/pulumi/pulumi-azure-native-sdk/appplatform"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := appplatform.NewMonitoringSetting(ctx, "monitoringSetting", &appplatform.MonitoringSettingArgs{
			Properties: &appplatform.MonitoringSettingPropertiesArgs{
				AppInsightsInstrumentationKey: pulumi.String("00000000-0000-0000-0000-000000000000"),
				AppInsightsSamplingRate:       pulumi.Float64(10),
				TraceEnabled:                  pulumi.Bool(true),
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
			ServiceName:       pulumi.String("myservice"),
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
import com.pulumi.azurenative.appplatform.MonitoringSetting;
import com.pulumi.azurenative.appplatform.MonitoringSettingArgs;
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
        var monitoringSetting = new MonitoringSetting("monitoringSetting", MonitoringSettingArgs.builder()        
            .properties(Map.ofEntries(
                Map.entry("appInsightsInstrumentationKey", "00000000-0000-0000-0000-000000000000"),
                Map.entry("appInsightsSamplingRate", 10),
                Map.entry("traceEnabled", true)
            ))
            .resourceGroupName("myResourceGroup")
            .serviceName("myservice")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const monitoringSetting = new azure_native.appplatform.MonitoringSetting("monitoringSetting", {
    properties: {
        appInsightsInstrumentationKey: "00000000-0000-0000-0000-000000000000",
        appInsightsSamplingRate: 10,
        traceEnabled: true,
    },
    resourceGroupName: "myResourceGroup",
    serviceName: "myservice",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

monitoring_setting = azure_native.appplatform.MonitoringSetting("monitoringSetting",
    properties=azure_native.appplatform.MonitoringSettingPropertiesArgs(
        app_insights_instrumentation_key="00000000-0000-0000-0000-000000000000",
        app_insights_sampling_rate=10,
        trace_enabled=True,
    ),
    resource_group_name="myResourceGroup",
    service_name="myservice")

```

```yaml
resources:
  monitoringSetting:
    type: azure-native:appplatform:MonitoringSetting
    properties:
      properties:
        appInsightsInstrumentationKey: 00000000-0000-0000-0000-000000000000
        appInsightsSamplingRate: 10
        traceEnabled: true
      resourceGroupName: myResourceGroup
      serviceName: myservice

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:appplatform:MonitoringSetting default /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.AppPlatform/Spring/myservice/monitoringSettings/default 
```
