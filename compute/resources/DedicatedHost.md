Specifies information about the Dedicated host.
API Version: 2022-11-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a dedicated host .
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var dedicatedHost = new AzureNative.Compute.DedicatedHost("dedicatedHost", new()
    {
        HostGroupName = "myDedicatedHostGroup",
        HostName = "myDedicatedHost",
        Location = "westus",
        PlatformFaultDomain = 1,
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Name = "DSv3-Type1",
        },
        Tags = 
        {
            { "department", "HR" },
        },
    });

});


```

```go
package main

import (
	compute "github.com/pulumi/pulumi-azure-native-sdk/compute"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := compute.NewDedicatedHost(ctx, "dedicatedHost", &compute.DedicatedHostArgs{
			HostGroupName:       pulumi.String("myDedicatedHostGroup"),
			HostName:            pulumi.String("myDedicatedHost"),
			Location:            pulumi.String("westus"),
			PlatformFaultDomain: pulumi.Int(1),
			ResourceGroupName:   pulumi.String("myResourceGroup"),
			Sku: &compute.SkuArgs{
				Name: pulumi.String("DSv3-Type1"),
			},
			Tags: pulumi.StringMap{
				"department": pulumi.String("HR"),
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
import com.pulumi.azurenative.compute.DedicatedHost;
import com.pulumi.azurenative.compute.DedicatedHostArgs;
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
        var dedicatedHost = new DedicatedHost("dedicatedHost", DedicatedHostArgs.builder()        
            .hostGroupName("myDedicatedHostGroup")
            .hostName("myDedicatedHost")
            .location("westus")
            .platformFaultDomain(1)
            .resourceGroupName("myResourceGroup")
            .sku(Map.of("name", "DSv3-Type1"))
            .tags(Map.of("department", "HR"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const dedicatedHost = new azure_native.compute.DedicatedHost("dedicatedHost", {
    hostGroupName: "myDedicatedHostGroup",
    hostName: "myDedicatedHost",
    location: "westus",
    platformFaultDomain: 1,
    resourceGroupName: "myResourceGroup",
    sku: {
        name: "DSv3-Type1",
    },
    tags: {
        department: "HR",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

dedicated_host = azure_native.compute.DedicatedHost("dedicatedHost",
    host_group_name="myDedicatedHostGroup",
    host_name="myDedicatedHost",
    location="westus",
    platform_fault_domain=1,
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        name="DSv3-Type1",
    ),
    tags={
        "department": "HR",
    })

```

```yaml
resources:
  dedicatedHost:
    type: azure-native:compute:DedicatedHost
    properties:
      hostGroupName: myDedicatedHostGroup
      hostName: myDedicatedHost
      location: westus
      platformFaultDomain: 1
      resourceGroupName: myResourceGroup
      sku:
        name: DSv3-Type1
      tags:
        department: HR

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:compute:DedicatedHost myDedicatedHost /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/HostGroups/myDedicatedHostGroup/hosts/myDedicatedHost 
```
