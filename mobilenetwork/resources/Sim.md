SIM resource.
API Version: 2022-11-01.
Previous API Version: 2022-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create SIM
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sim = new AzureNative.MobileNetwork.Sim("sim", new()
    {
        AuthenticationKey = "00000000000000000000000000000000",
        DeviceType = "Video camera",
        IntegratedCircuitCardIdentifier = "8900000000000000000",
        InternationalMobileSubscriberIdentity = "00000",
        OperatorKeyCode = "00000000000000000000000000000000",
        ResourceGroupName = "rg1",
        SimGroupName = "testSimGroup",
        SimName = "testSim",
        SimPolicy = new AzureNative.MobileNetwork.Inputs.SimPolicyResourceIdArgs
        {
            Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/simPolicies/MySimPolicy",
        },
        StaticIpConfiguration = new[]
        {
            new AzureNative.MobileNetwork.Inputs.SimStaticIpPropertiesArgs
            {
                AttachedDataNetwork = new AzureNative.MobileNetwork.Inputs.AttachedDataNetworkResourceIdArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/packetCoreControlPlanes/TestPacketCoreCP/packetCoreDataPlanes/TestPacketCoreDP/attachedDataNetworks/TestAttachedDataNetwork",
                },
                Slice = new AzureNative.MobileNetwork.Inputs.SliceResourceIdArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/slices/testSlice",
                },
                StaticIp = new AzureNative.MobileNetwork.Inputs.SimStaticIpPropertiesStaticIpArgs
                {
                    Ipv4Address = "2.4.0.1",
                },
            },
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
		_, err := mobilenetwork.NewSim(ctx, "sim", &mobilenetwork.SimArgs{
			AuthenticationKey:                     pulumi.String("00000000000000000000000000000000"),
			DeviceType:                            pulumi.String("Video camera"),
			IntegratedCircuitCardIdentifier:       pulumi.String("8900000000000000000"),
			InternationalMobileSubscriberIdentity: pulumi.String("00000"),
			OperatorKeyCode:                       pulumi.String("00000000000000000000000000000000"),
			ResourceGroupName:                     pulumi.String("rg1"),
			SimGroupName:                          pulumi.String("testSimGroup"),
			SimName:                               pulumi.String("testSim"),
			SimPolicy: &mobilenetwork.SimPolicyResourceIdArgs{
				Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/simPolicies/MySimPolicy"),
			},
			StaticIpConfiguration: []mobilenetwork.SimStaticIpPropertiesArgs{
				{
					AttachedDataNetwork: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/packetCoreControlPlanes/TestPacketCoreCP/packetCoreDataPlanes/TestPacketCoreDP/attachedDataNetworks/TestAttachedDataNetwork"),
					},
					Slice: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/slices/testSlice"),
					},
					StaticIp: {
						Ipv4Address: pulumi.String("2.4.0.1"),
					},
				},
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
import com.pulumi.azurenative.mobilenetwork.Sim;
import com.pulumi.azurenative.mobilenetwork.SimArgs;
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
        var sim = new Sim("sim", SimArgs.builder()        
            .authenticationKey("00000000000000000000000000000000")
            .deviceType("Video camera")
            .integratedCircuitCardIdentifier("8900000000000000000")
            .internationalMobileSubscriberIdentity("00000")
            .operatorKeyCode("00000000000000000000000000000000")
            .resourceGroupName("rg1")
            .simGroupName("testSimGroup")
            .simName("testSim")
            .simPolicy(Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/simPolicies/MySimPolicy"))
            .staticIpConfiguration(Map.ofEntries(
                Map.entry("attachedDataNetwork", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/packetCoreControlPlanes/TestPacketCoreCP/packetCoreDataPlanes/TestPacketCoreDP/attachedDataNetworks/TestAttachedDataNetwork")),
                Map.entry("slice", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/slices/testSlice")),
                Map.entry("staticIp", Map.of("ipv4Address", "2.4.0.1"))
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sim = new azure_native.mobilenetwork.Sim("sim", {
    authenticationKey: "00000000000000000000000000000000",
    deviceType: "Video camera",
    integratedCircuitCardIdentifier: "8900000000000000000",
    internationalMobileSubscriberIdentity: "00000",
    operatorKeyCode: "00000000000000000000000000000000",
    resourceGroupName: "rg1",
    simGroupName: "testSimGroup",
    simName: "testSim",
    simPolicy: {
        id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/simPolicies/MySimPolicy",
    },
    staticIpConfiguration: [{
        attachedDataNetwork: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/packetCoreControlPlanes/TestPacketCoreCP/packetCoreDataPlanes/TestPacketCoreDP/attachedDataNetworks/TestAttachedDataNetwork",
        },
        slice: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/slices/testSlice",
        },
        staticIp: {
            ipv4Address: "2.4.0.1",
        },
    }],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sim = azure_native.mobilenetwork.Sim("sim",
    authentication_key="00000000000000000000000000000000",
    device_type="Video camera",
    integrated_circuit_card_identifier="8900000000000000000",
    international_mobile_subscriber_identity="00000",
    operator_key_code="00000000000000000000000000000000",
    resource_group_name="rg1",
    sim_group_name="testSimGroup",
    sim_name="testSim",
    sim_policy=azure_native.mobilenetwork.SimPolicyResourceIdArgs(
        id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/simPolicies/MySimPolicy",
    ),
    static_ip_configuration=[{
        "attachedDataNetwork": azure_native.mobilenetwork.AttachedDataNetworkResourceIdArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/packetCoreControlPlanes/TestPacketCoreCP/packetCoreDataPlanes/TestPacketCoreDP/attachedDataNetworks/TestAttachedDataNetwork",
        ),
        "slice": azure_native.mobilenetwork.SliceResourceIdArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/slices/testSlice",
        ),
        "staticIp": azure_native.mobilenetwork.SimStaticIpPropertiesStaticIpArgs(
            ipv4_address="2.4.0.1",
        ),
    }])

```

```yaml
resources:
  sim:
    type: azure-native:mobilenetwork:Sim
    properties:
      authenticationKey: '00000000000000000000000000000000'
      deviceType: Video camera
      integratedCircuitCardIdentifier: '8900000000000000000'
      internationalMobileSubscriberIdentity: '00000'
      operatorKeyCode: '00000000000000000000000000000000'
      resourceGroupName: rg1
      simGroupName: testSimGroup
      simName: testSim
      simPolicy:
        id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/simPolicies/MySimPolicy
      staticIpConfiguration:
        - attachedDataNetwork:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/packetCoreControlPlanes/TestPacketCoreCP/packetCoreDataPlanes/TestPacketCoreDP/attachedDataNetworks/TestAttachedDataNetwork
          slice:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/slices/testSlice
          staticIp:
            ipv4Address: 2.4.0.1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:mobilenetwork:Sim testSim /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/simGroups/testSimGroup/sims/testSim 
```
