Represents a cluster role.
API Version: 2022-11-08.

{{% examples %}}
## Example Usage
{{% example %}}
### RoleCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var role = new AzureNative.DBforPostgreSQL.Role("role", new()
    {
        ClusterName = "pgtestsvc4",
        Password = "password",
        ResourceGroupName = "TestGroup",
        RoleName = "role1",
    });

});


```

```go
package main

import (
	dbforpostgresql "github.com/pulumi/pulumi-azure-native-sdk/dbforpostgresql"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := dbforpostgresql.NewRole(ctx, "role", &dbforpostgresql.RoleArgs{
			ClusterName:       pulumi.String("pgtestsvc4"),
			Password:          pulumi.String("password"),
			ResourceGroupName: pulumi.String("TestGroup"),
			RoleName:          pulumi.String("role1"),
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
import com.pulumi.azurenative.dbforpostgresql.Role;
import com.pulumi.azurenative.dbforpostgresql.RoleArgs;
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
        var role = new Role("role", RoleArgs.builder()        
            .clusterName("pgtestsvc4")
            .password("password")
            .resourceGroupName("TestGroup")
            .roleName("role1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const role = new azure_native.dbforpostgresql.Role("role", {
    clusterName: "pgtestsvc4",
    password: "password",
    resourceGroupName: "TestGroup",
    roleName: "role1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

role = azure_native.dbforpostgresql.Role("role",
    cluster_name="pgtestsvc4",
    password="password",
    resource_group_name="TestGroup",
    role_name="role1")

```

```yaml
resources:
  role:
    type: azure-native:dbforpostgresql:Role
    properties:
      clusterName: pgtestsvc4
      password: password
      resourceGroupName: TestGroup
      roleName: role1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:dbforpostgresql:Role role1 /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/TestGroup/providers/Microsoft.DBforPostgreSQL/serverGroupsv2/pgtestsvc4/roles/role1 
```
