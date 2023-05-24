A manifest file that defines the custom resource provider resources.
API Version: 2018-09-01-preview.
Previous API Version: 2018-09-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update the custom resource provider
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var customResourceProvider = new AzureNative.CustomProviders.CustomResourceProvider("customResourceProvider", new()
    {
        Actions = new[]
        {
            new AzureNative.CustomProviders.Inputs.CustomRPActionRouteDefinitionArgs
            {
                Endpoint = "https://mytestendpoint/",
                Name = "TestAction",
                RoutingType = "Proxy",
            },
        },
        Location = "eastus",
        ResourceGroupName = "testRG",
        ResourceProviderName = "newrp",
        ResourceTypes = new[]
        {
            new AzureNative.CustomProviders.Inputs.CustomRPResourceTypeRouteDefinitionArgs
            {
                Endpoint = "https://mytestendpoint2/",
                Name = "TestResource",
                RoutingType = "Proxy,Cache",
            },
        },
    });

});


```

```go
package main

import (
	customproviders "github.com/pulumi/pulumi-azure-native-sdk/customproviders"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := customproviders.NewCustomResourceProvider(ctx, "customResourceProvider", &customproviders.CustomResourceProviderArgs{
			Actions: []customproviders.CustomRPActionRouteDefinitionArgs{
				{
					Endpoint:    pulumi.String("https://mytestendpoint/"),
					Name:        pulumi.String("TestAction"),
					RoutingType: pulumi.String("Proxy"),
				},
			},
			Location:             pulumi.String("eastus"),
			ResourceGroupName:    pulumi.String("testRG"),
			ResourceProviderName: pulumi.String("newrp"),
			ResourceTypes: []customproviders.CustomRPResourceTypeRouteDefinitionArgs{
				{
					Endpoint:    pulumi.String("https://mytestendpoint2/"),
					Name:        pulumi.String("TestResource"),
					RoutingType: pulumi.String("Proxy,Cache"),
				},
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
import com.pulumi.azurenative.customproviders.CustomResourceProvider;
import com.pulumi.azurenative.customproviders.CustomResourceProviderArgs;
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
        var customResourceProvider = new CustomResourceProvider("customResourceProvider", CustomResourceProviderArgs.builder()        
            .actions(Map.ofEntries(
                Map.entry("endpoint", "https://mytestendpoint/"),
                Map.entry("name", "TestAction"),
                Map.entry("routingType", "Proxy")
            ))
            .location("eastus")
            .resourceGroupName("testRG")
            .resourceProviderName("newrp")
            .resourceTypes(Map.ofEntries(
                Map.entry("endpoint", "https://mytestendpoint2/"),
                Map.entry("name", "TestResource"),
                Map.entry("routingType", "Proxy,Cache")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const customResourceProvider = new azure_native.customproviders.CustomResourceProvider("customResourceProvider", {
    actions: [{
        endpoint: "https://mytestendpoint/",
        name: "TestAction",
        routingType: "Proxy",
    }],
    location: "eastus",
    resourceGroupName: "testRG",
    resourceProviderName: "newrp",
    resourceTypes: [{
        endpoint: "https://mytestendpoint2/",
        name: "TestResource",
        routingType: "Proxy,Cache",
    }],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

custom_resource_provider = azure_native.customproviders.CustomResourceProvider("customResourceProvider",
    actions=[azure_native.customproviders.CustomRPActionRouteDefinitionArgs(
        endpoint="https://mytestendpoint/",
        name="TestAction",
        routing_type="Proxy",
    )],
    location="eastus",
    resource_group_name="testRG",
    resource_provider_name="newrp",
    resource_types=[azure_native.customproviders.CustomRPResourceTypeRouteDefinitionArgs(
        endpoint="https://mytestendpoint2/",
        name="TestResource",
        routing_type="Proxy,Cache",
    )])

```

```yaml
resources:
  customResourceProvider:
    type: azure-native:customproviders:CustomResourceProvider
    properties:
      actions:
        - endpoint: https://mytestendpoint/
          name: TestAction
          routingType: Proxy
      location: eastus
      resourceGroupName: testRG
      resourceProviderName: newrp
      resourceTypes:
        - endpoint: https://mytestendpoint2/
          name: TestResource
          routingType: Proxy,Cache

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:customproviders:CustomResourceProvider newrp /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/testRG/providers/Microsoft.CustomProviders/resourceProviders/newrp 
```
