Label details
API Version: 2022-04-01-preview.
Previous API Version: 2022-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Labels
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var labelByWorkspace = new AzureNative.Easm.LabelByWorkspace("labelByWorkspace", new()
    {
        LabelName = "ThisisaLabel",
        ResourceGroupName = "dummyrg",
        WorkspaceName = "ThisisaWorkspace",
    });

});


```

```go
package main

import (
	easm "github.com/pulumi/pulumi-azure-native-sdk/easm"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := easm.NewLabelByWorkspace(ctx, "labelByWorkspace", &easm.LabelByWorkspaceArgs{
			LabelName:         pulumi.String("ThisisaLabel"),
			ResourceGroupName: pulumi.String("dummyrg"),
			WorkspaceName:     pulumi.String("ThisisaWorkspace"),
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
import com.pulumi.azurenative.easm.LabelByWorkspace;
import com.pulumi.azurenative.easm.LabelByWorkspaceArgs;
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
        var labelByWorkspace = new LabelByWorkspace("labelByWorkspace", LabelByWorkspaceArgs.builder()        
            .labelName("ThisisaLabel")
            .resourceGroupName("dummyrg")
            .workspaceName("ThisisaWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const labelByWorkspace = new azure_native.easm.LabelByWorkspace("labelByWorkspace", {
    labelName: "ThisisaLabel",
    resourceGroupName: "dummyrg",
    workspaceName: "ThisisaWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

label_by_workspace = azure_native.easm.LabelByWorkspace("labelByWorkspace",
    label_name="ThisisaLabel",
    resource_group_name="dummyrg",
    workspace_name="ThisisaWorkspace")

```

```yaml
resources:
  labelByWorkspace:
    type: azure-native:easm:LabelByWorkspace
    properties:
      labelName: ThisisaLabel
      resourceGroupName: dummyrg
      workspaceName: ThisisaWorkspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:easm:LabelByWorkspace ThisisaLabel /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/dummyrg/providers/Microsoft.Easm/workspaces/ThisisaWorkspace/labels/ThisisaLabel 
```
