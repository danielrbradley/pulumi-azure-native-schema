Content type contract details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateContentType
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var contentType = new AzureNative.ApiManagement.ContentType("contentType", new()
    {
        ContentTypeId = "page",
        Description = "A regular page",
        Name = "Page",
        ResourceGroupName = "rg1",
        Schema = 
        {
            { "additionalProperties", false },
            { "properties", 
            {
                { "en_us", 
                {
                    { "additionalProperties", false },
                    { "properties", 
                    {
                        { "description", 
                        {
                            { "description", "Page description. This property gets included in SEO attributes." },
                            { "indexed", true },
                            { "title", "Description" },
                            { "type", "string" },
                        } },
                        { "documentId", 
                        {
                            { "description", "Reference to page content document." },
                            { "title", "Document ID" },
                            { "type", "string" },
                        } },
                        { "keywords", 
                        {
                            { "description", "Page keywords. This property gets included in SEO attributes." },
                            { "indexed", true },
                            { "title", "Keywords" },
                            { "type", "string" },
                        } },
                        { "permalink", 
                        {
                            { "description", "Page permalink, e.g. '/about'." },
                            { "indexed", true },
                            { "title", "Permalink" },
                            { "type", "string" },
                        } },
                        { "title", 
                        {
                            { "description", "Page title. This property gets included in SEO attributes." },
                            { "indexed", true },
                            { "title", "Title" },
                            { "type", "string" },
                        } },
                    } },
                    { "required", new[]
                    {
                        "title",
                        "permalink",
                        "documentId",
                    } },
                    { "type", "object" },
                } },
            } },
        },
        ServiceName = "apimService1",
        Version = "1.0.0",
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
		_, err := apimanagement.NewContentType(ctx, "contentType", &apimanagement.ContentTypeArgs{
			ContentTypeId:     pulumi.String("page"),
			Description:       pulumi.String("A regular page"),
			Name:              pulumi.String("Page"),
			ResourceGroupName: pulumi.String("rg1"),
			Schema: pulumi.Any{
				AdditionalProperties: false,
				Properties: map[string]interface{}{
					"en_us": map[string]interface{}{
						"additionalProperties": false,
						"properties": map[string]interface{}{
							"description": map[string]interface{}{
								"description": "Page description. This property gets included in SEO attributes.",
								"indexed":     true,
								"title":       "Description",
								"type":        "string",
							},
							"documentId": map[string]interface{}{
								"description": "Reference to page content document.",
								"title":       "Document ID",
								"type":        "string",
							},
							"keywords": map[string]interface{}{
								"description": "Page keywords. This property gets included in SEO attributes.",
								"indexed":     true,
								"title":       "Keywords",
								"type":        "string",
							},
							"permalink": map[string]interface{}{
								"description": "Page permalink, e.g. '/about'.",
								"indexed":     true,
								"title":       "Permalink",
								"type":        "string",
							},
							"title": map[string]interface{}{
								"description": "Page title. This property gets included in SEO attributes.",
								"indexed":     true,
								"title":       "Title",
								"type":        "string",
							},
						},
						"required": []string{
							"title",
							"permalink",
							"documentId",
						},
						"type": "object",
					},
				},
			},
			ServiceName: pulumi.String("apimService1"),
			Version:     pulumi.String("1.0.0"),
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
import com.pulumi.azurenative.apimanagement.ContentType;
import com.pulumi.azurenative.apimanagement.ContentTypeArgs;
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
        var contentType = new ContentType("contentType", ContentTypeArgs.builder()        
            .contentTypeId("page")
            .description("A regular page")
            .name("Page")
            .resourceGroupName("rg1")
            .schema(Map.ofEntries(
                Map.entry("additionalProperties", false),
                Map.entry("properties", Map.of("en_us", Map.ofEntries(
                    Map.entry("additionalProperties", false),
                    Map.entry("properties", Map.ofEntries(
                        Map.entry("description", Map.ofEntries(
                            Map.entry("description", "Page description. This property gets included in SEO attributes."),
                            Map.entry("indexed", true),
                            Map.entry("title", "Description"),
                            Map.entry("type", "string")
                        )),
                        Map.entry("documentId", Map.ofEntries(
                            Map.entry("description", "Reference to page content document."),
                            Map.entry("title", "Document ID"),
                            Map.entry("type", "string")
                        )),
                        Map.entry("keywords", Map.ofEntries(
                            Map.entry("description", "Page keywords. This property gets included in SEO attributes."),
                            Map.entry("indexed", true),
                            Map.entry("title", "Keywords"),
                            Map.entry("type", "string")
                        )),
                        Map.entry("permalink", Map.ofEntries(
                            Map.entry("description", "Page permalink, e.g. '/about'."),
                            Map.entry("indexed", true),
                            Map.entry("title", "Permalink"),
                            Map.entry("type", "string")
                        )),
                        Map.entry("title", Map.ofEntries(
                            Map.entry("description", "Page title. This property gets included in SEO attributes."),
                            Map.entry("indexed", true),
                            Map.entry("title", "Title"),
                            Map.entry("type", "string")
                        ))
                    )),
                    Map.entry("required",                     
                        "title",
                        "permalink",
                        "documentId"),
                    Map.entry("type", "object")
                )))
            ))
            .serviceName("apimService1")
            .version("1.0.0")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const contentType = new azure_native.apimanagement.ContentType("contentType", {
    contentTypeId: "page",
    description: "A regular page",
    name: "Page",
    resourceGroupName: "rg1",
    schema: {
        additionalProperties: false,
        properties: {
            en_us: {
                additionalProperties: false,
                properties: {
                    description: {
                        description: "Page description. This property gets included in SEO attributes.",
                        indexed: true,
                        title: "Description",
                        type: "string",
                    },
                    documentId: {
                        description: "Reference to page content document.",
                        title: "Document ID",
                        type: "string",
                    },
                    keywords: {
                        description: "Page keywords. This property gets included in SEO attributes.",
                        indexed: true,
                        title: "Keywords",
                        type: "string",
                    },
                    permalink: {
                        description: "Page permalink, e.g. '/about'.",
                        indexed: true,
                        title: "Permalink",
                        type: "string",
                    },
                    title: {
                        description: "Page title. This property gets included in SEO attributes.",
                        indexed: true,
                        title: "Title",
                        type: "string",
                    },
                },
                required: [
                    "title",
                    "permalink",
                    "documentId",
                ],
                type: "object",
            },
        },
    },
    serviceName: "apimService1",
    version: "1.0.0",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

content_type = azure_native.apimanagement.ContentType("contentType",
    content_type_id="page",
    description="A regular page",
    name="Page",
    resource_group_name="rg1",
    schema={
        "additionalProperties": False,
        "properties": {
            "en_us": {
                "additionalProperties": False,
                "properties": {
                    "description": {
                        "description": "Page description. This property gets included in SEO attributes.",
                        "indexed": True,
                        "title": "Description",
                        "type": "string",
                    },
                    "documentId": {
                        "description": "Reference to page content document.",
                        "title": "Document ID",
                        "type": "string",
                    },
                    "keywords": {
                        "description": "Page keywords. This property gets included in SEO attributes.",
                        "indexed": True,
                        "title": "Keywords",
                        "type": "string",
                    },
                    "permalink": {
                        "description": "Page permalink, e.g. '/about'.",
                        "indexed": True,
                        "title": "Permalink",
                        "type": "string",
                    },
                    "title": {
                        "description": "Page title. This property gets included in SEO attributes.",
                        "indexed": True,
                        "title": "Title",
                        "type": "string",
                    },
                },
                "required": [
                    "title",
                    "permalink",
                    "documentId",
                ],
                "type": "object",
            },
        },
    },
    service_name="apimService1",
    version="1.0.0")

```

```yaml
resources:
  contentType:
    type: azure-native:apimanagement:ContentType
    properties:
      contentTypeId: page
      description: A regular page
      name: Page
      resourceGroupName: rg1
      schema:
        additionalProperties: false
        properties:
          en_us:
            additionalProperties: false
            properties:
              description:
                description: Page description. This property gets included in SEO attributes.
                indexed: true
                title: Description
                type: string
              documentId:
                description: Reference to page content document.
                title: Document ID
                type: string
              keywords:
                description: Page keywords. This property gets included in SEO attributes.
                indexed: true
                title: Keywords
                type: string
              permalink:
                description: Page permalink, e.g. '/about'.
                indexed: true
                title: Permalink
                type: string
              title:
                description: Page title. This property gets included in SEO attributes.
                indexed: true
                title: Title
                type: string
            required:
              - title
              - permalink
              - documentId
            type: object
      serviceName: apimService1
      version: 1.0.0

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:ContentType page /contentTypes/page 
```
