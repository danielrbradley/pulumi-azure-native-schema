An Application Insights workbook template definition.
API Version: 2020-11-20.
Previous API Version: 2019-10-17-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### WorkbookTemplateAdd
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var workbookTemplate = new AzureNative.Insights.WorkbookTemplate("workbookTemplate", new()
    {
        Author = "Contoso",
        Galleries = new[]
        {
            new AzureNative.Insights.Inputs.WorkbookTemplateGalleryArgs
            {
                Category = "Failures",
                Name = "Simple Template",
                Order = 100,
                ResourceType = "microsoft.insights/components",
                Type = "tsg",
            },
        },
        Location = "west us",
        Priority = 1,
        ResourceGroupName = "my-resource-group",
        ResourceName = "testtemplate2",
        TemplateData = 
        {
            { "$schema", "https://github.com/Microsoft/Application-Insights-Workbooks/blob/master/schema/workbook.json" },
            { "items", new[]
            {
                
                {
                    { "content", 
                    {
                        { "json", @"## New workbook
---

Welcome to your new workbook.  This area will display text formatted as markdown.


We've included a basic analytics query to get you started. Use the `Edit` button below each section to configure it or add more sections." },
                    } },
                    { "name", "text - 2" },
                    { "type", 1 },
                },
                
                {
                    { "content", 
                    {
                        { "exportToExcelOptions", "visible" },
                        { "query", @"union withsource=TableName *
| summarize Count=count() by TableName
| render barchart" },
                        { "queryType", 0 },
                        { "resourceType", "microsoft.operationalinsights/workspaces" },
                        { "size", 1 },
                        { "version", "KqlItem/1.0" },
                    } },
                    { "name", "query - 2" },
                    { "type", 3 },
                },
            } },
            { "styleSettings", null },
            { "version", "Notebook/1.0" },
        },
    });

});


```

```go
package main

import (
	insights "github.com/pulumi/pulumi-azure-native-sdk/insights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := insights.NewWorkbookTemplate(ctx, "workbookTemplate", &insights.WorkbookTemplateArgs{
			Author: pulumi.String("Contoso"),
			Galleries: []insights.WorkbookTemplateGalleryArgs{
				{
					Category:     pulumi.String("Failures"),
					Name:         pulumi.String("Simple Template"),
					Order:        pulumi.Int(100),
					ResourceType: pulumi.String("microsoft.insights/components"),
					Type:         pulumi.String("tsg"),
				},
			},
			Location:          pulumi.String("west us"),
			Priority:          pulumi.Int(1),
			ResourceGroupName: pulumi.String("my-resource-group"),
			ResourceName:      pulumi.String("testtemplate2"),
			TemplateData: pulumi.Any{
				Schema: "https://github.com/Microsoft/Application-Insights-Workbooks/blob/master/schema/workbook.json",
				Items: []interface{}{
					map[string]interface{}{
						"content": map[string]interface{}{
							"json": "## New workbook\n---\n\nWelcome to your new workbook.  This area will display text formatted as markdown.\n\n\nWe've included a basic analytics query to get you started. Use the `Edit` button below each section to configure it or add more sections.",
						},
						"name": "text - 2",
						"type": 1,
					},
					map[string]interface{}{
						"content": map[string]interface{}{
							"exportToExcelOptions": "visible",
							"query":                "union withsource=TableName *\n| summarize Count=count() by TableName\n| render barchart",
							"queryType":            0,
							"resourceType":         "microsoft.operationalinsights/workspaces",
							"size":                 1,
							"version":              "KqlItem/1.0",
						},
						"name": "query - 2",
						"type": 3,
					},
				},
				StyleSettings: nil,
				Version:       "Notebook/1.0",
			},
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
import com.pulumi.azurenative.insights.WorkbookTemplate;
import com.pulumi.azurenative.insights.WorkbookTemplateArgs;
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
        var workbookTemplate = new WorkbookTemplate("workbookTemplate", WorkbookTemplateArgs.builder()        
            .author("Contoso")
            .galleries(Map.ofEntries(
                Map.entry("category", "Failures"),
                Map.entry("name", "Simple Template"),
                Map.entry("order", 100),
                Map.entry("resourceType", "microsoft.insights/components"),
                Map.entry("type", "tsg")
            ))
            .location("west us")
            .priority(1)
            .resourceGroupName("my-resource-group")
            .resourceName("testtemplate2")
            .templateData(Map.ofEntries(
                Map.entry("$schema", "https://github.com/Microsoft/Application-Insights-Workbooks/blob/master/schema/workbook.json"),
                Map.entry("items",                 
                    Map.ofEntries(
                        Map.entry("content", Map.of("json", """
## New workbook
---

Welcome to your new workbook.  This area will display text formatted as markdown.


We've included a basic analytics query to get you started. Use the `Edit` button below each section to configure it or add more sections.                        """)),
                        Map.entry("name", "text - 2"),
                        Map.entry("type", 1)
                    ),
                    Map.ofEntries(
                        Map.entry("content", Map.ofEntries(
                            Map.entry("exportToExcelOptions", "visible"),
                            Map.entry("query", """
union withsource=TableName *
| summarize Count=count() by TableName
| render barchart                            """),
                            Map.entry("queryType", 0),
                            Map.entry("resourceType", "microsoft.operationalinsights/workspaces"),
                            Map.entry("size", 1),
                            Map.entry("version", "KqlItem/1.0")
                        )),
                        Map.entry("name", "query - 2"),
                        Map.entry("type", 3)
                    )),
                Map.entry("styleSettings", ),
                Map.entry("version", "Notebook/1.0")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const workbookTemplate = new azure_native.insights.WorkbookTemplate("workbookTemplate", {
    author: "Contoso",
    galleries: [{
        category: "Failures",
        name: "Simple Template",
        order: 100,
        resourceType: "microsoft.insights/components",
        type: "tsg",
    }],
    location: "west us",
    priority: 1,
    resourceGroupName: "my-resource-group",
    resourceName: "testtemplate2",
    templateData: {
        $schema: "https://github.com/Microsoft/Application-Insights-Workbooks/blob/master/schema/workbook.json",
        items: [
            {
                content: {
                    json: `## New workbook
---

Welcome to your new workbook.  This area will display text formatted as markdown.


We've included a basic analytics query to get you started. Use the \`Edit\` button below each section to configure it or add more sections.`,
                },
                name: "text - 2",
                type: 1,
            },
            {
                content: {
                    exportToExcelOptions: "visible",
                    query: `union withsource=TableName *
| summarize Count=count() by TableName
| render barchart`,
                    queryType: 0,
                    resourceType: "microsoft.operationalinsights/workspaces",
                    size: 1,
                    version: "KqlItem/1.0",
                },
                name: "query - 2",
                type: 3,
            },
        ],
        styleSettings: {},
        version: "Notebook/1.0",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

workbook_template = azure_native.insights.WorkbookTemplate("workbookTemplate",
    author="Contoso",
    galleries=[azure_native.insights.WorkbookTemplateGalleryArgs(
        category="Failures",
        name="Simple Template",
        order=100,
        resource_type="microsoft.insights/components",
        type="tsg",
    )],
    location="west us",
    priority=1,
    resource_group_name="my-resource-group",
    resource_name_="testtemplate2",
    template_data={
        "$schema": "https://github.com/Microsoft/Application-Insights-Workbooks/blob/master/schema/workbook.json",
        "items": [
            {
                "content": {
                    "json": """## New workbook
---

Welcome to your new workbook.  This area will display text formatted as markdown.


We've included a basic analytics query to get you started. Use the `Edit` button below each section to configure it or add more sections.""",
                },
                "name": "text - 2",
                "type": 1,
            },
            {
                "content": {
                    "exportToExcelOptions": "visible",
                    "query": """union withsource=TableName *
| summarize Count=count() by TableName
| render barchart""",
                    "queryType": 0,
                    "resourceType": "microsoft.operationalinsights/workspaces",
                    "size": 1,
                    "version": "KqlItem/1.0",
                },
                "name": "query - 2",
                "type": 3,
            },
        ],
        "styleSettings": {},
        "version": "Notebook/1.0",
    })

```

```yaml
resources:
  workbookTemplate:
    type: azure-native:insights:WorkbookTemplate
    properties:
      author: Contoso
      galleries:
        - category: Failures
          name: Simple Template
          order: 100
          resourceType: microsoft.insights/components
          type: tsg
      location: west us
      priority: 1
      resourceGroupName: my-resource-group
      resourceName: testtemplate2
      templateData:
        $schema: https://github.com/Microsoft/Application-Insights-Workbooks/blob/master/schema/workbook.json
        items:
          - content:
              json: |-
                ## New workbook
                ---

                Welcome to your new workbook.  This area will display text formatted as markdown.


                We've included a basic analytics query to get you started. Use the `Edit` button below each section to configure it or add more sections.
            name: text - 2
            type: 1
          - content:
              exportToExcelOptions: visible
              query: |-
                union withsource=TableName *
                | summarize Count=count() by TableName
                | render barchart
              queryType: 0
              resourceType: microsoft.operationalinsights/workspaces
              size: 1
              version: KqlItem/1.0
            name: query - 2
            type: 3
        styleSettings: {}
        version: Notebook/1.0

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:insights:WorkbookTemplate testtemplate2 /subscriptions/50359d91-7b9d-4823-85af-eb298a61ba95/resourceGroups/testrg/providers/microsoft.insights/workbooktemplates/testtemplate2 
```
