The management group details.
API Version: 2021-04-01.
Previous API Version: 2020-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PutManagementGroup
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managementGroup = new AzureNative.Management.ManagementGroup("managementGroup", new()
    {
        Details = new AzureNative.Management.Inputs.CreateManagementGroupDetailsArgs
        {
            Parent = new AzureNative.Management.Inputs.CreateParentGroupInfoArgs
            {
                Id = "/providers/Microsoft.Management/managementGroups/RootGroup",
            },
        },
        DisplayName = "ChildGroup",
        GroupId = "ChildGroup",
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
		_, err := management.NewManagementGroup(ctx, "managementGroup", &management.ManagementGroupArgs{
			Details: management.ManagementGroupDetailsResponse{
				Parent: &management.CreateParentGroupInfoArgs{
					Id: pulumi.String("/providers/Microsoft.Management/managementGroups/RootGroup"),
				},
			},
			DisplayName: pulumi.String("ChildGroup"),
			GroupId:     pulumi.String("ChildGroup"),
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
import com.pulumi.azurenative.management.ManagementGroup;
import com.pulumi.azurenative.management.ManagementGroupArgs;
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
        var managementGroup = new ManagementGroup("managementGroup", ManagementGroupArgs.builder()        
            .details(Map.of("parent", Map.of("id", "/providers/Microsoft.Management/managementGroups/RootGroup")))
            .displayName("ChildGroup")
            .groupId("ChildGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managementGroup = new azure_native.management.ManagementGroup("managementGroup", {
    details: {
        parent: {
            id: "/providers/Microsoft.Management/managementGroups/RootGroup",
        },
    },
    displayName: "ChildGroup",
    groupId: "ChildGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

management_group = azure_native.management.ManagementGroup("managementGroup",
    details=azure_native.management.ManagementGroupDetailsResponseArgs(
        parent=azure_native.management.CreateParentGroupInfoArgs(
            id="/providers/Microsoft.Management/managementGroups/RootGroup",
        ),
    ),
    display_name="ChildGroup",
    group_id="ChildGroup")

```

```yaml
resources:
  managementGroup:
    type: azure-native:management:ManagementGroup
    properties:
      details:
        parent:
          id: /providers/Microsoft.Management/managementGroups/RootGroup
      displayName: ChildGroup
      groupId: ChildGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:management:ManagementGroup ChildGroup /providers/Microsoft.Management/managementGroups/ChildGroup 
```
