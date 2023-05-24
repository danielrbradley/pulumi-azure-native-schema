Device resource.
API Version: 2021-05-01.
Previous API Version: 2020-01-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update device
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var device = new AzureNative.HybridNetwork.Device("device", new()
    {
        DeviceName = "TestDevice",
        DeviceType = "AzureStackEdge",
        Location = "eastus",
        ResourceGroupName = "rg1",
    });

});


```

```go
package main

import (
	hybridnetwork "github.com/pulumi/pulumi-azure-native-sdk/hybridnetwork"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := hybridnetwork.NewDevice(ctx, "device", &hybridnetwork.DeviceArgs{
			DeviceName:        pulumi.String("TestDevice"),
			DeviceType:        pulumi.String("AzureStackEdge"),
			Location:          pulumi.String("eastus"),
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
import com.pulumi.azurenative.hybridnetwork.Device;
import com.pulumi.azurenative.hybridnetwork.DeviceArgs;
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
        var device = new Device("device", DeviceArgs.builder()        
            .deviceName("TestDevice")
            .deviceType("AzureStackEdge")
            .location("eastus")
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const device = new azure_native.hybridnetwork.Device("device", {
    deviceName: "TestDevice",
    deviceType: "AzureStackEdge",
    location: "eastus",
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

device = azure_native.hybridnetwork.Device("device",
    device_name="TestDevice",
    device_type="AzureStackEdge",
    location="eastus",
    resource_group_name="rg1")

```

```yaml
resources:
  device:
    type: azure-native:hybridnetwork:Device
    properties:
      deviceName: TestDevice
      deviceType: AzureStackEdge
      location: eastus
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:hybridnetwork:Device TestDevice /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.HybridNetwork/devices/TestDevice 
```
