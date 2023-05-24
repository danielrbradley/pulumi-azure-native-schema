Definition of hybrid runbook worker group.
API Version: 2022-08-08.
Previous API Version: 2021-06-22. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a hybrid worker group
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var hybridRunbookWorkerGroup = new AzureNative.Automation.HybridRunbookWorkerGroup("hybridRunbookWorkerGroup", new()
    {
        AutomationAccountName = "testaccount",
        Credential = new AzureNative.Automation.Inputs.RunAsCredentialAssociationPropertyArgs
        {
            Name = "myRunAsCredentialName",
        },
        HybridRunbookWorkerGroupName = "TestHybridGroup",
        ResourceGroupName = "rg",
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
		_, err := automation.NewHybridRunbookWorkerGroup(ctx, "hybridRunbookWorkerGroup", &automation.HybridRunbookWorkerGroupArgs{
			AutomationAccountName: pulumi.String("testaccount"),
			Credential: &automation.RunAsCredentialAssociationPropertyArgs{
				Name: pulumi.String("myRunAsCredentialName"),
			},
			HybridRunbookWorkerGroupName: pulumi.String("TestHybridGroup"),
			ResourceGroupName:            pulumi.String("rg"),
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
import com.pulumi.azurenative.automation.HybridRunbookWorkerGroup;
import com.pulumi.azurenative.automation.HybridRunbookWorkerGroupArgs;
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
        var hybridRunbookWorkerGroup = new HybridRunbookWorkerGroup("hybridRunbookWorkerGroup", HybridRunbookWorkerGroupArgs.builder()        
            .automationAccountName("testaccount")
            .credential(Map.of("name", "myRunAsCredentialName"))
            .hybridRunbookWorkerGroupName("TestHybridGroup")
            .resourceGroupName("rg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const hybridRunbookWorkerGroup = new azure_native.automation.HybridRunbookWorkerGroup("hybridRunbookWorkerGroup", {
    automationAccountName: "testaccount",
    credential: {
        name: "myRunAsCredentialName",
    },
    hybridRunbookWorkerGroupName: "TestHybridGroup",
    resourceGroupName: "rg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

hybrid_runbook_worker_group = azure_native.automation.HybridRunbookWorkerGroup("hybridRunbookWorkerGroup",
    automation_account_name="testaccount",
    credential=azure_native.automation.RunAsCredentialAssociationPropertyArgs(
        name="myRunAsCredentialName",
    ),
    hybrid_runbook_worker_group_name="TestHybridGroup",
    resource_group_name="rg")

```

```yaml
resources:
  hybridRunbookWorkerGroup:
    type: azure-native:automation:HybridRunbookWorkerGroup
    properties:
      automationAccountName: testaccount
      credential:
        name: myRunAsCredentialName
      hybridRunbookWorkerGroupName: TestHybridGroup
      resourceGroupName: rg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:automation:HybridRunbookWorkerGroup TestHybridGroup /subscriptions/subid/resourceGroups/rg/providers/Microsoft.Automation/automationAccounts/testaccount/hybridRunbookWorkerGroups/TestHybridGroup 
```
