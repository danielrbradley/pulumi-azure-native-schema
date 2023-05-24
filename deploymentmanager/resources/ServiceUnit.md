Represents the response of a service unit resource.
API Version: 2019-11-01-preview.
Previous API Version: 2019-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create service unit using SAS URIs
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var serviceUnit = new AzureNative.DeploymentManager.ServiceUnit("serviceUnit", new()
    {
        Artifacts = new AzureNative.DeploymentManager.Inputs.ServiceUnitArtifactsArgs
        {
            ParametersUri = "https://mystorageaccount.blob.core.windows.net/myartifactsource/parameter/myTopologyUnit.parameters.json?st=2018-07-07T14%3A10%3A00Z&se=2019-12-31T15%3A10%3A00Z&sp=rl&sv=2017-04-17&sr=c&sig=Yh2SoJ1NhhLRwCLln7de%2Fkabcdefghijklmno5sWEIk%3D",
            TemplateUri = "https://mystorageaccount.blob.core.windows.net/myartifactsource/templates/myTopologyUnit.template.json?st=2018-07-07T14%3A10%3A00Z&se=2019-12-31T15%3A10%3A00Z&sp=rl&sv=2017-04-17&sr=c&sig=Yh2SoJ1NhhLRwCLln7de%2Fkabcdefghijklmno5sWEIk%3D",
        },
        DeploymentMode = AzureNative.DeploymentManager.DeploymentMode.Incremental,
        Location = "centralus",
        ResourceGroupName = "myResourceGroup",
        ServiceName = "myService",
        ServiceTopologyName = "myTopology",
        ServiceUnitName = "myServiceUnit",
        Tags = null,
        TargetResourceGroup = "myDeploymentResourceGroup",
    });

});


```

```go
package main

import (
	deploymentmanager "github.com/pulumi/pulumi-azure-native-sdk/deploymentmanager"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := deploymentmanager.NewServiceUnit(ctx, "serviceUnit", &deploymentmanager.ServiceUnitArgs{
			Artifacts: &deploymentmanager.ServiceUnitArtifactsArgs{
				ParametersUri: pulumi.String("https://mystorageaccount.blob.core.windows.net/myartifactsource/parameter/myTopologyUnit.parameters.json?st=2018-07-07T14%3A10%3A00Z&se=2019-12-31T15%3A10%3A00Z&sp=rl&sv=2017-04-17&sr=c&sig=Yh2SoJ1NhhLRwCLln7de%2Fkabcdefghijklmno5sWEIk%3D"),
				TemplateUri:   pulumi.String("https://mystorageaccount.blob.core.windows.net/myartifactsource/templates/myTopologyUnit.template.json?st=2018-07-07T14%3A10%3A00Z&se=2019-12-31T15%3A10%3A00Z&sp=rl&sv=2017-04-17&sr=c&sig=Yh2SoJ1NhhLRwCLln7de%2Fkabcdefghijklmno5sWEIk%3D"),
			},
			DeploymentMode:      deploymentmanager.DeploymentModeIncremental,
			Location:            pulumi.String("centralus"),
			ResourceGroupName:   pulumi.String("myResourceGroup"),
			ServiceName:         pulumi.String("myService"),
			ServiceTopologyName: pulumi.String("myTopology"),
			ServiceUnitName:     pulumi.String("myServiceUnit"),
			Tags:                nil,
			TargetResourceGroup: pulumi.String("myDeploymentResourceGroup"),
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
import com.pulumi.azurenative.deploymentmanager.ServiceUnit;
import com.pulumi.azurenative.deploymentmanager.ServiceUnitArgs;
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
        var serviceUnit = new ServiceUnit("serviceUnit", ServiceUnitArgs.builder()        
            .artifacts(Map.ofEntries(
                Map.entry("parametersUri", "https://mystorageaccount.blob.core.windows.net/myartifactsource/parameter/myTopologyUnit.parameters.json?st=2018-07-07T14%3A10%3A00Z&se=2019-12-31T15%3A10%3A00Z&sp=rl&sv=2017-04-17&sr=c&sig=Yh2SoJ1NhhLRwCLln7de%2Fkabcdefghijklmno5sWEIk%3D"),
                Map.entry("templateUri", "https://mystorageaccount.blob.core.windows.net/myartifactsource/templates/myTopologyUnit.template.json?st=2018-07-07T14%3A10%3A00Z&se=2019-12-31T15%3A10%3A00Z&sp=rl&sv=2017-04-17&sr=c&sig=Yh2SoJ1NhhLRwCLln7de%2Fkabcdefghijklmno5sWEIk%3D")
            ))
            .deploymentMode("Incremental")
            .location("centralus")
            .resourceGroupName("myResourceGroup")
            .serviceName("myService")
            .serviceTopologyName("myTopology")
            .serviceUnitName("myServiceUnit")
            .tags()
            .targetResourceGroup("myDeploymentResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const serviceUnit = new azure_native.deploymentmanager.ServiceUnit("serviceUnit", {
    artifacts: {
        parametersUri: "https://mystorageaccount.blob.core.windows.net/myartifactsource/parameter/myTopologyUnit.parameters.json?st=2018-07-07T14%3A10%3A00Z&se=2019-12-31T15%3A10%3A00Z&sp=rl&sv=2017-04-17&sr=c&sig=Yh2SoJ1NhhLRwCLln7de%2Fkabcdefghijklmno5sWEIk%3D",
        templateUri: "https://mystorageaccount.blob.core.windows.net/myartifactsource/templates/myTopologyUnit.template.json?st=2018-07-07T14%3A10%3A00Z&se=2019-12-31T15%3A10%3A00Z&sp=rl&sv=2017-04-17&sr=c&sig=Yh2SoJ1NhhLRwCLln7de%2Fkabcdefghijklmno5sWEIk%3D",
    },
    deploymentMode: azure_native.deploymentmanager.DeploymentMode.Incremental,
    location: "centralus",
    resourceGroupName: "myResourceGroup",
    serviceName: "myService",
    serviceTopologyName: "myTopology",
    serviceUnitName: "myServiceUnit",
    tags: {},
    targetResourceGroup: "myDeploymentResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service_unit = azure_native.deploymentmanager.ServiceUnit("serviceUnit",
    artifacts=azure_native.deploymentmanager.ServiceUnitArtifactsArgs(
        parameters_uri="https://mystorageaccount.blob.core.windows.net/myartifactsource/parameter/myTopologyUnit.parameters.json?st=2018-07-07T14%3A10%3A00Z&se=2019-12-31T15%3A10%3A00Z&sp=rl&sv=2017-04-17&sr=c&sig=Yh2SoJ1NhhLRwCLln7de%2Fkabcdefghijklmno5sWEIk%3D",
        template_uri="https://mystorageaccount.blob.core.windows.net/myartifactsource/templates/myTopologyUnit.template.json?st=2018-07-07T14%3A10%3A00Z&se=2019-12-31T15%3A10%3A00Z&sp=rl&sv=2017-04-17&sr=c&sig=Yh2SoJ1NhhLRwCLln7de%2Fkabcdefghijklmno5sWEIk%3D",
    ),
    deployment_mode=azure_native.deploymentmanager.DeploymentMode.INCREMENTAL,
    location="centralus",
    resource_group_name="myResourceGroup",
    service_name="myService",
    service_topology_name="myTopology",
    service_unit_name="myServiceUnit",
    tags={},
    target_resource_group="myDeploymentResourceGroup")

```

```yaml
resources:
  serviceUnit:
    type: azure-native:deploymentmanager:ServiceUnit
    properties:
      artifacts:
        parametersUri: https://mystorageaccount.blob.core.windows.net/myartifactsource/parameter/myTopologyUnit.parameters.json?st=2018-07-07T14%3A10%3A00Z&se=2019-12-31T15%3A10%3A00Z&sp=rl&sv=2017-04-17&sr=c&sig=Yh2SoJ1NhhLRwCLln7de%2Fkabcdefghijklmno5sWEIk%3D
        templateUri: https://mystorageaccount.blob.core.windows.net/myartifactsource/templates/myTopologyUnit.template.json?st=2018-07-07T14%3A10%3A00Z&se=2019-12-31T15%3A10%3A00Z&sp=rl&sv=2017-04-17&sr=c&sig=Yh2SoJ1NhhLRwCLln7de%2Fkabcdefghijklmno5sWEIk%3D
      deploymentMode: Incremental
      location: centralus
      resourceGroupName: myResourceGroup
      serviceName: myService
      serviceTopologyName: myTopology
      serviceUnitName: myServiceUnit
      tags: {}
      targetResourceGroup: myDeploymentResourceGroup

```

{{% /example %}}
{{% example %}}
### Create service unit using relative paths into the artifact source
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var serviceUnit = new AzureNative.DeploymentManager.ServiceUnit("serviceUnit", new()
    {
        Artifacts = new AzureNative.DeploymentManager.Inputs.ServiceUnitArtifactsArgs
        {
            ParametersArtifactSourceRelativePath = "parameter/myTopologyUnit.parameters.json",
            TemplateArtifactSourceRelativePath = "templates/myTopologyUnit.template.json",
        },
        DeploymentMode = AzureNative.DeploymentManager.DeploymentMode.Incremental,
        Location = "centralus",
        ResourceGroupName = "myResourceGroup",
        ServiceName = "myService",
        ServiceTopologyName = "myTopology",
        ServiceUnitName = "myServiceUnit",
        Tags = null,
        TargetResourceGroup = "myDeploymentResourceGroup",
    });

});


```

```go
package main

import (
	deploymentmanager "github.com/pulumi/pulumi-azure-native-sdk/deploymentmanager"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := deploymentmanager.NewServiceUnit(ctx, "serviceUnit", &deploymentmanager.ServiceUnitArgs{
			Artifacts: &deploymentmanager.ServiceUnitArtifactsArgs{
				ParametersArtifactSourceRelativePath: pulumi.String("parameter/myTopologyUnit.parameters.json"),
				TemplateArtifactSourceRelativePath:   pulumi.String("templates/myTopologyUnit.template.json"),
			},
			DeploymentMode:      deploymentmanager.DeploymentModeIncremental,
			Location:            pulumi.String("centralus"),
			ResourceGroupName:   pulumi.String("myResourceGroup"),
			ServiceName:         pulumi.String("myService"),
			ServiceTopologyName: pulumi.String("myTopology"),
			ServiceUnitName:     pulumi.String("myServiceUnit"),
			Tags:                nil,
			TargetResourceGroup: pulumi.String("myDeploymentResourceGroup"),
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
import com.pulumi.azurenative.deploymentmanager.ServiceUnit;
import com.pulumi.azurenative.deploymentmanager.ServiceUnitArgs;
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
        var serviceUnit = new ServiceUnit("serviceUnit", ServiceUnitArgs.builder()        
            .artifacts(Map.ofEntries(
                Map.entry("parametersArtifactSourceRelativePath", "parameter/myTopologyUnit.parameters.json"),
                Map.entry("templateArtifactSourceRelativePath", "templates/myTopologyUnit.template.json")
            ))
            .deploymentMode("Incremental")
            .location("centralus")
            .resourceGroupName("myResourceGroup")
            .serviceName("myService")
            .serviceTopologyName("myTopology")
            .serviceUnitName("myServiceUnit")
            .tags()
            .targetResourceGroup("myDeploymentResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const serviceUnit = new azure_native.deploymentmanager.ServiceUnit("serviceUnit", {
    artifacts: {
        parametersArtifactSourceRelativePath: "parameter/myTopologyUnit.parameters.json",
        templateArtifactSourceRelativePath: "templates/myTopologyUnit.template.json",
    },
    deploymentMode: azure_native.deploymentmanager.DeploymentMode.Incremental,
    location: "centralus",
    resourceGroupName: "myResourceGroup",
    serviceName: "myService",
    serviceTopologyName: "myTopology",
    serviceUnitName: "myServiceUnit",
    tags: {},
    targetResourceGroup: "myDeploymentResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service_unit = azure_native.deploymentmanager.ServiceUnit("serviceUnit",
    artifacts=azure_native.deploymentmanager.ServiceUnitArtifactsArgs(
        parameters_artifact_source_relative_path="parameter/myTopologyUnit.parameters.json",
        template_artifact_source_relative_path="templates/myTopologyUnit.template.json",
    ),
    deployment_mode=azure_native.deploymentmanager.DeploymentMode.INCREMENTAL,
    location="centralus",
    resource_group_name="myResourceGroup",
    service_name="myService",
    service_topology_name="myTopology",
    service_unit_name="myServiceUnit",
    tags={},
    target_resource_group="myDeploymentResourceGroup")

```

```yaml
resources:
  serviceUnit:
    type: azure-native:deploymentmanager:ServiceUnit
    properties:
      artifacts:
        parametersArtifactSourceRelativePath: parameter/myTopologyUnit.parameters.json
        templateArtifactSourceRelativePath: templates/myTopologyUnit.template.json
      deploymentMode: Incremental
      location: centralus
      resourceGroupName: myResourceGroup
      serviceName: myService
      serviceTopologyName: myTopology
      serviceUnitName: myServiceUnit
      tags: {}
      targetResourceGroup: myDeploymentResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:deploymentmanager:ServiceUnit myServiceUnit /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.DeploymentManager/serviceTopologies/{serviceTopologyName}/services/{serviceName}/serviceUnits/{serviceUnitName} 
```
