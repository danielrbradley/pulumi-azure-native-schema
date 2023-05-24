The resource representation of a service topology.
API Version: 2019-11-01-preview.
Previous API Version: 2019-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a topology with Artifact Source
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var serviceTopology = new AzureNative.DeploymentManager.ServiceTopology("serviceTopology", new()
    {
        ArtifactSourceId = "Microsoft.DeploymentManager/artifactSources/myArtifactSource",
        Location = "centralus",
        ResourceGroupName = "myResourceGroup",
        ServiceTopologyName = "myTopology",
        Tags = null,
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
		_, err := deploymentmanager.NewServiceTopology(ctx, "serviceTopology", &deploymentmanager.ServiceTopologyArgs{
			ArtifactSourceId:    pulumi.String("Microsoft.DeploymentManager/artifactSources/myArtifactSource"),
			Location:            pulumi.String("centralus"),
			ResourceGroupName:   pulumi.String("myResourceGroup"),
			ServiceTopologyName: pulumi.String("myTopology"),
			Tags:                nil,
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
import com.pulumi.azurenative.deploymentmanager.ServiceTopology;
import com.pulumi.azurenative.deploymentmanager.ServiceTopologyArgs;
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
        var serviceTopology = new ServiceTopology("serviceTopology", ServiceTopologyArgs.builder()        
            .artifactSourceId("Microsoft.DeploymentManager/artifactSources/myArtifactSource")
            .location("centralus")
            .resourceGroupName("myResourceGroup")
            .serviceTopologyName("myTopology")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const serviceTopology = new azure_native.deploymentmanager.ServiceTopology("serviceTopology", {
    artifactSourceId: "Microsoft.DeploymentManager/artifactSources/myArtifactSource",
    location: "centralus",
    resourceGroupName: "myResourceGroup",
    serviceTopologyName: "myTopology",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service_topology = azure_native.deploymentmanager.ServiceTopology("serviceTopology",
    artifact_source_id="Microsoft.DeploymentManager/artifactSources/myArtifactSource",
    location="centralus",
    resource_group_name="myResourceGroup",
    service_topology_name="myTopology",
    tags={})

```

```yaml
resources:
  serviceTopology:
    type: azure-native:deploymentmanager:ServiceTopology
    properties:
      artifactSourceId: Microsoft.DeploymentManager/artifactSources/myArtifactSource
      location: centralus
      resourceGroupName: myResourceGroup
      serviceTopologyName: myTopology
      tags: {}

```

{{% /example %}}
{{% example %}}
### Create a topology without Artifact Source
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var serviceTopology = new AzureNative.DeploymentManager.ServiceTopology("serviceTopology", new()
    {
        Location = "centralus",
        ResourceGroupName = "myResourceGroup",
        ServiceTopologyName = "myTopology",
        Tags = null,
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
		_, err := deploymentmanager.NewServiceTopology(ctx, "serviceTopology", &deploymentmanager.ServiceTopologyArgs{
			Location:            pulumi.String("centralus"),
			ResourceGroupName:   pulumi.String("myResourceGroup"),
			ServiceTopologyName: pulumi.String("myTopology"),
			Tags:                nil,
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
import com.pulumi.azurenative.deploymentmanager.ServiceTopology;
import com.pulumi.azurenative.deploymentmanager.ServiceTopologyArgs;
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
        var serviceTopology = new ServiceTopology("serviceTopology", ServiceTopologyArgs.builder()        
            .location("centralus")
            .resourceGroupName("myResourceGroup")
            .serviceTopologyName("myTopology")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const serviceTopology = new azure_native.deploymentmanager.ServiceTopology("serviceTopology", {
    location: "centralus",
    resourceGroupName: "myResourceGroup",
    serviceTopologyName: "myTopology",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service_topology = azure_native.deploymentmanager.ServiceTopology("serviceTopology",
    location="centralus",
    resource_group_name="myResourceGroup",
    service_topology_name="myTopology",
    tags={})

```

```yaml
resources:
  serviceTopology:
    type: azure-native:deploymentmanager:ServiceTopology
    properties:
      location: centralus
      resourceGroupName: myResourceGroup
      serviceTopologyName: myTopology
      tags: {}

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:deploymentmanager:ServiceTopology myTopology /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.DeploymentManager/serviceTopologies/{serviceTopologyName} 
```
