NetworkSecurityGroup resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create network security group
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var networkSecurityGroup = new AzureNative.Network.NetworkSecurityGroup("networkSecurityGroup", new()
    {
        Location = "eastus",
        NetworkSecurityGroupName = "testnsg",
        ResourceGroupName = "rg1",
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
		_, err := network.NewNetworkSecurityGroup(ctx, "networkSecurityGroup", &network.NetworkSecurityGroupArgs{
			Location:                 pulumi.String("eastus"),
			NetworkSecurityGroupName: pulumi.String("testnsg"),
			ResourceGroupName:        pulumi.String("rg1"),
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
import com.pulumi.azurenative.network.NetworkSecurityGroup;
import com.pulumi.azurenative.network.NetworkSecurityGroupArgs;
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
        var networkSecurityGroup = new NetworkSecurityGroup("networkSecurityGroup", NetworkSecurityGroupArgs.builder()        
            .location("eastus")
            .networkSecurityGroupName("testnsg")
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const networkSecurityGroup = new azure_native.network.NetworkSecurityGroup("networkSecurityGroup", {
    location: "eastus",
    networkSecurityGroupName: "testnsg",
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

network_security_group = azure_native.network.NetworkSecurityGroup("networkSecurityGroup",
    location="eastus",
    network_security_group_name="testnsg",
    resource_group_name="rg1")

```

```yaml
resources:
  networkSecurityGroup:
    type: azure-native:network:NetworkSecurityGroup
    properties:
      location: eastus
      networkSecurityGroupName: testnsg
      resourceGroupName: rg1

```

{{% /example %}}
{{% example %}}
### Create network security group with rule
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var networkSecurityGroup = new AzureNative.Network.NetworkSecurityGroup("networkSecurityGroup", new()
    {
        Location = "eastus",
        NetworkSecurityGroupName = "testnsg",
        ResourceGroupName = "rg1",
        SecurityRules = new[]
        {
            new AzureNative.Network.Inputs.SecurityRuleArgs
            {
                Access = "Allow",
                DestinationAddressPrefix = "*",
                DestinationPortRange = "80",
                Direction = "Inbound",
                Name = "rule1",
                Priority = 130,
                Protocol = "*",
                SourceAddressPrefix = "*",
                SourcePortRange = "*",
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
		_, err := network.NewNetworkSecurityGroup(ctx, "networkSecurityGroup", &network.NetworkSecurityGroupArgs{
			Location:                 pulumi.String("eastus"),
			NetworkSecurityGroupName: pulumi.String("testnsg"),
			ResourceGroupName:        pulumi.String("rg1"),
			SecurityRules: []network.SecurityRuleTypeArgs{
				{
					Access:                   pulumi.String("Allow"),
					DestinationAddressPrefix: pulumi.String("*"),
					DestinationPortRange:     pulumi.String("80"),
					Direction:                pulumi.String("Inbound"),
					Name:                     pulumi.String("rule1"),
					Priority:                 pulumi.Int(130),
					Protocol:                 pulumi.String("*"),
					SourceAddressPrefix:      pulumi.String("*"),
					SourcePortRange:          pulumi.String("*"),
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
import com.pulumi.azurenative.network.NetworkSecurityGroup;
import com.pulumi.azurenative.network.NetworkSecurityGroupArgs;
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
        var networkSecurityGroup = new NetworkSecurityGroup("networkSecurityGroup", NetworkSecurityGroupArgs.builder()        
            .location("eastus")
            .networkSecurityGroupName("testnsg")
            .resourceGroupName("rg1")
            .securityRules(Map.ofEntries(
                Map.entry("access", "Allow"),
                Map.entry("destinationAddressPrefix", "*"),
                Map.entry("destinationPortRange", "80"),
                Map.entry("direction", "Inbound"),
                Map.entry("name", "rule1"),
                Map.entry("priority", 130),
                Map.entry("protocol", "*"),
                Map.entry("sourceAddressPrefix", "*"),
                Map.entry("sourcePortRange", "*")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const networkSecurityGroup = new azure_native.network.NetworkSecurityGroup("networkSecurityGroup", {
    location: "eastus",
    networkSecurityGroupName: "testnsg",
    resourceGroupName: "rg1",
    securityRules: [{
        access: "Allow",
        destinationAddressPrefix: "*",
        destinationPortRange: "80",
        direction: "Inbound",
        name: "rule1",
        priority: 130,
        protocol: "*",
        sourceAddressPrefix: "*",
        sourcePortRange: "*",
    }],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

network_security_group = azure_native.network.NetworkSecurityGroup("networkSecurityGroup",
    location="eastus",
    network_security_group_name="testnsg",
    resource_group_name="rg1",
    security_rules=[azure_native.network.SecurityRuleArgs(
        access="Allow",
        destination_address_prefix="*",
        destination_port_range="80",
        direction="Inbound",
        name="rule1",
        priority=130,
        protocol="*",
        source_address_prefix="*",
        source_port_range="*",
    )])

```

```yaml
resources:
  networkSecurityGroup:
    type: azure-native:network:NetworkSecurityGroup
    properties:
      location: eastus
      networkSecurityGroupName: testnsg
      resourceGroupName: rg1
      securityRules:
        - access: Allow
          destinationAddressPrefix: '*'
          destinationPortRange: '80'
          direction: Inbound
          name: rule1
          priority: 130
          protocol: '*'
          sourceAddressPrefix: '*'
          sourcePortRange: '*'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:NetworkSecurityGroup testnsg /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/networkSecurityGroups/testnsg 
```
