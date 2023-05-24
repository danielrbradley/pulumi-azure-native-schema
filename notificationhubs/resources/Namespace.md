Description of a Namespace resource.
API Version: 2017-04-01.
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
    var @namespace = new AzureNative.NotificationHubs.Namespace("namespace", new()
    {
        Location = "South Central US",
        NamespaceName = "nh-sdk-ns",
        ResourceGroupName = "5ktrial",
        Sku = new AzureNative.NotificationHubs.Inputs.SkuArgs
        {
            Name = "Standard",
            Tier = "Standard",
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
	notificationhubs "github.com/pulumi/pulumi-azure-native-sdk/notificationhubs"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := notificationhubs.NewNamespace(ctx, "namespace", &notificationhubs.NamespaceArgs{
			Location:          pulumi.String("South Central US"),
			NamespaceName:     pulumi.String("nh-sdk-ns"),
			ResourceGroupName: pulumi.String("5ktrial"),
			Sku: &notificationhubs.SkuArgs{
				Name: pulumi.String("Standard"),
				Tier: pulumi.String("Standard"),
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
import com.pulumi.azurenative.notificationhubs.Namespace;
import com.pulumi.azurenative.notificationhubs.NamespaceArgs;
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
            .namespaceName("nh-sdk-ns")
            .resourceGroupName("5ktrial")
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

const namespace = new azure_native.notificationhubs.Namespace("namespace", {
    location: "South Central US",
    namespaceName: "nh-sdk-ns",
    resourceGroupName: "5ktrial",
    sku: {
        name: "Standard",
        tier: "Standard",
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

namespace = azure_native.notificationhubs.Namespace("namespace",
    location="South Central US",
    namespace_name="nh-sdk-ns",
    resource_group_name="5ktrial",
    sku=azure_native.notificationhubs.SkuArgs(
        name="Standard",
        tier="Standard",
    ),
    tags={
        "tag1": "value1",
        "tag2": "value2",
    })

```

```yaml
resources:
  namespace:
    type: azure-native:notificationhubs:Namespace
    properties:
      location: South Central US
      namespaceName: nh-sdk-ns
      resourceGroupName: 5ktrial
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
$ pulumi import azure-native:notificationhubs:Namespace sdk-Namespace-2924 /subscriptions/29cfa613-cbbc-4512-b1d6-1b3a92c7fa40/resourceGroups/ArunMonocle/providers/Microsoft.NotificationHubs/namespaces/sdk-Namespace-2924 
```
