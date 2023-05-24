Describes a Virtual Machine Scale Set.
API Version: 2022-11-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a VMSS with an extension that has suppressFailures enabled
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "westus",
        Overprovision = true,
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 3,
            Name = "Standard_D1_v2",
            Tier = "Standard",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            Mode = AzureNative.Compute.UpgradeMode.Manual,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            DiagnosticsProfile = new AzureNative.Compute.Inputs.DiagnosticsProfileArgs
            {
                BootDiagnostics = new AzureNative.Compute.Inputs.BootDiagnosticsArgs
                {
                    Enabled = true,
                    StorageUri = "http://{existing-storage-account-name}.blob.core.windows.net",
                },
            },
            ExtensionProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetExtensionProfileArgs
            {
                Extensions = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetExtensionArgs
                    {
                        AutoUpgradeMinorVersion = false,
                        Name = "{extension-name}",
                        Publisher = "{extension-Publisher}",
                        Settings = null,
                        SuppressFailures = true,
                        Type = "{extension-Type}",
                        TypeHandlerVersion = "{handler-version}",
                    },
                },
            },
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminPassword = "{your-password}",
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
            },
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
                {
                    Offer = "WindowsServer",
                    Publisher = "MicrosoftWindowsServer",
                    Sku = "2016-Datacenter",
                    Version = "latest",
                },
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                    CreateOption = "FromImage",
                    ManagedDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetManagedDiskParametersArgs
                    {
                        StorageAccountType = "Standard_LRS",
                    },
                },
            },
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("westus")
            .overprovision(true)
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 3),
                Map.entry("name", "Standard_D1_v2"),
                Map.entry("tier", "Standard")
            ))
            .upgradePolicy(Map.of("mode", "Manual"))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("diagnosticsProfile", Map.of("bootDiagnostics", Map.ofEntries(
                    Map.entry("enabled", true),
                    Map.entry("storageUri", "http://{existing-storage-account-name}.blob.core.windows.net")
                ))),
                Map.entry("extensionProfile", Map.of("extensions", Map.ofEntries(
                    Map.entry("autoUpgradeMinorVersion", false),
                    Map.entry("name", "{extension-name}"),
                    Map.entry("publisher", "{extension-Publisher}"),
                    Map.entry("settings", ),
                    Map.entry("suppressFailures", true),
                    Map.entry("type", "{extension-Type}"),
                    Map.entry("typeHandlerVersion", "{handler-version}")
                ))),
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                    )),
                    Map.entry("name", "{vmss-name}"),
                    Map.entry("primary", true)
                ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminPassword", "{your-password}"),
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}")
                )),
                Map.entry("storageProfile", Map.ofEntries(
                    Map.entry("imageReference", Map.ofEntries(
                        Map.entry("offer", "WindowsServer"),
                        Map.entry("publisher", "MicrosoftWindowsServer"),
                        Map.entry("sku", "2016-Datacenter"),
                        Map.entry("version", "latest")
                    )),
                    Map.entry("osDisk", Map.ofEntries(
                        Map.entry("caching", "ReadWrite"),
                        Map.entry("createOption", "FromImage"),
                        Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS"))
                    ))
                ))
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "westus",
    overprovision: true,
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 3,
        name: "Standard_D1_v2",
        tier: "Standard",
    },
    upgradePolicy: {
        mode: azure_native.compute.UpgradeMode.Manual,
    },
    virtualMachineProfile: {
        diagnosticsProfile: {
            bootDiagnostics: {
                enabled: true,
                storageUri: "http://{existing-storage-account-name}.blob.core.windows.net",
            },
        },
        extensionProfile: {
            extensions: [{
                autoUpgradeMinorVersion: false,
                name: "{extension-name}",
                publisher: "{extension-Publisher}",
                settings: {},
                suppressFailures: true,
                type: "{extension-Type}",
                typeHandlerVersion: "{handler-version}",
            }],
        },
        networkProfile: {
            networkInterfaceConfigurations: [{
                enableIPForwarding: true,
                ipConfigurations: [{
                    name: "{vmss-name}",
                    subnet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    },
                }],
                name: "{vmss-name}",
                primary: true,
            }],
        },
        osProfile: {
            adminPassword: "{your-password}",
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
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
            },
        },
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="westus",
    overprovision=True,
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=3,
        name="Standard_D1_v2",
        tier="Standard",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyArgs(
        mode=azure_native.compute.UpgradeMode.MANUAL,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        diagnostics_profile={
            "bootDiagnostics": azure_native.compute.BootDiagnosticsArgs(
                enabled=True,
                storage_uri="http://{existing-storage-account-name}.blob.core.windows.net",
            ),
        },
        extension_profile={
            "extensions": [azure_native.compute.VirtualMachineScaleSetExtensionArgs(
                auto_upgrade_minor_version=False,
                name="{extension-name}",
                publisher="{extension-Publisher}",
                settings={},
                suppress_failures=True,
                type="{extension-Type}",
                type_handler_version="{handler-version}",
            )],
        },
        network_profile={
            "networkInterfaceConfigurations": [{
                "enableIPForwarding": True,
                "ipConfigurations": [{
                    "name": "{vmss-name}",
                    "subnet": azure_native.compute.ApiEntityReferenceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    ),
                }],
                "name": "{vmss-name}",
                "primary": True,
            }],
        },
        os_profile=azure_native.compute.VirtualMachineScaleSetOSProfileArgs(
            admin_password="{your-password}",
            admin_username="{your-username}",
            computer_name_prefix="{vmss-name}",
        ),
        storage_profile={
            "imageReference": azure_native.compute.ImageReferenceArgs(
                offer="WindowsServer",
                publisher="MicrosoftWindowsServer",
                sku="2016-Datacenter",
                version="latest",
            ),
            "osDisk": {
                "caching": azure_native.compute.CachingTypes.READ_WRITE,
                "createOption": "FromImage",
                "managedDisk": azure_native.compute.VirtualMachineScaleSetManagedDiskParametersArgs(
                    storage_account_type="Standard_LRS",
                ),
            },
        },
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml
resources:
  virtualMachineScaleSet:
    type: azure-native:compute:VirtualMachineScaleSet
    properties:
      location: westus
      overprovision: true
      resourceGroupName: myResourceGroup
      sku:
        capacity: 3
        name: Standard_D1_v2
        tier: Standard
      upgradePolicy:
        mode: Manual
      virtualMachineProfile:
        diagnosticsProfile:
          bootDiagnostics:
            enabled: true
            storageUri: http://{existing-storage-account-name}.blob.core.windows.net
        extensionProfile:
          extensions:
            - autoUpgradeMinorVersion: false
              name: '{extension-name}'
              publisher: '{extension-Publisher}'
              settings: {}
              suppressFailures: true
              type: '{extension-Type}'
              typeHandlerVersion: '{handler-version}'
        networkProfile:
          networkInterfaceConfigurations:
            - enableIPForwarding: true
              ipConfigurations:
                - name: '{vmss-name}'
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}
              name: '{vmss-name}'
              primary: true
        osProfile:
          adminPassword: '{your-password}'
          adminUsername: '{your-username}'
          computerNamePrefix: '{vmss-name}'
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
      vmScaleSetName: '{vmss-name}'

```

{{% /example %}}
{{% example %}}
### Create a VMSS with an extension with protectedSettingsFromKeyVault
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "westus",
        Overprovision = true,
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 3,
            Name = "Standard_D1_v2",
            Tier = "Standard",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            Mode = AzureNative.Compute.UpgradeMode.Manual,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            DiagnosticsProfile = new AzureNative.Compute.Inputs.DiagnosticsProfileArgs
            {
                BootDiagnostics = new AzureNative.Compute.Inputs.BootDiagnosticsArgs
                {
                    Enabled = true,
                    StorageUri = "http://{existing-storage-account-name}.blob.core.windows.net",
                },
            },
            ExtensionProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetExtensionProfileArgs
            {
                Extensions = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetExtensionArgs
                    {
                        AutoUpgradeMinorVersion = false,
                        Name = "{extension-name}",
                        ProtectedSettingsFromKeyVault = new AzureNative.Compute.Inputs.KeyVaultSecretReferenceArgs
                        {
                            SecretUrl = "https://kvName.vault.azure.net/secrets/secretName/79b88b3a6f5440ffb2e73e44a0db712e",
                            SourceVault = new AzureNative.Compute.Inputs.SubResourceArgs
                            {
                                Id = "/subscriptions/a53f7094-a16c-47af-abe4-b05c05d0d79a/resourceGroups/myResourceGroup/providers/Microsoft.KeyVault/vaults/kvName",
                            },
                        },
                        Publisher = "{extension-Publisher}",
                        Settings = null,
                        Type = "{extension-Type}",
                        TypeHandlerVersion = "{handler-version}",
                    },
                },
            },
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminPassword = "{your-password}",
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
            },
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
                {
                    Offer = "WindowsServer",
                    Publisher = "MicrosoftWindowsServer",
                    Sku = "2016-Datacenter",
                    Version = "latest",
                },
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                    CreateOption = "FromImage",
                    ManagedDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetManagedDiskParametersArgs
                    {
                        StorageAccountType = "Standard_LRS",
                    },
                },
            },
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("westus")
            .overprovision(true)
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 3),
                Map.entry("name", "Standard_D1_v2"),
                Map.entry("tier", "Standard")
            ))
            .upgradePolicy(Map.of("mode", "Manual"))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("diagnosticsProfile", Map.of("bootDiagnostics", Map.ofEntries(
                    Map.entry("enabled", true),
                    Map.entry("storageUri", "http://{existing-storage-account-name}.blob.core.windows.net")
                ))),
                Map.entry("extensionProfile", Map.of("extensions", Map.ofEntries(
                    Map.entry("autoUpgradeMinorVersion", false),
                    Map.entry("name", "{extension-name}"),
                    Map.entry("protectedSettingsFromKeyVault", Map.ofEntries(
                        Map.entry("secretUrl", "https://kvName.vault.azure.net/secrets/secretName/79b88b3a6f5440ffb2e73e44a0db712e"),
                        Map.entry("sourceVault", Map.of("id", "/subscriptions/a53f7094-a16c-47af-abe4-b05c05d0d79a/resourceGroups/myResourceGroup/providers/Microsoft.KeyVault/vaults/kvName"))
                    )),
                    Map.entry("publisher", "{extension-Publisher}"),
                    Map.entry("settings", ),
                    Map.entry("type", "{extension-Type}"),
                    Map.entry("typeHandlerVersion", "{handler-version}")
                ))),
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                    )),
                    Map.entry("name", "{vmss-name}"),
                    Map.entry("primary", true)
                ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminPassword", "{your-password}"),
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}")
                )),
                Map.entry("storageProfile", Map.ofEntries(
                    Map.entry("imageReference", Map.ofEntries(
                        Map.entry("offer", "WindowsServer"),
                        Map.entry("publisher", "MicrosoftWindowsServer"),
                        Map.entry("sku", "2016-Datacenter"),
                        Map.entry("version", "latest")
                    )),
                    Map.entry("osDisk", Map.ofEntries(
                        Map.entry("caching", "ReadWrite"),
                        Map.entry("createOption", "FromImage"),
                        Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS"))
                    ))
                ))
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "westus",
    overprovision: true,
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 3,
        name: "Standard_D1_v2",
        tier: "Standard",
    },
    upgradePolicy: {
        mode: azure_native.compute.UpgradeMode.Manual,
    },
    virtualMachineProfile: {
        diagnosticsProfile: {
            bootDiagnostics: {
                enabled: true,
                storageUri: "http://{existing-storage-account-name}.blob.core.windows.net",
            },
        },
        extensionProfile: {
            extensions: [{
                autoUpgradeMinorVersion: false,
                name: "{extension-name}",
                protectedSettingsFromKeyVault: {
                    secretUrl: "https://kvName.vault.azure.net/secrets/secretName/79b88b3a6f5440ffb2e73e44a0db712e",
                    sourceVault: {
                        id: "/subscriptions/a53f7094-a16c-47af-abe4-b05c05d0d79a/resourceGroups/myResourceGroup/providers/Microsoft.KeyVault/vaults/kvName",
                    },
                },
                publisher: "{extension-Publisher}",
                settings: {},
                type: "{extension-Type}",
                typeHandlerVersion: "{handler-version}",
            }],
        },
        networkProfile: {
            networkInterfaceConfigurations: [{
                enableIPForwarding: true,
                ipConfigurations: [{
                    name: "{vmss-name}",
                    subnet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    },
                }],
                name: "{vmss-name}",
                primary: true,
            }],
        },
        osProfile: {
            adminPassword: "{your-password}",
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
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
            },
        },
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="westus",
    overprovision=True,
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=3,
        name="Standard_D1_v2",
        tier="Standard",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyArgs(
        mode=azure_native.compute.UpgradeMode.MANUAL,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        diagnostics_profile={
            "bootDiagnostics": azure_native.compute.BootDiagnosticsArgs(
                enabled=True,
                storage_uri="http://{existing-storage-account-name}.blob.core.windows.net",
            ),
        },
        extension_profile={
            "extensions": [{
                "autoUpgradeMinorVersion": False,
                "name": "{extension-name}",
                "protectedSettingsFromKeyVault": {
                    "secretUrl": "https://kvName.vault.azure.net/secrets/secretName/79b88b3a6f5440ffb2e73e44a0db712e",
                    "sourceVault": azure_native.compute.SubResourceArgs(
                        id="/subscriptions/a53f7094-a16c-47af-abe4-b05c05d0d79a/resourceGroups/myResourceGroup/providers/Microsoft.KeyVault/vaults/kvName",
                    ),
                },
                "publisher": "{extension-Publisher}",
                "settings": {},
                "type": "{extension-Type}",
                "typeHandlerVersion": "{handler-version}",
            }],
        },
        network_profile={
            "networkInterfaceConfigurations": [{
                "enableIPForwarding": True,
                "ipConfigurations": [{
                    "name": "{vmss-name}",
                    "subnet": azure_native.compute.ApiEntityReferenceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    ),
                }],
                "name": "{vmss-name}",
                "primary": True,
            }],
        },
        os_profile=azure_native.compute.VirtualMachineScaleSetOSProfileArgs(
            admin_password="{your-password}",
            admin_username="{your-username}",
            computer_name_prefix="{vmss-name}",
        ),
        storage_profile={
            "imageReference": azure_native.compute.ImageReferenceArgs(
                offer="WindowsServer",
                publisher="MicrosoftWindowsServer",
                sku="2016-Datacenter",
                version="latest",
            ),
            "osDisk": {
                "caching": azure_native.compute.CachingTypes.READ_WRITE,
                "createOption": "FromImage",
                "managedDisk": azure_native.compute.VirtualMachineScaleSetManagedDiskParametersArgs(
                    storage_account_type="Standard_LRS",
                ),
            },
        },
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml
resources:
  virtualMachineScaleSet:
    type: azure-native:compute:VirtualMachineScaleSet
    properties:
      location: westus
      overprovision: true
      resourceGroupName: myResourceGroup
      sku:
        capacity: 3
        name: Standard_D1_v2
        tier: Standard
      upgradePolicy:
        mode: Manual
      virtualMachineProfile:
        diagnosticsProfile:
          bootDiagnostics:
            enabled: true
            storageUri: http://{existing-storage-account-name}.blob.core.windows.net
        extensionProfile:
          extensions:
            - autoUpgradeMinorVersion: false
              name: '{extension-name}'
              protectedSettingsFromKeyVault:
                secretUrl: https://kvName.vault.azure.net/secrets/secretName/79b88b3a6f5440ffb2e73e44a0db712e
                sourceVault:
                  id: /subscriptions/a53f7094-a16c-47af-abe4-b05c05d0d79a/resourceGroups/myResourceGroup/providers/Microsoft.KeyVault/vaults/kvName
              publisher: '{extension-Publisher}'
              settings: {}
              type: '{extension-Type}'
              typeHandlerVersion: '{handler-version}'
        networkProfile:
          networkInterfaceConfigurations:
            - enableIPForwarding: true
              ipConfigurations:
                - name: '{vmss-name}'
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}
              name: '{vmss-name}'
              primary: true
        osProfile:
          adminPassword: '{your-password}'
          adminUsername: '{your-username}'
          computerNamePrefix: '{vmss-name}'
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
      vmScaleSetName: '{vmss-name}'

```

{{% /example %}}
{{% example %}}
### Create a custom-image scale set from an unmanaged generalized os image.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "westus",
        Overprovision = true,
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 3,
            Name = "Standard_D1_v2",
            Tier = "Standard",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            Mode = AzureNative.Compute.UpgradeMode.Manual,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminPassword = "{your-password}",
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
            },
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                    CreateOption = "FromImage",
                    Image = new AzureNative.Compute.Inputs.VirtualHardDiskArgs
                    {
                        Uri = "http://{existing-storage-account-name}.blob.core.windows.net/{existing-container-name}/{existing-generalized-os-image-blob-name}.vhd",
                    },
                    Name = "osDisk",
                },
            },
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("westus")
            .overprovision(true)
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 3),
                Map.entry("name", "Standard_D1_v2"),
                Map.entry("tier", "Standard")
            ))
            .upgradePolicy(Map.of("mode", "Manual"))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                    )),
                    Map.entry("name", "{vmss-name}"),
                    Map.entry("primary", true)
                ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminPassword", "{your-password}"),
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}")
                )),
                Map.entry("storageProfile", Map.of("osDisk", Map.ofEntries(
                    Map.entry("caching", "ReadWrite"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("image", Map.of("uri", "http://{existing-storage-account-name}.blob.core.windows.net/{existing-container-name}/{existing-generalized-os-image-blob-name}.vhd")),
                    Map.entry("name", "osDisk")
                )))
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "westus",
    overprovision: true,
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 3,
        name: "Standard_D1_v2",
        tier: "Standard",
    },
    upgradePolicy: {
        mode: azure_native.compute.UpgradeMode.Manual,
    },
    virtualMachineProfile: {
        networkProfile: {
            networkInterfaceConfigurations: [{
                enableIPForwarding: true,
                ipConfigurations: [{
                    name: "{vmss-name}",
                    subnet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    },
                }],
                name: "{vmss-name}",
                primary: true,
            }],
        },
        osProfile: {
            adminPassword: "{your-password}",
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
        },
        storageProfile: {
            osDisk: {
                caching: azure_native.compute.CachingTypes.ReadWrite,
                createOption: "FromImage",
                image: {
                    uri: "http://{existing-storage-account-name}.blob.core.windows.net/{existing-container-name}/{existing-generalized-os-image-blob-name}.vhd",
                },
                name: "osDisk",
            },
        },
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="westus",
    overprovision=True,
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=3,
        name="Standard_D1_v2",
        tier="Standard",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyArgs(
        mode=azure_native.compute.UpgradeMode.MANUAL,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        network_profile={
            "networkInterfaceConfigurations": [{
                "enableIPForwarding": True,
                "ipConfigurations": [{
                    "name": "{vmss-name}",
                    "subnet": azure_native.compute.ApiEntityReferenceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    ),
                }],
                "name": "{vmss-name}",
                "primary": True,
            }],
        },
        os_profile=azure_native.compute.VirtualMachineScaleSetOSProfileArgs(
            admin_password="{your-password}",
            admin_username="{your-username}",
            computer_name_prefix="{vmss-name}",
        ),
        storage_profile={
            "osDisk": {
                "caching": azure_native.compute.CachingTypes.READ_WRITE,
                "createOption": "FromImage",
                "image": azure_native.compute.VirtualHardDiskArgs(
                    uri="http://{existing-storage-account-name}.blob.core.windows.net/{existing-container-name}/{existing-generalized-os-image-blob-name}.vhd",
                ),
                "name": "osDisk",
            },
        },
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml
resources:
  virtualMachineScaleSet:
    type: azure-native:compute:VirtualMachineScaleSet
    properties:
      location: westus
      overprovision: true
      resourceGroupName: myResourceGroup
      sku:
        capacity: 3
        name: Standard_D1_v2
        tier: Standard
      upgradePolicy:
        mode: Manual
      virtualMachineProfile:
        networkProfile:
          networkInterfaceConfigurations:
            - enableIPForwarding: true
              ipConfigurations:
                - name: '{vmss-name}'
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}
              name: '{vmss-name}'
              primary: true
        osProfile:
          adminPassword: '{your-password}'
          adminUsername: '{your-username}'
          computerNamePrefix: '{vmss-name}'
        storageProfile:
          osDisk:
            caching: ReadWrite
            createOption: FromImage
            image:
              uri: http://{existing-storage-account-name}.blob.core.windows.net/{existing-container-name}/{existing-generalized-os-image-blob-name}.vhd
            name: osDisk
      vmScaleSetName: '{vmss-name}'

```

{{% /example %}}
{{% example %}}
### Create a platform-image scale set with unmanaged os disks.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "westus",
        Overprovision = true,
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 3,
            Name = "Standard_D1_v2",
            Tier = "Standard",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            Mode = AzureNative.Compute.UpgradeMode.Manual,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminPassword = "{your-password}",
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
            },
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
                {
                    Offer = "WindowsServer",
                    Publisher = "MicrosoftWindowsServer",
                    Sku = "2016-Datacenter",
                    Version = "latest",
                },
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                    CreateOption = "FromImage",
                    Name = "osDisk",
                    VhdContainers = new[]
                    {
                        "http://{existing-storage-account-name-0}.blob.core.windows.net/vhdContainer",
                        "http://{existing-storage-account-name-1}.blob.core.windows.net/vhdContainer",
                        "http://{existing-storage-account-name-2}.blob.core.windows.net/vhdContainer",
                        "http://{existing-storage-account-name-3}.blob.core.windows.net/vhdContainer",
                        "http://{existing-storage-account-name-4}.blob.core.windows.net/vhdContainer",
                    },
                },
            },
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("westus")
            .overprovision(true)
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 3),
                Map.entry("name", "Standard_D1_v2"),
                Map.entry("tier", "Standard")
            ))
            .upgradePolicy(Map.of("mode", "Manual"))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                    )),
                    Map.entry("name", "{vmss-name}"),
                    Map.entry("primary", true)
                ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminPassword", "{your-password}"),
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}")
                )),
                Map.entry("storageProfile", Map.ofEntries(
                    Map.entry("imageReference", Map.ofEntries(
                        Map.entry("offer", "WindowsServer"),
                        Map.entry("publisher", "MicrosoftWindowsServer"),
                        Map.entry("sku", "2016-Datacenter"),
                        Map.entry("version", "latest")
                    )),
                    Map.entry("osDisk", Map.ofEntries(
                        Map.entry("caching", "ReadWrite"),
                        Map.entry("createOption", "FromImage"),
                        Map.entry("name", "osDisk"),
                        Map.entry("vhdContainers",                         
                            "http://{existing-storage-account-name-0}.blob.core.windows.net/vhdContainer",
                            "http://{existing-storage-account-name-1}.blob.core.windows.net/vhdContainer",
                            "http://{existing-storage-account-name-2}.blob.core.windows.net/vhdContainer",
                            "http://{existing-storage-account-name-3}.blob.core.windows.net/vhdContainer",
                            "http://{existing-storage-account-name-4}.blob.core.windows.net/vhdContainer")
                    ))
                ))
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "westus",
    overprovision: true,
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 3,
        name: "Standard_D1_v2",
        tier: "Standard",
    },
    upgradePolicy: {
        mode: azure_native.compute.UpgradeMode.Manual,
    },
    virtualMachineProfile: {
        networkProfile: {
            networkInterfaceConfigurations: [{
                enableIPForwarding: true,
                ipConfigurations: [{
                    name: "{vmss-name}",
                    subnet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    },
                }],
                name: "{vmss-name}",
                primary: true,
            }],
        },
        osProfile: {
            adminPassword: "{your-password}",
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
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
                name: "osDisk",
                vhdContainers: [
                    "http://{existing-storage-account-name-0}.blob.core.windows.net/vhdContainer",
                    "http://{existing-storage-account-name-1}.blob.core.windows.net/vhdContainer",
                    "http://{existing-storage-account-name-2}.blob.core.windows.net/vhdContainer",
                    "http://{existing-storage-account-name-3}.blob.core.windows.net/vhdContainer",
                    "http://{existing-storage-account-name-4}.blob.core.windows.net/vhdContainer",
                ],
            },
        },
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="westus",
    overprovision=True,
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=3,
        name="Standard_D1_v2",
        tier="Standard",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyArgs(
        mode=azure_native.compute.UpgradeMode.MANUAL,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        network_profile={
            "networkInterfaceConfigurations": [{
                "enableIPForwarding": True,
                "ipConfigurations": [{
                    "name": "{vmss-name}",
                    "subnet": azure_native.compute.ApiEntityReferenceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    ),
                }],
                "name": "{vmss-name}",
                "primary": True,
            }],
        },
        os_profile=azure_native.compute.VirtualMachineScaleSetOSProfileArgs(
            admin_password="{your-password}",
            admin_username="{your-username}",
            computer_name_prefix="{vmss-name}",
        ),
        storage_profile={
            "imageReference": azure_native.compute.ImageReferenceArgs(
                offer="WindowsServer",
                publisher="MicrosoftWindowsServer",
                sku="2016-Datacenter",
                version="latest",
            ),
            "osDisk": azure_native.compute.VirtualMachineScaleSetOSDiskArgs(
                caching=azure_native.compute.CachingTypes.READ_WRITE,
                create_option="FromImage",
                name="osDisk",
                vhd_containers=[
                    "http://{existing-storage-account-name-0}.blob.core.windows.net/vhdContainer",
                    "http://{existing-storage-account-name-1}.blob.core.windows.net/vhdContainer",
                    "http://{existing-storage-account-name-2}.blob.core.windows.net/vhdContainer",
                    "http://{existing-storage-account-name-3}.blob.core.windows.net/vhdContainer",
                    "http://{existing-storage-account-name-4}.blob.core.windows.net/vhdContainer",
                ],
            ),
        },
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml
resources:
  virtualMachineScaleSet:
    type: azure-native:compute:VirtualMachineScaleSet
    properties:
      location: westus
      overprovision: true
      resourceGroupName: myResourceGroup
      sku:
        capacity: 3
        name: Standard_D1_v2
        tier: Standard
      upgradePolicy:
        mode: Manual
      virtualMachineProfile:
        networkProfile:
          networkInterfaceConfigurations:
            - enableIPForwarding: true
              ipConfigurations:
                - name: '{vmss-name}'
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}
              name: '{vmss-name}'
              primary: true
        osProfile:
          adminPassword: '{your-password}'
          adminUsername: '{your-username}'
          computerNamePrefix: '{vmss-name}'
        storageProfile:
          imageReference:
            offer: WindowsServer
            publisher: MicrosoftWindowsServer
            sku: 2016-Datacenter
            version: latest
          osDisk:
            caching: ReadWrite
            createOption: FromImage
            name: osDisk
            vhdContainers:
              - http://{existing-storage-account-name-0}.blob.core.windows.net/vhdContainer
              - http://{existing-storage-account-name-1}.blob.core.windows.net/vhdContainer
              - http://{existing-storage-account-name-2}.blob.core.windows.net/vhdContainer
              - http://{existing-storage-account-name-3}.blob.core.windows.net/vhdContainer
              - http://{existing-storage-account-name-4}.blob.core.windows.net/vhdContainer
      vmScaleSetName: '{vmss-name}'

```

{{% /example %}}
{{% example %}}
### Create a scale set from a custom image.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "westus",
        Overprovision = true,
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 3,
            Name = "Standard_D1_v2",
            Tier = "Standard",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            Mode = AzureNative.Compute.UpgradeMode.Manual,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminPassword = "{your-password}",
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
            },
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/images/{existing-custom-image-name}",
                },
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                    CreateOption = "FromImage",
                    ManagedDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetManagedDiskParametersArgs
                    {
                        StorageAccountType = "Standard_LRS",
                    },
                },
            },
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("westus")
            .overprovision(true)
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 3),
                Map.entry("name", "Standard_D1_v2"),
                Map.entry("tier", "Standard")
            ))
            .upgradePolicy(Map.of("mode", "Manual"))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                    )),
                    Map.entry("name", "{vmss-name}"),
                    Map.entry("primary", true)
                ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminPassword", "{your-password}"),
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}")
                )),
                Map.entry("storageProfile", Map.ofEntries(
                    Map.entry("imageReference", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/images/{existing-custom-image-name}")),
                    Map.entry("osDisk", Map.ofEntries(
                        Map.entry("caching", "ReadWrite"),
                        Map.entry("createOption", "FromImage"),
                        Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS"))
                    ))
                ))
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "westus",
    overprovision: true,
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 3,
        name: "Standard_D1_v2",
        tier: "Standard",
    },
    upgradePolicy: {
        mode: azure_native.compute.UpgradeMode.Manual,
    },
    virtualMachineProfile: {
        networkProfile: {
            networkInterfaceConfigurations: [{
                enableIPForwarding: true,
                ipConfigurations: [{
                    name: "{vmss-name}",
                    subnet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    },
                }],
                name: "{vmss-name}",
                primary: true,
            }],
        },
        osProfile: {
            adminPassword: "{your-password}",
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
        },
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
            },
        },
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="westus",
    overprovision=True,
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=3,
        name="Standard_D1_v2",
        tier="Standard",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyArgs(
        mode=azure_native.compute.UpgradeMode.MANUAL,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        network_profile={
            "networkInterfaceConfigurations": [{
                "enableIPForwarding": True,
                "ipConfigurations": [{
                    "name": "{vmss-name}",
                    "subnet": azure_native.compute.ApiEntityReferenceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    ),
                }],
                "name": "{vmss-name}",
                "primary": True,
            }],
        },
        os_profile=azure_native.compute.VirtualMachineScaleSetOSProfileArgs(
            admin_password="{your-password}",
            admin_username="{your-username}",
            computer_name_prefix="{vmss-name}",
        ),
        storage_profile={
            "imageReference": azure_native.compute.ImageReferenceArgs(
                id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/images/{existing-custom-image-name}",
            ),
            "osDisk": {
                "caching": azure_native.compute.CachingTypes.READ_WRITE,
                "createOption": "FromImage",
                "managedDisk": azure_native.compute.VirtualMachineScaleSetManagedDiskParametersArgs(
                    storage_account_type="Standard_LRS",
                ),
            },
        },
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml
resources:
  virtualMachineScaleSet:
    type: azure-native:compute:VirtualMachineScaleSet
    properties:
      location: westus
      overprovision: true
      resourceGroupName: myResourceGroup
      sku:
        capacity: 3
        name: Standard_D1_v2
        tier: Standard
      upgradePolicy:
        mode: Manual
      virtualMachineProfile:
        networkProfile:
          networkInterfaceConfigurations:
            - enableIPForwarding: true
              ipConfigurations:
                - name: '{vmss-name}'
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}
              name: '{vmss-name}'
              primary: true
        osProfile:
          adminPassword: '{your-password}'
          adminUsername: '{your-username}'
          computerNamePrefix: '{vmss-name}'
        storageProfile:
          imageReference:
            id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/images/{existing-custom-image-name}
          osDisk:
            caching: ReadWrite
            createOption: FromImage
            managedDisk:
              storageAccountType: Standard_LRS
      vmScaleSetName: '{vmss-name}'

```

{{% /example %}}
{{% example %}}
### Create a scale set from a generalized shared image.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "westus",
        Overprovision = true,
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 3,
            Name = "Standard_D1_v2",
            Tier = "Standard",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            Mode = AzureNative.Compute.UpgradeMode.Manual,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminPassword = "{your-password}",
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
            },
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/galleries/mySharedGallery/images/mySharedImage",
                },
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                    CreateOption = "FromImage",
                    ManagedDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetManagedDiskParametersArgs
                    {
                        StorageAccountType = "Standard_LRS",
                    },
                },
            },
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("westus")
            .overprovision(true)
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 3),
                Map.entry("name", "Standard_D1_v2"),
                Map.entry("tier", "Standard")
            ))
            .upgradePolicy(Map.of("mode", "Manual"))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                    )),
                    Map.entry("name", "{vmss-name}"),
                    Map.entry("primary", true)
                ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminPassword", "{your-password}"),
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}")
                )),
                Map.entry("storageProfile", Map.ofEntries(
                    Map.entry("imageReference", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/galleries/mySharedGallery/images/mySharedImage")),
                    Map.entry("osDisk", Map.ofEntries(
                        Map.entry("caching", "ReadWrite"),
                        Map.entry("createOption", "FromImage"),
                        Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS"))
                    ))
                ))
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "westus",
    overprovision: true,
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 3,
        name: "Standard_D1_v2",
        tier: "Standard",
    },
    upgradePolicy: {
        mode: azure_native.compute.UpgradeMode.Manual,
    },
    virtualMachineProfile: {
        networkProfile: {
            networkInterfaceConfigurations: [{
                enableIPForwarding: true,
                ipConfigurations: [{
                    name: "{vmss-name}",
                    subnet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    },
                }],
                name: "{vmss-name}",
                primary: true,
            }],
        },
        osProfile: {
            adminPassword: "{your-password}",
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
        },
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
            },
        },
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="westus",
    overprovision=True,
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=3,
        name="Standard_D1_v2",
        tier="Standard",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyArgs(
        mode=azure_native.compute.UpgradeMode.MANUAL,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        network_profile={
            "networkInterfaceConfigurations": [{
                "enableIPForwarding": True,
                "ipConfigurations": [{
                    "name": "{vmss-name}",
                    "subnet": azure_native.compute.ApiEntityReferenceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    ),
                }],
                "name": "{vmss-name}",
                "primary": True,
            }],
        },
        os_profile=azure_native.compute.VirtualMachineScaleSetOSProfileArgs(
            admin_password="{your-password}",
            admin_username="{your-username}",
            computer_name_prefix="{vmss-name}",
        ),
        storage_profile={
            "imageReference": azure_native.compute.ImageReferenceArgs(
                id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/galleries/mySharedGallery/images/mySharedImage",
            ),
            "osDisk": {
                "caching": azure_native.compute.CachingTypes.READ_WRITE,
                "createOption": "FromImage",
                "managedDisk": azure_native.compute.VirtualMachineScaleSetManagedDiskParametersArgs(
                    storage_account_type="Standard_LRS",
                ),
            },
        },
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml
resources:
  virtualMachineScaleSet:
    type: azure-native:compute:VirtualMachineScaleSet
    properties:
      location: westus
      overprovision: true
      resourceGroupName: myResourceGroup
      sku:
        capacity: 3
        name: Standard_D1_v2
        tier: Standard
      upgradePolicy:
        mode: Manual
      virtualMachineProfile:
        networkProfile:
          networkInterfaceConfigurations:
            - enableIPForwarding: true
              ipConfigurations:
                - name: '{vmss-name}'
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}
              name: '{vmss-name}'
              primary: true
        osProfile:
          adminPassword: '{your-password}'
          adminUsername: '{your-username}'
          computerNamePrefix: '{vmss-name}'
        storageProfile:
          imageReference:
            id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/galleries/mySharedGallery/images/mySharedImage
          osDisk:
            caching: ReadWrite
            createOption: FromImage
            managedDisk:
              storageAccountType: Standard_LRS
      vmScaleSetName: '{vmss-name}'

```

{{% /example %}}
{{% example %}}
### Create a scale set from a specialized shared image.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "westus",
        Overprovision = true,
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 3,
            Name = "Standard_D1_v2",
            Tier = "Standard",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            Mode = AzureNative.Compute.UpgradeMode.Manual,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                },
            },
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/galleries/mySharedGallery/images/mySharedImage",
                },
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                    CreateOption = "FromImage",
                    ManagedDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetManagedDiskParametersArgs
                    {
                        StorageAccountType = "Standard_LRS",
                    },
                },
            },
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("westus")
            .overprovision(true)
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 3),
                Map.entry("name", "Standard_D1_v2"),
                Map.entry("tier", "Standard")
            ))
            .upgradePolicy(Map.of("mode", "Manual"))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                    )),
                    Map.entry("name", "{vmss-name}"),
                    Map.entry("primary", true)
                ))),
                Map.entry("storageProfile", Map.ofEntries(
                    Map.entry("imageReference", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/galleries/mySharedGallery/images/mySharedImage")),
                    Map.entry("osDisk", Map.ofEntries(
                        Map.entry("caching", "ReadWrite"),
                        Map.entry("createOption", "FromImage"),
                        Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS"))
                    ))
                ))
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "westus",
    overprovision: true,
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 3,
        name: "Standard_D1_v2",
        tier: "Standard",
    },
    upgradePolicy: {
        mode: azure_native.compute.UpgradeMode.Manual,
    },
    virtualMachineProfile: {
        networkProfile: {
            networkInterfaceConfigurations: [{
                enableIPForwarding: true,
                ipConfigurations: [{
                    name: "{vmss-name}",
                    subnet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    },
                }],
                name: "{vmss-name}",
                primary: true,
            }],
        },
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
            },
        },
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="westus",
    overprovision=True,
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=3,
        name="Standard_D1_v2",
        tier="Standard",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyArgs(
        mode=azure_native.compute.UpgradeMode.MANUAL,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        network_profile={
            "networkInterfaceConfigurations": [{
                "enableIPForwarding": True,
                "ipConfigurations": [{
                    "name": "{vmss-name}",
                    "subnet": azure_native.compute.ApiEntityReferenceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    ),
                }],
                "name": "{vmss-name}",
                "primary": True,
            }],
        },
        storage_profile={
            "imageReference": azure_native.compute.ImageReferenceArgs(
                id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/galleries/mySharedGallery/images/mySharedImage",
            ),
            "osDisk": {
                "caching": azure_native.compute.CachingTypes.READ_WRITE,
                "createOption": "FromImage",
                "managedDisk": azure_native.compute.VirtualMachineScaleSetManagedDiskParametersArgs(
                    storage_account_type="Standard_LRS",
                ),
            },
        },
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml
resources:
  virtualMachineScaleSet:
    type: azure-native:compute:VirtualMachineScaleSet
    properties:
      location: westus
      overprovision: true
      resourceGroupName: myResourceGroup
      sku:
        capacity: 3
        name: Standard_D1_v2
        tier: Standard
      upgradePolicy:
        mode: Manual
      virtualMachineProfile:
        networkProfile:
          networkInterfaceConfigurations:
            - enableIPForwarding: true
              ipConfigurations:
                - name: '{vmss-name}'
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}
              name: '{vmss-name}'
              primary: true
        storageProfile:
          imageReference:
            id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/galleries/mySharedGallery/images/mySharedImage
          osDisk:
            caching: ReadWrite
            createOption: FromImage
            managedDisk:
              storageAccountType: Standard_LRS
      vmScaleSetName: '{vmss-name}'

```

{{% /example %}}
{{% example %}}
### Create a scale set where nic config has DisableTcpStateTracking property
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "westus",
        Overprovision = true,
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 3,
            Name = "Standard_D1_v2",
            Tier = "Standard",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            Mode = AzureNative.Compute.UpgradeMode.Manual,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        DisableTcpStateTracking = true,
                        EnableAcceleratedNetworking = true,
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{nicConfig1-name}",
                        Primary = true,
                    },
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        DisableTcpStateTracking = false,
                        EnableAcceleratedNetworking = false,
                        EnableIPForwarding = false,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{nicConfig2-name}",
                                Primary = true,
                                PrivateIPAddressVersion = "IPv4",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-fpga-subnet-name2}",
                                },
                            },
                        },
                        Name = "{nicConfig2-name}",
                        Primary = false,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminPassword = "{your-password}",
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
            },
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/images/{existing-custom-image-name}",
                },
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                    CreateOption = "FromImage",
                    ManagedDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetManagedDiskParametersArgs
                    {
                        StorageAccountType = "Standard_LRS",
                    },
                },
            },
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("westus")
            .overprovision(true)
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 3),
                Map.entry("name", "Standard_D1_v2"),
                Map.entry("tier", "Standard")
            ))
            .upgradePolicy(Map.of("mode", "Manual"))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations",                 
                    Map.ofEntries(
                        Map.entry("disableTcpStateTracking", true),
                        Map.entry("enableAcceleratedNetworking", true),
                        Map.entry("enableIPForwarding", true),
                        Map.entry("ipConfigurations", Map.ofEntries(
                            Map.entry("name", "{vmss-name}"),
                            Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                        )),
                        Map.entry("name", "{nicConfig1-name}"),
                        Map.entry("primary", true)
                    ),
                    Map.ofEntries(
                        Map.entry("disableTcpStateTracking", false),
                        Map.entry("enableAcceleratedNetworking", false),
                        Map.entry("enableIPForwarding", false),
                        Map.entry("ipConfigurations", Map.ofEntries(
                            Map.entry("name", "{nicConfig2-name}"),
                            Map.entry("primary", true),
                            Map.entry("privateIPAddressVersion", "IPv4"),
                            Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-fpga-subnet-name2}"))
                        )),
                        Map.entry("name", "{nicConfig2-name}"),
                        Map.entry("primary", false)
                    ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminPassword", "{your-password}"),
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}")
                )),
                Map.entry("storageProfile", Map.ofEntries(
                    Map.entry("imageReference", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/images/{existing-custom-image-name}")),
                    Map.entry("osDisk", Map.ofEntries(
                        Map.entry("caching", "ReadWrite"),
                        Map.entry("createOption", "FromImage"),
                        Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS"))
                    ))
                ))
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "westus",
    overprovision: true,
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 3,
        name: "Standard_D1_v2",
        tier: "Standard",
    },
    upgradePolicy: {
        mode: azure_native.compute.UpgradeMode.Manual,
    },
    virtualMachineProfile: {
        networkProfile: {
            networkInterfaceConfigurations: [
                {
                    disableTcpStateTracking: true,
                    enableAcceleratedNetworking: true,
                    enableIPForwarding: true,
                    ipConfigurations: [{
                        name: "{vmss-name}",
                        subnet: {
                            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                        },
                    }],
                    name: "{nicConfig1-name}",
                    primary: true,
                },
                {
                    disableTcpStateTracking: false,
                    enableAcceleratedNetworking: false,
                    enableIPForwarding: false,
                    ipConfigurations: [{
                        name: "{nicConfig2-name}",
                        primary: true,
                        privateIPAddressVersion: "IPv4",
                        subnet: {
                            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-fpga-subnet-name2}",
                        },
                    }],
                    name: "{nicConfig2-name}",
                    primary: false,
                },
            ],
        },
        osProfile: {
            adminPassword: "{your-password}",
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
        },
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
            },
        },
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="westus",
    overprovision=True,
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=3,
        name="Standard_D1_v2",
        tier="Standard",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyArgs(
        mode=azure_native.compute.UpgradeMode.MANUAL,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        network_profile={
            "networkInterfaceConfigurations": [
                {
                    "disableTcpStateTracking": True,
                    "enableAcceleratedNetworking": True,
                    "enableIPForwarding": True,
                    "ipConfigurations": [{
                        "name": "{vmss-name}",
                        "subnet": azure_native.compute.ApiEntityReferenceArgs(
                            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                        ),
                    }],
                    "name": "{nicConfig1-name}",
                    "primary": True,
                },
                {
                    "disableTcpStateTracking": False,
                    "enableAcceleratedNetworking": False,
                    "enableIPForwarding": False,
                    "ipConfigurations": [{
                        "name": "{nicConfig2-name}",
                        "primary": True,
                        "privateIPAddressVersion": "IPv4",
                        "subnet": azure_native.compute.ApiEntityReferenceArgs(
                            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-fpga-subnet-name2}",
                        ),
                    }],
                    "name": "{nicConfig2-name}",
                    "primary": False,
                },
            ],
        },
        os_profile=azure_native.compute.VirtualMachineScaleSetOSProfileArgs(
            admin_password="{your-password}",
            admin_username="{your-username}",
            computer_name_prefix="{vmss-name}",
        ),
        storage_profile={
            "imageReference": azure_native.compute.ImageReferenceArgs(
                id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/images/{existing-custom-image-name}",
            ),
            "osDisk": {
                "caching": azure_native.compute.CachingTypes.READ_WRITE,
                "createOption": "FromImage",
                "managedDisk": azure_native.compute.VirtualMachineScaleSetManagedDiskParametersArgs(
                    storage_account_type="Standard_LRS",
                ),
            },
        },
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml
resources:
  virtualMachineScaleSet:
    type: azure-native:compute:VirtualMachineScaleSet
    properties:
      location: westus
      overprovision: true
      resourceGroupName: myResourceGroup
      sku:
        capacity: 3
        name: Standard_D1_v2
        tier: Standard
      upgradePolicy:
        mode: Manual
      virtualMachineProfile:
        networkProfile:
          networkInterfaceConfigurations:
            - disableTcpStateTracking: true
              enableAcceleratedNetworking: true
              enableIPForwarding: true
              ipConfigurations:
                - name: '{vmss-name}'
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}
              name: '{nicConfig1-name}'
              primary: true
            - disableTcpStateTracking: false
              enableAcceleratedNetworking: false
              enableIPForwarding: false
              ipConfigurations:
                - name: '{nicConfig2-name}'
                  primary: true
                  privateIPAddressVersion: IPv4
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-fpga-subnet-name2}
              name: '{nicConfig2-name}'
              primary: false
        osProfile:
          adminPassword: '{your-password}'
          adminUsername: '{your-username}'
          computerNamePrefix: '{vmss-name}'
        storageProfile:
          imageReference:
            id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/images/{existing-custom-image-name}
          osDisk:
            caching: ReadWrite
            createOption: FromImage
            managedDisk:
              storageAccountType: Standard_LRS
      vmScaleSetName: '{vmss-name}'

```

{{% /example %}}
{{% example %}}
### Create a scale set with Application Profile
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "westus",
        Overprovision = true,
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 3,
            Name = "Standard_D1_v2",
            Tier = "Standard",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            Mode = AzureNative.Compute.UpgradeMode.Manual,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
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
                        TreatFailureAsDeploymentFailure = true,
                    },
                    new AzureNative.Compute.Inputs.VMGalleryApplicationArgs
                    {
                        PackageReferenceId = "/subscriptions/32c17a9e-aa7b-4ba5-a45b-e324116b6fdg/resourceGroups/myresourceGroupName3/providers/Microsoft.Compute/galleries/myGallery2/applications/MyApplication2/versions/1.1",
                    },
                },
            },
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminPassword = "{your-password}",
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
            },
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
                {
                    Offer = "WindowsServer",
                    Publisher = "MicrosoftWindowsServer",
                    Sku = "2016-Datacenter",
                    Version = "latest",
                },
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                    CreateOption = "FromImage",
                    ManagedDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetManagedDiskParametersArgs
                    {
                        StorageAccountType = "Standard_LRS",
                    },
                },
            },
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("westus")
            .overprovision(true)
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 3),
                Map.entry("name", "Standard_D1_v2"),
                Map.entry("tier", "Standard")
            ))
            .upgradePolicy(Map.of("mode", "Manual"))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("applicationProfile", Map.of("galleryApplications",                 
                    Map.ofEntries(
                        Map.entry("configurationReference", "https://mystorageaccount.blob.core.windows.net/configurations/settings.config"),
                        Map.entry("enableAutomaticUpgrade", false),
                        Map.entry("order", 1),
                        Map.entry("packageReferenceId", "/subscriptions/32c17a9e-aa7b-4ba5-a45b-e324116b6fdb/resourceGroups/myresourceGroupName2/providers/Microsoft.Compute/galleries/myGallery1/applications/MyApplication1/versions/1.0"),
                        Map.entry("tags", "myTag1"),
                        Map.entry("treatFailureAsDeploymentFailure", true)
                    ),
                    Map.of("packageReferenceId", "/subscriptions/32c17a9e-aa7b-4ba5-a45b-e324116b6fdg/resourceGroups/myresourceGroupName3/providers/Microsoft.Compute/galleries/myGallery2/applications/MyApplication2/versions/1.1"))),
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                    )),
                    Map.entry("name", "{vmss-name}"),
                    Map.entry("primary", true)
                ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminPassword", "{your-password}"),
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}")
                )),
                Map.entry("storageProfile", Map.ofEntries(
                    Map.entry("imageReference", Map.ofEntries(
                        Map.entry("offer", "WindowsServer"),
                        Map.entry("publisher", "MicrosoftWindowsServer"),
                        Map.entry("sku", "2016-Datacenter"),
                        Map.entry("version", "latest")
                    )),
                    Map.entry("osDisk", Map.ofEntries(
                        Map.entry("caching", "ReadWrite"),
                        Map.entry("createOption", "FromImage"),
                        Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS"))
                    ))
                ))
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "westus",
    overprovision: true,
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 3,
        name: "Standard_D1_v2",
        tier: "Standard",
    },
    upgradePolicy: {
        mode: azure_native.compute.UpgradeMode.Manual,
    },
    virtualMachineProfile: {
        applicationProfile: {
            galleryApplications: [
                {
                    configurationReference: "https://mystorageaccount.blob.core.windows.net/configurations/settings.config",
                    enableAutomaticUpgrade: false,
                    order: 1,
                    packageReferenceId: "/subscriptions/32c17a9e-aa7b-4ba5-a45b-e324116b6fdb/resourceGroups/myresourceGroupName2/providers/Microsoft.Compute/galleries/myGallery1/applications/MyApplication1/versions/1.0",
                    tags: "myTag1",
                    treatFailureAsDeploymentFailure: true,
                },
                {
                    packageReferenceId: "/subscriptions/32c17a9e-aa7b-4ba5-a45b-e324116b6fdg/resourceGroups/myresourceGroupName3/providers/Microsoft.Compute/galleries/myGallery2/applications/MyApplication2/versions/1.1",
                },
            ],
        },
        networkProfile: {
            networkInterfaceConfigurations: [{
                enableIPForwarding: true,
                ipConfigurations: [{
                    name: "{vmss-name}",
                    subnet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    },
                }],
                name: "{vmss-name}",
                primary: true,
            }],
        },
        osProfile: {
            adminPassword: "{your-password}",
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
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
            },
        },
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="westus",
    overprovision=True,
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=3,
        name="Standard_D1_v2",
        tier="Standard",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyArgs(
        mode=azure_native.compute.UpgradeMode.MANUAL,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        application_profile={
            "galleryApplications": [
                azure_native.compute.VMGalleryApplicationArgs(
                    configuration_reference="https://mystorageaccount.blob.core.windows.net/configurations/settings.config",
                    enable_automatic_upgrade=False,
                    order=1,
                    package_reference_id="/subscriptions/32c17a9e-aa7b-4ba5-a45b-e324116b6fdb/resourceGroups/myresourceGroupName2/providers/Microsoft.Compute/galleries/myGallery1/applications/MyApplication1/versions/1.0",
                    tags="myTag1",
                    treat_failure_as_deployment_failure=True,
                ),
                azure_native.compute.VMGalleryApplicationArgs(
                    package_reference_id="/subscriptions/32c17a9e-aa7b-4ba5-a45b-e324116b6fdg/resourceGroups/myresourceGroupName3/providers/Microsoft.Compute/galleries/myGallery2/applications/MyApplication2/versions/1.1",
                ),
            ],
        },
        network_profile={
            "networkInterfaceConfigurations": [{
                "enableIPForwarding": True,
                "ipConfigurations": [{
                    "name": "{vmss-name}",
                    "subnet": azure_native.compute.ApiEntityReferenceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    ),
                }],
                "name": "{vmss-name}",
                "primary": True,
            }],
        },
        os_profile=azure_native.compute.VirtualMachineScaleSetOSProfileArgs(
            admin_password="{your-password}",
            admin_username="{your-username}",
            computer_name_prefix="{vmss-name}",
        ),
        storage_profile={
            "imageReference": azure_native.compute.ImageReferenceArgs(
                offer="WindowsServer",
                publisher="MicrosoftWindowsServer",
                sku="2016-Datacenter",
                version="latest",
            ),
            "osDisk": {
                "caching": azure_native.compute.CachingTypes.READ_WRITE,
                "createOption": "FromImage",
                "managedDisk": azure_native.compute.VirtualMachineScaleSetManagedDiskParametersArgs(
                    storage_account_type="Standard_LRS",
                ),
            },
        },
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml
resources:
  virtualMachineScaleSet:
    type: azure-native:compute:VirtualMachineScaleSet
    properties:
      location: westus
      overprovision: true
      resourceGroupName: myResourceGroup
      sku:
        capacity: 3
        name: Standard_D1_v2
        tier: Standard
      upgradePolicy:
        mode: Manual
      virtualMachineProfile:
        applicationProfile:
          galleryApplications:
            - configurationReference: https://mystorageaccount.blob.core.windows.net/configurations/settings.config
              enableAutomaticUpgrade: false
              order: 1
              packageReferenceId: /subscriptions/32c17a9e-aa7b-4ba5-a45b-e324116b6fdb/resourceGroups/myresourceGroupName2/providers/Microsoft.Compute/galleries/myGallery1/applications/MyApplication1/versions/1.0
              tags: myTag1
              treatFailureAsDeploymentFailure: true
            - packageReferenceId: /subscriptions/32c17a9e-aa7b-4ba5-a45b-e324116b6fdg/resourceGroups/myresourceGroupName3/providers/Microsoft.Compute/galleries/myGallery2/applications/MyApplication2/versions/1.1
        networkProfile:
          networkInterfaceConfigurations:
            - enableIPForwarding: true
              ipConfigurations:
                - name: '{vmss-name}'
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}
              name: '{vmss-name}'
              primary: true
        osProfile:
          adminPassword: '{your-password}'
          adminUsername: '{your-username}'
          computerNamePrefix: '{vmss-name}'
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
      vmScaleSetName: '{vmss-name}'

```

{{% /example %}}
{{% example %}}
### Create a scale set with DiskEncryptionSet resource in os disk and data disk.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "westus",
        Overprovision = true,
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 3,
            Name = "Standard_DS1_v2",
            Tier = "Standard",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            Mode = AzureNative.Compute.UpgradeMode.Manual,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminPassword = "{your-password}",
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
            },
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                DataDisks = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetDataDiskArgs
                    {
                        Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                        CreateOption = "Empty",
                        DiskSizeGB = 1023,
                        Lun = 0,
                        ManagedDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetManagedDiskParametersArgs
                        {
                            DiskEncryptionSet = new AzureNative.Compute.Inputs.DiskEncryptionSetParametersArgs
                            {
                                Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}",
                            },
                            StorageAccountType = "Standard_LRS",
                        },
                    },
                },
                ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/images/{existing-custom-image-name}",
                },
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                    CreateOption = "FromImage",
                    ManagedDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetManagedDiskParametersArgs
                    {
                        DiskEncryptionSet = new AzureNative.Compute.Inputs.DiskEncryptionSetParametersArgs
                        {
                            Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}",
                        },
                        StorageAccountType = "Standard_LRS",
                    },
                },
            },
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("westus")
            .overprovision(true)
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 3),
                Map.entry("name", "Standard_DS1_v2"),
                Map.entry("tier", "Standard")
            ))
            .upgradePolicy(Map.of("mode", "Manual"))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                    )),
                    Map.entry("name", "{vmss-name}"),
                    Map.entry("primary", true)
                ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminPassword", "{your-password}"),
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}")
                )),
                Map.entry("storageProfile", Map.ofEntries(
                    Map.entry("dataDisks", Map.ofEntries(
                        Map.entry("caching", "ReadWrite"),
                        Map.entry("createOption", "Empty"),
                        Map.entry("diskSizeGB", 1023),
                        Map.entry("lun", 0),
                        Map.entry("managedDisk", Map.ofEntries(
                            Map.entry("diskEncryptionSet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}")),
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
                        ))
                    ))
                ))
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "westus",
    overprovision: true,
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 3,
        name: "Standard_DS1_v2",
        tier: "Standard",
    },
    upgradePolicy: {
        mode: azure_native.compute.UpgradeMode.Manual,
    },
    virtualMachineProfile: {
        networkProfile: {
            networkInterfaceConfigurations: [{
                enableIPForwarding: true,
                ipConfigurations: [{
                    name: "{vmss-name}",
                    subnet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    },
                }],
                name: "{vmss-name}",
                primary: true,
            }],
        },
        osProfile: {
            adminPassword: "{your-password}",
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
        },
        storageProfile: {
            dataDisks: [{
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
            }],
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
            },
        },
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="westus",
    overprovision=True,
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=3,
        name="Standard_DS1_v2",
        tier="Standard",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyArgs(
        mode=azure_native.compute.UpgradeMode.MANUAL,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        network_profile={
            "networkInterfaceConfigurations": [{
                "enableIPForwarding": True,
                "ipConfigurations": [{
                    "name": "{vmss-name}",
                    "subnet": azure_native.compute.ApiEntityReferenceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    ),
                }],
                "name": "{vmss-name}",
                "primary": True,
            }],
        },
        os_profile=azure_native.compute.VirtualMachineScaleSetOSProfileArgs(
            admin_password="{your-password}",
            admin_username="{your-username}",
            computer_name_prefix="{vmss-name}",
        ),
        storage_profile={
            "dataDisks": [{
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
            }],
            "imageReference": azure_native.compute.ImageReferenceArgs(
                id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/images/{existing-custom-image-name}",
            ),
            "osDisk": {
                "caching": azure_native.compute.CachingTypes.READ_WRITE,
                "createOption": "FromImage",
                "managedDisk": {
                    "diskEncryptionSet": azure_native.compute.DiskEncryptionSetParametersArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}",
                    ),
                    "storageAccountType": "Standard_LRS",
                },
            },
        },
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml
resources:
  virtualMachineScaleSet:
    type: azure-native:compute:VirtualMachineScaleSet
    properties:
      location: westus
      overprovision: true
      resourceGroupName: myResourceGroup
      sku:
        capacity: 3
        name: Standard_DS1_v2
        tier: Standard
      upgradePolicy:
        mode: Manual
      virtualMachineProfile:
        networkProfile:
          networkInterfaceConfigurations:
            - enableIPForwarding: true
              ipConfigurations:
                - name: '{vmss-name}'
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}
              name: '{vmss-name}'
              primary: true
        osProfile:
          adminPassword: '{your-password}'
          adminUsername: '{your-username}'
          computerNamePrefix: '{vmss-name}'
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
          imageReference:
            id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/images/{existing-custom-image-name}
          osDisk:
            caching: ReadWrite
            createOption: FromImage
            managedDisk:
              diskEncryptionSet:
                id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/diskEncryptionSets/{existing-diskEncryptionSet-name}
              storageAccountType: Standard_LRS
      vmScaleSetName: '{vmss-name}'

```

{{% /example %}}
{{% example %}}
### Create a scale set with Fpga Network Interfaces.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "westus",
        Overprovision = true,
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 3,
            Name = "Standard_D1_v2",
            Tier = "Standard",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            Mode = AzureNative.Compute.UpgradeMode.Manual,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableAcceleratedNetworking = false,
                        EnableFpga = true,
                        EnableIPForwarding = false,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{fpgaNic-Name}",
                                Primary = true,
                                PrivateIPAddressVersion = "IPv4",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-fpga-subnet-name}",
                                },
                            },
                        },
                        Name = "{fpgaNic-Name}",
                        Primary = false,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminPassword = "{your-password}",
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
            },
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
                {
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/images/{existing-custom-image-name}",
                },
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                    CreateOption = "FromImage",
                    ManagedDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetManagedDiskParametersArgs
                    {
                        StorageAccountType = "Standard_LRS",
                    },
                },
            },
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("westus")
            .overprovision(true)
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 3),
                Map.entry("name", "Standard_D1_v2"),
                Map.entry("tier", "Standard")
            ))
            .upgradePolicy(Map.of("mode", "Manual"))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations",                 
                    Map.ofEntries(
                        Map.entry("enableIPForwarding", true),
                        Map.entry("ipConfigurations", Map.ofEntries(
                            Map.entry("name", "{vmss-name}"),
                            Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                        )),
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("primary", true)
                    ),
                    Map.ofEntries(
                        Map.entry("enableAcceleratedNetworking", false),
                        Map.entry("enableFpga", true),
                        Map.entry("enableIPForwarding", false),
                        Map.entry("ipConfigurations", Map.ofEntries(
                            Map.entry("name", "{fpgaNic-Name}"),
                            Map.entry("primary", true),
                            Map.entry("privateIPAddressVersion", "IPv4"),
                            Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-fpga-subnet-name}"))
                        )),
                        Map.entry("name", "{fpgaNic-Name}"),
                        Map.entry("primary", false)
                    ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminPassword", "{your-password}"),
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}")
                )),
                Map.entry("storageProfile", Map.ofEntries(
                    Map.entry("imageReference", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/images/{existing-custom-image-name}")),
                    Map.entry("osDisk", Map.ofEntries(
                        Map.entry("caching", "ReadWrite"),
                        Map.entry("createOption", "FromImage"),
                        Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS"))
                    ))
                ))
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "westus",
    overprovision: true,
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 3,
        name: "Standard_D1_v2",
        tier: "Standard",
    },
    upgradePolicy: {
        mode: azure_native.compute.UpgradeMode.Manual,
    },
    virtualMachineProfile: {
        networkProfile: {
            networkInterfaceConfigurations: [
                {
                    enableIPForwarding: true,
                    ipConfigurations: [{
                        name: "{vmss-name}",
                        subnet: {
                            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                        },
                    }],
                    name: "{vmss-name}",
                    primary: true,
                },
                {
                    enableAcceleratedNetworking: false,
                    enableFpga: true,
                    enableIPForwarding: false,
                    ipConfigurations: [{
                        name: "{fpgaNic-Name}",
                        primary: true,
                        privateIPAddressVersion: "IPv4",
                        subnet: {
                            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-fpga-subnet-name}",
                        },
                    }],
                    name: "{fpgaNic-Name}",
                    primary: false,
                },
            ],
        },
        osProfile: {
            adminPassword: "{your-password}",
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
        },
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
            },
        },
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="westus",
    overprovision=True,
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=3,
        name="Standard_D1_v2",
        tier="Standard",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyArgs(
        mode=azure_native.compute.UpgradeMode.MANUAL,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        network_profile={
            "networkInterfaceConfigurations": [
                {
                    "enableIPForwarding": True,
                    "ipConfigurations": [{
                        "name": "{vmss-name}",
                        "subnet": azure_native.compute.ApiEntityReferenceArgs(
                            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                        ),
                    }],
                    "name": "{vmss-name}",
                    "primary": True,
                },
                {
                    "enableAcceleratedNetworking": False,
                    "enableFpga": True,
                    "enableIPForwarding": False,
                    "ipConfigurations": [{
                        "name": "{fpgaNic-Name}",
                        "primary": True,
                        "privateIPAddressVersion": "IPv4",
                        "subnet": azure_native.compute.ApiEntityReferenceArgs(
                            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-fpga-subnet-name}",
                        ),
                    }],
                    "name": "{fpgaNic-Name}",
                    "primary": False,
                },
            ],
        },
        os_profile=azure_native.compute.VirtualMachineScaleSetOSProfileArgs(
            admin_password="{your-password}",
            admin_username="{your-username}",
            computer_name_prefix="{vmss-name}",
        ),
        storage_profile={
            "imageReference": azure_native.compute.ImageReferenceArgs(
                id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/images/{existing-custom-image-name}",
            ),
            "osDisk": {
                "caching": azure_native.compute.CachingTypes.READ_WRITE,
                "createOption": "FromImage",
                "managedDisk": azure_native.compute.VirtualMachineScaleSetManagedDiskParametersArgs(
                    storage_account_type="Standard_LRS",
                ),
            },
        },
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml
resources:
  virtualMachineScaleSet:
    type: azure-native:compute:VirtualMachineScaleSet
    properties:
      location: westus
      overprovision: true
      resourceGroupName: myResourceGroup
      sku:
        capacity: 3
        name: Standard_D1_v2
        tier: Standard
      upgradePolicy:
        mode: Manual
      virtualMachineProfile:
        networkProfile:
          networkInterfaceConfigurations:
            - enableIPForwarding: true
              ipConfigurations:
                - name: '{vmss-name}'
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}
              name: '{vmss-name}'
              primary: true
            - enableAcceleratedNetworking: false
              enableFpga: true
              enableIPForwarding: false
              ipConfigurations:
                - name: '{fpgaNic-Name}'
                  primary: true
                  privateIPAddressVersion: IPv4
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-fpga-subnet-name}
              name: '{fpgaNic-Name}'
              primary: false
        osProfile:
          adminPassword: '{your-password}'
          adminUsername: '{your-username}'
          computerNamePrefix: '{vmss-name}'
        storageProfile:
          imageReference:
            id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/images/{existing-custom-image-name}
          osDisk:
            caching: ReadWrite
            createOption: FromImage
            managedDisk:
              storageAccountType: Standard_LRS
      vmScaleSetName: '{vmss-name}'

```

{{% /example %}}
{{% example %}}
### Create a scale set with Host Encryption using encryptionAtHost property.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "westus",
        Overprovision = true,
        Plan = new AzureNative.Compute.Inputs.PlanArgs
        {
            Name = "windows2016",
            Product = "windows-data-science-vm",
            Publisher = "microsoft-ads",
        },
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 3,
            Name = "Standard_DS1_v2",
            Tier = "Standard",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            Mode = AzureNative.Compute.UpgradeMode.Manual,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminPassword = "{your-password}",
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
            },
            SecurityProfile = new AzureNative.Compute.Inputs.SecurityProfileArgs
            {
                EncryptionAtHost = true,
            },
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
                {
                    Offer = "windows-data-science-vm",
                    Publisher = "microsoft-ads",
                    Sku = "windows2016",
                    Version = "latest",
                },
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadOnly,
                    CreateOption = "FromImage",
                    ManagedDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetManagedDiskParametersArgs
                    {
                        StorageAccountType = "Standard_LRS",
                    },
                },
            },
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("westus")
            .overprovision(true)
            .plan(Map.ofEntries(
                Map.entry("name", "windows2016"),
                Map.entry("product", "windows-data-science-vm"),
                Map.entry("publisher", "microsoft-ads")
            ))
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 3),
                Map.entry("name", "Standard_DS1_v2"),
                Map.entry("tier", "Standard")
            ))
            .upgradePolicy(Map.of("mode", "Manual"))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                    )),
                    Map.entry("name", "{vmss-name}"),
                    Map.entry("primary", true)
                ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminPassword", "{your-password}"),
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}")
                )),
                Map.entry("securityProfile", Map.of("encryptionAtHost", true)),
                Map.entry("storageProfile", Map.ofEntries(
                    Map.entry("imageReference", Map.ofEntries(
                        Map.entry("offer", "windows-data-science-vm"),
                        Map.entry("publisher", "microsoft-ads"),
                        Map.entry("sku", "windows2016"),
                        Map.entry("version", "latest")
                    )),
                    Map.entry("osDisk", Map.ofEntries(
                        Map.entry("caching", "ReadOnly"),
                        Map.entry("createOption", "FromImage"),
                        Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS"))
                    ))
                ))
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "westus",
    overprovision: true,
    plan: {
        name: "windows2016",
        product: "windows-data-science-vm",
        publisher: "microsoft-ads",
    },
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 3,
        name: "Standard_DS1_v2",
        tier: "Standard",
    },
    upgradePolicy: {
        mode: azure_native.compute.UpgradeMode.Manual,
    },
    virtualMachineProfile: {
        networkProfile: {
            networkInterfaceConfigurations: [{
                enableIPForwarding: true,
                ipConfigurations: [{
                    name: "{vmss-name}",
                    subnet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    },
                }],
                name: "{vmss-name}",
                primary: true,
            }],
        },
        osProfile: {
            adminPassword: "{your-password}",
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
        },
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
            },
        },
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="westus",
    overprovision=True,
    plan=azure_native.compute.PlanArgs(
        name="windows2016",
        product="windows-data-science-vm",
        publisher="microsoft-ads",
    ),
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=3,
        name="Standard_DS1_v2",
        tier="Standard",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyArgs(
        mode=azure_native.compute.UpgradeMode.MANUAL,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        network_profile={
            "networkInterfaceConfigurations": [{
                "enableIPForwarding": True,
                "ipConfigurations": [{
                    "name": "{vmss-name}",
                    "subnet": azure_native.compute.ApiEntityReferenceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    ),
                }],
                "name": "{vmss-name}",
                "primary": True,
            }],
        },
        os_profile=azure_native.compute.VirtualMachineScaleSetOSProfileArgs(
            admin_password="{your-password}",
            admin_username="{your-username}",
            computer_name_prefix="{vmss-name}",
        ),
        security_profile=azure_native.compute.SecurityProfileArgs(
            encryption_at_host=True,
        ),
        storage_profile={
            "imageReference": azure_native.compute.ImageReferenceArgs(
                offer="windows-data-science-vm",
                publisher="microsoft-ads",
                sku="windows2016",
                version="latest",
            ),
            "osDisk": {
                "caching": azure_native.compute.CachingTypes.READ_ONLY,
                "createOption": "FromImage",
                "managedDisk": azure_native.compute.VirtualMachineScaleSetManagedDiskParametersArgs(
                    storage_account_type="Standard_LRS",
                ),
            },
        },
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml
resources:
  virtualMachineScaleSet:
    type: azure-native:compute:VirtualMachineScaleSet
    properties:
      location: westus
      overprovision: true
      plan:
        name: windows2016
        product: windows-data-science-vm
        publisher: microsoft-ads
      resourceGroupName: myResourceGroup
      sku:
        capacity: 3
        name: Standard_DS1_v2
        tier: Standard
      upgradePolicy:
        mode: Manual
      virtualMachineProfile:
        networkProfile:
          networkInterfaceConfigurations:
            - enableIPForwarding: true
              ipConfigurations:
                - name: '{vmss-name}'
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}
              name: '{vmss-name}'
              primary: true
        osProfile:
          adminPassword: '{your-password}'
          adminUsername: '{your-username}'
          computerNamePrefix: '{vmss-name}'
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
      vmScaleSetName: '{vmss-name}'

```

{{% /example %}}
{{% example %}}
### Create a scale set with OS image scheduled events enabled.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "westus",
        Overprovision = true,
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 3,
            Name = "Standard_D1_v2",
            Tier = "Standard",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            Mode = AzureNative.Compute.UpgradeMode.Manual,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminPassword = "{your-password}",
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
            },
            ScheduledEventsProfile = new AzureNative.Compute.Inputs.ScheduledEventsProfileArgs
            {
                OsImageNotificationProfile = new AzureNative.Compute.Inputs.OSImageNotificationProfileArgs
                {
                    Enable = true,
                    NotBeforeTimeout = "PT15M",
                },
            },
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
                {
                    Offer = "WindowsServer",
                    Publisher = "MicrosoftWindowsServer",
                    Sku = "2016-Datacenter",
                    Version = "latest",
                },
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                    CreateOption = "FromImage",
                    ManagedDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetManagedDiskParametersArgs
                    {
                        StorageAccountType = "Standard_LRS",
                    },
                },
            },
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("westus")
            .overprovision(true)
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 3),
                Map.entry("name", "Standard_D1_v2"),
                Map.entry("tier", "Standard")
            ))
            .upgradePolicy(Map.of("mode", "Manual"))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                    )),
                    Map.entry("name", "{vmss-name}"),
                    Map.entry("primary", true)
                ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminPassword", "{your-password}"),
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}")
                )),
                Map.entry("scheduledEventsProfile", Map.of("osImageNotificationProfile", Map.ofEntries(
                    Map.entry("enable", true),
                    Map.entry("notBeforeTimeout", "PT15M")
                ))),
                Map.entry("storageProfile", Map.ofEntries(
                    Map.entry("imageReference", Map.ofEntries(
                        Map.entry("offer", "WindowsServer"),
                        Map.entry("publisher", "MicrosoftWindowsServer"),
                        Map.entry("sku", "2016-Datacenter"),
                        Map.entry("version", "latest")
                    )),
                    Map.entry("osDisk", Map.ofEntries(
                        Map.entry("caching", "ReadWrite"),
                        Map.entry("createOption", "FromImage"),
                        Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS"))
                    ))
                ))
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "westus",
    overprovision: true,
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 3,
        name: "Standard_D1_v2",
        tier: "Standard",
    },
    upgradePolicy: {
        mode: azure_native.compute.UpgradeMode.Manual,
    },
    virtualMachineProfile: {
        networkProfile: {
            networkInterfaceConfigurations: [{
                enableIPForwarding: true,
                ipConfigurations: [{
                    name: "{vmss-name}",
                    subnet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    },
                }],
                name: "{vmss-name}",
                primary: true,
            }],
        },
        osProfile: {
            adminPassword: "{your-password}",
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
        },
        scheduledEventsProfile: {
            osImageNotificationProfile: {
                enable: true,
                notBeforeTimeout: "PT15M",
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
            },
        },
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="westus",
    overprovision=True,
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=3,
        name="Standard_D1_v2",
        tier="Standard",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyArgs(
        mode=azure_native.compute.UpgradeMode.MANUAL,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        network_profile={
            "networkInterfaceConfigurations": [{
                "enableIPForwarding": True,
                "ipConfigurations": [{
                    "name": "{vmss-name}",
                    "subnet": azure_native.compute.ApiEntityReferenceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    ),
                }],
                "name": "{vmss-name}",
                "primary": True,
            }],
        },
        os_profile=azure_native.compute.VirtualMachineScaleSetOSProfileArgs(
            admin_password="{your-password}",
            admin_username="{your-username}",
            computer_name_prefix="{vmss-name}",
        ),
        scheduled_events_profile={
            "osImageNotificationProfile": azure_native.compute.OSImageNotificationProfileArgs(
                enable=True,
                not_before_timeout="PT15M",
            ),
        },
        storage_profile={
            "imageReference": azure_native.compute.ImageReferenceArgs(
                offer="WindowsServer",
                publisher="MicrosoftWindowsServer",
                sku="2016-Datacenter",
                version="latest",
            ),
            "osDisk": {
                "caching": azure_native.compute.CachingTypes.READ_WRITE,
                "createOption": "FromImage",
                "managedDisk": azure_native.compute.VirtualMachineScaleSetManagedDiskParametersArgs(
                    storage_account_type="Standard_LRS",
                ),
            },
        },
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml
resources:
  virtualMachineScaleSet:
    type: azure-native:compute:VirtualMachineScaleSet
    properties:
      location: westus
      overprovision: true
      resourceGroupName: myResourceGroup
      sku:
        capacity: 3
        name: Standard_D1_v2
        tier: Standard
      upgradePolicy:
        mode: Manual
      virtualMachineProfile:
        networkProfile:
          networkInterfaceConfigurations:
            - enableIPForwarding: true
              ipConfigurations:
                - name: '{vmss-name}'
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}
              name: '{vmss-name}'
              primary: true
        osProfile:
          adminPassword: '{your-password}'
          adminUsername: '{your-username}'
          computerNamePrefix: '{vmss-name}'
        scheduledEventsProfile:
          osImageNotificationProfile:
            enable: true
            notBeforeTimeout: PT15M
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
      vmScaleSetName: '{vmss-name}'

```

{{% /example %}}
{{% example %}}
### Create a scale set with SecurityType as ConfidentialVM
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "westus",
        Overprovision = true,
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 3,
            Name = "Standard_DC2as_v5",
            Tier = "Standard",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            Mode = AzureNative.Compute.UpgradeMode.Manual,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminPassword = "{your-password}",
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
            },
            SecurityProfile = new AzureNative.Compute.Inputs.SecurityProfileArgs
            {
                SecurityType = "ConfidentialVM",
                UefiSettings = new AzureNative.Compute.Inputs.UefiSettingsArgs
                {
                    SecureBootEnabled = true,
                    VTpmEnabled = true,
                },
            },
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
                {
                    Offer = "2019-datacenter-cvm",
                    Publisher = "MicrosoftWindowsServer",
                    Sku = "windows-cvm",
                    Version = "17763.2183.2109130127",
                },
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadOnly,
                    CreateOption = "FromImage",
                    ManagedDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetManagedDiskParametersArgs
                    {
                        SecurityProfile = new AzureNative.Compute.Inputs.VMDiskSecurityProfileArgs
                        {
                            SecurityEncryptionType = "VMGuestStateOnly",
                        },
                        StorageAccountType = "StandardSSD_LRS",
                    },
                },
            },
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("westus")
            .overprovision(true)
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 3),
                Map.entry("name", "Standard_DC2as_v5"),
                Map.entry("tier", "Standard")
            ))
            .upgradePolicy(Map.of("mode", "Manual"))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                    )),
                    Map.entry("name", "{vmss-name}"),
                    Map.entry("primary", true)
                ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminPassword", "{your-password}"),
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}")
                )),
                Map.entry("securityProfile", Map.ofEntries(
                    Map.entry("securityType", "ConfidentialVM"),
                    Map.entry("uefiSettings", Map.ofEntries(
                        Map.entry("secureBootEnabled", true),
                        Map.entry("vTpmEnabled", true)
                    ))
                )),
                Map.entry("storageProfile", Map.ofEntries(
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
                            Map.entry("securityProfile", Map.of("securityEncryptionType", "VMGuestStateOnly")),
                            Map.entry("storageAccountType", "StandardSSD_LRS")
                        ))
                    ))
                ))
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "westus",
    overprovision: true,
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 3,
        name: "Standard_DC2as_v5",
        tier: "Standard",
    },
    upgradePolicy: {
        mode: azure_native.compute.UpgradeMode.Manual,
    },
    virtualMachineProfile: {
        networkProfile: {
            networkInterfaceConfigurations: [{
                enableIPForwarding: true,
                ipConfigurations: [{
                    name: "{vmss-name}",
                    subnet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    },
                }],
                name: "{vmss-name}",
                primary: true,
            }],
        },
        osProfile: {
            adminPassword: "{your-password}",
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
        },
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
                        securityEncryptionType: "VMGuestStateOnly",
                    },
                    storageAccountType: "StandardSSD_LRS",
                },
            },
        },
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="westus",
    overprovision=True,
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=3,
        name="Standard_DC2as_v5",
        tier="Standard",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyArgs(
        mode=azure_native.compute.UpgradeMode.MANUAL,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        network_profile={
            "networkInterfaceConfigurations": [{
                "enableIPForwarding": True,
                "ipConfigurations": [{
                    "name": "{vmss-name}",
                    "subnet": azure_native.compute.ApiEntityReferenceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    ),
                }],
                "name": "{vmss-name}",
                "primary": True,
            }],
        },
        os_profile=azure_native.compute.VirtualMachineScaleSetOSProfileArgs(
            admin_password="{your-password}",
            admin_username="{your-username}",
            computer_name_prefix="{vmss-name}",
        ),
        security_profile={
            "securityType": "ConfidentialVM",
            "uefiSettings": azure_native.compute.UefiSettingsArgs(
                secure_boot_enabled=True,
                v_tpm_enabled=True,
            ),
        },
        storage_profile={
            "imageReference": azure_native.compute.ImageReferenceArgs(
                offer="2019-datacenter-cvm",
                publisher="MicrosoftWindowsServer",
                sku="windows-cvm",
                version="17763.2183.2109130127",
            ),
            "osDisk": {
                "caching": azure_native.compute.CachingTypes.READ_ONLY,
                "createOption": "FromImage",
                "managedDisk": {
                    "securityProfile": azure_native.compute.VMDiskSecurityProfileArgs(
                        security_encryption_type="VMGuestStateOnly",
                    ),
                    "storageAccountType": "StandardSSD_LRS",
                },
            },
        },
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml
resources:
  virtualMachineScaleSet:
    type: azure-native:compute:VirtualMachineScaleSet
    properties:
      location: westus
      overprovision: true
      resourceGroupName: myResourceGroup
      sku:
        capacity: 3
        name: Standard_DC2as_v5
        tier: Standard
      upgradePolicy:
        mode: Manual
      virtualMachineProfile:
        networkProfile:
          networkInterfaceConfigurations:
            - enableIPForwarding: true
              ipConfigurations:
                - name: '{vmss-name}'
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}
              name: '{vmss-name}'
              primary: true
        osProfile:
          adminPassword: '{your-password}'
          adminUsername: '{your-username}'
          computerNamePrefix: '{vmss-name}'
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
                securityEncryptionType: VMGuestStateOnly
              storageAccountType: StandardSSD_LRS
      vmScaleSetName: '{vmss-name}'

```

{{% /example %}}
{{% example %}}
### Create a scale set with Service Artifact Reference
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "eastus2euap",
        Overprovision = true,
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 3,
            Name = "Standard_A1",
            Tier = "Standard",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            AutomaticOSUpgradePolicy = new AzureNative.Compute.Inputs.AutomaticOSUpgradePolicyArgs
            {
                EnableAutomaticOSUpgrade = true,
            },
            Mode = AzureNative.Compute.UpgradeMode.Automatic,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminPassword = "{your-password}",
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
            },
            ServiceArtifactReference = new AzureNative.Compute.Inputs.ServiceArtifactReferenceArgs
            {
                Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/galleries/myGalleryName/serviceArtifacts/serviceArtifactName/vmArtifactsProfiles/vmArtifactsProfilesName",
            },
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
                {
                    Offer = "WindowsServer",
                    Publisher = "MicrosoftWindowsServer",
                    Sku = "2022-Datacenter",
                    Version = "latest",
                },
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                    CreateOption = "FromImage",
                    Name = "osDisk",
                },
            },
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("eastus2euap")
            .overprovision(true)
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 3),
                Map.entry("name", "Standard_A1"),
                Map.entry("tier", "Standard")
            ))
            .upgradePolicy(Map.ofEntries(
                Map.entry("automaticOSUpgradePolicy", Map.of("enableAutomaticOSUpgrade", true)),
                Map.entry("mode", "Automatic")
            ))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                    )),
                    Map.entry("name", "{vmss-name}"),
                    Map.entry("primary", true)
                ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminPassword", "{your-password}"),
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}")
                )),
                Map.entry("serviceArtifactReference", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/galleries/myGalleryName/serviceArtifacts/serviceArtifactName/vmArtifactsProfiles/vmArtifactsProfilesName")),
                Map.entry("storageProfile", Map.ofEntries(
                    Map.entry("imageReference", Map.ofEntries(
                        Map.entry("offer", "WindowsServer"),
                        Map.entry("publisher", "MicrosoftWindowsServer"),
                        Map.entry("sku", "2022-Datacenter"),
                        Map.entry("version", "latest")
                    )),
                    Map.entry("osDisk", Map.ofEntries(
                        Map.entry("caching", "ReadWrite"),
                        Map.entry("createOption", "FromImage"),
                        Map.entry("name", "osDisk")
                    ))
                ))
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "eastus2euap",
    overprovision: true,
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 3,
        name: "Standard_A1",
        tier: "Standard",
    },
    upgradePolicy: {
        automaticOSUpgradePolicy: {
            enableAutomaticOSUpgrade: true,
        },
        mode: azure_native.compute.UpgradeMode.Automatic,
    },
    virtualMachineProfile: {
        networkProfile: {
            networkInterfaceConfigurations: [{
                enableIPForwarding: true,
                ipConfigurations: [{
                    name: "{vmss-name}",
                    subnet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    },
                }],
                name: "{vmss-name}",
                primary: true,
            }],
        },
        osProfile: {
            adminPassword: "{your-password}",
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
        },
        serviceArtifactReference: {
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/galleries/myGalleryName/serviceArtifacts/serviceArtifactName/vmArtifactsProfiles/vmArtifactsProfilesName",
        },
        storageProfile: {
            imageReference: {
                offer: "WindowsServer",
                publisher: "MicrosoftWindowsServer",
                sku: "2022-Datacenter",
                version: "latest",
            },
            osDisk: {
                caching: azure_native.compute.CachingTypes.ReadWrite,
                createOption: "FromImage",
                name: "osDisk",
            },
        },
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="eastus2euap",
    overprovision=True,
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=3,
        name="Standard_A1",
        tier="Standard",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyResponseArgs(
        automatic_os_upgrade_policy=azure_native.compute.AutomaticOSUpgradePolicyArgs(
            enable_automatic_os_upgrade=True,
        ),
        mode=azure_native.compute.UpgradeMode.AUTOMATIC,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        network_profile={
            "networkInterfaceConfigurations": [{
                "enableIPForwarding": True,
                "ipConfigurations": [{
                    "name": "{vmss-name}",
                    "subnet": azure_native.compute.ApiEntityReferenceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    ),
                }],
                "name": "{vmss-name}",
                "primary": True,
            }],
        },
        os_profile=azure_native.compute.VirtualMachineScaleSetOSProfileArgs(
            admin_password="{your-password}",
            admin_username="{your-username}",
            computer_name_prefix="{vmss-name}",
        ),
        service_artifact_reference=azure_native.compute.ServiceArtifactReferenceArgs(
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/galleries/myGalleryName/serviceArtifacts/serviceArtifactName/vmArtifactsProfiles/vmArtifactsProfilesName",
        ),
        storage_profile={
            "imageReference": azure_native.compute.ImageReferenceArgs(
                offer="WindowsServer",
                publisher="MicrosoftWindowsServer",
                sku="2022-Datacenter",
                version="latest",
            ),
            "osDisk": azure_native.compute.VirtualMachineScaleSetOSDiskArgs(
                caching=azure_native.compute.CachingTypes.READ_WRITE,
                create_option="FromImage",
                name="osDisk",
            ),
        },
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml
resources:
  virtualMachineScaleSet:
    type: azure-native:compute:VirtualMachineScaleSet
    properties:
      location: eastus2euap
      overprovision: true
      resourceGroupName: myResourceGroup
      sku:
        capacity: 3
        name: Standard_A1
        tier: Standard
      upgradePolicy:
        automaticOSUpgradePolicy:
          enableAutomaticOSUpgrade: true
        mode: Automatic
      virtualMachineProfile:
        networkProfile:
          networkInterfaceConfigurations:
            - enableIPForwarding: true
              ipConfigurations:
                - name: '{vmss-name}'
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}
              name: '{vmss-name}'
              primary: true
        osProfile:
          adminPassword: '{your-password}'
          adminUsername: '{your-username}'
          computerNamePrefix: '{vmss-name}'
        serviceArtifactReference:
          id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/galleries/myGalleryName/serviceArtifacts/serviceArtifactName/vmArtifactsProfiles/vmArtifactsProfilesName
        storageProfile:
          imageReference:
            offer: WindowsServer
            publisher: MicrosoftWindowsServer
            sku: 2022-Datacenter
            version: latest
          osDisk:
            caching: ReadWrite
            createOption: FromImage
            name: osDisk
      vmScaleSetName: '{vmss-name}'

```

{{% /example %}}
{{% example %}}
### Create a scale set with Uefi Settings of secureBoot and vTPM.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "westus",
        Overprovision = true,
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 3,
            Name = "Standard_D2s_v3",
            Tier = "Standard",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            Mode = AzureNative.Compute.UpgradeMode.Manual,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminPassword = "{your-password}",
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
            },
            SecurityProfile = new AzureNative.Compute.Inputs.SecurityProfileArgs
            {
                SecurityType = "TrustedLaunch",
                UefiSettings = new AzureNative.Compute.Inputs.UefiSettingsArgs
                {
                    SecureBootEnabled = true,
                    VTpmEnabled = true,
                },
            },
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
                {
                    Offer = "windowsserver-gen2preview-preview",
                    Publisher = "MicrosoftWindowsServer",
                    Sku = "windows10-tvm",
                    Version = "18363.592.2001092016",
                },
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadOnly,
                    CreateOption = "FromImage",
                    ManagedDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetManagedDiskParametersArgs
                    {
                        StorageAccountType = "StandardSSD_LRS",
                    },
                },
            },
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("westus")
            .overprovision(true)
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 3),
                Map.entry("name", "Standard_D2s_v3"),
                Map.entry("tier", "Standard")
            ))
            .upgradePolicy(Map.of("mode", "Manual"))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                    )),
                    Map.entry("name", "{vmss-name}"),
                    Map.entry("primary", true)
                ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminPassword", "{your-password}"),
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}")
                )),
                Map.entry("securityProfile", Map.ofEntries(
                    Map.entry("securityType", "TrustedLaunch"),
                    Map.entry("uefiSettings", Map.ofEntries(
                        Map.entry("secureBootEnabled", true),
                        Map.entry("vTpmEnabled", true)
                    ))
                )),
                Map.entry("storageProfile", Map.ofEntries(
                    Map.entry("imageReference", Map.ofEntries(
                        Map.entry("offer", "windowsserver-gen2preview-preview"),
                        Map.entry("publisher", "MicrosoftWindowsServer"),
                        Map.entry("sku", "windows10-tvm"),
                        Map.entry("version", "18363.592.2001092016")
                    )),
                    Map.entry("osDisk", Map.ofEntries(
                        Map.entry("caching", "ReadOnly"),
                        Map.entry("createOption", "FromImage"),
                        Map.entry("managedDisk", Map.of("storageAccountType", "StandardSSD_LRS"))
                    ))
                ))
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "westus",
    overprovision: true,
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 3,
        name: "Standard_D2s_v3",
        tier: "Standard",
    },
    upgradePolicy: {
        mode: azure_native.compute.UpgradeMode.Manual,
    },
    virtualMachineProfile: {
        networkProfile: {
            networkInterfaceConfigurations: [{
                enableIPForwarding: true,
                ipConfigurations: [{
                    name: "{vmss-name}",
                    subnet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    },
                }],
                name: "{vmss-name}",
                primary: true,
            }],
        },
        osProfile: {
            adminPassword: "{your-password}",
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
        },
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
            },
        },
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="westus",
    overprovision=True,
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=3,
        name="Standard_D2s_v3",
        tier="Standard",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyArgs(
        mode=azure_native.compute.UpgradeMode.MANUAL,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        network_profile={
            "networkInterfaceConfigurations": [{
                "enableIPForwarding": True,
                "ipConfigurations": [{
                    "name": "{vmss-name}",
                    "subnet": azure_native.compute.ApiEntityReferenceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    ),
                }],
                "name": "{vmss-name}",
                "primary": True,
            }],
        },
        os_profile=azure_native.compute.VirtualMachineScaleSetOSProfileArgs(
            admin_password="{your-password}",
            admin_username="{your-username}",
            computer_name_prefix="{vmss-name}",
        ),
        security_profile={
            "securityType": "TrustedLaunch",
            "uefiSettings": azure_native.compute.UefiSettingsArgs(
                secure_boot_enabled=True,
                v_tpm_enabled=True,
            ),
        },
        storage_profile={
            "imageReference": azure_native.compute.ImageReferenceArgs(
                offer="windowsserver-gen2preview-preview",
                publisher="MicrosoftWindowsServer",
                sku="windows10-tvm",
                version="18363.592.2001092016",
            ),
            "osDisk": {
                "caching": azure_native.compute.CachingTypes.READ_ONLY,
                "createOption": "FromImage",
                "managedDisk": azure_native.compute.VirtualMachineScaleSetManagedDiskParametersArgs(
                    storage_account_type="StandardSSD_LRS",
                ),
            },
        },
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml
resources:
  virtualMachineScaleSet:
    type: azure-native:compute:VirtualMachineScaleSet
    properties:
      location: westus
      overprovision: true
      resourceGroupName: myResourceGroup
      sku:
        capacity: 3
        name: Standard_D2s_v3
        tier: Standard
      upgradePolicy:
        mode: Manual
      virtualMachineProfile:
        networkProfile:
          networkInterfaceConfigurations:
            - enableIPForwarding: true
              ipConfigurations:
                - name: '{vmss-name}'
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}
              name: '{vmss-name}'
              primary: true
        osProfile:
          adminPassword: '{your-password}'
          adminUsername: '{your-username}'
          computerNamePrefix: '{vmss-name}'
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
      vmScaleSetName: '{vmss-name}'

```

{{% /example %}}
{{% example %}}
### Create a scale set with a marketplace image plan.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "westus",
        Overprovision = true,
        Plan = new AzureNative.Compute.Inputs.PlanArgs
        {
            Name = "windows2016",
            Product = "windows-data-science-vm",
            Publisher = "microsoft-ads",
        },
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 3,
            Name = "Standard_D1_v2",
            Tier = "Standard",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            Mode = AzureNative.Compute.UpgradeMode.Manual,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminPassword = "{your-password}",
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
            },
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
                {
                    Offer = "windows-data-science-vm",
                    Publisher = "microsoft-ads",
                    Sku = "windows2016",
                    Version = "latest",
                },
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                    CreateOption = "FromImage",
                    ManagedDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetManagedDiskParametersArgs
                    {
                        StorageAccountType = "Standard_LRS",
                    },
                },
            },
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("westus")
            .overprovision(true)
            .plan(Map.ofEntries(
                Map.entry("name", "windows2016"),
                Map.entry("product", "windows-data-science-vm"),
                Map.entry("publisher", "microsoft-ads")
            ))
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 3),
                Map.entry("name", "Standard_D1_v2"),
                Map.entry("tier", "Standard")
            ))
            .upgradePolicy(Map.of("mode", "Manual"))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                    )),
                    Map.entry("name", "{vmss-name}"),
                    Map.entry("primary", true)
                ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminPassword", "{your-password}"),
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}")
                )),
                Map.entry("storageProfile", Map.ofEntries(
                    Map.entry("imageReference", Map.ofEntries(
                        Map.entry("offer", "windows-data-science-vm"),
                        Map.entry("publisher", "microsoft-ads"),
                        Map.entry("sku", "windows2016"),
                        Map.entry("version", "latest")
                    )),
                    Map.entry("osDisk", Map.ofEntries(
                        Map.entry("caching", "ReadWrite"),
                        Map.entry("createOption", "FromImage"),
                        Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS"))
                    ))
                ))
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "westus",
    overprovision: true,
    plan: {
        name: "windows2016",
        product: "windows-data-science-vm",
        publisher: "microsoft-ads",
    },
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 3,
        name: "Standard_D1_v2",
        tier: "Standard",
    },
    upgradePolicy: {
        mode: azure_native.compute.UpgradeMode.Manual,
    },
    virtualMachineProfile: {
        networkProfile: {
            networkInterfaceConfigurations: [{
                enableIPForwarding: true,
                ipConfigurations: [{
                    name: "{vmss-name}",
                    subnet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    },
                }],
                name: "{vmss-name}",
                primary: true,
            }],
        },
        osProfile: {
            adminPassword: "{your-password}",
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
        },
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
            },
        },
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="westus",
    overprovision=True,
    plan=azure_native.compute.PlanArgs(
        name="windows2016",
        product="windows-data-science-vm",
        publisher="microsoft-ads",
    ),
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=3,
        name="Standard_D1_v2",
        tier="Standard",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyArgs(
        mode=azure_native.compute.UpgradeMode.MANUAL,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        network_profile={
            "networkInterfaceConfigurations": [{
                "enableIPForwarding": True,
                "ipConfigurations": [{
                    "name": "{vmss-name}",
                    "subnet": azure_native.compute.ApiEntityReferenceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    ),
                }],
                "name": "{vmss-name}",
                "primary": True,
            }],
        },
        os_profile=azure_native.compute.VirtualMachineScaleSetOSProfileArgs(
            admin_password="{your-password}",
            admin_username="{your-username}",
            computer_name_prefix="{vmss-name}",
        ),
        storage_profile={
            "imageReference": azure_native.compute.ImageReferenceArgs(
                offer="windows-data-science-vm",
                publisher="microsoft-ads",
                sku="windows2016",
                version="latest",
            ),
            "osDisk": {
                "caching": azure_native.compute.CachingTypes.READ_WRITE,
                "createOption": "FromImage",
                "managedDisk": azure_native.compute.VirtualMachineScaleSetManagedDiskParametersArgs(
                    storage_account_type="Standard_LRS",
                ),
            },
        },
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml
resources:
  virtualMachineScaleSet:
    type: azure-native:compute:VirtualMachineScaleSet
    properties:
      location: westus
      overprovision: true
      plan:
        name: windows2016
        product: windows-data-science-vm
        publisher: microsoft-ads
      resourceGroupName: myResourceGroup
      sku:
        capacity: 3
        name: Standard_D1_v2
        tier: Standard
      upgradePolicy:
        mode: Manual
      virtualMachineProfile:
        networkProfile:
          networkInterfaceConfigurations:
            - enableIPForwarding: true
              ipConfigurations:
                - name: '{vmss-name}'
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}
              name: '{vmss-name}'
              primary: true
        osProfile:
          adminPassword: '{your-password}'
          adminUsername: '{your-username}'
          computerNamePrefix: '{vmss-name}'
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
      vmScaleSetName: '{vmss-name}'

```

{{% /example %}}
{{% example %}}
### Create a scale set with an azure application gateway.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "westus",
        Overprovision = true,
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 3,
            Name = "Standard_D1_v2",
            Tier = "Standard",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            Mode = AzureNative.Compute.UpgradeMode.Manual,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                ApplicationGatewayBackendAddressPools = new[]
                                {
                                    new AzureNative.Compute.Inputs.SubResourceArgs
                                    {
                                        Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/applicationGateways/{existing-application-gateway-name}/backendAddressPools/{existing-backend-address-pool-name}",
                                    },
                                },
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminPassword = "{your-password}",
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
            },
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
                {
                    Offer = "WindowsServer",
                    Publisher = "MicrosoftWindowsServer",
                    Sku = "2016-Datacenter",
                    Version = "latest",
                },
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                    CreateOption = "FromImage",
                    ManagedDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetManagedDiskParametersArgs
                    {
                        StorageAccountType = "Standard_LRS",
                    },
                },
            },
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("westus")
            .overprovision(true)
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 3),
                Map.entry("name", "Standard_D1_v2"),
                Map.entry("tier", "Standard")
            ))
            .upgradePolicy(Map.of("mode", "Manual"))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("applicationGatewayBackendAddressPools", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/applicationGateways/{existing-application-gateway-name}/backendAddressPools/{existing-backend-address-pool-name}")),
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                    )),
                    Map.entry("name", "{vmss-name}"),
                    Map.entry("primary", true)
                ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminPassword", "{your-password}"),
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}")
                )),
                Map.entry("storageProfile", Map.ofEntries(
                    Map.entry("imageReference", Map.ofEntries(
                        Map.entry("offer", "WindowsServer"),
                        Map.entry("publisher", "MicrosoftWindowsServer"),
                        Map.entry("sku", "2016-Datacenter"),
                        Map.entry("version", "latest")
                    )),
                    Map.entry("osDisk", Map.ofEntries(
                        Map.entry("caching", "ReadWrite"),
                        Map.entry("createOption", "FromImage"),
                        Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS"))
                    ))
                ))
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "westus",
    overprovision: true,
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 3,
        name: "Standard_D1_v2",
        tier: "Standard",
    },
    upgradePolicy: {
        mode: azure_native.compute.UpgradeMode.Manual,
    },
    virtualMachineProfile: {
        networkProfile: {
            networkInterfaceConfigurations: [{
                enableIPForwarding: true,
                ipConfigurations: [{
                    applicationGatewayBackendAddressPools: [{
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/applicationGateways/{existing-application-gateway-name}/backendAddressPools/{existing-backend-address-pool-name}",
                    }],
                    name: "{vmss-name}",
                    subnet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    },
                }],
                name: "{vmss-name}",
                primary: true,
            }],
        },
        osProfile: {
            adminPassword: "{your-password}",
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
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
            },
        },
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="westus",
    overprovision=True,
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=3,
        name="Standard_D1_v2",
        tier="Standard",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyArgs(
        mode=azure_native.compute.UpgradeMode.MANUAL,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        network_profile={
            "networkInterfaceConfigurations": [{
                "enableIPForwarding": True,
                "ipConfigurations": [{
                    "applicationGatewayBackendAddressPools": [azure_native.compute.SubResourceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/applicationGateways/{existing-application-gateway-name}/backendAddressPools/{existing-backend-address-pool-name}",
                    )],
                    "name": "{vmss-name}",
                    "subnet": azure_native.compute.ApiEntityReferenceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    ),
                }],
                "name": "{vmss-name}",
                "primary": True,
            }],
        },
        os_profile=azure_native.compute.VirtualMachineScaleSetOSProfileArgs(
            admin_password="{your-password}",
            admin_username="{your-username}",
            computer_name_prefix="{vmss-name}",
        ),
        storage_profile={
            "imageReference": azure_native.compute.ImageReferenceArgs(
                offer="WindowsServer",
                publisher="MicrosoftWindowsServer",
                sku="2016-Datacenter",
                version="latest",
            ),
            "osDisk": {
                "caching": azure_native.compute.CachingTypes.READ_WRITE,
                "createOption": "FromImage",
                "managedDisk": azure_native.compute.VirtualMachineScaleSetManagedDiskParametersArgs(
                    storage_account_type="Standard_LRS",
                ),
            },
        },
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml
resources:
  virtualMachineScaleSet:
    type: azure-native:compute:VirtualMachineScaleSet
    properties:
      location: westus
      overprovision: true
      resourceGroupName: myResourceGroup
      sku:
        capacity: 3
        name: Standard_D1_v2
        tier: Standard
      upgradePolicy:
        mode: Manual
      virtualMachineProfile:
        networkProfile:
          networkInterfaceConfigurations:
            - enableIPForwarding: true
              ipConfigurations:
                - applicationGatewayBackendAddressPools:
                    - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/applicationGateways/{existing-application-gateway-name}/backendAddressPools/{existing-backend-address-pool-name}
                  name: '{vmss-name}'
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}
              name: '{vmss-name}'
              primary: true
        osProfile:
          adminPassword: '{your-password}'
          adminUsername: '{your-username}'
          computerNamePrefix: '{vmss-name}'
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
      vmScaleSetName: '{vmss-name}'

```

{{% /example %}}
{{% example %}}
### Create a scale set with an azure load balancer.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "westus",
        Overprovision = true,
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 3,
            Name = "Standard_D1_v2",
            Tier = "Standard",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            Mode = AzureNative.Compute.UpgradeMode.Manual,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                LoadBalancerBackendAddressPools = new[]
                                {
                                    new AzureNative.Compute.Inputs.SubResourceArgs
                                    {
                                        Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/loadBalancers/{existing-load-balancer-name}/backendAddressPools/{existing-backend-address-pool-name}",
                                    },
                                },
                                LoadBalancerInboundNatPools = new[]
                                {
                                    new AzureNative.Compute.Inputs.SubResourceArgs
                                    {
                                        Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/loadBalancers/{existing-load-balancer-name}/inboundNatPools/{existing-nat-pool-name}",
                                    },
                                },
                                Name = "{vmss-name}",
                                PublicIPAddressConfiguration = new AzureNative.Compute.Inputs.VirtualMachineScaleSetPublicIPAddressConfigurationArgs
                                {
                                    Name = "{vmss-name}",
                                    PublicIPAddressVersion = "IPv4",
                                },
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminPassword = "{your-password}",
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
            },
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
                {
                    Offer = "WindowsServer",
                    Publisher = "MicrosoftWindowsServer",
                    Sku = "2016-Datacenter",
                    Version = "latest",
                },
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                    CreateOption = "FromImage",
                    ManagedDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetManagedDiskParametersArgs
                    {
                        StorageAccountType = "Standard_LRS",
                    },
                },
            },
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("westus")
            .overprovision(true)
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 3),
                Map.entry("name", "Standard_D1_v2"),
                Map.entry("tier", "Standard")
            ))
            .upgradePolicy(Map.of("mode", "Manual"))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("loadBalancerBackendAddressPools", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/loadBalancers/{existing-load-balancer-name}/backendAddressPools/{existing-backend-address-pool-name}")),
                        Map.entry("loadBalancerInboundNatPools", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/loadBalancers/{existing-load-balancer-name}/inboundNatPools/{existing-nat-pool-name}")),
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("publicIPAddressConfiguration", Map.ofEntries(
                            Map.entry("name", "{vmss-name}"),
                            Map.entry("publicIPAddressVersion", "IPv4")
                        )),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                    )),
                    Map.entry("name", "{vmss-name}"),
                    Map.entry("primary", true)
                ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminPassword", "{your-password}"),
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}")
                )),
                Map.entry("storageProfile", Map.ofEntries(
                    Map.entry("imageReference", Map.ofEntries(
                        Map.entry("offer", "WindowsServer"),
                        Map.entry("publisher", "MicrosoftWindowsServer"),
                        Map.entry("sku", "2016-Datacenter"),
                        Map.entry("version", "latest")
                    )),
                    Map.entry("osDisk", Map.ofEntries(
                        Map.entry("caching", "ReadWrite"),
                        Map.entry("createOption", "FromImage"),
                        Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS"))
                    ))
                ))
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "westus",
    overprovision: true,
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 3,
        name: "Standard_D1_v2",
        tier: "Standard",
    },
    upgradePolicy: {
        mode: azure_native.compute.UpgradeMode.Manual,
    },
    virtualMachineProfile: {
        networkProfile: {
            networkInterfaceConfigurations: [{
                enableIPForwarding: true,
                ipConfigurations: [{
                    loadBalancerBackendAddressPools: [{
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/loadBalancers/{existing-load-balancer-name}/backendAddressPools/{existing-backend-address-pool-name}",
                    }],
                    loadBalancerInboundNatPools: [{
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/loadBalancers/{existing-load-balancer-name}/inboundNatPools/{existing-nat-pool-name}",
                    }],
                    name: "{vmss-name}",
                    publicIPAddressConfiguration: {
                        name: "{vmss-name}",
                        publicIPAddressVersion: "IPv4",
                    },
                    subnet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    },
                }],
                name: "{vmss-name}",
                primary: true,
            }],
        },
        osProfile: {
            adminPassword: "{your-password}",
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
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
            },
        },
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="westus",
    overprovision=True,
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=3,
        name="Standard_D1_v2",
        tier="Standard",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyArgs(
        mode=azure_native.compute.UpgradeMode.MANUAL,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        network_profile={
            "networkInterfaceConfigurations": [{
                "enableIPForwarding": True,
                "ipConfigurations": [{
                    "loadBalancerBackendAddressPools": [azure_native.compute.SubResourceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/loadBalancers/{existing-load-balancer-name}/backendAddressPools/{existing-backend-address-pool-name}",
                    )],
                    "loadBalancerInboundNatPools": [azure_native.compute.SubResourceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/loadBalancers/{existing-load-balancer-name}/inboundNatPools/{existing-nat-pool-name}",
                    )],
                    "name": "{vmss-name}",
                    "publicIPAddressConfiguration": azure_native.compute.VirtualMachineScaleSetPublicIPAddressConfigurationArgs(
                        name="{vmss-name}",
                        public_ip_address_version="IPv4",
                    ),
                    "subnet": azure_native.compute.ApiEntityReferenceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    ),
                }],
                "name": "{vmss-name}",
                "primary": True,
            }],
        },
        os_profile=azure_native.compute.VirtualMachineScaleSetOSProfileArgs(
            admin_password="{your-password}",
            admin_username="{your-username}",
            computer_name_prefix="{vmss-name}",
        ),
        storage_profile={
            "imageReference": azure_native.compute.ImageReferenceArgs(
                offer="WindowsServer",
                publisher="MicrosoftWindowsServer",
                sku="2016-Datacenter",
                version="latest",
            ),
            "osDisk": {
                "caching": azure_native.compute.CachingTypes.READ_WRITE,
                "createOption": "FromImage",
                "managedDisk": azure_native.compute.VirtualMachineScaleSetManagedDiskParametersArgs(
                    storage_account_type="Standard_LRS",
                ),
            },
        },
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml
resources:
  virtualMachineScaleSet:
    type: azure-native:compute:VirtualMachineScaleSet
    properties:
      location: westus
      overprovision: true
      resourceGroupName: myResourceGroup
      sku:
        capacity: 3
        name: Standard_D1_v2
        tier: Standard
      upgradePolicy:
        mode: Manual
      virtualMachineProfile:
        networkProfile:
          networkInterfaceConfigurations:
            - enableIPForwarding: true
              ipConfigurations:
                - loadBalancerBackendAddressPools:
                    - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/loadBalancers/{existing-load-balancer-name}/backendAddressPools/{existing-backend-address-pool-name}
                  loadBalancerInboundNatPools:
                    - id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/loadBalancers/{existing-load-balancer-name}/inboundNatPools/{existing-nat-pool-name}
                  name: '{vmss-name}'
                  publicIPAddressConfiguration:
                    name: '{vmss-name}'
                    publicIPAddressVersion: IPv4
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}
              name: '{vmss-name}'
              primary: true
        osProfile:
          adminPassword: '{your-password}'
          adminUsername: '{your-username}'
          computerNamePrefix: '{vmss-name}'
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
      vmScaleSetName: '{vmss-name}'

```

{{% /example %}}
{{% example %}}
### Create a scale set with automatic repairs enabled
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        AutomaticRepairsPolicy = new AzureNative.Compute.Inputs.AutomaticRepairsPolicyArgs
        {
            Enabled = true,
            GracePeriod = "PT10M",
        },
        Location = "westus",
        Overprovision = true,
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 3,
            Name = "Standard_D1_v2",
            Tier = "Standard",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            Mode = AzureNative.Compute.UpgradeMode.Manual,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminPassword = "{your-password}",
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
            },
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
                {
                    Offer = "WindowsServer",
                    Publisher = "MicrosoftWindowsServer",
                    Sku = "2016-Datacenter",
                    Version = "latest",
                },
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                    CreateOption = "FromImage",
                    ManagedDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetManagedDiskParametersArgs
                    {
                        StorageAccountType = "Standard_LRS",
                    },
                },
            },
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .automaticRepairsPolicy(Map.ofEntries(
                Map.entry("enabled", true),
                Map.entry("gracePeriod", "PT10M")
            ))
            .location("westus")
            .overprovision(true)
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 3),
                Map.entry("name", "Standard_D1_v2"),
                Map.entry("tier", "Standard")
            ))
            .upgradePolicy(Map.of("mode", "Manual"))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                    )),
                    Map.entry("name", "{vmss-name}"),
                    Map.entry("primary", true)
                ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminPassword", "{your-password}"),
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}")
                )),
                Map.entry("storageProfile", Map.ofEntries(
                    Map.entry("imageReference", Map.ofEntries(
                        Map.entry("offer", "WindowsServer"),
                        Map.entry("publisher", "MicrosoftWindowsServer"),
                        Map.entry("sku", "2016-Datacenter"),
                        Map.entry("version", "latest")
                    )),
                    Map.entry("osDisk", Map.ofEntries(
                        Map.entry("caching", "ReadWrite"),
                        Map.entry("createOption", "FromImage"),
                        Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS"))
                    ))
                ))
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    automaticRepairsPolicy: {
        enabled: true,
        gracePeriod: "PT10M",
    },
    location: "westus",
    overprovision: true,
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 3,
        name: "Standard_D1_v2",
        tier: "Standard",
    },
    upgradePolicy: {
        mode: azure_native.compute.UpgradeMode.Manual,
    },
    virtualMachineProfile: {
        networkProfile: {
            networkInterfaceConfigurations: [{
                enableIPForwarding: true,
                ipConfigurations: [{
                    name: "{vmss-name}",
                    subnet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    },
                }],
                name: "{vmss-name}",
                primary: true,
            }],
        },
        osProfile: {
            adminPassword: "{your-password}",
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
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
            },
        },
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    automatic_repairs_policy=azure_native.compute.AutomaticRepairsPolicyArgs(
        enabled=True,
        grace_period="PT10M",
    ),
    location="westus",
    overprovision=True,
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=3,
        name="Standard_D1_v2",
        tier="Standard",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyArgs(
        mode=azure_native.compute.UpgradeMode.MANUAL,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        network_profile={
            "networkInterfaceConfigurations": [{
                "enableIPForwarding": True,
                "ipConfigurations": [{
                    "name": "{vmss-name}",
                    "subnet": azure_native.compute.ApiEntityReferenceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    ),
                }],
                "name": "{vmss-name}",
                "primary": True,
            }],
        },
        os_profile=azure_native.compute.VirtualMachineScaleSetOSProfileArgs(
            admin_password="{your-password}",
            admin_username="{your-username}",
            computer_name_prefix="{vmss-name}",
        ),
        storage_profile={
            "imageReference": azure_native.compute.ImageReferenceArgs(
                offer="WindowsServer",
                publisher="MicrosoftWindowsServer",
                sku="2016-Datacenter",
                version="latest",
            ),
            "osDisk": {
                "caching": azure_native.compute.CachingTypes.READ_WRITE,
                "createOption": "FromImage",
                "managedDisk": azure_native.compute.VirtualMachineScaleSetManagedDiskParametersArgs(
                    storage_account_type="Standard_LRS",
                ),
            },
        },
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml
resources:
  virtualMachineScaleSet:
    type: azure-native:compute:VirtualMachineScaleSet
    properties:
      automaticRepairsPolicy:
        enabled: true
        gracePeriod: PT10M
      location: westus
      overprovision: true
      resourceGroupName: myResourceGroup
      sku:
        capacity: 3
        name: Standard_D1_v2
        tier: Standard
      upgradePolicy:
        mode: Manual
      virtualMachineProfile:
        networkProfile:
          networkInterfaceConfigurations:
            - enableIPForwarding: true
              ipConfigurations:
                - name: '{vmss-name}'
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}
              name: '{vmss-name}'
              primary: true
        osProfile:
          adminPassword: '{your-password}'
          adminUsername: '{your-username}'
          computerNamePrefix: '{vmss-name}'
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
      vmScaleSetName: '{vmss-name}'

```

{{% /example %}}
{{% example %}}
### Create a scale set with boot diagnostics.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "westus",
        Overprovision = true,
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 3,
            Name = "Standard_D1_v2",
            Tier = "Standard",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            Mode = AzureNative.Compute.UpgradeMode.Manual,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            DiagnosticsProfile = new AzureNative.Compute.Inputs.DiagnosticsProfileArgs
            {
                BootDiagnostics = new AzureNative.Compute.Inputs.BootDiagnosticsArgs
                {
                    Enabled = true,
                    StorageUri = "http://{existing-storage-account-name}.blob.core.windows.net",
                },
            },
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminPassword = "{your-password}",
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
            },
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
                {
                    Offer = "WindowsServer",
                    Publisher = "MicrosoftWindowsServer",
                    Sku = "2016-Datacenter",
                    Version = "latest",
                },
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                    CreateOption = "FromImage",
                    ManagedDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetManagedDiskParametersArgs
                    {
                        StorageAccountType = "Standard_LRS",
                    },
                },
            },
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("westus")
            .overprovision(true)
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 3),
                Map.entry("name", "Standard_D1_v2"),
                Map.entry("tier", "Standard")
            ))
            .upgradePolicy(Map.of("mode", "Manual"))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("diagnosticsProfile", Map.of("bootDiagnostics", Map.ofEntries(
                    Map.entry("enabled", true),
                    Map.entry("storageUri", "http://{existing-storage-account-name}.blob.core.windows.net")
                ))),
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                    )),
                    Map.entry("name", "{vmss-name}"),
                    Map.entry("primary", true)
                ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminPassword", "{your-password}"),
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}")
                )),
                Map.entry("storageProfile", Map.ofEntries(
                    Map.entry("imageReference", Map.ofEntries(
                        Map.entry("offer", "WindowsServer"),
                        Map.entry("publisher", "MicrosoftWindowsServer"),
                        Map.entry("sku", "2016-Datacenter"),
                        Map.entry("version", "latest")
                    )),
                    Map.entry("osDisk", Map.ofEntries(
                        Map.entry("caching", "ReadWrite"),
                        Map.entry("createOption", "FromImage"),
                        Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS"))
                    ))
                ))
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "westus",
    overprovision: true,
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 3,
        name: "Standard_D1_v2",
        tier: "Standard",
    },
    upgradePolicy: {
        mode: azure_native.compute.UpgradeMode.Manual,
    },
    virtualMachineProfile: {
        diagnosticsProfile: {
            bootDiagnostics: {
                enabled: true,
                storageUri: "http://{existing-storage-account-name}.blob.core.windows.net",
            },
        },
        networkProfile: {
            networkInterfaceConfigurations: [{
                enableIPForwarding: true,
                ipConfigurations: [{
                    name: "{vmss-name}",
                    subnet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    },
                }],
                name: "{vmss-name}",
                primary: true,
            }],
        },
        osProfile: {
            adminPassword: "{your-password}",
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
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
            },
        },
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="westus",
    overprovision=True,
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=3,
        name="Standard_D1_v2",
        tier="Standard",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyArgs(
        mode=azure_native.compute.UpgradeMode.MANUAL,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        diagnostics_profile={
            "bootDiagnostics": azure_native.compute.BootDiagnosticsArgs(
                enabled=True,
                storage_uri="http://{existing-storage-account-name}.blob.core.windows.net",
            ),
        },
        network_profile={
            "networkInterfaceConfigurations": [{
                "enableIPForwarding": True,
                "ipConfigurations": [{
                    "name": "{vmss-name}",
                    "subnet": azure_native.compute.ApiEntityReferenceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    ),
                }],
                "name": "{vmss-name}",
                "primary": True,
            }],
        },
        os_profile=azure_native.compute.VirtualMachineScaleSetOSProfileArgs(
            admin_password="{your-password}",
            admin_username="{your-username}",
            computer_name_prefix="{vmss-name}",
        ),
        storage_profile={
            "imageReference": azure_native.compute.ImageReferenceArgs(
                offer="WindowsServer",
                publisher="MicrosoftWindowsServer",
                sku="2016-Datacenter",
                version="latest",
            ),
            "osDisk": {
                "caching": azure_native.compute.CachingTypes.READ_WRITE,
                "createOption": "FromImage",
                "managedDisk": azure_native.compute.VirtualMachineScaleSetManagedDiskParametersArgs(
                    storage_account_type="Standard_LRS",
                ),
            },
        },
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml
resources:
  virtualMachineScaleSet:
    type: azure-native:compute:VirtualMachineScaleSet
    properties:
      location: westus
      overprovision: true
      resourceGroupName: myResourceGroup
      sku:
        capacity: 3
        name: Standard_D1_v2
        tier: Standard
      upgradePolicy:
        mode: Manual
      virtualMachineProfile:
        diagnosticsProfile:
          bootDiagnostics:
            enabled: true
            storageUri: http://{existing-storage-account-name}.blob.core.windows.net
        networkProfile:
          networkInterfaceConfigurations:
            - enableIPForwarding: true
              ipConfigurations:
                - name: '{vmss-name}'
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}
              name: '{vmss-name}'
              primary: true
        osProfile:
          adminPassword: '{your-password}'
          adminUsername: '{your-username}'
          computerNamePrefix: '{vmss-name}'
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
      vmScaleSetName: '{vmss-name}'

```

{{% /example %}}
{{% example %}}
### Create a scale set with empty data disks on each vm.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "westus",
        Overprovision = true,
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 3,
            Name = "Standard_D2_v2",
            Tier = "Standard",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            Mode = AzureNative.Compute.UpgradeMode.Manual,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminPassword = "{your-password}",
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
            },
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                DataDisks = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetDataDiskArgs
                    {
                        CreateOption = "Empty",
                        DiskSizeGB = 1023,
                        Lun = 0,
                    },
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetDataDiskArgs
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
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                    CreateOption = "FromImage",
                    DiskSizeGB = 512,
                    ManagedDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetManagedDiskParametersArgs
                    {
                        StorageAccountType = "Standard_LRS",
                    },
                },
            },
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("westus")
            .overprovision(true)
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 3),
                Map.entry("name", "Standard_D2_v2"),
                Map.entry("tier", "Standard")
            ))
            .upgradePolicy(Map.of("mode", "Manual"))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                    )),
                    Map.entry("name", "{vmss-name}"),
                    Map.entry("primary", true)
                ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminPassword", "{your-password}"),
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}")
                )),
                Map.entry("storageProfile", Map.ofEntries(
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
                        Map.entry("diskSizeGB", 512),
                        Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS"))
                    ))
                ))
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "westus",
    overprovision: true,
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 3,
        name: "Standard_D2_v2",
        tier: "Standard",
    },
    upgradePolicy: {
        mode: azure_native.compute.UpgradeMode.Manual,
    },
    virtualMachineProfile: {
        networkProfile: {
            networkInterfaceConfigurations: [{
                enableIPForwarding: true,
                ipConfigurations: [{
                    name: "{vmss-name}",
                    subnet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    },
                }],
                name: "{vmss-name}",
                primary: true,
            }],
        },
        osProfile: {
            adminPassword: "{your-password}",
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
        },
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
                diskSizeGB: 512,
                managedDisk: {
                    storageAccountType: "Standard_LRS",
                },
            },
        },
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="westus",
    overprovision=True,
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=3,
        name="Standard_D2_v2",
        tier="Standard",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyArgs(
        mode=azure_native.compute.UpgradeMode.MANUAL,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        network_profile={
            "networkInterfaceConfigurations": [{
                "enableIPForwarding": True,
                "ipConfigurations": [{
                    "name": "{vmss-name}",
                    "subnet": azure_native.compute.ApiEntityReferenceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    ),
                }],
                "name": "{vmss-name}",
                "primary": True,
            }],
        },
        os_profile=azure_native.compute.VirtualMachineScaleSetOSProfileArgs(
            admin_password="{your-password}",
            admin_username="{your-username}",
            computer_name_prefix="{vmss-name}",
        ),
        storage_profile={
            "dataDisks": [
                azure_native.compute.VirtualMachineScaleSetDataDiskArgs(
                    create_option="Empty",
                    disk_size_gb=1023,
                    lun=0,
                ),
                azure_native.compute.VirtualMachineScaleSetDataDiskArgs(
                    create_option="Empty",
                    disk_size_gb=1023,
                    lun=1,
                ),
            ],
            "imageReference": azure_native.compute.ImageReferenceArgs(
                offer="WindowsServer",
                publisher="MicrosoftWindowsServer",
                sku="2016-Datacenter",
                version="latest",
            ),
            "osDisk": {
                "caching": azure_native.compute.CachingTypes.READ_WRITE,
                "createOption": "FromImage",
                "diskSizeGB": 512,
                "managedDisk": azure_native.compute.VirtualMachineScaleSetManagedDiskParametersArgs(
                    storage_account_type="Standard_LRS",
                ),
            },
        },
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml
resources:
  virtualMachineScaleSet:
    type: azure-native:compute:VirtualMachineScaleSet
    properties:
      location: westus
      overprovision: true
      resourceGroupName: myResourceGroup
      sku:
        capacity: 3
        name: Standard_D2_v2
        tier: Standard
      upgradePolicy:
        mode: Manual
      virtualMachineProfile:
        networkProfile:
          networkInterfaceConfigurations:
            - enableIPForwarding: true
              ipConfigurations:
                - name: '{vmss-name}'
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}
              name: '{vmss-name}'
              primary: true
        osProfile:
          adminPassword: '{your-password}'
          adminUsername: '{your-username}'
          computerNamePrefix: '{vmss-name}'
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
            diskSizeGB: 512
            managedDisk:
              storageAccountType: Standard_LRS
      vmScaleSetName: '{vmss-name}'

```

{{% /example %}}
{{% example %}}
### Create a scale set with ephemeral os disks using placement property.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "westus",
        Overprovision = true,
        Plan = new AzureNative.Compute.Inputs.PlanArgs
        {
            Name = "windows2016",
            Product = "windows-data-science-vm",
            Publisher = "microsoft-ads",
        },
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 3,
            Name = "Standard_DS1_v2",
            Tier = "Standard",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            Mode = AzureNative.Compute.UpgradeMode.Manual,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminPassword = "{your-password}",
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
            },
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
                {
                    Offer = "windows-data-science-vm",
                    Publisher = "microsoft-ads",
                    Sku = "windows2016",
                    Version = "latest",
                },
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadOnly,
                    CreateOption = "FromImage",
                    DiffDiskSettings = new AzureNative.Compute.Inputs.DiffDiskSettingsArgs
                    {
                        Option = "Local",
                        Placement = "ResourceDisk",
                    },
                    ManagedDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetManagedDiskParametersArgs
                    {
                        StorageAccountType = "Standard_LRS",
                    },
                },
            },
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("westus")
            .overprovision(true)
            .plan(Map.ofEntries(
                Map.entry("name", "windows2016"),
                Map.entry("product", "windows-data-science-vm"),
                Map.entry("publisher", "microsoft-ads")
            ))
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 3),
                Map.entry("name", "Standard_DS1_v2"),
                Map.entry("tier", "Standard")
            ))
            .upgradePolicy(Map.of("mode", "Manual"))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                    )),
                    Map.entry("name", "{vmss-name}"),
                    Map.entry("primary", true)
                ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminPassword", "{your-password}"),
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}")
                )),
                Map.entry("storageProfile", Map.ofEntries(
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
                        Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS"))
                    ))
                ))
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "westus",
    overprovision: true,
    plan: {
        name: "windows2016",
        product: "windows-data-science-vm",
        publisher: "microsoft-ads",
    },
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 3,
        name: "Standard_DS1_v2",
        tier: "Standard",
    },
    upgradePolicy: {
        mode: azure_native.compute.UpgradeMode.Manual,
    },
    virtualMachineProfile: {
        networkProfile: {
            networkInterfaceConfigurations: [{
                enableIPForwarding: true,
                ipConfigurations: [{
                    name: "{vmss-name}",
                    subnet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    },
                }],
                name: "{vmss-name}",
                primary: true,
            }],
        },
        osProfile: {
            adminPassword: "{your-password}",
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
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
                diffDiskSettings: {
                    option: "Local",
                    placement: "ResourceDisk",
                },
                managedDisk: {
                    storageAccountType: "Standard_LRS",
                },
            },
        },
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="westus",
    overprovision=True,
    plan=azure_native.compute.PlanArgs(
        name="windows2016",
        product="windows-data-science-vm",
        publisher="microsoft-ads",
    ),
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=3,
        name="Standard_DS1_v2",
        tier="Standard",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyArgs(
        mode=azure_native.compute.UpgradeMode.MANUAL,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        network_profile={
            "networkInterfaceConfigurations": [{
                "enableIPForwarding": True,
                "ipConfigurations": [{
                    "name": "{vmss-name}",
                    "subnet": azure_native.compute.ApiEntityReferenceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    ),
                }],
                "name": "{vmss-name}",
                "primary": True,
            }],
        },
        os_profile=azure_native.compute.VirtualMachineScaleSetOSProfileArgs(
            admin_password="{your-password}",
            admin_username="{your-username}",
            computer_name_prefix="{vmss-name}",
        ),
        storage_profile={
            "imageReference": azure_native.compute.ImageReferenceArgs(
                offer="windows-data-science-vm",
                publisher="microsoft-ads",
                sku="windows2016",
                version="latest",
            ),
            "osDisk": {
                "caching": azure_native.compute.CachingTypes.READ_ONLY,
                "createOption": "FromImage",
                "diffDiskSettings": azure_native.compute.DiffDiskSettingsArgs(
                    option="Local",
                    placement="ResourceDisk",
                ),
                "managedDisk": azure_native.compute.VirtualMachineScaleSetManagedDiskParametersArgs(
                    storage_account_type="Standard_LRS",
                ),
            },
        },
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml
resources:
  virtualMachineScaleSet:
    type: azure-native:compute:VirtualMachineScaleSet
    properties:
      location: westus
      overprovision: true
      plan:
        name: windows2016
        product: windows-data-science-vm
        publisher: microsoft-ads
      resourceGroupName: myResourceGroup
      sku:
        capacity: 3
        name: Standard_DS1_v2
        tier: Standard
      upgradePolicy:
        mode: Manual
      virtualMachineProfile:
        networkProfile:
          networkInterfaceConfigurations:
            - enableIPForwarding: true
              ipConfigurations:
                - name: '{vmss-name}'
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}
              name: '{vmss-name}'
              primary: true
        osProfile:
          adminPassword: '{your-password}'
          adminUsername: '{your-username}'
          computerNamePrefix: '{vmss-name}'
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
      vmScaleSetName: '{vmss-name}'

```

{{% /example %}}
{{% example %}}
### Create a scale set with ephemeral os disks.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "westus",
        Overprovision = true,
        Plan = new AzureNative.Compute.Inputs.PlanArgs
        {
            Name = "windows2016",
            Product = "windows-data-science-vm",
            Publisher = "microsoft-ads",
        },
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 3,
            Name = "Standard_DS1_v2",
            Tier = "Standard",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            Mode = AzureNative.Compute.UpgradeMode.Manual,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminPassword = "{your-password}",
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
            },
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
                {
                    Offer = "windows-data-science-vm",
                    Publisher = "microsoft-ads",
                    Sku = "windows2016",
                    Version = "latest",
                },
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadOnly,
                    CreateOption = "FromImage",
                    DiffDiskSettings = new AzureNative.Compute.Inputs.DiffDiskSettingsArgs
                    {
                        Option = "Local",
                    },
                    ManagedDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetManagedDiskParametersArgs
                    {
                        StorageAccountType = "Standard_LRS",
                    },
                },
            },
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("westus")
            .overprovision(true)
            .plan(Map.ofEntries(
                Map.entry("name", "windows2016"),
                Map.entry("product", "windows-data-science-vm"),
                Map.entry("publisher", "microsoft-ads")
            ))
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 3),
                Map.entry("name", "Standard_DS1_v2"),
                Map.entry("tier", "Standard")
            ))
            .upgradePolicy(Map.of("mode", "Manual"))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                    )),
                    Map.entry("name", "{vmss-name}"),
                    Map.entry("primary", true)
                ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminPassword", "{your-password}"),
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}")
                )),
                Map.entry("storageProfile", Map.ofEntries(
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
                        Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS"))
                    ))
                ))
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "westus",
    overprovision: true,
    plan: {
        name: "windows2016",
        product: "windows-data-science-vm",
        publisher: "microsoft-ads",
    },
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 3,
        name: "Standard_DS1_v2",
        tier: "Standard",
    },
    upgradePolicy: {
        mode: azure_native.compute.UpgradeMode.Manual,
    },
    virtualMachineProfile: {
        networkProfile: {
            networkInterfaceConfigurations: [{
                enableIPForwarding: true,
                ipConfigurations: [{
                    name: "{vmss-name}",
                    subnet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    },
                }],
                name: "{vmss-name}",
                primary: true,
            }],
        },
        osProfile: {
            adminPassword: "{your-password}",
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
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
                diffDiskSettings: {
                    option: "Local",
                },
                managedDisk: {
                    storageAccountType: "Standard_LRS",
                },
            },
        },
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="westus",
    overprovision=True,
    plan=azure_native.compute.PlanArgs(
        name="windows2016",
        product="windows-data-science-vm",
        publisher="microsoft-ads",
    ),
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=3,
        name="Standard_DS1_v2",
        tier="Standard",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyArgs(
        mode=azure_native.compute.UpgradeMode.MANUAL,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        network_profile={
            "networkInterfaceConfigurations": [{
                "enableIPForwarding": True,
                "ipConfigurations": [{
                    "name": "{vmss-name}",
                    "subnet": azure_native.compute.ApiEntityReferenceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    ),
                }],
                "name": "{vmss-name}",
                "primary": True,
            }],
        },
        os_profile=azure_native.compute.VirtualMachineScaleSetOSProfileArgs(
            admin_password="{your-password}",
            admin_username="{your-username}",
            computer_name_prefix="{vmss-name}",
        ),
        storage_profile={
            "imageReference": azure_native.compute.ImageReferenceArgs(
                offer="windows-data-science-vm",
                publisher="microsoft-ads",
                sku="windows2016",
                version="latest",
            ),
            "osDisk": {
                "caching": azure_native.compute.CachingTypes.READ_ONLY,
                "createOption": "FromImage",
                "diffDiskSettings": azure_native.compute.DiffDiskSettingsArgs(
                    option="Local",
                ),
                "managedDisk": azure_native.compute.VirtualMachineScaleSetManagedDiskParametersArgs(
                    storage_account_type="Standard_LRS",
                ),
            },
        },
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml
resources:
  virtualMachineScaleSet:
    type: azure-native:compute:VirtualMachineScaleSet
    properties:
      location: westus
      overprovision: true
      plan:
        name: windows2016
        product: windows-data-science-vm
        publisher: microsoft-ads
      resourceGroupName: myResourceGroup
      sku:
        capacity: 3
        name: Standard_DS1_v2
        tier: Standard
      upgradePolicy:
        mode: Manual
      virtualMachineProfile:
        networkProfile:
          networkInterfaceConfigurations:
            - enableIPForwarding: true
              ipConfigurations:
                - name: '{vmss-name}'
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}
              name: '{vmss-name}'
              primary: true
        osProfile:
          adminPassword: '{your-password}'
          adminUsername: '{your-username}'
          computerNamePrefix: '{vmss-name}'
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
      vmScaleSetName: '{vmss-name}'

```

{{% /example %}}
{{% example %}}
### Create a scale set with extension time budget.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "westus",
        Overprovision = true,
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 3,
            Name = "Standard_D1_v2",
            Tier = "Standard",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            Mode = AzureNative.Compute.UpgradeMode.Manual,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            DiagnosticsProfile = new AzureNative.Compute.Inputs.DiagnosticsProfileArgs
            {
                BootDiagnostics = new AzureNative.Compute.Inputs.BootDiagnosticsArgs
                {
                    Enabled = true,
                    StorageUri = "http://{existing-storage-account-name}.blob.core.windows.net",
                },
            },
            ExtensionProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetExtensionProfileArgs
            {
                Extensions = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetExtensionArgs
                    {
                        AutoUpgradeMinorVersion = false,
                        Name = "{extension-name}",
                        Publisher = "{extension-Publisher}",
                        Settings = null,
                        Type = "{extension-Type}",
                        TypeHandlerVersion = "{handler-version}",
                    },
                },
                ExtensionsTimeBudget = "PT1H20M",
            },
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminPassword = "{your-password}",
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
            },
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
                {
                    Offer = "WindowsServer",
                    Publisher = "MicrosoftWindowsServer",
                    Sku = "2016-Datacenter",
                    Version = "latest",
                },
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                    CreateOption = "FromImage",
                    ManagedDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetManagedDiskParametersArgs
                    {
                        StorageAccountType = "Standard_LRS",
                    },
                },
            },
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("westus")
            .overprovision(true)
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 3),
                Map.entry("name", "Standard_D1_v2"),
                Map.entry("tier", "Standard")
            ))
            .upgradePolicy(Map.of("mode", "Manual"))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("diagnosticsProfile", Map.of("bootDiagnostics", Map.ofEntries(
                    Map.entry("enabled", true),
                    Map.entry("storageUri", "http://{existing-storage-account-name}.blob.core.windows.net")
                ))),
                Map.entry("extensionProfile", Map.ofEntries(
                    Map.entry("extensions", Map.ofEntries(
                        Map.entry("autoUpgradeMinorVersion", false),
                        Map.entry("name", "{extension-name}"),
                        Map.entry("publisher", "{extension-Publisher}"),
                        Map.entry("settings", ),
                        Map.entry("type", "{extension-Type}"),
                        Map.entry("typeHandlerVersion", "{handler-version}")
                    )),
                    Map.entry("extensionsTimeBudget", "PT1H20M")
                )),
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                    )),
                    Map.entry("name", "{vmss-name}"),
                    Map.entry("primary", true)
                ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminPassword", "{your-password}"),
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}")
                )),
                Map.entry("storageProfile", Map.ofEntries(
                    Map.entry("imageReference", Map.ofEntries(
                        Map.entry("offer", "WindowsServer"),
                        Map.entry("publisher", "MicrosoftWindowsServer"),
                        Map.entry("sku", "2016-Datacenter"),
                        Map.entry("version", "latest")
                    )),
                    Map.entry("osDisk", Map.ofEntries(
                        Map.entry("caching", "ReadWrite"),
                        Map.entry("createOption", "FromImage"),
                        Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS"))
                    ))
                ))
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "westus",
    overprovision: true,
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 3,
        name: "Standard_D1_v2",
        tier: "Standard",
    },
    upgradePolicy: {
        mode: azure_native.compute.UpgradeMode.Manual,
    },
    virtualMachineProfile: {
        diagnosticsProfile: {
            bootDiagnostics: {
                enabled: true,
                storageUri: "http://{existing-storage-account-name}.blob.core.windows.net",
            },
        },
        extensionProfile: {
            extensions: [{
                autoUpgradeMinorVersion: false,
                name: "{extension-name}",
                publisher: "{extension-Publisher}",
                settings: {},
                type: "{extension-Type}",
                typeHandlerVersion: "{handler-version}",
            }],
            extensionsTimeBudget: "PT1H20M",
        },
        networkProfile: {
            networkInterfaceConfigurations: [{
                enableIPForwarding: true,
                ipConfigurations: [{
                    name: "{vmss-name}",
                    subnet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    },
                }],
                name: "{vmss-name}",
                primary: true,
            }],
        },
        osProfile: {
            adminPassword: "{your-password}",
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
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
            },
        },
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="westus",
    overprovision=True,
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=3,
        name="Standard_D1_v2",
        tier="Standard",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyArgs(
        mode=azure_native.compute.UpgradeMode.MANUAL,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        diagnostics_profile={
            "bootDiagnostics": azure_native.compute.BootDiagnosticsArgs(
                enabled=True,
                storage_uri="http://{existing-storage-account-name}.blob.core.windows.net",
            ),
        },
        extension_profile={
            "extensions": [azure_native.compute.VirtualMachineScaleSetExtensionArgs(
                auto_upgrade_minor_version=False,
                name="{extension-name}",
                publisher="{extension-Publisher}",
                settings={},
                type="{extension-Type}",
                type_handler_version="{handler-version}",
            )],
            "extensionsTimeBudget": "PT1H20M",
        },
        network_profile={
            "networkInterfaceConfigurations": [{
                "enableIPForwarding": True,
                "ipConfigurations": [{
                    "name": "{vmss-name}",
                    "subnet": azure_native.compute.ApiEntityReferenceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    ),
                }],
                "name": "{vmss-name}",
                "primary": True,
            }],
        },
        os_profile=azure_native.compute.VirtualMachineScaleSetOSProfileArgs(
            admin_password="{your-password}",
            admin_username="{your-username}",
            computer_name_prefix="{vmss-name}",
        ),
        storage_profile={
            "imageReference": azure_native.compute.ImageReferenceArgs(
                offer="WindowsServer",
                publisher="MicrosoftWindowsServer",
                sku="2016-Datacenter",
                version="latest",
            ),
            "osDisk": {
                "caching": azure_native.compute.CachingTypes.READ_WRITE,
                "createOption": "FromImage",
                "managedDisk": azure_native.compute.VirtualMachineScaleSetManagedDiskParametersArgs(
                    storage_account_type="Standard_LRS",
                ),
            },
        },
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml
resources:
  virtualMachineScaleSet:
    type: azure-native:compute:VirtualMachineScaleSet
    properties:
      location: westus
      overprovision: true
      resourceGroupName: myResourceGroup
      sku:
        capacity: 3
        name: Standard_D1_v2
        tier: Standard
      upgradePolicy:
        mode: Manual
      virtualMachineProfile:
        diagnosticsProfile:
          bootDiagnostics:
            enabled: true
            storageUri: http://{existing-storage-account-name}.blob.core.windows.net
        extensionProfile:
          extensions:
            - autoUpgradeMinorVersion: false
              name: '{extension-name}'
              publisher: '{extension-Publisher}'
              settings: {}
              type: '{extension-Type}'
              typeHandlerVersion: '{handler-version}'
          extensionsTimeBudget: PT1H20M
        networkProfile:
          networkInterfaceConfigurations:
            - enableIPForwarding: true
              ipConfigurations:
                - name: '{vmss-name}'
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}
              name: '{vmss-name}'
              primary: true
        osProfile:
          adminPassword: '{your-password}'
          adminUsername: '{your-username}'
          computerNamePrefix: '{vmss-name}'
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
      vmScaleSetName: '{vmss-name}'

```

{{% /example %}}
{{% example %}}
### Create a scale set with managed boot diagnostics.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "westus",
        Overprovision = true,
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 3,
            Name = "Standard_D1_v2",
            Tier = "Standard",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            Mode = AzureNative.Compute.UpgradeMode.Manual,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            DiagnosticsProfile = new AzureNative.Compute.Inputs.DiagnosticsProfileArgs
            {
                BootDiagnostics = new AzureNative.Compute.Inputs.BootDiagnosticsArgs
                {
                    Enabled = true,
                },
            },
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminPassword = "{your-password}",
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
            },
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
                {
                    Offer = "WindowsServer",
                    Publisher = "MicrosoftWindowsServer",
                    Sku = "2016-Datacenter",
                    Version = "latest",
                },
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                    CreateOption = "FromImage",
                    ManagedDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetManagedDiskParametersArgs
                    {
                        StorageAccountType = "Standard_LRS",
                    },
                },
            },
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("westus")
            .overprovision(true)
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 3),
                Map.entry("name", "Standard_D1_v2"),
                Map.entry("tier", "Standard")
            ))
            .upgradePolicy(Map.of("mode", "Manual"))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("diagnosticsProfile", Map.of("bootDiagnostics", Map.of("enabled", true))),
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                    )),
                    Map.entry("name", "{vmss-name}"),
                    Map.entry("primary", true)
                ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminPassword", "{your-password}"),
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}")
                )),
                Map.entry("storageProfile", Map.ofEntries(
                    Map.entry("imageReference", Map.ofEntries(
                        Map.entry("offer", "WindowsServer"),
                        Map.entry("publisher", "MicrosoftWindowsServer"),
                        Map.entry("sku", "2016-Datacenter"),
                        Map.entry("version", "latest")
                    )),
                    Map.entry("osDisk", Map.ofEntries(
                        Map.entry("caching", "ReadWrite"),
                        Map.entry("createOption", "FromImage"),
                        Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS"))
                    ))
                ))
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "westus",
    overprovision: true,
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 3,
        name: "Standard_D1_v2",
        tier: "Standard",
    },
    upgradePolicy: {
        mode: azure_native.compute.UpgradeMode.Manual,
    },
    virtualMachineProfile: {
        diagnosticsProfile: {
            bootDiagnostics: {
                enabled: true,
            },
        },
        networkProfile: {
            networkInterfaceConfigurations: [{
                enableIPForwarding: true,
                ipConfigurations: [{
                    name: "{vmss-name}",
                    subnet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    },
                }],
                name: "{vmss-name}",
                primary: true,
            }],
        },
        osProfile: {
            adminPassword: "{your-password}",
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
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
            },
        },
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="westus",
    overprovision=True,
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=3,
        name="Standard_D1_v2",
        tier="Standard",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyArgs(
        mode=azure_native.compute.UpgradeMode.MANUAL,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        diagnostics_profile={
            "bootDiagnostics": azure_native.compute.BootDiagnosticsArgs(
                enabled=True,
            ),
        },
        network_profile={
            "networkInterfaceConfigurations": [{
                "enableIPForwarding": True,
                "ipConfigurations": [{
                    "name": "{vmss-name}",
                    "subnet": azure_native.compute.ApiEntityReferenceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    ),
                }],
                "name": "{vmss-name}",
                "primary": True,
            }],
        },
        os_profile=azure_native.compute.VirtualMachineScaleSetOSProfileArgs(
            admin_password="{your-password}",
            admin_username="{your-username}",
            computer_name_prefix="{vmss-name}",
        ),
        storage_profile={
            "imageReference": azure_native.compute.ImageReferenceArgs(
                offer="WindowsServer",
                publisher="MicrosoftWindowsServer",
                sku="2016-Datacenter",
                version="latest",
            ),
            "osDisk": {
                "caching": azure_native.compute.CachingTypes.READ_WRITE,
                "createOption": "FromImage",
                "managedDisk": azure_native.compute.VirtualMachineScaleSetManagedDiskParametersArgs(
                    storage_account_type="Standard_LRS",
                ),
            },
        },
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml
resources:
  virtualMachineScaleSet:
    type: azure-native:compute:VirtualMachineScaleSet
    properties:
      location: westus
      overprovision: true
      resourceGroupName: myResourceGroup
      sku:
        capacity: 3
        name: Standard_D1_v2
        tier: Standard
      upgradePolicy:
        mode: Manual
      virtualMachineProfile:
        diagnosticsProfile:
          bootDiagnostics:
            enabled: true
        networkProfile:
          networkInterfaceConfigurations:
            - enableIPForwarding: true
              ipConfigurations:
                - name: '{vmss-name}'
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}
              name: '{vmss-name}'
              primary: true
        osProfile:
          adminPassword: '{your-password}'
          adminUsername: '{your-username}'
          computerNamePrefix: '{vmss-name}'
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
      vmScaleSetName: '{vmss-name}'

```

{{% /example %}}
{{% example %}}
### Create a scale set with password authentication.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "westus",
        Overprovision = true,
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 3,
            Name = "Standard_D1_v2",
            Tier = "Standard",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            Mode = AzureNative.Compute.UpgradeMode.Manual,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminPassword = "{your-password}",
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
            },
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
                {
                    Offer = "WindowsServer",
                    Publisher = "MicrosoftWindowsServer",
                    Sku = "2016-Datacenter",
                    Version = "latest",
                },
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                    CreateOption = "FromImage",
                    ManagedDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetManagedDiskParametersArgs
                    {
                        StorageAccountType = "Standard_LRS",
                    },
                },
            },
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("westus")
            .overprovision(true)
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 3),
                Map.entry("name", "Standard_D1_v2"),
                Map.entry("tier", "Standard")
            ))
            .upgradePolicy(Map.of("mode", "Manual"))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                    )),
                    Map.entry("name", "{vmss-name}"),
                    Map.entry("primary", true)
                ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminPassword", "{your-password}"),
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}")
                )),
                Map.entry("storageProfile", Map.ofEntries(
                    Map.entry("imageReference", Map.ofEntries(
                        Map.entry("offer", "WindowsServer"),
                        Map.entry("publisher", "MicrosoftWindowsServer"),
                        Map.entry("sku", "2016-Datacenter"),
                        Map.entry("version", "latest")
                    )),
                    Map.entry("osDisk", Map.ofEntries(
                        Map.entry("caching", "ReadWrite"),
                        Map.entry("createOption", "FromImage"),
                        Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS"))
                    ))
                ))
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "westus",
    overprovision: true,
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 3,
        name: "Standard_D1_v2",
        tier: "Standard",
    },
    upgradePolicy: {
        mode: azure_native.compute.UpgradeMode.Manual,
    },
    virtualMachineProfile: {
        networkProfile: {
            networkInterfaceConfigurations: [{
                enableIPForwarding: true,
                ipConfigurations: [{
                    name: "{vmss-name}",
                    subnet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    },
                }],
                name: "{vmss-name}",
                primary: true,
            }],
        },
        osProfile: {
            adminPassword: "{your-password}",
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
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
            },
        },
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="westus",
    overprovision=True,
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=3,
        name="Standard_D1_v2",
        tier="Standard",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyArgs(
        mode=azure_native.compute.UpgradeMode.MANUAL,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        network_profile={
            "networkInterfaceConfigurations": [{
                "enableIPForwarding": True,
                "ipConfigurations": [{
                    "name": "{vmss-name}",
                    "subnet": azure_native.compute.ApiEntityReferenceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    ),
                }],
                "name": "{vmss-name}",
                "primary": True,
            }],
        },
        os_profile=azure_native.compute.VirtualMachineScaleSetOSProfileArgs(
            admin_password="{your-password}",
            admin_username="{your-username}",
            computer_name_prefix="{vmss-name}",
        ),
        storage_profile={
            "imageReference": azure_native.compute.ImageReferenceArgs(
                offer="WindowsServer",
                publisher="MicrosoftWindowsServer",
                sku="2016-Datacenter",
                version="latest",
            ),
            "osDisk": {
                "caching": azure_native.compute.CachingTypes.READ_WRITE,
                "createOption": "FromImage",
                "managedDisk": azure_native.compute.VirtualMachineScaleSetManagedDiskParametersArgs(
                    storage_account_type="Standard_LRS",
                ),
            },
        },
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml
resources:
  virtualMachineScaleSet:
    type: azure-native:compute:VirtualMachineScaleSet
    properties:
      location: westus
      overprovision: true
      resourceGroupName: myResourceGroup
      sku:
        capacity: 3
        name: Standard_D1_v2
        tier: Standard
      upgradePolicy:
        mode: Manual
      virtualMachineProfile:
        networkProfile:
          networkInterfaceConfigurations:
            - enableIPForwarding: true
              ipConfigurations:
                - name: '{vmss-name}'
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}
              name: '{vmss-name}'
              primary: true
        osProfile:
          adminPassword: '{your-password}'
          adminUsername: '{your-username}'
          computerNamePrefix: '{vmss-name}'
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
      vmScaleSetName: '{vmss-name}'

```

{{% /example %}}
{{% example %}}
### Create a scale set with premium storage.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "westus",
        Overprovision = true,
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 3,
            Name = "Standard_D1_v2",
            Tier = "Standard",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            Mode = AzureNative.Compute.UpgradeMode.Manual,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminPassword = "{your-password}",
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
            },
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
                {
                    Offer = "WindowsServer",
                    Publisher = "MicrosoftWindowsServer",
                    Sku = "2016-Datacenter",
                    Version = "latest",
                },
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                    CreateOption = "FromImage",
                    ManagedDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetManagedDiskParametersArgs
                    {
                        StorageAccountType = "Premium_LRS",
                    },
                },
            },
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("westus")
            .overprovision(true)
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 3),
                Map.entry("name", "Standard_D1_v2"),
                Map.entry("tier", "Standard")
            ))
            .upgradePolicy(Map.of("mode", "Manual"))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                    )),
                    Map.entry("name", "{vmss-name}"),
                    Map.entry("primary", true)
                ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminPassword", "{your-password}"),
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}")
                )),
                Map.entry("storageProfile", Map.ofEntries(
                    Map.entry("imageReference", Map.ofEntries(
                        Map.entry("offer", "WindowsServer"),
                        Map.entry("publisher", "MicrosoftWindowsServer"),
                        Map.entry("sku", "2016-Datacenter"),
                        Map.entry("version", "latest")
                    )),
                    Map.entry("osDisk", Map.ofEntries(
                        Map.entry("caching", "ReadWrite"),
                        Map.entry("createOption", "FromImage"),
                        Map.entry("managedDisk", Map.of("storageAccountType", "Premium_LRS"))
                    ))
                ))
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "westus",
    overprovision: true,
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 3,
        name: "Standard_D1_v2",
        tier: "Standard",
    },
    upgradePolicy: {
        mode: azure_native.compute.UpgradeMode.Manual,
    },
    virtualMachineProfile: {
        networkProfile: {
            networkInterfaceConfigurations: [{
                enableIPForwarding: true,
                ipConfigurations: [{
                    name: "{vmss-name}",
                    subnet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    },
                }],
                name: "{vmss-name}",
                primary: true,
            }],
        },
        osProfile: {
            adminPassword: "{your-password}",
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
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
                    storageAccountType: "Premium_LRS",
                },
            },
        },
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="westus",
    overprovision=True,
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=3,
        name="Standard_D1_v2",
        tier="Standard",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyArgs(
        mode=azure_native.compute.UpgradeMode.MANUAL,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        network_profile={
            "networkInterfaceConfigurations": [{
                "enableIPForwarding": True,
                "ipConfigurations": [{
                    "name": "{vmss-name}",
                    "subnet": azure_native.compute.ApiEntityReferenceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    ),
                }],
                "name": "{vmss-name}",
                "primary": True,
            }],
        },
        os_profile=azure_native.compute.VirtualMachineScaleSetOSProfileArgs(
            admin_password="{your-password}",
            admin_username="{your-username}",
            computer_name_prefix="{vmss-name}",
        ),
        storage_profile={
            "imageReference": azure_native.compute.ImageReferenceArgs(
                offer="WindowsServer",
                publisher="MicrosoftWindowsServer",
                sku="2016-Datacenter",
                version="latest",
            ),
            "osDisk": {
                "caching": azure_native.compute.CachingTypes.READ_WRITE,
                "createOption": "FromImage",
                "managedDisk": azure_native.compute.VirtualMachineScaleSetManagedDiskParametersArgs(
                    storage_account_type="Premium_LRS",
                ),
            },
        },
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml
resources:
  virtualMachineScaleSet:
    type: azure-native:compute:VirtualMachineScaleSet
    properties:
      location: westus
      overprovision: true
      resourceGroupName: myResourceGroup
      sku:
        capacity: 3
        name: Standard_D1_v2
        tier: Standard
      upgradePolicy:
        mode: Manual
      virtualMachineProfile:
        networkProfile:
          networkInterfaceConfigurations:
            - enableIPForwarding: true
              ipConfigurations:
                - name: '{vmss-name}'
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}
              name: '{vmss-name}'
              primary: true
        osProfile:
          adminPassword: '{your-password}'
          adminUsername: '{your-username}'
          computerNamePrefix: '{vmss-name}'
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
      vmScaleSetName: '{vmss-name}'

```

{{% /example %}}
{{% example %}}
### Create a scale set with priority mix policy
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "westus",
        OrchestrationMode = "Flexible",
        PriorityMixPolicy = new AzureNative.Compute.Inputs.PriorityMixPolicyArgs
        {
            BaseRegularPriorityCount = 4,
            RegularPriorityPercentageAboveBase = 50,
        },
        ResourceGroupName = "myResourceGroup",
        SinglePlacementGroup = false,
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 10,
            Name = "Standard_A8m_v2",
            Tier = "Standard",
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            BillingProfile = new AzureNative.Compute.Inputs.BillingProfileArgs
            {
                MaxPrice = -1,
            },
            EvictionPolicy = "Deallocate",
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminPassword = "{your-password}",
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
            },
            Priority = "Spot",
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
                {
                    Offer = "WindowsServer",
                    Publisher = "MicrosoftWindowsServer",
                    Sku = "2016-Datacenter",
                    Version = "latest",
                },
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                    CreateOption = "FromImage",
                    ManagedDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetManagedDiskParametersArgs
                    {
                        StorageAccountType = "Standard_LRS",
                    },
                },
            },
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("westus")
            .orchestrationMode("Flexible")
            .priorityMixPolicy(Map.ofEntries(
                Map.entry("baseRegularPriorityCount", 4),
                Map.entry("regularPriorityPercentageAboveBase", 50)
            ))
            .resourceGroupName("myResourceGroup")
            .singlePlacementGroup(false)
            .sku(Map.ofEntries(
                Map.entry("capacity", 10),
                Map.entry("name", "Standard_A8m_v2"),
                Map.entry("tier", "Standard")
            ))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("billingProfile", Map.of("maxPrice", "TODO: GenUnaryOpExpression")),
                Map.entry("evictionPolicy", "Deallocate"),
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                    )),
                    Map.entry("name", "{vmss-name}"),
                    Map.entry("primary", true)
                ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminPassword", "{your-password}"),
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}")
                )),
                Map.entry("priority", "Spot"),
                Map.entry("storageProfile", Map.ofEntries(
                    Map.entry("imageReference", Map.ofEntries(
                        Map.entry("offer", "WindowsServer"),
                        Map.entry("publisher", "MicrosoftWindowsServer"),
                        Map.entry("sku", "2016-Datacenter"),
                        Map.entry("version", "latest")
                    )),
                    Map.entry("osDisk", Map.ofEntries(
                        Map.entry("caching", "ReadWrite"),
                        Map.entry("createOption", "FromImage"),
                        Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS"))
                    ))
                ))
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "westus",
    orchestrationMode: "Flexible",
    priorityMixPolicy: {
        baseRegularPriorityCount: 4,
        regularPriorityPercentageAboveBase: 50,
    },
    resourceGroupName: "myResourceGroup",
    singlePlacementGroup: false,
    sku: {
        capacity: 10,
        name: "Standard_A8m_v2",
        tier: "Standard",
    },
    virtualMachineProfile: {
        billingProfile: {
            maxPrice: -1,
        },
        evictionPolicy: "Deallocate",
        networkProfile: {
            networkInterfaceConfigurations: [{
                enableIPForwarding: true,
                ipConfigurations: [{
                    name: "{vmss-name}",
                    subnet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    },
                }],
                name: "{vmss-name}",
                primary: true,
            }],
        },
        osProfile: {
            adminPassword: "{your-password}",
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
        },
        priority: "Spot",
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
            },
        },
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="westus",
    orchestration_mode="Flexible",
    priority_mix_policy=azure_native.compute.PriorityMixPolicyArgs(
        base_regular_priority_count=4,
        regular_priority_percentage_above_base=50,
    ),
    resource_group_name="myResourceGroup",
    single_placement_group=False,
    sku=azure_native.compute.SkuArgs(
        capacity=10,
        name="Standard_A8m_v2",
        tier="Standard",
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        billing_profile=azure_native.compute.BillingProfileArgs(
            max_price=-1,
        ),
        eviction_policy="Deallocate",
        network_profile={
            "networkInterfaceConfigurations": [{
                "enableIPForwarding": True,
                "ipConfigurations": [{
                    "name": "{vmss-name}",
                    "subnet": azure_native.compute.ApiEntityReferenceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    ),
                }],
                "name": "{vmss-name}",
                "primary": True,
            }],
        },
        os_profile=azure_native.compute.VirtualMachineScaleSetOSProfileArgs(
            admin_password="{your-password}",
            admin_username="{your-username}",
            computer_name_prefix="{vmss-name}",
        ),
        priority="Spot",
        storage_profile={
            "imageReference": azure_native.compute.ImageReferenceArgs(
                offer="WindowsServer",
                publisher="MicrosoftWindowsServer",
                sku="2016-Datacenter",
                version="latest",
            ),
            "osDisk": {
                "caching": azure_native.compute.CachingTypes.READ_WRITE,
                "createOption": "FromImage",
                "managedDisk": azure_native.compute.VirtualMachineScaleSetManagedDiskParametersArgs(
                    storage_account_type="Standard_LRS",
                ),
            },
        },
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml

```

{{% /example %}}
{{% example %}}
### Create a scale set with scaleInPolicy.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "westus",
        Overprovision = true,
        ResourceGroupName = "myResourceGroup",
        ScaleInPolicy = new AzureNative.Compute.Inputs.ScaleInPolicyArgs
        {
            ForceDeletion = true,
            Rules = new[]
            {
                "OldestVM",
            },
        },
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 3,
            Name = "Standard_D1_v2",
            Tier = "Standard",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            Mode = AzureNative.Compute.UpgradeMode.Manual,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminPassword = "{your-password}",
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
            },
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
                {
                    Offer = "WindowsServer",
                    Publisher = "MicrosoftWindowsServer",
                    Sku = "2016-Datacenter",
                    Version = "latest",
                },
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                    CreateOption = "FromImage",
                    ManagedDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetManagedDiskParametersArgs
                    {
                        StorageAccountType = "Standard_LRS",
                    },
                },
            },
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("westus")
            .overprovision(true)
            .resourceGroupName("myResourceGroup")
            .scaleInPolicy(Map.ofEntries(
                Map.entry("forceDeletion", true),
                Map.entry("rules", "OldestVM")
            ))
            .sku(Map.ofEntries(
                Map.entry("capacity", 3),
                Map.entry("name", "Standard_D1_v2"),
                Map.entry("tier", "Standard")
            ))
            .upgradePolicy(Map.of("mode", "Manual"))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                    )),
                    Map.entry("name", "{vmss-name}"),
                    Map.entry("primary", true)
                ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminPassword", "{your-password}"),
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}")
                )),
                Map.entry("storageProfile", Map.ofEntries(
                    Map.entry("imageReference", Map.ofEntries(
                        Map.entry("offer", "WindowsServer"),
                        Map.entry("publisher", "MicrosoftWindowsServer"),
                        Map.entry("sku", "2016-Datacenter"),
                        Map.entry("version", "latest")
                    )),
                    Map.entry("osDisk", Map.ofEntries(
                        Map.entry("caching", "ReadWrite"),
                        Map.entry("createOption", "FromImage"),
                        Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS"))
                    ))
                ))
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "westus",
    overprovision: true,
    resourceGroupName: "myResourceGroup",
    scaleInPolicy: {
        forceDeletion: true,
        rules: ["OldestVM"],
    },
    sku: {
        capacity: 3,
        name: "Standard_D1_v2",
        tier: "Standard",
    },
    upgradePolicy: {
        mode: azure_native.compute.UpgradeMode.Manual,
    },
    virtualMachineProfile: {
        networkProfile: {
            networkInterfaceConfigurations: [{
                enableIPForwarding: true,
                ipConfigurations: [{
                    name: "{vmss-name}",
                    subnet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    },
                }],
                name: "{vmss-name}",
                primary: true,
            }],
        },
        osProfile: {
            adminPassword: "{your-password}",
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
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
            },
        },
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="westus",
    overprovision=True,
    resource_group_name="myResourceGroup",
    scale_in_policy=azure_native.compute.ScaleInPolicyArgs(
        force_deletion=True,
        rules=["OldestVM"],
    ),
    sku=azure_native.compute.SkuArgs(
        capacity=3,
        name="Standard_D1_v2",
        tier="Standard",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyArgs(
        mode=azure_native.compute.UpgradeMode.MANUAL,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        network_profile={
            "networkInterfaceConfigurations": [{
                "enableIPForwarding": True,
                "ipConfigurations": [{
                    "name": "{vmss-name}",
                    "subnet": azure_native.compute.ApiEntityReferenceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    ),
                }],
                "name": "{vmss-name}",
                "primary": True,
            }],
        },
        os_profile=azure_native.compute.VirtualMachineScaleSetOSProfileArgs(
            admin_password="{your-password}",
            admin_username="{your-username}",
            computer_name_prefix="{vmss-name}",
        ),
        storage_profile={
            "imageReference": azure_native.compute.ImageReferenceArgs(
                offer="WindowsServer",
                publisher="MicrosoftWindowsServer",
                sku="2016-Datacenter",
                version="latest",
            ),
            "osDisk": {
                "caching": azure_native.compute.CachingTypes.READ_WRITE,
                "createOption": "FromImage",
                "managedDisk": azure_native.compute.VirtualMachineScaleSetManagedDiskParametersArgs(
                    storage_account_type="Standard_LRS",
                ),
            },
        },
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml
resources:
  virtualMachineScaleSet:
    type: azure-native:compute:VirtualMachineScaleSet
    properties:
      location: westus
      overprovision: true
      resourceGroupName: myResourceGroup
      scaleInPolicy:
        forceDeletion: true
        rules:
          - OldestVM
      sku:
        capacity: 3
        name: Standard_D1_v2
        tier: Standard
      upgradePolicy:
        mode: Manual
      virtualMachineProfile:
        networkProfile:
          networkInterfaceConfigurations:
            - enableIPForwarding: true
              ipConfigurations:
                - name: '{vmss-name}'
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}
              name: '{vmss-name}'
              primary: true
        osProfile:
          adminPassword: '{your-password}'
          adminUsername: '{your-username}'
          computerNamePrefix: '{vmss-name}'
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
      vmScaleSetName: '{vmss-name}'

```

{{% /example %}}
{{% example %}}
### Create a scale set with spot restore policy
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "westus",
        Overprovision = true,
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 2,
            Name = "Standard_A8m_v2",
            Tier = "Standard",
        },
        SpotRestorePolicy = new AzureNative.Compute.Inputs.SpotRestorePolicyArgs
        {
            Enabled = true,
            RestoreTimeout = "PT1H",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            Mode = AzureNative.Compute.UpgradeMode.Manual,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            BillingProfile = new AzureNative.Compute.Inputs.BillingProfileArgs
            {
                MaxPrice = -1,
            },
            EvictionPolicy = "Deallocate",
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminPassword = "{your-password}",
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
            },
            Priority = "Spot",
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
                {
                    Offer = "WindowsServer",
                    Publisher = "MicrosoftWindowsServer",
                    Sku = "2016-Datacenter",
                    Version = "latest",
                },
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                    CreateOption = "FromImage",
                    ManagedDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetManagedDiskParametersArgs
                    {
                        StorageAccountType = "Standard_LRS",
                    },
                },
            },
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("westus")
            .overprovision(true)
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 2),
                Map.entry("name", "Standard_A8m_v2"),
                Map.entry("tier", "Standard")
            ))
            .spotRestorePolicy(Map.ofEntries(
                Map.entry("enabled", true),
                Map.entry("restoreTimeout", "PT1H")
            ))
            .upgradePolicy(Map.of("mode", "Manual"))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("billingProfile", Map.of("maxPrice", "TODO: GenUnaryOpExpression")),
                Map.entry("evictionPolicy", "Deallocate"),
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                    )),
                    Map.entry("name", "{vmss-name}"),
                    Map.entry("primary", true)
                ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminPassword", "{your-password}"),
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}")
                )),
                Map.entry("priority", "Spot"),
                Map.entry("storageProfile", Map.ofEntries(
                    Map.entry("imageReference", Map.ofEntries(
                        Map.entry("offer", "WindowsServer"),
                        Map.entry("publisher", "MicrosoftWindowsServer"),
                        Map.entry("sku", "2016-Datacenter"),
                        Map.entry("version", "latest")
                    )),
                    Map.entry("osDisk", Map.ofEntries(
                        Map.entry("caching", "ReadWrite"),
                        Map.entry("createOption", "FromImage"),
                        Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS"))
                    ))
                ))
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "westus",
    overprovision: true,
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 2,
        name: "Standard_A8m_v2",
        tier: "Standard",
    },
    spotRestorePolicy: {
        enabled: true,
        restoreTimeout: "PT1H",
    },
    upgradePolicy: {
        mode: azure_native.compute.UpgradeMode.Manual,
    },
    virtualMachineProfile: {
        billingProfile: {
            maxPrice: -1,
        },
        evictionPolicy: "Deallocate",
        networkProfile: {
            networkInterfaceConfigurations: [{
                enableIPForwarding: true,
                ipConfigurations: [{
                    name: "{vmss-name}",
                    subnet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    },
                }],
                name: "{vmss-name}",
                primary: true,
            }],
        },
        osProfile: {
            adminPassword: "{your-password}",
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
        },
        priority: "Spot",
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
            },
        },
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="westus",
    overprovision=True,
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=2,
        name="Standard_A8m_v2",
        tier="Standard",
    ),
    spot_restore_policy=azure_native.compute.SpotRestorePolicyArgs(
        enabled=True,
        restore_timeout="PT1H",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyArgs(
        mode=azure_native.compute.UpgradeMode.MANUAL,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        billing_profile=azure_native.compute.BillingProfileArgs(
            max_price=-1,
        ),
        eviction_policy="Deallocate",
        network_profile={
            "networkInterfaceConfigurations": [{
                "enableIPForwarding": True,
                "ipConfigurations": [{
                    "name": "{vmss-name}",
                    "subnet": azure_native.compute.ApiEntityReferenceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    ),
                }],
                "name": "{vmss-name}",
                "primary": True,
            }],
        },
        os_profile=azure_native.compute.VirtualMachineScaleSetOSProfileArgs(
            admin_password="{your-password}",
            admin_username="{your-username}",
            computer_name_prefix="{vmss-name}",
        ),
        priority="Spot",
        storage_profile={
            "imageReference": azure_native.compute.ImageReferenceArgs(
                offer="WindowsServer",
                publisher="MicrosoftWindowsServer",
                sku="2016-Datacenter",
                version="latest",
            ),
            "osDisk": {
                "caching": azure_native.compute.CachingTypes.READ_WRITE,
                "createOption": "FromImage",
                "managedDisk": azure_native.compute.VirtualMachineScaleSetManagedDiskParametersArgs(
                    storage_account_type="Standard_LRS",
                ),
            },
        },
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml

```

{{% /example %}}
{{% example %}}
### Create a scale set with ssh authentication.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "westus",
        Overprovision = true,
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 3,
            Name = "Standard_D1_v2",
            Tier = "Standard",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            Mode = AzureNative.Compute.UpgradeMode.Manual,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
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
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
                {
                    Offer = "WindowsServer",
                    Publisher = "MicrosoftWindowsServer",
                    Sku = "2016-Datacenter",
                    Version = "latest",
                },
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                    CreateOption = "FromImage",
                    ManagedDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetManagedDiskParametersArgs
                    {
                        StorageAccountType = "Standard_LRS",
                    },
                },
            },
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("westus")
            .overprovision(true)
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 3),
                Map.entry("name", "Standard_D1_v2"),
                Map.entry("tier", "Standard")
            ))
            .upgradePolicy(Map.of("mode", "Manual"))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                    )),
                    Map.entry("name", "{vmss-name}"),
                    Map.entry("primary", true)
                ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}"),
                    Map.entry("linuxConfiguration", Map.ofEntries(
                        Map.entry("disablePasswordAuthentication", true),
                        Map.entry("ssh", Map.of("publicKeys", Map.ofEntries(
                            Map.entry("keyData", "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCeClRAk2ipUs/l5voIsDC5q9RI+YSRd1Bvd/O+axgY4WiBzG+4FwJWZm/mLLe5DoOdHQwmU2FrKXZSW4w2sYE70KeWnrFViCOX5MTVvJgPE8ClugNl8RWth/tU849DvM9sT7vFgfVSHcAS2yDRyDlueii+8nF2ym8XWAPltFVCyLHRsyBp5YPqK8JFYIa1eybKsY3hEAxRCA+/7bq8et+Gj3coOsuRmrehav7rE6N12Pb80I6ofa6SM5XNYq4Xk0iYNx7R3kdz0Jj9XgZYWjAHjJmT0gTRoOnt6upOuxK7xI/ykWrllgpXrCPu3Ymz+c+ujaqcxDopnAl2lmf69/J1"),
                            Map.entry("path", "/home/{your-username}/.ssh/authorized_keys")
                        )))
                    ))
                )),
                Map.entry("storageProfile", Map.ofEntries(
                    Map.entry("imageReference", Map.ofEntries(
                        Map.entry("offer", "WindowsServer"),
                        Map.entry("publisher", "MicrosoftWindowsServer"),
                        Map.entry("sku", "2016-Datacenter"),
                        Map.entry("version", "latest")
                    )),
                    Map.entry("osDisk", Map.ofEntries(
                        Map.entry("caching", "ReadWrite"),
                        Map.entry("createOption", "FromImage"),
                        Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS"))
                    ))
                ))
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "westus",
    overprovision: true,
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 3,
        name: "Standard_D1_v2",
        tier: "Standard",
    },
    upgradePolicy: {
        mode: azure_native.compute.UpgradeMode.Manual,
    },
    virtualMachineProfile: {
        networkProfile: {
            networkInterfaceConfigurations: [{
                enableIPForwarding: true,
                ipConfigurations: [{
                    name: "{vmss-name}",
                    subnet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    },
                }],
                name: "{vmss-name}",
                primary: true,
            }],
        },
        osProfile: {
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
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
            },
        },
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="westus",
    overprovision=True,
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=3,
        name="Standard_D1_v2",
        tier="Standard",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyArgs(
        mode=azure_native.compute.UpgradeMode.MANUAL,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        network_profile={
            "networkInterfaceConfigurations": [{
                "enableIPForwarding": True,
                "ipConfigurations": [{
                    "name": "{vmss-name}",
                    "subnet": azure_native.compute.ApiEntityReferenceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    ),
                }],
                "name": "{vmss-name}",
                "primary": True,
            }],
        },
        os_profile={
            "adminUsername": "{your-username}",
            "computerNamePrefix": "{vmss-name}",
            "linuxConfiguration": {
                "disablePasswordAuthentication": True,
                "ssh": {
                    "publicKeys": [azure_native.compute.SshPublicKeyArgs(
                        key_data="ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCeClRAk2ipUs/l5voIsDC5q9RI+YSRd1Bvd/O+axgY4WiBzG+4FwJWZm/mLLe5DoOdHQwmU2FrKXZSW4w2sYE70KeWnrFViCOX5MTVvJgPE8ClugNl8RWth/tU849DvM9sT7vFgfVSHcAS2yDRyDlueii+8nF2ym8XWAPltFVCyLHRsyBp5YPqK8JFYIa1eybKsY3hEAxRCA+/7bq8et+Gj3coOsuRmrehav7rE6N12Pb80I6ofa6SM5XNYq4Xk0iYNx7R3kdz0Jj9XgZYWjAHjJmT0gTRoOnt6upOuxK7xI/ykWrllgpXrCPu3Ymz+c+ujaqcxDopnAl2lmf69/J1",
                        path="/home/{your-username}/.ssh/authorized_keys",
                    )],
                },
            },
        },
        storage_profile={
            "imageReference": azure_native.compute.ImageReferenceArgs(
                offer="WindowsServer",
                publisher="MicrosoftWindowsServer",
                sku="2016-Datacenter",
                version="latest",
            ),
            "osDisk": {
                "caching": azure_native.compute.CachingTypes.READ_WRITE,
                "createOption": "FromImage",
                "managedDisk": azure_native.compute.VirtualMachineScaleSetManagedDiskParametersArgs(
                    storage_account_type="Standard_LRS",
                ),
            },
        },
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml
resources:
  virtualMachineScaleSet:
    type: azure-native:compute:VirtualMachineScaleSet
    properties:
      location: westus
      overprovision: true
      resourceGroupName: myResourceGroup
      sku:
        capacity: 3
        name: Standard_D1_v2
        tier: Standard
      upgradePolicy:
        mode: Manual
      virtualMachineProfile:
        networkProfile:
          networkInterfaceConfigurations:
            - enableIPForwarding: true
              ipConfigurations:
                - name: '{vmss-name}'
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}
              name: '{vmss-name}'
              primary: true
        osProfile:
          adminUsername: '{your-username}'
          computerNamePrefix: '{vmss-name}'
          linuxConfiguration:
            disablePasswordAuthentication: true
            ssh:
              publicKeys:
                - keyData: ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCeClRAk2ipUs/l5voIsDC5q9RI+YSRd1Bvd/O+axgY4WiBzG+4FwJWZm/mLLe5DoOdHQwmU2FrKXZSW4w2sYE70KeWnrFViCOX5MTVvJgPE8ClugNl8RWth/tU849DvM9sT7vFgfVSHcAS2yDRyDlueii+8nF2ym8XWAPltFVCyLHRsyBp5YPqK8JFYIa1eybKsY3hEAxRCA+/7bq8et+Gj3coOsuRmrehav7rE6N12Pb80I6ofa6SM5XNYq4Xk0iYNx7R3kdz0Jj9XgZYWjAHjJmT0gTRoOnt6upOuxK7xI/ykWrllgpXrCPu3Ymz+c+ujaqcxDopnAl2lmf69/J1
                  path: /home/{your-username}/.ssh/authorized_keys
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
      vmScaleSetName: '{vmss-name}'

```

{{% /example %}}
{{% example %}}
### Create a scale set with terminate scheduled events enabled.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "westus",
        Overprovision = true,
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 3,
            Name = "Standard_D1_v2",
            Tier = "Standard",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            Mode = AzureNative.Compute.UpgradeMode.Manual,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminPassword = "{your-password}",
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
            },
            ScheduledEventsProfile = new AzureNative.Compute.Inputs.ScheduledEventsProfileArgs
            {
                TerminateNotificationProfile = new AzureNative.Compute.Inputs.TerminateNotificationProfileArgs
                {
                    Enable = true,
                    NotBeforeTimeout = "PT5M",
                },
            },
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
                {
                    Offer = "WindowsServer",
                    Publisher = "MicrosoftWindowsServer",
                    Sku = "2016-Datacenter",
                    Version = "latest",
                },
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                    CreateOption = "FromImage",
                    ManagedDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetManagedDiskParametersArgs
                    {
                        StorageAccountType = "Standard_LRS",
                    },
                },
            },
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("westus")
            .overprovision(true)
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 3),
                Map.entry("name", "Standard_D1_v2"),
                Map.entry("tier", "Standard")
            ))
            .upgradePolicy(Map.of("mode", "Manual"))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                    )),
                    Map.entry("name", "{vmss-name}"),
                    Map.entry("primary", true)
                ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminPassword", "{your-password}"),
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}")
                )),
                Map.entry("scheduledEventsProfile", Map.of("terminateNotificationProfile", Map.ofEntries(
                    Map.entry("enable", true),
                    Map.entry("notBeforeTimeout", "PT5M")
                ))),
                Map.entry("storageProfile", Map.ofEntries(
                    Map.entry("imageReference", Map.ofEntries(
                        Map.entry("offer", "WindowsServer"),
                        Map.entry("publisher", "MicrosoftWindowsServer"),
                        Map.entry("sku", "2016-Datacenter"),
                        Map.entry("version", "latest")
                    )),
                    Map.entry("osDisk", Map.ofEntries(
                        Map.entry("caching", "ReadWrite"),
                        Map.entry("createOption", "FromImage"),
                        Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS"))
                    ))
                ))
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "westus",
    overprovision: true,
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 3,
        name: "Standard_D1_v2",
        tier: "Standard",
    },
    upgradePolicy: {
        mode: azure_native.compute.UpgradeMode.Manual,
    },
    virtualMachineProfile: {
        networkProfile: {
            networkInterfaceConfigurations: [{
                enableIPForwarding: true,
                ipConfigurations: [{
                    name: "{vmss-name}",
                    subnet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    },
                }],
                name: "{vmss-name}",
                primary: true,
            }],
        },
        osProfile: {
            adminPassword: "{your-password}",
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
        },
        scheduledEventsProfile: {
            terminateNotificationProfile: {
                enable: true,
                notBeforeTimeout: "PT5M",
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
            },
        },
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="westus",
    overprovision=True,
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=3,
        name="Standard_D1_v2",
        tier="Standard",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyArgs(
        mode=azure_native.compute.UpgradeMode.MANUAL,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        network_profile={
            "networkInterfaceConfigurations": [{
                "enableIPForwarding": True,
                "ipConfigurations": [{
                    "name": "{vmss-name}",
                    "subnet": azure_native.compute.ApiEntityReferenceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    ),
                }],
                "name": "{vmss-name}",
                "primary": True,
            }],
        },
        os_profile=azure_native.compute.VirtualMachineScaleSetOSProfileArgs(
            admin_password="{your-password}",
            admin_username="{your-username}",
            computer_name_prefix="{vmss-name}",
        ),
        scheduled_events_profile={
            "terminateNotificationProfile": azure_native.compute.TerminateNotificationProfileArgs(
                enable=True,
                not_before_timeout="PT5M",
            ),
        },
        storage_profile={
            "imageReference": azure_native.compute.ImageReferenceArgs(
                offer="WindowsServer",
                publisher="MicrosoftWindowsServer",
                sku="2016-Datacenter",
                version="latest",
            ),
            "osDisk": {
                "caching": azure_native.compute.CachingTypes.READ_WRITE,
                "createOption": "FromImage",
                "managedDisk": azure_native.compute.VirtualMachineScaleSetManagedDiskParametersArgs(
                    storage_account_type="Standard_LRS",
                ),
            },
        },
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml
resources:
  virtualMachineScaleSet:
    type: azure-native:compute:VirtualMachineScaleSet
    properties:
      location: westus
      overprovision: true
      resourceGroupName: myResourceGroup
      sku:
        capacity: 3
        name: Standard_D1_v2
        tier: Standard
      upgradePolicy:
        mode: Manual
      virtualMachineProfile:
        networkProfile:
          networkInterfaceConfigurations:
            - enableIPForwarding: true
              ipConfigurations:
                - name: '{vmss-name}'
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}
              name: '{vmss-name}'
              primary: true
        osProfile:
          adminPassword: '{your-password}'
          adminUsername: '{your-username}'
          computerNamePrefix: '{vmss-name}'
        scheduledEventsProfile:
          terminateNotificationProfile:
            enable: true
            notBeforeTimeout: PT5M
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
      vmScaleSetName: '{vmss-name}'

```

{{% /example %}}
{{% example %}}
### Create a scale set with userData.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "westus",
        Overprovision = true,
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 3,
            Name = "Standard_D1_v2",
            Tier = "Standard",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            Mode = AzureNative.Compute.UpgradeMode.Manual,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminPassword = "{your-password}",
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
            },
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
                {
                    Offer = "WindowsServer",
                    Publisher = "MicrosoftWindowsServer",
                    Sku = "2016-Datacenter",
                    Version = "latest",
                },
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                    CreateOption = "FromImage",
                    ManagedDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetManagedDiskParametersArgs
                    {
                        StorageAccountType = "Standard_LRS",
                    },
                },
            },
            UserData = "RXhhbXBsZSBVc2VyRGF0YQ==",
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("westus")
            .overprovision(true)
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 3),
                Map.entry("name", "Standard_D1_v2"),
                Map.entry("tier", "Standard")
            ))
            .upgradePolicy(Map.of("mode", "Manual"))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                    )),
                    Map.entry("name", "{vmss-name}"),
                    Map.entry("primary", true)
                ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminPassword", "{your-password}"),
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}")
                )),
                Map.entry("storageProfile", Map.ofEntries(
                    Map.entry("imageReference", Map.ofEntries(
                        Map.entry("offer", "WindowsServer"),
                        Map.entry("publisher", "MicrosoftWindowsServer"),
                        Map.entry("sku", "2016-Datacenter"),
                        Map.entry("version", "latest")
                    )),
                    Map.entry("osDisk", Map.ofEntries(
                        Map.entry("caching", "ReadWrite"),
                        Map.entry("createOption", "FromImage"),
                        Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS"))
                    ))
                )),
                Map.entry("userData", "RXhhbXBsZSBVc2VyRGF0YQ==")
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "westus",
    overprovision: true,
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 3,
        name: "Standard_D1_v2",
        tier: "Standard",
    },
    upgradePolicy: {
        mode: azure_native.compute.UpgradeMode.Manual,
    },
    virtualMachineProfile: {
        networkProfile: {
            networkInterfaceConfigurations: [{
                enableIPForwarding: true,
                ipConfigurations: [{
                    name: "{vmss-name}",
                    subnet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    },
                }],
                name: "{vmss-name}",
                primary: true,
            }],
        },
        osProfile: {
            adminPassword: "{your-password}",
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
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
            },
        },
        userData: "RXhhbXBsZSBVc2VyRGF0YQ==",
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="westus",
    overprovision=True,
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=3,
        name="Standard_D1_v2",
        tier="Standard",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyArgs(
        mode=azure_native.compute.UpgradeMode.MANUAL,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        network_profile={
            "networkInterfaceConfigurations": [{
                "enableIPForwarding": True,
                "ipConfigurations": [{
                    "name": "{vmss-name}",
                    "subnet": azure_native.compute.ApiEntityReferenceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    ),
                }],
                "name": "{vmss-name}",
                "primary": True,
            }],
        },
        os_profile=azure_native.compute.VirtualMachineScaleSetOSProfileArgs(
            admin_password="{your-password}",
            admin_username="{your-username}",
            computer_name_prefix="{vmss-name}",
        ),
        storage_profile={
            "imageReference": azure_native.compute.ImageReferenceArgs(
                offer="WindowsServer",
                publisher="MicrosoftWindowsServer",
                sku="2016-Datacenter",
                version="latest",
            ),
            "osDisk": {
                "caching": azure_native.compute.CachingTypes.READ_WRITE,
                "createOption": "FromImage",
                "managedDisk": azure_native.compute.VirtualMachineScaleSetManagedDiskParametersArgs(
                    storage_account_type="Standard_LRS",
                ),
            },
        },
        user_data="RXhhbXBsZSBVc2VyRGF0YQ==",
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml
resources:
  virtualMachineScaleSet:
    type: azure-native:compute:VirtualMachineScaleSet
    properties:
      location: westus
      overprovision: true
      resourceGroupName: myResourceGroup
      sku:
        capacity: 3
        name: Standard_D1_v2
        tier: Standard
      upgradePolicy:
        mode: Manual
      virtualMachineProfile:
        networkProfile:
          networkInterfaceConfigurations:
            - enableIPForwarding: true
              ipConfigurations:
                - name: '{vmss-name}'
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}
              name: '{vmss-name}'
              primary: true
        osProfile:
          adminPassword: '{your-password}'
          adminUsername: '{your-username}'
          computerNamePrefix: '{vmss-name}'
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
        userData: RXhhbXBsZSBVc2VyRGF0YQ==
      vmScaleSetName: '{vmss-name}'

```

{{% /example %}}
{{% example %}}
### Create a scale set with virtual machines in different zones.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "centralus",
        Overprovision = true,
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 2,
            Name = "Standard_A1_v2",
            Tier = "Standard",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            Mode = AzureNative.Compute.UpgradeMode.Automatic,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminPassword = "{your-password}",
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
            },
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                DataDisks = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetDataDiskArgs
                    {
                        CreateOption = "Empty",
                        DiskSizeGB = 1023,
                        Lun = 0,
                    },
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetDataDiskArgs
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
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                    CreateOption = "FromImage",
                    DiskSizeGB = 512,
                    ManagedDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetManagedDiskParametersArgs
                    {
                        StorageAccountType = "Standard_LRS",
                    },
                },
            },
        },
        VmScaleSetName = "{vmss-name}",
        Zones = new[]
        {
            "1",
            "3",
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("centralus")
            .overprovision(true)
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 2),
                Map.entry("name", "Standard_A1_v2"),
                Map.entry("tier", "Standard")
            ))
            .upgradePolicy(Map.of("mode", "Automatic"))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                    )),
                    Map.entry("name", "{vmss-name}"),
                    Map.entry("primary", true)
                ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminPassword", "{your-password}"),
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}")
                )),
                Map.entry("storageProfile", Map.ofEntries(
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
                        Map.entry("diskSizeGB", 512),
                        Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS"))
                    ))
                ))
            ))
            .vmScaleSetName("{vmss-name}")
            .zones(            
                "1",
                "3")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "centralus",
    overprovision: true,
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 2,
        name: "Standard_A1_v2",
        tier: "Standard",
    },
    upgradePolicy: {
        mode: azure_native.compute.UpgradeMode.Automatic,
    },
    virtualMachineProfile: {
        networkProfile: {
            networkInterfaceConfigurations: [{
                enableIPForwarding: true,
                ipConfigurations: [{
                    name: "{vmss-name}",
                    subnet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    },
                }],
                name: "{vmss-name}",
                primary: true,
            }],
        },
        osProfile: {
            adminPassword: "{your-password}",
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
        },
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
                diskSizeGB: 512,
                managedDisk: {
                    storageAccountType: "Standard_LRS",
                },
            },
        },
    },
    vmScaleSetName: "{vmss-name}",
    zones: [
        "1",
        "3",
    ],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="centralus",
    overprovision=True,
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=2,
        name="Standard_A1_v2",
        tier="Standard",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyArgs(
        mode=azure_native.compute.UpgradeMode.AUTOMATIC,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        network_profile={
            "networkInterfaceConfigurations": [{
                "enableIPForwarding": True,
                "ipConfigurations": [{
                    "name": "{vmss-name}",
                    "subnet": azure_native.compute.ApiEntityReferenceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    ),
                }],
                "name": "{vmss-name}",
                "primary": True,
            }],
        },
        os_profile=azure_native.compute.VirtualMachineScaleSetOSProfileArgs(
            admin_password="{your-password}",
            admin_username="{your-username}",
            computer_name_prefix="{vmss-name}",
        ),
        storage_profile={
            "dataDisks": [
                azure_native.compute.VirtualMachineScaleSetDataDiskArgs(
                    create_option="Empty",
                    disk_size_gb=1023,
                    lun=0,
                ),
                azure_native.compute.VirtualMachineScaleSetDataDiskArgs(
                    create_option="Empty",
                    disk_size_gb=1023,
                    lun=1,
                ),
            ],
            "imageReference": azure_native.compute.ImageReferenceArgs(
                offer="WindowsServer",
                publisher="MicrosoftWindowsServer",
                sku="2016-Datacenter",
                version="latest",
            ),
            "osDisk": {
                "caching": azure_native.compute.CachingTypes.READ_WRITE,
                "createOption": "FromImage",
                "diskSizeGB": 512,
                "managedDisk": azure_native.compute.VirtualMachineScaleSetManagedDiskParametersArgs(
                    storage_account_type="Standard_LRS",
                ),
            },
        },
    ),
    vm_scale_set_name="{vmss-name}",
    zones=[
        "1",
        "3",
    ])

```

```yaml
resources:
  virtualMachineScaleSet:
    type: azure-native:compute:VirtualMachineScaleSet
    properties:
      location: centralus
      overprovision: true
      resourceGroupName: myResourceGroup
      sku:
        capacity: 2
        name: Standard_A1_v2
        tier: Standard
      upgradePolicy:
        mode: Automatic
      virtualMachineProfile:
        networkProfile:
          networkInterfaceConfigurations:
            - enableIPForwarding: true
              ipConfigurations:
                - name: '{vmss-name}'
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}
              name: '{vmss-name}'
              primary: true
        osProfile:
          adminPassword: '{your-password}'
          adminUsername: '{your-username}'
          computerNamePrefix: '{vmss-name}'
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
            diskSizeGB: 512
            managedDisk:
              storageAccountType: Standard_LRS
      vmScaleSetName: '{vmss-name}'
      zones:
        - '1'
        - '3'

```

{{% /example %}}
{{% example %}}
### Create a scale set with vm size properties
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "westus",
        Overprovision = true,
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 3,
            Name = "Standard_D1_v2",
            Tier = "Standard",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            Mode = AzureNative.Compute.UpgradeMode.Manual,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            HardwareProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetHardwareProfileArgs
            {
                VmSizeProperties = new AzureNative.Compute.Inputs.VMSizePropertiesArgs
                {
                    VCPUsAvailable = 1,
                    VCPUsPerCore = 1,
                },
            },
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminPassword = "{your-password}",
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
            },
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
                {
                    Offer = "WindowsServer",
                    Publisher = "MicrosoftWindowsServer",
                    Sku = "2016-Datacenter",
                    Version = "latest",
                },
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                    CreateOption = "FromImage",
                    ManagedDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetManagedDiskParametersArgs
                    {
                        StorageAccountType = "Standard_LRS",
                    },
                },
            },
            UserData = "RXhhbXBsZSBVc2VyRGF0YQ==",
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("westus")
            .overprovision(true)
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 3),
                Map.entry("name", "Standard_D1_v2"),
                Map.entry("tier", "Standard")
            ))
            .upgradePolicy(Map.of("mode", "Manual"))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("hardwareProfile", Map.of("vmSizeProperties", Map.ofEntries(
                    Map.entry("vCPUsAvailable", 1),
                    Map.entry("vCPUsPerCore", 1)
                ))),
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                    )),
                    Map.entry("name", "{vmss-name}"),
                    Map.entry("primary", true)
                ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminPassword", "{your-password}"),
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}")
                )),
                Map.entry("storageProfile", Map.ofEntries(
                    Map.entry("imageReference", Map.ofEntries(
                        Map.entry("offer", "WindowsServer"),
                        Map.entry("publisher", "MicrosoftWindowsServer"),
                        Map.entry("sku", "2016-Datacenter"),
                        Map.entry("version", "latest")
                    )),
                    Map.entry("osDisk", Map.ofEntries(
                        Map.entry("caching", "ReadWrite"),
                        Map.entry("createOption", "FromImage"),
                        Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS"))
                    ))
                )),
                Map.entry("userData", "RXhhbXBsZSBVc2VyRGF0YQ==")
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "westus",
    overprovision: true,
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 3,
        name: "Standard_D1_v2",
        tier: "Standard",
    },
    upgradePolicy: {
        mode: azure_native.compute.UpgradeMode.Manual,
    },
    virtualMachineProfile: {
        hardwareProfile: {
            vmSizeProperties: {
                vCPUsAvailable: 1,
                vCPUsPerCore: 1,
            },
        },
        networkProfile: {
            networkInterfaceConfigurations: [{
                enableIPForwarding: true,
                ipConfigurations: [{
                    name: "{vmss-name}",
                    subnet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    },
                }],
                name: "{vmss-name}",
                primary: true,
            }],
        },
        osProfile: {
            adminPassword: "{your-password}",
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
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
            },
        },
        userData: "RXhhbXBsZSBVc2VyRGF0YQ==",
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="westus",
    overprovision=True,
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=3,
        name="Standard_D1_v2",
        tier="Standard",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyArgs(
        mode=azure_native.compute.UpgradeMode.MANUAL,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        hardware_profile={
            "vmSizeProperties": azure_native.compute.VMSizePropertiesArgs(
                v_cpus_available=1,
                v_cpus_per_core=1,
            ),
        },
        network_profile={
            "networkInterfaceConfigurations": [{
                "enableIPForwarding": True,
                "ipConfigurations": [{
                    "name": "{vmss-name}",
                    "subnet": azure_native.compute.ApiEntityReferenceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    ),
                }],
                "name": "{vmss-name}",
                "primary": True,
            }],
        },
        os_profile=azure_native.compute.VirtualMachineScaleSetOSProfileArgs(
            admin_password="{your-password}",
            admin_username="{your-username}",
            computer_name_prefix="{vmss-name}",
        ),
        storage_profile={
            "imageReference": azure_native.compute.ImageReferenceArgs(
                offer="WindowsServer",
                publisher="MicrosoftWindowsServer",
                sku="2016-Datacenter",
                version="latest",
            ),
            "osDisk": {
                "caching": azure_native.compute.CachingTypes.READ_WRITE,
                "createOption": "FromImage",
                "managedDisk": azure_native.compute.VirtualMachineScaleSetManagedDiskParametersArgs(
                    storage_account_type="Standard_LRS",
                ),
            },
        },
        user_data="RXhhbXBsZSBVc2VyRGF0YQ==",
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml
resources:
  virtualMachineScaleSet:
    type: azure-native:compute:VirtualMachineScaleSet
    properties:
      location: westus
      overprovision: true
      resourceGroupName: myResourceGroup
      sku:
        capacity: 3
        name: Standard_D1_v2
        tier: Standard
      upgradePolicy:
        mode: Manual
      virtualMachineProfile:
        hardwareProfile:
          vmSizeProperties:
            vCPUsAvailable: 1
            vCPUsPerCore: 1
        networkProfile:
          networkInterfaceConfigurations:
            - enableIPForwarding: true
              ipConfigurations:
                - name: '{vmss-name}'
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}
              name: '{vmss-name}'
              primary: true
        osProfile:
          adminPassword: '{your-password}'
          adminUsername: '{your-username}'
          computerNamePrefix: '{vmss-name}'
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
        userData: RXhhbXBsZSBVc2VyRGF0YQ==
      vmScaleSetName: '{vmss-name}'

```

{{% /example %}}
{{% example %}}
### Create or update a scale set with capacity reservation.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSet = new AzureNative.Compute.VirtualMachineScaleSet("virtualMachineScaleSet", new()
    {
        Location = "westus",
        Overprovision = true,
        ResourceGroupName = "myResourceGroup",
        Sku = new AzureNative.Compute.Inputs.SkuArgs
        {
            Capacity = 3,
            Name = "Standard_DS1_v2",
            Tier = "Standard",
        },
        UpgradePolicy = new AzureNative.Compute.Inputs.UpgradePolicyArgs
        {
            Mode = AzureNative.Compute.UpgradeMode.Manual,
        },
        VirtualMachineProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProfileArgs
        {
            CapacityReservation = new AzureNative.Compute.Inputs.CapacityReservationProfileArgs
            {
                CapacityReservationGroup = new AzureNative.Compute.Inputs.SubResourceArgs
                {
                    Id = "subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/CapacityReservationGroups/{crgName}",
                },
            },
            NetworkProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkProfileArgs
            {
                NetworkInterfaceConfigurations = new[]
                {
                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                    {
                        EnableIPForwarding = true,
                        IpConfigurations = new[]
                        {
                            new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                            {
                                Name = "{vmss-name}",
                                Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                                {
                                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                                },
                            },
                        },
                        Name = "{vmss-name}",
                        Primary = true,
                    },
                },
            },
            OsProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSProfileArgs
            {
                AdminPassword = "{your-password}",
                AdminUsername = "{your-username}",
                ComputerNamePrefix = "{vmss-name}",
            },
            StorageProfile = new AzureNative.Compute.Inputs.VirtualMachineScaleSetStorageProfileArgs
            {
                ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
                {
                    Offer = "WindowsServer",
                    Publisher = "MicrosoftWindowsServer",
                    Sku = "2016-Datacenter",
                    Version = "latest",
                },
                OsDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetOSDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.ReadWrite,
                    CreateOption = "FromImage",
                    ManagedDisk = new AzureNative.Compute.Inputs.VirtualMachineScaleSetManagedDiskParametersArgs
                    {
                        StorageAccountType = "Standard_LRS",
                    },
                },
            },
        },
        VmScaleSetName = "{vmss-name}",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSet;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetArgs;
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
        var virtualMachineScaleSet = new VirtualMachineScaleSet("virtualMachineScaleSet", VirtualMachineScaleSetArgs.builder()        
            .location("westus")
            .overprovision(true)
            .resourceGroupName("myResourceGroup")
            .sku(Map.ofEntries(
                Map.entry("capacity", 3),
                Map.entry("name", "Standard_DS1_v2"),
                Map.entry("tier", "Standard")
            ))
            .upgradePolicy(Map.of("mode", "Manual"))
            .virtualMachineProfile(Map.ofEntries(
                Map.entry("capacityReservation", Map.of("capacityReservationGroup", Map.of("id", "subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/CapacityReservationGroups/{crgName}"))),
                Map.entry("networkProfile", Map.of("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("name", "{vmss-name}"),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}"))
                    )),
                    Map.entry("name", "{vmss-name}"),
                    Map.entry("primary", true)
                ))),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminPassword", "{your-password}"),
                    Map.entry("adminUsername", "{your-username}"),
                    Map.entry("computerNamePrefix", "{vmss-name}")
                )),
                Map.entry("storageProfile", Map.ofEntries(
                    Map.entry("imageReference", Map.ofEntries(
                        Map.entry("offer", "WindowsServer"),
                        Map.entry("publisher", "MicrosoftWindowsServer"),
                        Map.entry("sku", "2016-Datacenter"),
                        Map.entry("version", "latest")
                    )),
                    Map.entry("osDisk", Map.ofEntries(
                        Map.entry("caching", "ReadWrite"),
                        Map.entry("createOption", "FromImage"),
                        Map.entry("managedDisk", Map.of("storageAccountType", "Standard_LRS"))
                    ))
                ))
            ))
            .vmScaleSetName("{vmss-name}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSet = new azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet", {
    location: "westus",
    overprovision: true,
    resourceGroupName: "myResourceGroup",
    sku: {
        capacity: 3,
        name: "Standard_DS1_v2",
        tier: "Standard",
    },
    upgradePolicy: {
        mode: azure_native.compute.UpgradeMode.Manual,
    },
    virtualMachineProfile: {
        capacityReservation: {
            capacityReservationGroup: {
                id: "subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/CapacityReservationGroups/{crgName}",
            },
        },
        networkProfile: {
            networkInterfaceConfigurations: [{
                enableIPForwarding: true,
                ipConfigurations: [{
                    name: "{vmss-name}",
                    subnet: {
                        id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    },
                }],
                name: "{vmss-name}",
                primary: true,
            }],
        },
        osProfile: {
            adminPassword: "{your-password}",
            adminUsername: "{your-username}",
            computerNamePrefix: "{vmss-name}",
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
            },
        },
    },
    vmScaleSetName: "{vmss-name}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set = azure_native.compute.VirtualMachineScaleSet("virtualMachineScaleSet",
    location="westus",
    overprovision=True,
    resource_group_name="myResourceGroup",
    sku=azure_native.compute.SkuArgs(
        capacity=3,
        name="Standard_DS1_v2",
        tier="Standard",
    ),
    upgrade_policy=azure_native.compute.UpgradePolicyArgs(
        mode=azure_native.compute.UpgradeMode.MANUAL,
    ),
    virtual_machine_profile=azure_native.compute.VirtualMachineScaleSetVMProfileResponseArgs(
        capacity_reservation={
            "capacityReservationGroup": azure_native.compute.SubResourceArgs(
                id="subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/CapacityReservationGroups/{crgName}",
            ),
        },
        network_profile={
            "networkInterfaceConfigurations": [{
                "enableIPForwarding": True,
                "ipConfigurations": [{
                    "name": "{vmss-name}",
                    "subnet": azure_native.compute.ApiEntityReferenceArgs(
                        id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}",
                    ),
                }],
                "name": "{vmss-name}",
                "primary": True,
            }],
        },
        os_profile=azure_native.compute.VirtualMachineScaleSetOSProfileArgs(
            admin_password="{your-password}",
            admin_username="{your-username}",
            computer_name_prefix="{vmss-name}",
        ),
        storage_profile={
            "imageReference": azure_native.compute.ImageReferenceArgs(
                offer="WindowsServer",
                publisher="MicrosoftWindowsServer",
                sku="2016-Datacenter",
                version="latest",
            ),
            "osDisk": {
                "caching": azure_native.compute.CachingTypes.READ_WRITE,
                "createOption": "FromImage",
                "managedDisk": azure_native.compute.VirtualMachineScaleSetManagedDiskParametersArgs(
                    storage_account_type="Standard_LRS",
                ),
            },
        },
    ),
    vm_scale_set_name="{vmss-name}")

```

```yaml
resources:
  virtualMachineScaleSet:
    type: azure-native:compute:VirtualMachineScaleSet
    properties:
      location: westus
      overprovision: true
      resourceGroupName: myResourceGroup
      sku:
        capacity: 3
        name: Standard_DS1_v2
        tier: Standard
      upgradePolicy:
        mode: Manual
      virtualMachineProfile:
        capacityReservation:
          capacityReservationGroup:
            id: subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/CapacityReservationGroups/{crgName}
        networkProfile:
          networkInterfaceConfigurations:
            - enableIPForwarding: true
              ipConfigurations:
                - name: '{vmss-name}'
                  subnet:
                    id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/{existing-virtual-network-name}/subnets/{existing-subnet-name}
              name: '{vmss-name}'
              primary: true
        osProfile:
          adminPassword: '{your-password}'
          adminUsername: '{your-username}'
          computerNamePrefix: '{vmss-name}'
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
      vmScaleSetName: '{vmss-name}'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:compute:VirtualMachineScaleSet {vmss-name} /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/virtualMachineScaleSets/{vmss-name} 
```
