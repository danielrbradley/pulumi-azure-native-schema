Wiki properties
API Version: 2022-08-01.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateApiWiki
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var apiWiki = new AzureNative.ApiManagement.ApiWiki("apiWiki", new()
    {
        ApiId = "57d1f7558aa04f15146d9d8a",
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
		_, err := apimanagement.NewApiWiki(ctx, "apiWiki", &apimanagement.ApiWikiArgs{
			ApiId: pulumi.String("57d1f7558aa04f15146d9d8a"),
			Documents: []apimanagement.WikiDocumentationContractArgs{
				{
					DocumentationId: pulumi.String("docId1"),
				},
				{
					DocumentationId: pulumi.String("docId2"),
				},
			},
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
import com.pulumi.azurenative.apimanagement.ApiWiki;
import com.pulumi.azurenative.apimanagement.ApiWikiArgs;
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
        var apiWiki = new ApiWiki("apiWiki", ApiWikiArgs.builder()        
            .apiId("57d1f7558aa04f15146d9d8a")
            .documents(            
                Map.of("documentationId", "docId1"),
                Map.of("documentationId", "docId2"))
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const apiWiki = new azure_native.apimanagement.ApiWiki("apiWiki", {
    apiId: "57d1f7558aa04f15146d9d8a",
    documents: [
        {
            documentationId: "docId1",
        },
        {
            documentationId: "docId2",
        },
    ],
    resourceGroupName: "rg1",
    serviceName: "apimService1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api_wiki = azure_native.apimanagement.ApiWiki("apiWiki",
    api_id="57d1f7558aa04f15146d9d8a",
    documents=[
        azure_native.apimanagement.WikiDocumentationContractArgs(
            documentation_id="docId1",
        ),
        azure_native.apimanagement.WikiDocumentationContractArgs(
            documentation_id="docId2",
        ),
    ],
    resource_group_name="rg1",
    service_name="apimService1")

```

```yaml
resources:
  apiWiki:
    type: azure-native:apimanagement:ApiWiki
    properties:
      apiId: 57d1f7558aa04f15146d9d8a
      documents:
        - documentationId: docId1
        - documentationId: docId2
      resourceGroupName: rg1
      serviceName: apimService1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:ApiWiki default /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apis/57d1f7558aa04f15146d9d8a/wikis/default 
```
