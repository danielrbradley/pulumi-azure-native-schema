A Disk.
API Version: 2018-09-15.
Previous API Version: 2018-09-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Disks_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var disk = new AzureNative.DevTestLab.Disk("disk", new()
    {
        DiskSizeGiB = 1023,
        DiskType = "Standard",
        LabName = "{labName}",
        LeasedByLabVmId = "/subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}/virtualmachines/vmName",
        Name = "{diskName}",
        ResourceGroupName = "resourceGroupName",
        UserName = "{userId}",
    });

});


```

```go
package main

import (
	devtestlab "github.com/pulumi/pulumi-azure-native-sdk/devtestlab"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := devtestlab.NewDisk(ctx, "disk", &devtestlab.DiskArgs{
			DiskSizeGiB:       pulumi.Int(1023),
			DiskType:          pulumi.String("Standard"),
			LabName:           pulumi.String("{labName}"),
			LeasedByLabVmId:   pulumi.String("/subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}/virtualmachines/vmName"),
			Name:              pulumi.String("{diskName}"),
			ResourceGroupName: pulumi.String("resourceGroupName"),
			UserName:          pulumi.String("{userId}"),
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
import com.pulumi.azurenative.devtestlab.Disk;
import com.pulumi.azurenative.devtestlab.DiskArgs;
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
        var disk = new Disk("disk", DiskArgs.builder()        
            .diskSizeGiB(1023)
            .diskType("Standard")
            .labName("{labName}")
            .leasedByLabVmId("/subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}/virtualmachines/vmName")
            .name("{diskName}")
            .resourceGroupName("resourceGroupName")
            .userName("{userId}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const disk = new azure_native.devtestlab.Disk("disk", {
    diskSizeGiB: 1023,
    diskType: "Standard",
    labName: "{labName}",
    leasedByLabVmId: "/subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}/virtualmachines/vmName",
    name: "{diskName}",
    resourceGroupName: "resourceGroupName",
    userName: "{userId}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

disk = azure_native.devtestlab.Disk("disk",
    disk_size_gi_b=1023,
    disk_type="Standard",
    lab_name="{labName}",
    leased_by_lab_vm_id="/subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}/virtualmachines/vmName",
    name="{diskName}",
    resource_group_name="resourceGroupName",
    user_name="{userId}")

```

```yaml
resources:
  disk:
    type: azure-native:devtestlab:Disk
    properties:
      diskSizeGiB: 1023
      diskType: Standard
      labName: '{labName}'
      leasedByLabVmId: /subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}/virtualmachines/vmName
      name: '{diskName}'
      resourceGroupName: resourceGroupName
      userName: '{userId}'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devtestlab:Disk {diskName} /subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/l{labName}/users/{userId}/disks/{diskName} 
```
