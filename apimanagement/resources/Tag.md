Tag Contract details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateTag
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var tag = new AzureNative.ApiManagement.Tag("tag", new()
    {
        DisplayName = "tag1",
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
		_, err := apimanagement.NewTag(ctx, "tag", &apimanagement.TagArgs{
			DisplayName:       pulumi.String("tag1"),
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
import com.pulumi.azurenative.apimanagement.Tag;
import com.pulumi.azurenative.apimanagement.TagArgs;
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
        var tag = new Tag("tag", TagArgs.builder()        
            .displayName("tag1")
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

const tag = new azure_native.apimanagement.Tag("tag", {
    displayName: "tag1",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    tagId: "tagId1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

tag = azure_native.apimanagement.Tag("tag",
    display_name="tag1",
    resource_group_name="rg1",
    service_name="apimService1",
    tag_id="tagId1")

```

```yaml
resources:
  tag:
    type: azure-native:apimanagement:Tag
    properties:
      displayName: tag1
      resourceGroupName: rg1
      serviceName: apimService1
      tagId: tagId1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:Tag tagId1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/tags/tagId1 
```
