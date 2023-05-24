VirtualWAN Resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### VirtualWANCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualWan = new AzureNative.Network.VirtualWan("virtualWan", new()
    {
        DisableVpnEncryption = false,
        Location = "West US",
        ResourceGroupName = "rg1",
        Tags = 
        {
            { "key1", "value1" },
        },
        Type = "Basic",
        VirtualWANName = "wan1",
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
		_, err := network.NewVirtualWan(ctx, "virtualWan", &network.VirtualWanArgs{
			DisableVpnEncryption: pulumi.Bool(false),
			Location:             pulumi.String("West US"),
			ResourceGroupName:    pulumi.String("rg1"),
			Tags: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			Type:           pulumi.String("Basic"),
			VirtualWANName: pulumi.String("wan1"),
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
import com.pulumi.azurenative.network.VirtualWan;
import com.pulumi.azurenative.network.VirtualWanArgs;
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
        var virtualWan = new VirtualWan("virtualWan", VirtualWanArgs.builder()        
            .disableVpnEncryption(false)
            .location("West US")
            .resourceGroupName("rg1")
            .tags(Map.of("key1", "value1"))
            .type("Basic")
            .virtualWANName("wan1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualWan = new azure_native.network.VirtualWan("virtualWan", {
    disableVpnEncryption: false,
    location: "West US",
    resourceGroupName: "rg1",
    tags: {
        key1: "value1",
    },
    type: "Basic",
    virtualWANName: "wan1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_wan = azure_native.network.VirtualWan("virtualWan",
    disable_vpn_encryption=False,
    location="West US",
    resource_group_name="rg1",
    tags={
        "key1": "value1",
    },
    type="Basic",
    virtual_wan_name="wan1")

```

```yaml
resources:
  virtualWan:
    type: azure-native:network:VirtualWan
    properties:
      disableVpnEncryption: false
      location: West US
      resourceGroupName: rg1
      tags:
        key1: value1
      type: Basic
      virtualWANName: wan1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:VirtualWan wan1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualWANs/wan1 
```
