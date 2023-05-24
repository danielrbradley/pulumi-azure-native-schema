A Geo backup policy.
API Version: 2021-11-01.
Previous API Version: 2014-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a database default Geo backup policy.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var geoBackupPolicy = new AzureNative.Sql.GeoBackupPolicy("geoBackupPolicy", new()
    {
        DatabaseName = "testdw",
        GeoBackupPolicyName = "Default",
        ResourceGroupName = "sqlcrudtest-4799",
        ServerName = "sqlcrudtest-5961",
        State = AzureNative.Sql.GeoBackupPolicyState.Enabled,
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
		_, err := sql.NewGeoBackupPolicy(ctx, "geoBackupPolicy", &sql.GeoBackupPolicyArgs{
			DatabaseName:        pulumi.String("testdw"),
			GeoBackupPolicyName: pulumi.String("Default"),
			ResourceGroupName:   pulumi.String("sqlcrudtest-4799"),
			ServerName:          pulumi.String("sqlcrudtest-5961"),
			State:               sql.GeoBackupPolicyStateEnabled,
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
import com.pulumi.azurenative.sql.GeoBackupPolicy;
import com.pulumi.azurenative.sql.GeoBackupPolicyArgs;
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
        var geoBackupPolicy = new GeoBackupPolicy("geoBackupPolicy", GeoBackupPolicyArgs.builder()        
            .databaseName("testdw")
            .geoBackupPolicyName("Default")
            .resourceGroupName("sqlcrudtest-4799")
            .serverName("sqlcrudtest-5961")
            .state("Enabled")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const geoBackupPolicy = new azure_native.sql.GeoBackupPolicy("geoBackupPolicy", {
    databaseName: "testdw",
    geoBackupPolicyName: "Default",
    resourceGroupName: "sqlcrudtest-4799",
    serverName: "sqlcrudtest-5961",
    state: azure_native.sql.GeoBackupPolicyState.Enabled,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

geo_backup_policy = azure_native.sql.GeoBackupPolicy("geoBackupPolicy",
    database_name="testdw",
    geo_backup_policy_name="Default",
    resource_group_name="sqlcrudtest-4799",
    server_name="sqlcrudtest-5961",
    state=azure_native.sql.GeoBackupPolicyState.ENABLED)

```

```yaml
resources:
  geoBackupPolicy:
    type: azure-native:sql:GeoBackupPolicy
    properties:
      databaseName: testdw
      geoBackupPolicyName: Default
      resourceGroupName: sqlcrudtest-4799
      serverName: sqlcrudtest-5961
      state: Enabled

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:GeoBackupPolicy Default /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/sqlcrudtest-4799/providers/Microsoft.Sql/servers/sqlcrudtest-5961/databases/testdw/geoBackupPolicies/Default 
```
