Represents a server firewall rule.
API Version: 2022-12-01.
Previous API Version: 2017-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### FirewallRuleCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var firewallRule = new AzureNative.DBforPostgreSQL.FirewallRule("firewallRule", new()
    {
        EndIpAddress = "255.255.255.255",
        FirewallRuleName = "rule1",
        ResourceGroupName = "testrg",
        ServerName = "testserver",
        StartIpAddress = "0.0.0.0",
    });

});


```

```go
package main

import (
	dbforpostgresql "github.com/pulumi/pulumi-azure-native-sdk/dbforpostgresql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := dbforpostgresql.NewFirewallRule(ctx, "firewallRule", &dbforpostgresql.FirewallRuleArgs{
			EndIpAddress:      pulumi.String("255.255.255.255"),
			FirewallRuleName:  pulumi.String("rule1"),
			ResourceGroupName: pulumi.String("testrg"),
			ServerName:        pulumi.String("testserver"),
			StartIpAddress:    pulumi.String("0.0.0.0"),
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
import com.pulumi.azurenative.dbforpostgresql.FirewallRule;
import com.pulumi.azurenative.dbforpostgresql.FirewallRuleArgs;
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
            .endIpAddress("255.255.255.255")
            .firewallRuleName("rule1")
            .resourceGroupName("testrg")
            .serverName("testserver")
            .startIpAddress("0.0.0.0")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const firewallRule = new azure_native.dbforpostgresql.FirewallRule("firewallRule", {
    endIpAddress: "255.255.255.255",
    firewallRuleName: "rule1",
    resourceGroupName: "testrg",
    serverName: "testserver",
    startIpAddress: "0.0.0.0",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

firewall_rule = azure_native.dbforpostgresql.FirewallRule("firewallRule",
    end_ip_address="255.255.255.255",
    firewall_rule_name="rule1",
    resource_group_name="testrg",
    server_name="testserver",
    start_ip_address="0.0.0.0")

```

```yaml
resources:
  firewallRule:
    type: azure-native:dbforpostgresql:FirewallRule
    properties:
      endIpAddress: 255.255.255.255
      firewallRuleName: rule1
      resourceGroupName: testrg
      serverName: testserver
      startIpAddress: 0.0.0.0

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:dbforpostgresql:FirewallRule rule1 /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/testrg/providers/Microsoft.DBforPostgreSQL/servers/testserver/firewallRules/rule1 
```
