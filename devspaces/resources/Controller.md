
API Version: 2019-04-01.
Previous API Version: 2019-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ControllersCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var controller = new AzureNative.DevSpaces.Controller("controller", new()
    {
        Location = "eastus",
        Name = "myControllerResource",
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.DevSpaces.Inputs.SkuArgs
        {
            Name = "S1",
            Tier = "Standard",
        },
        Tags = null,
        TargetContainerHostCredentialsBase64 = "QmFzZTY0IEVuY29kZWQgVmFsdWUK",
        TargetContainerHostResourceId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.ContainerService/managedClusters/myCluster",
    });

});


```

```go
package main

import (
	devspaces "github.com/pulumi/pulumi-azure-native-sdk/devspaces"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := devspaces.NewController(ctx, "controller", &devspaces.ControllerArgs{
			Location:          pulumi.String("eastus"),
			Name:              pulumi.String("myControllerResource"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			Sku: &devspaces.SkuArgs{
				Name: pulumi.String("S1"),
				Tier: pulumi.String("Standard"),
			},
			Tags:                                 nil,
			TargetContainerHostCredentialsBase64: pulumi.String("QmFzZTY0IEVuY29kZWQgVmFsdWUK"),
			TargetContainerHostResourceId:        pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.ContainerService/managedClusters/myCluster"),
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
import com.pulumi.azurenative.devspaces.Controller;
import com.pulumi.azurenative.devspaces.ControllerArgs;
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
        var controller = new Controller("controller", ControllerArgs.builder()        
            .location("eastus")
            .name("myControllerResource")
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("name", "S1"),
                Map.entry("tier", "Standard")
            ))
            .tags()
            .targetContainerHostCredentialsBase64("QmFzZTY0IEVuY29kZWQgVmFsdWUK")
            .targetContainerHostResourceId("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.ContainerService/managedClusters/myCluster")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const controller = new azure_native.devspaces.Controller("controller", {
    location: "eastus",
    name: "myControllerResource",
    resourceGroupName: "myResourceGroup",
    sku: {
        name: "S1",
        tier: "Standard",
    },
    tags: {},
    targetContainerHostCredentialsBase64: "QmFzZTY0IEVuY29kZWQgVmFsdWUK",
    targetContainerHostResourceId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.ContainerService/managedClusters/myCluster",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

controller = azure_native.devspaces.Controller("controller",
    location="eastus",
    name="myControllerResource",
    resource_group_name="myResourceGroup",
    sku=azure_native.devspaces.SkuArgs(
        name="S1",
        tier="Standard",
    ),
    tags={},
    target_container_host_credentials_base64="QmFzZTY0IEVuY29kZWQgVmFsdWUK",
    target_container_host_resource_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.ContainerService/managedClusters/myCluster")

```

```yaml
resources:
  controller:
    type: azure-native:devspaces:Controller
    properties:
      location: eastus
      name: myControllerResource
      resourceGroupName: myResourceGroup
      sku:
        name: S1
        tier: Standard
      tags: {}
      targetContainerHostCredentialsBase64: QmFzZTY0IEVuY29kZWQgVmFsdWUK
      targetContainerHostResourceId: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.ContainerService/managedClusters/myCluster

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devspaces:Controller myControllerResource /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.DevSpaces/controllers/myControllerResource 
```
