Defines the NetworkInterface resource.
API Version: 2023-02-01-preview.
Previous API Version: 2023-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### NetworkInterfaces_Create_MaximumSet_Gen
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var networkInterface = new AzureNative.ManagedNetworkFabric.NetworkInterface("networkInterface", new()
    {
        Annotation = "null",
        NetworkDeviceName = "networkDeviceName",
        NetworkInterfaceName = "networkInterfaceName",
        ResourceGroupName = "resourceGroupName",
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
		_, err := managednetworkfabric.NewNetworkInterface(ctx, "networkInterface", &managednetworkfabric.NetworkInterfaceArgs{
			Annotation:           pulumi.String("null"),
			NetworkDeviceName:    pulumi.String("networkDeviceName"),
			NetworkInterfaceName: pulumi.String("networkInterfaceName"),
			ResourceGroupName:    pulumi.String("resourceGroupName"),
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
import com.pulumi.azurenative.managednetworkfabric.NetworkInterface;
import com.pulumi.azurenative.managednetworkfabric.NetworkInterfaceArgs;
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
        var networkInterface = new NetworkInterface("networkInterface", NetworkInterfaceArgs.builder()        
            .annotation("null")
            .networkDeviceName("networkDeviceName")
            .networkInterfaceName("networkInterfaceName")
            .resourceGroupName("resourceGroupName")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const networkInterface = new azure_native.managednetworkfabric.NetworkInterface("networkInterface", {
    annotation: "null",
    networkDeviceName: "networkDeviceName",
    networkInterfaceName: "networkInterfaceName",
    resourceGroupName: "resourceGroupName",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

network_interface = azure_native.managednetworkfabric.NetworkInterface("networkInterface",
    annotation="null",
    network_device_name="networkDeviceName",
    network_interface_name="networkInterfaceName",
    resource_group_name="resourceGroupName")

```

```yaml
resources:
  networkInterface:
    type: azure-native:managednetworkfabric:NetworkInterface
    properties:
      annotation: null
      networkDeviceName: networkDeviceName
      networkInterfaceName: networkInterfaceName
      resourceGroupName: resourceGroupName

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:managednetworkfabric:NetworkInterface networkInterfaceName /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkDevices/networkDeviceName/networkInterfaces/networkInterfaceName 
```
