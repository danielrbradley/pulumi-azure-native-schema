Create or update Restore Point collection parameters.
API Version: 2022-11-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a restore point collection for cross region copy.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var restorePointCollection = new AzureNative.Compute.RestorePointCollection("restorePointCollection", new()
    {
        Location = "norwayeast",
        ResourceGroupName = "myResourceGroup",
        RestorePointCollectionName = "myRpc",
        Source = new AzureNative.Compute.Inputs.RestorePointCollectionSourcePropertiesArgs
        {
            Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/restorePointCollections/sourceRpcName",
        },
        Tags = 
        {
            { "myTag1", "tagValue1" },
        },
    });

});


```

```go
package main

import (
	compute "github.com/pulumi/pulumi-azure-native-sdk/compute"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := compute.NewRestorePointCollection(ctx, "restorePointCollection", &compute.RestorePointCollectionArgs{
			Location:                   pulumi.String("norwayeast"),
			ResourceGroupName:          pulumi.String("myResourceGroup"),
			RestorePointCollectionName: pulumi.String("myRpc"),
			Source: &compute.RestorePointCollectionSourcePropertiesArgs{
				Id: pulumi.String("/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/restorePointCollections/sourceRpcName"),
			},
			Tags: pulumi.StringMap{
				"myTag1": pulumi.String("tagValue1"),
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
import com.pulumi.azurenative.compute.RestorePointCollection;
import com.pulumi.azurenative.compute.RestorePointCollectionArgs;
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
        var restorePointCollection = new RestorePointCollection("restorePointCollection", RestorePointCollectionArgs.builder()        
            .location("norwayeast")
            .resourceGroupName("myResourceGroup")
            .restorePointCollectionName("myRpc")
            .source(Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/restorePointCollections/sourceRpcName"))
            .tags(Map.of("myTag1", "tagValue1"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const restorePointCollection = new azure_native.compute.RestorePointCollection("restorePointCollection", {
    location: "norwayeast",
    resourceGroupName: "myResourceGroup",
    restorePointCollectionName: "myRpc",
    source: {
        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/restorePointCollections/sourceRpcName",
    },
    tags: {
        myTag1: "tagValue1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

restore_point_collection = azure_native.compute.RestorePointCollection("restorePointCollection",
    location="norwayeast",
    resource_group_name="myResourceGroup",
    restore_point_collection_name="myRpc",
    source=azure_native.compute.RestorePointCollectionSourcePropertiesArgs(
        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/restorePointCollections/sourceRpcName",
    ),
    tags={
        "myTag1": "tagValue1",
    })

```

```yaml
resources:
  restorePointCollection:
    type: azure-native:compute:RestorePointCollection
    properties:
      location: norwayeast
      resourceGroupName: myResourceGroup
      restorePointCollectionName: myRpc
      source:
        id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/restorePointCollections/sourceRpcName
      tags:
        myTag1: tagValue1

```

{{% /example %}}
{{% example %}}
### Create or update a restore point collection.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var restorePointCollection = new AzureNative.Compute.RestorePointCollection("restorePointCollection", new()
    {
        Location = "norwayeast",
        ResourceGroupName = "myResourceGroup",
        RestorePointCollectionName = "myRpc",
        Source = new AzureNative.Compute.Inputs.RestorePointCollectionSourcePropertiesArgs
        {
            Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/virtualMachines/myVM",
        },
        Tags = 
        {
            { "myTag1", "tagValue1" },
        },
    });

});


```

```go
package main

import (
	compute "github.com/pulumi/pulumi-azure-native-sdk/compute"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := compute.NewRestorePointCollection(ctx, "restorePointCollection", &compute.RestorePointCollectionArgs{
			Location:                   pulumi.String("norwayeast"),
			ResourceGroupName:          pulumi.String("myResourceGroup"),
			RestorePointCollectionName: pulumi.String("myRpc"),
			Source: &compute.RestorePointCollectionSourcePropertiesArgs{
				Id: pulumi.String("/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/virtualMachines/myVM"),
			},
			Tags: pulumi.StringMap{
				"myTag1": pulumi.String("tagValue1"),
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
import com.pulumi.azurenative.compute.RestorePointCollection;
import com.pulumi.azurenative.compute.RestorePointCollectionArgs;
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
        var restorePointCollection = new RestorePointCollection("restorePointCollection", RestorePointCollectionArgs.builder()        
            .location("norwayeast")
            .resourceGroupName("myResourceGroup")
            .restorePointCollectionName("myRpc")
            .source(Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/virtualMachines/myVM"))
            .tags(Map.of("myTag1", "tagValue1"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const restorePointCollection = new azure_native.compute.RestorePointCollection("restorePointCollection", {
    location: "norwayeast",
    resourceGroupName: "myResourceGroup",
    restorePointCollectionName: "myRpc",
    source: {
        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/virtualMachines/myVM",
    },
    tags: {
        myTag1: "tagValue1",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

restore_point_collection = azure_native.compute.RestorePointCollection("restorePointCollection",
    location="norwayeast",
    resource_group_name="myResourceGroup",
    restore_point_collection_name="myRpc",
    source=azure_native.compute.RestorePointCollectionSourcePropertiesArgs(
        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/virtualMachines/myVM",
    ),
    tags={
        "myTag1": "tagValue1",
    })

```

```yaml
resources:
  restorePointCollection:
    type: azure-native:compute:RestorePointCollection
    properties:
      location: norwayeast
      resourceGroupName: myResourceGroup
      restorePointCollectionName: myRpc
      source:
        id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/virtualMachines/myVM
      tags:
        myTag1: tagValue1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:compute:RestorePointCollection myRpc /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/restorePointCollections/myRpc 
```
