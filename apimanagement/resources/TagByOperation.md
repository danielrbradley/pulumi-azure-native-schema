Tag Contract details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateApiOperationTag
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var tagByOperation = new AzureNative.ApiManagement.TagByOperation("tagByOperation", new()
    {
        ApiId = "5931a75ae4bbd512a88c680b",
        OperationId = "5931a75ae4bbd512a88c680a",
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
		_, err := apimanagement.NewTagByOperation(ctx, "tagByOperation", &apimanagement.TagByOperationArgs{
			ApiId:             pulumi.String("5931a75ae4bbd512a88c680b"),
			OperationId:       pulumi.String("5931a75ae4bbd512a88c680a"),
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
import com.pulumi.azurenative.apimanagement.TagByOperation;
import com.pulumi.azurenative.apimanagement.TagByOperationArgs;
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
        var tagByOperation = new TagByOperation("tagByOperation", TagByOperationArgs.builder()        
            .apiId("5931a75ae4bbd512a88c680b")
            .operationId("5931a75ae4bbd512a88c680a")
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

const tagByOperation = new azure_native.apimanagement.TagByOperation("tagByOperation", {
    apiId: "5931a75ae4bbd512a88c680b",
    operationId: "5931a75ae4bbd512a88c680a",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    tagId: "tagId1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

tag_by_operation = azure_native.apimanagement.TagByOperation("tagByOperation",
    api_id="5931a75ae4bbd512a88c680b",
    operation_id="5931a75ae4bbd512a88c680a",
    resource_group_name="rg1",
    service_name="apimService1",
    tag_id="tagId1")

```

```yaml
resources:
  tagByOperation:
    type: azure-native:apimanagement:TagByOperation
    properties:
      apiId: 5931a75ae4bbd512a88c680b
      operationId: 5931a75ae4bbd512a88c680a
      resourceGroupName: rg1
      serviceName: apimService1
      tagId: tagId1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:TagByOperation tagId1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/tags/tagId1 
```
