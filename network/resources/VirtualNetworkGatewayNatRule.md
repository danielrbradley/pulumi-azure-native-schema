VirtualNetworkGatewayNatRule Resource.
API Version: 2022-09-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### VirtualNetworkGatewayNatRulePut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualNetworkGatewayNatRule = new AzureNative.Network.VirtualNetworkGatewayNatRule("virtualNetworkGatewayNatRule", new()
    {
        ExternalMappings = new[]
        {
            new AzureNative.Network.Inputs.VpnNatRuleMappingArgs
            {
                AddressSpace = "192.168.21.0/24",
                PortRange = "300-400",
            },
        },
        InternalMappings = new[]
        {
            new AzureNative.Network.Inputs.VpnNatRuleMappingArgs
            {
                AddressSpace = "10.4.0.0/24",
                PortRange = "200-300",
            },
        },
        IpConfigurationId = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/gateway1/ipConfigurations/default",
        Mode = "EgressSnat",
        NatRuleName = "natRule1",
        ResourceGroupName = "rg1",
        Type = "Static",
        VirtualNetworkGatewayName = "gateway1",
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
		_, err := network.NewVirtualNetworkGatewayNatRule(ctx, "virtualNetworkGatewayNatRule", &network.VirtualNetworkGatewayNatRuleArgs{
			ExternalMappings: []network.VpnNatRuleMappingArgs{
				{
					AddressSpace: pulumi.String("192.168.21.0/24"),
					PortRange:    pulumi.String("300-400"),
				},
			},
			InternalMappings: []network.VpnNatRuleMappingArgs{
				{
					AddressSpace: pulumi.String("10.4.0.0/24"),
					PortRange:    pulumi.String("200-300"),
				},
			},
			IpConfigurationId:         pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/gateway1/ipConfigurations/default"),
			Mode:                      pulumi.String("EgressSnat"),
			NatRuleName:               pulumi.String("natRule1"),
			ResourceGroupName:         pulumi.String("rg1"),
			Type:                      pulumi.String("Static"),
			VirtualNetworkGatewayName: pulumi.String("gateway1"),
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
import com.pulumi.azurenative.network.VirtualNetworkGatewayNatRule;
import com.pulumi.azurenative.network.VirtualNetworkGatewayNatRuleArgs;
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
        var virtualNetworkGatewayNatRule = new VirtualNetworkGatewayNatRule("virtualNetworkGatewayNatRule", VirtualNetworkGatewayNatRuleArgs.builder()        
            .externalMappings(Map.ofEntries(
                Map.entry("addressSpace", "192.168.21.0/24"),
                Map.entry("portRange", "300-400")
            ))
            .internalMappings(Map.ofEntries(
                Map.entry("addressSpace", "10.4.0.0/24"),
                Map.entry("portRange", "200-300")
            ))
            .ipConfigurationId("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/gateway1/ipConfigurations/default")
            .mode("EgressSnat")
            .natRuleName("natRule1")
            .resourceGroupName("rg1")
            .type("Static")
            .virtualNetworkGatewayName("gateway1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualNetworkGatewayNatRule = new azure_native.network.VirtualNetworkGatewayNatRule("virtualNetworkGatewayNatRule", {
    externalMappings: [{
        addressSpace: "192.168.21.0/24",
        portRange: "300-400",
    }],
    internalMappings: [{
        addressSpace: "10.4.0.0/24",
        portRange: "200-300",
    }],
    ipConfigurationId: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/gateway1/ipConfigurations/default",
    mode: "EgressSnat",
    natRuleName: "natRule1",
    resourceGroupName: "rg1",
    type: "Static",
    virtualNetworkGatewayName: "gateway1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_network_gateway_nat_rule = azure_native.network.VirtualNetworkGatewayNatRule("virtualNetworkGatewayNatRule",
    external_mappings=[azure_native.network.VpnNatRuleMappingArgs(
        address_space="192.168.21.0/24",
        port_range="300-400",
    )],
    internal_mappings=[azure_native.network.VpnNatRuleMappingArgs(
        address_space="10.4.0.0/24",
        port_range="200-300",
    )],
    ip_configuration_id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/gateway1/ipConfigurations/default",
    mode="EgressSnat",
    nat_rule_name="natRule1",
    resource_group_name="rg1",
    type="Static",
    virtual_network_gateway_name="gateway1")

```

```yaml
resources:
  virtualNetworkGatewayNatRule:
    type: azure-native:network:VirtualNetworkGatewayNatRule
    properties:
      externalMappings:
        - addressSpace: 192.168.21.0/24
          portRange: 300-400
      internalMappings:
        - addressSpace: 10.4.0.0/24
          portRange: 200-300
      ipConfigurationId: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/gateway1/ipConfigurations/default
      mode: EgressSnat
      natRuleName: natRule1
      resourceGroupName: rg1
      type: Static
      virtualNetworkGatewayName: gateway1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:VirtualNetworkGatewayNatRule natRule1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/gateway1/natRules/natRule1 
```
