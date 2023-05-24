A workbook definition.
API Version: 2022-04-01.
Previous API Version: 2020-10-20. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### WorkbookAdd
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var workbook = new AzureNative.Insights.Workbook("workbook", new()
    {
        Category = "workbook",
        Description = "Sample workbook",
        DisplayName = "Sample workbook",
        Kind = "shared",
        Location = "westus",
        ResourceGroupName = "my-resource-group",
        ResourceName = "deadb33f-5e0d-4064-8ebb-1a4ed0313eb2",
        SerializedData = "{\"version\":\"Notebook/1.0\",\"items\":[{\"type\":1,\"content\":\"{\"json\":\"## New workbook\\r\\n---\\r\\n\\r\\nWelcome to your new workbook.  This area will display text formatted as markdown.\\r\\n\\r\\n\\r\\nWe've included a basic analytics query to get you started. Use the `Edit` button below each section to configure it or add more sections.\"}\",\"halfWidth\":null,\"conditionalVisibility\":null},{\"type\":3,\"content\":\"{\"version\":\"KqlItem/1.0\",\"query\":\"union withsource=TableName *\\n| summarize Count=count() by TableName\\n| render barchart\",\"showQuery\":false,\"size\":1,\"aggregation\":0,\"showAnnotations\":false}\",\"halfWidth\":null,\"conditionalVisibility\":null}],\"isLocked\":false}",
        SourceId = "/subscriptions/6b643656-33eb-422f-aee8-3ac145d124af/resourcegroups/my-resource-group",
        Tags = 
        {
            { "TagSample01", "sample01" },
            { "TagSample02", "sample02" },
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
		_, err := insights.NewWorkbook(ctx, "workbook", &insights.WorkbookArgs{
			Category:          pulumi.String("workbook"),
			Description:       pulumi.String("Sample workbook"),
			DisplayName:       pulumi.String("Sample workbook"),
			Kind:              pulumi.String("shared"),
			Location:          pulumi.String("westus"),
			ResourceGroupName: pulumi.String("my-resource-group"),
			ResourceName:      pulumi.String("deadb33f-5e0d-4064-8ebb-1a4ed0313eb2"),
			SerializedData:    pulumi.String("{\"version\":\"Notebook/1.0\",\"items\":[{\"type\":1,\"content\":\"{\"json\":\"## New workbook\\r\\n---\\r\\n\\r\\nWelcome to your new workbook.  This area will display text formatted as markdown.\\r\\n\\r\\n\\r\\nWe've included a basic analytics query to get you started. Use the `Edit` button below each section to configure it or add more sections.\"}\",\"halfWidth\":null,\"conditionalVisibility\":null},{\"type\":3,\"content\":\"{\"version\":\"KqlItem/1.0\",\"query\":\"union withsource=TableName *\\n| summarize Count=count() by TableName\\n| render barchart\",\"showQuery\":false,\"size\":1,\"aggregation\":0,\"showAnnotations\":false}\",\"halfWidth\":null,\"conditionalVisibility\":null}],\"isLocked\":false}"),
			SourceId:          pulumi.String("/subscriptions/6b643656-33eb-422f-aee8-3ac145d124af/resourcegroups/my-resource-group"),
			Tags: pulumi.StringMap{
				"TagSample01": pulumi.String("sample01"),
				"TagSample02": pulumi.String("sample02"),
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
import com.pulumi.azurenative.insights.Workbook;
import com.pulumi.azurenative.insights.WorkbookArgs;
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
        var workbook = new Workbook("workbook", WorkbookArgs.builder()        
            .category("workbook")
            .description("Sample workbook")
            .displayName("Sample workbook")
            .kind("shared")
            .location("westus")
            .resourceGroupName("my-resource-group")
            .resourceName("deadb33f-5e0d-4064-8ebb-1a4ed0313eb2")
            .serializedData("{\"version\":\"Notebook/1.0\",\"items\":[{\"type\":1,\"content\":\"{\"json\":\"## New workbook\\r\\n---\\r\\n\\r\\nWelcome to your new workbook.  This area will display text formatted as markdown.\\r\\n\\r\\n\\r\\nWe've included a basic analytics query to get you started. Use the `Edit` button below each section to configure it or add more sections.\"}\",\"halfWidth\":null,\"conditionalVisibility\":null},{\"type\":3,\"content\":\"{\"version\":\"KqlItem/1.0\",\"query\":\"union withsource=TableName *\\n| summarize Count=count() by TableName\\n| render barchart\",\"showQuery\":false,\"size\":1,\"aggregation\":0,\"showAnnotations\":false}\",\"halfWidth\":null,\"conditionalVisibility\":null}],\"isLocked\":false}")
            .sourceId("/subscriptions/6b643656-33eb-422f-aee8-3ac145d124af/resourcegroups/my-resource-group")
            .tags(Map.ofEntries(
                Map.entry("TagSample01", "sample01"),
                Map.entry("TagSample02", "sample02")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const workbook = new azure_native.insights.Workbook("workbook", {
    category: "workbook",
    description: "Sample workbook",
    displayName: "Sample workbook",
    kind: "shared",
    location: "westus",
    resourceGroupName: "my-resource-group",
    resourceName: "deadb33f-5e0d-4064-8ebb-1a4ed0313eb2",
    serializedData: "{\"version\":\"Notebook/1.0\",\"items\":[{\"type\":1,\"content\":\"{\"json\":\"## New workbook\\r\\n---\\r\\n\\r\\nWelcome to your new workbook.  This area will display text formatted as markdown.\\r\\n\\r\\n\\r\\nWe've included a basic analytics query to get you started. Use the `Edit` button below each section to configure it or add more sections.\"}\",\"halfWidth\":null,\"conditionalVisibility\":null},{\"type\":3,\"content\":\"{\"version\":\"KqlItem/1.0\",\"query\":\"union withsource=TableName *\\n| summarize Count=count() by TableName\\n| render barchart\",\"showQuery\":false,\"size\":1,\"aggregation\":0,\"showAnnotations\":false}\",\"halfWidth\":null,\"conditionalVisibility\":null}],\"isLocked\":false}",
    sourceId: "/subscriptions/6b643656-33eb-422f-aee8-3ac145d124af/resourcegroups/my-resource-group",
    tags: {
        TagSample01: "sample01",
        TagSample02: "sample02",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

workbook = azure_native.insights.Workbook("workbook",
    category="workbook",
    description="Sample workbook",
    display_name="Sample workbook",
    kind="shared",
    location="westus",
    resource_group_name="my-resource-group",
    resource_name_="deadb33f-5e0d-4064-8ebb-1a4ed0313eb2",
    serialized_data="{\"version\":\"Notebook/1.0\",\"items\":[{\"type\":1,\"content\":\"{\"json\":\"## New workbook\\r\\n---\\r\\n\\r\\nWelcome to your new workbook.  This area will display text formatted as markdown.\\r\\n\\r\\n\\r\\nWe've included a basic analytics query to get you started. Use the `Edit` button below each section to configure it or add more sections.\"}\",\"halfWidth\":null,\"conditionalVisibility\":null},{\"type\":3,\"content\":\"{\"version\":\"KqlItem/1.0\",\"query\":\"union withsource=TableName *\\n| summarize Count=count() by TableName\\n| render barchart\",\"showQuery\":false,\"size\":1,\"aggregation\":0,\"showAnnotations\":false}\",\"halfWidth\":null,\"conditionalVisibility\":null}],\"isLocked\":false}",
    source_id="/subscriptions/6b643656-33eb-422f-aee8-3ac145d124af/resourcegroups/my-resource-group",
    tags={
        "TagSample01": "sample01",
        "TagSample02": "sample02",
    })

```

```yaml
resources:
  workbook:
    type: azure-native:insights:Workbook
    properties:
      category: workbook
      description: Sample workbook
      displayName: Sample workbook
      kind: shared
      location: westus
      resourceGroupName: my-resource-group
      resourceName: deadb33f-5e0d-4064-8ebb-1a4ed0313eb2
      serializedData: '{"version":"Notebook/1.0","items":[{"type":1,"content":"{"json":"## New workbook\r\n---\r\n\r\nWelcome to your new workbook.  This area will display text formatted as markdown.\r\n\r\n\r\nWe''ve included a basic analytics query to get you started. Use the `Edit` button below each section to configure it or add more sections."}","halfWidth":null,"conditionalVisibility":null},{"type":3,"content":"{"version":"KqlItem/1.0","query":"union withsource=TableName *\n| summarize Count=count() by TableName\n| render barchart","showQuery":false,"size":1,"aggregation":0,"showAnnotations":false}","halfWidth":null,"conditionalVisibility":null}],"isLocked":false}'
      sourceId: /subscriptions/6b643656-33eb-422f-aee8-3ac145d124af/resourcegroups/my-resource-group
      tags:
        TagSample01: sample01
        TagSample02: sample02

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:insights:Workbook deadb33f-5e0d-4064-8ebb-1a4ed0313eb2 /subscriptions/6b643656-33eb-422f-aee8-3ac145d124af/resourcegroups/my-resource-group/providers/Microsoft.Insights/workbooks/deadb33f-5e0d-4064-8ebb-1a4ed0313eb2 
```
