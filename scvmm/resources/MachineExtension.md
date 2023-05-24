Describes a Machine Extension.
API Version: 2022-05-21-preview.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or Update a Machine Extension (PUT)
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var machineExtension = new AzureNative.ScVmm.MachineExtension("machineExtension", new()
    {
        ExtensionName = "CustomScriptExtension",
        Location = "eastus2euap",
        Publisher = "Microsoft.Compute",
        ResourceGroupName = "myResourceGroup",
        Settings = 
        {
            { "commandToExecute", "powershell.exe -c \"Get-Process | Where-Object { $_.CPU -gt 10000 }\"" },
        },
        Type = "CustomScriptExtension",
        TypeHandlerVersion = "1.10",
        VirtualMachineName = "myMachine",
    });

});


```

```go
package main

import (
	scvmm "github.com/pulumi/pulumi-azure-native-sdk/scvmm"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := scvmm.NewMachineExtension(ctx, "machineExtension", &scvmm.MachineExtensionArgs{
			ExtensionName:     pulumi.String("CustomScriptExtension"),
			Location:          pulumi.String("eastus2euap"),
			Publisher:         pulumi.String("Microsoft.Compute"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			Settings: pulumi.Any{
				CommandToExecute: "powershell.exe -c \"Get-Process | Where-Object { $_.CPU -gt 10000 }\"",
			},
			Type:               pulumi.String("CustomScriptExtension"),
			TypeHandlerVersion: pulumi.String("1.10"),
			VirtualMachineName: pulumi.String("myMachine"),
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
import com.pulumi.azurenative.scvmm.MachineExtension;
import com.pulumi.azurenative.scvmm.MachineExtensionArgs;
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
        var machineExtension = new MachineExtension("machineExtension", MachineExtensionArgs.builder()        
            .extensionName("CustomScriptExtension")
            .location("eastus2euap")
            .publisher("Microsoft.Compute")
            .resourceGroupName("myResourceGroup")
            .settings(Map.of("commandToExecute", "powershell.exe -c \"Get-Process | Where-Object { $_.CPU -gt 10000 }\""))
            .type("CustomScriptExtension")
            .typeHandlerVersion("1.10")
            .virtualMachineName("myMachine")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const machineExtension = new azure_native.scvmm.MachineExtension("machineExtension", {
    extensionName: "CustomScriptExtension",
    location: "eastus2euap",
    publisher: "Microsoft.Compute",
    resourceGroupName: "myResourceGroup",
    settings: {
        commandToExecute: "powershell.exe -c \"Get-Process | Where-Object { $_.CPU -gt 10000 }\"",
    },
    type: "CustomScriptExtension",
    typeHandlerVersion: "1.10",
    virtualMachineName: "myMachine",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

machine_extension = azure_native.scvmm.MachineExtension("machineExtension",
    extension_name="CustomScriptExtension",
    location="eastus2euap",
    publisher="Microsoft.Compute",
    resource_group_name="myResourceGroup",
    settings={
        "commandToExecute": "powershell.exe -c \"Get-Process | Where-Object { $_.CPU -gt 10000 }\"",
    },
    type="CustomScriptExtension",
    type_handler_version="1.10",
    virtual_machine_name="myMachine")

```

```yaml
resources:
  machineExtension:
    type: azure-native:scvmm:MachineExtension
    properties:
      extensionName: CustomScriptExtension
      location: eastus2euap
      publisher: Microsoft.Compute
      resourceGroupName: myResourceGroup
      settings:
        commandToExecute: powershell.exe -c "Get-Process | Where-Object { $_.CPU -gt 10000 }"
      type: CustomScriptExtension
      typeHandlerVersion: '1.10'
      virtualMachineName: myMachine

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:scvmm:MachineExtension CustomScriptExtension /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.HybridCompute/Machines/myMachine/Extensions/CustomScriptExtension 
```
