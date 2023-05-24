vCenter definition.
API Version: 2023-02-01.
Previous API Version: 2018-07-10. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Add vCenter.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var replicationvCenter = new AzureNative.RecoveryServices.ReplicationvCenter("replicationvCenter", new()
    {
        FabricName = "MadhaviFabric",
        Properties = new AzureNative.RecoveryServices.Inputs.AddVCenterRequestPropertiesArgs
        {
            FriendlyName = "esx-78",
            IpAddress = "inmtest78",
            Port = "443",
            ProcessServerId = "5A720CAB-39CB-F445-BD1662B0B33164B5",
            RunAsAccountId = "2",
        },
        ResourceGroupName = "MadhaviVRG",
        ResourceName = "MadhaviVault",
        VcenterName = "esx-78",
    });

});


```

```go
package main

import (
	recoveryservices "github.com/pulumi/pulumi-azure-native-sdk/recoveryservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := recoveryservices.NewReplicationvCenter(ctx, "replicationvCenter", &recoveryservices.ReplicationvCenterArgs{
			FabricName: pulumi.String("MadhaviFabric"),
			Properties: &recoveryservices.AddVCenterRequestPropertiesArgs{
				FriendlyName:    pulumi.String("esx-78"),
				IpAddress:       pulumi.String("inmtest78"),
				Port:            pulumi.String("443"),
				ProcessServerId: pulumi.String("5A720CAB-39CB-F445-BD1662B0B33164B5"),
				RunAsAccountId:  pulumi.String("2"),
			},
			ResourceGroupName: pulumi.String("MadhaviVRG"),
			ResourceName:      pulumi.String("MadhaviVault"),
			VcenterName:       pulumi.String("esx-78"),
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
import com.pulumi.azurenative.recoveryservices.ReplicationvCenter;
import com.pulumi.azurenative.recoveryservices.ReplicationvCenterArgs;
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
        var replicationvCenter = new ReplicationvCenter("replicationvCenter", ReplicationvCenterArgs.builder()        
            .fabricName("MadhaviFabric")
            .properties(Map.ofEntries(
                Map.entry("friendlyName", "esx-78"),
                Map.entry("ipAddress", "inmtest78"),
                Map.entry("port", "443"),
                Map.entry("processServerId", "5A720CAB-39CB-F445-BD1662B0B33164B5"),
                Map.entry("runAsAccountId", "2")
            ))
            .resourceGroupName("MadhaviVRG")
            .resourceName("MadhaviVault")
            .vcenterName("esx-78")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const replicationvCenter = new azure_native.recoveryservices.ReplicationvCenter("replicationvCenter", {
    fabricName: "MadhaviFabric",
    properties: {
        friendlyName: "esx-78",
        ipAddress: "inmtest78",
        port: "443",
        processServerId: "5A720CAB-39CB-F445-BD1662B0B33164B5",
        runAsAccountId: "2",
    },
    resourceGroupName: "MadhaviVRG",
    resourceName: "MadhaviVault",
    vcenterName: "esx-78",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

replicationv_center = azure_native.recoveryservices.ReplicationvCenter("replicationvCenter",
    fabric_name="MadhaviFabric",
    properties=azure_native.recoveryservices.AddVCenterRequestPropertiesArgs(
        friendly_name="esx-78",
        ip_address="inmtest78",
        port="443",
        process_server_id="5A720CAB-39CB-F445-BD1662B0B33164B5",
        run_as_account_id="2",
    ),
    resource_group_name="MadhaviVRG",
    resource_name_="MadhaviVault",
    vcenter_name="esx-78")

```

```yaml
resources:
  replicationvCenter:
    type: azure-native:recoveryservices:ReplicationvCenter
    properties:
      fabricName: MadhaviFabric
      properties:
        friendlyName: esx-78
        ipAddress: inmtest78
        port: '443'
        processServerId: 5A720CAB-39CB-F445-BD1662B0B33164B5
        runAsAccountId: '2'
      resourceGroupName: MadhaviVRG
      resourceName: MadhaviVault
      vcenterName: esx-78

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:recoveryservices:ReplicationvCenter esx-78 /Subscriptions/7c943c1b-5122-4097-90c8-861411bdd574/resourceGroups/MadhaviVRG/providers/Microsoft.RecoveryServices/vaults/MadhaviVault/replicationFabrics/239f778f368e34f78216d81f030725cdf2033174b47879b9f2eeede06fdd9c4d/replicationvCenters/esx-78 
```
