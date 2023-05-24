A Service Fabric.
API Version: 2018-09-15.
Previous API Version: 2018-09-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ServiceFabrics_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var serviceFabric = new AzureNative.DevTestLab.ServiceFabric("serviceFabric", new()
    {
        EnvironmentId = "{environmentId}",
        ExternalServiceFabricId = "{serviceFabricId}",
        LabName = "{labName}",
        Location = "{location}",
        Name = "{serviceFabricName}",
        ResourceGroupName = "resourceGroupName",
        Tags = 
        {
            { "tagName1", "tagValue1" },
        },
        UserName = "{userName}",
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
		_, err := devtestlab.NewServiceFabric(ctx, "serviceFabric", &devtestlab.ServiceFabricArgs{
			EnvironmentId:           pulumi.String("{environmentId}"),
			ExternalServiceFabricId: pulumi.String("{serviceFabricId}"),
			LabName:                 pulumi.String("{labName}"),
			Location:                pulumi.String("{location}"),
			Name:                    pulumi.String("{serviceFabricName}"),
			ResourceGroupName:       pulumi.String("resourceGroupName"),
			Tags: pulumi.StringMap{
				"tagName1": pulumi.String("tagValue1"),
			},
			UserName: pulumi.String("{userName}"),
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
import com.pulumi.azurenative.devtestlab.ServiceFabric;
import com.pulumi.azurenative.devtestlab.ServiceFabricArgs;
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
        var serviceFabric = new ServiceFabric("serviceFabric", ServiceFabricArgs.builder()        
            .environmentId("{environmentId}")
            .externalServiceFabricId("{serviceFabricId}")
            .labName("{labName}")
            .location("{location}")
            .name("{serviceFabricName}")
            .resourceGroupName("resourceGroupName")
            .tags(Map.of("tagName1", "tagValue1"))
            .userName("{userName}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const serviceFabric = new azure_native.devtestlab.ServiceFabric("serviceFabric", {
    environmentId: "{environmentId}",
    externalServiceFabricId: "{serviceFabricId}",
    labName: "{labName}",
    location: "{location}",
    name: "{serviceFabricName}",
    resourceGroupName: "resourceGroupName",
    tags: {
        tagName1: "tagValue1",
    },
    userName: "{userName}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

service_fabric = azure_native.devtestlab.ServiceFabric("serviceFabric",
    environment_id="{environmentId}",
    external_service_fabric_id="{serviceFabricId}",
    lab_name="{labName}",
    location="{location}",
    name="{serviceFabricName}",
    resource_group_name="resourceGroupName",
    tags={
        "tagName1": "tagValue1",
    },
    user_name="{userName}")

```

```yaml
resources:
  serviceFabric:
    type: azure-native:devtestlab:ServiceFabric
    properties:
      environmentId: '{environmentId}'
      externalServiceFabricId: '{serviceFabricId}'
      labName: '{labName}'
      location: '{location}'
      name: '{serviceFabricName}'
      resourceGroupName: resourceGroupName
      tags:
        tagName1: tagValue1
      userName: '{userName}'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devtestlab:ServiceFabric {serviceFabricName} /subscriptions/{subscriptionId}/resourcegroups/resourceGroupName/providers/microsoft.devtestlab/labs/{labName}/users/{userName}/servicefabrics/{serviceFabricName} 
```
