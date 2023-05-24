Configuration settings for the Azure App Service Authentication / Authorization feature.
API Version: 2022-09-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Update Auth Settings
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var webAppAuthSettings = new AzureNative.Web.WebAppAuthSettings("webAppAuthSettings", new()
    {
        AllowedExternalRedirectUrls = new[]
        {
            "sitef6141.customdomain.net",
            "sitef6141.customdomain.info",
        },
        ClientId = "42d795a9-8abb-4d06-8534-39528af40f8e.apps.googleusercontent.com",
        DefaultProvider = AzureNative.Web.BuiltInAuthenticationProvider.Google,
        Enabled = true,
        Name = "sitef6141",
        ResourceGroupName = "testrg123",
        RuntimeVersion = "~1",
        TokenRefreshExtensionHours = 120,
        TokenStoreEnabled = true,
        UnauthenticatedClientAction = AzureNative.Web.UnauthenticatedClientAction.RedirectToLoginPage,
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
		_, err := web.NewWebAppAuthSettings(ctx, "webAppAuthSettings", &web.WebAppAuthSettingsArgs{
			AllowedExternalRedirectUrls: pulumi.StringArray{
				pulumi.String("sitef6141.customdomain.net"),
				pulumi.String("sitef6141.customdomain.info"),
			},
			ClientId:                    pulumi.String("42d795a9-8abb-4d06-8534-39528af40f8e.apps.googleusercontent.com"),
			DefaultProvider:             web.BuiltInAuthenticationProviderGoogle,
			Enabled:                     pulumi.Bool(true),
			Name:                        pulumi.String("sitef6141"),
			ResourceGroupName:           pulumi.String("testrg123"),
			RuntimeVersion:              pulumi.String("~1"),
			TokenRefreshExtensionHours:  pulumi.Float64(120),
			TokenStoreEnabled:           pulumi.Bool(true),
			UnauthenticatedClientAction: web.UnauthenticatedClientActionRedirectToLoginPage,
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
import com.pulumi.azurenative.web.WebAppAuthSettings;
import com.pulumi.azurenative.web.WebAppAuthSettingsArgs;
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
        var webAppAuthSettings = new WebAppAuthSettings("webAppAuthSettings", WebAppAuthSettingsArgs.builder()        
            .allowedExternalRedirectUrls(            
                "sitef6141.customdomain.net",
                "sitef6141.customdomain.info")
            .clientId("42d795a9-8abb-4d06-8534-39528af40f8e.apps.googleusercontent.com")
            .defaultProvider("Google")
            .enabled(true)
            .name("sitef6141")
            .resourceGroupName("testrg123")
            .runtimeVersion("~1")
            .tokenRefreshExtensionHours(120)
            .tokenStoreEnabled(true)
            .unauthenticatedClientAction("RedirectToLoginPage")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const webAppAuthSettings = new azure_native.web.WebAppAuthSettings("webAppAuthSettings", {
    allowedExternalRedirectUrls: [
        "sitef6141.customdomain.net",
        "sitef6141.customdomain.info",
    ],
    clientId: "42d795a9-8abb-4d06-8534-39528af40f8e.apps.googleusercontent.com",
    defaultProvider: azure_native.web.BuiltInAuthenticationProvider.Google,
    enabled: true,
    name: "sitef6141",
    resourceGroupName: "testrg123",
    runtimeVersion: "~1",
    tokenRefreshExtensionHours: 120,
    tokenStoreEnabled: true,
    unauthenticatedClientAction: azure_native.web.UnauthenticatedClientAction.RedirectToLoginPage,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

web_app_auth_settings = azure_native.web.WebAppAuthSettings("webAppAuthSettings",
    allowed_external_redirect_urls=[
        "sitef6141.customdomain.net",
        "sitef6141.customdomain.info",
    ],
    client_id="42d795a9-8abb-4d06-8534-39528af40f8e.apps.googleusercontent.com",
    default_provider=azure_native.web.BuiltInAuthenticationProvider.GOOGLE,
    enabled=True,
    name="sitef6141",
    resource_group_name="testrg123",
    runtime_version="~1",
    token_refresh_extension_hours=120,
    token_store_enabled=True,
    unauthenticated_client_action=azure_native.web.UnauthenticatedClientAction.REDIRECT_TO_LOGIN_PAGE)

```

```yaml
resources:
  webAppAuthSettings:
    type: azure-native:web:WebAppAuthSettings
    properties:
      allowedExternalRedirectUrls:
        - sitef6141.customdomain.net
        - sitef6141.customdomain.info
      clientId: 42d795a9-8abb-4d06-8534-39528af40f8e.apps.googleusercontent.com
      defaultProvider: Google
      enabled: true
      name: sitef6141
      resourceGroupName: testrg123
      runtimeVersion: ~1
      tokenRefreshExtensionHours: 120
      tokenStoreEnabled: true
      unauthenticatedClientAction: RedirectToLoginPage

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:web:WebAppAuthSettings authsettings /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testrg123/providers/Microsoft.Web/sites/sitef6141/config/authsettings 
```
