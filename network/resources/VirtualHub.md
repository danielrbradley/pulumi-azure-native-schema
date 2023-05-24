VirtualHub Resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### VirtualHubPut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualHub = new AzureNative.Network.VirtualHub("virtualHub", new()
    {
        AddressPrefix = "10.168.0.0/24",
        Location = "West US",
        ResourceGroupName = "rg1",
        Sku = "Basic",
        Tags = 
        {
            { "key1", "value1" },
        },
        VirtualHubName = "virtualHub2",
        VirtualWan = new AzureNative.Network.Inputs.SubResourceArgs
        {
            Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualWans/virtualWan1",
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
		_, err := network.NewVirtualHub(ctx, "virtualHub", &network.VirtualHubArgs{
			AddressPrefix:     pulumi.String("10.168.0.0/24"),
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("rg1"),
			Sku:               pulumi.String("Basic"),
			Tags: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			VirtualHubName: pulumi.String("virtualHub2"),
			VirtualWan: &network.SubResourceArgs{
				Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualWans/virtualWan1"),
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
import com.pulumi.azurenative.network.VirtualHub;
import com.pulumi.azurenative.network.VirtualHubArgs;
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
        var virtualHub = new VirtualHub("virtualHub", VirtualHubArgs.builder()        
            .addressPrefix("10.168.0.0/24")
            .location("West US")
            .resourceGroupName("rg1")
            .sku("Basic")
            .tags(Map.of("key1", "value1"))
            .virtualHubName("virtualHub2")
            .virtualWan(Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualWans/virtualWan1"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualHub = new azure_native.network.VirtualHub("virtualHub", {
    addressPrefix: "10.168.0.0/24",
    location: "West US",
    resourceGroupName: "rg1",
    sku: "Basic",
    tags: {
        key1: "value1",
    },
    virtualHubName: "virtualHub2",
    virtualWan: {
        id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualWans/virtualWan1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_hub = azure_native.network.VirtualHub("virtualHub",
    address_prefix="10.168.0.0/24",
    location="West US",
    resource_group_name="rg1",
    sku="Basic",
    tags={
        "key1": "value1",
    },
    virtual_hub_name="virtualHub2",
    virtual_wan=azure_native.network.SubResourceArgs(
        id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualWans/virtualWan1",
    ))

```

```yaml
resources:
  virtualHub:
    type: azure-native:network:VirtualHub
    properties:
      addressPrefix: 10.168.0.0/24
      location: West US
      resourceGroupName: rg1
      sku: Basic
      tags:
        key1: value1
      virtualHubName: virtualHub2
      virtualWan:
        id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualWans/virtualWan1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:VirtualHub virtualHub2 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/virtualHub2 
```
