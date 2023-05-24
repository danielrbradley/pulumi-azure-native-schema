Security assessment metadata response
API Version: 2021-06-01.
Previous API Version: 2020-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create security assessment metadata for subscription
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var assessmentMetadataInSubscription = new AzureNative.Security.AssessmentMetadataInSubscription("assessmentMetadataInSubscription", new()
    {
        AssessmentMetadataName = "ca039e75-a276-4175-aebc-bcd41e4b14b7",
        AssessmentType = "CustomerManaged",
        Categories = new[]
        {
            "Compute",
        },
        Description = "Install an endpoint protection solution on your virtual machines scale sets, to protect them from threats and vulnerabilities.",
        DisplayName = "Install endpoint protection solution on virtual machine scale sets",
        ImplementationEffort = "Low",
        RemediationDescription = "To install an endpoint protection solution: 1.  <a href=\"https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-faq#how-do-i-turn-on-antimalware-in-my-virtual-machine-scale-set\">Follow the instructions in How do I turn on antimalware in my virtual machine scale set</a>",
        Severity = "Medium",
        Threats = new[]
        {
            "dataExfiltration",
            "dataSpillage",
            "maliciousInsider",
        },
        UserImpact = "Low",
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
		_, err := security.NewAssessmentMetadataInSubscription(ctx, "assessmentMetadataInSubscription", &security.AssessmentMetadataInSubscriptionArgs{
			AssessmentMetadataName: pulumi.String("ca039e75-a276-4175-aebc-bcd41e4b14b7"),
			AssessmentType:         pulumi.String("CustomerManaged"),
			Categories: pulumi.StringArray{
				pulumi.String("Compute"),
			},
			Description:            pulumi.String("Install an endpoint protection solution on your virtual machines scale sets, to protect them from threats and vulnerabilities."),
			DisplayName:            pulumi.String("Install endpoint protection solution on virtual machine scale sets"),
			ImplementationEffort:   pulumi.String("Low"),
			RemediationDescription: pulumi.String("To install an endpoint protection solution: 1.  <a href=\"https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-faq#how-do-i-turn-on-antimalware-in-my-virtual-machine-scale-set\">Follow the instructions in How do I turn on antimalware in my virtual machine scale set</a>"),
			Severity:               pulumi.String("Medium"),
			Threats: pulumi.StringArray{
				pulumi.String("dataExfiltration"),
				pulumi.String("dataSpillage"),
				pulumi.String("maliciousInsider"),
			},
			UserImpact: pulumi.String("Low"),
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
import com.pulumi.azurenative.security.AssessmentMetadataInSubscription;
import com.pulumi.azurenative.security.AssessmentMetadataInSubscriptionArgs;
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
        var assessmentMetadataInSubscription = new AssessmentMetadataInSubscription("assessmentMetadataInSubscription", AssessmentMetadataInSubscriptionArgs.builder()        
            .assessmentMetadataName("ca039e75-a276-4175-aebc-bcd41e4b14b7")
            .assessmentType("CustomerManaged")
            .categories("Compute")
            .description("Install an endpoint protection solution on your virtual machines scale sets, to protect them from threats and vulnerabilities.")
            .displayName("Install endpoint protection solution on virtual machine scale sets")
            .implementationEffort("Low")
            .remediationDescription("To install an endpoint protection solution: 1.  <a href=\"https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-faq#how-do-i-turn-on-antimalware-in-my-virtual-machine-scale-set\">Follow the instructions in How do I turn on antimalware in my virtual machine scale set</a>")
            .severity("Medium")
            .threats(            
                "dataExfiltration",
                "dataSpillage",
                "maliciousInsider")
            .userImpact("Low")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const assessmentMetadataInSubscription = new azure_native.security.AssessmentMetadataInSubscription("assessmentMetadataInSubscription", {
    assessmentMetadataName: "ca039e75-a276-4175-aebc-bcd41e4b14b7",
    assessmentType: "CustomerManaged",
    categories: ["Compute"],
    description: "Install an endpoint protection solution on your virtual machines scale sets, to protect them from threats and vulnerabilities.",
    displayName: "Install endpoint protection solution on virtual machine scale sets",
    implementationEffort: "Low",
    remediationDescription: "To install an endpoint protection solution: 1.  <a href=\"https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-faq#how-do-i-turn-on-antimalware-in-my-virtual-machine-scale-set\">Follow the instructions in How do I turn on antimalware in my virtual machine scale set</a>",
    severity: "Medium",
    threats: [
        "dataExfiltration",
        "dataSpillage",
        "maliciousInsider",
    ],
    userImpact: "Low",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

assessment_metadata_in_subscription = azure_native.security.AssessmentMetadataInSubscription("assessmentMetadataInSubscription",
    assessment_metadata_name="ca039e75-a276-4175-aebc-bcd41e4b14b7",
    assessment_type="CustomerManaged",
    categories=["Compute"],
    description="Install an endpoint protection solution on your virtual machines scale sets, to protect them from threats and vulnerabilities.",
    display_name="Install endpoint protection solution on virtual machine scale sets",
    implementation_effort="Low",
    remediation_description="To install an endpoint protection solution: 1.  <a href=\"https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-faq#how-do-i-turn-on-antimalware-in-my-virtual-machine-scale-set\">Follow the instructions in How do I turn on antimalware in my virtual machine scale set</a>",
    severity="Medium",
    threats=[
        "dataExfiltration",
        "dataSpillage",
        "maliciousInsider",
    ],
    user_impact="Low")

```

```yaml
resources:
  assessmentMetadataInSubscription:
    type: azure-native:security:AssessmentMetadataInSubscription
    properties:
      assessmentMetadataName: ca039e75-a276-4175-aebc-bcd41e4b14b7
      assessmentType: CustomerManaged
      categories:
        - Compute
      description: Install an endpoint protection solution on your virtual machines scale sets, to protect them from threats and vulnerabilities.
      displayName: Install endpoint protection solution on virtual machine scale sets
      implementationEffort: Low
      remediationDescription: 'To install an endpoint protection solution: 1.  <a href="https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-faq#how-do-i-turn-on-antimalware-in-my-virtual-machine-scale-set">Follow the instructions in How do I turn on antimalware in my virtual machine scale set</a>'
      severity: Medium
      threats:
        - dataExfiltration
        - dataSpillage
        - maliciousInsider
      userImpact: Low

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:security:AssessmentMetadataInSubscription ca039e75-a276-4175-aebc-bcd41e4b14b7 /providers/Microsoft.Security/assessmentMetadata/ca039e75-a276-4175-aebc-bcd41e4b14b7 
```
