Volume resource
API Version: 2022-09-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Volumes_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var volume = new AzureNative.NetApp.Volume("volume", new()
    {
        AccountName = "account1",
        CreationToken = "my-unique-file-path",
        Location = "eastus",
        PoolName = "pool1",
        ResourceGroupName = "myRG",
        ServiceLevel = "Premium",
        SubnetId = "/subscriptions/9760acf5-4638-11e7-9bdb-020073ca7778/resourceGroups/myRP/providers/Microsoft.Network/virtualNetworks/testvnet3/subnets/testsubnet3",
        UsageThreshold = 107374182400,
        VolumeName = "volume1",
    });

});


```

```go
package main

import (
	netapp "github.com/pulumi/pulumi-azure-native-sdk/netapp"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := netapp.NewVolume(ctx, "volume", &netapp.VolumeArgs{
			AccountName:       pulumi.String("account1"),
			CreationToken:     pulumi.String("my-unique-file-path"),
			Location:          pulumi.String("eastus"),
			PoolName:          pulumi.String("pool1"),
			ResourceGroupName: pulumi.String("myRG"),
			ServiceLevel:      pulumi.String("Premium"),
			SubnetId:          pulumi.String("/subscriptions/9760acf5-4638-11e7-9bdb-020073ca7778/resourceGroups/myRP/providers/Microsoft.Network/virtualNetworks/testvnet3/subnets/testsubnet3"),
			UsageThreshold:    pulumi.Float64(107374182400),
			VolumeName:        pulumi.String("volume1"),
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
import com.pulumi.azurenative.netapp.Volume;
import com.pulumi.azurenative.netapp.VolumeArgs;
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
        var volume = new Volume("volume", VolumeArgs.builder()        
            .accountName("account1")
            .creationToken("my-unique-file-path")
            .location("eastus")
            .poolName("pool1")
            .resourceGroupName("myRG")
            .serviceLevel("Premium")
            .subnetId("/subscriptions/9760acf5-4638-11e7-9bdb-020073ca7778/resourceGroups/myRP/providers/Microsoft.Network/virtualNetworks/testvnet3/subnets/testsubnet3")
            .usageThreshold(107374182400)
            .volumeName("volume1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const volume = new azure_native.netapp.Volume("volume", {
    accountName: "account1",
    creationToken: "my-unique-file-path",
    location: "eastus",
    poolName: "pool1",
    resourceGroupName: "myRG",
    serviceLevel: "Premium",
    subnetId: "/subscriptions/9760acf5-4638-11e7-9bdb-020073ca7778/resourceGroups/myRP/providers/Microsoft.Network/virtualNetworks/testvnet3/subnets/testsubnet3",
    usageThreshold: 107374182400,
    volumeName: "volume1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

volume = azure_native.netapp.Volume("volume",
    account_name="account1",
    creation_token="my-unique-file-path",
    location="eastus",
    pool_name="pool1",
    resource_group_name="myRG",
    service_level="Premium",
    subnet_id="/subscriptions/9760acf5-4638-11e7-9bdb-020073ca7778/resourceGroups/myRP/providers/Microsoft.Network/virtualNetworks/testvnet3/subnets/testsubnet3",
    usage_threshold=107374182400,
    volume_name="volume1")

```

```yaml
resources:
  volume:
    type: azure-native:netapp:Volume
    properties:
      accountName: account1
      creationToken: my-unique-file-path
      location: eastus
      poolName: pool1
      resourceGroupName: myRG
      serviceLevel: Premium
      subnetId: /subscriptions/9760acf5-4638-11e7-9bdb-020073ca7778/resourceGroups/myRP/providers/Microsoft.Network/virtualNetworks/testvnet3/subnets/testsubnet3
      usageThreshold: 1.073741824e+11
      volumeName: volume1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:netapp:Volume account1/pool1/volume1 /subscriptions/D633CC2E-722B-4AE1-B636-BBD9E4C60ED9/resourceGroups/myRG/providers/Microsoft.NetApp/netAppAccounts/account1/capacityPools/pool1/volumes/volume1 
```
