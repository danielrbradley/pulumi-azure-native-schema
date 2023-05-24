An IPv6 server firewall rule.
API Version: 2021-11-01.
Previous API Version: 2021-08-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create an IPv6 firewall rule max/min
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var iPv6FirewallRule = new AzureNative.Sql.IPv6FirewallRule("iPv6FirewallRule", new()
    {
        EndIPv6Address = "0000:0000:0000:0000:0000:ffff:0000:0003",
        FirewallRuleName = "firewallrulecrudtest-5370",
        ResourceGroupName = "firewallrulecrudtest-12",
        ServerName = "firewallrulecrudtest-6285",
        StartIPv6Address = "0000:0000:0000:0000:0000:ffff:0000:0003",
    });

});


```

```go
package main

import (
	sql "github.com/pulumi/pulumi-azure-native-sdk/sql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := sql.NewIPv6FirewallRule(ctx, "iPv6FirewallRule", &sql.IPv6FirewallRuleArgs{
			EndIPv6Address:    pulumi.String("0000:0000:0000:0000:0000:ffff:0000:0003"),
			FirewallRuleName:  pulumi.String("firewallrulecrudtest-5370"),
			ResourceGroupName: pulumi.String("firewallrulecrudtest-12"),
			ServerName:        pulumi.String("firewallrulecrudtest-6285"),
			StartIPv6Address:  pulumi.String("0000:0000:0000:0000:0000:ffff:0000:0003"),
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
import com.pulumi.azurenative.sql.IPv6FirewallRule;
import com.pulumi.azurenative.sql.IPv6FirewallRuleArgs;
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
        var iPv6FirewallRule = new IPv6FirewallRule("iPv6FirewallRule", IPv6FirewallRuleArgs.builder()        
            .endIPv6Address("0000:0000:0000:0000:0000:ffff:0000:0003")
            .firewallRuleName("firewallrulecrudtest-5370")
            .resourceGroupName("firewallrulecrudtest-12")
            .serverName("firewallrulecrudtest-6285")
            .startIPv6Address("0000:0000:0000:0000:0000:ffff:0000:0003")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const iPv6FirewallRule = new azure_native.sql.IPv6FirewallRule("iPv6FirewallRule", {
    endIPv6Address: "0000:0000:0000:0000:0000:ffff:0000:0003",
    firewallRuleName: "firewallrulecrudtest-5370",
    resourceGroupName: "firewallrulecrudtest-12",
    serverName: "firewallrulecrudtest-6285",
    startIPv6Address: "0000:0000:0000:0000:0000:ffff:0000:0003",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

i_pv6_firewall_rule = azure_native.sql.IPv6FirewallRule("iPv6FirewallRule",
    end_i_pv6_address="0000:0000:0000:0000:0000:ffff:0000:0003",
    firewall_rule_name="firewallrulecrudtest-5370",
    resource_group_name="firewallrulecrudtest-12",
    server_name="firewallrulecrudtest-6285",
    start_i_pv6_address="0000:0000:0000:0000:0000:ffff:0000:0003")

```

```yaml
resources:
  iPv6FirewallRule:
    type: azure-native:sql:IPv6FirewallRule
    properties:
      endIPv6Address: 0000:0000:0000:0000:0000:ffff:0000:0003
      firewallRuleName: firewallrulecrudtest-5370
      resourceGroupName: firewallrulecrudtest-12
      serverName: firewallrulecrudtest-6285
      startIPv6Address: 0000:0000:0000:0000:0000:ffff:0000:0003

```

{{% /example %}}
{{% example %}}
### Update an IPv6 firewall rule max/min
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var iPv6FirewallRule = new AzureNative.Sql.IPv6FirewallRule("iPv6FirewallRule", new()
    {
        EndIPv6Address = "0000:0000:0000:0000:0000:ffff:0000:0001",
        FirewallRuleName = "firewallrulecrudtest-3927",
        ResourceGroupName = "firewallrulecrudtest-12",
        ServerName = "firewallrulecrudtest-6285",
        StartIPv6Address = "0000:0000:0000:0000:0000:ffff:0000:0001",
    });

});


```

```go
package main

import (
	sql "github.com/pulumi/pulumi-azure-native-sdk/sql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := sql.NewIPv6FirewallRule(ctx, "iPv6FirewallRule", &sql.IPv6FirewallRuleArgs{
			EndIPv6Address:    pulumi.String("0000:0000:0000:0000:0000:ffff:0000:0001"),
			FirewallRuleName:  pulumi.String("firewallrulecrudtest-3927"),
			ResourceGroupName: pulumi.String("firewallrulecrudtest-12"),
			ServerName:        pulumi.String("firewallrulecrudtest-6285"),
			StartIPv6Address:  pulumi.String("0000:0000:0000:0000:0000:ffff:0000:0001"),
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
import com.pulumi.azurenative.sql.IPv6FirewallRule;
import com.pulumi.azurenative.sql.IPv6FirewallRuleArgs;
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
        var iPv6FirewallRule = new IPv6FirewallRule("iPv6FirewallRule", IPv6FirewallRuleArgs.builder()        
            .endIPv6Address("0000:0000:0000:0000:0000:ffff:0000:0001")
            .firewallRuleName("firewallrulecrudtest-3927")
            .resourceGroupName("firewallrulecrudtest-12")
            .serverName("firewallrulecrudtest-6285")
            .startIPv6Address("0000:0000:0000:0000:0000:ffff:0000:0001")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const iPv6FirewallRule = new azure_native.sql.IPv6FirewallRule("iPv6FirewallRule", {
    endIPv6Address: "0000:0000:0000:0000:0000:ffff:0000:0001",
    firewallRuleName: "firewallrulecrudtest-3927",
    resourceGroupName: "firewallrulecrudtest-12",
    serverName: "firewallrulecrudtest-6285",
    startIPv6Address: "0000:0000:0000:0000:0000:ffff:0000:0001",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

i_pv6_firewall_rule = azure_native.sql.IPv6FirewallRule("iPv6FirewallRule",
    end_i_pv6_address="0000:0000:0000:0000:0000:ffff:0000:0001",
    firewall_rule_name="firewallrulecrudtest-3927",
    resource_group_name="firewallrulecrudtest-12",
    server_name="firewallrulecrudtest-6285",
    start_i_pv6_address="0000:0000:0000:0000:0000:ffff:0000:0001")

```

```yaml
resources:
  iPv6FirewallRule:
    type: azure-native:sql:IPv6FirewallRule
    properties:
      endIPv6Address: 0000:0000:0000:0000:0000:ffff:0000:0001
      firewallRuleName: firewallrulecrudtest-3927
      resourceGroupName: firewallrulecrudtest-12
      serverName: firewallrulecrudtest-6285
      startIPv6Address: 0000:0000:0000:0000:0000:ffff:0000:0001

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:IPv6FirewallRule firewallrulecrudtest-3927 /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/firewallrulecrudtest-12/providers/Microsoft.Sql/servers/firewallrulecrudtest-6285/ipv6FirewallRules/firewallrulecrudtest-3927 
```
