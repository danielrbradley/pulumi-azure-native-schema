Route Filter Rule Resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### RouteFilterRuleCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var routeFilterRule = new AzureNative.Network.RouteFilterRule("routeFilterRule", new()
    {
        Access = "Allow",
        Communities = new[]
        {
            "12076:5030",
            "12076:5040",
        },
        ResourceGroupName = "rg1",
        RouteFilterName = "filterName",
        RouteFilterRuleType = "Community",
        RuleName = "ruleName",
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
		_, err := network.NewRouteFilterRule(ctx, "routeFilterRule", &network.RouteFilterRuleArgs{
			Access: pulumi.String("Allow"),
			Communities: pulumi.StringArray{
				pulumi.String("12076:5030"),
				pulumi.String("12076:5040"),
			},
			ResourceGroupName:   pulumi.String("rg1"),
			RouteFilterName:     pulumi.String("filterName"),
			RouteFilterRuleType: pulumi.String("Community"),
			RuleName:            pulumi.String("ruleName"),
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
import com.pulumi.azurenative.network.RouteFilterRule;
import com.pulumi.azurenative.network.RouteFilterRuleArgs;
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
        var routeFilterRule = new RouteFilterRule("routeFilterRule", RouteFilterRuleArgs.builder()        
            .access("Allow")
            .communities(            
                "12076:5030",
                "12076:5040")
            .resourceGroupName("rg1")
            .routeFilterName("filterName")
            .routeFilterRuleType("Community")
            .ruleName("ruleName")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const routeFilterRule = new azure_native.network.RouteFilterRule("routeFilterRule", {
    access: "Allow",
    communities: [
        "12076:5030",
        "12076:5040",
    ],
    resourceGroupName: "rg1",
    routeFilterName: "filterName",
    routeFilterRuleType: "Community",
    ruleName: "ruleName",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

route_filter_rule = azure_native.network.RouteFilterRule("routeFilterRule",
    access="Allow",
    communities=[
        "12076:5030",
        "12076:5040",
    ],
    resource_group_name="rg1",
    route_filter_name="filterName",
    route_filter_rule_type="Community",
    rule_name="ruleName")

```

```yaml
resources:
  routeFilterRule:
    type: azure-native:network:RouteFilterRule
    properties:
      access: Allow
      communities:
        - 12076:5030
        - 12076:5040
      resourceGroupName: rg1
      routeFilterName: filterName
      routeFilterRuleType: Community
      ruleName: ruleName

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:RouteFilterRule ruleName /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/routeFilters/filterName/routeFilterRules/ruleName 
```
