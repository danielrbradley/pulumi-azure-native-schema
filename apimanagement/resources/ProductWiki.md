Wiki properties
API Version: 2022-08-01.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateProductWiki
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var productWiki = new AzureNative.ApiManagement.ProductWiki("productWiki", new()
    {
        Documents = new[]
        {
            new AzureNative.ApiManagement.Inputs.WikiDocumentationContractArgs
            {
                DocumentationId = "docId1",
            },
            new AzureNative.ApiManagement.Inputs.WikiDocumentationContractArgs
            {
                DocumentationId = "docId2",
            },
        },
        ProductId = "57d1f7558aa04f15146d9d8a",
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
		_, err := apimanagement.NewProductWiki(ctx, "productWiki", &apimanagement.ProductWikiArgs{
			Documents: []apimanagement.WikiDocumentationContractArgs{
				{
					DocumentationId: pulumi.String("docId1"),
				},
				{
					DocumentationId: pulumi.String("docId2"),
				},
			},
			ProductId:         pulumi.String("57d1f7558aa04f15146d9d8a"),
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
import com.pulumi.azurenative.apimanagement.ProductWiki;
import com.pulumi.azurenative.apimanagement.ProductWikiArgs;
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
        var productWiki = new ProductWiki("productWiki", ProductWikiArgs.builder()        
            .documents(            
                Map.of("documentationId", "docId1"),
                Map.of("documentationId", "docId2"))
            .productId("57d1f7558aa04f15146d9d8a")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const productWiki = new azure_native.apimanagement.ProductWiki("productWiki", {
    documents: [
        {
            documentationId: "docId1",
        },
        {
            documentationId: "docId2",
        },
    ],
    productId: "57d1f7558aa04f15146d9d8a",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

product_wiki = azure_native.apimanagement.ProductWiki("productWiki",
    documents=[
        azure_native.apimanagement.WikiDocumentationContractArgs(
            documentation_id="docId1",
        ),
        azure_native.apimanagement.WikiDocumentationContractArgs(
            documentation_id="docId2",
        ),
    ],
    product_id="57d1f7558aa04f15146d9d8a",
    resource_group_name="rg1",
    service_name="apimService1")

```

```yaml
resources:
  productWiki:
    type: azure-native:apimanagement:ProductWiki
    properties:
      documents:
        - documentationId: docId1
        - documentationId: docId2
      productId: 57d1f7558aa04f15146d9d8a
      resourceGroupName: rg1
      serviceName: apimService1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:ProductWiki default /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/products/57d1f7558aa04f15146d9d8a/wikis/default 
```
