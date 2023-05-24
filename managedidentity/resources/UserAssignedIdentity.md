Describes an identity resource.
API Version: 2023-01-31.
Previous API Version: 2018-11-30. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### IdentityCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var userAssignedIdentity = new AzureNative.ManagedIdentity.UserAssignedIdentity("userAssignedIdentity", new()
    {
        Location = "eastus",
        ResourceGroupName = "rgName",
        ResourceName = "resourceName",
        Tags = 
        {
            { "key1", "value1" },
            { "key2", "value2" },
        },
    });

});


```

```go
package main

import (
	managedidentity "github.com/pulumi/pulumi-azure-native-sdk/managedidentity"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := managedidentity.NewUserAssignedIdentity(ctx, "userAssignedIdentity", &managedidentity.UserAssignedIdentityArgs{
			Location:          pulumi.String("eastus"),
			ResourceGroupName: pulumi.String("rgName"),
			ResourceName:      pulumi.String("resourceName"),
			Tags: pulumi.StringMap{
				"key1": pulumi.String("value1"),
				"key2": pulumi.String("value2"),
			},
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
import com.pulumi.azurenative.managedidentity.UserAssignedIdentity;
import com.pulumi.azurenative.managedidentity.UserAssignedIdentityArgs;
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
        var userAssignedIdentity = new UserAssignedIdentity("userAssignedIdentity", UserAssignedIdentityArgs.builder()        
            .location("eastus")
            .resourceGroupName("rgName")
            .resourceName("resourceName")
            .tags(Map.ofEntries(
                Map.entry("key1", "value1"),
                Map.entry("key2", "value2")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const userAssignedIdentity = new azure_native.managedidentity.UserAssignedIdentity("userAssignedIdentity", {
    location: "eastus",
    resourceGroupName: "rgName",
    resourceName: "resourceName",
    tags: {
        key1: "value1",
        key2: "value2",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

user_assigned_identity = azure_native.managedidentity.UserAssignedIdentity("userAssignedIdentity",
    location="eastus",
    resource_group_name="rgName",
    resource_name_="resourceName",
    tags={
        "key1": "value1",
        "key2": "value2",
    })

```

```yaml
resources:
  userAssignedIdentity:
    type: azure-native:managedidentity:UserAssignedIdentity
    properties:
      location: eastus
      resourceGroupName: rgName
      resourceName: resourceName
      tags:
        key1: value1
        key2: value2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:managedidentity:UserAssignedIdentity identityName /subscriptions/subid/resourcegroups/rgName/providers/Microsoft.ManagedIdentity/userAssignedIdentities/identityName 
```
