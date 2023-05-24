disk access resource.
API Version: 2022-07-02.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a disk access resource.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var diskAccess = new AzureNative.Compute.DiskAccess("diskAccess", new()
    {
        DiskAccessName = "myDiskAccess",
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
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
		_, err := compute.NewDiskAccess(ctx, "diskAccess", &compute.DiskAccessArgs{
			DiskAccessName:    pulumi.String("myDiskAccess"),
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.compute.DiskAccess;
import com.pulumi.azurenative.compute.DiskAccessArgs;
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
        var diskAccess = new DiskAccess("diskAccess", DiskAccessArgs.builder()        
            .diskAccessName("myDiskAccess")
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const diskAccess = new azure_native.compute.DiskAccess("diskAccess", {
    diskAccessName: "myDiskAccess",
    location: "West US",
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

disk_access = azure_native.compute.DiskAccess("diskAccess",
    disk_access_name="myDiskAccess",
    location="West US",
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  diskAccess:
    type: azure-native:compute:DiskAccess
    properties:
      diskAccessName: myDiskAccess
      location: West US
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:compute:DiskAccess myDiskAccess /subscriptions/{subscription-id}/resourceGroups/myResourcegroup/providers/Microsoft.Compute/diskAccesses/myDiskAccess 
```
