SAP monitor info on Azure (ARM properties and SAP monitor properties)
API Version: 2020-02-07-preview.
Previous API Version: 2020-02-07-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a SAP Monitor
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sapMonitor = new AzureNative.HanaOnAzure.SapMonitor("sapMonitor", new()
    {
        EnableCustomerAnalytics = true,
        Location = "westus",
        LogAnalyticsWorkspaceArmId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/microsoft.operationalinsights/workspaces/myWorkspace",
        LogAnalyticsWorkspaceId = "00000000-0000-0000-0000-000000000000",
        LogAnalyticsWorkspaceSharedKey = "00000000000000000000000000000000000000000000000000000000000000000000000000000000000000==",
        MonitorSubnet = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet",
        ResourceGroupName = "myResourceGroup",
        SapMonitorName = "mySapMonitor",
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
	hanaonazure "github.com/pulumi/pulumi-azure-native-sdk/hanaonazure"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := hanaonazure.NewSapMonitor(ctx, "sapMonitor", &hanaonazure.SapMonitorArgs{
			EnableCustomerAnalytics:        pulumi.Bool(true),
			Location:                       pulumi.String("westus"),
			LogAnalyticsWorkspaceArmId:     pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/microsoft.operationalinsights/workspaces/myWorkspace"),
			LogAnalyticsWorkspaceId:        pulumi.String("00000000-0000-0000-0000-000000000000"),
			LogAnalyticsWorkspaceSharedKey: pulumi.String("00000000000000000000000000000000000000000000000000000000000000000000000000000000000000=="),
			MonitorSubnet:                  pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet"),
			ResourceGroupName:              pulumi.String("myResourceGroup"),
			SapMonitorName:                 pulumi.String("mySapMonitor"),
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
import com.pulumi.azurenative.hanaonazure.SapMonitor;
import com.pulumi.azurenative.hanaonazure.SapMonitorArgs;
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
        var sapMonitor = new SapMonitor("sapMonitor", SapMonitorArgs.builder()        
            .enableCustomerAnalytics(true)
            .location("westus")
            .logAnalyticsWorkspaceArmId("/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/microsoft.operationalinsights/workspaces/myWorkspace")
            .logAnalyticsWorkspaceId("00000000-0000-0000-0000-000000000000")
            .logAnalyticsWorkspaceSharedKey("00000000000000000000000000000000000000000000000000000000000000000000000000000000000000==")
            .monitorSubnet("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet")
            .resourceGroupName("myResourceGroup")
            .sapMonitorName("mySapMonitor")
            .tags(Map.of("key", "value"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sapMonitor = new azure_native.hanaonazure.SapMonitor("sapMonitor", {
    enableCustomerAnalytics: true,
    location: "westus",
    logAnalyticsWorkspaceArmId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/microsoft.operationalinsights/workspaces/myWorkspace",
    logAnalyticsWorkspaceId: "00000000-0000-0000-0000-000000000000",
    logAnalyticsWorkspaceSharedKey: "00000000000000000000000000000000000000000000000000000000000000000000000000000000000000==",
    monitorSubnet: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet",
    resourceGroupName: "myResourceGroup",
    sapMonitorName: "mySapMonitor",
    tags: {
        key: "value",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sap_monitor = azure_native.hanaonazure.SapMonitor("sapMonitor",
    enable_customer_analytics=True,
    location="westus",
    log_analytics_workspace_arm_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/microsoft.operationalinsights/workspaces/myWorkspace",
    log_analytics_workspace_id="00000000-0000-0000-0000-000000000000",
    log_analytics_workspace_shared_key="00000000000000000000000000000000000000000000000000000000000000000000000000000000000000==",
    monitor_subnet="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet",
    resource_group_name="myResourceGroup",
    sap_monitor_name="mySapMonitor",
    tags={
        "key": "value",
    })

```

```yaml
resources:
  sapMonitor:
    type: azure-native:hanaonazure:SapMonitor
    properties:
      enableCustomerAnalytics: true
      location: westus
      logAnalyticsWorkspaceArmId: /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/microsoft.operationalinsights/workspaces/myWorkspace
      logAnalyticsWorkspaceId: 00000000-0000-0000-0000-000000000000
      logAnalyticsWorkspaceSharedKey: 00000000000000000000000000000000000000000000000000000000000000000000000000000000000000==
      monitorSubnet: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myVnet/subnets/mySubnet
      resourceGroupName: myResourceGroup
      sapMonitorName: mySapMonitor
      tags:
        key: value

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:hanaonazure:SapMonitor myHanaInstance /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.HanaOnAzure/hanaInstances/myHanaInstance 
```
