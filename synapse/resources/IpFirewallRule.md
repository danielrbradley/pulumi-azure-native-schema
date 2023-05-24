IP firewall rule
API Version: 2021-06-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create an IP firewall rule
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var ipFirewallRule = new AzureNative.Synapse.IpFirewallRule("ipFirewallRule", new()
    {
        EndIpAddress = "10.0.0.254",
        ResourceGroupName = "ExampleResourceGroup",
        RuleName = "ExampleIpFirewallRule",
        StartIpAddress = "10.0.0.0",
        WorkspaceName = "ExampleWorkspace",
    });

});


```

```go
package main

import (
	synapse "github.com/pulumi/pulumi-azure-native-sdk/synapse"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := synapse.NewIpFirewallRule(ctx, "ipFirewallRule", &synapse.IpFirewallRuleArgs{
			EndIpAddress:      pulumi.String("10.0.0.254"),
			ResourceGroupName: pulumi.String("ExampleResourceGroup"),
			RuleName:          pulumi.String("ExampleIpFirewallRule"),
			StartIpAddress:    pulumi.String("10.0.0.0"),
			WorkspaceName:     pulumi.String("ExampleWorkspace"),
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
import com.pulumi.azurenative.synapse.IpFirewallRule;
import com.pulumi.azurenative.synapse.IpFirewallRuleArgs;
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
        var ipFirewallRule = new IpFirewallRule("ipFirewallRule", IpFirewallRuleArgs.builder()        
            .endIpAddress("10.0.0.254")
            .resourceGroupName("ExampleResourceGroup")
            .ruleName("ExampleIpFirewallRule")
            .startIpAddress("10.0.0.0")
            .workspaceName("ExampleWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const ipFirewallRule = new azure_native.synapse.IpFirewallRule("ipFirewallRule", {
    endIpAddress: "10.0.0.254",
    resourceGroupName: "ExampleResourceGroup",
    ruleName: "ExampleIpFirewallRule",
    startIpAddress: "10.0.0.0",
    workspaceName: "ExampleWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

ip_firewall_rule = azure_native.synapse.IpFirewallRule("ipFirewallRule",
    end_ip_address="10.0.0.254",
    resource_group_name="ExampleResourceGroup",
    rule_name="ExampleIpFirewallRule",
    start_ip_address="10.0.0.0",
    workspace_name="ExampleWorkspace")

```

```yaml
resources:
  ipFirewallRule:
    type: azure-native:synapse:IpFirewallRule
    properties:
      endIpAddress: 10.0.0.254
      resourceGroupName: ExampleResourceGroup
      ruleName: ExampleIpFirewallRule
      startIpAddress: 10.0.0.0
      workspaceName: ExampleWorkspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:synapse:IpFirewallRule ExampleIpFirewallRule /subscriptions/01234567-89ab-4def-0123-456789abcdef/resourceGroups/ExampleResourceGroup/providers/Microsoft.Synapse/workspaces/ExampleWorkspace/firewallRules/ExampleIpFirewallRule 
```
