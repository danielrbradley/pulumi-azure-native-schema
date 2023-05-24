Configuration Assignment
API Version: 2022-11-01-preview.
Previous API Version: 2021-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ConfigurationAssignments_CreateOrUpdateParent
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var configurationAssignmentParent = new AzureNative.Maintenance.ConfigurationAssignmentParent("configurationAssignmentParent", new()
    {
        ConfigurationAssignmentName = "workervmPolicy",
        MaintenanceConfigurationId = "/subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourcegroups/examplerg/providers/Microsoft.Maintenance/maintenanceConfigurations/policy1",
        ProviderName = "Microsoft.Compute",
        ResourceGroupName = "examplerg",
        ResourceName = "smdvm1",
        ResourceParentName = "smdtest1",
        ResourceParentType = "virtualMachineScaleSets",
        ResourceType = "virtualMachines",
    });

});


```

```go
package main

import (
	maintenance "github.com/pulumi/pulumi-azure-native-sdk/maintenance"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := maintenance.NewConfigurationAssignmentParent(ctx, "configurationAssignmentParent", &maintenance.ConfigurationAssignmentParentArgs{
			ConfigurationAssignmentName: pulumi.String("workervmPolicy"),
			MaintenanceConfigurationId:  pulumi.String("/subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourcegroups/examplerg/providers/Microsoft.Maintenance/maintenanceConfigurations/policy1"),
			ProviderName:                pulumi.String("Microsoft.Compute"),
			ResourceGroupName:           pulumi.String("examplerg"),
			ResourceName:                pulumi.String("smdvm1"),
			ResourceParentName:          pulumi.String("smdtest1"),
			ResourceParentType:          pulumi.String("virtualMachineScaleSets"),
			ResourceType:                pulumi.String("virtualMachines"),
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
import com.pulumi.azurenative.maintenance.ConfigurationAssignmentParent;
import com.pulumi.azurenative.maintenance.ConfigurationAssignmentParentArgs;
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
        var configurationAssignmentParent = new ConfigurationAssignmentParent("configurationAssignmentParent", ConfigurationAssignmentParentArgs.builder()        
            .configurationAssignmentName("workervmPolicy")
            .maintenanceConfigurationId("/subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourcegroups/examplerg/providers/Microsoft.Maintenance/maintenanceConfigurations/policy1")
            .providerName("Microsoft.Compute")
            .resourceGroupName("examplerg")
            .resourceName("smdvm1")
            .resourceParentName("smdtest1")
            .resourceParentType("virtualMachineScaleSets")
            .resourceType("virtualMachines")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const configurationAssignmentParent = new azure_native.maintenance.ConfigurationAssignmentParent("configurationAssignmentParent", {
    configurationAssignmentName: "workervmPolicy",
    maintenanceConfigurationId: "/subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourcegroups/examplerg/providers/Microsoft.Maintenance/maintenanceConfigurations/policy1",
    providerName: "Microsoft.Compute",
    resourceGroupName: "examplerg",
    resourceName: "smdvm1",
    resourceParentName: "smdtest1",
    resourceParentType: "virtualMachineScaleSets",
    resourceType: "virtualMachines",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

configuration_assignment_parent = azure_native.maintenance.ConfigurationAssignmentParent("configurationAssignmentParent",
    configuration_assignment_name="workervmPolicy",
    maintenance_configuration_id="/subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourcegroups/examplerg/providers/Microsoft.Maintenance/maintenanceConfigurations/policy1",
    provider_name="Microsoft.Compute",
    resource_group_name="examplerg",
    resource_name_="smdvm1",
    resource_parent_name="smdtest1",
    resource_parent_type="virtualMachineScaleSets",
    resource_type="virtualMachines")

```

```yaml
resources:
  configurationAssignmentParent:
    type: azure-native:maintenance:ConfigurationAssignmentParent
    properties:
      configurationAssignmentName: workervmPolicy
      maintenanceConfigurationId: /subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourcegroups/examplerg/providers/Microsoft.Maintenance/maintenanceConfigurations/policy1
      providerName: Microsoft.Compute
      resourceGroupName: examplerg
      resourceName: smdvm1
      resourceParentName: smdtest1
      resourceParentType: virtualMachineScaleSets
      resourceType: virtualMachines

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:maintenance:ConfigurationAssignmentParent workervmPolicy /subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourcegroups/examplerg/providers/Microsoft.Compute/virtualMachineScaleSets/smdtest1/virtualMachines/smdvm1/providers/Microsoft.Maintenance/configurationAssignments/workervmPolicy 
```
