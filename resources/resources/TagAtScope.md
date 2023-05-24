Wrapper resource for tags API requests and responses.
API Version: 2022-09-01.
Previous API Version: 2019-10-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Update tags on a resource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var tagAtScope = new AzureNative.Resources.TagAtScope("tagAtScope", new()
    {
        Properties = new AzureNative.Resources.Inputs.TagsArgs
        {
            Tags = 
            {
                { "tagKey1", "tag-value-1" },
                { "tagKey2", "tag-value-2" },
            },
        },
        Scope = "subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/my-resource-group/providers/myPRNameSpace/VM/myVm",
    });

});


```

```go
package main

import (
	resources "github.com/pulumi/pulumi-azure-native-sdk/resources"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := resources.NewTagAtScope(ctx, "tagAtScope", &resources.TagAtScopeArgs{
			Properties: &resources.TagsArgs{
				Tags: pulumi.StringMap{
					"tagKey1": pulumi.String("tag-value-1"),
					"tagKey2": pulumi.String("tag-value-2"),
				},
			},
			Scope: pulumi.String("subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/my-resource-group/providers/myPRNameSpace/VM/myVm"),
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
import com.pulumi.azurenative.resources.TagAtScope;
import com.pulumi.azurenative.resources.TagAtScopeArgs;
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
        var tagAtScope = new TagAtScope("tagAtScope", TagAtScopeArgs.builder()        
            .properties(Map.of("tags", Map.ofEntries(
                Map.entry("tagKey1", "tag-value-1"),
                Map.entry("tagKey2", "tag-value-2")
            )))
            .scope("subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/my-resource-group/providers/myPRNameSpace/VM/myVm")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const tagAtScope = new azure_native.resources.TagAtScope("tagAtScope", {
    properties: {
        tags: {
            tagKey1: "tag-value-1",
            tagKey2: "tag-value-2",
        },
    },
    scope: "subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/my-resource-group/providers/myPRNameSpace/VM/myVm",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

tag_at_scope = azure_native.resources.TagAtScope("tagAtScope",
    properties=azure_native.resources.TagsArgs(
        tags={
            "tagKey1": "tag-value-1",
            "tagKey2": "tag-value-2",
        },
    ),
    scope="subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/my-resource-group/providers/myPRNameSpace/VM/myVm")

```

```yaml
resources:
  tagAtScope:
    type: azure-native:resources:TagAtScope
    properties:
      properties:
        tags:
          tagKey1: tag-value-1
          tagKey2: tag-value-2
      scope: subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/my-resource-group/providers/myPRNameSpace/VM/myVm

```

{{% /example %}}
{{% example %}}
### Update tags on a subscription
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var tagAtScope = new AzureNative.Resources.TagAtScope("tagAtScope", new()
    {
        Properties = new AzureNative.Resources.Inputs.TagsArgs
        {
            Tags = 
            {
                { "tagKey1", "tag-value-1" },
                { "tagKey2", "tag-value-2" },
            },
        },
        Scope = "subscriptions/00000000-0000-0000-0000-000000000000",
    });

});


```

```go
package main

import (
	resources "github.com/pulumi/pulumi-azure-native-sdk/resources"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := resources.NewTagAtScope(ctx, "tagAtScope", &resources.TagAtScopeArgs{
			Properties: &resources.TagsArgs{
				Tags: pulumi.StringMap{
					"tagKey1": pulumi.String("tag-value-1"),
					"tagKey2": pulumi.String("tag-value-2"),
				},
			},
			Scope: pulumi.String("subscriptions/00000000-0000-0000-0000-000000000000"),
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
import com.pulumi.azurenative.resources.TagAtScope;
import com.pulumi.azurenative.resources.TagAtScopeArgs;
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
        var tagAtScope = new TagAtScope("tagAtScope", TagAtScopeArgs.builder()        
            .properties(Map.of("tags", Map.ofEntries(
                Map.entry("tagKey1", "tag-value-1"),
                Map.entry("tagKey2", "tag-value-2")
            )))
            .scope("subscriptions/00000000-0000-0000-0000-000000000000")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const tagAtScope = new azure_native.resources.TagAtScope("tagAtScope", {
    properties: {
        tags: {
            tagKey1: "tag-value-1",
            tagKey2: "tag-value-2",
        },
    },
    scope: "subscriptions/00000000-0000-0000-0000-000000000000",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

tag_at_scope = azure_native.resources.TagAtScope("tagAtScope",
    properties=azure_native.resources.TagsArgs(
        tags={
            "tagKey1": "tag-value-1",
            "tagKey2": "tag-value-2",
        },
    ),
    scope="subscriptions/00000000-0000-0000-0000-000000000000")

```

```yaml
resources:
  tagAtScope:
    type: azure-native:resources:TagAtScope
    properties:
      properties:
        tags:
          tagKey1: tag-value-1
          tagKey2: tag-value-2
      scope: subscriptions/00000000-0000-0000-0000-000000000000

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:resources:TagAtScope myresource1 subscriptions/00000000-0000-0000-0000-000000000000 
```
