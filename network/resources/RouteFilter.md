Route Filter Resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### RouteFilterCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var routeFilter = new AzureNative.Network.RouteFilter("routeFilter", new()
    {
        Location = "West US",
        ResourceGroupName = "rg1",
        RouteFilterName = "filterName",
        Rules = new[]
        {
            new AzureNative.Network.Inputs.RouteFilterRuleArgs
            {
                Access = "Allow",
                Communities = new[]
                {
                    "12076:5030",
                    "12076:5040",
                },
                Name = "ruleName",
                RouteFilterRuleType = "Community",
            },
        },
        Tags = 
        {
            { "key1", "value1" },
        },
    });

});


```

```go
package main

import (
	network "github.com/pulumi/pulumi-azure-native-sdk/network"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := network.NewRouteFilter(ctx, "routeFilter", &network.RouteFilterArgs{
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("rg1"),
			RouteFilterName:   pulumi.String("filterName"),
			Rules: []network.RouteFilterRuleTypeArgs{
				{
					Access: pulumi.String("Allow"),
					Communities: pulumi.StringArray{
						pulumi.String("12076:5030"),
						pulumi.String("12076:5040"),
					},
					Name:                pulumi.String("ruleName"),
					RouteFilterRuleType: pulumi.String("Community"),
				},
			},
			Tags: pulumi.StringMap{
				"key1": pulumi.String("value1"),
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
import com.pulumi.azurenative.network.RouteFilter;
import com.pulumi.azurenative.network.RouteFilterArgs;
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
        var routeFilter = new RouteFilter("routeFilter", RouteFilterArgs.builder()        
            .location("West US")
            .resourceGroupName("rg1")
            .routeFilterName("filterName")
            .rules(Map.ofEntries(
                Map.entry("access", "Allow"),
                Map.entry("communities",                 
                    "12076:5030",
                    "12076:5040"),
                Map.entry("name", "ruleName"),
                Map.entry("routeFilterRuleType", "Community")
            ))
            .tags(Map.of("key1", "value1"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const routeFilter = new azure_native.network.RouteFilter("routeFilter", {
    location: "West US",
    resourceGroupName: "rg1",
    routeFilterName: "filterName",
    rules: [{
        access: "Allow",
        communities: [
            "12076:5030",
            "12076:5040",
        ],
        name: "ruleName",
        routeFilterRuleType: "Community",
    }],
    tags: {
        key1: "value1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

route_filter = azure_native.network.RouteFilter("routeFilter",
    location="West US",
    resource_group_name="rg1",
    route_filter_name="filterName",
    rules=[azure_native.network.RouteFilterRuleArgs(
        access="Allow",
        communities=[
            "12076:5030",
            "12076:5040",
        ],
        name="ruleName",
        route_filter_rule_type="Community",
    )],
    tags={
        "key1": "value1",
    })

```

```yaml
resources:
  routeFilter:
    type: azure-native:network:RouteFilter
    properties:
      location: West US
      resourceGroupName: rg1
      routeFilterName: filterName
      rules:
        - access: Allow
          communities:
            - 12076:5030
            - 12076:5040
          name: ruleName
          routeFilterRuleType: Community
      tags:
        key1: value1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:RouteFilter filterName /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/routeFilters/filterName 
```
