Data Lake Analytics firewall rule information.
API Version: 2019-11-01-preview.
Previous API Version: 2016-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates or updates the specified firewall rule
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var firewallRule = new AzureNative.DataLakeAnalytics.FirewallRule("firewallRule", new()
    {
        AccountName = "contosoadla",
        EndIpAddress = "2.2.2.2",
        FirewallRuleName = "test_rule",
        ResourceGroupName = "contosorg",
        StartIpAddress = "1.1.1.1",
    });

});


```

```go
package main

import (
	datalakeanalytics "github.com/pulumi/pulumi-azure-native-sdk/datalakeanalytics"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := datalakeanalytics.NewFirewallRule(ctx, "firewallRule", &datalakeanalytics.FirewallRuleArgs{
			AccountName:       pulumi.String("contosoadla"),
			EndIpAddress:      pulumi.String("2.2.2.2"),
			FirewallRuleName:  pulumi.String("test_rule"),
			ResourceGroupName: pulumi.String("contosorg"),
			StartIpAddress:    pulumi.String("1.1.1.1"),
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
import com.pulumi.azurenative.datalakeanalytics.FirewallRule;
import com.pulumi.azurenative.datalakeanalytics.FirewallRuleArgs;
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
            .accountName("contosoadla")
            .endIpAddress("2.2.2.2")
            .firewallRuleName("test_rule")
            .resourceGroupName("contosorg")
            .startIpAddress("1.1.1.1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const firewallRule = new azure_native.datalakeanalytics.FirewallRule("firewallRule", {
    accountName: "contosoadla",
    endIpAddress: "2.2.2.2",
    firewallRuleName: "test_rule",
    resourceGroupName: "contosorg",
    startIpAddress: "1.1.1.1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

firewall_rule = azure_native.datalakeanalytics.FirewallRule("firewallRule",
    account_name="contosoadla",
    end_ip_address="2.2.2.2",
    firewall_rule_name="test_rule",
    resource_group_name="contosorg",
    start_ip_address="1.1.1.1")

```

```yaml
resources:
  firewallRule:
    type: azure-native:datalakeanalytics:FirewallRule
    properties:
      accountName: contosoadla
      endIpAddress: 2.2.2.2
      firewallRuleName: test_rule
      resourceGroupName: contosorg
      startIpAddress: 1.1.1.1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:datalakeanalytics:FirewallRule test_rule 34adfa4f-cedf-4dc0-ba29-b6d1a69ab345 
```
