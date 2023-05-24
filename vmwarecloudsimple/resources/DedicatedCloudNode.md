Dedicated cloud node model
API Version: 2019-04-01.
Previous API Version: 2019-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateDedicatedCloudNode
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var dedicatedCloudNode = new AzureNative.VMwareCloudSimple.DedicatedCloudNode("dedicatedCloudNode", new()
    {
        AvailabilityZoneId = "az1",
        DedicatedCloudNodeName = "myNode",
        Id = "general",
        Location = "westus",
        Name = "CS28-Node",
        NodesCount = 1,
        PlacementGroupId = "n1",
        PurchaseId = "56acbd46-3d36-4bbf-9b08-57c30fdf6932",
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.VMwareCloudSimple.Inputs.SkuArgs
        {
            Name = "VMware_CloudSimple_CS28",
        },
    });

});


```

```go
package main

import (
	vmwarecloudsimple "github.com/pulumi/pulumi-azure-native-sdk/vmwarecloudsimple"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := vmwarecloudsimple.NewDedicatedCloudNode(ctx, "dedicatedCloudNode", &vmwarecloudsimple.DedicatedCloudNodeArgs{
			AvailabilityZoneId:     pulumi.String("az1"),
			DedicatedCloudNodeName: pulumi.String("myNode"),
			Id:                     pulumi.String("general"),
			Location:               pulumi.String("westus"),
			Name:                   pulumi.String("CS28-Node"),
			NodesCount:             pulumi.Int(1),
			PlacementGroupId:       pulumi.String("n1"),
			PurchaseId:             pulumi.String("56acbd46-3d36-4bbf-9b08-57c30fdf6932"),
			ResourceGroupName:      pulumi.String("myResourceGroup"),
			Sku: &vmwarecloudsimple.SkuArgs{
				Name: pulumi.String("VMware_CloudSimple_CS28"),
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
import com.pulumi.azurenative.vmwarecloudsimple.DedicatedCloudNode;
import com.pulumi.azurenative.vmwarecloudsimple.DedicatedCloudNodeArgs;
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
        var dedicatedCloudNode = new DedicatedCloudNode("dedicatedCloudNode", DedicatedCloudNodeArgs.builder()        
            .availabilityZoneId("az1")
            .dedicatedCloudNodeName("myNode")
            .id("general")
            .location("westus")
            .name("CS28-Node")
            .nodesCount(1)
            .placementGroupId("n1")
            .purchaseId("56acbd46-3d36-4bbf-9b08-57c30fdf6932")
            .resourceGroupName("myResourceGroup")
            .sku(Map.of("name", "VMware_CloudSimple_CS28"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const dedicatedCloudNode = new azure_native.vmwarecloudsimple.DedicatedCloudNode("dedicatedCloudNode", {
    availabilityZoneId: "az1",
    dedicatedCloudNodeName: "myNode",
    id: "general",
    location: "westus",
    name: "CS28-Node",
    nodesCount: 1,
    placementGroupId: "n1",
    purchaseId: "56acbd46-3d36-4bbf-9b08-57c30fdf6932",
    resourceGroupName: "myResourceGroup",
    sku: {
        name: "VMware_CloudSimple_CS28",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

dedicated_cloud_node = azure_native.vmwarecloudsimple.DedicatedCloudNode("dedicatedCloudNode",
    availability_zone_id="az1",
    dedicated_cloud_node_name="myNode",
    id="general",
    location="westus",
    name="CS28-Node",
    nodes_count=1,
    placement_group_id="n1",
    purchase_id="56acbd46-3d36-4bbf-9b08-57c30fdf6932",
    resource_group_name="myResourceGroup",
    sku=azure_native.vmwarecloudsimple.SkuArgs(
        name="VMware_CloudSimple_CS28",
    ))

```

```yaml
resources:
  dedicatedCloudNode:
    type: azure-native:vmwarecloudsimple:DedicatedCloudNode
    properties:
      availabilityZoneId: az1
      dedicatedCloudNodeName: myNode
      id: general
      location: westus
      name: CS28-Node
      nodesCount: 1
      placementGroupId: n1
      purchaseId: 56acbd46-3d36-4bbf-9b08-57c30fdf6932
      resourceGroupName: myResourceGroup
      sku:
        name: VMware_CloudSimple_CS28

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:vmwarecloudsimple:DedicatedCloudNode myNode /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.VMwareCloudSimple/dedicatedCloudNodes/myNode 
```
