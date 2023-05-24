An environment, which is essentially an ARM template deployment.
API Version: 2018-09-15.
Previous API Version: 2018-09-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Environments_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var environment = new AzureNative.DevTestLab.Environment("environment", new()
    {
        DeploymentProperties = new AzureNative.DevTestLab.Inputs.EnvironmentDeploymentPropertiesArgs
        {
            ArmTemplateId = "/subscriptions/{subscriptionId}/resourceGroups/resourceGroupName/providers/Microsoft.DevTestLab/labs/{labName}/artifactSources/{artifactSourceName}/armTemplates/{armTemplateName}",
            Parameters = new[] {},
        },
        LabName = "{labName}",
        Name = "{environmentName}",
        ResourceGroupName = "resourceGroupName",
        UserName = "@me",
    });

});


```

```go
package main

import (
	devtestlab "github.com/pulumi/pulumi-azure-native-sdk/devtestlab"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := devtestlab.NewEnvironment(ctx, "environment", &devtestlab.EnvironmentArgs{
			DeploymentProperties: devtestlab.EnvironmentDeploymentPropertiesResponse{
				ArmTemplateId: pulumi.String("/subscriptions/{subscriptionId}/resourceGroups/resourceGroupName/providers/Microsoft.DevTestLab/labs/{labName}/artifactSources/{artifactSourceName}/armTemplates/{armTemplateName}"),
				Parameters:    devtestlab.ArmTemplateParameterPropertiesArray{},
			},
			LabName:           pulumi.String("{labName}"),
			Name:              pulumi.String("{environmentName}"),
			ResourceGroupName: pulumi.String("resourceGroupName"),
			UserName:          pulumi.String("@me"),
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
import com.pulumi.azurenative.devtestlab.Environment;
import com.pulumi.azurenative.devtestlab.EnvironmentArgs;
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
        var environment = new Environment("environment", EnvironmentArgs.builder()        
            .deploymentProperties(Map.ofEntries(
                Map.entry("armTemplateId", "/subscriptions/{subscriptionId}/resourceGroups/resourceGroupName/providers/Microsoft.DevTestLab/labs/{labName}/artifactSources/{artifactSourceName}/armTemplates/{armTemplateName}"),
                Map.entry("parameters", )
            ))
            .labName("{labName}")
            .name("{environmentName}")
            .resourceGroupName("resourceGroupName")
            .userName("@me")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const environment = new azure_native.devtestlab.Environment("environment", {
    deploymentProperties: {
        armTemplateId: "/subscriptions/{subscriptionId}/resourceGroups/resourceGroupName/providers/Microsoft.DevTestLab/labs/{labName}/artifactSources/{artifactSourceName}/armTemplates/{armTemplateName}",
        parameters: [],
    },
    labName: "{labName}",
    name: "{environmentName}",
    resourceGroupName: "resourceGroupName",
    userName: "@me",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

environment = azure_native.devtestlab.Environment("environment",
    deployment_properties=azure_native.devtestlab.EnvironmentDeploymentPropertiesResponseArgs(
        arm_template_id="/subscriptions/{subscriptionId}/resourceGroups/resourceGroupName/providers/Microsoft.DevTestLab/labs/{labName}/artifactSources/{artifactSourceName}/armTemplates/{armTemplateName}",
        parameters=[],
    ),
    lab_name="{labName}",
    name="{environmentName}",
    resource_group_name="resourceGroupName",
    user_name="@me")

```

```yaml
resources:
  environment:
    type: azure-native:devtestlab:Environment
    properties:
      deploymentProperties:
        armTemplateId: /subscriptions/{subscriptionId}/resourceGroups/resourceGroupName/providers/Microsoft.DevTestLab/labs/{labName}/artifactSources/{artifactSourceName}/armTemplates/{armTemplateName}
        parameters: []
      labName: '{labName}'
      name: '{environmentName}'
      resourceGroupName: resourceGroupName
      userName: '@me'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devtestlab:Environment {environmentName} /subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}/users/{uniqueIdentifier}/environments/{environmentName} 
```
