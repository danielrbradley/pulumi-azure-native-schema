Class representing a managed private endpoint.
API Version: 2022-12-29.
Previous API Version: 2021-08-27. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### KustoManagedPrivateEndpointsCreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedPrivateEndpoint = new AzureNative.Kusto.ManagedPrivateEndpoint("managedPrivateEndpoint", new()
    {
        ClusterName = "kustoCluster",
        GroupId = "blob",
        ManagedPrivateEndpointName = "managedPrivateEndpointTest",
        PrivateLinkResourceId = "/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.Storage/storageAccounts/storageAccountTest",
        RequestMessage = "Please Approve.",
        ResourceGroupName = "kustorptest",
    });

});


```

```go
package main

import (
	kusto "github.com/pulumi/pulumi-azure-native-sdk/kusto"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := kusto.NewManagedPrivateEndpoint(ctx, "managedPrivateEndpoint", &kusto.ManagedPrivateEndpointArgs{
			ClusterName:                pulumi.String("kustoCluster"),
			GroupId:                    pulumi.String("blob"),
			ManagedPrivateEndpointName: pulumi.String("managedPrivateEndpointTest"),
			PrivateLinkResourceId:      pulumi.String("/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.Storage/storageAccounts/storageAccountTest"),
			RequestMessage:             pulumi.String("Please Approve."),
			ResourceGroupName:          pulumi.String("kustorptest"),
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
import com.pulumi.azurenative.kusto.ManagedPrivateEndpoint;
import com.pulumi.azurenative.kusto.ManagedPrivateEndpointArgs;
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
        var managedPrivateEndpoint = new ManagedPrivateEndpoint("managedPrivateEndpoint", ManagedPrivateEndpointArgs.builder()        
            .clusterName("kustoCluster")
            .groupId("blob")
            .managedPrivateEndpointName("managedPrivateEndpointTest")
            .privateLinkResourceId("/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.Storage/storageAccounts/storageAccountTest")
            .requestMessage("Please Approve.")
            .resourceGroupName("kustorptest")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedPrivateEndpoint = new azure_native.kusto.ManagedPrivateEndpoint("managedPrivateEndpoint", {
    clusterName: "kustoCluster",
    groupId: "blob",
    managedPrivateEndpointName: "managedPrivateEndpointTest",
    privateLinkResourceId: "/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.Storage/storageAccounts/storageAccountTest",
    requestMessage: "Please Approve.",
    resourceGroupName: "kustorptest",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_private_endpoint = azure_native.kusto.ManagedPrivateEndpoint("managedPrivateEndpoint",
    cluster_name="kustoCluster",
    group_id="blob",
    managed_private_endpoint_name="managedPrivateEndpointTest",
    private_link_resource_id="/subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.Storage/storageAccounts/storageAccountTest",
    request_message="Please Approve.",
    resource_group_name="kustorptest")

```

```yaml
resources:
  managedPrivateEndpoint:
    type: azure-native:kusto:ManagedPrivateEndpoint
    properties:
      clusterName: kustoCluster
      groupId: blob
      managedPrivateEndpointName: managedPrivateEndpointTest
      privateLinkResourceId: /subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.Storage/storageAccounts/storageAccountTest
      requestMessage: Please Approve.
      resourceGroupName: kustorptest

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:kusto:ManagedPrivateEndpoint kustoCluster/KustoDatabase8/managedPrivateEndpointTest /subscriptions/12345678-1234-1234-1234-123456789098/resourceGroups/kustorptest/providers/Microsoft.Kusto/Clusters/kustoCluster/ManagedPrivateEndpoints/managedPrivateEndpointTest 
```
