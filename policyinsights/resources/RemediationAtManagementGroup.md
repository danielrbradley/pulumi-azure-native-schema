The remediation definition.
API Version: 2021-10-01.
Previous API Version: 2019-07-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create remediation at management group scope
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var remediationAtManagementGroup = new AzureNative.PolicyInsights.RemediationAtManagementGroup("remediationAtManagementGroup", new()
    {
        ManagementGroupId = "financeMg",
        ManagementGroupsNamespace = "Microsoft.Management",
        PolicyAssignmentId = "/providers/microsoft.management/managementGroups/financeMg/providers/microsoft.authorization/policyassignments/b101830944f246d8a14088c5",
        RemediationName = "storageRemediation",
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
		_, err := policyinsights.NewRemediationAtManagementGroup(ctx, "remediationAtManagementGroup", &policyinsights.RemediationAtManagementGroupArgs{
			ManagementGroupId:         pulumi.String("financeMg"),
			ManagementGroupsNamespace: pulumi.String("Microsoft.Management"),
			PolicyAssignmentId:        pulumi.String("/providers/microsoft.management/managementGroups/financeMg/providers/microsoft.authorization/policyassignments/b101830944f246d8a14088c5"),
			RemediationName:           pulumi.String("storageRemediation"),
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
import com.pulumi.azurenative.policyinsights.RemediationAtManagementGroup;
import com.pulumi.azurenative.policyinsights.RemediationAtManagementGroupArgs;
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
        var remediationAtManagementGroup = new RemediationAtManagementGroup("remediationAtManagementGroup", RemediationAtManagementGroupArgs.builder()        
            .managementGroupId("financeMg")
            .managementGroupsNamespace("Microsoft.Management")
            .policyAssignmentId("/providers/microsoft.management/managementGroups/financeMg/providers/microsoft.authorization/policyassignments/b101830944f246d8a14088c5")
            .remediationName("storageRemediation")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const remediationAtManagementGroup = new azure_native.policyinsights.RemediationAtManagementGroup("remediationAtManagementGroup", {
    managementGroupId: "financeMg",
    managementGroupsNamespace: "Microsoft.Management",
    policyAssignmentId: "/providers/microsoft.management/managementGroups/financeMg/providers/microsoft.authorization/policyassignments/b101830944f246d8a14088c5",
    remediationName: "storageRemediation",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

remediation_at_management_group = azure_native.policyinsights.RemediationAtManagementGroup("remediationAtManagementGroup",
    management_group_id="financeMg",
    management_groups_namespace="Microsoft.Management",
    policy_assignment_id="/providers/microsoft.management/managementGroups/financeMg/providers/microsoft.authorization/policyassignments/b101830944f246d8a14088c5",
    remediation_name="storageRemediation")

```

```yaml
resources:
  remediationAtManagementGroup:
    type: azure-native:policyinsights:RemediationAtManagementGroup
    properties:
      managementGroupId: financeMg
      managementGroupsNamespace: Microsoft.Management
      policyAssignmentId: /providers/microsoft.management/managementGroups/financeMg/providers/microsoft.authorization/policyassignments/b101830944f246d8a14088c5
      remediationName: storageRemediation

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:policyinsights:RemediationAtManagementGroup storageRemediation /providers/microsoft.management/managementGroups/financeMg/providers/microsoft.policyinsights/remediations/storageRemediation 
```
