Definition of the configuration profile.
API Version: 2022-05-04.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update configuration profile
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var configurationProfile = new AzureNative.Automanage.ConfigurationProfile("configurationProfile", new()
    {
        ConfigurationProfileName = "customConfigurationProfile",
        Location = "East US",
        Properties = new AzureNative.Automanage.Inputs.ConfigurationProfilePropertiesArgs
        {
            Configuration = 
            {
                { "Antimalware/Enable", false },
                { "AzureSecurityCenter/Enable", true },
                { "Backup/Enable", false },
                { "BootDiagnostics/Enable", true },
                { "ChangeTrackingAndInventory/Enable", true },
                { "GuestConfiguration/Enable", true },
                { "LogAnalytics/Enable", true },
                { "UpdateManagement/Enable", true },
                { "VMInsights/Enable", true },
            },
        },
        ResourceGroupName = "myResourceGroupName",
        Tags = 
        {
            { "Organization", "Administration" },
        },
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
		_, err := automanage.NewConfigurationProfile(ctx, "configurationProfile", &automanage.ConfigurationProfileArgs{
			ConfigurationProfileName: pulumi.String("customConfigurationProfile"),
			Location:                 pulumi.String("East US"),
			Properties: &automanage.ConfigurationProfilePropertiesArgs{
				Configuration: pulumi.Any{
					Antimalware / Enable:                false,
					AzureSecurityCenter / Enable:        true,
					Backup / Enable:                     false,
					BootDiagnostics / Enable:            true,
					ChangeTrackingAndInventory / Enable: true,
					GuestConfiguration / Enable:         true,
					LogAnalytics / Enable:               true,
					UpdateManagement / Enable:           true,
					VMInsights / Enable:                 true,
				},
			},
			ResourceGroupName: pulumi.String("myResourceGroupName"),
			Tags: pulumi.StringMap{
				"Organization": pulumi.String("Administration"),
			},
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
import com.pulumi.azurenative.automanage.ConfigurationProfile;
import com.pulumi.azurenative.automanage.ConfigurationProfileArgs;
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
        var configurationProfile = new ConfigurationProfile("configurationProfile", ConfigurationProfileArgs.builder()        
            .configurationProfileName("customConfigurationProfile")
            .location("East US")
            .properties(Map.of("configuration", Map.ofEntries(
                Map.entry("Antimalware/Enable", false),
                Map.entry("AzureSecurityCenter/Enable", true),
                Map.entry("Backup/Enable", false),
                Map.entry("BootDiagnostics/Enable", true),
                Map.entry("ChangeTrackingAndInventory/Enable", true),
                Map.entry("GuestConfiguration/Enable", true),
                Map.entry("LogAnalytics/Enable", true),
                Map.entry("UpdateManagement/Enable", true),
                Map.entry("VMInsights/Enable", true)
            )))
            .resourceGroupName("myResourceGroupName")
            .tags(Map.of("Organization", "Administration"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const configurationProfile = new azure_native.automanage.ConfigurationProfile("configurationProfile", {
    configurationProfileName: "customConfigurationProfile",
    location: "East US",
    properties: {
        configuration: {
            "Antimalware/Enable": false,
            "AzureSecurityCenter/Enable": true,
            "Backup/Enable": false,
            "BootDiagnostics/Enable": true,
            "ChangeTrackingAndInventory/Enable": true,
            "GuestConfiguration/Enable": true,
            "LogAnalytics/Enable": true,
            "UpdateManagement/Enable": true,
            "VMInsights/Enable": true,
        },
    },
    resourceGroupName: "myResourceGroupName",
    tags: {
        Organization: "Administration",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

configuration_profile = azure_native.automanage.ConfigurationProfile("configurationProfile",
    configuration_profile_name="customConfigurationProfile",
    location="East US",
    properties=azure_native.automanage.ConfigurationProfilePropertiesArgs(
        configuration={
            "Antimalware/Enable": False,
            "AzureSecurityCenter/Enable": True,
            "Backup/Enable": False,
            "BootDiagnostics/Enable": True,
            "ChangeTrackingAndInventory/Enable": True,
            "GuestConfiguration/Enable": True,
            "LogAnalytics/Enable": True,
            "UpdateManagement/Enable": True,
            "VMInsights/Enable": True,
        },
    ),
    resource_group_name="myResourceGroupName",
    tags={
        "Organization": "Administration",
    })

```

```yaml
resources:
  configurationProfile:
    type: azure-native:automanage:ConfigurationProfile
    properties:
      configurationProfileName: customConfigurationProfile
      location: East US
      properties:
        configuration:
          Antimalware/Enable: false
          AzureSecurityCenter/Enable: true
          Backup/Enable: false
          BootDiagnostics/Enable: true
          ChangeTrackingAndInventory/Enable: true
          GuestConfiguration/Enable: true
          LogAnalytics/Enable: true
          UpdateManagement/Enable: true
          VMInsights/Enable: true
      resourceGroupName: myResourceGroupName
      tags:
        Organization: Administration

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:automanage:ConfigurationProfile customConfigurationProfile /subscriptions/subscriptionId/resourceGroups/myResourceGroupName/providers/Microsoft.Automanage/configurationProfiles/customConfigurationProfile 
```
