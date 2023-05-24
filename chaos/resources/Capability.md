Model that represents a Capability resource.
API Version: 2022-10-01-preview.
Previous API Version: 2021-09-15-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create/update a Capability that extends a virtual machine Target resource.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var capability = new AzureNative.Chaos.Capability("capability", new()
    {
        CapabilityName = "Shutdown-1.0",
        ParentProviderNamespace = "Microsoft.Compute",
        ParentResourceName = "exampleVM",
        ParentResourceType = "virtualMachines",
        ResourceGroupName = "exampleRG",
        TargetName = "Microsoft-VirtualMachine",
    });

});


```

```go
package main

import (
	chaos "github.com/pulumi/pulumi-azure-native-sdk/chaos"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := chaos.NewCapability(ctx, "capability", &chaos.CapabilityArgs{
			CapabilityName:          pulumi.String("Shutdown-1.0"),
			ParentProviderNamespace: pulumi.String("Microsoft.Compute"),
			ParentResourceName:      pulumi.String("exampleVM"),
			ParentResourceType:      pulumi.String("virtualMachines"),
			ResourceGroupName:       pulumi.String("exampleRG"),
			TargetName:              pulumi.String("Microsoft-VirtualMachine"),
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
import com.pulumi.azurenative.chaos.Capability;
import com.pulumi.azurenative.chaos.CapabilityArgs;
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
        var capability = new Capability("capability", CapabilityArgs.builder()        
            .capabilityName("Shutdown-1.0")
            .parentProviderNamespace("Microsoft.Compute")
            .parentResourceName("exampleVM")
            .parentResourceType("virtualMachines")
            .resourceGroupName("exampleRG")
            .targetName("Microsoft-VirtualMachine")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const capability = new azure_native.chaos.Capability("capability", {
    capabilityName: "Shutdown-1.0",
    parentProviderNamespace: "Microsoft.Compute",
    parentResourceName: "exampleVM",
    parentResourceType: "virtualMachines",
    resourceGroupName: "exampleRG",
    targetName: "Microsoft-VirtualMachine",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

capability = azure_native.chaos.Capability("capability",
    capability_name="Shutdown-1.0",
    parent_provider_namespace="Microsoft.Compute",
    parent_resource_name="exampleVM",
    parent_resource_type="virtualMachines",
    resource_group_name="exampleRG",
    target_name="Microsoft-VirtualMachine")

```

```yaml
resources:
  capability:
    type: azure-native:chaos:Capability
    properties:
      capabilityName: Shutdown-1.0
      parentProviderNamespace: Microsoft.Compute
      parentResourceName: exampleVM
      parentResourceType: virtualMachines
      resourceGroupName: exampleRG
      targetName: Microsoft-VirtualMachine

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:chaos:Capability Shutdown-1.0 /subscriptions/6b052e15-03d3-4f17-b2e1-be7f07588291/resourceGroups/exampleRG/providers/Microsoft.Compute/virtualMachines/exampleVM/providers/Microsoft.Chaos/targets/Microsoft-VirtualMachine/capabilities/Shutdown-1.0 
```
