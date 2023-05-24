The top level Workspace resource container.
API Version: 2022-10-01.
Previous API Version: 2020-10-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### WorkspacesCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var workspace = new AzureNative.OperationalInsights.Workspace("workspace", new()
    {
        Location = "australiasoutheast",
        ResourceGroupName = "oiautorest6685",
        RetentionInDays = 30,
        Sku = new AzureNative.OperationalInsights.Inputs.WorkspaceSkuArgs
        {
            Name = "PerGB2018",
        },
        Tags = 
        {
            { "tag1", "val1" },
        },
        WorkspaceName = "oiautorest6685",
    });

});


```

```go
package main

import (
	operationalinsights "github.com/pulumi/pulumi-azure-native-sdk/operationalinsights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := operationalinsights.NewWorkspace(ctx, "workspace", &operationalinsights.WorkspaceArgs{
			Location:          pulumi.String("australiasoutheast"),
			ResourceGroupName: pulumi.String("oiautorest6685"),
			RetentionInDays:   pulumi.Int(30),
			Sku: &operationalinsights.WorkspaceSkuArgs{
				Name: pulumi.String("PerGB2018"),
			},
			Tags: pulumi.StringMap{
				"tag1": pulumi.String("val1"),
			},
			WorkspaceName: pulumi.String("oiautorest6685"),
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
import com.pulumi.azurenative.operationalinsights.Workspace;
import com.pulumi.azurenative.operationalinsights.WorkspaceArgs;
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
            .location("australiasoutheast")
            .resourceGroupName("oiautorest6685")
            .retentionInDays(30)
            .sku(Map.of("name", "PerGB2018"))
            .tags(Map.of("tag1", "val1"))
            .workspaceName("oiautorest6685")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const workspace = new azure_native.operationalinsights.Workspace("workspace", {
    location: "australiasoutheast",
    resourceGroupName: "oiautorest6685",
    retentionInDays: 30,
    sku: {
        name: "PerGB2018",
    },
    tags: {
        tag1: "val1",
    },
    workspaceName: "oiautorest6685",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

workspace = azure_native.operationalinsights.Workspace("workspace",
    location="australiasoutheast",
    resource_group_name="oiautorest6685",
    retention_in_days=30,
    sku=azure_native.operationalinsights.WorkspaceSkuArgs(
        name="PerGB2018",
    ),
    tags={
        "tag1": "val1",
    },
    workspace_name="oiautorest6685")

```

```yaml
resources:
  workspace:
    type: azure-native:operationalinsights:Workspace
    properties:
      location: australiasoutheast
      resourceGroupName: oiautorest6685
      retentionInDays: 30
      sku:
        name: PerGB2018
      tags:
        tag1: val1
      workspaceName: oiautorest6685

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:operationalinsights:Workspace AzTest2170 /subscriptions/00000000-0000-0000-0000-000000000005/resourcegroups/oiautorest6685/providers/microsoft.operationalinsights/workspaces/aztest2170 
```
