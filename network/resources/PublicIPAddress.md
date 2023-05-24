Public IP address resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create public IP address DNS
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var publicIPAddress = new AzureNative.Network.PublicIPAddress("publicIPAddress", new()
    {
        DnsSettings = new AzureNative.Network.Inputs.PublicIPAddressDnsSettingsArgs
        {
            DomainNameLabel = "dnslbl",
        },
        Location = "eastus",
        PublicIpAddressName = "test-ip",
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
		_, err := network.NewPublicIPAddress(ctx, "publicIPAddress", &network.PublicIPAddressArgs{
			DnsSettings: &network.PublicIPAddressDnsSettingsArgs{
				DomainNameLabel: pulumi.String("dnslbl"),
			},
			Location:            pulumi.String("eastus"),
			PublicIpAddressName: pulumi.String("test-ip"),
			ResourceGroupName:   pulumi.String("rg1"),
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
import com.pulumi.azurenative.network.PublicIPAddress;
import com.pulumi.azurenative.network.PublicIPAddressArgs;
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
        var publicIPAddress = new PublicIPAddress("publicIPAddress", PublicIPAddressArgs.builder()        
            .dnsSettings(Map.of("domainNameLabel", "dnslbl"))
            .location("eastus")
            .publicIpAddressName("test-ip")
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const publicIPAddress = new azure_native.network.PublicIPAddress("publicIPAddress", {
    dnsSettings: {
        domainNameLabel: "dnslbl",
    },
    location: "eastus",
    publicIpAddressName: "test-ip",
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

public_ip_address = azure_native.network.PublicIPAddress("publicIPAddress",
    dns_settings=azure_native.network.PublicIPAddressDnsSettingsArgs(
        domain_name_label="dnslbl",
    ),
    location="eastus",
    public_ip_address_name="test-ip",
    resource_group_name="rg1")

```

```yaml
resources:
  publicIPAddress:
    type: azure-native:network:PublicIPAddress
    properties:
      dnsSettings:
        domainNameLabel: dnslbl
      location: eastus
      publicIpAddressName: test-ip
      resourceGroupName: rg1

```

{{% /example %}}
{{% example %}}
### Create public IP address allocation method
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var publicIPAddress = new AzureNative.Network.PublicIPAddress("publicIPAddress", new()
    {
        IdleTimeoutInMinutes = 10,
        Location = "eastus",
        PublicIPAddressVersion = "IPv4",
        PublicIPAllocationMethod = "Static",
        PublicIpAddressName = "test-ip",
        ResourceGroupName = "rg1",
        Sku = new AzureNative.Network.Inputs.PublicIPAddressSkuArgs
        {
            Name = "Standard",
            Tier = "Global",
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
		_, err := network.NewPublicIPAddress(ctx, "publicIPAddress", &network.PublicIPAddressArgs{
			IdleTimeoutInMinutes:     pulumi.Int(10),
			Location:                 pulumi.String("eastus"),
			PublicIPAddressVersion:   pulumi.String("IPv4"),
			PublicIPAllocationMethod: pulumi.String("Static"),
			PublicIpAddressName:      pulumi.String("test-ip"),
			ResourceGroupName:        pulumi.String("rg1"),
			Sku: &network.PublicIPAddressSkuArgs{
				Name: pulumi.String("Standard"),
				Tier: pulumi.String("Global"),
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
import com.pulumi.azurenative.network.PublicIPAddress;
import com.pulumi.azurenative.network.PublicIPAddressArgs;
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
        var publicIPAddress = new PublicIPAddress("publicIPAddress", PublicIPAddressArgs.builder()        
            .idleTimeoutInMinutes(10)
            .location("eastus")
            .publicIPAddressVersion("IPv4")
            .publicIPAllocationMethod("Static")
            .publicIpAddressName("test-ip")
            .resourceGroupName("rg1")
            .sku(Map.ofEntries(
                Map.entry("name", "Standard"),
                Map.entry("tier", "Global")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const publicIPAddress = new azure_native.network.PublicIPAddress("publicIPAddress", {
    idleTimeoutInMinutes: 10,
    location: "eastus",
    publicIPAddressVersion: "IPv4",
    publicIPAllocationMethod: "Static",
    publicIpAddressName: "test-ip",
    resourceGroupName: "rg1",
    sku: {
        name: "Standard",
        tier: "Global",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

public_ip_address = azure_native.network.PublicIPAddress("publicIPAddress",
    idle_timeout_in_minutes=10,
    location="eastus",
    public_ip_address_version="IPv4",
    public_ip_allocation_method="Static",
    public_ip_address_name="test-ip",
    resource_group_name="rg1",
    sku=azure_native.network.PublicIPAddressSkuArgs(
        name="Standard",
        tier="Global",
    ))

```

```yaml
resources:
  publicIPAddress:
    type: azure-native:network:PublicIPAddress
    properties:
      idleTimeoutInMinutes: 10
      location: eastus
      publicIPAddressVersion: IPv4
      publicIPAllocationMethod: Static
      publicIpAddressName: test-ip
      resourceGroupName: rg1
      sku:
        name: Standard
        tier: Global

```

{{% /example %}}
{{% example %}}
### Create public IP address defaults
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var publicIPAddress = new AzureNative.Network.PublicIPAddress("publicIPAddress", new()
    {
        Location = "eastus",
        PublicIpAddressName = "test-ip",
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
		_, err := network.NewPublicIPAddress(ctx, "publicIPAddress", &network.PublicIPAddressArgs{
			Location:            pulumi.String("eastus"),
			PublicIpAddressName: pulumi.String("test-ip"),
			ResourceGroupName:   pulumi.String("rg1"),
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
import com.pulumi.azurenative.network.PublicIPAddress;
import com.pulumi.azurenative.network.PublicIPAddressArgs;
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
        var publicIPAddress = new PublicIPAddress("publicIPAddress", PublicIPAddressArgs.builder()        
            .location("eastus")
            .publicIpAddressName("test-ip")
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const publicIPAddress = new azure_native.network.PublicIPAddress("publicIPAddress", {
    location: "eastus",
    publicIpAddressName: "test-ip",
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

public_ip_address = azure_native.network.PublicIPAddress("publicIPAddress",
    location="eastus",
    public_ip_address_name="test-ip",
    resource_group_name="rg1")

```

```yaml
resources:
  publicIPAddress:
    type: azure-native:network:PublicIPAddress
    properties:
      location: eastus
      publicIpAddressName: test-ip
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:PublicIPAddress testDNS-ip /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/test-ip 
```
