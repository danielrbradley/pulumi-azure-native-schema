Metadata resource definition.
API Version: 2023-02-01.
Previous API Version: 2021-03-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create/update full metadata.
{{% /example %}}
{{% example %}}
### Create/update minimal metadata.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var metadata = new AzureNative.SecurityInsights.Metadata("metadata", new()
    {
        ContentId = "c00ee137-7475-47c8-9cce-ec6f0f1bedd0",
        Kind = "AnalyticsRule",
        MetadataName = "metadataName",
        ParentId = "/subscriptions/2e1dc338-d04d-4443-b721-037eff4fdcac/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace/providers/Microsoft.SecurityInsights/alertRules/ruleName",
        ResourceGroupName = "myRg",
        WorkspaceName = "myWorkspace",
    });

});


```

```go
package main

import (
	securityinsights "github.com/pulumi/pulumi-azure-native-sdk/securityinsights"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := securityinsights.NewMetadata(ctx, "metadata", &securityinsights.MetadataArgs{
			ContentId:         pulumi.String("c00ee137-7475-47c8-9cce-ec6f0f1bedd0"),
			Kind:              pulumi.String("AnalyticsRule"),
			MetadataName:      pulumi.String("metadataName"),
			ParentId:          pulumi.String("/subscriptions/2e1dc338-d04d-4443-b721-037eff4fdcac/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace/providers/Microsoft.SecurityInsights/alertRules/ruleName"),
			ResourceGroupName: pulumi.String("myRg"),
			WorkspaceName:     pulumi.String("myWorkspace"),
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
import com.pulumi.azurenative.securityinsights.Metadata;
import com.pulumi.azurenative.securityinsights.MetadataArgs;
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
        var metadata = new Metadata("metadata", MetadataArgs.builder()        
            .contentId("c00ee137-7475-47c8-9cce-ec6f0f1bedd0")
            .kind("AnalyticsRule")
            .metadataName("metadataName")
            .parentId("/subscriptions/2e1dc338-d04d-4443-b721-037eff4fdcac/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace/providers/Microsoft.SecurityInsights/alertRules/ruleName")
            .resourceGroupName("myRg")
            .workspaceName("myWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const metadata = new azure_native.securityinsights.Metadata("metadata", {
    contentId: "c00ee137-7475-47c8-9cce-ec6f0f1bedd0",
    kind: "AnalyticsRule",
    metadataName: "metadataName",
    parentId: "/subscriptions/2e1dc338-d04d-4443-b721-037eff4fdcac/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace/providers/Microsoft.SecurityInsights/alertRules/ruleName",
    resourceGroupName: "myRg",
    workspaceName: "myWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

metadata = azure_native.securityinsights.Metadata("metadata",
    content_id="c00ee137-7475-47c8-9cce-ec6f0f1bedd0",
    kind="AnalyticsRule",
    metadata_name="metadataName",
    parent_id="/subscriptions/2e1dc338-d04d-4443-b721-037eff4fdcac/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace/providers/Microsoft.SecurityInsights/alertRules/ruleName",
    resource_group_name="myRg",
    workspace_name="myWorkspace")

```

```yaml
resources:
  metadata:
    type: azure-native:securityinsights:Metadata
    properties:
      contentId: c00ee137-7475-47c8-9cce-ec6f0f1bedd0
      kind: AnalyticsRule
      metadataName: metadataName
      parentId: /subscriptions/2e1dc338-d04d-4443-b721-037eff4fdcac/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace/providers/Microsoft.SecurityInsights/alertRules/ruleName
      resourceGroupName: myRg
      workspaceName: myWorkspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:securityinsights:Metadata metadataName /subscriptions/2e1dc338-d04d-4443-b721-037eff4fdcac/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace/providers/Microsoft.SecurityInsights/metadata/metadataName 
```
