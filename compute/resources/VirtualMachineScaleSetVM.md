Describes a virtual machine scale set virtual machine.
API Version: 2022-11-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### VirtualMachineScaleSetVM_Update_MaximumSet_Gen
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSetVM = new AzureNative.Compute.VirtualMachineScaleSetVM("virtualMachineScaleSetVM", new()
    {
        AdditionalCapabilities = new AzureNative.Compute.Inputs.AdditionalCapabilitiesArgs
        {
            HibernationEnabled = true,
            UltraSSDEnabled = true,
        },
        AvailabilitySet = new AzureNative.Compute.Inputs.SubResourceArgs
        {
            Id = "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
        },
        DiagnosticsProfile = new AzureNative.Compute.Inputs.DiagnosticsProfileArgs
        {
            BootDiagnostics = new AzureNative.Compute.Inputs.BootDiagnosticsArgs
            {
                Enabled = true,
                StorageUri = "aaaaaaaaaaaaa",
            },
        },
        HardwareProfile = new AzureNative.Compute.Inputs.HardwareProfileArgs
        {
            VmSize = "Basic_A0",
            VmSizeProperties = new AzureNative.Compute.Inputs.VMSizePropertiesArgs
            {
                VCPUsAvailable = 9,
                VCPUsPerCore = 12,
            },
        },
        InstanceId = "aaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
        LicenseType = "aaaaaaaaaa",
        Location = "westus",
        NetworkProfile = new AzureNative.Compute.Inputs.NetworkProfileArgs
        {
            NetworkApiVersion = "2020-11-01",
            NetworkInterfaceConfigurations = new[]
            {
                new AzureNative.Compute.Inputs.VirtualMachineNetworkInterfaceConfigurationArgs
                {
                    DeleteOption = "Delete",
                    DnsSettings = new AzureNative.Compute.Inputs.VirtualMachineNetworkInterfaceDnsSettingsConfigurationArgs
                    {
                        DnsServers = new[]
                        {
                            "aaaaaa",
                        },
                    },
                    DscpConfiguration = new AzureNative.Compute.Inputs.SubResourceArgs
                    {
                        Id = "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                    },
                    EnableAcceleratedNetworking = true,
                    EnableFpga = true,
                    EnableIPForwarding = true,
                    IpConfigurations = new[]
                    {
                        new AzureNative.Compute.Inputs.VirtualMachineNetworkInterfaceIPConfigurationArgs
                        {
                            ApplicationGatewayBackendAddressPools = new[]
                            {
                                new AzureNative.Compute.Inputs.SubResourceArgs
                                {
                                    Id = "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                                },
                            },
                            ApplicationSecurityGroups = new[]
                            {
                                new AzureNative.Compute.Inputs.SubResourceArgs
                                {
                                    Id = "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                                },
                            },
                            LoadBalancerBackendAddressPools = new[]
                            {
                                new AzureNative.Compute.Inputs.SubResourceArgs
                                {
                                    Id = "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                                },
                            },
                            Name = "aa",
                            Primary = true,
                            PrivateIPAddressVersion = "IPv4",
                            PublicIPAddressConfiguration = new AzureNative.Compute.Inputs.VirtualMachinePublicIPAddressConfigurationArgs
                            {
                                DeleteOption = "Delete",
                                DnsSettings = new AzureNative.Compute.Inputs.VirtualMachinePublicIPAddressDnsSettingsConfigurationArgs
                                {
                                    DomainNameLabel = "aaaaaaaaaaaaaaaaaaaaaaaaa",
                                },
                                IdleTimeoutInMinutes = 2,
                                IpTags = new[]
                                {
                                    new AzureNative.Compute.Inputs.VirtualMachineIpTagArgs
                                    {
                                        IpTagType = "aaaaaaaaaaaaaaaaaaaaaaaaa",
                                        Tag = "aaaaaaaaaaaaaaaaaaaa",
                                    },
                                },
                                Name = "aaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
                                PublicIPAddressVersion = "IPv4",
                                PublicIPAllocationMethod = "Dynamic",
                                PublicIPPrefix = new AzureNative.Compute.Inputs.SubResourceArgs
                                {
                                    Id = "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                                },
                                Sku = new AzureNative.Compute.Inputs.PublicIPAddressSkuArgs
                                {
                                    Name = "Basic",
                                    Tier = "Regional",
                                },
                            },
                            Subnet = new AzureNative.Compute.Inputs.SubResourceArgs
                            {
                                Id = "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                            },
                        },
                    },
                    Name = "aaaaaaaaaaa",
                    NetworkSecurityGroup = new AzureNative.Compute.Inputs.SubResourceArgs
                    {
                        Id = "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                    },
                    Primary = true,
                },
            },
            NetworkInterfaces = new[]
            {
                new AzureNative.Compute.Inputs.NetworkInterfaceReferenceArgs
                {
                    DeleteOption = "Delete",
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/virtualMachineScaleSets/{vmss-name}/virtualMachines/0/networkInterfaces/vmsstestnetconfig5415",
                    Primary = true,
                },
            },
        },
        NetworkProfileConfiguration = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMNetworkProfileConfigurationArgs
        {
            NetworkInterfaceConfigurations = new[]
            {
                new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationArgs
                {
                    DeleteOption = "Delete",
                    DnsSettings = new AzureNative.Compute.Inputs.VirtualMachineScaleSetNetworkConfigurationDnsSettingsArgs
                    {
                        DnsServers = new[] {},
                    },
                    EnableAcceleratedNetworking = true,
                    EnableFpga = true,
                    EnableIPForwarding = true,
                    IpConfigurations = new[]
                    {
                        new AzureNative.Compute.Inputs.VirtualMachineScaleSetIPConfigurationArgs
                        {
                            ApplicationGatewayBackendAddressPools = new[]
                            {
                                new AzureNative.Compute.Inputs.SubResourceArgs
                                {
                                    Id = "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                                },
                            },
                            ApplicationSecurityGroups = new[]
                            {
                                new AzureNative.Compute.Inputs.SubResourceArgs
                                {
                                    Id = "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                                },
                            },
                            LoadBalancerBackendAddressPools = new[]
                            {
                                new AzureNative.Compute.Inputs.SubResourceArgs
                                {
                                    Id = "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                                },
                            },
                            LoadBalancerInboundNatPools = new[]
                            {
                                new AzureNative.Compute.Inputs.SubResourceArgs
                                {
                                    Id = "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                                },
                            },
                            Name = "vmsstestnetconfig9693",
                            Primary = true,
                            PrivateIPAddressVersion = "IPv4",
                            PublicIPAddressConfiguration = new AzureNative.Compute.Inputs.VirtualMachineScaleSetPublicIPAddressConfigurationArgs
                            {
                                DeleteOption = "Delete",
                                DnsSettings = new AzureNative.Compute.Inputs.VirtualMachineScaleSetPublicIPAddressConfigurationDnsSettingsArgs
                                {
                                    DomainNameLabel = "aaaaaaaaaaaaaaaaaa",
                                },
                                IdleTimeoutInMinutes = 18,
                                IpTags = new[]
                                {
                                    new AzureNative.Compute.Inputs.VirtualMachineScaleSetIpTagArgs
                                    {
                                        IpTagType = "aaaaaaa",
                                        Tag = "aaaaaaaaaaaaaaaaaaaaaaaaaaa",
                                    },
                                },
                                Name = "aaaaaaaaaaaaaaaaaa",
                                PublicIPAddressVersion = "IPv4",
                                PublicIPPrefix = new AzureNative.Compute.Inputs.SubResourceArgs
                                {
                                    Id = "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                                },
                                Sku = new AzureNative.Compute.Inputs.PublicIPAddressSkuArgs
                                {
                                    Name = "Basic",
                                    Tier = "Regional",
                                },
                            },
                            Subnet = new AzureNative.Compute.Inputs.ApiEntityReferenceArgs
                            {
                                Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/vn4071/subnets/sn5503",
                            },
                        },
                    },
                    Name = "vmsstestnetconfig5415",
                    NetworkSecurityGroup = new AzureNative.Compute.Inputs.SubResourceArgs
                    {
                        Id = "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                    },
                    Primary = true,
                },
            },
        },
        OsProfile = new AzureNative.Compute.Inputs.OSProfileArgs
        {
            AdminPassword = "aaaaaaaaaaaaaaaa",
            AdminUsername = "Foo12",
            AllowExtensionOperations = true,
            ComputerName = "test000000",
            CustomData = "aaaa",
            LinuxConfiguration = new AzureNative.Compute.Inputs.LinuxConfigurationArgs
            {
                DisablePasswordAuthentication = true,
                PatchSettings = new AzureNative.Compute.Inputs.LinuxPatchSettingsArgs
                {
                    AssessmentMode = "ImageDefault",
                    PatchMode = "ImageDefault",
                },
                ProvisionVMAgent = true,
                Ssh = new AzureNative.Compute.Inputs.SshConfigurationArgs
                {
                    PublicKeys = new[]
                    {
                        new AzureNative.Compute.Inputs.SshPublicKeyArgs
                        {
                            KeyData = "aaaaaa",
                            Path = "aaa",
                        },
                    },
                },
            },
            RequireGuestProvisionSignal = true,
            Secrets = new[] {},
            WindowsConfiguration = new AzureNative.Compute.Inputs.WindowsConfigurationArgs
            {
                AdditionalUnattendContent = new[]
                {
                    new AzureNative.Compute.Inputs.AdditionalUnattendContentArgs
                    {
                        ComponentName = AzureNative.Compute.ComponentNames.Microsoft_Windows_Shell_Setup,
                        Content = "aaaaaaaaaaaaaaaaaaaa",
                        PassName = AzureNative.Compute.PassNames.OobeSystem,
                        SettingName = AzureNative.Compute.SettingNames.AutoLogon,
                    },
                },
                EnableAutomaticUpdates = true,
                PatchSettings = new AzureNative.Compute.Inputs.PatchSettingsArgs
                {
                    AssessmentMode = "ImageDefault",
                    EnableHotpatching = true,
                    PatchMode = "Manual",
                },
                ProvisionVMAgent = true,
                TimeZone = "aaaaaaaaaaaaaaaaaaaaaaaaaaa",
                WinRM = new AzureNative.Compute.Inputs.WinRMConfigurationArgs
                {
                    Listeners = new[]
                    {
                        new AzureNative.Compute.Inputs.WinRMListenerArgs
                        {
                            CertificateUrl = "aaaaaaaaaaaaaaaaaaaaaa",
                            Protocol = AzureNative.Compute.ProtocolTypes.Http,
                        },
                    },
                },
            },
        },
        Plan = new AzureNative.Compute.Inputs.PlanArgs
        {
            Name = "aaaaaaaaaa",
            Product = "aaaaaaaaaaaaaaaaaaaa",
            PromotionCode = "aaaaaaaaaaaaaaaaaaaa",
            Publisher = "aaaaaaaaaaaaaaaaaaaaaa",
        },
        ProtectionPolicy = new AzureNative.Compute.Inputs.VirtualMachineScaleSetVMProtectionPolicyArgs
        {
            ProtectFromScaleIn = true,
            ProtectFromScaleSetActions = true,
        },
        ResourceGroupName = "rgcompute",
        SecurityProfile = new AzureNative.Compute.Inputs.SecurityProfileArgs
        {
            EncryptionAtHost = true,
            SecurityType = "TrustedLaunch",
            UefiSettings = new AzureNative.Compute.Inputs.UefiSettingsArgs
            {
                SecureBootEnabled = true,
                VTpmEnabled = true,
            },
        },
        StorageProfile = new AzureNative.Compute.Inputs.StorageProfileArgs
        {
            DataDisks = new[]
            {
                new AzureNative.Compute.Inputs.DataDiskArgs
                {
                    Caching = AzureNative.Compute.CachingTypes.None,
                    CreateOption = "Empty",
                    DeleteOption = "Delete",
                    DetachOption = "ForceDetach",
                    DiskSizeGB = 128,
                    Image = new AzureNative.Compute.Inputs.VirtualHardDiskArgs
                    {
                        Uri = "https://{storageAccountName}.blob.core.windows.net/{containerName}/{vhdName}.vhd",
                    },
                    Lun = 1,
                    ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                    {
                        DiskEncryptionSet = new AzureNative.Compute.Inputs.DiskEncryptionSetParametersArgs
                        {
                            Id = "aaaaaaaaaaaa",
                        },
                        Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/vmss3176_vmss3176_0_disk2_6c4f554bdafa49baa780eb2d128ff39d",
                        StorageAccountType = "Standard_LRS",
                    },
                    Name = "vmss3176_vmss3176_0_disk2_6c4f554bdafa49baa780eb2d128ff39d",
                    ToBeDetached = true,
                    Vhd = new AzureNative.Compute.Inputs.VirtualHardDiskArgs
                    {
                        Uri = "https://{storageAccountName}.blob.core.windows.net/{containerName}/{vhdName}.vhd",
                    },
                    WriteAcceleratorEnabled = true,
                },
            },
            ImageReference = new AzureNative.Compute.Inputs.ImageReferenceArgs
            {
                Id = "a",
                Offer = "WindowsServer",
                Publisher = "MicrosoftWindowsServer",
                SharedGalleryImageId = "aaaaaaaaaaaaaaaaaaaa",
                Sku = "2012-R2-Datacenter",
                Version = "4.127.20180315",
            },
            OsDisk = new AzureNative.Compute.Inputs.OSDiskArgs
            {
                Caching = AzureNative.Compute.CachingTypes.None,
                CreateOption = "FromImage",
                DeleteOption = "Delete",
                DiffDiskSettings = new AzureNative.Compute.Inputs.DiffDiskSettingsArgs
                {
                    Option = "Local",
                    Placement = "CacheDisk",
                },
                DiskSizeGB = 127,
                EncryptionSettings = new AzureNative.Compute.Inputs.DiskEncryptionSettingsArgs
                {
                    DiskEncryptionKey = new AzureNative.Compute.Inputs.KeyVaultSecretReferenceArgs
                    {
                        SecretUrl = "aaaaaaaa",
                        SourceVault = new AzureNative.Compute.Inputs.SubResourceArgs
                        {
                            Id = "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                        },
                    },
                    Enabled = true,
                    KeyEncryptionKey = new AzureNative.Compute.Inputs.KeyVaultKeyReferenceArgs
                    {
                        KeyUrl = "aaaaaaaaaaaaaa",
                        SourceVault = new AzureNative.Compute.Inputs.SubResourceArgs
                        {
                            Id = "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                        },
                    },
                },
                Image = new AzureNative.Compute.Inputs.VirtualHardDiskArgs
                {
                    Uri = "https://{storageAccountName}.blob.core.windows.net/{containerName}/{vhdName}.vhd",
                },
                ManagedDisk = new AzureNative.Compute.Inputs.ManagedDiskParametersArgs
                {
                    DiskEncryptionSet = new AzureNative.Compute.Inputs.DiskEncryptionSetParametersArgs
                    {
                        Id = "aaaaaaaaaaaa",
                    },
                    Id = "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/vmss3176_vmss3176_0_OsDisk_1_6d72b805e50e4de6830303c5055077fc",
                    StorageAccountType = "Standard_LRS",
                },
                Name = "vmss3176_vmss3176_0_OsDisk_1_6d72b805e50e4de6830303c5055077fc",
                OsType = AzureNative.Compute.OperatingSystemTypes.Windows,
                Vhd = new AzureNative.Compute.Inputs.VirtualHardDiskArgs
                {
                    Uri = "https://{storageAccountName}.blob.core.windows.net/{containerName}/{vhdName}.vhd",
                },
                WriteAcceleratorEnabled = true,
            },
        },
        Tags = null,
        UserData = "RXhhbXBsZSBVc2VyRGF0YQ==",
        VmScaleSetName = "aaaaaaaaaaaaaa",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetVM;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetVMArgs;
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
        var virtualMachineScaleSetVM = new VirtualMachineScaleSetVM("virtualMachineScaleSetVM", VirtualMachineScaleSetVMArgs.builder()        
            .additionalCapabilities(Map.ofEntries(
                Map.entry("hibernationEnabled", true),
                Map.entry("ultraSSDEnabled", true)
            ))
            .availabilitySet(Map.of("id", "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}"))
            .diagnosticsProfile(Map.of("bootDiagnostics", Map.ofEntries(
                Map.entry("enabled", true),
                Map.entry("storageUri", "aaaaaaaaaaaaa")
            )))
            .hardwareProfile(Map.ofEntries(
                Map.entry("vmSize", "Basic_A0"),
                Map.entry("vmSizeProperties", Map.ofEntries(
                    Map.entry("vCPUsAvailable", 9),
                    Map.entry("vCPUsPerCore", 12)
                ))
            ))
            .instanceId("aaaaaaaaaaaaaaaaaaaaaaaaaaaaa")
            .licenseType("aaaaaaaaaa")
            .location("westus")
            .networkProfile(Map.ofEntries(
                Map.entry("networkApiVersion", "2020-11-01"),
                Map.entry("networkInterfaceConfigurations", Map.ofEntries(
                    Map.entry("deleteOption", "Delete"),
                    Map.entry("dnsSettings", Map.of("dnsServers", "aaaaaa")),
                    Map.entry("dscpConfiguration", Map.of("id", "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}")),
                    Map.entry("enableAcceleratedNetworking", true),
                    Map.entry("enableFpga", true),
                    Map.entry("enableIPForwarding", true),
                    Map.entry("ipConfigurations", Map.ofEntries(
                        Map.entry("applicationGatewayBackendAddressPools", Map.of("id", "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}")),
                        Map.entry("applicationSecurityGroups", Map.of("id", "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}")),
                        Map.entry("loadBalancerBackendAddressPools", Map.of("id", "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}")),
                        Map.entry("name", "aa"),
                        Map.entry("primary", true),
                        Map.entry("privateIPAddressVersion", "IPv4"),
                        Map.entry("publicIPAddressConfiguration", Map.ofEntries(
                            Map.entry("deleteOption", "Delete"),
                            Map.entry("dnsSettings", Map.of("domainNameLabel", "aaaaaaaaaaaaaaaaaaaaaaaaa")),
                            Map.entry("idleTimeoutInMinutes", 2),
                            Map.entry("ipTags", Map.ofEntries(
                                Map.entry("ipTagType", "aaaaaaaaaaaaaaaaaaaaaaaaa"),
                                Map.entry("tag", "aaaaaaaaaaaaaaaaaaaa")
                            )),
                            Map.entry("name", "aaaaaaaaaaaaaaaaaaaaaaaaaaaaa"),
                            Map.entry("publicIPAddressVersion", "IPv4"),
                            Map.entry("publicIPAllocationMethod", "Dynamic"),
                            Map.entry("publicIPPrefix", Map.of("id", "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}")),
                            Map.entry("sku", Map.ofEntries(
                                Map.entry("name", "Basic"),
                                Map.entry("tier", "Regional")
                            ))
                        )),
                        Map.entry("subnet", Map.of("id", "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}"))
                    )),
                    Map.entry("name", "aaaaaaaaaaa"),
                    Map.entry("networkSecurityGroup", Map.of("id", "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}")),
                    Map.entry("primary", true)
                )),
                Map.entry("networkInterfaces", Map.ofEntries(
                    Map.entry("deleteOption", "Delete"),
                    Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/virtualMachineScaleSets/{vmss-name}/virtualMachines/0/networkInterfaces/vmsstestnetconfig5415"),
                    Map.entry("primary", true)
                ))
            ))
            .networkProfileConfiguration(Map.of("networkInterfaceConfigurations", Map.ofEntries(
                Map.entry("deleteOption", "Delete"),
                Map.entry("dnsSettings", Map.of("dnsServers", )),
                Map.entry("enableAcceleratedNetworking", true),
                Map.entry("enableFpga", true),
                Map.entry("enableIPForwarding", true),
                Map.entry("ipConfigurations", Map.ofEntries(
                    Map.entry("applicationGatewayBackendAddressPools", Map.of("id", "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}")),
                    Map.entry("applicationSecurityGroups", Map.of("id", "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}")),
                    Map.entry("loadBalancerBackendAddressPools", Map.of("id", "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}")),
                    Map.entry("loadBalancerInboundNatPools", Map.of("id", "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}")),
                    Map.entry("name", "vmsstestnetconfig9693"),
                    Map.entry("primary", true),
                    Map.entry("privateIPAddressVersion", "IPv4"),
                    Map.entry("publicIPAddressConfiguration", Map.ofEntries(
                        Map.entry("deleteOption", "Delete"),
                        Map.entry("dnsSettings", Map.of("domainNameLabel", "aaaaaaaaaaaaaaaaaa")),
                        Map.entry("idleTimeoutInMinutes", 18),
                        Map.entry("ipTags", Map.ofEntries(
                            Map.entry("ipTagType", "aaaaaaa"),
                            Map.entry("tag", "aaaaaaaaaaaaaaaaaaaaaaaaaaa")
                        )),
                        Map.entry("name", "aaaaaaaaaaaaaaaaaa"),
                        Map.entry("publicIPAddressVersion", "IPv4"),
                        Map.entry("publicIPPrefix", Map.of("id", "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}")),
                        Map.entry("sku", Map.ofEntries(
                            Map.entry("name", "Basic"),
                            Map.entry("tier", "Regional")
                        ))
                    )),
                    Map.entry("subnet", Map.of("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/vn4071/subnets/sn5503"))
                )),
                Map.entry("name", "vmsstestnetconfig5415"),
                Map.entry("networkSecurityGroup", Map.of("id", "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}")),
                Map.entry("primary", true)
            )))
            .osProfile(Map.ofEntries(
                Map.entry("adminPassword", "aaaaaaaaaaaaaaaa"),
                Map.entry("adminUsername", "Foo12"),
                Map.entry("allowExtensionOperations", true),
                Map.entry("computerName", "test000000"),
                Map.entry("customData", "aaaa"),
                Map.entry("linuxConfiguration", Map.ofEntries(
                    Map.entry("disablePasswordAuthentication", true),
                    Map.entry("patchSettings", Map.ofEntries(
                        Map.entry("assessmentMode", "ImageDefault"),
                        Map.entry("patchMode", "ImageDefault")
                    )),
                    Map.entry("provisionVMAgent", true),
                    Map.entry("ssh", Map.of("publicKeys", Map.ofEntries(
                        Map.entry("keyData", "aaaaaa"),
                        Map.entry("path", "aaa")
                    )))
                )),
                Map.entry("requireGuestProvisionSignal", true),
                Map.entry("secrets", ),
                Map.entry("windowsConfiguration", Map.ofEntries(
                    Map.entry("additionalUnattendContent", Map.ofEntries(
                        Map.entry("componentName", "Microsoft-Windows-Shell-Setup"),
                        Map.entry("content", "aaaaaaaaaaaaaaaaaaaa"),
                        Map.entry("passName", "OobeSystem"),
                        Map.entry("settingName", "AutoLogon")
                    )),
                    Map.entry("enableAutomaticUpdates", true),
                    Map.entry("patchSettings", Map.ofEntries(
                        Map.entry("assessmentMode", "ImageDefault"),
                        Map.entry("enableHotpatching", true),
                        Map.entry("patchMode", "Manual")
                    )),
                    Map.entry("provisionVMAgent", true),
                    Map.entry("timeZone", "aaaaaaaaaaaaaaaaaaaaaaaaaaa"),
                    Map.entry("winRM", Map.of("listeners", Map.ofEntries(
                        Map.entry("certificateUrl", "aaaaaaaaaaaaaaaaaaaaaa"),
                        Map.entry("protocol", "Http")
                    )))
                ))
            ))
            .plan(Map.ofEntries(
                Map.entry("name", "aaaaaaaaaa"),
                Map.entry("product", "aaaaaaaaaaaaaaaaaaaa"),
                Map.entry("promotionCode", "aaaaaaaaaaaaaaaaaaaa"),
                Map.entry("publisher", "aaaaaaaaaaaaaaaaaaaaaa")
            ))
            .protectionPolicy(Map.ofEntries(
                Map.entry("protectFromScaleIn", true),
                Map.entry("protectFromScaleSetActions", true)
            ))
            .resourceGroupName("rgcompute")
            .securityProfile(Map.ofEntries(
                Map.entry("encryptionAtHost", true),
                Map.entry("securityType", "TrustedLaunch"),
                Map.entry("uefiSettings", Map.ofEntries(
                    Map.entry("secureBootEnabled", true),
                    Map.entry("vTpmEnabled", true)
                ))
            ))
            .storageProfile(Map.ofEntries(
                Map.entry("dataDisks", Map.ofEntries(
                    Map.entry("caching", "None"),
                    Map.entry("createOption", "Empty"),
                    Map.entry("deleteOption", "Delete"),
                    Map.entry("detachOption", "ForceDetach"),
                    Map.entry("diskSizeGB", 128),
                    Map.entry("image", Map.of("uri", "https://{storageAccountName}.blob.core.windows.net/{containerName}/{vhdName}.vhd")),
                    Map.entry("lun", 1),
                    Map.entry("managedDisk", Map.ofEntries(
                        Map.entry("diskEncryptionSet", Map.of("id", "aaaaaaaaaaaa")),
                        Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/vmss3176_vmss3176_0_disk2_6c4f554bdafa49baa780eb2d128ff39d"),
                        Map.entry("storageAccountType", "Standard_LRS")
                    )),
                    Map.entry("name", "vmss3176_vmss3176_0_disk2_6c4f554bdafa49baa780eb2d128ff39d"),
                    Map.entry("toBeDetached", true),
                    Map.entry("vhd", Map.of("uri", "https://{storageAccountName}.blob.core.windows.net/{containerName}/{vhdName}.vhd")),
                    Map.entry("writeAcceleratorEnabled", true)
                )),
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("id", "a"),
                    Map.entry("offer", "WindowsServer"),
                    Map.entry("publisher", "MicrosoftWindowsServer"),
                    Map.entry("sharedGalleryImageId", "aaaaaaaaaaaaaaaaaaaa"),
                    Map.entry("sku", "2012-R2-Datacenter"),
                    Map.entry("version", "4.127.20180315")
                )),
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("caching", "None"),
                    Map.entry("createOption", "FromImage"),
                    Map.entry("deleteOption", "Delete"),
                    Map.entry("diffDiskSettings", Map.ofEntries(
                        Map.entry("option", "Local"),
                        Map.entry("placement", "CacheDisk")
                    )),
                    Map.entry("diskSizeGB", 127),
                    Map.entry("encryptionSettings", Map.ofEntries(
                        Map.entry("diskEncryptionKey", Map.ofEntries(
                            Map.entry("secretUrl", "aaaaaaaa"),
                            Map.entry("sourceVault", Map.of("id", "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}"))
                        )),
                        Map.entry("enabled", true),
                        Map.entry("keyEncryptionKey", Map.ofEntries(
                            Map.entry("keyUrl", "aaaaaaaaaaaaaa"),
                            Map.entry("sourceVault", Map.of("id", "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}"))
                        ))
                    )),
                    Map.entry("image", Map.of("uri", "https://{storageAccountName}.blob.core.windows.net/{containerName}/{vhdName}.vhd")),
                    Map.entry("managedDisk", Map.ofEntries(
                        Map.entry("diskEncryptionSet", Map.of("id", "aaaaaaaaaaaa")),
                        Map.entry("id", "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/vmss3176_vmss3176_0_OsDisk_1_6d72b805e50e4de6830303c5055077fc"),
                        Map.entry("storageAccountType", "Standard_LRS")
                    )),
                    Map.entry("name", "vmss3176_vmss3176_0_OsDisk_1_6d72b805e50e4de6830303c5055077fc"),
                    Map.entry("osType", "Windows"),
                    Map.entry("vhd", Map.of("uri", "https://{storageAccountName}.blob.core.windows.net/{containerName}/{vhdName}.vhd")),
                    Map.entry("writeAcceleratorEnabled", true)
                ))
            ))
            .tags()
            .userData("RXhhbXBsZSBVc2VyRGF0YQ==")
            .vmScaleSetName("aaaaaaaaaaaaaa")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSetVM = new azure_native.compute.VirtualMachineScaleSetVM("virtualMachineScaleSetVM", {
    additionalCapabilities: {
        hibernationEnabled: true,
        ultraSSDEnabled: true,
    },
    availabilitySet: {
        id: "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
    },
    diagnosticsProfile: {
        bootDiagnostics: {
            enabled: true,
            storageUri: "aaaaaaaaaaaaa",
        },
    },
    hardwareProfile: {
        vmSize: "Basic_A0",
        vmSizeProperties: {
            vCPUsAvailable: 9,
            vCPUsPerCore: 12,
        },
    },
    instanceId: "aaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    licenseType: "aaaaaaaaaa",
    location: "westus",
    networkProfile: {
        networkApiVersion: "2020-11-01",
        networkInterfaceConfigurations: [{
            deleteOption: "Delete",
            dnsSettings: {
                dnsServers: ["aaaaaa"],
            },
            dscpConfiguration: {
                id: "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
            },
            enableAcceleratedNetworking: true,
            enableFpga: true,
            enableIPForwarding: true,
            ipConfigurations: [{
                applicationGatewayBackendAddressPools: [{
                    id: "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                }],
                applicationSecurityGroups: [{
                    id: "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                }],
                loadBalancerBackendAddressPools: [{
                    id: "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                }],
                name: "aa",
                primary: true,
                privateIPAddressVersion: "IPv4",
                publicIPAddressConfiguration: {
                    deleteOption: "Delete",
                    dnsSettings: {
                        domainNameLabel: "aaaaaaaaaaaaaaaaaaaaaaaaa",
                    },
                    idleTimeoutInMinutes: 2,
                    ipTags: [{
                        ipTagType: "aaaaaaaaaaaaaaaaaaaaaaaaa",
                        tag: "aaaaaaaaaaaaaaaaaaaa",
                    }],
                    name: "aaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
                    publicIPAddressVersion: "IPv4",
                    publicIPAllocationMethod: "Dynamic",
                    publicIPPrefix: {
                        id: "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                    },
                    sku: {
                        name: "Basic",
                        tier: "Regional",
                    },
                },
                subnet: {
                    id: "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                },
            }],
            name: "aaaaaaaaaaa",
            networkSecurityGroup: {
                id: "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
            },
            primary: true,
        }],
        networkInterfaces: [{
            deleteOption: "Delete",
            id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/virtualMachineScaleSets/{vmss-name}/virtualMachines/0/networkInterfaces/vmsstestnetconfig5415",
            primary: true,
        }],
    },
    networkProfileConfiguration: {
        networkInterfaceConfigurations: [{
            deleteOption: "Delete",
            dnsSettings: {
                dnsServers: [],
            },
            enableAcceleratedNetworking: true,
            enableFpga: true,
            enableIPForwarding: true,
            ipConfigurations: [{
                applicationGatewayBackendAddressPools: [{
                    id: "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                }],
                applicationSecurityGroups: [{
                    id: "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                }],
                loadBalancerBackendAddressPools: [{
                    id: "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                }],
                loadBalancerInboundNatPools: [{
                    id: "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                }],
                name: "vmsstestnetconfig9693",
                primary: true,
                privateIPAddressVersion: "IPv4",
                publicIPAddressConfiguration: {
                    deleteOption: "Delete",
                    dnsSettings: {
                        domainNameLabel: "aaaaaaaaaaaaaaaaaa",
                    },
                    idleTimeoutInMinutes: 18,
                    ipTags: [{
                        ipTagType: "aaaaaaa",
                        tag: "aaaaaaaaaaaaaaaaaaaaaaaaaaa",
                    }],
                    name: "aaaaaaaaaaaaaaaaaa",
                    publicIPAddressVersion: "IPv4",
                    publicIPPrefix: {
                        id: "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                    },
                    sku: {
                        name: "Basic",
                        tier: "Regional",
                    },
                },
                subnet: {
                    id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/vn4071/subnets/sn5503",
                },
            }],
            name: "vmsstestnetconfig5415",
            networkSecurityGroup: {
                id: "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
            },
            primary: true,
        }],
    },
    osProfile: {
        adminPassword: "aaaaaaaaaaaaaaaa",
        adminUsername: "Foo12",
        allowExtensionOperations: true,
        computerName: "test000000",
        customData: "aaaa",
        linuxConfiguration: {
            disablePasswordAuthentication: true,
            patchSettings: {
                assessmentMode: "ImageDefault",
                patchMode: "ImageDefault",
            },
            provisionVMAgent: true,
            ssh: {
                publicKeys: [{
                    keyData: "aaaaaa",
                    path: "aaa",
                }],
            },
        },
        requireGuestProvisionSignal: true,
        secrets: [],
        windowsConfiguration: {
            additionalUnattendContent: [{
                componentName: azure_native.compute.ComponentNames.Microsoft_Windows_Shell_Setup,
                content: "aaaaaaaaaaaaaaaaaaaa",
                passName: azure_native.compute.PassNames.OobeSystem,
                settingName: azure_native.compute.SettingNames.AutoLogon,
            }],
            enableAutomaticUpdates: true,
            patchSettings: {
                assessmentMode: "ImageDefault",
                enableHotpatching: true,
                patchMode: "Manual",
            },
            provisionVMAgent: true,
            timeZone: "aaaaaaaaaaaaaaaaaaaaaaaaaaa",
            winRM: {
                listeners: [{
                    certificateUrl: "aaaaaaaaaaaaaaaaaaaaaa",
                    protocol: azure_native.compute.ProtocolTypes.Http,
                }],
            },
        },
    },
    plan: {
        name: "aaaaaaaaaa",
        product: "aaaaaaaaaaaaaaaaaaaa",
        promotionCode: "aaaaaaaaaaaaaaaaaaaa",
        publisher: "aaaaaaaaaaaaaaaaaaaaaa",
    },
    protectionPolicy: {
        protectFromScaleIn: true,
        protectFromScaleSetActions: true,
    },
    resourceGroupName: "rgcompute",
    securityProfile: {
        encryptionAtHost: true,
        securityType: "TrustedLaunch",
        uefiSettings: {
            secureBootEnabled: true,
            vTpmEnabled: true,
        },
    },
    storageProfile: {
        dataDisks: [{
            caching: azure_native.compute.CachingTypes.None,
            createOption: "Empty",
            deleteOption: "Delete",
            detachOption: "ForceDetach",
            diskSizeGB: 128,
            image: {
                uri: "https://{storageAccountName}.blob.core.windows.net/{containerName}/{vhdName}.vhd",
            },
            lun: 1,
            managedDisk: {
                diskEncryptionSet: {
                    id: "aaaaaaaaaaaa",
                },
                id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/vmss3176_vmss3176_0_disk2_6c4f554bdafa49baa780eb2d128ff39d",
                storageAccountType: "Standard_LRS",
            },
            name: "vmss3176_vmss3176_0_disk2_6c4f554bdafa49baa780eb2d128ff39d",
            toBeDetached: true,
            vhd: {
                uri: "https://{storageAccountName}.blob.core.windows.net/{containerName}/{vhdName}.vhd",
            },
            writeAcceleratorEnabled: true,
        }],
        imageReference: {
            id: "a",
            offer: "WindowsServer",
            publisher: "MicrosoftWindowsServer",
            sharedGalleryImageId: "aaaaaaaaaaaaaaaaaaaa",
            sku: "2012-R2-Datacenter",
            version: "4.127.20180315",
        },
        osDisk: {
            caching: azure_native.compute.CachingTypes.None,
            createOption: "FromImage",
            deleteOption: "Delete",
            diffDiskSettings: {
                option: "Local",
                placement: "CacheDisk",
            },
            diskSizeGB: 127,
            encryptionSettings: {
                diskEncryptionKey: {
                    secretUrl: "aaaaaaaa",
                    sourceVault: {
                        id: "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                    },
                },
                enabled: true,
                keyEncryptionKey: {
                    keyUrl: "aaaaaaaaaaaaaa",
                    sourceVault: {
                        id: "/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                    },
                },
            },
            image: {
                uri: "https://{storageAccountName}.blob.core.windows.net/{containerName}/{vhdName}.vhd",
            },
            managedDisk: {
                diskEncryptionSet: {
                    id: "aaaaaaaaaaaa",
                },
                id: "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/vmss3176_vmss3176_0_OsDisk_1_6d72b805e50e4de6830303c5055077fc",
                storageAccountType: "Standard_LRS",
            },
            name: "vmss3176_vmss3176_0_OsDisk_1_6d72b805e50e4de6830303c5055077fc",
            osType: azure_native.compute.OperatingSystemTypes.Windows,
            vhd: {
                uri: "https://{storageAccountName}.blob.core.windows.net/{containerName}/{vhdName}.vhd",
            },
            writeAcceleratorEnabled: true,
        },
    },
    tags: {},
    userData: "RXhhbXBsZSBVc2VyRGF0YQ==",
    vmScaleSetName: "aaaaaaaaaaaaaa",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set_vm = azure_native.compute.VirtualMachineScaleSetVM("virtualMachineScaleSetVM",
    additional_capabilities=azure_native.compute.AdditionalCapabilitiesArgs(
        hibernation_enabled=True,
        ultra_ssd_enabled=True,
    ),
    availability_set=azure_native.compute.SubResourceArgs(
        id="/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
    ),
    diagnostics_profile=azure_native.compute.DiagnosticsProfileResponseArgs(
        boot_diagnostics=azure_native.compute.BootDiagnosticsArgs(
            enabled=True,
            storage_uri="aaaaaaaaaaaaa",
        ),
    ),
    hardware_profile=azure_native.compute.HardwareProfileResponseArgs(
        vm_size="Basic_A0",
        vm_size_properties=azure_native.compute.VMSizePropertiesArgs(
            v_cpus_available=9,
            v_cpus_per_core=12,
        ),
    ),
    instance_id="aaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    license_type="aaaaaaaaaa",
    location="westus",
    network_profile=azure_native.compute.NetworkProfileResponseArgs(
        network_api_version="2020-11-01",
        network_interface_configurations=[{
            "deleteOption": "Delete",
            "dnsSettings": azure_native.compute.VirtualMachineNetworkInterfaceDnsSettingsConfigurationArgs(
                dns_servers=["aaaaaa"],
            ),
            "dscpConfiguration": azure_native.compute.SubResourceArgs(
                id="/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
            ),
            "enableAcceleratedNetworking": True,
            "enableFpga": True,
            "enableIPForwarding": True,
            "ipConfigurations": [{
                "applicationGatewayBackendAddressPools": [azure_native.compute.SubResourceArgs(
                    id="/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                )],
                "applicationSecurityGroups": [azure_native.compute.SubResourceArgs(
                    id="/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                )],
                "loadBalancerBackendAddressPools": [azure_native.compute.SubResourceArgs(
                    id="/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                )],
                "name": "aa",
                "primary": True,
                "privateIPAddressVersion": "IPv4",
                "publicIPAddressConfiguration": {
                    "deleteOption": "Delete",
                    "dnsSettings": azure_native.compute.VirtualMachinePublicIPAddressDnsSettingsConfigurationArgs(
                        domain_name_label="aaaaaaaaaaaaaaaaaaaaaaaaa",
                    ),
                    "idleTimeoutInMinutes": 2,
                    "ipTags": [azure_native.compute.VirtualMachineIpTagArgs(
                        ip_tag_type="aaaaaaaaaaaaaaaaaaaaaaaaa",
                        tag="aaaaaaaaaaaaaaaaaaaa",
                    )],
                    "name": "aaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
                    "publicIPAddressVersion": "IPv4",
                    "publicIPAllocationMethod": "Dynamic",
                    "publicIPPrefix": azure_native.compute.SubResourceArgs(
                        id="/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                    ),
                    "sku": azure_native.compute.PublicIPAddressSkuArgs(
                        name="Basic",
                        tier="Regional",
                    ),
                },
                "subnet": azure_native.compute.SubResourceArgs(
                    id="/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                ),
            }],
            "name": "aaaaaaaaaaa",
            "networkSecurityGroup": azure_native.compute.SubResourceArgs(
                id="/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
            ),
            "primary": True,
        }],
        network_interfaces=[azure_native.compute.NetworkInterfaceReferenceArgs(
            delete_option="Delete",
            id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/virtualMachineScaleSets/{vmss-name}/virtualMachines/0/networkInterfaces/vmsstestnetconfig5415",
            primary=True,
        )],
    ),
    network_profile_configuration=azure_native.compute.VirtualMachineScaleSetVMNetworkProfileConfigurationResponseArgs(
        network_interface_configurations=[{
            "deleteOption": "Delete",
            "dnsSettings": azure_native.compute.VirtualMachineScaleSetNetworkConfigurationDnsSettingsArgs(
                dns_servers=[],
            ),
            "enableAcceleratedNetworking": True,
            "enableFpga": True,
            "enableIPForwarding": True,
            "ipConfigurations": [{
                "applicationGatewayBackendAddressPools": [azure_native.compute.SubResourceArgs(
                    id="/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                )],
                "applicationSecurityGroups": [azure_native.compute.SubResourceArgs(
                    id="/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                )],
                "loadBalancerBackendAddressPools": [azure_native.compute.SubResourceArgs(
                    id="/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                )],
                "loadBalancerInboundNatPools": [azure_native.compute.SubResourceArgs(
                    id="/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                )],
                "name": "vmsstestnetconfig9693",
                "primary": True,
                "privateIPAddressVersion": "IPv4",
                "publicIPAddressConfiguration": {
                    "deleteOption": "Delete",
                    "dnsSettings": azure_native.compute.VirtualMachineScaleSetPublicIPAddressConfigurationDnsSettingsArgs(
                        domain_name_label="aaaaaaaaaaaaaaaaaa",
                    ),
                    "idleTimeoutInMinutes": 18,
                    "ipTags": [azure_native.compute.VirtualMachineScaleSetIpTagArgs(
                        ip_tag_type="aaaaaaa",
                        tag="aaaaaaaaaaaaaaaaaaaaaaaaaaa",
                    )],
                    "name": "aaaaaaaaaaaaaaaaaa",
                    "publicIPAddressVersion": "IPv4",
                    "publicIPPrefix": azure_native.compute.SubResourceArgs(
                        id="/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                    ),
                    "sku": azure_native.compute.PublicIPAddressSkuArgs(
                        name="Basic",
                        tier="Regional",
                    ),
                },
                "subnet": azure_native.compute.ApiEntityReferenceArgs(
                    id="/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/vn4071/subnets/sn5503",
                ),
            }],
            "name": "vmsstestnetconfig5415",
            "networkSecurityGroup": azure_native.compute.SubResourceArgs(
                id="/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
            ),
            "primary": True,
        }],
    ),
    os_profile=azure_native.compute.OSProfileResponseArgs(
        admin_password="aaaaaaaaaaaaaaaa",
        admin_username="Foo12",
        allow_extension_operations=True,
        computer_name="test000000",
        custom_data="aaaa",
        linux_configuration={
            "disablePasswordAuthentication": True,
            "patchSettings": azure_native.compute.LinuxPatchSettingsArgs(
                assessment_mode="ImageDefault",
                patch_mode="ImageDefault",
            ),
            "provisionVMAgent": True,
            "ssh": {
                "publicKeys": [azure_native.compute.SshPublicKeyArgs(
                    key_data="aaaaaa",
                    path="aaa",
                )],
            },
        },
        require_guest_provision_signal=True,
        secrets=[],
        windows_configuration={
            "additionalUnattendContent": [azure_native.compute.AdditionalUnattendContentArgs(
                component_name=azure_native.compute.ComponentNames.MICROSOFT_WINDOWS_SHELL_SETUP,
                content="aaaaaaaaaaaaaaaaaaaa",
                pass_name=azure_native.compute.PassNames.OOBE_SYSTEM,
                setting_name=azure_native.compute.SettingNames.AUTO_LOGON,
            )],
            "enableAutomaticUpdates": True,
            "patchSettings": azure_native.compute.PatchSettingsArgs(
                assessment_mode="ImageDefault",
                enable_hotpatching=True,
                patch_mode="Manual",
            ),
            "provisionVMAgent": True,
            "timeZone": "aaaaaaaaaaaaaaaaaaaaaaaaaaa",
            "winRM": {
                "listeners": [azure_native.compute.WinRMListenerArgs(
                    certificate_url="aaaaaaaaaaaaaaaaaaaaaa",
                    protocol=azure_native.compute.ProtocolTypes.HTTP,
                )],
            },
        },
    ),
    plan=azure_native.compute.PlanArgs(
        name="aaaaaaaaaa",
        product="aaaaaaaaaaaaaaaaaaaa",
        promotion_code="aaaaaaaaaaaaaaaaaaaa",
        publisher="aaaaaaaaaaaaaaaaaaaaaa",
    ),
    protection_policy=azure_native.compute.VirtualMachineScaleSetVMProtectionPolicyArgs(
        protect_from_scale_in=True,
        protect_from_scale_set_actions=True,
    ),
    resource_group_name="rgcompute",
    security_profile=azure_native.compute.SecurityProfileResponseArgs(
        encryption_at_host=True,
        security_type="TrustedLaunch",
        uefi_settings=azure_native.compute.UefiSettingsArgs(
            secure_boot_enabled=True,
            v_tpm_enabled=True,
        ),
    ),
    storage_profile=azure_native.compute.StorageProfileResponseArgs(
        data_disks=[{
            "caching": azure_native.compute.CachingTypes.NONE,
            "createOption": "Empty",
            "deleteOption": "Delete",
            "detachOption": "ForceDetach",
            "diskSizeGB": 128,
            "image": azure_native.compute.VirtualHardDiskArgs(
                uri="https://{storageAccountName}.blob.core.windows.net/{containerName}/{vhdName}.vhd",
            ),
            "lun": 1,
            "managedDisk": {
                "diskEncryptionSet": azure_native.compute.DiskEncryptionSetParametersArgs(
                    id="aaaaaaaaaaaa",
                ),
                "id": "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/vmss3176_vmss3176_0_disk2_6c4f554bdafa49baa780eb2d128ff39d",
                "storageAccountType": "Standard_LRS",
            },
            "name": "vmss3176_vmss3176_0_disk2_6c4f554bdafa49baa780eb2d128ff39d",
            "toBeDetached": True,
            "vhd": azure_native.compute.VirtualHardDiskArgs(
                uri="https://{storageAccountName}.blob.core.windows.net/{containerName}/{vhdName}.vhd",
            ),
            "writeAcceleratorEnabled": True,
        }],
        image_reference=azure_native.compute.ImageReferenceArgs(
            id="a",
            offer="WindowsServer",
            publisher="MicrosoftWindowsServer",
            shared_gallery_image_id="aaaaaaaaaaaaaaaaaaaa",
            sku="2012-R2-Datacenter",
            version="4.127.20180315",
        ),
        os_disk={
            "caching": azure_native.compute.CachingTypes.NONE,
            "createOption": "FromImage",
            "deleteOption": "Delete",
            "diffDiskSettings": azure_native.compute.DiffDiskSettingsArgs(
                option="Local",
                placement="CacheDisk",
            ),
            "diskSizeGB": 127,
            "encryptionSettings": {
                "diskEncryptionKey": {
                    "secretUrl": "aaaaaaaa",
                    "sourceVault": azure_native.compute.SubResourceArgs(
                        id="/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                    ),
                },
                "enabled": True,
                "keyEncryptionKey": {
                    "keyUrl": "aaaaaaaaaaaaaa",
                    "sourceVault": azure_native.compute.SubResourceArgs(
                        id="/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}",
                    ),
                },
            },
            "image": azure_native.compute.VirtualHardDiskArgs(
                uri="https://{storageAccountName}.blob.core.windows.net/{containerName}/{vhdName}.vhd",
            ),
            "managedDisk": {
                "diskEncryptionSet": azure_native.compute.DiskEncryptionSetParametersArgs(
                    id="aaaaaaaaaaaa",
                ),
                "id": "/subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/vmss3176_vmss3176_0_OsDisk_1_6d72b805e50e4de6830303c5055077fc",
                "storageAccountType": "Standard_LRS",
            },
            "name": "vmss3176_vmss3176_0_OsDisk_1_6d72b805e50e4de6830303c5055077fc",
            "osType": azure_native.compute.OperatingSystemTypes.WINDOWS,
            "vhd": azure_native.compute.VirtualHardDiskArgs(
                uri="https://{storageAccountName}.blob.core.windows.net/{containerName}/{vhdName}.vhd",
            ),
            "writeAcceleratorEnabled": True,
        },
    ),
    tags={},
    user_data="RXhhbXBsZSBVc2VyRGF0YQ==",
    vm_scale_set_name="aaaaaaaaaaaaaa")

```

```yaml
resources:
  virtualMachineScaleSetVM:
    type: azure-native:compute:VirtualMachineScaleSetVM
    properties:
      additionalCapabilities:
        hibernationEnabled: true
        ultraSSDEnabled: true
      availabilitySet:
        id: /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}
      diagnosticsProfile:
        bootDiagnostics:
          enabled: true
          storageUri: aaaaaaaaaaaaa
      hardwareProfile:
        vmSize: Basic_A0
        vmSizeProperties:
          vCPUsAvailable: 9
          vCPUsPerCore: 12
      instanceId: aaaaaaaaaaaaaaaaaaaaaaaaaaaaa
      licenseType: aaaaaaaaaa
      location: westus
      networkProfile:
        networkApiVersion: 2020-11-01
        networkInterfaceConfigurations:
          - deleteOption: Delete
            dnsSettings:
              dnsServers:
                - aaaaaa
            dscpConfiguration:
              id: /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}
            enableAcceleratedNetworking: true
            enableFpga: true
            enableIPForwarding: true
            ipConfigurations:
              - applicationGatewayBackendAddressPools:
                  - id: /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}
                applicationSecurityGroups:
                  - id: /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}
                loadBalancerBackendAddressPools:
                  - id: /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}
                name: aa
                primary: true
                privateIPAddressVersion: IPv4
                publicIPAddressConfiguration:
                  deleteOption: Delete
                  dnsSettings:
                    domainNameLabel: aaaaaaaaaaaaaaaaaaaaaaaaa
                  idleTimeoutInMinutes: 2
                  ipTags:
                    - ipTagType: aaaaaaaaaaaaaaaaaaaaaaaaa
                      tag: aaaaaaaaaaaaaaaaaaaa
                  name: aaaaaaaaaaaaaaaaaaaaaaaaaaaaa
                  publicIPAddressVersion: IPv4
                  publicIPAllocationMethod: Dynamic
                  publicIPPrefix:
                    id: /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}
                  sku:
                    name: Basic
                    tier: Regional
                subnet:
                  id: /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}
            name: aaaaaaaaaaa
            networkSecurityGroup:
              id: /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}
            primary: true
        networkInterfaces:
          - deleteOption: Delete
            id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/virtualMachineScaleSets/{vmss-name}/virtualMachines/0/networkInterfaces/vmsstestnetconfig5415
            primary: true
      networkProfileConfiguration:
        networkInterfaceConfigurations:
          - deleteOption: Delete
            dnsSettings:
              dnsServers: []
            enableAcceleratedNetworking: true
            enableFpga: true
            enableIPForwarding: true
            ipConfigurations:
              - applicationGatewayBackendAddressPools:
                  - id: /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}
                applicationSecurityGroups:
                  - id: /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}
                loadBalancerBackendAddressPools:
                  - id: /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}
                loadBalancerInboundNatPools:
                  - id: /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}
                name: vmsstestnetconfig9693
                primary: true
                privateIPAddressVersion: IPv4
                publicIPAddressConfiguration:
                  deleteOption: Delete
                  dnsSettings:
                    domainNameLabel: aaaaaaaaaaaaaaaaaa
                  idleTimeoutInMinutes: 18
                  ipTags:
                    - ipTagType: aaaaaaa
                      tag: aaaaaaaaaaaaaaaaaaaaaaaaaaa
                  name: aaaaaaaaaaaaaaaaaa
                  publicIPAddressVersion: IPv4
                  publicIPPrefix:
                    id: /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}
                  sku:
                    name: Basic
                    tier: Regional
                subnet:
                  id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Network/virtualNetworks/vn4071/subnets/sn5503
            name: vmsstestnetconfig5415
            networkSecurityGroup:
              id: /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}
            primary: true
      osProfile:
        adminPassword: aaaaaaaaaaaaaaaa
        adminUsername: Foo12
        allowExtensionOperations: true
        computerName: test000000
        customData: aaaa
        linuxConfiguration:
          disablePasswordAuthentication: true
          patchSettings:
            assessmentMode: ImageDefault
            patchMode: ImageDefault
          provisionVMAgent: true
          ssh:
            publicKeys:
              - keyData: aaaaaa
                path: aaa
        requireGuestProvisionSignal: true
        secrets: []
        windowsConfiguration:
          additionalUnattendContent:
            - componentName: Microsoft-Windows-Shell-Setup
              content: aaaaaaaaaaaaaaaaaaaa
              passName: OobeSystem
              settingName: AutoLogon
          enableAutomaticUpdates: true
          patchSettings:
            assessmentMode: ImageDefault
            enableHotpatching: true
            patchMode: Manual
          provisionVMAgent: true
          timeZone: aaaaaaaaaaaaaaaaaaaaaaaaaaa
          winRM:
            listeners:
              - certificateUrl: aaaaaaaaaaaaaaaaaaaaaa
                protocol: Http
      plan:
        name: aaaaaaaaaa
        product: aaaaaaaaaaaaaaaaaaaa
        promotionCode: aaaaaaaaaaaaaaaaaaaa
        publisher: aaaaaaaaaaaaaaaaaaaaaa
      protectionPolicy:
        protectFromScaleIn: true
        protectFromScaleSetActions: true
      resourceGroupName: rgcompute
      securityProfile:
        encryptionAtHost: true
        securityType: TrustedLaunch
        uefiSettings:
          secureBootEnabled: true
          vTpmEnabled: true
      storageProfile:
        dataDisks:
          - caching: None
            createOption: Empty
            deleteOption: Delete
            detachOption: ForceDetach
            diskSizeGB: 128
            image:
              uri: https://{storageAccountName}.blob.core.windows.net/{containerName}/{vhdName}.vhd
            lun: 1
            managedDisk:
              diskEncryptionSet:
                id: aaaaaaaaaaaa
              id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/vmss3176_vmss3176_0_disk2_6c4f554bdafa49baa780eb2d128ff39d
              storageAccountType: Standard_LRS
            name: vmss3176_vmss3176_0_disk2_6c4f554bdafa49baa780eb2d128ff39d
            toBeDetached: true
            vhd:
              uri: https://{storageAccountName}.blob.core.windows.net/{containerName}/{vhdName}.vhd
            writeAcceleratorEnabled: true
        imageReference:
          id: a
          offer: WindowsServer
          publisher: MicrosoftWindowsServer
          sharedGalleryImageId: aaaaaaaaaaaaaaaaaaaa
          sku: 2012-R2-Datacenter
          version: 4.127.20180315
        osDisk:
          caching: None
          createOption: FromImage
          deleteOption: Delete
          diffDiskSettings:
            option: Local
            placement: CacheDisk
          diskSizeGB: 127
          encryptionSettings:
            diskEncryptionKey:
              secretUrl: aaaaaaaa
              sourceVault:
                id: /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}
            enabled: true
            keyEncryptionKey:
              keyUrl: aaaaaaaaaaaaaa
              sourceVault:
                id: /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/availabilitySets/{availabilitySetName}
          image:
            uri: https://{storageAccountName}.blob.core.windows.net/{containerName}/{vhdName}.vhd
          managedDisk:
            diskEncryptionSet:
              id: aaaaaaaaaaaa
            id: /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/disks/vmss3176_vmss3176_0_OsDisk_1_6d72b805e50e4de6830303c5055077fc
            storageAccountType: Standard_LRS
          name: vmss3176_vmss3176_0_OsDisk_1_6d72b805e50e4de6830303c5055077fc
          osType: Windows
          vhd:
            uri: https://{storageAccountName}.blob.core.windows.net/{containerName}/{vhdName}.vhd
          writeAcceleratorEnabled: true
      tags: {}
      userData: RXhhbXBsZSBVc2VyRGF0YQ==
      vmScaleSetName: aaaaaaaaaaaaaa

```

{{% /example %}}
{{% example %}}
### VirtualMachineScaleSetVM_Update_MinimumSet_Gen
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachineScaleSetVM = new AzureNative.Compute.VirtualMachineScaleSetVM("virtualMachineScaleSetVM", new()
    {
        InstanceId = "aaaaaaaaaaaaaaaaaaaa",
        Location = "westus",
        ResourceGroupName = "rgcompute",
        VmScaleSetName = "aaaaaaaaaaaaaaaaaa",
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
		_, err := compute.NewVirtualMachineScaleSetVM(ctx, "virtualMachineScaleSetVM", &compute.VirtualMachineScaleSetVMArgs{
			InstanceId:        pulumi.String("aaaaaaaaaaaaaaaaaaaa"),
			Location:          pulumi.String("westus"),
			ResourceGroupName: pulumi.String("rgcompute"),
			VmScaleSetName:    pulumi.String("aaaaaaaaaaaaaaaaaa"),
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
import com.pulumi.azurenative.compute.VirtualMachineScaleSetVM;
import com.pulumi.azurenative.compute.VirtualMachineScaleSetVMArgs;
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
        var virtualMachineScaleSetVM = new VirtualMachineScaleSetVM("virtualMachineScaleSetVM", VirtualMachineScaleSetVMArgs.builder()        
            .instanceId("aaaaaaaaaaaaaaaaaaaa")
            .location("westus")
            .resourceGroupName("rgcompute")
            .vmScaleSetName("aaaaaaaaaaaaaaaaaa")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachineScaleSetVM = new azure_native.compute.VirtualMachineScaleSetVM("virtualMachineScaleSetVM", {
    instanceId: "aaaaaaaaaaaaaaaaaaaa",
    location: "westus",
    resourceGroupName: "rgcompute",
    vmScaleSetName: "aaaaaaaaaaaaaaaaaa",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine_scale_set_vm = azure_native.compute.VirtualMachineScaleSetVM("virtualMachineScaleSetVM",
    instance_id="aaaaaaaaaaaaaaaaaaaa",
    location="westus",
    resource_group_name="rgcompute",
    vm_scale_set_name="aaaaaaaaaaaaaaaaaa")

```

```yaml
resources:
  virtualMachineScaleSetVM:
    type: azure-native:compute:VirtualMachineScaleSetVM
    properties:
      instanceId: aaaaaaaaaaaaaaaaaaaa
      location: westus
      resourceGroupName: rgcompute
      vmScaleSetName: aaaaaaaaaaaaaaaaaa

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:compute:VirtualMachineScaleSetVM {vmss-vm-name} /subscriptions/{subscription-id}/resourceGroups/myResourceGroup/providers/Microsoft.Compute/virtualMachineScaleSets/{vmss-name}/virtualMachines/0 
```
