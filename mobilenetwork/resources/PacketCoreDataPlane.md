Packet core data plane resource. Must be created in the same location as its parent packet core control plane.
API Version: 2022-11-01.
Previous API Version: 2022-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create packet core data plane
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var packetCoreDataPlane = new AzureNative.MobileNetwork.PacketCoreDataPlane("packetCoreDataPlane", new()
    {
        Location = "eastus",
        PacketCoreControlPlaneName = "testPacketCoreCP",
        PacketCoreDataPlaneName = "testPacketCoreDP",
        ResourceGroupName = "rg1",
        UserPlaneAccessInterface = new AzureNative.MobileNetwork.Inputs.InterfacePropertiesArgs
        {
            Name = "N3",
        },
    });

});


```

```go
package main

import (
	mobilenetwork "github.com/pulumi/pulumi-azure-native-sdk/mobilenetwork"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := mobilenetwork.NewPacketCoreDataPlane(ctx, "packetCoreDataPlane", &mobilenetwork.PacketCoreDataPlaneArgs{
			Location:                   pulumi.String("eastus"),
			PacketCoreControlPlaneName: pulumi.String("testPacketCoreCP"),
			PacketCoreDataPlaneName:    pulumi.String("testPacketCoreDP"),
			ResourceGroupName:          pulumi.String("rg1"),
			UserPlaneAccessInterface: &mobilenetwork.InterfacePropertiesArgs{
				Name: pulumi.String("N3"),
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
import com.pulumi.azurenative.mobilenetwork.PacketCoreDataPlane;
import com.pulumi.azurenative.mobilenetwork.PacketCoreDataPlaneArgs;
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
        var packetCoreDataPlane = new PacketCoreDataPlane("packetCoreDataPlane", PacketCoreDataPlaneArgs.builder()        
            .location("eastus")
            .packetCoreControlPlaneName("testPacketCoreCP")
            .packetCoreDataPlaneName("testPacketCoreDP")
            .resourceGroupName("rg1")
            .userPlaneAccessInterface(Map.of("name", "N3"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const packetCoreDataPlane = new azure_native.mobilenetwork.PacketCoreDataPlane("packetCoreDataPlane", {
    location: "eastus",
    packetCoreControlPlaneName: "testPacketCoreCP",
    packetCoreDataPlaneName: "testPacketCoreDP",
    resourceGroupName: "rg1",
    userPlaneAccessInterface: {
        name: "N3",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

packet_core_data_plane = azure_native.mobilenetwork.PacketCoreDataPlane("packetCoreDataPlane",
    location="eastus",
    packet_core_control_plane_name="testPacketCoreCP",
    packet_core_data_plane_name="testPacketCoreDP",
    resource_group_name="rg1",
    user_plane_access_interface=azure_native.mobilenetwork.InterfacePropertiesArgs(
        name="N3",
    ))

```

```yaml
resources:
  packetCoreDataPlane:
    type: azure-native:mobilenetwork:PacketCoreDataPlane
    properties:
      location: eastus
      packetCoreControlPlaneName: testPacketCoreCP
      packetCoreDataPlaneName: testPacketCoreDP
      resourceGroupName: rg1
      userPlaneAccessInterface:
        name: N3

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:mobilenetwork:PacketCoreDataPlane TestPacketCoreDP /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/packetCoreControlPlanes/TestPacketCoreCP/packetCoreDataPlanes/TestPacketCoreDP 
```
