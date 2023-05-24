Network security rule.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create security rule
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var securityRule = new AzureNative.Network.SecurityRule("securityRule", new()
    {
        Access = "Deny",
        DestinationAddressPrefix = "11.0.0.0/8",
        DestinationPortRange = "8080",
        Direction = "Outbound",
        NetworkSecurityGroupName = "testnsg",
        Priority = 100,
        Protocol = "*",
        ResourceGroupName = "rg1",
        SecurityRuleName = "rule1",
        SourceAddressPrefix = "10.0.0.0/8",
        SourcePortRange = "*",
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
		_, err := network.NewSecurityRule(ctx, "securityRule", &network.SecurityRuleArgs{
			Access:                   pulumi.String("Deny"),
			DestinationAddressPrefix: pulumi.String("11.0.0.0/8"),
			DestinationPortRange:     pulumi.String("8080"),
			Direction:                pulumi.String("Outbound"),
			NetworkSecurityGroupName: pulumi.String("testnsg"),
			Priority:                 pulumi.Int(100),
			Protocol:                 pulumi.String("*"),
			ResourceGroupName:        pulumi.String("rg1"),
			SecurityRuleName:         pulumi.String("rule1"),
			SourceAddressPrefix:      pulumi.String("10.0.0.0/8"),
			SourcePortRange:          pulumi.String("*"),
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
import com.pulumi.azurenative.network.SecurityRule;
import com.pulumi.azurenative.network.SecurityRuleArgs;
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
        var securityRule = new SecurityRule("securityRule", SecurityRuleArgs.builder()        
            .access("Deny")
            .destinationAddressPrefix("11.0.0.0/8")
            .destinationPortRange("8080")
            .direction("Outbound")
            .networkSecurityGroupName("testnsg")
            .priority(100)
            .protocol("*")
            .resourceGroupName("rg1")
            .securityRuleName("rule1")
            .sourceAddressPrefix("10.0.0.0/8")
            .sourcePortRange("*")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const securityRule = new azure_native.network.SecurityRule("securityRule", {
    access: "Deny",
    destinationAddressPrefix: "11.0.0.0/8",
    destinationPortRange: "8080",
    direction: "Outbound",
    networkSecurityGroupName: "testnsg",
    priority: 100,
    protocol: "*",
    resourceGroupName: "rg1",
    securityRuleName: "rule1",
    sourceAddressPrefix: "10.0.0.0/8",
    sourcePortRange: "*",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

security_rule = azure_native.network.SecurityRule("securityRule",
    access="Deny",
    destination_address_prefix="11.0.0.0/8",
    destination_port_range="8080",
    direction="Outbound",
    network_security_group_name="testnsg",
    priority=100,
    protocol="*",
    resource_group_name="rg1",
    security_rule_name="rule1",
    source_address_prefix="10.0.0.0/8",
    source_port_range="*")

```

```yaml
resources:
  securityRule:
    type: azure-native:network:SecurityRule
    properties:
      access: Deny
      destinationAddressPrefix: 11.0.0.0/8
      destinationPortRange: '8080'
      direction: Outbound
      networkSecurityGroupName: testnsg
      priority: 100
      protocol: '*'
      resourceGroupName: rg1
      securityRuleName: rule1
      sourceAddressPrefix: 10.0.0.0/8
      sourcePortRange: '*'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:SecurityRule rule1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/networkSecurityGroups/testnsg/securityRules/rule1 
```
