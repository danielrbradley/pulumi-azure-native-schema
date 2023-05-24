VpnServerConfigurationPolicyGroup Resource.
API Version: 2022-09-01.
Previous API Version: 2022-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ConfigurationPolicyGroupPut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var configurationPolicyGroup = new AzureNative.Network.ConfigurationPolicyGroup("configurationPolicyGroup", new()
    {
        ConfigurationPolicyGroupName = "policyGroup1",
        IsDefault = true,
        PolicyMembers = new[]
        {
            new AzureNative.Network.Inputs.VpnServerConfigurationPolicyGroupMemberArgs
            {
                AttributeType = "RadiusAzureGroupId",
                AttributeValue = "6ad1bd08",
                Name = "policy1",
            },
            new AzureNative.Network.Inputs.VpnServerConfigurationPolicyGroupMemberArgs
            {
                AttributeType = "CertificateGroupId",
                AttributeValue = "red.com",
                Name = "policy2",
            },
        },
        Priority = 0,
        ResourceGroupName = "rg1",
        VpnServerConfigurationName = "vpnServerConfiguration1",
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
		_, err := network.NewConfigurationPolicyGroup(ctx, "configurationPolicyGroup", &network.ConfigurationPolicyGroupArgs{
			ConfigurationPolicyGroupName: pulumi.String("policyGroup1"),
			IsDefault:                    pulumi.Bool(true),
			PolicyMembers: []network.VpnServerConfigurationPolicyGroupMemberArgs{
				{
					AttributeType:  pulumi.String("RadiusAzureGroupId"),
					AttributeValue: pulumi.String("6ad1bd08"),
					Name:           pulumi.String("policy1"),
				},
				{
					AttributeType:  pulumi.String("CertificateGroupId"),
					AttributeValue: pulumi.String("red.com"),
					Name:           pulumi.String("policy2"),
				},
			},
			Priority:                   pulumi.Int(0),
			ResourceGroupName:          pulumi.String("rg1"),
			VpnServerConfigurationName: pulumi.String("vpnServerConfiguration1"),
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
import com.pulumi.azurenative.network.ConfigurationPolicyGroup;
import com.pulumi.azurenative.network.ConfigurationPolicyGroupArgs;
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
        var configurationPolicyGroup = new ConfigurationPolicyGroup("configurationPolicyGroup", ConfigurationPolicyGroupArgs.builder()        
            .configurationPolicyGroupName("policyGroup1")
            .isDefault(true)
            .policyMembers(            
                Map.ofEntries(
                    Map.entry("attributeType", "RadiusAzureGroupId"),
                    Map.entry("attributeValue", "6ad1bd08"),
                    Map.entry("name", "policy1")
                ),
                Map.ofEntries(
                    Map.entry("attributeType", "CertificateGroupId"),
                    Map.entry("attributeValue", "red.com"),
                    Map.entry("name", "policy2")
                ))
            .priority(0)
            .resourceGroupName("rg1")
            .vpnServerConfigurationName("vpnServerConfiguration1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const configurationPolicyGroup = new azure_native.network.ConfigurationPolicyGroup("configurationPolicyGroup", {
    configurationPolicyGroupName: "policyGroup1",
    isDefault: true,
    policyMembers: [
        {
            attributeType: "RadiusAzureGroupId",
            attributeValue: "6ad1bd08",
            name: "policy1",
        },
        {
            attributeType: "CertificateGroupId",
            attributeValue: "red.com",
            name: "policy2",
        },
    ],
    priority: 0,
    resourceGroupName: "rg1",
    vpnServerConfigurationName: "vpnServerConfiguration1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

configuration_policy_group = azure_native.network.ConfigurationPolicyGroup("configurationPolicyGroup",
    configuration_policy_group_name="policyGroup1",
    is_default=True,
    policy_members=[
        azure_native.network.VpnServerConfigurationPolicyGroupMemberArgs(
            attribute_type="RadiusAzureGroupId",
            attribute_value="6ad1bd08",
            name="policy1",
        ),
        azure_native.network.VpnServerConfigurationPolicyGroupMemberArgs(
            attribute_type="CertificateGroupId",
            attribute_value="red.com",
            name="policy2",
        ),
    ],
    priority=0,
    resource_group_name="rg1",
    vpn_server_configuration_name="vpnServerConfiguration1")

```

```yaml
resources:
  configurationPolicyGroup:
    type: azure-native:network:ConfigurationPolicyGroup
    properties:
      configurationPolicyGroupName: policyGroup1
      isDefault: true
      policyMembers:
        - attributeType: RadiusAzureGroupId
          attributeValue: 6ad1bd08
          name: policy1
        - attributeType: CertificateGroupId
          attributeValue: red.com
          name: policy2
      priority: 0
      resourceGroupName: rg1
      vpnServerConfigurationName: vpnServerConfiguration1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:ConfigurationPolicyGroup policyGroup1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/vpnServerConfigurations/vpnServerConfiguration1/vpnServerConfigurationPolicyGroups/policyGroup1 
```
