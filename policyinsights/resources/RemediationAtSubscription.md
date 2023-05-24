The remediation definition.
API Version: 2021-10-01.
Previous API Version: 2019-07-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create remediation at subscription scope
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var remediationAtSubscription = new AzureNative.PolicyInsights.RemediationAtSubscription("remediationAtSubscription", new()
    {
        PolicyAssignmentId = "/subscriptions/35ee058e-5fa0-414c-8145-3ebb8d09b6e2/providers/microsoft.authorization/policyassignments/b101830944f246d8a14088c5",
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
		_, err := policyinsights.NewRemediationAtSubscription(ctx, "remediationAtSubscription", &policyinsights.RemediationAtSubscriptionArgs{
			PolicyAssignmentId: pulumi.String("/subscriptions/35ee058e-5fa0-414c-8145-3ebb8d09b6e2/providers/microsoft.authorization/policyassignments/b101830944f246d8a14088c5"),
			RemediationName:    pulumi.String("storageRemediation"),
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
import com.pulumi.azurenative.policyinsights.RemediationAtSubscription;
import com.pulumi.azurenative.policyinsights.RemediationAtSubscriptionArgs;
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
        var remediationAtSubscription = new RemediationAtSubscription("remediationAtSubscription", RemediationAtSubscriptionArgs.builder()        
            .policyAssignmentId("/subscriptions/35ee058e-5fa0-414c-8145-3ebb8d09b6e2/providers/microsoft.authorization/policyassignments/b101830944f246d8a14088c5")
            .remediationName("storageRemediation")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const remediationAtSubscription = new azure_native.policyinsights.RemediationAtSubscription("remediationAtSubscription", {
    policyAssignmentId: "/subscriptions/35ee058e-5fa0-414c-8145-3ebb8d09b6e2/providers/microsoft.authorization/policyassignments/b101830944f246d8a14088c5",
    remediationName: "storageRemediation",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

remediation_at_subscription = azure_native.policyinsights.RemediationAtSubscription("remediationAtSubscription",
    policy_assignment_id="/subscriptions/35ee058e-5fa0-414c-8145-3ebb8d09b6e2/providers/microsoft.authorization/policyassignments/b101830944f246d8a14088c5",
    remediation_name="storageRemediation")

```

```yaml
resources:
  remediationAtSubscription:
    type: azure-native:policyinsights:RemediationAtSubscription
    properties:
      policyAssignmentId: /subscriptions/35ee058e-5fa0-414c-8145-3ebb8d09b6e2/providers/microsoft.authorization/policyassignments/b101830944f246d8a14088c5
      remediationName: storageRemediation

```

{{% /example %}}
{{% example %}}
### Create remediation at subscription scope with all properties
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var remediationAtSubscription = new AzureNative.PolicyInsights.RemediationAtSubscription("remediationAtSubscription", new()
    {
        FailureThreshold = new AzureNative.PolicyInsights.Inputs.RemediationPropertiesFailureThresholdArgs
        {
            Percentage = 0.1,
        },
        Filters = new AzureNative.PolicyInsights.Inputs.RemediationFiltersArgs
        {
            Locations = new[]
            {
                "eastus",
                "westus",
            },
        },
        ParallelDeployments = 6,
        PolicyAssignmentId = "/subscriptions/35ee058e-5fa0-414c-8145-3ebb8d09b6e2/providers/microsoft.authorization/policyassignments/b101830944f246d8a14088c5",
        PolicyDefinitionReferenceId = "8c8fa9e4",
        RemediationName = "storageRemediation",
        ResourceCount = 42,
        ResourceDiscoveryMode = "ReEvaluateCompliance",
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
		_, err := policyinsights.NewRemediationAtSubscription(ctx, "remediationAtSubscription", &policyinsights.RemediationAtSubscriptionArgs{
			FailureThreshold: &policyinsights.RemediationPropertiesFailureThresholdArgs{
				Percentage: pulumi.Float64(0.1),
			},
			Filters: &policyinsights.RemediationFiltersArgs{
				Locations: pulumi.StringArray{
					pulumi.String("eastus"),
					pulumi.String("westus"),
				},
			},
			ParallelDeployments:         pulumi.Int(6),
			PolicyAssignmentId:          pulumi.String("/subscriptions/35ee058e-5fa0-414c-8145-3ebb8d09b6e2/providers/microsoft.authorization/policyassignments/b101830944f246d8a14088c5"),
			PolicyDefinitionReferenceId: pulumi.String("8c8fa9e4"),
			RemediationName:             pulumi.String("storageRemediation"),
			ResourceCount:               pulumi.Int(42),
			ResourceDiscoveryMode:       pulumi.String("ReEvaluateCompliance"),
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
import com.pulumi.azurenative.policyinsights.RemediationAtSubscription;
import com.pulumi.azurenative.policyinsights.RemediationAtSubscriptionArgs;
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
        var remediationAtSubscription = new RemediationAtSubscription("remediationAtSubscription", RemediationAtSubscriptionArgs.builder()        
            .failureThreshold(Map.of("percentage", 0.1))
            .filters(Map.of("locations",             
                "eastus",
                "westus"))
            .parallelDeployments(6)
            .policyAssignmentId("/subscriptions/35ee058e-5fa0-414c-8145-3ebb8d09b6e2/providers/microsoft.authorization/policyassignments/b101830944f246d8a14088c5")
            .policyDefinitionReferenceId("8c8fa9e4")
            .remediationName("storageRemediation")
            .resourceCount(42)
            .resourceDiscoveryMode("ReEvaluateCompliance")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const remediationAtSubscription = new azure_native.policyinsights.RemediationAtSubscription("remediationAtSubscription", {
    failureThreshold: {
        percentage: 0.1,
    },
    filters: {
        locations: [
            "eastus",
            "westus",
        ],
    },
    parallelDeployments: 6,
    policyAssignmentId: "/subscriptions/35ee058e-5fa0-414c-8145-3ebb8d09b6e2/providers/microsoft.authorization/policyassignments/b101830944f246d8a14088c5",
    policyDefinitionReferenceId: "8c8fa9e4",
    remediationName: "storageRemediation",
    resourceCount: 42,
    resourceDiscoveryMode: "ReEvaluateCompliance",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

remediation_at_subscription = azure_native.policyinsights.RemediationAtSubscription("remediationAtSubscription",
    failure_threshold=azure_native.policyinsights.RemediationPropertiesFailureThresholdArgs(
        percentage=0.1,
    ),
    filters=azure_native.policyinsights.RemediationFiltersArgs(
        locations=[
            "eastus",
            "westus",
        ],
    ),
    parallel_deployments=6,
    policy_assignment_id="/subscriptions/35ee058e-5fa0-414c-8145-3ebb8d09b6e2/providers/microsoft.authorization/policyassignments/b101830944f246d8a14088c5",
    policy_definition_reference_id="8c8fa9e4",
    remediation_name="storageRemediation",
    resource_count=42,
    resource_discovery_mode="ReEvaluateCompliance")

```

```yaml
resources:
  remediationAtSubscription:
    type: azure-native:policyinsights:RemediationAtSubscription
    properties:
      failureThreshold:
        percentage: 0.1
      filters:
        locations:
          - eastus
          - westus
      parallelDeployments: 6
      policyAssignmentId: /subscriptions/35ee058e-5fa0-414c-8145-3ebb8d09b6e2/providers/microsoft.authorization/policyassignments/b101830944f246d8a14088c5
      policyDefinitionReferenceId: 8c8fa9e4
      remediationName: storageRemediation
      resourceCount: 42
      resourceDiscoveryMode: ReEvaluateCompliance

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:policyinsights:RemediationAtSubscription storageRemediation /subscriptions/35ee058e-5fa0-414c-8145-3ebb8d09b6e2/providers/microsoft.policyinsights/remediations/storageRemediation 
```
