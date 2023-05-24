Describes a Machine Extension.
API Version: 2022-11-10.
Previous API Version: 2020-08-02. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or Update a Machine Extension
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var machineExtension = new AzureNative.HybridCompute.MachineExtension("machineExtension", new()
    {
        ExtensionName = "CustomScriptExtension",
        Location = "eastus2euap",
        MachineName = "myMachine",
        Publisher = "Microsoft.Compute",
        ResourceGroupName = "myResourceGroup",
        Settings = 
        {
            { "commandToExecute", "powershell.exe -c \"Get-Process | Where-Object { $_.CPU -gt 10000 }\"" },
        },
        Type = "CustomScriptExtension",
        TypeHandlerVersion = "1.10",
    });

});


```

```go
package main

import (
	hybridcompute "github.com/pulumi/pulumi-azure-native-sdk/hybridcompute"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := hybridcompute.NewMachineExtension(ctx, "machineExtension", &hybridcompute.MachineExtensionArgs{
			ExtensionName:     pulumi.String("CustomScriptExtension"),
			Location:          pulumi.String("eastus2euap"),
			MachineName:       pulumi.String("myMachine"),
			Publisher:         pulumi.String("Microsoft.Compute"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			Settings: pulumi.Any{
				CommandToExecute: "powershell.exe -c \"Get-Process | Where-Object { $_.CPU -gt 10000 }\"",
			},
			Type:               pulumi.String("CustomScriptExtension"),
			TypeHandlerVersion: pulumi.String("1.10"),
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
import com.pulumi.azurenative.hybridcompute.MachineExtension;
import com.pulumi.azurenative.hybridcompute.MachineExtensionArgs;
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
            .machineName("myMachine")
            .publisher("Microsoft.Compute")
            .resourceGroupName("myResourceGroup")
            .settings(Map.of("commandToExecute", "powershell.exe -c \"Get-Process | Where-Object { $_.CPU -gt 10000 }\""))
            .type("CustomScriptExtension")
            .typeHandlerVersion("1.10")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const machineExtension = new azure_native.hybridcompute.MachineExtension("machineExtension", {
    extensionName: "CustomScriptExtension",
    location: "eastus2euap",
    machineName: "myMachine",
    publisher: "Microsoft.Compute",
    resourceGroupName: "myResourceGroup",
    settings: {
        commandToExecute: "powershell.exe -c \"Get-Process | Where-Object { $_.CPU -gt 10000 }\"",
    },
    type: "CustomScriptExtension",
    typeHandlerVersion: "1.10",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

machine_extension = azure_native.hybridcompute.MachineExtension("machineExtension",
    extension_name="CustomScriptExtension",
    location="eastus2euap",
    machine_name="myMachine",
    publisher="Microsoft.Compute",
    resource_group_name="myResourceGroup",
    settings={
        "commandToExecute": "powershell.exe -c \"Get-Process | Where-Object { $_.CPU -gt 10000 }\"",
    },
    type="CustomScriptExtension",
    type_handler_version="1.10")

```

```yaml
resources:
  machineExtension:
    type: azure-native:hybridcompute:MachineExtension
    properties:
      extensionName: CustomScriptExtension
      location: eastus2euap
      machineName: myMachine
      publisher: Microsoft.Compute
      resourceGroupName: myResourceGroup
      settings:
        commandToExecute: powershell.exe -c "Get-Process | Where-Object { $_.CPU -gt 10000 }"
      type: CustomScriptExtension
      typeHandlerVersion: '1.10'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:hybridcompute:MachineExtension CustomScriptExtension /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.HybridCompute/Machines/myMachine/Extensions/CustomScriptExtension 
```
