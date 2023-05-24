A DDoS custom policy in a resource group.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create DDoS custom policy
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var ddosCustomPolicy = new AzureNative.Network.DdosCustomPolicy("ddosCustomPolicy", new()
    {
        DdosCustomPolicyName = "test-ddos-custom-policy",
        Location = "centraluseuap",
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
		_, err := network.NewDdosCustomPolicy(ctx, "ddosCustomPolicy", &network.DdosCustomPolicyArgs{
			DdosCustomPolicyName: pulumi.String("test-ddos-custom-policy"),
			Location:             pulumi.String("centraluseuap"),
			ResourceGroupName:    pulumi.String("rg1"),
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
import com.pulumi.azurenative.network.DdosCustomPolicy;
import com.pulumi.azurenative.network.DdosCustomPolicyArgs;
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
        var ddosCustomPolicy = new DdosCustomPolicy("ddosCustomPolicy", DdosCustomPolicyArgs.builder()        
            .ddosCustomPolicyName("test-ddos-custom-policy")
            .location("centraluseuap")
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const ddosCustomPolicy = new azure_native.network.DdosCustomPolicy("ddosCustomPolicy", {
    ddosCustomPolicyName: "test-ddos-custom-policy",
    location: "centraluseuap",
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

ddos_custom_policy = azure_native.network.DdosCustomPolicy("ddosCustomPolicy",
    ddos_custom_policy_name="test-ddos-custom-policy",
    location="centraluseuap",
    resource_group_name="rg1")

```

```yaml
resources:
  ddosCustomPolicy:
    type: azure-native:network:DdosCustomPolicy
    properties:
      ddosCustomPolicyName: test-ddos-custom-policy
      location: centraluseuap
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:DdosCustomPolicy test-ddos-custom-policy /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/ddosCustomPolicies/test-ddos-custom-policy 
```
