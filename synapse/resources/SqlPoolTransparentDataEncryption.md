Represents a Sql pool transparent data encryption configuration.
API Version: 2021-06-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a Sql pool's transparent data encryption configuration
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sqlPoolTransparentDataEncryption = new AzureNative.Synapse.SqlPoolTransparentDataEncryption("sqlPoolTransparentDataEncryption", new()
    {
        ResourceGroupName = "sqlcrudtest-6852",
        SqlPoolName = "sqlcrudtest-9187",
        Status = "Enabled",
        TransparentDataEncryptionName = "current",
        WorkspaceName = "sqlcrudtest-2080",
    });

});


```

```go
package main

import (
	synapse "github.com/pulumi/pulumi-azure-native-sdk/synapse"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := synapse.NewSqlPoolTransparentDataEncryption(ctx, "sqlPoolTransparentDataEncryption", &synapse.SqlPoolTransparentDataEncryptionArgs{
			ResourceGroupName:             pulumi.String("sqlcrudtest-6852"),
			SqlPoolName:                   pulumi.String("sqlcrudtest-9187"),
			Status:                        pulumi.String("Enabled"),
			TransparentDataEncryptionName: pulumi.String("current"),
			WorkspaceName:                 pulumi.String("sqlcrudtest-2080"),
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
import com.pulumi.azurenative.synapse.SqlPoolTransparentDataEncryption;
import com.pulumi.azurenative.synapse.SqlPoolTransparentDataEncryptionArgs;
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
        var sqlPoolTransparentDataEncryption = new SqlPoolTransparentDataEncryption("sqlPoolTransparentDataEncryption", SqlPoolTransparentDataEncryptionArgs.builder()        
            .resourceGroupName("sqlcrudtest-6852")
            .sqlPoolName("sqlcrudtest-9187")
            .status("Enabled")
            .transparentDataEncryptionName("current")
            .workspaceName("sqlcrudtest-2080")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sqlPoolTransparentDataEncryption = new azure_native.synapse.SqlPoolTransparentDataEncryption("sqlPoolTransparentDataEncryption", {
    resourceGroupName: "sqlcrudtest-6852",
    sqlPoolName: "sqlcrudtest-9187",
    status: "Enabled",
    transparentDataEncryptionName: "current",
    workspaceName: "sqlcrudtest-2080",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sql_pool_transparent_data_encryption = azure_native.synapse.SqlPoolTransparentDataEncryption("sqlPoolTransparentDataEncryption",
    resource_group_name="sqlcrudtest-6852",
    sql_pool_name="sqlcrudtest-9187",
    status="Enabled",
    transparent_data_encryption_name="current",
    workspace_name="sqlcrudtest-2080")

```

```yaml
resources:
  sqlPoolTransparentDataEncryption:
    type: azure-native:synapse:SqlPoolTransparentDataEncryption
    properties:
      resourceGroupName: sqlcrudtest-6852
      sqlPoolName: sqlcrudtest-9187
      status: Enabled
      transparentDataEncryptionName: current
      workspaceName: sqlcrudtest-2080

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:synapse:SqlPoolTransparentDataEncryption current /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/sqlcrudtest-6852/providers/Microsoft.Synapse/workspaces/sqlcrudtest-2080/sqlPools/sqlcrudtest-9187/transparentDataEncryption/current 
```
