IoT sensor model
API Version: 2021-02-01-preview.
Previous API Version: 2021-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update IoT sensor
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sensor = new AzureNative.IoTSecurity.Sensor("sensor", new()
    {
        Scope = "subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/myRg/providers/Microsoft.Devices/IotHubs/myHub",
        SensorName = "mySensor",
        SensorType = "Ot",
        TiAutomaticUpdates = true,
        Zone = "Zone Name",
    });

});


```

```go
package main

import (
	iotsecurity "github.com/pulumi/pulumi-azure-native-sdk/iotsecurity"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := iotsecurity.NewSensor(ctx, "sensor", &iotsecurity.SensorArgs{
			Scope:              pulumi.String("subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/myRg/providers/Microsoft.Devices/IotHubs/myHub"),
			SensorName:         pulumi.String("mySensor"),
			SensorType:         pulumi.String("Ot"),
			TiAutomaticUpdates: pulumi.Bool(true),
			Zone:               pulumi.String("Zone Name"),
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
import com.pulumi.azurenative.iotsecurity.Sensor;
import com.pulumi.azurenative.iotsecurity.SensorArgs;
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
        var sensor = new Sensor("sensor", SensorArgs.builder()        
            .scope("subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/myRg/providers/Microsoft.Devices/IotHubs/myHub")
            .sensorName("mySensor")
            .sensorType("Ot")
            .tiAutomaticUpdates(true)
            .zone("Zone Name")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sensor = new azure_native.iotsecurity.Sensor("sensor", {
    scope: "subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/myRg/providers/Microsoft.Devices/IotHubs/myHub",
    sensorName: "mySensor",
    sensorType: "Ot",
    tiAutomaticUpdates: true,
    zone: "Zone Name",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sensor = azure_native.iotsecurity.Sensor("sensor",
    scope="subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/myRg/providers/Microsoft.Devices/IotHubs/myHub",
    sensor_name="mySensor",
    sensor_type="Ot",
    ti_automatic_updates=True,
    zone="Zone Name")

```

```yaml
resources:
  sensor:
    type: azure-native:iotsecurity:Sensor
    properties:
      scope: subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/myRg/providers/Microsoft.Devices/IotHubs/myHub
      sensorName: mySensor
      sensorType: Ot
      tiAutomaticUpdates: true
      zone: Zone Name

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:iotsecurity:Sensor mySensor /subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/myRg/providers/Microsoft.Devices/IotHubs/myHub/providers/Microsoft.IoTSecurity/sensors/mySensor 
```
