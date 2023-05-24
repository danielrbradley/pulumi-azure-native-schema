Backup policy information
API Version: 2022-09-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### BackupPolicies_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var backupPolicy = new AzureNative.NetApp.BackupPolicy("backupPolicy", new()
    {
        AccountName = "account1",
        BackupPolicyName = "backupPolicyName",
        DailyBackupsToKeep = 10,
        Enabled = true,
        Location = "westus",
        MonthlyBackupsToKeep = 10,
        ResourceGroupName = "myRG",
        WeeklyBackupsToKeep = 10,
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
		_, err := netapp.NewBackupPolicy(ctx, "backupPolicy", &netapp.BackupPolicyArgs{
			AccountName:          pulumi.String("account1"),
			BackupPolicyName:     pulumi.String("backupPolicyName"),
			DailyBackupsToKeep:   pulumi.Int(10),
			Enabled:              pulumi.Bool(true),
			Location:             pulumi.String("westus"),
			MonthlyBackupsToKeep: pulumi.Int(10),
			ResourceGroupName:    pulumi.String("myRG"),
			WeeklyBackupsToKeep:  pulumi.Int(10),
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
import com.pulumi.azurenative.netapp.BackupPolicy;
import com.pulumi.azurenative.netapp.BackupPolicyArgs;
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
        var backupPolicy = new BackupPolicy("backupPolicy", BackupPolicyArgs.builder()        
            .accountName("account1")
            .backupPolicyName("backupPolicyName")
            .dailyBackupsToKeep(10)
            .enabled(true)
            .location("westus")
            .monthlyBackupsToKeep(10)
            .resourceGroupName("myRG")
            .weeklyBackupsToKeep(10)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const backupPolicy = new azure_native.netapp.BackupPolicy("backupPolicy", {
    accountName: "account1",
    backupPolicyName: "backupPolicyName",
    dailyBackupsToKeep: 10,
    enabled: true,
    location: "westus",
    monthlyBackupsToKeep: 10,
    resourceGroupName: "myRG",
    weeklyBackupsToKeep: 10,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

backup_policy = azure_native.netapp.BackupPolicy("backupPolicy",
    account_name="account1",
    backup_policy_name="backupPolicyName",
    daily_backups_to_keep=10,
    enabled=True,
    location="westus",
    monthly_backups_to_keep=10,
    resource_group_name="myRG",
    weekly_backups_to_keep=10)

```

```yaml
resources:
  backupPolicy:
    type: azure-native:netapp:BackupPolicy
    properties:
      accountName: account1
      backupPolicyName: backupPolicyName
      dailyBackupsToKeep: 10
      enabled: true
      location: westus
      monthlyBackupsToKeep: 10
      resourceGroupName: myRG
      weeklyBackupsToKeep: 10

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:netapp:BackupPolicy account1/backupPolicyName /subscriptions/D633CC2E-722B-4AE1-B636-BBD9E4C60ED9/resourceGroups/myRG/providers/Microsoft.NetApp/netAppAccounts/account1/backupPolocies/backupPolicyName 
```
