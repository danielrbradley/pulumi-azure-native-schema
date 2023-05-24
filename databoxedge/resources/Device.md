The Data Box Edge/Gateway device.
API Version: 2022-03-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### DataBoxEdgeDevicePut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var device = new AzureNative.DataBoxEdge.Device("device", new()
    {
        DeviceName = "testedgedevice",
        Location = "WUS",
        ResourceGroupName = "GroupForEdgeAutomation",
        Sku = new AzureNative.DataBoxEdge.Inputs.SkuArgs
        {
            Name = "Edge",
            Tier = "Standard",
        },
        Tags = null,
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
		_, err := databoxedge.NewDevice(ctx, "device", &databoxedge.DeviceArgs{
			DeviceName:        pulumi.String("testedgedevice"),
			Location:          pulumi.String("WUS"),
			ResourceGroupName: pulumi.String("GroupForEdgeAutomation"),
			Sku: &databoxedge.SkuArgs{
				Name: pulumi.String("Edge"),
				Tier: pulumi.String("Standard"),
			},
			Tags: nil,
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
import com.pulumi.azurenative.databoxedge.Device;
import com.pulumi.azurenative.databoxedge.DeviceArgs;
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
            .deviceName("testedgedevice")
            .location("WUS")
            .resourceGroupName("GroupForEdgeAutomation")
            .sku(Map.ofEntries(
                Map.entry("name", "Edge"),
                Map.entry("tier", "Standard")
            ))
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const device = new azure_native.databoxedge.Device("device", {
    deviceName: "testedgedevice",
    location: "WUS",
    resourceGroupName: "GroupForEdgeAutomation",
    sku: {
        name: "Edge",
        tier: "Standard",
    },
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

device = azure_native.databoxedge.Device("device",
    device_name="testedgedevice",
    location="WUS",
    resource_group_name="GroupForEdgeAutomation",
    sku=azure_native.databoxedge.SkuArgs(
        name="Edge",
        tier="Standard",
    ),
    tags={})

```

```yaml
resources:
  device:
    type: azure-native:databoxedge:Device
    properties:
      deviceName: testedgedevice
      location: WUS
      resourceGroupName: GroupForEdgeAutomation
      sku:
        name: Edge
        tier: Standard
      tags: {}

```

{{% /example %}}
{{% example %}}
### DataBoxEdgeDevicePutWithDataResidency
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var device = new AzureNative.DataBoxEdge.Device("device", new()
    {
        DataResidency = new AzureNative.DataBoxEdge.Inputs.DataResidencyArgs
        {
            Type = "ZoneReplication",
        },
        DeviceName = "testedgedevice",
        Location = "WUS",
        ResourceGroupName = "GroupForEdgeAutomation",
        Sku = new AzureNative.DataBoxEdge.Inputs.SkuArgs
        {
            Name = "Edge",
            Tier = "Standard",
        },
        Tags = null,
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
		_, err := databoxedge.NewDevice(ctx, "device", &databoxedge.DeviceArgs{
			DataResidency: &databoxedge.DataResidencyArgs{
				Type: pulumi.String("ZoneReplication"),
			},
			DeviceName:        pulumi.String("testedgedevice"),
			Location:          pulumi.String("WUS"),
			ResourceGroupName: pulumi.String("GroupForEdgeAutomation"),
			Sku: &databoxedge.SkuArgs{
				Name: pulumi.String("Edge"),
				Tier: pulumi.String("Standard"),
			},
			Tags: nil,
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
import com.pulumi.azurenative.databoxedge.Device;
import com.pulumi.azurenative.databoxedge.DeviceArgs;
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
            .dataResidency(Map.of("type", "ZoneReplication"))
            .deviceName("testedgedevice")
            .location("WUS")
            .resourceGroupName("GroupForEdgeAutomation")
            .sku(Map.ofEntries(
                Map.entry("name", "Edge"),
                Map.entry("tier", "Standard")
            ))
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const device = new azure_native.databoxedge.Device("device", {
    dataResidency: {
        type: "ZoneReplication",
    },
    deviceName: "testedgedevice",
    location: "WUS",
    resourceGroupName: "GroupForEdgeAutomation",
    sku: {
        name: "Edge",
        tier: "Standard",
    },
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

device = azure_native.databoxedge.Device("device",
    data_residency=azure_native.databoxedge.DataResidencyArgs(
        type="ZoneReplication",
    ),
    device_name="testedgedevice",
    location="WUS",
    resource_group_name="GroupForEdgeAutomation",
    sku=azure_native.databoxedge.SkuArgs(
        name="Edge",
        tier="Standard",
    ),
    tags={})

```

```yaml
resources:
  device:
    type: azure-native:databoxedge:Device
    properties:
      dataResidency:
        type: ZoneReplication
      deviceName: testedgedevice
      location: WUS
      resourceGroupName: GroupForEdgeAutomation
      sku:
        name: Edge
        tier: Standard
      tags: {}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:databoxedge:Device testedgedevice /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/{deviceName} 
```
