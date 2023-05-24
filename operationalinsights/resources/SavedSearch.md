Value object for saved search results.
API Version: 2020-08-01.
Previous API Version: 2020-08-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### SavedSearchCreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var savedSearch = new AzureNative.OperationalInsights.SavedSearch("savedSearch", new()
    {
        Category = "Saved Search Test Category",
        DisplayName = "Create or Update Saved Search Test",
        FunctionAlias = "heartbeat_func",
        FunctionParameters = "a:int=1",
        Query = "Heartbeat | summarize Count() by Computer | take a",
        ResourceGroupName = "TestRG",
        SavedSearchId = "00000000-0000-0000-0000-00000000000",
        Tags = new[]
        {
            new AzureNative.OperationalInsights.Inputs.TagArgs
            {
                Name = "Group",
                Value = "Computer",
            },
        },
        Version = 2,
        WorkspaceName = "TestWS",
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
		_, err := operationalinsights.NewSavedSearch(ctx, "savedSearch", &operationalinsights.SavedSearchArgs{
			Category:           pulumi.String("Saved Search Test Category"),
			DisplayName:        pulumi.String("Create or Update Saved Search Test"),
			FunctionAlias:      pulumi.String("heartbeat_func"),
			FunctionParameters: pulumi.String("a:int=1"),
			Query:              pulumi.String("Heartbeat | summarize Count() by Computer | take a"),
			ResourceGroupName:  pulumi.String("TestRG"),
			SavedSearchId:      pulumi.String("00000000-0000-0000-0000-00000000000"),
			Tags: []operationalinsights.TagArgs{
				{
					Name:  pulumi.String("Group"),
					Value: pulumi.String("Computer"),
				},
			},
			Version:       pulumi.Float64(2),
			WorkspaceName: pulumi.String("TestWS"),
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
import com.pulumi.azurenative.operationalinsights.SavedSearch;
import com.pulumi.azurenative.operationalinsights.SavedSearchArgs;
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
        var savedSearch = new SavedSearch("savedSearch", SavedSearchArgs.builder()        
            .category("Saved Search Test Category")
            .displayName("Create or Update Saved Search Test")
            .functionAlias("heartbeat_func")
            .functionParameters("a:int=1")
            .query("Heartbeat | summarize Count() by Computer | take a")
            .resourceGroupName("TestRG")
            .savedSearchId("00000000-0000-0000-0000-00000000000")
            .tags(Map.ofEntries(
                Map.entry("name", "Group"),
                Map.entry("value", "Computer")
            ))
            .version(2)
            .workspaceName("TestWS")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const savedSearch = new azure_native.operationalinsights.SavedSearch("savedSearch", {
    category: "Saved Search Test Category",
    displayName: "Create or Update Saved Search Test",
    functionAlias: "heartbeat_func",
    functionParameters: "a:int=1",
    query: "Heartbeat | summarize Count() by Computer | take a",
    resourceGroupName: "TestRG",
    savedSearchId: "00000000-0000-0000-0000-00000000000",
    tags: [{
        name: "Group",
        value: "Computer",
    }],
    version: 2,
    workspaceName: "TestWS",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

saved_search = azure_native.operationalinsights.SavedSearch("savedSearch",
    category="Saved Search Test Category",
    display_name="Create or Update Saved Search Test",
    function_alias="heartbeat_func",
    function_parameters="a:int=1",
    query="Heartbeat | summarize Count() by Computer | take a",
    resource_group_name="TestRG",
    saved_search_id="00000000-0000-0000-0000-00000000000",
    tags=[azure_native.operationalinsights.TagArgs(
        name="Group",
        value="Computer",
    )],
    version=2,
    workspace_name="TestWS")

```

```yaml
resources:
  savedSearch:
    type: azure-native:operationalinsights:SavedSearch
    properties:
      category: Saved Search Test Category
      displayName: Create or Update Saved Search Test
      functionAlias: heartbeat_func
      functionParameters: a:int=1
      query: Heartbeat | summarize Count() by Computer | take a
      resourceGroupName: TestRG
      savedSearchId: 00000000-0000-0000-0000-00000000000
      tags:
        - name: Group
          value: Computer
      version: 2
      workspaceName: TestWS

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:operationalinsights:SavedSearch myresource1 subscriptions/00000000-0000-0000-0000-000000000005/resourceGroups/mms-eus/providers/Microsoft.OperationalInsights/workspaces/AtlantisDemo/savedSearches/test-new-saved-search-id-2015 
```
