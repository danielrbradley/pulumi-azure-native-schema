Schema for Application properties.
API Version: 2022-09-09.
Previous API Version: 2021-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Application_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var application = new AzureNative.DesktopVirtualization.Application("application", new()
    {
        ApplicationGroupName = "applicationGroup1",
        ApplicationName = "application1",
        CommandLineArguments = "arguments",
        CommandLineSetting = "Allow",
        Description = "des1",
        FilePath = "path",
        FriendlyName = "friendly",
        IconIndex = 1,
        IconPath = "icon",
        ResourceGroupName = "resourceGroup1",
        ShowInPortal = true,
    });

});


```

```go
package main

import (
	desktopvirtualization "github.com/pulumi/pulumi-azure-native-sdk/desktopvirtualization"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := desktopvirtualization.NewApplication(ctx, "application", &desktopvirtualization.ApplicationArgs{
			ApplicationGroupName: pulumi.String("applicationGroup1"),
			ApplicationName:      pulumi.String("application1"),
			CommandLineArguments: pulumi.String("arguments"),
			CommandLineSetting:   pulumi.String("Allow"),
			Description:          pulumi.String("des1"),
			FilePath:             pulumi.String("path"),
			FriendlyName:         pulumi.String("friendly"),
			IconIndex:            pulumi.Int(1),
			IconPath:             pulumi.String("icon"),
			ResourceGroupName:    pulumi.String("resourceGroup1"),
			ShowInPortal:         pulumi.Bool(true),
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
import com.pulumi.azurenative.desktopvirtualization.Application;
import com.pulumi.azurenative.desktopvirtualization.ApplicationArgs;
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
        var application = new Application("application", ApplicationArgs.builder()        
            .applicationGroupName("applicationGroup1")
            .applicationName("application1")
            .commandLineArguments("arguments")
            .commandLineSetting("Allow")
            .description("des1")
            .filePath("path")
            .friendlyName("friendly")
            .iconIndex(1)
            .iconPath("icon")
            .resourceGroupName("resourceGroup1")
            .showInPortal(true)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const application = new azure_native.desktopvirtualization.Application("application", {
    applicationGroupName: "applicationGroup1",
    applicationName: "application1",
    commandLineArguments: "arguments",
    commandLineSetting: "Allow",
    description: "des1",
    filePath: "path",
    friendlyName: "friendly",
    iconIndex: 1,
    iconPath: "icon",
    resourceGroupName: "resourceGroup1",
    showInPortal: true,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

application = azure_native.desktopvirtualization.Application("application",
    application_group_name="applicationGroup1",
    application_name="application1",
    command_line_arguments="arguments",
    command_line_setting="Allow",
    description="des1",
    file_path="path",
    friendly_name="friendly",
    icon_index=1,
    icon_path="icon",
    resource_group_name="resourceGroup1",
    show_in_portal=True)

```

```yaml
resources:
  application:
    type: azure-native:desktopvirtualization:Application
    properties:
      applicationGroupName: applicationGroup1
      applicationName: application1
      commandLineArguments: arguments
      commandLineSetting: Allow
      description: des1
      filePath: path
      friendlyName: friendly
      iconIndex: 1
      iconPath: icon
      resourceGroupName: resourceGroup1
      showInPortal: true

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:desktopvirtualization:Application applicationGroup1/application1 /subscriptions/daefabc0-95b4-48b3-b645-8a753a63c4fa/resourceGroups/resourceGroup1/providers/Microsoft.DesktopVirtualization/applicationGroups/applicationGroup1/applications/application1 
```
