Backup of a Volume
API Version: 2022-09-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Backups_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var backup = new AzureNative.NetApp.Backup("backup", new()
    {
        AccountName = "account1",
        BackupName = "backup1",
        Label = "myLabel",
        Location = "eastus",
        PoolName = "pool1",
        ResourceGroupName = "myRG",
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
		_, err := netapp.NewBackup(ctx, "backup", &netapp.BackupArgs{
			AccountName:       pulumi.String("account1"),
			BackupName:        pulumi.String("backup1"),
			Label:             pulumi.String("myLabel"),
			Location:          pulumi.String("eastus"),
			PoolName:          pulumi.String("pool1"),
			ResourceGroupName: pulumi.String("myRG"),
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
import com.pulumi.azurenative.netapp.Backup;
import com.pulumi.azurenative.netapp.BackupArgs;
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
        var backup = new Backup("backup", BackupArgs.builder()        
            .accountName("account1")
            .backupName("backup1")
            .label("myLabel")
            .location("eastus")
            .poolName("pool1")
            .resourceGroupName("myRG")
            .volumeName("volume1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const backup = new azure_native.netapp.Backup("backup", {
    accountName: "account1",
    backupName: "backup1",
    label: "myLabel",
    location: "eastus",
    poolName: "pool1",
    resourceGroupName: "myRG",
    volumeName: "volume1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

backup = azure_native.netapp.Backup("backup",
    account_name="account1",
    backup_name="backup1",
    label="myLabel",
    location="eastus",
    pool_name="pool1",
    resource_group_name="myRG",
    volume_name="volume1")

```

```yaml
resources:
  backup:
    type: azure-native:netapp:Backup
    properties:
      accountName: account1
      backupName: backup1
      label: myLabel
      location: eastus
      poolName: pool1
      resourceGroupName: myRG
      volumeName: volume1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:netapp:Backup account1/pool1/volume1/backup1 /subscriptions/D633CC2E-722B-4AE1-B636-BBD9E4C60ED9/resourceGroups/myRG/providers/Microsoft.NetApp/netAppAccounts/account1/capacityPools/pool1/volumes/volume1/backups/backup1 
```
