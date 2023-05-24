Capacity pool resource
API Version: 2022-09-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Pools_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var pool = new AzureNative.NetApp.Pool("pool", new()
    {
        AccountName = "account1",
        Location = "eastus",
        PoolName = "pool1",
        QosType = "Auto",
        ResourceGroupName = "myRG",
        ServiceLevel = "Premium",
        Size = 4398046511104,
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
		_, err := netapp.NewPool(ctx, "pool", &netapp.PoolArgs{
			AccountName:       pulumi.String("account1"),
			Location:          pulumi.String("eastus"),
			PoolName:          pulumi.String("pool1"),
			QosType:           pulumi.String("Auto"),
			ResourceGroupName: pulumi.String("myRG"),
			ServiceLevel:      pulumi.String("Premium"),
			Size:              pulumi.Float64(4398046511104),
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
import com.pulumi.azurenative.netapp.Pool;
import com.pulumi.azurenative.netapp.PoolArgs;
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
        var pool = new Pool("pool", PoolArgs.builder()        
            .accountName("account1")
            .location("eastus")
            .poolName("pool1")
            .qosType("Auto")
            .resourceGroupName("myRG")
            .serviceLevel("Premium")
            .size(4398046511104)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const pool = new azure_native.netapp.Pool("pool", {
    accountName: "account1",
    location: "eastus",
    poolName: "pool1",
    qosType: "Auto",
    resourceGroupName: "myRG",
    serviceLevel: "Premium",
    size: 4398046511104,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

pool = azure_native.netapp.Pool("pool",
    account_name="account1",
    location="eastus",
    pool_name="pool1",
    qos_type="Auto",
    resource_group_name="myRG",
    service_level="Premium",
    size=4398046511104)

```

```yaml
resources:
  pool:
    type: azure-native:netapp:Pool
    properties:
      accountName: account1
      location: eastus
      poolName: pool1
      qosType: Auto
      resourceGroupName: myRG
      serviceLevel: Premium
      size: 4.398046511104e+12

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:netapp:Pool account1/pool1 /subscriptions/D633CC2E-722B-4AE1-B636-BBD9E4C60ED9/resourceGroups/myRG/providers/Microsoft.NetApp/netAppAccounts/account1/capacityPools/pool1 
```
