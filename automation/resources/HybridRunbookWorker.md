Definition of hybrid runbook worker.
API Version: 2022-08-08.
Previous API Version: 2021-06-22. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a V2 hybrid runbook worker
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var hybridRunbookWorker = new AzureNative.Automation.HybridRunbookWorker("hybridRunbookWorker", new()
    {
        AutomationAccountName = "testaccount",
        HybridRunbookWorkerGroupName = "TestHybridGroup",
        HybridRunbookWorkerId = "c010ad12-ef14-4a2a-aa9e-ef22c4745ddd",
        ResourceGroupName = "rg",
        VmResourceId = "/subscriptions/vmsubid/resourceGroups/vmrg/providers/Microsoft.Compute/virtualMachines/vmname",
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
		_, err := automation.NewHybridRunbookWorker(ctx, "hybridRunbookWorker", &automation.HybridRunbookWorkerArgs{
			AutomationAccountName:        pulumi.String("testaccount"),
			HybridRunbookWorkerGroupName: pulumi.String("TestHybridGroup"),
			HybridRunbookWorkerId:        pulumi.String("c010ad12-ef14-4a2a-aa9e-ef22c4745ddd"),
			ResourceGroupName:            pulumi.String("rg"),
			VmResourceId:                 pulumi.String("/subscriptions/vmsubid/resourceGroups/vmrg/providers/Microsoft.Compute/virtualMachines/vmname"),
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
import com.pulumi.azurenative.automation.HybridRunbookWorker;
import com.pulumi.azurenative.automation.HybridRunbookWorkerArgs;
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
        var hybridRunbookWorker = new HybridRunbookWorker("hybridRunbookWorker", HybridRunbookWorkerArgs.builder()        
            .automationAccountName("testaccount")
            .hybridRunbookWorkerGroupName("TestHybridGroup")
            .hybridRunbookWorkerId("c010ad12-ef14-4a2a-aa9e-ef22c4745ddd")
            .resourceGroupName("rg")
            .vmResourceId("/subscriptions/vmsubid/resourceGroups/vmrg/providers/Microsoft.Compute/virtualMachines/vmname")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const hybridRunbookWorker = new azure_native.automation.HybridRunbookWorker("hybridRunbookWorker", {
    automationAccountName: "testaccount",
    hybridRunbookWorkerGroupName: "TestHybridGroup",
    hybridRunbookWorkerId: "c010ad12-ef14-4a2a-aa9e-ef22c4745ddd",
    resourceGroupName: "rg",
    vmResourceId: "/subscriptions/vmsubid/resourceGroups/vmrg/providers/Microsoft.Compute/virtualMachines/vmname",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

hybrid_runbook_worker = azure_native.automation.HybridRunbookWorker("hybridRunbookWorker",
    automation_account_name="testaccount",
    hybrid_runbook_worker_group_name="TestHybridGroup",
    hybrid_runbook_worker_id="c010ad12-ef14-4a2a-aa9e-ef22c4745ddd",
    resource_group_name="rg",
    vm_resource_id="/subscriptions/vmsubid/resourceGroups/vmrg/providers/Microsoft.Compute/virtualMachines/vmname")

```

```yaml
resources:
  hybridRunbookWorker:
    type: azure-native:automation:HybridRunbookWorker
    properties:
      automationAccountName: testaccount
      hybridRunbookWorkerGroupName: TestHybridGroup
      hybridRunbookWorkerId: c010ad12-ef14-4a2a-aa9e-ef22c4745ddd
      resourceGroupName: rg
      vmResourceId: /subscriptions/vmsubid/resourceGroups/vmrg/providers/Microsoft.Compute/virtualMachines/vmname

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:automation:HybridRunbookWorker c010ad12-ef14-4a2a-aa9e-ef22c4745ddd /subscriptions/subid/resourceGroups/rg/providers/Microsoft.Automation/automationAccounts/testaccount/hybridRunbookWorkerGroups/TestHybridGroup/hybridRunbookWorkers/c010ad12-ef14-4a2a-aa9e-ef22c4745ddd 
```
