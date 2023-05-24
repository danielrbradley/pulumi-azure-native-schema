Content type contract details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateContentTypeContentItem
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var contentItem = new AzureNative.ApiManagement.ContentItem("contentItem", new()
    {
        ContentItemId = "4e3cf6a5-574a-ba08-1f23-2e7a38faa6d8",
        ContentTypeId = "page",
        Properties = 
        {
            { "en_us", 
            {
                { "description", "Short story about the company." },
                { "documentId", "contentTypes/document/contentItems/4e3cf6a5-574a-ba08-1f23-2e7a38faa6d8" },
                { "keywords", "company, about" },
                { "permalink", "/about" },
                { "title", "About" },
            } },
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
		_, err := apimanagement.NewContentItem(ctx, "contentItem", &apimanagement.ContentItemArgs{
			ContentItemId: pulumi.String("4e3cf6a5-574a-ba08-1f23-2e7a38faa6d8"),
			ContentTypeId: pulumi.String("page"),
			Properties: pulumi.Any{
				En_us: map[string]interface{}{
					"description": "Short story about the company.",
					"documentId":  "contentTypes/document/contentItems/4e3cf6a5-574a-ba08-1f23-2e7a38faa6d8",
					"keywords":    "company, about",
					"permalink":   "/about",
					"title":       "About",
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
import com.pulumi.azurenative.apimanagement.ContentItem;
import com.pulumi.azurenative.apimanagement.ContentItemArgs;
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
        var contentItem = new ContentItem("contentItem", ContentItemArgs.builder()        
            .contentItemId("4e3cf6a5-574a-ba08-1f23-2e7a38faa6d8")
            .contentTypeId("page")
            .properties(Map.of("en_us", Map.ofEntries(
                Map.entry("description", "Short story about the company."),
                Map.entry("documentId", "contentTypes/document/contentItems/4e3cf6a5-574a-ba08-1f23-2e7a38faa6d8"),
                Map.entry("keywords", "company, about"),
                Map.entry("permalink", "/about"),
                Map.entry("title", "About")
            )))
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const contentItem = new azure_native.apimanagement.ContentItem("contentItem", {
    contentItemId: "4e3cf6a5-574a-ba08-1f23-2e7a38faa6d8",
    contentTypeId: "page",
    properties: {
        en_us: {
            description: "Short story about the company.",
            documentId: "contentTypes/document/contentItems/4e3cf6a5-574a-ba08-1f23-2e7a38faa6d8",
            keywords: "company, about",
            permalink: "/about",
            title: "About",
        },
    },
    resourceGroupName: "rg1",
    serviceName: "apimService1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

content_item = azure_native.apimanagement.ContentItem("contentItem",
    content_item_id="4e3cf6a5-574a-ba08-1f23-2e7a38faa6d8",
    content_type_id="page",
    properties={
        "en_us": {
            "description": "Short story about the company.",
            "documentId": "contentTypes/document/contentItems/4e3cf6a5-574a-ba08-1f23-2e7a38faa6d8",
            "keywords": "company, about",
            "permalink": "/about",
            "title": "About",
        },
    },
    resource_group_name="rg1",
    service_name="apimService1")

```

```yaml
resources:
  contentItem:
    type: azure-native:apimanagement:ContentItem
    properties:
      contentItemId: 4e3cf6a5-574a-ba08-1f23-2e7a38faa6d8
      contentTypeId: page
      properties:
        en_us:
          description: Short story about the company.
          documentId: contentTypes/document/contentItems/4e3cf6a5-574a-ba08-1f23-2e7a38faa6d8
          keywords: company, about
          permalink: /about
          title: About
      resourceGroupName: rg1
      serviceName: apimService1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:ContentItem 4e3cf6a5-574a-ba08-1f23-2e7a38faa6d8 /contentTypes/page/contentItems/4e3cf6a5-574a-ba08-1f23-2e7a38faa6d8 
```
