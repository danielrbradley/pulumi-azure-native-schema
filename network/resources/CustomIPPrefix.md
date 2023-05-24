Custom IP prefix resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create custom IP prefix allocation method
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var customIPPrefix = new AzureNative.Network.CustomIPPrefix("customIPPrefix", new()
    {
        Cidr = "0.0.0.0/24",
        CustomIpPrefixName = "test-customipprefix",
        Location = "westus",
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
		_, err := network.NewCustomIPPrefix(ctx, "customIPPrefix", &network.CustomIPPrefixArgs{
			Cidr:               pulumi.String("0.0.0.0/24"),
			CustomIpPrefixName: pulumi.String("test-customipprefix"),
			Location:           pulumi.String("westus"),
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
import com.pulumi.azurenative.network.CustomIPPrefix;
import com.pulumi.azurenative.network.CustomIPPrefixArgs;
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
        var customIPPrefix = new CustomIPPrefix("customIPPrefix", CustomIPPrefixArgs.builder()        
            .cidr("0.0.0.0/24")
            .customIpPrefixName("test-customipprefix")
            .location("westus")
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const customIPPrefix = new azure_native.network.CustomIPPrefix("customIPPrefix", {
    cidr: "0.0.0.0/24",
    customIpPrefixName: "test-customipprefix",
    location: "westus",
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

custom_ip_prefix = azure_native.network.CustomIPPrefix("customIPPrefix",
    cidr="0.0.0.0/24",
    custom_ip_prefix_name="test-customipprefix",
    location="westus",
    resource_group_name="rg1")

```

```yaml
resources:
  customIPPrefix:
    type: azure-native:network:CustomIPPrefix
    properties:
      cidr: 0.0.0.0/24
      customIpPrefixName: test-customipprefix
      location: westus
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:CustomIPPrefix test-customipprefix /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/customIpPrefixes/test-customipprefix 
```
