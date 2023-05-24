Inbound NAT rule of the load balancer.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### InboundNatRuleCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var inboundNatRule = new AzureNative.Network.InboundNatRule("inboundNatRule", new()
    {
        BackendPort = 3389,
        EnableFloatingIP = false,
        EnableTcpReset = false,
        FrontendIPConfiguration = new AzureNative.Network.Inputs.SubResourceArgs
        {
            Id = "/subscriptions/subid/resourceGroups/testrg/providers/Microsoft.Network/loadBalancers/lb1/frontendIPConfigurations/ip1",
        },
        FrontendPort = 3390,
        IdleTimeoutInMinutes = 4,
        InboundNatRuleName = "natRule1.1",
        LoadBalancerName = "lb1",
        Protocol = "Tcp",
        ResourceGroupName = "testrg",
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
		_, err := network.NewInboundNatRule(ctx, "inboundNatRule", &network.InboundNatRuleArgs{
			BackendPort:      pulumi.Int(3389),
			EnableFloatingIP: pulumi.Bool(false),
			EnableTcpReset:   pulumi.Bool(false),
			FrontendIPConfiguration: &network.SubResourceArgs{
				Id: pulumi.String("/subscriptions/subid/resourceGroups/testrg/providers/Microsoft.Network/loadBalancers/lb1/frontendIPConfigurations/ip1"),
			},
			FrontendPort:         pulumi.Int(3390),
			IdleTimeoutInMinutes: pulumi.Int(4),
			InboundNatRuleName:   pulumi.String("natRule1.1"),
			LoadBalancerName:     pulumi.String("lb1"),
			Protocol:             pulumi.String("Tcp"),
			ResourceGroupName:    pulumi.String("testrg"),
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
import com.pulumi.azurenative.network.InboundNatRule;
import com.pulumi.azurenative.network.InboundNatRuleArgs;
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
        var inboundNatRule = new InboundNatRule("inboundNatRule", InboundNatRuleArgs.builder()        
            .backendPort(3389)
            .enableFloatingIP(false)
            .enableTcpReset(false)
            .frontendIPConfiguration(Map.of("id", "/subscriptions/subid/resourceGroups/testrg/providers/Microsoft.Network/loadBalancers/lb1/frontendIPConfigurations/ip1"))
            .frontendPort(3390)
            .idleTimeoutInMinutes(4)
            .inboundNatRuleName("natRule1.1")
            .loadBalancerName("lb1")
            .protocol("Tcp")
            .resourceGroupName("testrg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const inboundNatRule = new azure_native.network.InboundNatRule("inboundNatRule", {
    backendPort: 3389,
    enableFloatingIP: false,
    enableTcpReset: false,
    frontendIPConfiguration: {
        id: "/subscriptions/subid/resourceGroups/testrg/providers/Microsoft.Network/loadBalancers/lb1/frontendIPConfigurations/ip1",
    },
    frontendPort: 3390,
    idleTimeoutInMinutes: 4,
    inboundNatRuleName: "natRule1.1",
    loadBalancerName: "lb1",
    protocol: "Tcp",
    resourceGroupName: "testrg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

inbound_nat_rule = azure_native.network.InboundNatRule("inboundNatRule",
    backend_port=3389,
    enable_floating_ip=False,
    enable_tcp_reset=False,
    frontend_ip_configuration=azure_native.network.SubResourceArgs(
        id="/subscriptions/subid/resourceGroups/testrg/providers/Microsoft.Network/loadBalancers/lb1/frontendIPConfigurations/ip1",
    ),
    frontend_port=3390,
    idle_timeout_in_minutes=4,
    inbound_nat_rule_name="natRule1.1",
    load_balancer_name="lb1",
    protocol="Tcp",
    resource_group_name="testrg")

```

```yaml
resources:
  inboundNatRule:
    type: azure-native:network:InboundNatRule
    properties:
      backendPort: 3389
      enableFloatingIP: false
      enableTcpReset: false
      frontendIPConfiguration:
        id: /subscriptions/subid/resourceGroups/testrg/providers/Microsoft.Network/loadBalancers/lb1/frontendIPConfigurations/ip1
      frontendPort: 3390
      idleTimeoutInMinutes: 4
      inboundNatRuleName: natRule1.1
      loadBalancerName: lb1
      protocol: Tcp
      resourceGroupName: testrg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:InboundNatRule natRule1.1 /subscriptions/subid/resourceGroups/testrg/providers/Microsoft.Network/loadBalancers/lb1/inboundNatRules/natRule1.1 
```
