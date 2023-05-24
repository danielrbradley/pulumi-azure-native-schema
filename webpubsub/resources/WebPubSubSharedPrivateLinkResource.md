Describes a Shared Private Link Resource
API Version: 2023-02-01.
Previous API Version: 2021-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### WebPubSubSharedPrivateLinkResources_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var webPubSubSharedPrivateLinkResource = new AzureNative.WebPubSub.WebPubSubSharedPrivateLinkResource("webPubSubSharedPrivateLinkResource", new()
    {
        GroupId = "sites",
        PrivateLinkResourceId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.Web/sites/myWebApp",
        RequestMessage = "Please approve",
        ResourceGroupName = "myResourceGroup",
        ResourceName = "myWebPubSubService",
        SharedPrivateLinkResourceName = "upstream",
    });

});


```

```go
package main

import (
	webpubsub "github.com/pulumi/pulumi-azure-native-sdk/webpubsub"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := webpubsub.NewWebPubSubSharedPrivateLinkResource(ctx, "webPubSubSharedPrivateLinkResource", &webpubsub.WebPubSubSharedPrivateLinkResourceArgs{
			GroupId:                       pulumi.String("sites"),
			PrivateLinkResourceId:         pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.Web/sites/myWebApp"),
			RequestMessage:                pulumi.String("Please approve"),
			ResourceGroupName:             pulumi.String("myResourceGroup"),
			ResourceName:                  pulumi.String("myWebPubSubService"),
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
import com.pulumi.azurenative.webpubsub.WebPubSubSharedPrivateLinkResource;
import com.pulumi.azurenative.webpubsub.WebPubSubSharedPrivateLinkResourceArgs;
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
        var webPubSubSharedPrivateLinkResource = new WebPubSubSharedPrivateLinkResource("webPubSubSharedPrivateLinkResource", WebPubSubSharedPrivateLinkResourceArgs.builder()        
            .groupId("sites")
            .privateLinkResourceId("/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.Web/sites/myWebApp")
            .requestMessage("Please approve")
            .resourceGroupName("myResourceGroup")
            .resourceName("myWebPubSubService")
            .sharedPrivateLinkResourceName("upstream")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const webPubSubSharedPrivateLinkResource = new azure_native.webpubsub.WebPubSubSharedPrivateLinkResource("webPubSubSharedPrivateLinkResource", {
    groupId: "sites",
    privateLinkResourceId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.Web/sites/myWebApp",
    requestMessage: "Please approve",
    resourceGroupName: "myResourceGroup",
    resourceName: "myWebPubSubService",
    sharedPrivateLinkResourceName: "upstream",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

web_pub_sub_shared_private_link_resource = azure_native.webpubsub.WebPubSubSharedPrivateLinkResource("webPubSubSharedPrivateLinkResource",
    group_id="sites",
    private_link_resource_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.Web/sites/myWebApp",
    request_message="Please approve",
    resource_group_name="myResourceGroup",
    resource_name_="myWebPubSubService",
    shared_private_link_resource_name="upstream")

```

```yaml
resources:
  webPubSubSharedPrivateLinkResource:
    type: azure-native:webpubsub:WebPubSubSharedPrivateLinkResource
    properties:
      groupId: sites
      privateLinkResourceId: /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.Web/sites/myWebApp
      requestMessage: Please approve
      resourceGroupName: myResourceGroup
      resourceName: myWebPubSubService
      sharedPrivateLinkResourceName: upstream

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:webpubsub:WebPubSubSharedPrivateLinkResource upstream /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/myResourceGroup/providers/Microsoft.SignalRService/WebPubSub/myWebPubSubService/privateEndpointConnections/upstream 
```
