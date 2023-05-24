ExpressRoutePort resource definition.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ExpressRoutePortCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var expressRoutePort = new AzureNative.Network.ExpressRoutePort("expressRoutePort", new()
    {
        BandwidthInGbps = 100,
        BillingType = "UnlimitedData",
        Encapsulation = "QinQ",
        ExpressRoutePortName = "portName",
        Location = "westus",
        PeeringLocation = "peeringLocationName",
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
		_, err := network.NewExpressRoutePort(ctx, "expressRoutePort", &network.ExpressRoutePortArgs{
			BandwidthInGbps:      pulumi.Int(100),
			BillingType:          pulumi.String("UnlimitedData"),
			Encapsulation:        pulumi.String("QinQ"),
			ExpressRoutePortName: pulumi.String("portName"),
			Location:             pulumi.String("westus"),
			PeeringLocation:      pulumi.String("peeringLocationName"),
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
import com.pulumi.azurenative.network.ExpressRoutePort;
import com.pulumi.azurenative.network.ExpressRoutePortArgs;
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
        var expressRoutePort = new ExpressRoutePort("expressRoutePort", ExpressRoutePortArgs.builder()        
            .bandwidthInGbps(100)
            .billingType("UnlimitedData")
            .encapsulation("QinQ")
            .expressRoutePortName("portName")
            .location("westus")
            .peeringLocation("peeringLocationName")
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const expressRoutePort = new azure_native.network.ExpressRoutePort("expressRoutePort", {
    bandwidthInGbps: 100,
    billingType: "UnlimitedData",
    encapsulation: "QinQ",
    expressRoutePortName: "portName",
    location: "westus",
    peeringLocation: "peeringLocationName",
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

express_route_port = azure_native.network.ExpressRoutePort("expressRoutePort",
    bandwidth_in_gbps=100,
    billing_type="UnlimitedData",
    encapsulation="QinQ",
    express_route_port_name="portName",
    location="westus",
    peering_location="peeringLocationName",
    resource_group_name="rg1")

```

```yaml
resources:
  expressRoutePort:
    type: azure-native:network:ExpressRoutePort
    properties:
      bandwidthInGbps: 100
      billingType: UnlimitedData
      encapsulation: QinQ
      expressRoutePortName: portName
      location: westus
      peeringLocation: peeringLocationName
      resourceGroupName: rg1

```

{{% /example %}}
{{% example %}}
### ExpressRoutePortUpdateLink
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var expressRoutePort = new AzureNative.Network.ExpressRoutePort("expressRoutePort", new()
    {
        BandwidthInGbps = 100,
        BillingType = "UnlimitedData",
        Encapsulation = "QinQ",
        ExpressRoutePortName = "portName",
        Links = new[]
        {
            new AzureNative.Network.Inputs.ExpressRouteLinkArgs
            {
                AdminState = "Enabled",
                Name = "link1",
            },
        },
        Location = "westus",
        PeeringLocation = "peeringLocationName",
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
		_, err := network.NewExpressRoutePort(ctx, "expressRoutePort", &network.ExpressRoutePortArgs{
			BandwidthInGbps:      pulumi.Int(100),
			BillingType:          pulumi.String("UnlimitedData"),
			Encapsulation:        pulumi.String("QinQ"),
			ExpressRoutePortName: pulumi.String("portName"),
			Links: []network.ExpressRouteLinkArgs{
				{
					AdminState: pulumi.String("Enabled"),
					Name:       pulumi.String("link1"),
				},
			},
			Location:          pulumi.String("westus"),
			PeeringLocation:   pulumi.String("peeringLocationName"),
			ResourceGroupName: pulumi.String("rg1"),
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
import com.pulumi.azurenative.network.ExpressRoutePort;
import com.pulumi.azurenative.network.ExpressRoutePortArgs;
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
        var expressRoutePort = new ExpressRoutePort("expressRoutePort", ExpressRoutePortArgs.builder()        
            .bandwidthInGbps(100)
            .billingType("UnlimitedData")
            .encapsulation("QinQ")
            .expressRoutePortName("portName")
            .links(Map.ofEntries(
                Map.entry("adminState", "Enabled"),
                Map.entry("name", "link1")
            ))
            .location("westus")
            .peeringLocation("peeringLocationName")
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const expressRoutePort = new azure_native.network.ExpressRoutePort("expressRoutePort", {
    bandwidthInGbps: 100,
    billingType: "UnlimitedData",
    encapsulation: "QinQ",
    expressRoutePortName: "portName",
    links: [{
        adminState: "Enabled",
        name: "link1",
    }],
    location: "westus",
    peeringLocation: "peeringLocationName",
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

express_route_port = azure_native.network.ExpressRoutePort("expressRoutePort",
    bandwidth_in_gbps=100,
    billing_type="UnlimitedData",
    encapsulation="QinQ",
    express_route_port_name="portName",
    links=[azure_native.network.ExpressRouteLinkArgs(
        admin_state="Enabled",
        name="link1",
    )],
    location="westus",
    peering_location="peeringLocationName",
    resource_group_name="rg1")

```

```yaml
resources:
  expressRoutePort:
    type: azure-native:network:ExpressRoutePort
    properties:
      bandwidthInGbps: 100
      billingType: UnlimitedData
      encapsulation: QinQ
      expressRoutePortName: portName
      links:
        - adminState: Enabled
          name: link1
      location: westus
      peeringLocation: peeringLocationName
      resourceGroupName: rg1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:ExpressRoutePort portName /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/expressRoutePorts/portName 
```
