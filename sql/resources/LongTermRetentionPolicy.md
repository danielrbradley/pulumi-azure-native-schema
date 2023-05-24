A long term retention policy.
API Version: 2021-11-01.
Previous API Version: 2020-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update the long term retention policy for the database.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var longTermRetentionPolicy = new AzureNative.Sql.LongTermRetentionPolicy("longTermRetentionPolicy", new()
    {
        DatabaseName = "testDatabase",
        MonthlyRetention = "P1Y",
        PolicyName = "default",
        ResourceGroupName = "resourceGroup",
        ServerName = "testserver",
        WeekOfYear = 5,
        WeeklyRetention = "P1M",
        YearlyRetention = "P5Y",
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
		_, err := sql.NewLongTermRetentionPolicy(ctx, "longTermRetentionPolicy", &sql.LongTermRetentionPolicyArgs{
			DatabaseName:      pulumi.String("testDatabase"),
			MonthlyRetention:  pulumi.String("P1Y"),
			PolicyName:        pulumi.String("default"),
			ResourceGroupName: pulumi.String("resourceGroup"),
			ServerName:        pulumi.String("testserver"),
			WeekOfYear:        pulumi.Int(5),
			WeeklyRetention:   pulumi.String("P1M"),
			YearlyRetention:   pulumi.String("P5Y"),
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
import com.pulumi.azurenative.sql.LongTermRetentionPolicy;
import com.pulumi.azurenative.sql.LongTermRetentionPolicyArgs;
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
        var longTermRetentionPolicy = new LongTermRetentionPolicy("longTermRetentionPolicy", LongTermRetentionPolicyArgs.builder()        
            .databaseName("testDatabase")
            .monthlyRetention("P1Y")
            .policyName("default")
            .resourceGroupName("resourceGroup")
            .serverName("testserver")
            .weekOfYear(5)
            .weeklyRetention("P1M")
            .yearlyRetention("P5Y")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const longTermRetentionPolicy = new azure_native.sql.LongTermRetentionPolicy("longTermRetentionPolicy", {
    databaseName: "testDatabase",
    monthlyRetention: "P1Y",
    policyName: "default",
    resourceGroupName: "resourceGroup",
    serverName: "testserver",
    weekOfYear: 5,
    weeklyRetention: "P1M",
    yearlyRetention: "P5Y",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

long_term_retention_policy = azure_native.sql.LongTermRetentionPolicy("longTermRetentionPolicy",
    database_name="testDatabase",
    monthly_retention="P1Y",
    policy_name="default",
    resource_group_name="resourceGroup",
    server_name="testserver",
    week_of_year=5,
    weekly_retention="P1M",
    yearly_retention="P5Y")

```

```yaml
resources:
  longTermRetentionPolicy:
    type: azure-native:sql:LongTermRetentionPolicy
    properties:
      databaseName: testDatabase
      monthlyRetention: P1Y
      policyName: default
      resourceGroupName: resourceGroup
      serverName: testserver
      weekOfYear: 5
      weeklyRetention: P1M
      yearlyRetention: P5Y

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:LongTermRetentionPolicy default /subscriptions/00000000-1111-2222-3333-444444444444/providers/Microsoft.Sql/resourceGroups/resourceGroup/servers/testserver/databases/testDatabase/backupLongTermRetentionPolicies/default 
```
