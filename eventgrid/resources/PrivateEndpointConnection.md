
API Version: 2022-06-15.
Previous API Version: 2020-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PrivateEndpointConnections_Update
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnection = new AzureNative.EventGrid.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        ParentName = "exampletopic1",
        ParentType = "topics",
        PrivateEndpointConnectionName = "BMTPE5.8A30D251-4C61-489D-A1AA-B37C4A329B8B",
        PrivateLinkServiceConnectionState = new AzureNative.EventGrid.Inputs.ConnectionStateArgs
        {
            ActionsRequired = "None",
            Description = "approving connection",
            Status = "Approved",
        },
        ResourceGroupName = "examplerg",
    });

});


```

```go
package main

import (
	eventgrid "github.com/pulumi/pulumi-azure-native-sdk/eventgrid"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := eventgrid.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &eventgrid.PrivateEndpointConnectionArgs{
			ParentName:                    pulumi.String("exampletopic1"),
			ParentType:                    pulumi.String("topics"),
			PrivateEndpointConnectionName: pulumi.String("BMTPE5.8A30D251-4C61-489D-A1AA-B37C4A329B8B"),
			PrivateLinkServiceConnectionState: &eventgrid.ConnectionStateArgs{
				ActionsRequired: pulumi.String("None"),
				Description:     pulumi.String("approving connection"),
				Status:          pulumi.String("Approved"),
			},
			ResourceGroupName: pulumi.String("examplerg"),
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
import com.pulumi.azurenative.eventgrid.PrivateEndpointConnection;
import com.pulumi.azurenative.eventgrid.PrivateEndpointConnectionArgs;
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
        var privateEndpointConnection = new PrivateEndpointConnection("privateEndpointConnection", PrivateEndpointConnectionArgs.builder()        
            .parentName("exampletopic1")
            .parentType("topics")
            .privateEndpointConnectionName("BMTPE5.8A30D251-4C61-489D-A1AA-B37C4A329B8B")
            .privateLinkServiceConnectionState(Map.ofEntries(
                Map.entry("actionsRequired", "None"),
                Map.entry("description", "approving connection"),
                Map.entry("status", "Approved")
            ))
            .resourceGroupName("examplerg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.eventgrid.PrivateEndpointConnection("privateEndpointConnection", {
    parentName: "exampletopic1",
    parentType: "topics",
    privateEndpointConnectionName: "BMTPE5.8A30D251-4C61-489D-A1AA-B37C4A329B8B",
    privateLinkServiceConnectionState: {
        actionsRequired: "None",
        description: "approving connection",
        status: "Approved",
    },
    resourceGroupName: "examplerg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.eventgrid.PrivateEndpointConnection("privateEndpointConnection",
    parent_name="exampletopic1",
    parent_type="topics",
    private_endpoint_connection_name="BMTPE5.8A30D251-4C61-489D-A1AA-B37C4A329B8B",
    private_link_service_connection_state=azure_native.eventgrid.ConnectionStateArgs(
        actions_required="None",
        description="approving connection",
        status="Approved",
    ),
    resource_group_name="examplerg")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:eventgrid:PrivateEndpointConnection
    properties:
      parentName: exampletopic1
      parentType: topics
      privateEndpointConnectionName: BMTPE5.8A30D251-4C61-489D-A1AA-B37C4A329B8B
      privateLinkServiceConnectionState:
        actionsRequired: None
        description: approving connection
        status: Approved
      resourceGroupName: examplerg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:eventgrid:PrivateEndpointConnection BMTPE5.8A30D251-4C61-489D-A1AA-B37C4A329B8B /subscriptions/5B4B650E-28B9-4790-B3AB-DDBD88D727C4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1/privateEndpointConnections/BMTPE5.8A30D251-4C61-489D-A1AA-B37C4A329B8B 
```
