VpnGatewayNatRule Resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### NatRulePut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var natRule = new AzureNative.Network.NatRule("natRule", new()
    {
        ExternalMappings = new[]
        {
            new AzureNative.Network.Inputs.VpnNatRuleMappingArgs
            {
                AddressSpace = "192.168.21.0/24",
            },
        },
        GatewayName = "gateway1",
        InternalMappings = new[]
        {
            new AzureNative.Network.Inputs.VpnNatRuleMappingArgs
            {
                AddressSpace = "10.4.0.0/24",
            },
        },
        IpConfigurationId = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/cloudnet1-VNG/ipConfigurations/default",
        Mode = "EgressSnat",
        NatRuleName = "natRule1",
        ResourceGroupName = "rg1",
        Type = "Static",
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
		_, err := network.NewNatRule(ctx, "natRule", &network.NatRuleArgs{
			ExternalMappings: []network.VpnNatRuleMappingArgs{
				{
					AddressSpace: pulumi.String("192.168.21.0/24"),
				},
			},
			GatewayName: pulumi.String("gateway1"),
			InternalMappings: []network.VpnNatRuleMappingArgs{
				{
					AddressSpace: pulumi.String("10.4.0.0/24"),
				},
			},
			IpConfigurationId: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/cloudnet1-VNG/ipConfigurations/default"),
			Mode:              pulumi.String("EgressSnat"),
			NatRuleName:       pulumi.String("natRule1"),
			ResourceGroupName: pulumi.String("rg1"),
			Type:              pulumi.String("Static"),
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
import com.pulumi.azurenative.network.NatRule;
import com.pulumi.azurenative.network.NatRuleArgs;
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
        var natRule = new NatRule("natRule", NatRuleArgs.builder()        
            .externalMappings(Map.of("addressSpace", "192.168.21.0/24"))
            .gatewayName("gateway1")
            .internalMappings(Map.of("addressSpace", "10.4.0.0/24"))
            .ipConfigurationId("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/cloudnet1-VNG/ipConfigurations/default")
            .mode("EgressSnat")
            .natRuleName("natRule1")
            .resourceGroupName("rg1")
            .type("Static")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const natRule = new azure_native.network.NatRule("natRule", {
    externalMappings: [{
        addressSpace: "192.168.21.0/24",
    }],
    gatewayName: "gateway1",
    internalMappings: [{
        addressSpace: "10.4.0.0/24",
    }],
    ipConfigurationId: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/cloudnet1-VNG/ipConfigurations/default",
    mode: "EgressSnat",
    natRuleName: "natRule1",
    resourceGroupName: "rg1",
    type: "Static",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

nat_rule = azure_native.network.NatRule("natRule",
    external_mappings=[azure_native.network.VpnNatRuleMappingArgs(
        address_space="192.168.21.0/24",
    )],
    gateway_name="gateway1",
    internal_mappings=[azure_native.network.VpnNatRuleMappingArgs(
        address_space="10.4.0.0/24",
    )],
    ip_configuration_id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/cloudnet1-VNG/ipConfigurations/default",
    mode="EgressSnat",
    nat_rule_name="natRule1",
    resource_group_name="rg1",
    type="Static")

```

```yaml
resources:
  natRule:
    type: azure-native:network:NatRule
    properties:
      externalMappings:
        - addressSpace: 192.168.21.0/24
      gatewayName: gateway1
      internalMappings:
        - addressSpace: 10.4.0.0/24
      ipConfigurationId: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworkGateways/cloudnet1-VNG/ipConfigurations/default
      mode: EgressSnat
      natRuleName: natRule1
      resourceGroupName: rg1
      type: Static

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:NatRule natRule1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnGateways/gateway1/natRules/natRule1 
```
