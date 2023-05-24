The Managed Network resource
API Version: 2019-06-01-preview.
Previous API Version: 2019-06-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ScopeAssignmentsPut
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var scopeAssignment = new AzureNative.ManagedNetwork.ScopeAssignment("scopeAssignment", new()
    {
        AssignedManagedNetwork = "/subscriptions/subscriptionA/resourceGroups/myResourceGroup/providers/Microsoft.ManagedNetwork/managedNetworks/myManagedNetwork",
        Scope = "subscriptions/subscriptionC",
        ScopeAssignmentName = "subscriptionCAssignment",
    });

});


```

```go
package main

import (
	managednetwork "github.com/pulumi/pulumi-azure-native-sdk/managednetwork"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := managednetwork.NewScopeAssignment(ctx, "scopeAssignment", &managednetwork.ScopeAssignmentArgs{
			AssignedManagedNetwork: pulumi.String("/subscriptions/subscriptionA/resourceGroups/myResourceGroup/providers/Microsoft.ManagedNetwork/managedNetworks/myManagedNetwork"),
			Scope:                  pulumi.String("subscriptions/subscriptionC"),
			ScopeAssignmentName:    pulumi.String("subscriptionCAssignment"),
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
import com.pulumi.azurenative.managednetwork.ScopeAssignment;
import com.pulumi.azurenative.managednetwork.ScopeAssignmentArgs;
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
        var scopeAssignment = new ScopeAssignment("scopeAssignment", ScopeAssignmentArgs.builder()        
            .assignedManagedNetwork("/subscriptions/subscriptionA/resourceGroups/myResourceGroup/providers/Microsoft.ManagedNetwork/managedNetworks/myManagedNetwork")
            .scope("subscriptions/subscriptionC")
            .scopeAssignmentName("subscriptionCAssignment")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const scopeAssignment = new azure_native.managednetwork.ScopeAssignment("scopeAssignment", {
    assignedManagedNetwork: "/subscriptions/subscriptionA/resourceGroups/myResourceGroup/providers/Microsoft.ManagedNetwork/managedNetworks/myManagedNetwork",
    scope: "subscriptions/subscriptionC",
    scopeAssignmentName: "subscriptionCAssignment",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

scope_assignment = azure_native.managednetwork.ScopeAssignment("scopeAssignment",
    assigned_managed_network="/subscriptions/subscriptionA/resourceGroups/myResourceGroup/providers/Microsoft.ManagedNetwork/managedNetworks/myManagedNetwork",
    scope="subscriptions/subscriptionC",
    scope_assignment_name="subscriptionCAssignment")

```

```yaml
resources:
  scopeAssignment:
    type: azure-native:managednetwork:ScopeAssignment
    properties:
      assignedManagedNetwork: /subscriptions/subscriptionA/resourceGroups/myResourceGroup/providers/Microsoft.ManagedNetwork/managedNetworks/myManagedNetwork
      scope: subscriptions/subscriptionC
      scopeAssignmentName: subscriptionCAssignment

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:managednetwork:ScopeAssignment subscriptionCAssignment /subscriptions/subscriptionC/providers/Microsoft.ManagedNetwork/scopeAssignments/subscriptionCAssignment 
```
