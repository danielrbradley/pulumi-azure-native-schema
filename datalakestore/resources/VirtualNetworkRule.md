Data Lake Store virtual network rule information.
API Version: 2016-11-01.
Previous API Version: 2016-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates or updates the specified virtual network rule. During update, the virtual network rule with the specified name will be replaced with this new virtual network rule.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualNetworkRule = new AzureNative.DataLakeStore.VirtualNetworkRule("virtualNetworkRule", new()
    {
        AccountName = "contosoadla",
        ResourceGroupName = "contosorg",
        SubnetId = "test_subnetId",
        VirtualNetworkRuleName = "test_virtual_network_rules_name",
    });

});


```

```go
package main

import (
	datalakestore "github.com/pulumi/pulumi-azure-native-sdk/datalakestore"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := datalakestore.NewVirtualNetworkRule(ctx, "virtualNetworkRule", &datalakestore.VirtualNetworkRuleArgs{
			AccountName:            pulumi.String("contosoadla"),
			ResourceGroupName:      pulumi.String("contosorg"),
			SubnetId:               pulumi.String("test_subnetId"),
			VirtualNetworkRuleName: pulumi.String("test_virtual_network_rules_name"),
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
import com.pulumi.azurenative.datalakestore.VirtualNetworkRule;
import com.pulumi.azurenative.datalakestore.VirtualNetworkRuleArgs;
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
            .accountName("contosoadla")
            .resourceGroupName("contosorg")
            .subnetId("test_subnetId")
            .virtualNetworkRuleName("test_virtual_network_rules_name")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualNetworkRule = new azure_native.datalakestore.VirtualNetworkRule("virtualNetworkRule", {
    accountName: "contosoadla",
    resourceGroupName: "contosorg",
    subnetId: "test_subnetId",
    virtualNetworkRuleName: "test_virtual_network_rules_name",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_network_rule = azure_native.datalakestore.VirtualNetworkRule("virtualNetworkRule",
    account_name="contosoadla",
    resource_group_name="contosorg",
    subnet_id="test_subnetId",
    virtual_network_rule_name="test_virtual_network_rules_name")

```

```yaml
resources:
  virtualNetworkRule:
    type: azure-native:datalakestore:VirtualNetworkRule
    properties:
      accountName: contosoadla
      resourceGroupName: contosorg
      subnetId: test_subnetId
      virtualNetworkRuleName: test_virtual_network_rules_name

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:datalakestore:VirtualNetworkRule test_virtual_network_rules_name 34adfa4f-cedf-4dc0-ba29-b6d1a69ab345 
```
