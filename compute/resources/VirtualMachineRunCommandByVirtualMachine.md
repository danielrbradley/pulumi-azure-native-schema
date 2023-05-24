Describes a Virtual Machine run command.
API Version: 2022-11-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a run command.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineRunCommandByVirtualMachine = new AzureNative.Compute.VirtualMachineRunCommandByVirtualMachine("virtualMachineRunCommandByVirtualMachine", new()
    {
        AsyncExecution = false,
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
        VmName = "myVM",
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
		_, err := compute.NewVirtualMachineRunCommandByVirtualMachine(ctx, "virtualMachineRunCommandByVirtualMachine", &compute.VirtualMachineRunCommandByVirtualMachineArgs{
			AsyncExecution: pulumi.Bool(false),
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
			VmName:           pulumi.String("myVM"),
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
import com.pulumi.azurenative.compute.VirtualMachineRunCommandByVirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineRunCommandByVirtualMachineArgs;
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
        var virtualMachineRunCommandByVirtualMachine = new VirtualMachineRunCommandByVirtualMachine("virtualMachineRunCommandByVirtualMachine", VirtualMachineRunCommandByVirtualMachineArgs.builder()        
            .asyncExecution(false)
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
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineRunCommandByVirtualMachine = new azure_native.compute.VirtualMachineRunCommandByVirtualMachine("virtualMachineRunCommandByVirtualMachine", {
    asyncExecution: false,
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
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_run_command_by_virtual_machine = azure_native.compute.VirtualMachineRunCommandByVirtualMachine("virtualMachineRunCommandByVirtualMachine",
    async_execution=False,
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
    vm_name="myVM")

```

```yaml
resources:
  virtualMachineRunCommandByVirtualMachine:
    type: azure-native:compute:VirtualMachineRunCommandByVirtualMachine
    properties:
      asyncExecution: false
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
      vmName: myVM

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:compute:VirtualMachineRunCommandByVirtualMachine myRunCommand /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/virtualMachines/myVM/runCommands/myRunCommand 
```
