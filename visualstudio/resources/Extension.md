The response to an extension resource GET request.
API Version: 2017-11-01-preview.
Previous API Version: 2014-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create an extension resource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var extension = new AzureNative.VisualStudio.Extension("extension", new()
    {
        AccountResourceName = "ExampleAccount",
        ExtensionResourceName = "ms.example",
        Location = "Central US",
        Plan = new AzureNative.VisualStudio.Inputs.ExtensionResourcePlanArgs
        {
            Name = "ExamplePlan",
            Product = "ExampleExtensionName",
            PromotionCode = "",
            Publisher = "ExampleExtensionPublisher",
            Version = "1.0",
        },
        Properties = null,
        ResourceGroupName = "VS-Example-Group",
        Tags = null,
    });

});


```

```go
package main

import (
	visualstudio "github.com/pulumi/pulumi-azure-native-sdk/visualstudio"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := visualstudio.NewExtension(ctx, "extension", &visualstudio.ExtensionArgs{
			AccountResourceName:   pulumi.String("ExampleAccount"),
			ExtensionResourceName: pulumi.String("ms.example"),
			Location:              pulumi.String("Central US"),
			Plan: &visualstudio.ExtensionResourcePlanArgs{
				Name:          pulumi.String("ExamplePlan"),
				Product:       pulumi.String("ExampleExtensionName"),
				PromotionCode: pulumi.String(""),
				Publisher:     pulumi.String("ExampleExtensionPublisher"),
				Version:       pulumi.String("1.0"),
			},
			Properties:        nil,
			ResourceGroupName: pulumi.String("VS-Example-Group"),
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
import com.pulumi.azurenative.visualstudio.Extension;
import com.pulumi.azurenative.visualstudio.ExtensionArgs;
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
        var extension = new Extension("extension", ExtensionArgs.builder()        
            .accountResourceName("ExampleAccount")
            .extensionResourceName("ms.example")
            .location("Central US")
            .plan(Map.ofEntries(
                Map.entry("name", "ExamplePlan"),
                Map.entry("product", "ExampleExtensionName"),
                Map.entry("promotionCode", ""),
                Map.entry("publisher", "ExampleExtensionPublisher"),
                Map.entry("version", "1.0")
            ))
            .properties()
            .resourceGroupName("VS-Example-Group")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const extension = new azure_native.visualstudio.Extension("extension", {
    accountResourceName: "ExampleAccount",
    extensionResourceName: "ms.example",
    location: "Central US",
    plan: {
        name: "ExamplePlan",
        product: "ExampleExtensionName",
        promotionCode: "",
        publisher: "ExampleExtensionPublisher",
        version: "1.0",
    },
    properties: {},
    resourceGroupName: "VS-Example-Group",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

extension = azure_native.visualstudio.Extension("extension",
    account_resource_name="ExampleAccount",
    extension_resource_name="ms.example",
    location="Central US",
    plan=azure_native.visualstudio.ExtensionResourcePlanArgs(
        name="ExamplePlan",
        product="ExampleExtensionName",
        promotion_code="",
        publisher="ExampleExtensionPublisher",
        version="1.0",
    ),
    properties={},
    resource_group_name="VS-Example-Group",
    tags={})

```

```yaml
resources:
  extension:
    type: azure-native:visualstudio:Extension
    properties:
      accountResourceName: ExampleAccount
      extensionResourceName: ms.example
      location: Central US
      plan:
        name: ExamplePlan
        product: ExampleExtensionName
        promotionCode:
        publisher: ExampleExtensionPublisher
        version: '1.0'
      properties: {}
      resourceGroupName: VS-Example-Group
      tags: {}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:visualstudio:Extension ms.example /subscriptions/0de7f055-dbea-498d-8e9e-da287eedca90/resourceGroups/VS-Example-Group/providers/Microsoft.VisualStudio/account/ExampleAccount/extension/ms.example 
```
