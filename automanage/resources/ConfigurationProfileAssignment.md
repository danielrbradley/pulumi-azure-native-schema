Configuration profile assignment is an association between a VM and automanage profile configuration.
API Version: 2022-05-04.
Previous API Version: 2020-06-30-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update configuration profile assignment
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var configurationProfileAssignment = new AzureNative.Automanage.ConfigurationProfileAssignment("configurationProfileAssignment", new()
    {
        ConfigurationProfileAssignmentName = "default",
        Properties = new AzureNative.Automanage.Inputs.ConfigurationProfileAssignmentPropertiesArgs
        {
            ConfigurationProfile = "/providers/Microsoft.Automanage/bestPractices/AzureBestPracticesProduction",
        },
        ResourceGroupName = "myResourceGroupName",
        VmName = "myVMName",
    });

});


```

```go
package main

import (
	automanage "github.com/pulumi/pulumi-azure-native-sdk/automanage"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := automanage.NewConfigurationProfileAssignment(ctx, "configurationProfileAssignment", &automanage.ConfigurationProfileAssignmentArgs{
			ConfigurationProfileAssignmentName: pulumi.String("default"),
			Properties: &automanage.ConfigurationProfileAssignmentPropertiesArgs{
				ConfigurationProfile: pulumi.String("/providers/Microsoft.Automanage/bestPractices/AzureBestPracticesProduction"),
			},
			ResourceGroupName: pulumi.String("myResourceGroupName"),
			VmName:            pulumi.String("myVMName"),
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
import com.pulumi.azurenative.automanage.ConfigurationProfileAssignment;
import com.pulumi.azurenative.automanage.ConfigurationProfileAssignmentArgs;
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
        var configurationProfileAssignment = new ConfigurationProfileAssignment("configurationProfileAssignment", ConfigurationProfileAssignmentArgs.builder()        
            .configurationProfileAssignmentName("default")
            .properties(Map.of("configurationProfile", "/providers/Microsoft.Automanage/bestPractices/AzureBestPracticesProduction"))
            .resourceGroupName("myResourceGroupName")
            .vmName("myVMName")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const configurationProfileAssignment = new azure_native.automanage.ConfigurationProfileAssignment("configurationProfileAssignment", {
    configurationProfileAssignmentName: "default",
    properties: {
        configurationProfile: "/providers/Microsoft.Automanage/bestPractices/AzureBestPracticesProduction",
    },
    resourceGroupName: "myResourceGroupName",
    vmName: "myVMName",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

configuration_profile_assignment = azure_native.automanage.ConfigurationProfileAssignment("configurationProfileAssignment",
    configuration_profile_assignment_name="default",
    properties=azure_native.automanage.ConfigurationProfileAssignmentPropertiesArgs(
        configuration_profile="/providers/Microsoft.Automanage/bestPractices/AzureBestPracticesProduction",
    ),
    resource_group_name="myResourceGroupName",
    vm_name="myVMName")

```

```yaml
resources:
  configurationProfileAssignment:
    type: azure-native:automanage:ConfigurationProfileAssignment
    properties:
      configurationProfileAssignmentName: default
      properties:
        configurationProfile: /providers/Microsoft.Automanage/bestPractices/AzureBestPracticesProduction
      resourceGroupName: myResourceGroupName
      vmName: myVMName

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:automanage:ConfigurationProfileAssignment default /subscriptions/subscriptionId/resourceGroups/myResourceGroupName/providers/Microsoft.Compute/virtualMachines/myVMName/providers/Microsoft.Automanage/configurationProfileAssignments/default 
```
