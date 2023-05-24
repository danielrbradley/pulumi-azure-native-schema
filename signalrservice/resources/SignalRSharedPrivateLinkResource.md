Describes a Shared Private Link Resource
API Version: 2023-02-01.
Previous API Version: 2021-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### SignalRSharedPrivateLinkResources_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var signalRSharedPrivateLinkResource = new AzureNative.SignalRService.SignalRSharedPrivateLinkResource("signalRSharedPrivateLinkResource", new()
    {
        GroupId = "sites",
        PrivateLinkResourceId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.Web/sites/myWebApp",
        RequestMessage = "Please approve",
        ResourceGroupName = "myResourceGroup",
        ResourceName = "mySignalRService",
        SharedPrivateLinkResourceName = "upstream",
    });

});


```

```go
package main

import (
	signalrservice "github.com/pulumi/pulumi-azure-native-sdk/signalrservice"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := signalrservice.NewSignalRSharedPrivateLinkResource(ctx, "signalRSharedPrivateLinkResource", &signalrservice.SignalRSharedPrivateLinkResourceArgs{
			GroupId:                       pulumi.String("sites"),
			PrivateLinkResourceId:         pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.Web/sites/myWebApp"),
			RequestMessage:                pulumi.String("Please approve"),
			ResourceGroupName:             pulumi.String("myResourceGroup"),
			ResourceName:                  pulumi.String("mySignalRService"),
			SharedPrivateLinkResourceName: pulumi.String("upstream"),
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
import com.pulumi.azurenative.signalrservice.SignalRSharedPrivateLinkResource;
import com.pulumi.azurenative.signalrservice.SignalRSharedPrivateLinkResourceArgs;
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
        var signalRSharedPrivateLinkResource = new SignalRSharedPrivateLinkResource("signalRSharedPrivateLinkResource", SignalRSharedPrivateLinkResourceArgs.builder()        
            .groupId("sites")
            .privateLinkResourceId("/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.Web/sites/myWebApp")
            .requestMessage("Please approve")
            .resourceGroupName("myResourceGroup")
            .resourceName("mySignalRService")
            .sharedPrivateLinkResourceName("upstream")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const signalRSharedPrivateLinkResource = new azure_native.signalrservice.SignalRSharedPrivateLinkResource("signalRSharedPrivateLinkResource", {
    groupId: "sites",
    privateLinkResourceId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.Web/sites/myWebApp",
    requestMessage: "Please approve",
    resourceGroupName: "myResourceGroup",
    resourceName: "mySignalRService",
    sharedPrivateLinkResourceName: "upstream",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

signal_r_shared_private_link_resource = azure_native.signalrservice.SignalRSharedPrivateLinkResource("signalRSharedPrivateLinkResource",
    group_id="sites",
    private_link_resource_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.Web/sites/myWebApp",
    request_message="Please approve",
    resource_group_name="myResourceGroup",
    resource_name_="mySignalRService",
    shared_private_link_resource_name="upstream")

```

```yaml
resources:
  signalRSharedPrivateLinkResource:
    type: azure-native:signalrservice:SignalRSharedPrivateLinkResource
    properties:
      groupId: sites
      privateLinkResourceId: /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.Web/sites/myWebApp
      requestMessage: Please approve
      resourceGroupName: myResourceGroup
      resourceName: mySignalRService
      sharedPrivateLinkResourceName: upstream

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:signalrservice:SignalRSharedPrivateLinkResource upstream /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.SignalRService/SignalR/mySignalRService/privateEndpointConnections/upstream 
```
