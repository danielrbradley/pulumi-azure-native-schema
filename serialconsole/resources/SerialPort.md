Represents the serial port of the parent resource.
API Version: 2018-05-01.
Previous API Version: 2018-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a new serial port resource.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var serialPort = new AzureNative.SerialConsole.SerialPort("serialPort", new()
    {
        ParentResource = "myVM",
        ParentResourceType = "virtualMachines",
        ResourceGroupName = "myResourceGroup",
        ResourceProviderNamespace = "Microsoft.Compute",
        SerialPort = "0",
        State = AzureNative.SerialConsole.SerialPortState.Enabled,
    });

});


```

```go
package main

import (
	serialconsole "github.com/pulumi/pulumi-azure-native-sdk/serialconsole"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := serialconsole.NewSerialPort(ctx, "serialPort", &serialconsole.SerialPortArgs{
			ParentResource:            pulumi.String("myVM"),
			ParentResourceType:        pulumi.String("virtualMachines"),
			ResourceGroupName:         pulumi.String("myResourceGroup"),
			ResourceProviderNamespace: pulumi.String("Microsoft.Compute"),
			SerialPort:                pulumi.String("0"),
			State:                     serialconsole.SerialPortStateEnabled,
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
import com.pulumi.azurenative.serialconsole.SerialPort;
import com.pulumi.azurenative.serialconsole.SerialPortArgs;
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
        var serialPort = new SerialPort("serialPort", SerialPortArgs.builder()        
            .parentResource("myVM")
            .parentResourceType("virtualMachines")
            .resourceGroupName("myResourceGroup")
            .resourceProviderNamespace("Microsoft.Compute")
            .serialPort("0")
            .state("enabled")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const serialPort = new azure_native.serialconsole.SerialPort("serialPort", {
    parentResource: "myVM",
    parentResourceType: "virtualMachines",
    resourceGroupName: "myResourceGroup",
    resourceProviderNamespace: "Microsoft.Compute",
    serialPort: "0",
    state: azure_native.serialconsole.SerialPortState.Enabled,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

serial_port = azure_native.serialconsole.SerialPort("serialPort",
    parent_resource="myVM",
    parent_resource_type="virtualMachines",
    resource_group_name="myResourceGroup",
    resource_provider_namespace="Microsoft.Compute",
    serial_port="0",
    state=azure_native.serialconsole.SerialPortState.ENABLED)

```

```yaml
resources:
  serialPort:
    type: azure-native:serialconsole:SerialPort
    properties:
      parentResource: myVM
      parentResourceType: virtualMachines
      resourceGroupName: myResourceGroup
      resourceProviderNamespace: Microsoft.Compute
      serialPort: '0'
      state: enabled

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:serialconsole:SerialPort 0 /subscriptions/00000000-00000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.Compute/virtualMachines/myVM/providers/Microsoft.SerialConsole/serialPorts/0 
```
