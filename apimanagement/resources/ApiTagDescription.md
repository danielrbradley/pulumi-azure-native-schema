Contract details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateApiTagDescription
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var apiTagDescription = new AzureNative.ApiManagement.ApiTagDescription("apiTagDescription", new()
    {
        ApiId = "5931a75ae4bbd512a88c680b",
        Description = "Some description that will be displayed for operation's tag if the tag is assigned to operation of the API",
        ExternalDocsDescription = "Description of the external docs resource",
        ExternalDocsUrl = "http://some.url/additionaldoc",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        TagDescriptionId = "tagId1",
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
		_, err := apimanagement.NewApiTagDescription(ctx, "apiTagDescription", &apimanagement.ApiTagDescriptionArgs{
			ApiId:                   pulumi.String("5931a75ae4bbd512a88c680b"),
			Description:             pulumi.String("Some description that will be displayed for operation's tag if the tag is assigned to operation of the API"),
			ExternalDocsDescription: pulumi.String("Description of the external docs resource"),
			ExternalDocsUrl:         pulumi.String("http://some.url/additionaldoc"),
			ResourceGroupName:       pulumi.String("rg1"),
			ServiceName:             pulumi.String("apimService1"),
			TagDescriptionId:        pulumi.String("tagId1"),
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
import com.pulumi.azurenative.apimanagement.ApiTagDescription;
import com.pulumi.azurenative.apimanagement.ApiTagDescriptionArgs;
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
        var apiTagDescription = new ApiTagDescription("apiTagDescription", ApiTagDescriptionArgs.builder()        
            .apiId("5931a75ae4bbd512a88c680b")
            .description("Some description that will be displayed for operation's tag if the tag is assigned to operation of the API")
            .externalDocsDescription("Description of the external docs resource")
            .externalDocsUrl("http://some.url/additionaldoc")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .tagDescriptionId("tagId1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const apiTagDescription = new azure_native.apimanagement.ApiTagDescription("apiTagDescription", {
    apiId: "5931a75ae4bbd512a88c680b",
    description: "Some description that will be displayed for operation's tag if the tag is assigned to operation of the API",
    externalDocsDescription: "Description of the external docs resource",
    externalDocsUrl: "http://some.url/additionaldoc",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    tagDescriptionId: "tagId1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api_tag_description = azure_native.apimanagement.ApiTagDescription("apiTagDescription",
    api_id="5931a75ae4bbd512a88c680b",
    description="Some description that will be displayed for operation's tag if the tag is assigned to operation of the API",
    external_docs_description="Description of the external docs resource",
    external_docs_url="http://some.url/additionaldoc",
    resource_group_name="rg1",
    service_name="apimService1",
    tag_description_id="tagId1")

```

```yaml
resources:
  apiTagDescription:
    type: azure-native:apimanagement:ApiTagDescription
    properties:
      apiId: 5931a75ae4bbd512a88c680b
      description: Some description that will be displayed for operation's tag if the tag is assigned to operation of the API
      externalDocsDescription: Description of the external docs resource
      externalDocsUrl: http://some.url/additionaldoc
      resourceGroupName: rg1
      serviceName: apimService1
      tagDescriptionId: tagId1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:ApiTagDescription tagId1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/apis/5931a75ae4bbd512a88c680b/tagDescriptions/tagId1 
```
