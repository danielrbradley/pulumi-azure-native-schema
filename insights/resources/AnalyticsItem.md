Properties that define an Analytics item that is associated to an Application Insights component.
API Version: 2015-05-01.
Previous API Version: 2015-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### AnalyticsItemPut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var analyticsItem = new AzureNative.Insights.AnalyticsItem("analyticsItem", new()
    {
        Content = @"let newExceptionsTimeRange = 1d;
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
        Name = "Exceptions - New in the last 24 hours",
        ResourceGroupName = "my-resource-group",
        ResourceName = "my-component",
        Scope = "shared",
        ScopePath = "analyticsItems",
        Type = "query",
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
		_, err := insights.NewAnalyticsItem(ctx, "analyticsItem", &insights.AnalyticsItemArgs{
			Content:           pulumi.String("let newExceptionsTimeRange = 1d;\nlet timeRangeToCheckBefore = 7d;\nexceptions\n| where timestamp < ago(timeRangeToCheckBefore)\n| summarize count() by problemId\n| join kind= rightanti (\nexceptions\n| where timestamp >= ago(newExceptionsTimeRange)\n| extend stack = tostring(details[0].rawStack)\n| summarize count(), dcount(user_AuthenticatedId), min(timestamp), max(timestamp), any(stack) by problemId  \n) on problemId \n| order by  count_ desc\n"),
			Name:              pulumi.String("Exceptions - New in the last 24 hours"),
			ResourceGroupName: pulumi.String("my-resource-group"),
			ResourceName:      pulumi.String("my-component"),
			Scope:             pulumi.String("shared"),
			ScopePath:         pulumi.String("analyticsItems"),
			Type:              pulumi.String("query"),
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
import com.pulumi.azurenative.insights.AnalyticsItem;
import com.pulumi.azurenative.insights.AnalyticsItemArgs;
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
        var analyticsItem = new AnalyticsItem("analyticsItem", AnalyticsItemArgs.builder()        
            .content("""
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
            .name("Exceptions - New in the last 24 hours")
            .resourceGroupName("my-resource-group")
            .resourceName("my-component")
            .scope("shared")
            .scopePath("analyticsItems")
            .type("query")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const analyticsItem = new azure_native.insights.AnalyticsItem("analyticsItem", {
    content: `let newExceptionsTimeRange = 1d;
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
    name: "Exceptions - New in the last 24 hours",
    resourceGroupName: "my-resource-group",
    resourceName: "my-component",
    scope: "shared",
    scopePath: "analyticsItems",
    type: "query",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

analytics_item = azure_native.insights.AnalyticsItem("analyticsItem",
    content="""let newExceptionsTimeRange = 1d;
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
    name="Exceptions - New in the last 24 hours",
    resource_group_name="my-resource-group",
    resource_name_="my-component",
    scope="shared",
    scope_path="analyticsItems",
    type="query")

```

```yaml
resources:
  analyticsItem:
    type: azure-native:insights:AnalyticsItem
    properties:
      content: "let newExceptionsTimeRange = 1d;\nlet timeRangeToCheckBefore = 7d;\nexceptions\n| where timestamp < ago(timeRangeToCheckBefore)\n| summarize count() by problemId\n| join kind= rightanti (\nexceptions\n| where timestamp >= ago(newExceptionsTimeRange)\n| extend stack = tostring(details[0].rawStack)\n| summarize count(), dcount(user_AuthenticatedId), min(timestamp), max(timestamp), any(stack) by problemId  \n) on problemId \n| order by  count_ desc\n"
      name: Exceptions - New in the last 24 hours
      resourceGroupName: my-resource-group
      resourceName: my-component
      scope: shared
      scopePath: analyticsItems
      type: query

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:insights:AnalyticsItem myresource1 /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/microsoft.insights/components/{resourceName}/{scopePath}/item 
```
