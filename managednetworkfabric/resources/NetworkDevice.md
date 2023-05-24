The NetworkDevice resource definition.
API Version: 2023-02-01-preview.
Previous API Version: 2023-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### NetworkDevices_Create_MaximumSet_Gen
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var networkDevice = new AzureNative.ManagedNetworkFabric.NetworkDevice("networkDevice", new()
    {
        Annotation = "null",
        HostName = "networkDeviceName",
        Location = "eastus",
        NetworkDeviceName = "networkDeviceName",
        NetworkDeviceRole = "CE",
        NetworkDeviceSku = "DefaultSku",
        ResourceGroupName = "resourceGroupName",
        SerialNumber = "Arista;DCS-7280PR3-24;12.05;JPE21330382",
        Tags = 
        {
            { "keyID", "keyValue" },
        },
    });

});


```

```go
package main

import (
	managednetworkfabric "github.com/pulumi/pulumi-azure-native-sdk/managednetworkfabric"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := managednetworkfabric.NewNetworkDevice(ctx, "networkDevice", &managednetworkfabric.NetworkDeviceArgs{
			Annotation:        pulumi.String("null"),
			HostName:          pulumi.String("networkDeviceName"),
			Location:          pulumi.String("eastus"),
			NetworkDeviceName: pulumi.String("networkDeviceName"),
			NetworkDeviceRole: pulumi.String("CE"),
			NetworkDeviceSku:  pulumi.String("DefaultSku"),
			ResourceGroupName: pulumi.String("resourceGroupName"),
			SerialNumber:      pulumi.String("Arista;DCS-7280PR3-24;12.05;JPE21330382"),
			Tags: pulumi.StringMap{
				"keyID": pulumi.String("keyValue"),
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
import com.pulumi.azurenative.managednetworkfabric.NetworkDevice;
import com.pulumi.azurenative.managednetworkfabric.NetworkDeviceArgs;
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
        var networkDevice = new NetworkDevice("networkDevice", NetworkDeviceArgs.builder()        
            .annotation("null")
            .hostName("networkDeviceName")
            .location("eastus")
            .networkDeviceName("networkDeviceName")
            .networkDeviceRole("CE")
            .networkDeviceSku("DefaultSku")
            .resourceGroupName("resourceGroupName")
            .serialNumber("Arista;DCS-7280PR3-24;12.05;JPE21330382")
            .tags(Map.of("keyID", "keyValue"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const networkDevice = new azure_native.managednetworkfabric.NetworkDevice("networkDevice", {
    annotation: "null",
    hostName: "networkDeviceName",
    location: "eastus",
    networkDeviceName: "networkDeviceName",
    networkDeviceRole: "CE",
    networkDeviceSku: "DefaultSku",
    resourceGroupName: "resourceGroupName",
    serialNumber: "Arista;DCS-7280PR3-24;12.05;JPE21330382",
    tags: {
        keyID: "keyValue",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

network_device = azure_native.managednetworkfabric.NetworkDevice("networkDevice",
    annotation="null",
    host_name="networkDeviceName",
    location="eastus",
    network_device_name="networkDeviceName",
    network_device_role="CE",
    network_device_sku="DefaultSku",
    resource_group_name="resourceGroupName",
    serial_number="Arista;DCS-7280PR3-24;12.05;JPE21330382",
    tags={
        "keyID": "keyValue",
    })

```

```yaml
resources:
  networkDevice:
    type: azure-native:managednetworkfabric:NetworkDevice
    properties:
      annotation: null
      hostName: networkDeviceName
      location: eastus
      networkDeviceName: networkDeviceName
      networkDeviceRole: CE
      networkDeviceSku: DefaultSku
      resourceGroupName: resourceGroupName
      serialNumber: Arista;DCS-7280PR3-24;12.05;JPE21330382
      tags:
        keyID: keyValue

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:managednetworkfabric:NetworkDevice networkDeviceName /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkDevices/networkDeviceName 
```
