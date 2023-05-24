Private link service resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create private link service
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateLinkService = new AzureNative.Network.PrivateLinkService("privateLinkService", new()
    {
        AutoApproval = new AzureNative.Network.Inputs.PrivateLinkServicePropertiesAutoApprovalArgs
        {
            Subscriptions = new[]
            {
                "subscription1",
                "subscription2",
            },
        },
        Fqdns = new[]
        {
            "fqdn1",
            "fqdn2",
            "fqdn3",
        },
        IpConfigurations = new[]
        {
            new AzureNative.Network.Inputs.PrivateLinkServiceIpConfigurationArgs
            {
                Name = "fe-lb",
                PrivateIPAddress = "10.0.1.4",
                PrivateIPAddressVersion = "IPv4",
                PrivateIPAllocationMethod = "Static",
                Subnet = new AzureNative.Network.Inputs.SubnetArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb",
                },
            },
        },
        LoadBalancerFrontendIpConfigurations = new[]
        {
            new AzureNative.Network.Inputs.FrontendIPConfigurationArgs
            {
                Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
            },
        },
        Location = "eastus",
        ResourceGroupName = "rg1",
        ServiceName = "testPls",
        Visibility = new AzureNative.Network.Inputs.PrivateLinkServicePropertiesVisibilityArgs
        {
            Subscriptions = new[]
            {
                "subscription1",
                "subscription2",
                "subscription3",
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
		_, err := network.NewPrivateLinkService(ctx, "privateLinkService", &network.PrivateLinkServiceArgs{
			AutoApproval: &network.PrivateLinkServicePropertiesAutoApprovalArgs{
				Subscriptions: pulumi.StringArray{
					pulumi.String("subscription1"),
					pulumi.String("subscription2"),
				},
			},
			Fqdns: pulumi.StringArray{
				pulumi.String("fqdn1"),
				pulumi.String("fqdn2"),
				pulumi.String("fqdn3"),
			},
			IpConfigurations: []network.PrivateLinkServiceIpConfigurationArgs{
				{
					Name:                      pulumi.String("fe-lb"),
					PrivateIPAddress:          pulumi.String("10.0.1.4"),
					PrivateIPAddressVersion:   pulumi.String("IPv4"),
					PrivateIPAllocationMethod: pulumi.String("Static"),
					Subnet: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb"),
					},
				},
			},
			LoadBalancerFrontendIpConfigurations: []network.FrontendIPConfigurationArgs{
				{
					Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb"),
				},
			},
			Location:          pulumi.String("eastus"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("testPls"),
			Visibility: &network.PrivateLinkServicePropertiesVisibilityArgs{
				Subscriptions: pulumi.StringArray{
					pulumi.String("subscription1"),
					pulumi.String("subscription2"),
					pulumi.String("subscription3"),
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
import com.pulumi.azurenative.network.PrivateLinkService;
import com.pulumi.azurenative.network.PrivateLinkServiceArgs;
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
        var privateLinkService = new PrivateLinkService("privateLinkService", PrivateLinkServiceArgs.builder()        
            .autoApproval(Map.of("subscriptions",             
                "subscription1",
                "subscription2"))
            .fqdns(            
                "fqdn1",
                "fqdn2",
                "fqdn3")
            .ipConfigurations(Map.ofEntries(
                Map.entry("name", "fe-lb"),
                Map.entry("privateIPAddress", "10.0.1.4"),
                Map.entry("privateIPAddressVersion", "IPv4"),
                Map.entry("privateIPAllocationMethod", "Static"),
                Map.entry("subnet", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb"))
            ))
            .loadBalancerFrontendIpConfigurations(Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb"))
            .location("eastus")
            .resourceGroupName("rg1")
            .serviceName("testPls")
            .visibility(Map.of("subscriptions",             
                "subscription1",
                "subscription2",
                "subscription3"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateLinkService = new azure_native.network.PrivateLinkService("privateLinkService", {
    autoApproval: {
        subscriptions: [
            "subscription1",
            "subscription2",
        ],
    },
    fqdns: [
        "fqdn1",
        "fqdn2",
        "fqdn3",
    ],
    ipConfigurations: [{
        name: "fe-lb",
        privateIPAddress: "10.0.1.4",
        privateIPAddressVersion: "IPv4",
        privateIPAllocationMethod: "Static",
        subnet: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb",
        },
    }],
    loadBalancerFrontendIpConfigurations: [{
        id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
    }],
    location: "eastus",
    resourceGroupName: "rg1",
    serviceName: "testPls",
    visibility: {
        subscriptions: [
            "subscription1",
            "subscription2",
            "subscription3",
        ],
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_link_service = azure_native.network.PrivateLinkService("privateLinkService",
    auto_approval=azure_native.network.PrivateLinkServicePropertiesAutoApprovalArgs(
        subscriptions=[
            "subscription1",
            "subscription2",
        ],
    ),
    fqdns=[
        "fqdn1",
        "fqdn2",
        "fqdn3",
    ],
    ip_configurations=[{
        "name": "fe-lb",
        "privateIPAddress": "10.0.1.4",
        "privateIPAddressVersion": "IPv4",
        "privateIPAllocationMethod": "Static",
        "subnet": azure_native.network.SubnetArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb",
        ),
    }],
    load_balancer_frontend_ip_configurations=[azure_native.network.FrontendIPConfigurationArgs(
        id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
    )],
    location="eastus",
    resource_group_name="rg1",
    service_name="testPls",
    visibility=azure_native.network.PrivateLinkServicePropertiesVisibilityArgs(
        subscriptions=[
            "subscription1",
            "subscription2",
            "subscription3",
        ],
    ))

```

```yaml
resources:
  privateLinkService:
    type: azure-native:network:PrivateLinkService
    properties:
      autoApproval:
        subscriptions:
          - subscription1
          - subscription2
      fqdns:
        - fqdn1
        - fqdn2
        - fqdn3
      ipConfigurations:
        - name: fe-lb
          privateIPAddress: 10.0.1.4
          privateIPAddressVersion: IPv4
          privateIPAllocationMethod: Static
          subnet:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb
      loadBalancerFrontendIpConfigurations:
        - id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb
      location: eastus
      resourceGroupName: rg1
      serviceName: testPls
      visibility:
        subscriptions:
          - subscription1
          - subscription2
          - subscription3

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:PrivateLinkService testPls /subscriptions/subId/resourceGroups/rg1/providers/Microsoft.Network/privateLinkServices/testPls 
```
