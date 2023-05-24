Response to get user settings
API Version: 2018-10-01.
Previous API Version: 2018-10-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PutUserSettings
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var userSettings = new AzureNative.Portal.UserSettings("userSettings", new()
    {
        Properties = new AzureNative.Portal.Inputs.UserPropertiesArgs
        {
            PreferredLocation = "eastus",
            PreferredOsType = "Linux",
            PreferredShellType = "bash",
            StorageProfile = new AzureNative.Portal.Inputs.StorageProfileArgs
            {
                DiskSizeInGB = 5,
                FileShareName = "string",
                StorageAccountResourceId = "string",
            },
            TerminalSettings = new AzureNative.Portal.Inputs.TerminalSettingsArgs
            {
                FontSize = "Medium",
                FontStyle = "Monospace",
            },
        },
        UserSettingsName = "cloudconsole",
    });

});


```

```go
package main

import (
	portal "github.com/pulumi/pulumi-azure-native-sdk/portal"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := portal.NewUserSettings(ctx, "userSettings", &portal.UserSettingsArgs{
			Properties: portal.UserPropertiesResponse{
				PreferredLocation:  pulumi.String("eastus"),
				PreferredOsType:    pulumi.String("Linux"),
				PreferredShellType: pulumi.String("bash"),
				StorageProfile: &portal.StorageProfileArgs{
					DiskSizeInGB:             pulumi.Int(5),
					FileShareName:            pulumi.String("string"),
					StorageAccountResourceId: pulumi.String("string"),
				},
				TerminalSettings: &portal.TerminalSettingsArgs{
					FontSize:  pulumi.String("Medium"),
					FontStyle: pulumi.String("Monospace"),
				},
			},
			UserSettingsName: pulumi.String("cloudconsole"),
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
import com.pulumi.azurenative.portal.UserSettings;
import com.pulumi.azurenative.portal.UserSettingsArgs;
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
        var userSettings = new UserSettings("userSettings", UserSettingsArgs.builder()        
            .properties(Map.ofEntries(
                Map.entry("preferredLocation", "eastus"),
                Map.entry("preferredOsType", "Linux"),
                Map.entry("preferredShellType", "bash"),
                Map.entry("storageProfile", Map.ofEntries(
                    Map.entry("diskSizeInGB", 5),
                    Map.entry("fileShareName", "string"),
                    Map.entry("storageAccountResourceId", "string")
                )),
                Map.entry("terminalSettings", Map.ofEntries(
                    Map.entry("fontSize", "Medium"),
                    Map.entry("fontStyle", "Monospace")
                ))
            ))
            .userSettingsName("cloudconsole")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const userSettings = new azure_native.portal.UserSettings("userSettings", {
    properties: {
        preferredLocation: "eastus",
        preferredOsType: "Linux",
        preferredShellType: "bash",
        storageProfile: {
            diskSizeInGB: 5,
            fileShareName: "string",
            storageAccountResourceId: "string",
        },
        terminalSettings: {
            fontSize: "Medium",
            fontStyle: "Monospace",
        },
    },
    userSettingsName: "cloudconsole",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

user_settings = azure_native.portal.UserSettings("userSettings",
    properties=azure_native.portal.UserPropertiesResponseArgs(
        preferred_location="eastus",
        preferred_os_type="Linux",
        preferred_shell_type="bash",
        storage_profile=azure_native.portal.StorageProfileArgs(
            disk_size_in_gb=5,
            file_share_name="string",
            storage_account_resource_id="string",
        ),
        terminal_settings=azure_native.portal.TerminalSettingsArgs(
            font_size="Medium",
            font_style="Monospace",
        ),
    ),
    user_settings_name="cloudconsole")

```

```yaml
resources:
  userSettings:
    type: azure-native:portal:UserSettings
    properties:
      properties:
        preferredLocation: eastus
        preferredOsType: Linux
        preferredShellType: bash
        storageProfile:
          diskSizeInGB: 5
          fileShareName: string
          storageAccountResourceId: string
        terminalSettings:
          fontSize: Medium
          fontStyle: Monospace
      userSettingsName: cloudconsole

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:portal:UserSettings myresource1 /providers/Microsoft.Portal/userSettings/{userSettingsName} 
```
