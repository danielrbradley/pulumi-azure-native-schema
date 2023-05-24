Configuration settings for the Azure ContainerApp Service Authentication / Authorization feature.
API Version: 2022-10-01.
Previous API Version: 2022-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or Update Container App AuthConfig
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var containerAppsAuthConfig = new AzureNative.App.ContainerAppsAuthConfig("containerAppsAuthConfig", new()
    {
        AuthConfigName = "current",
        ContainerAppName = "testcanadacentral",
        GlobalValidation = new AzureNative.App.Inputs.GlobalValidationArgs
        {
            UnauthenticatedClientAction = AzureNative.App.UnauthenticatedClientActionV2.AllowAnonymous,
        },
        IdentityProviders = new AzureNative.App.Inputs.IdentityProvidersArgs
        {
            Facebook = new AzureNative.App.Inputs.FacebookArgs
            {
                Registration = new AzureNative.App.Inputs.AppRegistrationArgs
                {
                    AppId = "123",
                    AppSecretSettingName = "facebook-secret",
                },
            },
        },
        Platform = new AzureNative.App.Inputs.AuthPlatformArgs
        {
            Enabled = true,
        },
        ResourceGroupName = "workerapps-rg-xj",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.app.ContainerAppsAuthConfig;
import com.pulumi.azurenative.app.ContainerAppsAuthConfigArgs;
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
        var containerAppsAuthConfig = new ContainerAppsAuthConfig("containerAppsAuthConfig", ContainerAppsAuthConfigArgs.builder()        
            .authConfigName("current")
            .containerAppName("testcanadacentral")
            .globalValidation(Map.of("unauthenticatedClientAction", "AllowAnonymous"))
            .identityProviders(Map.of("facebook", Map.of("registration", Map.ofEntries(
                Map.entry("appId", "123"),
                Map.entry("appSecretSettingName", "facebook-secret")
            ))))
            .platform(Map.of("enabled", true))
            .resourceGroupName("workerapps-rg-xj")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const containerAppsAuthConfig = new azure_native.app.ContainerAppsAuthConfig("containerAppsAuthConfig", {
    authConfigName: "current",
    containerAppName: "testcanadacentral",
    globalValidation: {
        unauthenticatedClientAction: azure_native.app.UnauthenticatedClientActionV2.AllowAnonymous,
    },
    identityProviders: {
        facebook: {
            registration: {
                appId: "123",
                appSecretSettingName: "facebook-secret",
            },
        },
    },
    platform: {
        enabled: true,
    },
    resourceGroupName: "workerapps-rg-xj",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

container_apps_auth_config = azure_native.app.ContainerAppsAuthConfig("containerAppsAuthConfig",
    auth_config_name="current",
    container_app_name="testcanadacentral",
    global_validation=azure_native.app.GlobalValidationArgs(
        unauthenticated_client_action=azure_native.app.UnauthenticatedClientActionV2.ALLOW_ANONYMOUS,
    ),
    identity_providers=azure_native.app.IdentityProvidersResponseArgs(
        facebook={
            "registration": azure_native.app.AppRegistrationArgs(
                app_id="123",
                app_secret_setting_name="facebook-secret",
            ),
        },
    ),
    platform=azure_native.app.AuthPlatformArgs(
        enabled=True,
    ),
    resource_group_name="workerapps-rg-xj")

```

```yaml
resources:
  containerAppsAuthConfig:
    type: azure-native:app:ContainerAppsAuthConfig
    properties:
      authConfigName: current
      containerAppName: testcanadacentral
      globalValidation:
        unauthenticatedClientAction: AllowAnonymous
      identityProviders:
        facebook:
          registration:
            appId: '123'
            appSecretSettingName: facebook-secret
      platform:
        enabled: true
      resourceGroupName: workerapps-rg-xj

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:app:ContainerAppsAuthConfig current /subscriptions/651f8027-33e8-4ec4-97b4-f6e9f3dc8744/resourceGroups/workerapps-rg-xj/providers/Microsoft.App/containerApps/myapp/authconfigs/current 
```
