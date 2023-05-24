String dictionary resource.
API Version: 2022-09-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Update App Settings
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var webAppApplicationSettings = new AzureNative.Web.WebAppApplicationSettings("webAppApplicationSettings", new()
    {
        Name = "sitef6141",
        Properties = 
        {
            { "Setting1", "Value1" },
            { "Setting2", "Value2" },
        },
        ResourceGroupName = "testrg123",
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
		_, err := web.NewWebAppApplicationSettings(ctx, "webAppApplicationSettings", &web.WebAppApplicationSettingsArgs{
			Name: pulumi.String("sitef6141"),
			Properties: pulumi.StringMap{
				"Setting1": pulumi.String("Value1"),
				"Setting2": pulumi.String("Value2"),
			},
			ResourceGroupName: pulumi.String("testrg123"),
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
import com.pulumi.azurenative.web.WebAppApplicationSettings;
import com.pulumi.azurenative.web.WebAppApplicationSettingsArgs;
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
        var webAppApplicationSettings = new WebAppApplicationSettings("webAppApplicationSettings", WebAppApplicationSettingsArgs.builder()        
            .name("sitef6141")
            .properties(Map.ofEntries(
                Map.entry("Setting1", "Value1"),
                Map.entry("Setting2", "Value2")
            ))
            .resourceGroupName("testrg123")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const webAppApplicationSettings = new azure_native.web.WebAppApplicationSettings("webAppApplicationSettings", {
    name: "sitef6141",
    properties: {
        Setting1: "Value1",
        Setting2: "Value2",
    },
    resourceGroupName: "testrg123",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

web_app_application_settings = azure_native.web.WebAppApplicationSettings("webAppApplicationSettings",
    name="sitef6141",
    properties={
        "Setting1": "Value1",
        "Setting2": "Value2",
    },
    resource_group_name="testrg123")

```

```yaml
resources:
  webAppApplicationSettings:
    type: azure-native:web:WebAppApplicationSettings
    properties:
      name: sitef6141
      properties:
        Setting1: Value1
        Setting2: Value2
      resourceGroupName: testrg123

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:web:WebAppApplicationSettings appsettings /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Web/sites/sitef6141/config/appsettings 
```
