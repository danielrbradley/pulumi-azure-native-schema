Guest configuration assignment is an association between a machine and guest configuration.
API Version: 2022-01-25.
Previous API Version: 2020-06-25. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update guest configuration assignment
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var guestConfigurationAssignment = new AzureNative.GuestConfiguration.GuestConfigurationAssignment("guestConfigurationAssignment", new()
    {
        GuestConfigurationAssignmentName = "NotInstalledApplicationForWindows",
        Location = "westcentralus",
        Name = "NotInstalledApplicationForWindows",
        Properties = new AzureNative.GuestConfiguration.Inputs.GuestConfigurationAssignmentPropertiesArgs
        {
            Context = "Azure policy",
            GuestConfiguration = new AzureNative.GuestConfiguration.Inputs.GuestConfigurationNavigationArgs
            {
                AssignmentType = "ApplyAndAutoCorrect",
                ConfigurationParameter = new[]
                {
                    new AzureNative.GuestConfiguration.Inputs.ConfigurationParameterArgs
                    {
                        Name = "[InstalledApplication]NotInstalledApplicationResource1;Name",
                        Value = "NotePad,sql",
                    },
                },
                ContentHash = "123contenthash",
                ContentUri = "https://thisisfake/pacakge",
                Name = "NotInstalledApplicationForWindows",
                Version = "1.0.0.3",
            },
        },
        ResourceGroupName = "myResourceGroupName",
        VmName = "myVMName",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.guestconfiguration.GuestConfigurationAssignment;
import com.pulumi.azurenative.guestconfiguration.GuestConfigurationAssignmentArgs;
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
        var guestConfigurationAssignment = new GuestConfigurationAssignment("guestConfigurationAssignment", GuestConfigurationAssignmentArgs.builder()        
            .guestConfigurationAssignmentName("NotInstalledApplicationForWindows")
            .location("westcentralus")
            .name("NotInstalledApplicationForWindows")
            .properties(Map.ofEntries(
                Map.entry("context", "Azure policy"),
                Map.entry("guestConfiguration", Map.ofEntries(
                    Map.entry("assignmentType", "ApplyAndAutoCorrect"),
                    Map.entry("configurationParameter", Map.ofEntries(
                        Map.entry("name", "[InstalledApplication]NotInstalledApplicationResource1;Name"),
                        Map.entry("value", "NotePad,sql")
                    )),
                    Map.entry("contentHash", "123contenthash"),
                    Map.entry("contentUri", "https://thisisfake/pacakge"),
                    Map.entry("name", "NotInstalledApplicationForWindows"),
                    Map.entry("version", "1.0.0.3")
                ))
            ))
            .resourceGroupName("myResourceGroupName")
            .vmName("myVMName")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const guestConfigurationAssignment = new azure_native.guestconfiguration.GuestConfigurationAssignment("guestConfigurationAssignment", {
    guestConfigurationAssignmentName: "NotInstalledApplicationForWindows",
    location: "westcentralus",
    name: "NotInstalledApplicationForWindows",
    properties: {
        context: "Azure policy",
        guestConfiguration: {
            assignmentType: "ApplyAndAutoCorrect",
            configurationParameter: [{
                name: "[InstalledApplication]NotInstalledApplicationResource1;Name",
                value: "NotePad,sql",
            }],
            contentHash: "123contenthash",
            contentUri: "https://thisisfake/pacakge",
            name: "NotInstalledApplicationForWindows",
            version: "1.0.0.3",
        },
    },
    resourceGroupName: "myResourceGroupName",
    vmName: "myVMName",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

guest_configuration_assignment = azure_native.guestconfiguration.GuestConfigurationAssignment("guestConfigurationAssignment",
    guest_configuration_assignment_name="NotInstalledApplicationForWindows",
    location="westcentralus",
    name="NotInstalledApplicationForWindows",
    properties=azure_native.guestconfiguration.GuestConfigurationAssignmentPropertiesResponseArgs(
        context="Azure policy",
        guest_configuration={
            "assignmentType": "ApplyAndAutoCorrect",
            "configurationParameter": [azure_native.guestconfiguration.ConfigurationParameterArgs(
                name="[InstalledApplication]NotInstalledApplicationResource1;Name",
                value="NotePad,sql",
            )],
            "contentHash": "123contenthash",
            "contentUri": "https://thisisfake/pacakge",
            "name": "NotInstalledApplicationForWindows",
            "version": "1.0.0.3",
        },
    ),
    resource_group_name="myResourceGroupName",
    vm_name="myVMName")

```

```yaml
resources:
  guestConfigurationAssignment:
    type: azure-native:guestconfiguration:GuestConfigurationAssignment
    properties:
      guestConfigurationAssignmentName: NotInstalledApplicationForWindows
      location: westcentralus
      name: NotInstalledApplicationForWindows
      properties:
        context: Azure policy
        guestConfiguration:
          assignmentType: ApplyAndAutoCorrect
          configurationParameter:
            - name: '[InstalledApplication]NotInstalledApplicationResource1;Name'
              value: NotePad,sql
          contentHash: 123contenthash
          contentUri: https://thisisfake/pacakge
          name: NotInstalledApplicationForWindows
          version: 1.0.0.3
      resourceGroupName: myResourceGroupName
      vmName: myVMName

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:guestconfiguration:GuestConfigurationAssignment NotInstalledApplicationForWindows /subscriptions/mysubscriptionid/resourceGroups/myResourceGroupName/providers/Microsoft.Compute/virtualMachines/myvm/providers/Microsoft.GuestConfiguration/guestConfigurationAssignments/NotInstalledApplicationForWindows 
```
