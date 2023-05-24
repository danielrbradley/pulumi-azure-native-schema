Public IP prefix resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create public IP prefix allocation method
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var publicIPPrefix = new AzureNative.Network.PublicIPPrefix("publicIPPrefix", new()
    {
        Location = "westus",
        PrefixLength = 30,
        PublicIPAddressVersion = "IPv4",
        PublicIpPrefixName = "test-ipprefix",
        ResourceGroupName = "rg1",
        Sku = new AzureNative.Network.Inputs.PublicIPPrefixSkuArgs
        {
            Name = "Standard",
            Tier = "Regional",
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
		_, err := network.NewPublicIPPrefix(ctx, "publicIPPrefix", &network.PublicIPPrefixArgs{
			Location:               pulumi.String("westus"),
			PrefixLength:           pulumi.Int(30),
			PublicIPAddressVersion: pulumi.String("IPv4"),
			PublicIpPrefixName:     pulumi.String("test-ipprefix"),
			ResourceGroupName:      pulumi.String("rg1"),
			Sku: &network.PublicIPPrefixSkuArgs{
				Name: pulumi.String("Standard"),
				Tier: pulumi.String("Regional"),
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
import com.pulumi.azurenative.network.PublicIPPrefix;
import com.pulumi.azurenative.network.PublicIPPrefixArgs;
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
        var publicIPPrefix = new PublicIPPrefix("publicIPPrefix", PublicIPPrefixArgs.builder()        
            .location("westus")
            .prefixLength(30)
            .publicIPAddressVersion("IPv4")
            .publicIpPrefixName("test-ipprefix")
            .resourceGroupName("rg1")
            .sku(Map.ofEntries(
                Map.entry("name", "Standard"),
                Map.entry("tier", "Regional")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const publicIPPrefix = new azure_native.network.PublicIPPrefix("publicIPPrefix", {
    location: "westus",
    prefixLength: 30,
    publicIPAddressVersion: "IPv4",
    publicIpPrefixName: "test-ipprefix",
    resourceGroupName: "rg1",
    sku: {
        name: "Standard",
        tier: "Regional",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

public_ip_prefix = azure_native.network.PublicIPPrefix("publicIPPrefix",
    location="westus",
    prefix_length=30,
    public_ip_address_version="IPv4",
    public_ip_prefix_name="test-ipprefix",
    resource_group_name="rg1",
    sku=azure_native.network.PublicIPPrefixSkuArgs(
        name="Standard",
        tier="Regional",
    ))

```

```yaml
resources:
  publicIPPrefix:
    type: azure-native:network:PublicIPPrefix
    properties:
      location: westus
      prefixLength: 30
      publicIPAddressVersion: IPv4
      publicIpPrefixName: test-ipprefix
      resourceGroupName: rg1
      sku:
        name: Standard
        tier: Regional

```

{{% /example %}}
{{% example %}}
### Create public IP prefix defaults
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var publicIPPrefix = new AzureNative.Network.PublicIPPrefix("publicIPPrefix", new()
    {
        Location = "westus",
        PrefixLength = 30,
        PublicIpPrefixName = "test-ipprefix",
        ResourceGroupName = "rg1",
        Sku = new AzureNative.Network.Inputs.PublicIPPrefixSkuArgs
        {
            Name = "Standard",
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
		_, err := network.NewPublicIPPrefix(ctx, "publicIPPrefix", &network.PublicIPPrefixArgs{
			Location:           pulumi.String("westus"),
			PrefixLength:       pulumi.Int(30),
			PublicIpPrefixName: pulumi.String("test-ipprefix"),
			ResourceGroupName:  pulumi.String("rg1"),
			Sku: &network.PublicIPPrefixSkuArgs{
				Name: pulumi.String("Standard"),
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
import com.pulumi.azurenative.network.PublicIPPrefix;
import com.pulumi.azurenative.network.PublicIPPrefixArgs;
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
        var publicIPPrefix = new PublicIPPrefix("publicIPPrefix", PublicIPPrefixArgs.builder()        
            .location("westus")
            .prefixLength(30)
            .publicIpPrefixName("test-ipprefix")
            .resourceGroupName("rg1")
            .sku(Map.of("name", "Standard"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const publicIPPrefix = new azure_native.network.PublicIPPrefix("publicIPPrefix", {
    location: "westus",
    prefixLength: 30,
    publicIpPrefixName: "test-ipprefix",
    resourceGroupName: "rg1",
    sku: {
        name: "Standard",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

public_ip_prefix = azure_native.network.PublicIPPrefix("publicIPPrefix",
    location="westus",
    prefix_length=30,
    public_ip_prefix_name="test-ipprefix",
    resource_group_name="rg1",
    sku=azure_native.network.PublicIPPrefixSkuArgs(
        name="Standard",
    ))

```

```yaml
resources:
  publicIPPrefix:
    type: azure-native:network:PublicIPPrefix
    properties:
      location: westus
      prefixLength: 30
      publicIpPrefixName: test-ipprefix
      resourceGroupName: rg1
      sku:
        name: Standard

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:PublicIPPrefix test-ipprefix /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPPrefixes/test-ipprefix 
```
