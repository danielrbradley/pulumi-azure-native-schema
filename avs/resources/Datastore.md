A datastore resource
API Version: 2022-05-01.
Previous API Version: 2021-01-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Datastores_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var datastore = new AzureNative.AVS.Datastore("datastore", new()
    {
        ClusterName = "cluster1",
        DatastoreName = "datastore1",
        NetAppVolume = new AzureNative.AVS.Inputs.NetAppVolumeArgs
        {
            Id = "/subscriptions/11111111-1111-1111-1111-111111111111/resourceGroups/ResourceGroup1/providers/Microsoft.NetApp/netAppAccounts/NetAppAccount1/capacityPools/CapacityPool1/volumes/NFSVol1",
        },
        PrivateCloudName = "cloud1",
        ResourceGroupName = "group1",
    });

});


```

```go
package main

import (
	avs "github.com/pulumi/pulumi-azure-native-sdk/avs"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := avs.NewDatastore(ctx, "datastore", &avs.DatastoreArgs{
			ClusterName:   pulumi.String("cluster1"),
			DatastoreName: pulumi.String("datastore1"),
			NetAppVolume: &avs.NetAppVolumeArgs{
				Id: pulumi.String("/subscriptions/11111111-1111-1111-1111-111111111111/resourceGroups/ResourceGroup1/providers/Microsoft.NetApp/netAppAccounts/NetAppAccount1/capacityPools/CapacityPool1/volumes/NFSVol1"),
			},
			PrivateCloudName:  pulumi.String("cloud1"),
			ResourceGroupName: pulumi.String("group1"),
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
import com.pulumi.azurenative.avs.Datastore;
import com.pulumi.azurenative.avs.DatastoreArgs;
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
        var datastore = new Datastore("datastore", DatastoreArgs.builder()        
            .clusterName("cluster1")
            .datastoreName("datastore1")
            .netAppVolume(Map.of("id", "/subscriptions/11111111-1111-1111-1111-111111111111/resourceGroups/ResourceGroup1/providers/Microsoft.NetApp/netAppAccounts/NetAppAccount1/capacityPools/CapacityPool1/volumes/NFSVol1"))
            .privateCloudName("cloud1")
            .resourceGroupName("group1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const datastore = new azure_native.avs.Datastore("datastore", {
    clusterName: "cluster1",
    datastoreName: "datastore1",
    netAppVolume: {
        id: "/subscriptions/11111111-1111-1111-1111-111111111111/resourceGroups/ResourceGroup1/providers/Microsoft.NetApp/netAppAccounts/NetAppAccount1/capacityPools/CapacityPool1/volumes/NFSVol1",
    },
    privateCloudName: "cloud1",
    resourceGroupName: "group1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

datastore = azure_native.avs.Datastore("datastore",
    cluster_name="cluster1",
    datastore_name="datastore1",
    net_app_volume=azure_native.avs.NetAppVolumeArgs(
        id="/subscriptions/11111111-1111-1111-1111-111111111111/resourceGroups/ResourceGroup1/providers/Microsoft.NetApp/netAppAccounts/NetAppAccount1/capacityPools/CapacityPool1/volumes/NFSVol1",
    ),
    private_cloud_name="cloud1",
    resource_group_name="group1")

```

```yaml
resources:
  datastore:
    type: azure-native:avs:Datastore
    properties:
      clusterName: cluster1
      datastoreName: datastore1
      netAppVolume:
        id: /subscriptions/11111111-1111-1111-1111-111111111111/resourceGroups/ResourceGroup1/providers/Microsoft.NetApp/netAppAccounts/NetAppAccount1/capacityPools/CapacityPool1/volumes/NFSVol1
      privateCloudName: cloud1
      resourceGroupName: group1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:avs:Datastore datastore1 /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/group1/providers/Microsoft.AVS/privateClouds/cloud1/clusters/cluster1/datastores/datastore1 
```
