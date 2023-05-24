Defines the inventory item.
API Version: 2020-06-05-preview.
Previous API Version: 2020-06-05-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

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
    var inventoryItem = new AzureNative.ScVmm.InventoryItem("inventoryItem", new()
    {
        InventoryItemName = "12345678-1234-1234-1234-123456789abc",
        InventoryType = "Cloud",
        ResourceGroupName = "testrg",
        VmmServerName = "ContosoVMMServer",
    });

});


```

```go
package main

import (
	scvmm "github.com/pulumi/pulumi-azure-native-sdk/scvmm"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := scvmm.NewInventoryItem(ctx, "inventoryItem", &scvmm.InventoryItemArgs{
			InventoryItemName: pulumi.String("12345678-1234-1234-1234-123456789abc"),
			InventoryType:     pulumi.String("Cloud"),
			ResourceGroupName: pulumi.String("testrg"),
			VmmServerName:     pulumi.String("ContosoVMMServer"),
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
import com.pulumi.azurenative.scvmm.InventoryItem;
import com.pulumi.azurenative.scvmm.InventoryItemArgs;
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
            .inventoryItemName("12345678-1234-1234-1234-123456789abc")
            .inventoryType("Cloud")
            .resourceGroupName("testrg")
            .vmmServerName("ContosoVMMServer")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const inventoryItem = new azure_native.scvmm.InventoryItem("inventoryItem", {
    inventoryItemName: "12345678-1234-1234-1234-123456789abc",
    inventoryType: "Cloud",
    resourceGroupName: "testrg",
    vmmServerName: "ContosoVMMServer",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

inventory_item = azure_native.scvmm.InventoryItem("inventoryItem",
    inventory_item_name="12345678-1234-1234-1234-123456789abc",
    inventory_type="Cloud",
    resource_group_name="testrg",
    vmm_server_name="ContosoVMMServer")

```

```yaml
resources:
  inventoryItem:
    type: azure-native:scvmm:InventoryItem
    properties:
      inventoryItemName: 12345678-1234-1234-1234-123456789abc
      inventoryType: Cloud
      resourceGroupName: testrg
      vmmServerName: ContosoVMMServer

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:scvmm:InventoryItem 12345678-1234-1234-1234-123456789abc /subscriptions/fd3c3665-1729-4b7b-9a38-238e83b0f98b/resourceGroups/testrg/providers/Microsoft.SCVMM/VMMServers/ContosoVMMServer/InventoryItems/12345678-1234-1234-1234-123456789abc 
```
