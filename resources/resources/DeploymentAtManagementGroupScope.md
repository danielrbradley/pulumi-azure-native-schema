Deployment information.
API Version: 2022-09-01.
Previous API Version: 2021-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create deployment at management group scope.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var deploymentAtManagementGroupScope = new AzureNative.Resources.DeploymentAtManagementGroupScope("deploymentAtManagementGroupScope", new()
    {
        DeploymentName = "my-deployment",
        GroupId = "my-management-group-id",
        Location = "eastus",
        Properties = new AzureNative.Resources.Inputs.DeploymentPropertiesArgs
        {
            Mode = AzureNative.Resources.DeploymentMode.Incremental,
            Parameters = null,
            TemplateLink = new AzureNative.Resources.Inputs.TemplateLinkArgs
            {
                Uri = "https://example.com/exampleTemplate.json",
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
		_, err := resources.NewDeploymentAtManagementGroupScope(ctx, "deploymentAtManagementGroupScope", &resources.DeploymentAtManagementGroupScopeArgs{
			DeploymentName: pulumi.String("my-deployment"),
			GroupId:        pulumi.String("my-management-group-id"),
			Location:       pulumi.String("eastus"),
			Properties: resources.DeploymentPropertiesExtendedResponse{
				Mode:       resources.DeploymentModeIncremental,
				Parameters: nil,
				TemplateLink: &resources.TemplateLinkArgs{
					Uri: pulumi.String("https://example.com/exampleTemplate.json"),
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
import com.pulumi.azurenative.resources.DeploymentAtManagementGroupScope;
import com.pulumi.azurenative.resources.DeploymentAtManagementGroupScopeArgs;
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
        var deploymentAtManagementGroupScope = new DeploymentAtManagementGroupScope("deploymentAtManagementGroupScope", DeploymentAtManagementGroupScopeArgs.builder()        
            .deploymentName("my-deployment")
            .groupId("my-management-group-id")
            .location("eastus")
            .properties(Map.ofEntries(
                Map.entry("mode", "Incremental"),
                Map.entry("parameters", ),
                Map.entry("templateLink", Map.of("uri", "https://example.com/exampleTemplate.json"))
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const deploymentAtManagementGroupScope = new azure_native.resources.DeploymentAtManagementGroupScope("deploymentAtManagementGroupScope", {
    deploymentName: "my-deployment",
    groupId: "my-management-group-id",
    location: "eastus",
    properties: {
        mode: azure_native.resources.DeploymentMode.Incremental,
        parameters: {},
        templateLink: {
            uri: "https://example.com/exampleTemplate.json",
        },
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

deployment_at_management_group_scope = azure_native.resources.DeploymentAtManagementGroupScope("deploymentAtManagementGroupScope",
    deployment_name="my-deployment",
    group_id="my-management-group-id",
    location="eastus",
    properties=azure_native.resources.DeploymentPropertiesExtendedResponseArgs(
        mode=azure_native.resources.DeploymentMode.INCREMENTAL,
        parameters={},
        template_link=azure_native.resources.TemplateLinkArgs(
            uri="https://example.com/exampleTemplate.json",
        ),
    ))

```

```yaml
resources:
  deploymentAtManagementGroupScope:
    type: azure-native:resources:DeploymentAtManagementGroupScope
    properties:
      deploymentName: my-deployment
      groupId: my-management-group-id
      location: eastus
      properties:
        mode: Incremental
        parameters: {}
        templateLink:
          uri: https://example.com/exampleTemplate.json

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:resources:DeploymentAtManagementGroupScope my-deployment /providers/Microsoft.Management/managementGroups/my-management-group-id/providers/Microsoft.Resources/deployments/my-deployment 
```
