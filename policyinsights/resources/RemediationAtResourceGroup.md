The remediation definition.
API Version: 2021-10-01.
Previous API Version: 2019-07-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create remediation at resource group scope
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var remediationAtResourceGroup = new AzureNative.PolicyInsights.RemediationAtResourceGroup("remediationAtResourceGroup", new()
    {
        PolicyAssignmentId = "/subscriptions/35ee058e-5fa0-414c-8145-3ebb8d09b6e2/resourceGroups/myResourceGroup/providers/microsoft.authorization/policyassignments/b101830944f246d8a14088c5",
        RemediationName = "storageRemediation",
        ResourceGroupName = "myResourceGroup",
    });

});


```

```go
package main

import (
	policyinsights "github.com/pulumi/pulumi-azure-native-sdk/policyinsights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := policyinsights.NewRemediationAtResourceGroup(ctx, "remediationAtResourceGroup", &policyinsights.RemediationAtResourceGroupArgs{
			PolicyAssignmentId: pulumi.String("/subscriptions/35ee058e-5fa0-414c-8145-3ebb8d09b6e2/resourceGroups/myResourceGroup/providers/microsoft.authorization/policyassignments/b101830944f246d8a14088c5"),
			RemediationName:    pulumi.String("storageRemediation"),
			ResourceGroupName:  pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.policyinsights.RemediationAtResourceGroup;
import com.pulumi.azurenative.policyinsights.RemediationAtResourceGroupArgs;
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
        var remediationAtResourceGroup = new RemediationAtResourceGroup("remediationAtResourceGroup", RemediationAtResourceGroupArgs.builder()        
            .policyAssignmentId("/subscriptions/35ee058e-5fa0-414c-8145-3ebb8d09b6e2/resourceGroups/myResourceGroup/providers/microsoft.authorization/policyassignments/b101830944f246d8a14088c5")
            .remediationName("storageRemediation")
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const remediationAtResourceGroup = new azure_native.policyinsights.RemediationAtResourceGroup("remediationAtResourceGroup", {
    policyAssignmentId: "/subscriptions/35ee058e-5fa0-414c-8145-3ebb8d09b6e2/resourceGroups/myResourceGroup/providers/microsoft.authorization/policyassignments/b101830944f246d8a14088c5",
    remediationName: "storageRemediation",
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

remediation_at_resource_group = azure_native.policyinsights.RemediationAtResourceGroup("remediationAtResourceGroup",
    policy_assignment_id="/subscriptions/35ee058e-5fa0-414c-8145-3ebb8d09b6e2/resourceGroups/myResourceGroup/providers/microsoft.authorization/policyassignments/b101830944f246d8a14088c5",
    remediation_name="storageRemediation",
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  remediationAtResourceGroup:
    type: azure-native:policyinsights:RemediationAtResourceGroup
    properties:
      policyAssignmentId: /subscriptions/35ee058e-5fa0-414c-8145-3ebb8d09b6e2/resourceGroups/myResourceGroup/providers/microsoft.authorization/policyassignments/b101830944f246d8a14088c5
      remediationName: storageRemediation
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:policyinsights:RemediationAtResourceGroup storageRemediation /subscriptions/35ee058e-5fa0-414c-8145-3ebb8d09b6e2/resourceGroups/myResourceGroup/providers/microsoft.policyinsights/remediations/storageRemediation 
```
