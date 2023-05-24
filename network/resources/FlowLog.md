A flow log resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update flow log
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var flowLog = new AzureNative.Network.FlowLog("flowLog", new()
    {
        Enabled = true,
        FlowLogName = "fl",
        Format = new AzureNative.Network.Inputs.FlowLogFormatParametersArgs
        {
            Type = "JSON",
            Version = 1,
        },
        Location = "centraluseuap",
        NetworkWatcherName = "nw1",
        ResourceGroupName = "rg1",
        StorageId = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Storage/storageAccounts/nwtest1mgvbfmqsigdxe",
        TargetResourceId = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/networkSecurityGroups/desmondcentral-nsg",
    });

});


```

```go
package main

import (
	network "github.com/pulumi/pulumi-azure-native-sdk/network"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := network.NewFlowLog(ctx, "flowLog", &network.FlowLogArgs{
			Enabled:     pulumi.Bool(true),
			FlowLogName: pulumi.String("fl"),
			Format: &network.FlowLogFormatParametersArgs{
				Type:    pulumi.String("JSON"),
				Version: pulumi.Int(1),
			},
			Location:           pulumi.String("centraluseuap"),
			NetworkWatcherName: pulumi.String("nw1"),
			ResourceGroupName:  pulumi.String("rg1"),
			StorageId:          pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Storage/storageAccounts/nwtest1mgvbfmqsigdxe"),
			TargetResourceId:   pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/networkSecurityGroups/desmondcentral-nsg"),
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
import com.pulumi.azurenative.network.FlowLog;
import com.pulumi.azurenative.network.FlowLogArgs;
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
        var flowLog = new FlowLog("flowLog", FlowLogArgs.builder()        
            .enabled(true)
            .flowLogName("fl")
            .format(Map.ofEntries(
                Map.entry("type", "JSON"),
                Map.entry("version", 1)
            ))
            .location("centraluseuap")
            .networkWatcherName("nw1")
            .resourceGroupName("rg1")
            .storageId("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Storage/storageAccounts/nwtest1mgvbfmqsigdxe")
            .targetResourceId("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/networkSecurityGroups/desmondcentral-nsg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const flowLog = new azure_native.network.FlowLog("flowLog", {
    enabled: true,
    flowLogName: "fl",
    format: {
        type: "JSON",
        version: 1,
    },
    location: "centraluseuap",
    networkWatcherName: "nw1",
    resourceGroupName: "rg1",
    storageId: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Storage/storageAccounts/nwtest1mgvbfmqsigdxe",
    targetResourceId: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/networkSecurityGroups/desmondcentral-nsg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

flow_log = azure_native.network.FlowLog("flowLog",
    enabled=True,
    flow_log_name="fl",
    format=azure_native.network.FlowLogFormatParametersArgs(
        type="JSON",
        version=1,
    ),
    location="centraluseuap",
    network_watcher_name="nw1",
    resource_group_name="rg1",
    storage_id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Storage/storageAccounts/nwtest1mgvbfmqsigdxe",
    target_resource_id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/networkSecurityGroups/desmondcentral-nsg")

```

```yaml
resources:
  flowLog:
    type: azure-native:network:FlowLog
    properties:
      enabled: true
      flowLogName: fl
      format:
        type: JSON
        version: 1
      location: centraluseuap
      networkWatcherName: nw1
      resourceGroupName: rg1
      storageId: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Storage/storageAccounts/nwtest1mgvbfmqsigdxe
      targetResourceId: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/networkSecurityGroups/desmondcentral-nsg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:FlowLog Microsoft.Networkdesmond-rgdesmondcentral-nsg /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/networkWatchers/nw/FlowLogs/fl 
```
