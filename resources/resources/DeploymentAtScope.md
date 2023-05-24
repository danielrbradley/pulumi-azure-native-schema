Deployment information.
API Version: 2022-09-01.
Previous API Version: 2021-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create deployment at a given scope.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var deploymentAtScope = new AzureNative.Resources.DeploymentAtScope("deploymentAtScope", new()
    {
        DeploymentName = "my-deployment",
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
        Scope = "providers/Microsoft.Management/managementGroups/my-management-group-id",
        Tags = 
        {
            { "tagKey1", "tag-value-1" },
            { "tagKey2", "tag-value-2" },
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
		_, err := resources.NewDeploymentAtScope(ctx, "deploymentAtScope", &resources.DeploymentAtScopeArgs{
			DeploymentName: pulumi.String("my-deployment"),
			Location:       pulumi.String("eastus"),
			Properties: resources.DeploymentPropertiesExtendedResponse{
				Mode:       resources.DeploymentModeIncremental,
				Parameters: nil,
				TemplateLink: &resources.TemplateLinkArgs{
					Uri: pulumi.String("https://example.com/exampleTemplate.json"),
				},
			},
			Scope: pulumi.String("providers/Microsoft.Management/managementGroups/my-management-group-id"),
			Tags: pulumi.StringMap{
				"tagKey1": pulumi.String("tag-value-1"),
				"tagKey2": pulumi.String("tag-value-2"),
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
import com.pulumi.azurenative.resources.DeploymentAtScope;
import com.pulumi.azurenative.resources.DeploymentAtScopeArgs;
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
        var deploymentAtScope = new DeploymentAtScope("deploymentAtScope", DeploymentAtScopeArgs.builder()        
            .deploymentName("my-deployment")
            .location("eastus")
            .properties(Map.ofEntries(
                Map.entry("mode", "Incremental"),
                Map.entry("parameters", ),
                Map.entry("templateLink", Map.of("uri", "https://example.com/exampleTemplate.json"))
            ))
            .scope("providers/Microsoft.Management/managementGroups/my-management-group-id")
            .tags(Map.ofEntries(
                Map.entry("tagKey1", "tag-value-1"),
                Map.entry("tagKey2", "tag-value-2")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const deploymentAtScope = new azure_native.resources.DeploymentAtScope("deploymentAtScope", {
    deploymentName: "my-deployment",
    location: "eastus",
    properties: {
        mode: azure_native.resources.DeploymentMode.Incremental,
        parameters: {},
        templateLink: {
            uri: "https://example.com/exampleTemplate.json",
        },
    },
    scope: "providers/Microsoft.Management/managementGroups/my-management-group-id",
    tags: {
        tagKey1: "tag-value-1",
        tagKey2: "tag-value-2",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

deployment_at_scope = azure_native.resources.DeploymentAtScope("deploymentAtScope",
    deployment_name="my-deployment",
    location="eastus",
    properties=azure_native.resources.DeploymentPropertiesExtendedResponseArgs(
        mode=azure_native.resources.DeploymentMode.INCREMENTAL,
        parameters={},
        template_link=azure_native.resources.TemplateLinkArgs(
            uri="https://example.com/exampleTemplate.json",
        ),
    ),
    scope="providers/Microsoft.Management/managementGroups/my-management-group-id",
    tags={
        "tagKey1": "tag-value-1",
        "tagKey2": "tag-value-2",
    })

```

```yaml
resources:
  deploymentAtScope:
    type: azure-native:resources:DeploymentAtScope
    properties:
      deploymentName: my-deployment
      location: eastus
      properties:
        mode: Incremental
        parameters: {}
        templateLink:
          uri: https://example.com/exampleTemplate.json
      scope: providers/Microsoft.Management/managementGroups/my-management-group-id
      tags:
        tagKey1: tag-value-1
        tagKey2: tag-value-2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:resources:DeploymentAtScope my-deployment /providers/Microsoft.Management/managementGroups/my-management-group-id/providers/Microsoft.Resources/deployments/my-deployment 
```
