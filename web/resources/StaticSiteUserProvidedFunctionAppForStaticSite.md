Static Site User Provided Function App ARM resource.
API Version: 2022-09-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Register a user provided function app with a static site
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var staticSiteUserProvidedFunctionAppForStaticSite = new AzureNative.Web.StaticSiteUserProvidedFunctionAppForStaticSite("staticSiteUserProvidedFunctionAppForStaticSite", new()
    {
        FunctionAppName = "testFunctionApp",
        FunctionAppRegion = "West US 2",
        FunctionAppResourceId = "/subscription/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/functionRG/providers/Microsoft.Web/sites/testFunctionApp",
        IsForced = true,
        Name = "testStaticSite0",
        ResourceGroupName = "rg",
    });

});


```

```go
package main

import (
	web "github.com/pulumi/pulumi-azure-native-sdk/web"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := web.NewStaticSiteUserProvidedFunctionAppForStaticSite(ctx, "staticSiteUserProvidedFunctionAppForStaticSite", &web.StaticSiteUserProvidedFunctionAppForStaticSiteArgs{
			FunctionAppName:       pulumi.String("testFunctionApp"),
			FunctionAppRegion:     pulumi.String("West US 2"),
			FunctionAppResourceId: pulumi.String("/subscription/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/functionRG/providers/Microsoft.Web/sites/testFunctionApp"),
			IsForced:              pulumi.Bool(true),
			Name:                  pulumi.String("testStaticSite0"),
			ResourceGroupName:     pulumi.String("rg"),
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
import com.pulumi.azurenative.web.StaticSiteUserProvidedFunctionAppForStaticSite;
import com.pulumi.azurenative.web.StaticSiteUserProvidedFunctionAppForStaticSiteArgs;
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
        var staticSiteUserProvidedFunctionAppForStaticSite = new StaticSiteUserProvidedFunctionAppForStaticSite("staticSiteUserProvidedFunctionAppForStaticSite", StaticSiteUserProvidedFunctionAppForStaticSiteArgs.builder()        
            .functionAppName("testFunctionApp")
            .functionAppRegion("West US 2")
            .functionAppResourceId("/subscription/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/functionRG/providers/Microsoft.Web/sites/testFunctionApp")
            .isForced(true)
            .name("testStaticSite0")
            .resourceGroupName("rg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const staticSiteUserProvidedFunctionAppForStaticSite = new azure_native.web.StaticSiteUserProvidedFunctionAppForStaticSite("staticSiteUserProvidedFunctionAppForStaticSite", {
    functionAppName: "testFunctionApp",
    functionAppRegion: "West US 2",
    functionAppResourceId: "/subscription/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/functionRG/providers/Microsoft.Web/sites/testFunctionApp",
    isForced: true,
    name: "testStaticSite0",
    resourceGroupName: "rg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

static_site_user_provided_function_app_for_static_site = azure_native.web.StaticSiteUserProvidedFunctionAppForStaticSite("staticSiteUserProvidedFunctionAppForStaticSite",
    function_app_name="testFunctionApp",
    function_app_region="West US 2",
    function_app_resource_id="/subscription/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/functionRG/providers/Microsoft.Web/sites/testFunctionApp",
    is_forced=True,
    name="testStaticSite0",
    resource_group_name="rg")

```

```yaml
resources:
  staticSiteUserProvidedFunctionAppForStaticSite:
    type: azure-native:web:StaticSiteUserProvidedFunctionAppForStaticSite
    properties:
      functionAppName: testFunctionApp
      functionAppRegion: West US 2
      functionAppResourceId: /subscription/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/functionRG/providers/Microsoft.Web/sites/testFunctionApp
      isForced: true
      name: testStaticSite0
      resourceGroupName: rg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:web:StaticSiteUserProvidedFunctionAppForStaticSite testFunctionApp /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/rg/providers/Microsoft.Web/staticSites/testStaticSite0/builds/default/userProvidedFunctionApps/testFunctionApp 
```
