The application type name resource
API Version: 2023-02-01-preview.
Previous API Version: 2020-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Put an application type
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var applicationType = new AzureNative.ServiceFabric.ApplicationType("applicationType", new()
    {
        ApplicationTypeName = "myAppType",
        ClusterName = "myCluster",
        Location = "eastus",
        ResourceGroupName = "resRg",
    });

});


```

```go
package main

import (
	servicefabric "github.com/pulumi/pulumi-azure-native-sdk/servicefabric"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := servicefabric.NewApplicationType(ctx, "applicationType", &servicefabric.ApplicationTypeArgs{
			ApplicationTypeName: pulumi.String("myAppType"),
			ClusterName:         pulumi.String("myCluster"),
			Location:            pulumi.String("eastus"),
			ResourceGroupName:   pulumi.String("resRg"),
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
import com.pulumi.azurenative.servicefabric.ApplicationType;
import com.pulumi.azurenative.servicefabric.ApplicationTypeArgs;
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
        var applicationType = new ApplicationType("applicationType", ApplicationTypeArgs.builder()        
            .applicationTypeName("myAppType")
            .clusterName("myCluster")
            .location("eastus")
            .resourceGroupName("resRg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const applicationType = new azure_native.servicefabric.ApplicationType("applicationType", {
    applicationTypeName: "myAppType",
    clusterName: "myCluster",
    location: "eastus",
    resourceGroupName: "resRg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

application_type = azure_native.servicefabric.ApplicationType("applicationType",
    application_type_name="myAppType",
    cluster_name="myCluster",
    location="eastus",
    resource_group_name="resRg")

```

```yaml
resources:
  applicationType:
    type: azure-native:servicefabric:ApplicationType
    properties:
      applicationTypeName: myAppType
      clusterName: myCluster
      location: eastus
      resourceGroupName: resRg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:servicefabric:ApplicationType myAppType /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/resRg/providers/Microsoft.ServiceFabric/managedclusters/myCluster/applicationTypes/myAppType 
```
