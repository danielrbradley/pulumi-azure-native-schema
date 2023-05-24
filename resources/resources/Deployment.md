Deployment information.
API Version: 2022-09-01.
Previous API Version: 2021-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a deployment that will deploy a template with a uri and queryString
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var deployment = new AzureNative.Resources.Deployment("deployment", new()
    {
        DeploymentName = "my-deployment",
        Properties = new AzureNative.Resources.Inputs.DeploymentPropertiesArgs
        {
            Mode = AzureNative.Resources.DeploymentMode.Incremental,
            Parameters = null,
            TemplateLink = new AzureNative.Resources.Inputs.TemplateLinkArgs
            {
                QueryString = "sv=2019-02-02&st=2019-04-29T22%3A18%3A26Z&se=2019-04-30T02%3A23%3A26Z&sr=b&sp=rw&sip=168.1.5.60-168.1.5.70&spr=https&sig=xxxxxxxx0xxxxxxxxxxxxx%2bxxxxxxxxxxxxxxxxxxxx%3d",
                Uri = "https://example.com/exampleTemplate.json",
            },
        },
        ResourceGroupName = "my-resource-group",
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
		_, err := resources.NewDeployment(ctx, "deployment", &resources.DeploymentArgs{
			DeploymentName: pulumi.String("my-deployment"),
			Properties: resources.DeploymentPropertiesExtendedResponse{
				Mode:       resources.DeploymentModeIncremental,
				Parameters: nil,
				TemplateLink: &resources.TemplateLinkArgs{
					QueryString: pulumi.String("sv=2019-02-02&st=2019-04-29T22%3A18%3A26Z&se=2019-04-30T02%3A23%3A26Z&sr=b&sp=rw&sip=168.1.5.60-168.1.5.70&spr=https&sig=xxxxxxxx0xxxxxxxxxxxxx%2bxxxxxxxxxxxxxxxxxxxx%3d"),
					Uri:         pulumi.String("https://example.com/exampleTemplate.json"),
				},
			},
			ResourceGroupName: pulumi.String("my-resource-group"),
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
import com.pulumi.azurenative.resources.Deployment;
import com.pulumi.azurenative.resources.DeploymentArgs;
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
            .deploymentName("my-deployment")
            .properties(Map.ofEntries(
                Map.entry("mode", "Incremental"),
                Map.entry("parameters", ),
                Map.entry("templateLink", Map.ofEntries(
                    Map.entry("queryString", "sv=2019-02-02&st=2019-04-29T22%3A18%3A26Z&se=2019-04-30T02%3A23%3A26Z&sr=b&sp=rw&sip=168.1.5.60-168.1.5.70&spr=https&sig=xxxxxxxx0xxxxxxxxxxxxx%2bxxxxxxxxxxxxxxxxxxxx%3d"),
                    Map.entry("uri", "https://example.com/exampleTemplate.json")
                ))
            ))
            .resourceGroupName("my-resource-group")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const deployment = new azure_native.resources.Deployment("deployment", {
    deploymentName: "my-deployment",
    properties: {
        mode: azure_native.resources.DeploymentMode.Incremental,
        parameters: {},
        templateLink: {
            queryString: "sv=2019-02-02&st=2019-04-29T22%3A18%3A26Z&se=2019-04-30T02%3A23%3A26Z&sr=b&sp=rw&sip=168.1.5.60-168.1.5.70&spr=https&sig=xxxxxxxx0xxxxxxxxxxxxx%2bxxxxxxxxxxxxxxxxxxxx%3d",
            uri: "https://example.com/exampleTemplate.json",
        },
    },
    resourceGroupName: "my-resource-group",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

deployment = azure_native.resources.Deployment("deployment",
    deployment_name="my-deployment",
    properties=azure_native.resources.DeploymentPropertiesExtendedResponseArgs(
        mode=azure_native.resources.DeploymentMode.INCREMENTAL,
        parameters={},
        template_link=azure_native.resources.TemplateLinkArgs(
            query_string="sv=2019-02-02&st=2019-04-29T22%3A18%3A26Z&se=2019-04-30T02%3A23%3A26Z&sr=b&sp=rw&sip=168.1.5.60-168.1.5.70&spr=https&sig=xxxxxxxx0xxxxxxxxxxxxx%2bxxxxxxxxxxxxxxxxxxxx%3d",
            uri="https://example.com/exampleTemplate.json",
        ),
    ),
    resource_group_name="my-resource-group")

```

```yaml
resources:
  deployment:
    type: azure-native:resources:Deployment
    properties:
      deploymentName: my-deployment
      properties:
        mode: Incremental
        parameters: {}
        templateLink:
          queryString: sv=2019-02-02&st=2019-04-29T22%3A18%3A26Z&se=2019-04-30T02%3A23%3A26Z&sr=b&sp=rw&sip=168.1.5.60-168.1.5.70&spr=https&sig=xxxxxxxx0xxxxxxxxxxxxx%2bxxxxxxxxxxxxxxxxxxxx%3d
          uri: https://example.com/exampleTemplate.json
      resourceGroupName: my-resource-group

```

{{% /example %}}
{{% example %}}
### Create a deployment that will deploy a templateSpec with the given resourceId
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var deployment = new AzureNative.Resources.Deployment("deployment", new()
    {
        DeploymentName = "my-deployment",
        Properties = new AzureNative.Resources.Inputs.DeploymentPropertiesArgs
        {
            Mode = AzureNative.Resources.DeploymentMode.Incremental,
            Parameters = null,
            TemplateLink = new AzureNative.Resources.Inputs.TemplateLinkArgs
            {
                Id = "/subscriptions/00000000-0000-0000-0000-000000000001/resourceGroups/my-resource-group/providers/Microsoft.Resources/TemplateSpecs/TemplateSpec-Name/versions/v1",
            },
        },
        ResourceGroupName = "my-resource-group",
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
		_, err := resources.NewDeployment(ctx, "deployment", &resources.DeploymentArgs{
			DeploymentName: pulumi.String("my-deployment"),
			Properties: resources.DeploymentPropertiesExtendedResponse{
				Mode:       resources.DeploymentModeIncremental,
				Parameters: nil,
				TemplateLink: &resources.TemplateLinkArgs{
					Id: pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000001/resourceGroups/my-resource-group/providers/Microsoft.Resources/TemplateSpecs/TemplateSpec-Name/versions/v1"),
				},
			},
			ResourceGroupName: pulumi.String("my-resource-group"),
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
import com.pulumi.azurenative.resources.Deployment;
import com.pulumi.azurenative.resources.DeploymentArgs;
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
            .deploymentName("my-deployment")
            .properties(Map.ofEntries(
                Map.entry("mode", "Incremental"),
                Map.entry("parameters", ),
                Map.entry("templateLink", Map.of("id", "/subscriptions/00000000-0000-0000-0000-000000000001/resourceGroups/my-resource-group/providers/Microsoft.Resources/TemplateSpecs/TemplateSpec-Name/versions/v1"))
            ))
            .resourceGroupName("my-resource-group")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const deployment = new azure_native.resources.Deployment("deployment", {
    deploymentName: "my-deployment",
    properties: {
        mode: azure_native.resources.DeploymentMode.Incremental,
        parameters: {},
        templateLink: {
            id: "/subscriptions/00000000-0000-0000-0000-000000000001/resourceGroups/my-resource-group/providers/Microsoft.Resources/TemplateSpecs/TemplateSpec-Name/versions/v1",
        },
    },
    resourceGroupName: "my-resource-group",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

deployment = azure_native.resources.Deployment("deployment",
    deployment_name="my-deployment",
    properties=azure_native.resources.DeploymentPropertiesExtendedResponseArgs(
        mode=azure_native.resources.DeploymentMode.INCREMENTAL,
        parameters={},
        template_link=azure_native.resources.TemplateLinkArgs(
            id="/subscriptions/00000000-0000-0000-0000-000000000001/resourceGroups/my-resource-group/providers/Microsoft.Resources/TemplateSpecs/TemplateSpec-Name/versions/v1",
        ),
    ),
    resource_group_name="my-resource-group")

```

```yaml
resources:
  deployment:
    type: azure-native:resources:Deployment
    properties:
      deploymentName: my-deployment
      properties:
        mode: Incremental
        parameters: {}
        templateLink:
          id: /subscriptions/00000000-0000-0000-0000-000000000001/resourceGroups/my-resource-group/providers/Microsoft.Resources/TemplateSpecs/TemplateSpec-Name/versions/v1
      resourceGroupName: my-resource-group

```

{{% /example %}}
{{% example %}}
### Create a deployment that will redeploy another deployment on failure
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var deployment = new AzureNative.Resources.Deployment("deployment", new()
    {
        DeploymentName = "my-deployment",
        Properties = new AzureNative.Resources.Inputs.DeploymentPropertiesArgs
        {
            Mode = AzureNative.Resources.DeploymentMode.Complete,
            OnErrorDeployment = new AzureNative.Resources.Inputs.OnErrorDeploymentArgs
            {
                DeploymentName = "name-of-deployment-to-use",
                Type = AzureNative.Resources.OnErrorDeploymentType.SpecificDeployment,
            },
            Parameters = null,
            TemplateLink = new AzureNative.Resources.Inputs.TemplateLinkArgs
            {
                Uri = "https://example.com/exampleTemplate.json",
            },
        },
        ResourceGroupName = "my-resource-group",
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
		_, err := resources.NewDeployment(ctx, "deployment", &resources.DeploymentArgs{
			DeploymentName: pulumi.String("my-deployment"),
			Properties: resources.DeploymentPropertiesExtendedResponse{
				Mode: resources.DeploymentModeComplete,
				OnErrorDeployment: &resources.OnErrorDeploymentArgs{
					DeploymentName: pulumi.String("name-of-deployment-to-use"),
					Type:           resources.OnErrorDeploymentTypeSpecificDeployment,
				},
				Parameters: nil,
				TemplateLink: &resources.TemplateLinkArgs{
					Uri: pulumi.String("https://example.com/exampleTemplate.json"),
				},
			},
			ResourceGroupName: pulumi.String("my-resource-group"),
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
import com.pulumi.azurenative.resources.Deployment;
import com.pulumi.azurenative.resources.DeploymentArgs;
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
            .deploymentName("my-deployment")
            .properties(Map.ofEntries(
                Map.entry("mode", "Complete"),
                Map.entry("onErrorDeployment", Map.ofEntries(
                    Map.entry("deploymentName", "name-of-deployment-to-use"),
                    Map.entry("type", "SpecificDeployment")
                )),
                Map.entry("parameters", ),
                Map.entry("templateLink", Map.of("uri", "https://example.com/exampleTemplate.json"))
            ))
            .resourceGroupName("my-resource-group")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const deployment = new azure_native.resources.Deployment("deployment", {
    deploymentName: "my-deployment",
    properties: {
        mode: azure_native.resources.DeploymentMode.Complete,
        onErrorDeployment: {
            deploymentName: "name-of-deployment-to-use",
            type: azure_native.resources.OnErrorDeploymentType.SpecificDeployment,
        },
        parameters: {},
        templateLink: {
            uri: "https://example.com/exampleTemplate.json",
        },
    },
    resourceGroupName: "my-resource-group",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

deployment = azure_native.resources.Deployment("deployment",
    deployment_name="my-deployment",
    properties=azure_native.resources.DeploymentPropertiesExtendedResponseArgs(
        mode=azure_native.resources.DeploymentMode.COMPLETE,
        on_error_deployment=azure_native.resources.OnErrorDeploymentArgs(
            deployment_name="name-of-deployment-to-use",
            type=azure_native.resources.OnErrorDeploymentType.SPECIFIC_DEPLOYMENT,
        ),
        parameters={},
        template_link=azure_native.resources.TemplateLinkArgs(
            uri="https://example.com/exampleTemplate.json",
        ),
    ),
    resource_group_name="my-resource-group")

```

```yaml
resources:
  deployment:
    type: azure-native:resources:Deployment
    properties:
      deploymentName: my-deployment
      properties:
        mode: Complete
        onErrorDeployment:
          deploymentName: name-of-deployment-to-use
          type: SpecificDeployment
        parameters: {}
        templateLink:
          uri: https://example.com/exampleTemplate.json
      resourceGroupName: my-resource-group

```

{{% /example %}}
{{% example %}}
### Create a deployment that will redeploy the last successful deployment on failure
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var deployment = new AzureNative.Resources.Deployment("deployment", new()
    {
        DeploymentName = "my-deployment",
        Properties = new AzureNative.Resources.Inputs.DeploymentPropertiesArgs
        {
            Mode = AzureNative.Resources.DeploymentMode.Complete,
            OnErrorDeployment = new AzureNative.Resources.Inputs.OnErrorDeploymentArgs
            {
                Type = AzureNative.Resources.OnErrorDeploymentType.LastSuccessful,
            },
            Parameters = null,
            TemplateLink = new AzureNative.Resources.Inputs.TemplateLinkArgs
            {
                Uri = "https://example.com/exampleTemplate.json",
            },
        },
        ResourceGroupName = "my-resource-group",
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
		_, err := resources.NewDeployment(ctx, "deployment", &resources.DeploymentArgs{
			DeploymentName: pulumi.String("my-deployment"),
			Properties: resources.DeploymentPropertiesExtendedResponse{
				Mode: resources.DeploymentModeComplete,
				OnErrorDeployment: &resources.OnErrorDeploymentArgs{
					Type: resources.OnErrorDeploymentTypeLastSuccessful,
				},
				Parameters: nil,
				TemplateLink: &resources.TemplateLinkArgs{
					Uri: pulumi.String("https://example.com/exampleTemplate.json"),
				},
			},
			ResourceGroupName: pulumi.String("my-resource-group"),
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
import com.pulumi.azurenative.resources.Deployment;
import com.pulumi.azurenative.resources.DeploymentArgs;
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
            .deploymentName("my-deployment")
            .properties(Map.ofEntries(
                Map.entry("mode", "Complete"),
                Map.entry("onErrorDeployment", Map.of("type", "LastSuccessful")),
                Map.entry("parameters", ),
                Map.entry("templateLink", Map.of("uri", "https://example.com/exampleTemplate.json"))
            ))
            .resourceGroupName("my-resource-group")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const deployment = new azure_native.resources.Deployment("deployment", {
    deploymentName: "my-deployment",
    properties: {
        mode: azure_native.resources.DeploymentMode.Complete,
        onErrorDeployment: {
            type: azure_native.resources.OnErrorDeploymentType.LastSuccessful,
        },
        parameters: {},
        templateLink: {
            uri: "https://example.com/exampleTemplate.json",
        },
    },
    resourceGroupName: "my-resource-group",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

deployment = azure_native.resources.Deployment("deployment",
    deployment_name="my-deployment",
    properties=azure_native.resources.DeploymentPropertiesExtendedResponseArgs(
        mode=azure_native.resources.DeploymentMode.COMPLETE,
        on_error_deployment=azure_native.resources.OnErrorDeploymentArgs(
            type=azure_native.resources.OnErrorDeploymentType.LAST_SUCCESSFUL,
        ),
        parameters={},
        template_link=azure_native.resources.TemplateLinkArgs(
            uri="https://example.com/exampleTemplate.json",
        ),
    ),
    resource_group_name="my-resource-group")

```

```yaml
resources:
  deployment:
    type: azure-native:resources:Deployment
    properties:
      deploymentName: my-deployment
      properties:
        mode: Complete
        onErrorDeployment:
          type: LastSuccessful
        parameters: {}
        templateLink:
          uri: https://example.com/exampleTemplate.json
      resourceGroupName: my-resource-group

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:resources:Deployment my-deployment /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/my-resource-group/providers/Microsoft.Resources/deployments/my-deployment 
```
