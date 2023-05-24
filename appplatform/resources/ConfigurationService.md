Application Configuration Service resource
API Version: 2022-12-01.
Previous API Version: 2022-01-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ConfigurationServices_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var configurationService = new AzureNative.AppPlatform.ConfigurationService("configurationService", new()
    {
        ConfigurationServiceName = "default",
        Properties = new AzureNative.AppPlatform.Inputs.ConfigurationServicePropertiesArgs
        {
            Settings = new AzureNative.AppPlatform.Inputs.ConfigurationServiceSettingsArgs
            {
                GitProperty = new AzureNative.AppPlatform.Inputs.ConfigurationServiceGitPropertyArgs
                {
                    Repositories = new[]
                    {
                        new AzureNative.AppPlatform.Inputs.ConfigurationServiceGitRepositoryArgs
                        {
                            Label = "master",
                            Name = "fake",
                            Patterns = new[]
                            {
                                "app/dev",
                            },
                            Uri = "https://github.com/fake-user/fake-repository",
                        },
                    },
                },
            },
        },
        ResourceGroupName = "myResourceGroup",
        ServiceName = "myservice",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.appplatform.ConfigurationService;
import com.pulumi.azurenative.appplatform.ConfigurationServiceArgs;
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
        var configurationService = new ConfigurationService("configurationService", ConfigurationServiceArgs.builder()        
            .configurationServiceName("default")
            .properties(Map.of("settings", Map.of("gitProperty", Map.of("repositories", Map.ofEntries(
                Map.entry("label", "master"),
                Map.entry("name", "fake"),
                Map.entry("patterns", "app/dev"),
                Map.entry("uri", "https://github.com/fake-user/fake-repository")
            )))))
            .resourceGroupName("myResourceGroup")
            .serviceName("myservice")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const configurationService = new azure_native.appplatform.ConfigurationService("configurationService", {
    configurationServiceName: "default",
    properties: {
        settings: {
            gitProperty: {
                repositories: [{
                    label: "master",
                    name: "fake",
                    patterns: ["app/dev"],
                    uri: "https://github.com/fake-user/fake-repository",
                }],
            },
        },
    },
    resourceGroupName: "myResourceGroup",
    serviceName: "myservice",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

configuration_service = azure_native.appplatform.ConfigurationService("configurationService",
    configuration_service_name="default",
    properties=azure_native.appplatform.ConfigurationServicePropertiesResponseArgs(
        settings={
            "gitProperty": {
                "repositories": [azure_native.appplatform.ConfigurationServiceGitRepositoryArgs(
                    label="master",
                    name="fake",
                    patterns=["app/dev"],
                    uri="https://github.com/fake-user/fake-repository",
                )],
            },
        },
    ),
    resource_group_name="myResourceGroup",
    service_name="myservice")

```

```yaml
resources:
  configurationService:
    type: azure-native:appplatform:ConfigurationService
    properties:
      configurationServiceName: default
      properties:
        settings:
          gitProperty:
            repositories:
              - label: master
                name: fake
                patterns:
                  - app/dev
                uri: https://github.com/fake-user/fake-repository
      resourceGroupName: myResourceGroup
      serviceName: myservice

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:appplatform:ConfigurationService default /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.AppPlatform/Spring/myservice/configurationServices/default 
```
