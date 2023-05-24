Definition of the module type.
API Version: 2022-08-08.
Previous API Version: 2019-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a module
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var module = new AzureNative.Automation.Module("module", new()
    {
        AutomationAccountName = "myAutomationAccount33",
        ContentLink = new AzureNative.Automation.Inputs.ContentLinkArgs
        {
            ContentHash = new AzureNative.Automation.Inputs.ContentHashArgs
            {
                Algorithm = "sha265",
                Value = "07E108A962B81DD9C9BAA89BB47C0F6EE52B29E83758B07795E408D258B2B87A",
            },
            Uri = "https://teststorage.blob.core.windows.net/dsccomposite/OmsCompositeResources.zip",
            Version = "1.0.0.0",
        },
        ModuleName = "OmsCompositeResources",
        ResourceGroupName = "rg",
    });

});


```

```go
package main

import (
	automation "github.com/pulumi/pulumi-azure-native-sdk/automation"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := automation.NewModule(ctx, "module", &automation.ModuleArgs{
			AutomationAccountName: pulumi.String("myAutomationAccount33"),
			ContentLink: automation.ContentLinkResponse{
				ContentHash: &automation.ContentHashArgs{
					Algorithm: pulumi.String("sha265"),
					Value:     pulumi.String("07E108A962B81DD9C9BAA89BB47C0F6EE52B29E83758B07795E408D258B2B87A"),
				},
				Uri:     pulumi.String("https://teststorage.blob.core.windows.net/dsccomposite/OmsCompositeResources.zip"),
				Version: pulumi.String("1.0.0.0"),
			},
			ModuleName:        pulumi.String("OmsCompositeResources"),
			ResourceGroupName: pulumi.String("rg"),
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
import com.pulumi.azurenative.automation.Module;
import com.pulumi.azurenative.automation.ModuleArgs;
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
        var module = new Module("module", ModuleArgs.builder()        
            .automationAccountName("myAutomationAccount33")
            .contentLink(Map.ofEntries(
                Map.entry("contentHash", Map.ofEntries(
                    Map.entry("algorithm", "sha265"),
                    Map.entry("value", "07E108A962B81DD9C9BAA89BB47C0F6EE52B29E83758B07795E408D258B2B87A")
                )),
                Map.entry("uri", "https://teststorage.blob.core.windows.net/dsccomposite/OmsCompositeResources.zip"),
                Map.entry("version", "1.0.0.0")
            ))
            .moduleName("OmsCompositeResources")
            .resourceGroupName("rg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const module = new azure_native.automation.Module("module", {
    automationAccountName: "myAutomationAccount33",
    contentLink: {
        contentHash: {
            algorithm: "sha265",
            value: "07E108A962B81DD9C9BAA89BB47C0F6EE52B29E83758B07795E408D258B2B87A",
        },
        uri: "https://teststorage.blob.core.windows.net/dsccomposite/OmsCompositeResources.zip",
        version: "1.0.0.0",
    },
    moduleName: "OmsCompositeResources",
    resourceGroupName: "rg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

module = azure_native.automation.Module("module",
    automation_account_name="myAutomationAccount33",
    content_link=azure_native.automation.ContentLinkResponseArgs(
        content_hash=azure_native.automation.ContentHashArgs(
            algorithm="sha265",
            value="07E108A962B81DD9C9BAA89BB47C0F6EE52B29E83758B07795E408D258B2B87A",
        ),
        uri="https://teststorage.blob.core.windows.net/dsccomposite/OmsCompositeResources.zip",
        version="1.0.0.0",
    ),
    module_name="OmsCompositeResources",
    resource_group_name="rg")

```

```yaml
resources:
  module:
    type: azure-native:automation:Module
    properties:
      automationAccountName: myAutomationAccount33
      contentLink:
        contentHash:
          algorithm: sha265
          value: 07E108A962B81DD9C9BAA89BB47C0F6EE52B29E83758B07795E408D258B2B87A
        uri: https://teststorage.blob.core.windows.net/dsccomposite/OmsCompositeResources.zip
        version: 1.0.0.0
      moduleName: OmsCompositeResources
      resourceGroupName: rg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:automation:Module OmsCompositeResources /subscriptions/subid/resourceGroups/rg/providers/Microsoft.Automation/automationAccounts/myAutomationAccount33/modules/OmsCompositeResources 
```
