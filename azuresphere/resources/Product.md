An product resource belonging to a catalog resource.
API Version: 2022-09-01-preview.
Previous API Version: 2022-09-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Products_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var product = new AzureNative.AzureSphere.Product("product", new()
    {
        CatalogName = "MyCatalog1",
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
		_, err := azuresphere.NewProduct(ctx, "product", &azuresphere.ProductArgs{
			CatalogName:       pulumi.String("MyCatalog1"),
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
import com.pulumi.azurenative.azuresphere.Product;
import com.pulumi.azurenative.azuresphere.ProductArgs;
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
        var product = new Product("product", ProductArgs.builder()        
            .catalogName("MyCatalog1")
            .productName("MyProduct1")
            .resourceGroupName("MyResourceGroup1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const product = new azure_native.azuresphere.Product("product", {
    catalogName: "MyCatalog1",
    productName: "MyProduct1",
    resourceGroupName: "MyResourceGroup1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

product = azure_native.azuresphere.Product("product",
    catalog_name="MyCatalog1",
    product_name="MyProduct1",
    resource_group_name="MyResourceGroup1")

```

```yaml
resources:
  product:
    type: azure-native:azuresphere:Product
    properties:
      catalogName: MyCatalog1
      productName: MyProduct1
      resourceGroupName: MyResourceGroup1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:azuresphere:Product MyProduct1 /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/MyResourceGroup1/providers/Microsoft.AzureSphere/catalogs/MyCatalog1/products/MyProduct1 
```
