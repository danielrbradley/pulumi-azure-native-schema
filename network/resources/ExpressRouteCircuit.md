ExpressRouteCircuit resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create ExpressRouteCircuit
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var expressRouteCircuit = new AzureNative.Network.ExpressRouteCircuit("expressRouteCircuit", new()
    {
        AllowClassicOperations = false,
        Authorizations = new[] {},
        CircuitName = "circuitName",
        Location = "Brazil South",
        Peerings = new[] {},
        ResourceGroupName = "rg1",
        ServiceProviderProperties = new AzureNative.Network.Inputs.ExpressRouteCircuitServiceProviderPropertiesArgs
        {
            BandwidthInMbps = 200,
            PeeringLocation = "Silicon Valley",
            ServiceProviderName = "Equinix",
        },
        Sku = new AzureNative.Network.Inputs.ExpressRouteCircuitSkuArgs
        {
            Family = "MeteredData",
            Name = "Standard_MeteredData",
            Tier = "Standard",
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
		_, err := network.NewExpressRouteCircuit(ctx, "expressRouteCircuit", &network.ExpressRouteCircuitArgs{
			AllowClassicOperations: pulumi.Bool(false),
			Authorizations:         network.ExpressRouteCircuitAuthorizationTypeArray{},
			CircuitName:            pulumi.String("circuitName"),
			Location:               pulumi.String("Brazil South"),
			Peerings:               network.ExpressRouteCircuitPeeringTypeArray{},
			ResourceGroupName:      pulumi.String("rg1"),
			ServiceProviderProperties: &network.ExpressRouteCircuitServiceProviderPropertiesArgs{
				BandwidthInMbps:     pulumi.Int(200),
				PeeringLocation:     pulumi.String("Silicon Valley"),
				ServiceProviderName: pulumi.String("Equinix"),
			},
			Sku: &network.ExpressRouteCircuitSkuArgs{
				Family: pulumi.String("MeteredData"),
				Name:   pulumi.String("Standard_MeteredData"),
				Tier:   pulumi.String("Standard"),
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
import com.pulumi.azurenative.network.ExpressRouteCircuit;
import com.pulumi.azurenative.network.ExpressRouteCircuitArgs;
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
        var expressRouteCircuit = new ExpressRouteCircuit("expressRouteCircuit", ExpressRouteCircuitArgs.builder()        
            .allowClassicOperations(false)
            .authorizations()
            .circuitName("circuitName")
            .location("Brazil South")
            .peerings()
            .resourceGroupName("rg1")
            .serviceProviderProperties(Map.ofEntries(
                Map.entry("bandwidthInMbps", 200),
                Map.entry("peeringLocation", "Silicon Valley"),
                Map.entry("serviceProviderName", "Equinix")
            ))
            .sku(Map.ofEntries(
                Map.entry("family", "MeteredData"),
                Map.entry("name", "Standard_MeteredData"),
                Map.entry("tier", "Standard")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const expressRouteCircuit = new azure_native.network.ExpressRouteCircuit("expressRouteCircuit", {
    allowClassicOperations: false,
    authorizations: [],
    circuitName: "circuitName",
    location: "Brazil South",
    peerings: [],
    resourceGroupName: "rg1",
    serviceProviderProperties: {
        bandwidthInMbps: 200,
        peeringLocation: "Silicon Valley",
        serviceProviderName: "Equinix",
    },
    sku: {
        family: "MeteredData",
        name: "Standard_MeteredData",
        tier: "Standard",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

express_route_circuit = azure_native.network.ExpressRouteCircuit("expressRouteCircuit",
    allow_classic_operations=False,
    authorizations=[],
    circuit_name="circuitName",
    location="Brazil South",
    peerings=[],
    resource_group_name="rg1",
    service_provider_properties=azure_native.network.ExpressRouteCircuitServiceProviderPropertiesArgs(
        bandwidth_in_mbps=200,
        peering_location="Silicon Valley",
        service_provider_name="Equinix",
    ),
    sku=azure_native.network.ExpressRouteCircuitSkuArgs(
        family="MeteredData",
        name="Standard_MeteredData",
        tier="Standard",
    ))

```

```yaml
resources:
  expressRouteCircuit:
    type: azure-native:network:ExpressRouteCircuit
    properties:
      allowClassicOperations: false
      authorizations: []
      circuitName: circuitName
      location: Brazil South
      peerings: []
      resourceGroupName: rg1
      serviceProviderProperties:
        bandwidthInMbps: 200
        peeringLocation: Silicon Valley
        serviceProviderName: Equinix
      sku:
        family: MeteredData
        name: Standard_MeteredData
        tier: Standard

```

{{% /example %}}
{{% example %}}
### Create ExpressRouteCircuit on ExpressRoutePort
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var expressRouteCircuit = new AzureNative.Network.ExpressRouteCircuit("expressRouteCircuit", new()
    {
        AuthorizationKey = "b0be57f5-1fba-463b-adec-ffe767354cdd",
        BandwidthInGbps = 10,
        CircuitName = "expressRouteCircuit1",
        ExpressRoutePort = new AzureNative.Network.Inputs.SubResourceArgs
        {
            Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/expressRoutePorts/portName",
        },
        Location = "westus",
        ResourceGroupName = "rg1",
        Sku = new AzureNative.Network.Inputs.ExpressRouteCircuitSkuArgs
        {
            Family = "MeteredData",
            Name = "Premium_MeteredData",
            Tier = "Premium",
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
		_, err := network.NewExpressRouteCircuit(ctx, "expressRouteCircuit", &network.ExpressRouteCircuitArgs{
			AuthorizationKey: pulumi.String("b0be57f5-1fba-463b-adec-ffe767354cdd"),
			BandwidthInGbps:  pulumi.Float64(10),
			CircuitName:      pulumi.String("expressRouteCircuit1"),
			ExpressRoutePort: &network.SubResourceArgs{
				Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/expressRoutePorts/portName"),
			},
			Location:          pulumi.String("westus"),
			ResourceGroupName: pulumi.String("rg1"),
			Sku: &network.ExpressRouteCircuitSkuArgs{
				Family: pulumi.String("MeteredData"),
				Name:   pulumi.String("Premium_MeteredData"),
				Tier:   pulumi.String("Premium"),
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
import com.pulumi.azurenative.network.ExpressRouteCircuit;
import com.pulumi.azurenative.network.ExpressRouteCircuitArgs;
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
        var expressRouteCircuit = new ExpressRouteCircuit("expressRouteCircuit", ExpressRouteCircuitArgs.builder()        
            .authorizationKey("b0be57f5-1fba-463b-adec-ffe767354cdd")
            .bandwidthInGbps(10)
            .circuitName("expressRouteCircuit1")
            .expressRoutePort(Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/expressRoutePorts/portName"))
            .location("westus")
            .resourceGroupName("rg1")
            .sku(Map.ofEntries(
                Map.entry("family", "MeteredData"),
                Map.entry("name", "Premium_MeteredData"),
                Map.entry("tier", "Premium")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const expressRouteCircuit = new azure_native.network.ExpressRouteCircuit("expressRouteCircuit", {
    authorizationKey: "b0be57f5-1fba-463b-adec-ffe767354cdd",
    bandwidthInGbps: 10,
    circuitName: "expressRouteCircuit1",
    expressRoutePort: {
        id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/expressRoutePorts/portName",
    },
    location: "westus",
    resourceGroupName: "rg1",
    sku: {
        family: "MeteredData",
        name: "Premium_MeteredData",
        tier: "Premium",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

express_route_circuit = azure_native.network.ExpressRouteCircuit("expressRouteCircuit",
    authorization_key="b0be57f5-1fba-463b-adec-ffe767354cdd",
    bandwidth_in_gbps=10,
    circuit_name="expressRouteCircuit1",
    express_route_port=azure_native.network.SubResourceArgs(
        id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/expressRoutePorts/portName",
    ),
    location="westus",
    resource_group_name="rg1",
    sku=azure_native.network.ExpressRouteCircuitSkuArgs(
        family="MeteredData",
        name="Premium_MeteredData",
        tier="Premium",
    ))

```

```yaml
resources:
  expressRouteCircuit:
    type: azure-native:network:ExpressRouteCircuit
    properties:
      authorizationKey: b0be57f5-1fba-463b-adec-ffe767354cdd
      bandwidthInGbps: 10
      circuitName: expressRouteCircuit1
      expressRoutePort:
        id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/expressRoutePorts/portName
      location: westus
      resourceGroupName: rg1
      sku:
        family: MeteredData
        name: Premium_MeteredData
        tier: Premium

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:ExpressRouteCircuit expressRouteCircuit1 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/expressRouteCircuits/expressRouteCircuit1 
```
