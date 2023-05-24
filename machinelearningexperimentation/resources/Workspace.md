An object that represents a machine learning team account workspace.
API Version: 2017-05-01-preview.
Previous API Version: 2017-05-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

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
    var workspace = new AzureNative.MachineLearningExperimentation.Workspace("workspace", new()
    {
        AccountName = "testaccount",
        FriendlyName = "testName",
        Location = "East US",
        ResourceGroupName = "myResourceGroup",
        Tags = 
        {
            { "tagKey1", "TagValue1" },
        },
        WorkspaceName = "testworkspace",
    });

});


```

```go
package main

import (
	machinelearningexperimentation "github.com/pulumi/pulumi-azure-native-sdk/machinelearningexperimentation"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := machinelearningexperimentation.NewWorkspace(ctx, "workspace", &machinelearningexperimentation.WorkspaceArgs{
			AccountName:       pulumi.String("testaccount"),
			FriendlyName:      pulumi.String("testName"),
			Location:          pulumi.String("East US"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
			Tags: pulumi.StringMap{
				"tagKey1": pulumi.String("TagValue1"),
			},
			WorkspaceName: pulumi.String("testworkspace"),
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
import com.pulumi.azurenative.machinelearningexperimentation.Workspace;
import com.pulumi.azurenative.machinelearningexperimentation.WorkspaceArgs;
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
            .accountName("testaccount")
            .friendlyName("testName")
            .location("East US")
            .resourceGroupName("myResourceGroup")
            .tags(Map.of("tagKey1", "TagValue1"))
            .workspaceName("testworkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const workspace = new azure_native.machinelearningexperimentation.Workspace("workspace", {
    accountName: "testaccount",
    friendlyName: "testName",
    location: "East US",
    resourceGroupName: "myResourceGroup",
    tags: {
        tagKey1: "TagValue1",
    },
    workspaceName: "testworkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

workspace = azure_native.machinelearningexperimentation.Workspace("workspace",
    account_name="testaccount",
    friendly_name="testName",
    location="East US",
    resource_group_name="myResourceGroup",
    tags={
        "tagKey1": "TagValue1",
    },
    workspace_name="testworkspace")

```

```yaml
resources:
  workspace:
    type: azure-native:machinelearningexperimentation:Workspace
    properties:
      accountName: testaccount
      friendlyName: testName
      location: East US
      resourceGroupName: myResourceGroup
      tags:
        tagKey1: TagValue1
      workspaceName: testworkspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:machinelearningexperimentation:Workspace testworkspace /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myResourceGroup/providers/Microsoft.MachineLearningExperimentation/accounts/testaccount/workspaces/testworkspace 
```
