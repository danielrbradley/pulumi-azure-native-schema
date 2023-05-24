Definition of the automation account type.
API Version: 2022-08-08.
Previous API Version: 2021-06-22. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update automation account
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var automationAccount = new AzureNative.Automation.AutomationAccount("automationAccount", new()
    {
        AutomationAccountName = "myAutomationAccount9",
        Location = "East US 2",
        Name = "myAutomationAccount9",
        ResourceGroupName = "rg",
        Sku = new AzureNative.Automation.Inputs.SkuArgs
        {
            Name = "Free",
        },
    });

});


```

```go
package main

import (
	automation "github.com/pulumi/pulumi-azure-native-sdk/automation"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := automation.NewAutomationAccount(ctx, "automationAccount", &automation.AutomationAccountArgs{
			AutomationAccountName: pulumi.String("myAutomationAccount9"),
			Location:              pulumi.String("East US 2"),
			Name:                  pulumi.String("myAutomationAccount9"),
			ResourceGroupName:     pulumi.String("rg"),
			Sku: &automation.SkuArgs{
				Name: pulumi.String("Free"),
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
import com.pulumi.azurenative.automation.AutomationAccount;
import com.pulumi.azurenative.automation.AutomationAccountArgs;
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
        var automationAccount = new AutomationAccount("automationAccount", AutomationAccountArgs.builder()        
            .automationAccountName("myAutomationAccount9")
            .location("East US 2")
            .name("myAutomationAccount9")
            .resourceGroupName("rg")
            .sku(Map.of("name", "Free"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const automationAccount = new azure_native.automation.AutomationAccount("automationAccount", {
    automationAccountName: "myAutomationAccount9",
    location: "East US 2",
    name: "myAutomationAccount9",
    resourceGroupName: "rg",
    sku: {
        name: "Free",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

automation_account = azure_native.automation.AutomationAccount("automationAccount",
    automation_account_name="myAutomationAccount9",
    location="East US 2",
    name="myAutomationAccount9",
    resource_group_name="rg",
    sku=azure_native.automation.SkuArgs(
        name="Free",
    ))

```

```yaml
resources:
  automationAccount:
    type: azure-native:automation:AutomationAccount
    properties:
      automationAccountName: myAutomationAccount9
      location: East US 2
      name: myAutomationAccount9
      resourceGroupName: rg
      sku:
        name: Free

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:automation:AutomationAccount ContoseAutomationAccount /subscriptions/subid/resourceGroups/rg/providers/Microsoft.Automation/automationAccounts/myAutomationAccount9 
```
