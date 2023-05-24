The description of the provisioning service.
API Version: 2022-12-12.
Previous API Version: 2020-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### DPSCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var iotDpsResource = new AzureNative.Devices.IotDpsResource("iotDpsResource", new()
    {
        Location = "East US",
        Properties = new AzureNative.Devices.Inputs.IotDpsPropertiesDescriptionArgs
        {
            EnableDataResidency = false,
        },
        ProvisioningServiceName = "myFirstProvisioningService",
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Devices.Inputs.IotDpsSkuInfoArgs
        {
            Capacity = 1,
            Name = "S1",
        },
        Tags = null,
    });

});


```

```go
package main

import (
	devices "github.com/pulumi/pulumi-azure-native-sdk/devices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := devices.NewIotDpsResource(ctx, "iotDpsResource", &devices.IotDpsResourceArgs{
			Location: pulumi.String("East US"),
			Properties: &devices.IotDpsPropertiesDescriptionArgs{
				EnableDataResidency: pulumi.Bool(false),
			},
			ProvisioningServiceName: pulumi.String("myFirstProvisioningService"),
			ResourceGroupName:       pulumi.String("myResourceGroup"),
			Sku: &devices.IotDpsSkuInfoArgs{
				Capacity: pulumi.Float64(1),
				Name:     pulumi.String("S1"),
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
import com.pulumi.azurenative.devices.IotDpsResource;
import com.pulumi.azurenative.devices.IotDpsResourceArgs;
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
        var iotDpsResource = new IotDpsResource("iotDpsResource", IotDpsResourceArgs.builder()        
            .location("East US")
            .properties(Map.of("enableDataResidency", false))
            .provisioningServiceName("myFirstProvisioningService")
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 1),
                Map.entry("name", "S1")
            ))
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const iotDpsResource = new azure_native.devices.IotDpsResource("iotDpsResource", {
    location: "East US",
    properties: {
        enableDataResidency: false,
    },
    provisioningServiceName: "myFirstProvisioningService",
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 1,
        name: "S1",
    },
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

iot_dps_resource = azure_native.devices.IotDpsResource("iotDpsResource",
    location="East US",
    properties=azure_native.devices.IotDpsPropertiesDescriptionArgs(
        enable_data_residency=False,
    ),
    provisioning_service_name="myFirstProvisioningService",
    resource_group_name="myResourceGroup",
    sku=azure_native.devices.IotDpsSkuInfoArgs(
        capacity=1,
        name="S1",
    ),
    tags={})

```

```yaml
resources:
  iotDpsResource:
    type: azure-native:devices:IotDpsResource
    properties:
      location: East US
      properties:
        enableDataResidency: false
      provisioningServiceName: myFirstProvisioningService
      resourceGroupName: myResourceGroup
      sku:
        capacity: 1
        name: S1
      tags: {}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devices:IotDpsResource myFirstProvisioningService /subscriptions/91d12660-3dec-467a-be2a-213b5544ddc0/resourceGroups//providers/Microsoft.Devices/ProvisioningServices/myFirstProvisioningService 
```
