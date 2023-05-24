Security assessment on a resource - response format
API Version: 2021-06-01.
Previous API Version: 2020-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create security recommendation task on a resource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var assessment = new AzureNative.Security.Assessment("assessment", new()
    {
        AssessmentName = "8bb8be0a-6010-4789-812f-e4d661c4ed0e",
        ResourceDetails = new AzureNative.Security.Inputs.AzureResourceDetailsArgs
        {
            Source = "Azure",
        },
        ResourceId = "subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/myRg/providers/Microsoft.Compute/virtualMachineScaleSets/vmss2",
        Status = new AzureNative.Security.Inputs.AssessmentStatusArgs
        {
            Code = "Healthy",
        },
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
		_, err := security.NewAssessment(ctx, "assessment", &security.AssessmentArgs{
			AssessmentName: pulumi.String("8bb8be0a-6010-4789-812f-e4d661c4ed0e"),
			ResourceDetails: security.AzureResourceDetails{
				Source: "Azure",
			},
			ResourceId: pulumi.String("subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/myRg/providers/Microsoft.Compute/virtualMachineScaleSets/vmss2"),
			Status: &security.AssessmentStatusArgs{
				Code: pulumi.String("Healthy"),
			},
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
import com.pulumi.azurenative.security.Assessment;
import com.pulumi.azurenative.security.AssessmentArgs;
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
        var assessment = new Assessment("assessment", AssessmentArgs.builder()        
            .assessmentName("8bb8be0a-6010-4789-812f-e4d661c4ed0e")
            .resourceDetails(Map.of("source", "Azure"))
            .resourceId("subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/myRg/providers/Microsoft.Compute/virtualMachineScaleSets/vmss2")
            .status(Map.of("code", "Healthy"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const assessment = new azure_native.security.Assessment("assessment", {
    assessmentName: "8bb8be0a-6010-4789-812f-e4d661c4ed0e",
    resourceDetails: {
        source: "Azure",
    },
    resourceId: "subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/myRg/providers/Microsoft.Compute/virtualMachineScaleSets/vmss2",
    status: {
        code: "Healthy",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

assessment = azure_native.security.Assessment("assessment",
    assessment_name="8bb8be0a-6010-4789-812f-e4d661c4ed0e",
    resource_details=azure_native.security.AzureResourceDetailsArgs(
        source="Azure",
    ),
    resource_id="subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/myRg/providers/Microsoft.Compute/virtualMachineScaleSets/vmss2",
    status=azure_native.security.AssessmentStatusArgs(
        code="Healthy",
    ))

```

```yaml
resources:
  assessment:
    type: azure-native:security:Assessment
    properties:
      assessmentName: 8bb8be0a-6010-4789-812f-e4d661c4ed0e
      resourceDetails:
        source: Azure
      resourceId: subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/myRg/providers/Microsoft.Compute/virtualMachineScaleSets/vmss2
      status:
        code: Healthy

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:security:Assessment 8bb8be0a-6010-4789-812f-e4d661c4ed0e /subscriptions/20ff7fc3-e762-44dd-bd96-b71116dcdc23/resourceGroups/myRg/providers/Microsoft.Compute/virtualMachineScaleSets/vmss1/providers/Microsoft.Security/assessments/8bb8be0a-6010-4789-812f-e4d661c4ed0e 
```
