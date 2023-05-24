Base class for backup items.
API Version: 2023-02-01.
Previous API Version: 2021-02-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Enable Protection on Azure IaasVm
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var protectedItem = new AzureNative.RecoveryServices.ProtectedItem("protectedItem", new()
    {
        ContainerName = "IaasVMContainer;iaasvmcontainerv2;netsdktestrg;netvmtestv2vm1",
        FabricName = "Azure",
        Properties = new AzureNative.RecoveryServices.Inputs.AzureIaaSComputeVMProtectedItemArgs
        {
            PolicyId = "/Subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/SwaggerTestRg/providers/Microsoft.RecoveryServices/vaults/NetSDKTestRsVault/backupPolicies/DefaultPolicy",
            ProtectedItemType = "Microsoft.Compute/virtualMachines",
            SourceResourceId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/netsdktestrg/providers/Microsoft.Compute/virtualMachines/netvmtestv2vm1",
        },
        ProtectedItemName = "VM;iaasvmcontainerv2;netsdktestrg;netvmtestv2vm1",
        ResourceGroupName = "SwaggerTestRg",
        VaultName = "NetSDKTestRsVault",
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
		_, err := recoveryservices.NewProtectedItem(ctx, "protectedItem", &recoveryservices.ProtectedItemArgs{
			ContainerName: pulumi.String("IaasVMContainer;iaasvmcontainerv2;netsdktestrg;netvmtestv2vm1"),
			FabricName:    pulumi.String("Azure"),
			Properties: recoveryservices.AzureIaaSComputeVMProtectedItem{
				PolicyId:          "/Subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/SwaggerTestRg/providers/Microsoft.RecoveryServices/vaults/NetSDKTestRsVault/backupPolicies/DefaultPolicy",
				ProtectedItemType: "Microsoft.Compute/virtualMachines",
				SourceResourceId:  "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/netsdktestrg/providers/Microsoft.Compute/virtualMachines/netvmtestv2vm1",
			},
			ProtectedItemName: pulumi.String("VM;iaasvmcontainerv2;netsdktestrg;netvmtestv2vm1"),
			ResourceGroupName: pulumi.String("SwaggerTestRg"),
			VaultName:         pulumi.String("NetSDKTestRsVault"),
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
import com.pulumi.azurenative.recoveryservices.ProtectedItem;
import com.pulumi.azurenative.recoveryservices.ProtectedItemArgs;
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
        var protectedItem = new ProtectedItem("protectedItem", ProtectedItemArgs.builder()        
            .containerName("IaasVMContainer;iaasvmcontainerv2;netsdktestrg;netvmtestv2vm1")
            .fabricName("Azure")
            .properties(Map.ofEntries(
                Map.entry("policyId", "/Subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/SwaggerTestRg/providers/Microsoft.RecoveryServices/vaults/NetSDKTestRsVault/backupPolicies/DefaultPolicy"),
                Map.entry("protectedItemType", "Microsoft.Compute/virtualMachines"),
                Map.entry("sourceResourceId", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/netsdktestrg/providers/Microsoft.Compute/virtualMachines/netvmtestv2vm1")
            ))
            .protectedItemName("VM;iaasvmcontainerv2;netsdktestrg;netvmtestv2vm1")
            .resourceGroupName("SwaggerTestRg")
            .vaultName("NetSDKTestRsVault")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const protectedItem = new azure_native.recoveryservices.ProtectedItem("protectedItem", {
    containerName: "IaasVMContainer;iaasvmcontainerv2;netsdktestrg;netvmtestv2vm1",
    fabricName: "Azure",
    properties: {
        policyId: "/Subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/SwaggerTestRg/providers/Microsoft.RecoveryServices/vaults/NetSDKTestRsVault/backupPolicies/DefaultPolicy",
        protectedItemType: "Microsoft.Compute/virtualMachines",
        sourceResourceId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/netsdktestrg/providers/Microsoft.Compute/virtualMachines/netvmtestv2vm1",
    },
    protectedItemName: "VM;iaasvmcontainerv2;netsdktestrg;netvmtestv2vm1",
    resourceGroupName: "SwaggerTestRg",
    vaultName: "NetSDKTestRsVault",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

protected_item = azure_native.recoveryservices.ProtectedItem("protectedItem",
    container_name="IaasVMContainer;iaasvmcontainerv2;netsdktestrg;netvmtestv2vm1",
    fabric_name="Azure",
    properties=azure_native.recoveryservices.AzureIaaSComputeVMProtectedItemArgs(
        policy_id="/Subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/SwaggerTestRg/providers/Microsoft.RecoveryServices/vaults/NetSDKTestRsVault/backupPolicies/DefaultPolicy",
        protected_item_type="Microsoft.Compute/virtualMachines",
        source_resource_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/netsdktestrg/providers/Microsoft.Compute/virtualMachines/netvmtestv2vm1",
    ),
    protected_item_name="VM;iaasvmcontainerv2;netsdktestrg;netvmtestv2vm1",
    resource_group_name="SwaggerTestRg",
    vault_name="NetSDKTestRsVault")

```

```yaml
resources:
  protectedItem:
    type: azure-native:recoveryservices:ProtectedItem
    properties:
      containerName: IaasVMContainer;iaasvmcontainerv2;netsdktestrg;netvmtestv2vm1
      fabricName: Azure
      properties:
        policyId: /Subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/SwaggerTestRg/providers/Microsoft.RecoveryServices/vaults/NetSDKTestRsVault/backupPolicies/DefaultPolicy
        protectedItemType: Microsoft.Compute/virtualMachines
        sourceResourceId: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/netsdktestrg/providers/Microsoft.Compute/virtualMachines/netvmtestv2vm1
      protectedItemName: VM;iaasvmcontainerv2;netsdktestrg;netvmtestv2vm1
      resourceGroupName: SwaggerTestRg
      vaultName: NetSDKTestRsVault

```

{{% /example %}}
{{% example %}}
### Stop Protection with retain data on Azure IaasVm
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var protectedItem = new AzureNative.RecoveryServices.ProtectedItem("protectedItem", new()
    {
        ContainerName = "IaasVMContainer;iaasvmcontainerv2;netsdktestrg;netvmtestv2vm1",
        FabricName = "Azure",
        Properties = new AzureNative.RecoveryServices.Inputs.AzureIaaSComputeVMProtectedItemArgs
        {
            ProtectedItemType = "Microsoft.Compute/virtualMachines",
            ProtectionState = "ProtectionStopped",
            SourceResourceId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/netsdktestrg/providers/Microsoft.Compute/virtualMachines/netvmtestv2vm1",
        },
        ProtectedItemName = "VM;iaasvmcontainerv2;netsdktestrg;netvmtestv2vm1",
        ResourceGroupName = "SwaggerTestRg",
        VaultName = "NetSDKTestRsVault",
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
		_, err := recoveryservices.NewProtectedItem(ctx, "protectedItem", &recoveryservices.ProtectedItemArgs{
			ContainerName: pulumi.String("IaasVMContainer;iaasvmcontainerv2;netsdktestrg;netvmtestv2vm1"),
			FabricName:    pulumi.String("Azure"),
			Properties: recoveryservices.AzureIaaSComputeVMProtectedItem{
				ProtectedItemType: "Microsoft.Compute/virtualMachines",
				ProtectionState:   "ProtectionStopped",
				SourceResourceId:  "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/netsdktestrg/providers/Microsoft.Compute/virtualMachines/netvmtestv2vm1",
			},
			ProtectedItemName: pulumi.String("VM;iaasvmcontainerv2;netsdktestrg;netvmtestv2vm1"),
			ResourceGroupName: pulumi.String("SwaggerTestRg"),
			VaultName:         pulumi.String("NetSDKTestRsVault"),
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
import com.pulumi.azurenative.recoveryservices.ProtectedItem;
import com.pulumi.azurenative.recoveryservices.ProtectedItemArgs;
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
        var protectedItem = new ProtectedItem("protectedItem", ProtectedItemArgs.builder()        
            .containerName("IaasVMContainer;iaasvmcontainerv2;netsdktestrg;netvmtestv2vm1")
            .fabricName("Azure")
            .properties(Map.ofEntries(
                Map.entry("protectedItemType", "Microsoft.Compute/virtualMachines"),
                Map.entry("protectionState", "ProtectionStopped"),
                Map.entry("sourceResourceId", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/netsdktestrg/providers/Microsoft.Compute/virtualMachines/netvmtestv2vm1")
            ))
            .protectedItemName("VM;iaasvmcontainerv2;netsdktestrg;netvmtestv2vm1")
            .resourceGroupName("SwaggerTestRg")
            .vaultName("NetSDKTestRsVault")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const protectedItem = new azure_native.recoveryservices.ProtectedItem("protectedItem", {
    containerName: "IaasVMContainer;iaasvmcontainerv2;netsdktestrg;netvmtestv2vm1",
    fabricName: "Azure",
    properties: {
        protectedItemType: "Microsoft.Compute/virtualMachines",
        protectionState: "ProtectionStopped",
        sourceResourceId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/netsdktestrg/providers/Microsoft.Compute/virtualMachines/netvmtestv2vm1",
    },
    protectedItemName: "VM;iaasvmcontainerv2;netsdktestrg;netvmtestv2vm1",
    resourceGroupName: "SwaggerTestRg",
    vaultName: "NetSDKTestRsVault",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

protected_item = azure_native.recoveryservices.ProtectedItem("protectedItem",
    container_name="IaasVMContainer;iaasvmcontainerv2;netsdktestrg;netvmtestv2vm1",
    fabric_name="Azure",
    properties=azure_native.recoveryservices.AzureIaaSComputeVMProtectedItemArgs(
        protected_item_type="Microsoft.Compute/virtualMachines",
        protection_state="ProtectionStopped",
        source_resource_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/netsdktestrg/providers/Microsoft.Compute/virtualMachines/netvmtestv2vm1",
    ),
    protected_item_name="VM;iaasvmcontainerv2;netsdktestrg;netvmtestv2vm1",
    resource_group_name="SwaggerTestRg",
    vault_name="NetSDKTestRsVault")

```

```yaml
resources:
  protectedItem:
    type: azure-native:recoveryservices:ProtectedItem
    properties:
      containerName: IaasVMContainer;iaasvmcontainerv2;netsdktestrg;netvmtestv2vm1
      fabricName: Azure
      properties:
        protectedItemType: Microsoft.Compute/virtualMachines
        protectionState: ProtectionStopped
        sourceResourceId: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/netsdktestrg/providers/Microsoft.Compute/virtualMachines/netvmtestv2vm1
      protectedItemName: VM;iaasvmcontainerv2;netsdktestrg;netvmtestv2vm1
      resourceGroupName: SwaggerTestRg
      vaultName: NetSDKTestRsVault

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:recoveryservices:ProtectedItem VM;iaasvmcontainerv2;netsdktestrg;netvmtestv2vm1 /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/PythonSDKBackupTestRg/providers/Microsoft.RecoveryServices/vaults/PySDKBackupTestRsVault/backupFabrics/Azure/protectionContainers/IaasVMContainer;iaasvmcontainerv2;netsdktestrg;netvmtestv2vm1/protectedItems/VM;iaasvmcontainerv2;netsdktestrg;netvmtestv2vm1 
```
