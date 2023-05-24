Describes a Virtual Machine Scale Set Extension.
API Version: 2022-11-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### VirtualMachineScaleSetExtension_CreateOrUpdate_MaximumSet_Gen
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSetExtension = new AzureNative.Compute.VirtualMachineScaleSetExtension("virtualMachineScaleSetExtension", new()
    {
        AutoUpgradeMinorVersion = true,
        EnableAutomaticUpgrade = true,
        ForceUpdateTag = "aaaaaaaaa",
        Name = "{extension-name}",
        ProtectedSettings = null,
        ProvisionAfterExtensions = new[]
        {
            "aa",
        },
        Publisher = "{extension-Publisher}",
        ResourceGroupName = "rgcompute",
        Settings = null,
        SuppressFailures = true,
        Type = "{extension-Type}",
        TypeHandlerVersion = "{handler-version}",
        VmScaleSetName = "aaaaaaa",
        VmssExtensionName = "aaaaaaaaaaaaaaaaaaaaa",
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
		_, err := compute.NewVirtualMachineScaleSetExtension(ctx, "virtualMachineScaleSetExtension", &compute.VirtualMachineScaleSetExtensionArgs{
			AutoUpgradeMinorVersion: pulumi.Bool(true),
			EnableAutomaticUpgrade:  pulumi.Bool(true),
			ForceUpdateTag:          pulumi.String("aaaaaaaaa"),
			Name:                    pulumi.String("{extension-name}"),
			ProtectedSettings:       nil,
			ProvisionAfterExtensions: pulumi.StringArray{
				pulumi.String("aa"),
			},
			Publisher:          pulumi.String("{extension-Publisher}"),
			ResourceGroupName:  pulumi.String("rgcompute"),
			Settings:           nil,
			SuppressFailures:   pulumi.Bool(true),
			Type:               pulumi.String("{extension-Type}"),
			TypeHandlerVersion: pulumi.String("{handler-version}"),
			VmScaleSetName:     pulumi.String("aaaaaaa"),
			VmssExtensionName:  pulumi.String("aaaaaaaaaaaaaaaaaaaaa"),
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
import com.pulumi.azurenative.compute.VirtualMachineScaleSetExtension;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetExtensionArgs;
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
        var virtualMachineScaleSetExtension = new VirtualMachineScaleSetExtension("virtualMachineScaleSetExtension", VirtualMachineScaleSetExtensionArgs.builder()        
            .autoUpgradeMinorVersion(true)
            .enableAutomaticUpgrade(true)
            .forceUpdateTag("aaaaaaaaa")
            .name("{extension-name}")
            .protectedSettings()
            .provisionAfterExtensions("aa")
            .publisher("{extension-Publisher}")
            .resourceGroupName("rgcompute")
            .settings()
            .suppressFailures(true)
            .type("{extension-Type}")
            .typeHandlerVersion("{handler-version}")
            .vmScaleSetName("aaaaaaa")
            .vmssExtensionName("aaaaaaaaaaaaaaaaaaaaa")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSetExtension = new azure_native.compute.VirtualMachineScaleSetExtension("virtualMachineScaleSetExtension", {
    autoUpgradeMinorVersion: true,
    enableAutomaticUpgrade: true,
    forceUpdateTag: "aaaaaaaaa",
    name: "{extension-name}",
    protectedSettings: {},
    provisionAfterExtensions: ["aa"],
    publisher: "{extension-Publisher}",
    resourceGroupName: "rgcompute",
    settings: {},
    suppressFailures: true,
    type: "{extension-Type}",
    typeHandlerVersion: "{handler-version}",
    vmScaleSetName: "aaaaaaa",
    vmssExtensionName: "aaaaaaaaaaaaaaaaaaaaa",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set_extension = azure_native.compute.VirtualMachineScaleSetExtension("virtualMachineScaleSetExtension",
    auto_upgrade_minor_version=True,
    enable_automatic_upgrade=True,
    force_update_tag="aaaaaaaaa",
    name="{extension-name}",
    protected_settings={},
    provision_after_extensions=["aa"],
    publisher="{extension-Publisher}",
    resource_group_name="rgcompute",
    settings={},
    suppress_failures=True,
    type="{extension-Type}",
    type_handler_version="{handler-version}",
    vm_scale_set_name="aaaaaaa",
    vmss_extension_name="aaaaaaaaaaaaaaaaaaaaa")

```

```yaml
resources:
  virtualMachineScaleSetExtension:
    type: azure-native:compute:VirtualMachineScaleSetExtension
    properties:
      autoUpgradeMinorVersion: true
      enableAutomaticUpgrade: true
      forceUpdateTag: aaaaaaaaa
      name: '{extension-name}'
      protectedSettings: {}
      provisionAfterExtensions:
        - aa
      publisher: '{extension-Publisher}'
      resourceGroupName: rgcompute
      settings: {}
      suppressFailures: true
      type: '{extension-Type}'
      typeHandlerVersion: '{handler-version}'
      vmScaleSetName: aaaaaaa
      vmssExtensionName: aaaaaaaaaaaaaaaaaaaaa

```

{{% /example %}}
{{% example %}}
### VirtualMachineScaleSetExtension_CreateOrUpdate_MinimumSet_Gen
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSetExtension = new AzureNative.Compute.VirtualMachineScaleSetExtension("virtualMachineScaleSetExtension", new()
    {
        ResourceGroupName = "rgcompute",
        VmScaleSetName = "aaaaaaaaaaa",
        VmssExtensionName = "aaaaaaaaaaa",
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
		_, err := compute.NewVirtualMachineScaleSetExtension(ctx, "virtualMachineScaleSetExtension", &compute.VirtualMachineScaleSetExtensionArgs{
			ResourceGroupName: pulumi.String("rgcompute"),
			VmScaleSetName:    pulumi.String("aaaaaaaaaaa"),
			VmssExtensionName: pulumi.String("aaaaaaaaaaa"),
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
import com.pulumi.azurenative.compute.VirtualMachineScaleSetExtension;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetExtensionArgs;
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
        var virtualMachineScaleSetExtension = new VirtualMachineScaleSetExtension("virtualMachineScaleSetExtension", VirtualMachineScaleSetExtensionArgs.builder()        
            .resourceGroupName("rgcompute")
            .vmScaleSetName("aaaaaaaaaaa")
            .vmssExtensionName("aaaaaaaaaaa")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSetExtension = new azure_native.compute.VirtualMachineScaleSetExtension("virtualMachineScaleSetExtension", {
    resourceGroupName: "rgcompute",
    vmScaleSetName: "aaaaaaaaaaa",
    vmssExtensionName: "aaaaaaaaaaa",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set_extension = azure_native.compute.VirtualMachineScaleSetExtension("virtualMachineScaleSetExtension",
    resource_group_name="rgcompute",
    vm_scale_set_name="aaaaaaaaaaa",
    vmss_extension_name="aaaaaaaaaaa")

```

```yaml
resources:
  virtualMachineScaleSetExtension:
    type: azure-native:compute:VirtualMachineScaleSetExtension
    properties:
      resourceGroupName: rgcompute
      vmScaleSetName: aaaaaaaaaaa
      vmssExtensionName: aaaaaaaaaaa

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:compute:VirtualMachineScaleSetExtension {extension-name} aaaaaaaa 
```
