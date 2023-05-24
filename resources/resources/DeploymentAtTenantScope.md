Deployment information.
API Version: 2022-09-01.
Previous API Version: 2021-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create deployment at tenant scope.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var deploymentAtTenantScope = new AzureNative.Resources.DeploymentAtTenantScope("deploymentAtTenantScope", new()
    {
        DeploymentName = "tenant-dep01",
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
		_, err := resources.NewDeploymentAtTenantScope(ctx, "deploymentAtTenantScope", &resources.DeploymentAtTenantScopeArgs{
			DeploymentName: pulumi.String("tenant-dep01"),
			Location:       pulumi.String("eastus"),
			Properties: resources.DeploymentPropertiesExtendedResponse{
				Mode:       resources.DeploymentModeIncremental,
				Parameters: nil,
				TemplateLink: &resources.TemplateLinkArgs{
					Uri: pulumi.String("https://example.com/exampleTemplate.json"),
				},
			},
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
import com.pulumi.azurenative.resources.DeploymentAtTenantScope;
import com.pulumi.azurenative.resources.DeploymentAtTenantScopeArgs;
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
        var deploymentAtTenantScope = new DeploymentAtTenantScope("deploymentAtTenantScope", DeploymentAtTenantScopeArgs.builder()        
            .deploymentName("tenant-dep01")
            .location("eastus")
            .properties(Map.ofEntries(
                Map.entry("mode", "Incremental"),
                Map.entry("parameters", ),
                Map.entry("templateLink", Map.of("uri", "https://example.com/exampleTemplate.json"))
            ))
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

const deploymentAtTenantScope = new azure_native.resources.DeploymentAtTenantScope("deploymentAtTenantScope", {
    deploymentName: "tenant-dep01",
    location: "eastus",
    properties: {
        mode: azure_native.resources.DeploymentMode.Incremental,
        parameters: {},
        templateLink: {
            uri: "https://example.com/exampleTemplate.json",
        },
    },
    tags: {
        tagKey1: "tag-value-1",
        tagKey2: "tag-value-2",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

deployment_at_tenant_scope = azure_native.resources.DeploymentAtTenantScope("deploymentAtTenantScope",
    deployment_name="tenant-dep01",
    location="eastus",
    properties=azure_native.resources.DeploymentPropertiesExtendedResponseArgs(
        mode=azure_native.resources.DeploymentMode.INCREMENTAL,
        parameters={},
        template_link=azure_native.resources.TemplateLinkArgs(
            uri="https://example.com/exampleTemplate.json",
        ),
    ),
    tags={
        "tagKey1": "tag-value-1",
        "tagKey2": "tag-value-2",
    })

```

```yaml
resources:
  deploymentAtTenantScope:
    type: azure-native:resources:DeploymentAtTenantScope
    properties:
      deploymentName: tenant-dep01
      location: eastus
      properties:
        mode: Incremental
        parameters: {}
        templateLink:
          uri: https://example.com/exampleTemplate.json
      tags:
        tagKey1: tag-value-1
        tagKey2: tag-value-2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:resources:DeploymentAtTenantScope tenant-dep01 /providers/Microsoft.Resources/deployments/tenant-dep01 
```
