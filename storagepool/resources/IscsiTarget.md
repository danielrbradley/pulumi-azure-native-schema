Response for iSCSI Target requests.
API Version: 2021-08-01.
Previous API Version: 2020-03-15-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or Update iSCSI Target
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var iscsiTarget = new AzureNative.StoragePool.IscsiTarget("iscsiTarget", new()
    {
        AclMode = "Dynamic",
        DiskPoolName = "myDiskPool",
        IscsiTargetName = "myIscsiTarget",
        Luns = new[]
        {
            new AzureNative.StoragePool.Inputs.IscsiLunArgs
            {
                ManagedDiskAzureResourceId = "/subscriptions/11111111-1111-1111-1111-111111111111/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/vm-name_DataDisk_1",
                Name = "lun0",
            },
        },
        ResourceGroupName = "myResourceGroup",
        TargetIqn = "iqn.2005-03.org.iscsi:server1",
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
		_, err := storagepool.NewIscsiTarget(ctx, "iscsiTarget", &storagepool.IscsiTargetArgs{
			AclMode:         pulumi.String("Dynamic"),
			DiskPoolName:    pulumi.String("myDiskPool"),
			IscsiTargetName: pulumi.String("myIscsiTarget"),
			Luns: []storagepool.IscsiLunArgs{
				{
					ManagedDiskAzureResourceId: pulumi.String("/subscriptions/11111111-1111-1111-1111-111111111111/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/vm-name_DataDisk_1"),
					Name:                       pulumi.String("lun0"),
				},
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
			TargetIqn:         pulumi.String("iqn.2005-03.org.iscsi:server1"),
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
import com.pulumi.azurenative.storagepool.IscsiTarget;
import com.pulumi.azurenative.storagepool.IscsiTargetArgs;
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
        var iscsiTarget = new IscsiTarget("iscsiTarget", IscsiTargetArgs.builder()        
            .aclMode("Dynamic")
            .diskPoolName("myDiskPool")
            .iscsiTargetName("myIscsiTarget")
            .luns(Map.ofEntries(
                Map.entry("managedDiskAzureResourceId", "/subscriptions/11111111-1111-1111-1111-111111111111/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/vm-name_DataDisk_1"),
                Map.entry("name", "lun0")
            ))
            .resourceGroupName("myResourceGroup")
            .targetIqn("iqn.2005-03.org.iscsi:server1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const iscsiTarget = new azure_native.storagepool.IscsiTarget("iscsiTarget", {
    aclMode: "Dynamic",
    diskPoolName: "myDiskPool",
    iscsiTargetName: "myIscsiTarget",
    luns: [{
        managedDiskAzureResourceId: "/subscriptions/11111111-1111-1111-1111-111111111111/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/vm-name_DataDisk_1",
        name: "lun0",
    }],
    resourceGroupName: "myResourceGroup",
    targetIqn: "iqn.2005-03.org.iscsi:server1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

iscsi_target = azure_native.storagepool.IscsiTarget("iscsiTarget",
    acl_mode="Dynamic",
    disk_pool_name="myDiskPool",
    iscsi_target_name="myIscsiTarget",
    luns=[azure_native.storagepool.IscsiLunArgs(
        managed_disk_azure_resource_id="/subscriptions/11111111-1111-1111-1111-111111111111/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/vm-name_DataDisk_1",
        name="lun0",
    )],
    resource_group_name="myResourceGroup",
    target_iqn="iqn.2005-03.org.iscsi:server1")

```

```yaml
resources:
  iscsiTarget:
    type: azure-native:storagepool:IscsiTarget
    properties:
      aclMode: Dynamic
      diskPoolName: myDiskPool
      iscsiTargetName: myIscsiTarget
      luns:
        - managedDiskAzureResourceId: /subscriptions/11111111-1111-1111-1111-111111111111/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/vm-name_DataDisk_1
          name: lun0
      resourceGroupName: myResourceGroup
      targetIqn: iqn.2005-03.org.iscsi:server1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:storagepool:IscsiTarget myIscsiTarget /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.StoragePool/diskPools/myDiskPool/iscsiTargets/myIscsiTarget 
```
