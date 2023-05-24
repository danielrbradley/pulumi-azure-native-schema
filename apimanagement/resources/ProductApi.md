API details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateProductApi
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var productApi = new AzureNative.ApiManagement.ProductApi("productApi", new()
    {
        ApiId = "echo-api",
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
		_, err := apimanagement.NewProductApi(ctx, "productApi", &apimanagement.ProductApiArgs{
			ApiId:             pulumi.String("echo-api"),
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
import com.pulumi.azurenative.apimanagement.ProductApi;
import com.pulumi.azurenative.apimanagement.ProductApiArgs;
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
        var productApi = new ProductApi("productApi", ProductApiArgs.builder()        
            .apiId("echo-api")
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

const productApi = new azure_native.apimanagement.ProductApi("productApi", {
    apiId: "echo-api",
    productId: "testproduct",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

product_api = azure_native.apimanagement.ProductApi("productApi",
    api_id="echo-api",
    product_id="testproduct",
    resource_group_name="rg1",
    service_name="apimService1")

```

```yaml
resources:
  productApi:
    type: azure-native:apimanagement:ProductApi
    properties:
      apiId: echo-api
      productId: testproduct
      resourceGroupName: rg1
      serviceName: apimService1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:ProductApi 5931a75ae4bbd512a88c680b /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apis/5931a75ae4bbd512a88c680b 
```
