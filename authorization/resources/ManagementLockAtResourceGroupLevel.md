The lock information.
API Version: 2020-05-01.
Previous API Version: 2017-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create management lock at resource group level
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managementLockAtResourceGroupLevel = new AzureNative.Authorization.ManagementLockAtResourceGroupLevel("managementLockAtResourceGroupLevel", new()
    {
        Level = "ReadOnly",
        LockName = "testlock",
        ResourceGroupName = "resourcegroupname",
    });

});


```

```go
package main

import (
	authorization "github.com/pulumi/pulumi-azure-native-sdk/authorization"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := authorization.NewManagementLockAtResourceGroupLevel(ctx, "managementLockAtResourceGroupLevel", &authorization.ManagementLockAtResourceGroupLevelArgs{
			Level:             pulumi.String("ReadOnly"),
			LockName:          pulumi.String("testlock"),
			ResourceGroupName: pulumi.String("resourcegroupname"),
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
import com.pulumi.azurenative.authorization.ManagementLockAtResourceGroupLevel;
import com.pulumi.azurenative.authorization.ManagementLockAtResourceGroupLevelArgs;
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
        var managementLockAtResourceGroupLevel = new ManagementLockAtResourceGroupLevel("managementLockAtResourceGroupLevel", ManagementLockAtResourceGroupLevelArgs.builder()        
            .level("ReadOnly")
            .lockName("testlock")
            .resourceGroupName("resourcegroupname")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managementLockAtResourceGroupLevel = new azure_native.authorization.ManagementLockAtResourceGroupLevel("managementLockAtResourceGroupLevel", {
    level: "ReadOnly",
    lockName: "testlock",
    resourceGroupName: "resourcegroupname",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

management_lock_at_resource_group_level = azure_native.authorization.ManagementLockAtResourceGroupLevel("managementLockAtResourceGroupLevel",
    level="ReadOnly",
    lock_name="testlock",
    resource_group_name="resourcegroupname")

```

```yaml
resources:
  managementLockAtResourceGroupLevel:
    type: azure-native:authorization:ManagementLockAtResourceGroupLevel
    properties:
      level: ReadOnly
      lockName: testlock
      resourceGroupName: resourcegroupname

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:authorization:ManagementLockAtResourceGroupLevel testlock /subscriptions/subscriptionId/resourceGroups/resourcegroupname/providers/Microsoft.Authorization/locks/testlock 
```
