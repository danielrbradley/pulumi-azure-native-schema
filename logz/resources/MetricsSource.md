
API Version: 2022-01-01-preview.
Previous API Version: 2022-01-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### metricsSource_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var metricsSource = new AzureNative.Logz.MetricsSource("metricsSource", new()
    {
        MetricsSourceName = "MetricsSource1",
        MonitorName = "myMonitor",
        ResourceGroupName = "myResourceGroup",
    });

});


```

```go
package main

import (
	logz "github.com/pulumi/pulumi-azure-native-sdk/logz"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := logz.NewMetricsSource(ctx, "metricsSource", &logz.MetricsSourceArgs{
			MetricsSourceName: pulumi.String("MetricsSource1"),
			MonitorName:       pulumi.String("myMonitor"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.logz.MetricsSource;
import com.pulumi.azurenative.logz.MetricsSourceArgs;
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
        var metricsSource = new MetricsSource("metricsSource", MetricsSourceArgs.builder()        
            .metricsSourceName("MetricsSource1")
            .monitorName("myMonitor")
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const metricsSource = new azure_native.logz.MetricsSource("metricsSource", {
    metricsSourceName: "MetricsSource1",
    monitorName: "myMonitor",
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

metrics_source = azure_native.logz.MetricsSource("metricsSource",
    metrics_source_name="MetricsSource1",
    monitor_name="myMonitor",
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  metricsSource:
    type: azure-native:logz:MetricsSource
    properties:
      metricsSourceName: MetricsSource1
      monitorName: myMonitor
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:logz:MetricsSource myMonitor /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/monitors/myMonitor/metricsSource/MetricsSource1 
```
