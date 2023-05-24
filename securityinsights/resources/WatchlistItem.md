Represents a Watchlist Item in Azure Security Insights.
API Version: 2023-02-01.
Previous API Version: 2021-03-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a watchlist item.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var watchlistItem = new AzureNative.SecurityInsights.WatchlistItem("watchlistItem", new()
    {
        ItemsKeyValue = 
        {
            { "Business tier", "10.0.2.0/24" },
            { "Data tier", "10.0.2.0/24" },
            { "Gateway subnet", "10.0.255.224/27" },
            { "Private DMZ in", "10.0.0.0/27" },
            { "Public DMZ out", "10.0.0.96/27" },
            { "Web Tier", "10.0.1.0/24" },
        },
        ResourceGroupName = "myRg",
        WatchlistAlias = "highValueAsset",
        WatchlistItemId = "82ba292c-dc97-4dfc-969d-d4dd9e666842",
        WorkspaceName = "myWorkspace",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.securityinsights.WatchlistItem;
import com.pulumi.azurenative.securityinsights.WatchlistItemArgs;
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
        var watchlistItem = new WatchlistItem("watchlistItem", WatchlistItemArgs.builder()        
            .itemsKeyValue(Map.ofEntries(
                Map.entry("Business tier", "10.0.2.0/24"),
                Map.entry("Data tier", "10.0.2.0/24"),
                Map.entry("Gateway subnet", "10.0.255.224/27"),
                Map.entry("Private DMZ in", "10.0.0.0/27"),
                Map.entry("Public DMZ out", "10.0.0.96/27"),
                Map.entry("Web Tier", "10.0.1.0/24")
            ))
            .resourceGroupName("myRg")
            .watchlistAlias("highValueAsset")
            .watchlistItemId("82ba292c-dc97-4dfc-969d-d4dd9e666842")
            .workspaceName("myWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const watchlistItem = new azure_native.securityinsights.WatchlistItem("watchlistItem", {
    itemsKeyValue: {
        "Business tier": "10.0.2.0/24",
        "Data tier": "10.0.2.0/24",
        "Gateway subnet": "10.0.255.224/27",
        "Private DMZ in": "10.0.0.0/27",
        "Public DMZ out": "10.0.0.96/27",
        "Web Tier": "10.0.1.0/24",
    },
    resourceGroupName: "myRg",
    watchlistAlias: "highValueAsset",
    watchlistItemId: "82ba292c-dc97-4dfc-969d-d4dd9e666842",
    workspaceName: "myWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

watchlist_item = azure_native.securityinsights.WatchlistItem("watchlistItem",
    items_key_value={
        "Business tier": "10.0.2.0/24",
        "Data tier": "10.0.2.0/24",
        "Gateway subnet": "10.0.255.224/27",
        "Private DMZ in": "10.0.0.0/27",
        "Public DMZ out": "10.0.0.96/27",
        "Web Tier": "10.0.1.0/24",
    },
    resource_group_name="myRg",
    watchlist_alias="highValueAsset",
    watchlist_item_id="82ba292c-dc97-4dfc-969d-d4dd9e666842",
    workspace_name="myWorkspace")

```

```yaml
resources:
  watchlistItem:
    type: azure-native:securityinsights:WatchlistItem
    properties:
      itemsKeyValue:
        Business tier: 10.0.2.0/24
        Data tier: 10.0.2.0/24
        Gateway subnet: 10.0.255.224/27
        Private DMZ in: 10.0.0.0/27
        Public DMZ out: 10.0.0.96/27
        Web Tier: 10.0.1.0/24
      resourceGroupName: myRg
      watchlistAlias: highValueAsset
      watchlistItemId: 82ba292c-dc97-4dfc-969d-d4dd9e666842
      workspaceName: myWorkspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:securityinsights:WatchlistItem myresource1 /subscriptions/d0cfe6b2-9ac0-4464-9919-dccaee2e48c0/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace/providers/Microsoft.SecurityInsights/Watchlists/highValueAsset/WatchlistItems/82ba292c-dc97-4dfc-969d-d4dd9e666842 
```
