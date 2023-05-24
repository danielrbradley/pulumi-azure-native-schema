An Azure Arc PrivateLinkScope definition.
API Version: 2022-11-10.
Previous API Version: 2021-03-25-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PrivateLinkScopeCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateLinkScope = new AzureNative.HybridCompute.PrivateLinkScope("privateLinkScope", new()
    {
        Location = "westus",
        ResourceGroupName = "my-resource-group",
        ScopeName = "my-privatelinkscope",
    });

});


```

```go
package main

import (
	hybridcompute "github.com/pulumi/pulumi-azure-native-sdk/hybridcompute"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := hybridcompute.NewPrivateLinkScope(ctx, "privateLinkScope", &hybridcompute.PrivateLinkScopeArgs{
			Location:          pulumi.String("westus"),
			ResourceGroupName: pulumi.String("my-resource-group"),
			ScopeName:         pulumi.String("my-privatelinkscope"),
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
import com.pulumi.azurenative.hybridcompute.PrivateLinkScope;
import com.pulumi.azurenative.hybridcompute.PrivateLinkScopeArgs;
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
        var privateLinkScope = new PrivateLinkScope("privateLinkScope", PrivateLinkScopeArgs.builder()        
            .location("westus")
            .resourceGroupName("my-resource-group")
            .scopeName("my-privatelinkscope")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateLinkScope = new azure_native.hybridcompute.PrivateLinkScope("privateLinkScope", {
    location: "westus",
    resourceGroupName: "my-resource-group",
    scopeName: "my-privatelinkscope",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_link_scope = azure_native.hybridcompute.PrivateLinkScope("privateLinkScope",
    location="westus",
    resource_group_name="my-resource-group",
    scope_name="my-privatelinkscope")

```

```yaml
resources:
  privateLinkScope:
    type: azure-native:hybridcompute:PrivateLinkScope
    properties:
      location: westus
      resourceGroupName: my-resource-group
      scopeName: my-privatelinkscope

```

{{% /example %}}
{{% example %}}
### PrivateLinkScopeUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateLinkScope = new AzureNative.HybridCompute.PrivateLinkScope("privateLinkScope", new()
    {
        Location = "westus",
        ResourceGroupName = "my-resource-group",
        ScopeName = "my-privatelinkscope",
        Tags = 
        {
            { "Tag1", "Value1" },
        },
    });

});


```

```go
package main

import (
	hybridcompute "github.com/pulumi/pulumi-azure-native-sdk/hybridcompute"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := hybridcompute.NewPrivateLinkScope(ctx, "privateLinkScope", &hybridcompute.PrivateLinkScopeArgs{
			Location:          pulumi.String("westus"),
			ResourceGroupName: pulumi.String("my-resource-group"),
			ScopeName:         pulumi.String("my-privatelinkscope"),
			Tags: pulumi.StringMap{
				"Tag1": pulumi.String("Value1"),
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
import com.pulumi.azurenative.hybridcompute.PrivateLinkScope;
import com.pulumi.azurenative.hybridcompute.PrivateLinkScopeArgs;
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
        var privateLinkScope = new PrivateLinkScope("privateLinkScope", PrivateLinkScopeArgs.builder()        
            .location("westus")
            .resourceGroupName("my-resource-group")
            .scopeName("my-privatelinkscope")
            .tags(Map.of("Tag1", "Value1"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateLinkScope = new azure_native.hybridcompute.PrivateLinkScope("privateLinkScope", {
    location: "westus",
    resourceGroupName: "my-resource-group",
    scopeName: "my-privatelinkscope",
    tags: {
        Tag1: "Value1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_link_scope = azure_native.hybridcompute.PrivateLinkScope("privateLinkScope",
    location="westus",
    resource_group_name="my-resource-group",
    scope_name="my-privatelinkscope",
    tags={
        "Tag1": "Value1",
    })

```

```yaml
resources:
  privateLinkScope:
    type: azure-native:hybridcompute:PrivateLinkScope
    properties:
      location: westus
      resourceGroupName: my-resource-group
      scopeName: my-privatelinkscope
      tags:
        Tag1: Value1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:hybridcompute:PrivateLinkScope my-privatelinkscope /subscriptions/86dc51d3-92ed-4d7e-947a-775ea79b4919/resourceGroups/my-resource-group/providers/microsoft.hybridCompute/privateLinkScopes/my-privatelinkscope 
```
