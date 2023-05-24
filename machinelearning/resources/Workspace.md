An object that represents a machine learning workspace.
API Version: 2019-10-01.
Previous API Version: 2016-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### WorkspaceCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var workspace = new AzureNative.MachineLearning.Workspace("workspace", new()
    {
        Location = "West Europe",
        OwnerEmail = "abc@microsoft.com",
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.MachineLearning.Inputs.SkuArgs
        {
            Name = "Enterprise",
            Tier = "Enterprise",
        },
        Tags = 
        {
            { "tagKey1", "TagValue1" },
        },
        UserStorageAccountId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/teststorage",
        WorkspaceName = "testworkspace",
    });

});


```

```go
package main

import (
	machinelearning "github.com/pulumi/pulumi-azure-native-sdk/machinelearning"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := machinelearning.NewWorkspace(ctx, "workspace", &machinelearning.WorkspaceArgs{
			Location:          pulumi.String("West Europe"),
			OwnerEmail:        pulumi.String("abc@microsoft.com"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			Sku: &machinelearning.SkuArgs{
				Name: pulumi.String("Enterprise"),
				Tier: pulumi.String("Enterprise"),
			},
			Tags: pulumi.StringMap{
				"tagKey1": pulumi.String("TagValue1"),
			},
			UserStorageAccountId: pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/teststorage"),
			WorkspaceName:        pulumi.String("testworkspace"),
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
import com.pulumi.azurenative.machinelearning.Workspace;
import com.pulumi.azurenative.machinelearning.WorkspaceArgs;
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
        var workspace = new Workspace("workspace", WorkspaceArgs.builder()        
            .location("West Europe")
            .ownerEmail("abc@microsoft.com")
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("name", "Enterprise"),
                Map.entry("tier", "Enterprise")
            ))
            .tags(Map.of("tagKey1", "TagValue1"))
            .userStorageAccountId("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/teststorage")
            .workspaceName("testworkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const workspace = new azure_native.machinelearning.Workspace("workspace", {
    location: "West Europe",
    ownerEmail: "abc@microsoft.com",
    resourceGroupName: "myResourceGroup",
    sku: {
        name: "Enterprise",
        tier: "Enterprise",
    },
    tags: {
        tagKey1: "TagValue1",
    },
    userStorageAccountId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/teststorage",
    workspaceName: "testworkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

workspace = azure_native.machinelearning.Workspace("workspace",
    location="West Europe",
    owner_email="abc@microsoft.com",
    resource_group_name="myResourceGroup",
    sku=azure_native.machinelearning.SkuArgs(
        name="Enterprise",
        tier="Enterprise",
    ),
    tags={
        "tagKey1": "TagValue1",
    },
    user_storage_account_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/teststorage",
    workspace_name="testworkspace")

```

```yaml
resources:
  workspace:
    type: azure-native:machinelearning:Workspace
    properties:
      location: West Europe
      ownerEmail: abc@microsoft.com
      resourceGroupName: myResourceGroup
      sku:
        name: Enterprise
        tier: Enterprise
      tags:
        tagKey1: TagValue1
      userStorageAccountId: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.Storage/storageAccounts/teststorage
      workspaceName: testworkspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:machinelearning:Workspace testworkspace /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.MachineLearning/workspaces/testworkspace 
```
