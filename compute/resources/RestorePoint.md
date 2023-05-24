Restore Point details.
API Version: 2022-11-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Copy a restore point to a different region
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var restorePoint = new AzureNative.Compute.RestorePoint("restorePoint", new()
    {
        ResourceGroupName = "myResourceGroup",
        RestorePointCollectionName = "rpcName",
        RestorePointName = "rpName",
        SourceRestorePoint = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
        {
            Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/restorePointCollections/sourceRpcName/restorePoints/sourceRpName",
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
		_, err := compute.NewRestorePoint(ctx, "restorePoint", &compute.RestorePointArgs{
			ResourceGroupName:          pulumi.String("myResourceGroup"),
			RestorePointCollectionName: pulumi.String("rpcName"),
			RestorePointName:           pulumi.String("rpName"),
			SourceRestorePoint: &compute.ApiEntityReferenceArgs{
				Id: pulumi.String("/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/restorePointCollections/sourceRpcName/restorePoints/sourceRpName"),
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
import com.pulumi.azurenative.compute.RestorePoint;
import com.pulumi.azurenative.compute.RestorePointArgs;
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
        var restorePoint = new RestorePoint("restorePoint", RestorePointArgs.builder()        
            .resourceGroupName("myResourceGroup")
            .restorePointCollectionName("rpcName")
            .restorePointName("rpName")
            .sourceRestorePoint(Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/restorePointCollections/sourceRpcName/restorePoints/sourceRpName"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const restorePoint = new azure_native.compute.RestorePoint("restorePoint", {
    resourceGroupName: "myResourceGroup",
    restorePointCollectionName: "rpcName",
    restorePointName: "rpName",
    sourceRestorePoint: {
        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/restorePointCollections/sourceRpcName/restorePoints/sourceRpName",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

restore_point = azure_native.compute.RestorePoint("restorePoint",
    resource_group_name="myResourceGroup",
    restore_point_collection_name="rpcName",
    restore_point_name="rpName",
    source_restore_point=azure_native.compute.ApiEntityReferenceArgs(
        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/restorePointCollections/sourceRpcName/restorePoints/sourceRpName",
    ))

```

```yaml
resources:
  restorePoint:
    type: azure-native:compute:RestorePoint
    properties:
      resourceGroupName: myResourceGroup
      restorePointCollectionName: rpcName
      restorePointName: rpName
      sourceRestorePoint:
        id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/restorePointCollections/sourceRpcName/restorePoints/sourceRpName

```

{{% /example %}}
{{% example %}}
### Create a restore point
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var restorePoint = new AzureNative.Compute.RestorePoint("restorePoint", new()
    {
        ExcludeDisks = new[]
        {
            new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
            {
                Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/disk123",
            },
        },
        ResourceGroupName = "myResourceGroup",
        RestorePointCollectionName = "rpcName",
        RestorePointName = "rpName",
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
		_, err := compute.NewRestorePoint(ctx, "restorePoint", &compute.RestorePointArgs{
			ExcludeDisks: []compute.ApiEntityReferenceArgs{
				{
					Id: pulumi.String("/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/disk123"),
				},
			},
			ResourceGroupName:          pulumi.String("myResourceGroup"),
			RestorePointCollectionName: pulumi.String("rpcName"),
			RestorePointName:           pulumi.String("rpName"),
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
import com.pulumi.azurenative.compute.RestorePoint;
import com.pulumi.azurenative.compute.RestorePointArgs;
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
        var restorePoint = new RestorePoint("restorePoint", RestorePointArgs.builder()        
            .excludeDisks(Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/disk123"))
            .resourceGroupName("myResourceGroup")
            .restorePointCollectionName("rpcName")
            .restorePointName("rpName")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const restorePoint = new azure_native.compute.RestorePoint("restorePoint", {
    excludeDisks: [{
        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/disk123",
    }],
    resourceGroupName: "myResourceGroup",
    restorePointCollectionName: "rpcName",
    restorePointName: "rpName",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

restore_point = azure_native.compute.RestorePoint("restorePoint",
    exclude_disks=[azure_native.compute.ApiEntityReferenceArgs(
        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/disk123",
    )],
    resource_group_name="myResourceGroup",
    restore_point_collection_name="rpcName",
    restore_point_name="rpName")

```

```yaml
resources:
  restorePoint:
    type: azure-native:compute:RestorePoint
    properties:
      excludeDisks:
        - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/disk123
      resourceGroupName: myResourceGroup
      restorePointCollectionName: rpcName
      restorePointName: rpName

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:compute:RestorePoint rpName /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/restorePointCollections/rpcName/restorePoints/rpName 
```
