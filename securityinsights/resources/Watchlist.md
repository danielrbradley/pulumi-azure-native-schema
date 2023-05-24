Represents a Watchlist in Azure Security Insights.
API Version: 2023-02-01.
Previous API Version: 2021-03-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a watchlist and bulk creates watchlist items.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var watchlist = new AzureNative.SecurityInsights.Watchlist("watchlist", new()
    {
        ContentType = "text/csv",
        Description = "Watchlist from CSV content",
        DisplayName = "High Value Assets Watchlist",
        ItemsSearchKey = "header1",
        NumberOfLinesToSkip = 1,
        Provider = "Microsoft",
        RawContent = @"This line will be skipped
header1,header2
value1,value2",
        ResourceGroupName = "myRg",
        Source = "Local file",
        WatchlistAlias = "highValueAsset",
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
		_, err := securityinsights.NewWatchlist(ctx, "watchlist", &securityinsights.WatchlistArgs{
			ContentType:         pulumi.String("text/csv"),
			Description:         pulumi.String("Watchlist from CSV content"),
			DisplayName:         pulumi.String("High Value Assets Watchlist"),
			ItemsSearchKey:      pulumi.String("header1"),
			NumberOfLinesToSkip: pulumi.Int(1),
			Provider:            pulumi.String("Microsoft"),
			RawContent:          pulumi.String("This line will be skipped\nheader1,header2\nvalue1,value2"),
			ResourceGroupName:   pulumi.String("myRg"),
			Source:              pulumi.String("Local file"),
			WatchlistAlias:      pulumi.String("highValueAsset"),
			WorkspaceName:       pulumi.String("myWorkspace"),
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
import com.pulumi.azurenative.securityinsights.Watchlist;
import com.pulumi.azurenative.securityinsights.WatchlistArgs;
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
        var watchlist = new Watchlist("watchlist", WatchlistArgs.builder()        
            .contentType("text/csv")
            .description("Watchlist from CSV content")
            .displayName("High Value Assets Watchlist")
            .itemsSearchKey("header1")
            .numberOfLinesToSkip(1)
            .provider("Microsoft")
            .rawContent("""
This line will be skipped
header1,header2
value1,value2            """)
            .resourceGroupName("myRg")
            .source("Local file")
            .watchlistAlias("highValueAsset")
            .workspaceName("myWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const watchlist = new azure_native.securityinsights.Watchlist("watchlist", {
    contentType: "text/csv",
    description: "Watchlist from CSV content",
    displayName: "High Value Assets Watchlist",
    itemsSearchKey: "header1",
    numberOfLinesToSkip: 1,
    provider: "Microsoft",
    rawContent: `This line will be skipped
header1,header2
value1,value2`,
    resourceGroupName: "myRg",
    source: "Local file",
    watchlistAlias: "highValueAsset",
    workspaceName: "myWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

watchlist = azure_native.securityinsights.Watchlist("watchlist",
    content_type="text/csv",
    description="Watchlist from CSV content",
    display_name="High Value Assets Watchlist",
    items_search_key="header1",
    number_of_lines_to_skip=1,
    provider="Microsoft",
    raw_content="""This line will be skipped
header1,header2
value1,value2""",
    resource_group_name="myRg",
    source="Local file",
    watchlist_alias="highValueAsset",
    workspace_name="myWorkspace")

```

```yaml
resources:
  watchlist:
    type: azure-native:securityinsights:Watchlist
    properties:
      contentType: text/csv
      description: Watchlist from CSV content
      displayName: High Value Assets Watchlist
      itemsSearchKey: header1
      numberOfLinesToSkip: 1
      provider: Microsoft
      rawContent: |-
        This line will be skipped
        header1,header2
        value1,value2
      resourceGroupName: myRg
      source: Local file
      watchlistAlias: highValueAsset
      workspaceName: myWorkspace

```

{{% /example %}}
{{% example %}}
### Create or update a watchlist.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var watchlist = new AzureNative.SecurityInsights.Watchlist("watchlist", new()
    {
        Description = "Watchlist from CSV content",
        DisplayName = "High Value Assets Watchlist",
        ItemsSearchKey = "header1",
        Provider = "Microsoft",
        ResourceGroupName = "myRg",
        Source = "Local file",
        WatchlistAlias = "highValueAsset",
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
		_, err := securityinsights.NewWatchlist(ctx, "watchlist", &securityinsights.WatchlistArgs{
			Description:       pulumi.String("Watchlist from CSV content"),
			DisplayName:       pulumi.String("High Value Assets Watchlist"),
			ItemsSearchKey:    pulumi.String("header1"),
			Provider:          pulumi.String("Microsoft"),
			ResourceGroupName: pulumi.String("myRg"),
			Source:            pulumi.String("Local file"),
			WatchlistAlias:    pulumi.String("highValueAsset"),
			WorkspaceName:     pulumi.String("myWorkspace"),
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
import com.pulumi.azurenative.securityinsights.Watchlist;
import com.pulumi.azurenative.securityinsights.WatchlistArgs;
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
        var watchlist = new Watchlist("watchlist", WatchlistArgs.builder()        
            .description("Watchlist from CSV content")
            .displayName("High Value Assets Watchlist")
            .itemsSearchKey("header1")
            .provider("Microsoft")
            .resourceGroupName("myRg")
            .source("Local file")
            .watchlistAlias("highValueAsset")
            .workspaceName("myWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const watchlist = new azure_native.securityinsights.Watchlist("watchlist", {
    description: "Watchlist from CSV content",
    displayName: "High Value Assets Watchlist",
    itemsSearchKey: "header1",
    provider: "Microsoft",
    resourceGroupName: "myRg",
    source: "Local file",
    watchlistAlias: "highValueAsset",
    workspaceName: "myWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

watchlist = azure_native.securityinsights.Watchlist("watchlist",
    description="Watchlist from CSV content",
    display_name="High Value Assets Watchlist",
    items_search_key="header1",
    provider="Microsoft",
    resource_group_name="myRg",
    source="Local file",
    watchlist_alias="highValueAsset",
    workspace_name="myWorkspace")

```

```yaml
resources:
  watchlist:
    type: azure-native:securityinsights:Watchlist
    properties:
      description: Watchlist from CSV content
      displayName: High Value Assets Watchlist
      itemsSearchKey: header1
      provider: Microsoft
      resourceGroupName: myRg
      source: Local file
      watchlistAlias: highValueAsset
      workspaceName: myWorkspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:securityinsights:Watchlist highValueAsset /subscriptions/d0cfe6b2-9ac0-4464-9919-dccaee2e48c0/resourceGroups/myRg/providers/Microsoft.OperationalIinsights/workspaces/myWorkspace/providers/Microsoft.SecurityInsights/watchlists/highValueAsset 
```
