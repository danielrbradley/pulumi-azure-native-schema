Action for alert rule.
API Version: 2023-02-01.
Previous API Version: 2020-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates or updates an action of alert rule.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var action = new AzureNative.SecurityInsights.Action("action", new()
    {
        ActionId = "912bec42-cb66-4c03-ac63-1761b6898c3e",
        LogicAppResourceId = "/subscriptions/d0cfe6b2-9ac0-4464-9919-dccaee2e48c0/resourceGroups/myRg/providers/Microsoft.Logic/workflows/MyAlerts",
        ResourceGroupName = "myRg",
        RuleId = "73e01a99-5cd7-4139-a149-9f2736ff2ab5",
        TriggerUri = "https://prod-31.northcentralus.logic.azure.com:443/workflows/cd3765391efd48549fd7681ded1d48d7/triggers/manual/paths/invoke?api-version=2016-10-01&sp=%2Ftriggers%2Fmanual%2Frun&sv=1.0&sig=signature",
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
		_, err := securityinsights.NewAction(ctx, "action", &securityinsights.ActionArgs{
			ActionId:           pulumi.String("912bec42-cb66-4c03-ac63-1761b6898c3e"),
			LogicAppResourceId: pulumi.String("/subscriptions/d0cfe6b2-9ac0-4464-9919-dccaee2e48c0/resourceGroups/myRg/providers/Microsoft.Logic/workflows/MyAlerts"),
			ResourceGroupName:  pulumi.String("myRg"),
			RuleId:             pulumi.String("73e01a99-5cd7-4139-a149-9f2736ff2ab5"),
			TriggerUri:         pulumi.String("https://prod-31.northcentralus.logic.azure.com:443/workflows/cd3765391efd48549fd7681ded1d48d7/triggers/manual/paths/invoke?api-version=2016-10-01&sp=%2Ftriggers%2Fmanual%2Frun&sv=1.0&sig=signature"),
			WorkspaceName:      pulumi.String("myWorkspace"),
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
import com.pulumi.azurenative.securityinsights.Action;
import com.pulumi.azurenative.securityinsights.ActionArgs;
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
        var action = new Action("action", ActionArgs.builder()        
            .actionId("912bec42-cb66-4c03-ac63-1761b6898c3e")
            .logicAppResourceId("/subscriptions/d0cfe6b2-9ac0-4464-9919-dccaee2e48c0/resourceGroups/myRg/providers/Microsoft.Logic/workflows/MyAlerts")
            .resourceGroupName("myRg")
            .ruleId("73e01a99-5cd7-4139-a149-9f2736ff2ab5")
            .triggerUri("https://prod-31.northcentralus.logic.azure.com:443/workflows/cd3765391efd48549fd7681ded1d48d7/triggers/manual/paths/invoke?api-version=2016-10-01&sp=%2Ftriggers%2Fmanual%2Frun&sv=1.0&sig=signature")
            .workspaceName("myWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const action = new azure_native.securityinsights.Action("action", {
    actionId: "912bec42-cb66-4c03-ac63-1761b6898c3e",
    logicAppResourceId: "/subscriptions/d0cfe6b2-9ac0-4464-9919-dccaee2e48c0/resourceGroups/myRg/providers/Microsoft.Logic/workflows/MyAlerts",
    resourceGroupName: "myRg",
    ruleId: "73e01a99-5cd7-4139-a149-9f2736ff2ab5",
    triggerUri: "https://prod-31.northcentralus.logic.azure.com:443/workflows/cd3765391efd48549fd7681ded1d48d7/triggers/manual/paths/invoke?api-version=2016-10-01&sp=%2Ftriggers%2Fmanual%2Frun&sv=1.0&sig=signature",
    workspaceName: "myWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

action = azure_native.securityinsights.Action("action",
    action_id="912bec42-cb66-4c03-ac63-1761b6898c3e",
    logic_app_resource_id="/subscriptions/d0cfe6b2-9ac0-4464-9919-dccaee2e48c0/resourceGroups/myRg/providers/Microsoft.Logic/workflows/MyAlerts",
    resource_group_name="myRg",
    rule_id="73e01a99-5cd7-4139-a149-9f2736ff2ab5",
    trigger_uri="https://prod-31.northcentralus.logic.azure.com:443/workflows/cd3765391efd48549fd7681ded1d48d7/triggers/manual/paths/invoke?api-version=2016-10-01&sp=%2Ftriggers%2Fmanual%2Frun&sv=1.0&sig=signature",
    workspace_name="myWorkspace")

```

```yaml
resources:
  action:
    type: azure-native:securityinsights:Action
    properties:
      actionId: 912bec42-cb66-4c03-ac63-1761b6898c3e
      logicAppResourceId: /subscriptions/d0cfe6b2-9ac0-4464-9919-dccaee2e48c0/resourceGroups/myRg/providers/Microsoft.Logic/workflows/MyAlerts
      resourceGroupName: myRg
      ruleId: 73e01a99-5cd7-4139-a149-9f2736ff2ab5
      triggerUri: https://prod-31.northcentralus.logic.azure.com:443/workflows/cd3765391efd48549fd7681ded1d48d7/triggers/manual/paths/invoke?api-version=2016-10-01&sp=%2Ftriggers%2Fmanual%2Frun&sv=1.0&sig=signature
      workspaceName: myWorkspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:securityinsights:Action 912bec42-cb66-4c03-ac63-1761b6898c3e /subscriptions/d0cfe6b2-9ac0-4464-9919-dccaee2e48c0/resourceGroups/myRg/providers/Microsoft.OperationalIinsights/workspaces/myWorkspace/providers/Microsoft.SecurityInsights/alertRules/73e01a99-5cd7-4139-a149-9f2736ff2ab5/actions/912bec42-cb66-4c03-ac63-1761b6898c3e 
```
