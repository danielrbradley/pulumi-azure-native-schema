Description of NetworkRuleSet resource.
API Version: 2021-11-01.
Previous API Version: 2017-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### NameSpaceNetworkRuleSetCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var namespaceNetworkRuleSet = new AzureNative.ServiceBus.NamespaceNetworkRuleSet("namespaceNetworkRuleSet", new()
    {
        DefaultAction = "Deny",
        IpRules = new[]
        {
            new AzureNative.ServiceBus.Inputs.NWRuleSetIpRulesArgs
            {
                Action = "Allow",
                IpMask = "1.1.1.1",
            },
            new AzureNative.ServiceBus.Inputs.NWRuleSetIpRulesArgs
            {
                Action = "Allow",
                IpMask = "1.1.1.2",
            },
            new AzureNative.ServiceBus.Inputs.NWRuleSetIpRulesArgs
            {
                Action = "Allow",
                IpMask = "1.1.1.3",
            },
            new AzureNative.ServiceBus.Inputs.NWRuleSetIpRulesArgs
            {
                Action = "Allow",
                IpMask = "1.1.1.4",
            },
            new AzureNative.ServiceBus.Inputs.NWRuleSetIpRulesArgs
            {
                Action = "Allow",
                IpMask = "1.1.1.5",
            },
        },
        NamespaceName = "sdk-Namespace-6019",
        ResourceGroupName = "ResourceGroup",
        VirtualNetworkRules = new[]
        {
            new AzureNative.ServiceBus.Inputs.NWRuleSetVirtualNetworkRulesArgs
            {
                IgnoreMissingVnetServiceEndpoint = true,
                Subnet = new AzureNative.ServiceBus.Inputs.SubnetArgs
                {
                    Id = "/subscriptions/854d368f-1828-428f-8f3c-f2affa9b2f7d/resourcegroups/alitest/providers/Microsoft.Network/virtualNetworks/myvn/subnets/subnet2",
                },
            },
            new AzureNative.ServiceBus.Inputs.NWRuleSetVirtualNetworkRulesArgs
            {
                IgnoreMissingVnetServiceEndpoint = false,
                Subnet = new AzureNative.ServiceBus.Inputs.SubnetArgs
                {
                    Id = "/subscriptions/854d368f-1828-428f-8f3c-f2affa9b2f7d/resourcegroups/alitest/providers/Microsoft.Network/virtualNetworks/myvn/subnets/subnet3",
                },
            },
            new AzureNative.ServiceBus.Inputs.NWRuleSetVirtualNetworkRulesArgs
            {
                IgnoreMissingVnetServiceEndpoint = false,
                Subnet = new AzureNative.ServiceBus.Inputs.SubnetArgs
                {
                    Id = "/subscriptions/854d368f-1828-428f-8f3c-f2affa9b2f7d/resourcegroups/alitest/providers/Microsoft.Network/virtualNetworks/myvn/subnets/subnet6",
                },
            },
        },
    });

});


```

```go
package main

import (
	servicebus "github.com/pulumi/pulumi-azure-native-sdk/servicebus"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := servicebus.NewNamespaceNetworkRuleSet(ctx, "namespaceNetworkRuleSet", &servicebus.NamespaceNetworkRuleSetArgs{
			DefaultAction: pulumi.String("Deny"),
			IpRules: []servicebus.NWRuleSetIpRulesArgs{
				{
					Action: pulumi.String("Allow"),
					IpMask: pulumi.String("1.1.1.1"),
				},
				{
					Action: pulumi.String("Allow"),
					IpMask: pulumi.String("1.1.1.2"),
				},
				{
					Action: pulumi.String("Allow"),
					IpMask: pulumi.String("1.1.1.3"),
				},
				{
					Action: pulumi.String("Allow"),
					IpMask: pulumi.String("1.1.1.4"),
				},
				{
					Action: pulumi.String("Allow"),
					IpMask: pulumi.String("1.1.1.5"),
				},
			},
			NamespaceName:     pulumi.String("sdk-Namespace-6019"),
			ResourceGroupName: pulumi.String("ResourceGroup"),
			VirtualNetworkRules: []servicebus.NWRuleSetVirtualNetworkRulesArgs{
				{
					IgnoreMissingVnetServiceEndpoint: pulumi.Bool(true),
					Subnet: {
						Id: pulumi.String("/subscriptions/854d368f-1828-428f-8f3c-f2affa9b2f7d/resourcegroups/alitest/providers/Microsoft.Network/virtualNetworks/myvn/subnets/subnet2"),
					},
				},
				{
					IgnoreMissingVnetServiceEndpoint: pulumi.Bool(false),
					Subnet: {
						Id: pulumi.String("/subscriptions/854d368f-1828-428f-8f3c-f2affa9b2f7d/resourcegroups/alitest/providers/Microsoft.Network/virtualNetworks/myvn/subnets/subnet3"),
					},
				},
				{
					IgnoreMissingVnetServiceEndpoint: pulumi.Bool(false),
					Subnet: {
						Id: pulumi.String("/subscriptions/854d368f-1828-428f-8f3c-f2affa9b2f7d/resourcegroups/alitest/providers/Microsoft.Network/virtualNetworks/myvn/subnets/subnet6"),
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
import com.pulumi.azurenative.servicebus.NamespaceNetworkRuleSet;
import com.pulumi.azurenative.servicebus.NamespaceNetworkRuleSetArgs;
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
        var namespaceNetworkRuleSet = new NamespaceNetworkRuleSet("namespaceNetworkRuleSet", NamespaceNetworkRuleSetArgs.builder()        
            .defaultAction("Deny")
            .ipRules(            
                Map.ofEntries(
                    Map.entry("action", "Allow"),
                    Map.entry("ipMask", "1.1.1.1")
                ),
                Map.ofEntries(
                    Map.entry("action", "Allow"),
                    Map.entry("ipMask", "1.1.1.2")
                ),
                Map.ofEntries(
                    Map.entry("action", "Allow"),
                    Map.entry("ipMask", "1.1.1.3")
                ),
                Map.ofEntries(
                    Map.entry("action", "Allow"),
                    Map.entry("ipMask", "1.1.1.4")
                ),
                Map.ofEntries(
                    Map.entry("action", "Allow"),
                    Map.entry("ipMask", "1.1.1.5")
                ))
            .namespaceName("sdk-Namespace-6019")
            .resourceGroupName("ResourceGroup")
            .virtualNetworkRules(            
                Map.ofEntries(
                    Map.entry("ignoreMissingVnetServiceEndpoint", true),
                    Map.entry("subnet", Map.of("id", "/subscriptions/854d368f-1828-428f-8f3c-f2affa9b2f7d/resourcegroups/alitest/providers/Microsoft.Network/virtualNetworks/myvn/subnets/subnet2"))
                ),
                Map.ofEntries(
                    Map.entry("ignoreMissingVnetServiceEndpoint", false),
                    Map.entry("subnet", Map.of("id", "/subscriptions/854d368f-1828-428f-8f3c-f2affa9b2f7d/resourcegroups/alitest/providers/Microsoft.Network/virtualNetworks/myvn/subnets/subnet3"))
                ),
                Map.ofEntries(
                    Map.entry("ignoreMissingVnetServiceEndpoint", false),
                    Map.entry("subnet", Map.of("id", "/subscriptions/854d368f-1828-428f-8f3c-f2affa9b2f7d/resourcegroups/alitest/providers/Microsoft.Network/virtualNetworks/myvn/subnets/subnet6"))
                ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const namespaceNetworkRuleSet = new azure_native.servicebus.NamespaceNetworkRuleSet("namespaceNetworkRuleSet", {
    defaultAction: "Deny",
    ipRules: [
        {
            action: "Allow",
            ipMask: "1.1.1.1",
        },
        {
            action: "Allow",
            ipMask: "1.1.1.2",
        },
        {
            action: "Allow",
            ipMask: "1.1.1.3",
        },
        {
            action: "Allow",
            ipMask: "1.1.1.4",
        },
        {
            action: "Allow",
            ipMask: "1.1.1.5",
        },
    ],
    namespaceName: "sdk-Namespace-6019",
    resourceGroupName: "ResourceGroup",
    virtualNetworkRules: [
        {
            ignoreMissingVnetServiceEndpoint: true,
            subnet: {
                id: "/subscriptions/854d368f-1828-428f-8f3c-f2affa9b2f7d/resourcegroups/alitest/providers/Microsoft.Network/virtualNetworks/myvn/subnets/subnet2",
            },
        },
        {
            ignoreMissingVnetServiceEndpoint: false,
            subnet: {
                id: "/subscriptions/854d368f-1828-428f-8f3c-f2affa9b2f7d/resourcegroups/alitest/providers/Microsoft.Network/virtualNetworks/myvn/subnets/subnet3",
            },
        },
        {
            ignoreMissingVnetServiceEndpoint: false,
            subnet: {
                id: "/subscriptions/854d368f-1828-428f-8f3c-f2affa9b2f7d/resourcegroups/alitest/providers/Microsoft.Network/virtualNetworks/myvn/subnets/subnet6",
            },
        },
    ],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

namespace_network_rule_set = azure_native.servicebus.NamespaceNetworkRuleSet("namespaceNetworkRuleSet",
    default_action="Deny",
    ip_rules=[
        azure_native.servicebus.NWRuleSetIpRulesArgs(
            action="Allow",
            ip_mask="1.1.1.1",
        ),
        azure_native.servicebus.NWRuleSetIpRulesArgs(
            action="Allow",
            ip_mask="1.1.1.2",
        ),
        azure_native.servicebus.NWRuleSetIpRulesArgs(
            action="Allow",
            ip_mask="1.1.1.3",
        ),
        azure_native.servicebus.NWRuleSetIpRulesArgs(
            action="Allow",
            ip_mask="1.1.1.4",
        ),
        azure_native.servicebus.NWRuleSetIpRulesArgs(
            action="Allow",
            ip_mask="1.1.1.5",
        ),
    ],
    namespace_name="sdk-Namespace-6019",
    resource_group_name="ResourceGroup",
    virtual_network_rules=[
        {
            "ignoreMissingVnetServiceEndpoint": True,
            "subnet": azure_native.servicebus.SubnetArgs(
                id="/subscriptions/854d368f-1828-428f-8f3c-f2affa9b2f7d/resourcegroups/alitest/providers/Microsoft.Network/virtualNetworks/myvn/subnets/subnet2",
            ),
        },
        {
            "ignoreMissingVnetServiceEndpoint": False,
            "subnet": azure_native.servicebus.SubnetArgs(
                id="/subscriptions/854d368f-1828-428f-8f3c-f2affa9b2f7d/resourcegroups/alitest/providers/Microsoft.Network/virtualNetworks/myvn/subnets/subnet3",
            ),
        },
        {
            "ignoreMissingVnetServiceEndpoint": False,
            "subnet": azure_native.servicebus.SubnetArgs(
                id="/subscriptions/854d368f-1828-428f-8f3c-f2affa9b2f7d/resourcegroups/alitest/providers/Microsoft.Network/virtualNetworks/myvn/subnets/subnet6",
            ),
        },
    ])

```

```yaml
resources:
  namespaceNetworkRuleSet:
    type: azure-native:servicebus:NamespaceNetworkRuleSet
    properties:
      defaultAction: Deny
      ipRules:
        - action: Allow
          ipMask: 1.1.1.1
        - action: Allow
          ipMask: 1.1.1.2
        - action: Allow
          ipMask: 1.1.1.3
        - action: Allow
          ipMask: 1.1.1.4
        - action: Allow
          ipMask: 1.1.1.5
      namespaceName: sdk-Namespace-6019
      resourceGroupName: ResourceGroup
      virtualNetworkRules:
        - ignoreMissingVnetServiceEndpoint: true
          subnet:
            id: /subscriptions/854d368f-1828-428f-8f3c-f2affa9b2f7d/resourcegroups/alitest/providers/Microsoft.Network/virtualNetworks/myvn/subnets/subnet2
        - ignoreMissingVnetServiceEndpoint: false
          subnet:
            id: /subscriptions/854d368f-1828-428f-8f3c-f2affa9b2f7d/resourcegroups/alitest/providers/Microsoft.Network/virtualNetworks/myvn/subnets/subnet3
        - ignoreMissingVnetServiceEndpoint: false
          subnet:
            id: /subscriptions/854d368f-1828-428f-8f3c-f2affa9b2f7d/resourcegroups/alitest/providers/Microsoft.Network/virtualNetworks/myvn/subnets/subnet6

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:servicebus:NamespaceNetworkRuleSet default /subscriptions/854d368f-1828-428f-8f3c-f2affa9b2f7d/resourceGroups/Default-ServiceBus-AustraliaEast/providers/Microsoft.ServiceBus/namespaces/sdk-Namespace-9659/networkruleset/default 
```
