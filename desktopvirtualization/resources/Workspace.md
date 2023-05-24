Represents a Workspace definition.
API Version: 2022-09-09.
Previous API Version: 2021-02-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Workspace_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var workspace = new AzureNative.DesktopVirtualization.Workspace("workspace", new()
    {
        Description = "des1",
        FriendlyName = "friendly",
        Location = "centralus",
        ResourceGroupName = "resourceGroup1",
        Tags = 
        {
            { "tag1", "value1" },
            { "tag2", "value2" },
        },
        WorkspaceName = "workspace1",
    });

});


```

```go
package main

import (
	desktopvirtualization "github.com/pulumi/pulumi-azure-native-sdk/desktopvirtualization"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := desktopvirtualization.NewWorkspace(ctx, "workspace", &desktopvirtualization.WorkspaceArgs{
			Description:       pulumi.String("des1"),
			FriendlyName:      pulumi.String("friendly"),
			Location:          pulumi.String("centralus"),
			ResourceGroupName: pulumi.String("resourceGroup1"),
			Tags: pulumi.StringMap{
				"tag1": pulumi.String("value1"),
				"tag2": pulumi.String("value2"),
			},
			WorkspaceName: pulumi.String("workspace1"),
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
import com.pulumi.azurenative.desktopvirtualization.Workspace;
import com.pulumi.azurenative.desktopvirtualization.WorkspaceArgs;
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
            .description("des1")
            .friendlyName("friendly")
            .location("centralus")
            .resourceGroupName("resourceGroup1")
            .tags(Map.ofEntries(
                Map.entry("tag1", "value1"),
                Map.entry("tag2", "value2")
            ))
            .workspaceName("workspace1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const workspace = new azure_native.desktopvirtualization.Workspace("workspace", {
    description: "des1",
    friendlyName: "friendly",
    location: "centralus",
    resourceGroupName: "resourceGroup1",
    tags: {
        tag1: "value1",
        tag2: "value2",
    },
    workspaceName: "workspace1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

workspace = azure_native.desktopvirtualization.Workspace("workspace",
    description="des1",
    friendly_name="friendly",
    location="centralus",
    resource_group_name="resourceGroup1",
    tags={
        "tag1": "value1",
        "tag2": "value2",
    },
    workspace_name="workspace1")

```

```yaml
resources:
  workspace:
    type: azure-native:desktopvirtualization:Workspace
    properties:
      description: des1
      friendlyName: friendly
      location: centralus
      resourceGroupName: resourceGroup1
      tags:
        tag1: value1
        tag2: value2
      workspaceName: workspace1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:desktopvirtualization:Workspace workspace1 /subscriptions/daefabc0-95b4-48b3-b645-8a753a63c4fa/resourceGroups/resourceGroup1/providers/Microsoft.DesktopVirtualization/workspaces/workspace1 
```
