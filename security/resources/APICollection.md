An API collection as represented by Defender for APIs.
API Version: 2022-11-20-preview.

{{% examples %}}
## Example Usage
{{% example %}}
### Onboard an Azure API Management API to Defender for APIs
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var apiCollection = new AzureNative.Security.APICollection("apiCollection", new()
    {
        ApiCollectionId = "echo-api",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
    });

});


```

```go
package main

import (
	security "github.com/pulumi/pulumi-azure-native-sdk/security"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := security.NewAPICollection(ctx, "apiCollection", &security.APICollectionArgs{
			ApiCollectionId:   pulumi.String("echo-api"),
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
import com.pulumi.azurenative.security.APICollection;
import com.pulumi.azurenative.security.APICollectionArgs;
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
        var apiCollection = new APICollection("apiCollection", APICollectionArgs.builder()        
            .apiCollectionId("echo-api")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const apiCollection = new azure_native.security.APICollection("apiCollection", {
    apiCollectionId: "echo-api",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api_collection = azure_native.security.APICollection("apiCollection",
    api_collection_id="echo-api",
    resource_group_name="rg1",
    service_name="apimService1")

```

```yaml
resources:
  apiCollection:
    type: azure-native:security:APICollection
    properties:
      apiCollectionId: echo-api
      resourceGroupName: rg1
      serviceName: apimService1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:security:APICollection echo-api /subscriptions/3fa85f64-5717-4562-b3fc-2c963f66afa6/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/providers/Microsoft.Security/apiCollections/echo-api 
```
