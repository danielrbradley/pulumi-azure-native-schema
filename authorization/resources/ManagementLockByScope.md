The lock information.
API Version: 2020-05-01.
Previous API Version: 2017-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create management lock at scope
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managementLockByScope = new AzureNative.Authorization.ManagementLockByScope("managementLockByScope", new()
    {
        Level = "ReadOnly",
        LockName = "testlock",
        Scope = "subscriptions/subscriptionId",
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
		_, err := authorization.NewManagementLockByScope(ctx, "managementLockByScope", &authorization.ManagementLockByScopeArgs{
			Level:    pulumi.String("ReadOnly"),
			LockName: pulumi.String("testlock"),
			Scope:    pulumi.String("subscriptions/subscriptionId"),
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
import com.pulumi.azurenative.authorization.ManagementLockByScope;
import com.pulumi.azurenative.authorization.ManagementLockByScopeArgs;
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
        var managementLockByScope = new ManagementLockByScope("managementLockByScope", ManagementLockByScopeArgs.builder()        
            .level("ReadOnly")
            .lockName("testlock")
            .scope("subscriptions/subscriptionId")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managementLockByScope = new azure_native.authorization.ManagementLockByScope("managementLockByScope", {
    level: "ReadOnly",
    lockName: "testlock",
    scope: "subscriptions/subscriptionId",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

management_lock_by_scope = azure_native.authorization.ManagementLockByScope("managementLockByScope",
    level="ReadOnly",
    lock_name="testlock",
    scope="subscriptions/subscriptionId")

```

```yaml
resources:
  managementLockByScope:
    type: azure-native:authorization:ManagementLockByScope
    properties:
      level: ReadOnly
      lockName: testlock
      scope: subscriptions/subscriptionId

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:authorization:ManagementLockByScope testlock /subscriptions/subscriptionId/resourceGroups/resourcegroupname/providers/Microsoft.Authorization/locks/testlock 
```
