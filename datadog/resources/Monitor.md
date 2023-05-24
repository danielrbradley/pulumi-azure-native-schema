
API Version: 2022-06-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Monitors_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var monitor = new AzureNative.Datadog.Monitor("monitor", new()
    {
        MonitorName = "myMonitor",
        ResourceGroupName = "myResourceGroup",
    });

});


```

```go
package main

import (
	datadog "github.com/pulumi/pulumi-azure-native-sdk/datadog"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := datadog.NewMonitor(ctx, "monitor", &datadog.MonitorArgs{
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
import com.pulumi.azurenative.datadog.Monitor;
import com.pulumi.azurenative.datadog.MonitorArgs;
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
        var monitor = new Monitor("monitor", MonitorArgs.builder()        
            .monitorName("myMonitor")
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const monitor = new azure_native.datadog.Monitor("monitor", {
    monitorName: "myMonitor",
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

monitor = azure_native.datadog.Monitor("monitor",
    monitor_name="myMonitor",
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  monitor:
    type: azure-native:datadog:Monitor
    properties:
      monitorName: myMonitor
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:datadog:Monitor myMonitor /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/monitors/myMonitor 
```
