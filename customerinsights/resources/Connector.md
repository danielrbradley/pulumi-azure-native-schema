The connector resource format.
API Version: 2017-04-26.
Previous API Version: 2017-04-26. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Connectors_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var connector = new AzureNative.CustomerInsights.Connector("connector", new()
    {
        ConnectorName = "testConnector",
        ConnectorProperties = 
        {
            { "connectionKeyVaultUrl", 
            {
                { "organizationId", "XXX" },
                { "organizationUrl", "https://XXX.crmlivetie.com/" },
            } },
        },
        ConnectorType = "AzureBlob",
        Description = "Test connector",
        DisplayName = "testConnector",
        HubName = "sdkTestHub",
        ResourceGroupName = "TestHubRG",
    });

});


```

```go
package main

import (
	customerinsights "github.com/pulumi/pulumi-azure-native-sdk/customerinsights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := customerinsights.NewConnector(ctx, "connector", &customerinsights.ConnectorArgs{
			ConnectorName: pulumi.String("testConnector"),
			ConnectorProperties: pulumi.AnyMap{
				"connectionKeyVaultUrl": pulumi.Any{
					OrganizationId:  "XXX",
					OrganizationUrl: "https://XXX.crmlivetie.com/",
				},
			},
			ConnectorType:     pulumi.String("AzureBlob"),
			Description:       pulumi.String("Test connector"),
			DisplayName:       pulumi.String("testConnector"),
			HubName:           pulumi.String("sdkTestHub"),
			ResourceGroupName: pulumi.String("TestHubRG"),
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
import com.pulumi.azurenative.customerinsights.Connector;
import com.pulumi.azurenative.customerinsights.ConnectorArgs;
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
        var connector = new Connector("connector", ConnectorArgs.builder()        
            .connectorName("testConnector")
            .connectorProperties(Map.of("connectionKeyVaultUrl", Map.ofEntries(
                Map.entry("organizationId", "XXX"),
                Map.entry("organizationUrl", "https://XXX.crmlivetie.com/")
            )))
            .connectorType("AzureBlob")
            .description("Test connector")
            .displayName("testConnector")
            .hubName("sdkTestHub")
            .resourceGroupName("TestHubRG")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const connector = new azure_native.customerinsights.Connector("connector", {
    connectorName: "testConnector",
    connectorProperties: {
        connectionKeyVaultUrl: {
            organizationId: "XXX",
            organizationUrl: "https://XXX.crmlivetie.com/",
        },
    },
    connectorType: "AzureBlob",
    description: "Test connector",
    displayName: "testConnector",
    hubName: "sdkTestHub",
    resourceGroupName: "TestHubRG",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

connector = azure_native.customerinsights.Connector("connector",
    connector_name="testConnector",
    connector_properties={
        "connectionKeyVaultUrl": {
            "organizationId": "XXX",
            "organizationUrl": "https://XXX.crmlivetie.com/",
        },
    },
    connector_type="AzureBlob",
    description="Test connector",
    display_name="testConnector",
    hub_name="sdkTestHub",
    resource_group_name="TestHubRG")

```

```yaml
resources:
  connector:
    type: azure-native:customerinsights:Connector
    properties:
      connectorName: testConnector
      connectorProperties:
        connectionKeyVaultUrl:
          organizationId: XXX
          organizationUrl: https://XXX.crmlivetie.com/
      connectorType: AzureBlob
      description: Test connector
      displayName: testConnector
      hubName: sdkTestHub
      resourceGroupName: TestHubRG

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:customerinsights:Connector sdkTestHub/testConnector /subscriptions/c909e979-ef71-4def-a970-bc7c154db8c5/resourceGroups/TestHubRG/providers/Microsoft.CustomerInsights/hubs/sdkTestHub/connectors/testConnector 
```
