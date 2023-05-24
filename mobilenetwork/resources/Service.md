Service resource. Must be created in the same location as its parent mobile network.
API Version: 2022-11-01.
Previous API Version: 2022-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create service
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var service = new AzureNative.MobileNetwork.Service("service", new()
    {
        Location = "eastus",
        MobileNetworkName = "testMobileNetwork",
        PccRules = new[]
        {
            new AzureNative.MobileNetwork.Inputs.PccRuleConfigurationArgs
            {
                RuleName = "default-rule",
                RulePrecedence = 255,
                RuleQosPolicy = new AzureNative.MobileNetwork.Inputs.PccRuleQosPolicyArgs
                {
                    AllocationAndRetentionPriorityLevel = 9,
                    FiveQi = 9,
                    MaximumBitRate = new AzureNative.MobileNetwork.Inputs.AmbrArgs
                    {
                        Downlink = "1 Gbps",
                        Uplink = "500 Mbps",
                    },
                    PreemptionCapability = "NotPreempt",
                    PreemptionVulnerability = "Preemptable",
                },
                ServiceDataFlowTemplates = new[]
                {
                    new AzureNative.MobileNetwork.Inputs.ServiceDataFlowTemplateArgs
                    {
                        Direction = "Uplink",
                        Ports = new[] {},
                        Protocol = new[]
                        {
                            "ip",
                        },
                        RemoteIpList = new[]
                        {
                            "10.3.4.0/24",
                        },
                        TemplateName = "IP-to-server",
                    },
                },
                TrafficControl = "Enabled",
            },
        },
        ResourceGroupName = "rg1",
        ServiceName = "TestService",
        ServicePrecedence = 255,
        ServiceQosPolicy = new AzureNative.MobileNetwork.Inputs.QosPolicyArgs
        {
            AllocationAndRetentionPriorityLevel = 9,
            FiveQi = 9,
            MaximumBitRate = new AzureNative.MobileNetwork.Inputs.AmbrArgs
            {
                Downlink = "1 Gbps",
                Uplink = "500 Mbps",
            },
            PreemptionCapability = "NotPreempt",
            PreemptionVulnerability = "Preemptable",
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
		_, err := mobilenetwork.NewService(ctx, "service", &mobilenetwork.ServiceArgs{
			Location:          pulumi.String("eastus"),
			MobileNetworkName: pulumi.String("testMobileNetwork"),
			PccRules: []mobilenetwork.PccRuleConfigurationArgs{
				{
					RuleName:       pulumi.String("default-rule"),
					RulePrecedence: pulumi.Int(255),
					RuleQosPolicy: {
						AllocationAndRetentionPriorityLevel: pulumi.Int(9),
						FiveQi:                              pulumi.Int(9),
						MaximumBitRate: {
							Downlink: pulumi.String("1 Gbps"),
							Uplink:   pulumi.String("500 Mbps"),
						},
						PreemptionCapability:    pulumi.String("NotPreempt"),
						PreemptionVulnerability: pulumi.String("Preemptable"),
					},
					ServiceDataFlowTemplates: mobilenetwork.ServiceDataFlowTemplateArray{
						{
							Direction: pulumi.String("Uplink"),
							Ports:     pulumi.StringArray{},
							Protocol: pulumi.StringArray{
								pulumi.String("ip"),
							},
							RemoteIpList: pulumi.StringArray{
								pulumi.String("10.3.4.0/24"),
							},
							TemplateName: pulumi.String("IP-to-server"),
						},
					},
					TrafficControl: pulumi.String("Enabled"),
				},
			},
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("TestService"),
			ServicePrecedence: pulumi.Int(255),
			ServiceQosPolicy: mobilenetwork.QosPolicyResponse{
				AllocationAndRetentionPriorityLevel: pulumi.Int(9),
				FiveQi:                              pulumi.Int(9),
				MaximumBitRate: &mobilenetwork.AmbrArgs{
					Downlink: pulumi.String("1 Gbps"),
					Uplink:   pulumi.String("500 Mbps"),
				},
				PreemptionCapability:    pulumi.String("NotPreempt"),
				PreemptionVulnerability: pulumi.String("Preemptable"),
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
import com.pulumi.azurenative.mobilenetwork.Service;
import com.pulumi.azurenative.mobilenetwork.ServiceArgs;
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
        var service = new Service("service", ServiceArgs.builder()        
            .location("eastus")
            .mobileNetworkName("testMobileNetwork")
            .pccRules(Map.ofEntries(
                Map.entry("ruleName", "default-rule"),
                Map.entry("rulePrecedence", 255),
                Map.entry("ruleQosPolicy", Map.ofEntries(
                    Map.entry("allocationAndRetentionPriorityLevel", 9),
                    Map.entry("fiveQi", 9),
                    Map.entry("maximumBitRate", Map.ofEntries(
                        Map.entry("downlink", "1 Gbps"),
                        Map.entry("uplink", "500 Mbps")
                    )),
                    Map.entry("preemptionCapability", "NotPreempt"),
                    Map.entry("preemptionVulnerability", "Preemptable")
                )),
                Map.entry("serviceDataFlowTemplates", Map.ofEntries(
                    Map.entry("direction", "Uplink"),
                    Map.entry("ports", ),
                    Map.entry("protocol", "ip"),
                    Map.entry("remoteIpList", "10.3.4.0/24"),
                    Map.entry("templateName", "IP-to-server")
                )),
                Map.entry("trafficControl", "Enabled")
            ))
            .resourceGroupName("rg1")
            .serviceName("TestService")
            .servicePrecedence(255)
            .serviceQosPolicy(Map.ofEntries(
                Map.entry("allocationAndRetentionPriorityLevel", 9),
                Map.entry("fiveQi", 9),
                Map.entry("maximumBitRate", Map.ofEntries(
                    Map.entry("downlink", "1 Gbps"),
                    Map.entry("uplink", "500 Mbps")
                )),
                Map.entry("preemptionCapability", "NotPreempt"),
                Map.entry("preemptionVulnerability", "Preemptable")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const service = new azure_native.mobilenetwork.Service("service", {
    location: "eastus",
    mobileNetworkName: "testMobileNetwork",
    pccRules: [{
        ruleName: "default-rule",
        rulePrecedence: 255,
        ruleQosPolicy: {
            allocationAndRetentionPriorityLevel: 9,
            fiveQi: 9,
            maximumBitRate: {
                downlink: "1 Gbps",
                uplink: "500 Mbps",
            },
            preemptionCapability: "NotPreempt",
            preemptionVulnerability: "Preemptable",
        },
        serviceDataFlowTemplates: [{
            direction: "Uplink",
            ports: [],
            protocol: ["ip"],
            remoteIpList: ["10.3.4.0/24"],
            templateName: "IP-to-server",
        }],
        trafficControl: "Enabled",
    }],
    resourceGroupName: "rg1",
    serviceName: "TestService",
    servicePrecedence: 255,
    serviceQosPolicy: {
        allocationAndRetentionPriorityLevel: 9,
        fiveQi: 9,
        maximumBitRate: {
            downlink: "1 Gbps",
            uplink: "500 Mbps",
        },
        preemptionCapability: "NotPreempt",
        preemptionVulnerability: "Preemptable",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service = azure_native.mobilenetwork.Service("service",
    location="eastus",
    mobile_network_name="testMobileNetwork",
    pcc_rules=[{
        "ruleName": "default-rule",
        "rulePrecedence": 255,
        "ruleQosPolicy": {
            "allocationAndRetentionPriorityLevel": 9,
            "fiveQi": 9,
            "maximumBitRate": azure_native.mobilenetwork.AmbrArgs(
                downlink="1 Gbps",
                uplink="500 Mbps",
            ),
            "preemptionCapability": "NotPreempt",
            "preemptionVulnerability": "Preemptable",
        },
        "serviceDataFlowTemplates": [azure_native.mobilenetwork.ServiceDataFlowTemplateArgs(
            direction="Uplink",
            ports=[],
            protocol=["ip"],
            remote_ip_list=["10.3.4.0/24"],
            template_name="IP-to-server",
        )],
        "trafficControl": "Enabled",
    }],
    resource_group_name="rg1",
    service_name="TestService",
    service_precedence=255,
    service_qos_policy=azure_native.mobilenetwork.QosPolicyResponseArgs(
        allocation_and_retention_priority_level=9,
        five_qi=9,
        maximum_bit_rate=azure_native.mobilenetwork.AmbrArgs(
            downlink="1 Gbps",
            uplink="500 Mbps",
        ),
        preemption_capability="NotPreempt",
        preemption_vulnerability="Preemptable",
    ))

```

```yaml
resources:
  service:
    type: azure-native:mobilenetwork:Service
    properties:
      location: eastus
      mobileNetworkName: testMobileNetwork
      pccRules:
        - ruleName: default-rule
          rulePrecedence: 255
          ruleQosPolicy:
            allocationAndRetentionPriorityLevel: 9
            fiveQi: 9
            maximumBitRate:
              downlink: 1 Gbps
              uplink: 500 Mbps
            preemptionCapability: NotPreempt
            preemptionVulnerability: Preemptable
          serviceDataFlowTemplates:
            - direction: Uplink
              ports: []
              protocol:
                - ip
              remoteIpList:
                - 10.3.4.0/24
              templateName: IP-to-server
          trafficControl: Enabled
      resourceGroupName: rg1
      serviceName: TestService
      servicePrecedence: 255
      serviceQosPolicy:
        allocationAndRetentionPriorityLevel: 9
        fiveQi: 9
        maximumBitRate:
          downlink: 1 Gbps
          uplink: 500 Mbps
        preemptionCapability: NotPreempt
        preemptionVulnerability: Preemptable

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:mobilenetwork:Service testPolicy /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/services/TestService 
```
