Information about managed application.
API Version: 2021-07-01.
Previous API Version: 2019-07-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update managed application
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var application = new AzureNative.Solutions.Application("application", new()
    {
        ApplicationDefinitionId = "/subscriptions/subid/resourceGroups/rg/providers/Microsoft.Solutions/applicationDefinitions/myAppDef",
        ApplicationName = "myManagedApplication",
        Kind = "ServiceCatalog",
        ManagedResourceGroupId = "/subscriptions/subid/resourceGroups/myManagedRG",
        ResourceGroupName = "rg",
    });

});


```

```go
package main

import (
	solutions "github.com/pulumi/pulumi-azure-native-sdk/solutions"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := solutions.NewApplication(ctx, "application", &solutions.ApplicationArgs{
			ApplicationDefinitionId: pulumi.String("/subscriptions/subid/resourceGroups/rg/providers/Microsoft.Solutions/applicationDefinitions/myAppDef"),
			ApplicationName:         pulumi.String("myManagedApplication"),
			Kind:                    pulumi.String("ServiceCatalog"),
			ManagedResourceGroupId:  pulumi.String("/subscriptions/subid/resourceGroups/myManagedRG"),
			ResourceGroupName:       pulumi.String("rg"),
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
import com.pulumi.azurenative.solutions.Application;
import com.pulumi.azurenative.solutions.ApplicationArgs;
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
        var application = new Application("application", ApplicationArgs.builder()        
            .applicationDefinitionId("/subscriptions/subid/resourceGroups/rg/providers/Microsoft.Solutions/applicationDefinitions/myAppDef")
            .applicationName("myManagedApplication")
            .kind("ServiceCatalog")
            .managedResourceGroupId("/subscriptions/subid/resourceGroups/myManagedRG")
            .resourceGroupName("rg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const application = new azure_native.solutions.Application("application", {
    applicationDefinitionId: "/subscriptions/subid/resourceGroups/rg/providers/Microsoft.Solutions/applicationDefinitions/myAppDef",
    applicationName: "myManagedApplication",
    kind: "ServiceCatalog",
    managedResourceGroupId: "/subscriptions/subid/resourceGroups/myManagedRG",
    resourceGroupName: "rg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

application = azure_native.solutions.Application("application",
    application_definition_id="/subscriptions/subid/resourceGroups/rg/providers/Microsoft.Solutions/applicationDefinitions/myAppDef",
    application_name="myManagedApplication",
    kind="ServiceCatalog",
    managed_resource_group_id="/subscriptions/subid/resourceGroups/myManagedRG",
    resource_group_name="rg")

```

```yaml
resources:
  application:
    type: azure-native:solutions:Application
    properties:
      applicationDefinitionId: /subscriptions/subid/resourceGroups/rg/providers/Microsoft.Solutions/applicationDefinitions/myAppDef
      applicationName: myManagedApplication
      kind: ServiceCatalog
      managedResourceGroupId: /subscriptions/subid/resourceGroups/myManagedRG
      resourceGroupName: rg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:solutions:Application myManagedApplication /subscriptions/subid/resourceGroups/rg/providers/Microsoft.Solutions/applications/myManagedApplication 
```
