Markdown documentation details.
API Version: 2022-08-01.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateDocumentation
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var documentation = new AzureNative.ApiManagement.Documentation("documentation", new()
    {
        Content = "content",
        DocumentationId = "57d1f7558aa04f15146d9d8a",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        Title = "Title",
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
		_, err := apimanagement.NewDocumentation(ctx, "documentation", &apimanagement.DocumentationArgs{
			Content:           pulumi.String("content"),
			DocumentationId:   pulumi.String("57d1f7558aa04f15146d9d8a"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			Title:             pulumi.String("Title"),
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
import com.pulumi.azurenative.apimanagement.Documentation;
import com.pulumi.azurenative.apimanagement.DocumentationArgs;
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
        var documentation = new Documentation("documentation", DocumentationArgs.builder()        
            .content("content")
            .documentationId("57d1f7558aa04f15146d9d8a")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .title("Title")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const documentation = new azure_native.apimanagement.Documentation("documentation", {
    content: "content",
    documentationId: "57d1f7558aa04f15146d9d8a",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    title: "Title",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

documentation = azure_native.apimanagement.Documentation("documentation",
    content="content",
    documentation_id="57d1f7558aa04f15146d9d8a",
    resource_group_name="rg1",
    service_name="apimService1",
    title="Title")

```

```yaml
resources:
  documentation:
    type: azure-native:apimanagement:Documentation
    properties:
      content: content
      documentationId: 57d1f7558aa04f15146d9d8a
      resourceGroupName: rg1
      serviceName: apimService1
      title: Title

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:Documentation 57d1f7558aa04f15146d9d8a /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/documentations/57d1f7558aa04f15146d9d8a 
```
