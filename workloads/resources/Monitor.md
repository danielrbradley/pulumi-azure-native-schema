SAP monitor info on Azure (ARM properties and SAP monitor properties)
API Version: 2023-04-01.
Previous API Version: 2021-12-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a SAP monitor
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var monitor = new AzureNative.Workloads.Monitor("monitor", new()
    {
        AppLocation = "westus",
        Location = "westus",
        LogAnalyticsWorkspaceArmId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/microsoft.operationalinsights/workspaces/myWorkspace",
        ManagedResourceGroupConfiguration = new AzureNative.Workloads.Inputs.ManagedRGConfigurationArgs
        {
            Name = "myManagedRg",
        },
        MonitorName = "mySapMonitor",
        MonitorSubnet = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet",
        ResourceGroupName = "myResourceGroup",
        RoutingPreference = "RouteAll",
        Tags = 
        {
            { "key", "value" },
        },
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewMonitor(ctx, "monitor", &workloads.MonitorArgs{
			AppLocation:                pulumi.String("westus"),
			Location:                   pulumi.String("westus"),
			LogAnalyticsWorkspaceArmId: pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/microsoft.operationalinsights/workspaces/myWorkspace"),
			ManagedResourceGroupConfiguration: &workloads.ManagedRGConfigurationArgs{
				Name: pulumi.String("myManagedRg"),
			},
			MonitorName:       pulumi.String("mySapMonitor"),
			MonitorSubnet:     pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			RoutingPreference: pulumi.String("RouteAll"),
			Tags: pulumi.StringMap{
				"key": pulumi.String("value"),
			},
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
import com.pulumi.azurenative.workloads.Monitor;
import com.pulumi.azurenative.workloads.MonitorArgs;
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
        var monitor = new Monitor("monitor", MonitorArgs.builder()        
            .appLocation("westus")
            .location("westus")
            .logAnalyticsWorkspaceArmId("/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/microsoft.operationalinsights/workspaces/myWorkspace")
            .managedResourceGroupConfiguration(Map.of("name", "myManagedRg"))
            .monitorName("mySapMonitor")
            .monitorSubnet("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet")
            .resourceGroupName("myResourceGroup")
            .routingPreference("RouteAll")
            .tags(Map.of("key", "value"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const monitor = new azure_native.workloads.Monitor("monitor", {
    appLocation: "westus",
    location: "westus",
    logAnalyticsWorkspaceArmId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/microsoft.operationalinsights/workspaces/myWorkspace",
    managedResourceGroupConfiguration: {
        name: "myManagedRg",
    },
    monitorName: "mySapMonitor",
    monitorSubnet: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet",
    resourceGroupName: "myResourceGroup",
    routingPreference: "RouteAll",
    tags: {
        key: "value",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

monitor = azure_native.workloads.Monitor("monitor",
    app_location="westus",
    location="westus",
    log_analytics_workspace_arm_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/microsoft.operationalinsights/workspaces/myWorkspace",
    managed_resource_group_configuration=azure_native.workloads.ManagedRGConfigurationArgs(
        name="myManagedRg",
    ),
    monitor_name="mySapMonitor",
    monitor_subnet="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet",
    resource_group_name="myResourceGroup",
    routing_preference="RouteAll",
    tags={
        "key": "value",
    })

```

```yaml
resources:
  monitor:
    type: azure-native:workloads:Monitor
    properties:
      appLocation: westus
      location: westus
      logAnalyticsWorkspaceArmId: /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/microsoft.operationalinsights/workspaces/myWorkspace
      managedResourceGroupConfiguration:
        name: myManagedRg
      monitorName: mySapMonitor
      monitorSubnet: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet
      resourceGroupName: myResourceGroup
      routingPreference: RouteAll
      tags:
        key: value

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:workloads:Monitor mySapMonitor /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Workloads/monitors/mySapMonitor 
```
