A short term retention policy.
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Update the short term retention policy for the database.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var backupShortTermRetentionPolicy = new AzureNative.Sql.BackupShortTermRetentionPolicy("backupShortTermRetentionPolicy", new()
    {
        DatabaseName = "testdb",
        DiffBackupIntervalInHours = 24,
        PolicyName = "default",
        ResourceGroupName = "resourceGroup",
        RetentionDays = 7,
        ServerName = "testsvr",
    });

});


```

```go
package main

import (
	sql "github.com/pulumi/pulumi-azure-native-sdk/sql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := sql.NewBackupShortTermRetentionPolicy(ctx, "backupShortTermRetentionPolicy", &sql.BackupShortTermRetentionPolicyArgs{
			DatabaseName:              pulumi.String("testdb"),
			DiffBackupIntervalInHours: pulumi.Int(24),
			PolicyName:                pulumi.String("default"),
			ResourceGroupName:         pulumi.String("resourceGroup"),
			RetentionDays:             pulumi.Int(7),
			ServerName:                pulumi.String("testsvr"),
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
import com.pulumi.azurenative.sql.BackupShortTermRetentionPolicy;
import com.pulumi.azurenative.sql.BackupShortTermRetentionPolicyArgs;
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
        var backupShortTermRetentionPolicy = new BackupShortTermRetentionPolicy("backupShortTermRetentionPolicy", BackupShortTermRetentionPolicyArgs.builder()        
            .databaseName("testdb")
            .diffBackupIntervalInHours(24)
            .policyName("default")
            .resourceGroupName("resourceGroup")
            .retentionDays(7)
            .serverName("testsvr")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const backupShortTermRetentionPolicy = new azure_native.sql.BackupShortTermRetentionPolicy("backupShortTermRetentionPolicy", {
    databaseName: "testdb",
    diffBackupIntervalInHours: 24,
    policyName: "default",
    resourceGroupName: "resourceGroup",
    retentionDays: 7,
    serverName: "testsvr",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

backup_short_term_retention_policy = azure_native.sql.BackupShortTermRetentionPolicy("backupShortTermRetentionPolicy",
    database_name="testdb",
    diff_backup_interval_in_hours=24,
    policy_name="default",
    resource_group_name="resourceGroup",
    retention_days=7,
    server_name="testsvr")

```

```yaml
resources:
  backupShortTermRetentionPolicy:
    type: azure-native:sql:BackupShortTermRetentionPolicy
    properties:
      databaseName: testdb
      diffBackupIntervalInHours: 24
      policyName: default
      resourceGroupName: resourceGroup
      retentionDays: 7
      serverName: testsvr

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:BackupShortTermRetentionPolicy default /subscriptions/00000000-1111-2222-3333-444444444444/providers/Microsoft.Sql/resourceGroups/resourceGroup/servers/testsvr/databases/testdb/backupShortTermRetentionPolicies/default 
```
