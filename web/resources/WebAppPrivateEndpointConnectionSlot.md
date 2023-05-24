Remote Private Endpoint Connection ARM resource.
API Version: 2022-09-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Approves or rejects a private endpoint connection for a site.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var webAppPrivateEndpointConnectionSlot = new AzureNative.Web.WebAppPrivateEndpointConnectionSlot("webAppPrivateEndpointConnectionSlot", new()
    {
        Name = "testSite",
        PrivateEndpointConnectionName = "connection",
        PrivateLinkServiceConnectionState = new AzureNative.Web.Inputs.PrivateLinkConnectionStateArgs
        {
            ActionsRequired = "",
            Description = "Approved by admin.",
            Status = "Approved",
        },
        ResourceGroupName = "rg",
        Slot = "stage",
    });

});


```

```go
package main

import (
	web "github.com/pulumi/pulumi-azure-native-sdk/web"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := web.NewWebAppPrivateEndpointConnectionSlot(ctx, "webAppPrivateEndpointConnectionSlot", &web.WebAppPrivateEndpointConnectionSlotArgs{
			Name:                          pulumi.String("testSite"),
			PrivateEndpointConnectionName: pulumi.String("connection"),
			PrivateLinkServiceConnectionState: &web.PrivateLinkConnectionStateArgs{
				ActionsRequired: pulumi.String(""),
				Description:     pulumi.String("Approved by admin."),
				Status:          pulumi.String("Approved"),
			},
			ResourceGroupName: pulumi.String("rg"),
			Slot:              pulumi.String("stage"),
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
import com.pulumi.azurenative.web.WebAppPrivateEndpointConnectionSlot;
import com.pulumi.azurenative.web.WebAppPrivateEndpointConnectionSlotArgs;
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
        var webAppPrivateEndpointConnectionSlot = new WebAppPrivateEndpointConnectionSlot("webAppPrivateEndpointConnectionSlot", WebAppPrivateEndpointConnectionSlotArgs.builder()        
            .name("testSite")
            .privateEndpointConnectionName("connection")
            .privateLinkServiceConnectionState(Map.ofEntries(
                Map.entry("actionsRequired", ""),
                Map.entry("description", "Approved by admin."),
                Map.entry("status", "Approved")
            ))
            .resourceGroupName("rg")
            .slot("stage")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const webAppPrivateEndpointConnectionSlot = new azure_native.web.WebAppPrivateEndpointConnectionSlot("webAppPrivateEndpointConnectionSlot", {
    name: "testSite",
    privateEndpointConnectionName: "connection",
    privateLinkServiceConnectionState: {
        actionsRequired: "",
        description: "Approved by admin.",
        status: "Approved",
    },
    resourceGroupName: "rg",
    slot: "stage",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

web_app_private_endpoint_connection_slot = azure_native.web.WebAppPrivateEndpointConnectionSlot("webAppPrivateEndpointConnectionSlot",
    name="testSite",
    private_endpoint_connection_name="connection",
    private_link_service_connection_state=azure_native.web.PrivateLinkConnectionStateArgs(
        actions_required="",
        description="Approved by admin.",
        status="Approved",
    ),
    resource_group_name="rg",
    slot="stage")

```

```yaml
resources:
  webAppPrivateEndpointConnectionSlot:
    type: azure-native:web:WebAppPrivateEndpointConnectionSlot
    properties:
      name: testSite
      privateEndpointConnectionName: connection
      privateLinkServiceConnectionState:
        actionsRequired:
        description: Approved by admin.
        status: Approved
      resourceGroupName: rg
      slot: stage

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:web:WebAppPrivateEndpointConnectionSlot myresource1 /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/rg/providers/Microsoft.Web/sites/testSite/slots/stage/privateEndpointConnections/connection 
```
