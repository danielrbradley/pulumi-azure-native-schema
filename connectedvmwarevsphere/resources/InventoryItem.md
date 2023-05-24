Defines the inventory item.
API Version: 2022-07-15-preview.
Previous API Version: 2020-10-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreateInventoryItem
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var inventoryItem = new AzureNative.ConnectedVMwarevSphere.InventoryItem("inventoryItem", new()
    {
        InventoryItemName = "testItem",
        InventoryType = "ResourcePool",
        ResourceGroupName = "testrg",
        VcenterName = "ContosoVCenter",
    });

});


```

```go
package main

import (
	connectedvmwarevsphere "github.com/pulumi/pulumi-azure-native-sdk/connectedvmwarevsphere"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := connectedvmwarevsphere.NewInventoryItem(ctx, "inventoryItem", &connectedvmwarevsphere.InventoryItemArgs{
			InventoryItemName: pulumi.String("testItem"),
			InventoryType:     pulumi.String("ResourcePool"),
			ResourceGroupName: pulumi.String("testrg"),
			VcenterName:       pulumi.String("ContosoVCenter"),
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
import com.pulumi.azurenative.connectedvmwarevsphere.InventoryItem;
import com.pulumi.azurenative.connectedvmwarevsphere.InventoryItemArgs;
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
        var inventoryItem = new InventoryItem("inventoryItem", InventoryItemArgs.builder()        
            .inventoryItemName("testItem")
            .inventoryType("ResourcePool")
            .resourceGroupName("testrg")
            .vcenterName("ContosoVCenter")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const inventoryItem = new azure_native.connectedvmwarevsphere.InventoryItem("inventoryItem", {
    inventoryItemName: "testItem",
    inventoryType: "ResourcePool",
    resourceGroupName: "testrg",
    vcenterName: "ContosoVCenter",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

inventory_item = azure_native.connectedvmwarevsphere.InventoryItem("inventoryItem",
    inventory_item_name="testItem",
    inventory_type="ResourcePool",
    resource_group_name="testrg",
    vcenter_name="ContosoVCenter")

```

```yaml
resources:
  inventoryItem:
    type: azure-native:connectedvmwarevsphere:InventoryItem
    properties:
      inventoryItemName: testItem
      inventoryType: ResourcePool
      resourceGroupName: testrg
      vcenterName: ContosoVCenter

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:connectedvmwarevsphere:InventoryItem testItem /subscriptions/fd3c3665-1729-4b7b-9a38-238e83b0f98b/resourceGroups/testrg/providers/Microsoft.ConnectedVMwarevSphere/VCenters/ContosoVCenter/InventoryItems/testItem 
```
