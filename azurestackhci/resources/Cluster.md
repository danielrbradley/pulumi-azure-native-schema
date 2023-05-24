Cluster details.
API Version: 2023-02-01.
Previous API Version: 2020-10-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create cluster
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cluster = new AzureNative.AzureStackHCI.Cluster("cluster", new()
    {
        AadClientId = "24a6e53d-04e5-44d2-b7cc-1b732a847dfc",
        AadTenantId = "7e589cc1-a8b6-4dff-91bd-5ec0fa18db94",
        CloudManagementEndpoint = "https://98294836-31be-4668-aeae-698667faf99b.waconazure.com",
        ClusterName = "myCluster",
        Location = "East US",
        ResourceGroupName = "test-rg",
        Type = "SystemAssigned",
    });

});


```

```go
package main

import (
	azurestackhci "github.com/pulumi/pulumi-azure-native-sdk/azurestackhci"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := azurestackhci.NewCluster(ctx, "cluster", &azurestackhci.ClusterArgs{
			AadClientId:             pulumi.String("24a6e53d-04e5-44d2-b7cc-1b732a847dfc"),
			AadTenantId:             pulumi.String("7e589cc1-a8b6-4dff-91bd-5ec0fa18db94"),
			CloudManagementEndpoint: pulumi.String("https://98294836-31be-4668-aeae-698667faf99b.waconazure.com"),
			ClusterName:             pulumi.String("myCluster"),
			Location:                pulumi.String("East US"),
			ResourceGroupName:       pulumi.String("test-rg"),
			Type:                    pulumi.String("SystemAssigned"),
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
import com.pulumi.azurenative.azurestackhci.Cluster;
import com.pulumi.azurenative.azurestackhci.ClusterArgs;
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
        var cluster = new Cluster("cluster", ClusterArgs.builder()        
            .aadClientId("24a6e53d-04e5-44d2-b7cc-1b732a847dfc")
            .aadTenantId("7e589cc1-a8b6-4dff-91bd-5ec0fa18db94")
            .cloudManagementEndpoint("https://98294836-31be-4668-aeae-698667faf99b.waconazure.com")
            .clusterName("myCluster")
            .location("East US")
            .resourceGroupName("test-rg")
            .type("SystemAssigned")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cluster = new azure_native.azurestackhci.Cluster("cluster", {
    aadClientId: "24a6e53d-04e5-44d2-b7cc-1b732a847dfc",
    aadTenantId: "7e589cc1-a8b6-4dff-91bd-5ec0fa18db94",
    cloudManagementEndpoint: "https://98294836-31be-4668-aeae-698667faf99b.waconazure.com",
    clusterName: "myCluster",
    location: "East US",
    resourceGroupName: "test-rg",
    type: "SystemAssigned",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cluster = azure_native.azurestackhci.Cluster("cluster",
    aad_client_id="24a6e53d-04e5-44d2-b7cc-1b732a847dfc",
    aad_tenant_id="7e589cc1-a8b6-4dff-91bd-5ec0fa18db94",
    cloud_management_endpoint="https://98294836-31be-4668-aeae-698667faf99b.waconazure.com",
    cluster_name="myCluster",
    location="East US",
    resource_group_name="test-rg",
    type="SystemAssigned")

```

```yaml
resources:
  cluster:
    type: azure-native:azurestackhci:Cluster
    properties:
      aadClientId: 24a6e53d-04e5-44d2-b7cc-1b732a847dfc
      aadTenantId: 7e589cc1-a8b6-4dff-91bd-5ec0fa18db94
      cloudManagementEndpoint: https://98294836-31be-4668-aeae-698667faf99b.waconazure.com
      clusterName: myCluster
      location: East US
      resourceGroupName: test-rg
      type: SystemAssigned

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:azurestackhci:Cluster myCluster /subscriptions/fd3c3665-1729-4b7b-9a38-238e83b0f98b/resourceGroups/test-rg/providers/Microsoft.AzureStackHCI/clusters/myCluster 
```
