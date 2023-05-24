Virtual Appliance Site resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Network Virtual Appliance Site
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualApplianceSite = new AzureNative.Network.VirtualApplianceSite("virtualApplianceSite", new()
    {
        AddressPrefix = "192.168.1.0/24",
        NetworkVirtualApplianceName = "nva",
        O365Policy = new AzureNative.Network.Inputs.Office365PolicyPropertiesArgs
        {
            BreakOutCategories = new AzureNative.Network.Inputs.BreakOutCategoryPoliciesArgs
            {
                Allow = true,
                Default = true,
                Optimize = true,
            },
        },
        ResourceGroupName = "rg1",
        SiteName = "site1",
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
		_, err := network.NewVirtualApplianceSite(ctx, "virtualApplianceSite", &network.VirtualApplianceSiteArgs{
			AddressPrefix:               pulumi.String("192.168.1.0/24"),
			NetworkVirtualApplianceName: pulumi.String("nva"),
			O365Policy: network.Office365PolicyPropertiesResponse{
				BreakOutCategories: &network.BreakOutCategoryPoliciesArgs{
					Allow:    pulumi.Bool(true),
					Default:  pulumi.Bool(true),
					Optimize: pulumi.Bool(true),
				},
			},
			ResourceGroupName: pulumi.String("rg1"),
			SiteName:          pulumi.String("site1"),
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
import com.pulumi.azurenative.network.VirtualApplianceSite;
import com.pulumi.azurenative.network.VirtualApplianceSiteArgs;
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
        var virtualApplianceSite = new VirtualApplianceSite("virtualApplianceSite", VirtualApplianceSiteArgs.builder()        
            .addressPrefix("192.168.1.0/24")
            .networkVirtualApplianceName("nva")
            .o365Policy(Map.of("breakOutCategories", Map.ofEntries(
                Map.entry("allow", true),
                Map.entry("default", true),
                Map.entry("optimize", true)
            )))
            .resourceGroupName("rg1")
            .siteName("site1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualApplianceSite = new azure_native.network.VirtualApplianceSite("virtualApplianceSite", {
    addressPrefix: "192.168.1.0/24",
    networkVirtualApplianceName: "nva",
    o365Policy: {
        breakOutCategories: {
            allow: true,
            "default": true,
            optimize: true,
        },
    },
    resourceGroupName: "rg1",
    siteName: "site1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_appliance_site = azure_native.network.VirtualApplianceSite("virtualApplianceSite",
    address_prefix="192.168.1.0/24",
    network_virtual_appliance_name="nva",
    o365_policy=azure_native.network.Office365PolicyPropertiesResponseArgs(
        break_out_categories=azure_native.network.BreakOutCategoryPoliciesArgs(
            allow=True,
            default=True,
            optimize=True,
        ),
    ),
    resource_group_name="rg1",
    site_name="site1")

```

```yaml
resources:
  virtualApplianceSite:
    type: azure-native:network:VirtualApplianceSite
    properties:
      addressPrefix: 192.168.1.0/24
      networkVirtualApplianceName: nva
      o365Policy:
        breakOutCategories:
          allow: true
          default: true
          optimize: true
      resourceGroupName: rg1
      siteName: site1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:VirtualApplianceSite site1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/networkVirtualAppliances/nva/virtualApplianceSites/site1 
```
