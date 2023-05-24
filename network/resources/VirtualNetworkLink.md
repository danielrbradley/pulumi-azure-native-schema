Describes a virtual network link.
API Version: 2022-07-01.
Previous API Version: 2020-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Upsert virtual network link to a DNS forwarding ruleset
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualNetworkLink = new AzureNative.Network.VirtualNetworkLink("virtualNetworkLink", new()
    {
        DnsForwardingRulesetName = "sampleDnsForwardingRuleset",
        Metadata = 
        {
            { "additionalProp1", "value1" },
        },
        ResourceGroupName = "sampleResourceGroup",
        VirtualNetwork = new AzureNative.Network.Inputs.SubResourceArgs
        {
            Id = "/subscriptions/0403cfa9-9659-4f33-9f30-1f191c51d111/resourceGroups/sampleVnetResourceGroupName/providers/Microsoft.Network/virtualNetworks/sampleVirtualNetwork",
        },
        VirtualNetworkLinkName = "sampleVirtualNetworkLink",
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
		_, err := network.NewVirtualNetworkLink(ctx, "virtualNetworkLink", &network.VirtualNetworkLinkArgs{
			DnsForwardingRulesetName: pulumi.String("sampleDnsForwardingRuleset"),
			Metadata: pulumi.StringMap{
				"additionalProp1": pulumi.String("value1"),
			},
			ResourceGroupName: pulumi.String("sampleResourceGroup"),
			VirtualNetwork: &network.SubResourceArgs{
				Id: pulumi.String("/subscriptions/0403cfa9-9659-4f33-9f30-1f191c51d111/resourceGroups/sampleVnetResourceGroupName/providers/Microsoft.Network/virtualNetworks/sampleVirtualNetwork"),
			},
			VirtualNetworkLinkName: pulumi.String("sampleVirtualNetworkLink"),
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
import com.pulumi.azurenative.network.VirtualNetworkLink;
import com.pulumi.azurenative.network.VirtualNetworkLinkArgs;
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
        var virtualNetworkLink = new VirtualNetworkLink("virtualNetworkLink", VirtualNetworkLinkArgs.builder()        
            .dnsForwardingRulesetName("sampleDnsForwardingRuleset")
            .metadata(Map.of("additionalProp1", "value1"))
            .resourceGroupName("sampleResourceGroup")
            .virtualNetwork(Map.of("id", "/subscriptions/0403cfa9-9659-4f33-9f30-1f191c51d111/resourceGroups/sampleVnetResourceGroupName/providers/Microsoft.Network/virtualNetworks/sampleVirtualNetwork"))
            .virtualNetworkLinkName("sampleVirtualNetworkLink")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualNetworkLink = new azure_native.network.VirtualNetworkLink("virtualNetworkLink", {
    dnsForwardingRulesetName: "sampleDnsForwardingRuleset",
    metadata: {
        additionalProp1: "value1",
    },
    resourceGroupName: "sampleResourceGroup",
    virtualNetwork: {
        id: "/subscriptions/0403cfa9-9659-4f33-9f30-1f191c51d111/resourceGroups/sampleVnetResourceGroupName/providers/Microsoft.Network/virtualNetworks/sampleVirtualNetwork",
    },
    virtualNetworkLinkName: "sampleVirtualNetworkLink",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_network_link = azure_native.network.VirtualNetworkLink("virtualNetworkLink",
    dns_forwarding_ruleset_name="sampleDnsForwardingRuleset",
    metadata={
        "additionalProp1": "value1",
    },
    resource_group_name="sampleResourceGroup",
    virtual_network=azure_native.network.SubResourceArgs(
        id="/subscriptions/0403cfa9-9659-4f33-9f30-1f191c51d111/resourceGroups/sampleVnetResourceGroupName/providers/Microsoft.Network/virtualNetworks/sampleVirtualNetwork",
    ),
    virtual_network_link_name="sampleVirtualNetworkLink")

```

```yaml
resources:
  virtualNetworkLink:
    type: azure-native:network:VirtualNetworkLink
    properties:
      dnsForwardingRulesetName: sampleDnsForwardingRuleset
      metadata:
        additionalProp1: value1
      resourceGroupName: sampleResourceGroup
      virtualNetwork:
        id: /subscriptions/0403cfa9-9659-4f33-9f30-1f191c51d111/resourceGroups/sampleVnetResourceGroupName/providers/Microsoft.Network/virtualNetworks/sampleVirtualNetwork
      virtualNetworkLinkName: sampleVirtualNetworkLink

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:VirtualNetworkLink sampleVirtualNetworkLink /subscriptions/abdd4249-9f34-4cc6-8e42-c2e32110603e/resourceGroups/sampleResourceGroup/providers/Microsoft.Network/dnsForwardingRuleset/sampleDnsForwardingRuleset/virtualNetworkLinks/sampleVirtualNetworkLink 
```
