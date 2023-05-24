Service resource
API Version: 2022-12-01.
Previous API Version: 2020-07-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Services_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var service = new AzureNative.AppPlatform.Service("service", new()
    {
        Location = "eastus",
        Properties = null,
        ResourceGroupName = "myResourceGroup",
        ServiceName = "myservice",
        Sku = new AzureNative.AppPlatform.Inputs.SkuArgs
        {
            Name = "S0",
            Tier = "Standard",
        },
        Tags = 
        {
            { "key1", "value1" },
        },
    });

});


```

```go
package main

import (
	appplatform "github.com/pulumi/pulumi-azure-native-sdk/appplatform"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := appplatform.NewService(ctx, "service", &appplatform.ServiceArgs{
			Location:          pulumi.String("eastus"),
			Properties:        nil,
			ResourceGroupName: pulumi.String("myResourceGroup"),
			ServiceName:       pulumi.String("myservice"),
			Sku: &appplatform.SkuArgs{
				Name: pulumi.String("S0"),
				Tier: pulumi.String("Standard"),
			},
			Tags: pulumi.StringMap{
				"key1": pulumi.String("value1"),
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
import com.pulumi.azurenative.appplatform.Service;
import com.pulumi.azurenative.appplatform.ServiceArgs;
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
        var service = new Service("service", ServiceArgs.builder()        
            .location("eastus")
            .properties()
            .resourceGroupName("myResourceGroup")
            .serviceName("myservice")
            .sku(Map.ofEntries(
                Map.entry("name", "S0"),
                Map.entry("tier", "Standard")
            ))
            .tags(Map.of("key1", "value1"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const service = new azure_native.appplatform.Service("service", {
    location: "eastus",
    properties: {},
    resourceGroupName: "myResourceGroup",
    serviceName: "myservice",
    sku: {
        name: "S0",
        tier: "Standard",
    },
    tags: {
        key1: "value1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service = azure_native.appplatform.Service("service",
    location="eastus",
    properties=azure_native.appplatform.ClusterResourcePropertiesArgs(),
    resource_group_name="myResourceGroup",
    service_name="myservice",
    sku=azure_native.appplatform.SkuArgs(
        name="S0",
        tier="Standard",
    ),
    tags={
        "key1": "value1",
    })

```

```yaml
resources:
  service:
    type: azure-native:appplatform:Service
    properties:
      location: eastus
      properties: {}
      resourceGroupName: myResourceGroup
      serviceName: myservice
      sku:
        name: S0
        tier: Standard
      tags:
        key1: value1

```

{{% /example %}}
{{% example %}}
### Services_CreateOrUpdate_Enterprise
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var service = new AzureNative.AppPlatform.Service("service", new()
    {
        Location = "eastus",
        Properties = null,
        ResourceGroupName = "myResourceGroup",
        ServiceName = "myservice",
        Sku = new AzureNative.AppPlatform.Inputs.SkuArgs
        {
            Name = "E0",
            Tier = "Enterprise",
        },
        Tags = 
        {
            { "key1", "value1" },
        },
    });

});


```

```go
package main

import (
	appplatform "github.com/pulumi/pulumi-azure-native-sdk/appplatform"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := appplatform.NewService(ctx, "service", &appplatform.ServiceArgs{
			Location:          pulumi.String("eastus"),
			Properties:        nil,
			ResourceGroupName: pulumi.String("myResourceGroup"),
			ServiceName:       pulumi.String("myservice"),
			Sku: &appplatform.SkuArgs{
				Name: pulumi.String("E0"),
				Tier: pulumi.String("Enterprise"),
			},
			Tags: pulumi.StringMap{
				"key1": pulumi.String("value1"),
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
import com.pulumi.azurenative.appplatform.Service;
import com.pulumi.azurenative.appplatform.ServiceArgs;
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
        var service = new Service("service", ServiceArgs.builder()        
            .location("eastus")
            .properties()
            .resourceGroupName("myResourceGroup")
            .serviceName("myservice")
            .sku(Map.ofEntries(
                Map.entry("name", "E0"),
                Map.entry("tier", "Enterprise")
            ))
            .tags(Map.of("key1", "value1"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const service = new azure_native.appplatform.Service("service", {
    location: "eastus",
    properties: {},
    resourceGroupName: "myResourceGroup",
    serviceName: "myservice",
    sku: {
        name: "E0",
        tier: "Enterprise",
    },
    tags: {
        key1: "value1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service = azure_native.appplatform.Service("service",
    location="eastus",
    properties=azure_native.appplatform.ClusterResourcePropertiesArgs(),
    resource_group_name="myResourceGroup",
    service_name="myservice",
    sku=azure_native.appplatform.SkuArgs(
        name="E0",
        tier="Enterprise",
    ),
    tags={
        "key1": "value1",
    })

```

```yaml
resources:
  service:
    type: azure-native:appplatform:Service
    properties:
      location: eastus
      properties: {}
      resourceGroupName: myResourceGroup
      serviceName: myservice
      sku:
        name: E0
        tier: Enterprise
      tags:
        key1: value1

```

{{% /example %}}
{{% example %}}
### Services_CreateOrUpdate_VNetInjection
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var service = new AzureNative.AppPlatform.Service("service", new()
    {
        Location = "eastus",
        Properties = new AzureNative.AppPlatform.Inputs.ClusterResourcePropertiesArgs
        {
            NetworkProfile = new AzureNative.AppPlatform.Inputs.NetworkProfileArgs
            {
                AppNetworkResourceGroup = "my-app-network-rg",
                AppSubnetId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myVirtualNetwork/subnets/apps",
                IngressConfig = new AzureNative.AppPlatform.Inputs.IngressConfigArgs
                {
                    ReadTimeoutInSeconds = 300,
                },
                ServiceCidr = "10.8.0.0/16,10.244.0.0/16,10.245.0.1/16",
                ServiceRuntimeNetworkResourceGroup = "my-service-runtime-network-rg",
                ServiceRuntimeSubnetId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myVirtualNetwork/subnets/serviceRuntime",
            },
            VnetAddons = new AzureNative.AppPlatform.Inputs.ServiceVNetAddonsArgs
            {
                LogStreamPublicEndpoint = true,
            },
        },
        ResourceGroupName = "myResourceGroup",
        ServiceName = "myservice",
        Sku = new AzureNative.AppPlatform.Inputs.SkuArgs
        {
            Name = "S0",
            Tier = "Standard",
        },
        Tags = 
        {
            { "key1", "value1" },
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.appplatform.Service;
import com.pulumi.azurenative.appplatform.ServiceArgs;
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
        var service = new Service("service", ServiceArgs.builder()        
            .location("eastus")
            .properties(Map.ofEntries(
                Map.entry("networkProfile", Map.ofEntries(
                    Map.entry("appNetworkResourceGroup", "my-app-network-rg"),
                    Map.entry("appSubnetId", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myVirtualNetwork/subnets/apps"),
                    Map.entry("ingressConfig", Map.of("readTimeoutInSeconds", 300)),
                    Map.entry("serviceCidr", "10.8.0.0/16,10.244.0.0/16,10.245.0.1/16"),
                    Map.entry("serviceRuntimeNetworkResourceGroup", "my-service-runtime-network-rg"),
                    Map.entry("serviceRuntimeSubnetId", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myVirtualNetwork/subnets/serviceRuntime")
                )),
                Map.entry("vnetAddons", Map.of("logStreamPublicEndpoint", true))
            ))
            .resourceGroupName("myResourceGroup")
            .serviceName("myservice")
            .sku(Map.ofEntries(
                Map.entry("name", "S0"),
                Map.entry("tier", "Standard")
            ))
            .tags(Map.of("key1", "value1"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const service = new azure_native.appplatform.Service("service", {
    location: "eastus",
    properties: {
        networkProfile: {
            appNetworkResourceGroup: "my-app-network-rg",
            appSubnetId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myVirtualNetwork/subnets/apps",
            ingressConfig: {
                readTimeoutInSeconds: 300,
            },
            serviceCidr: "10.8.0.0/16,10.244.0.0/16,10.245.0.1/16",
            serviceRuntimeNetworkResourceGroup: "my-service-runtime-network-rg",
            serviceRuntimeSubnetId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myVirtualNetwork/subnets/serviceRuntime",
        },
        vnetAddons: {
            logStreamPublicEndpoint: true,
        },
    },
    resourceGroupName: "myResourceGroup",
    serviceName: "myservice",
    sku: {
        name: "S0",
        tier: "Standard",
    },
    tags: {
        key1: "value1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service = azure_native.appplatform.Service("service",
    location="eastus",
    properties=azure_native.appplatform.ClusterResourcePropertiesResponseArgs(
        network_profile={
            "appNetworkResourceGroup": "my-app-network-rg",
            "appSubnetId": "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myVirtualNetwork/subnets/apps",
            "ingressConfig": azure_native.appplatform.IngressConfigArgs(
                read_timeout_in_seconds=300,
            ),
            "serviceCidr": "10.8.0.0/16,10.244.0.0/16,10.245.0.1/16",
            "serviceRuntimeNetworkResourceGroup": "my-service-runtime-network-rg",
            "serviceRuntimeSubnetId": "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myVirtualNetwork/subnets/serviceRuntime",
        },
        vnet_addons=azure_native.appplatform.ServiceVNetAddonsArgs(
            log_stream_public_endpoint=True,
        ),
    ),
    resource_group_name="myResourceGroup",
    service_name="myservice",
    sku=azure_native.appplatform.SkuArgs(
        name="S0",
        tier="Standard",
    ),
    tags={
        "key1": "value1",
    })

```

```yaml
resources:
  service:
    type: azure-native:appplatform:Service
    properties:
      location: eastus
      properties:
        networkProfile:
          appNetworkResourceGroup: my-app-network-rg
          appSubnetId: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myVirtualNetwork/subnets/apps
          ingressConfig:
            readTimeoutInSeconds: 300
          serviceCidr: 10.8.0.0/16,10.244.0.0/16,10.245.0.1/16
          serviceRuntimeNetworkResourceGroup: my-service-runtime-network-rg
          serviceRuntimeSubnetId: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/myVirtualNetwork/subnets/serviceRuntime
        vnetAddons:
          logStreamPublicEndpoint: true
      resourceGroupName: myResourceGroup
      serviceName: myservice
      sku:
        name: S0
        tier: Standard
      tags:
        key1: value1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:appplatform:Service myservice /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.AppPlatform/Spring/myservice 
```
