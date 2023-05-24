Base class for backup ProtectionIntent.
API Version: 2023-02-01.
Previous API Version: 2021-02-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or Update Azure Vm Protection Intent
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var protectionIntent = new AzureNative.RecoveryServices.ProtectionIntent("protectionIntent", new()
    {
        FabricName = "Azure",
        IntentObjectName = "vm;iaasvmcontainerv2;chamsrgtest;chamscandel",
        Properties = new AzureNative.RecoveryServices.Inputs.AzureResourceProtectionIntentArgs
        {
            PolicyId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myRG/providers/Microsoft.RecoveryServices/vaults/myVault/backupPolicies/myPolicy",
            ProtectionIntentItemType = "AzureResourceItem",
            SourceResourceId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/chamsrgtest/providers/Microsoft.Compute/virtualMachines/chamscandel",
        },
        ResourceGroupName = "myRG",
        VaultName = "myVault",
    });

});


```

```go
package main

import (
	recoveryservices "github.com/pulumi/pulumi-azure-native-sdk/recoveryservices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := recoveryservices.NewProtectionIntent(ctx, "protectionIntent", &recoveryservices.ProtectionIntentArgs{
			FabricName:       pulumi.String("Azure"),
			IntentObjectName: pulumi.String("vm;iaasvmcontainerv2;chamsrgtest;chamscandel"),
			Properties: recoveryservices.AzureResourceProtectionIntent{
				PolicyId:                 "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myRG/providers/Microsoft.RecoveryServices/vaults/myVault/backupPolicies/myPolicy",
				ProtectionIntentItemType: "AzureResourceItem",
				SourceResourceId:         "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/chamsrgtest/providers/Microsoft.Compute/virtualMachines/chamscandel",
			},
			ResourceGroupName: pulumi.String("myRG"),
			VaultName:         pulumi.String("myVault"),
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
import com.pulumi.azurenative.recoveryservices.ProtectionIntent;
import com.pulumi.azurenative.recoveryservices.ProtectionIntentArgs;
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
        var protectionIntent = new ProtectionIntent("protectionIntent", ProtectionIntentArgs.builder()        
            .fabricName("Azure")
            .intentObjectName("vm;iaasvmcontainerv2;chamsrgtest;chamscandel")
            .properties(Map.ofEntries(
                Map.entry("policyId", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myRG/providers/Microsoft.RecoveryServices/vaults/myVault/backupPolicies/myPolicy"),
                Map.entry("protectionIntentItemType", "AzureResourceItem"),
                Map.entry("sourceResourceId", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/chamsrgtest/providers/Microsoft.Compute/virtualMachines/chamscandel")
            ))
            .resourceGroupName("myRG")
            .vaultName("myVault")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const protectionIntent = new azure_native.recoveryservices.ProtectionIntent("protectionIntent", {
    fabricName: "Azure",
    intentObjectName: "vm;iaasvmcontainerv2;chamsrgtest;chamscandel",
    properties: {
        policyId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myRG/providers/Microsoft.RecoveryServices/vaults/myVault/backupPolicies/myPolicy",
        protectionIntentItemType: "AzureResourceItem",
        sourceResourceId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/chamsrgtest/providers/Microsoft.Compute/virtualMachines/chamscandel",
    },
    resourceGroupName: "myRG",
    vaultName: "myVault",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

protection_intent = azure_native.recoveryservices.ProtectionIntent("protectionIntent",
    fabric_name="Azure",
    intent_object_name="vm;iaasvmcontainerv2;chamsrgtest;chamscandel",
    properties=azure_native.recoveryservices.AzureResourceProtectionIntentArgs(
        policy_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myRG/providers/Microsoft.RecoveryServices/vaults/myVault/backupPolicies/myPolicy",
        protection_intent_item_type="AzureResourceItem",
        source_resource_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/chamsrgtest/providers/Microsoft.Compute/virtualMachines/chamscandel",
    ),
    resource_group_name="myRG",
    vault_name="myVault")

```

```yaml
resources:
  protectionIntent:
    type: azure-native:recoveryservices:ProtectionIntent
    properties:
      fabricName: Azure
      intentObjectName: vm;iaasvmcontainerv2;chamsrgtest;chamscandel
      properties:
        policyId: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myRG/providers/Microsoft.RecoveryServices/vaults/myVault/backupPolicies/myPolicy
        protectionIntentItemType: AzureResourceItem
        sourceResourceId: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/chamsrgtest/providers/Microsoft.Compute/virtualMachines/chamscandel
      resourceGroupName: myRG
      vaultName: myVault

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:recoveryservices:ProtectionIntent vm;iaasvmcontainerv2;chamsrgtest;chamscandel /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/myRG/providers/Microsoft.RecoveryServices/vaults/myVault/backupFabrics/Azure/backupProtectionIntent/vm;iaasvmcontainerv2;chamsrgtest;chamscandel 
```
