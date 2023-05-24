Network admin rule.
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
    var adminRule = new AzureNative.Network.AdminRule("adminRule", new()
    {
        ConfigurationName = "myTestSecurityConfig",
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
		_, err := network.NewAdminRule(ctx, "adminRule", &network.AdminRuleArgs{
			ConfigurationName:  pulumi.String("myTestSecurityConfig"),
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
import com.pulumi.azurenative.network.AdminRule;
import com.pulumi.azurenative.network.AdminRuleArgs;
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
        var adminRule = new AdminRule("adminRule", AdminRuleArgs.builder()        
            .configurationName("myTestSecurityConfig")
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

const adminRule = new azure_native.network.AdminRule("adminRule", {
    configurationName: "myTestSecurityConfig",
    networkManagerName: "testNetworkManager",
    resourceGroupName: "rg1",
    ruleCollectionName: "testRuleCollection",
    ruleName: "SampleDefaultAdminRule",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

admin_rule = azure_native.network.AdminRule("adminRule",
    configuration_name="myTestSecurityConfig",
    network_manager_name="testNetworkManager",
    resource_group_name="rg1",
    rule_collection_name="testRuleCollection",
    rule_name="SampleDefaultAdminRule")

```

```yaml
resources:
  adminRule:
    type: azure-native:network:AdminRule
    properties:
      configurationName: myTestSecurityConfig
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
    var adminRule = new AzureNative.Network.AdminRule("adminRule", new()
    {
        Access = "Deny",
        ConfigurationName = "myTestSecurityConfig",
        Description = "This is Sample Admin Rule",
        DestinationPortRanges = new[]
        {
            "22",
        },
        Destinations = new[]
        {
            new AzureNative.Network.Inputs.AddressPrefixItemArgs
            {
                AddressPrefix = "*",
                AddressPrefixType = "IPPrefix",
            },
        },
        Direction = "Inbound",
        Kind = "Custom",
        NetworkManagerName = "testNetworkManager",
        Priority = 1,
        Protocol = "Tcp",
        ResourceGroupName = "rg1",
        RuleCollectionName = "testRuleCollection",
        RuleName = "SampleAdminRule",
        SourcePortRanges = new[]
        {
            "0-65535",
        },
        Sources = new[]
        {
            new AzureNative.Network.Inputs.AddressPrefixItemArgs
            {
                AddressPrefix = "Internet",
                AddressPrefixType = "ServiceTag",
            },
        },
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
		_, err := network.NewAdminRule(ctx, "adminRule", &network.AdminRuleArgs{
			Access:            pulumi.String("Deny"),
			ConfigurationName: pulumi.String("myTestSecurityConfig"),
			Description:       pulumi.String("This is Sample Admin Rule"),
			DestinationPortRanges: pulumi.StringArray{
				pulumi.String("22"),
			},
			Destinations: []network.AddressPrefixItemArgs{
				{
					AddressPrefix:     pulumi.String("*"),
					AddressPrefixType: pulumi.String("IPPrefix"),
				},
			},
			Direction:          pulumi.String("Inbound"),
			Kind:               pulumi.String("Custom"),
			NetworkManagerName: pulumi.String("testNetworkManager"),
			Priority:           pulumi.Int(1),
			Protocol:           pulumi.String("Tcp"),
			ResourceGroupName:  pulumi.String("rg1"),
			RuleCollectionName: pulumi.String("testRuleCollection"),
			RuleName:           pulumi.String("SampleAdminRule"),
			SourcePortRanges: pulumi.StringArray{
				pulumi.String("0-65535"),
			},
			Sources: []network.AddressPrefixItemArgs{
				{
					AddressPrefix:     pulumi.String("Internet"),
					AddressPrefixType: pulumi.String("ServiceTag"),
				},
			},
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
import com.pulumi.azurenative.network.AdminRule;
import com.pulumi.azurenative.network.AdminRuleArgs;
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
        var adminRule = new AdminRule("adminRule", AdminRuleArgs.builder()        
            .access("Deny")
            .configurationName("myTestSecurityConfig")
            .description("This is Sample Admin Rule")
            .destinationPortRanges("22")
            .destinations(Map.ofEntries(
                Map.entry("addressPrefix", "*"),
                Map.entry("addressPrefixType", "IPPrefix")
            ))
            .direction("Inbound")
            .kind("Custom")
            .networkManagerName("testNetworkManager")
            .priority(1)
            .protocol("Tcp")
            .resourceGroupName("rg1")
            .ruleCollectionName("testRuleCollection")
            .ruleName("SampleAdminRule")
            .sourcePortRanges("0-65535")
            .sources(Map.ofEntries(
                Map.entry("addressPrefix", "Internet"),
                Map.entry("addressPrefixType", "ServiceTag")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const adminRule = new azure_native.network.AdminRule("adminRule", {
    access: "Deny",
    configurationName: "myTestSecurityConfig",
    description: "This is Sample Admin Rule",
    destinationPortRanges: ["22"],
    destinations: [{
        addressPrefix: "*",
        addressPrefixType: "IPPrefix",
    }],
    direction: "Inbound",
    kind: "Custom",
    networkManagerName: "testNetworkManager",
    priority: 1,
    protocol: "Tcp",
    resourceGroupName: "rg1",
    ruleCollectionName: "testRuleCollection",
    ruleName: "SampleAdminRule",
    sourcePortRanges: ["0-65535"],
    sources: [{
        addressPrefix: "Internet",
        addressPrefixType: "ServiceTag",
    }],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

admin_rule = azure_native.network.AdminRule("adminRule",
    access="Deny",
    configuration_name="myTestSecurityConfig",
    description="This is Sample Admin Rule",
    destination_port_ranges=["22"],
    destinations=[azure_native.network.AddressPrefixItemArgs(
        address_prefix="*",
        address_prefix_type="IPPrefix",
    )],
    direction="Inbound",
    kind="Custom",
    network_manager_name="testNetworkManager",
    priority=1,
    protocol="Tcp",
    resource_group_name="rg1",
    rule_collection_name="testRuleCollection",
    rule_name="SampleAdminRule",
    source_port_ranges=["0-65535"],
    sources=[azure_native.network.AddressPrefixItemArgs(
        address_prefix="Internet",
        address_prefix_type="ServiceTag",
    )])

```

```yaml
resources:
  adminRule:
    type: azure-native:network:AdminRule
    properties:
      access: Deny
      configurationName: myTestSecurityConfig
      description: This is Sample Admin Rule
      destinationPortRanges:
        - '22'
      destinations:
        - addressPrefix: '*'
          addressPrefixType: IPPrefix
      direction: Inbound
      kind: Custom
      networkManagerName: testNetworkManager
      priority: 1
      protocol: Tcp
      resourceGroupName: rg1
      ruleCollectionName: testRuleCollection
      ruleName: SampleAdminRule
      sourcePortRanges:
        - 0-65535
      sources:
        - addressPrefix: Internet
          addressPrefixType: ServiceTag

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:AdminRule SampleAdminRule /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/rg1/providers/Microsoft.Network/networkManagers/testNetworkManager/securityAdminConfigurations/myTestSecurityConfig/ruleCollections/testRuleCollection/rules/SampleAdminRule 
```
