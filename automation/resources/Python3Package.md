Definition of the module type.
API Version: 2022-08-08.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a python 3 package
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var python3Package = new AzureNative.Automation.Python3Package("python3Package", new()
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
        PackageName = "OmsCompositeResources",
        ResourceGroupName = "rg",
        Tags = null,
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
		_, err := automation.NewPython3Package(ctx, "python3Package", &automation.Python3PackageArgs{
			AutomationAccountName: pulumi.String("myAutomationAccount33"),
			ContentLink: automation.ContentLinkResponse{
				ContentHash: &automation.ContentHashArgs{
					Algorithm: pulumi.String("sha265"),
					Value:     pulumi.String("07E108A962B81DD9C9BAA89BB47C0F6EE52B29E83758B07795E408D258B2B87A"),
				},
				Uri:     pulumi.String("https://teststorage.blob.core.windows.net/dsccomposite/OmsCompositeResources.zip"),
				Version: pulumi.String("1.0.0.0"),
			},
			PackageName:       pulumi.String("OmsCompositeResources"),
			ResourceGroupName: pulumi.String("rg"),
			Tags:              nil,
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
import com.pulumi.azurenative.automation.Python3Package;
import com.pulumi.azurenative.automation.Python3PackageArgs;
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
        var python3Package = new Python3Package("python3Package", Python3PackageArgs.builder()        
            .automationAccountName("myAutomationAccount33")
            .contentLink(Map.ofEntries(
                Map.entry("contentHash", Map.ofEntries(
                    Map.entry("algorithm", "sha265"),
                    Map.entry("value", "07E108A962B81DD9C9BAA89BB47C0F6EE52B29E83758B07795E408D258B2B87A")
                )),
                Map.entry("uri", "https://teststorage.blob.core.windows.net/dsccomposite/OmsCompositeResources.zip"),
                Map.entry("version", "1.0.0.0")
            ))
            .packageName("OmsCompositeResources")
            .resourceGroupName("rg")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const python3Package = new azure_native.automation.Python3Package("python3Package", {
    automationAccountName: "myAutomationAccount33",
    contentLink: {
        contentHash: {
            algorithm: "sha265",
            value: "07E108A962B81DD9C9BAA89BB47C0F6EE52B29E83758B07795E408D258B2B87A",
        },
        uri: "https://teststorage.blob.core.windows.net/dsccomposite/OmsCompositeResources.zip",
        version: "1.0.0.0",
    },
    packageName: "OmsCompositeResources",
    resourceGroupName: "rg",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

python3_package = azure_native.automation.Python3Package("python3Package",
    automation_account_name="myAutomationAccount33",
    content_link=azure_native.automation.ContentLinkResponseArgs(
        content_hash=azure_native.automation.ContentHashArgs(
            algorithm="sha265",
            value="07E108A962B81DD9C9BAA89BB47C0F6EE52B29E83758B07795E408D258B2B87A",
        ),
        uri="https://teststorage.blob.core.windows.net/dsccomposite/OmsCompositeResources.zip",
        version="1.0.0.0",
    ),
    package_name="OmsCompositeResources",
    resource_group_name="rg",
    tags={})

```

```yaml
resources:
  python3Package:
    type: azure-native:automation:Python3Package
    properties:
      automationAccountName: myAutomationAccount33
      contentLink:
        contentHash:
          algorithm: sha265
          value: 07E108A962B81DD9C9BAA89BB47C0F6EE52B29E83758B07795E408D258B2B87A
        uri: https://teststorage.blob.core.windows.net/dsccomposite/OmsCompositeResources.zip
        version: 1.0.0.0
      packageName: OmsCompositeResources
      resourceGroupName: rg
      tags: {}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:automation:Python3Package OmsCompositeResources /subscriptions/subid/resourceGroups/rg/providers/Microsoft.Automation/automationAccounts/myAutomationAccount33/python3Packages/OmsCompositeResources 
```
