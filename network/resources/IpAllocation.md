IpAllocation resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create IpAllocation
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var ipAllocation = new AzureNative.Network.IpAllocation("ipAllocation", new()
    {
        AllocationTags = 
        {
            { "VNetID", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/HypernetVnet1" },
        },
        IpAllocationName = "test-ipallocation",
        Location = "centraluseuap",
        Prefix = "3.2.5.0/24",
        ResourceGroupName = "rg1",
        Type = "Hypernet",
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
		_, err := network.NewIpAllocation(ctx, "ipAllocation", &network.IpAllocationArgs{
			AllocationTags: pulumi.StringMap{
				"VNetID": pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/HypernetVnet1"),
			},
			IpAllocationName:  pulumi.String("test-ipallocation"),
			Location:          pulumi.String("centraluseuap"),
			Prefix:            pulumi.String("3.2.5.0/24"),
			ResourceGroupName: pulumi.String("rg1"),
			Type:              pulumi.String("Hypernet"),
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
import com.pulumi.azurenative.network.IpAllocation;
import com.pulumi.azurenative.network.IpAllocationArgs;
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
        var ipAllocation = new IpAllocation("ipAllocation", IpAllocationArgs.builder()        
            .allocationTags(Map.of("VNetID", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/HypernetVnet1"))
            .ipAllocationName("test-ipallocation")
            .location("centraluseuap")
            .prefix("3.2.5.0/24")
            .resourceGroupName("rg1")
            .type("Hypernet")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const ipAllocation = new azure_native.network.IpAllocation("ipAllocation", {
    allocationTags: {
        VNetID: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/HypernetVnet1",
    },
    ipAllocationName: "test-ipallocation",
    location: "centraluseuap",
    prefix: "3.2.5.0/24",
    resourceGroupName: "rg1",
    type: "Hypernet",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

ip_allocation = azure_native.network.IpAllocation("ipAllocation",
    allocation_tags={
        "VNetID": "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/HypernetVnet1",
    },
    ip_allocation_name="test-ipallocation",
    location="centraluseuap",
    prefix="3.2.5.0/24",
    resource_group_name="rg1",
    type="Hypernet")

```

```yaml
resources:
  ipAllocation:
    type: azure-native:network:IpAllocation
    properties:
      allocationTags:
        VNetID: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/HypernetVnet1
      ipAllocationName: test-ipallocation
      location: centraluseuap
      prefix: 3.2.5.0/24
      resourceGroupName: rg1
      type: Hypernet

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:IpAllocation test-ipallocation /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/IpAllocations/test-ipallocation 
```
