
API Version: 2023-02-01.
Previous API Version: 2019-01-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### AutomationRules_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var automationRule = new AzureNative.SecurityInsights.AutomationRule("automationRule", new()
    {
        AutomationRuleId = "73e01a99-5cd7-4139-a149-9f2736ff2ab5",
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
		_, err := securityinsights.NewAutomationRule(ctx, "automationRule", &securityinsights.AutomationRuleArgs{
			AutomationRuleId:  pulumi.String("73e01a99-5cd7-4139-a149-9f2736ff2ab5"),
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
import com.pulumi.azurenative.securityinsights.AutomationRule;
import com.pulumi.azurenative.securityinsights.AutomationRuleArgs;
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
        var automationRule = new AutomationRule("automationRule", AutomationRuleArgs.builder()        
            .automationRuleId("73e01a99-5cd7-4139-a149-9f2736ff2ab5")
            .resourceGroupName("myRg")
            .workspaceName("myWorkspace")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const automationRule = new azure_native.securityinsights.AutomationRule("automationRule", {
    automationRuleId: "73e01a99-5cd7-4139-a149-9f2736ff2ab5",
    resourceGroupName: "myRg",
    workspaceName: "myWorkspace",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

automation_rule = azure_native.securityinsights.AutomationRule("automationRule",
    automation_rule_id="73e01a99-5cd7-4139-a149-9f2736ff2ab5",
    resource_group_name="myRg",
    workspace_name="myWorkspace")

```

```yaml
resources:
  automationRule:
    type: azure-native:securityinsights:AutomationRule
    properties:
      automationRuleId: 73e01a99-5cd7-4139-a149-9f2736ff2ab5
      resourceGroupName: myRg
      workspaceName: myWorkspace

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:securityinsights:AutomationRule 73e01a99-5cd7-4139-a149-9f2736ff2ab5 /subscriptions/d0cfe6b2-9ac0-4464-9919-dccaee2e48c0/resourceGroups/myRg/providers/Microsoft.OperationalInsights/workspaces/myWorkspace/providers/Microsoft.SecurityInsights/automationRules/73e01a99-5cd7-4139-a149-9f2736ff2ab5 
```
