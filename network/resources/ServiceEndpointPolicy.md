Service End point policy resource.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create service endpoint policy
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var serviceEndpointPolicy = new AzureNative.Network.ServiceEndpointPolicy("serviceEndpointPolicy", new()
    {
        Location = "westus",
        ResourceGroupName = "rg1",
        ServiceEndpointPolicyName = "testPolicy",
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
		_, err := network.NewServiceEndpointPolicy(ctx, "serviceEndpointPolicy", &network.ServiceEndpointPolicyArgs{
			Location:                  pulumi.String("westus"),
			ResourceGroupName:         pulumi.String("rg1"),
			ServiceEndpointPolicyName: pulumi.String("testPolicy"),
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
import com.pulumi.azurenative.network.ServiceEndpointPolicy;
import com.pulumi.azurenative.network.ServiceEndpointPolicyArgs;
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
        var serviceEndpointPolicy = new ServiceEndpointPolicy("serviceEndpointPolicy", ServiceEndpointPolicyArgs.builder()        
            .location("westus")
            .resourceGroupName("rg1")
            .serviceEndpointPolicyName("testPolicy")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const serviceEndpointPolicy = new azure_native.network.ServiceEndpointPolicy("serviceEndpointPolicy", {
    location: "westus",
    resourceGroupName: "rg1",
    serviceEndpointPolicyName: "testPolicy",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service_endpoint_policy = azure_native.network.ServiceEndpointPolicy("serviceEndpointPolicy",
    location="westus",
    resource_group_name="rg1",
    service_endpoint_policy_name="testPolicy")

```

```yaml
resources:
  serviceEndpointPolicy:
    type: azure-native:network:ServiceEndpointPolicy
    properties:
      location: westus
      resourceGroupName: rg1
      serviceEndpointPolicyName: testPolicy

```

{{% /example %}}
{{% example %}}
### Create service endpoint policy with definition
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var serviceEndpointPolicy = new AzureNative.Network.ServiceEndpointPolicy("serviceEndpointPolicy", new()
    {
        Location = "westus",
        ResourceGroupName = "rg1",
        ServiceEndpointPolicyDefinitions = new[]
        {
            new AzureNative.Network.Inputs.ServiceEndpointPolicyDefinitionArgs
            {
                Description = "Storage Service EndpointPolicy Definition",
                Name = "StorageServiceEndpointPolicyDefinition",
                Service = "Microsoft.Storage",
                ServiceResources = new[]
                {
                    "/subscriptions/subid1",
                    "/subscriptions/subid1/resourceGroups/storageRg",
                    "/subscriptions/subid1/resourceGroups/storageRg/providers/Microsoft.Storage/storageAccounts/stAccount",
                },
            },
        },
        ServiceEndpointPolicyName = "testPolicy",
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
		_, err := network.NewServiceEndpointPolicy(ctx, "serviceEndpointPolicy", &network.ServiceEndpointPolicyArgs{
			Location:          pulumi.String("westus"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceEndpointPolicyDefinitions: []network.ServiceEndpointPolicyDefinitionTypeArgs{
				{
					Description: pulumi.String("Storage Service EndpointPolicy Definition"),
					Name:        pulumi.String("StorageServiceEndpointPolicyDefinition"),
					Service:     pulumi.String("Microsoft.Storage"),
					ServiceResources: pulumi.StringArray{
						pulumi.String("/subscriptions/subid1"),
						pulumi.String("/subscriptions/subid1/resourceGroups/storageRg"),
						pulumi.String("/subscriptions/subid1/resourceGroups/storageRg/providers/Microsoft.Storage/storageAccounts/stAccount"),
					},
				},
			},
			ServiceEndpointPolicyName: pulumi.String("testPolicy"),
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
import com.pulumi.azurenative.network.ServiceEndpointPolicy;
import com.pulumi.azurenative.network.ServiceEndpointPolicyArgs;
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
        var serviceEndpointPolicy = new ServiceEndpointPolicy("serviceEndpointPolicy", ServiceEndpointPolicyArgs.builder()        
            .location("westus")
            .resourceGroupName("rg1")
            .serviceEndpointPolicyDefinitions(Map.ofEntries(
                Map.entry("description", "Storage Service EndpointPolicy Definition"),
                Map.entry("name", "StorageServiceEndpointPolicyDefinition"),
                Map.entry("service", "Microsoft.Storage"),
                Map.entry("serviceResources",                 
                    "/subscriptions/subid1",
                    "/subscriptions/subid1/resourceGroups/storageRg",
                    "/subscriptions/subid1/resourceGroups/storageRg/providers/Microsoft.Storage/storageAccounts/stAccount")
            ))
            .serviceEndpointPolicyName("testPolicy")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const serviceEndpointPolicy = new azure_native.network.ServiceEndpointPolicy("serviceEndpointPolicy", {
    location: "westus",
    resourceGroupName: "rg1",
    serviceEndpointPolicyDefinitions: [{
        description: "Storage Service EndpointPolicy Definition",
        name: "StorageServiceEndpointPolicyDefinition",
        service: "Microsoft.Storage",
        serviceResources: [
            "/subscriptions/subid1",
            "/subscriptions/subid1/resourceGroups/storageRg",
            "/subscriptions/subid1/resourceGroups/storageRg/providers/Microsoft.Storage/storageAccounts/stAccount",
        ],
    }],
    serviceEndpointPolicyName: "testPolicy",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service_endpoint_policy = azure_native.network.ServiceEndpointPolicy("serviceEndpointPolicy",
    location="westus",
    resource_group_name="rg1",
    service_endpoint_policy_definitions=[azure_native.network.ServiceEndpointPolicyDefinitionArgs(
        description="Storage Service EndpointPolicy Definition",
        name="StorageServiceEndpointPolicyDefinition",
        service="Microsoft.Storage",
        service_resources=[
            "/subscriptions/subid1",
            "/subscriptions/subid1/resourceGroups/storageRg",
            "/subscriptions/subid1/resourceGroups/storageRg/providers/Microsoft.Storage/storageAccounts/stAccount",
        ],
    )],
    service_endpoint_policy_name="testPolicy")

```

```yaml
resources:
  serviceEndpointPolicy:
    type: azure-native:network:ServiceEndpointPolicy
    properties:
      location: westus
      resourceGroupName: rg1
      serviceEndpointPolicyDefinitions:
        - description: Storage Service EndpointPolicy Definition
          name: StorageServiceEndpointPolicyDefinition
          service: Microsoft.Storage
          serviceResources:
            - /subscriptions/subid1
            - /subscriptions/subid1/resourceGroups/storageRg
            - /subscriptions/subid1/resourceGroups/storageRg/providers/Microsoft.Storage/storageAccounts/stAccount
      serviceEndpointPolicyName: testPolicy

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:ServiceEndpointPolicy testnsg /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/ServiceEndpointPolicies/testpolicy 
```
