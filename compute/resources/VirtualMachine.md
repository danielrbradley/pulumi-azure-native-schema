Describes a Virtual Machine.
API Version: 2022-11-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a Linux vm with a patch setting assessmentMode of ImageDefault.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D2s_v3",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
            LinuxConfiguration = new AzureNative.Compute.Inputs.LinuxConfigurationArgs
            {
                PatchSettings = new AzureNative.Compute.Inputs.LinuxPatchSettingsArgs
                {
                    AssessmentMode = "ImageDefault",
                },
                ProvisionVMAgent = true,
            },
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "UbuntuServer",
                Publisher = "Canonical",
                Sku = "16.04-LTS",
                Version = "latest",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Premium_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .hardwareProfile(Map.of("vmSize", "Standard_D2s_v3"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM"),
                Map.entry("linuxConfiguration", Map.ofEntries(
                    Map.entry("patchSettings", Map.of("assessmentMode", "ImageDefault")),
                    Map.entry("provisionVMAgent", true)
                ))
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "UbuntuServer"),
                    Map.entry("publisher", "Canonical"),
                    Map.entry("sku", "16.04-LTS"),
                    Map.entry("version", "latest")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadWrite"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Premium_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    hardwareProfile: {
        vmSize: "Standard_D2s_v3",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
        linuxConfiguration: {
            patchSettings: {
                assessmentMode: "ImageDefault",
            },
            provisionVMAgent: true,
        },
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        imageReference: {
            offer: "UbuntuServer",
            publisher: "Canonical",
            sku: "16.04-LTS",
            version: "latest",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadWrite,
            createOption: "FromImage",
            managedDisk: {
                storageAccountType: "Premium_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_D2s_v3",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileResponseArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
        linux_configuration={
            "patchSettings": azure_native.compute.LinuxPatchSettingsArgs(
                assessment_mode="ImageDefault",
            ),
            "provisionVMAgent": True,
        },
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="UbuntuServer",
            publisher="Canonical",
            sku="16.04-LTS",
            version="latest",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_WRITE,
            "createOption": "FromImage",
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Premium_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      hardwareProfile:
        vmSize: Standard_D2s_v3
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
        linuxConfiguration:
          patchSettings:
            assessmentMode: ImageDefault
          provisionVMAgent: true
      resourceGroupName: myResourceGroup
      storageProfile:
        imageReference:
          offer: UbuntuServer
          publisher: Canonical
          sku: 16.04-LTS
          version: latest
        osDisk:
          caching: ReadWrite
          createOption: FromImage
          managedDisk:
            storageAccountType: Premium_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a Linux vm with a patch setting patchMode of AutomaticByPlatform and AutomaticByPlatformSettings.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D2s_v3",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
            LinuxConfiguration = new AzureNative.Compute.Inputs.LinuxConfigurationArgs
            {
                PatchSettings = new AzureNative.Compute.Inputs.LinuxPatchSettingsArgs
                {
                    AssessmentMode = "AutomaticByPlatform",
                    AutomaticByPlatformSettings = new AzureNative.Compute.Inputs.LinuxVMGuestPatchAutomaticByPlatformSettingsArgs
                    {
                        RebootSetting = "Never",
                    },
                    PatchMode = "AutomaticByPlatform",
                },
                ProvisionVMAgent = true,
            },
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "UbuntuServer",
                Publisher = "Canonical",
                Sku = "16.04-LTS",
                Version = "latest",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Premium_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .hardwareProfile(Map.of("vmSize", "Standard_D2s_v3"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM"),
                Map.entry("linuxConfiguration", Map.ofEntries(
                    Map.entry("patchSettings", Map.ofEntries(
                        Map.entry("assessmentMode", "AutomaticByPlatform"),
                        Map.entry("automaticByPlatformSettings", Map.of("rebootSetting", "Never")),
                        Map.entry("patchMode", "AutomaticByPlatform")
                    )),
                    Map.entry("provisionVMAgent", true)
                ))
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "UbuntuServer"),
                    Map.entry("publisher", "Canonical"),
                    Map.entry("sku", "16.04-LTS"),
                    Map.entry("version", "latest")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadWrite"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Premium_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    hardwareProfile: {
        vmSize: "Standard_D2s_v3",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
        linuxConfiguration: {
            patchSettings: {
                assessmentMode: "AutomaticByPlatform",
                automaticByPlatformSettings: {
                    rebootSetting: "Never",
                },
                patchMode: "AutomaticByPlatform",
            },
            provisionVMAgent: true,
        },
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        imageReference: {
            offer: "UbuntuServer",
            publisher: "Canonical",
            sku: "16.04-LTS",
            version: "latest",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadWrite,
            createOption: "FromImage",
            managedDisk: {
                storageAccountType: "Premium_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_D2s_v3",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileResponseArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
        linux_configuration={
            "patchSettings": {
                "assessmentMode": "AutomaticByPlatform",
                "automaticByPlatformSettings": azure_native.compute.LinuxVMGuestPatchAutomaticByPlatformSettingsArgs(
                    reboot_setting="Never",
                ),
                "patchMode": "AutomaticByPlatform",
            },
            "provisionVMAgent": True,
        },
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="UbuntuServer",
            publisher="Canonical",
            sku="16.04-LTS",
            version="latest",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_WRITE,
            "createOption": "FromImage",
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Premium_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      hardwareProfile:
        vmSize: Standard_D2s_v3
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
        linuxConfiguration:
          patchSettings:
            assessmentMode: AutomaticByPlatform
            automaticByPlatformSettings:
              rebootSetting: Never
            patchMode: AutomaticByPlatform
          provisionVMAgent: true
      resourceGroupName: myResourceGroup
      storageProfile:
        imageReference:
          offer: UbuntuServer
          publisher: Canonical
          sku: 16.04-LTS
          version: latest
        osDisk:
          caching: ReadWrite
          createOption: FromImage
          managedDisk:
            storageAccountType: Premium_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a Linux vm with a patch setting patchMode of ImageDefault.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D2s_v3",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
            LinuxConfiguration = new AzureNative.Compute.Inputs.LinuxConfigurationArgs
            {
                PatchSettings = new AzureNative.Compute.Inputs.LinuxPatchSettingsArgs
                {
                    PatchMode = "ImageDefault",
                },
                ProvisionVMAgent = true,
            },
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "UbuntuServer",
                Publisher = "Canonical",
                Sku = "16.04-LTS",
                Version = "latest",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Premium_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .hardwareProfile(Map.of("vmSize", "Standard_D2s_v3"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM"),
                Map.entry("linuxConfiguration", Map.ofEntries(
                    Map.entry("patchSettings", Map.of("patchMode", "ImageDefault")),
                    Map.entry("provisionVMAgent", true)
                ))
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "UbuntuServer"),
                    Map.entry("publisher", "Canonical"),
                    Map.entry("sku", "16.04-LTS"),
                    Map.entry("version", "latest")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadWrite"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Premium_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    hardwareProfile: {
        vmSize: "Standard_D2s_v3",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
        linuxConfiguration: {
            patchSettings: {
                patchMode: "ImageDefault",
            },
            provisionVMAgent: true,
        },
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        imageReference: {
            offer: "UbuntuServer",
            publisher: "Canonical",
            sku: "16.04-LTS",
            version: "latest",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadWrite,
            createOption: "FromImage",
            managedDisk: {
                storageAccountType: "Premium_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_D2s_v3",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileResponseArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
        linux_configuration={
            "patchSettings": azure_native.compute.LinuxPatchSettingsArgs(
                patch_mode="ImageDefault",
            ),
            "provisionVMAgent": True,
        },
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="UbuntuServer",
            publisher="Canonical",
            sku="16.04-LTS",
            version="latest",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_WRITE,
            "createOption": "FromImage",
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Premium_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      hardwareProfile:
        vmSize: Standard_D2s_v3
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
        linuxConfiguration:
          patchSettings:
            patchMode: ImageDefault
          provisionVMAgent: true
      resourceGroupName: myResourceGroup
      storageProfile:
        imageReference:
          offer: UbuntuServer
          publisher: Canonical
          sku: 16.04-LTS
          version: latest
        osDisk:
          caching: ReadWrite
          createOption: FromImage
          managedDisk:
            storageAccountType: Premium_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a Linux vm with a patch settings patchMode and assessmentMode set to AutomaticByPlatform.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D2s_v3",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
            LinuxConfiguration = new AzureNative.Compute.Inputs.LinuxConfigurationArgs
            {
                PatchSettings = new AzureNative.Compute.Inputs.LinuxPatchSettingsArgs
                {
                    AssessmentMode = "AutomaticByPlatform",
                    PatchMode = "AutomaticByPlatform",
                },
                ProvisionVMAgent = true,
            },
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "UbuntuServer",
                Publisher = "Canonical",
                Sku = "16.04-LTS",
                Version = "latest",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Premium_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .hardwareProfile(Map.of("vmSize", "Standard_D2s_v3"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM"),
                Map.entry("linuxConfiguration", Map.ofEntries(
                    Map.entry("patchSettings", Map.ofEntries(
                        Map.entry("assessmentMode", "AutomaticByPlatform"),
                        Map.entry("patchMode", "AutomaticByPlatform")
                    )),
                    Map.entry("provisionVMAgent", true)
                ))
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "UbuntuServer"),
                    Map.entry("publisher", "Canonical"),
                    Map.entry("sku", "16.04-LTS"),
                    Map.entry("version", "latest")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadWrite"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Premium_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    hardwareProfile: {
        vmSize: "Standard_D2s_v3",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
        linuxConfiguration: {
            patchSettings: {
                assessmentMode: "AutomaticByPlatform",
                patchMode: "AutomaticByPlatform",
            },
            provisionVMAgent: true,
        },
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        imageReference: {
            offer: "UbuntuServer",
            publisher: "Canonical",
            sku: "16.04-LTS",
            version: "latest",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadWrite,
            createOption: "FromImage",
            managedDisk: {
                storageAccountType: "Premium_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_D2s_v3",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileResponseArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
        linux_configuration={
            "patchSettings": azure_native.compute.LinuxPatchSettingsArgs(
                assessment_mode="AutomaticByPlatform",
                patch_mode="AutomaticByPlatform",
            ),
            "provisionVMAgent": True,
        },
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="UbuntuServer",
            publisher="Canonical",
            sku="16.04-LTS",
            version="latest",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_WRITE,
            "createOption": "FromImage",
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Premium_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      hardwareProfile:
        vmSize: Standard_D2s_v3
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
        linuxConfiguration:
          patchSettings:
            assessmentMode: AutomaticByPlatform
            patchMode: AutomaticByPlatform
          provisionVMAgent: true
      resourceGroupName: myResourceGroup
      storageProfile:
        imageReference:
          offer: UbuntuServer
          publisher: Canonical
          sku: 16.04-LTS
          version: latest
        osDisk:
          caching: ReadWrite
          createOption: FromImage
          managedDisk:
            storageAccountType: Premium_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a VM from a community gallery image
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D1_v2",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                CommunityGalleryImageId = "/CommunityGalleries/galleryPublicName/Images/communityGalleryImageName/Versions/communityGalleryImageVersionName",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Standard_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .hardwareProfile(Map.of("vmSize", "Standard_D1_v2"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM")
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.of("communityGalleryImageId", "/CommunityGalleries/galleryPublicName/Images/communityGalleryImageName/Versions/communityGalleryImageVersionName")),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadWrite"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    hardwareProfile: {
        vmSize: "Standard_D1_v2",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        imageReference: {
            communityGalleryImageId: "/CommunityGalleries/galleryPublicName/Images/communityGalleryImageName/Versions/communityGalleryImageVersionName",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadWrite,
            createOption: "FromImage",
            managedDisk: {
                storageAccountType: "Standard_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_D1_v2",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            community_gallery_image_id="/CommunityGalleries/galleryPublicName/Images/communityGalleryImageName/Versions/communityGalleryImageVersionName",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_WRITE,
            "createOption": "FromImage",
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Standard_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      hardwareProfile:
        vmSize: Standard_D1_v2
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
      resourceGroupName: myResourceGroup
      storageProfile:
        imageReference:
          communityGalleryImageId: /CommunityGalleries/galleryPublicName/Images/communityGalleryImageName/Versions/communityGalleryImageVersionName
        osDisk:
          caching: ReadWrite
          createOption: FromImage
          managedDisk:
            storageAccountType: Standard_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a VM from a shared gallery image
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D1_v2",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                SharedGalleryImageId = "/SharedGalleries/sharedGalleryName/Images/sharedGalleryImageName/Versions/sharedGalleryImageVersionName",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Standard_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .hardwareProfile(Map.of("vmSize", "Standard_D1_v2"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM")
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.of("sharedGalleryImageId", "/SharedGalleries/sharedGalleryName/Images/sharedGalleryImageName/Versions/sharedGalleryImageVersionName")),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadWrite"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    hardwareProfile: {
        vmSize: "Standard_D1_v2",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        imageReference: {
            sharedGalleryImageId: "/SharedGalleries/sharedGalleryName/Images/sharedGalleryImageName/Versions/sharedGalleryImageVersionName",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadWrite,
            createOption: "FromImage",
            managedDisk: {
                storageAccountType: "Standard_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_D1_v2",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            shared_gallery_image_id="/SharedGalleries/sharedGalleryName/Images/sharedGalleryImageName/Versions/sharedGalleryImageVersionName",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_WRITE,
            "createOption": "FromImage",
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Standard_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      hardwareProfile:
        vmSize: Standard_D1_v2
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
      resourceGroupName: myResourceGroup
      storageProfile:
        imageReference:
          sharedGalleryImageId: /SharedGalleries/sharedGalleryName/Images/sharedGalleryImageName/Versions/sharedGalleryImageVersionName
        osDisk:
          caching: ReadWrite
          createOption: FromImage
          managedDisk:
            storageAccountType: Standard_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a VM with Disk Controller Type
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        DiagnosticsProfile = new AzureNative.Compute.Inputs.DiagnosticsProfileArgs
        {
            BootDiagnostics = new AzureNative.Compute.Inputs.BootDiagnosticsArgs
            {
                Enabled = true,
                StorageUri = "http://{existing-storage-account-name}.blob.core.windows.net",
            },
        },
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D4_v3",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            DiskControllerType = "NVMe",
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "WindowsServer",
                Publisher = "MicrosoftWindowsServer",
                Sku = "2016-Datacenter",
                Version = "latest",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Standard_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        UserData = "U29tZSBDdXN0b20gRGF0YQ==",
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .diagnosticsProfile(Map.of("bootDiagnostics", Map.ofEntries(
                Map.entry("enabled", true),
                Map.entry("storageUri", "http://{existing-storage-account-name}.blob.core.windows.net")
            )))
            .hardwareProfile(Map.of("vmSize", "Standard_D4_v3"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM")
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("diskControllerType", "NVMe"),
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "WindowsServer"),
                    Map.entry("publisher", "MicrosoftWindowsServer"),
                    Map.entry("sku", "2016-Datacenter"),
                    Map.entry("version", "latest")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadWrite"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .userData("U29tZSBDdXN0b20gRGF0YQ==")
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    diagnosticsProfile: {
        bootDiagnostics: {
            enabled: true,
            storageUri: "http://{existing-storage-account-name}.blob.core.windows.net",
        },
    },
    hardwareProfile: {
        vmSize: "Standard_D4_v3",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        diskControllerType: "NVMe",
        imageReference: {
            offer: "WindowsServer",
            publisher: "MicrosoftWindowsServer",
            sku: "2016-Datacenter",
            version: "latest",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadWrite,
            createOption: "FromImage",
            managedDisk: {
                storageAccountType: "Standard_LRS",
            },
            name: "myVMosdisk",
        },
    },
    userData: "U29tZSBDdXN0b20gRGF0YQ==",
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    diagnostics_profile=azure_native.compute.DiagnosticsProfileResponseArgs(
        boot_diagnostics=azure_native.compute.BootDiagnosticsArgs(
            enabled=True,
            storage_uri="http://{existing-storage-account-name}.blob.core.windows.net",
        ),
    ),
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_D4_v3",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        disk_controller_type="NVMe",
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="WindowsServer",
            publisher="MicrosoftWindowsServer",
            sku="2016-Datacenter",
            version="latest",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_WRITE,
            "createOption": "FromImage",
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Standard_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    user_data="U29tZSBDdXN0b20gRGF0YQ==",
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      diagnosticsProfile:
        bootDiagnostics:
          enabled: true
          storageUri: http://{existing-storage-account-name}.blob.core.windows.net
      hardwareProfile:
        vmSize: Standard_D4_v3
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
      resourceGroupName: myResourceGroup
      storageProfile:
        diskControllerType: NVMe
        imageReference:
          offer: WindowsServer
          publisher: MicrosoftWindowsServer
          sku: 2016-Datacenter
          version: latest
        osDisk:
          caching: ReadWrite
          createOption: FromImage
          managedDisk:
            storageAccountType: Standard_LRS
          name: myVMosdisk
      userData: U29tZSBDdXN0b20gRGF0YQ==
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a VM with HibernationEnabled
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        AdditionalCapabilities = new AzureNative.Compute.Inputs.AdditionalCapabilitiesArgs
        {
            HibernationEnabled = true,
        },
        DiagnosticsProfile = new AzureNative.Compute.Inputs.DiagnosticsProfileArgs
        {
            BootDiagnostics = new AzureNative.Compute.Inputs.BootDiagnosticsArgs
            {
                Enabled = true,
                StorageUri = "http://{existing-storage-account-name}.blob.core.windows.net",
            },
        },
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D2s_v3",
        },
        Location = "eastus2euap",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "{vm-name}",
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "WindowsServer",
                Publisher = "MicrosoftWindowsServer",
                Sku = "2019-Datacenter",
                Version = "latest",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Standard_LRS",
                },
                Name = "vmOSdisk",
            },
        },
        VmName = "{vm-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .additionalCapabilities(Map.of("hibernationEnabled", true))
            .diagnosticsProfile(Map.of("bootDiagnostics", Map.ofEntries(
                Map.entry("enabled", true),
                Map.entry("storageUri", "http://{existing-storage-account-name}.blob.core.windows.net")
            )))
            .hardwareProfile(Map.of("vmSize", "Standard_D2s_v3"))
            .location("eastus2euap")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "{vm-name}")
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "WindowsServer"),
                    Map.entry("publisher", "MicrosoftWindowsServer"),
                    Map.entry("sku", "2019-Datacenter"),
                    Map.entry("version", "latest")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadWrite"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS")),
                    Map.entry("name", "vmOSdisk")
                ))
            ))
            .vmName("{vm-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    additionalCapabilities: {
        hibernationEnabled: true,
    },
    diagnosticsProfile: {
        bootDiagnostics: {
            enabled: true,
            storageUri: "http://{existing-storage-account-name}.blob.core.windows.net",
        },
    },
    hardwareProfile: {
        vmSize: "Standard_D2s_v3",
    },
    location: "eastus2euap",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "{vm-name}",
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        imageReference: {
            offer: "WindowsServer",
            publisher: "MicrosoftWindowsServer",
            sku: "2019-Datacenter",
            version: "latest",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadWrite,
            createOption: "FromImage",
            managedDisk: {
                storageAccountType: "Standard_LRS",
            },
            name: "vmOSdisk",
        },
    },
    vmName: "{vm-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    additional_capabilities=azure_native.compute.AdditionalCapabilitiesArgs(
        hibernation_enabled=True,
    ),
    diagnostics_profile=azure_native.compute.DiagnosticsProfileResponseArgs(
        boot_diagnostics=azure_native.compute.BootDiagnosticsArgs(
            enabled=True,
            storage_uri="http://{existing-storage-account-name}.blob.core.windows.net",
        ),
    ),
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_D2s_v3",
    ),
    location="eastus2euap",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="{vm-name}",
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="WindowsServer",
            publisher="MicrosoftWindowsServer",
            sku="2019-Datacenter",
            version="latest",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_WRITE,
            "createOption": "FromImage",
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Standard_LRS",
            ),
            "name": "vmOSdisk",
        },
    ),
    vm_name="{vm-name}")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      additionalCapabilities:
        hibernationEnabled: true
      diagnosticsProfile:
        bootDiagnostics:
          enabled: true
          storageUri: http://{existing-storage-account-name}.blob.core.windows.net
      hardwareProfile:
        vmSize: Standard_D2s_v3
      location: eastus2euap
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: '{vm-name}'
      resourceGroupName: myResourceGroup
      storageProfile:
        imageReference:
          offer: WindowsServer
          publisher: MicrosoftWindowsServer
          sku: 2019-Datacenter
          version: latest
        osDisk:
          caching: ReadWrite
          createOption: FromImage
          managedDisk:
            storageAccountType: Standard_LRS
          name: vmOSdisk
      vmName: '{vm-name}'

```

{{% /example %}}
{{% example %}}
### Create a VM with Uefi Settings of secureBoot and vTPM.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D2s_v3",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
        },
        ResourceGroupName = "myResourceGroup",
        SecurityProfile = new AzureNative.Compute.Inputs.SecurityProfileArgs
        {
            SecurityType = "TrustedLaunch",
            UefiSettings = new AzureNative.Compute.Inputs.UefiSettingsArgs
            {
                SecureBootEnabled = true,
                VTpmEnabled = true,
            },
        },
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "windowsserver-gen2preview-preview",
                Publisher = "MicrosoftWindowsServer",
                Sku = "windows10-tvm",
                Version = "18363.592.2001092016",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadOnly,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "StandardSSD_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .hardwareProfile(Map.of("vmSize", "Standard_D2s_v3"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM")
            ))
            .resourceGroupName("myResourceGroup")
            .securityProfile(Map.ofEntries(
                Map.entry("securityType", "TrustedLaunch"),
                Map.entry("uefiSettings", Map.ofEntries(
                    Map.entry("secureBootEnabled", true),
                    Map.entry("vTpmEnabled", true)
                ))
            ))
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "windowsserver-gen2preview-preview"),
                    Map.entry("publisher", "MicrosoftWindowsServer"),
                    Map.entry("sku", "windows10-tvm"),
                    Map.entry("version", "18363.592.2001092016")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadOnly"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.of("storageAccountType", "StandardSSD_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    hardwareProfile: {
        vmSize: "Standard_D2s_v3",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
    },
    resourceGroupName: "myResourceGroup",
    securityProfile: {
        securityType: "TrustedLaunch",
        uefiSettings: {
            secureBootEnabled: true,
            vTpmEnabled: true,
        },
    },
    storageProfile: {
        imageReference: {
            offer: "windowsserver-gen2preview-preview",
            publisher: "MicrosoftWindowsServer",
            sku: "windows10-tvm",
            version: "18363.592.2001092016",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadOnly,
            createOption: "FromImage",
            managedDisk: {
                storageAccountType: "StandardSSD_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_D2s_v3",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
    ),
    resource_group_name="myResourceGroup",
    security_profile=azure_native.compute.SecurityProfileResponseArgs(
        security_type="TrustedLaunch",
        uefi_settings=azure_native.compute.UefiSettingsArgs(
            secure_boot_enabled=True,
            v_tpm_enabled=True,
        ),
    ),
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="windowsserver-gen2preview-preview",
            publisher="MicrosoftWindowsServer",
            sku="windows10-tvm",
            version="18363.592.2001092016",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_ONLY,
            "createOption": "FromImage",
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="StandardSSD_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      hardwareProfile:
        vmSize: Standard_D2s_v3
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
      resourceGroupName: myResourceGroup
      securityProfile:
        securityType: TrustedLaunch
        uefiSettings:
          secureBootEnabled: true
          vTpmEnabled: true
      storageProfile:
        imageReference:
          offer: windowsserver-gen2preview-preview
          publisher: MicrosoftWindowsServer
          sku: windows10-tvm
          version: 18363.592.2001092016
        osDisk:
          caching: ReadOnly
          createOption: FromImage
          managedDisk:
            storageAccountType: StandardSSD_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a VM with UserData
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        DiagnosticsProfile = new AzureNative.Compute.Inputs.DiagnosticsProfileArgs
        {
            BootDiagnostics = new AzureNative.Compute.Inputs.BootDiagnosticsArgs
            {
                Enabled = true,
                StorageUri = "http://{existing-storage-account-name}.blob.core.windows.net",
            },
        },
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D1_v2",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "{vm-name}",
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "WindowsServer",
                Publisher = "MicrosoftWindowsServer",
                Sku = "2016-Datacenter",
                Version = "latest",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Standard_LRS",
                },
                Name = "vmOSdisk",
            },
        },
        UserData = "RXhhbXBsZSBVc2VyRGF0YQ==",
        VmName = "{vm-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .diagnosticsProfile(Map.of("bootDiagnostics", Map.ofEntries(
                Map.entry("enabled", true),
                Map.entry("storageUri", "http://{existing-storage-account-name}.blob.core.windows.net")
            )))
            .hardwareProfile(Map.of("vmSize", "Standard_D1_v2"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "{vm-name}")
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "WindowsServer"),
                    Map.entry("publisher", "MicrosoftWindowsServer"),
                    Map.entry("sku", "2016-Datacenter"),
                    Map.entry("version", "latest")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadWrite"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS")),
                    Map.entry("name", "vmOSdisk")
                ))
            ))
            .userData("RXhhbXBsZSBVc2VyRGF0YQ==")
            .vmName("{vm-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    diagnosticsProfile: {
        bootDiagnostics: {
            enabled: true,
            storageUri: "http://{existing-storage-account-name}.blob.core.windows.net",
        },
    },
    hardwareProfile: {
        vmSize: "Standard_D1_v2",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "{vm-name}",
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        imageReference: {
            offer: "WindowsServer",
            publisher: "MicrosoftWindowsServer",
            sku: "2016-Datacenter",
            version: "latest",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadWrite,
            createOption: "FromImage",
            managedDisk: {
                storageAccountType: "Standard_LRS",
            },
            name: "vmOSdisk",
        },
    },
    userData: "RXhhbXBsZSBVc2VyRGF0YQ==",
    vmName: "{vm-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    diagnostics_profile=azure_native.compute.DiagnosticsProfileResponseArgs(
        boot_diagnostics=azure_native.compute.BootDiagnosticsArgs(
            enabled=True,
            storage_uri="http://{existing-storage-account-name}.blob.core.windows.net",
        ),
    ),
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_D1_v2",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="{vm-name}",
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="WindowsServer",
            publisher="MicrosoftWindowsServer",
            sku="2016-Datacenter",
            version="latest",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_WRITE,
            "createOption": "FromImage",
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Standard_LRS",
            ),
            "name": "vmOSdisk",
        },
    ),
    user_data="RXhhbXBsZSBVc2VyRGF0YQ==",
    vm_name="{vm-name}")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      diagnosticsProfile:
        bootDiagnostics:
          enabled: true
          storageUri: http://{existing-storage-account-name}.blob.core.windows.net
      hardwareProfile:
        vmSize: Standard_D1_v2
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: '{vm-name}'
      resourceGroupName: myResourceGroup
      storageProfile:
        imageReference:
          offer: WindowsServer
          publisher: MicrosoftWindowsServer
          sku: 2016-Datacenter
          version: latest
        osDisk:
          caching: ReadWrite
          createOption: FromImage
          managedDisk:
            storageAccountType: Standard_LRS
          name: vmOSdisk
      userData: RXhhbXBsZSBVc2VyRGF0YQ==
      vmName: '{vm-name}'

```

{{% /example %}}
{{% example %}}
### Create a VM with VM Size Properties
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        DiagnosticsProfile = new AzureNative.Compute.Inputs.DiagnosticsProfileArgs
        {
            BootDiagnostics = new AzureNative.Compute.Inputs.BootDiagnosticsArgs
            {
                Enabled = true,
                StorageUri = "http://{existing-storage-account-name}.blob.core.windows.net",
            },
        },
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D4_v3",
            VmSizeProperties = new AzureNative.Compute.Inputs.VMSizePropertiesArgs
            {
                VCPUsAvailable = 1,
                VCPUsPerCore = 1,
            },
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "WindowsServer",
                Publisher = "MicrosoftWindowsServer",
                Sku = "2016-Datacenter",
                Version = "latest",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Standard_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        UserData = "U29tZSBDdXN0b20gRGF0YQ==",
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .diagnosticsProfile(Map.of("bootDiagnostics", Map.ofEntries(
                Map.entry("enabled", true),
                Map.entry("storageUri", "http://{existing-storage-account-name}.blob.core.windows.net")
            )))
            .hardwareProfile(Map.ofEntries(
                Map.entry("vmSize", "Standard_D4_v3"),
                Map.entry("vmSizeProperties", Map.ofEntries(
                    Map.entry("vCPUsAvailable", 1),
                    Map.entry("vCPUsPerCore", 1)
                ))
            ))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM")
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "WindowsServer"),
                    Map.entry("publisher", "MicrosoftWindowsServer"),
                    Map.entry("sku", "2016-Datacenter"),
                    Map.entry("version", "latest")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadWrite"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .userData("U29tZSBDdXN0b20gRGF0YQ==")
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    diagnosticsProfile: {
        bootDiagnostics: {
            enabled: true,
            storageUri: "http://{existing-storage-account-name}.blob.core.windows.net",
        },
    },
    hardwareProfile: {
        vmSize: "Standard_D4_v3",
        vmSizeProperties: {
            vCPUsAvailable: 1,
            vCPUsPerCore: 1,
        },
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        imageReference: {
            offer: "WindowsServer",
            publisher: "MicrosoftWindowsServer",
            sku: "2016-Datacenter",
            version: "latest",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadWrite,
            createOption: "FromImage",
            managedDisk: {
                storageAccountType: "Standard_LRS",
            },
            name: "myVMosdisk",
        },
    },
    userData: "U29tZSBDdXN0b20gRGF0YQ==",
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    diagnostics_profile=azure_native.compute.DiagnosticsProfileResponseArgs(
        boot_diagnostics=azure_native.compute.BootDiagnosticsArgs(
            enabled=True,
            storage_uri="http://{existing-storage-account-name}.blob.core.windows.net",
        ),
    ),
    hardware_profile=azure_native.compute.HardwareProfileResponseArgs(
        vm_size="Standard_D4_v3",
        vm_size_properties=azure_native.compute.VMSizePropertiesArgs(
            v_cpus_available=1,
            v_cpus_per_core=1,
        ),
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="WindowsServer",
            publisher="MicrosoftWindowsServer",
            sku="2016-Datacenter",
            version="latest",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_WRITE,
            "createOption": "FromImage",
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Standard_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    user_data="U29tZSBDdXN0b20gRGF0YQ==",
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      diagnosticsProfile:
        bootDiagnostics:
          enabled: true
          storageUri: http://{existing-storage-account-name}.blob.core.windows.net
      hardwareProfile:
        vmSize: Standard_D4_v3
        vmSizeProperties:
          vCPUsAvailable: 1
          vCPUsPerCore: 1
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
      resourceGroupName: myResourceGroup
      storageProfile:
        imageReference:
          offer: WindowsServer
          publisher: MicrosoftWindowsServer
          sku: 2016-Datacenter
          version: latest
        osDisk:
          caching: ReadWrite
          createOption: FromImage
          managedDisk:
            storageAccountType: Standard_LRS
          name: myVMosdisk
      userData: U29tZSBDdXN0b20gRGF0YQ==
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a VM with network interface configuration
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D1_v2",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkApiVersion = "2020-11-01",
            NetworkInterfaceConfigurations = new[]
            {
                new AzureNative.Compute.Inputs.VirtualMachineNetworkInterfaceConfigurationArgs
                {
                    DeleteOption = "Delete",
                    IpConfigurations = new[]
                    {
                        new AzureNative.Compute.Inputs.VirtualMachineNetworkInterfaceIPConfigurationArgs
                        {
                            Name = "{ip-config-name}",
                            Primary = true,
                            PublicIPAddressConfiguration = new AzureNative.Compute.Inputs.VirtualMachinePublicIPAddressConfigurationArgs
                            {
                                DeleteOption = "Detach",
                                Name = "{publicIP-config-name}",
                                PublicIPAllocationMethod = "Static",
                                Sku = new AzureNative.Compute.Inputs.PublicIPAddressSkuArgs
                                {
                                    Name = "Basic",
                                    Tier = "Global",
                                },
                            },
                        },
                    },
                    Name = "{nic-config-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "WindowsServer",
                Publisher = "MicrosoftWindowsServer",
                Sku = "2016-Datacenter",
                Version = "latest",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Standard_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .hardwareProfile(Map.of("vmSize", "Standard_D1_v2"))
            .location("westus")
            .networkProfile(Map.ofEntries(
                Map.entry("networkApiVersion", "2020-11-01"),
                Map.entry("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("deleteOption", "Delete"),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("name", "{ip-config-name}"),
                        Map.entry("primary", true),
                        Map.entry("publicIPAddressConfiguration", Map.ofEntries(
                            Map.entry("deleteOption", "Detach"),
                            Map.entry("name", "{publicIP-config-name}"),
                            Map.entry("publicIPAllocationMethod", "Static"),
                            Map.entry("sku", Map.ofEntries(
                                Map.entry("name", "Basic"),
                                Map.entry("tier", "Global")
                            ))
                        ))
                    )),
                    Map.entry("name", "{nic-config-name}"),
                    Map.entry("primary", true)
                ))
            ))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM")
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "WindowsServer"),
                    Map.entry("publisher", "MicrosoftWindowsServer"),
                    Map.entry("sku", "2016-Datacenter"),
                    Map.entry("version", "latest")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadWrite"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    hardwareProfile: {
        vmSize: "Standard_D1_v2",
    },
    location: "westus",
    networkProfile: {
        networkApiVersion: "2020-11-01",
        networkInterfaceConfigurations: [{
            deleteOption: "Delete",
            ipConfigurations: [{
                name: "{ip-config-name}",
                primary: true,
                publicIPAddressConfiguration: {
                    deleteOption: "Detach",
                    name: "{publicIP-config-name}",
                    publicIPAllocationMethod: "Static",
                    sku: {
                        name: "Basic",
                        tier: "Global",
                    },
                },
            }],
            name: "{nic-config-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        imageReference: {
            offer: "WindowsServer",
            publisher: "MicrosoftWindowsServer",
            sku: "2016-Datacenter",
            version: "latest",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadWrite,
            createOption: "FromImage",
            managedDisk: {
                storageAccountType: "Standard_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_D1_v2",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_api_version="2020-11-01",
        network_interface_configurations=[{
            "deleteOption": "Delete",
            "ipConfigurations": [{
                "name": "{ip-config-name}",
                "primary": True,
                "publicIPAddressConfiguration": {
                    "deleteOption": "Detach",
                    "name": "{publicIP-config-name}",
                    "publicIPAllocationMethod": "Static",
                    "sku": azure_native.compute.PublicIPAddressSkuArgs(
                        name="Basic",
                        tier="Global",
                    ),
                },
            }],
            "name": "{nic-config-name}",
            "primary": True,
        }],
    ),
    os_profile=azure_native.compute.OSProfileArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="WindowsServer",
            publisher="MicrosoftWindowsServer",
            sku="2016-Datacenter",
            version="latest",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_WRITE,
            "createOption": "FromImage",
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Standard_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      hardwareProfile:
        vmSize: Standard_D1_v2
      location: westus
      networkProfile:
        networkApiVersion: 2020-11-01
        networkInterfaceConfigurations:
          - deleteOption: Delete
            ipConfigurations:
              - name: '{ip-config-name}'
                primary: true
                publicIPAddressConfiguration:
                  deleteOption: Detach
                  name: '{publicIP-config-name}'
                  publicIPAllocationMethod: Static
                  sku:
                    name: Basic
                    tier: Global
            name: '{nic-config-name}'
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
      resourceGroupName: myResourceGroup
      storageProfile:
        imageReference:
          offer: WindowsServer
          publisher: MicrosoftWindowsServer
          sku: 2016-Datacenter
          version: latest
        osDisk:
          caching: ReadWrite
          createOption: FromImage
          managedDisk:
            storageAccountType: Standard_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a VM with securityType ConfidentialVM with Customer Managed Keys
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_DC2as_v5",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
        },
        ResourceGroupName = "myResourceGroup",
        SecurityProfile = new AzureNative.Compute.Inputs.SecurityProfileArgs
        {
            SecurityType = "ConfidentialVM",
            UefiSettings = new AzureNative.Compute.Inputs.UefiSettingsArgs
            {
                SecureBootEnabled = true,
                VTpmEnabled = true,
            },
        },
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "2019-datacenter-cvm",
                Publisher = "MicrosoftWindowsServer",
                Sku = "windows-cvm",
                Version = "17763.2183.2109130127",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadOnly,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    SecurityProfile = new AzureNative.Compute.Inputs.VMDiskSecurityProfileArgs
                    {
                        DiskEncryptionSet = new AzureNative.Compute.Inputs.DiskEncryptionSetParametersArgs
                        {
                            Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}",
                        },
                        SecurityEncryptionType = "DiskWithVMGuestState",
                    },
                    StorageAccountType = "StandardSSD_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .hardwareProfile(Map.of("vmSize", "Standard_DC2as_v5"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM")
            ))
            .resourceGroupName("myResourceGroup")
            .securityProfile(Map.ofEntries(
                Map.entry("securityType", "ConfidentialVM"),
                Map.entry("uefiSettings", Map.ofEntries(
                    Map.entry("secureBootEnabled", true),
                    Map.entry("vTpmEnabled", true)
                ))
            ))
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "2019-datacenter-cvm"),
                    Map.entry("publisher", "MicrosoftWindowsServer"),
                    Map.entry("sku", "windows-cvm"),
                    Map.entry("version", "17763.2183.2109130127")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadOnly"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.ofEntries(
                        Map.entry("securityProfile", Map.ofEntries(
                            Map.entry("diskEncryptionSet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}")),
                            Map.entry("securityEncryptionType", "DiskWithVMGuestState")
                        )),
                        Map.entry("storageAccountType", "StandardSSD_LRS")
                    )),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    hardwareProfile: {
        vmSize: "Standard_DC2as_v5",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
    },
    resourceGroupName: "myResourceGroup",
    securityProfile: {
        securityType: "ConfidentialVM",
        uefiSettings: {
            secureBootEnabled: true,
            vTpmEnabled: true,
        },
    },
    storageProfile: {
        imageReference: {
            offer: "2019-datacenter-cvm",
            publisher: "MicrosoftWindowsServer",
            sku: "windows-cvm",
            version: "17763.2183.2109130127",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadOnly,
            createOption: "FromImage",
            managedDisk: {
                securityProfile: {
                    diskEncryptionSet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}",
                    },
                    securityEncryptionType: "DiskWithVMGuestState",
                },
                storageAccountType: "StandardSSD_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_DC2as_v5",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
    ),
    resource_group_name="myResourceGroup",
    security_profile=azure_native.compute.SecurityProfileResponseArgs(
        security_type="ConfidentialVM",
        uefi_settings=azure_native.compute.UefiSettingsArgs(
            secure_boot_enabled=True,
            v_tpm_enabled=True,
        ),
    ),
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="2019-datacenter-cvm",
            publisher="MicrosoftWindowsServer",
            sku="windows-cvm",
            version="17763.2183.2109130127",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_ONLY,
            "createOption": "FromImage",
            "managedDisk": {
                "securityProfile": {
                    "diskEncryptionSet": azure_native.compute.DiskEncryptionSetParametersArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}",
                    ),
                    "securityEncryptionType": "DiskWithVMGuestState",
                },
                "storageAccountType": "StandardSSD_LRS",
            },
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      hardwareProfile:
        vmSize: Standard_DC2as_v5
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
      resourceGroupName: myResourceGroup
      securityProfile:
        securityType: ConfidentialVM
        uefiSettings:
          secureBootEnabled: true
          vTpmEnabled: true
      storageProfile:
        imageReference:
          offer: 2019-datacenter-cvm
          publisher: MicrosoftWindowsServer
          sku: windows-cvm
          version: 17763.2183.2109130127
        osDisk:
          caching: ReadOnly
          createOption: FromImage
          managedDisk:
            securityProfile:
              diskEncryptionSet:
                id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}
              securityEncryptionType: DiskWithVMGuestState
            storageAccountType: StandardSSD_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a VM with securityType ConfidentialVM with Platform Managed Keys
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_DC2as_v5",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
        },
        ResourceGroupName = "myResourceGroup",
        SecurityProfile = new AzureNative.Compute.Inputs.SecurityProfileArgs
        {
            SecurityType = "ConfidentialVM",
            UefiSettings = new AzureNative.Compute.Inputs.UefiSettingsArgs
            {
                SecureBootEnabled = true,
                VTpmEnabled = true,
            },
        },
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "2019-datacenter-cvm",
                Publisher = "MicrosoftWindowsServer",
                Sku = "windows-cvm",
                Version = "17763.2183.2109130127",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadOnly,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    SecurityProfile = new AzureNative.Compute.Inputs.VMDiskSecurityProfileArgs
                    {
                        SecurityEncryptionType = "DiskWithVMGuestState",
                    },
                    StorageAccountType = "StandardSSD_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .hardwareProfile(Map.of("vmSize", "Standard_DC2as_v5"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM")
            ))
            .resourceGroupName("myResourceGroup")
            .securityProfile(Map.ofEntries(
                Map.entry("securityType", "ConfidentialVM"),
                Map.entry("uefiSettings", Map.ofEntries(
                    Map.entry("secureBootEnabled", true),
                    Map.entry("vTpmEnabled", true)
                ))
            ))
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "2019-datacenter-cvm"),
                    Map.entry("publisher", "MicrosoftWindowsServer"),
                    Map.entry("sku", "windows-cvm"),
                    Map.entry("version", "17763.2183.2109130127")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadOnly"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.ofEntries(
                        Map.entry("securityProfile", Map.of("securityEncryptionType", "DiskWithVMGuestState")),
                        Map.entry("storageAccountType", "StandardSSD_LRS")
                    )),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    hardwareProfile: {
        vmSize: "Standard_DC2as_v5",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
    },
    resourceGroupName: "myResourceGroup",
    securityProfile: {
        securityType: "ConfidentialVM",
        uefiSettings: {
            secureBootEnabled: true,
            vTpmEnabled: true,
        },
    },
    storageProfile: {
        imageReference: {
            offer: "2019-datacenter-cvm",
            publisher: "MicrosoftWindowsServer",
            sku: "windows-cvm",
            version: "17763.2183.2109130127",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadOnly,
            createOption: "FromImage",
            managedDisk: {
                securityProfile: {
                    securityEncryptionType: "DiskWithVMGuestState",
                },
                storageAccountType: "StandardSSD_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_DC2as_v5",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
    ),
    resource_group_name="myResourceGroup",
    security_profile=azure_native.compute.SecurityProfileResponseArgs(
        security_type="ConfidentialVM",
        uefi_settings=azure_native.compute.UefiSettingsArgs(
            secure_boot_enabled=True,
            v_tpm_enabled=True,
        ),
    ),
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="2019-datacenter-cvm",
            publisher="MicrosoftWindowsServer",
            sku="windows-cvm",
            version="17763.2183.2109130127",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_ONLY,
            "createOption": "FromImage",
            "managedDisk": {
                "securityProfile": azure_native.compute.VMDiskSecurityProfileArgs(
                    security_encryption_type="DiskWithVMGuestState",
                ),
                "storageAccountType": "StandardSSD_LRS",
            },
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      hardwareProfile:
        vmSize: Standard_DC2as_v5
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
      resourceGroupName: myResourceGroup
      securityProfile:
        securityType: ConfidentialVM
        uefiSettings:
          secureBootEnabled: true
          vTpmEnabled: true
      storageProfile:
        imageReference:
          offer: 2019-datacenter-cvm
          publisher: MicrosoftWindowsServer
          sku: windows-cvm
          version: 17763.2183.2109130127
        osDisk:
          caching: ReadOnly
          createOption: FromImage
          managedDisk:
            securityProfile:
              securityEncryptionType: DiskWithVMGuestState
            storageAccountType: StandardSSD_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a Windows vm with a patch setting assessmentMode of ImageDefault.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D1_v2",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
            WindowsConfiguration = new AzureNative.Compute.Inputs.WindowsConfigurationArgs
            {
                EnableAutomaticUpdates = true,
                PatchSettings = new AzureNative.Compute.Inputs.PatchSettingsArgs
                {
                    AssessmentMode = "ImageDefault",
                },
                ProvisionVMAgent = true,
            },
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "WindowsServer",
                Publisher = "MicrosoftWindowsServer",
                Sku = "2016-Datacenter",
                Version = "latest",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Premium_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .hardwareProfile(Map.of("vmSize", "Standard_D1_v2"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM"),
                Map.entry("windowsConfiguration", Map.ofEntries(
                    Map.entry("enableAutomaticUpdates", true),
                    Map.entry("patchSettings", Map.of("assessmentMode", "ImageDefault")),
                    Map.entry("provisionVMAgent", true)
                ))
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "WindowsServer"),
                    Map.entry("publisher", "MicrosoftWindowsServer"),
                    Map.entry("sku", "2016-Datacenter"),
                    Map.entry("version", "latest")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadWrite"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Premium_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    hardwareProfile: {
        vmSize: "Standard_D1_v2",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
        windowsConfiguration: {
            enableAutomaticUpdates: true,
            patchSettings: {
                assessmentMode: "ImageDefault",
            },
            provisionVMAgent: true,
        },
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        imageReference: {
            offer: "WindowsServer",
            publisher: "MicrosoftWindowsServer",
            sku: "2016-Datacenter",
            version: "latest",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadWrite,
            createOption: "FromImage",
            managedDisk: {
                storageAccountType: "Premium_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_D1_v2",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileResponseArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
        windows_configuration={
            "enableAutomaticUpdates": True,
            "patchSettings": azure_native.compute.PatchSettingsArgs(
                assessment_mode="ImageDefault",
            ),
            "provisionVMAgent": True,
        },
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="WindowsServer",
            publisher="MicrosoftWindowsServer",
            sku="2016-Datacenter",
            version="latest",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_WRITE,
            "createOption": "FromImage",
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Premium_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      hardwareProfile:
        vmSize: Standard_D1_v2
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
        windowsConfiguration:
          enableAutomaticUpdates: true
          patchSettings:
            assessmentMode: ImageDefault
          provisionVMAgent: true
      resourceGroupName: myResourceGroup
      storageProfile:
        imageReference:
          offer: WindowsServer
          publisher: MicrosoftWindowsServer
          sku: 2016-Datacenter
          version: latest
        osDisk:
          caching: ReadWrite
          createOption: FromImage
          managedDisk:
            storageAccountType: Premium_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a Windows vm with a patch setting patchMode of AutomaticByOS.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D1_v2",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/nsgExistingNic",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
            WindowsConfiguration = new AzureNative.Compute.Inputs.WindowsConfigurationArgs
            {
                EnableAutomaticUpdates = true,
                PatchSettings = new AzureNative.Compute.Inputs.PatchSettingsArgs
                {
                    PatchMode = "AutomaticByOS",
                },
                ProvisionVMAgent = true,
            },
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "WindowsServer",
                Publisher = "MicrosoftWindowsServer",
                Sku = "2016-Datacenter",
                Version = "latest",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Premium_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .hardwareProfile(Map.of("vmSize", "Standard_D1_v2"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/nsgExistingNic"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM"),
                Map.entry("windowsConfiguration", Map.ofEntries(
                    Map.entry("enableAutomaticUpdates", true),
                    Map.entry("patchSettings", Map.of("patchMode", "AutomaticByOS")),
                    Map.entry("provisionVMAgent", true)
                ))
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "WindowsServer"),
                    Map.entry("publisher", "MicrosoftWindowsServer"),
                    Map.entry("sku", "2016-Datacenter"),
                    Map.entry("version", "latest")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadWrite"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Premium_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    hardwareProfile: {
        vmSize: "Standard_D1_v2",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/nsgExistingNic",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
        windowsConfiguration: {
            enableAutomaticUpdates: true,
            patchSettings: {
                patchMode: "AutomaticByOS",
            },
            provisionVMAgent: true,
        },
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        imageReference: {
            offer: "WindowsServer",
            publisher: "MicrosoftWindowsServer",
            sku: "2016-Datacenter",
            version: "latest",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadWrite,
            createOption: "FromImage",
            managedDisk: {
                storageAccountType: "Premium_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_D1_v2",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/nsgExistingNic",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileResponseArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
        windows_configuration={
            "enableAutomaticUpdates": True,
            "patchSettings": azure_native.compute.PatchSettingsArgs(
                patch_mode="AutomaticByOS",
            ),
            "provisionVMAgent": True,
        },
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="WindowsServer",
            publisher="MicrosoftWindowsServer",
            sku="2016-Datacenter",
            version="latest",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_WRITE,
            "createOption": "FromImage",
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Premium_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      hardwareProfile:
        vmSize: Standard_D1_v2
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/nsgExistingNic
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
        windowsConfiguration:
          enableAutomaticUpdates: true
          patchSettings:
            patchMode: AutomaticByOS
          provisionVMAgent: true
      resourceGroupName: myResourceGroup
      storageProfile:
        imageReference:
          offer: WindowsServer
          publisher: MicrosoftWindowsServer
          sku: 2016-Datacenter
          version: latest
        osDisk:
          caching: ReadWrite
          createOption: FromImage
          managedDisk:
            storageAccountType: Premium_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a Windows vm with a patch setting patchMode of AutomaticByPlatform and AutomaticByPlatformSettings.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D1_v2",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
            WindowsConfiguration = new AzureNative.Compute.Inputs.WindowsConfigurationArgs
            {
                EnableAutomaticUpdates = true,
                PatchSettings = new AzureNative.Compute.Inputs.PatchSettingsArgs
                {
                    AssessmentMode = "AutomaticByPlatform",
                    AutomaticByPlatformSettings = new AzureNative.Compute.Inputs.WindowsVMGuestPatchAutomaticByPlatformSettingsArgs
                    {
                        RebootSetting = "Never",
                    },
                    PatchMode = "AutomaticByPlatform",
                },
                ProvisionVMAgent = true,
            },
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "WindowsServer",
                Publisher = "MicrosoftWindowsServer",
                Sku = "2016-Datacenter",
                Version = "latest",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Premium_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .hardwareProfile(Map.of("vmSize", "Standard_D1_v2"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM"),
                Map.entry("windowsConfiguration", Map.ofEntries(
                    Map.entry("enableAutomaticUpdates", true),
                    Map.entry("patchSettings", Map.ofEntries(
                        Map.entry("assessmentMode", "AutomaticByPlatform"),
                        Map.entry("automaticByPlatformSettings", Map.of("rebootSetting", "Never")),
                        Map.entry("patchMode", "AutomaticByPlatform")
                    )),
                    Map.entry("provisionVMAgent", true)
                ))
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "WindowsServer"),
                    Map.entry("publisher", "MicrosoftWindowsServer"),
                    Map.entry("sku", "2016-Datacenter"),
                    Map.entry("version", "latest")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadWrite"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Premium_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    hardwareProfile: {
        vmSize: "Standard_D1_v2",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
        windowsConfiguration: {
            enableAutomaticUpdates: true,
            patchSettings: {
                assessmentMode: "AutomaticByPlatform",
                automaticByPlatformSettings: {
                    rebootSetting: "Never",
                },
                patchMode: "AutomaticByPlatform",
            },
            provisionVMAgent: true,
        },
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        imageReference: {
            offer: "WindowsServer",
            publisher: "MicrosoftWindowsServer",
            sku: "2016-Datacenter",
            version: "latest",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadWrite,
            createOption: "FromImage",
            managedDisk: {
                storageAccountType: "Premium_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_D1_v2",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileResponseArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
        windows_configuration={
            "enableAutomaticUpdates": True,
            "patchSettings": {
                "assessmentMode": "AutomaticByPlatform",
                "automaticByPlatformSettings": azure_native.compute.WindowsVMGuestPatchAutomaticByPlatformSettingsArgs(
                    reboot_setting="Never",
                ),
                "patchMode": "AutomaticByPlatform",
            },
            "provisionVMAgent": True,
        },
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="WindowsServer",
            publisher="MicrosoftWindowsServer",
            sku="2016-Datacenter",
            version="latest",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_WRITE,
            "createOption": "FromImage",
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Premium_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      hardwareProfile:
        vmSize: Standard_D1_v2
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
        windowsConfiguration:
          enableAutomaticUpdates: true
          patchSettings:
            assessmentMode: AutomaticByPlatform
            automaticByPlatformSettings:
              rebootSetting: Never
            patchMode: AutomaticByPlatform
          provisionVMAgent: true
      resourceGroupName: myResourceGroup
      storageProfile:
        imageReference:
          offer: WindowsServer
          publisher: MicrosoftWindowsServer
          sku: 2016-Datacenter
          version: latest
        osDisk:
          caching: ReadWrite
          createOption: FromImage
          managedDisk:
            storageAccountType: Premium_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a Windows vm with a patch setting patchMode of AutomaticByPlatform and enableHotpatching set to true.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D1_v2",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
            WindowsConfiguration = new AzureNative.Compute.Inputs.WindowsConfigurationArgs
            {
                EnableAutomaticUpdates = true,
                PatchSettings = new AzureNative.Compute.Inputs.PatchSettingsArgs
                {
                    EnableHotpatching = true,
                    PatchMode = "AutomaticByPlatform",
                },
                ProvisionVMAgent = true,
            },
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "WindowsServer",
                Publisher = "MicrosoftWindowsServer",
                Sku = "2016-Datacenter",
                Version = "latest",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Premium_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .hardwareProfile(Map.of("vmSize", "Standard_D1_v2"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM"),
                Map.entry("windowsConfiguration", Map.ofEntries(
                    Map.entry("enableAutomaticUpdates", true),
                    Map.entry("patchSettings", Map.ofEntries(
                        Map.entry("enableHotpatching", true),
                        Map.entry("patchMode", "AutomaticByPlatform")
                    )),
                    Map.entry("provisionVMAgent", true)
                ))
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "WindowsServer"),
                    Map.entry("publisher", "MicrosoftWindowsServer"),
                    Map.entry("sku", "2016-Datacenter"),
                    Map.entry("version", "latest")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadWrite"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Premium_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    hardwareProfile: {
        vmSize: "Standard_D1_v2",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
        windowsConfiguration: {
            enableAutomaticUpdates: true,
            patchSettings: {
                enableHotpatching: true,
                patchMode: "AutomaticByPlatform",
            },
            provisionVMAgent: true,
        },
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        imageReference: {
            offer: "WindowsServer",
            publisher: "MicrosoftWindowsServer",
            sku: "2016-Datacenter",
            version: "latest",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadWrite,
            createOption: "FromImage",
            managedDisk: {
                storageAccountType: "Premium_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_D1_v2",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileResponseArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
        windows_configuration={
            "enableAutomaticUpdates": True,
            "patchSettings": azure_native.compute.PatchSettingsArgs(
                enable_hotpatching=True,
                patch_mode="AutomaticByPlatform",
            ),
            "provisionVMAgent": True,
        },
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="WindowsServer",
            publisher="MicrosoftWindowsServer",
            sku="2016-Datacenter",
            version="latest",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_WRITE,
            "createOption": "FromImage",
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Premium_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      hardwareProfile:
        vmSize: Standard_D1_v2
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
        windowsConfiguration:
          enableAutomaticUpdates: true
          patchSettings:
            enableHotpatching: true
            patchMode: AutomaticByPlatform
          provisionVMAgent: true
      resourceGroupName: myResourceGroup
      storageProfile:
        imageReference:
          offer: WindowsServer
          publisher: MicrosoftWindowsServer
          sku: 2016-Datacenter
          version: latest
        osDisk:
          caching: ReadWrite
          createOption: FromImage
          managedDisk:
            storageAccountType: Premium_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a Windows vm with a patch setting patchMode of Manual.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D1_v2",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
            WindowsConfiguration = new AzureNative.Compute.Inputs.WindowsConfigurationArgs
            {
                EnableAutomaticUpdates = true,
                PatchSettings = new AzureNative.Compute.Inputs.PatchSettingsArgs
                {
                    PatchMode = "Manual",
                },
                ProvisionVMAgent = true,
            },
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "WindowsServer",
                Publisher = "MicrosoftWindowsServer",
                Sku = "2016-Datacenter",
                Version = "latest",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Premium_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .hardwareProfile(Map.of("vmSize", "Standard_D1_v2"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM"),
                Map.entry("windowsConfiguration", Map.ofEntries(
                    Map.entry("enableAutomaticUpdates", true),
                    Map.entry("patchSettings", Map.of("patchMode", "Manual")),
                    Map.entry("provisionVMAgent", true)
                ))
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "WindowsServer"),
                    Map.entry("publisher", "MicrosoftWindowsServer"),
                    Map.entry("sku", "2016-Datacenter"),
                    Map.entry("version", "latest")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadWrite"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Premium_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    hardwareProfile: {
        vmSize: "Standard_D1_v2",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
        windowsConfiguration: {
            enableAutomaticUpdates: true,
            patchSettings: {
                patchMode: "Manual",
            },
            provisionVMAgent: true,
        },
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        imageReference: {
            offer: "WindowsServer",
            publisher: "MicrosoftWindowsServer",
            sku: "2016-Datacenter",
            version: "latest",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadWrite,
            createOption: "FromImage",
            managedDisk: {
                storageAccountType: "Premium_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_D1_v2",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileResponseArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
        windows_configuration={
            "enableAutomaticUpdates": True,
            "patchSettings": azure_native.compute.PatchSettingsArgs(
                patch_mode="Manual",
            ),
            "provisionVMAgent": True,
        },
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="WindowsServer",
            publisher="MicrosoftWindowsServer",
            sku="2016-Datacenter",
            version="latest",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_WRITE,
            "createOption": "FromImage",
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Premium_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      hardwareProfile:
        vmSize: Standard_D1_v2
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
        windowsConfiguration:
          enableAutomaticUpdates: true
          patchSettings:
            patchMode: Manual
          provisionVMAgent: true
      resourceGroupName: myResourceGroup
      storageProfile:
        imageReference:
          offer: WindowsServer
          publisher: MicrosoftWindowsServer
          sku: 2016-Datacenter
          version: latest
        osDisk:
          caching: ReadWrite
          createOption: FromImage
          managedDisk:
            storageAccountType: Premium_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a Windows vm with patch settings patchMode and assessmentMode set to AutomaticByPlatform.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D1_v2",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
            WindowsConfiguration = new AzureNative.Compute.Inputs.WindowsConfigurationArgs
            {
                EnableAutomaticUpdates = true,
                PatchSettings = new AzureNative.Compute.Inputs.PatchSettingsArgs
                {
                    AssessmentMode = "AutomaticByPlatform",
                    PatchMode = "AutomaticByPlatform",
                },
                ProvisionVMAgent = true,
            },
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "WindowsServer",
                Publisher = "MicrosoftWindowsServer",
                Sku = "2016-Datacenter",
                Version = "latest",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Premium_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .hardwareProfile(Map.of("vmSize", "Standard_D1_v2"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM"),
                Map.entry("windowsConfiguration", Map.ofEntries(
                    Map.entry("enableAutomaticUpdates", true),
                    Map.entry("patchSettings", Map.ofEntries(
                        Map.entry("assessmentMode", "AutomaticByPlatform"),
                        Map.entry("patchMode", "AutomaticByPlatform")
                    )),
                    Map.entry("provisionVMAgent", true)
                ))
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "WindowsServer"),
                    Map.entry("publisher", "MicrosoftWindowsServer"),
                    Map.entry("sku", "2016-Datacenter"),
                    Map.entry("version", "latest")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadWrite"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Premium_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    hardwareProfile: {
        vmSize: "Standard_D1_v2",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
        windowsConfiguration: {
            enableAutomaticUpdates: true,
            patchSettings: {
                assessmentMode: "AutomaticByPlatform",
                patchMode: "AutomaticByPlatform",
            },
            provisionVMAgent: true,
        },
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        imageReference: {
            offer: "WindowsServer",
            publisher: "MicrosoftWindowsServer",
            sku: "2016-Datacenter",
            version: "latest",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadWrite,
            createOption: "FromImage",
            managedDisk: {
                storageAccountType: "Premium_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_D1_v2",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileResponseArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
        windows_configuration={
            "enableAutomaticUpdates": True,
            "patchSettings": azure_native.compute.PatchSettingsArgs(
                assessment_mode="AutomaticByPlatform",
                patch_mode="AutomaticByPlatform",
            ),
            "provisionVMAgent": True,
        },
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="WindowsServer",
            publisher="MicrosoftWindowsServer",
            sku="2016-Datacenter",
            version="latest",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_WRITE,
            "createOption": "FromImage",
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Premium_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      hardwareProfile:
        vmSize: Standard_D1_v2
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
        windowsConfiguration:
          enableAutomaticUpdates: true
          patchSettings:
            assessmentMode: AutomaticByPlatform
            patchMode: AutomaticByPlatform
          provisionVMAgent: true
      resourceGroupName: myResourceGroup
      storageProfile:
        imageReference:
          offer: WindowsServer
          publisher: MicrosoftWindowsServer
          sku: 2016-Datacenter
          version: latest
        osDisk:
          caching: ReadWrite
          createOption: FromImage
          managedDisk:
            storageAccountType: Premium_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a custom-image vm from an unmanaged generalized os image.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D1_v2",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                CreateOption = "FromImage",
                Image = new AzureNative.Compute.Inputs.VirtualHardDiskArgs
                {
                    Uri = "http://{existing-storage-account-name}.blob.core.windows.net/{existing-container-name}/{existing-generalized-os-image-blob-name}.vhd",
                },
                Name = "myVMosdisk",
                OsType = AzureNative.Compute.OperatingSystemTypes.Windows,
                Vhd = new AzureNative.Compute.Inputs.VirtualHardDiskArgs
                {
                    Uri = "http://{existing-storage-account-name}.blob.core.windows.net/{existing-container-name}/myDisk.vhd",
                },
            },
        },
        VmName = "{vm-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .hardwareProfile(Map.of("vmSize", "Standard_D1_v2"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM")
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.of("osDisk", Map.ofEntries(
                Map.entry("caching", "ReadWrite"),
                Map.entry("createOption", "FromImage"),
                Map.entry("image", Map.of("uri", "http://{existing-storage-account-name}.blob.core.windows.net/{existing-container-name}/{existing-generalized-os-image-blob-name}.vhd")),
                Map.entry("name", "myVMosdisk"),
                Map.entry("osType", "Windows"),
                Map.entry("vhd", Map.of("uri", "http://{existing-storage-account-name}.blob.core.windows.net/{existing-container-name}/myDisk.vhd"))
            )))
            .vmName("{vm-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    hardwareProfile: {
        vmSize: "Standard_D1_v2",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadWrite,
            createOption: "FromImage",
            image: {
                uri: "http://{existing-storage-account-name}.blob.core.windows.net/{existing-container-name}/{existing-generalized-os-image-blob-name}.vhd",
            },
            name: "myVMosdisk",
            osType: azure_native.compute.OperatingSystemTypes.Windows,
            vhd: {
                uri: "http://{existing-storage-account-name}.blob.core.windows.net/{existing-container-name}/myDisk.vhd",
            },
        },
    },
    vmName: "{vm-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_D1_v2",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_WRITE,
            "createOption": "FromImage",
            "image": azure_native.compute.VirtualHardDiskArgs(
                uri="http://{existing-storage-account-name}.blob.core.windows.net/{existing-container-name}/{existing-generalized-os-image-blob-name}.vhd",
            ),
            "name": "myVMosdisk",
            "osType": azure_native.compute.OperatingSystemTypes.WINDOWS,
            "vhd": azure_native.compute.VirtualHardDiskArgs(
                uri="http://{existing-storage-account-name}.blob.core.windows.net/{existing-container-name}/myDisk.vhd",
            ),
        },
    ),
    vm_name="{vm-name}")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      hardwareProfile:
        vmSize: Standard_D1_v2
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
      resourceGroupName: myResourceGroup
      storageProfile:
        osDisk:
          caching: ReadWrite
          createOption: FromImage
          image:
            uri: http://{existing-storage-account-name}.blob.core.windows.net/{existing-container-name}/{existing-generalized-os-image-blob-name}.vhd
          name: myVMosdisk
          osType: Windows
          vhd:
            uri: http://{existing-storage-account-name}.blob.core.windows.net/{existing-container-name}/myDisk.vhd
      vmName: '{vm-name}'

```

{{% /example %}}
{{% example %}}
### Create a platform-image vm with unmanaged os and data disks.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D2_v2",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            DataDisks = new[]
            {
                new AzureNative.Compute.Inputs.DataDiskArgs
                {
                    CreateOption = "Empty",
                    DiskSizeGB = 1023,
                    Lun = 0,
                    Vhd = new AzureNative.Compute.Inputs.VirtualHardDiskArgs
                    {
                        Uri = "http://{existing-storage-account-name}.blob.core.windows.net/{existing-container-name}/myDisk0.vhd",
                    },
                },
                new AzureNative.Compute.Inputs.DataDiskArgs
                {
                    CreateOption = "Empty",
                    DiskSizeGB = 1023,
                    Lun = 1,
                    Vhd = new AzureNative.Compute.Inputs.VirtualHardDiskArgs
                    {
                        Uri = "http://{existing-storage-account-name}.blob.core.windows.net/{existing-container-name}/myDisk1.vhd",
                    },
                },
            },
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "WindowsServer",
                Publisher = "MicrosoftWindowsServer",
                Sku = "2016-Datacenter",
                Version = "latest",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                CreateOption = "FromImage",
                Name = "myVMosdisk",
                Vhd = new AzureNative.Compute.Inputs.VirtualHardDiskArgs
                {
                    Uri = "http://{existing-storage-account-name}.blob.core.windows.net/{existing-container-name}/myDisk.vhd",
                },
            },
        },
        VmName = "{vm-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .hardwareProfile(Map.of("vmSize", "Standard_D2_v2"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM")
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("dataDisks",                 
                    Map.ofEntries(
                        Map.entry("createOption", "Empty"),
                        Map.entry("diskSizeGB", 1023),
                        Map.entry("lun", 0),
                        Map.entry("vhd", Map.of("uri", "http://{existing-storage-account-name}.blob.core.windows.net/{existing-container-name}/myDisk0.vhd"))
                    ),
                    Map.ofEntries(
                        Map.entry("createOption", "Empty"),
                        Map.entry("diskSizeGB", 1023),
                        Map.entry("lun", 1),
                        Map.entry("vhd", Map.of("uri", "http://{existing-storage-account-name}.blob.core.windows.net/{existing-container-name}/myDisk1.vhd"))
                    )),
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "WindowsServer"),
                    Map.entry("publisher", "MicrosoftWindowsServer"),
                    Map.entry("sku", "2016-Datacenter"),
                    Map.entry("version", "latest")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadWrite"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("name", "myVMosdisk"),
                    Map.entry("vhd", Map.of("uri", "http://{existing-storage-account-name}.blob.core.windows.net/{existing-container-name}/myDisk.vhd"))
                ))
            ))
            .vmName("{vm-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    hardwareProfile: {
        vmSize: "Standard_D2_v2",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        dataDisks: [
            {
                createOption: "Empty",
                diskSizeGB: 1023,
                lun: 0,
                vhd: {
                    uri: "http://{existing-storage-account-name}.blob.core.windows.net/{existing-container-name}/myDisk0.vhd",
                },
            },
            {
                createOption: "Empty",
                diskSizeGB: 1023,
                lun: 1,
                vhd: {
                    uri: "http://{existing-storage-account-name}.blob.core.windows.net/{existing-container-name}/myDisk1.vhd",
                },
            },
        ],
        imageReference: {
            offer: "WindowsServer",
            publisher: "MicrosoftWindowsServer",
            sku: "2016-Datacenter",
            version: "latest",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadWrite,
            createOption: "FromImage",
            name: "myVMosdisk",
            vhd: {
                uri: "http://{existing-storage-account-name}.blob.core.windows.net/{existing-container-name}/myDisk.vhd",
            },
        },
    },
    vmName: "{vm-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_D2_v2",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        data_disks=[
            {
                "createOption": "Empty",
                "diskSizeGB": 1023,
                "lun": 0,
                "vhd": azure_native.compute.VirtualHardDiskArgs(
                    uri="http://{existing-storage-account-name}.blob.core.windows.net/{existing-container-name}/myDisk0.vhd",
                ),
            },
            {
                "createOption": "Empty",
                "diskSizeGB": 1023,
                "lun": 1,
                "vhd": azure_native.compute.VirtualHardDiskArgs(
                    uri="http://{existing-storage-account-name}.blob.core.windows.net/{existing-container-name}/myDisk1.vhd",
                ),
            },
        ],
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="WindowsServer",
            publisher="MicrosoftWindowsServer",
            sku="2016-Datacenter",
            version="latest",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_WRITE,
            "createOption": "FromImage",
            "name": "myVMosdisk",
            "vhd": azure_native.compute.VirtualHardDiskArgs(
                uri="http://{existing-storage-account-name}.blob.core.windows.net/{existing-container-name}/myDisk.vhd",
            ),
        },
    ),
    vm_name="{vm-name}")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      hardwareProfile:
        vmSize: Standard_D2_v2
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
      resourceGroupName: myResourceGroup
      storageProfile:
        dataDisks:
          - createOption: Empty
            diskSizeGB: 1023
            lun: 0
            vhd:
              uri: http://{existing-storage-account-name}.blob.core.windows.net/{existing-container-name}/myDisk0.vhd
          - createOption: Empty
            diskSizeGB: 1023
            lun: 1
            vhd:
              uri: http://{existing-storage-account-name}.blob.core.windows.net/{existing-container-name}/myDisk1.vhd
        imageReference:
          offer: WindowsServer
          publisher: MicrosoftWindowsServer
          sku: 2016-Datacenter
          version: latest
        osDisk:
          caching: ReadWrite
          createOption: FromImage
          name: myVMosdisk
          vhd:
            uri: http://{existing-storage-account-name}.blob.core.windows.net/{existing-container-name}/myDisk.vhd
      vmName: '{vm-name}'

```

{{% /example %}}
{{% example %}}
### Create a vm from a custom image.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D1_v2",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/images/{existing-custom-image-name}",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Standard_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .hardwareProfile(Map.of("vmSize", "Standard_D1_v2"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM")
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/images/{existing-custom-image-name}")),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadWrite"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    hardwareProfile: {
        vmSize: "Standard_D1_v2",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        imageReference: {
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/images/{existing-custom-image-name}",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadWrite,
            createOption: "FromImage",
            managedDisk: {
                storageAccountType: "Standard_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_D1_v2",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/images/{existing-custom-image-name}",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_WRITE,
            "createOption": "FromImage",
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Standard_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      hardwareProfile:
        vmSize: Standard_D1_v2
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
      resourceGroupName: myResourceGroup
      storageProfile:
        imageReference:
          id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/images/{existing-custom-image-name}
        osDisk:
          caching: ReadWrite
          createOption: FromImage
          managedDisk:
            storageAccountType: Standard_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a vm from a generalized shared image.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D1_v2",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/galleries/mySharedGallery/images/mySharedImage",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Standard_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .hardwareProfile(Map.of("vmSize", "Standard_D1_v2"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM")
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/galleries/mySharedGallery/images/mySharedImage")),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadWrite"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    hardwareProfile: {
        vmSize: "Standard_D1_v2",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        imageReference: {
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/galleries/mySharedGallery/images/mySharedImage",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadWrite,
            createOption: "FromImage",
            managedDisk: {
                storageAccountType: "Standard_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_D1_v2",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/galleries/mySharedGallery/images/mySharedImage",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_WRITE,
            "createOption": "FromImage",
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Standard_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      hardwareProfile:
        vmSize: Standard_D1_v2
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
      resourceGroupName: myResourceGroup
      storageProfile:
        imageReference:
          id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/galleries/mySharedGallery/images/mySharedImage
        osDisk:
          caching: ReadWrite
          createOption: FromImage
          managedDisk:
            storageAccountType: Standard_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a vm from a specialized shared image.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D1_v2",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/galleries/mySharedGallery/images/mySharedImage",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Standard_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .hardwareProfile(Map.of("vmSize", "Standard_D1_v2"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/galleries/mySharedGallery/images/mySharedImage")),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadWrite"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    hardwareProfile: {
        vmSize: "Standard_D1_v2",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        imageReference: {
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/galleries/mySharedGallery/images/mySharedImage",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadWrite,
            createOption: "FromImage",
            managedDisk: {
                storageAccountType: "Standard_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_D1_v2",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/galleries/mySharedGallery/images/mySharedImage",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_WRITE,
            "createOption": "FromImage",
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Standard_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      hardwareProfile:
        vmSize: Standard_D1_v2
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      resourceGroupName: myResourceGroup
      storageProfile:
        imageReference:
          id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/galleries/mySharedGallery/images/mySharedImage
        osDisk:
          caching: ReadWrite
          createOption: FromImage
          managedDisk:
            storageAccountType: Standard_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a vm in a Virtual Machine Scale Set with customer assigned platformFaultDomain.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D1_v2",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
        },
        PlatformFaultDomain = 1,
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "WindowsServer",
                Publisher = "MicrosoftWindowsServer",
                Sku = "2016-Datacenter",
                Version = "latest",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Standard_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VirtualMachineScaleSet = new AzureNative.Compute.Inputs.SubResourceArgs
        {
            Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/virtualMachineScaleSets/{existing-flex-vmss-name-with-platformFaultDomainCount-greater-than-1}",
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .hardwareProfile(Map.of("vmSize", "Standard_D1_v2"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM")
            ))
            .platformFaultDomain(1)
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "WindowsServer"),
                    Map.entry("publisher", "MicrosoftWindowsServer"),
                    Map.entry("sku", "2016-Datacenter"),
                    Map.entry("version", "latest")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadWrite"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .virtualMachineScaleSet(Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/virtualMachineScaleSets/{existing-flex-vmss-name-with-platformFaultDomainCount-greater-than-1}"))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    hardwareProfile: {
        vmSize: "Standard_D1_v2",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
    },
    platformFaultDomain: 1,
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        imageReference: {
            offer: "WindowsServer",
            publisher: "MicrosoftWindowsServer",
            sku: "2016-Datacenter",
            version: "latest",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadWrite,
            createOption: "FromImage",
            managedDisk: {
                storageAccountType: "Standard_LRS",
            },
            name: "myVMosdisk",
        },
    },
    virtualMachineScaleSet: {
        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/virtualMachineScaleSets/{existing-flex-vmss-name-with-platformFaultDomainCount-greater-than-1}",
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_D1_v2",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
    ),
    platform_fault_domain=1,
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="WindowsServer",
            publisher="MicrosoftWindowsServer",
            sku="2016-Datacenter",
            version="latest",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_WRITE,
            "createOption": "FromImage",
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Standard_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    virtual_machine_scale_set=azure_native.compute.SubResourceArgs(
        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/virtualMachineScaleSets/{existing-flex-vmss-name-with-platformFaultDomainCount-greater-than-1}",
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      hardwareProfile:
        vmSize: Standard_D1_v2
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
      platformFaultDomain: 1
      resourceGroupName: myResourceGroup
      storageProfile:
        imageReference:
          offer: WindowsServer
          publisher: MicrosoftWindowsServer
          sku: 2016-Datacenter
          version: latest
        osDisk:
          caching: ReadWrite
          createOption: FromImage
          managedDisk:
            storageAccountType: Standard_LRS
          name: myVMosdisk
      virtualMachineScaleSet:
        id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/virtualMachineScaleSets/{existing-flex-vmss-name-with-platformFaultDomainCount-greater-than-1}
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a vm in an availability set.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        AvailabilitySet = new AzureNative.Compute.Inputs.SubResourceArgs
        {
            Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/availabilitySets/{existing-availability-set-name}",
        },
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D1_v2",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "WindowsServer",
                Publisher = "MicrosoftWindowsServer",
                Sku = "2016-Datacenter",
                Version = "latest",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Standard_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .availabilitySet(Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/availabilitySets/{existing-availability-set-name}"))
            .hardwareProfile(Map.of("vmSize", "Standard_D1_v2"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM")
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "WindowsServer"),
                    Map.entry("publisher", "MicrosoftWindowsServer"),
                    Map.entry("sku", "2016-Datacenter"),
                    Map.entry("version", "latest")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadWrite"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    availabilitySet: {
        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/availabilitySets/{existing-availability-set-name}",
    },
    hardwareProfile: {
        vmSize: "Standard_D1_v2",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        imageReference: {
            offer: "WindowsServer",
            publisher: "MicrosoftWindowsServer",
            sku: "2016-Datacenter",
            version: "latest",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadWrite,
            createOption: "FromImage",
            managedDisk: {
                storageAccountType: "Standard_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    availability_set=azure_native.compute.SubResourceArgs(
        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/availabilitySets/{existing-availability-set-name}",
    ),
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_D1_v2",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="WindowsServer",
            publisher="MicrosoftWindowsServer",
            sku="2016-Datacenter",
            version="latest",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_WRITE,
            "createOption": "FromImage",
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Standard_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      availabilitySet:
        id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/availabilitySets/{existing-availability-set-name}
      hardwareProfile:
        vmSize: Standard_D1_v2
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
      resourceGroupName: myResourceGroup
      storageProfile:
        imageReference:
          offer: WindowsServer
          publisher: MicrosoftWindowsServer
          sku: 2016-Datacenter
          version: latest
        osDisk:
          caching: ReadWrite
          createOption: FromImage
          managedDisk:
            storageAccountType: Standard_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a vm with Application Profile.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        ApplicationProfile = new AzureNative.Compute.Inputs.ApplicationProfileArgs
        {
            GalleryApplications = new[]
            {
                new AzureNative.Compute.Inputs.VMGalleryApplicationArgs
                {
                    ConfigurationReference = "https://mystorageaccount.blob.core.windows.net/configurations/settings.config",
                    EnableAutomaticUpgrade = false,
                    Order = 1,
                    PackageReferenceId = "/subscriptions/32c17a9e-aa7b-4ba5-a45b-e324116b6fdb/resourceGroups/myresourceGroupName2/providers/Microsoft.Compute/galleries/myGallery1/applications/MyApplication1/versions/1.0",
                    Tags = "myTag1",
                    TreatFailureAsDeploymentFailure = false,
                },
                new AzureNative.Compute.Inputs.VMGalleryApplicationArgs
                {
                    PackageReferenceId = "/subscriptions/32c17a9e-aa7b-4ba5-a45b-e324116b6fdg/resourceGroups/myresourceGroupName3/providers/Microsoft.Compute/galleries/myGallery2/applications/MyApplication2/versions/1.1",
                },
            },
        },
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D1_v2",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "{image_offer}",
                Publisher = "{image_publisher}",
                Sku = "{image_sku}",
                Version = "latest",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Standard_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .applicationProfile(Map.of("galleryApplications",             
                Map.ofEntries(
                    Map.entry("configurationReference", "https://mystorageaccount.blob.core.windows.net/configurations/settings.config"),
                    Map.entry("enableAutomaticUpgrade", false),
                    Map.entry("order", 1),
                    Map.entry("packageReferenceId", "/subscriptions/32c17a9e-aa7b-4ba5-a45b-e324116b6fdb/resourceGroups/myresourceGroupName2/providers/Microsoft.Compute/galleries/myGallery1/applications/MyApplication1/versions/1.0"),
                    Map.entry("tags", "myTag1"),
                    Map.entry("treatFailureAsDeploymentFailure", false)
                ),
                Map.of("packageReferenceId", "/subscriptions/32c17a9e-aa7b-4ba5-a45b-e324116b6fdg/resourceGroups/myresourceGroupName3/providers/Microsoft.Compute/galleries/myGallery2/applications/MyApplication2/versions/1.1")))
            .hardwareProfile(Map.of("vmSize", "Standard_D1_v2"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM")
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "{image_offer}"),
                    Map.entry("publisher", "{image_publisher}"),
                    Map.entry("sku", "{image_sku}"),
                    Map.entry("version", "latest")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadWrite"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    applicationProfile: {
        galleryApplications: [
            {
                configurationReference: "https://mystorageaccount.blob.core.windows.net/configurations/settings.config",
                enableAutomaticUpgrade: false,
                order: 1,
                packageReferenceId: "/subscriptions/32c17a9e-aa7b-4ba5-a45b-e324116b6fdb/resourceGroups/myresourceGroupName2/providers/Microsoft.Compute/galleries/myGallery1/applications/MyApplication1/versions/1.0",
                tags: "myTag1",
                treatFailureAsDeploymentFailure: false,
            },
            {
                packageReferenceId: "/subscriptions/32c17a9e-aa7b-4ba5-a45b-e324116b6fdg/resourceGroups/myresourceGroupName3/providers/Microsoft.Compute/galleries/myGallery2/applications/MyApplication2/versions/1.1",
            },
        ],
    },
    hardwareProfile: {
        vmSize: "Standard_D1_v2",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        imageReference: {
            offer: "{image_offer}",
            publisher: "{image_publisher}",
            sku: "{image_sku}",
            version: "latest",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadWrite,
            createOption: "FromImage",
            managedDisk: {
                storageAccountType: "Standard_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    application_profile=azure_native.compute.ApplicationProfileResponseArgs(
        gallery_applications=[
            azure_native.compute.VMGalleryApplicationArgs(
                configuration_reference="https://mystorageaccount.blob.core.windows.net/configurations/settings.config",
                enable_automatic_upgrade=False,
                order=1,
                package_reference_id="/subscriptions/32c17a9e-aa7b-4ba5-a45b-e324116b6fdb/resourceGroups/myresourceGroupName2/providers/Microsoft.Compute/galleries/myGallery1/applications/MyApplication1/versions/1.0",
                tags="myTag1",
                treat_failure_as_deployment_failure=False,
            ),
            azure_native.compute.VMGalleryApplicationArgs(
                package_reference_id="/subscriptions/32c17a9e-aa7b-4ba5-a45b-e324116b6fdg/resourceGroups/myresourceGroupName3/providers/Microsoft.Compute/galleries/myGallery2/applications/MyApplication2/versions/1.1",
            ),
        ],
    ),
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_D1_v2",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="{image_offer}",
            publisher="{image_publisher}",
            sku="{image_sku}",
            version="latest",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_WRITE,
            "createOption": "FromImage",
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Standard_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      applicationProfile:
        galleryApplications:
          - configurationReference: https://mystorageaccount.blob.core.windows.net/configurations/settings.config
            enableAutomaticUpgrade: false
            order: 1
            packageReferenceId: /subscriptions/32c17a9e-aa7b-4ba5-a45b-e324116b6fdb/resourceGroups/myresourceGroupName2/providers/Microsoft.Compute/galleries/myGallery1/applications/MyApplication1/versions/1.0
            tags: myTag1
            treatFailureAsDeploymentFailure: false
          - packageReferenceId: /subscriptions/32c17a9e-aa7b-4ba5-a45b-e324116b6fdg/resourceGroups/myresourceGroupName3/providers/Microsoft.Compute/galleries/myGallery2/applications/MyApplication2/versions/1.1
      hardwareProfile:
        vmSize: Standard_D1_v2
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
      resourceGroupName: myResourceGroup
      storageProfile:
        imageReference:
          offer: '{image_offer}'
          publisher: '{image_publisher}'
          sku: '{image_sku}'
          version: latest
        osDisk:
          caching: ReadWrite
          createOption: FromImage
          managedDisk:
            storageAccountType: Standard_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a vm with DiskEncryptionSet resource id in the os disk and data disk.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D1_v2",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            DataDisks = new[]
            {
                new AzureNative.Compute.Inputs.DataDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                    CreateOption = "Empty",
                    DiskSizeGB = 1023,
                    Lun = 0,
                    ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                    {
                        DiskEncryptionSet = new AzureNative.Compute.Inputs.DiskEncryptionSetParametersArgs
                        {
                            Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}",
                        },
                        StorageAccountType = "Standard_LRS",
                    },
                },
                new AzureNative.Compute.Inputs.DataDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                    CreateOption = "Attach",
                    DiskSizeGB = 1023,
                    Lun = 1,
                    ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                    {
                        DiskEncryptionSet = new AzureNative.Compute.Inputs.DiskEncryptionSetParametersArgs
                        {
                            Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}",
                        },
                        Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/{existing-managed-disk-name}",
                        StorageAccountType = "Standard_LRS",
                    },
                },
            },
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/images/{existing-custom-image-name}",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    DiskEncryptionSet = new AzureNative.Compute.Inputs.DiskEncryptionSetParametersArgs
                    {
                        Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}",
                    },
                    StorageAccountType = "Standard_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .hardwareProfile(Map.of("vmSize", "Standard_D1_v2"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM")
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("dataDisks",                 
                    Map.ofEntries(
                        Map.entry("caching", "ReadWrite"),
                        Map.entry("createOption", "Empty"),
                        Map.entry("diskSizeGB", 1023),
                        Map.entry("lun", 0),
                        Map.entry("managedDisk", Map.ofEntries(
                            Map.entry("diskEncryptionSet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}")),
                            Map.entry("storageAccountType", "Standard_LRS")
                        ))
                    ),
                    Map.ofEntries(
                        Map.entry("caching", "ReadWrite"),
                        Map.entry("createOption", "Attach"),
                        Map.entry("diskSizeGB", 1023),
                        Map.entry("lun", 1),
                        Map.entry("managedDisk", Map.ofEntries(
                            Map.entry("diskEncryptionSet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}")),
                            Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/{existing-managed-disk-name}"),
                            Map.entry("storageAccountType", "Standard_LRS")
                        ))
                    )),
                Map.entry("imageReference", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/images/{existing-custom-image-name}")),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadWrite"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.ofEntries(
                        Map.entry("diskEncryptionSet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}")),
                        Map.entry("storageAccountType", "Standard_LRS")
                    )),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    hardwareProfile: {
        vmSize: "Standard_D1_v2",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        dataDisks: [
            {
                caching: azure_native.compute.CachingTypes.ReadWrite,
                createOption: "Empty",
                diskSizeGB: 1023,
                lun: 0,
                managedDisk: {
                    diskEncryptionSet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}",
                    },
                    storageAccountType: "Standard_LRS",
                },
            },
            {
                caching: azure_native.compute.CachingTypes.ReadWrite,
                createOption: "Attach",
                diskSizeGB: 1023,
                lun: 1,
                managedDisk: {
                    diskEncryptionSet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}",
                    },
                    id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/{existing-managed-disk-name}",
                    storageAccountType: "Standard_LRS",
                },
            },
        ],
        imageReference: {
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/images/{existing-custom-image-name}",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadWrite,
            createOption: "FromImage",
            managedDisk: {
                diskEncryptionSet: {
                    id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}",
                },
                storageAccountType: "Standard_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_D1_v2",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        data_disks=[
            {
                "caching": azure_native.compute.CachingTypes.READ_WRITE,
                "createOption": "Empty",
                "diskSizeGB": 1023,
                "lun": 0,
                "managedDisk": {
                    "diskEncryptionSet": azure_native.compute.DiskEncryptionSetParametersArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}",
                    ),
                    "storageAccountType": "Standard_LRS",
                },
            },
            {
                "caching": azure_native.compute.CachingTypes.READ_WRITE,
                "createOption": "Attach",
                "diskSizeGB": 1023,
                "lun": 1,
                "managedDisk": {
                    "diskEncryptionSet": azure_native.compute.DiskEncryptionSetParametersArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}",
                    ),
                    "id": "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/{existing-managed-disk-name}",
                    "storageAccountType": "Standard_LRS",
                },
            },
        ],
        image_reference=azure_native.compute.ImageReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/images/{existing-custom-image-name}",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_WRITE,
            "createOption": "FromImage",
            "managedDisk": {
                "diskEncryptionSet": azure_native.compute.DiskEncryptionSetParametersArgs(
                    id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}",
                ),
                "storageAccountType": "Standard_LRS",
            },
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      hardwareProfile:
        vmSize: Standard_D1_v2
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
      resourceGroupName: myResourceGroup
      storageProfile:
        dataDisks:
          - caching: ReadWrite
            createOption: Empty
            diskSizeGB: 1023
            lun: 0
            managedDisk:
              diskEncryptionSet:
                id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}
              storageAccountType: Standard_LRS
          - caching: ReadWrite
            createOption: Attach
            diskSizeGB: 1023
            lun: 1
            managedDisk:
              diskEncryptionSet:
                id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}
              id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/{existing-managed-disk-name}
              storageAccountType: Standard_LRS
        imageReference:
          id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/images/{existing-custom-image-name}
        osDisk:
          caching: ReadWrite
          createOption: FromImage
          managedDisk:
            diskEncryptionSet:
              id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}
            storageAccountType: Standard_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a vm with Host Encryption using encryptionAtHost property.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_DS1_v2",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
        },
        Plan = new AzureNative.Compute.Inputs.PlanArgs
        {
            Name = "windows2016",
            Product = "windows-data-science-vm",
            Publisher = "microsoft-ads",
        },
        ResourceGroupName = "myResourceGroup",
        SecurityProfile = new AzureNative.Compute.Inputs.SecurityProfileArgs
        {
            EncryptionAtHost = true,
        },
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "windows-data-science-vm",
                Publisher = "microsoft-ads",
                Sku = "windows2016",
                Version = "latest",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadOnly,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Standard_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .hardwareProfile(Map.of("vmSize", "Standard_DS1_v2"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM")
            ))
            .plan(Map.ofEntries(
                Map.entry("name", "windows2016"),
                Map.entry("product", "windows-data-science-vm"),
                Map.entry("publisher", "microsoft-ads")
            ))
            .resourceGroupName("myResourceGroup")
            .securityProfile(Map.of("encryptionAtHost", true))
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "windows-data-science-vm"),
                    Map.entry("publisher", "microsoft-ads"),
                    Map.entry("sku", "windows2016"),
                    Map.entry("version", "latest")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadOnly"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    hardwareProfile: {
        vmSize: "Standard_DS1_v2",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
    },
    plan: {
        name: "windows2016",
        product: "windows-data-science-vm",
        publisher: "microsoft-ads",
    },
    resourceGroupName: "myResourceGroup",
    securityProfile: {
        encryptionAtHost: true,
    },
    storageProfile: {
        imageReference: {
            offer: "windows-data-science-vm",
            publisher: "microsoft-ads",
            sku: "windows2016",
            version: "latest",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadOnly,
            createOption: "FromImage",
            managedDisk: {
                storageAccountType: "Standard_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_DS1_v2",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
    ),
    plan=azure_native.compute.PlanArgs(
        name="windows2016",
        product="windows-data-science-vm",
        publisher="microsoft-ads",
    ),
    resource_group_name="myResourceGroup",
    security_profile=azure_native.compute.SecurityProfileArgs(
        encryption_at_host=True,
    ),
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="windows-data-science-vm",
            publisher="microsoft-ads",
            sku="windows2016",
            version="latest",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_ONLY,
            "createOption": "FromImage",
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Standard_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      hardwareProfile:
        vmSize: Standard_DS1_v2
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
      plan:
        name: windows2016
        product: windows-data-science-vm
        publisher: microsoft-ads
      resourceGroupName: myResourceGroup
      securityProfile:
        encryptionAtHost: true
      storageProfile:
        imageReference:
          offer: windows-data-science-vm
          publisher: microsoft-ads
          sku: windows2016
          version: latest
        osDisk:
          caching: ReadOnly
          createOption: FromImage
          managedDisk:
            storageAccountType: Standard_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a vm with Scheduled Events Profile
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        DiagnosticsProfile = new AzureNative.Compute.Inputs.DiagnosticsProfileArgs
        {
            BootDiagnostics = new AzureNative.Compute.Inputs.BootDiagnosticsArgs
            {
                Enabled = true,
                StorageUri = "http://{existing-storage-account-name}.blob.core.windows.net",
            },
        },
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D1_v2",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
        },
        ResourceGroupName = "myResourceGroup",
        ScheduledEventsProfile = new AzureNative.Compute.Inputs.ScheduledEventsProfileArgs
        {
            OsImageNotificationProfile = new AzureNative.Compute.Inputs.OSImageNotificationProfileArgs
            {
                Enable = true,
                NotBeforeTimeout = "PT15M",
            },
            TerminateNotificationProfile = new AzureNative.Compute.Inputs.TerminateNotificationProfileArgs
            {
                Enable = true,
                NotBeforeTimeout = "PT10M",
            },
        },
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "WindowsServer",
                Publisher = "MicrosoftWindowsServer",
                Sku = "2016-Datacenter",
                Version = "latest",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Standard_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .diagnosticsProfile(Map.of("bootDiagnostics", Map.ofEntries(
                Map.entry("enabled", true),
                Map.entry("storageUri", "http://{existing-storage-account-name}.blob.core.windows.net")
            )))
            .hardwareProfile(Map.of("vmSize", "Standard_D1_v2"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM")
            ))
            .resourceGroupName("myResourceGroup")
            .scheduledEventsProfile(Map.ofEntries(
                Map.entry("osImageNotificationProfile", Map.ofEntries(
                    Map.entry("enable", true),
                    Map.entry("notBeforeTimeout", "PT15M")
                )),
                Map.entry("terminateNotificationProfile", Map.ofEntries(
                    Map.entry("enable", true),
                    Map.entry("notBeforeTimeout", "PT10M")
                ))
            ))
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "WindowsServer"),
                    Map.entry("publisher", "MicrosoftWindowsServer"),
                    Map.entry("sku", "2016-Datacenter"),
                    Map.entry("version", "latest")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadWrite"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    diagnosticsProfile: {
        bootDiagnostics: {
            enabled: true,
            storageUri: "http://{existing-storage-account-name}.blob.core.windows.net",
        },
    },
    hardwareProfile: {
        vmSize: "Standard_D1_v2",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
    },
    resourceGroupName: "myResourceGroup",
    scheduledEventsProfile: {
        osImageNotificationProfile: {
            enable: true,
            notBeforeTimeout: "PT15M",
        },
        terminateNotificationProfile: {
            enable: true,
            notBeforeTimeout: "PT10M",
        },
    },
    storageProfile: {
        imageReference: {
            offer: "WindowsServer",
            publisher: "MicrosoftWindowsServer",
            sku: "2016-Datacenter",
            version: "latest",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadWrite,
            createOption: "FromImage",
            managedDisk: {
                storageAccountType: "Standard_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    diagnostics_profile=azure_native.compute.DiagnosticsProfileResponseArgs(
        boot_diagnostics=azure_native.compute.BootDiagnosticsArgs(
            enabled=True,
            storage_uri="http://{existing-storage-account-name}.blob.core.windows.net",
        ),
    ),
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_D1_v2",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
    ),
    resource_group_name="myResourceGroup",
    scheduled_events_profile=azure_native.compute.ScheduledEventsProfileResponseArgs(
        os_image_notification_profile=azure_native.compute.OSImageNotificationProfileArgs(
            enable=True,
            not_before_timeout="PT15M",
        ),
        terminate_notification_profile=azure_native.compute.TerminateNotificationProfileArgs(
            enable=True,
            not_before_timeout="PT10M",
        ),
    ),
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="WindowsServer",
            publisher="MicrosoftWindowsServer",
            sku="2016-Datacenter",
            version="latest",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_WRITE,
            "createOption": "FromImage",
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Standard_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      diagnosticsProfile:
        bootDiagnostics:
          enabled: true
          storageUri: http://{existing-storage-account-name}.blob.core.windows.net
      hardwareProfile:
        vmSize: Standard_D1_v2
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
      resourceGroupName: myResourceGroup
      scheduledEventsProfile:
        osImageNotificationProfile:
          enable: true
          notBeforeTimeout: PT15M
        terminateNotificationProfile:
          enable: true
          notBeforeTimeout: PT10M
      storageProfile:
        imageReference:
          offer: WindowsServer
          publisher: MicrosoftWindowsServer
          sku: 2016-Datacenter
          version: latest
        osDisk:
          caching: ReadWrite
          createOption: FromImage
          managedDisk:
            storageAccountType: Standard_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a vm with a marketplace image plan.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D1_v2",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
        },
        Plan = new AzureNative.Compute.Inputs.PlanArgs
        {
            Name = "windows2016",
            Product = "windows-data-science-vm",
            Publisher = "microsoft-ads",
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "windows-data-science-vm",
                Publisher = "microsoft-ads",
                Sku = "windows2016",
                Version = "latest",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Standard_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .hardwareProfile(Map.of("vmSize", "Standard_D1_v2"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM")
            ))
            .plan(Map.ofEntries(
                Map.entry("name", "windows2016"),
                Map.entry("product", "windows-data-science-vm"),
                Map.entry("publisher", "microsoft-ads")
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "windows-data-science-vm"),
                    Map.entry("publisher", "microsoft-ads"),
                    Map.entry("sku", "windows2016"),
                    Map.entry("version", "latest")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadWrite"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    hardwareProfile: {
        vmSize: "Standard_D1_v2",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
    },
    plan: {
        name: "windows2016",
        product: "windows-data-science-vm",
        publisher: "microsoft-ads",
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        imageReference: {
            offer: "windows-data-science-vm",
            publisher: "microsoft-ads",
            sku: "windows2016",
            version: "latest",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadWrite,
            createOption: "FromImage",
            managedDisk: {
                storageAccountType: "Standard_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_D1_v2",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
    ),
    plan=azure_native.compute.PlanArgs(
        name="windows2016",
        product="windows-data-science-vm",
        publisher="microsoft-ads",
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="windows-data-science-vm",
            publisher="microsoft-ads",
            sku="windows2016",
            version="latest",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_WRITE,
            "createOption": "FromImage",
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Standard_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      hardwareProfile:
        vmSize: Standard_D1_v2
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
      plan:
        name: windows2016
        product: windows-data-science-vm
        publisher: microsoft-ads
      resourceGroupName: myResourceGroup
      storageProfile:
        imageReference:
          offer: windows-data-science-vm
          publisher: microsoft-ads
          sku: windows2016
          version: latest
        osDisk:
          caching: ReadWrite
          createOption: FromImage
          managedDisk:
            storageAccountType: Standard_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a vm with an extensions time budget.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        DiagnosticsProfile = new AzureNative.Compute.Inputs.DiagnosticsProfileArgs
        {
            BootDiagnostics = new AzureNative.Compute.Inputs.BootDiagnosticsArgs
            {
                Enabled = true,
                StorageUri = "http://{existing-storage-account-name}.blob.core.windows.net",
            },
        },
        ExtensionsTimeBudget = "PT30M",
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D1_v2",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "WindowsServer",
                Publisher = "MicrosoftWindowsServer",
                Sku = "2016-Datacenter",
                Version = "latest",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Standard_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .diagnosticsProfile(Map.of("bootDiagnostics", Map.ofEntries(
                Map.entry("enabled", true),
                Map.entry("storageUri", "http://{existing-storage-account-name}.blob.core.windows.net")
            )))
            .extensionsTimeBudget("PT30M")
            .hardwareProfile(Map.of("vmSize", "Standard_D1_v2"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM")
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "WindowsServer"),
                    Map.entry("publisher", "MicrosoftWindowsServer"),
                    Map.entry("sku", "2016-Datacenter"),
                    Map.entry("version", "latest")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadWrite"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    diagnosticsProfile: {
        bootDiagnostics: {
            enabled: true,
            storageUri: "http://{existing-storage-account-name}.blob.core.windows.net",
        },
    },
    extensionsTimeBudget: "PT30M",
    hardwareProfile: {
        vmSize: "Standard_D1_v2",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        imageReference: {
            offer: "WindowsServer",
            publisher: "MicrosoftWindowsServer",
            sku: "2016-Datacenter",
            version: "latest",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadWrite,
            createOption: "FromImage",
            managedDisk: {
                storageAccountType: "Standard_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    diagnostics_profile=azure_native.compute.DiagnosticsProfileResponseArgs(
        boot_diagnostics=azure_native.compute.BootDiagnosticsArgs(
            enabled=True,
            storage_uri="http://{existing-storage-account-name}.blob.core.windows.net",
        ),
    ),
    extensions_time_budget="PT30M",
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_D1_v2",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="WindowsServer",
            publisher="MicrosoftWindowsServer",
            sku="2016-Datacenter",
            version="latest",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_WRITE,
            "createOption": "FromImage",
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Standard_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      diagnosticsProfile:
        bootDiagnostics:
          enabled: true
          storageUri: http://{existing-storage-account-name}.blob.core.windows.net
      extensionsTimeBudget: PT30M
      hardwareProfile:
        vmSize: Standard_D1_v2
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
      resourceGroupName: myResourceGroup
      storageProfile:
        imageReference:
          offer: WindowsServer
          publisher: MicrosoftWindowsServer
          sku: 2016-Datacenter
          version: latest
        osDisk:
          caching: ReadWrite
          createOption: FromImage
          managedDisk:
            storageAccountType: Standard_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a vm with boot diagnostics.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        DiagnosticsProfile = new AzureNative.Compute.Inputs.DiagnosticsProfileArgs
        {
            BootDiagnostics = new AzureNative.Compute.Inputs.BootDiagnosticsArgs
            {
                Enabled = true,
                StorageUri = "http://{existing-storage-account-name}.blob.core.windows.net",
            },
        },
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D1_v2",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "WindowsServer",
                Publisher = "MicrosoftWindowsServer",
                Sku = "2016-Datacenter",
                Version = "latest",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Standard_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .diagnosticsProfile(Map.of("bootDiagnostics", Map.ofEntries(
                Map.entry("enabled", true),
                Map.entry("storageUri", "http://{existing-storage-account-name}.blob.core.windows.net")
            )))
            .hardwareProfile(Map.of("vmSize", "Standard_D1_v2"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM")
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "WindowsServer"),
                    Map.entry("publisher", "MicrosoftWindowsServer"),
                    Map.entry("sku", "2016-Datacenter"),
                    Map.entry("version", "latest")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadWrite"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    diagnosticsProfile: {
        bootDiagnostics: {
            enabled: true,
            storageUri: "http://{existing-storage-account-name}.blob.core.windows.net",
        },
    },
    hardwareProfile: {
        vmSize: "Standard_D1_v2",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        imageReference: {
            offer: "WindowsServer",
            publisher: "MicrosoftWindowsServer",
            sku: "2016-Datacenter",
            version: "latest",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadWrite,
            createOption: "FromImage",
            managedDisk: {
                storageAccountType: "Standard_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    diagnostics_profile=azure_native.compute.DiagnosticsProfileResponseArgs(
        boot_diagnostics=azure_native.compute.BootDiagnosticsArgs(
            enabled=True,
            storage_uri="http://{existing-storage-account-name}.blob.core.windows.net",
        ),
    ),
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_D1_v2",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="WindowsServer",
            publisher="MicrosoftWindowsServer",
            sku="2016-Datacenter",
            version="latest",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_WRITE,
            "createOption": "FromImage",
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Standard_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      diagnosticsProfile:
        bootDiagnostics:
          enabled: true
          storageUri: http://{existing-storage-account-name}.blob.core.windows.net
      hardwareProfile:
        vmSize: Standard_D1_v2
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
      resourceGroupName: myResourceGroup
      storageProfile:
        imageReference:
          offer: WindowsServer
          publisher: MicrosoftWindowsServer
          sku: 2016-Datacenter
          version: latest
        osDisk:
          caching: ReadWrite
          createOption: FromImage
          managedDisk:
            storageAccountType: Standard_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a vm with empty data disks.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D2_v2",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            DataDisks = new[]
            {
                new AzureNative.Compute.Inputs.DataDiskArgs
                {
                    CreateOption = "Empty",
                    DiskSizeGB = 1023,
                    Lun = 0,
                },
                new AzureNative.Compute.Inputs.DataDiskArgs
                {
                    CreateOption = "Empty",
                    DiskSizeGB = 1023,
                    Lun = 1,
                },
            },
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "WindowsServer",
                Publisher = "MicrosoftWindowsServer",
                Sku = "2016-Datacenter",
                Version = "latest",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Standard_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .hardwareProfile(Map.of("vmSize", "Standard_D2_v2"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM")
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("dataDisks",                 
                    Map.ofEntries(
                        Map.entry("createOption", "Empty"),
                        Map.entry("diskSizeGB", 1023),
                        Map.entry("lun", 0)
                    ),
                    Map.ofEntries(
                        Map.entry("createOption", "Empty"),
                        Map.entry("diskSizeGB", 1023),
                        Map.entry("lun", 1)
                    )),
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "WindowsServer"),
                    Map.entry("publisher", "MicrosoftWindowsServer"),
                    Map.entry("sku", "2016-Datacenter"),
                    Map.entry("version", "latest")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadWrite"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    hardwareProfile: {
        vmSize: "Standard_D2_v2",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        dataDisks: [
            {
                createOption: "Empty",
                diskSizeGB: 1023,
                lun: 0,
            },
            {
                createOption: "Empty",
                diskSizeGB: 1023,
                lun: 1,
            },
        ],
        imageReference: {
            offer: "WindowsServer",
            publisher: "MicrosoftWindowsServer",
            sku: "2016-Datacenter",
            version: "latest",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadWrite,
            createOption: "FromImage",
            managedDisk: {
                storageAccountType: "Standard_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_D2_v2",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        data_disks=[
            azure_native.compute.DataDiskArgs(
                create_option="Empty",
                disk_size_gb=1023,
                lun=0,
            ),
            azure_native.compute.DataDiskArgs(
                create_option="Empty",
                disk_size_gb=1023,
                lun=1,
            ),
        ],
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="WindowsServer",
            publisher="MicrosoftWindowsServer",
            sku="2016-Datacenter",
            version="latest",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_WRITE,
            "createOption": "FromImage",
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Standard_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      hardwareProfile:
        vmSize: Standard_D2_v2
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
      resourceGroupName: myResourceGroup
      storageProfile:
        dataDisks:
          - createOption: Empty
            diskSizeGB: 1023
            lun: 0
          - createOption: Empty
            diskSizeGB: 1023
            lun: 1
        imageReference:
          offer: WindowsServer
          publisher: MicrosoftWindowsServer
          sku: 2016-Datacenter
          version: latest
        osDisk:
          caching: ReadWrite
          createOption: FromImage
          managedDisk:
            storageAccountType: Standard_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a vm with ephemeral os disk provisioning in Cache disk using placement property.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_DS1_v2",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
        },
        Plan = new AzureNative.Compute.Inputs.PlanArgs
        {
            Name = "windows2016",
            Product = "windows-data-science-vm",
            Publisher = "microsoft-ads",
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "windows-data-science-vm",
                Publisher = "microsoft-ads",
                Sku = "windows2016",
                Version = "latest",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadOnly,
                CreateOption = "FromImage",
                DiffDiskSettings = new AzureNative.Compute.Inputs.DiffDiskSettingsArgs
                {
                    Option = "Local",
                    Placement = "CacheDisk",
                },
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Standard_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .hardwareProfile(Map.of("vmSize", "Standard_DS1_v2"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM")
            ))
            .plan(Map.ofEntries(
                Map.entry("name", "windows2016"),
                Map.entry("product", "windows-data-science-vm"),
                Map.entry("publisher", "microsoft-ads")
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "windows-data-science-vm"),
                    Map.entry("publisher", "microsoft-ads"),
                    Map.entry("sku", "windows2016"),
                    Map.entry("version", "latest")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadOnly"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("diffDiskSettings", Map.ofEntries(
                        Map.entry("option", "Local"),
                        Map.entry("placement", "CacheDisk")
                    )),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    hardwareProfile: {
        vmSize: "Standard_DS1_v2",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
    },
    plan: {
        name: "windows2016",
        product: "windows-data-science-vm",
        publisher: "microsoft-ads",
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        imageReference: {
            offer: "windows-data-science-vm",
            publisher: "microsoft-ads",
            sku: "windows2016",
            version: "latest",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadOnly,
            createOption: "FromImage",
            diffDiskSettings: {
                option: "Local",
                placement: "CacheDisk",
            },
            managedDisk: {
                storageAccountType: "Standard_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_DS1_v2",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
    ),
    plan=azure_native.compute.PlanArgs(
        name="windows2016",
        product="windows-data-science-vm",
        publisher="microsoft-ads",
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="windows-data-science-vm",
            publisher="microsoft-ads",
            sku="windows2016",
            version="latest",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_ONLY,
            "createOption": "FromImage",
            "diffDiskSettings": azure_native.compute.DiffDiskSettingsArgs(
                option="Local",
                placement="CacheDisk",
            ),
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Standard_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      hardwareProfile:
        vmSize: Standard_DS1_v2
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
      plan:
        name: windows2016
        product: windows-data-science-vm
        publisher: microsoft-ads
      resourceGroupName: myResourceGroup
      storageProfile:
        imageReference:
          offer: windows-data-science-vm
          publisher: microsoft-ads
          sku: windows2016
          version: latest
        osDisk:
          caching: ReadOnly
          createOption: FromImage
          diffDiskSettings:
            option: Local
            placement: CacheDisk
          managedDisk:
            storageAccountType: Standard_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a vm with ephemeral os disk provisioning in Resource disk using placement property.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_DS1_v2",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
        },
        Plan = new AzureNative.Compute.Inputs.PlanArgs
        {
            Name = "windows2016",
            Product = "windows-data-science-vm",
            Publisher = "microsoft-ads",
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "windows-data-science-vm",
                Publisher = "microsoft-ads",
                Sku = "windows2016",
                Version = "latest",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadOnly,
                CreateOption = "FromImage",
                DiffDiskSettings = new AzureNative.Compute.Inputs.DiffDiskSettingsArgs
                {
                    Option = "Local",
                    Placement = "ResourceDisk",
                },
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Standard_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .hardwareProfile(Map.of("vmSize", "Standard_DS1_v2"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM")
            ))
            .plan(Map.ofEntries(
                Map.entry("name", "windows2016"),
                Map.entry("product", "windows-data-science-vm"),
                Map.entry("publisher", "microsoft-ads")
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "windows-data-science-vm"),
                    Map.entry("publisher", "microsoft-ads"),
                    Map.entry("sku", "windows2016"),
                    Map.entry("version", "latest")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadOnly"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("diffDiskSettings", Map.ofEntries(
                        Map.entry("option", "Local"),
                        Map.entry("placement", "ResourceDisk")
                    )),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    hardwareProfile: {
        vmSize: "Standard_DS1_v2",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
    },
    plan: {
        name: "windows2016",
        product: "windows-data-science-vm",
        publisher: "microsoft-ads",
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        imageReference: {
            offer: "windows-data-science-vm",
            publisher: "microsoft-ads",
            sku: "windows2016",
            version: "latest",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadOnly,
            createOption: "FromImage",
            diffDiskSettings: {
                option: "Local",
                placement: "ResourceDisk",
            },
            managedDisk: {
                storageAccountType: "Standard_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_DS1_v2",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
    ),
    plan=azure_native.compute.PlanArgs(
        name="windows2016",
        product="windows-data-science-vm",
        publisher="microsoft-ads",
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="windows-data-science-vm",
            publisher="microsoft-ads",
            sku="windows2016",
            version="latest",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_ONLY,
            "createOption": "FromImage",
            "diffDiskSettings": azure_native.compute.DiffDiskSettingsArgs(
                option="Local",
                placement="ResourceDisk",
            ),
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Standard_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      hardwareProfile:
        vmSize: Standard_DS1_v2
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
      plan:
        name: windows2016
        product: windows-data-science-vm
        publisher: microsoft-ads
      resourceGroupName: myResourceGroup
      storageProfile:
        imageReference:
          offer: windows-data-science-vm
          publisher: microsoft-ads
          sku: windows2016
          version: latest
        osDisk:
          caching: ReadOnly
          createOption: FromImage
          diffDiskSettings:
            option: Local
            placement: ResourceDisk
          managedDisk:
            storageAccountType: Standard_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a vm with ephemeral os disk.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_DS1_v2",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
        },
        Plan = new AzureNative.Compute.Inputs.PlanArgs
        {
            Name = "windows2016",
            Product = "windows-data-science-vm",
            Publisher = "microsoft-ads",
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "windows-data-science-vm",
                Publisher = "microsoft-ads",
                Sku = "windows2016",
                Version = "latest",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadOnly,
                CreateOption = "FromImage",
                DiffDiskSettings = new AzureNative.Compute.Inputs.DiffDiskSettingsArgs
                {
                    Option = "Local",
                },
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Standard_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .hardwareProfile(Map.of("vmSize", "Standard_DS1_v2"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM")
            ))
            .plan(Map.ofEntries(
                Map.entry("name", "windows2016"),
                Map.entry("product", "windows-data-science-vm"),
                Map.entry("publisher", "microsoft-ads")
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "windows-data-science-vm"),
                    Map.entry("publisher", "microsoft-ads"),
                    Map.entry("sku", "windows2016"),
                    Map.entry("version", "latest")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadOnly"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("diffDiskSettings", Map.of("option", "Local")),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    hardwareProfile: {
        vmSize: "Standard_DS1_v2",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
    },
    plan: {
        name: "windows2016",
        product: "windows-data-science-vm",
        publisher: "microsoft-ads",
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        imageReference: {
            offer: "windows-data-science-vm",
            publisher: "microsoft-ads",
            sku: "windows2016",
            version: "latest",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadOnly,
            createOption: "FromImage",
            diffDiskSettings: {
                option: "Local",
            },
            managedDisk: {
                storageAccountType: "Standard_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_DS1_v2",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
    ),
    plan=azure_native.compute.PlanArgs(
        name="windows2016",
        product="windows-data-science-vm",
        publisher="microsoft-ads",
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="windows-data-science-vm",
            publisher="microsoft-ads",
            sku="windows2016",
            version="latest",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_ONLY,
            "createOption": "FromImage",
            "diffDiskSettings": azure_native.compute.DiffDiskSettingsArgs(
                option="Local",
            ),
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Standard_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      hardwareProfile:
        vmSize: Standard_DS1_v2
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
      plan:
        name: windows2016
        product: windows-data-science-vm
        publisher: microsoft-ads
      resourceGroupName: myResourceGroup
      storageProfile:
        imageReference:
          offer: windows-data-science-vm
          publisher: microsoft-ads
          sku: windows2016
          version: latest
        osDisk:
          caching: ReadOnly
          createOption: FromImage
          diffDiskSettings:
            option: Local
          managedDisk:
            storageAccountType: Standard_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a vm with managed boot diagnostics.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        DiagnosticsProfile = new AzureNative.Compute.Inputs.DiagnosticsProfileArgs
        {
            BootDiagnostics = new AzureNative.Compute.Inputs.BootDiagnosticsArgs
            {
                Enabled = true,
            },
        },
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D1_v2",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "WindowsServer",
                Publisher = "MicrosoftWindowsServer",
                Sku = "2016-Datacenter",
                Version = "latest",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Standard_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .diagnosticsProfile(Map.of("bootDiagnostics", Map.of("enabled", true)))
            .hardwareProfile(Map.of("vmSize", "Standard_D1_v2"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM")
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "WindowsServer"),
                    Map.entry("publisher", "MicrosoftWindowsServer"),
                    Map.entry("sku", "2016-Datacenter"),
                    Map.entry("version", "latest")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadWrite"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    diagnosticsProfile: {
        bootDiagnostics: {
            enabled: true,
        },
    },
    hardwareProfile: {
        vmSize: "Standard_D1_v2",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        imageReference: {
            offer: "WindowsServer",
            publisher: "MicrosoftWindowsServer",
            sku: "2016-Datacenter",
            version: "latest",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadWrite,
            createOption: "FromImage",
            managedDisk: {
                storageAccountType: "Standard_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    diagnostics_profile=azure_native.compute.DiagnosticsProfileResponseArgs(
        boot_diagnostics=azure_native.compute.BootDiagnosticsArgs(
            enabled=True,
        ),
    ),
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_D1_v2",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="WindowsServer",
            publisher="MicrosoftWindowsServer",
            sku="2016-Datacenter",
            version="latest",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_WRITE,
            "createOption": "FromImage",
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Standard_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      diagnosticsProfile:
        bootDiagnostics:
          enabled: true
      hardwareProfile:
        vmSize: Standard_D1_v2
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
      resourceGroupName: myResourceGroup
      storageProfile:
        imageReference:
          offer: WindowsServer
          publisher: MicrosoftWindowsServer
          sku: 2016-Datacenter
          version: latest
        osDisk:
          caching: ReadWrite
          createOption: FromImage
          managedDisk:
            storageAccountType: Standard_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a vm with password authentication.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D1_v2",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "WindowsServer",
                Publisher = "MicrosoftWindowsServer",
                Sku = "2016-Datacenter",
                Version = "latest",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Standard_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .hardwareProfile(Map.of("vmSize", "Standard_D1_v2"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM")
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "WindowsServer"),
                    Map.entry("publisher", "MicrosoftWindowsServer"),
                    Map.entry("sku", "2016-Datacenter"),
                    Map.entry("version", "latest")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadWrite"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    hardwareProfile: {
        vmSize: "Standard_D1_v2",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        imageReference: {
            offer: "WindowsServer",
            publisher: "MicrosoftWindowsServer",
            sku: "2016-Datacenter",
            version: "latest",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadWrite,
            createOption: "FromImage",
            managedDisk: {
                storageAccountType: "Standard_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_D1_v2",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="WindowsServer",
            publisher="MicrosoftWindowsServer",
            sku="2016-Datacenter",
            version="latest",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_WRITE,
            "createOption": "FromImage",
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Standard_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      hardwareProfile:
        vmSize: Standard_D1_v2
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
      resourceGroupName: myResourceGroup
      storageProfile:
        imageReference:
          offer: WindowsServer
          publisher: MicrosoftWindowsServer
          sku: 2016-Datacenter
          version: latest
        osDisk:
          caching: ReadWrite
          createOption: FromImage
          managedDisk:
            storageAccountType: Standard_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a vm with premium storage.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D1_v2",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "WindowsServer",
                Publisher = "MicrosoftWindowsServer",
                Sku = "2016-Datacenter",
                Version = "latest",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Premium_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .hardwareProfile(Map.of("vmSize", "Standard_D1_v2"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM")
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "WindowsServer"),
                    Map.entry("publisher", "MicrosoftWindowsServer"),
                    Map.entry("sku", "2016-Datacenter"),
                    Map.entry("version", "latest")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadWrite"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Premium_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    hardwareProfile: {
        vmSize: "Standard_D1_v2",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        imageReference: {
            offer: "WindowsServer",
            publisher: "MicrosoftWindowsServer",
            sku: "2016-Datacenter",
            version: "latest",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadWrite,
            createOption: "FromImage",
            managedDisk: {
                storageAccountType: "Premium_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_D1_v2",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="WindowsServer",
            publisher="MicrosoftWindowsServer",
            sku="2016-Datacenter",
            version="latest",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_WRITE,
            "createOption": "FromImage",
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Premium_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      hardwareProfile:
        vmSize: Standard_D1_v2
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
      resourceGroupName: myResourceGroup
      storageProfile:
        imageReference:
          offer: WindowsServer
          publisher: MicrosoftWindowsServer
          sku: 2016-Datacenter
          version: latest
        osDisk:
          caching: ReadWrite
          createOption: FromImage
          managedDisk:
            storageAccountType: Premium_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create a vm with ssh authentication.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_D1_v2",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
            LinuxConfiguration = new AzureNative.Compute.Inputs.LinuxConfigurationArgs
            {
                DisablePasswordAuthentication = true,
                Ssh = new AzureNative.Compute.Inputs.SshConfigurationArgs
                {
                    PublicKeys = new[]
                    {
                        new AzureNative.Compute.Inputs.SshPublicKeyArgs
                        {
                            KeyData = "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCeClRAk2ipUs/l5voIsDC5q9RI+YSRd1Bvd/O+axgY4WiBzG+4FwJWZm/mLLe5DoOdHQwmU2FrKXZSW4w2sYE70KeWnrFViCOX5MTVvJgPE8ClugNl8RWth/tU849DvM9sT7vFgfVSHcAS2yDRyDlueii+8nF2ym8XWAPltFVCyLHRsyBp5YPqK8JFYIa1eybKsY3hEAxRCA+/7bq8et+Gj3coOsuRmrehav7rE6N12Pb80I6ofa6SM5XNYq4Xk0iYNx7R3kdz0Jj9XgZYWjAHjJmT0gTRoOnt6upOuxK7xI/ykWrllgpXrCPu3Ymz+c+ujaqcxDopnAl2lmf69/J1",
                            Path = "/home/{your-username}/.ssh/authorized_keys",
                        },
                    },
                },
            },
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "{image_offer}",
                Publisher = "{image_publisher}",
                Sku = "{image_sku}",
                Version = "latest",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Standard_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .hardwareProfile(Map.of("vmSize", "Standard_D1_v2"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM"),
                Map.entry("linuxConfiguration", Map.ofEntries(
                    Map.entry("disablePasswordAuthentication", true),
                    Map.entry("ssh", Map.of("publicKeys", Map.ofEntries(
                        Map.entry("keyData", "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCeClRAk2ipUs/l5voIsDC5q9RI+YSRd1Bvd/O+axgY4WiBzG+4FwJWZm/mLLe5DoOdHQwmU2FrKXZSW4w2sYE70KeWnrFViCOX5MTVvJgPE8ClugNl8RWth/tU849DvM9sT7vFgfVSHcAS2yDRyDlueii+8nF2ym8XWAPltFVCyLHRsyBp5YPqK8JFYIa1eybKsY3hEAxRCA+/7bq8et+Gj3coOsuRmrehav7rE6N12Pb80I6ofa6SM5XNYq4Xk0iYNx7R3kdz0Jj9XgZYWjAHjJmT0gTRoOnt6upOuxK7xI/ykWrllgpXrCPu3Ymz+c+ujaqcxDopnAl2lmf69/J1"),
                        Map.entry("path", "/home/{your-username}/.ssh/authorized_keys")
                    )))
                ))
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "{image_offer}"),
                    Map.entry("publisher", "{image_publisher}"),
                    Map.entry("sku", "{image_sku}"),
                    Map.entry("version", "latest")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadWrite"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    hardwareProfile: {
        vmSize: "Standard_D1_v2",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminUsername: "{your-username}",
        computerName: "myVM",
        linuxConfiguration: {
            disablePasswordAuthentication: true,
            ssh: {
                publicKeys: [{
                    keyData: "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCeClRAk2ipUs/l5voIsDC5q9RI+YSRd1Bvd/O+axgY4WiBzG+4FwJWZm/mLLe5DoOdHQwmU2FrKXZSW4w2sYE70KeWnrFViCOX5MTVvJgPE8ClugNl8RWth/tU849DvM9sT7vFgfVSHcAS2yDRyDlueii+8nF2ym8XWAPltFVCyLHRsyBp5YPqK8JFYIa1eybKsY3hEAxRCA+/7bq8et+Gj3coOsuRmrehav7rE6N12Pb80I6ofa6SM5XNYq4Xk0iYNx7R3kdz0Jj9XgZYWjAHjJmT0gTRoOnt6upOuxK7xI/ykWrllgpXrCPu3Ymz+c+ujaqcxDopnAl2lmf69/J1",
                    path: "/home/{your-username}/.ssh/authorized_keys",
                }],
            },
        },
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        imageReference: {
            offer: "{image_offer}",
            publisher: "{image_publisher}",
            sku: "{image_sku}",
            version: "latest",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadWrite,
            createOption: "FromImage",
            managedDisk: {
                storageAccountType: "Standard_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_D1_v2",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileResponseArgs(
        admin_username="{your-username}",
        computer_name="myVM",
        linux_configuration={
            "disablePasswordAuthentication": True,
            "ssh": {
                "publicKeys": [azure_native.compute.SshPublicKeyArgs(
                    key_data="ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCeClRAk2ipUs/l5voIsDC5q9RI+YSRd1Bvd/O+axgY4WiBzG+4FwJWZm/mLLe5DoOdHQwmU2FrKXZSW4w2sYE70KeWnrFViCOX5MTVvJgPE8ClugNl8RWth/tU849DvM9sT7vFgfVSHcAS2yDRyDlueii+8nF2ym8XWAPltFVCyLHRsyBp5YPqK8JFYIa1eybKsY3hEAxRCA+/7bq8et+Gj3coOsuRmrehav7rE6N12Pb80I6ofa6SM5XNYq4Xk0iYNx7R3kdz0Jj9XgZYWjAHjJmT0gTRoOnt6upOuxK7xI/ykWrllgpXrCPu3Ymz+c+ujaqcxDopnAl2lmf69/J1",
                    path="/home/{your-username}/.ssh/authorized_keys",
                )],
            },
        },
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="{image_offer}",
            publisher="{image_publisher}",
            sku="{image_sku}",
            version="latest",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_WRITE,
            "createOption": "FromImage",
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Standard_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      hardwareProfile:
        vmSize: Standard_D1_v2
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminUsername: '{your-username}'
        computerName: myVM
        linuxConfiguration:
          disablePasswordAuthentication: true
          ssh:
            publicKeys:
              - keyData: ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCeClRAk2ipUs/l5voIsDC5q9RI+YSRd1Bvd/O+axgY4WiBzG+4FwJWZm/mLLe5DoOdHQwmU2FrKXZSW4w2sYE70KeWnrFViCOX5MTVvJgPE8ClugNl8RWth/tU849DvM9sT7vFgfVSHcAS2yDRyDlueii+8nF2ym8XWAPltFVCyLHRsyBp5YPqK8JFYIa1eybKsY3hEAxRCA+/7bq8et+Gj3coOsuRmrehav7rE6N12Pb80I6ofa6SM5XNYq4Xk0iYNx7R3kdz0Jj9XgZYWjAHjJmT0gTRoOnt6upOuxK7xI/ykWrllgpXrCPu3Ymz+c+ujaqcxDopnAl2lmf69/J1
                path: /home/{your-username}/.ssh/authorized_keys
      resourceGroupName: myResourceGroup
      storageProfile:
        imageReference:
          offer: '{image_offer}'
          publisher: '{image_publisher}'
          sku: '{image_sku}'
          version: latest
        osDisk:
          caching: ReadWrite
          createOption: FromImage
          managedDisk:
            storageAccountType: Standard_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% example %}}
### Create or update a VM with capacity reservation
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.Compute.VirtualMachine("virtualMachine", new()
    {
        CapacityReservation = new AzureNative.Compute.Inputs.CapacityReservationProfileArgs
        {
            CapacityReservationGroup = new AzureNative.Compute.Inputs.SubResourceArgs
            {
                Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/CapacityReservationGroups/{crgName}",
            },
        },
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Standard_DS1_v2",
        },
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "{your-password}",
            AdminUsername = "{your-username}",
            ComputerName = "myVM",
        },
        Plan = new AzureNative.Compute.Inputs.PlanArgs
        {
            Name = "windows2016",
            Product = "windows-data-science-vm",
            Publisher = "microsoft-ads",
        },
        ResourceGroupName = "myResourceGroup",
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Offer = "windows-data-science-vm",
                Publisher = "microsoft-ads",
                Sku = "windows2016",
                Version = "latest",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.ReadOnly,
                CreateOption = "FromImage",
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    StorageAccountType = "Standard_LRS",
                },
                Name = "myVMosdisk",
            },
        },
        VmName = "myVM",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachine;
import com.pulumi.azurenative.compute.VirtualMachineArgs;
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
        var virtualMachine = new VirtualMachine("virtualMachine", VirtualMachineArgs.builder()        
            .capacityReservation(Map.of("capacityReservationGroup", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/CapacityReservationGroups/{crgName}")))
            .hardwareProfile(Map.of("vmSize", "Standard_DS1_v2"))
            .location("westus")
            .networkProfile(Map.of("networkInterfaces", Map.ofEntries(
                Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}"),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "{your-password}"),
                Map.entry("adminUsername", "{your-username}"),
                Map.entry("computerName", "myVM")
            ))
            .plan(Map.ofEntries(
                Map.entry("name", "windows2016"),
                Map.entry("product", "windows-data-science-vm"),
                Map.entry("publisher", "microsoft-ads")
            ))
            .resourceGroupName("myResourceGroup")
            .storageProfile(Map.ofEntries(
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "windows-data-science-vm"),
                    Map.entry("publisher", "microsoft-ads"),
                    Map.entry("sku", "windows2016"),
                    Map.entry("version", "latest")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadOnly"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS")),
                    Map.entry("name", "myVMosdisk")
                ))
            ))
            .vmName("myVM")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.compute.VirtualMachine("virtualMachine", {
    capacityReservation: {
        capacityReservationGroup: {
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/CapacityReservationGroups/{crgName}",
        },
    },
    hardwareProfile: {
        vmSize: "Standard_DS1_v2",
    },
    location: "westus",
    networkProfile: {
        networkInterfaces: [{
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "{your-password}",
        adminUsername: "{your-username}",
        computerName: "myVM",
    },
    plan: {
        name: "windows2016",
        product: "windows-data-science-vm",
        publisher: "microsoft-ads",
    },
    resourceGroupName: "myResourceGroup",
    storageProfile: {
        imageReference: {
            offer: "windows-data-science-vm",
            publisher: "microsoft-ads",
            sku: "windows2016",
            version: "latest",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.ReadOnly,
            createOption: "FromImage",
            managedDisk: {
                storageAccountType: "Standard_LRS",
            },
            name: "myVMosdisk",
        },
    },
    vmName: "myVM",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.compute.VirtualMachine("virtualMachine",
    capacity_reservation=azure_native.compute.CapacityReservationProfileResponseArgs(
        capacity_reservation_group=azure_native.compute.SubResourceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/CapacityReservationGroups/{crgName}",
        ),
    ),
    hardware_profile=azure_native.compute.HardwareProfileArgs(
        vm_size="Standard_DS1_v2",
    ),
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}",
            primary=True,
        )],
    ),
    os_profile=azure_native.compute.OSProfileArgs(
        admin_password="{your-password}",
        admin_username="{your-username}",
        computer_name="myVM",
    ),
    plan=azure_native.compute.PlanArgs(
        name="windows2016",
        product="windows-data-science-vm",
        publisher="microsoft-ads",
    ),
    resource_group_name="myResourceGroup",
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        image_reference=azure_native.compute.ImageReferenceArgs(
            offer="windows-data-science-vm",
            publisher="microsoft-ads",
            sku="windows2016",
            version="latest",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.READ_ONLY,
            "createOption": "FromImage",
            "managedDisk": azure_native.compute.ManagedDiskParametersArgs(
                storage_account_type="Standard_LRS",
            ),
            "name": "myVMosdisk",
        },
    ),
    vm_name="myVM")

```

```yaml
resources:
  virtualMachine:
    type: azure-native:compute:VirtualMachine
    properties:
      capacityReservation:
        capacityReservationGroup:
          id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/CapacityReservationGroups/{crgName}
      hardwareProfile:
        vmSize: Standard_DS1_v2
      location: westus
      networkProfile:
        networkInterfaces:
          - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/networkInterfaces/{existing-nic-name}
            primary: true
      osProfile:
        adminPassword: '{your-password}'
        adminUsername: '{your-username}'
        computerName: myVM
      plan:
        name: windows2016
        product: windows-data-science-vm
        publisher: microsoft-ads
      resourceGroupName: myResourceGroup
      storageProfile:
        imageReference:
          offer: windows-data-science-vm
          publisher: microsoft-ads
          sku: windows2016
          version: latest
        osDisk:
          caching: ReadOnly
          createOption: FromImage
          managedDisk:
            storageAccountType: Standard_LRS
          name: myVMosdisk
      vmName: myVM

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:compute:VirtualMachine myVM /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/virtualMachines/myVM 
```
