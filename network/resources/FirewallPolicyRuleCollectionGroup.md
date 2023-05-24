Rule Collection Group resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create FirewallPolicyNatRuleCollectionGroup
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var firewallPolicyRuleCollectionGroup = new AzureNative.Network.FirewallPolicyRuleCollectionGroup("firewallPolicyRuleCollectionGroup", new()
    {
        FirewallPolicyName = "firewallPolicy",
        Priority = 100,
        ResourceGroupName = "rg1",
        RuleCollectionGroupName = "ruleCollectionGroup1",
        RuleCollections = new[]
        {
            new AzureNative.Network.Inputs.FirewallPolicyNatRuleCollectionArgs
            {
                Action = new AzureNative.Network.Inputs.FirewallPolicyNatRuleCollectionActionArgs
                {
                    Type = "DNAT",
                },
                Name = "Example-Nat-Rule-Collection",
                Priority = 100,
                RuleCollectionType = "FirewallPolicyNatRuleCollection",
                Rules = new[]
                {
                    new AzureNative.Network.Inputs.NatRuleArgs
                    {
                        DestinationAddresses = new[]
                        {
                            "152.23.32.23",
                        },
                        DestinationPorts = new[]
                        {
                            "8080",
                        },
                        IpProtocols = new[]
                        {
                            "TCP",
                            "UDP",
                        },
                        Name = "nat-rule1",
                        RuleType = "NatRule",
                        SourceAddresses = new[]
                        {
                            "2.2.2.2",
                        },
                        SourceIpGroups = new[] {},
                        TranslatedFqdn = "internalhttp.server.net",
                        TranslatedPort = "8080",
                    },
                },
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
		_, err := network.NewFirewallPolicyRuleCollectionGroup(ctx, "firewallPolicyRuleCollectionGroup", &network.FirewallPolicyRuleCollectionGroupArgs{
			FirewallPolicyName:      pulumi.String("firewallPolicy"),
			Priority:                pulumi.Int(100),
			ResourceGroupName:       pulumi.String("rg1"),
			RuleCollectionGroupName: pulumi.String("ruleCollectionGroup1"),
			RuleCollections: pulumi.AnyArray{
				network.FirewallPolicyNatRuleCollection{
					Action: network.FirewallPolicyNatRuleCollectionAction{
						Type: "DNAT",
					},
					Name:               "Example-Nat-Rule-Collection",
					Priority:           100,
					RuleCollectionType: "FirewallPolicyNatRuleCollection",
					Rules: []interface{}{
						network.NatRuleType{
							DestinationAddresses: []string{
								"152.23.32.23",
							},
							DestinationPorts: []string{
								"8080",
							},
							IpProtocols: []network.FirewallPolicyRuleNetworkProtocol{
								"TCP",
								"UDP",
							},
							Name:     "nat-rule1",
							RuleType: "NatRule",
							SourceAddresses: []string{
								"2.2.2.2",
							},
							SourceIpGroups: []interface{}{},
							TranslatedFqdn: "internalhttp.server.net",
							TranslatedPort: "8080",
						},
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
import com.pulumi.azurenative.network.FirewallPolicyRuleCollectionGroup;
import com.pulumi.azurenative.network.FirewallPolicyRuleCollectionGroupArgs;
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
        var firewallPolicyRuleCollectionGroup = new FirewallPolicyRuleCollectionGroup("firewallPolicyRuleCollectionGroup", FirewallPolicyRuleCollectionGroupArgs.builder()        
            .firewallPolicyName("firewallPolicy")
            .priority(100)
            .resourceGroupName("rg1")
            .ruleCollectionGroupName("ruleCollectionGroup1")
            .ruleCollections(Map.ofEntries(
                Map.entry("action", Map.of("type", "DNAT")),
                Map.entry("name", "Example-Nat-Rule-Collection"),
                Map.entry("priority", 100),
                Map.entry("ruleCollectionType", "FirewallPolicyNatRuleCollection"),
                Map.entry("rules", Map.ofEntries(
                    Map.entry("destinationAddresses", "152.23.32.23"),
                    Map.entry("destinationPorts", "8080"),
                    Map.entry("ipProtocols",                     
                        "TCP",
                        "UDP"),
                    Map.entry("name", "nat-rule1"),
                    Map.entry("ruleType", "NatRule"),
                    Map.entry("sourceAddresses", "2.2.2.2"),
                    Map.entry("sourceIpGroups", ),
                    Map.entry("translatedFqdn", "internalhttp.server.net"),
                    Map.entry("translatedPort", "8080")
                ))
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const firewallPolicyRuleCollectionGroup = new azure_native.network.FirewallPolicyRuleCollectionGroup("firewallPolicyRuleCollectionGroup", {
    firewallPolicyName: "firewallPolicy",
    priority: 100,
    resourceGroupName: "rg1",
    ruleCollectionGroupName: "ruleCollectionGroup1",
    ruleCollections: [{
        action: {
            type: "DNAT",
        },
        name: "Example-Nat-Rule-Collection",
        priority: 100,
        ruleCollectionType: "FirewallPolicyNatRuleCollection",
        rules: [{
            destinationAddresses: ["152.23.32.23"],
            destinationPorts: ["8080"],
            ipProtocols: [
                "TCP",
                "UDP",
            ],
            name: "nat-rule1",
            ruleType: "NatRule",
            sourceAddresses: ["2.2.2.2"],
            sourceIpGroups: [],
            translatedFqdn: "internalhttp.server.net",
            translatedPort: "8080",
        }],
    }],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

firewall_policy_rule_collection_group = azure_native.network.FirewallPolicyRuleCollectionGroup("firewallPolicyRuleCollectionGroup",
    firewall_policy_name="firewallPolicy",
    priority=100,
    resource_group_name="rg1",
    rule_collection_group_name="ruleCollectionGroup1",
    rule_collections=[azure_native.network.FirewallPolicyNatRuleCollectionArgs(
        action=azure_native.network.FirewallPolicyNatRuleCollectionActionArgs(
            type="DNAT",
        ),
        name="Example-Nat-Rule-Collection",
        priority=100,
        rule_collection_type="FirewallPolicyNatRuleCollection",
        rules=[azure_native.network.NatRuleArgs(
            destination_addresses=["152.23.32.23"],
            destination_ports=["8080"],
            ip_protocols=[
                "TCP",
                "UDP",
            ],
            name="nat-rule1",
            rule_type="NatRule",
            source_addresses=["2.2.2.2"],
            source_ip_groups=[],
            translated_fqdn="internalhttp.server.net",
            translated_port="8080",
        )],
    )])

```

```yaml
resources:
  firewallPolicyRuleCollectionGroup:
    type: azure-native:network:FirewallPolicyRuleCollectionGroup
    properties:
      firewallPolicyName: firewallPolicy
      priority: 100
      resourceGroupName: rg1
      ruleCollectionGroupName: ruleCollectionGroup1
      ruleCollections:
        - action:
            type: DNAT
          name: Example-Nat-Rule-Collection
          priority: 100
          ruleCollectionType: FirewallPolicyNatRuleCollection
          rules:
            - destinationAddresses:
                - 152.23.32.23
              destinationPorts:
                - '8080'
              ipProtocols:
                - TCP
                - UDP
              name: nat-rule1
              ruleType: NatRule
              sourceAddresses:
                - 2.2.2.2
              sourceIpGroups: []
              translatedFqdn: internalhttp.server.net
              translatedPort: '8080'

```

{{% /example %}}
{{% example %}}
### Create FirewallPolicyRuleCollectionGroup
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var firewallPolicyRuleCollectionGroup = new AzureNative.Network.FirewallPolicyRuleCollectionGroup("firewallPolicyRuleCollectionGroup", new()
    {
        FirewallPolicyName = "firewallPolicy",
        Priority = 100,
        ResourceGroupName = "rg1",
        RuleCollectionGroupName = "ruleCollectionGroup1",
        RuleCollections = new[]
        {
            new AzureNative.Network.Inputs.FirewallPolicyFilterRuleCollectionArgs
            {
                Action = new AzureNative.Network.Inputs.FirewallPolicyFilterRuleCollectionActionArgs
                {
                    Type = "Deny",
                },
                Name = "Example-Filter-Rule-Collection",
                Priority = 100,
                RuleCollectionType = "FirewallPolicyFilterRuleCollection",
                Rules = new[]
                {
                    new AzureNative.Network.Inputs.NetworkRuleArgs
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
                        Name = "network-rule1",
                        RuleType = "NetworkRule",
                        SourceAddresses = new[]
                        {
                            "10.1.25.0/24",
                        },
                    },
                },
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
		_, err := network.NewFirewallPolicyRuleCollectionGroup(ctx, "firewallPolicyRuleCollectionGroup", &network.FirewallPolicyRuleCollectionGroupArgs{
			FirewallPolicyName:      pulumi.String("firewallPolicy"),
			Priority:                pulumi.Int(100),
			ResourceGroupName:       pulumi.String("rg1"),
			RuleCollectionGroupName: pulumi.String("ruleCollectionGroup1"),
			RuleCollections: pulumi.AnyArray{
				network.FirewallPolicyFilterRuleCollection{
					Action: network.FirewallPolicyFilterRuleCollectionAction{
						Type: "Deny",
					},
					Name:               "Example-Filter-Rule-Collection",
					Priority:           100,
					RuleCollectionType: "FirewallPolicyFilterRuleCollection",
					Rules: []interface{}{
						network.NetworkRule{
							DestinationAddresses: []string{
								"*",
							},
							DestinationPorts: []string{
								"*",
							},
							IpProtocols: []network.FirewallPolicyRuleNetworkProtocol{
								"TCP",
							},
							Name:     "network-rule1",
							RuleType: "NetworkRule",
							SourceAddresses: []string{
								"10.1.25.0/24",
							},
						},
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
import com.pulumi.azurenative.network.FirewallPolicyRuleCollectionGroup;
import com.pulumi.azurenative.network.FirewallPolicyRuleCollectionGroupArgs;
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
        var firewallPolicyRuleCollectionGroup = new FirewallPolicyRuleCollectionGroup("firewallPolicyRuleCollectionGroup", FirewallPolicyRuleCollectionGroupArgs.builder()        
            .firewallPolicyName("firewallPolicy")
            .priority(100)
            .resourceGroupName("rg1")
            .ruleCollectionGroupName("ruleCollectionGroup1")
            .ruleCollections(Map.ofEntries(
                Map.entry("action", Map.of("type", "Deny")),
                Map.entry("name", "Example-Filter-Rule-Collection"),
                Map.entry("priority", 100),
                Map.entry("ruleCollectionType", "FirewallPolicyFilterRuleCollection"),
                Map.entry("rules", Map.ofEntries(
                    Map.entry("destinationAddresses", "*"),
                    Map.entry("destinationPorts", "*"),
                    Map.entry("ipProtocols", "TCP"),
                    Map.entry("name", "network-rule1"),
                    Map.entry("ruleType", "NetworkRule"),
                    Map.entry("sourceAddresses", "10.1.25.0/24")
                ))
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const firewallPolicyRuleCollectionGroup = new azure_native.network.FirewallPolicyRuleCollectionGroup("firewallPolicyRuleCollectionGroup", {
    firewallPolicyName: "firewallPolicy",
    priority: 100,
    resourceGroupName: "rg1",
    ruleCollectionGroupName: "ruleCollectionGroup1",
    ruleCollections: [{
        action: {
            type: "Deny",
        },
        name: "Example-Filter-Rule-Collection",
        priority: 100,
        ruleCollectionType: "FirewallPolicyFilterRuleCollection",
        rules: [{
            destinationAddresses: ["*"],
            destinationPorts: ["*"],
            ipProtocols: ["TCP"],
            name: "network-rule1",
            ruleType: "NetworkRule",
            sourceAddresses: ["10.1.25.0/24"],
        }],
    }],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

firewall_policy_rule_collection_group = azure_native.network.FirewallPolicyRuleCollectionGroup("firewallPolicyRuleCollectionGroup",
    firewall_policy_name="firewallPolicy",
    priority=100,
    resource_group_name="rg1",
    rule_collection_group_name="ruleCollectionGroup1",
    rule_collections=[azure_native.network.FirewallPolicyFilterRuleCollectionArgs(
        action=azure_native.network.FirewallPolicyFilterRuleCollectionActionArgs(
            type="Deny",
        ),
        name="Example-Filter-Rule-Collection",
        priority=100,
        rule_collection_type="FirewallPolicyFilterRuleCollection",
        rules=[azure_native.network.NetworkRuleArgs(
            destination_addresses=["*"],
            destination_ports=["*"],
            ip_protocols=["TCP"],
            name="network-rule1",
            rule_type="NetworkRule",
            source_addresses=["10.1.25.0/24"],
        )],
    )])

```

```yaml
resources:
  firewallPolicyRuleCollectionGroup:
    type: azure-native:network:FirewallPolicyRuleCollectionGroup
    properties:
      firewallPolicyName: firewallPolicy
      priority: 100
      resourceGroupName: rg1
      ruleCollectionGroupName: ruleCollectionGroup1
      ruleCollections:
        - action:
            type: Deny
          name: Example-Filter-Rule-Collection
          priority: 100
          ruleCollectionType: FirewallPolicyFilterRuleCollection
          rules:
            - destinationAddresses:
                - '*'
              destinationPorts:
                - '*'
              ipProtocols:
                - TCP
              name: network-rule1
              ruleType: NetworkRule
              sourceAddresses:
                - 10.1.25.0/24

```

{{% /example %}}
{{% example %}}
### Create FirewallPolicyRuleCollectionGroup With IpGroups
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var firewallPolicyRuleCollectionGroup = new AzureNative.Network.FirewallPolicyRuleCollectionGroup("firewallPolicyRuleCollectionGroup", new()
    {
        FirewallPolicyName = "firewallPolicy",
        Priority = 110,
        ResourceGroupName = "rg1",
        RuleCollectionGroupName = "ruleCollectionGroup1",
        RuleCollections = new[]
        {
            new AzureNative.Network.Inputs.FirewallPolicyFilterRuleCollectionArgs
            {
                Action = new AzureNative.Network.Inputs.FirewallPolicyFilterRuleCollectionActionArgs
                {
                    Type = "Deny",
                },
                Name = "Example-Filter-Rule-Collection",
                RuleCollectionType = "FirewallPolicyFilterRuleCollection",
                Rules = new[]
                {
                    new AzureNative.Network.Inputs.NetworkRuleArgs
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
                        Name = "network-1",
                        RuleType = "NetworkRule",
                        SourceIpGroups = new[]
                        {
                            "/subscriptions/subid/providers/Microsoft.Network/resourceGroup/rg1/ipGroups/ipGroups1",
                        },
                    },
                },
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
		_, err := network.NewFirewallPolicyRuleCollectionGroup(ctx, "firewallPolicyRuleCollectionGroup", &network.FirewallPolicyRuleCollectionGroupArgs{
			FirewallPolicyName:      pulumi.String("firewallPolicy"),
			Priority:                pulumi.Int(110),
			ResourceGroupName:       pulumi.String("rg1"),
			RuleCollectionGroupName: pulumi.String("ruleCollectionGroup1"),
			RuleCollections: pulumi.AnyArray{
				network.FirewallPolicyFilterRuleCollection{
					Action: network.FirewallPolicyFilterRuleCollectionAction{
						Type: "Deny",
					},
					Name:               "Example-Filter-Rule-Collection",
					RuleCollectionType: "FirewallPolicyFilterRuleCollection",
					Rules: []interface{}{
						network.NetworkRule{
							DestinationIpGroups: []string{
								"/subscriptions/subid/providers/Microsoft.Network/resourceGroup/rg1/ipGroups/ipGroups2",
							},
							DestinationPorts: []string{
								"*",
							},
							IpProtocols: []network.FirewallPolicyRuleNetworkProtocol{
								"TCP",
							},
							Name:     "network-1",
							RuleType: "NetworkRule",
							SourceIpGroups: []string{
								"/subscriptions/subid/providers/Microsoft.Network/resourceGroup/rg1/ipGroups/ipGroups1",
							},
						},
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
import com.pulumi.azurenative.network.FirewallPolicyRuleCollectionGroup;
import com.pulumi.azurenative.network.FirewallPolicyRuleCollectionGroupArgs;
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
        var firewallPolicyRuleCollectionGroup = new FirewallPolicyRuleCollectionGroup("firewallPolicyRuleCollectionGroup", FirewallPolicyRuleCollectionGroupArgs.builder()        
            .firewallPolicyName("firewallPolicy")
            .priority(110)
            .resourceGroupName("rg1")
            .ruleCollectionGroupName("ruleCollectionGroup1")
            .ruleCollections(Map.ofEntries(
                Map.entry("action", Map.of("type", "Deny")),
                Map.entry("name", "Example-Filter-Rule-Collection"),
                Map.entry("ruleCollectionType", "FirewallPolicyFilterRuleCollection"),
                Map.entry("rules", Map.ofEntries(
                    Map.entry("destinationIpGroups", "/subscriptions/subid/providers/Microsoft.Network/resourceGroup/rg1/ipGroups/ipGroups2"),
                    Map.entry("destinationPorts", "*"),
                    Map.entry("ipProtocols", "TCP"),
                    Map.entry("name", "network-1"),
                    Map.entry("ruleType", "NetworkRule"),
                    Map.entry("sourceIpGroups", "/subscriptions/subid/providers/Microsoft.Network/resourceGroup/rg1/ipGroups/ipGroups1")
                ))
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const firewallPolicyRuleCollectionGroup = new azure_native.network.FirewallPolicyRuleCollectionGroup("firewallPolicyRuleCollectionGroup", {
    firewallPolicyName: "firewallPolicy",
    priority: 110,
    resourceGroupName: "rg1",
    ruleCollectionGroupName: "ruleCollectionGroup1",
    ruleCollections: [{
        action: {
            type: "Deny",
        },
        name: "Example-Filter-Rule-Collection",
        ruleCollectionType: "FirewallPolicyFilterRuleCollection",
        rules: [{
            destinationIpGroups: ["/subscriptions/subid/providers/Microsoft.Network/resourceGroup/rg1/ipGroups/ipGroups2"],
            destinationPorts: ["*"],
            ipProtocols: ["TCP"],
            name: "network-1",
            ruleType: "NetworkRule",
            sourceIpGroups: ["/subscriptions/subid/providers/Microsoft.Network/resourceGroup/rg1/ipGroups/ipGroups1"],
        }],
    }],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

firewall_policy_rule_collection_group = azure_native.network.FirewallPolicyRuleCollectionGroup("firewallPolicyRuleCollectionGroup",
    firewall_policy_name="firewallPolicy",
    priority=110,
    resource_group_name="rg1",
    rule_collection_group_name="ruleCollectionGroup1",
    rule_collections=[azure_native.network.FirewallPolicyFilterRuleCollectionArgs(
        action=azure_native.network.FirewallPolicyFilterRuleCollectionActionArgs(
            type="Deny",
        ),
        name="Example-Filter-Rule-Collection",
        rule_collection_type="FirewallPolicyFilterRuleCollection",
        rules=[azure_native.network.NetworkRuleArgs(
            destination_ip_groups=["/subscriptions/subid/providers/Microsoft.Network/resourceGroup/rg1/ipGroups/ipGroups2"],
            destination_ports=["*"],
            ip_protocols=["TCP"],
            name="network-1",
            rule_type="NetworkRule",
            source_ip_groups=["/subscriptions/subid/providers/Microsoft.Network/resourceGroup/rg1/ipGroups/ipGroups1"],
        )],
    )])

```

```yaml
resources:
  firewallPolicyRuleCollectionGroup:
    type: azure-native:network:FirewallPolicyRuleCollectionGroup
    properties:
      firewallPolicyName: firewallPolicy
      priority: 110
      resourceGroupName: rg1
      ruleCollectionGroupName: ruleCollectionGroup1
      ruleCollections:
        - action:
            type: Deny
          name: Example-Filter-Rule-Collection
          ruleCollectionType: FirewallPolicyFilterRuleCollection
          rules:
            - destinationIpGroups:
                - /subscriptions/subid/providers/Microsoft.Network/resourceGroup/rg1/ipGroups/ipGroups2
              destinationPorts:
                - '*'
              ipProtocols:
                - TCP
              name: network-1
              ruleType: NetworkRule
              sourceIpGroups:
                - /subscriptions/subid/providers/Microsoft.Network/resourceGroup/rg1/ipGroups/ipGroups1

```

{{% /example %}}
{{% example %}}
### Create FirewallPolicyRuleCollectionGroup With Web Categories
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var firewallPolicyRuleCollectionGroup = new AzureNative.Network.FirewallPolicyRuleCollectionGroup("firewallPolicyRuleCollectionGroup", new()
    {
        FirewallPolicyName = "firewallPolicy",
        Priority = 110,
        ResourceGroupName = "rg1",
        RuleCollectionGroupName = "ruleCollectionGroup1",
        RuleCollections = new[]
        {
            new AzureNative.Network.Inputs.FirewallPolicyFilterRuleCollectionArgs
            {
                Action = new AzureNative.Network.Inputs.FirewallPolicyFilterRuleCollectionActionArgs
                {
                    Type = "Deny",
                },
                Name = "Example-Filter-Rule-Collection",
                RuleCollectionType = "FirewallPolicyFilterRuleCollection",
                Rules = new[]
                {
                    new AzureNative.Network.Inputs.ApplicationRuleArgs
                    {
                        Description = "Deny inbound rule",
                        Name = "rule1",
                        Protocols = new[]
                        {
                            new AzureNative.Network.Inputs.FirewallPolicyRuleApplicationProtocolArgs
                            {
                                Port = 443,
                                ProtocolType = "Https",
                            },
                        },
                        RuleType = "ApplicationRule",
                        SourceAddresses = new[]
                        {
                            "216.58.216.164",
                            "10.0.0.0/24",
                        },
                        WebCategories = new[]
                        {
                            "Hacking",
                        },
                    },
                },
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
		_, err := network.NewFirewallPolicyRuleCollectionGroup(ctx, "firewallPolicyRuleCollectionGroup", &network.FirewallPolicyRuleCollectionGroupArgs{
			FirewallPolicyName:      pulumi.String("firewallPolicy"),
			Priority:                pulumi.Int(110),
			ResourceGroupName:       pulumi.String("rg1"),
			RuleCollectionGroupName: pulumi.String("ruleCollectionGroup1"),
			RuleCollections: pulumi.AnyArray{
				network.FirewallPolicyFilterRuleCollection{
					Action: network.FirewallPolicyFilterRuleCollectionAction{
						Type: "Deny",
					},
					Name:               "Example-Filter-Rule-Collection",
					RuleCollectionType: "FirewallPolicyFilterRuleCollection",
					Rules: []interface{}{
						network.ApplicationRule{
							Description: "Deny inbound rule",
							Name:        "rule1",
							Protocols: []network.FirewallPolicyRuleApplicationProtocol{
								{
									Port:         443,
									ProtocolType: "Https",
								},
							},
							RuleType: "ApplicationRule",
							SourceAddresses: []string{
								"216.58.216.164",
								"10.0.0.0/24",
							},
							WebCategories: []string{
								"Hacking",
							},
						},
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
import com.pulumi.azurenative.network.FirewallPolicyRuleCollectionGroup;
import com.pulumi.azurenative.network.FirewallPolicyRuleCollectionGroupArgs;
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
        var firewallPolicyRuleCollectionGroup = new FirewallPolicyRuleCollectionGroup("firewallPolicyRuleCollectionGroup", FirewallPolicyRuleCollectionGroupArgs.builder()        
            .firewallPolicyName("firewallPolicy")
            .priority(110)
            .resourceGroupName("rg1")
            .ruleCollectionGroupName("ruleCollectionGroup1")
            .ruleCollections(Map.ofEntries(
                Map.entry("action", Map.of("type", "Deny")),
                Map.entry("name", "Example-Filter-Rule-Collection"),
                Map.entry("ruleCollectionType", "FirewallPolicyFilterRuleCollection"),
                Map.entry("rules", Map.ofEntries(
                    Map.entry("description", "Deny inbound rule"),
                    Map.entry("name", "rule1"),
                    Map.entry("protocols", Map.ofEntries(
                        Map.entry("port", 443),
                        Map.entry("protocolType", "Https")
                    )),
                    Map.entry("ruleType", "ApplicationRule"),
                    Map.entry("sourceAddresses",                     
                        "216.58.216.164",
                        "10.0.0.0/24"),
                    Map.entry("webCategories", "Hacking")
                ))
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const firewallPolicyRuleCollectionGroup = new azure_native.network.FirewallPolicyRuleCollectionGroup("firewallPolicyRuleCollectionGroup", {
    firewallPolicyName: "firewallPolicy",
    priority: 110,
    resourceGroupName: "rg1",
    ruleCollectionGroupName: "ruleCollectionGroup1",
    ruleCollections: [{
        action: {
            type: "Deny",
        },
        name: "Example-Filter-Rule-Collection",
        ruleCollectionType: "FirewallPolicyFilterRuleCollection",
        rules: [{
            description: "Deny inbound rule",
            name: "rule1",
            protocols: [{
                port: 443,
                protocolType: "Https",
            }],
            ruleType: "ApplicationRule",
            sourceAddresses: [
                "216.58.216.164",
                "10.0.0.0/24",
            ],
            webCategories: ["Hacking"],
        }],
    }],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

firewall_policy_rule_collection_group = azure_native.network.FirewallPolicyRuleCollectionGroup("firewallPolicyRuleCollectionGroup",
    firewall_policy_name="firewallPolicy",
    priority=110,
    resource_group_name="rg1",
    rule_collection_group_name="ruleCollectionGroup1",
    rule_collections=[azure_native.network.FirewallPolicyFilterRuleCollectionArgs(
        action=azure_native.network.FirewallPolicyFilterRuleCollectionActionArgs(
            type="Deny",
        ),
        name="Example-Filter-Rule-Collection",
        rule_collection_type="FirewallPolicyFilterRuleCollection",
        rules=[azure_native.network.ApplicationRuleArgs(
            description="Deny inbound rule",
            name="rule1",
            protocols=[azure_native.network.FirewallPolicyRuleApplicationProtocolArgs(
                port=443,
                protocol_type="Https",
            )],
            rule_type="ApplicationRule",
            source_addresses=[
                "216.58.216.164",
                "10.0.0.0/24",
            ],
            web_categories=["Hacking"],
        )],
    )])

```

```yaml
resources:
  firewallPolicyRuleCollectionGroup:
    type: azure-native:network:FirewallPolicyRuleCollectionGroup
    properties:
      firewallPolicyName: firewallPolicy
      priority: 110
      resourceGroupName: rg1
      ruleCollectionGroupName: ruleCollectionGroup1
      ruleCollections:
        - action:
            type: Deny
          name: Example-Filter-Rule-Collection
          ruleCollectionType: FirewallPolicyFilterRuleCollection
          rules:
            - description: Deny inbound rule
              name: rule1
              protocols:
                - port: 443
                  protocolType: Https
              ruleType: ApplicationRule
              sourceAddresses:
                - 216.58.216.164
                - 10.0.0.0/24
              webCategories:
                - Hacking

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:FirewallPolicyRuleCollectionGroup ruleCollectionGroup1 /subscriptions/e747cc13-97d4-4a79-b463-42d7f4e558f2/resourceGroups/rg1/providers/Microsoft.Network/firewallPolicies/firewallPolicy/ruleCollectionGroups/ruleCollectionGroup1 
```
