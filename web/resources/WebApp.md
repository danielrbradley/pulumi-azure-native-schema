A web app, a mobile app backend, or an API app.
API Version: 2022-09-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Clone web app
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var webApp = new AzureNative.Web.WebApp("webApp", new()
    {
        CloningInfo = new AzureNative.Web.Inputs.CloningInfoArgs
        {
            AppSettingsOverrides = 
            {
                { "Setting1", "NewValue1" },
                { "Setting3", "NewValue5" },
            },
            CloneCustomHostNames = true,
            CloneSourceControl = true,
            ConfigureLoadBalancing = false,
            HostingEnvironment = "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg456/providers/Microsoft.Web/hostingenvironments/aseforsites",
            Overwrite = false,
            SourceWebAppId = "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg456/providers/Microsoft.Web/sites/srcsiteg478",
            SourceWebAppLocation = "West Europe",
        },
        Kind = "app",
        Location = "East US",
        Name = "sitef6141",
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
		_, err := web.NewWebApp(ctx, "webApp", &web.WebAppArgs{
			CloningInfo: &web.CloningInfoArgs{
				AppSettingsOverrides: pulumi.StringMap{
					"Setting1": pulumi.String("NewValue1"),
					"Setting3": pulumi.String("NewValue5"),
				},
				CloneCustomHostNames:   pulumi.Bool(true),
				CloneSourceControl:     pulumi.Bool(true),
				ConfigureLoadBalancing: pulumi.Bool(false),
				HostingEnvironment:     pulumi.String("/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg456/providers/Microsoft.Web/hostingenvironments/aseforsites"),
				Overwrite:              pulumi.Bool(false),
				SourceWebAppId:         pulumi.String("/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg456/providers/Microsoft.Web/sites/srcsiteg478"),
				SourceWebAppLocation:   pulumi.String("West Europe"),
			},
			Kind:              pulumi.String("app"),
			Location:          pulumi.String("East US"),
			Name:              pulumi.String("sitef6141"),
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
import com.pulumi.azurenative.web.WebApp;
import com.pulumi.azurenative.web.WebAppArgs;
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
        var webApp = new WebApp("webApp", WebAppArgs.builder()        
            .cloningInfo(Map.ofEntries(
                Map.entry("appSettingsOverrides", Map.ofEntries(
                    Map.entry("Setting1", "NewValue1"),
                    Map.entry("Setting3", "NewValue5")
                )),
                Map.entry("cloneCustomHostNames", true),
                Map.entry("cloneSourceControl", true),
                Map.entry("configureLoadBalancing", false),
                Map.entry("hostingEnvironment", "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg456/providers/Microsoft.Web/hostingenvironments/aseforsites"),
                Map.entry("overwrite", false),
                Map.entry("sourceWebAppId", "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg456/providers/Microsoft.Web/sites/srcsiteg478"),
                Map.entry("sourceWebAppLocation", "West Europe")
            ))
            .kind("app")
            .location("East US")
            .name("sitef6141")
            .resourceGroupName("testrg123")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const webApp = new azure_native.web.WebApp("webApp", {
    cloningInfo: {
        appSettingsOverrides: {
            Setting1: "NewValue1",
            Setting3: "NewValue5",
        },
        cloneCustomHostNames: true,
        cloneSourceControl: true,
        configureLoadBalancing: false,
        hostingEnvironment: "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg456/providers/Microsoft.Web/hostingenvironments/aseforsites",
        overwrite: false,
        sourceWebAppId: "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg456/providers/Microsoft.Web/sites/srcsiteg478",
        sourceWebAppLocation: "West Europe",
    },
    kind: "app",
    location: "East US",
    name: "sitef6141",
    resourceGroupName: "testrg123",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

web_app = azure_native.web.WebApp("webApp",
    cloning_info=azure_native.web.CloningInfoArgs(
        app_settings_overrides={
            "Setting1": "NewValue1",
            "Setting3": "NewValue5",
        },
        clone_custom_host_names=True,
        clone_source_control=True,
        configure_load_balancing=False,
        hosting_environment="/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg456/providers/Microsoft.Web/hostingenvironments/aseforsites",
        overwrite=False,
        source_web_app_id="/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg456/providers/Microsoft.Web/sites/srcsiteg478",
        source_web_app_location="West Europe",
    ),
    kind="app",
    location="East US",
    name="sitef6141",
    resource_group_name="testrg123")

```

```yaml
resources:
  webApp:
    type: azure-native:web:WebApp
    properties:
      cloningInfo:
        appSettingsOverrides:
          Setting1: NewValue1
          Setting3: NewValue5
        cloneCustomHostNames: true
        cloneSourceControl: true
        configureLoadBalancing: false
        hostingEnvironment: /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg456/providers/Microsoft.Web/hostingenvironments/aseforsites
        overwrite: false
        sourceWebAppId: /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg456/providers/Microsoft.Web/sites/srcsiteg478
        sourceWebAppLocation: West Europe
      kind: app
      location: East US
      name: sitef6141
      resourceGroupName: testrg123

```

{{% /example %}}
{{% example %}}
### Create or Update web app
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var webApp = new AzureNative.Web.WebApp("webApp", new()
    {
        Kind = "app",
        Location = "East US",
        Name = "sitef6141",
        ResourceGroupName = "testrg123",
        ServerFarmId = "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Web/serverfarms/DefaultAsp",
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
		_, err := web.NewWebApp(ctx, "webApp", &web.WebAppArgs{
			Kind:              pulumi.String("app"),
			Location:          pulumi.String("East US"),
			Name:              pulumi.String("sitef6141"),
			ResourceGroupName: pulumi.String("testrg123"),
			ServerFarmId:      pulumi.String("/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Web/serverfarms/DefaultAsp"),
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
import com.pulumi.azurenative.web.WebApp;
import com.pulumi.azurenative.web.WebAppArgs;
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
        var webApp = new WebApp("webApp", WebAppArgs.builder()        
            .kind("app")
            .location("East US")
            .name("sitef6141")
            .resourceGroupName("testrg123")
            .serverFarmId("/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Web/serverfarms/DefaultAsp")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const webApp = new azure_native.web.WebApp("webApp", {
    kind: "app",
    location: "East US",
    name: "sitef6141",
    resourceGroupName: "testrg123",
    serverFarmId: "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Web/serverfarms/DefaultAsp",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

web_app = azure_native.web.WebApp("webApp",
    kind="app",
    location="East US",
    name="sitef6141",
    resource_group_name="testrg123",
    server_farm_id="/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Web/serverfarms/DefaultAsp")

```

```yaml
resources:
  webApp:
    type: azure-native:web:WebApp
    properties:
      kind: app
      location: East US
      name: sitef6141
      resourceGroupName: testrg123
      serverFarmId: /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Web/serverfarms/DefaultAsp

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:web:WebApp sitef6141 /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Web/sites/sitef6141 
```
