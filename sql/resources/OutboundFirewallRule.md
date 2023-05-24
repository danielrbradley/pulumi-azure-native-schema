An Azure SQL DB Server Outbound Firewall Rule.
API Version: 2021-11-01.
Previous API Version: 2021-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Approve or reject a outbound firewall rule with a given name.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var outboundFirewallRule = new AzureNative.Sql.OutboundFirewallRule("outboundFirewallRule", new()
    {
        OutboundRuleFqdn = "server.database.windows.net",
        ResourceGroupName = "sqlcrudtest-7398",
        ServerName = "sqlcrudtest-4645",
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
		_, err := sql.NewOutboundFirewallRule(ctx, "outboundFirewallRule", &sql.OutboundFirewallRuleArgs{
			OutboundRuleFqdn:  pulumi.String("server.database.windows.net"),
			ResourceGroupName: pulumi.String("sqlcrudtest-7398"),
			ServerName:        pulumi.String("sqlcrudtest-4645"),
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
import com.pulumi.azurenative.sql.OutboundFirewallRule;
import com.pulumi.azurenative.sql.OutboundFirewallRuleArgs;
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
        var outboundFirewallRule = new OutboundFirewallRule("outboundFirewallRule", OutboundFirewallRuleArgs.builder()        
            .outboundRuleFqdn("server.database.windows.net")
            .resourceGroupName("sqlcrudtest-7398")
            .serverName("sqlcrudtest-4645")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const outboundFirewallRule = new azure_native.sql.OutboundFirewallRule("outboundFirewallRule", {
    outboundRuleFqdn: "server.database.windows.net",
    resourceGroupName: "sqlcrudtest-7398",
    serverName: "sqlcrudtest-4645",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

outbound_firewall_rule = azure_native.sql.OutboundFirewallRule("outboundFirewallRule",
    outbound_rule_fqdn="server.database.windows.net",
    resource_group_name="sqlcrudtest-7398",
    server_name="sqlcrudtest-4645")

```

```yaml
resources:
  outboundFirewallRule:
    type: azure-native:sql:OutboundFirewallRule
    properties:
      outboundRuleFqdn: server.database.windows.net
      resourceGroupName: sqlcrudtest-7398
      serverName: sqlcrudtest-4645

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:OutboundFirewallRule server.database.windows.net /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/sqlcrudtest-7398/providers/Microsoft.Sql/servers/sqlcrudtest-4645/outboundFirewallRules/server.datbase.windows.net 
```
