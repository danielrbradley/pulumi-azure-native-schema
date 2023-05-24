Managed private endpoint resource type.
API Version: 2018-06-01.
Previous API Version: 2018-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ManagedVirtualNetworks_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedPrivateEndpoint = new AzureNative.DataFactory.ManagedPrivateEndpoint("managedPrivateEndpoint", new()
    {
        FactoryName = "exampleFactoryName",
        ManagedPrivateEndpointName = "exampleManagedPrivateEndpointName",
        ManagedVirtualNetworkName = "exampleManagedVirtualNetworkName",
        Properties = new AzureNative.DataFactory.Inputs.ManagedPrivateEndpointArgs
        {
            Fqdns = new[] {},
            GroupId = "blob",
            PrivateLinkResourceId = "/subscriptions/12345678-1234-1234-1234-12345678abc/resourceGroups/exampleResourceGroup/providers/Microsoft.Storage/storageAccounts/exampleBlobStorage",
        },
        ResourceGroupName = "exampleResourceGroup",
    });

});


```

```go
package main

import (
	datafactory "github.com/pulumi/pulumi-azure-native-sdk/datafactory"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := datafactory.NewManagedPrivateEndpoint(ctx, "managedPrivateEndpoint", &datafactory.ManagedPrivateEndpointArgs{
			FactoryName:                pulumi.String("exampleFactoryName"),
			ManagedPrivateEndpointName: pulumi.String("exampleManagedPrivateEndpointName"),
			ManagedVirtualNetworkName:  pulumi.String("exampleManagedVirtualNetworkName"),
			Properties: &datafactory.ManagedPrivateEndpointTypeArgs{
				Fqdns:                 pulumi.StringArray{},
				GroupId:               pulumi.String("blob"),
				PrivateLinkResourceId: pulumi.String("/subscriptions/12345678-1234-1234-1234-12345678abc/resourceGroups/exampleResourceGroup/providers/Microsoft.Storage/storageAccounts/exampleBlobStorage"),
			},
			ResourceGroupName: pulumi.String("exampleResourceGroup"),
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
import com.pulumi.azurenative.datafactory.ManagedPrivateEndpoint;
import com.pulumi.azurenative.datafactory.ManagedPrivateEndpointArgs;
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
        var managedPrivateEndpoint = new ManagedPrivateEndpoint("managedPrivateEndpoint", ManagedPrivateEndpointArgs.builder()        
            .factoryName("exampleFactoryName")
            .managedPrivateEndpointName("exampleManagedPrivateEndpointName")
            .managedVirtualNetworkName("exampleManagedVirtualNetworkName")
            .properties(Map.ofEntries(
                Map.entry("fqdns", ),
                Map.entry("groupId", "blob"),
                Map.entry("privateLinkResourceId", "/subscriptions/12345678-1234-1234-1234-12345678abc/resourceGroups/exampleResourceGroup/providers/Microsoft.Storage/storageAccounts/exampleBlobStorage")
            ))
            .resourceGroupName("exampleResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedPrivateEndpoint = new azure_native.datafactory.ManagedPrivateEndpoint("managedPrivateEndpoint", {
    factoryName: "exampleFactoryName",
    managedPrivateEndpointName: "exampleManagedPrivateEndpointName",
    managedVirtualNetworkName: "exampleManagedVirtualNetworkName",
    properties: {
        fqdns: [],
        groupId: "blob",
        privateLinkResourceId: "/subscriptions/12345678-1234-1234-1234-12345678abc/resourceGroups/exampleResourceGroup/providers/Microsoft.Storage/storageAccounts/exampleBlobStorage",
    },
    resourceGroupName: "exampleResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_private_endpoint = azure_native.datafactory.ManagedPrivateEndpoint("managedPrivateEndpoint",
    factory_name="exampleFactoryName",
    managed_private_endpoint_name="exampleManagedPrivateEndpointName",
    managed_virtual_network_name="exampleManagedVirtualNetworkName",
    properties=azure_native.datafactory.ManagedPrivateEndpointArgs(
        fqdns=[],
        group_id="blob",
        private_link_resource_id="/subscriptions/12345678-1234-1234-1234-12345678abc/resourceGroups/exampleResourceGroup/providers/Microsoft.Storage/storageAccounts/exampleBlobStorage",
    ),
    resource_group_name="exampleResourceGroup")

```

```yaml
resources:
  managedPrivateEndpoint:
    type: azure-native:datafactory:ManagedPrivateEndpoint
    properties:
      factoryName: exampleFactoryName
      managedPrivateEndpointName: exampleManagedPrivateEndpointName
      managedVirtualNetworkName: exampleManagedVirtualNetworkName
      properties:
        fqdns: []
        groupId: blob
        privateLinkResourceId: /subscriptions/12345678-1234-1234-1234-12345678abc/resourceGroups/exampleResourceGroup/providers/Microsoft.Storage/storageAccounts/exampleBlobStorage
      resourceGroupName: exampleResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:datafactory:ManagedPrivateEndpoint exampleManagedPrivateEndpointName /subscriptions/12345678-1234-1234-1234-12345678abc/resourceGroups/exampleResourceGroup/providers/Microsoft.DataFactory/factories/exampleFactoryName/managedVirtualNetworks/exampleManagedVirtualNetworkName/managedPrivateEndpoints/exampleManagedPrivateEndpointName 
```
