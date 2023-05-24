A server firewall rule.
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a firewall rule max/min
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var firewallRule = new AzureNative.Sql.FirewallRule("firewallRule", new()
    {
        EndIpAddress = "0.0.0.3",
        FirewallRuleName = "firewallrulecrudtest-5370",
        ResourceGroupName = "firewallrulecrudtest-12",
        ServerName = "firewallrulecrudtest-6285",
        StartIpAddress = "0.0.0.3",
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
		_, err := sql.NewFirewallRule(ctx, "firewallRule", &sql.FirewallRuleArgs{
			EndIpAddress:      pulumi.String("0.0.0.3"),
			FirewallRuleName:  pulumi.String("firewallrulecrudtest-5370"),
			ResourceGroupName: pulumi.String("firewallrulecrudtest-12"),
			ServerName:        pulumi.String("firewallrulecrudtest-6285"),
			StartIpAddress:    pulumi.String("0.0.0.3"),
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
import com.pulumi.azurenative.sql.FirewallRule;
import com.pulumi.azurenative.sql.FirewallRuleArgs;
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
            .endIpAddress("0.0.0.3")
            .firewallRuleName("firewallrulecrudtest-5370")
            .resourceGroupName("firewallrulecrudtest-12")
            .serverName("firewallrulecrudtest-6285")
            .startIpAddress("0.0.0.3")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const firewallRule = new azure_native.sql.FirewallRule("firewallRule", {
    endIpAddress: "0.0.0.3",
    firewallRuleName: "firewallrulecrudtest-5370",
    resourceGroupName: "firewallrulecrudtest-12",
    serverName: "firewallrulecrudtest-6285",
    startIpAddress: "0.0.0.3",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

firewall_rule = azure_native.sql.FirewallRule("firewallRule",
    end_ip_address="0.0.0.3",
    firewall_rule_name="firewallrulecrudtest-5370",
    resource_group_name="firewallrulecrudtest-12",
    server_name="firewallrulecrudtest-6285",
    start_ip_address="0.0.0.3")

```

```yaml
resources:
  firewallRule:
    type: azure-native:sql:FirewallRule
    properties:
      endIpAddress: 0.0.0.3
      firewallRuleName: firewallrulecrudtest-5370
      resourceGroupName: firewallrulecrudtest-12
      serverName: firewallrulecrudtest-6285
      startIpAddress: 0.0.0.3

```

{{% /example %}}
{{% example %}}
### Update a firewall rule max/min
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var firewallRule = new AzureNative.Sql.FirewallRule("firewallRule", new()
    {
        EndIpAddress = "0.0.0.1",
        FirewallRuleName = "firewallrulecrudtest-3927",
        ResourceGroupName = "firewallrulecrudtest-12",
        ServerName = "firewallrulecrudtest-6285",
        StartIpAddress = "0.0.0.1",
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
		_, err := sql.NewFirewallRule(ctx, "firewallRule", &sql.FirewallRuleArgs{
			EndIpAddress:      pulumi.String("0.0.0.1"),
			FirewallRuleName:  pulumi.String("firewallrulecrudtest-3927"),
			ResourceGroupName: pulumi.String("firewallrulecrudtest-12"),
			ServerName:        pulumi.String("firewallrulecrudtest-6285"),
			StartIpAddress:    pulumi.String("0.0.0.1"),
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
import com.pulumi.azurenative.sql.FirewallRule;
import com.pulumi.azurenative.sql.FirewallRuleArgs;
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
            .endIpAddress("0.0.0.1")
            .firewallRuleName("firewallrulecrudtest-3927")
            .resourceGroupName("firewallrulecrudtest-12")
            .serverName("firewallrulecrudtest-6285")
            .startIpAddress("0.0.0.1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const firewallRule = new azure_native.sql.FirewallRule("firewallRule", {
    endIpAddress: "0.0.0.1",
    firewallRuleName: "firewallrulecrudtest-3927",
    resourceGroupName: "firewallrulecrudtest-12",
    serverName: "firewallrulecrudtest-6285",
    startIpAddress: "0.0.0.1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

firewall_rule = azure_native.sql.FirewallRule("firewallRule",
    end_ip_address="0.0.0.1",
    firewall_rule_name="firewallrulecrudtest-3927",
    resource_group_name="firewallrulecrudtest-12",
    server_name="firewallrulecrudtest-6285",
    start_ip_address="0.0.0.1")

```

```yaml
resources:
  firewallRule:
    type: azure-native:sql:FirewallRule
    properties:
      endIpAddress: 0.0.0.1
      firewallRuleName: firewallrulecrudtest-3927
      resourceGroupName: firewallrulecrudtest-12
      serverName: firewallrulecrudtest-6285
      startIpAddress: 0.0.0.1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:FirewallRule firewallrulecrudtest-3927 /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/firewallrulecrudtest-12/providers/Microsoft.Sql/servers/firewallrulecrudtest-6285/firewallRules/firewallrulecrudtest-3927 
```
