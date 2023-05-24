Describes an outbound endpoint for a DNS resolver.
API Version: 2022-07-01.
Previous API Version: 2020-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Upsert outbound endpoint for DNS resolver
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var outboundEndpoint = new AzureNative.Network.OutboundEndpoint("outboundEndpoint", new()
    {
        DnsResolverName = "sampleDnsResolver",
        Location = "westus2",
        OutboundEndpointName = "sampleOutboundEndpoint",
        ResourceGroupName = "sampleResourceGroup",
        Subnet = new AzureNative.Network.Inputs.SubResourceArgs
        {
            Id = "/subscriptions/0403cfa9-9659-4f33-9f30-1f191c51d111/resourceGroups/sampleVnetResourceGroupName/providers/Microsoft.Network/virtualNetworks/sampleVirtualNetwork/subnets/sampleSubnet",
        },
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
		_, err := network.NewOutboundEndpoint(ctx, "outboundEndpoint", &network.OutboundEndpointArgs{
			DnsResolverName:      pulumi.String("sampleDnsResolver"),
			Location:             pulumi.String("westus2"),
			OutboundEndpointName: pulumi.String("sampleOutboundEndpoint"),
			ResourceGroupName:    pulumi.String("sampleResourceGroup"),
			Subnet: &network.SubResourceArgs{
				Id: pulumi.String("/subscriptions/0403cfa9-9659-4f33-9f30-1f191c51d111/resourceGroups/sampleVnetResourceGroupName/providers/Microsoft.Network/virtualNetworks/sampleVirtualNetwork/subnets/sampleSubnet"),
			},
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
import com.pulumi.azurenative.network.OutboundEndpoint;
import com.pulumi.azurenative.network.OutboundEndpointArgs;
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
        var outboundEndpoint = new OutboundEndpoint("outboundEndpoint", OutboundEndpointArgs.builder()        
            .dnsResolverName("sampleDnsResolver")
            .location("westus2")
            .outboundEndpointName("sampleOutboundEndpoint")
            .resourceGroupName("sampleResourceGroup")
            .subnet(Map.of("id", "/subscriptions/0403cfa9-9659-4f33-9f30-1f191c51d111/resourceGroups/sampleVnetResourceGroupName/providers/Microsoft.Network/virtualNetworks/sampleVirtualNetwork/subnets/sampleSubnet"))
            .tags(Map.of("key1", "value1"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const outboundEndpoint = new azure_native.network.OutboundEndpoint("outboundEndpoint", {
    dnsResolverName: "sampleDnsResolver",
    location: "westus2",
    outboundEndpointName: "sampleOutboundEndpoint",
    resourceGroupName: "sampleResourceGroup",
    subnet: {
        id: "/subscriptions/0403cfa9-9659-4f33-9f30-1f191c51d111/resourceGroups/sampleVnetResourceGroupName/providers/Microsoft.Network/virtualNetworks/sampleVirtualNetwork/subnets/sampleSubnet",
    },
    tags: {
        key1: "value1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

outbound_endpoint = azure_native.network.OutboundEndpoint("outboundEndpoint",
    dns_resolver_name="sampleDnsResolver",
    location="westus2",
    outbound_endpoint_name="sampleOutboundEndpoint",
    resource_group_name="sampleResourceGroup",
    subnet=azure_native.network.SubResourceArgs(
        id="/subscriptions/0403cfa9-9659-4f33-9f30-1f191c51d111/resourceGroups/sampleVnetResourceGroupName/providers/Microsoft.Network/virtualNetworks/sampleVirtualNetwork/subnets/sampleSubnet",
    ),
    tags={
        "key1": "value1",
    })

```

```yaml
resources:
  outboundEndpoint:
    type: azure-native:network:OutboundEndpoint
    properties:
      dnsResolverName: sampleDnsResolver
      location: westus2
      outboundEndpointName: sampleOutboundEndpoint
      resourceGroupName: sampleResourceGroup
      subnet:
        id: /subscriptions/0403cfa9-9659-4f33-9f30-1f191c51d111/resourceGroups/sampleVnetResourceGroupName/providers/Microsoft.Network/virtualNetworks/sampleVirtualNetwork/subnets/sampleSubnet
      tags:
        key1: value1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:OutboundEndpoint sampleOutboundEndpoint /subscriptions/abdd4249-9f34-4cc6-8e42-c2e32110603e/resourceGroups/sampleResourceGroup/providers/Microsoft.Network/outboundEndpoints/sampleOutboundEndpoint 
```
