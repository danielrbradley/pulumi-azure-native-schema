Settings defined at the Management Group scope.
API Version: 2021-04-01.
Previous API Version: 2020-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### GetGroupSettings
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var hierarchySetting = new AzureNative.Management.HierarchySetting("hierarchySetting", new()
    {
        DefaultManagementGroup = "/providers/Microsoft.Management/managementGroups/DefaultGroup",
        GroupId = "root",
        RequireAuthorizationForGroupCreation = true,
    });

});


```

```go
package main

import (
	management "github.com/pulumi/pulumi-azure-native-sdk/management"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := management.NewHierarchySetting(ctx, "hierarchySetting", &management.HierarchySettingArgs{
			DefaultManagementGroup:               pulumi.String("/providers/Microsoft.Management/managementGroups/DefaultGroup"),
			GroupId:                              pulumi.String("root"),
			RequireAuthorizationForGroupCreation: pulumi.Bool(true),
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
import com.pulumi.azurenative.management.HierarchySetting;
import com.pulumi.azurenative.management.HierarchySettingArgs;
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
        var hierarchySetting = new HierarchySetting("hierarchySetting", HierarchySettingArgs.builder()        
            .defaultManagementGroup("/providers/Microsoft.Management/managementGroups/DefaultGroup")
            .groupId("root")
            .requireAuthorizationForGroupCreation(true)
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const hierarchySetting = new azure_native.management.HierarchySetting("hierarchySetting", {
    defaultManagementGroup: "/providers/Microsoft.Management/managementGroups/DefaultGroup",
    groupId: "root",
    requireAuthorizationForGroupCreation: true,
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

hierarchy_setting = azure_native.management.HierarchySetting("hierarchySetting",
    default_management_group="/providers/Microsoft.Management/managementGroups/DefaultGroup",
    group_id="root",
    require_authorization_for_group_creation=True)

```

```yaml
resources:
  hierarchySetting:
    type: azure-native:management:HierarchySetting
    properties:
      defaultManagementGroup: /providers/Microsoft.Management/managementGroups/DefaultGroup
      groupId: root
      requireAuthorizationForGroupCreation: true

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:management:HierarchySetting root /providers/Microsoft.Management/managementGroups/root/settings/default 
```
