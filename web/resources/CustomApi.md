A custom API
API Version: 2016-06-01.
Previous API Version: 2016-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Replace a custom API
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var customApi = new AzureNative.Web.CustomApi("customApi", new()
    {
        ApiName = "testCustomApi",
        Properties = new AzureNative.Web.Inputs.CustomApiPropertiesDefinitionArgs
        {
            ApiDefinitions = new AzureNative.Web.Inputs.ApiResourceDefinitionsArgs
            {
                OriginalSwaggerUrl = "https://tempuri.org/swagger.json",
            },
            ApiType = "Rest",
            Capabilities = new[] {},
            Description = "",
            DisplayName = "testCustomApi",
            IconUri = "/testIcon.svg",
        },
        ResourceGroupName = "testResourceGroup",
    });

});


```

```go
package main

import (
	web "github.com/pulumi/pulumi-azure-native-sdk/web"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := web.NewCustomApi(ctx, "customApi", &web.CustomApiArgs{
			ApiName: pulumi.String("testCustomApi"),
			Properties: web.CustomApiPropertiesDefinitionResponse{
				ApiDefinitions: &web.ApiResourceDefinitionsArgs{
					OriginalSwaggerUrl: pulumi.String("https://tempuri.org/swagger.json"),
				},
				ApiType:      pulumi.String("Rest"),
				Capabilities: pulumi.StringArray{},
				Description:  pulumi.String(""),
				DisplayName:  pulumi.String("testCustomApi"),
				IconUri:      pulumi.String("/testIcon.svg"),
			},
			ResourceGroupName: pulumi.String("testResourceGroup"),
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
import com.pulumi.azurenative.web.CustomApi;
import com.pulumi.azurenative.web.CustomApiArgs;
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
        var customApi = new CustomApi("customApi", CustomApiArgs.builder()        
            .apiName("testCustomApi")
            .properties(Map.ofEntries(
                Map.entry("apiDefinitions", Map.of("originalSwaggerUrl", "https://tempuri.org/swagger.json")),
                Map.entry("apiType", "Rest"),
                Map.entry("capabilities", ),
                Map.entry("description", ""),
                Map.entry("displayName", "testCustomApi"),
                Map.entry("iconUri", "/testIcon.svg")
            ))
            .resourceGroupName("testResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const customApi = new azure_native.web.CustomApi("customApi", {
    apiName: "testCustomApi",
    properties: {
        apiDefinitions: {
            originalSwaggerUrl: "https://tempuri.org/swagger.json",
        },
        apiType: "Rest",
        capabilities: [],
        description: "",
        displayName: "testCustomApi",
        iconUri: "/testIcon.svg",
    },
    resourceGroupName: "testResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

custom_api = azure_native.web.CustomApi("customApi",
    api_name="testCustomApi",
    properties=azure_native.web.CustomApiPropertiesDefinitionResponseArgs(
        api_definitions=azure_native.web.ApiResourceDefinitionsArgs(
            original_swagger_url="https://tempuri.org/swagger.json",
        ),
        api_type="Rest",
        capabilities=[],
        description="",
        display_name="testCustomApi",
        icon_uri="/testIcon.svg",
    ),
    resource_group_name="testResourceGroup")

```

```yaml
resources:
  customApi:
    type: azure-native:web:CustomApi
    properties:
      apiName: testCustomApi
      properties:
        apiDefinitions:
          originalSwaggerUrl: https://tempuri.org/swagger.json
        apiType: Rest
        capabilities: []
        description:
        displayName: testCustomApi
        iconUri: /testIcon.svg
      resourceGroupName: testResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:web:CustomApi testCustomApi /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testResourceGroup/providers/Microsoft.Web/customApis/testCustomApi 
```
