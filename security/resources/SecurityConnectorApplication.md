Security Application over a given scope
API Version: 2022-07-01-preview.
Previous API Version: 2022-07-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Application
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var securityConnectorApplication = new AzureNative.Security.SecurityConnectorApplication("securityConnectorApplication", new()
    {
        ApplicationId = "ad9a8e26-29d9-4829-bb30-e597a58cdbb8",
        Description = "An application on critical GCP recommendations",
        DisplayName = "GCP Admin's application",
        ResourceGroupName = "gcpResourceGroup",
        SecurityConnectorName = "gcpconnector",
        SourceResourceType = "Assessments",
    });

});


```

```go
package main

import (
	security "github.com/pulumi/pulumi-azure-native-sdk/security"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := security.NewSecurityConnectorApplication(ctx, "securityConnectorApplication", &security.SecurityConnectorApplicationArgs{
			ApplicationId:         pulumi.String("ad9a8e26-29d9-4829-bb30-e597a58cdbb8"),
			Description:           pulumi.String("An application on critical GCP recommendations"),
			DisplayName:           pulumi.String("GCP Admin's application"),
			ResourceGroupName:     pulumi.String("gcpResourceGroup"),
			SecurityConnectorName: pulumi.String("gcpconnector"),
			SourceResourceType:    pulumi.String("Assessments"),
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
import com.pulumi.azurenative.security.SecurityConnectorApplication;
import com.pulumi.azurenative.security.SecurityConnectorApplicationArgs;
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
        var securityConnectorApplication = new SecurityConnectorApplication("securityConnectorApplication", SecurityConnectorApplicationArgs.builder()        
            .applicationId("ad9a8e26-29d9-4829-bb30-e597a58cdbb8")
            .description("An application on critical GCP recommendations")
            .displayName("GCP Admin's application")
            .resourceGroupName("gcpResourceGroup")
            .securityConnectorName("gcpconnector")
            .sourceResourceType("Assessments")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const securityConnectorApplication = new azure_native.security.SecurityConnectorApplication("securityConnectorApplication", {
    applicationId: "ad9a8e26-29d9-4829-bb30-e597a58cdbb8",
    description: "An application on critical GCP recommendations",
    displayName: "GCP Admin's application",
    resourceGroupName: "gcpResourceGroup",
    securityConnectorName: "gcpconnector",
    sourceResourceType: "Assessments",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

security_connector_application = azure_native.security.SecurityConnectorApplication("securityConnectorApplication",
    application_id="ad9a8e26-29d9-4829-bb30-e597a58cdbb8",
    description="An application on critical GCP recommendations",
    display_name="GCP Admin's application",
    resource_group_name="gcpResourceGroup",
    security_connector_name="gcpconnector",
    source_resource_type="Assessments")

```

```yaml
resources:
  securityConnectorApplication:
    type: azure-native:security:SecurityConnectorApplication
    properties:
      applicationId: ad9a8e26-29d9-4829-bb30-e597a58cdbb8
      description: An application on critical GCP recommendations
      displayName: GCP Admin's application
      resourceGroupName: gcpResourceGroup
      securityConnectorName: gcpconnector
      sourceResourceType: Assessments

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:security:SecurityConnectorApplication 1f3afdf9-d0c9-4c3d-847f-89da613e70a8 subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourcegroups/gcpResourceGroup/providers/Microsoft.Security/securityConnectors/gcpconnector/providers/Microsoft.Security/applications/ad9a8e26-29d9-4829-bb30-e597a58cdbb8 
```
