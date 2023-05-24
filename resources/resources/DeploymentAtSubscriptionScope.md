Deployment information.
API Version: 2022-09-01.
Previous API Version: 2021-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a deployment that will deploy a templateSpec with the given resourceId
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var deploymentAtSubscriptionScope = new AzureNative.Resources.DeploymentAtSubscriptionScope("deploymentAtSubscriptionScope", new()
    {
        DeploymentName = "my-deployment",
        Location = "eastus",
        Properties = new AzureNative.Resources.Inputs.DeploymentPropertiesArgs
        {
            Mode = AzureNative.Resources.DeploymentMode.Incremental,
            Parameters = null,
            TemplateLink = new AzureNative.Resources.Inputs.TemplateLinkArgs
            {
                Id = "/subscriptions/00000000-0000-0000-0000-000000000001/resourceGroups/my-resource-group/providers/Microsoft.Resources/TemplateSpecs/TemplateSpec-Name/versions/v1",
            },
        },
    });

});


```

```go
package main

import (
	resources "github.com/pulumi/pulumi-azure-native-sdk/resources"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := resources.NewDeploymentAtSubscriptionScope(ctx, "deploymentAtSubscriptionScope", &resources.DeploymentAtSubscriptionScopeArgs{
			DeploymentName: pulumi.String("my-deployment"),
			Location:       pulumi.String("eastus"),
			Properties: resources.DeploymentPropertiesExtendedResponse{
				Mode:       resources.DeploymentModeIncremental,
				Parameters: nil,
				TemplateLink: &resources.TemplateLinkArgs{
					Id: pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000001/resourceGroups/my-resource-group/providers/Microsoft.Resources/TemplateSpecs/TemplateSpec-Name/versions/v1"),
				},
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
import com.pulumi.azurenative.resources.DeploymentAtSubscriptionScope;
import com.pulumi.azurenative.resources.DeploymentAtSubscriptionScopeArgs;
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
        var deploymentAtSubscriptionScope = new DeploymentAtSubscriptionScope("deploymentAtSubscriptionScope", DeploymentAtSubscriptionScopeArgs.builder()        
            .deploymentName("my-deployment")
            .location("eastus")
            .properties(Map.ofEntries(
                Map.entry("mode", "Incremental"),
                Map.entry("parameters", ),
                Map.entry("templateLink", Map.of("id", "/subscriptions/00000000-0000-0000-0000-000000000001/resourceGroups/my-resource-group/providers/Microsoft.Resources/TemplateSpecs/TemplateSpec-Name/versions/v1"))
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const deploymentAtSubscriptionScope = new azure_native.resources.DeploymentAtSubscriptionScope("deploymentAtSubscriptionScope", {
    deploymentName: "my-deployment",
    location: "eastus",
    properties: {
        mode: azure_native.resources.DeploymentMode.Incremental,
        parameters: {},
        templateLink: {
            id: "/subscriptions/00000000-0000-0000-0000-000000000001/resourceGroups/my-resource-group/providers/Microsoft.Resources/TemplateSpecs/TemplateSpec-Name/versions/v1",
        },
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

deployment_at_subscription_scope = azure_native.resources.DeploymentAtSubscriptionScope("deploymentAtSubscriptionScope",
    deployment_name="my-deployment",
    location="eastus",
    properties=azure_native.resources.DeploymentPropertiesExtendedResponseArgs(
        mode=azure_native.resources.DeploymentMode.INCREMENTAL,
        parameters={},
        template_link=azure_native.resources.TemplateLinkArgs(
            id="/subscriptions/00000000-0000-0000-0000-000000000001/resourceGroups/my-resource-group/providers/Microsoft.Resources/TemplateSpecs/TemplateSpec-Name/versions/v1",
        ),
    ))

```

```yaml
resources:
  deploymentAtSubscriptionScope:
    type: azure-native:resources:DeploymentAtSubscriptionScope
    properties:
      deploymentName: my-deployment
      location: eastus
      properties:
        mode: Incremental
        parameters: {}
        templateLink:
          id: /subscriptions/00000000-0000-0000-0000-000000000001/resourceGroups/my-resource-group/providers/Microsoft.Resources/TemplateSpecs/TemplateSpec-Name/versions/v1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:resources:DeploymentAtSubscriptionScope my-deployment /subscriptions/00000000-0000-0000-0000-000000000001/providers/Microsoft.Resources/deployments/my-deployment 
```
