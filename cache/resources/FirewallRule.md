A firewall rule on a redis cache has a name, and describes a contiguous range of IP addresses permitted to connect
API Version: 2022-06-01.
Previous API Version: 2020-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### RedisCacheFirewallRuleCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var firewallRule = new AzureNative.Cache.FirewallRule("firewallRule", new()
    {
        CacheName = "cache1",
        EndIP = "192.168.1.4",
        ResourceGroupName = "rg1",
        RuleName = "rule1",
        StartIP = "192.168.1.1",
    });

});


```

```go
package main

import (
	cache "github.com/pulumi/pulumi-azure-native-sdk/cache"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := cache.NewFirewallRule(ctx, "firewallRule", &cache.FirewallRuleArgs{
			CacheName:         pulumi.String("cache1"),
			EndIP:             pulumi.String("192.168.1.4"),
			ResourceGroupName: pulumi.String("rg1"),
			RuleName:          pulumi.String("rule1"),
			StartIP:           pulumi.String("192.168.1.1"),
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
import com.pulumi.azurenative.cache.FirewallRule;
import com.pulumi.azurenative.cache.FirewallRuleArgs;
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
        var firewallRule = new FirewallRule("firewallRule", FirewallRuleArgs.builder()        
            .cacheName("cache1")
            .endIP("192.168.1.4")
            .resourceGroupName("rg1")
            .ruleName("rule1")
            .startIP("192.168.1.1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const firewallRule = new azure_native.cache.FirewallRule("firewallRule", {
    cacheName: "cache1",
    endIP: "192.168.1.4",
    resourceGroupName: "rg1",
    ruleName: "rule1",
    startIP: "192.168.1.1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

firewall_rule = azure_native.cache.FirewallRule("firewallRule",
    cache_name="cache1",
    end_ip="192.168.1.4",
    resource_group_name="rg1",
    rule_name="rule1",
    start_ip="192.168.1.1")

```

```yaml
resources:
  firewallRule:
    type: azure-native:cache:FirewallRule
    properties:
      cacheName: cache1
      endIP: 192.168.1.4
      resourceGroupName: rg1
      ruleName: rule1
      startIP: 192.168.1.1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:cache:FirewallRule cache1/rule1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Cache/Redis/cache1/firewallRules/rule1 
```
