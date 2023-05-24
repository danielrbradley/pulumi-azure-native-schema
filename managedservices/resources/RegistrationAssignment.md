The registration assignment.
API Version: 2022-10-01.
Previous API Version: 2019-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Put Registration Assignment
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var registrationAssignment = new AzureNative.ManagedServices.RegistrationAssignment("registrationAssignment", new()
    {
        Properties = new AzureNative.ManagedServices.Inputs.RegistrationAssignmentPropertiesArgs
        {
            RegistrationDefinitionId = "/subscriptions/0afefe50-734e-4610-8a82-a144ahf49dea/providers/Microsoft.ManagedServices/registrationDefinitions/26c128c2-fefa-4340-9bb1-6e081c90ada2",
        },
        RegistrationAssignmentId = "26c128c2-fefa-4340-9bb1-6e081c90ada2",
        Scope = "subscription/0afefe50-734e-4610-8a82-a144ahf49dea",
    });

});


```

```go
package main

import (
	managedservices "github.com/pulumi/pulumi-azure-native-sdk/managedservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := managedservices.NewRegistrationAssignment(ctx, "registrationAssignment", &managedservices.RegistrationAssignmentArgs{
			Properties: &managedservices.RegistrationAssignmentPropertiesArgs{
				RegistrationDefinitionId: pulumi.String("/subscriptions/0afefe50-734e-4610-8a82-a144ahf49dea/providers/Microsoft.ManagedServices/registrationDefinitions/26c128c2-fefa-4340-9bb1-6e081c90ada2"),
			},
			RegistrationAssignmentId: pulumi.String("26c128c2-fefa-4340-9bb1-6e081c90ada2"),
			Scope:                    pulumi.String("subscription/0afefe50-734e-4610-8a82-a144ahf49dea"),
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
import com.pulumi.azurenative.managedservices.RegistrationAssignment;
import com.pulumi.azurenative.managedservices.RegistrationAssignmentArgs;
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
        var registrationAssignment = new RegistrationAssignment("registrationAssignment", RegistrationAssignmentArgs.builder()        
            .properties(Map.of("registrationDefinitionId", "/subscriptions/0afefe50-734e-4610-8a82-a144ahf49dea/providers/Microsoft.ManagedServices/registrationDefinitions/26c128c2-fefa-4340-9bb1-6e081c90ada2"))
            .registrationAssignmentId("26c128c2-fefa-4340-9bb1-6e081c90ada2")
            .scope("subscription/0afefe50-734e-4610-8a82-a144ahf49dea")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const registrationAssignment = new azure_native.managedservices.RegistrationAssignment("registrationAssignment", {
    properties: {
        registrationDefinitionId: "/subscriptions/0afefe50-734e-4610-8a82-a144ahf49dea/providers/Microsoft.ManagedServices/registrationDefinitions/26c128c2-fefa-4340-9bb1-6e081c90ada2",
    },
    registrationAssignmentId: "26c128c2-fefa-4340-9bb1-6e081c90ada2",
    scope: "subscription/0afefe50-734e-4610-8a82-a144ahf49dea",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

registration_assignment = azure_native.managedservices.RegistrationAssignment("registrationAssignment",
    properties=azure_native.managedservices.RegistrationAssignmentPropertiesArgs(
        registration_definition_id="/subscriptions/0afefe50-734e-4610-8a82-a144ahf49dea/providers/Microsoft.ManagedServices/registrationDefinitions/26c128c2-fefa-4340-9bb1-6e081c90ada2",
    ),
    registration_assignment_id="26c128c2-fefa-4340-9bb1-6e081c90ada2",
    scope="subscription/0afefe50-734e-4610-8a82-a144ahf49dea")

```

```yaml
resources:
  registrationAssignment:
    type: azure-native:managedservices:RegistrationAssignment
    properties:
      properties:
        registrationDefinitionId: /subscriptions/0afefe50-734e-4610-8a82-a144ahf49dea/providers/Microsoft.ManagedServices/registrationDefinitions/26c128c2-fefa-4340-9bb1-6e081c90ada2
      registrationAssignmentId: 26c128c2-fefa-4340-9bb1-6e081c90ada2
      scope: subscription/0afefe50-734e-4610-8a82-a144ahf49dea

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:managedservices:RegistrationAssignment 484a7d5f-9729-4b87-bc9b-26610985a013 /subscriptions/0afefe50-734e-4610-8c82-a144aff49dea/providers/Microsoft.ManagedServices/registrationAssignments/484a7d5f-9729-4b87-bc9b-26610985a013 
```
