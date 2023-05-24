Definition of the EnterprisePolicy.
API Version: 2020-10-30-preview.
Previous API Version: 2020-10-30-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update EnterprisePolicy
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var enterprisePolicy = new AzureNative.PowerPlatform.EnterprisePolicy("enterprisePolicy", new()
    {
        EnterprisePolicyName = "enterprisePolicy",
        Identity = new AzureNative.PowerPlatform.Inputs.EnterprisePolicyIdentityArgs
        {
            Type = AzureNative.PowerPlatform.ResourceIdentityType.SystemAssigned,
        },
        Kind = "Lockbox",
        Location = "East US",
        ResourceGroupName = "resourceGroup",
        Tags = 
        {
            { "Organization", "Administration" },
        },
    });

});


```

```go
package main

import (
	powerplatform "github.com/pulumi/pulumi-azure-native-sdk/powerplatform"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := powerplatform.NewEnterprisePolicy(ctx, "enterprisePolicy", &powerplatform.EnterprisePolicyArgs{
			EnterprisePolicyName: pulumi.String("enterprisePolicy"),
			Identity: &powerplatform.EnterprisePolicyIdentityArgs{
				Type: powerplatform.ResourceIdentityTypeSystemAssigned,
			},
			Kind:              pulumi.String("Lockbox"),
			Location:          pulumi.String("East US"),
			ResourceGroupName: pulumi.String("resourceGroup"),
			Tags: pulumi.StringMap{
				"Organization": pulumi.String("Administration"),
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
import com.pulumi.azurenative.powerplatform.EnterprisePolicy;
import com.pulumi.azurenative.powerplatform.EnterprisePolicyArgs;
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
        var enterprisePolicy = new EnterprisePolicy("enterprisePolicy", EnterprisePolicyArgs.builder()        
            .enterprisePolicyName("enterprisePolicy")
            .identity(Map.of("type", "SystemAssigned"))
            .kind("Lockbox")
            .location("East US")
            .resourceGroupName("resourceGroup")
            .tags(Map.of("Organization", "Administration"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const enterprisePolicy = new azure_native.powerplatform.EnterprisePolicy("enterprisePolicy", {
    enterprisePolicyName: "enterprisePolicy",
    identity: {
        type: azure_native.powerplatform.ResourceIdentityType.SystemAssigned,
    },
    kind: "Lockbox",
    location: "East US",
    resourceGroupName: "resourceGroup",
    tags: {
        Organization: "Administration",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

enterprise_policy = azure_native.powerplatform.EnterprisePolicy("enterprisePolicy",
    enterprise_policy_name="enterprisePolicy",
    identity=azure_native.powerplatform.EnterprisePolicyIdentityArgs(
        type=azure_native.powerplatform.ResourceIdentityType.SYSTEM_ASSIGNED,
    ),
    kind="Lockbox",
    location="East US",
    resource_group_name="resourceGroup",
    tags={
        "Organization": "Administration",
    })

```

```yaml
resources:
  enterprisePolicy:
    type: azure-native:powerplatform:EnterprisePolicy
    properties:
      enterprisePolicyName: enterprisePolicy
      identity:
        type: SystemAssigned
      kind: Lockbox
      location: East US
      resourceGroupName: resourceGroup
      tags:
        Organization: Administration

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:powerplatform:EnterprisePolicy enterprisePolicy /subscriptions/subid/resourceGroups/resourceGroup/providers/Microsoft.PowerPlatform/enterprisePolicies/enterprisePolicy 
```
