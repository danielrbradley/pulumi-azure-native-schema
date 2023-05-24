Virtual Network resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create virtual network
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualNetwork = new AzureNative.Network.VirtualNetwork("virtualNetwork", new()
    {
        AddressSpace = new AzureNative.Network.Inputs.AddressSpaceArgs
        {
            AddressPrefixes = new[]
            {
                "10.0.0.0/16",
            },
        },
        FlowTimeoutInMinutes = 10,
        Location = "eastus",
        ResourceGroupName = "rg1",
        VirtualNetworkName = "test-vnet",
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
		_, err := network.NewVirtualNetwork(ctx, "virtualNetwork", &network.VirtualNetworkArgs{
			AddressSpace: &network.AddressSpaceArgs{
				AddressPrefixes: pulumi.StringArray{
					pulumi.String("10.0.0.0/16"),
				},
			},
			FlowTimeoutInMinutes: pulumi.Int(10),
			Location:             pulumi.String("eastus"),
			ResourceGroupName:    pulumi.String("rg1"),
			VirtualNetworkName:   pulumi.String("test-vnet"),
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
import com.pulumi.azurenative.network.VirtualNetwork;
import com.pulumi.azurenative.network.VirtualNetworkArgs;
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
        var virtualNetwork = new VirtualNetwork("virtualNetwork", VirtualNetworkArgs.builder()        
            .addressSpace(Map.of("addressPrefixes", "10.0.0.0/16"))
            .flowTimeoutInMinutes(10)
            .location("eastus")
            .resourceGroupName("rg1")
            .virtualNetworkName("test-vnet")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualNetwork = new azure_native.network.VirtualNetwork("virtualNetwork", {
    addressSpace: {
        addressPrefixes: ["10.0.0.0/16"],
    },
    flowTimeoutInMinutes: 10,
    location: "eastus",
    resourceGroupName: "rg1",
    virtualNetworkName: "test-vnet",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_network = azure_native.network.VirtualNetwork("virtualNetwork",
    address_space=azure_native.network.AddressSpaceArgs(
        address_prefixes=["10.0.0.0/16"],
    ),
    flow_timeout_in_minutes=10,
    location="eastus",
    resource_group_name="rg1",
    virtual_network_name="test-vnet")

```

```yaml
resources:
  virtualNetwork:
    type: azure-native:network:VirtualNetwork
    properties:
      addressSpace:
        addressPrefixes:
          - 10.0.0.0/16
      flowTimeoutInMinutes: 10
      location: eastus
      resourceGroupName: rg1
      virtualNetworkName: test-vnet

```

{{% /example %}}
{{% example %}}
### Create virtual network with Bgp Communities
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualNetwork = new AzureNative.Network.VirtualNetwork("virtualNetwork", new()
    {
        AddressSpace = new AzureNative.Network.Inputs.AddressSpaceArgs
        {
            AddressPrefixes = new[]
            {
                "10.0.0.0/16",
            },
        },
        BgpCommunities = new AzureNative.Network.Inputs.VirtualNetworkBgpCommunitiesArgs
        {
            VirtualNetworkCommunity = "12076:20000",
        },
        Location = "eastus",
        ResourceGroupName = "rg1",
        Subnets = new[]
        {
            new AzureNative.Network.Inputs.SubnetArgs
            {
                AddressPrefix = "10.0.0.0/24",
                Name = "test-1",
            },
        },
        VirtualNetworkName = "test-vnet",
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
		_, err := network.NewVirtualNetwork(ctx, "virtualNetwork", &network.VirtualNetworkArgs{
			AddressSpace: &network.AddressSpaceArgs{
				AddressPrefixes: pulumi.StringArray{
					pulumi.String("10.0.0.0/16"),
				},
			},
			BgpCommunities: &network.VirtualNetworkBgpCommunitiesArgs{
				VirtualNetworkCommunity: pulumi.String("12076:20000"),
			},
			Location:          pulumi.String("eastus"),
			ResourceGroupName: pulumi.String("rg1"),
			Subnets: []network.SubnetTypeArgs{
				{
					AddressPrefix: pulumi.String("10.0.0.0/24"),
					Name:          pulumi.String("test-1"),
				},
			},
			VirtualNetworkName: pulumi.String("test-vnet"),
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
import com.pulumi.azurenative.network.VirtualNetwork;
import com.pulumi.azurenative.network.VirtualNetworkArgs;
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
        var virtualNetwork = new VirtualNetwork("virtualNetwork", VirtualNetworkArgs.builder()        
            .addressSpace(Map.of("addressPrefixes", "10.0.0.0/16"))
            .bgpCommunities(Map.of("virtualNetworkCommunity", "12076:20000"))
            .location("eastus")
            .resourceGroupName("rg1")
            .subnets(Map.ofEntries(
                Map.entry("addressPrefix", "10.0.0.0/24"),
                Map.entry("name", "test-1")
            ))
            .virtualNetworkName("test-vnet")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualNetwork = new azure_native.network.VirtualNetwork("virtualNetwork", {
    addressSpace: {
        addressPrefixes: ["10.0.0.0/16"],
    },
    bgpCommunities: {
        virtualNetworkCommunity: "12076:20000",
    },
    location: "eastus",
    resourceGroupName: "rg1",
    subnets: [{
        addressPrefix: "10.0.0.0/24",
        name: "test-1",
    }],
    virtualNetworkName: "test-vnet",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_network = azure_native.network.VirtualNetwork("virtualNetwork",
    address_space=azure_native.network.AddressSpaceArgs(
        address_prefixes=["10.0.0.0/16"],
    ),
    bgp_communities=azure_native.network.VirtualNetworkBgpCommunitiesArgs(
        virtual_network_community="12076:20000",
    ),
    location="eastus",
    resource_group_name="rg1",
    subnets=[azure_native.network.SubnetArgs(
        address_prefix="10.0.0.0/24",
        name="test-1",
    )],
    virtual_network_name="test-vnet")

```

```yaml
resources:
  virtualNetwork:
    type: azure-native:network:VirtualNetwork
    properties:
      addressSpace:
        addressPrefixes:
          - 10.0.0.0/16
      bgpCommunities:
        virtualNetworkCommunity: 12076:20000
      location: eastus
      resourceGroupName: rg1
      subnets:
        - addressPrefix: 10.0.0.0/24
          name: test-1
      virtualNetworkName: test-vnet

```

{{% /example %}}
{{% example %}}
### Create virtual network with delegated subnets
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualNetwork = new AzureNative.Network.VirtualNetwork("virtualNetwork", new()
    {
        AddressSpace = new AzureNative.Network.Inputs.AddressSpaceArgs
        {
            AddressPrefixes = new[]
            {
                "10.0.0.0/16",
            },
        },
        Location = "westcentralus",
        ResourceGroupName = "rg1",
        Subnets = new[]
        {
            new AzureNative.Network.Inputs.SubnetArgs
            {
                AddressPrefix = "10.0.0.0/24",
                Delegations = new[]
                {
                    new AzureNative.Network.Inputs.DelegationArgs
                    {
                        Name = "myDelegation",
                        ServiceName = "Microsoft.Sql/managedInstances",
                    },
                },
                Name = "test-1",
            },
        },
        VirtualNetworkName = "test-vnet",
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
		_, err := network.NewVirtualNetwork(ctx, "virtualNetwork", &network.VirtualNetworkArgs{
			AddressSpace: &network.AddressSpaceArgs{
				AddressPrefixes: pulumi.StringArray{
					pulumi.String("10.0.0.0/16"),
				},
			},
			Location:          pulumi.String("westcentralus"),
			ResourceGroupName: pulumi.String("rg1"),
			Subnets: []network.SubnetTypeArgs{
				{
					AddressPrefix: pulumi.String("10.0.0.0/24"),
					Delegations: network.DelegationArray{
						{
							Name:        pulumi.String("myDelegation"),
							ServiceName: pulumi.String("Microsoft.Sql/managedInstances"),
						},
					},
					Name: pulumi.String("test-1"),
				},
			},
			VirtualNetworkName: pulumi.String("test-vnet"),
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
import com.pulumi.azurenative.network.VirtualNetwork;
import com.pulumi.azurenative.network.VirtualNetworkArgs;
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
        var virtualNetwork = new VirtualNetwork("virtualNetwork", VirtualNetworkArgs.builder()        
            .addressSpace(Map.of("addressPrefixes", "10.0.0.0/16"))
            .location("westcentralus")
            .resourceGroupName("rg1")
            .subnets(Map.ofEntries(
                Map.entry("addressPrefix", "10.0.0.0/24"),
                Map.entry("delegations", Map.ofEntries(
                    Map.entry("name", "myDelegation"),
                    Map.entry("serviceName", "Microsoft.Sql/managedInstances")
                )),
                Map.entry("name", "test-1")
            ))
            .virtualNetworkName("test-vnet")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualNetwork = new azure_native.network.VirtualNetwork("virtualNetwork", {
    addressSpace: {
        addressPrefixes: ["10.0.0.0/16"],
    },
    location: "westcentralus",
    resourceGroupName: "rg1",
    subnets: [{
        addressPrefix: "10.0.0.0/24",
        delegations: [{
            name: "myDelegation",
            serviceName: "Microsoft.Sql/managedInstances",
        }],
        name: "test-1",
    }],
    virtualNetworkName: "test-vnet",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_network = azure_native.network.VirtualNetwork("virtualNetwork",
    address_space=azure_native.network.AddressSpaceArgs(
        address_prefixes=["10.0.0.0/16"],
    ),
    location="westcentralus",
    resource_group_name="rg1",
    subnets=[{
        "addressPrefix": "10.0.0.0/24",
        "delegations": [azure_native.network.DelegationArgs(
            name="myDelegation",
            service_name="Microsoft.Sql/managedInstances",
        )],
        "name": "test-1",
    }],
    virtual_network_name="test-vnet")

```

```yaml
resources:
  virtualNetwork:
    type: azure-native:network:VirtualNetwork
    properties:
      addressSpace:
        addressPrefixes:
          - 10.0.0.0/16
      location: westcentralus
      resourceGroupName: rg1
      subnets:
        - addressPrefix: 10.0.0.0/24
          delegations:
            - name: myDelegation
              serviceName: Microsoft.Sql/managedInstances
          name: test-1
      virtualNetworkName: test-vnet

```

{{% /example %}}
{{% example %}}
### Create virtual network with encryption
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualNetwork = new AzureNative.Network.VirtualNetwork("virtualNetwork", new()
    {
        AddressSpace = new AzureNative.Network.Inputs.AddressSpaceArgs
        {
            AddressPrefixes = new[]
            {
                "10.0.0.0/16",
            },
        },
        Encryption = new AzureNative.Network.Inputs.VirtualNetworkEncryptionArgs
        {
            Enabled = true,
            Enforcement = "AllowUnencrypted",
        },
        Location = "eastus",
        ResourceGroupName = "rg1",
        Subnets = new[]
        {
            new AzureNative.Network.Inputs.SubnetArgs
            {
                AddressPrefix = "10.0.0.0/24",
                Name = "test-1",
            },
        },
        VirtualNetworkName = "test-vnet",
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
		_, err := network.NewVirtualNetwork(ctx, "virtualNetwork", &network.VirtualNetworkArgs{
			AddressSpace: &network.AddressSpaceArgs{
				AddressPrefixes: pulumi.StringArray{
					pulumi.String("10.0.0.0/16"),
				},
			},
			Encryption: &network.VirtualNetworkEncryptionArgs{
				Enabled:     pulumi.Bool(true),
				Enforcement: pulumi.String("AllowUnencrypted"),
			},
			Location:          pulumi.String("eastus"),
			ResourceGroupName: pulumi.String("rg1"),
			Subnets: []network.SubnetTypeArgs{
				{
					AddressPrefix: pulumi.String("10.0.0.0/24"),
					Name:          pulumi.String("test-1"),
				},
			},
			VirtualNetworkName: pulumi.String("test-vnet"),
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
import com.pulumi.azurenative.network.VirtualNetwork;
import com.pulumi.azurenative.network.VirtualNetworkArgs;
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
        var virtualNetwork = new VirtualNetwork("virtualNetwork", VirtualNetworkArgs.builder()        
            .addressSpace(Map.of("addressPrefixes", "10.0.0.0/16"))
            .encryption(Map.ofEntries(
                Map.entry("enabled", true),
                Map.entry("enforcement", "AllowUnencrypted")
            ))
            .location("eastus")
            .resourceGroupName("rg1")
            .subnets(Map.ofEntries(
                Map.entry("addressPrefix", "10.0.0.0/24"),
                Map.entry("name", "test-1")
            ))
            .virtualNetworkName("test-vnet")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualNetwork = new azure_native.network.VirtualNetwork("virtualNetwork", {
    addressSpace: {
        addressPrefixes: ["10.0.0.0/16"],
    },
    encryption: {
        enabled: true,
        enforcement: "AllowUnencrypted",
    },
    location: "eastus",
    resourceGroupName: "rg1",
    subnets: [{
        addressPrefix: "10.0.0.0/24",
        name: "test-1",
    }],
    virtualNetworkName: "test-vnet",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_network = azure_native.network.VirtualNetwork("virtualNetwork",
    address_space=azure_native.network.AddressSpaceArgs(
        address_prefixes=["10.0.0.0/16"],
    ),
    encryption=azure_native.network.VirtualNetworkEncryptionArgs(
        enabled=True,
        enforcement="AllowUnencrypted",
    ),
    location="eastus",
    resource_group_name="rg1",
    subnets=[azure_native.network.SubnetArgs(
        address_prefix="10.0.0.0/24",
        name="test-1",
    )],
    virtual_network_name="test-vnet")

```

```yaml
resources:
  virtualNetwork:
    type: azure-native:network:VirtualNetwork
    properties:
      addressSpace:
        addressPrefixes:
          - 10.0.0.0/16
      encryption:
        enabled: true
        enforcement: AllowUnencrypted
      location: eastus
      resourceGroupName: rg1
      subnets:
        - addressPrefix: 10.0.0.0/24
          name: test-1
      virtualNetworkName: test-vnet

```

{{% /example %}}
{{% example %}}
### Create virtual network with service endpoints
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualNetwork = new AzureNative.Network.VirtualNetwork("virtualNetwork", new()
    {
        AddressSpace = new AzureNative.Network.Inputs.AddressSpaceArgs
        {
            AddressPrefixes = new[]
            {
                "10.0.0.0/16",
            },
        },
        Location = "eastus",
        ResourceGroupName = "vnetTest",
        Subnets = new[]
        {
            new AzureNative.Network.Inputs.SubnetArgs
            {
                AddressPrefix = "10.0.0.0/16",
                Name = "test-1",
                ServiceEndpoints = new[]
                {
                    new AzureNative.Network.Inputs.ServiceEndpointPropertiesFormatArgs
                    {
                        Service = "Microsoft.Storage",
                    },
                },
            },
        },
        VirtualNetworkName = "vnet1",
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
		_, err := network.NewVirtualNetwork(ctx, "virtualNetwork", &network.VirtualNetworkArgs{
			AddressSpace: &network.AddressSpaceArgs{
				AddressPrefixes: pulumi.StringArray{
					pulumi.String("10.0.0.0/16"),
				},
			},
			Location:          pulumi.String("eastus"),
			ResourceGroupName: pulumi.String("vnetTest"),
			Subnets: []network.SubnetTypeArgs{
				{
					AddressPrefix: pulumi.String("10.0.0.0/16"),
					Name:          pulumi.String("test-1"),
					ServiceEndpoints: network.ServiceEndpointPropertiesFormatArray{
						{
							Service: pulumi.String("Microsoft.Storage"),
						},
					},
				},
			},
			VirtualNetworkName: pulumi.String("vnet1"),
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
import com.pulumi.azurenative.network.VirtualNetwork;
import com.pulumi.azurenative.network.VirtualNetworkArgs;
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
        var virtualNetwork = new VirtualNetwork("virtualNetwork", VirtualNetworkArgs.builder()        
            .addressSpace(Map.of("addressPrefixes", "10.0.0.0/16"))
            .location("eastus")
            .resourceGroupName("vnetTest")
            .subnets(Map.ofEntries(
                Map.entry("addressPrefix", "10.0.0.0/16"),
                Map.entry("name", "test-1"),
                Map.entry("serviceEndpoints", Map.of("service", "Microsoft.Storage"))
            ))
            .virtualNetworkName("vnet1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualNetwork = new azure_native.network.VirtualNetwork("virtualNetwork", {
    addressSpace: {
        addressPrefixes: ["10.0.0.0/16"],
    },
    location: "eastus",
    resourceGroupName: "vnetTest",
    subnets: [{
        addressPrefix: "10.0.0.0/16",
        name: "test-1",
        serviceEndpoints: [{
            service: "Microsoft.Storage",
        }],
    }],
    virtualNetworkName: "vnet1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_network = azure_native.network.VirtualNetwork("virtualNetwork",
    address_space=azure_native.network.AddressSpaceArgs(
        address_prefixes=["10.0.0.0/16"],
    ),
    location="eastus",
    resource_group_name="vnetTest",
    subnets=[{
        "addressPrefix": "10.0.0.0/16",
        "name": "test-1",
        "serviceEndpoints": [azure_native.network.ServiceEndpointPropertiesFormatArgs(
            service="Microsoft.Storage",
        )],
    }],
    virtual_network_name="vnet1")

```

```yaml
resources:
  virtualNetwork:
    type: azure-native:network:VirtualNetwork
    properties:
      addressSpace:
        addressPrefixes:
          - 10.0.0.0/16
      location: eastus
      resourceGroupName: vnetTest
      subnets:
        - addressPrefix: 10.0.0.0/16
          name: test-1
          serviceEndpoints:
            - service: Microsoft.Storage
      virtualNetworkName: vnet1

```

{{% /example %}}
{{% example %}}
### Create virtual network with service endpoints and service endpoint policy
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualNetwork = new AzureNative.Network.VirtualNetwork("virtualNetwork", new()
    {
        AddressSpace = new AzureNative.Network.Inputs.AddressSpaceArgs
        {
            AddressPrefixes = new[]
            {
                "10.0.0.0/16",
            },
        },
        Location = "eastus2euap",
        ResourceGroupName = "vnetTest",
        Subnets = new[]
        {
            new AzureNative.Network.Inputs.SubnetArgs
            {
                AddressPrefix = "10.0.0.0/16",
                Name = "test-1",
                ServiceEndpointPolicies = new[]
                {
                    new AzureNative.Network.Inputs.ServiceEndpointPolicyArgs
                    {
                        Id = "/subscriptions/subid/resourceGroups/vnetTest/providers/Microsoft.Network/serviceEndpointPolicies/ServiceEndpointPolicy1",
                    },
                },
                ServiceEndpoints = new[]
                {
                    new AzureNative.Network.Inputs.ServiceEndpointPropertiesFormatArgs
                    {
                        Service = "Microsoft.Storage",
                    },
                },
            },
        },
        VirtualNetworkName = "vnet1",
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
		_, err := network.NewVirtualNetwork(ctx, "virtualNetwork", &network.VirtualNetworkArgs{
			AddressSpace: &network.AddressSpaceArgs{
				AddressPrefixes: pulumi.StringArray{
					pulumi.String("10.0.0.0/16"),
				},
			},
			Location:          pulumi.String("eastus2euap"),
			ResourceGroupName: pulumi.String("vnetTest"),
			Subnets: []network.SubnetTypeArgs{
				{
					AddressPrefix: pulumi.String("10.0.0.0/16"),
					Name:          pulumi.String("test-1"),
					ServiceEndpointPolicies: network.ServiceEndpointPolicyTypeArray{
						{
							Id: pulumi.String("/subscriptions/subid/resourceGroups/vnetTest/providers/Microsoft.Network/serviceEndpointPolicies/ServiceEndpointPolicy1"),
						},
					},
					ServiceEndpoints: network.ServiceEndpointPropertiesFormatArray{
						{
							Service: pulumi.String("Microsoft.Storage"),
						},
					},
				},
			},
			VirtualNetworkName: pulumi.String("vnet1"),
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
import com.pulumi.azurenative.network.VirtualNetwork;
import com.pulumi.azurenative.network.VirtualNetworkArgs;
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
        var virtualNetwork = new VirtualNetwork("virtualNetwork", VirtualNetworkArgs.builder()        
            .addressSpace(Map.of("addressPrefixes", "10.0.0.0/16"))
            .location("eastus2euap")
            .resourceGroupName("vnetTest")
            .subnets(Map.ofEntries(
                Map.entry("addressPrefix", "10.0.0.0/16"),
                Map.entry("name", "test-1"),
                Map.entry("serviceEndpointPolicies", Map.of("id", "/subscriptions/subid/resourceGroups/vnetTest/providers/Microsoft.Network/serviceEndpointPolicies/ServiceEndpointPolicy1")),
                Map.entry("serviceEndpoints", Map.of("service", "Microsoft.Storage"))
            ))
            .virtualNetworkName("vnet1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualNetwork = new azure_native.network.VirtualNetwork("virtualNetwork", {
    addressSpace: {
        addressPrefixes: ["10.0.0.0/16"],
    },
    location: "eastus2euap",
    resourceGroupName: "vnetTest",
    subnets: [{
        addressPrefix: "10.0.0.0/16",
        name: "test-1",
        serviceEndpointPolicies: [{
            id: "/subscriptions/subid/resourceGroups/vnetTest/providers/Microsoft.Network/serviceEndpointPolicies/ServiceEndpointPolicy1",
        }],
        serviceEndpoints: [{
            service: "Microsoft.Storage",
        }],
    }],
    virtualNetworkName: "vnet1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_network = azure_native.network.VirtualNetwork("virtualNetwork",
    address_space=azure_native.network.AddressSpaceArgs(
        address_prefixes=["10.0.0.0/16"],
    ),
    location="eastus2euap",
    resource_group_name="vnetTest",
    subnets=[{
        "addressPrefix": "10.0.0.0/16",
        "name": "test-1",
        "serviceEndpointPolicies": [azure_native.network.ServiceEndpointPolicyArgs(
            id="/subscriptions/subid/resourceGroups/vnetTest/providers/Microsoft.Network/serviceEndpointPolicies/ServiceEndpointPolicy1",
        )],
        "serviceEndpoints": [azure_native.network.ServiceEndpointPropertiesFormatArgs(
            service="Microsoft.Storage",
        )],
    }],
    virtual_network_name="vnet1")

```

```yaml
resources:
  virtualNetwork:
    type: azure-native:network:VirtualNetwork
    properties:
      addressSpace:
        addressPrefixes:
          - 10.0.0.0/16
      location: eastus2euap
      resourceGroupName: vnetTest
      subnets:
        - addressPrefix: 10.0.0.0/16
          name: test-1
          serviceEndpointPolicies:
            - id: /subscriptions/subid/resourceGroups/vnetTest/providers/Microsoft.Network/serviceEndpointPolicies/ServiceEndpointPolicy1
          serviceEndpoints:
            - service: Microsoft.Storage
      virtualNetworkName: vnet1

```

{{% /example %}}
{{% example %}}
### Create virtual network with subnet
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualNetwork = new AzureNative.Network.VirtualNetwork("virtualNetwork", new()
    {
        AddressSpace = new AzureNative.Network.Inputs.AddressSpaceArgs
        {
            AddressPrefixes = new[]
            {
                "10.0.0.0/16",
            },
        },
        Location = "eastus",
        ResourceGroupName = "rg1",
        Subnets = new[]
        {
            new AzureNative.Network.Inputs.SubnetArgs
            {
                AddressPrefix = "10.0.0.0/24",
                Name = "test-1",
            },
        },
        VirtualNetworkName = "test-vnet",
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
		_, err := network.NewVirtualNetwork(ctx, "virtualNetwork", &network.VirtualNetworkArgs{
			AddressSpace: &network.AddressSpaceArgs{
				AddressPrefixes: pulumi.StringArray{
					pulumi.String("10.0.0.0/16"),
				},
			},
			Location:          pulumi.String("eastus"),
			ResourceGroupName: pulumi.String("rg1"),
			Subnets: []network.SubnetTypeArgs{
				{
					AddressPrefix: pulumi.String("10.0.0.0/24"),
					Name:          pulumi.String("test-1"),
				},
			},
			VirtualNetworkName: pulumi.String("test-vnet"),
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
import com.pulumi.azurenative.network.VirtualNetwork;
import com.pulumi.azurenative.network.VirtualNetworkArgs;
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
        var virtualNetwork = new VirtualNetwork("virtualNetwork", VirtualNetworkArgs.builder()        
            .addressSpace(Map.of("addressPrefixes", "10.0.0.0/16"))
            .location("eastus")
            .resourceGroupName("rg1")
            .subnets(Map.ofEntries(
                Map.entry("addressPrefix", "10.0.0.0/24"),
                Map.entry("name", "test-1")
            ))
            .virtualNetworkName("test-vnet")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualNetwork = new azure_native.network.VirtualNetwork("virtualNetwork", {
    addressSpace: {
        addressPrefixes: ["10.0.0.0/16"],
    },
    location: "eastus",
    resourceGroupName: "rg1",
    subnets: [{
        addressPrefix: "10.0.0.0/24",
        name: "test-1",
    }],
    virtualNetworkName: "test-vnet",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_network = azure_native.network.VirtualNetwork("virtualNetwork",
    address_space=azure_native.network.AddressSpaceArgs(
        address_prefixes=["10.0.0.0/16"],
    ),
    location="eastus",
    resource_group_name="rg1",
    subnets=[azure_native.network.SubnetArgs(
        address_prefix="10.0.0.0/24",
        name="test-1",
    )],
    virtual_network_name="test-vnet")

```

```yaml
resources:
  virtualNetwork:
    type: azure-native:network:VirtualNetwork
    properties:
      addressSpace:
        addressPrefixes:
          - 10.0.0.0/16
      location: eastus
      resourceGroupName: rg1
      subnets:
        - addressPrefix: 10.0.0.0/24
          name: test-1
      virtualNetworkName: test-vnet

```

{{% /example %}}
{{% example %}}
### Create virtual network with subnet containing address prefixes
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualNetwork = new AzureNative.Network.VirtualNetwork("virtualNetwork", new()
    {
        AddressSpace = new AzureNative.Network.Inputs.AddressSpaceArgs
        {
            AddressPrefixes = new[]
            {
                "10.0.0.0/16",
            },
        },
        Location = "eastus",
        ResourceGroupName = "rg1",
        Subnets = new[]
        {
            new AzureNative.Network.Inputs.SubnetArgs
            {
                AddressPrefixes = new[]
                {
                    "10.0.0.0/28",
                    "10.0.1.0/28",
                },
                Name = "test-2",
            },
        },
        VirtualNetworkName = "test-vnet",
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
		_, err := network.NewVirtualNetwork(ctx, "virtualNetwork", &network.VirtualNetworkArgs{
			AddressSpace: &network.AddressSpaceArgs{
				AddressPrefixes: pulumi.StringArray{
					pulumi.String("10.0.0.0/16"),
				},
			},
			Location:          pulumi.String("eastus"),
			ResourceGroupName: pulumi.String("rg1"),
			Subnets: []network.SubnetTypeArgs{
				{
					AddressPrefixes: pulumi.StringArray{
						pulumi.String("10.0.0.0/28"),
						pulumi.String("10.0.1.0/28"),
					},
					Name: pulumi.String("test-2"),
				},
			},
			VirtualNetworkName: pulumi.String("test-vnet"),
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
import com.pulumi.azurenative.network.VirtualNetwork;
import com.pulumi.azurenative.network.VirtualNetworkArgs;
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
        var virtualNetwork = new VirtualNetwork("virtualNetwork", VirtualNetworkArgs.builder()        
            .addressSpace(Map.of("addressPrefixes", "10.0.0.0/16"))
            .location("eastus")
            .resourceGroupName("rg1")
            .subnets(Map.ofEntries(
                Map.entry("addressPrefixes",                 
                    "10.0.0.0/28",
                    "10.0.1.0/28"),
                Map.entry("name", "test-2")
            ))
            .virtualNetworkName("test-vnet")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualNetwork = new azure_native.network.VirtualNetwork("virtualNetwork", {
    addressSpace: {
        addressPrefixes: ["10.0.0.0/16"],
    },
    location: "eastus",
    resourceGroupName: "rg1",
    subnets: [{
        addressPrefixes: [
            "10.0.0.0/28",
            "10.0.1.0/28",
        ],
        name: "test-2",
    }],
    virtualNetworkName: "test-vnet",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_network = azure_native.network.VirtualNetwork("virtualNetwork",
    address_space=azure_native.network.AddressSpaceArgs(
        address_prefixes=["10.0.0.0/16"],
    ),
    location="eastus",
    resource_group_name="rg1",
    subnets=[azure_native.network.SubnetArgs(
        address_prefixes=[
            "10.0.0.0/28",
            "10.0.1.0/28",
        ],
        name="test-2",
    )],
    virtual_network_name="test-vnet")

```

```yaml
resources:
  virtualNetwork:
    type: azure-native:network:VirtualNetwork
    properties:
      addressSpace:
        addressPrefixes:
          - 10.0.0.0/16
      location: eastus
      resourceGroupName: rg1
      subnets:
        - addressPrefixes:
            - 10.0.0.0/28
            - 10.0.1.0/28
          name: test-2
      virtualNetworkName: test-vnet

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:VirtualNetwork test-vnet /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/virtualNetworks/test-vnet 
```
