Config Server resource
API Version: 2022-12-01.
Previous API Version: 2020-07-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ConfigServers_UpdatePut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var configServer = new AzureNative.AppPlatform.ConfigServer("configServer", new()
    {
        Properties = new AzureNative.AppPlatform.Inputs.ConfigServerPropertiesArgs
        {
            ConfigServer = new AzureNative.AppPlatform.Inputs.ConfigServerSettingsArgs
            {
                GitProperty = new AzureNative.AppPlatform.Inputs.ConfigServerGitPropertyArgs
                {
                    Label = "master",
                    SearchPaths = new[]
                    {
                        "/",
                    },
                    Uri = "https://github.com/fake-user/fake-repository.git",
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
import com.pulumi.azurenative.appplatform.ConfigServer;
import com.pulumi.azurenative.appplatform.ConfigServerArgs;
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
        var configServer = new ConfigServer("configServer", ConfigServerArgs.builder()        
            .properties(Map.of("configServer", Map.of("gitProperty", Map.ofEntries(
                Map.entry("label", "master"),
                Map.entry("searchPaths", "/"),
                Map.entry("uri", "https://github.com/fake-user/fake-repository.git")
            ))))
            .resourceGroupName("myResourceGroup")
            .serviceName("myservice")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const configServer = new azure_native.appplatform.ConfigServer("configServer", {
    properties: {
        configServer: {
            gitProperty: {
                label: "master",
                searchPaths: ["/"],
                uri: "https://github.com/fake-user/fake-repository.git",
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

config_server = azure_native.appplatform.ConfigServer("configServer",
    properties=azure_native.appplatform.ConfigServerPropertiesResponseArgs(
        config_server={
            "gitProperty": azure_native.appplatform.ConfigServerGitPropertyArgs(
                label="master",
                search_paths=["/"],
                uri="https://github.com/fake-user/fake-repository.git",
            ),
        },
    ),
    resource_group_name="myResourceGroup",
    service_name="myservice")

```

```yaml
resources:
  configServer:
    type: azure-native:appplatform:ConfigServer
    properties:
      properties:
        configServer:
          gitProperty:
            label: master
            searchPaths:
              - /
            uri: https://github.com/fake-user/fake-repository.git
      resourceGroupName: myResourceGroup
      serviceName: myservice

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:appplatform:ConfigServer default /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.AppPlatform/Spring/myservice/configServers/default 
```
