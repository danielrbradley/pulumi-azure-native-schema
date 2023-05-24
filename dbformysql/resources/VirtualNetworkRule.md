A virtual network rule.
API Version: 2017-12-01.
Previous API Version: 2017-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a virtual network rule
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualNetworkRule = new AzureNative.DBforMySQL.VirtualNetworkRule("virtualNetworkRule", new()
    {
        IgnoreMissingVnetServiceEndpoint = false,
        ResourceGroupName = "TestGroup",
        ServerName = "vnet-test-svr",
        VirtualNetworkRuleName = "vnet-firewall-rule",
        VirtualNetworkSubnetId = "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/TestGroup/providers/Microsoft.Network/virtualNetworks/testvnet/subnets/testsubnet",
    });

});


```

```go
package main

import (
	dbformysql "github.com/pulumi/pulumi-azure-native-sdk/dbformysql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := dbformysql.NewVirtualNetworkRule(ctx, "virtualNetworkRule", &dbformysql.VirtualNetworkRuleArgs{
			IgnoreMissingVnetServiceEndpoint: pulumi.Bool(false),
			ResourceGroupName:                pulumi.String("TestGroup"),
			ServerName:                       pulumi.String("vnet-test-svr"),
			VirtualNetworkRuleName:           pulumi.String("vnet-firewall-rule"),
			VirtualNetworkSubnetId:           pulumi.String("/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/TestGroup/providers/Microsoft.Network/virtualNetworks/testvnet/subnets/testsubnet"),
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
import com.pulumi.azurenative.dbformysql.VirtualNetworkRule;
import com.pulumi.azurenative.dbformysql.VirtualNetworkRuleArgs;
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
        var virtualNetworkRule = new VirtualNetworkRule("virtualNetworkRule", VirtualNetworkRuleArgs.builder()        
            .ignoreMissingVnetServiceEndpoint(false)
            .resourceGroupName("TestGroup")
            .serverName("vnet-test-svr")
            .virtualNetworkRuleName("vnet-firewall-rule")
            .virtualNetworkSubnetId("/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/TestGroup/providers/Microsoft.Network/virtualNetworks/testvnet/subnets/testsubnet")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualNetworkRule = new azure_native.dbformysql.VirtualNetworkRule("virtualNetworkRule", {
    ignoreMissingVnetServiceEndpoint: false,
    resourceGroupName: "TestGroup",
    serverName: "vnet-test-svr",
    virtualNetworkRuleName: "vnet-firewall-rule",
    virtualNetworkSubnetId: "/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/TestGroup/providers/Microsoft.Network/virtualNetworks/testvnet/subnets/testsubnet",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_network_rule = azure_native.dbformysql.VirtualNetworkRule("virtualNetworkRule",
    ignore_missing_vnet_service_endpoint=False,
    resource_group_name="TestGroup",
    server_name="vnet-test-svr",
    virtual_network_rule_name="vnet-firewall-rule",
    virtual_network_subnet_id="/subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/TestGroup/providers/Microsoft.Network/virtualNetworks/testvnet/subnets/testsubnet")

```

```yaml
resources:
  virtualNetworkRule:
    type: azure-native:dbformysql:VirtualNetworkRule
    properties:
      ignoreMissingVnetServiceEndpoint: false
      resourceGroupName: TestGroup
      serverName: vnet-test-svr
      virtualNetworkRuleName: vnet-firewall-rule
      virtualNetworkSubnetId: /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/TestGroup/providers/Microsoft.Network/virtualNetworks/testvnet/subnets/testsubnet

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:dbformysql:VirtualNetworkRule vnet-firewall-rule /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/TestGroup/providers/Microsoft.DBforMySQL/servers/vnet-test-svr/virtualNetworkRules/vnet-firewall-rule 
```
