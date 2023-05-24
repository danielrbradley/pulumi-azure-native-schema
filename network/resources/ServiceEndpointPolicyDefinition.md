Service Endpoint policy definitions.
API Version: 2022-09-01.
Previous API Version: 2020-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create service endpoint policy definition
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var serviceEndpointPolicyDefinition = new AzureNative.Network.ServiceEndpointPolicyDefinition("serviceEndpointPolicyDefinition", new()
    {
        Description = "Storage Service EndpointPolicy Definition",
        ResourceGroupName = "rg1",
        Service = "Microsoft.Storage",
        ServiceEndpointPolicyDefinitionName = "testDefinition",
        ServiceEndpointPolicyName = "testPolicy",
        ServiceResources = new[]
        {
            "/subscriptions/subid1",
            "/subscriptions/subid1/resourceGroups/storageRg",
            "/subscriptions/subid1/resourceGroups/storageRg/providers/Microsoft.Storage/storageAccounts/stAccount",
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
		_, err := network.NewServiceEndpointPolicyDefinition(ctx, "serviceEndpointPolicyDefinition", &network.ServiceEndpointPolicyDefinitionArgs{
			Description:                         pulumi.String("Storage Service EndpointPolicy Definition"),
			ResourceGroupName:                   pulumi.String("rg1"),
			Service:                             pulumi.String("Microsoft.Storage"),
			ServiceEndpointPolicyDefinitionName: pulumi.String("testDefinition"),
			ServiceEndpointPolicyName:           pulumi.String("testPolicy"),
			ServiceResources: pulumi.StringArray{
				pulumi.String("/subscriptions/subid1"),
				pulumi.String("/subscriptions/subid1/resourceGroups/storageRg"),
				pulumi.String("/subscriptions/subid1/resourceGroups/storageRg/providers/Microsoft.Storage/storageAccounts/stAccount"),
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
import com.pulumi.azurenative.network.ServiceEndpointPolicyDefinition;
import com.pulumi.azurenative.network.ServiceEndpointPolicyDefinitionArgs;
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
        var serviceEndpointPolicyDefinition = new ServiceEndpointPolicyDefinition("serviceEndpointPolicyDefinition", ServiceEndpointPolicyDefinitionArgs.builder()        
            .description("Storage Service EndpointPolicy Definition")
            .resourceGroupName("rg1")
            .service("Microsoft.Storage")
            .serviceEndpointPolicyDefinitionName("testDefinition")
            .serviceEndpointPolicyName("testPolicy")
            .serviceResources(            
                "/subscriptions/subid1",
                "/subscriptions/subid1/resourceGroups/storageRg",
                "/subscriptions/subid1/resourceGroups/storageRg/providers/Microsoft.Storage/storageAccounts/stAccount")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const serviceEndpointPolicyDefinition = new azure_native.network.ServiceEndpointPolicyDefinition("serviceEndpointPolicyDefinition", {
    description: "Storage Service EndpointPolicy Definition",
    resourceGroupName: "rg1",
    service: "Microsoft.Storage",
    serviceEndpointPolicyDefinitionName: "testDefinition",
    serviceEndpointPolicyName: "testPolicy",
    serviceResources: [
        "/subscriptions/subid1",
        "/subscriptions/subid1/resourceGroups/storageRg",
        "/subscriptions/subid1/resourceGroups/storageRg/providers/Microsoft.Storage/storageAccounts/stAccount",
    ],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service_endpoint_policy_definition = azure_native.network.ServiceEndpointPolicyDefinition("serviceEndpointPolicyDefinition",
    description="Storage Service EndpointPolicy Definition",
    resource_group_name="rg1",
    service="Microsoft.Storage",
    service_endpoint_policy_definition_name="testDefinition",
    service_endpoint_policy_name="testPolicy",
    service_resources=[
        "/subscriptions/subid1",
        "/subscriptions/subid1/resourceGroups/storageRg",
        "/subscriptions/subid1/resourceGroups/storageRg/providers/Microsoft.Storage/storageAccounts/stAccount",
    ])

```

```yaml
resources:
  serviceEndpointPolicyDefinition:
    type: azure-native:network:ServiceEndpointPolicyDefinition
    properties:
      description: Storage Service EndpointPolicy Definition
      resourceGroupName: rg1
      service: Microsoft.Storage
      serviceEndpointPolicyDefinitionName: testDefinition
      serviceEndpointPolicyName: testPolicy
      serviceResources:
        - /subscriptions/subid1
        - /subscriptions/subid1/resourceGroups/storageRg
        - /subscriptions/subid1/resourceGroups/storageRg/providers/Microsoft.Storage/storageAccounts/stAccount

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:network:ServiceEndpointPolicyDefinition testDefinition /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Network/serviceEndpointPolicies/testPolicy/serviceEndpointPolicyDefinitions/testDefinition 
```
