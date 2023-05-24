An attestation resource.
API Version: 2022-09-01.
Previous API Version: 2021-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create attestation at resource group scope
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var attestationAtResourceGroup = new AzureNative.PolicyInsights.AttestationAtResourceGroup("attestationAtResourceGroup", new()
    {
        AssessmentDate = "2021-06-10T00:00:00Z",
        AttestationName = "790996e6-9871-4b1f-9cd9-ec42cd6ced1e",
        Comments = "This subscription has passed a security audit.",
        ComplianceState = "Compliant",
        Evidence = new[]
        {
            new AzureNative.PolicyInsights.Inputs.AttestationEvidenceArgs
            {
                Description = "The results of the security audit.",
                SourceUri = "https://gist.github.com/contoso/9573e238762c60166c090ae16b814011",
            },
        },
        ExpiresOn = "2021-06-15T00:00:00Z",
        Metadata = 
        {
            { "departmentId", "NYC-MARKETING-1" },
        },
        Owner = "55a32e28-3aa5-4eea-9b5a-4cd85153b966",
        PolicyAssignmentId = "/subscriptions/35ee058e-5fa0-414c-8145-3ebb8d09b6e2/providers/microsoft.authorization/policyassignments/b101830944f246d8a14088c5",
        PolicyDefinitionReferenceId = "0b158b46-ff42-4799-8e39-08a5c23b4551",
        ResourceGroupName = "myRg",
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
		_, err := policyinsights.NewAttestationAtResourceGroup(ctx, "attestationAtResourceGroup", &policyinsights.AttestationAtResourceGroupArgs{
			AssessmentDate:  pulumi.String("2021-06-10T00:00:00Z"),
			AttestationName: pulumi.String("790996e6-9871-4b1f-9cd9-ec42cd6ced1e"),
			Comments:        pulumi.String("This subscription has passed a security audit."),
			ComplianceState: pulumi.String("Compliant"),
			Evidence: []policyinsights.AttestationEvidenceArgs{
				{
					Description: pulumi.String("The results of the security audit."),
					SourceUri:   pulumi.String("https://gist.github.com/contoso/9573e238762c60166c090ae16b814011"),
				},
			},
			ExpiresOn: pulumi.String("2021-06-15T00:00:00Z"),
			Metadata: pulumi.Any{
				DepartmentId: "NYC-MARKETING-1",
			},
			Owner:                       pulumi.String("55a32e28-3aa5-4eea-9b5a-4cd85153b966"),
			PolicyAssignmentId:          pulumi.String("/subscriptions/35ee058e-5fa0-414c-8145-3ebb8d09b6e2/providers/microsoft.authorization/policyassignments/b101830944f246d8a14088c5"),
			PolicyDefinitionReferenceId: pulumi.String("0b158b46-ff42-4799-8e39-08a5c23b4551"),
			ResourceGroupName:           pulumi.String("myRg"),
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
import com.pulumi.azurenative.policyinsights.AttestationAtResourceGroup;
import com.pulumi.azurenative.policyinsights.AttestationAtResourceGroupArgs;
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
        var attestationAtResourceGroup = new AttestationAtResourceGroup("attestationAtResourceGroup", AttestationAtResourceGroupArgs.builder()        
            .assessmentDate("2021-06-10T00:00:00Z")
            .attestationName("790996e6-9871-4b1f-9cd9-ec42cd6ced1e")
            .comments("This subscription has passed a security audit.")
            .complianceState("Compliant")
            .evidence(Map.ofEntries(
                Map.entry("description", "The results of the security audit."),
                Map.entry("sourceUri", "https://gist.github.com/contoso/9573e238762c60166c090ae16b814011")
            ))
            .expiresOn("2021-06-15T00:00:00Z")
            .metadata(Map.of("departmentId", "NYC-MARKETING-1"))
            .owner("55a32e28-3aa5-4eea-9b5a-4cd85153b966")
            .policyAssignmentId("/subscriptions/35ee058e-5fa0-414c-8145-3ebb8d09b6e2/providers/microsoft.authorization/policyassignments/b101830944f246d8a14088c5")
            .policyDefinitionReferenceId("0b158b46-ff42-4799-8e39-08a5c23b4551")
            .resourceGroupName("myRg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const attestationAtResourceGroup = new azure_native.policyinsights.AttestationAtResourceGroup("attestationAtResourceGroup", {
    assessmentDate: "2021-06-10T00:00:00Z",
    attestationName: "790996e6-9871-4b1f-9cd9-ec42cd6ced1e",
    comments: "This subscription has passed a security audit.",
    complianceState: "Compliant",
    evidence: [{
        description: "The results of the security audit.",
        sourceUri: "https://gist.github.com/contoso/9573e238762c60166c090ae16b814011",
    }],
    expiresOn: "2021-06-15T00:00:00Z",
    metadata: {
        departmentId: "NYC-MARKETING-1",
    },
    owner: "55a32e28-3aa5-4eea-9b5a-4cd85153b966",
    policyAssignmentId: "/subscriptions/35ee058e-5fa0-414c-8145-3ebb8d09b6e2/providers/microsoft.authorization/policyassignments/b101830944f246d8a14088c5",
    policyDefinitionReferenceId: "0b158b46-ff42-4799-8e39-08a5c23b4551",
    resourceGroupName: "myRg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

attestation_at_resource_group = azure_native.policyinsights.AttestationAtResourceGroup("attestationAtResourceGroup",
    assessment_date="2021-06-10T00:00:00Z",
    attestation_name="790996e6-9871-4b1f-9cd9-ec42cd6ced1e",
    comments="This subscription has passed a security audit.",
    compliance_state="Compliant",
    evidence=[azure_native.policyinsights.AttestationEvidenceArgs(
        description="The results of the security audit.",
        source_uri="https://gist.github.com/contoso/9573e238762c60166c090ae16b814011",
    )],
    expires_on="2021-06-15T00:00:00Z",
    metadata={
        "departmentId": "NYC-MARKETING-1",
    },
    owner="55a32e28-3aa5-4eea-9b5a-4cd85153b966",
    policy_assignment_id="/subscriptions/35ee058e-5fa0-414c-8145-3ebb8d09b6e2/providers/microsoft.authorization/policyassignments/b101830944f246d8a14088c5",
    policy_definition_reference_id="0b158b46-ff42-4799-8e39-08a5c23b4551",
    resource_group_name="myRg")

```

```yaml
resources:
  attestationAtResourceGroup:
    type: azure-native:policyinsights:AttestationAtResourceGroup
    properties:
      assessmentDate: 2021-06-10T00:00:00Z
      attestationName: 790996e6-9871-4b1f-9cd9-ec42cd6ced1e
      comments: This subscription has passed a security audit.
      complianceState: Compliant
      evidence:
        - description: The results of the security audit.
          sourceUri: https://gist.github.com/contoso/9573e238762c60166c090ae16b814011
      expiresOn: 2021-06-15T00:00:00Z
      metadata:
        departmentId: NYC-MARKETING-1
      owner: 55a32e28-3aa5-4eea-9b5a-4cd85153b966
      policyAssignmentId: /subscriptions/35ee058e-5fa0-414c-8145-3ebb8d09b6e2/providers/microsoft.authorization/policyassignments/b101830944f246d8a14088c5
      policyDefinitionReferenceId: 0b158b46-ff42-4799-8e39-08a5c23b4551
      resourceGroupName: myRg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:policyinsights:AttestationAtResourceGroup 790996e6-9871-4b1f-9cd9-ec42cd6ced1e /subscriptions/35ee058e-5fa0-414c-8145-3ebb8d09b6e2/resourcegroups/myrg/providers/microsoft.policyinsights/attestations/790996e6-9871-4b1f-9cd9-ec42cd6ced1e 
```
