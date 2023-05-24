disk encryption set resource.
API Version: 2022-07-02.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a disk encryption set with key vault from a different subscription.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var diskEncryptionSet = new AzureNative.Compute.DiskEncryptionSet("diskEncryptionSet", new()
    {
        ActiveKey = new AzureNative.Compute.Inputs.KeyForDiskEncryptionSetArgs
        {
            KeyUrl = "https://myvaultdifferentsub.vault-int.azure-int.net/keys/{key}",
        },
        DiskEncryptionSetName = "myDiskEncryptionSet",
        EncryptionType = "EncryptionAtRestWithCustomerKey",
        Identity = new AzureNative.Compute.Inputs.EncryptionSetIdentityArgs
        {
            Type = "SystemAssigned",
        },
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
    });

});


```

```go
package main

import (
	compute "github.com/pulumi/pulumi-azure-native-sdk/compute"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := compute.NewDiskEncryptionSet(ctx, "diskEncryptionSet", &compute.DiskEncryptionSetArgs{
			ActiveKey: &compute.KeyForDiskEncryptionSetArgs{
				KeyUrl: pulumi.String("https://myvaultdifferentsub.vault-int.azure-int.net/keys/{key}"),
			},
			DiskEncryptionSetName: pulumi.String("myDiskEncryptionSet"),
			EncryptionType:        pulumi.String("EncryptionAtRestWithCustomerKey"),
			Identity: &compute.EncryptionSetIdentityArgs{
				Type: pulumi.String("SystemAssigned"),
			},
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.compute.DiskEncryptionSet;
import com.pulumi.azurenative.compute.DiskEncryptionSetArgs;
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
        var diskEncryptionSet = new DiskEncryptionSet("diskEncryptionSet", DiskEncryptionSetArgs.builder()        
            .activeKey(Map.of("keyUrl", "https://myvaultdifferentsub.vault-int.azure-int.net/keys/{key}"))
            .diskEncryptionSetName("myDiskEncryptionSet")
            .encryptionType("EncryptionAtRestWithCustomerKey")
            .identity(Map.of("type", "SystemAssigned"))
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const diskEncryptionSet = new azure_native.compute.DiskEncryptionSet("diskEncryptionSet", {
    activeKey: {
        keyUrl: "https://myvaultdifferentsub.vault-int.azure-int.net/keys/{key}",
    },
    diskEncryptionSetName: "myDiskEncryptionSet",
    encryptionType: "EncryptionAtRestWithCustomerKey",
    identity: {
        type: "SystemAssigned",
    },
    location: "West US",
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

disk_encryption_set = azure_native.compute.DiskEncryptionSet("diskEncryptionSet",
    active_key=azure_native.compute.KeyForDiskEncryptionSetArgs(
        key_url="https://myvaultdifferentsub.vault-int.azure-int.net/keys/{key}",
    ),
    disk_encryption_set_name="myDiskEncryptionSet",
    encryption_type="EncryptionAtRestWithCustomerKey",
    identity=azure_native.compute.EncryptionSetIdentityArgs(
        type="SystemAssigned",
    ),
    location="West US",
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  diskEncryptionSet:
    type: azure-native:compute:DiskEncryptionSet
    properties:
      activeKey:
        keyUrl: https://myvaultdifferentsub.vault-int.azure-int.net/keys/{key}
      diskEncryptionSetName: myDiskEncryptionSet
      encryptionType: EncryptionAtRestWithCustomerKey
      identity:
        type: SystemAssigned
      location: West US
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% example %}}
### Create a disk encryption set.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var diskEncryptionSet = new AzureNative.Compute.DiskEncryptionSet("diskEncryptionSet", new()
    {
        ActiveKey = new AzureNative.Compute.Inputs.KeyForDiskEncryptionSetArgs
        {
            KeyUrl = "https://myvmvault.vault-int.azure-int.net/keys/{key}",
            SourceVault = new AzureNative.Compute.Inputs.SourceVaultArgs
            {
                Id = "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.KeyVault/vaults/myVMVault",
            },
        },
        DiskEncryptionSetName = "myDiskEncryptionSet",
        EncryptionType = "EncryptionAtRestWithCustomerKey",
        Identity = new AzureNative.Compute.Inputs.EncryptionSetIdentityArgs
        {
            Type = "SystemAssigned",
        },
        Location = "West US",
        ResourceGroupName = "myResourceGroup",
    });

});


```

```go
package main

import (
	compute "github.com/pulumi/pulumi-azure-native-sdk/compute"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := compute.NewDiskEncryptionSet(ctx, "diskEncryptionSet", &compute.DiskEncryptionSetArgs{
			ActiveKey: compute.KeyForDiskEncryptionSetResponse{
				KeyUrl: pulumi.String("https://myvmvault.vault-int.azure-int.net/keys/{key}"),
				SourceVault: &compute.SourceVaultArgs{
					Id: pulumi.String("/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.KeyVault/vaults/myVMVault"),
				},
			},
			DiskEncryptionSetName: pulumi.String("myDiskEncryptionSet"),
			EncryptionType:        pulumi.String("EncryptionAtRestWithCustomerKey"),
			Identity: &compute.EncryptionSetIdentityArgs{
				Type: pulumi.String("SystemAssigned"),
			},
			Location:          pulumi.String("West US"),
			ResourceGroupName: pulumi.String("myResourceGroup"),
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
import com.pulumi.azurenative.compute.DiskEncryptionSet;
import com.pulumi.azurenative.compute.DiskEncryptionSetArgs;
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
        var diskEncryptionSet = new DiskEncryptionSet("diskEncryptionSet", DiskEncryptionSetArgs.builder()        
            .activeKey(Map.ofEntries(
                Map.entry("keyUrl", "https://myvmvault.vault-int.azure-int.net/keys/{key}"),
                Map.entry("sourceVault", Map.of("id", "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.KeyVault/vaults/myVMVault"))
            ))
            .diskEncryptionSetName("myDiskEncryptionSet")
            .encryptionType("EncryptionAtRestWithCustomerKey")
            .identity(Map.of("type", "SystemAssigned"))
            .location("West US")
            .resourceGroupName("myResourceGroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const diskEncryptionSet = new azure_native.compute.DiskEncryptionSet("diskEncryptionSet", {
    activeKey: {
        keyUrl: "https://myvmvault.vault-int.azure-int.net/keys/{key}",
        sourceVault: {
            id: "/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.KeyVault/vaults/myVMVault",
        },
    },
    diskEncryptionSetName: "myDiskEncryptionSet",
    encryptionType: "EncryptionAtRestWithCustomerKey",
    identity: {
        type: "SystemAssigned",
    },
    location: "West US",
    resourceGroupName: "myResourceGroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

disk_encryption_set = azure_native.compute.DiskEncryptionSet("diskEncryptionSet",
    active_key=azure_native.compute.KeyForDiskEncryptionSetResponseArgs(
        key_url="https://myvmvault.vault-int.azure-int.net/keys/{key}",
        source_vault=azure_native.compute.SourceVaultArgs(
            id="/subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.KeyVault/vaults/myVMVault",
        ),
    ),
    disk_encryption_set_name="myDiskEncryptionSet",
    encryption_type="EncryptionAtRestWithCustomerKey",
    identity=azure_native.compute.EncryptionSetIdentityArgs(
        type="SystemAssigned",
    ),
    location="West US",
    resource_group_name="myResourceGroup")

```

```yaml
resources:
  diskEncryptionSet:
    type: azure-native:compute:DiskEncryptionSet
    properties:
      activeKey:
        keyUrl: https://myvmvault.vault-int.azure-int.net/keys/{key}
        sourceVault:
          id: /subscriptions/{subscriptionId}/resourceGroups/myResourceGroup/providers/Microsoft.KeyVault/vaults/myVMVault
      diskEncryptionSetName: myDiskEncryptionSet
      encryptionType: EncryptionAtRestWithCustomerKey
      identity:
        type: SystemAssigned
      location: West US
      resourceGroupName: myResourceGroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:compute:DiskEncryptionSet myDiskEncryptionSet /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/diskEncryptionSets/{diskEncryptionSetName} 
```
