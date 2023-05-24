ServiceEndpoint resource details.
API Version: 2022-02-01.
Previous API Version: 2022-02-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update ServiceEndpoint resource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var serviceEndpoint = new AzureNative.RecommendationsService.ServiceEndpoint("serviceEndpoint", new()
    {
        AccountName = "sampleAccount",
        Location = "West US",
        Properties = new AzureNative.RecommendationsService.Inputs.ServiceEndpointResourcePropertiesArgs
        {
            PreAllocatedCapacity = 100,
        },
        ResourceGroupName = "rg",
        ServiceEndpointName = "s1",
        Tags = 
        {
            { "Environment", "Prod" },
        },
    });

});


```

```go
package main

import (
	recommendationsservice "github.com/pulumi/pulumi-azure-native-sdk/recommendationsservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := recommendationsservice.NewServiceEndpoint(ctx, "serviceEndpoint", &recommendationsservice.ServiceEndpointArgs{
			AccountName: pulumi.String("sampleAccount"),
			Location:    pulumi.String("West US"),
			Properties: &recommendationsservice.ServiceEndpointResourcePropertiesArgs{
				PreAllocatedCapacity: pulumi.Int(100),
			},
			ResourceGroupName:   pulumi.String("rg"),
			ServiceEndpointName: pulumi.String("s1"),
			Tags: pulumi.StringMap{
				"Environment": pulumi.String("Prod"),
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
import com.pulumi.azurenative.recommendationsservice.ServiceEndpoint;
import com.pulumi.azurenative.recommendationsservice.ServiceEndpointArgs;
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
        var serviceEndpoint = new ServiceEndpoint("serviceEndpoint", ServiceEndpointArgs.builder()        
            .accountName("sampleAccount")
            .location("West US")
            .properties(Map.of("preAllocatedCapacity", 100))
            .resourceGroupName("rg")
            .serviceEndpointName("s1")
            .tags(Map.of("Environment", "Prod"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const serviceEndpoint = new azure_native.recommendationsservice.ServiceEndpoint("serviceEndpoint", {
    accountName: "sampleAccount",
    location: "West US",
    properties: {
        preAllocatedCapacity: 100,
    },
    resourceGroupName: "rg",
    serviceEndpointName: "s1",
    tags: {
        Environment: "Prod",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service_endpoint = azure_native.recommendationsservice.ServiceEndpoint("serviceEndpoint",
    account_name="sampleAccount",
    location="West US",
    properties=azure_native.recommendationsservice.ServiceEndpointResourcePropertiesArgs(
        pre_allocated_capacity=100,
    ),
    resource_group_name="rg",
    service_endpoint_name="s1",
    tags={
        "Environment": "Prod",
    })

```

```yaml
resources:
  serviceEndpoint:
    type: azure-native:recommendationsservice:ServiceEndpoint
    properties:
      accountName: sampleAccount
      location: West US
      properties:
        preAllocatedCapacity: 100
      resourceGroupName: rg
      serviceEndpointName: s1
      tags:
        Environment: Prod

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:recommendationsservice:ServiceEndpoint s1 /subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/resourceGroups/rg/providers/Microsoft.RecommendationsService/accounts/sampleAccount/serviceEndpoints/s1 
```
