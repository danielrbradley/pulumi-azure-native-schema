SIM policy resource.
API Version: 2022-11-01.
Previous API Version: 2022-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create SIM policy
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var simPolicy = new AzureNative.MobileNetwork.SimPolicy("simPolicy", new()
    {
        DefaultSlice = new AzureNative.MobileNetwork.Inputs.SliceResourceIdArgs
        {
            Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/slices/testSlice",
        },
        Location = "eastus",
        MobileNetworkName = "testMobileNetwork",
        RegistrationTimer = 3240,
        ResourceGroupName = "rg1",
        SimPolicyName = "testPolicy",
        SliceConfigurations = new[]
        {
            new AzureNative.MobileNetwork.Inputs.SliceConfigurationArgs
            {
                DataNetworkConfigurations = new[]
                {
                    new AzureNative.MobileNetwork.Inputs.DataNetworkConfigurationArgs
                    {
                        AdditionalAllowedSessionTypes = new[] {},
                        AllocationAndRetentionPriorityLevel = 9,
                        AllowedServices = new[]
                        {
                            new AzureNative.MobileNetwork.Inputs.ServiceResourceIdArgs
                            {
                                Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/services/testService",
                            },
                        },
                        DataNetwork = new AzureNative.MobileNetwork.Inputs.DataNetworkResourceIdArgs
                        {
                            Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/dataNetworks/testdataNetwork",
                        },
                        DefaultSessionType = "IPv4",
                        FiveQi = 9,
                        MaximumNumberOfBufferedPackets = 200,
                        PreemptionCapability = "NotPreempt",
                        PreemptionVulnerability = "Preemptable",
                        SessionAmbr = new AzureNative.MobileNetwork.Inputs.AmbrArgs
                        {
                            Downlink = "1 Gbps",
                            Uplink = "500 Mbps",
                        },
                    },
                },
                DefaultDataNetwork = new AzureNative.MobileNetwork.Inputs.DataNetworkResourceIdArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/dataNetworks/testdataNetwork",
                },
                Slice = new AzureNative.MobileNetwork.Inputs.SliceResourceIdArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/slices/testSlice",
                },
            },
        },
        UeAmbr = new AzureNative.MobileNetwork.Inputs.AmbrArgs
        {
            Downlink = "1 Gbps",
            Uplink = "500 Mbps",
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
		_, err := mobilenetwork.NewSimPolicy(ctx, "simPolicy", &mobilenetwork.SimPolicyArgs{
			DefaultSlice: &mobilenetwork.SliceResourceIdArgs{
				Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/slices/testSlice"),
			},
			Location:          pulumi.String("eastus"),
			MobileNetworkName: pulumi.String("testMobileNetwork"),
			RegistrationTimer: pulumi.Int(3240),
			ResourceGroupName: pulumi.String("rg1"),
			SimPolicyName:     pulumi.String("testPolicy"),
			SliceConfigurations: []mobilenetwork.SliceConfigurationArgs{
				{
					DataNetworkConfigurations: mobilenetwork.DataNetworkConfigurationArray{
						{
							AdditionalAllowedSessionTypes:       pulumi.StringArray{},
							AllocationAndRetentionPriorityLevel: pulumi.Int(9),
							AllowedServices: mobilenetwork.ServiceResourceIdArray{
								{
									Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/services/testService"),
								},
							},
							DataNetwork: {
								Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/dataNetworks/testdataNetwork"),
							},
							DefaultSessionType:             pulumi.String("IPv4"),
							FiveQi:                         pulumi.Int(9),
							MaximumNumberOfBufferedPackets: pulumi.Int(200),
							PreemptionCapability:           pulumi.String("NotPreempt"),
							PreemptionVulnerability:        pulumi.String("Preemptable"),
							SessionAmbr: {
								Downlink: pulumi.String("1 Gbps"),
								Uplink:   pulumi.String("500 Mbps"),
							},
						},
					},
					DefaultDataNetwork: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/dataNetworks/testdataNetwork"),
					},
					Slice: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/slices/testSlice"),
					},
				},
			},
			UeAmbr: &mobilenetwork.AmbrArgs{
				Downlink: pulumi.String("1 Gbps"),
				Uplink:   pulumi.String("500 Mbps"),
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
import com.pulumi.azurenative.mobilenetwork.SimPolicy;
import com.pulumi.azurenative.mobilenetwork.SimPolicyArgs;
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
        var simPolicy = new SimPolicy("simPolicy", SimPolicyArgs.builder()        
            .defaultSlice(Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/slices/testSlice"))
            .location("eastus")
            .mobileNetworkName("testMobileNetwork")
            .registrationTimer(3240)
            .resourceGroupName("rg1")
            .simPolicyName("testPolicy")
            .sliceConfigurations(Map.ofEntries(
                Map.entry("dataNetworkConfigurations", Map.ofEntries(
                    Map.entry("additionalAllowedSessionTypes", ),
                    Map.entry("allocationAndRetentionPriorityLevel", 9),
                    Map.entry("allowedServices", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/services/testService")),
                    Map.entry("dataNetwork", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/dataNetworks/testdataNetwork")),
                    Map.entry("defaultSessionType", "IPv4"),
                    Map.entry("fiveQi", 9),
                    Map.entry("maximumNumberOfBufferedPackets", 200),
                    Map.entry("preemptionCapability", "NotPreempt"),
                    Map.entry("preemptionVulnerability", "Preemptable"),
                    Map.entry("sessionAmbr", Map.ofEntries(
                        Map.entry("downlink", "1 Gbps"),
                        Map.entry("uplink", "500 Mbps")
                    ))
                )),
                Map.entry("defaultDataNetwork", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/dataNetworks/testdataNetwork")),
                Map.entry("slice", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/slices/testSlice"))
            ))
            .ueAmbr(Map.ofEntries(
                Map.entry("downlink", "1 Gbps"),
                Map.entry("uplink", "500 Mbps")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const simPolicy = new azure_native.mobilenetwork.SimPolicy("simPolicy", {
    defaultSlice: {
        id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/slices/testSlice",
    },
    location: "eastus",
    mobileNetworkName: "testMobileNetwork",
    registrationTimer: 3240,
    resourceGroupName: "rg1",
    simPolicyName: "testPolicy",
    sliceConfigurations: [{
        dataNetworkConfigurations: [{
            additionalAllowedSessionTypes: [],
            allocationAndRetentionPriorityLevel: 9,
            allowedServices: [{
                id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/services/testService",
            }],
            dataNetwork: {
                id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/dataNetworks/testdataNetwork",
            },
            defaultSessionType: "IPv4",
            fiveQi: 9,
            maximumNumberOfBufferedPackets: 200,
            preemptionCapability: "NotPreempt",
            preemptionVulnerability: "Preemptable",
            sessionAmbr: {
                downlink: "1 Gbps",
                uplink: "500 Mbps",
            },
        }],
        defaultDataNetwork: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/dataNetworks/testdataNetwork",
        },
        slice: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/slices/testSlice",
        },
    }],
    ueAmbr: {
        downlink: "1 Gbps",
        uplink: "500 Mbps",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sim_policy = azure_native.mobilenetwork.SimPolicy("simPolicy",
    default_slice=azure_native.mobilenetwork.SliceResourceIdArgs(
        id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/slices/testSlice",
    ),
    location="eastus",
    mobile_network_name="testMobileNetwork",
    registration_timer=3240,
    resource_group_name="rg1",
    sim_policy_name="testPolicy",
    slice_configurations=[{
        "dataNetworkConfigurations": [{
            "additionalAllowedSessionTypes": [],
            "allocationAndRetentionPriorityLevel": 9,
            "allowedServices": [azure_native.mobilenetwork.ServiceResourceIdArgs(
                id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/services/testService",
            )],
            "dataNetwork": azure_native.mobilenetwork.DataNetworkResourceIdArgs(
                id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/dataNetworks/testdataNetwork",
            ),
            "defaultSessionType": "IPv4",
            "fiveQi": 9,
            "maximumNumberOfBufferedPackets": 200,
            "preemptionCapability": "NotPreempt",
            "preemptionVulnerability": "Preemptable",
            "sessionAmbr": azure_native.mobilenetwork.AmbrArgs(
                downlink="1 Gbps",
                uplink="500 Mbps",
            ),
        }],
        "defaultDataNetwork": azure_native.mobilenetwork.DataNetworkResourceIdArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/dataNetworks/testdataNetwork",
        ),
        "slice": azure_native.mobilenetwork.SliceResourceIdArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/slices/testSlice",
        ),
    }],
    ue_ambr=azure_native.mobilenetwork.AmbrArgs(
        downlink="1 Gbps",
        uplink="500 Mbps",
    ))

```

```yaml
resources:
  simPolicy:
    type: azure-native:mobilenetwork:SimPolicy
    properties:
      defaultSlice:
        id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/slices/testSlice
      location: eastus
      mobileNetworkName: testMobileNetwork
      registrationTimer: 3240
      resourceGroupName: rg1
      simPolicyName: testPolicy
      sliceConfigurations:
        - dataNetworkConfigurations:
            - additionalAllowedSessionTypes: []
              allocationAndRetentionPriorityLevel: 9
              allowedServices:
                - id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/services/testService
              dataNetwork:
                id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/dataNetworks/testdataNetwork
              defaultSessionType: IPv4
              fiveQi: 9
              maximumNumberOfBufferedPackets: 200
              preemptionCapability: NotPreempt
              preemptionVulnerability: Preemptable
              sessionAmbr:
                downlink: 1 Gbps
                uplink: 500 Mbps
          defaultDataNetwork:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/dataNetworks/testdataNetwork
          slice:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/slices/testSlice
      ueAmbr:
        downlink: 1 Gbps
        uplink: 500 Mbps

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:mobilenetwork:SimPolicy testPolicy /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/simPolicies/testPolicy 
```
