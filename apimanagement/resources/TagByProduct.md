Tag Contract details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateProductTag
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var tagByProduct = new AzureNative.ApiManagement.TagByProduct("tagByProduct", new()
    {
        ProductId = "5931a75ae4bbd512a88c680b",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        TagId = "tagId1",
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
		_, err := apimanagement.NewTagByProduct(ctx, "tagByProduct", &apimanagement.TagByProductArgs{
			ProductId:         pulumi.String("5931a75ae4bbd512a88c680b"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			TagId:             pulumi.String("tagId1"),
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
import com.pulumi.azurenative.apimanagement.TagByProduct;
import com.pulumi.azurenative.apimanagement.TagByProductArgs;
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
        var tagByProduct = new TagByProduct("tagByProduct", TagByProductArgs.builder()        
            .productId("5931a75ae4bbd512a88c680b")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .tagId("tagId1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const tagByProduct = new azure_native.apimanagement.TagByProduct("tagByProduct", {
    productId: "5931a75ae4bbd512a88c680b",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    tagId: "tagId1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

tag_by_product = azure_native.apimanagement.TagByProduct("tagByProduct",
    product_id="5931a75ae4bbd512a88c680b",
    resource_group_name="rg1",
    service_name="apimService1",
    tag_id="tagId1")

```

```yaml
resources:
  tagByProduct:
    type: azure-native:apimanagement:TagByProduct
    properties:
      productId: 5931a75ae4bbd512a88c680b
      resourceGroupName: rg1
      serviceName: apimService1
      tagId: tagId1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:TagByProduct tagId1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/tags/tagId1 
```
