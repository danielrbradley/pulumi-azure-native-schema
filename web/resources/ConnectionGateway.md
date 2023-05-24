The gateway definition
API Version: 2016-06-01.
Previous API Version: 2016-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Replace a connection gateway definition
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var connectionGateway = new AzureNative.Web.ConnectionGateway("connectionGateway", new()
    {
        ConnectionGatewayName = "test123",
        Properties = new AzureNative.Web.Inputs.ConnectionGatewayDefinitionPropertiesArgs
        {
            BackendUri = "https://WABI-WEST-US-redirect.analysis.windows.net",
            ConnectionGatewayInstallation = new AzureNative.Web.Inputs.ConnectionGatewayReferenceArgs
            {
                Id = "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/providers/Microsoft.Web/locations/westus/connectionGatewayInstallations/865dccd1-5d5c-45fe-b5a0-249d4de4134c",
            },
            ContactInformation = new[]
            {
                "test123@microsoft.com",
            },
            DisplayName = "test123",
            MachineName = "TEST123",
            Status = "Installed",
        },
        ResourceGroupName = "testResourceGroup",
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
		_, err := web.NewConnectionGateway(ctx, "connectionGateway", &web.ConnectionGatewayArgs{
			ConnectionGatewayName: pulumi.String("test123"),
			Properties: web.ConnectionGatewayDefinitionResponseProperties{
				BackendUri: pulumi.String("https://WABI-WEST-US-redirect.analysis.windows.net"),
				ConnectionGatewayInstallation: &web.ConnectionGatewayReferenceArgs{
					Id: pulumi.String("/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/providers/Microsoft.Web/locations/westus/connectionGatewayInstallations/865dccd1-5d5c-45fe-b5a0-249d4de4134c"),
				},
				ContactInformation: pulumi.StringArray{
					pulumi.String("test123@microsoft.com"),
				},
				DisplayName: pulumi.String("test123"),
				MachineName: pulumi.String("TEST123"),
				Status:      pulumi.Any("Installed"),
			},
			ResourceGroupName: pulumi.String("testResourceGroup"),
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
import com.pulumi.azurenative.web.ConnectionGateway;
import com.pulumi.azurenative.web.ConnectionGatewayArgs;
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
        var connectionGateway = new ConnectionGateway("connectionGateway", ConnectionGatewayArgs.builder()        
            .connectionGatewayName("test123")
            .properties(Map.ofEntries(
                Map.entry("backendUri", "https://WABI-WEST-US-redirect.analysis.windows.net"),
                Map.entry("connectionGatewayInstallation", Map.of("id", "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/providers/Microsoft.Web/locations/westus/connectionGatewayInstallations/865dccd1-5d5c-45fe-b5a0-249d4de4134c")),
                Map.entry("contactInformation", "test123@microsoft.com"),
                Map.entry("displayName", "test123"),
                Map.entry("machineName", "TEST123"),
                Map.entry("status", "Installed")
            ))
            .resourceGroupName("testResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const connectionGateway = new azure_native.web.ConnectionGateway("connectionGateway", {
    connectionGatewayName: "test123",
    properties: {
        backendUri: "https://WABI-WEST-US-redirect.analysis.windows.net",
        connectionGatewayInstallation: {
            id: "/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/providers/Microsoft.Web/locations/westus/connectionGatewayInstallations/865dccd1-5d5c-45fe-b5a0-249d4de4134c",
        },
        contactInformation: ["test123@microsoft.com"],
        displayName: "test123",
        machineName: "TEST123",
        status: "Installed",
    },
    resourceGroupName: "testResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

connection_gateway = azure_native.web.ConnectionGateway("connectionGateway",
    connection_gateway_name="test123",
    properties=azure_native.web.ConnectionGatewayDefinitionResponsePropertiesArgs(
        backend_uri="https://WABI-WEST-US-redirect.analysis.windows.net",
        connection_gateway_installation=azure_native.web.ConnectionGatewayReferenceArgs(
            id="/subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/providers/Microsoft.Web/locations/westus/connectionGatewayInstallations/865dccd1-5d5c-45fe-b5a0-249d4de4134c",
        ),
        contact_information=["test123@microsoft.com"],
        display_name="test123",
        machine_name="TEST123",
        status="Installed",
    ),
    resource_group_name="testResourceGroup")

```

```yaml
resources:
  connectionGateway:
    type: azure-native:web:ConnectionGateway
    properties:
      connectionGatewayName: test123
      properties:
        backendUri: https://WABI-WEST-US-redirect.analysis.windows.net
        connectionGatewayInstallation:
          id: /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/providers/Microsoft.Web/locations/westus/connectionGatewayInstallations/865dccd1-5d5c-45fe-b5a0-249d4de4134c
        contactInformation:
          - test123@microsoft.com
        displayName: test123
        machineName: TEST123
        status: Installed
      resourceGroupName: testResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:web:ConnectionGateway test123 /subscriptions/34adfa4f-cedf-4dc0-ba29-b6d1a69ab345/resourceGroups/testResourceGroup/providers/Microsoft.Web/connectionGateways/test123 
```
