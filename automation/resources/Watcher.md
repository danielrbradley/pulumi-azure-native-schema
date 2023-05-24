Definition of the watcher type.
API Version: 2019-06-01.
Previous API Version: 2019-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update watcher
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var watcher = new AzureNative.Automation.Watcher("watcher", new()
    {
        AutomationAccountName = "MyTestAutomationAccount",
        Description = "This is a test watcher.",
        ExecutionFrequencyInSeconds = 60,
        ResourceGroupName = "rg",
        ScriptName = "MyTestWatcherRunbook",
        ScriptRunOn = "MyTestHybridWorkerGroup",
        Tags = null,
        WatcherName = "MyTestWatcher",
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
		_, err := automation.NewWatcher(ctx, "watcher", &automation.WatcherArgs{
			AutomationAccountName:       pulumi.String("MyTestAutomationAccount"),
			Description:                 pulumi.String("This is a test watcher."),
			ExecutionFrequencyInSeconds: pulumi.Float64(60),
			ResourceGroupName:           pulumi.String("rg"),
			ScriptName:                  pulumi.String("MyTestWatcherRunbook"),
			ScriptRunOn:                 pulumi.String("MyTestHybridWorkerGroup"),
			Tags:                        nil,
			WatcherName:                 pulumi.String("MyTestWatcher"),
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
import com.pulumi.azurenative.automation.Watcher;
import com.pulumi.azurenative.automation.WatcherArgs;
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
        var watcher = new Watcher("watcher", WatcherArgs.builder()        
            .automationAccountName("MyTestAutomationAccount")
            .description("This is a test watcher.")
            .executionFrequencyInSeconds(60)
            .resourceGroupName("rg")
            .scriptName("MyTestWatcherRunbook")
            .scriptRunOn("MyTestHybridWorkerGroup")
            .tags()
            .watcherName("MyTestWatcher")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const watcher = new azure_native.automation.Watcher("watcher", {
    automationAccountName: "MyTestAutomationAccount",
    description: "This is a test watcher.",
    executionFrequencyInSeconds: 60,
    resourceGroupName: "rg",
    scriptName: "MyTestWatcherRunbook",
    scriptRunOn: "MyTestHybridWorkerGroup",
    tags: {},
    watcherName: "MyTestWatcher",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

watcher = azure_native.automation.Watcher("watcher",
    automation_account_name="MyTestAutomationAccount",
    description="This is a test watcher.",
    execution_frequency_in_seconds=60,
    resource_group_name="rg",
    script_name="MyTestWatcherRunbook",
    script_run_on="MyTestHybridWorkerGroup",
    tags={},
    watcher_name="MyTestWatcher")

```

```yaml
resources:
  watcher:
    type: azure-native:automation:Watcher
    properties:
      automationAccountName: MyTestAutomationAccount
      description: This is a test watcher.
      executionFrequencyInSeconds: 60
      resourceGroupName: rg
      scriptName: MyTestWatcherRunbook
      scriptRunOn: MyTestHybridWorkerGroup
      tags: {}
      watcherName: MyTestWatcher

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:automation:Watcher MyTestWatcher /subscriptions/subId/resourceGroups/rg/providers/Microsoft.Automation/automationAccounts/MyTestAutomationAccount/watchers/MyTestWatcher 
```
