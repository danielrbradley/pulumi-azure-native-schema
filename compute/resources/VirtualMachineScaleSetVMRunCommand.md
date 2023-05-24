Describes a Virtual Machine run command.
API Version: 2022-11-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create VirtualMachineScaleSet VM run command.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSetVMRunCommand = new AzureNative.Compute.VirtualMachineScaleSetVMRunCommand("virtualMachineScaleSetVMRunCommand", new()
    {
        AsyncExecution = false,
        InstanceId = "0",
        Location = "West US",
        Parameters = new[]
        {
            new AzureNative.Compute.Inputs.RunCommandInputParameterArgs
            {
                Name = "param1",
                Value = "value1",
            },
            new AzureNative.Compute.Inputs.RunCommandInputParameterArgs
            {
                Name = "param2",
                Value = "value2",
            },
        },
        ResourceGroupName = "myResourceGroup",
        RunAsPassword = "<runAsPassword>",
        RunAsUser = "user1",
        RunCommandName = "myRunCommand",
        Source = new AzureNative.Compute.Inputs.VirtualMachineRunCommandScriptSourceArgs
        {
            Script = "Write-Host Hello World!",
        },
        TimeoutInSeconds = 3600,
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
		_, err := compute.NewVirtualMachineScaleSetVMRunCommand(ctx, "virtualMachineScaleSetVMRunCommand", &compute.VirtualMachineScaleSetVMRunCommandArgs{
			AsyncExecution: pulumi.Bool(false),
			InstanceId:     pulumi.String("0"),
			Location:       pulumi.String("West US"),
			Parameters: []compute.RunCommandInputParameterArgs{
				{
					Name:  pulumi.String("param1"),
					Value: pulumi.String("value1"),
				},
				{
					Name:  pulumi.String("param2"),
					Value: pulumi.String("value2"),
				},
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
			RunAsPassword:     pulumi.String("<runAsPassword>"),
			RunAsUser:         pulumi.String("user1"),
			RunCommandName:    pulumi.String("myRunCommand"),
			Source: &compute.VirtualMachineRunCommandScriptSourceArgs{
				Script: pulumi.String("Write-Host Hello World!"),
			},
			TimeoutInSeconds: pulumi.Int(3600),
			VmScaleSetName:   pulumi.String("myvmScaleSet"),
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
import com.pulumi.azurenative.compute.VirtualMachineScaleSetVMRunCommand;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetVMRunCommandArgs;
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
        var virtualMachineScaleSetVMRunCommand = new VirtualMachineScaleSetVMRunCommand("virtualMachineScaleSetVMRunCommand", VirtualMachineScaleSetVMRunCommandArgs.builder()        
            .asyncExecution(false)
            .instanceId("0")
            .location("West US")
            .parameters(            
                Map.ofEntries(
                    Map.entry("name", "param1"),
                    Map.entry("value", "value1")
                ),
                Map.ofEntries(
                    Map.entry("name", "param2"),
                    Map.entry("value", "value2")
                ))
            .resourceGroupName("myResourceGroup")
            .runAsPassword("<runAsPassword>")
            .runAsUser("user1")
            .runCommandName("myRunCommand")
            .source(Map.of("script", "Write-Host Hello World!"))
            .timeoutInSeconds(3600)
            .vmScaleSetName("myvmScaleSet")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSetVMRunCommand = new azure_native.compute.VirtualMachineScaleSetVMRunCommand("virtualMachineScaleSetVMRunCommand", {
    asyncExecution: false,
    instanceId: "0",
    location: "West US",
    parameters: [
        {
            name: "param1",
            value: "value1",
        },
        {
            name: "param2",
            value: "value2",
        },
    ],
    resourceGroupName: "myResourceGroup",
    runAsPassword: "<runAsPassword>",
    runAsUser: "user1",
    runCommandName: "myRunCommand",
    source: {
        script: "Write-Host Hello World!",
    },
    timeoutInSeconds: 3600,
    vmScaleSetName: "myvmScaleSet",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set_vm_run_command = azure_native.compute.VirtualMachineScaleSetVMRunCommand("virtualMachineScaleSetVMRunCommand",
    async_execution=False,
    instance_id="0",
    location="West US",
    parameters=[
        azure_native.compute.RunCommandInputParameterArgs(
            name="param1",
            value="value1",
        ),
        azure_native.compute.RunCommandInputParameterArgs(
            name="param2",
            value="value2",
        ),
    ],
    resource_group_name="myResourceGroup",
    run_as_password="<runAsPassword>",
    run_as_user="user1",
    run_command_name="myRunCommand",
    source=azure_native.compute.VirtualMachineRunCommandScriptSourceArgs(
        script="Write-Host Hello World!",
    ),
    timeout_in_seconds=3600,
    vm_scale_set_name="myvmScaleSet")

```

```yaml
resources:
  virtualMachineScaleSetVMRunCommand:
    type: azure-native:compute:VirtualMachineScaleSetVMRunCommand
    properties:
      asyncExecution: false
      instanceId: '0'
      location: West US
      parameters:
        - name: param1
          value: value1
        - name: param2
          value: value2
      resourceGroupName: myResourceGroup
      runAsPassword: <runAsPassword>
      runAsUser: user1
      runCommandName: myRunCommand
      source:
        script: Write-Host Hello World!
      timeoutInSeconds: 3600
      vmScaleSetName: myvmScaleSet

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:compute:VirtualMachineScaleSetVMRunCommand myRunCommand /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/virtualMachineScaleSets/myvmScaleSet/virtualMachines/0/runCommands/myRunCommand 
```
