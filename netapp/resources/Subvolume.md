Subvolume Information properties
API Version: 2022-09-01.
Previous API Version: 2021-10-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Subvolumes_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var subvolume = new AzureNative.NetApp.Subvolume("subvolume", new()
    {
        AccountName = "account1",
        Path = "/subvolumePath",
        PoolName = "pool1",
        ResourceGroupName = "myRG",
        SubvolumeName = "subvolume1",
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
		_, err := netapp.NewSubvolume(ctx, "subvolume", &netapp.SubvolumeArgs{
			AccountName:       pulumi.String("account1"),
			Path:              pulumi.String("/subvolumePath"),
			PoolName:          pulumi.String("pool1"),
			ResourceGroupName: pulumi.String("myRG"),
			SubvolumeName:     pulumi.String("subvolume1"),
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
import com.pulumi.azurenative.netapp.Subvolume;
import com.pulumi.azurenative.netapp.SubvolumeArgs;
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
        var subvolume = new Subvolume("subvolume", SubvolumeArgs.builder()        
            .accountName("account1")
            .path("/subvolumePath")
            .poolName("pool1")
            .resourceGroupName("myRG")
            .subvolumeName("subvolume1")
            .volumeName("volume1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const subvolume = new azure_native.netapp.Subvolume("subvolume", {
    accountName: "account1",
    path: "/subvolumePath",
    poolName: "pool1",
    resourceGroupName: "myRG",
    subvolumeName: "subvolume1",
    volumeName: "volume1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

subvolume = azure_native.netapp.Subvolume("subvolume",
    account_name="account1",
    path="/subvolumePath",
    pool_name="pool1",
    resource_group_name="myRG",
    subvolume_name="subvolume1",
    volume_name="volume1")

```

```yaml
resources:
  subvolume:
    type: azure-native:netapp:Subvolume
    properties:
      accountName: account1
      path: /subvolumePath
      poolName: pool1
      resourceGroupName: myRG
      subvolumeName: subvolume1
      volumeName: volume1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:netapp:Subvolume account1/pool1/volume1/subvolume1 /subscriptions/D633CC2E-722B-4AE1-B636-BBD9E4C60ED9/resourceGroups/myRG/providers/Microsoft.NetApp/netAppAccounts/account1/capacityPools/pool1/volumes/volume1/subvolumes/subvolume1 
```
