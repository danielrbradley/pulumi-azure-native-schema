Describes a DNS forwarding ruleset.
API Version: 2022-07-01.
Previous API Version: 2020-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Upsert DNS forwarding ruleset
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var dnsForwardingRuleset = new AzureNative.Network.DnsForwardingRuleset("dnsForwardingRuleset", new()
    {
        DnsForwardingRulesetName = "samplednsForwardingRuleset",
        DnsResolverOutboundEndpoints = new[]
        {
            new AzureNative.Network.Inputs.SubResourceArgs
            {
                Id = "/subscriptions/abdd4249-9f34-4cc6-8e42-c2e32110603e/resourceGroups/sampleResourceGroup/providers/Microsoft.Network/dnsResolvers/sampleDnsResolver/outboundEndpoints/sampleOutboundEndpoint0",
            },
            new AzureNative.Network.Inputs.SubResourceArgs
            {
                Id = "/subscriptions/abdd4249-9f34-4cc6-8e42-c2e32110603e/resourceGroups/sampleResourceGroup/providers/Microsoft.Network/dnsResolvers/sampleDnsResolver/outboundEndpoints/sampleOutboundEndpoint1",
            },
        },
        Location = "westus2",
        ResourceGroupName = "sampleResourceGroup",
        Tags = 
        {
            { "key1", "value1" },
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
		_, err := network.NewDnsForwardingRuleset(ctx, "dnsForwardingRuleset", &network.DnsForwardingRulesetArgs{
			DnsForwardingRulesetName: pulumi.String("samplednsForwardingRuleset"),
			DnsResolverOutboundEndpoints: []network.SubResourceArgs{
				{
					Id: pulumi.String("/subscriptions/abdd4249-9f34-4cc6-8e42-c2e32110603e/resourceGroups/sampleResourceGroup/providers/Microsoft.Network/dnsResolvers/sampleDnsResolver/outboundEndpoints/sampleOutboundEndpoint0"),
				},
				{
					Id: pulumi.String("/subscriptions/abdd4249-9f34-4cc6-8e42-c2e32110603e/resourceGroups/sampleResourceGroup/providers/Microsoft.Network/dnsResolvers/sampleDnsResolver/outboundEndpoints/sampleOutboundEndpoint1"),
				},
			},
			Location:          pulumi.String("westus2"),
			ResourceGroupName: pulumi.String("sampleResourceGroup"),
			Tags: pulumi.StringMap{
				"key1": pulumi.String("value1"),
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
import com.pulumi.azurenative.network.DnsForwardingRuleset;
import com.pulumi.azurenative.network.DnsForwardingRulesetArgs;
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
        var dnsForwardingRuleset = new DnsForwardingRuleset("dnsForwardingRuleset", DnsForwardingRulesetArgs.builder()        
            .dnsForwardingRulesetName("samplednsForwardingRuleset")
            .dnsResolverOutboundEndpoints(            
                Map.of("id", "/subscriptions/abdd4249-9f34-4cc6-8e42-c2e32110603e/resourceGroups/sampleResourceGroup/providers/Microsoft.Network/dnsResolvers/sampleDnsResolver/outboundEndpoints/sampleOutboundEndpoint0"),
                Map.of("id", "/subscriptions/abdd4249-9f34-4cc6-8e42-c2e32110603e/resourceGroups/sampleResourceGroup/providers/Microsoft.Network/dnsResolvers/sampleDnsResolver/outboundEndpoints/sampleOutboundEndpoint1"))
            .location("westus2")
            .resourceGroupName("sampleResourceGroup")
            .tags(Map.of("key1", "value1"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const dnsForwardingRuleset = new azure_native.network.DnsForwardingRuleset("dnsForwardingRuleset", {
    dnsForwardingRulesetName: "samplednsForwardingRuleset",
    dnsResolverOutboundEndpoints: [
        {
            id: "/subscriptions/abdd4249-9f34-4cc6-8e42-c2e32110603e/resourceGroups/sampleResourceGroup/providers/Microsoft.Network/dnsResolvers/sampleDnsResolver/outboundEndpoints/sampleOutboundEndpoint0",
        },
        {
            id: "/subscriptions/abdd4249-9f34-4cc6-8e42-c2e32110603e/resourceGroups/sampleResourceGroup/providers/Microsoft.Network/dnsResolvers/sampleDnsResolver/outboundEndpoints/sampleOutboundEndpoint1",
        },
    ],
    location: "westus2",
    resourceGroupName: "sampleResourceGroup",
    tags: {
        key1: "value1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

dns_forwarding_ruleset = azure_native.network.DnsForwardingRuleset("dnsForwardingRuleset",
    dns_forwarding_ruleset_name="samplednsForwardingRuleset",
    dns_resolver_outbound_endpoints=[
        azure_native.network.SubResourceArgs(
            id="/subscriptions/abdd4249-9f34-4cc6-8e42-c2e32110603e/resourceGroups/sampleResourceGroup/providers/Microsoft.Network/dnsResolvers/sampleDnsResolver/outboundEndpoints/sampleOutboundEndpoint0",
        ),
        azure_native.network.SubResourceArgs(
            id="/subscriptions/abdd4249-9f34-4cc6-8e42-c2e32110603e/resourceGroups/sampleResourceGroup/providers/Microsoft.Network/dnsResolvers/sampleDnsResolver/outboundEndpoints/sampleOutboundEndpoint1",
        ),
    ],
    location="westus2",
    resource_group_name="sampleResourceGroup",
    tags={
        "key1": "value1",
    })

```

```yaml
resources:
  dnsForwardingRuleset:
    type: azure-native:network:DnsForwardingRuleset
    properties:
      dnsForwardingRulesetName: samplednsForwardingRuleset
      dnsResolverOutboundEndpoints:
        - id: /subscriptions/abdd4249-9f34-4cc6-8e42-c2e32110603e/resourceGroups/sampleResourceGroup/providers/Microsoft.Network/dnsResolvers/sampleDnsResolver/outboundEndpoints/sampleOutboundEndpoint0
        - id: /subscriptions/abdd4249-9f34-4cc6-8e42-c2e32110603e/resourceGroups/sampleResourceGroup/providers/Microsoft.Network/dnsResolvers/sampleDnsResolver/outboundEndpoints/sampleOutboundEndpoint1
      location: westus2
      resourceGroupName: sampleResourceGroup
      tags:
        key1: value1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:DnsForwardingRuleset sampleDnsForwardingRuleset /subscriptions/abdd4249-9f34-4cc6-8e42-c2e32110603e/resourceGroups/sampleResourceGroup/providers/Microsoft.Network/dnsForwardingRulesets/sampleDnsForwardingRuleset 
```
