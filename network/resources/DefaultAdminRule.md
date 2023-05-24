Network default admin rule.
API Version: 2022-09-01.
Previous API Version: 2021-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a default admin rule
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var defaultAdminRule = new AzureNative.Network.DefaultAdminRule("defaultAdminRule", new()
    {
        ConfigurationName = "myTestSecurityConfig",
        Flag = "AllowVnetInbound",
        Kind = "Default",
        NetworkManagerName = "testNetworkManager",
        ResourceGroupName = "rg1",
        RuleCollectionName = "testRuleCollection",
        RuleName = "SampleDefaultAdminRule",
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
		_, err := network.NewDefaultAdminRule(ctx, "defaultAdminRule", &network.DefaultAdminRuleArgs{
			ConfigurationName:  pulumi.String("myTestSecurityConfig"),
			Flag:               pulumi.String("AllowVnetInbound"),
			Kind:               pulumi.String("Default"),
			NetworkManagerName: pulumi.String("testNetworkManager"),
			ResourceGroupName:  pulumi.String("rg1"),
			RuleCollectionName: pulumi.String("testRuleCollection"),
			RuleName:           pulumi.String("SampleDefaultAdminRule"),
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
import com.pulumi.azurenative.network.DefaultAdminRule;
import com.pulumi.azurenative.network.DefaultAdminRuleArgs;
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
        var defaultAdminRule = new DefaultAdminRule("defaultAdminRule", DefaultAdminRuleArgs.builder()        
            .configurationName("myTestSecurityConfig")
            .flag("AllowVnetInbound")
            .kind("Default")
            .networkManagerName("testNetworkManager")
            .resourceGroupName("rg1")
            .ruleCollectionName("testRuleCollection")
            .ruleName("SampleDefaultAdminRule")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const defaultAdminRule = new azure_native.network.DefaultAdminRule("defaultAdminRule", {
    configurationName: "myTestSecurityConfig",
    flag: "AllowVnetInbound",
    kind: "Default",
    networkManagerName: "testNetworkManager",
    resourceGroupName: "rg1",
    ruleCollectionName: "testRuleCollection",
    ruleName: "SampleDefaultAdminRule",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

default_admin_rule = azure_native.network.DefaultAdminRule("defaultAdminRule",
    configuration_name="myTestSecurityConfig",
    flag="AllowVnetInbound",
    kind="Default",
    network_manager_name="testNetworkManager",
    resource_group_name="rg1",
    rule_collection_name="testRuleCollection",
    rule_name="SampleDefaultAdminRule")

```

```yaml
resources:
  defaultAdminRule:
    type: azure-native:network:DefaultAdminRule
    properties:
      configurationName: myTestSecurityConfig
      flag: AllowVnetInbound
      kind: Default
      networkManagerName: testNetworkManager
      resourceGroupName: rg1
      ruleCollectionName: testRuleCollection
      ruleName: SampleDefaultAdminRule

```

{{% /example %}}
{{% example %}}
### Create an admin rule
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var defaultAdminRule = new AzureNative.Network.DefaultAdminRule("defaultAdminRule", new()
    {
        ConfigurationName = "myTestSecurityConfig",
        NetworkManagerName = "testNetworkManager",
        ResourceGroupName = "rg1",
        RuleCollectionName = "testRuleCollection",
        RuleName = "SampleAdminRule",
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
		_, err := network.NewDefaultAdminRule(ctx, "defaultAdminRule", &network.DefaultAdminRuleArgs{
			ConfigurationName:  pulumi.String("myTestSecurityConfig"),
			NetworkManagerName: pulumi.String("testNetworkManager"),
			ResourceGroupName:  pulumi.String("rg1"),
			RuleCollectionName: pulumi.String("testRuleCollection"),
			RuleName:           pulumi.String("SampleAdminRule"),
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
import com.pulumi.azurenative.network.DefaultAdminRule;
import com.pulumi.azurenative.network.DefaultAdminRuleArgs;
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
        var defaultAdminRule = new DefaultAdminRule("defaultAdminRule", DefaultAdminRuleArgs.builder()        
            .configurationName("myTestSecurityConfig")
            .networkManagerName("testNetworkManager")
            .resourceGroupName("rg1")
            .ruleCollectionName("testRuleCollection")
            .ruleName("SampleAdminRule")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const defaultAdminRule = new azure_native.network.DefaultAdminRule("defaultAdminRule", {
    configurationName: "myTestSecurityConfig",
    networkManagerName: "testNetworkManager",
    resourceGroupName: "rg1",
    ruleCollectionName: "testRuleCollection",
    ruleName: "SampleAdminRule",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

default_admin_rule = azure_native.network.DefaultAdminRule("defaultAdminRule",
    configuration_name="myTestSecurityConfig",
    network_manager_name="testNetworkManager",
    resource_group_name="rg1",
    rule_collection_name="testRuleCollection",
    rule_name="SampleAdminRule")

```

```yaml
resources:
  defaultAdminRule:
    type: azure-native:network:DefaultAdminRule
    properties:
      configurationName: myTestSecurityConfig
      networkManagerName: testNetworkManager
      resourceGroupName: rg1
      ruleCollectionName: testRuleCollection
      ruleName: SampleAdminRule

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:DefaultAdminRule SampleAdminRule /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/rg1/providers/Microsoft.Network/networkManagers/testNetworkManager/securityAdminConfigurations/myTestSecurityConfig/ruleCollections/testRuleCollection/rules/SampleAdminRule 
```
