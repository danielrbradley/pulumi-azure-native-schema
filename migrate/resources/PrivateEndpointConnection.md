A private endpoint connection for a project.
API Version: 2019-10-01.
Previous API Version: 2019-10-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PrivateEndpointConnections_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var privateEndpointConnection = new AzureNative.Migrate.PrivateEndpointConnection("privateEndpointConnection", new()
    {
        ETag = "\"00009300-0000-0300-0000-602b967b0000\"",
        PrivateEndpointConnectionName = "custestpece80project3980pe.7e35576b-3df4-478e-9759-f64351cf4f43",
        ProjectName = "abgoyalWEselfhostb72bproject",
        Properties = new AzureNative.Migrate.Inputs.PrivateEndpointConnectionPropertiesArgs
        {
            PrivateLinkServiceConnectionState = new AzureNative.Migrate.Inputs.PrivateLinkServiceConnectionStateArgs
            {
                ActionsRequired = "",
                Status = "Approved",
            },
        },
        ResourceGroupName = "abgoyal-westEurope",
    });

});


```

```go
package main

import (
	migrate "github.com/pulumi/pulumi-azure-native-sdk/migrate"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := migrate.NewPrivateEndpointConnection(ctx, "privateEndpointConnection", &migrate.PrivateEndpointConnectionArgs{
			ETag:                          pulumi.String("\"00009300-0000-0300-0000-602b967b0000\""),
			PrivateEndpointConnectionName: pulumi.String("custestpece80project3980pe.7e35576b-3df4-478e-9759-f64351cf4f43"),
			ProjectName:                   pulumi.String("abgoyalWEselfhostb72bproject"),
			Properties: migrate.PrivateEndpointConnectionPropertiesResponse{
				PrivateLinkServiceConnectionState: &migrate.PrivateLinkServiceConnectionStateArgs{
					ActionsRequired: pulumi.String(""),
					Status:          pulumi.String("Approved"),
				},
			},
			ResourceGroupName: pulumi.String("abgoyal-westEurope"),
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
import com.pulumi.azurenative.migrate.PrivateEndpointConnection;
import com.pulumi.azurenative.migrate.PrivateEndpointConnectionArgs;
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
            .eTag("\"00009300-0000-0300-0000-602b967b0000\"")
            .privateEndpointConnectionName("custestpece80project3980pe.7e35576b-3df4-478e-9759-f64351cf4f43")
            .projectName("abgoyalWEselfhostb72bproject")
            .properties(Map.of("privateLinkServiceConnectionState", Map.ofEntries(
                Map.entry("actionsRequired", ""),
                Map.entry("status", "Approved")
            )))
            .resourceGroupName("abgoyal-westEurope")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const privateEndpointConnection = new azure_native.migrate.PrivateEndpointConnection("privateEndpointConnection", {
    eTag: "\"00009300-0000-0300-0000-602b967b0000\"",
    privateEndpointConnectionName: "custestpece80project3980pe.7e35576b-3df4-478e-9759-f64351cf4f43",
    projectName: "abgoyalWEselfhostb72bproject",
    properties: {
        privateLinkServiceConnectionState: {
            actionsRequired: "",
            status: "Approved",
        },
    },
    resourceGroupName: "abgoyal-westEurope",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

private_endpoint_connection = azure_native.migrate.PrivateEndpointConnection("privateEndpointConnection",
    e_tag="\"00009300-0000-0300-0000-602b967b0000\"",
    private_endpoint_connection_name="custestpece80project3980pe.7e35576b-3df4-478e-9759-f64351cf4f43",
    project_name="abgoyalWEselfhostb72bproject",
    properties=azure_native.migrate.PrivateEndpointConnectionPropertiesResponseArgs(
        private_link_service_connection_state=azure_native.migrate.PrivateLinkServiceConnectionStateArgs(
            actions_required="",
            status="Approved",
        ),
    ),
    resource_group_name="abgoyal-westEurope")

```

```yaml
resources:
  privateEndpointConnection:
    type: azure-native:migrate:PrivateEndpointConnection
    properties:
      eTag: '"00009300-0000-0300-0000-602b967b0000"'
      privateEndpointConnectionName: custestpece80project3980pe.7e35576b-3df4-478e-9759-f64351cf4f43
      projectName: abgoyalWEselfhostb72bproject
      properties:
        privateLinkServiceConnectionState:
          actionsRequired:
          status: Approved
      resourceGroupName: abgoyal-westEurope

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:migrate:PrivateEndpointConnection custestpece80project3980pe.7e35576b-3df4-478e-9759-f64351cf4f43 /subscriptions/4bd2aa0f-2bd2-4d67-91a8-5a4533d58600/resourceGroups/madhavicus/providers/Microsoft.Migrate/assessmentprojects/custestpece80project/privateEndpointConnections/custestpece80project3980pe.7e35576b-3df4-478e-9759-f64351cf4f43 
```
