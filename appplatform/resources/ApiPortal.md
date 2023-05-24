API portal resource
API Version: 2022-12-01.
Previous API Version: 2022-01-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiPortals_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var apiPortal = new AzureNative.AppPlatform.ApiPortal("apiPortal", new()
    {
        ApiPortalName = "default",
        Properties = new AzureNative.AppPlatform.Inputs.ApiPortalPropertiesArgs
        {
            GatewayIds = new[]
            {
                "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.AppPlatform/Spring/myservice/gateways/default",
            },
            Public = true,
        },
        ResourceGroupName = "myResourceGroup",
        ServiceName = "myservice",
        Sku = new AzureNative.AppPlatform.Inputs.SkuArgs
        {
            Capacity = 2,
            Name = "E0",
            Tier = "Enterprise",
        },
    });

});


```

```go
package main

import (
	appplatform "github.com/pulumi/pulumi-azure-native-sdk/appplatform"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := appplatform.NewApiPortal(ctx, "apiPortal", &appplatform.ApiPortalArgs{
			ApiPortalName: pulumi.String("default"),
			Properties: &appplatform.ApiPortalPropertiesArgs{
				GatewayIds: pulumi.StringArray{
					pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.AppPlatform/Spring/myservice/gateways/default"),
				},
				Public: pulumi.Bool(true),
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
			ServiceName:       pulumi.String("myservice"),
			Sku: &appplatform.SkuArgs{
				Capacity: pulumi.Int(2),
				Name:     pulumi.String("E0"),
				Tier:     pulumi.String("Enterprise"),
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
import com.pulumi.azurenative.appplatform.ApiPortal;
import com.pulumi.azurenative.appplatform.ApiPortalArgs;
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
        var apiPortal = new ApiPortal("apiPortal", ApiPortalArgs.builder()        
            .apiPortalName("default")
            .properties(Map.ofEntries(
                Map.entry("gatewayIds", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.AppPlatform/Spring/myservice/gateways/default"),
                Map.entry("public", true)
            ))
            .resourceGroupName("myResourceGroup")
            .serviceName("myservice")
            .sku(Map.ofEntries(
                Map.entry("capacity", 2),
                Map.entry("name", "E0"),
                Map.entry("tier", "Enterprise")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const apiPortal = new azure_native.appplatform.ApiPortal("apiPortal", {
    apiPortalName: "default",
    properties: {
        gatewayIds: ["/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.AppPlatform/Spring/myservice/gateways/default"],
        "public": true,
    },
    resourceGroupName: "myResourceGroup",
    serviceName: "myservice",
    sku: {
        capacity: 2,
        name: "E0",
        tier: "Enterprise",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

api_portal = azure_native.appplatform.ApiPortal("apiPortal",
    api_portal_name="default",
    properties=azure_native.appplatform.ApiPortalPropertiesArgs(
        gateway_ids=["/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.AppPlatform/Spring/myservice/gateways/default"],
        public=True,
    ),
    resource_group_name="myResourceGroup",
    service_name="myservice",
    sku=azure_native.appplatform.SkuArgs(
        capacity=2,
        name="E0",
        tier="Enterprise",
    ))

```

```yaml
resources:
  apiPortal:
    type: azure-native:appplatform:ApiPortal
    properties:
      apiPortalName: default
      properties:
        gatewayIds:
          - /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.AppPlatform/Spring/myservice/gateways/default
        public: true
      resourceGroupName: myResourceGroup
      serviceName: myservice
      sku:
        capacity: 2
        name: E0
        tier: Enterprise

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:appplatform:ApiPortal default /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.AppPlatform/Spring/myservice/apiPortals/default 
```
