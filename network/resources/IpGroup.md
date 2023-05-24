The IpGroups resource information.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateOrUpdate_IpGroups
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var ipGroup = new AzureNative.Network.IpGroup("ipGroup", new()
    {
        IpAddresses = new[]
        {
            "13.64.39.16/32",
            "40.74.146.80/31",
            "40.74.147.32/28",
        },
        IpGroupsName = "ipGroups1",
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
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
		_, err := network.NewIpGroup(ctx, "ipGroup", &network.IpGroupArgs{
			IpAddresses: pulumi.StringArray{
				pulumi.String("13.64.39.16/32"),
				pulumi.String("40.74.146.80/31"),
				pulumi.String("40.74.147.32/28"),
			},
			IpGroupsName:      pulumi.String("ipGroups1"),
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.network.IpGroup;
import com.pulumi.azurenative.network.IpGroupArgs;
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
        var ipGroup = new IpGroup("ipGroup", IpGroupArgs.builder()        
            .ipAddresses(            
                "13.64.39.16/32",
                "40.74.146.80/31",
                "40.74.147.32/28")
            .ipGroupsName("ipGroups1")
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .tags(Map.of("key1", "value1"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const ipGroup = new azure_native.network.IpGroup("ipGroup", {
    ipAddresses: [
        "13.64.39.16/32",
        "40.74.146.80/31",
        "40.74.147.32/28",
    ],
    ipGroupsName: "ipGroups1",
    location: "West US",
    resourceGroupName: "myResourceGroup",
    tags: {
        key1: "value1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

ip_group = azure_native.network.IpGroup("ipGroup",
    ip_addresses=[
        "13.64.39.16/32",
        "40.74.146.80/31",
        "40.74.147.32/28",
    ],
    ip_groups_name="ipGroups1",
    location="West US",
    resource_group_name="myResourceGroup",
    tags={
        "key1": "value1",
    })

```

```yaml
resources:
  ipGroup:
    type: azure-native:network:IpGroup
    properties:
      ipAddresses:
        - 13.64.39.16/32
        - 40.74.146.80/31
        - 40.74.147.32/28
      ipGroupsName: ipGroups1
      location: West US
      resourceGroupName: myResourceGroup
      tags:
        key1: value1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:IpGroup ipGroups1 /subscriptions/subId/providers/Microsoft.Network/resourceGroup/myResourceGroup/ipGroups/ipGroups1 
```
