An deployment resource belonging to a device group resource.
API Version: 2022-09-01-preview.
Previous API Version: 2022-09-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Deployments_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var deployment = new AzureNative.AzureSphere.Deployment("deployment", new()
    {
        CatalogName = "MyCatalog1",
        DeploymentName = "MyDeployment1",
        DeviceGroupName = "myDeviceGroup1",
        ProductName = "MyProduct1",
        ResourceGroupName = "MyResourceGroup1",
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
		_, err := azuresphere.NewDeployment(ctx, "deployment", &azuresphere.DeploymentArgs{
			CatalogName:       pulumi.String("MyCatalog1"),
			DeploymentName:    pulumi.String("MyDeployment1"),
			DeviceGroupName:   pulumi.String("myDeviceGroup1"),
			ProductName:       pulumi.String("MyProduct1"),
			ResourceGroupName: pulumi.String("MyResourceGroup1"),
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
import com.pulumi.azurenative.azuresphere.Deployment;
import com.pulumi.azurenative.azuresphere.DeploymentArgs;
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
        var deployment = new Deployment("deployment", DeploymentArgs.builder()        
            .catalogName("MyCatalog1")
            .deploymentName("MyDeployment1")
            .deviceGroupName("myDeviceGroup1")
            .productName("MyProduct1")
            .resourceGroupName("MyResourceGroup1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const deployment = new azure_native.azuresphere.Deployment("deployment", {
    catalogName: "MyCatalog1",
    deploymentName: "MyDeployment1",
    deviceGroupName: "myDeviceGroup1",
    productName: "MyProduct1",
    resourceGroupName: "MyResourceGroup1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

deployment = azure_native.azuresphere.Deployment("deployment",
    catalog_name="MyCatalog1",
    deployment_name="MyDeployment1",
    device_group_name="myDeviceGroup1",
    product_name="MyProduct1",
    resource_group_name="MyResourceGroup1")

```

```yaml
resources:
  deployment:
    type: azure-native:azuresphere:Deployment
    properties:
      catalogName: MyCatalog1
      deploymentName: MyDeployment1
      deviceGroupName: myDeviceGroup1
      productName: MyProduct1
      resourceGroupName: MyResourceGroup1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:azuresphere:Deployment MyDeployment1 /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MyResourceGroup1/providers/Microsoft.AzureSphere/catalogs/MyCatalog1/products/MyProduct1/deviceGroups/MyDeviceGroup1/deployments/MyDeployment1 
```
