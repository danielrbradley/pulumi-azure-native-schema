Describes a DNS resolver.
API Version: 2022-07-01.
Previous API Version: 2020-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Upsert DNS resolver
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var dnsResolver = new AzureNative.Network.DnsResolver("dnsResolver", new()
    {
        DnsResolverName = "sampleDnsResolver",
        Location = "westus2",
        ResourceGroupName = "sampleResourceGroup",
        Tags = 
        {
            { "key1", "value1" },
        },
        VirtualNetwork = new AzureNative.Network.Inputs.SubResourceArgs
        {
            Id = "/subscriptions/cbb1387e-4b03-44f2-ad41-58d4677b9873/resourceGroups/virtualNetworkResourceGroup/providers/Microsoft.Network/virtualNetworks/sampleVirtualNetwork",
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
		_, err := network.NewDnsResolver(ctx, "dnsResolver", &network.DnsResolverArgs{
			DnsResolverName:   pulumi.String("sampleDnsResolver"),
			Location:          pulumi.String("westus2"),
			ResourceGroupName: pulumi.String("sampleResourceGroup"),
			Tags: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			VirtualNetwork: &network.SubResourceArgs{
				Id: pulumi.String("/subscriptions/cbb1387e-4b03-44f2-ad41-58d4677b9873/resourceGroups/virtualNetworkResourceGroup/providers/Microsoft.Network/virtualNetworks/sampleVirtualNetwork"),
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
import com.pulumi.azurenative.network.DnsResolver;
import com.pulumi.azurenative.network.DnsResolverArgs;
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
        var dnsResolver = new DnsResolver("dnsResolver", DnsResolverArgs.builder()        
            .dnsResolverName("sampleDnsResolver")
            .location("westus2")
            .resourceGroupName("sampleResourceGroup")
            .tags(Map.of("key1", "value1"))
            .virtualNetwork(Map.of("id", "/subscriptions/cbb1387e-4b03-44f2-ad41-58d4677b9873/resourceGroups/virtualNetworkResourceGroup/providers/Microsoft.Network/virtualNetworks/sampleVirtualNetwork"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const dnsResolver = new azure_native.network.DnsResolver("dnsResolver", {
    dnsResolverName: "sampleDnsResolver",
    location: "westus2",
    resourceGroupName: "sampleResourceGroup",
    tags: {
        key1: "value1",
    },
    virtualNetwork: {
        id: "/subscriptions/cbb1387e-4b03-44f2-ad41-58d4677b9873/resourceGroups/virtualNetworkResourceGroup/providers/Microsoft.Network/virtualNetworks/sampleVirtualNetwork",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

dns_resolver = azure_native.network.DnsResolver("dnsResolver",
    dns_resolver_name="sampleDnsResolver",
    location="westus2",
    resource_group_name="sampleResourceGroup",
    tags={
        "key1": "value1",
    },
    virtual_network=azure_native.network.SubResourceArgs(
        id="/subscriptions/cbb1387e-4b03-44f2-ad41-58d4677b9873/resourceGroups/virtualNetworkResourceGroup/providers/Microsoft.Network/virtualNetworks/sampleVirtualNetwork",
    ))

```

```yaml
resources:
  dnsResolver:
    type: azure-native:network:DnsResolver
    properties:
      dnsResolverName: sampleDnsResolver
      location: westus2
      resourceGroupName: sampleResourceGroup
      tags:
        key1: value1
      virtualNetwork:
        id: /subscriptions/cbb1387e-4b03-44f2-ad41-58d4677b9873/resourceGroups/virtualNetworkResourceGroup/providers/Microsoft.Network/virtualNetworks/sampleVirtualNetwork

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:DnsResolver sampleDnsResolver /subscriptions/abdd4249-9f34-4cc6-8e42-c2e32110603e/resourceGroups/sampleResourceGroup/providers/Microsoft.Network/dnsResolvers/sampleDnsResolver 
```
