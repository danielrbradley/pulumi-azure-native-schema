An application type version resource for the specified application type name resource.
API Version: 2023-02-01-preview.
Previous API Version: 2020-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Put an application type version
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var applicationTypeVersion = new AzureNative.ServiceFabric.ApplicationTypeVersion("applicationTypeVersion", new()
    {
        AppPackageUrl = "http://fakelink.test.com/MyAppType",
        ApplicationTypeName = "myAppType",
        ClusterName = "myCluster",
        Location = "eastus",
        ResourceGroupName = "resRg",
        Version = "1.0",
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
		_, err := servicefabric.NewApplicationTypeVersion(ctx, "applicationTypeVersion", &servicefabric.ApplicationTypeVersionArgs{
			AppPackageUrl:       pulumi.String("http://fakelink.test.com/MyAppType"),
			ApplicationTypeName: pulumi.String("myAppType"),
			ClusterName:         pulumi.String("myCluster"),
			Location:            pulumi.String("eastus"),
			ResourceGroupName:   pulumi.String("resRg"),
			Version:             pulumi.String("1.0"),
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
import com.pulumi.azurenative.servicefabric.ApplicationTypeVersion;
import com.pulumi.azurenative.servicefabric.ApplicationTypeVersionArgs;
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
        var applicationTypeVersion = new ApplicationTypeVersion("applicationTypeVersion", ApplicationTypeVersionArgs.builder()        
            .appPackageUrl("http://fakelink.test.com/MyAppType")
            .applicationTypeName("myAppType")
            .clusterName("myCluster")
            .location("eastus")
            .resourceGroupName("resRg")
            .version("1.0")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const applicationTypeVersion = new azure_native.servicefabric.ApplicationTypeVersion("applicationTypeVersion", {
    appPackageUrl: "http://fakelink.test.com/MyAppType",
    applicationTypeName: "myAppType",
    clusterName: "myCluster",
    location: "eastus",
    resourceGroupName: "resRg",
    version: "1.0",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

application_type_version = azure_native.servicefabric.ApplicationTypeVersion("applicationTypeVersion",
    app_package_url="http://fakelink.test.com/MyAppType",
    application_type_name="myAppType",
    cluster_name="myCluster",
    location="eastus",
    resource_group_name="resRg",
    version="1.0")

```

```yaml
resources:
  applicationTypeVersion:
    type: azure-native:servicefabric:ApplicationTypeVersion
    properties:
      appPackageUrl: http://fakelink.test.com/MyAppType
      applicationTypeName: myAppType
      clusterName: myCluster
      location: eastus
      resourceGroupName: resRg
      version: '1.0'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:servicefabric:ApplicationTypeVersion 1.0 /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/resRg/providers/Microsoft.ServiceFabric/managedclusters/myCluster/applicationTypes/myAppType/versions/1.0 
```
