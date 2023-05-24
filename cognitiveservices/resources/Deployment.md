Cognitive Services account deployment.
API Version: 2022-12-01.
Previous API Version: 2021-10-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PutDeployment
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var deployment = new AzureNative.CognitiveServices.Deployment("deployment", new()
    {
        AccountName = "accountName",
        DeploymentName = "deploymentName",
        Properties = new AzureNative.CognitiveServices.Inputs.DeploymentPropertiesArgs
        {
            Model = new AzureNative.CognitiveServices.Inputs.DeploymentModelArgs
            {
                Format = "OpenAI",
                Name = "ada",
                Version = "1",
            },
            ScaleSettings = new AzureNative.CognitiveServices.Inputs.DeploymentScaleSettingsArgs
            {
                Capacity = 1,
                ScaleType = "Manual",
            },
        },
        ResourceGroupName = "resourceGroupName",
    });

});


```

```go
package main

import (
	cognitiveservices "github.com/pulumi/pulumi-azure-native-sdk/cognitiveservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := cognitiveservices.NewDeployment(ctx, "deployment", &cognitiveservices.DeploymentArgs{
			AccountName:    pulumi.String("accountName"),
			DeploymentName: pulumi.String("deploymentName"),
			Properties: cognitiveservices.DeploymentPropertiesResponse{
				Model: &cognitiveservices.DeploymentModelArgs{
					Format:  pulumi.String("OpenAI"),
					Name:    pulumi.String("ada"),
					Version: pulumi.String("1"),
				},
				ScaleSettings: &cognitiveservices.DeploymentScaleSettingsArgs{
					Capacity:  pulumi.Int(1),
					ScaleType: pulumi.String("Manual"),
				},
			},
			ResourceGroupName: pulumi.String("resourceGroupName"),
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
import com.pulumi.azurenative.cognitiveservices.Deployment;
import com.pulumi.azurenative.cognitiveservices.DeploymentArgs;
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
        var deployment = new Deployment("deployment", DeploymentArgs.builder()        
            .accountName("accountName")
            .deploymentName("deploymentName")
            .properties(Map.ofEntries(
                Map.entry("model", Map.ofEntries(
                    Map.entry("format", "OpenAI"),
                    Map.entry("name", "ada"),
                    Map.entry("version", "1")
                )),
                Map.entry("scaleSettings", Map.ofEntries(
                    Map.entry("capacity", 1),
                    Map.entry("scaleType", "Manual")
                ))
            ))
            .resourceGroupName("resourceGroupName")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const deployment = new azure_native.cognitiveservices.Deployment("deployment", {
    accountName: "accountName",
    deploymentName: "deploymentName",
    properties: {
        model: {
            format: "OpenAI",
            name: "ada",
            version: "1",
        },
        scaleSettings: {
            capacity: 1,
            scaleType: "Manual",
        },
    },
    resourceGroupName: "resourceGroupName",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

deployment = azure_native.cognitiveservices.Deployment("deployment",
    account_name="accountName",
    deployment_name="deploymentName",
    properties=azure_native.cognitiveservices.DeploymentPropertiesResponseArgs(
        model=azure_native.cognitiveservices.DeploymentModelArgs(
            format="OpenAI",
            name="ada",
            version="1",
        ),
        scale_settings=azure_native.cognitiveservices.DeploymentScaleSettingsArgs(
            capacity=1,
            scale_type="Manual",
        ),
    ),
    resource_group_name="resourceGroupName")

```

```yaml
resources:
  deployment:
    type: azure-native:cognitiveservices:Deployment
    properties:
      accountName: accountName
      deploymentName: deploymentName
      properties:
        model:
          format: OpenAI
          name: ada
          version: '1'
        scaleSettings:
          capacity: 1
          scaleType: Manual
      resourceGroupName: resourceGroupName

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:cognitiveservices:Deployment deploymentName /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.CognitiveServices/accounts/accountName/deployments/deploymentName 
```
