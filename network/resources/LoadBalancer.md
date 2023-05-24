LoadBalancer resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create load balancer
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var loadBalancer = new AzureNative.Network.LoadBalancer("loadBalancer", new()
    {
        BackendAddressPools = new[]
        {
            new AzureNative.Network.Inputs.BackendAddressPoolArgs
            {
                Name = "be-lb",
            },
        },
        FrontendIPConfigurations = new[]
        {
            new AzureNative.Network.Inputs.FrontendIPConfigurationArgs
            {
                Name = "fe-lb",
                Subnet = new AzureNative.Network.Inputs.SubnetArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb",
                },
            },
        },
        InboundNatPools = new[] {},
        InboundNatRules = new[]
        {
            new AzureNative.Network.Inputs.InboundNatRuleArgs
            {
                BackendPort = 3389,
                EnableFloatingIP = true,
                EnableTcpReset = false,
                FrontendIPConfiguration = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
                },
                FrontendPort = 3389,
                IdleTimeoutInMinutes = 15,
                Name = "in-nat-rule",
                Protocol = "Tcp",
            },
        },
        LoadBalancerName = "lb",
        LoadBalancingRules = new[]
        {
            new AzureNative.Network.Inputs.LoadBalancingRuleArgs
            {
                BackendAddressPool = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb",
                },
                BackendPort = 80,
                EnableFloatingIP = true,
                EnableTcpReset = false,
                FrontendIPConfiguration = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
                },
                FrontendPort = 80,
                IdleTimeoutInMinutes = 15,
                LoadDistribution = "Default",
                Name = "rulelb",
                Probe = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb",
                },
                Protocol = "Tcp",
            },
        },
        Location = "eastus",
        Probes = new[]
        {
            new AzureNative.Network.Inputs.ProbeArgs
            {
                IntervalInSeconds = 15,
                Name = "probe-lb",
                NumberOfProbes = 2,
                Port = 80,
                ProbeThreshold = 1,
                Protocol = "Http",
                RequestPath = "healthcheck.aspx",
            },
        },
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
		_, err := network.NewLoadBalancer(ctx, "loadBalancer", &network.LoadBalancerArgs{
			BackendAddressPools: []network.BackendAddressPoolArgs{
				{
					Name: pulumi.String("be-lb"),
				},
			},
			FrontendIPConfigurations: []network.FrontendIPConfigurationArgs{
				{
					Name: pulumi.String("fe-lb"),
					Subnet: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb"),
					},
				},
			},
			InboundNatPools: network.InboundNatPoolArray{},
			InboundNatRules: []network.InboundNatRuleTypeArgs{
				{
					BackendPort:      pulumi.Int(3389),
					EnableFloatingIP: pulumi.Bool(true),
					EnableTcpReset:   pulumi.Bool(false),
					FrontendIPConfiguration: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb"),
					},
					FrontendPort:         pulumi.Int(3389),
					IdleTimeoutInMinutes: pulumi.Int(15),
					Name:                 pulumi.String("in-nat-rule"),
					Protocol:             pulumi.String("Tcp"),
				},
			},
			LoadBalancerName: pulumi.String("lb"),
			LoadBalancingRules: []network.LoadBalancingRuleArgs{
				{
					BackendAddressPool: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb"),
					},
					BackendPort:      pulumi.Int(80),
					EnableFloatingIP: pulumi.Bool(true),
					EnableTcpReset:   pulumi.Bool(false),
					FrontendIPConfiguration: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb"),
					},
					FrontendPort:         pulumi.Int(80),
					IdleTimeoutInMinutes: pulumi.Int(15),
					LoadDistribution:     pulumi.String("Default"),
					Name:                 pulumi.String("rulelb"),
					Probe: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb"),
					},
					Protocol: pulumi.String("Tcp"),
				},
			},
			Location: pulumi.String("eastus"),
			Probes: []network.ProbeArgs{
				{
					IntervalInSeconds: pulumi.Int(15),
					Name:              pulumi.String("probe-lb"),
					NumberOfProbes:    pulumi.Int(2),
					Port:              pulumi.Int(80),
					ProbeThreshold:    pulumi.Int(1),
					Protocol:          pulumi.String("Http"),
					RequestPath:       pulumi.String("healthcheck.aspx"),
				},
			},
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
import com.pulumi.azurenative.network.LoadBalancer;
import com.pulumi.azurenative.network.LoadBalancerArgs;
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
        var loadBalancer = new LoadBalancer("loadBalancer", LoadBalancerArgs.builder()        
            .backendAddressPools(Map.of("name", "be-lb"))
            .frontendIPConfigurations(Map.ofEntries(
                Map.entry("name", "fe-lb"),
                Map.entry("subnet", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb"))
            ))
            .inboundNatPools()
            .inboundNatRules(Map.ofEntries(
                Map.entry("backendPort", 3389),
                Map.entry("enableFloatingIP", true),
                Map.entry("enableTcpReset", false),
                Map.entry("frontendIPConfiguration", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb")),
                Map.entry("frontendPort", 3389),
                Map.entry("idleTimeoutInMinutes", 15),
                Map.entry("name", "in-nat-rule"),
                Map.entry("protocol", "Tcp")
            ))
            .loadBalancerName("lb")
            .loadBalancingRules(Map.ofEntries(
                Map.entry("backendAddressPool", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb")),
                Map.entry("backendPort", 80),
                Map.entry("enableFloatingIP", true),
                Map.entry("enableTcpReset", false),
                Map.entry("frontendIPConfiguration", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb")),
                Map.entry("frontendPort", 80),
                Map.entry("idleTimeoutInMinutes", 15),
                Map.entry("loadDistribution", "Default"),
                Map.entry("name", "rulelb"),
                Map.entry("probe", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb")),
                Map.entry("protocol", "Tcp")
            ))
            .location("eastus")
            .probes(Map.ofEntries(
                Map.entry("intervalInSeconds", 15),
                Map.entry("name", "probe-lb"),
                Map.entry("numberOfProbes", 2),
                Map.entry("port", 80),
                Map.entry("probeThreshold", 1),
                Map.entry("protocol", "Http"),
                Map.entry("requestPath", "healthcheck.aspx")
            ))
            .resourceGroupName("rg1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const loadBalancer = new azure_native.network.LoadBalancer("loadBalancer", {
    backendAddressPools: [{
        name: "be-lb",
    }],
    frontendIPConfigurations: [{
        name: "fe-lb",
        subnet: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb",
        },
    }],
    inboundNatPools: [],
    inboundNatRules: [{
        backendPort: 3389,
        enableFloatingIP: true,
        enableTcpReset: false,
        frontendIPConfiguration: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
        },
        frontendPort: 3389,
        idleTimeoutInMinutes: 15,
        name: "in-nat-rule",
        protocol: "Tcp",
    }],
    loadBalancerName: "lb",
    loadBalancingRules: [{
        backendAddressPool: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb",
        },
        backendPort: 80,
        enableFloatingIP: true,
        enableTcpReset: false,
        frontendIPConfiguration: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
        },
        frontendPort: 80,
        idleTimeoutInMinutes: 15,
        loadDistribution: "Default",
        name: "rulelb",
        probe: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb",
        },
        protocol: "Tcp",
    }],
    location: "eastus",
    probes: [{
        intervalInSeconds: 15,
        name: "probe-lb",
        numberOfProbes: 2,
        port: 80,
        probeThreshold: 1,
        protocol: "Http",
        requestPath: "healthcheck.aspx",
    }],
    resourceGroupName: "rg1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

load_balancer = azure_native.network.LoadBalancer("loadBalancer",
    backend_address_pools=[azure_native.network.BackendAddressPoolArgs(
        name="be-lb",
    )],
    frontend_ip_configurations=[{
        "name": "fe-lb",
        "subnet": azure_native.network.SubnetArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb",
        ),
    }],
    inbound_nat_pools=[],
    inbound_nat_rules=[{
        "backendPort": 3389,
        "enableFloatingIP": True,
        "enableTcpReset": False,
        "frontendIPConfiguration": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
        ),
        "frontendPort": 3389,
        "idleTimeoutInMinutes": 15,
        "name": "in-nat-rule",
        "protocol": "Tcp",
    }],
    load_balancer_name="lb",
    load_balancing_rules=[{
        "backendAddressPool": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb",
        ),
        "backendPort": 80,
        "enableFloatingIP": True,
        "enableTcpReset": False,
        "frontendIPConfiguration": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
        ),
        "frontendPort": 80,
        "idleTimeoutInMinutes": 15,
        "loadDistribution": "Default",
        "name": "rulelb",
        "probe": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb",
        ),
        "protocol": "Tcp",
    }],
    location="eastus",
    probes=[azure_native.network.ProbeArgs(
        interval_in_seconds=15,
        name="probe-lb",
        number_of_probes=2,
        port=80,
        probe_threshold=1,
        protocol="Http",
        request_path="healthcheck.aspx",
    )],
    resource_group_name="rg1")

```

```yaml
resources:
  loadBalancer:
    type: azure-native:network:LoadBalancer
    properties:
      backendAddressPools:
        - name: be-lb
      frontendIPConfigurations:
        - name: fe-lb
          subnet:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb
      inboundNatPools: []
      inboundNatRules:
        - backendPort: 3389
          enableFloatingIP: true
          enableTcpReset: false
          frontendIPConfiguration:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb
          frontendPort: 3389
          idleTimeoutInMinutes: 15
          name: in-nat-rule
          protocol: Tcp
      loadBalancerName: lb
      loadBalancingRules:
        - backendAddressPool:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb
          backendPort: 80
          enableFloatingIP: true
          enableTcpReset: false
          frontendIPConfiguration:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb
          frontendPort: 80
          idleTimeoutInMinutes: 15
          loadDistribution: Default
          name: rulelb
          probe:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb
          protocol: Tcp
      location: eastus
      probes:
        - intervalInSeconds: 15
          name: probe-lb
          numberOfProbes: 2
          port: 80
          probeThreshold: 1
          protocol: Http
          requestPath: healthcheck.aspx
      resourceGroupName: rg1

```

{{% /example %}}
{{% example %}}
### Create load balancer with Frontend IP in Zone 1
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var loadBalancer = new AzureNative.Network.LoadBalancer("loadBalancer", new()
    {
        BackendAddressPools = new[]
        {
            new AzureNative.Network.Inputs.BackendAddressPoolArgs
            {
                Name = "be-lb",
            },
        },
        FrontendIPConfigurations = new[]
        {
            new AzureNative.Network.Inputs.FrontendIPConfigurationArgs
            {
                Name = "fe-lb",
                Subnet = new AzureNative.Network.Inputs.SubnetArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb",
                },
                Zones = new[]
                {
                    "1",
                },
            },
        },
        InboundNatPools = new[] {},
        InboundNatRules = new[]
        {
            new AzureNative.Network.Inputs.InboundNatRuleArgs
            {
                BackendPort = 3389,
                EnableFloatingIP = true,
                FrontendIPConfiguration = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
                },
                FrontendPort = 3389,
                IdleTimeoutInMinutes = 15,
                Name = "in-nat-rule",
                Protocol = "Tcp",
            },
        },
        LoadBalancerName = "lb",
        LoadBalancingRules = new[]
        {
            new AzureNative.Network.Inputs.LoadBalancingRuleArgs
            {
                BackendAddressPool = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb",
                },
                BackendPort = 80,
                EnableFloatingIP = true,
                FrontendIPConfiguration = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
                },
                FrontendPort = 80,
                IdleTimeoutInMinutes = 15,
                LoadDistribution = "Default",
                Name = "rulelb",
                Probe = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb",
                },
                Protocol = "Tcp",
            },
        },
        Location = "eastus",
        OutboundRules = new[] {},
        Probes = new[]
        {
            new AzureNative.Network.Inputs.ProbeArgs
            {
                IntervalInSeconds = 15,
                Name = "probe-lb",
                NumberOfProbes = 2,
                Port = 80,
                ProbeThreshold = 1,
                Protocol = "Http",
                RequestPath = "healthcheck.aspx",
            },
        },
        ResourceGroupName = "rg1",
        Sku = new AzureNative.Network.Inputs.LoadBalancerSkuArgs
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
		_, err := network.NewLoadBalancer(ctx, "loadBalancer", &network.LoadBalancerArgs{
			BackendAddressPools: []network.BackendAddressPoolArgs{
				{
					Name: pulumi.String("be-lb"),
				},
			},
			FrontendIPConfigurations: []network.FrontendIPConfigurationArgs{
				{
					Name: pulumi.String("fe-lb"),
					Subnet: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb"),
					},
					Zones: pulumi.StringArray{
						pulumi.String("1"),
					},
				},
			},
			InboundNatPools: network.InboundNatPoolArray{},
			InboundNatRules: []network.InboundNatRuleTypeArgs{
				{
					BackendPort:      pulumi.Int(3389),
					EnableFloatingIP: pulumi.Bool(true),
					FrontendIPConfiguration: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb"),
					},
					FrontendPort:         pulumi.Int(3389),
					IdleTimeoutInMinutes: pulumi.Int(15),
					Name:                 pulumi.String("in-nat-rule"),
					Protocol:             pulumi.String("Tcp"),
				},
			},
			LoadBalancerName: pulumi.String("lb"),
			LoadBalancingRules: []network.LoadBalancingRuleArgs{
				{
					BackendAddressPool: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb"),
					},
					BackendPort:      pulumi.Int(80),
					EnableFloatingIP: pulumi.Bool(true),
					FrontendIPConfiguration: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb"),
					},
					FrontendPort:         pulumi.Int(80),
					IdleTimeoutInMinutes: pulumi.Int(15),
					LoadDistribution:     pulumi.String("Default"),
					Name:                 pulumi.String("rulelb"),
					Probe: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb"),
					},
					Protocol: pulumi.String("Tcp"),
				},
			},
			Location:      pulumi.String("eastus"),
			OutboundRules: network.OutboundRuleArray{},
			Probes: []network.ProbeArgs{
				{
					IntervalInSeconds: pulumi.Int(15),
					Name:              pulumi.String("probe-lb"),
					NumberOfProbes:    pulumi.Int(2),
					Port:              pulumi.Int(80),
					ProbeThreshold:    pulumi.Int(1),
					Protocol:          pulumi.String("Http"),
					RequestPath:       pulumi.String("healthcheck.aspx"),
				},
			},
			ResourceGroupName: pulumi.String("rg1"),
			Sku: &network.LoadBalancerSkuArgs{
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
import com.pulumi.azurenative.network.LoadBalancer;
import com.pulumi.azurenative.network.LoadBalancerArgs;
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
        var loadBalancer = new LoadBalancer("loadBalancer", LoadBalancerArgs.builder()        
            .backendAddressPools(Map.of("name", "be-lb"))
            .frontendIPConfigurations(Map.ofEntries(
                Map.entry("name", "fe-lb"),
                Map.entry("subnet", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb")),
                Map.entry("zones", "1")
            ))
            .inboundNatPools()
            .inboundNatRules(Map.ofEntries(
                Map.entry("backendPort", 3389),
                Map.entry("enableFloatingIP", true),
                Map.entry("frontendIPConfiguration", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb")),
                Map.entry("frontendPort", 3389),
                Map.entry("idleTimeoutInMinutes", 15),
                Map.entry("name", "in-nat-rule"),
                Map.entry("protocol", "Tcp")
            ))
            .loadBalancerName("lb")
            .loadBalancingRules(Map.ofEntries(
                Map.entry("backendAddressPool", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb")),
                Map.entry("backendPort", 80),
                Map.entry("enableFloatingIP", true),
                Map.entry("frontendIPConfiguration", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb")),
                Map.entry("frontendPort", 80),
                Map.entry("idleTimeoutInMinutes", 15),
                Map.entry("loadDistribution", "Default"),
                Map.entry("name", "rulelb"),
                Map.entry("probe", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb")),
                Map.entry("protocol", "Tcp")
            ))
            .location("eastus")
            .outboundRules()
            .probes(Map.ofEntries(
                Map.entry("intervalInSeconds", 15),
                Map.entry("name", "probe-lb"),
                Map.entry("numberOfProbes", 2),
                Map.entry("port", 80),
                Map.entry("probeThreshold", 1),
                Map.entry("protocol", "Http"),
                Map.entry("requestPath", "healthcheck.aspx")
            ))
            .resourceGroupName("rg1")
            .sku(Map.of("name", "Standard"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const loadBalancer = new azure_native.network.LoadBalancer("loadBalancer", {
    backendAddressPools: [{
        name: "be-lb",
    }],
    frontendIPConfigurations: [{
        name: "fe-lb",
        subnet: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb",
        },
        zones: ["1"],
    }],
    inboundNatPools: [],
    inboundNatRules: [{
        backendPort: 3389,
        enableFloatingIP: true,
        frontendIPConfiguration: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
        },
        frontendPort: 3389,
        idleTimeoutInMinutes: 15,
        name: "in-nat-rule",
        protocol: "Tcp",
    }],
    loadBalancerName: "lb",
    loadBalancingRules: [{
        backendAddressPool: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb",
        },
        backendPort: 80,
        enableFloatingIP: true,
        frontendIPConfiguration: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
        },
        frontendPort: 80,
        idleTimeoutInMinutes: 15,
        loadDistribution: "Default",
        name: "rulelb",
        probe: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb",
        },
        protocol: "Tcp",
    }],
    location: "eastus",
    outboundRules: [],
    probes: [{
        intervalInSeconds: 15,
        name: "probe-lb",
        numberOfProbes: 2,
        port: 80,
        probeThreshold: 1,
        protocol: "Http",
        requestPath: "healthcheck.aspx",
    }],
    resourceGroupName: "rg1",
    sku: {
        name: "Standard",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

load_balancer = azure_native.network.LoadBalancer("loadBalancer",
    backend_address_pools=[azure_native.network.BackendAddressPoolArgs(
        name="be-lb",
    )],
    frontend_ip_configurations=[{
        "name": "fe-lb",
        "subnet": azure_native.network.SubnetArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb",
        ),
        "zones": ["1"],
    }],
    inbound_nat_pools=[],
    inbound_nat_rules=[{
        "backendPort": 3389,
        "enableFloatingIP": True,
        "frontendIPConfiguration": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
        ),
        "frontendPort": 3389,
        "idleTimeoutInMinutes": 15,
        "name": "in-nat-rule",
        "protocol": "Tcp",
    }],
    load_balancer_name="lb",
    load_balancing_rules=[{
        "backendAddressPool": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb",
        ),
        "backendPort": 80,
        "enableFloatingIP": True,
        "frontendIPConfiguration": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
        ),
        "frontendPort": 80,
        "idleTimeoutInMinutes": 15,
        "loadDistribution": "Default",
        "name": "rulelb",
        "probe": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb",
        ),
        "protocol": "Tcp",
    }],
    location="eastus",
    outbound_rules=[],
    probes=[azure_native.network.ProbeArgs(
        interval_in_seconds=15,
        name="probe-lb",
        number_of_probes=2,
        port=80,
        probe_threshold=1,
        protocol="Http",
        request_path="healthcheck.aspx",
    )],
    resource_group_name="rg1",
    sku=azure_native.network.LoadBalancerSkuArgs(
        name="Standard",
    ))

```

```yaml
resources:
  loadBalancer:
    type: azure-native:network:LoadBalancer
    properties:
      backendAddressPools:
        - name: be-lb
      frontendIPConfigurations:
        - name: fe-lb
          subnet:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb
          zones:
            - '1'
      inboundNatPools: []
      inboundNatRules:
        - backendPort: 3389
          enableFloatingIP: true
          frontendIPConfiguration:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb
          frontendPort: 3389
          idleTimeoutInMinutes: 15
          name: in-nat-rule
          protocol: Tcp
      loadBalancerName: lb
      loadBalancingRules:
        - backendAddressPool:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb
          backendPort: 80
          enableFloatingIP: true
          frontendIPConfiguration:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb
          frontendPort: 80
          idleTimeoutInMinutes: 15
          loadDistribution: Default
          name: rulelb
          probe:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb
          protocol: Tcp
      location: eastus
      outboundRules: []
      probes:
        - intervalInSeconds: 15
          name: probe-lb
          numberOfProbes: 2
          port: 80
          probeThreshold: 1
          protocol: Http
          requestPath: healthcheck.aspx
      resourceGroupName: rg1
      sku:
        name: Standard

```

{{% /example %}}
{{% example %}}
### Create load balancer with Gateway Load Balancer Consumer configured
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var loadBalancer = new AzureNative.Network.LoadBalancer("loadBalancer", new()
    {
        BackendAddressPools = new[]
        {
            new AzureNative.Network.Inputs.BackendAddressPoolArgs
            {
                Name = "be-lb",
            },
        },
        FrontendIPConfigurations = new[]
        {
            new AzureNative.Network.Inputs.FrontendIPConfigurationArgs
            {
                GatewayLoadBalancer = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb-provider",
                },
                Name = "fe-lb",
                Subnet = new AzureNative.Network.Inputs.SubnetArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb",
                },
            },
        },
        InboundNatPools = new[] {},
        InboundNatRules = new[]
        {
            new AzureNative.Network.Inputs.InboundNatRuleArgs
            {
                BackendPort = 3389,
                EnableFloatingIP = true,
                FrontendIPConfiguration = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
                },
                FrontendPort = 3389,
                IdleTimeoutInMinutes = 15,
                Name = "in-nat-rule",
                Protocol = "Tcp",
            },
        },
        LoadBalancerName = "lb",
        LoadBalancingRules = new[]
        {
            new AzureNative.Network.Inputs.LoadBalancingRuleArgs
            {
                BackendAddressPool = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb",
                },
                BackendPort = 80,
                EnableFloatingIP = true,
                FrontendIPConfiguration = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
                },
                FrontendPort = 80,
                IdleTimeoutInMinutes = 15,
                LoadDistribution = "Default",
                Name = "rulelb",
                Probe = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb",
                },
                Protocol = "Tcp",
            },
        },
        Location = "eastus",
        OutboundRules = new[] {},
        Probes = new[]
        {
            new AzureNative.Network.Inputs.ProbeArgs
            {
                IntervalInSeconds = 15,
                Name = "probe-lb",
                NumberOfProbes = 2,
                Port = 80,
                ProbeThreshold = 1,
                Protocol = "Http",
                RequestPath = "healthcheck.aspx",
            },
        },
        ResourceGroupName = "rg1",
        Sku = new AzureNative.Network.Inputs.LoadBalancerSkuArgs
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
		_, err := network.NewLoadBalancer(ctx, "loadBalancer", &network.LoadBalancerArgs{
			BackendAddressPools: []network.BackendAddressPoolArgs{
				{
					Name: pulumi.String("be-lb"),
				},
			},
			FrontendIPConfigurations: []network.FrontendIPConfigurationArgs{
				{
					GatewayLoadBalancer: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb-provider"),
					},
					Name: pulumi.String("fe-lb"),
					Subnet: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb"),
					},
				},
			},
			InboundNatPools: network.InboundNatPoolArray{},
			InboundNatRules: []network.InboundNatRuleTypeArgs{
				{
					BackendPort:      pulumi.Int(3389),
					EnableFloatingIP: pulumi.Bool(true),
					FrontendIPConfiguration: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb"),
					},
					FrontendPort:         pulumi.Int(3389),
					IdleTimeoutInMinutes: pulumi.Int(15),
					Name:                 pulumi.String("in-nat-rule"),
					Protocol:             pulumi.String("Tcp"),
				},
			},
			LoadBalancerName: pulumi.String("lb"),
			LoadBalancingRules: []network.LoadBalancingRuleArgs{
				{
					BackendAddressPool: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb"),
					},
					BackendPort:      pulumi.Int(80),
					EnableFloatingIP: pulumi.Bool(true),
					FrontendIPConfiguration: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb"),
					},
					FrontendPort:         pulumi.Int(80),
					IdleTimeoutInMinutes: pulumi.Int(15),
					LoadDistribution:     pulumi.String("Default"),
					Name:                 pulumi.String("rulelb"),
					Probe: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb"),
					},
					Protocol: pulumi.String("Tcp"),
				},
			},
			Location:      pulumi.String("eastus"),
			OutboundRules: network.OutboundRuleArray{},
			Probes: []network.ProbeArgs{
				{
					IntervalInSeconds: pulumi.Int(15),
					Name:              pulumi.String("probe-lb"),
					NumberOfProbes:    pulumi.Int(2),
					Port:              pulumi.Int(80),
					ProbeThreshold:    pulumi.Int(1),
					Protocol:          pulumi.String("Http"),
					RequestPath:       pulumi.String("healthcheck.aspx"),
				},
			},
			ResourceGroupName: pulumi.String("rg1"),
			Sku: &network.LoadBalancerSkuArgs{
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
import com.pulumi.azurenative.network.LoadBalancer;
import com.pulumi.azurenative.network.LoadBalancerArgs;
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
        var loadBalancer = new LoadBalancer("loadBalancer", LoadBalancerArgs.builder()        
            .backendAddressPools(Map.of("name", "be-lb"))
            .frontendIPConfigurations(Map.ofEntries(
                Map.entry("gatewayLoadBalancer", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb-provider")),
                Map.entry("name", "fe-lb"),
                Map.entry("subnet", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb"))
            ))
            .inboundNatPools()
            .inboundNatRules(Map.ofEntries(
                Map.entry("backendPort", 3389),
                Map.entry("enableFloatingIP", true),
                Map.entry("frontendIPConfiguration", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb")),
                Map.entry("frontendPort", 3389),
                Map.entry("idleTimeoutInMinutes", 15),
                Map.entry("name", "in-nat-rule"),
                Map.entry("protocol", "Tcp")
            ))
            .loadBalancerName("lb")
            .loadBalancingRules(Map.ofEntries(
                Map.entry("backendAddressPool", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb")),
                Map.entry("backendPort", 80),
                Map.entry("enableFloatingIP", true),
                Map.entry("frontendIPConfiguration", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb")),
                Map.entry("frontendPort", 80),
                Map.entry("idleTimeoutInMinutes", 15),
                Map.entry("loadDistribution", "Default"),
                Map.entry("name", "rulelb"),
                Map.entry("probe", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb")),
                Map.entry("protocol", "Tcp")
            ))
            .location("eastus")
            .outboundRules()
            .probes(Map.ofEntries(
                Map.entry("intervalInSeconds", 15),
                Map.entry("name", "probe-lb"),
                Map.entry("numberOfProbes", 2),
                Map.entry("port", 80),
                Map.entry("probeThreshold", 1),
                Map.entry("protocol", "Http"),
                Map.entry("requestPath", "healthcheck.aspx")
            ))
            .resourceGroupName("rg1")
            .sku(Map.of("name", "Standard"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const loadBalancer = new azure_native.network.LoadBalancer("loadBalancer", {
    backendAddressPools: [{
        name: "be-lb",
    }],
    frontendIPConfigurations: [{
        gatewayLoadBalancer: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb-provider",
        },
        name: "fe-lb",
        subnet: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb",
        },
    }],
    inboundNatPools: [],
    inboundNatRules: [{
        backendPort: 3389,
        enableFloatingIP: true,
        frontendIPConfiguration: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
        },
        frontendPort: 3389,
        idleTimeoutInMinutes: 15,
        name: "in-nat-rule",
        protocol: "Tcp",
    }],
    loadBalancerName: "lb",
    loadBalancingRules: [{
        backendAddressPool: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb",
        },
        backendPort: 80,
        enableFloatingIP: true,
        frontendIPConfiguration: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
        },
        frontendPort: 80,
        idleTimeoutInMinutes: 15,
        loadDistribution: "Default",
        name: "rulelb",
        probe: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb",
        },
        protocol: "Tcp",
    }],
    location: "eastus",
    outboundRules: [],
    probes: [{
        intervalInSeconds: 15,
        name: "probe-lb",
        numberOfProbes: 2,
        port: 80,
        probeThreshold: 1,
        protocol: "Http",
        requestPath: "healthcheck.aspx",
    }],
    resourceGroupName: "rg1",
    sku: {
        name: "Standard",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

load_balancer = azure_native.network.LoadBalancer("loadBalancer",
    backend_address_pools=[azure_native.network.BackendAddressPoolArgs(
        name="be-lb",
    )],
    frontend_ip_configurations=[{
        "gatewayLoadBalancer": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb-provider",
        ),
        "name": "fe-lb",
        "subnet": azure_native.network.SubnetArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb",
        ),
    }],
    inbound_nat_pools=[],
    inbound_nat_rules=[{
        "backendPort": 3389,
        "enableFloatingIP": True,
        "frontendIPConfiguration": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
        ),
        "frontendPort": 3389,
        "idleTimeoutInMinutes": 15,
        "name": "in-nat-rule",
        "protocol": "Tcp",
    }],
    load_balancer_name="lb",
    load_balancing_rules=[{
        "backendAddressPool": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb",
        ),
        "backendPort": 80,
        "enableFloatingIP": True,
        "frontendIPConfiguration": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
        ),
        "frontendPort": 80,
        "idleTimeoutInMinutes": 15,
        "loadDistribution": "Default",
        "name": "rulelb",
        "probe": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb",
        ),
        "protocol": "Tcp",
    }],
    location="eastus",
    outbound_rules=[],
    probes=[azure_native.network.ProbeArgs(
        interval_in_seconds=15,
        name="probe-lb",
        number_of_probes=2,
        port=80,
        probe_threshold=1,
        protocol="Http",
        request_path="healthcheck.aspx",
    )],
    resource_group_name="rg1",
    sku=azure_native.network.LoadBalancerSkuArgs(
        name="Standard",
    ))

```

```yaml
resources:
  loadBalancer:
    type: azure-native:network:LoadBalancer
    properties:
      backendAddressPools:
        - name: be-lb
      frontendIPConfigurations:
        - gatewayLoadBalancer:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb-provider
          name: fe-lb
          subnet:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb
      inboundNatPools: []
      inboundNatRules:
        - backendPort: 3389
          enableFloatingIP: true
          frontendIPConfiguration:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb
          frontendPort: 3389
          idleTimeoutInMinutes: 15
          name: in-nat-rule
          protocol: Tcp
      loadBalancerName: lb
      loadBalancingRules:
        - backendAddressPool:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb
          backendPort: 80
          enableFloatingIP: true
          frontendIPConfiguration:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb
          frontendPort: 80
          idleTimeoutInMinutes: 15
          loadDistribution: Default
          name: rulelb
          probe:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb
          protocol: Tcp
      location: eastus
      outboundRules: []
      probes:
        - intervalInSeconds: 15
          name: probe-lb
          numberOfProbes: 2
          port: 80
          probeThreshold: 1
          protocol: Http
          requestPath: healthcheck.aspx
      resourceGroupName: rg1
      sku:
        name: Standard

```

{{% /example %}}
{{% example %}}
### Create load balancer with Gateway Load Balancer Provider configured with one Backend Pool
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var loadBalancer = new AzureNative.Network.LoadBalancer("loadBalancer", new()
    {
        BackendAddressPools = new[]
        {
            new AzureNative.Network.Inputs.BackendAddressPoolArgs
            {
                Name = "be-lb",
                TunnelInterfaces = new[]
                {
                    new AzureNative.Network.Inputs.GatewayLoadBalancerTunnelInterfaceArgs
                    {
                        Identifier = 900,
                        Port = 15000,
                        Protocol = "VXLAN",
                        Type = "Internal",
                    },
                    new AzureNative.Network.Inputs.GatewayLoadBalancerTunnelInterfaceArgs
                    {
                        Identifier = 901,
                        Port = 15001,
                        Protocol = "VXLAN",
                        Type = "Internal",
                    },
                },
            },
        },
        FrontendIPConfigurations = new[]
        {
            new AzureNative.Network.Inputs.FrontendIPConfigurationArgs
            {
                Name = "fe-lb",
                Subnet = new AzureNative.Network.Inputs.SubnetArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb",
                },
            },
        },
        InboundNatPools = new[] {},
        LoadBalancerName = "lb",
        LoadBalancingRules = new[]
        {
            new AzureNative.Network.Inputs.LoadBalancingRuleArgs
            {
                BackendAddressPools = new[]
                {
                    new AzureNative.Network.Inputs.SubResourceArgs
                    {
                        Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb",
                    },
                },
                BackendPort = 0,
                EnableFloatingIP = true,
                FrontendIPConfiguration = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
                },
                FrontendPort = 0,
                IdleTimeoutInMinutes = 15,
                LoadDistribution = "Default",
                Name = "rulelb",
                Probe = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb",
                },
                Protocol = "All",
            },
        },
        Location = "eastus",
        OutboundRules = new[] {},
        Probes = new[]
        {
            new AzureNative.Network.Inputs.ProbeArgs
            {
                IntervalInSeconds = 15,
                Name = "probe-lb",
                NumberOfProbes = 2,
                Port = 80,
                ProbeThreshold = 1,
                Protocol = "Http",
                RequestPath = "healthcheck.aspx",
            },
        },
        ResourceGroupName = "rg1",
        Sku = new AzureNative.Network.Inputs.LoadBalancerSkuArgs
        {
            Name = "Premium",
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
		_, err := network.NewLoadBalancer(ctx, "loadBalancer", &network.LoadBalancerArgs{
			BackendAddressPools: []network.BackendAddressPoolArgs{
				{
					Name: pulumi.String("be-lb"),
					TunnelInterfaces: network.GatewayLoadBalancerTunnelInterfaceArray{
						{
							Identifier: pulumi.Int(900),
							Port:       pulumi.Int(15000),
							Protocol:   pulumi.String("VXLAN"),
							Type:       pulumi.String("Internal"),
						},
						{
							Identifier: pulumi.Int(901),
							Port:       pulumi.Int(15001),
							Protocol:   pulumi.String("VXLAN"),
							Type:       pulumi.String("Internal"),
						},
					},
				},
			},
			FrontendIPConfigurations: []network.FrontendIPConfigurationArgs{
				{
					Name: pulumi.String("fe-lb"),
					Subnet: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb"),
					},
				},
			},
			InboundNatPools:  network.InboundNatPoolArray{},
			LoadBalancerName: pulumi.String("lb"),
			LoadBalancingRules: []network.LoadBalancingRuleArgs{
				{
					BackendAddressPools: network.SubResourceArray{
						{
							Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb"),
						},
					},
					BackendPort:      pulumi.Int(0),
					EnableFloatingIP: pulumi.Bool(true),
					FrontendIPConfiguration: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb"),
					},
					FrontendPort:         pulumi.Int(0),
					IdleTimeoutInMinutes: pulumi.Int(15),
					LoadDistribution:     pulumi.String("Default"),
					Name:                 pulumi.String("rulelb"),
					Probe: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb"),
					},
					Protocol: pulumi.String("All"),
				},
			},
			Location:      pulumi.String("eastus"),
			OutboundRules: network.OutboundRuleArray{},
			Probes: []network.ProbeArgs{
				{
					IntervalInSeconds: pulumi.Int(15),
					Name:              pulumi.String("probe-lb"),
					NumberOfProbes:    pulumi.Int(2),
					Port:              pulumi.Int(80),
					ProbeThreshold:    pulumi.Int(1),
					Protocol:          pulumi.String("Http"),
					RequestPath:       pulumi.String("healthcheck.aspx"),
				},
			},
			ResourceGroupName: pulumi.String("rg1"),
			Sku: &network.LoadBalancerSkuArgs{
				Name: pulumi.String("Premium"),
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
import com.pulumi.azurenative.network.LoadBalancer;
import com.pulumi.azurenative.network.LoadBalancerArgs;
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
        var loadBalancer = new LoadBalancer("loadBalancer", LoadBalancerArgs.builder()        
            .backendAddressPools(Map.ofEntries(
                Map.entry("name", "be-lb"),
                Map.entry("tunnelInterfaces",                 
                    Map.ofEntries(
                        Map.entry("identifier", 900),
                        Map.entry("port", 15000),
                        Map.entry("protocol", "VXLAN"),
                        Map.entry("type", "Internal")
                    ),
                    Map.ofEntries(
                        Map.entry("identifier", 901),
                        Map.entry("port", 15001),
                        Map.entry("protocol", "VXLAN"),
                        Map.entry("type", "Internal")
                    ))
            ))
            .frontendIPConfigurations(Map.ofEntries(
                Map.entry("name", "fe-lb"),
                Map.entry("subnet", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb"))
            ))
            .inboundNatPools()
            .loadBalancerName("lb")
            .loadBalancingRules(Map.ofEntries(
                Map.entry("backendAddressPools", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb")),
                Map.entry("backendPort", 0),
                Map.entry("enableFloatingIP", true),
                Map.entry("frontendIPConfiguration", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb")),
                Map.entry("frontendPort", 0),
                Map.entry("idleTimeoutInMinutes", 15),
                Map.entry("loadDistribution", "Default"),
                Map.entry("name", "rulelb"),
                Map.entry("probe", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb")),
                Map.entry("protocol", "All")
            ))
            .location("eastus")
            .outboundRules()
            .probes(Map.ofEntries(
                Map.entry("intervalInSeconds", 15),
                Map.entry("name", "probe-lb"),
                Map.entry("numberOfProbes", 2),
                Map.entry("port", 80),
                Map.entry("probeThreshold", 1),
                Map.entry("protocol", "Http"),
                Map.entry("requestPath", "healthcheck.aspx")
            ))
            .resourceGroupName("rg1")
            .sku(Map.of("name", "Premium"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const loadBalancer = new azure_native.network.LoadBalancer("loadBalancer", {
    backendAddressPools: [{
        name: "be-lb",
        tunnelInterfaces: [
            {
                identifier: 900,
                port: 15000,
                protocol: "VXLAN",
                type: "Internal",
            },
            {
                identifier: 901,
                port: 15001,
                protocol: "VXLAN",
                type: "Internal",
            },
        ],
    }],
    frontendIPConfigurations: [{
        name: "fe-lb",
        subnet: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb",
        },
    }],
    inboundNatPools: [],
    loadBalancerName: "lb",
    loadBalancingRules: [{
        backendAddressPools: [{
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb",
        }],
        backendPort: 0,
        enableFloatingIP: true,
        frontendIPConfiguration: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
        },
        frontendPort: 0,
        idleTimeoutInMinutes: 15,
        loadDistribution: "Default",
        name: "rulelb",
        probe: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb",
        },
        protocol: "All",
    }],
    location: "eastus",
    outboundRules: [],
    probes: [{
        intervalInSeconds: 15,
        name: "probe-lb",
        numberOfProbes: 2,
        port: 80,
        probeThreshold: 1,
        protocol: "Http",
        requestPath: "healthcheck.aspx",
    }],
    resourceGroupName: "rg1",
    sku: {
        name: "Premium",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

load_balancer = azure_native.network.LoadBalancer("loadBalancer",
    backend_address_pools=[{
        "name": "be-lb",
        "tunnelInterfaces": [
            azure_native.network.GatewayLoadBalancerTunnelInterfaceArgs(
                identifier=900,
                port=15000,
                protocol="VXLAN",
                type="Internal",
            ),
            azure_native.network.GatewayLoadBalancerTunnelInterfaceArgs(
                identifier=901,
                port=15001,
                protocol="VXLAN",
                type="Internal",
            ),
        ],
    }],
    frontend_ip_configurations=[{
        "name": "fe-lb",
        "subnet": azure_native.network.SubnetArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb",
        ),
    }],
    inbound_nat_pools=[],
    load_balancer_name="lb",
    load_balancing_rules=[{
        "backendAddressPools": [azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb",
        )],
        "backendPort": 0,
        "enableFloatingIP": True,
        "frontendIPConfiguration": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
        ),
        "frontendPort": 0,
        "idleTimeoutInMinutes": 15,
        "loadDistribution": "Default",
        "name": "rulelb",
        "probe": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb",
        ),
        "protocol": "All",
    }],
    location="eastus",
    outbound_rules=[],
    probes=[azure_native.network.ProbeArgs(
        interval_in_seconds=15,
        name="probe-lb",
        number_of_probes=2,
        port=80,
        probe_threshold=1,
        protocol="Http",
        request_path="healthcheck.aspx",
    )],
    resource_group_name="rg1",
    sku=azure_native.network.LoadBalancerSkuArgs(
        name="Premium",
    ))

```

```yaml
resources:
  loadBalancer:
    type: azure-native:network:LoadBalancer
    properties:
      backendAddressPools:
        - name: be-lb
          tunnelInterfaces:
            - identifier: 900
              port: 15000
              protocol: VXLAN
              type: Internal
            - identifier: 901
              port: 15001
              protocol: VXLAN
              type: Internal
      frontendIPConfigurations:
        - name: fe-lb
          subnet:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb
      inboundNatPools: []
      loadBalancerName: lb
      loadBalancingRules:
        - backendAddressPools:
            - id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb
          backendPort: 0
          enableFloatingIP: true
          frontendIPConfiguration:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb
          frontendPort: 0
          idleTimeoutInMinutes: 15
          loadDistribution: Default
          name: rulelb
          probe:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb
          protocol: All
      location: eastus
      outboundRules: []
      probes:
        - intervalInSeconds: 15
          name: probe-lb
          numberOfProbes: 2
          port: 80
          probeThreshold: 1
          protocol: Http
          requestPath: healthcheck.aspx
      resourceGroupName: rg1
      sku:
        name: Premium

```

{{% /example %}}
{{% example %}}
### Create load balancer with Gateway Load Balancer Provider configured with two Backend Pool
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var loadBalancer = new AzureNative.Network.LoadBalancer("loadBalancer", new()
    {
        BackendAddressPools = new[]
        {
            new AzureNative.Network.Inputs.BackendAddressPoolArgs
            {
                Name = "be-lb1",
            },
            new AzureNative.Network.Inputs.BackendAddressPoolArgs
            {
                Name = "be-lb2",
            },
        },
        FrontendIPConfigurations = new[]
        {
            new AzureNative.Network.Inputs.FrontendIPConfigurationArgs
            {
                Name = "fe-lb",
                Subnet = new AzureNative.Network.Inputs.SubnetArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb",
                },
            },
        },
        InboundNatPools = new[] {},
        LoadBalancerName = "lb",
        LoadBalancingRules = new[]
        {
            new AzureNative.Network.Inputs.LoadBalancingRuleArgs
            {
                BackendAddressPool = null,
                BackendAddressPools = new[]
                {
                    new AzureNative.Network.Inputs.SubResourceArgs
                    {
                        Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb1",
                    },
                    new AzureNative.Network.Inputs.SubResourceArgs
                    {
                        Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb2",
                    },
                },
                BackendPort = 0,
                EnableFloatingIP = true,
                FrontendIPConfiguration = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
                },
                FrontendPort = 0,
                IdleTimeoutInMinutes = 15,
                LoadDistribution = "Default",
                Name = "rulelb",
                Probe = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb",
                },
                Protocol = "All",
            },
        },
        Location = "eastus",
        OutboundRules = new[] {},
        Probes = new[]
        {
            new AzureNative.Network.Inputs.ProbeArgs
            {
                IntervalInSeconds = 15,
                Name = "probe-lb",
                NumberOfProbes = 2,
                Port = 80,
                ProbeThreshold = 1,
                Protocol = "Http",
                RequestPath = "healthcheck.aspx",
            },
        },
        ResourceGroupName = "rg1",
        Sku = new AzureNative.Network.Inputs.LoadBalancerSkuArgs
        {
            Name = "Premium",
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
		_, err := network.NewLoadBalancer(ctx, "loadBalancer", &network.LoadBalancerArgs{
			BackendAddressPools: []network.BackendAddressPoolArgs{
				{
					Name: pulumi.String("be-lb1"),
				},
				{
					Name: pulumi.String("be-lb2"),
				},
			},
			FrontendIPConfigurations: []network.FrontendIPConfigurationArgs{
				{
					Name: pulumi.String("fe-lb"),
					Subnet: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb"),
					},
				},
			},
			InboundNatPools:  network.InboundNatPoolArray{},
			LoadBalancerName: pulumi.String("lb"),
			LoadBalancingRules: []network.LoadBalancingRuleArgs{
				{
					BackendAddressPool: nil,
					BackendAddressPools: network.SubResourceArray{
						{
							Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb1"),
						},
						{
							Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb2"),
						},
					},
					BackendPort:      pulumi.Int(0),
					EnableFloatingIP: pulumi.Bool(true),
					FrontendIPConfiguration: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb"),
					},
					FrontendPort:         pulumi.Int(0),
					IdleTimeoutInMinutes: pulumi.Int(15),
					LoadDistribution:     pulumi.String("Default"),
					Name:                 pulumi.String("rulelb"),
					Probe: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb"),
					},
					Protocol: pulumi.String("All"),
				},
			},
			Location:      pulumi.String("eastus"),
			OutboundRules: network.OutboundRuleArray{},
			Probes: []network.ProbeArgs{
				{
					IntervalInSeconds: pulumi.Int(15),
					Name:              pulumi.String("probe-lb"),
					NumberOfProbes:    pulumi.Int(2),
					Port:              pulumi.Int(80),
					ProbeThreshold:    pulumi.Int(1),
					Protocol:          pulumi.String("Http"),
					RequestPath:       pulumi.String("healthcheck.aspx"),
				},
			},
			ResourceGroupName: pulumi.String("rg1"),
			Sku: &network.LoadBalancerSkuArgs{
				Name: pulumi.String("Premium"),
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
import com.pulumi.azurenative.network.LoadBalancer;
import com.pulumi.azurenative.network.LoadBalancerArgs;
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
        var loadBalancer = new LoadBalancer("loadBalancer", LoadBalancerArgs.builder()        
            .backendAddressPools(            
                Map.of("name", "be-lb1"),
                Map.of("name", "be-lb2"))
            .frontendIPConfigurations(Map.ofEntries(
                Map.entry("name", "fe-lb"),
                Map.entry("subnet", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb"))
            ))
            .inboundNatPools()
            .loadBalancerName("lb")
            .loadBalancingRules(Map.ofEntries(
                Map.entry("backendAddressPool", ),
                Map.entry("backendAddressPools",                 
                    Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb1"),
                    Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb2")),
                Map.entry("backendPort", 0),
                Map.entry("enableFloatingIP", true),
                Map.entry("frontendIPConfiguration", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb")),
                Map.entry("frontendPort", 0),
                Map.entry("idleTimeoutInMinutes", 15),
                Map.entry("loadDistribution", "Default"),
                Map.entry("name", "rulelb"),
                Map.entry("probe", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb")),
                Map.entry("protocol", "All")
            ))
            .location("eastus")
            .outboundRules()
            .probes(Map.ofEntries(
                Map.entry("intervalInSeconds", 15),
                Map.entry("name", "probe-lb"),
                Map.entry("numberOfProbes", 2),
                Map.entry("port", 80),
                Map.entry("probeThreshold", 1),
                Map.entry("protocol", "Http"),
                Map.entry("requestPath", "healthcheck.aspx")
            ))
            .resourceGroupName("rg1")
            .sku(Map.of("name", "Premium"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const loadBalancer = new azure_native.network.LoadBalancer("loadBalancer", {
    backendAddressPools: [
        {
            name: "be-lb1",
        },
        {
            name: "be-lb2",
        },
    ],
    frontendIPConfigurations: [{
        name: "fe-lb",
        subnet: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb",
        },
    }],
    inboundNatPools: [],
    loadBalancerName: "lb",
    loadBalancingRules: [{
        backendAddressPool: {},
        backendAddressPools: [
            {
                id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb1",
            },
            {
                id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb2",
            },
        ],
        backendPort: 0,
        enableFloatingIP: true,
        frontendIPConfiguration: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
        },
        frontendPort: 0,
        idleTimeoutInMinutes: 15,
        loadDistribution: "Default",
        name: "rulelb",
        probe: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb",
        },
        protocol: "All",
    }],
    location: "eastus",
    outboundRules: [],
    probes: [{
        intervalInSeconds: 15,
        name: "probe-lb",
        numberOfProbes: 2,
        port: 80,
        probeThreshold: 1,
        protocol: "Http",
        requestPath: "healthcheck.aspx",
    }],
    resourceGroupName: "rg1",
    sku: {
        name: "Premium",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

load_balancer = azure_native.network.LoadBalancer("loadBalancer",
    backend_address_pools=[
        azure_native.network.BackendAddressPoolArgs(
            name="be-lb1",
        ),
        azure_native.network.BackendAddressPoolArgs(
            name="be-lb2",
        ),
    ],
    frontend_ip_configurations=[{
        "name": "fe-lb",
        "subnet": azure_native.network.SubnetArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb",
        ),
    }],
    inbound_nat_pools=[],
    load_balancer_name="lb",
    load_balancing_rules=[{
        "backendAddressPool": azure_native.network.SubResourceArgs(),
        "backendAddressPools": [
            azure_native.network.SubResourceArgs(
                id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb1",
            ),
            azure_native.network.SubResourceArgs(
                id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb2",
            ),
        ],
        "backendPort": 0,
        "enableFloatingIP": True,
        "frontendIPConfiguration": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
        ),
        "frontendPort": 0,
        "idleTimeoutInMinutes": 15,
        "loadDistribution": "Default",
        "name": "rulelb",
        "probe": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb",
        ),
        "protocol": "All",
    }],
    location="eastus",
    outbound_rules=[],
    probes=[azure_native.network.ProbeArgs(
        interval_in_seconds=15,
        name="probe-lb",
        number_of_probes=2,
        port=80,
        probe_threshold=1,
        protocol="Http",
        request_path="healthcheck.aspx",
    )],
    resource_group_name="rg1",
    sku=azure_native.network.LoadBalancerSkuArgs(
        name="Premium",
    ))

```

```yaml
resources:
  loadBalancer:
    type: azure-native:network:LoadBalancer
    properties:
      backendAddressPools:
        - name: be-lb1
        - name: be-lb2
      frontendIPConfigurations:
        - name: fe-lb
          subnet:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb
      inboundNatPools: []
      loadBalancerName: lb
      loadBalancingRules:
        - backendAddressPool: {}
          backendAddressPools:
            - id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb1
            - id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb2
          backendPort: 0
          enableFloatingIP: true
          frontendIPConfiguration:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb
          frontendPort: 0
          idleTimeoutInMinutes: 15
          loadDistribution: Default
          name: rulelb
          probe:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb
          protocol: All
      location: eastus
      outboundRules: []
      probes:
        - intervalInSeconds: 15
          name: probe-lb
          numberOfProbes: 2
          port: 80
          probeThreshold: 1
          protocol: Http
          requestPath: healthcheck.aspx
      resourceGroupName: rg1
      sku:
        name: Premium

```

{{% /example %}}
{{% example %}}
### Create load balancer with Global Tier and one regional load balancer in its backend pool
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var loadBalancer = new AzureNative.Network.LoadBalancer("loadBalancer", new()
    {
        BackendAddressPools = new[]
        {
            new AzureNative.Network.Inputs.BackendAddressPoolArgs
            {
                LoadBalancerBackendAddresses = new[]
                {
                    new AzureNative.Network.Inputs.LoadBalancerBackendAddressArgs
                    {
                        LoadBalancerFrontendIPConfiguration = new AzureNative.Network.Inputs.SubResourceArgs
                        {
                            Id = "/subscriptions/subid/resourceGroups/regional-lb-rg1/providers/Microsoft.Network/loadBalancers/regional-lb/frontendIPConfigurations/fe-rlb",
                        },
                        Name = "regional-lb1-address",
                    },
                },
                Name = "be-lb",
            },
        },
        FrontendIPConfigurations = new[]
        {
            new AzureNative.Network.Inputs.FrontendIPConfigurationArgs
            {
                Name = "fe-lb",
                Subnet = new AzureNative.Network.Inputs.SubnetArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb",
                },
            },
        },
        LoadBalancerName = "lb",
        LoadBalancingRules = new[]
        {
            new AzureNative.Network.Inputs.LoadBalancingRuleArgs
            {
                BackendAddressPool = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb",
                },
                BackendPort = 80,
                EnableFloatingIP = false,
                FrontendIPConfiguration = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
                },
                FrontendPort = 80,
                IdleTimeoutInMinutes = 15,
                LoadDistribution = "Default",
                Name = "rulelb",
                Probe = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb",
                },
                Protocol = "Tcp",
            },
        },
        Location = "eastus",
        Probes = new[]
        {
            new AzureNative.Network.Inputs.ProbeArgs
            {
                IntervalInSeconds = 15,
                Name = "probe-lb",
                NumberOfProbes = 2,
                Port = 80,
                ProbeThreshold = 1,
                Protocol = "Http",
                RequestPath = "healthcheck.aspx",
            },
        },
        ResourceGroupName = "rg1",
        Sku = new AzureNative.Network.Inputs.LoadBalancerSkuArgs
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
		_, err := network.NewLoadBalancer(ctx, "loadBalancer", &network.LoadBalancerArgs{
			BackendAddressPools: []network.BackendAddressPoolArgs{
				{
					LoadBalancerBackendAddresses: network.LoadBalancerBackendAddressArray{
						{
							LoadBalancerFrontendIPConfiguration: {
								Id: pulumi.String("/subscriptions/subid/resourceGroups/regional-lb-rg1/providers/Microsoft.Network/loadBalancers/regional-lb/frontendIPConfigurations/fe-rlb"),
							},
							Name: pulumi.String("regional-lb1-address"),
						},
					},
					Name: pulumi.String("be-lb"),
				},
			},
			FrontendIPConfigurations: []network.FrontendIPConfigurationArgs{
				{
					Name: pulumi.String("fe-lb"),
					Subnet: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb"),
					},
				},
			},
			LoadBalancerName: pulumi.String("lb"),
			LoadBalancingRules: []network.LoadBalancingRuleArgs{
				{
					BackendAddressPool: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb"),
					},
					BackendPort:      pulumi.Int(80),
					EnableFloatingIP: pulumi.Bool(false),
					FrontendIPConfiguration: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb"),
					},
					FrontendPort:         pulumi.Int(80),
					IdleTimeoutInMinutes: pulumi.Int(15),
					LoadDistribution:     pulumi.String("Default"),
					Name:                 pulumi.String("rulelb"),
					Probe: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb"),
					},
					Protocol: pulumi.String("Tcp"),
				},
			},
			Location: pulumi.String("eastus"),
			Probes: []network.ProbeArgs{
				{
					IntervalInSeconds: pulumi.Int(15),
					Name:              pulumi.String("probe-lb"),
					NumberOfProbes:    pulumi.Int(2),
					Port:              pulumi.Int(80),
					ProbeThreshold:    pulumi.Int(1),
					Protocol:          pulumi.String("Http"),
					RequestPath:       pulumi.String("healthcheck.aspx"),
				},
			},
			ResourceGroupName: pulumi.String("rg1"),
			Sku: &network.LoadBalancerSkuArgs{
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
import com.pulumi.azurenative.network.LoadBalancer;
import com.pulumi.azurenative.network.LoadBalancerArgs;
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
        var loadBalancer = new LoadBalancer("loadBalancer", LoadBalancerArgs.builder()        
            .backendAddressPools(Map.ofEntries(
                Map.entry("loadBalancerBackendAddresses", Map.ofEntries(
                    Map.entry("loadBalancerFrontendIPConfiguration", Map.of("id", "/subscriptions/subid/resourceGroups/regional-lb-rg1/providers/Microsoft.Network/loadBalancers/regional-lb/frontendIPConfigurations/fe-rlb")),
                    Map.entry("name", "regional-lb1-address")
                )),
                Map.entry("name", "be-lb")
            ))
            .frontendIPConfigurations(Map.ofEntries(
                Map.entry("name", "fe-lb"),
                Map.entry("subnet", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb"))
            ))
            .loadBalancerName("lb")
            .loadBalancingRules(Map.ofEntries(
                Map.entry("backendAddressPool", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb")),
                Map.entry("backendPort", 80),
                Map.entry("enableFloatingIP", false),
                Map.entry("frontendIPConfiguration", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb")),
                Map.entry("frontendPort", 80),
                Map.entry("idleTimeoutInMinutes", 15),
                Map.entry("loadDistribution", "Default"),
                Map.entry("name", "rulelb"),
                Map.entry("probe", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb")),
                Map.entry("protocol", "Tcp")
            ))
            .location("eastus")
            .probes(Map.ofEntries(
                Map.entry("intervalInSeconds", 15),
                Map.entry("name", "probe-lb"),
                Map.entry("numberOfProbes", 2),
                Map.entry("port", 80),
                Map.entry("probeThreshold", 1),
                Map.entry("protocol", "Http"),
                Map.entry("requestPath", "healthcheck.aspx")
            ))
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

const loadBalancer = new azure_native.network.LoadBalancer("loadBalancer", {
    backendAddressPools: [{
        loadBalancerBackendAddresses: [{
            loadBalancerFrontendIPConfiguration: {
                id: "/subscriptions/subid/resourceGroups/regional-lb-rg1/providers/Microsoft.Network/loadBalancers/regional-lb/frontendIPConfigurations/fe-rlb",
            },
            name: "regional-lb1-address",
        }],
        name: "be-lb",
    }],
    frontendIPConfigurations: [{
        name: "fe-lb",
        subnet: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb",
        },
    }],
    loadBalancerName: "lb",
    loadBalancingRules: [{
        backendAddressPool: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb",
        },
        backendPort: 80,
        enableFloatingIP: false,
        frontendIPConfiguration: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
        },
        frontendPort: 80,
        idleTimeoutInMinutes: 15,
        loadDistribution: "Default",
        name: "rulelb",
        probe: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb",
        },
        protocol: "Tcp",
    }],
    location: "eastus",
    probes: [{
        intervalInSeconds: 15,
        name: "probe-lb",
        numberOfProbes: 2,
        port: 80,
        probeThreshold: 1,
        protocol: "Http",
        requestPath: "healthcheck.aspx",
    }],
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

load_balancer = azure_native.network.LoadBalancer("loadBalancer",
    backend_address_pools=[{
        "loadBalancerBackendAddresses": [{
            "loadBalancerFrontendIPConfiguration": azure_native.network.SubResourceArgs(
                id="/subscriptions/subid/resourceGroups/regional-lb-rg1/providers/Microsoft.Network/loadBalancers/regional-lb/frontendIPConfigurations/fe-rlb",
            ),
            "name": "regional-lb1-address",
        }],
        "name": "be-lb",
    }],
    frontend_ip_configurations=[{
        "name": "fe-lb",
        "subnet": azure_native.network.SubnetArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb",
        ),
    }],
    load_balancer_name="lb",
    load_balancing_rules=[{
        "backendAddressPool": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb",
        ),
        "backendPort": 80,
        "enableFloatingIP": False,
        "frontendIPConfiguration": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
        ),
        "frontendPort": 80,
        "idleTimeoutInMinutes": 15,
        "loadDistribution": "Default",
        "name": "rulelb",
        "probe": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb",
        ),
        "protocol": "Tcp",
    }],
    location="eastus",
    probes=[azure_native.network.ProbeArgs(
        interval_in_seconds=15,
        name="probe-lb",
        number_of_probes=2,
        port=80,
        probe_threshold=1,
        protocol="Http",
        request_path="healthcheck.aspx",
    )],
    resource_group_name="rg1",
    sku=azure_native.network.LoadBalancerSkuArgs(
        name="Standard",
        tier="Global",
    ))

```

```yaml
resources:
  loadBalancer:
    type: azure-native:network:LoadBalancer
    properties:
      backendAddressPools:
        - loadBalancerBackendAddresses:
            - loadBalancerFrontendIPConfiguration:
                id: /subscriptions/subid/resourceGroups/regional-lb-rg1/providers/Microsoft.Network/loadBalancers/regional-lb/frontendIPConfigurations/fe-rlb
              name: regional-lb1-address
          name: be-lb
      frontendIPConfigurations:
        - name: fe-lb
          subnet:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb
      loadBalancerName: lb
      loadBalancingRules:
        - backendAddressPool:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb
          backendPort: 80
          enableFloatingIP: false
          frontendIPConfiguration:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb
          frontendPort: 80
          idleTimeoutInMinutes: 15
          loadDistribution: Default
          name: rulelb
          probe:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb
          protocol: Tcp
      location: eastus
      probes:
        - intervalInSeconds: 15
          name: probe-lb
          numberOfProbes: 2
          port: 80
          probeThreshold: 1
          protocol: Http
          requestPath: healthcheck.aspx
      resourceGroupName: rg1
      sku:
        name: Standard
        tier: Global

```

{{% /example %}}
{{% example %}}
### Create load balancer with Standard SKU
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var loadBalancer = new AzureNative.Network.LoadBalancer("loadBalancer", new()
    {
        BackendAddressPools = new[]
        {
            new AzureNative.Network.Inputs.BackendAddressPoolArgs
            {
                Name = "be-lb",
            },
        },
        FrontendIPConfigurations = new[]
        {
            new AzureNative.Network.Inputs.FrontendIPConfigurationArgs
            {
                Name = "fe-lb",
                Subnet = new AzureNative.Network.Inputs.SubnetArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb",
                },
            },
        },
        InboundNatPools = new[] {},
        InboundNatRules = new[]
        {
            new AzureNative.Network.Inputs.InboundNatRuleArgs
            {
                BackendPort = 3389,
                EnableFloatingIP = true,
                FrontendIPConfiguration = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
                },
                FrontendPort = 3389,
                IdleTimeoutInMinutes = 15,
                Name = "in-nat-rule",
                Protocol = "Tcp",
            },
        },
        LoadBalancerName = "lb",
        LoadBalancingRules = new[]
        {
            new AzureNative.Network.Inputs.LoadBalancingRuleArgs
            {
                BackendAddressPool = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb",
                },
                BackendPort = 80,
                EnableFloatingIP = true,
                FrontendIPConfiguration = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
                },
                FrontendPort = 80,
                IdleTimeoutInMinutes = 15,
                LoadDistribution = "Default",
                Name = "rulelb",
                Probe = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb",
                },
                Protocol = "Tcp",
            },
        },
        Location = "eastus",
        OutboundRules = new[] {},
        Probes = new[]
        {
            new AzureNative.Network.Inputs.ProbeArgs
            {
                IntervalInSeconds = 15,
                Name = "probe-lb",
                NumberOfProbes = 2,
                Port = 80,
                ProbeThreshold = 1,
                Protocol = "Http",
                RequestPath = "healthcheck.aspx",
            },
        },
        ResourceGroupName = "rg1",
        Sku = new AzureNative.Network.Inputs.LoadBalancerSkuArgs
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
		_, err := network.NewLoadBalancer(ctx, "loadBalancer", &network.LoadBalancerArgs{
			BackendAddressPools: []network.BackendAddressPoolArgs{
				{
					Name: pulumi.String("be-lb"),
				},
			},
			FrontendIPConfigurations: []network.FrontendIPConfigurationArgs{
				{
					Name: pulumi.String("fe-lb"),
					Subnet: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb"),
					},
				},
			},
			InboundNatPools: network.InboundNatPoolArray{},
			InboundNatRules: []network.InboundNatRuleTypeArgs{
				{
					BackendPort:      pulumi.Int(3389),
					EnableFloatingIP: pulumi.Bool(true),
					FrontendIPConfiguration: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb"),
					},
					FrontendPort:         pulumi.Int(3389),
					IdleTimeoutInMinutes: pulumi.Int(15),
					Name:                 pulumi.String("in-nat-rule"),
					Protocol:             pulumi.String("Tcp"),
				},
			},
			LoadBalancerName: pulumi.String("lb"),
			LoadBalancingRules: []network.LoadBalancingRuleArgs{
				{
					BackendAddressPool: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb"),
					},
					BackendPort:      pulumi.Int(80),
					EnableFloatingIP: pulumi.Bool(true),
					FrontendIPConfiguration: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb"),
					},
					FrontendPort:         pulumi.Int(80),
					IdleTimeoutInMinutes: pulumi.Int(15),
					LoadDistribution:     pulumi.String("Default"),
					Name:                 pulumi.String("rulelb"),
					Probe: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb"),
					},
					Protocol: pulumi.String("Tcp"),
				},
			},
			Location:      pulumi.String("eastus"),
			OutboundRules: network.OutboundRuleArray{},
			Probes: []network.ProbeArgs{
				{
					IntervalInSeconds: pulumi.Int(15),
					Name:              pulumi.String("probe-lb"),
					NumberOfProbes:    pulumi.Int(2),
					Port:              pulumi.Int(80),
					ProbeThreshold:    pulumi.Int(1),
					Protocol:          pulumi.String("Http"),
					RequestPath:       pulumi.String("healthcheck.aspx"),
				},
			},
			ResourceGroupName: pulumi.String("rg1"),
			Sku: &network.LoadBalancerSkuArgs{
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
import com.pulumi.azurenative.network.LoadBalancer;
import com.pulumi.azurenative.network.LoadBalancerArgs;
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
        var loadBalancer = new LoadBalancer("loadBalancer", LoadBalancerArgs.builder()        
            .backendAddressPools(Map.of("name", "be-lb"))
            .frontendIPConfigurations(Map.ofEntries(
                Map.entry("name", "fe-lb"),
                Map.entry("subnet", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb"))
            ))
            .inboundNatPools()
            .inboundNatRules(Map.ofEntries(
                Map.entry("backendPort", 3389),
                Map.entry("enableFloatingIP", true),
                Map.entry("frontendIPConfiguration", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb")),
                Map.entry("frontendPort", 3389),
                Map.entry("idleTimeoutInMinutes", 15),
                Map.entry("name", "in-nat-rule"),
                Map.entry("protocol", "Tcp")
            ))
            .loadBalancerName("lb")
            .loadBalancingRules(Map.ofEntries(
                Map.entry("backendAddressPool", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb")),
                Map.entry("backendPort", 80),
                Map.entry("enableFloatingIP", true),
                Map.entry("frontendIPConfiguration", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb")),
                Map.entry("frontendPort", 80),
                Map.entry("idleTimeoutInMinutes", 15),
                Map.entry("loadDistribution", "Default"),
                Map.entry("name", "rulelb"),
                Map.entry("probe", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb")),
                Map.entry("protocol", "Tcp")
            ))
            .location("eastus")
            .outboundRules()
            .probes(Map.ofEntries(
                Map.entry("intervalInSeconds", 15),
                Map.entry("name", "probe-lb"),
                Map.entry("numberOfProbes", 2),
                Map.entry("port", 80),
                Map.entry("probeThreshold", 1),
                Map.entry("protocol", "Http"),
                Map.entry("requestPath", "healthcheck.aspx")
            ))
            .resourceGroupName("rg1")
            .sku(Map.of("name", "Standard"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const loadBalancer = new azure_native.network.LoadBalancer("loadBalancer", {
    backendAddressPools: [{
        name: "be-lb",
    }],
    frontendIPConfigurations: [{
        name: "fe-lb",
        subnet: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb",
        },
    }],
    inboundNatPools: [],
    inboundNatRules: [{
        backendPort: 3389,
        enableFloatingIP: true,
        frontendIPConfiguration: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
        },
        frontendPort: 3389,
        idleTimeoutInMinutes: 15,
        name: "in-nat-rule",
        protocol: "Tcp",
    }],
    loadBalancerName: "lb",
    loadBalancingRules: [{
        backendAddressPool: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb",
        },
        backendPort: 80,
        enableFloatingIP: true,
        frontendIPConfiguration: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
        },
        frontendPort: 80,
        idleTimeoutInMinutes: 15,
        loadDistribution: "Default",
        name: "rulelb",
        probe: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb",
        },
        protocol: "Tcp",
    }],
    location: "eastus",
    outboundRules: [],
    probes: [{
        intervalInSeconds: 15,
        name: "probe-lb",
        numberOfProbes: 2,
        port: 80,
        probeThreshold: 1,
        protocol: "Http",
        requestPath: "healthcheck.aspx",
    }],
    resourceGroupName: "rg1",
    sku: {
        name: "Standard",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

load_balancer = azure_native.network.LoadBalancer("loadBalancer",
    backend_address_pools=[azure_native.network.BackendAddressPoolArgs(
        name="be-lb",
    )],
    frontend_ip_configurations=[{
        "name": "fe-lb",
        "subnet": azure_native.network.SubnetArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb",
        ),
    }],
    inbound_nat_pools=[],
    inbound_nat_rules=[{
        "backendPort": 3389,
        "enableFloatingIP": True,
        "frontendIPConfiguration": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
        ),
        "frontendPort": 3389,
        "idleTimeoutInMinutes": 15,
        "name": "in-nat-rule",
        "protocol": "Tcp",
    }],
    load_balancer_name="lb",
    load_balancing_rules=[{
        "backendAddressPool": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb",
        ),
        "backendPort": 80,
        "enableFloatingIP": True,
        "frontendIPConfiguration": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
        ),
        "frontendPort": 80,
        "idleTimeoutInMinutes": 15,
        "loadDistribution": "Default",
        "name": "rulelb",
        "probe": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb",
        ),
        "protocol": "Tcp",
    }],
    location="eastus",
    outbound_rules=[],
    probes=[azure_native.network.ProbeArgs(
        interval_in_seconds=15,
        name="probe-lb",
        number_of_probes=2,
        port=80,
        probe_threshold=1,
        protocol="Http",
        request_path="healthcheck.aspx",
    )],
    resource_group_name="rg1",
    sku=azure_native.network.LoadBalancerSkuArgs(
        name="Standard",
    ))

```

```yaml
resources:
  loadBalancer:
    type: azure-native:network:LoadBalancer
    properties:
      backendAddressPools:
        - name: be-lb
      frontendIPConfigurations:
        - name: fe-lb
          subnet:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/vnetlb/subnets/subnetlb
      inboundNatPools: []
      inboundNatRules:
        - backendPort: 3389
          enableFloatingIP: true
          frontendIPConfiguration:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb
          frontendPort: 3389
          idleTimeoutInMinutes: 15
          name: in-nat-rule
          protocol: Tcp
      loadBalancerName: lb
      loadBalancingRules:
        - backendAddressPool:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb
          backendPort: 80
          enableFloatingIP: true
          frontendIPConfiguration:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb
          frontendPort: 80
          idleTimeoutInMinutes: 15
          loadDistribution: Default
          name: rulelb
          probe:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb
          protocol: Tcp
      location: eastus
      outboundRules: []
      probes:
        - intervalInSeconds: 15
          name: probe-lb
          numberOfProbes: 2
          port: 80
          probeThreshold: 1
          protocol: Http
          requestPath: healthcheck.aspx
      resourceGroupName: rg1
      sku:
        name: Standard

```

{{% /example %}}
{{% example %}}
### Create load balancer with inbound nat pool
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var loadBalancer = new AzureNative.Network.LoadBalancer("loadBalancer", new()
    {
        BackendAddressPools = new[] {},
        FrontendIPConfigurations = new[]
        {
            new AzureNative.Network.Inputs.FrontendIPConfigurationArgs
            {
                Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/test",
                Name = "test",
                PrivateIPAllocationMethod = "Dynamic",
                Subnet = new AzureNative.Network.Inputs.SubnetArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/lbvnet/subnets/lbsubnet",
                },
                Zones = new[] {},
            },
        },
        InboundNatPools = new[]
        {
            new AzureNative.Network.Inputs.InboundNatPoolArgs
            {
                BackendPort = 8888,
                EnableFloatingIP = true,
                EnableTcpReset = true,
                FrontendIPConfiguration = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/test",
                },
                FrontendPortRangeEnd = 8085,
                FrontendPortRangeStart = 8080,
                Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/inboundNatPools/test",
                IdleTimeoutInMinutes = 10,
                Name = "test",
                Protocol = "Tcp",
            },
        },
        InboundNatRules = new[] {},
        LoadBalancerName = "lb",
        LoadBalancingRules = new[] {},
        Location = "eastus",
        OutboundRules = new[] {},
        Probes = new[] {},
        ResourceGroupName = "rg1",
        Sku = new AzureNative.Network.Inputs.LoadBalancerSkuArgs
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
		_, err := network.NewLoadBalancer(ctx, "loadBalancer", &network.LoadBalancerArgs{
			BackendAddressPools: network.BackendAddressPoolArray{},
			FrontendIPConfigurations: []network.FrontendIPConfigurationArgs{
				{
					Id:                        pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/test"),
					Name:                      pulumi.String("test"),
					PrivateIPAllocationMethod: pulumi.String("Dynamic"),
					Subnet: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/lbvnet/subnets/lbsubnet"),
					},
					Zones: pulumi.StringArray{},
				},
			},
			InboundNatPools: []network.InboundNatPoolArgs{
				{
					BackendPort:      pulumi.Int(8888),
					EnableFloatingIP: pulumi.Bool(true),
					EnableTcpReset:   pulumi.Bool(true),
					FrontendIPConfiguration: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/test"),
					},
					FrontendPortRangeEnd:   pulumi.Int(8085),
					FrontendPortRangeStart: pulumi.Int(8080),
					Id:                     pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/inboundNatPools/test"),
					IdleTimeoutInMinutes:   pulumi.Int(10),
					Name:                   pulumi.String("test"),
					Protocol:               pulumi.String("Tcp"),
				},
			},
			InboundNatRules:    network.InboundNatRuleTypeArray{},
			LoadBalancerName:   pulumi.String("lb"),
			LoadBalancingRules: network.LoadBalancingRuleArray{},
			Location:           pulumi.String("eastus"),
			OutboundRules:      network.OutboundRuleArray{},
			Probes:             network.ProbeArray{},
			ResourceGroupName:  pulumi.String("rg1"),
			Sku: &network.LoadBalancerSkuArgs{
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
import com.pulumi.azurenative.network.LoadBalancer;
import com.pulumi.azurenative.network.LoadBalancerArgs;
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
        var loadBalancer = new LoadBalancer("loadBalancer", LoadBalancerArgs.builder()        
            .backendAddressPools()
            .frontendIPConfigurations(Map.ofEntries(
                Map.entry("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/test"),
                Map.entry("name", "test"),
                Map.entry("privateIPAllocationMethod", "Dynamic"),
                Map.entry("subnet", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/lbvnet/subnets/lbsubnet")),
                Map.entry("zones", )
            ))
            .inboundNatPools(Map.ofEntries(
                Map.entry("backendPort", 8888),
                Map.entry("enableFloatingIP", true),
                Map.entry("enableTcpReset", true),
                Map.entry("frontendIPConfiguration", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/test")),
                Map.entry("frontendPortRangeEnd", 8085),
                Map.entry("frontendPortRangeStart", 8080),
                Map.entry("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/inboundNatPools/test"),
                Map.entry("idleTimeoutInMinutes", 10),
                Map.entry("name", "test"),
                Map.entry("protocol", "Tcp")
            ))
            .inboundNatRules()
            .loadBalancerName("lb")
            .loadBalancingRules()
            .location("eastus")
            .outboundRules()
            .probes()
            .resourceGroupName("rg1")
            .sku(Map.of("name", "Standard"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const loadBalancer = new azure_native.network.LoadBalancer("loadBalancer", {
    backendAddressPools: [],
    frontendIPConfigurations: [{
        id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/test",
        name: "test",
        privateIPAllocationMethod: "Dynamic",
        subnet: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/lbvnet/subnets/lbsubnet",
        },
        zones: [],
    }],
    inboundNatPools: [{
        backendPort: 8888,
        enableFloatingIP: true,
        enableTcpReset: true,
        frontendIPConfiguration: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/test",
        },
        frontendPortRangeEnd: 8085,
        frontendPortRangeStart: 8080,
        id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/inboundNatPools/test",
        idleTimeoutInMinutes: 10,
        name: "test",
        protocol: "Tcp",
    }],
    inboundNatRules: [],
    loadBalancerName: "lb",
    loadBalancingRules: [],
    location: "eastus",
    outboundRules: [],
    probes: [],
    resourceGroupName: "rg1",
    sku: {
        name: "Standard",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

load_balancer = azure_native.network.LoadBalancer("loadBalancer",
    backend_address_pools=[],
    frontend_ip_configurations=[{
        "id": "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/test",
        "name": "test",
        "privateIPAllocationMethod": "Dynamic",
        "subnet": azure_native.network.SubnetArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/lbvnet/subnets/lbsubnet",
        ),
        "zones": [],
    }],
    inbound_nat_pools=[{
        "backendPort": 8888,
        "enableFloatingIP": True,
        "enableTcpReset": True,
        "frontendIPConfiguration": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/test",
        ),
        "frontendPortRangeEnd": 8085,
        "frontendPortRangeStart": 8080,
        "id": "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/inboundNatPools/test",
        "idleTimeoutInMinutes": 10,
        "name": "test",
        "protocol": "Tcp",
    }],
    inbound_nat_rules=[],
    load_balancer_name="lb",
    load_balancing_rules=[],
    location="eastus",
    outbound_rules=[],
    probes=[],
    resource_group_name="rg1",
    sku=azure_native.network.LoadBalancerSkuArgs(
        name="Standard",
    ))

```

```yaml
resources:
  loadBalancer:
    type: azure-native:network:LoadBalancer
    properties:
      backendAddressPools: []
      frontendIPConfigurations:
        - id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/test
          name: test
          privateIPAllocationMethod: Dynamic
          subnet:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/lbvnet/subnets/lbsubnet
          zones: []
      inboundNatPools:
        - backendPort: 8888
          enableFloatingIP: true
          enableTcpReset: true
          frontendIPConfiguration:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/test
          frontendPortRangeEnd: 8085
          frontendPortRangeStart: 8080
          id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/inboundNatPools/test
          idleTimeoutInMinutes: 10
          name: test
          protocol: Tcp
      inboundNatRules: []
      loadBalancerName: lb
      loadBalancingRules: []
      location: eastus
      outboundRules: []
      probes: []
      resourceGroupName: rg1
      sku:
        name: Standard

```

{{% /example %}}
{{% example %}}
### Create load balancer with outbound rules
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var loadBalancer = new AzureNative.Network.LoadBalancer("loadBalancer", new()
    {
        BackendAddressPools = new[]
        {
            new AzureNative.Network.Inputs.BackendAddressPoolArgs
            {
                Name = "be-lb",
            },
        },
        FrontendIPConfigurations = new[]
        {
            new AzureNative.Network.Inputs.FrontendIPConfigurationArgs
            {
                Name = "fe-lb",
                PublicIPAddress = new AzureNative.Network.Inputs.PublicIPAddressArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pip",
                },
            },
        },
        InboundNatPools = new[] {},
        InboundNatRules = new[]
        {
            new AzureNative.Network.Inputs.InboundNatRuleArgs
            {
                BackendPort = 3389,
                EnableFloatingIP = true,
                FrontendIPConfiguration = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
                },
                FrontendPort = 3389,
                IdleTimeoutInMinutes = 15,
                Name = "in-nat-rule",
                Protocol = "Tcp",
            },
        },
        LoadBalancerName = "lb",
        LoadBalancingRules = new[]
        {
            new AzureNative.Network.Inputs.LoadBalancingRuleArgs
            {
                BackendAddressPool = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb",
                },
                BackendPort = 80,
                DisableOutboundSnat = true,
                EnableFloatingIP = true,
                FrontendIPConfiguration = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
                },
                FrontendPort = 80,
                IdleTimeoutInMinutes = 15,
                LoadDistribution = "Default",
                Name = "rulelb",
                Probe = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb",
                },
                Protocol = "Tcp",
            },
        },
        Location = "eastus",
        OutboundRules = new[]
        {
            new AzureNative.Network.Inputs.OutboundRuleArgs
            {
                BackendAddressPool = new AzureNative.Network.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb",
                },
                FrontendIPConfigurations = new[]
                {
                    new AzureNative.Network.Inputs.SubResourceArgs
                    {
                        Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
                    },
                },
                Name = "rule1",
                Protocol = "All",
            },
        },
        Probes = new[]
        {
            new AzureNative.Network.Inputs.ProbeArgs
            {
                IntervalInSeconds = 15,
                Name = "probe-lb",
                NumberOfProbes = 2,
                Port = 80,
                ProbeThreshold = 1,
                Protocol = "Http",
                RequestPath = "healthcheck.aspx",
            },
        },
        ResourceGroupName = "rg1",
        Sku = new AzureNative.Network.Inputs.LoadBalancerSkuArgs
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
		_, err := network.NewLoadBalancer(ctx, "loadBalancer", &network.LoadBalancerArgs{
			BackendAddressPools: []network.BackendAddressPoolArgs{
				{
					Name: pulumi.String("be-lb"),
				},
			},
			FrontendIPConfigurations: []network.FrontendIPConfigurationArgs{
				{
					Name: pulumi.String("fe-lb"),
					PublicIPAddress: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pip"),
					},
				},
			},
			InboundNatPools: network.InboundNatPoolArray{},
			InboundNatRules: []network.InboundNatRuleTypeArgs{
				{
					BackendPort:      pulumi.Int(3389),
					EnableFloatingIP: pulumi.Bool(true),
					FrontendIPConfiguration: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb"),
					},
					FrontendPort:         pulumi.Int(3389),
					IdleTimeoutInMinutes: pulumi.Int(15),
					Name:                 pulumi.String("in-nat-rule"),
					Protocol:             pulumi.String("Tcp"),
				},
			},
			LoadBalancerName: pulumi.String("lb"),
			LoadBalancingRules: []network.LoadBalancingRuleArgs{
				{
					BackendAddressPool: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb"),
					},
					BackendPort:         pulumi.Int(80),
					DisableOutboundSnat: pulumi.Bool(true),
					EnableFloatingIP:    pulumi.Bool(true),
					FrontendIPConfiguration: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb"),
					},
					FrontendPort:         pulumi.Int(80),
					IdleTimeoutInMinutes: pulumi.Int(15),
					LoadDistribution:     pulumi.String("Default"),
					Name:                 pulumi.String("rulelb"),
					Probe: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb"),
					},
					Protocol: pulumi.String("Tcp"),
				},
			},
			Location: pulumi.String("eastus"),
			OutboundRules: []network.OutboundRuleArgs{
				{
					BackendAddressPool: {
						Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb"),
					},
					FrontendIPConfigurations: network.SubResourceArray{
						{
							Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb"),
						},
					},
					Name:     pulumi.String("rule1"),
					Protocol: pulumi.String("All"),
				},
			},
			Probes: []network.ProbeArgs{
				{
					IntervalInSeconds: pulumi.Int(15),
					Name:              pulumi.String("probe-lb"),
					NumberOfProbes:    pulumi.Int(2),
					Port:              pulumi.Int(80),
					ProbeThreshold:    pulumi.Int(1),
					Protocol:          pulumi.String("Http"),
					RequestPath:       pulumi.String("healthcheck.aspx"),
				},
			},
			ResourceGroupName: pulumi.String("rg1"),
			Sku: &network.LoadBalancerSkuArgs{
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
import com.pulumi.azurenative.network.LoadBalancer;
import com.pulumi.azurenative.network.LoadBalancerArgs;
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
        var loadBalancer = new LoadBalancer("loadBalancer", LoadBalancerArgs.builder()        
            .backendAddressPools(Map.of("name", "be-lb"))
            .frontendIPConfigurations(Map.ofEntries(
                Map.entry("name", "fe-lb"),
                Map.entry("publicIPAddress", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pip"))
            ))
            .inboundNatPools()
            .inboundNatRules(Map.ofEntries(
                Map.entry("backendPort", 3389),
                Map.entry("enableFloatingIP", true),
                Map.entry("frontendIPConfiguration", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb")),
                Map.entry("frontendPort", 3389),
                Map.entry("idleTimeoutInMinutes", 15),
                Map.entry("name", "in-nat-rule"),
                Map.entry("protocol", "Tcp")
            ))
            .loadBalancerName("lb")
            .loadBalancingRules(Map.ofEntries(
                Map.entry("backendAddressPool", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb")),
                Map.entry("backendPort", 80),
                Map.entry("disableOutboundSnat", true),
                Map.entry("enableFloatingIP", true),
                Map.entry("frontendIPConfiguration", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb")),
                Map.entry("frontendPort", 80),
                Map.entry("idleTimeoutInMinutes", 15),
                Map.entry("loadDistribution", "Default"),
                Map.entry("name", "rulelb"),
                Map.entry("probe", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb")),
                Map.entry("protocol", "Tcp")
            ))
            .location("eastus")
            .outboundRules(Map.ofEntries(
                Map.entry("backendAddressPool", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb")),
                Map.entry("frontendIPConfigurations", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb")),
                Map.entry("name", "rule1"),
                Map.entry("protocol", "All")
            ))
            .probes(Map.ofEntries(
                Map.entry("intervalInSeconds", 15),
                Map.entry("name", "probe-lb"),
                Map.entry("numberOfProbes", 2),
                Map.entry("port", 80),
                Map.entry("probeThreshold", 1),
                Map.entry("protocol", "Http"),
                Map.entry("requestPath", "healthcheck.aspx")
            ))
            .resourceGroupName("rg1")
            .sku(Map.of("name", "Standard"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const loadBalancer = new azure_native.network.LoadBalancer("loadBalancer", {
    backendAddressPools: [{
        name: "be-lb",
    }],
    frontendIPConfigurations: [{
        name: "fe-lb",
        publicIPAddress: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pip",
        },
    }],
    inboundNatPools: [],
    inboundNatRules: [{
        backendPort: 3389,
        enableFloatingIP: true,
        frontendIPConfiguration: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
        },
        frontendPort: 3389,
        idleTimeoutInMinutes: 15,
        name: "in-nat-rule",
        protocol: "Tcp",
    }],
    loadBalancerName: "lb",
    loadBalancingRules: [{
        backendAddressPool: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb",
        },
        backendPort: 80,
        disableOutboundSnat: true,
        enableFloatingIP: true,
        frontendIPConfiguration: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
        },
        frontendPort: 80,
        idleTimeoutInMinutes: 15,
        loadDistribution: "Default",
        name: "rulelb",
        probe: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb",
        },
        protocol: "Tcp",
    }],
    location: "eastus",
    outboundRules: [{
        backendAddressPool: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb",
        },
        frontendIPConfigurations: [{
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
        }],
        name: "rule1",
        protocol: "All",
    }],
    probes: [{
        intervalInSeconds: 15,
        name: "probe-lb",
        numberOfProbes: 2,
        port: 80,
        probeThreshold: 1,
        protocol: "Http",
        requestPath: "healthcheck.aspx",
    }],
    resourceGroupName: "rg1",
    sku: {
        name: "Standard",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

load_balancer = azure_native.network.LoadBalancer("loadBalancer",
    backend_address_pools=[azure_native.network.BackendAddressPoolArgs(
        name="be-lb",
    )],
    frontend_ip_configurations=[azure_native.network.FrontendIPConfigurationArgs(
        name="fe-lb",
        public_ip_address=azure_native.network.PublicIPAddressArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pip",
        ),
    )],
    inbound_nat_pools=[],
    inbound_nat_rules=[{
        "backendPort": 3389,
        "enableFloatingIP": True,
        "frontendIPConfiguration": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
        ),
        "frontendPort": 3389,
        "idleTimeoutInMinutes": 15,
        "name": "in-nat-rule",
        "protocol": "Tcp",
    }],
    load_balancer_name="lb",
    load_balancing_rules=[{
        "backendAddressPool": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb",
        ),
        "backendPort": 80,
        "disableOutboundSnat": True,
        "enableFloatingIP": True,
        "frontendIPConfiguration": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
        ),
        "frontendPort": 80,
        "idleTimeoutInMinutes": 15,
        "loadDistribution": "Default",
        "name": "rulelb",
        "probe": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb",
        ),
        "protocol": "Tcp",
    }],
    location="eastus",
    outbound_rules=[{
        "backendAddressPool": azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb",
        ),
        "frontendIPConfigurations": [azure_native.network.SubResourceArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb",
        )],
        "name": "rule1",
        "protocol": "All",
    }],
    probes=[azure_native.network.ProbeArgs(
        interval_in_seconds=15,
        name="probe-lb",
        number_of_probes=2,
        port=80,
        probe_threshold=1,
        protocol="Http",
        request_path="healthcheck.aspx",
    )],
    resource_group_name="rg1",
    sku=azure_native.network.LoadBalancerSkuArgs(
        name="Standard",
    ))

```

```yaml
resources:
  loadBalancer:
    type: azure-native:network:LoadBalancer
    properties:
      backendAddressPools:
        - name: be-lb
      frontendIPConfigurations:
        - name: fe-lb
          publicIPAddress:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/publicIPAddresses/pip
      inboundNatPools: []
      inboundNatRules:
        - backendPort: 3389
          enableFloatingIP: true
          frontendIPConfiguration:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb
          frontendPort: 3389
          idleTimeoutInMinutes: 15
          name: in-nat-rule
          protocol: Tcp
      loadBalancerName: lb
      loadBalancingRules:
        - backendAddressPool:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb
          backendPort: 80
          disableOutboundSnat: true
          enableFloatingIP: true
          frontendIPConfiguration:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb
          frontendPort: 80
          idleTimeoutInMinutes: 15
          loadDistribution: Default
          name: rulelb
          probe:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/probes/probe-lb
          protocol: Tcp
      location: eastus
      outboundRules:
        - backendAddressPool:
            id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/backendAddressPools/be-lb
          frontendIPConfigurations:
            - id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb/frontendIPConfigurations/fe-lb
          name: rule1
          protocol: All
      probes:
        - intervalInSeconds: 15
          name: probe-lb
          numberOfProbes: 2
          port: 80
          probeThreshold: 1
          protocol: Http
          requestPath: healthcheck.aspx
      resourceGroupName: rg1
      sku:
        name: Standard

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:LoadBalancer lb /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/loadBalancers/lb 
```
