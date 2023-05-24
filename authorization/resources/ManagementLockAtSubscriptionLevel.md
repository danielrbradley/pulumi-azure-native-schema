The lock information.
API Version: 2020-05-01.
Previous API Version: 2017-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create management lock at subscription level
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managementLockAtSubscriptionLevel = new AzureNative.Authorization.ManagementLockAtSubscriptionLevel("managementLockAtSubscriptionLevel", new()
    {
        Level = "ReadOnly",
        LockName = "testlock",
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
		_, err := authorization.NewManagementLockAtSubscriptionLevel(ctx, "managementLockAtSubscriptionLevel", &authorization.ManagementLockAtSubscriptionLevelArgs{
			Level:    pulumi.String("ReadOnly"),
			LockName: pulumi.String("testlock"),
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
import com.pulumi.azurenative.authorization.ManagementLockAtSubscriptionLevel;
import com.pulumi.azurenative.authorization.ManagementLockAtSubscriptionLevelArgs;
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
        var managementLockAtSubscriptionLevel = new ManagementLockAtSubscriptionLevel("managementLockAtSubscriptionLevel", ManagementLockAtSubscriptionLevelArgs.builder()        
            .level("ReadOnly")
            .lockName("testlock")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managementLockAtSubscriptionLevel = new azure_native.authorization.ManagementLockAtSubscriptionLevel("managementLockAtSubscriptionLevel", {
    level: "ReadOnly",
    lockName: "testlock",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

management_lock_at_subscription_level = azure_native.authorization.ManagementLockAtSubscriptionLevel("managementLockAtSubscriptionLevel",
    level="ReadOnly",
    lock_name="testlock")

```

```yaml
resources:
  managementLockAtSubscriptionLevel:
    type: azure-native:authorization:ManagementLockAtSubscriptionLevel
    properties:
      level: ReadOnly
      lockName: testlock

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:authorization:ManagementLockAtSubscriptionLevel testlock /subscriptions/subscriptionId/resourceGroups/resourcegroupname/providers/Microsoft.Authorization/locks/testlock 
```
