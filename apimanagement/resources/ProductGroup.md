Contract details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateProductGroup
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var productGroup = new AzureNative.ApiManagement.ProductGroup("productGroup", new()
    {
        GroupId = "templateGroup",
        ProductId = "testproduct",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
    });

});


```

```go
package main

import (
	apimanagement "github.com/pulumi/pulumi-azure-native-sdk/apimanagement"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := apimanagement.NewProductGroup(ctx, "productGroup", &apimanagement.ProductGroupArgs{
			GroupId:           pulumi.String("templateGroup"),
			ProductId:         pulumi.String("testproduct"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
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
import com.pulumi.azurenative.apimanagement.ProductGroup;
import com.pulumi.azurenative.apimanagement.ProductGroupArgs;
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
        var productGroup = new ProductGroup("productGroup", ProductGroupArgs.builder()        
            .groupId("templateGroup")
            .productId("testproduct")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const productGroup = new azure_native.apimanagement.ProductGroup("productGroup", {
    groupId: "templateGroup",
    productId: "testproduct",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

product_group = azure_native.apimanagement.ProductGroup("productGroup",
    group_id="templateGroup",
    product_id="testproduct",
    resource_group_name="rg1",
    service_name="apimService1")

```

```yaml
resources:
  productGroup:
    type: azure-native:apimanagement:ProductGroup
    properties:
      groupId: templateGroup
      productId: testproduct
      resourceGroupName: rg1
      serviceName: apimService1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:ProductGroup templateGroup /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/groups/templateGroup 
```
