Represents a bookmark in Azure Security Insights.
API Version: 2023-02-01.
Previous API Version: 2020-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates or updates a bookmark.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var bookmark = new AzureNative.SecurityInsights.Bookmark("bookmark", new()
    {
        BookmarkId = "73e01a99-5cd7-4139-a149-9f2736ff2ab5",
        Created = "2019-01-01T13:15:30Z",
        CreatedBy = new AzureNative.SecurityInsights.Inputs.UserInfoArgs
        {
            ObjectId = "2046feea-040d-4a46-9e2b-91c2941bfa70",
        },
        DisplayName = "My bookmark",
        Labels = new[]
        {
            "Tag1",
            "Tag2",
        },
        Notes = "Found a suspicious activity",
        Query = "SecurityEvent | where TimeGenerated > ago(1d) and TimeGenerated < ago(2d)",
        QueryResult = "Security Event query result",
        ResourceGroupName = "myRg",
        Updated = "2019-01-01T13:15:30Z",
        UpdatedBy = new AzureNative.SecurityInsights.Inputs.UserInfoArgs
        {
            ObjectId = "2046feea-040d-4a46-9e2b-91c2941bfa70",
        },
        WorkspaceName = "myWorkspace",
    });

});


```

```go
package main

import (
	securityinsights "github.com/pulumi/pulumi-azure-native-sdk/securityinsights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := securityinsights.NewBookmark(ctx, "bookmark", &securityinsights.BookmarkArgs{
			BookmarkId: pulumi.String("73e01a99-5cd7-4139-a149-9f2736ff2ab5"),
			Created:    pulumi.String("2019-01-01T13:15:30Z"),
			CreatedBy: &securityinsights.UserInfoArgs{
				ObjectId: pulumi.String("2046feea-040d-4a46-9e2b-91c2941bfa70"),
			},
			DisplayName: pulumi.String("My bookmark"),
			Labels: pulumi.StringArray{
				pulumi.String("Tag1"),
				pulumi.String("Tag2"),
			},
			Notes:             pulumi.String("Found a suspicious activity"),
			Query:             pulumi.String("SecurityEvent | where TimeGenerated > ago(1d) and TimeGenerated < ago(2d)"),
			QueryResult:       pulumi.String("Security Event query result"),
			ResourceGroupName: pulumi.String("myRg"),
			Updated:           pulumi.String("2019-01-01T13:15:30Z"),
			UpdatedBy: &securityinsights.UserInfoArgs{
				ObjectId: pulumi.String("2046feea-040d-4a46-9e2b-91c2941bfa70"),
			},
			WorkspaceName: pulumi.String("myWorkspace"),
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
import com.pulumi.azurenative.securityinsights.Bookmark;
import com.pulumi.azurenative.securityinsights.BookmarkArgs;
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
        var bookmark = new Bookmark("bookmark", BookmarkArgs.builder()        
            .bookmarkId("73e01a99-5cd7-4139-a149-9f2736ff2ab5")
            .created("2019-01-01T13:15:30Z")
            .createdBy(Map.of("objectId", "2046feea-040d-4a46-9e2b-91c2941bfa70"))
            .displayName("My bookmark")
            .labels(            
                "Tag1",
                "Tag2")
            .notes("Found a suspicious activity")
            .query("SecurityEvent | where TimeGenerated > ago(1d) and TimeGenerated < ago(2d)")
            .queryResult("Security Event query result")
            .resourceGroupName("myRg")
            .updated("2019-01-01T13:15:30Z")
            .updatedBy(Map.of("objectId", "2046feea-040d-4a46-9e2b-91c2941bfa70"))
            .workspaceName("myWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const bookmark = new azure_native.securityinsights.Bookmark("bookmark", {
    bookmarkId: "73e01a99-5cd7-4139-a149-9f2736ff2ab5",
    created: "2019-01-01T13:15:30Z",
    createdBy: {
        objectId: "2046feea-040d-4a46-9e2b-91c2941bfa70",
    },
    displayName: "My bookmark",
    labels: [
        "Tag1",
        "Tag2",
    ],
    notes: "Found a suspicious activity",
    query: "SecurityEvent | where TimeGenerated > ago(1d) and TimeGenerated < ago(2d)",
    queryResult: "Security Event query result",
    resourceGroupName: "myRg",
    updated: "2019-01-01T13:15:30Z",
    updatedBy: {
        objectId: "2046feea-040d-4a46-9e2b-91c2941bfa70",
    },
    workspaceName: "myWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

bookmark = azure_native.securityinsights.Bookmark("bookmark",
    bookmark_id="73e01a99-5cd7-4139-a149-9f2736ff2ab5",
    created="2019-01-01T13:15:30Z",
    created_by=azure_native.securityinsights.UserInfoArgs(
        object_id="2046feea-040d-4a46-9e2b-91c2941bfa70",
    ),
    display_name="My bookmark",
    labels=[
        "Tag1",
        "Tag2",
    ],
    notes="Found a suspicious activity",
    query="SecurityEvent | where TimeGenerated > ago(1d) and TimeGenerated < ago(2d)",
    query_result="Security Event query result",
    resource_group_name="myRg",
    updated="2019-01-01T13:15:30Z",
    updated_by=azure_native.securityinsights.UserInfoArgs(
        object_id="2046feea-040d-4a46-9e2b-91c2941bfa70",
    ),
    workspace_name="myWorkspace")

```

```yaml
resources:
  bookmark:
    type: azure-native:securityinsights:Bookmark
    properties:
      bookmarkId: 73e01a99-5cd7-4139-a149-9f2736ff2ab5
      created: 2019-01-01T13:15:30Z
      createdBy:
        objectId: 2046feea-040d-4a46-9e2b-91c2941bfa70
      displayName: My bookmark
      labels:
        - Tag1
        - Tag2
      notes: Found a suspicious activity
      query: SecurityEvent | where TimeGenerated > ago(1d) and TimeGenerated < ago(2d)
      queryResult: Security Event query result
      resourceGroupName: myRg
      updated: 2019-01-01T13:15:30Z
      updatedBy:
        objectId: 2046feea-040d-4a46-9e2b-91c2941bfa70
      workspaceName: myWorkspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:securityinsights:Bookmark 73e01a99-5cd7-4139-a149-9f2736ff2ab5 /subscriptions/d0cfe6b2-9ac0-4464-9919-dccaee2e48c0/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace/providers/Microsoft.SecurityInsights/bookmarks/73e01a99-5cd7-4139-a149-9f2736ff2ab5 
```
