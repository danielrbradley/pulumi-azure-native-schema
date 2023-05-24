Rule Group resource.
API Version: 2020-04-01.
Previous API Version: 2020-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create FirewallPolicyRuleGroup
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var firewallPolicyRuleGroup = new AzureNative.Network.FirewallPolicyRuleGroup("firewallPolicyRuleGroup", new()
    {
        FirewallPolicyName = "firewallPolicy",
        Priority = 110,
        ResourceGroupName = "rg1",
        RuleGroupName = "ruleGroup1",
        Rules = new[]
        {
            new AzureNative.Network.Inputs.FirewallPolicyFilterRuleArgs
            {
                Action = new AzureNative.Network.Inputs.FirewallPolicyFilterRuleActionArgs
                {
                    Type = "Deny",
                },
                Name = "Example-Filter-Rule",
                RuleConditions = new[]
                {
                    new AzureNative.Network.Inputs.NetworkRuleConditionArgs
                    {
                        DestinationAddresses = new[]
                        {
                            "*",
                        },
                        DestinationPorts = new[]
                        {
                            "*",
                        },
                        IpProtocols = new[]
                        {
                            "TCP",
                        },
                        Name = "network-condition1",
                        RuleConditionType = "NetworkRuleCondition",
                        SourceAddresses = new[]
                        {
                            "10.1.25.0/24",
                        },
                    },
                },
                RuleType = "FirewallPolicyFilterRule",
            },
        },
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
		_, err := network.NewFirewallPolicyRuleGroup(ctx, "firewallPolicyRuleGroup", &network.FirewallPolicyRuleGroupArgs{
			FirewallPolicyName: pulumi.String("firewallPolicy"),
			Priority:           pulumi.Int(110),
			ResourceGroupName:  pulumi.String("rg1"),
			RuleGroupName:      pulumi.String("ruleGroup1"),
			Rules: pulumi.AnyArray{
				network.FirewallPolicyFilterRule{
					Action: network.FirewallPolicyFilterRuleAction{
						Type: "Deny",
					},
					Name: "Example-Filter-Rule",
					RuleConditions: []interface{}{
						network.NetworkRuleCondition{
							DestinationAddresses: []string{
								"*",
							},
							DestinationPorts: []string{
								"*",
							},
							IpProtocols: []network.FirewallPolicyRuleConditionNetworkProtocol{
								"TCP",
							},
							Name:              "network-condition1",
							RuleConditionType: "NetworkRuleCondition",
							SourceAddresses: []string{
								"10.1.25.0/24",
							},
						},
					},
					RuleType: "FirewallPolicyFilterRule",
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
import com.pulumi.azurenative.network.FirewallPolicyRuleGroup;
import com.pulumi.azurenative.network.FirewallPolicyRuleGroupArgs;
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
        var firewallPolicyRuleGroup = new FirewallPolicyRuleGroup("firewallPolicyRuleGroup", FirewallPolicyRuleGroupArgs.builder()        
            .firewallPolicyName("firewallPolicy")
            .priority(110)
            .resourceGroupName("rg1")
            .ruleGroupName("ruleGroup1")
            .rules(Map.ofEntries(
                Map.entry("action", Map.of("type", "Deny")),
                Map.entry("name", "Example-Filter-Rule"),
                Map.entry("ruleConditions", Map.ofEntries(
                    Map.entry("destinationAddresses", "*"),
                    Map.entry("destinationPorts", "*"),
                    Map.entry("ipProtocols", "TCP"),
                    Map.entry("name", "network-condition1"),
                    Map.entry("ruleConditionType", "NetworkRuleCondition"),
                    Map.entry("sourceAddresses", "10.1.25.0/24")
                )),
                Map.entry("ruleType", "FirewallPolicyFilterRule")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const firewallPolicyRuleGroup = new azure_native.network.FirewallPolicyRuleGroup("firewallPolicyRuleGroup", {
    firewallPolicyName: "firewallPolicy",
    priority: 110,
    resourceGroupName: "rg1",
    ruleGroupName: "ruleGroup1",
    rules: [{
        action: {
            type: "Deny",
        },
        name: "Example-Filter-Rule",
        ruleConditions: [{
            destinationAddresses: ["*"],
            destinationPorts: ["*"],
            ipProtocols: ["TCP"],
            name: "network-condition1",
            ruleConditionType: "NetworkRuleCondition",
            sourceAddresses: ["10.1.25.0/24"],
        }],
        ruleType: "FirewallPolicyFilterRule",
    }],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

firewall_policy_rule_group = azure_native.network.FirewallPolicyRuleGroup("firewallPolicyRuleGroup",
    firewall_policy_name="firewallPolicy",
    priority=110,
    resource_group_name="rg1",
    rule_group_name="ruleGroup1",
    rules=[azure_native.network.FirewallPolicyFilterRuleArgs(
        action=azure_native.network.FirewallPolicyFilterRuleActionArgs(
            type="Deny",
        ),
        name="Example-Filter-Rule",
        rule_conditions=[azure_native.network.NetworkRuleConditionArgs(
            destination_addresses=["*"],
            destination_ports=["*"],
            ip_protocols=["TCP"],
            name="network-condition1",
            rule_condition_type="NetworkRuleCondition",
            source_addresses=["10.1.25.0/24"],
        )],
        rule_type="FirewallPolicyFilterRule",
    )])

```

```yaml
resources:
  firewallPolicyRuleGroup:
    type: azure-native:network:FirewallPolicyRuleGroup
    properties:
      firewallPolicyName: firewallPolicy
      priority: 110
      resourceGroupName: rg1
      ruleGroupName: ruleGroup1
      rules:
        - action:
            type: Deny
          name: Example-Filter-Rule
          ruleConditions:
            - destinationAddresses:
                - '*'
              destinationPorts:
                - '*'
              ipProtocols:
                - TCP
              name: network-condition1
              ruleConditionType: NetworkRuleCondition
              sourceAddresses:
                - 10.1.25.0/24
          ruleType: FirewallPolicyFilterRule

```

{{% /example %}}
{{% example %}}
### Create FirewallPolicyRuleGroup With IpGroups
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var firewallPolicyRuleGroup = new AzureNative.Network.FirewallPolicyRuleGroup("firewallPolicyRuleGroup", new()
    {
        FirewallPolicyName = "firewallPolicy",
        Priority = 110,
        ResourceGroupName = "rg1",
        RuleGroupName = "ruleGroup1",
        Rules = new[]
        {
            new AzureNative.Network.Inputs.FirewallPolicyFilterRuleArgs
            {
                Action = new AzureNative.Network.Inputs.FirewallPolicyFilterRuleActionArgs
                {
                    Type = "Deny",
                },
                Name = "Example-Filter-Rule",
                RuleConditions = new[]
                {
                    new AzureNative.Network.Inputs.NetworkRuleConditionArgs
                    {
                        DestinationIpGroups = new[]
                        {
                            "/subscriptions/subid/providers/Microsoft.Network/resourceGroup/rg1/ipGroups/ipGroups2",
                        },
                        DestinationPorts = new[]
                        {
                            "*",
                        },
                        IpProtocols = new[]
                        {
                            "TCP",
                        },
                        Name = "network-condition1",
                        RuleConditionType = "NetworkRuleCondition",
                        SourceIpGroups = new[]
                        {
                            "/subscriptions/subid/providers/Microsoft.Network/resourceGroup/rg1/ipGroups/ipGroups1",
                        },
                    },
                },
                RuleType = "FirewallPolicyFilterRule",
            },
        },
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
		_, err := network.NewFirewallPolicyRuleGroup(ctx, "firewallPolicyRuleGroup", &network.FirewallPolicyRuleGroupArgs{
			FirewallPolicyName: pulumi.String("firewallPolicy"),
			Priority:           pulumi.Int(110),
			ResourceGroupName:  pulumi.String("rg1"),
			RuleGroupName:      pulumi.String("ruleGroup1"),
			Rules: pulumi.AnyArray{
				network.FirewallPolicyFilterRule{
					Action: network.FirewallPolicyFilterRuleAction{
						Type: "Deny",
					},
					Name: "Example-Filter-Rule",
					RuleConditions: []interface{}{
						network.NetworkRuleCondition{
							DestinationIpGroups: []string{
								"/subscriptions/subid/providers/Microsoft.Network/resourceGroup/rg1/ipGroups/ipGroups2",
							},
							DestinationPorts: []string{
								"*",
							},
							IpProtocols: []network.FirewallPolicyRuleConditionNetworkProtocol{
								"TCP",
							},
							Name:              "network-condition1",
							RuleConditionType: "NetworkRuleCondition",
							SourceIpGroups: []string{
								"/subscriptions/subid/providers/Microsoft.Network/resourceGroup/rg1/ipGroups/ipGroups1",
							},
						},
					},
					RuleType: "FirewallPolicyFilterRule",
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
import com.pulumi.azurenative.network.FirewallPolicyRuleGroup;
import com.pulumi.azurenative.network.FirewallPolicyRuleGroupArgs;
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
        var firewallPolicyRuleGroup = new FirewallPolicyRuleGroup("firewallPolicyRuleGroup", FirewallPolicyRuleGroupArgs.builder()        
            .firewallPolicyName("firewallPolicy")
            .priority(110)
            .resourceGroupName("rg1")
            .ruleGroupName("ruleGroup1")
            .rules(Map.ofEntries(
                Map.entry("action", Map.of("type", "Deny")),
                Map.entry("name", "Example-Filter-Rule"),
                Map.entry("ruleConditions", Map.ofEntries(
                    Map.entry("destinationIpGroups", "/subscriptions/subid/providers/Microsoft.Network/resourceGroup/rg1/ipGroups/ipGroups2"),
                    Map.entry("destinationPorts", "*"),
                    Map.entry("ipProtocols", "TCP"),
                    Map.entry("name", "network-condition1"),
                    Map.entry("ruleConditionType", "NetworkRuleCondition"),
                    Map.entry("sourceIpGroups", "/subscriptions/subid/providers/Microsoft.Network/resourceGroup/rg1/ipGroups/ipGroups1")
                )),
                Map.entry("ruleType", "FirewallPolicyFilterRule")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const firewallPolicyRuleGroup = new azure_native.network.FirewallPolicyRuleGroup("firewallPolicyRuleGroup", {
    firewallPolicyName: "firewallPolicy",
    priority: 110,
    resourceGroupName: "rg1",
    ruleGroupName: "ruleGroup1",
    rules: [{
        action: {
            type: "Deny",
        },
        name: "Example-Filter-Rule",
        ruleConditions: [{
            destinationIpGroups: ["/subscriptions/subid/providers/Microsoft.Network/resourceGroup/rg1/ipGroups/ipGroups2"],
            destinationPorts: ["*"],
            ipProtocols: ["TCP"],
            name: "network-condition1",
            ruleConditionType: "NetworkRuleCondition",
            sourceIpGroups: ["/subscriptions/subid/providers/Microsoft.Network/resourceGroup/rg1/ipGroups/ipGroups1"],
        }],
        ruleType: "FirewallPolicyFilterRule",
    }],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

firewall_policy_rule_group = azure_native.network.FirewallPolicyRuleGroup("firewallPolicyRuleGroup",
    firewall_policy_name="firewallPolicy",
    priority=110,
    resource_group_name="rg1",
    rule_group_name="ruleGroup1",
    rules=[azure_native.network.FirewallPolicyFilterRuleArgs(
        action=azure_native.network.FirewallPolicyFilterRuleActionArgs(
            type="Deny",
        ),
        name="Example-Filter-Rule",
        rule_conditions=[azure_native.network.NetworkRuleConditionArgs(
            destination_ip_groups=["/subscriptions/subid/providers/Microsoft.Network/resourceGroup/rg1/ipGroups/ipGroups2"],
            destination_ports=["*"],
            ip_protocols=["TCP"],
            name="network-condition1",
            rule_condition_type="NetworkRuleCondition",
            source_ip_groups=["/subscriptions/subid/providers/Microsoft.Network/resourceGroup/rg1/ipGroups/ipGroups1"],
        )],
        rule_type="FirewallPolicyFilterRule",
    )])

```

```yaml
resources:
  firewallPolicyRuleGroup:
    type: azure-native:network:FirewallPolicyRuleGroup
    properties:
      firewallPolicyName: firewallPolicy
      priority: 110
      resourceGroupName: rg1
      ruleGroupName: ruleGroup1
      rules:
        - action:
            type: Deny
          name: Example-Filter-Rule
          ruleConditions:
            - destinationIpGroups:
                - /subscriptions/subid/providers/Microsoft.Network/resourceGroup/rg1/ipGroups/ipGroups2
              destinationPorts:
                - '*'
              ipProtocols:
                - TCP
              name: network-condition1
              ruleConditionType: NetworkRuleCondition
              sourceIpGroups:
                - /subscriptions/subid/providers/Microsoft.Network/resourceGroup/rg1/ipGroups/ipGroups1
          ruleType: FirewallPolicyFilterRule

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:FirewallPolicyRuleGroup ruleGroup1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/firewallPolicies/firewallPolicy/ruleGroups/ruleGroup1 
```
