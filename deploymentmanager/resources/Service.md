The resource representation of a service in a service topology.
API Version: 2019-11-01-preview.
Previous API Version: 2019-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create service
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var service = new AzureNative.DeploymentManager.Service("service", new()
    {
        Location = "centralus",
        ResourceGroupName = "myResourceGroup",
        ServiceName = "myService",
        ServiceTopologyName = "myTopology",
        Tags = null,
        TargetLocation = "centralus",
        TargetSubscriptionId = "600c95c5-3ee5-44fe-b190-ca38a19adcd7",
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
		_, err := deploymentmanager.NewService(ctx, "service", &deploymentmanager.ServiceArgs{
			Location:             pulumi.String("centralus"),
			ResourceGroupName:    pulumi.String("myResourceGroup"),
			ServiceName:          pulumi.String("myService"),
			ServiceTopologyName:  pulumi.String("myTopology"),
			Tags:                 nil,
			TargetLocation:       pulumi.String("centralus"),
			TargetSubscriptionId: pulumi.String("600c95c5-3ee5-44fe-b190-ca38a19adcd7"),
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
import com.pulumi.azurenative.deploymentmanager.Service;
import com.pulumi.azurenative.deploymentmanager.ServiceArgs;
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
        var service = new Service("service", ServiceArgs.builder()        
            .location("centralus")
            .resourceGroupName("myResourceGroup")
            .serviceName("myService")
            .serviceTopologyName("myTopology")
            .tags()
            .targetLocation("centralus")
            .targetSubscriptionId("600c95c5-3ee5-44fe-b190-ca38a19adcd7")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const service = new azure_native.deploymentmanager.Service("service", {
    location: "centralus",
    resourceGroupName: "myResourceGroup",
    serviceName: "myService",
    serviceTopologyName: "myTopology",
    tags: {},
    targetLocation: "centralus",
    targetSubscriptionId: "600c95c5-3ee5-44fe-b190-ca38a19adcd7",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service = azure_native.deploymentmanager.Service("service",
    location="centralus",
    resource_group_name="myResourceGroup",
    service_name="myService",
    service_topology_name="myTopology",
    tags={},
    target_location="centralus",
    target_subscription_id="600c95c5-3ee5-44fe-b190-ca38a19adcd7")

```

```yaml
resources:
  service:
    type: azure-native:deploymentmanager:Service
    properties:
      location: centralus
      resourceGroupName: myResourceGroup
      serviceName: myService
      serviceTopologyName: myTopology
      tags: {}
      targetLocation: centralus
      targetSubscriptionId: 600c95c5-3ee5-44fe-b190-ca38a19adcd7

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:deploymentmanager:Service myService /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.DeploymentManager/serviceTopologies/{serviceTopologyName}/services/{serviceName} 
```
