Configuration Assignment
API Version: 2022-11-01-preview.
Previous API Version: 2021-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ConfigurationAssignments_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var configurationAssignment = new AzureNative.Maintenance.ConfigurationAssignment("configurationAssignment", new()
    {
        ConfigurationAssignmentName = "workervmConfiguration",
        MaintenanceConfigurationId = "/subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourcegroups/examplerg/providers/Microsoft.Maintenance/maintenanceConfigurations/configuration1",
        ProviderName = "Microsoft.Compute",
        ResourceGroupName = "examplerg",
        ResourceName = "smdtest1",
        ResourceType = "virtualMachineScaleSets",
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
		_, err := maintenance.NewConfigurationAssignment(ctx, "configurationAssignment", &maintenance.ConfigurationAssignmentArgs{
			ConfigurationAssignmentName: pulumi.String("workervmConfiguration"),
			MaintenanceConfigurationId:  pulumi.String("/subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourcegroups/examplerg/providers/Microsoft.Maintenance/maintenanceConfigurations/configuration1"),
			ProviderName:                pulumi.String("Microsoft.Compute"),
			ResourceGroupName:           pulumi.String("examplerg"),
			ResourceName:                pulumi.String("smdtest1"),
			ResourceType:                pulumi.String("virtualMachineScaleSets"),
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
import com.pulumi.azurenative.maintenance.ConfigurationAssignment;
import com.pulumi.azurenative.maintenance.ConfigurationAssignmentArgs;
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
        var configurationAssignment = new ConfigurationAssignment("configurationAssignment", ConfigurationAssignmentArgs.builder()        
            .configurationAssignmentName("workervmConfiguration")
            .maintenanceConfigurationId("/subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourcegroups/examplerg/providers/Microsoft.Maintenance/maintenanceConfigurations/configuration1")
            .providerName("Microsoft.Compute")
            .resourceGroupName("examplerg")
            .resourceName("smdtest1")
            .resourceType("virtualMachineScaleSets")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const configurationAssignment = new azure_native.maintenance.ConfigurationAssignment("configurationAssignment", {
    configurationAssignmentName: "workervmConfiguration",
    maintenanceConfigurationId: "/subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourcegroups/examplerg/providers/Microsoft.Maintenance/maintenanceConfigurations/configuration1",
    providerName: "Microsoft.Compute",
    resourceGroupName: "examplerg",
    resourceName: "smdtest1",
    resourceType: "virtualMachineScaleSets",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

configuration_assignment = azure_native.maintenance.ConfigurationAssignment("configurationAssignment",
    configuration_assignment_name="workervmConfiguration",
    maintenance_configuration_id="/subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourcegroups/examplerg/providers/Microsoft.Maintenance/maintenanceConfigurations/configuration1",
    provider_name="Microsoft.Compute",
    resource_group_name="examplerg",
    resource_name_="smdtest1",
    resource_type="virtualMachineScaleSets")

```

```yaml
resources:
  configurationAssignment:
    type: azure-native:maintenance:ConfigurationAssignment
    properties:
      configurationAssignmentName: workervmConfiguration
      maintenanceConfigurationId: /subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourcegroups/examplerg/providers/Microsoft.Maintenance/maintenanceConfigurations/configuration1
      providerName: Microsoft.Compute
      resourceGroupName: examplerg
      resourceName: smdtest1
      resourceType: virtualMachineScaleSets

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:maintenance:ConfigurationAssignment workervmConfiguration /subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourcegroups/examplerg/providers/Microsoft.Compute/virtualMachineScaleSets/smdtest1/providers/Microsoft.Maintenance/configurationAssignments/workervmConfiguration 
```
