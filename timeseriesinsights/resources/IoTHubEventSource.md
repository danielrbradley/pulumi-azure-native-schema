An event source that receives its data from an Azure IoTHub.
API Version: 2020-05-15.
Previous API Version: 2020-05-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateEventHubEventSource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var ioTHubEventSource = new AzureNative.TimeSeriesInsights.IoTHubEventSource("ioTHubEventSource", new()
    {
        EnvironmentName = "env1",
        EventSourceName = "es1",
        ResourceGroupName = "rg1",
    });

});


```

```go
package main

import (
	timeseriesinsights "github.com/pulumi/pulumi-azure-native-sdk/timeseriesinsights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := timeseriesinsights.NewIoTHubEventSource(ctx, "ioTHubEventSource", &timeseriesinsights.IoTHubEventSourceArgs{
			EnvironmentName:   pulumi.String("env1"),
			EventSourceName:   pulumi.String("es1"),
			ResourceGroupName: pulumi.String("rg1"),
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
import com.pulumi.azurenative.timeseriesinsights.IoTHubEventSource;
import com.pulumi.azurenative.timeseriesinsights.IoTHubEventSourceArgs;
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
        var ioTHubEventSource = new IoTHubEventSource("ioTHubEventSource", IoTHubEventSourceArgs.builder()        
            .environmentName("env1")
            .eventSourceName("es1")
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const ioTHubEventSource = new azure_native.timeseriesinsights.IoTHubEventSource("ioTHubEventSource", {
    environmentName: "env1",
    eventSourceName: "es1",
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

io_t_hub_event_source = azure_native.timeseriesinsights.IoTHubEventSource("ioTHubEventSource",
    environment_name="env1",
    event_source_name="es1",
    resource_group_name="rg1")

```

```yaml
resources:
  ioTHubEventSource:
    type: azure-native:timeseriesinsights:IoTHubEventSource
    properties:
      environmentName: env1
      eventSourceName: es1
      resourceGroupName: rg1

```

{{% /example %}}
{{% example %}}
### EventSourcesCreateEventHubWithCustomEnquedTime
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var ioTHubEventSource = new AzureNative.TimeSeriesInsights.IoTHubEventSource("ioTHubEventSource", new()
    {
        EnvironmentName = "env1",
        EventSourceName = "es1",
        ResourceGroupName = "rg1",
    });

});


```

```go
package main

import (
	timeseriesinsights "github.com/pulumi/pulumi-azure-native-sdk/timeseriesinsights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := timeseriesinsights.NewIoTHubEventSource(ctx, "ioTHubEventSource", &timeseriesinsights.IoTHubEventSourceArgs{
			EnvironmentName:   pulumi.String("env1"),
			EventSourceName:   pulumi.String("es1"),
			ResourceGroupName: pulumi.String("rg1"),
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
import com.pulumi.azurenative.timeseriesinsights.IoTHubEventSource;
import com.pulumi.azurenative.timeseriesinsights.IoTHubEventSourceArgs;
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
        var ioTHubEventSource = new IoTHubEventSource("ioTHubEventSource", IoTHubEventSourceArgs.builder()        
            .environmentName("env1")
            .eventSourceName("es1")
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const ioTHubEventSource = new azure_native.timeseriesinsights.IoTHubEventSource("ioTHubEventSource", {
    environmentName: "env1",
    eventSourceName: "es1",
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

io_t_hub_event_source = azure_native.timeseriesinsights.IoTHubEventSource("ioTHubEventSource",
    environment_name="env1",
    event_source_name="es1",
    resource_group_name="rg1")

```

```yaml
resources:
  ioTHubEventSource:
    type: azure-native:timeseriesinsights:IoTHubEventSource
    properties:
      environmentName: env1
      eventSourceName: es1
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:timeseriesinsights:IoTHubEventSource es1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.TimeSeriesInsights/Environments/env1/eventSources/es1 
```
