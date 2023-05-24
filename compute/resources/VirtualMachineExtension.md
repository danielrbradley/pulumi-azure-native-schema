Describes a Virtual Machine Extension.
API Version: 2022-11-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### VirtualMachineExtension_CreateOrUpdate_MaximumSet_Gen
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineExtension = new AzureNative.Compute.VirtualMachineExtension("virtualMachineExtension", new()
    {
        AutoUpgradeMinorVersion = true,
        EnableAutomaticUpgrade = true,
        ForceUpdateTag = "a",
        InstanceView = new AzureNative.Compute.Inputs.VirtualMachineExtensionInstanceViewArgs
        {
            Name = "aaaaaaaaaaaaaaaaa",
            Statuses = new[]
            {
                new AzureNative.Compute.Inputs.InstanceViewStatusArgs
                {
                    Code = "aaaaaaaaaaaaaaaaaaaaaaa",
                    DisplayStatus = "aaaaaa",
                    Level = AzureNative.Compute.StatusLevelTypes.Info,
                    Message = "a",
                    Time = "2021-11-30T12:58:26.522Z",
                },
            },
            Substatuses = new[]
            {
                new AzureNative.Compute.Inputs.InstanceViewStatusArgs
                {
                    Code = "aaaaaaaaaaaaaaaaaaaaaaa",
                    DisplayStatus = "aaaaaa",
                    Level = AzureNative.Compute.StatusLevelTypes.Info,
                    Message = "a",
                    Time = "2021-11-30T12:58:26.522Z",
                },
            },
            Type = "aaaaaaaaa",
            TypeHandlerVersion = "aaaaaaaaaaaaaaaaaaaaaaaaaa",
        },
        Location = "westus",
        ProtectedSettings = null,
        Publisher = "extPublisher",
        ResourceGroupName = "rgcompute",
        Settings = null,
        SuppressFailures = true,
        Tags = 
        {
            { "key9183", "aa" },
        },
        Type = "extType",
        TypeHandlerVersion = "1.2",
        VmExtensionName = "aaaaaaaaaaaaa",
        VmName = "aaaaaaaaaaaaaaaaaaaaaaaa",
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
		_, err := compute.NewVirtualMachineExtension(ctx, "virtualMachineExtension", &compute.VirtualMachineExtensionArgs{
			AutoUpgradeMinorVersion: pulumi.Bool(true),
			EnableAutomaticUpgrade:  pulumi.Bool(true),
			ForceUpdateTag:          pulumi.String("a"),
			InstanceView: compute.VirtualMachineExtensionInstanceViewResponse{
				Name: pulumi.String("aaaaaaaaaaaaaaaaa"),
				Statuses: compute.InstanceViewStatusArray{
					&compute.InstanceViewStatusArgs{
						Code:          pulumi.String("aaaaaaaaaaaaaaaaaaaaaaa"),
						DisplayStatus: pulumi.String("aaaaaa"),
						Level:         compute.StatusLevelTypesInfo,
						Message:       pulumi.String("a"),
						Time:          pulumi.String("2021-11-30T12:58:26.522Z"),
					},
				},
				Substatuses: compute.InstanceViewStatusArray{
					&compute.InstanceViewStatusArgs{
						Code:          pulumi.String("aaaaaaaaaaaaaaaaaaaaaaa"),
						DisplayStatus: pulumi.String("aaaaaa"),
						Level:         compute.StatusLevelTypesInfo,
						Message:       pulumi.String("a"),
						Time:          pulumi.String("2021-11-30T12:58:26.522Z"),
					},
				},
				Type:               pulumi.String("aaaaaaaaa"),
				TypeHandlerVersion: pulumi.String("aaaaaaaaaaaaaaaaaaaaaaaaaa"),
			},
			Location:          pulumi.String("westus"),
			ProtectedSettings: nil,
			Publisher:         pulumi.String("extPublisher"),
			ResourceGroupName: pulumi.String("rgcompute"),
			Settings:          nil,
			SuppressFailures:  pulumi.Bool(true),
			Tags: pulumi.StringMap{
				"key9183": pulumi.String("aa"),
			},
			Type:               pulumi.String("extType"),
			TypeHandlerVersion: pulumi.String("1.2"),
			VmExtensionName:    pulumi.String("aaaaaaaaaaaaa"),
			VmName:             pulumi.String("aaaaaaaaaaaaaaaaaaaaaaaa"),
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
import com.pulumi.azurenative.compute.VirtualMachineExtension;
import com.pulumi.azurenative.compute.VirtualMachineExtensionArgs;
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
        var virtualMachineExtension = new VirtualMachineExtension("virtualMachineExtension", VirtualMachineExtensionArgs.builder()        
            .autoUpgradeMinorVersion(true)
            .enableAutomaticUpgrade(true)
            .forceUpdateTag("a")
            .instanceView(Map.ofEntries(
                Map.entry("name", "aaaaaaaaaaaaaaaaa"),
                Map.entry("statuses", Map.ofEntries(
                    Map.entry("code", "aaaaaaaaaaaaaaaaaaaaaaa"),
                    Map.entry("displayStatus", "aaaaaa"),
                    Map.entry("level", "Info"),
                    Map.entry("message", "a"),
                    Map.entry("time", "2021-11-30T12:58:26.522Z")
                )),
                Map.entry("substatuses", Map.ofEntries(
                    Map.entry("code", "aaaaaaaaaaaaaaaaaaaaaaa"),
                    Map.entry("displayStatus", "aaaaaa"),
                    Map.entry("level", "Info"),
                    Map.entry("message", "a"),
                    Map.entry("time", "2021-11-30T12:58:26.522Z")
                )),
                Map.entry("type", "aaaaaaaaa"),
                Map.entry("typeHandlerVersion", "aaaaaaaaaaaaaaaaaaaaaaaaaa")
            ))
            .location("westus")
            .protectedSettings()
            .publisher("extPublisher")
            .resourceGroupName("rgcompute")
            .settings()
            .suppressFailures(true)
            .tags(Map.of("key9183", "aa"))
            .type("extType")
            .typeHandlerVersion("1.2")
            .vmExtensionName("aaaaaaaaaaaaa")
            .vmName("aaaaaaaaaaaaaaaaaaaaaaaa")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineExtension = new azure_native.compute.VirtualMachineExtension("virtualMachineExtension", {
    autoUpgradeMinorVersion: true,
    enableAutomaticUpgrade: true,
    forceUpdateTag: "a",
    instanceView: {
        name: "aaaaaaaaaaaaaaaaa",
        statuses: [{
            code: "aaaaaaaaaaaaaaaaaaaaaaa",
            displayStatus: "aaaaaa",
            level: azure_native.compute.StatusLevelTypes.Info,
            message: "a",
            time: "2021-11-30T12:58:26.522Z",
        }],
        substatuses: [{
            code: "aaaaaaaaaaaaaaaaaaaaaaa",
            displayStatus: "aaaaaa",
            level: azure_native.compute.StatusLevelTypes.Info,
            message: "a",
            time: "2021-11-30T12:58:26.522Z",
        }],
        type: "aaaaaaaaa",
        typeHandlerVersion: "aaaaaaaaaaaaaaaaaaaaaaaaaa",
    },
    location: "westus",
    protectedSettings: {},
    publisher: "extPublisher",
    resourceGroupName: "rgcompute",
    settings: {},
    suppressFailures: true,
    tags: {
        key9183: "aa",
    },
    type: "extType",
    typeHandlerVersion: "1.2",
    vmExtensionName: "aaaaaaaaaaaaa",
    vmName: "aaaaaaaaaaaaaaaaaaaaaaaa",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_extension = azure_native.compute.VirtualMachineExtension("virtualMachineExtension",
    auto_upgrade_minor_version=True,
    enable_automatic_upgrade=True,
    force_update_tag="a",
    instance_view=azure_native.compute.VirtualMachineExtensionInstanceViewResponseArgs(
        name="aaaaaaaaaaaaaaaaa",
        statuses=[azure_native.compute.InstanceViewStatusArgs(
            code="aaaaaaaaaaaaaaaaaaaaaaa",
            display_status="aaaaaa",
            level=azure_native.compute.StatusLevelTypes.INFO,
            message="a",
            time="2021-11-30T12:58:26.522Z",
        )],
        substatuses=[azure_native.compute.InstanceViewStatusArgs(
            code="aaaaaaaaaaaaaaaaaaaaaaa",
            display_status="aaaaaa",
            level=azure_native.compute.StatusLevelTypes.INFO,
            message="a",
            time="2021-11-30T12:58:26.522Z",
        )],
        type="aaaaaaaaa",
        type_handler_version="aaaaaaaaaaaaaaaaaaaaaaaaaa",
    ),
    location="westus",
    protected_settings={},
    publisher="extPublisher",
    resource_group_name="rgcompute",
    settings={},
    suppress_failures=True,
    tags={
        "key9183": "aa",
    },
    type="extType",
    type_handler_version="1.2",
    vm_extension_name="aaaaaaaaaaaaa",
    vm_name="aaaaaaaaaaaaaaaaaaaaaaaa")

```

```yaml
resources:
  virtualMachineExtension:
    type: azure-native:compute:VirtualMachineExtension
    properties:
      autoUpgradeMinorVersion: true
      enableAutomaticUpgrade: true
      forceUpdateTag: a
      instanceView:
        name: aaaaaaaaaaaaaaaaa
        statuses:
          - code: aaaaaaaaaaaaaaaaaaaaaaa
            displayStatus: aaaaaa
            level: Info
            message: a
            time: 2021-11-30T12:58:26.522Z
        substatuses:
          - code: aaaaaaaaaaaaaaaaaaaaaaa
            displayStatus: aaaaaa
            level: Info
            message: a
            time: 2021-11-30T12:58:26.522Z
        type: aaaaaaaaa
        typeHandlerVersion: aaaaaaaaaaaaaaaaaaaaaaaaaa
      location: westus
      protectedSettings: {}
      publisher: extPublisher
      resourceGroupName: rgcompute
      settings: {}
      suppressFailures: true
      tags:
        key9183: aa
      type: extType
      typeHandlerVersion: '1.2'
      vmExtensionName: aaaaaaaaaaaaa
      vmName: aaaaaaaaaaaaaaaaaaaaaaaa

```

{{% /example %}}
{{% example %}}
### VirtualMachineExtension_CreateOrUpdate_MinimumSet_Gen
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineExtension = new AzureNative.Compute.VirtualMachineExtension("virtualMachineExtension", new()
    {
        Location = "westus",
        ResourceGroupName = "rgcompute",
        VmExtensionName = "myVMExtension",
        VmName = "myVM",
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
		_, err := compute.NewVirtualMachineExtension(ctx, "virtualMachineExtension", &compute.VirtualMachineExtensionArgs{
			Location:          pulumi.String("westus"),
			ResourceGroupName: pulumi.String("rgcompute"),
			VmExtensionName:   pulumi.String("myVMExtension"),
			VmName:            pulumi.String("myVM"),
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
import com.pulumi.azurenative.compute.VirtualMachineExtension;
import com.pulumi.azurenative.compute.VirtualMachineExtensionArgs;
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
        var virtualMachineExtension = new VirtualMachineExtension("virtualMachineExtension", VirtualMachineExtensionArgs.builder()        
            .location("westus")
            .resourceGroupName("rgcompute")
            .vmExtensionName("myVMExtension")
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineExtension = new azure_native.compute.VirtualMachineExtension("virtualMachineExtension", {
    location: "westus",
    resourceGroupName: "rgcompute",
    vmExtensionName: "myVMExtension",
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_extension = azure_native.compute.VirtualMachineExtension("virtualMachineExtension",
    location="westus",
    resource_group_name="rgcompute",
    vm_extension_name="myVMExtension",
    vm_name="myVM")

```

```yaml
resources:
  virtualMachineExtension:
    type: azure-native:compute:VirtualMachineExtension
    properties:
      location: westus
      resourceGroupName: rgcompute
      vmExtensionName: myVMExtension
      vmName: myVM

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:compute:VirtualMachineExtension myVMExtension /subscriptions/{subscription-id}/resourceGroups/rgcompute/providers/Microsoft.Compute/virtualMachines/myVM/extensions/myVMExtension 
```
