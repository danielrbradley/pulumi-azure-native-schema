Configuration profile assignment is an association between a VM and automanage profile configuration.
API Version: 2022-05-04.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update HCRP configuration profile assignment
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var configurationProfileHCRPAssignment = new AzureNative.Automanage.ConfigurationProfileHCRPAssignment("configurationProfileHCRPAssignment", new()
    {
        ConfigurationProfileAssignmentName = "default",
        MachineName = "myMachineName",
        Properties = new AzureNative.Automanage.Inputs.ConfigurationProfileAssignmentPropertiesArgs
        {
            ConfigurationProfile = "/providers/Microsoft.Automanage/bestPractices/AzureBestPracticesProduction",
        },
        ResourceGroupName = "myResourceGroupName",
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
		_, err := automanage.NewConfigurationProfileHCRPAssignment(ctx, "configurationProfileHCRPAssignment", &automanage.ConfigurationProfileHCRPAssignmentArgs{
			ConfigurationProfileAssignmentName: pulumi.String("default"),
			MachineName:                        pulumi.String("myMachineName"),
			Properties: &automanage.ConfigurationProfileAssignmentPropertiesArgs{
				ConfigurationProfile: pulumi.String("/providers/Microsoft.Automanage/bestPractices/AzureBestPracticesProduction"),
			},
			ResourceGroupName: pulumi.String("myResourceGroupName"),
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
import com.pulumi.azurenative.automanage.ConfigurationProfileHCRPAssignment;
import com.pulumi.azurenative.automanage.ConfigurationProfileHCRPAssignmentArgs;
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
        var configurationProfileHCRPAssignment = new ConfigurationProfileHCRPAssignment("configurationProfileHCRPAssignment", ConfigurationProfileHCRPAssignmentArgs.builder()        
            .configurationProfileAssignmentName("default")
            .machineName("myMachineName")
            .properties(Map.of("configurationProfile", "/providers/Microsoft.Automanage/bestPractices/AzureBestPracticesProduction"))
            .resourceGroupName("myResourceGroupName")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const configurationProfileHCRPAssignment = new azure_native.automanage.ConfigurationProfileHCRPAssignment("configurationProfileHCRPAssignment", {
    configurationProfileAssignmentName: "default",
    machineName: "myMachineName",
    properties: {
        configurationProfile: "/providers/Microsoft.Automanage/bestPractices/AzureBestPracticesProduction",
    },
    resourceGroupName: "myResourceGroupName",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

configuration_profile_hcrpassignment = azure_native.automanage.ConfigurationProfileHCRPAssignment("configurationProfileHCRPAssignment",
    configuration_profile_assignment_name="default",
    machine_name="myMachineName",
    properties=azure_native.automanage.ConfigurationProfileAssignmentPropertiesArgs(
        configuration_profile="/providers/Microsoft.Automanage/bestPractices/AzureBestPracticesProduction",
    ),
    resource_group_name="myResourceGroupName")

```

```yaml
resources:
  configurationProfileHCRPAssignment:
    type: azure-native:automanage:ConfigurationProfileHCRPAssignment
    properties:
      configurationProfileAssignmentName: default
      machineName: myMachineName
      properties:
        configurationProfile: /providers/Microsoft.Automanage/bestPractices/AzureBestPracticesProduction
      resourceGroupName: myResourceGroupName

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:automanage:ConfigurationProfileHCRPAssignment default /subscriptions/subscriptionId/resourceGroups/myResourceGroupName/providers/Microsoft.HybridCompute/machines/myMachineName/providers/Microsoft.Automanage/configurationProfileAssignments/default 
```
