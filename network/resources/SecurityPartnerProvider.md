Security Partner Provider resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Security Partner Provider
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var securityPartnerProvider = new AzureNative.Network.SecurityPartnerProvider("securityPartnerProvider", new()
    {
        Location = "West US",
        ResourceGroupName = "rg1",
        SecurityPartnerProviderName = "securityPartnerProvider",
        SecurityProviderName = "ZScaler",
        Tags = 
        {
            { "key1", "value1" },
        },
        VirtualHub = new AzureNative.Network.Inputs.SubResourceArgs
        {
            Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1",
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
		_, err := network.NewSecurityPartnerProvider(ctx, "securityPartnerProvider", &network.SecurityPartnerProviderArgs{
			Location:                    pulumi.String("West US"),
			ResourceGroupName:           pulumi.String("rg1"),
			SecurityPartnerProviderName: pulumi.String("securityPartnerProvider"),
			SecurityProviderName:        pulumi.String("ZScaler"),
			Tags: pulumi.StringMap{
				"key1": pulumi.String("value1"),
			},
			VirtualHub: &network.SubResourceArgs{
				Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1"),
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
import com.pulumi.azurenative.network.SecurityPartnerProvider;
import com.pulumi.azurenative.network.SecurityPartnerProviderArgs;
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
        var securityPartnerProvider = new SecurityPartnerProvider("securityPartnerProvider", SecurityPartnerProviderArgs.builder()        
            .location("West US")
            .resourceGroupName("rg1")
            .securityPartnerProviderName("securityPartnerProvider")
            .securityProviderName("ZScaler")
            .tags(Map.of("key1", "value1"))
            .virtualHub(Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const securityPartnerProvider = new azure_native.network.SecurityPartnerProvider("securityPartnerProvider", {
    location: "West US",
    resourceGroupName: "rg1",
    securityPartnerProviderName: "securityPartnerProvider",
    securityProviderName: "ZScaler",
    tags: {
        key1: "value1",
    },
    virtualHub: {
        id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

security_partner_provider = azure_native.network.SecurityPartnerProvider("securityPartnerProvider",
    location="West US",
    resource_group_name="rg1",
    security_partner_provider_name="securityPartnerProvider",
    security_provider_name="ZScaler",
    tags={
        "key1": "value1",
    },
    virtual_hub=azure_native.network.SubResourceArgs(
        id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1",
    ))

```

```yaml
resources:
  securityPartnerProvider:
    type: azure-native:network:SecurityPartnerProvider
    properties:
      location: West US
      resourceGroupName: rg1
      securityPartnerProviderName: securityPartnerProvider
      securityProviderName: ZScaler
      tags:
        key1: value1
      virtualHub:
        id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualHubs/hub1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:SecurityPartnerProvider securityPartnerProvider /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/securityPartnerProviders/securityPartnerProvider 
```
