Describes an inbound endpoint for a DNS resolver.
API Version: 2022-07-01.
Previous API Version: 2020-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Upsert inbound endpoint for DNS resolver
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var inboundEndpoint = new AzureNative.Network.InboundEndpoint("inboundEndpoint", new()
    {
        DnsResolverName = "sampleDnsResolver",
        InboundEndpointName = "sampleInboundEndpoint",
        IpConfigurations = new[]
        {
            new AzureNative.Network.Inputs.InboundEndpointIPConfigurationArgs
            {
                PrivateIpAllocationMethod = "Dynamic",
                Subnet = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/0403cfa9-9659-4f33-9f30-1f191c51d111/resourceGroups/sampleVnetResourceGroupName/providers/Microsoft.Network/virtualNetworks/sampleVirtualNetwork/subnets/sampleSubnet",
                },
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
		_, err := network.NewInboundEndpoint(ctx, "inboundEndpoint", &network.InboundEndpointArgs{
			DnsResolverName:     pulumi.String("sampleDnsResolver"),
			InboundEndpointName: pulumi.String("sampleInboundEndpoint"),
			IpConfigurations: []network.InboundEndpointIPConfigurationArgs{
				{
					PrivateIpAllocationMethod: pulumi.String("Dynamic"),
					Subnet: {
						Id: pulumi.String("/subscriptions/0403cfa9-9659-4f33-9f30-1f191c51d111/resourceGroups/sampleVnetResourceGroupName/providers/Microsoft.Network/virtualNetworks/sampleVirtualNetwork/subnets/sampleSubnet"),
					},
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
import com.pulumi.azurenative.network.InboundEndpoint;
import com.pulumi.azurenative.network.InboundEndpointArgs;
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
        var inboundEndpoint = new InboundEndpoint("inboundEndpoint", InboundEndpointArgs.builder()        
            .dnsResolverName("sampleDnsResolver")
            .inboundEndpointName("sampleInboundEndpoint")
            .ipConfigurations(Map.ofEntries(
                Map.entry("privateIpAllocationMethod", "Dynamic"),
                Map.entry("subnet", Map.of("id", "/subscriptions/0403cfa9-9659-4f33-9f30-1f191c51d111/resourceGroups/sampleVnetResourceGroupName/providers/Microsoft.Network/virtualNetworks/sampleVirtualNetwork/subnets/sampleSubnet"))
            ))
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

const inboundEndpoint = new azure_native.network.InboundEndpoint("inboundEndpoint", {
    dnsResolverName: "sampleDnsResolver",
    inboundEndpointName: "sampleInboundEndpoint",
    ipConfigurations: [{
        privateIpAllocationMethod: "Dynamic",
        subnet: {
            id: "/subscriptions/0403cfa9-9659-4f33-9f30-1f191c51d111/resourceGroups/sampleVnetResourceGroupName/providers/Microsoft.Network/virtualNetworks/sampleVirtualNetwork/subnets/sampleSubnet",
        },
    }],
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

inbound_endpoint = azure_native.network.InboundEndpoint("inboundEndpoint",
    dns_resolver_name="sampleDnsResolver",
    inbound_endpoint_name="sampleInboundEndpoint",
    ip_configurations=[{
        "privateIpAllocationMethod": "Dynamic",
        "subnet": azure_native.network.SubResourceArgs(
            id="/subscriptions/0403cfa9-9659-4f33-9f30-1f191c51d111/resourceGroups/sampleVnetResourceGroupName/providers/Microsoft.Network/virtualNetworks/sampleVirtualNetwork/subnets/sampleSubnet",
        ),
    }],
    location="westus2",
    resource_group_name="sampleResourceGroup",
    tags={
        "key1": "value1",
    })

```

```yaml
resources:
  inboundEndpoint:
    type: azure-native:network:InboundEndpoint
    properties:
      dnsResolverName: sampleDnsResolver
      inboundEndpointName: sampleInboundEndpoint
      ipConfigurations:
        - privateIpAllocationMethod: Dynamic
          subnet:
            id: /subscriptions/0403cfa9-9659-4f33-9f30-1f191c51d111/resourceGroups/sampleVnetResourceGroupName/providers/Microsoft.Network/virtualNetworks/sampleVirtualNetwork/subnets/sampleSubnet
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
$ pulumi import azure-native:network:InboundEndpoint sampleInboundEndpoint /subscriptions/abdd4249-9f34-4cc6-8e42-c2e32110603e/resourceGroups/sampleResourceGroup/providers/Microsoft.Network/inboundEndpoints/sampleInboundEndpoint 
```
