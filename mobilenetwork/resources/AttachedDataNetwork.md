Attached data network resource. Must be created in the same location as its parent packet core data plane.
API Version: 2022-11-01.
Previous API Version: 2022-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create attached data network
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var attachedDataNetwork = new AzureNative.MobileNetwork.AttachedDataNetwork("attachedDataNetwork", new()
    {
        AttachedDataNetworkName = "TestAttachedDataNetwork",
        DnsAddresses = new[]
        {
            "1.1.1.1",
        },
        Location = "eastus",
        NaptConfiguration = new AzureNative.MobileNetwork.Inputs.NaptConfigurationArgs
        {
            Enabled = "Enabled",
            PinholeLimits = 65536,
            PinholeTimeouts = new AzureNative.MobileNetwork.Inputs.PinholeTimeoutsArgs
            {
                Icmp = 30,
                Tcp = 180,
                Udp = 30,
            },
            PortRange = new AzureNative.MobileNetwork.Inputs.PortRangeArgs
            {
                MaxPort = 49999,
                MinPort = 1024,
            },
            PortReuseHoldTime = new AzureNative.MobileNetwork.Inputs.PortReuseHoldTimesArgs
            {
                Tcp = 120,
                Udp = 60,
            },
        },
        PacketCoreControlPlaneName = "TestPacketCoreCP",
        PacketCoreDataPlaneName = "TestPacketCoreDP",
        ResourceGroupName = "rg1",
        UserEquipmentAddressPoolPrefix = new[]
        {
            "2.2.0.0/16",
        },
        UserEquipmentStaticAddressPoolPrefix = new[]
        {
            "2.4.0.0/16",
        },
        UserPlaneDataInterface = new AzureNative.MobileNetwork.Inputs.InterfacePropertiesArgs
        {
            Name = "N6",
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
		_, err := mobilenetwork.NewAttachedDataNetwork(ctx, "attachedDataNetwork", &mobilenetwork.AttachedDataNetworkArgs{
			AttachedDataNetworkName: pulumi.String("TestAttachedDataNetwork"),
			DnsAddresses: pulumi.StringArray{
				pulumi.String("1.1.1.1"),
			},
			Location: pulumi.String("eastus"),
			NaptConfiguration: mobilenetwork.NaptConfigurationResponse{
				Enabled:       pulumi.String("Enabled"),
				PinholeLimits: pulumi.Int(65536),
				PinholeTimeouts: &mobilenetwork.PinholeTimeoutsArgs{
					Icmp: pulumi.Int(30),
					Tcp:  pulumi.Int(180),
					Udp:  pulumi.Int(30),
				},
				PortRange: &mobilenetwork.PortRangeArgs{
					MaxPort: pulumi.Int(49999),
					MinPort: pulumi.Int(1024),
				},
				PortReuseHoldTime: &mobilenetwork.PortReuseHoldTimesArgs{
					Tcp: pulumi.Int(120),
					Udp: pulumi.Int(60),
				},
			},
			PacketCoreControlPlaneName: pulumi.String("TestPacketCoreCP"),
			PacketCoreDataPlaneName:    pulumi.String("TestPacketCoreDP"),
			ResourceGroupName:          pulumi.String("rg1"),
			UserEquipmentAddressPoolPrefix: pulumi.StringArray{
				pulumi.String("2.2.0.0/16"),
			},
			UserEquipmentStaticAddressPoolPrefix: pulumi.StringArray{
				pulumi.String("2.4.0.0/16"),
			},
			UserPlaneDataInterface: &mobilenetwork.InterfacePropertiesArgs{
				Name: pulumi.String("N6"),
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
import com.pulumi.azurenative.mobilenetwork.AttachedDataNetwork;
import com.pulumi.azurenative.mobilenetwork.AttachedDataNetworkArgs;
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
        var attachedDataNetwork = new AttachedDataNetwork("attachedDataNetwork", AttachedDataNetworkArgs.builder()        
            .attachedDataNetworkName("TestAttachedDataNetwork")
            .dnsAddresses("1.1.1.1")
            .location("eastus")
            .naptConfiguration(Map.ofEntries(
                Map.entry("enabled", "Enabled"),
                Map.entry("pinholeLimits", 65536),
                Map.entry("pinholeTimeouts", Map.ofEntries(
                    Map.entry("icmp", 30),
                    Map.entry("tcp", 180),
                    Map.entry("udp", 30)
                )),
                Map.entry("portRange", Map.ofEntries(
                    Map.entry("maxPort", 49999),
                    Map.entry("minPort", 1024)
                )),
                Map.entry("portReuseHoldTime", Map.ofEntries(
                    Map.entry("tcp", 120),
                    Map.entry("udp", 60)
                ))
            ))
            .packetCoreControlPlaneName("TestPacketCoreCP")
            .packetCoreDataPlaneName("TestPacketCoreDP")
            .resourceGroupName("rg1")
            .userEquipmentAddressPoolPrefix("2.2.0.0/16")
            .userEquipmentStaticAddressPoolPrefix("2.4.0.0/16")
            .userPlaneDataInterface(Map.of("name", "N6"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const attachedDataNetwork = new azure_native.mobilenetwork.AttachedDataNetwork("attachedDataNetwork", {
    attachedDataNetworkName: "TestAttachedDataNetwork",
    dnsAddresses: ["1.1.1.1"],
    location: "eastus",
    naptConfiguration: {
        enabled: "Enabled",
        pinholeLimits: 65536,
        pinholeTimeouts: {
            icmp: 30,
            tcp: 180,
            udp: 30,
        },
        portRange: {
            maxPort: 49999,
            minPort: 1024,
        },
        portReuseHoldTime: {
            tcp: 120,
            udp: 60,
        },
    },
    packetCoreControlPlaneName: "TestPacketCoreCP",
    packetCoreDataPlaneName: "TestPacketCoreDP",
    resourceGroupName: "rg1",
    userEquipmentAddressPoolPrefix: ["2.2.0.0/16"],
    userEquipmentStaticAddressPoolPrefix: ["2.4.0.0/16"],
    userPlaneDataInterface: {
        name: "N6",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

attached_data_network = azure_native.mobilenetwork.AttachedDataNetwork("attachedDataNetwork",
    attached_data_network_name="TestAttachedDataNetwork",
    dns_addresses=["1.1.1.1"],
    location="eastus",
    napt_configuration=azure_native.mobilenetwork.NaptConfigurationResponseArgs(
        enabled="Enabled",
        pinhole_limits=65536,
        pinhole_timeouts=azure_native.mobilenetwork.PinholeTimeoutsArgs(
            icmp=30,
            tcp=180,
            udp=30,
        ),
        port_range=azure_native.mobilenetwork.PortRangeArgs(
            max_port=49999,
            min_port=1024,
        ),
        port_reuse_hold_time=azure_native.mobilenetwork.PortReuseHoldTimesArgs(
            tcp=120,
            udp=60,
        ),
    ),
    packet_core_control_plane_name="TestPacketCoreCP",
    packet_core_data_plane_name="TestPacketCoreDP",
    resource_group_name="rg1",
    user_equipment_address_pool_prefix=["2.2.0.0/16"],
    user_equipment_static_address_pool_prefix=["2.4.0.0/16"],
    user_plane_data_interface=azure_native.mobilenetwork.InterfacePropertiesArgs(
        name="N6",
    ))

```

```yaml
resources:
  attachedDataNetwork:
    type: azure-native:mobilenetwork:AttachedDataNetwork
    properties:
      attachedDataNetworkName: TestAttachedDataNetwork
      dnsAddresses:
        - 1.1.1.1
      location: eastus
      naptConfiguration:
        enabled: Enabled
        pinholeLimits: 65536
        pinholeTimeouts:
          icmp: 30
          tcp: 180
          udp: 30
        portRange:
          maxPort: 49999
          minPort: 1024
        portReuseHoldTime:
          tcp: 120
          udp: 60
      packetCoreControlPlaneName: TestPacketCoreCP
      packetCoreDataPlaneName: TestPacketCoreDP
      resourceGroupName: rg1
      userEquipmentAddressPoolPrefix:
        - 2.2.0.0/16
      userEquipmentStaticAddressPoolPrefix:
        - 2.4.0.0/16
      userPlaneDataInterface:
        name: N6

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:mobilenetwork:AttachedDataNetwork TestAttachedDataNetwork /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/packetCoreControlPlanes/TestPacketCoreCP/packetCoreDataPlanes/TestPacketCoreDP/attachedDataNetworks/TestAttachedDataNetwork 
```
