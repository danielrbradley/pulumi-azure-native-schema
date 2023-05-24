Description of a namespace resource.
API Version: 2021-11-01.
Previous API Version: 2017-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### RelayNamespaceCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var @namespace = new AzureNative.Relay.Namespace("namespace", new()
    {
        Location = "South Central US",
        NamespaceName = "example-RelayNamespace-5849",
        ResourceGroupName = "resourcegroup",
        Sku = new AzureNative.Relay.Inputs.SkuArgs
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
	relay "github.com/pulumi/pulumi-azure-native-sdk/relay"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := relay.NewNamespace(ctx, "namespace", &relay.NamespaceArgs{
			Location:          pulumi.String("South Central US"),
			NamespaceName:     pulumi.String("example-RelayNamespace-5849"),
			ResourceGroupName: pulumi.String("resourcegroup"),
			Sku: &relay.SkuArgs{
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
import com.pulumi.azurenative.relay.Namespace;
import com.pulumi.azurenative.relay.NamespaceArgs;
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
            .namespaceName("example-RelayNamespace-5849")
            .resourceGroupName("resourcegroup")
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

const namespace = new azure_native.relay.Namespace("namespace", {
    location: "South Central US",
    namespaceName: "example-RelayNamespace-5849",
    resourceGroupName: "resourcegroup",
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

namespace = azure_native.relay.Namespace("namespace",
    location="South Central US",
    namespace_name="example-RelayNamespace-5849",
    resource_group_name="resourcegroup",
    sku=azure_native.relay.SkuArgs(
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
    type: azure-native:relay:Namespace
    properties:
      location: South Central US
      namespaceName: example-RelayNamespace-5849
      resourceGroupName: resourcegroup
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
$ pulumi import azure-native:relay:Namespace example-RelayNamespace-5849 /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/resourcegroup/providers/Microsoft.Relay/namespaces/example-RelayNamespace-5849 
```
