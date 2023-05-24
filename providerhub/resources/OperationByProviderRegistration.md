
API Version: 2020-11-20.
Previous API Version: 2020-11-20. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Operations_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var operationByProviderRegistration = new AzureNative.ProviderHub.OperationByProviderRegistration("operationByProviderRegistration", new()
    {
        Contents = new[]
        {
            new AzureNative.ProviderHub.Inputs.OperationsDefinitionArgs
            {
                Display = new AzureNative.ProviderHub.Inputs.OperationsDefinitionDisplayArgs
                {
                    Description = "Read employees",
                    Operation = "Gets/List employee resources",
                    Provider = "Microsoft.Contoso",
                    Resource = "Employees",
                },
                Name = "Microsoft.Contoso/Employees/Read",
            },
        },
        ProviderNamespace = "Microsoft.Contoso",
    });

});


```

```go
package main

import (
	providerhub "github.com/pulumi/pulumi-azure-native-sdk/providerhub"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := providerhub.NewOperationByProviderRegistration(ctx, "operationByProviderRegistration", &providerhub.OperationByProviderRegistrationArgs{
			Contents: []providerhub.OperationsDefinitionArgs{
				{
					Display: {
						Description: pulumi.String("Read employees"),
						Operation:   pulumi.String("Gets/List employee resources"),
						Provider:    pulumi.String("Microsoft.Contoso"),
						Resource:    pulumi.String("Employees"),
					},
					Name: pulumi.String("Microsoft.Contoso/Employees/Read"),
				},
			},
			ProviderNamespace: pulumi.String("Microsoft.Contoso"),
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
import com.pulumi.azurenative.providerhub.OperationByProviderRegistration;
import com.pulumi.azurenative.providerhub.OperationByProviderRegistrationArgs;
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
        var operationByProviderRegistration = new OperationByProviderRegistration("operationByProviderRegistration", OperationByProviderRegistrationArgs.builder()        
            .contents(Map.ofEntries(
                Map.entry("display", Map.ofEntries(
                    Map.entry("description", "Read employees"),
                    Map.entry("operation", "Gets/List employee resources"),
                    Map.entry("provider", "Microsoft.Contoso"),
                    Map.entry("resource", "Employees")
                )),
                Map.entry("name", "Microsoft.Contoso/Employees/Read")
            ))
            .providerNamespace("Microsoft.Contoso")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const operationByProviderRegistration = new azure_native.providerhub.OperationByProviderRegistration("operationByProviderRegistration", {
    contents: [{
        display: {
            description: "Read employees",
            operation: "Gets/List employee resources",
            provider: "Microsoft.Contoso",
            resource: "Employees",
        },
        name: "Microsoft.Contoso/Employees/Read",
    }],
    providerNamespace: "Microsoft.Contoso",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

operation_by_provider_registration = azure_native.providerhub.OperationByProviderRegistration("operationByProviderRegistration",
    contents=[azure_native.providerhub.OperationsDefinitionArgs(
        display=azure_native.providerhub.OperationsDefinitionDisplayArgs(
            description="Read employees",
            operation="Gets/List employee resources",
            provider="Microsoft.Contoso",
            resource="Employees",
        ),
        name="Microsoft.Contoso/Employees/Read",
    )],
    provider_namespace="Microsoft.Contoso")

```

```yaml
resources:
  operationByProviderRegistration:
    type: azure-native:providerhub:OperationByProviderRegistration
    properties:
      contents:
        - display:
            description: Read employees
            operation: Gets/List employee resources
            provider: Microsoft.Contoso
            resource: Employees
          name: Microsoft.Contoso/Employees/Read
      providerNamespace: Microsoft.Contoso

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:providerhub:OperationByProviderRegistration myresource1 /subscriptions/{subscriptionId}/providers/Microsoft.ProviderHub/providerRegistrations/{providerNamespace}/operations/default 
```
