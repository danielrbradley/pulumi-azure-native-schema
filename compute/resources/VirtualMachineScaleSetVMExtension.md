Describes a VMSS VM Extension.
API Version: 2022-11-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create VirtualMachineScaleSet VM extension.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSetVMExtension = new AzureNative.Compute.VirtualMachineScaleSetVMExtension("virtualMachineScaleSetVMExtension", new()
    {
        AutoUpgradeMinorVersion = true,
        InstanceId = "0",
        Publisher = "extPublisher",
        ResourceGroupName = "myResourceGroup",
        Settings = 
        {
            { "UserName", "xyz@microsoft.com" },
        },
        Type = "extType",
        TypeHandlerVersion = "1.2",
        VmExtensionName = "myVMExtension",
        VmScaleSetName = "myvmScaleSet",
    });

});


```

```go
package main

import (
	compute "github.com/pulumi/pulumi-azure-native-sdk/compute"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := compute.NewVirtualMachineScaleSetVMExtension(ctx, "virtualMachineScaleSetVMExtension", &compute.VirtualMachineScaleSetVMExtensionArgs{
			AutoUpgradeMinorVersion: pulumi.Bool(true),
			InstanceId:              pulumi.String("0"),
			Publisher:               pulumi.String("extPublisher"),
			ResourceGroupName:       pulumi.String("myResourceGroup"),
			Settings: pulumi.Any{
				UserName: "xyz@microsoft.com",
			},
			Type:               pulumi.String("extType"),
			TypeHandlerVersion: pulumi.String("1.2"),
			VmExtensionName:    pulumi.String("myVMExtension"),
			VmScaleSetName:     pulumi.String("myvmScaleSet"),
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
import com.pulumi.azurenative.compute.VirtualMachineScaleSetVMExtension;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetVMExtensionArgs;
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
        var virtualMachineScaleSetVMExtension = new VirtualMachineScaleSetVMExtension("virtualMachineScaleSetVMExtension", VirtualMachineScaleSetVMExtensionArgs.builder()        
            .autoUpgradeMinorVersion(true)
            .instanceId("0")
            .publisher("extPublisher")
            .resourceGroupName("myResourceGroup")
            .settings(Map.of("UserName", "xyz@microsoft.com"))
            .type("extType")
            .typeHandlerVersion("1.2")
            .vmExtensionName("myVMExtension")
            .vmScaleSetName("myvmScaleSet")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSetVMExtension = new azure_native.compute.VirtualMachineScaleSetVMExtension("virtualMachineScaleSetVMExtension", {
    autoUpgradeMinorVersion: true,
    instanceId: "0",
    publisher: "extPublisher",
    resourceGroupName: "myResourceGroup",
    settings: {
        UserName: "xyz@microsoft.com",
    },
    type: "extType",
    typeHandlerVersion: "1.2",
    vmExtensionName: "myVMExtension",
    vmScaleSetName: "myvmScaleSet",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set_vm_extension = azure_native.compute.VirtualMachineScaleSetVMExtension("virtualMachineScaleSetVMExtension",
    auto_upgrade_minor_version=True,
    instance_id="0",
    publisher="extPublisher",
    resource_group_name="myResourceGroup",
    settings={
        "UserName": "xyz@microsoft.com",
    },
    type="extType",
    type_handler_version="1.2",
    vm_extension_name="myVMExtension",
    vm_scale_set_name="myvmScaleSet")

```

```yaml
resources:
  virtualMachineScaleSetVMExtension:
    type: azure-native:compute:VirtualMachineScaleSetVMExtension
    properties:
      autoUpgradeMinorVersion: true
      instanceId: '0'
      publisher: extPublisher
      resourceGroupName: myResourceGroup
      settings:
        UserName: xyz@microsoft.com
      type: extType
      typeHandlerVersion: '1.2'
      vmExtensionName: myVMExtension
      vmScaleSetName: myvmScaleSet

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:compute:VirtualMachineScaleSetVMExtension myVMExtension /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/virtualMachineScaleSets/myvmScaleSet/virtualMachines/0/extensions/myVMExtension 
```
