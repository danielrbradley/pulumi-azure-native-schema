An Log Analytics QueryPack definition.
API Version: 2019-09-01.
Previous API Version: 2019-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### QueryPackCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var queryPack = new AzureNative.OperationalInsights.QueryPack("queryPack", new()
    {
        Location = "South Central US",
        QueryPackName = "my-querypack",
        ResourceGroupName = "my-resource-group",
    });

});


```

```go
package main

import (
	operationalinsights "github.com/pulumi/pulumi-azure-native-sdk/operationalinsights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := operationalinsights.NewQueryPack(ctx, "queryPack", &operationalinsights.QueryPackArgs{
			Location:          pulumi.String("South Central US"),
			QueryPackName:     pulumi.String("my-querypack"),
			ResourceGroupName: pulumi.String("my-resource-group"),
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
import com.pulumi.azurenative.operationalinsights.QueryPack;
import com.pulumi.azurenative.operationalinsights.QueryPackArgs;
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
        var queryPack = new QueryPack("queryPack", QueryPackArgs.builder()        
            .location("South Central US")
            .queryPackName("my-querypack")
            .resourceGroupName("my-resource-group")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const queryPack = new azure_native.operationalinsights.QueryPack("queryPack", {
    location: "South Central US",
    queryPackName: "my-querypack",
    resourceGroupName: "my-resource-group",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

query_pack = azure_native.operationalinsights.QueryPack("queryPack",
    location="South Central US",
    query_pack_name="my-querypack",
    resource_group_name="my-resource-group")

```

```yaml
resources:
  queryPack:
    type: azure-native:operationalinsights:QueryPack
    properties:
      location: South Central US
      queryPackName: my-querypack
      resourceGroupName: my-resource-group

```

{{% /example %}}
{{% example %}}
### QueryPackUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var queryPack = new AzureNative.OperationalInsights.QueryPack("queryPack", new()
    {
        Location = "South Central US",
        QueryPackName = "my-querypack",
        ResourceGroupName = "my-resource-group",
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
	operationalinsights "github.com/pulumi/pulumi-azure-native-sdk/operationalinsights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := operationalinsights.NewQueryPack(ctx, "queryPack", &operationalinsights.QueryPackArgs{
			Location:          pulumi.String("South Central US"),
			QueryPackName:     pulumi.String("my-querypack"),
			ResourceGroupName: pulumi.String("my-resource-group"),
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
import com.pulumi.azurenative.operationalinsights.QueryPack;
import com.pulumi.azurenative.operationalinsights.QueryPackArgs;
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
        var queryPack = new QueryPack("queryPack", QueryPackArgs.builder()        
            .location("South Central US")
            .queryPackName("my-querypack")
            .resourceGroupName("my-resource-group")
            .tags(Map.of("Tag1", "Value1"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const queryPack = new azure_native.operationalinsights.QueryPack("queryPack", {
    location: "South Central US",
    queryPackName: "my-querypack",
    resourceGroupName: "my-resource-group",
    tags: {
        Tag1: "Value1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

query_pack = azure_native.operationalinsights.QueryPack("queryPack",
    location="South Central US",
    query_pack_name="my-querypack",
    resource_group_name="my-resource-group",
    tags={
        "Tag1": "Value1",
    })

```

```yaml
resources:
  queryPack:
    type: azure-native:operationalinsights:QueryPack
    properties:
      location: South Central US
      queryPackName: my-querypack
      resourceGroupName: my-resource-group
      tags:
        Tag1: Value1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:operationalinsights:QueryPack my-querypack /subscriptions/86dc51d3-92ed-4d7e-947a-775ea79b4919/resourceGroups/my-resource-group/providers/microsoft.operationalinsights/queryPacks/my-querypack 
```
