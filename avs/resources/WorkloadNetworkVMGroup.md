NSX VM Group
API Version: 2022-05-01.
Previous API Version: 2020-07-17-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### WorkloadNetworks_CreateVMGroup
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var workloadNetworkVMGroup = new AzureNative.AVS.WorkloadNetworkVMGroup("workloadNetworkVMGroup", new()
    {
        DisplayName = "vmGroup1",
        Members = new[]
        {
            "564d43da-fefc-2a3b-1d92-42855622fa50",
        },
        PrivateCloudName = "cloud1",
        ResourceGroupName = "group1",
        Revision = 1,
        VmGroupId = "vmGroup1",
    });

});


```

```go
package main

import (
	avs "github.com/pulumi/pulumi-azure-native-sdk/avs"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := avs.NewWorkloadNetworkVMGroup(ctx, "workloadNetworkVMGroup", &avs.WorkloadNetworkVMGroupArgs{
			DisplayName: pulumi.String("vmGroup1"),
			Members: pulumi.StringArray{
				pulumi.String("564d43da-fefc-2a3b-1d92-42855622fa50"),
			},
			PrivateCloudName:  pulumi.String("cloud1"),
			ResourceGroupName: pulumi.String("group1"),
			Revision:          pulumi.Float64(1),
			VmGroupId:         pulumi.String("vmGroup1"),
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
import com.pulumi.azurenative.avs.WorkloadNetworkVMGroup;
import com.pulumi.azurenative.avs.WorkloadNetworkVMGroupArgs;
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
        var workloadNetworkVMGroup = new WorkloadNetworkVMGroup("workloadNetworkVMGroup", WorkloadNetworkVMGroupArgs.builder()        
            .displayName("vmGroup1")
            .members("564d43da-fefc-2a3b-1d92-42855622fa50")
            .privateCloudName("cloud1")
            .resourceGroupName("group1")
            .revision(1)
            .vmGroupId("vmGroup1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const workloadNetworkVMGroup = new azure_native.avs.WorkloadNetworkVMGroup("workloadNetworkVMGroup", {
    displayName: "vmGroup1",
    members: ["564d43da-fefc-2a3b-1d92-42855622fa50"],
    privateCloudName: "cloud1",
    resourceGroupName: "group1",
    revision: 1,
    vmGroupId: "vmGroup1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

workload_network_vm_group = azure_native.avs.WorkloadNetworkVMGroup("workloadNetworkVMGroup",
    display_name="vmGroup1",
    members=["564d43da-fefc-2a3b-1d92-42855622fa50"],
    private_cloud_name="cloud1",
    resource_group_name="group1",
    revision=1,
    vm_group_id="vmGroup1")

```

```yaml
resources:
  workloadNetworkVMGroup:
    type: azure-native:avs:WorkloadNetworkVMGroup
    properties:
      displayName: vmGroup1
      members:
        - 564d43da-fefc-2a3b-1d92-42855622fa50
      privateCloudName: cloud1
      resourceGroupName: group1
      revision: 1
      vmGroupId: vmGroup1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:avs:WorkloadNetworkVMGroup vmGroup1 /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/group1/providers/Microsoft.AVS/privateClouds/cloud1/workloadNetworks/default/vmGroups/vmGroup1 
```
