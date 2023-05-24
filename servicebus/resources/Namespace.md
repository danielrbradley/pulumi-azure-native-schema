Description of a namespace resource.
API Version: 2021-11-01.
Previous API Version: 2017-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### NameSpaceCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var @namespace = new AzureNative.ServiceBus.Namespace("namespace", new()
    {
        Location = "South Central US",
        NamespaceName = "sdk-Namespace2924",
        ResourceGroupName = "ArunMonocle",
        Sku = new AzureNative.ServiceBus.Inputs.SBSkuArgs
        {
            Name = AzureNative.ServiceBus.SkuName.Standard,
            Tier = AzureNative.ServiceBus.SkuTier.Standard,
        },
        Tags = 
        {
            { "tag1", "value1" },
            { "tag2", "value2" },
        },
    });

});


```

```go
package main

import (
	servicebus "github.com/pulumi/pulumi-azure-native-sdk/servicebus"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := servicebus.NewNamespace(ctx, "namespace", &servicebus.NamespaceArgs{
			Location:          pulumi.String("South Central US"),
			NamespaceName:     pulumi.String("sdk-Namespace2924"),
			ResourceGroupName: pulumi.String("ArunMonocle"),
			Sku: &servicebus.SBSkuArgs{
				Name: servicebus.SkuNameStandard,
				Tier: servicebus.SkuTierStandard,
			},
			Tags: pulumi.StringMap{
				"tag1": pulumi.String("value1"),
				"tag2": pulumi.String("value2"),
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
import com.pulumi.azurenative.servicebus.Namespace;
import com.pulumi.azurenative.servicebus.NamespaceArgs;
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
        var namespace = new Namespace("namespace", NamespaceArgs.builder()        
            .location("South Central US")
            .namespaceName("sdk-Namespace2924")
            .resourceGroupName("ArunMonocle")
            .sku(Map.ofEntries(
                Map.entry("name", "Standard"),
                Map.entry("tier", "Standard")
            ))
            .tags(Map.ofEntries(
                Map.entry("tag1", "value1"),
                Map.entry("tag2", "value2")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const namespace = new azure_native.servicebus.Namespace("namespace", {
    location: "South Central US",
    namespaceName: "sdk-Namespace2924",
    resourceGroupName: "ArunMonocle",
    sku: {
        name: azure_native.servicebus.SkuName.Standard,
        tier: azure_native.servicebus.SkuTier.Standard,
    },
    tags: {
        tag1: "value1",
        tag2: "value2",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

namespace = azure_native.servicebus.Namespace("namespace",
    location="South Central US",
    namespace_name="sdk-Namespace2924",
    resource_group_name="ArunMonocle",
    sku=azure_native.servicebus.SBSkuArgs(
        name=azure_native.servicebus.SkuName.STANDARD,
        tier=azure_native.servicebus.SkuTier.STANDARD,
    ),
    tags={
        "tag1": "value1",
        "tag2": "value2",
    })

```

```yaml
resources:
  namespace:
    type: azure-native:servicebus:Namespace
    properties:
      location: South Central US
      namespaceName: sdk-Namespace2924
      resourceGroupName: ArunMonocle
      sku:
        name: Standard
        tier: Standard
      tags:
        tag1: value1
        tag2: value2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:servicebus:Namespace sdk-Namespace-2924 /subscriptions/5f750a97-50d9-4e36-8081-c9ee4c0210d4/resourceGroups/ArunMonocle/providers/Microsoft.ServiceBus/namespaces/sdk-Namespace-2924 
```
