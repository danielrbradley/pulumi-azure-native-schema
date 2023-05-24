App Service Environment ARM resource.
API Version: 2022-09-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update an App Service Environment.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var appServiceEnvironment = new AzureNative.Web.AppServiceEnvironment("appServiceEnvironment", new()
    {
        Kind = "Asev3",
        Location = "South Central US",
        Name = "test-ase",
        ResourceGroupName = "test-rg",
        VirtualNetwork = new AzureNative.Web.Inputs.VirtualNetworkProfileArgs
        {
            Id = "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/delegated",
        },
    });

});


```

```go
package main

import (
	web "github.com/pulumi/pulumi-azure-native-sdk/web"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := web.NewAppServiceEnvironment(ctx, "appServiceEnvironment", &web.AppServiceEnvironmentArgs{
			Kind:              pulumi.String("Asev3"),
			Location:          pulumi.String("South Central US"),
			Name:              pulumi.String("test-ase"),
			ResourceGroupName: pulumi.String("test-rg"),
			VirtualNetwork: &web.VirtualNetworkProfileArgs{
				Id: pulumi.String("/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/delegated"),
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
import com.pulumi.azurenative.web.AppServiceEnvironment;
import com.pulumi.azurenative.web.AppServiceEnvironmentArgs;
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
        var appServiceEnvironment = new AppServiceEnvironment("appServiceEnvironment", AppServiceEnvironmentArgs.builder()        
            .kind("Asev3")
            .location("South Central US")
            .name("test-ase")
            .resourceGroupName("test-rg")
            .virtualNetwork(Map.of("id", "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/delegated"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const appServiceEnvironment = new azure_native.web.AppServiceEnvironment("appServiceEnvironment", {
    kind: "Asev3",
    location: "South Central US",
    name: "test-ase",
    resourceGroupName: "test-rg",
    virtualNetwork: {
        id: "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/delegated",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

app_service_environment = azure_native.web.AppServiceEnvironment("appServiceEnvironment",
    kind="Asev3",
    location="South Central US",
    name="test-ase",
    resource_group_name="test-rg",
    virtual_network=azure_native.web.VirtualNetworkProfileArgs(
        id="/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/delegated",
    ))

```

```yaml
resources:
  appServiceEnvironment:
    type: azure-native:web:AppServiceEnvironment
    properties:
      kind: Asev3
      location: South Central US
      name: test-ase
      resourceGroupName: test-rg
      virtualNetwork:
        id: /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/delegated

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:web:AppServiceEnvironment test-ase /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/test-rg/providers/Microsoft.Web/hostingEnvironments/test-ase 
```
