Response for Disk Pool request.
API Version: 2021-08-01.
Previous API Version: 2020-03-15-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or Update Disk pool
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var diskPool = new AzureNative.StoragePool.DiskPool("diskPool", new()
    {
        AvailabilityZones = new[]
        {
            "1",
        },
        DiskPoolName = "myDiskPool",
        Disks = new[]
        {
            new AzureNative.StoragePool.Inputs.DiskArgs
            {
                Id = "/subscriptions/11111111-1111-1111-1111-111111111111/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/vm-name_DataDisk_0",
            },
            new AzureNative.StoragePool.Inputs.DiskArgs
            {
                Id = "/subscriptions/11111111-1111-1111-1111-111111111111/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/vm-name_DataDisk_1",
            },
        },
        Location = "westus",
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.StoragePool.Inputs.SkuArgs
        {
            Name = "Basic_V1",
            Tier = "Basic",
        },
        SubnetId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myvnet/subnets/mysubnet",
        Tags = 
        {
            { "key", "value" },
        },
    });

});


```

```go
package main

import (
	storagepool "github.com/pulumi/pulumi-azure-native-sdk/storagepool"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := storagepool.NewDiskPool(ctx, "diskPool", &storagepool.DiskPoolArgs{
			AvailabilityZones: pulumi.StringArray{
				pulumi.String("1"),
			},
			DiskPoolName: pulumi.String("myDiskPool"),
			Disks: []storagepool.DiskArgs{
				{
					Id: pulumi.String("/subscriptions/11111111-1111-1111-1111-111111111111/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/vm-name_DataDisk_0"),
				},
				{
					Id: pulumi.String("/subscriptions/11111111-1111-1111-1111-111111111111/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/vm-name_DataDisk_1"),
				},
			},
			Location:          pulumi.String("westus"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			Sku: &storagepool.SkuArgs{
				Name: pulumi.String("Basic_V1"),
				Tier: pulumi.String("Basic"),
			},
			SubnetId: pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myvnet/subnets/mysubnet"),
			Tags: pulumi.StringMap{
				"key": pulumi.String("value"),
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
import com.pulumi.azurenative.storagepool.DiskPool;
import com.pulumi.azurenative.storagepool.DiskPoolArgs;
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
        var diskPool = new DiskPool("diskPool", DiskPoolArgs.builder()        
            .availabilityZones("1")
            .diskPoolName("myDiskPool")
            .disks(            
                Map.of("id", "/subscriptions/11111111-1111-1111-1111-111111111111/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/vm-name_DataDisk_0"),
                Map.of("id", "/subscriptions/11111111-1111-1111-1111-111111111111/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/vm-name_DataDisk_1"))
            .location("westus")
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("name", "Basic_V1"),
                Map.entry("tier", "Basic")
            ))
            .subnetId("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myvnet/subnets/mysubnet")
            .tags(Map.of("key", "value"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const diskPool = new azure_native.storagepool.DiskPool("diskPool", {
    availabilityZones: ["1"],
    diskPoolName: "myDiskPool",
    disks: [
        {
            id: "/subscriptions/11111111-1111-1111-1111-111111111111/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/vm-name_DataDisk_0",
        },
        {
            id: "/subscriptions/11111111-1111-1111-1111-111111111111/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/vm-name_DataDisk_1",
        },
    ],
    location: "westus",
    resourceGroupName: "myResourceGroup",
    sku: {
        name: "Basic_V1",
        tier: "Basic",
    },
    subnetId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myvnet/subnets/mysubnet",
    tags: {
        key: "value",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

disk_pool = azure_native.storagepool.DiskPool("diskPool",
    availability_zones=["1"],
    disk_pool_name="myDiskPool",
    disks=[
        azure_native.storagepool.DiskArgs(
            id="/subscriptions/11111111-1111-1111-1111-111111111111/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/vm-name_DataDisk_0",
        ),
        azure_native.storagepool.DiskArgs(
            id="/subscriptions/11111111-1111-1111-1111-111111111111/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/vm-name_DataDisk_1",
        ),
    ],
    location="westus",
    resource_group_name="myResourceGroup",
    sku=azure_native.storagepool.SkuArgs(
        name="Basic_V1",
        tier="Basic",
    ),
    subnet_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myvnet/subnets/mysubnet",
    tags={
        "key": "value",
    })

```

```yaml
resources:
  diskPool:
    type: azure-native:storagepool:DiskPool
    properties:
      availabilityZones:
        - '1'
      diskPoolName: myDiskPool
      disks:
        - id: /subscriptions/11111111-1111-1111-1111-111111111111/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/vm-name_DataDisk_0
        - id: /subscriptions/11111111-1111-1111-1111-111111111111/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/vm-name_DataDisk_1
      location: westus
      resourceGroupName: myResourceGroup
      sku:
        name: Basic_V1
        tier: Basic
      subnetId: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myvnet/subnets/mysubnet
      tags:
        key: value

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:storagepool:DiskPool myDiskPool /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.StoragePool/diskPools/myDiskPool 
```
