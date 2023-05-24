Remote Private Endpoint Connection ARM resource.
API Version: 2022-09-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Approves or rejects a private endpoint connection.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var appServiceEnvironmentPrivateEndpointConnection = new AzureNative.Web.AppServiceEnvironmentPrivateEndpointConnection("appServiceEnvironmentPrivateEndpointConnection", new()
    {
        Name = "test-ase",
        PrivateEndpointConnectionName = "fa38656c-034e-43d8-adce-fe06ce039c98",
        PrivateLinkServiceConnectionState = new AzureNative.Web.Inputs.PrivateLinkConnectionStateArgs
        {
            Description = "Approved by johndoe@company.com",
            Status = "Approved",
        },
        ResourceGroupName = "test-rg",
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
		_, err := web.NewAppServiceEnvironmentPrivateEndpointConnection(ctx, "appServiceEnvironmentPrivateEndpointConnection", &web.AppServiceEnvironmentPrivateEndpointConnectionArgs{
			Name:                          pulumi.String("test-ase"),
			PrivateEndpointConnectionName: pulumi.String("fa38656c-034e-43d8-adce-fe06ce039c98"),
			PrivateLinkServiceConnectionState: &web.PrivateLinkConnectionStateArgs{
				Description: pulumi.String("Approved by johndoe@company.com"),
				Status:      pulumi.String("Approved"),
			},
			ResourceGroupName: pulumi.String("test-rg"),
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
import com.pulumi.azurenative.web.AppServiceEnvironmentPrivateEndpointConnection;
import com.pulumi.azurenative.web.AppServiceEnvironmentPrivateEndpointConnectionArgs;
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
        var appServiceEnvironmentPrivateEndpointConnection = new AppServiceEnvironmentPrivateEndpointConnection("appServiceEnvironmentPrivateEndpointConnection", AppServiceEnvironmentPrivateEndpointConnectionArgs.builder()        
            .name("test-ase")
            .privateEndpointConnectionName("fa38656c-034e-43d8-adce-fe06ce039c98")
            .privateLinkServiceConnectionState(Map.ofEntries(
                Map.entry("description", "Approved by johndoe@company.com"),
                Map.entry("status", "Approved")
            ))
            .resourceGroupName("test-rg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const appServiceEnvironmentPrivateEndpointConnection = new azure_native.web.AppServiceEnvironmentPrivateEndpointConnection("appServiceEnvironmentPrivateEndpointConnection", {
    name: "test-ase",
    privateEndpointConnectionName: "fa38656c-034e-43d8-adce-fe06ce039c98",
    privateLinkServiceConnectionState: {
        description: "Approved by johndoe@company.com",
        status: "Approved",
    },
    resourceGroupName: "test-rg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

app_service_environment_private_endpoint_connection = azure_native.web.AppServiceEnvironmentPrivateEndpointConnection("appServiceEnvironmentPrivateEndpointConnection",
    name="test-ase",
    private_endpoint_connection_name="fa38656c-034e-43d8-adce-fe06ce039c98",
    private_link_service_connection_state=azure_native.web.PrivateLinkConnectionStateArgs(
        description="Approved by johndoe@company.com",
        status="Approved",
    ),
    resource_group_name="test-rg")

```

```yaml
resources:
  appServiceEnvironmentPrivateEndpointConnection:
    type: azure-native:web:AppServiceEnvironmentPrivateEndpointConnection
    properties:
      name: test-ase
      privateEndpointConnectionName: fa38656c-034e-43d8-adce-fe06ce039c98
      privateLinkServiceConnectionState:
        description: Approved by johndoe@company.com
        status: Approved
      resourceGroupName: test-rg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:web:AppServiceEnvironmentPrivateEndpointConnection fa38656c-034e-43d8-adce-fe06ce039c98 /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/test-rg/providers/Microsoft.Web/hostingEnvironments/test-ase/privateEndpointConnections/fa38656c-034e-43d8-adce-fe06ce039c98 
```
