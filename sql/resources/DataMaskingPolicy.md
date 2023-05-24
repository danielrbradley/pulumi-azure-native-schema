A database data masking policy.
API Version: 2021-11-01.
Previous API Version: 2014-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update data masking policy max
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var dataMaskingPolicy = new AzureNative.Sql.DataMaskingPolicy("dataMaskingPolicy", new()
    {
        DataMaskingPolicyName = "Default",
        DataMaskingState = AzureNative.Sql.DataMaskingState.Enabled,
        DatabaseName = "sqlcrudtest-331",
        ExemptPrincipals = "testuser;",
        ResourceGroupName = "sqlcrudtest-6852",
        ServerName = "sqlcrudtest-2080",
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
		_, err := sql.NewDataMaskingPolicy(ctx, "dataMaskingPolicy", &sql.DataMaskingPolicyArgs{
			DataMaskingPolicyName: pulumi.String("Default"),
			DataMaskingState:      sql.DataMaskingStateEnabled,
			DatabaseName:          pulumi.String("sqlcrudtest-331"),
			ExemptPrincipals:      pulumi.String("testuser;"),
			ResourceGroupName:     pulumi.String("sqlcrudtest-6852"),
			ServerName:            pulumi.String("sqlcrudtest-2080"),
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
import com.pulumi.azurenative.sql.DataMaskingPolicy;
import com.pulumi.azurenative.sql.DataMaskingPolicyArgs;
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
        var dataMaskingPolicy = new DataMaskingPolicy("dataMaskingPolicy", DataMaskingPolicyArgs.builder()        
            .dataMaskingPolicyName("Default")
            .dataMaskingState("Enabled")
            .databaseName("sqlcrudtest-331")
            .exemptPrincipals("testuser;")
            .resourceGroupName("sqlcrudtest-6852")
            .serverName("sqlcrudtest-2080")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const dataMaskingPolicy = new azure_native.sql.DataMaskingPolicy("dataMaskingPolicy", {
    dataMaskingPolicyName: "Default",
    dataMaskingState: azure_native.sql.DataMaskingState.Enabled,
    databaseName: "sqlcrudtest-331",
    exemptPrincipals: "testuser;",
    resourceGroupName: "sqlcrudtest-6852",
    serverName: "sqlcrudtest-2080",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

data_masking_policy = azure_native.sql.DataMaskingPolicy("dataMaskingPolicy",
    data_masking_policy_name="Default",
    data_masking_state=azure_native.sql.DataMaskingState.ENABLED,
    database_name="sqlcrudtest-331",
    exempt_principals="testuser;",
    resource_group_name="sqlcrudtest-6852",
    server_name="sqlcrudtest-2080")

```

```yaml
resources:
  dataMaskingPolicy:
    type: azure-native:sql:DataMaskingPolicy
    properties:
      dataMaskingPolicyName: Default
      dataMaskingState: Enabled
      databaseName: sqlcrudtest-331
      exemptPrincipals: testuser;
      resourceGroupName: sqlcrudtest-6852
      serverName: sqlcrudtest-2080

```

{{% /example %}}
{{% example %}}
### Create or update data masking policy min.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var dataMaskingPolicy = new AzureNative.Sql.DataMaskingPolicy("dataMaskingPolicy", new()
    {
        DataMaskingPolicyName = "Default",
        DataMaskingState = AzureNative.Sql.DataMaskingState.Enabled,
        DatabaseName = "sqlcrudtest-331",
        ResourceGroupName = "sqlcrudtest-6852",
        ServerName = "sqlcrudtest-2080",
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
		_, err := sql.NewDataMaskingPolicy(ctx, "dataMaskingPolicy", &sql.DataMaskingPolicyArgs{
			DataMaskingPolicyName: pulumi.String("Default"),
			DataMaskingState:      sql.DataMaskingStateEnabled,
			DatabaseName:          pulumi.String("sqlcrudtest-331"),
			ResourceGroupName:     pulumi.String("sqlcrudtest-6852"),
			ServerName:            pulumi.String("sqlcrudtest-2080"),
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
import com.pulumi.azurenative.sql.DataMaskingPolicy;
import com.pulumi.azurenative.sql.DataMaskingPolicyArgs;
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
        var dataMaskingPolicy = new DataMaskingPolicy("dataMaskingPolicy", DataMaskingPolicyArgs.builder()        
            .dataMaskingPolicyName("Default")
            .dataMaskingState("Enabled")
            .databaseName("sqlcrudtest-331")
            .resourceGroupName("sqlcrudtest-6852")
            .serverName("sqlcrudtest-2080")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const dataMaskingPolicy = new azure_native.sql.DataMaskingPolicy("dataMaskingPolicy", {
    dataMaskingPolicyName: "Default",
    dataMaskingState: azure_native.sql.DataMaskingState.Enabled,
    databaseName: "sqlcrudtest-331",
    resourceGroupName: "sqlcrudtest-6852",
    serverName: "sqlcrudtest-2080",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

data_masking_policy = azure_native.sql.DataMaskingPolicy("dataMaskingPolicy",
    data_masking_policy_name="Default",
    data_masking_state=azure_native.sql.DataMaskingState.ENABLED,
    database_name="sqlcrudtest-331",
    resource_group_name="sqlcrudtest-6852",
    server_name="sqlcrudtest-2080")

```

```yaml
resources:
  dataMaskingPolicy:
    type: azure-native:sql:DataMaskingPolicy
    properties:
      dataMaskingPolicyName: Default
      dataMaskingState: Enabled
      databaseName: sqlcrudtest-331
      resourceGroupName: sqlcrudtest-6852
      serverName: sqlcrudtest-2080

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:sql:DataMaskingPolicy Default /subscriptions/00000000-1111-2222-3333-444444444444/resourceGroups/sqlcrudtest-6852/providers/Microsoft.Sql/servers/sqlcrudtest-2080/databases/sqlcrudtest-331/dataMaskingPolicies/Default 
```
