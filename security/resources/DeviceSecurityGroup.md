The device security group resource
API Version: 2019-08-01.
Previous API Version: 2019-08-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a device security group for the specified IoT hub resource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var deviceSecurityGroup = new AzureNative.Security.DeviceSecurityGroup("deviceSecurityGroup", new()
    {
        DeviceSecurityGroupName = "samplesecuritygroup",
        ResourceId = "subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/SampleRG/providers/Microsoft.Devices/iotHubs/sampleiothub",
        TimeWindowRules = new[]
        {
            null,
        },
    });

});


```

```go
package main

import (
	security "github.com/pulumi/pulumi-azure-native-sdk/security"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := security.NewDeviceSecurityGroup(ctx, "deviceSecurityGroup", &security.DeviceSecurityGroupArgs{
			DeviceSecurityGroupName: pulumi.String("samplesecuritygroup"),
			ResourceId:              pulumi.String("subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/SampleRG/providers/Microsoft.Devices/iotHubs/sampleiothub"),
			TimeWindowRules: []security.TimeWindowCustomAlertRuleArgs{
				nil,
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
import com.pulumi.azurenative.security.DeviceSecurityGroup;
import com.pulumi.azurenative.security.DeviceSecurityGroupArgs;
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
        var deviceSecurityGroup = new DeviceSecurityGroup("deviceSecurityGroup", DeviceSecurityGroupArgs.builder()        
            .deviceSecurityGroupName("samplesecuritygroup")
            .resourceId("subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/SampleRG/providers/Microsoft.Devices/iotHubs/sampleiothub")
            .timeWindowRules()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const deviceSecurityGroup = new azure_native.security.DeviceSecurityGroup("deviceSecurityGroup", {
    deviceSecurityGroupName: "samplesecuritygroup",
    resourceId: "subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/SampleRG/providers/Microsoft.Devices/iotHubs/sampleiothub",
    timeWindowRules: [{}],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

device_security_group = azure_native.security.DeviceSecurityGroup("deviceSecurityGroup",
    device_security_group_name="samplesecuritygroup",
    resource_id="subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/SampleRG/providers/Microsoft.Devices/iotHubs/sampleiothub",
    time_window_rules=[azure_native.security.TimeWindowCustomAlertRuleArgs()])

```

```yaml
resources:
  deviceSecurityGroup:
    type: azure-native:security:DeviceSecurityGroup
    properties:
      deviceSecurityGroupName: samplesecuritygroup
      resourceId: subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/SampleRG/providers/Microsoft.Devices/iotHubs/sampleiothub
      timeWindowRules:
        - {}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:security:DeviceSecurityGroup samplesecuritygroup /subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/SampleRG/providers/Microsoft.Devices/iotHubs/sampleiothub/providers/Microsoft.Security/deviceSecurityGroups/samplesecuritygroup 
```
