NetworkVirtualAppliance Resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create SaaS NetworkVirtualAppliance
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var networkVirtualAppliance = new AzureNative.Network.NetworkVirtualAppliance("networkVirtualAppliance", new()
    {
        Delegation = new AzureNative.Network.Inputs.DelegationPropertiesArgs
        {
            ServiceName = "PaloAltoNetworks.Cloudngfw/firewalls",
        },
        Location = "West US",
        NetworkVirtualApplianceName = "nva",
        ResourceGroupName = "rg1",
        Tags = 
        {
            { "key1", "value1" },
        },
        VirtualHub = new AzureNative.Network.Inputs.SubResourceArgs
        {
            Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1",
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
		_, err := network.NewNetworkVirtualAppliance(ctx, "networkVirtualAppliance", &network.NetworkVirtualApplianceArgs{
			Delegation: &network.DelegationPropertiesArgs{
				ServiceName: pulumi.String("PaloAltoNetworks.Cloudngfw/firewalls"),
			},
			Location:                    pulumi.String("West US"),
			NetworkVirtualApplianceName: pulumi.String("nva"),
			ResourceGroupName:           pulumi.String("rg1"),
			Tags: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			VirtualHub: &network.SubResourceArgs{
				Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1"),
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
import com.pulumi.azurenative.network.NetworkVirtualAppliance;
import com.pulumi.azurenative.network.NetworkVirtualApplianceArgs;
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
        var networkVirtualAppliance = new NetworkVirtualAppliance("networkVirtualAppliance", NetworkVirtualApplianceArgs.builder()        
            .delegation(Map.of("serviceName", "PaloAltoNetworks.Cloudngfw/firewalls"))
            .location("West US")
            .networkVirtualApplianceName("nva")
            .resourceGroupName("rg1")
            .tags(Map.of("key1", "value1"))
            .virtualHub(Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const networkVirtualAppliance = new azure_native.network.NetworkVirtualAppliance("networkVirtualAppliance", {
    delegation: {
        serviceName: "PaloAltoNetworks.Cloudngfw/firewalls",
    },
    location: "West US",
    networkVirtualApplianceName: "nva",
    resourceGroupName: "rg1",
    tags: {
        key1: "value1",
    },
    virtualHub: {
        id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

network_virtual_appliance = azure_native.network.NetworkVirtualAppliance("networkVirtualAppliance",
    delegation=azure_native.network.DelegationPropertiesArgs(
        service_name="PaloAltoNetworks.Cloudngfw/firewalls",
    ),
    location="West US",
    network_virtual_appliance_name="nva",
    resource_group_name="rg1",
    tags={
        "key1": "value1",
    },
    virtual_hub=azure_native.network.SubResourceArgs(
        id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1",
    ))

```

```yaml
resources:
  networkVirtualAppliance:
    type: azure-native:network:NetworkVirtualAppliance
    properties:
      delegation:
        serviceName: PaloAltoNetworks.Cloudngfw/firewalls
      location: West US
      networkVirtualApplianceName: nva
      resourceGroupName: rg1
      tags:
        key1: value1
      virtualHub:
        id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:NetworkVirtualAppliance nva /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/networkVirtualAppliances/nva 
```
