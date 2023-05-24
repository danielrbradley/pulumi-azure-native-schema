An device group resource belonging to a product resource.
API Version: 2022-09-01-preview.
Previous API Version: 2022-09-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### DeviceGroups_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var deviceGroup = new AzureNative.AzureSphere.DeviceGroup("deviceGroup", new()
    {
        CatalogName = "MyCatalog1",
        Description = "Description for MyDeviceGroup1",
        DeviceGroupName = "MyDeviceGroup1",
        OsFeedType = "Retail",
        ProductName = "MyProduct1",
        ResourceGroupName = "MyResourceGroup1",
        UpdatePolicy = "UpdateAll",
    });

});


```

```go
package main

import (
	azuresphere "github.com/pulumi/pulumi-azure-native-sdk/azuresphere"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := azuresphere.NewDeviceGroup(ctx, "deviceGroup", &azuresphere.DeviceGroupArgs{
			CatalogName:       pulumi.String("MyCatalog1"),
			Description:       pulumi.String("Description for MyDeviceGroup1"),
			DeviceGroupName:   pulumi.String("MyDeviceGroup1"),
			OsFeedType:        pulumi.String("Retail"),
			ProductName:       pulumi.String("MyProduct1"),
			ResourceGroupName: pulumi.String("MyResourceGroup1"),
			UpdatePolicy:      pulumi.String("UpdateAll"),
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
import com.pulumi.azurenative.azuresphere.DeviceGroup;
import com.pulumi.azurenative.azuresphere.DeviceGroupArgs;
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
        var deviceGroup = new DeviceGroup("deviceGroup", DeviceGroupArgs.builder()        
            .catalogName("MyCatalog1")
            .description("Description for MyDeviceGroup1")
            .deviceGroupName("MyDeviceGroup1")
            .osFeedType("Retail")
            .productName("MyProduct1")
            .resourceGroupName("MyResourceGroup1")
            .updatePolicy("UpdateAll")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const deviceGroup = new azure_native.azuresphere.DeviceGroup("deviceGroup", {
    catalogName: "MyCatalog1",
    description: "Description for MyDeviceGroup1",
    deviceGroupName: "MyDeviceGroup1",
    osFeedType: "Retail",
    productName: "MyProduct1",
    resourceGroupName: "MyResourceGroup1",
    updatePolicy: "UpdateAll",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

device_group = azure_native.azuresphere.DeviceGroup("deviceGroup",
    catalog_name="MyCatalog1",
    description="Description for MyDeviceGroup1",
    device_group_name="MyDeviceGroup1",
    os_feed_type="Retail",
    product_name="MyProduct1",
    resource_group_name="MyResourceGroup1",
    update_policy="UpdateAll")

```

```yaml
resources:
  deviceGroup:
    type: azure-native:azuresphere:DeviceGroup
    properties:
      catalogName: MyCatalog1
      description: Description for MyDeviceGroup1
      deviceGroupName: MyDeviceGroup1
      osFeedType: Retail
      productName: MyProduct1
      resourceGroupName: MyResourceGroup1
      updatePolicy: UpdateAll

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:azuresphere:DeviceGroup MyDeviceId1 /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MyResourceGroup1/providers/Microsoft.AzureSphere/catalogs/MyCatalog1/products/myProduct1/deviceGroups/myDeviceGroup1 
```
