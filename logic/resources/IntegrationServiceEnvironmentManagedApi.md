The integration service environment managed api.
API Version: 2019-05-01.
Previous API Version: 2019-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Gets the integration service environment managed Apis
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var integrationServiceEnvironmentManagedApi = new AzureNative.Logic.IntegrationServiceEnvironmentManagedApi("integrationServiceEnvironmentManagedApi", new()
    {
        ApiName = "servicebus",
        IntegrationServiceEnvironmentName = "testIntegrationServiceEnvironment",
        Location = "brazilsouth",
        ResourceGroup = "testResourceGroup",
    });

});


```

```go
package main

import (
	logic "github.com/pulumi/pulumi-azure-native-sdk/logic"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := logic.NewIntegrationServiceEnvironmentManagedApi(ctx, "integrationServiceEnvironmentManagedApi", &logic.IntegrationServiceEnvironmentManagedApiArgs{
			ApiName:                           pulumi.String("servicebus"),
			IntegrationServiceEnvironmentName: pulumi.String("testIntegrationServiceEnvironment"),
			Location:                          pulumi.String("brazilsouth"),
			ResourceGroup:                     pulumi.String("testResourceGroup"),
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
import com.pulumi.azurenative.logic.IntegrationServiceEnvironmentManagedApi;
import com.pulumi.azurenative.logic.IntegrationServiceEnvironmentManagedApiArgs;
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
        var integrationServiceEnvironmentManagedApi = new IntegrationServiceEnvironmentManagedApi("integrationServiceEnvironmentManagedApi", IntegrationServiceEnvironmentManagedApiArgs.builder()        
            .apiName("servicebus")
            .integrationServiceEnvironmentName("testIntegrationServiceEnvironment")
            .location("brazilsouth")
            .resourceGroup("testResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const integrationServiceEnvironmentManagedApi = new azure_native.logic.IntegrationServiceEnvironmentManagedApi("integrationServiceEnvironmentManagedApi", {
    apiName: "servicebus",
    integrationServiceEnvironmentName: "testIntegrationServiceEnvironment",
    location: "brazilsouth",
    resourceGroup: "testResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

integration_service_environment_managed_api = azure_native.logic.IntegrationServiceEnvironmentManagedApi("integrationServiceEnvironmentManagedApi",
    api_name="servicebus",
    integration_service_environment_name="testIntegrationServiceEnvironment",
    location="brazilsouth",
    resource_group="testResourceGroup")

```

```yaml
resources:
  integrationServiceEnvironmentManagedApi:
    type: azure-native:logic:IntegrationServiceEnvironmentManagedApi
    properties:
      apiName: servicebus
      integrationServiceEnvironmentName: testIntegrationServiceEnvironment
      location: brazilsouth
      resourceGroup: testResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:logic:IntegrationServiceEnvironmentManagedApi servicebus /subscriptions/80d4fe69-c95b-4dd2-a938-9250f1c8ab03/resourceGroups/rohithah-ise/providers/Microsoft.Logic/integrationServiceEnvironments/tes-ise-ga/managedApis/servicebus 
```
