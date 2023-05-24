The details of subscription under management group.
API Version: 2021-04-01.
Previous API Version: 2020-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### AddSubscriptionToManagementGroup
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managementGroupSubscription = new AzureNative.Management.ManagementGroupSubscription("managementGroupSubscription", new()
    {
        GroupId = "Group",
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
		_, err := management.NewManagementGroupSubscription(ctx, "managementGroupSubscription", &management.ManagementGroupSubscriptionArgs{
			GroupId: pulumi.String("Group"),
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
import com.pulumi.azurenative.management.ManagementGroupSubscription;
import com.pulumi.azurenative.management.ManagementGroupSubscriptionArgs;
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
        var managementGroupSubscription = new ManagementGroupSubscription("managementGroupSubscription", ManagementGroupSubscriptionArgs.builder()        
            .groupId("Group")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managementGroupSubscription = new azure_native.management.ManagementGroupSubscription("managementGroupSubscription", {groupId: "Group"});

```

```python
import pulumi
import pulumi_azure_native as azure_native

management_group_subscription = azure_native.management.ManagementGroupSubscription("managementGroupSubscription", group_id="Group")

```

```yaml
resources:
  managementGroupSubscription:
    type: azure-native:management:ManagementGroupSubscription
    properties:
      groupId: Group

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:management:ManagementGroupSubscription 728bcbe4-8d56-4510-86c2-4921b8beefbc  /providers/Microsoft.Management/managementGroups/Group/subscriptions/728bcbe4-8d56-4510-86c2-4921b8beefbc 
```
