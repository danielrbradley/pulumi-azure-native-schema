Details of a particular extension in HCI Cluster.
API Version: 2023-02-01.
Previous API Version: 2021-01-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Arc Extension
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var extension = new AzureNative.AzureStackHCI.Extension("extension", new()
    {
        ArcSettingName = "default",
        ClusterName = "myCluster",
        EnableAutomaticUpgrade = false,
        ExtensionName = "MicrosoftMonitoringAgent",
        ProtectedSettings = 
        {
            { "workspaceKey", "xx" },
        },
        Publisher = "Microsoft.Compute",
        ResourceGroupName = "test-rg",
        Settings = 
        {
            { "workspaceId", "xx" },
        },
        Type = "MicrosoftMonitoringAgent",
        TypeHandlerVersion = "1.10",
    });

});


```

```go
package main

import (
	azurestackhci "github.com/pulumi/pulumi-azure-native-sdk/azurestackhci"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := azurestackhci.NewExtension(ctx, "extension", &azurestackhci.ExtensionArgs{
			ArcSettingName:         pulumi.String("default"),
			ClusterName:            pulumi.String("myCluster"),
			EnableAutomaticUpgrade: pulumi.Bool(false),
			ExtensionName:          pulumi.String("MicrosoftMonitoringAgent"),
			ProtectedSettings: pulumi.Any{
				WorkspaceKey: "xx",
			},
			Publisher:         pulumi.String("Microsoft.Compute"),
			ResourceGroupName: pulumi.String("test-rg"),
			Settings: pulumi.Any{
				WorkspaceId: "xx",
			},
			Type:               pulumi.String("MicrosoftMonitoringAgent"),
			TypeHandlerVersion: pulumi.String("1.10"),
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
import com.pulumi.azurenative.azurestackhci.Extension;
import com.pulumi.azurenative.azurestackhci.ExtensionArgs;
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
            .arcSettingName("default")
            .clusterName("myCluster")
            .enableAutomaticUpgrade(false)
            .extensionName("MicrosoftMonitoringAgent")
            .protectedSettings(Map.of("workspaceKey", "xx"))
            .publisher("Microsoft.Compute")
            .resourceGroupName("test-rg")
            .settings(Map.of("workspaceId", "xx"))
            .type("MicrosoftMonitoringAgent")
            .typeHandlerVersion("1.10")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const extension = new azure_native.azurestackhci.Extension("extension", {
    arcSettingName: "default",
    clusterName: "myCluster",
    enableAutomaticUpgrade: false,
    extensionName: "MicrosoftMonitoringAgent",
    protectedSettings: {
        workspaceKey: "xx",
    },
    publisher: "Microsoft.Compute",
    resourceGroupName: "test-rg",
    settings: {
        workspaceId: "xx",
    },
    type: "MicrosoftMonitoringAgent",
    typeHandlerVersion: "1.10",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

extension = azure_native.azurestackhci.Extension("extension",
    arc_setting_name="default",
    cluster_name="myCluster",
    enable_automatic_upgrade=False,
    extension_name="MicrosoftMonitoringAgent",
    protected_settings={
        "workspaceKey": "xx",
    },
    publisher="Microsoft.Compute",
    resource_group_name="test-rg",
    settings={
        "workspaceId": "xx",
    },
    type="MicrosoftMonitoringAgent",
    type_handler_version="1.10")

```

```yaml
resources:
  extension:
    type: azure-native:azurestackhci:Extension
    properties:
      arcSettingName: default
      clusterName: myCluster
      enableAutomaticUpgrade: false
      extensionName: MicrosoftMonitoringAgent
      protectedSettings:
        workspaceKey: xx
      publisher: Microsoft.Compute
      resourceGroupName: test-rg
      settings:
        workspaceId: xx
      type: MicrosoftMonitoringAgent
      typeHandlerVersion: '1.10'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:azurestackhci:Extension MicrosoftMonitoringAgent /subscriptions/fd3c3665-1729-4b7b-9a38-238e83b0f98b/resourceGroups/test-rg/providers/Microsoft.AzureStackHCI/clusters/myCluster/arcSettings/default/extensions/MicrosoftMonitoringAgent 
```
