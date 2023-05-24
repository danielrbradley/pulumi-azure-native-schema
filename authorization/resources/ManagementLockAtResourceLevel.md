The lock information.
API Version: 2020-05-01.
Previous API Version: 2017-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create management lock at resource level
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managementLockAtResourceLevel = new AzureNative.Authorization.ManagementLockAtResourceLevel("managementLockAtResourceLevel", new()
    {
        Level = "ReadOnly",
        LockName = "testlock",
        ParentResourcePath = "parentResourcePath",
        ResourceGroupName = "resourcegroupname",
        ResourceName = "teststorageaccount",
        ResourceProviderNamespace = "Microsoft.Storage",
        ResourceType = "storageAccounts",
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
		_, err := authorization.NewManagementLockAtResourceLevel(ctx, "managementLockAtResourceLevel", &authorization.ManagementLockAtResourceLevelArgs{
			Level:                     pulumi.String("ReadOnly"),
			LockName:                  pulumi.String("testlock"),
			ParentResourcePath:        pulumi.String("parentResourcePath"),
			ResourceGroupName:         pulumi.String("resourcegroupname"),
			ResourceName:              pulumi.String("teststorageaccount"),
			ResourceProviderNamespace: pulumi.String("Microsoft.Storage"),
			ResourceType:              pulumi.String("storageAccounts"),
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
import com.pulumi.azurenative.authorization.ManagementLockAtResourceLevel;
import com.pulumi.azurenative.authorization.ManagementLockAtResourceLevelArgs;
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
        var managementLockAtResourceLevel = new ManagementLockAtResourceLevel("managementLockAtResourceLevel", ManagementLockAtResourceLevelArgs.builder()        
            .level("ReadOnly")
            .lockName("testlock")
            .parentResourcePath("parentResourcePath")
            .resourceGroupName("resourcegroupname")
            .resourceName("teststorageaccount")
            .resourceProviderNamespace("Microsoft.Storage")
            .resourceType("storageAccounts")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managementLockAtResourceLevel = new azure_native.authorization.ManagementLockAtResourceLevel("managementLockAtResourceLevel", {
    level: "ReadOnly",
    lockName: "testlock",
    parentResourcePath: "parentResourcePath",
    resourceGroupName: "resourcegroupname",
    resourceName: "teststorageaccount",
    resourceProviderNamespace: "Microsoft.Storage",
    resourceType: "storageAccounts",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

management_lock_at_resource_level = azure_native.authorization.ManagementLockAtResourceLevel("managementLockAtResourceLevel",
    level="ReadOnly",
    lock_name="testlock",
    parent_resource_path="parentResourcePath",
    resource_group_name="resourcegroupname",
    resource_name_="teststorageaccount",
    resource_provider_namespace="Microsoft.Storage",
    resource_type="storageAccounts")

```

```yaml
resources:
  managementLockAtResourceLevel:
    type: azure-native:authorization:ManagementLockAtResourceLevel
    properties:
      level: ReadOnly
      lockName: testlock
      parentResourcePath: parentResourcePath
      resourceGroupName: resourcegroupname
      resourceName: teststorageaccount
      resourceProviderNamespace: Microsoft.Storage
      resourceType: storageAccounts

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:authorization:ManagementLockAtResourceLevel testlock /subscriptions/subscriptionId/resourceGroups/resourcegroupname/providers/Microsoft.Authorization/locks/testlock 
```
