Subnet in a virtual network resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create subnet
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var subnet = new AzureNative.Network.Subnet("subnet", new()
    {
        AddressPrefix = "10.0.0.0/16",
        ResourceGroupName = "subnet-test",
        SubnetName = "subnet1",
        VirtualNetworkName = "vnetname",
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
		_, err := network.NewSubnet(ctx, "subnet", &network.SubnetArgs{
			AddressPrefix:      pulumi.String("10.0.0.0/16"),
			ResourceGroupName:  pulumi.String("subnet-test"),
			SubnetName:         pulumi.String("subnet1"),
			VirtualNetworkName: pulumi.String("vnetname"),
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
import com.pulumi.azurenative.network.Subnet;
import com.pulumi.azurenative.network.SubnetArgs;
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
        var subnet = new Subnet("subnet", SubnetArgs.builder()        
            .addressPrefix("10.0.0.0/16")
            .resourceGroupName("subnet-test")
            .subnetName("subnet1")
            .virtualNetworkName("vnetname")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const subnet = new azure_native.network.Subnet("subnet", {
    addressPrefix: "10.0.0.0/16",
    resourceGroupName: "subnet-test",
    subnetName: "subnet1",
    virtualNetworkName: "vnetname",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

subnet = azure_native.network.Subnet("subnet",
    address_prefix="10.0.0.0/16",
    resource_group_name="subnet-test",
    subnet_name="subnet1",
    virtual_network_name="vnetname")

```

```yaml
resources:
  subnet:
    type: azure-native:network:Subnet
    properties:
      addressPrefix: 10.0.0.0/16
      resourceGroupName: subnet-test
      subnetName: subnet1
      virtualNetworkName: vnetname

```

{{% /example %}}
{{% example %}}
### Create subnet with a delegation
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var subnet = new AzureNative.Network.Subnet("subnet", new()
    {
        AddressPrefix = "10.0.0.0/16",
        ResourceGroupName = "subnet-test",
        SubnetName = "subnet1",
        VirtualNetworkName = "vnetname",
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
		_, err := network.NewSubnet(ctx, "subnet", &network.SubnetArgs{
			AddressPrefix:      pulumi.String("10.0.0.0/16"),
			ResourceGroupName:  pulumi.String("subnet-test"),
			SubnetName:         pulumi.String("subnet1"),
			VirtualNetworkName: pulumi.String("vnetname"),
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
import com.pulumi.azurenative.network.Subnet;
import com.pulumi.azurenative.network.SubnetArgs;
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
        var subnet = new Subnet("subnet", SubnetArgs.builder()        
            .addressPrefix("10.0.0.0/16")
            .resourceGroupName("subnet-test")
            .subnetName("subnet1")
            .virtualNetworkName("vnetname")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const subnet = new azure_native.network.Subnet("subnet", {
    addressPrefix: "10.0.0.0/16",
    resourceGroupName: "subnet-test",
    subnetName: "subnet1",
    virtualNetworkName: "vnetname",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

subnet = azure_native.network.Subnet("subnet",
    address_prefix="10.0.0.0/16",
    resource_group_name="subnet-test",
    subnet_name="subnet1",
    virtual_network_name="vnetname")

```

```yaml
resources:
  subnet:
    type: azure-native:network:Subnet
    properties:
      addressPrefix: 10.0.0.0/16
      resourceGroupName: subnet-test
      subnetName: subnet1
      virtualNetworkName: vnetname

```

{{% /example %}}
{{% example %}}
### Create subnet with service endpoints
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var subnet = new AzureNative.Network.Subnet("subnet", new()
    {
        AddressPrefix = "10.0.0.0/16",
        ResourceGroupName = "subnet-test",
        ServiceEndpoints = new[]
        {
            new AzureNative.Network.Inputs.ServiceEndpointPropertiesFormatArgs
            {
                Service = "Microsoft.Storage",
            },
        },
        SubnetName = "subnet1",
        VirtualNetworkName = "vnetname",
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
		_, err := network.NewSubnet(ctx, "subnet", &network.SubnetArgs{
			AddressPrefix:     pulumi.String("10.0.0.0/16"),
			ResourceGroupName: pulumi.String("subnet-test"),
			ServiceEndpoints: []network.ServiceEndpointPropertiesFormatArgs{
				{
					Service: pulumi.String("Microsoft.Storage"),
				},
			},
			SubnetName:         pulumi.String("subnet1"),
			VirtualNetworkName: pulumi.String("vnetname"),
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
import com.pulumi.azurenative.network.Subnet;
import com.pulumi.azurenative.network.SubnetArgs;
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
        var subnet = new Subnet("subnet", SubnetArgs.builder()        
            .addressPrefix("10.0.0.0/16")
            .resourceGroupName("subnet-test")
            .serviceEndpoints(Map.of("service", "Microsoft.Storage"))
            .subnetName("subnet1")
            .virtualNetworkName("vnetname")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const subnet = new azure_native.network.Subnet("subnet", {
    addressPrefix: "10.0.0.0/16",
    resourceGroupName: "subnet-test",
    serviceEndpoints: [{
        service: "Microsoft.Storage",
    }],
    subnetName: "subnet1",
    virtualNetworkName: "vnetname",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

subnet = azure_native.network.Subnet("subnet",
    address_prefix="10.0.0.0/16",
    resource_group_name="subnet-test",
    service_endpoints=[azure_native.network.ServiceEndpointPropertiesFormatArgs(
        service="Microsoft.Storage",
    )],
    subnet_name="subnet1",
    virtual_network_name="vnetname")

```

```yaml
resources:
  subnet:
    type: azure-native:network:Subnet
    properties:
      addressPrefix: 10.0.0.0/16
      resourceGroupName: subnet-test
      serviceEndpoints:
        - service: Microsoft.Storage
      subnetName: subnet1
      virtualNetworkName: vnetname

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:Subnet subnet1 /subscriptions/subid/resourceGroups/subnet-test/providers/Microsoft.Network/virtualNetworks/vnetname/subnets/subnet1 
```
