A Log Analytics QueryPack-Query definition.
API Version: 2019-09-01.
Previous API Version: 2019-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### QueryPut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var query = new AzureNative.OperationalInsights.Query("query", new()
    {
        Body = @"let newExceptionsTimeRange = 1d;
let timeRangeToCheckBefore = 7d;
exceptions
| where timestamp < ago(timeRangeToCheckBefore)
| summarize count() by problemId
| join kind= rightanti (
exceptions
| where timestamp >= ago(newExceptionsTimeRange)
| extend stack = tostring(details[0].rawStack)
| summarize count(), dcount(user_AuthenticatedId), min(timestamp), max(timestamp), any(stack) by problemId  
) on problemId 
| order by  count_ desc
",
        Description = "my description",
        DisplayName = "Exceptions - New in the last 24 hours",
        Id = "a449f8af-8e64-4b3a-9b16-5a7165ff98c4",
        QueryPackName = "my-querypack",
        Related = new AzureNative.OperationalInsights.Inputs.LogAnalyticsQueryPackQueryPropertiesRelatedArgs
        {
            Categories = new[]
            {
                "analytics",
            },
        },
        ResourceGroupName = "my-resource-group",
        Tags = 
        {
            { "my-label", new[]
            {
                "label1",
            } },
            { "my-other-label", new[]
            {
                "label2",
            } },
        },
    });

});


```

```go
package main

import (
	operationalinsights "github.com/pulumi/pulumi-azure-native-sdk/operationalinsights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := operationalinsights.NewQuery(ctx, "query", &operationalinsights.QueryArgs{
			Body:          pulumi.String("let newExceptionsTimeRange = 1d;\nlet timeRangeToCheckBefore = 7d;\nexceptions\n| where timestamp < ago(timeRangeToCheckBefore)\n| summarize count() by problemId\n| join kind= rightanti (\nexceptions\n| where timestamp >= ago(newExceptionsTimeRange)\n| extend stack = tostring(details[0].rawStack)\n| summarize count(), dcount(user_AuthenticatedId), min(timestamp), max(timestamp), any(stack) by problemId  \n) on problemId \n| order by  count_ desc\n"),
			Description:   pulumi.String("my description"),
			DisplayName:   pulumi.String("Exceptions - New in the last 24 hours"),
			Id:            pulumi.String("a449f8af-8e64-4b3a-9b16-5a7165ff98c4"),
			QueryPackName: pulumi.String("my-querypack"),
			Related: &operationalinsights.LogAnalyticsQueryPackQueryPropertiesRelatedArgs{
				Categories: pulumi.StringArray{
					pulumi.String("analytics"),
				},
			},
			ResourceGroupName: pulumi.String("my-resource-group"),
			Tags: pulumi.StringArrayMap{
				"my-label": pulumi.StringArray{
					pulumi.String("label1"),
				},
				"my-other-label": pulumi.StringArray{
					pulumi.String("label2"),
				},
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
import com.pulumi.azurenative.operationalinsights.Query;
import com.pulumi.azurenative.operationalinsights.QueryArgs;
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
        var query = new Query("query", QueryArgs.builder()        
            .body("""
let newExceptionsTimeRange = 1d;
let timeRangeToCheckBefore = 7d;
exceptions
| where timestamp < ago(timeRangeToCheckBefore)
| summarize count() by problemId
| join kind= rightanti (
exceptions
| where timestamp >= ago(newExceptionsTimeRange)
| extend stack = tostring(details[0].rawStack)
| summarize count(), dcount(user_AuthenticatedId), min(timestamp), max(timestamp), any(stack) by problemId  
) on problemId 
| order by  count_ desc
            """)
            .description("my description")
            .displayName("Exceptions - New in the last 24 hours")
            .id("a449f8af-8e64-4b3a-9b16-5a7165ff98c4")
            .queryPackName("my-querypack")
            .related(Map.of("categories", "analytics"))
            .resourceGroupName("my-resource-group")
            .tags(Map.ofEntries(
                Map.entry("my-label", "label1"),
                Map.entry("my-other-label", "label2")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const query = new azure_native.operationalinsights.Query("query", {
    body: `let newExceptionsTimeRange = 1d;
let timeRangeToCheckBefore = 7d;
exceptions
| where timestamp < ago(timeRangeToCheckBefore)
| summarize count() by problemId
| join kind= rightanti (
exceptions
| where timestamp >= ago(newExceptionsTimeRange)
| extend stack = tostring(details[0].rawStack)
| summarize count(), dcount(user_AuthenticatedId), min(timestamp), max(timestamp), any(stack) by problemId  
) on problemId 
| order by  count_ desc
`,
    description: "my description",
    displayName: "Exceptions - New in the last 24 hours",
    id: "a449f8af-8e64-4b3a-9b16-5a7165ff98c4",
    queryPackName: "my-querypack",
    related: {
        categories: ["analytics"],
    },
    resourceGroupName: "my-resource-group",
    tags: {
        "my-label": ["label1"],
        "my-other-label": ["label2"],
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

query = azure_native.operationalinsights.Query("query",
    body="""let newExceptionsTimeRange = 1d;
let timeRangeToCheckBefore = 7d;
exceptions
| where timestamp < ago(timeRangeToCheckBefore)
| summarize count() by problemId
| join kind= rightanti (
exceptions
| where timestamp >= ago(newExceptionsTimeRange)
| extend stack = tostring(details[0].rawStack)
| summarize count(), dcount(user_AuthenticatedId), min(timestamp), max(timestamp), any(stack) by problemId  
) on problemId 
| order by  count_ desc
""",
    description="my description",
    display_name="Exceptions - New in the last 24 hours",
    id="a449f8af-8e64-4b3a-9b16-5a7165ff98c4",
    query_pack_name="my-querypack",
    related=azure_native.operationalinsights.LogAnalyticsQueryPackQueryPropertiesRelatedArgs(
        categories=["analytics"],
    ),
    resource_group_name="my-resource-group",
    tags={
        "my-label": ["label1"],
        "my-other-label": ["label2"],
    })

```

```yaml
resources:
  query:
    type: azure-native:operationalinsights:Query
    properties:
      body: "let newExceptionsTimeRange = 1d;\nlet timeRangeToCheckBefore = 7d;\nexceptions\n| where timestamp < ago(timeRangeToCheckBefore)\n| summarize count() by problemId\n| join kind= rightanti (\nexceptions\n| where timestamp >= ago(newExceptionsTimeRange)\n| extend stack = tostring(details[0].rawStack)\n| summarize count(), dcount(user_AuthenticatedId), min(timestamp), max(timestamp), any(stack) by problemId  \n) on problemId \n| order by  count_ desc\n"
      description: my description
      displayName: Exceptions - New in the last 24 hours
      id: a449f8af-8e64-4b3a-9b16-5a7165ff98c4
      queryPackName: my-querypack
      related:
        categories:
          - analytics
      resourceGroupName: my-resource-group
      tags:
        my-label:
          - label1
        my-other-label:
          - label2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:operationalinsights:Query a449f8af-8e64-4b3a-9b16-5a7165ff98c4 /subscriptions/86dc51d3-92ed-4d7e-947a-775ea79b4918/resourceGroups/my-resource-group/providers/microsoft.operationalinsights/queryPacks/my-querypack/queries/a449f8af-8e64-4b3a-9b16-5a7165ff98c4 
```
