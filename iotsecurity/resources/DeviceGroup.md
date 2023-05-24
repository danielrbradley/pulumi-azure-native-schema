Device group
API Version: 2021-02-01-preview.
Previous API Version: 2021-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update device group
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var deviceGroup = new AzureNative.IoTSecurity.DeviceGroup("deviceGroup", new()
    {
        DeviceGroupName = "myGroup",
        IotDefenderLocation = "eastus",
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
		_, err := iotsecurity.NewDeviceGroup(ctx, "deviceGroup", &iotsecurity.DeviceGroupArgs{
			DeviceGroupName:     pulumi.String("myGroup"),
			IotDefenderLocation: pulumi.String("eastus"),
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
import com.pulumi.azurenative.iotsecurity.DeviceGroup;
import com.pulumi.azurenative.iotsecurity.DeviceGroupArgs;
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
        var deviceGroup = new DeviceGroup("deviceGroup", DeviceGroupArgs.builder()        
            .deviceGroupName("myGroup")
            .iotDefenderLocation("eastus")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const deviceGroup = new azure_native.iotsecurity.DeviceGroup("deviceGroup", {
    deviceGroupName: "myGroup",
    iotDefenderLocation: "eastus",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

device_group = azure_native.iotsecurity.DeviceGroup("deviceGroup",
    device_group_name="myGroup",
    iot_defender_location="eastus")

```

```yaml
resources:
  deviceGroup:
    type: azure-native:iotsecurity:DeviceGroup
    properties:
      deviceGroupName: myGroup
      iotDefenderLocation: eastus

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:iotsecurity:DeviceGroup myGroup /subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/providers/Microsoft.IoTSecurity/deviceGroups/myGroup 
```
