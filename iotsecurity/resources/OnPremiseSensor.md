On-premise IoT sensor
API Version: 2021-02-01-preview.
Previous API Version: 2021-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update on-premise IoT sensor
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var onPremiseSensor = new AzureNative.IoTSecurity.OnPremiseSensor("onPremiseSensor", new()
    {
        OnPremiseSensorName = "mySensor",
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
		_, err := iotsecurity.NewOnPremiseSensor(ctx, "onPremiseSensor", &iotsecurity.OnPremiseSensorArgs{
			OnPremiseSensorName: pulumi.String("mySensor"),
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
import com.pulumi.azurenative.iotsecurity.OnPremiseSensor;
import com.pulumi.azurenative.iotsecurity.OnPremiseSensorArgs;
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
        var onPremiseSensor = new OnPremiseSensor("onPremiseSensor", OnPremiseSensorArgs.builder()        
            .onPremiseSensorName("mySensor")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const onPremiseSensor = new azure_native.iotsecurity.OnPremiseSensor("onPremiseSensor", {onPremiseSensorName: "mySensor"});

```

```python
import pulumi
import pulumi_azure_native as azure_native

on_premise_sensor = azure_native.iotsecurity.OnPremiseSensor("onPremiseSensor", on_premise_sensor_name="mySensor")

```

```yaml
resources:
  onPremiseSensor:
    type: azure-native:iotsecurity:OnPremiseSensor
    properties:
      onPremiseSensorName: mySensor

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:iotsecurity:OnPremiseSensor mySensor /subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/providers/Microsoft.IoTSecurity/sensors/mySensor 
```
