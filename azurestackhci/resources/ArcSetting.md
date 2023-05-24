ArcSetting details.
API Version: 2023-02-01.
Previous API Version: 2021-01-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create ArcSetting
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var arcSetting = new AzureNative.AzureStackHCI.ArcSetting("arcSetting", new()
    {
        ArcSettingName = "default",
        ClusterName = "myCluster",
        ResourceGroupName = "test-rg",
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
		_, err := azurestackhci.NewArcSetting(ctx, "arcSetting", &azurestackhci.ArcSettingArgs{
			ArcSettingName:    pulumi.String("default"),
			ClusterName:       pulumi.String("myCluster"),
			ResourceGroupName: pulumi.String("test-rg"),
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
import com.pulumi.azurenative.azurestackhci.ArcSetting;
import com.pulumi.azurenative.azurestackhci.ArcSettingArgs;
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
        var arcSetting = new ArcSetting("arcSetting", ArcSettingArgs.builder()        
            .arcSettingName("default")
            .clusterName("myCluster")
            .resourceGroupName("test-rg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const arcSetting = new azure_native.azurestackhci.ArcSetting("arcSetting", {
    arcSettingName: "default",
    clusterName: "myCluster",
    resourceGroupName: "test-rg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

arc_setting = azure_native.azurestackhci.ArcSetting("arcSetting",
    arc_setting_name="default",
    cluster_name="myCluster",
    resource_group_name="test-rg")

```

```yaml
resources:
  arcSetting:
    type: azure-native:azurestackhci:ArcSetting
    properties:
      arcSettingName: default
      clusterName: myCluster
      resourceGroupName: test-rg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:azurestackhci:ArcSetting myresource1 /subscriptions/fd3c3665-1729-4b7b-9a38-238e83b0f98b/resourceGroups/test-rg/providers/Microsoft.AzureStackHCI/clusters/myCluster/arcSettings/default 
```
