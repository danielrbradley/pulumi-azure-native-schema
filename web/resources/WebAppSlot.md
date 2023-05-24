A web app, a mobile app backend, or an API app.
API Version: 2022-09-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Clone web app slot
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var webAppSlot = new AzureNative.Web.WebAppSlot("webAppSlot", new()
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
            SourceWebAppId = "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg456/providers/Microsoft.Web/sites/srcsiteg478/slot/qa",
            SourceWebAppLocation = "West Europe",
        },
        Kind = "app",
        Location = "East US",
        Name = "sitef6141",
        ResourceGroupName = "testrg123",
        Slot = "staging",
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
		_, err := web.NewWebAppSlot(ctx, "webAppSlot", &web.WebAppSlotArgs{
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
				SourceWebAppId:         pulumi.String("/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg456/providers/Microsoft.Web/sites/srcsiteg478/slot/qa"),
				SourceWebAppLocation:   pulumi.String("West Europe"),
			},
			Kind:              pulumi.String("app"),
			Location:          pulumi.String("East US"),
			Name:              pulumi.String("sitef6141"),
			ResourceGroupName: pulumi.String("testrg123"),
			Slot:              pulumi.String("staging"),
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
import com.pulumi.azurenative.web.WebAppSlot;
import com.pulumi.azurenative.web.WebAppSlotArgs;
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
        var webAppSlot = new WebAppSlot("webAppSlot", WebAppSlotArgs.builder()        
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
                Map.entry("sourceWebAppId", "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg456/providers/Microsoft.Web/sites/srcsiteg478/slot/qa"),
                Map.entry("sourceWebAppLocation", "West Europe")
            ))
            .kind("app")
            .location("East US")
            .name("sitef6141")
            .resourceGroupName("testrg123")
            .slot("staging")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const webAppSlot = new azure_native.web.WebAppSlot("webAppSlot", {
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
        sourceWebAppId: "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg456/providers/Microsoft.Web/sites/srcsiteg478/slot/qa",
        sourceWebAppLocation: "West Europe",
    },
    kind: "app",
    location: "East US",
    name: "sitef6141",
    resourceGroupName: "testrg123",
    slot: "staging",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

web_app_slot = azure_native.web.WebAppSlot("webAppSlot",
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
        source_web_app_id="/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg456/providers/Microsoft.Web/sites/srcsiteg478/slot/qa",
        source_web_app_location="West Europe",
    ),
    kind="app",
    location="East US",
    name="sitef6141",
    resource_group_name="testrg123",
    slot="staging")

```

```yaml
resources:
  webAppSlot:
    type: azure-native:web:WebAppSlot
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
        sourceWebAppId: /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg456/providers/Microsoft.Web/sites/srcsiteg478/slot/qa
        sourceWebAppLocation: West Europe
      kind: app
      location: East US
      name: sitef6141
      resourceGroupName: testrg123
      slot: staging

```

{{% /example %}}
{{% example %}}
### Create or Update Web App Slot
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var webAppSlot = new AzureNative.Web.WebAppSlot("webAppSlot", new()
    {
        Kind = "app",
        Location = "East US",
        Name = "sitef6141",
        ResourceGroupName = "testrg123",
        ServerFarmId = "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Web/serverfarms/DefaultAsp",
        Slot = "staging",
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
		_, err := web.NewWebAppSlot(ctx, "webAppSlot", &web.WebAppSlotArgs{
			Kind:              pulumi.String("app"),
			Location:          pulumi.String("East US"),
			Name:              pulumi.String("sitef6141"),
			ResourceGroupName: pulumi.String("testrg123"),
			ServerFarmId:      pulumi.String("/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Web/serverfarms/DefaultAsp"),
			Slot:              pulumi.String("staging"),
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
import com.pulumi.azurenative.web.WebAppSlot;
import com.pulumi.azurenative.web.WebAppSlotArgs;
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
        var webAppSlot = new WebAppSlot("webAppSlot", WebAppSlotArgs.builder()        
            .kind("app")
            .location("East US")
            .name("sitef6141")
            .resourceGroupName("testrg123")
            .serverFarmId("/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Web/serverfarms/DefaultAsp")
            .slot("staging")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const webAppSlot = new azure_native.web.WebAppSlot("webAppSlot", {
    kind: "app",
    location: "East US",
    name: "sitef6141",
    resourceGroupName: "testrg123",
    serverFarmId: "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Web/serverfarms/DefaultAsp",
    slot: "staging",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

web_app_slot = azure_native.web.WebAppSlot("webAppSlot",
    kind="app",
    location="East US",
    name="sitef6141",
    resource_group_name="testrg123",
    server_farm_id="/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Web/serverfarms/DefaultAsp",
    slot="staging")

```

```yaml
resources:
  webAppSlot:
    type: azure-native:web:WebAppSlot
    properties:
      kind: app
      location: East US
      name: sitef6141
      resourceGroupName: testrg123
      serverFarmId: /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Web/serverfarms/DefaultAsp
      slot: staging

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:web:WebAppSlot sitef6141/staging /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Web/sites/sitef6141/slots/staging 
```
