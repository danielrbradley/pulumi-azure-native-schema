An Azure Monitor Workspace definition
API Version: 2021-06-03-preview.
Previous API Version: 2021-06-03-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update workspace
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var azureMonitorWorkspace = new AzureNative.Monitor.AzureMonitorWorkspace("azureMonitorWorkspace", new()
    {
        AzureMonitorWorkspaceName = "myAzureMonitorWorkspace",
        Location = "eastus",
        ResourceGroupName = "myResourceGroup",
    });

});


```

```go
package main

import (
	monitor "github.com/pulumi/pulumi-azure-native-sdk/monitor"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := monitor.NewAzureMonitorWorkspace(ctx, "azureMonitorWorkspace", &monitor.AzureMonitorWorkspaceArgs{
			AzureMonitorWorkspaceName: pulumi.String("myAzureMonitorWorkspace"),
			Location:                  pulumi.String("eastus"),
			ResourceGroupName:         pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.monitor.AzureMonitorWorkspace;
import com.pulumi.azurenative.monitor.AzureMonitorWorkspaceArgs;
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
        var azureMonitorWorkspace = new AzureMonitorWorkspace("azureMonitorWorkspace", AzureMonitorWorkspaceArgs.builder()        
            .azureMonitorWorkspaceName("myAzureMonitorWorkspace")
            .location("eastus")
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const azureMonitorWorkspace = new azure_native.monitor.AzureMonitorWorkspace("azureMonitorWorkspace", {
    azureMonitorWorkspaceName: "myAzureMonitorWorkspace",
    location: "eastus",
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

azure_monitor_workspace = azure_native.monitor.AzureMonitorWorkspace("azureMonitorWorkspace",
    azure_monitor_workspace_name="myAzureMonitorWorkspace",
    location="eastus",
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  azureMonitorWorkspace:
    type: azure-native:monitor:AzureMonitorWorkspace
    properties:
      azureMonitorWorkspaceName: myAzureMonitorWorkspace
      location: eastus
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:monitor:AzureMonitorWorkspace myAzureMonitorWorkspace /subscriptions/703362b3-f278-4e4b-9179-c76eaf41ffc2/resourceGroups/myResourceGroup/providers/Microsoft.Monitor/accounts/myAzureMonitorWorkspace 
```
