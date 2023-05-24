NSX DHCP
API Version: 2022-05-01.
Previous API Version: 2020-07-17-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### WorkloadNetworks_CreateDhcp
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var workloadNetworkDhcp = new AzureNative.AVS.WorkloadNetworkDhcp("workloadNetworkDhcp", new()
    {
        DhcpId = "dhcp1",
        PrivateCloudName = "cloud1",
        Properties = new AzureNative.AVS.Inputs.WorkloadNetworkDhcpServerArgs
        {
            DhcpType = "SERVER",
            DisplayName = "dhcpConfigurations1",
            LeaseTime = 86400,
            Revision = 1,
            ServerAddress = "40.1.5.1/24",
        },
        ResourceGroupName = "group1",
    });

});


```

```go
package main

import (
	avs "github.com/pulumi/pulumi-azure-native-sdk/avs"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := avs.NewWorkloadNetworkDhcp(ctx, "workloadNetworkDhcp", &avs.WorkloadNetworkDhcpArgs{
			DhcpId:           pulumi.String("dhcp1"),
			PrivateCloudName: pulumi.String("cloud1"),
			Properties: avs.WorkloadNetworkDhcpServer{
				DhcpType:      "SERVER",
				DisplayName:   "dhcpConfigurations1",
				LeaseTime:     86400,
				Revision:      1,
				ServerAddress: "40.1.5.1/24",
			},
			ResourceGroupName: pulumi.String("group1"),
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
import com.pulumi.azurenative.avs.WorkloadNetworkDhcp;
import com.pulumi.azurenative.avs.WorkloadNetworkDhcpArgs;
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
        var workloadNetworkDhcp = new WorkloadNetworkDhcp("workloadNetworkDhcp", WorkloadNetworkDhcpArgs.builder()        
            .dhcpId("dhcp1")
            .privateCloudName("cloud1")
            .properties(Map.ofEntries(
                Map.entry("dhcpType", "SERVER"),
                Map.entry("displayName", "dhcpConfigurations1"),
                Map.entry("leaseTime", 86400),
                Map.entry("revision", 1),
                Map.entry("serverAddress", "40.1.5.1/24")
            ))
            .resourceGroupName("group1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const workloadNetworkDhcp = new azure_native.avs.WorkloadNetworkDhcp("workloadNetworkDhcp", {
    dhcpId: "dhcp1",
    privateCloudName: "cloud1",
    properties: {
        dhcpType: "SERVER",
        displayName: "dhcpConfigurations1",
        leaseTime: 86400,
        revision: 1,
        serverAddress: "40.1.5.1/24",
    },
    resourceGroupName: "group1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

workload_network_dhcp = azure_native.avs.WorkloadNetworkDhcp("workloadNetworkDhcp",
    dhcp_id="dhcp1",
    private_cloud_name="cloud1",
    properties=azure_native.avs.WorkloadNetworkDhcpServerArgs(
        dhcp_type="SERVER",
        display_name="dhcpConfigurations1",
        lease_time=86400,
        revision=1,
        server_address="40.1.5.1/24",
    ),
    resource_group_name="group1")

```

```yaml
resources:
  workloadNetworkDhcp:
    type: azure-native:avs:WorkloadNetworkDhcp
    properties:
      dhcpId: dhcp1
      privateCloudName: cloud1
      properties:
        dhcpType: SERVER
        displayName: dhcpConfigurations1
        leaseTime: 86400
        revision: 1
        serverAddress: 40.1.5.1/24
      resourceGroupName: group1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:avs:WorkloadNetworkDhcp dhcp1 /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/group1/providers/Microsoft.AVS/privateClouds/cloud1/workloadNetworks/default/dhcpConfigurations/dhcpConfigurations1 
```
