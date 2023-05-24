Defines the security admin configuration
API Version: 2022-09-01.
Previous API Version: 2021-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create network manager security admin configuration
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var securityAdminConfiguration = new AzureNative.Network.SecurityAdminConfiguration("securityAdminConfiguration", new()
    {
        ApplyOnNetworkIntentPolicyBasedServices = new[]
        {
            "None",
        },
        ConfigurationName = "myTestSecurityConfig",
        Description = "A sample policy",
        NetworkManagerName = "testNetworkManager",
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
		_, err := network.NewSecurityAdminConfiguration(ctx, "securityAdminConfiguration", &network.SecurityAdminConfigurationArgs{
			ApplyOnNetworkIntentPolicyBasedServices: pulumi.StringArray{
				pulumi.String("None"),
			},
			ConfigurationName:  pulumi.String("myTestSecurityConfig"),
			Description:        pulumi.String("A sample policy"),
			NetworkManagerName: pulumi.String("testNetworkManager"),
			ResourceGroupName:  pulumi.String("rg1"),
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
import com.pulumi.azurenative.network.SecurityAdminConfiguration;
import com.pulumi.azurenative.network.SecurityAdminConfigurationArgs;
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
        var securityAdminConfiguration = new SecurityAdminConfiguration("securityAdminConfiguration", SecurityAdminConfigurationArgs.builder()        
            .applyOnNetworkIntentPolicyBasedServices("None")
            .configurationName("myTestSecurityConfig")
            .description("A sample policy")
            .networkManagerName("testNetworkManager")
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const securityAdminConfiguration = new azure_native.network.SecurityAdminConfiguration("securityAdminConfiguration", {
    applyOnNetworkIntentPolicyBasedServices: ["None"],
    configurationName: "myTestSecurityConfig",
    description: "A sample policy",
    networkManagerName: "testNetworkManager",
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

security_admin_configuration = azure_native.network.SecurityAdminConfiguration("securityAdminConfiguration",
    apply_on_network_intent_policy_based_services=["None"],
    configuration_name="myTestSecurityConfig",
    description="A sample policy",
    network_manager_name="testNetworkManager",
    resource_group_name="rg1")

```

```yaml
resources:
  securityAdminConfiguration:
    type: azure-native:network:SecurityAdminConfiguration
    properties:
      applyOnNetworkIntentPolicyBasedServices:
        - None
      configurationName: myTestSecurityConfig
      description: A sample policy
      networkManagerName: testNetworkManager
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:SecurityAdminConfiguration myTestSecurityConfig /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/rg1/providers/Microsoft.Network/networkManager/testNetworkManager/securityAdminConfigurations/myTestSecurityConfig 
```
