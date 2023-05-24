Sku sub resource.
API Version: 2021-05-01.
Previous API Version: 2020-01-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update the sku of vendor resource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var vendorSkus = new AzureNative.HybridNetwork.VendorSkus("vendorSkus", new()
    {
        DeploymentMode = "PrivateEdgeZone",
        ManagedApplicationTemplate = null,
        NetworkFunctionTemplate = new AzureNative.HybridNetwork.Inputs.NetworkFunctionTemplateArgs
        {
            NetworkFunctionRoleConfigurations = new[]
            {
                new AzureNative.HybridNetwork.Inputs.NetworkFunctionRoleConfigurationArgs
                {
                    CustomProfile = new AzureNative.HybridNetwork.Inputs.CustomProfileArgs
                    {
                        MetadataConfigurationPath = "/var/logs/network.cfg",
                    },
                    NetworkInterfaces = new[]
                    {
                        new AzureNative.HybridNetwork.Inputs.NetworkInterfaceArgs
                        {
                            IpConfigurations = new[]
                            {
                                new AzureNative.HybridNetwork.Inputs.NetworkInterfaceIPConfigurationArgs
                                {
                                    Gateway = "",
                                    IpAddress = "",
                                    IpAllocationMethod = "Dynamic",
                                    IpVersion = "IPv4",
                                    Subnet = "",
                                },
                            },
                            MacAddress = "",
                            NetworkInterfaceName = "nic1",
                            VmSwitchType = "Wan",
                        },
                        new AzureNative.HybridNetwork.Inputs.NetworkInterfaceArgs
                        {
                            IpConfigurations = new[]
                            {
                                new AzureNative.HybridNetwork.Inputs.NetworkInterfaceIPConfigurationArgs
                                {
                                    Gateway = "",
                                    IpAddress = "",
                                    IpAllocationMethod = "Dynamic",
                                    IpVersion = "IPv4",
                                    Subnet = "",
                                },
                            },
                            MacAddress = "",
                            NetworkInterfaceName = "nic2",
                            VmSwitchType = "Management",
                        },
                    },
                    OsProfile = new AzureNative.HybridNetwork.Inputs.OsProfileArgs
                    {
                        AdminUsername = "dummyuser",
                        CustomData = "base-64 encoded string of custom data",
                        LinuxConfiguration = new AzureNative.HybridNetwork.Inputs.LinuxConfigurationArgs
                        {
                            Ssh = new AzureNative.HybridNetwork.Inputs.SshConfigurationArgs
                            {
                                PublicKeys = new[]
                                {
                                    new AzureNative.HybridNetwork.Inputs.SshPublicKeyArgs
                                    {
                                        KeyData = "ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAgEAwrr66r8n6B8Y0zMF3dOpXEapIQD9DiYQ6D6/zwor9o39jSkHNiMMER/GETBbzP83LOcekm02aRjo55ArO7gPPVvCXbrirJu9pkm4AC4BBre5xSLS= user@constoso-DSH",
                                        Path = "home/user/.ssh/authorized_keys",
                                    },
                                },
                            },
                        },
                    },
                    RoleName = "test",
                    RoleType = "VirtualMachine",
                    StorageProfile = new AzureNative.HybridNetwork.Inputs.StorageProfileArgs
                    {
                        DataDisks = new[]
                        {
                            new AzureNative.HybridNetwork.Inputs.DataDiskArgs
                            {
                                CreateOption = "Empty",
                                DiskSizeGB = 10,
                                Name = "DataDisk1",
                            },
                        },
                        ImageReference = new AzureNative.HybridNetwork.Inputs.ImageReferenceArgs
                        {
                            Offer = "UbuntuServer",
                            Publisher = "Canonical",
                            Sku = "18.04-LTS",
                            Version = "18.04.201804262",
                        },
                        OsDisk = new AzureNative.HybridNetwork.Inputs.OsDiskArgs
                        {
                            DiskSizeGB = 30,
                            Name = "vhdName",
                            OsType = "Linux",
                            Vhd = new AzureNative.HybridNetwork.Inputs.VirtualHardDiskArgs
                            {
                                Uri = "https://contoso.net/link/vnd.vhd?sp=rl&st=2020-10-08T20:38:19Z&se=2020-12-09T19:38:00Z&sv=2019-12-12&sr=b&sig=7BM2f4yOw%3D",
                            },
                        },
                    },
                    VirtualMachineSize = "Standard_D3_v2",
                },
            },
        },
        Preview = true,
        SkuName = "TestSku",
        VendorName = "TestVendor",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.hybridnetwork.VendorSkus;
import com.pulumi.azurenative.hybridnetwork.VendorSkusArgs;
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
        var vendorSkus = new VendorSkus("vendorSkus", VendorSkusArgs.builder()        
            .deploymentMode("PrivateEdgeZone")
            .managedApplicationTemplate()
            .networkFunctionTemplate(Map.of("networkFunctionRoleConfigurations", Map.ofEntries(
                Map.entry("customProfile", Map.of("metadataConfigurationPath", "/var/logs/network.cfg")),
                Map.entry("networkInterfaces",                 
                    Map.ofEntries(
                        Map.entry("ipConfigurations", Map.ofEntries(
                            Map.entry("gateway", ""),
                            Map.entry("ipAddress", ""),
                            Map.entry("ipAllocationMethod", "Dynamic"),
                            Map.entry("ipVersion", "IPv4"),
                            Map.entry("subnet", "")
                        )),
                        Map.entry("macAddress", ""),
                        Map.entry("networkInterfaceName", "nic1"),
                        Map.entry("vmSwitchType", "Wan")
                    ),
                    Map.ofEntries(
                        Map.entry("ipConfigurations", Map.ofEntries(
                            Map.entry("gateway", ""),
                            Map.entry("ipAddress", ""),
                            Map.entry("ipAllocationMethod", "Dynamic"),
                            Map.entry("ipVersion", "IPv4"),
                            Map.entry("subnet", "")
                        )),
                        Map.entry("macAddress", ""),
                        Map.entry("networkInterfaceName", "nic2"),
                        Map.entry("vmSwitchType", "Management")
                    )),
                Map.entry("osProfile", Map.ofEntries(
                    Map.entry("adminUsername", "dummyuser"),
                    Map.entry("customData", "base-64 encoded string of custom data"),
                    Map.entry("linuxConfiguration", Map.of("ssh", Map.of("publicKeys", Map.ofEntries(
                        Map.entry("keyData", "ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAgEAwrr66r8n6B8Y0zMF3dOpXEapIQD9DiYQ6D6/zwor9o39jSkHNiMMER/GETBbzP83LOcekm02aRjo55ArO7gPPVvCXbrirJu9pkm4AC4BBre5xSLS= user@constoso-DSH"),
                        Map.entry("path", "home/user/.ssh/authorized_keys")
                    ))))
                )),
                Map.entry("roleName", "test"),
                Map.entry("roleType", "VirtualMachine"),
                Map.entry("storageProfile", Map.ofEntries(
                    Map.entry("dataDisks", Map.ofEntries(
                        Map.entry("createOption", "Empty"),
                        Map.entry("diskSizeGB", 10),
                        Map.entry("name", "DataDisk1")
                    )),
                    Map.entry("imageReference", Map.ofEntries(
                        Map.entry("offer", "UbuntuServer"),
                        Map.entry("publisher", "Canonical"),
                        Map.entry("sku", "18.04-LTS"),
                        Map.entry("version", "18.04.201804262")
                    )),
                    Map.entry("osDisk", Map.ofEntries(
                        Map.entry("diskSizeGB", 30),
                        Map.entry("name", "vhdName"),
                        Map.entry("osType", "Linux"),
                        Map.entry("vhd", Map.of("uri", "https://contoso.net/link/vnd.vhd?sp=rl&st=2020-10-08T20:38:19Z&se=2020-12-09T19:38:00Z&sv=2019-12-12&sr=b&sig=7BM2f4yOw%3D"))
                    ))
                )),
                Map.entry("virtualMachineSize", "Standard_D3_v2")
            )))
            .preview(true)
            .skuName("TestSku")
            .vendorName("TestVendor")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const vendorSkus = new azure_native.hybridnetwork.VendorSkus("vendorSkus", {
    deploymentMode: "PrivateEdgeZone",
    managedApplicationTemplate: {},
    networkFunctionTemplate: {
        networkFunctionRoleConfigurations: [{
            customProfile: {
                metadataConfigurationPath: "/var/logs/network.cfg",
            },
            networkInterfaces: [
                {
                    ipConfigurations: [{
                        gateway: "",
                        ipAddress: "",
                        ipAllocationMethod: "Dynamic",
                        ipVersion: "IPv4",
                        subnet: "",
                    }],
                    macAddress: "",
                    networkInterfaceName: "nic1",
                    vmSwitchType: "Wan",
                },
                {
                    ipConfigurations: [{
                        gateway: "",
                        ipAddress: "",
                        ipAllocationMethod: "Dynamic",
                        ipVersion: "IPv4",
                        subnet: "",
                    }],
                    macAddress: "",
                    networkInterfaceName: "nic2",
                    vmSwitchType: "Management",
                },
            ],
            osProfile: {
                adminUsername: "dummyuser",
                customData: "base-64 encoded string of custom data",
                linuxConfiguration: {
                    ssh: {
                        publicKeys: [{
                            keyData: "ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAgEAwrr66r8n6B8Y0zMF3dOpXEapIQD9DiYQ6D6/zwor9o39jSkHNiMMER/GETBbzP83LOcekm02aRjo55ArO7gPPVvCXbrirJu9pkm4AC4BBre5xSLS= user@constoso-DSH",
                            path: "home/user/.ssh/authorized_keys",
                        }],
                    },
                },
            },
            roleName: "test",
            roleType: "VirtualMachine",
            storageProfile: {
                dataDisks: [{
                    createOption: "Empty",
                    diskSizeGB: 10,
                    name: "DataDisk1",
                }],
                imageReference: {
                    offer: "UbuntuServer",
                    publisher: "Canonical",
                    sku: "18.04-LTS",
                    version: "18.04.201804262",
                },
                osDisk: {
                    diskSizeGB: 30,
                    name: "vhdName",
                    osType: "Linux",
                    vhd: {
                        uri: "https://contoso.net/link/vnd.vhd?sp=rl&st=2020-10-08T20:38:19Z&se=2020-12-09T19:38:00Z&sv=2019-12-12&sr=b&sig=7BM2f4yOw%3D",
                    },
                },
            },
            virtualMachineSize: "Standard_D3_v2",
        }],
    },
    preview: true,
    skuName: "TestSku",
    vendorName: "TestVendor",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

vendor_skus = azure_native.hybridnetwork.VendorSkus("vendorSkus",
    deployment_mode="PrivateEdgeZone",
    managed_application_template={},
    network_function_template=azure_native.hybridnetwork.NetworkFunctionTemplateResponseArgs(
        network_function_role_configurations=[{
            "customProfile": azure_native.hybridnetwork.CustomProfileArgs(
                metadata_configuration_path="/var/logs/network.cfg",
            ),
            "networkInterfaces": [
                {
                    "ipConfigurations": [azure_native.hybridnetwork.NetworkInterfaceIPConfigurationArgs(
                        gateway="",
                        ip_address="",
                        ip_allocation_method="Dynamic",
                        ip_version="IPv4",
                        subnet="",
                    )],
                    "macAddress": "",
                    "networkInterfaceName": "nic1",
                    "vmSwitchType": "Wan",
                },
                {
                    "ipConfigurations": [azure_native.hybridnetwork.NetworkInterfaceIPConfigurationArgs(
                        gateway="",
                        ip_address="",
                        ip_allocation_method="Dynamic",
                        ip_version="IPv4",
                        subnet="",
                    )],
                    "macAddress": "",
                    "networkInterfaceName": "nic2",
                    "vmSwitchType": "Management",
                },
            ],
            "osProfile": {
                "adminUsername": "dummyuser",
                "customData": "base-64 encoded string of custom data",
                "linuxConfiguration": {
                    "ssh": {
                        "publicKeys": [azure_native.hybridnetwork.SshPublicKeyArgs(
                            key_data="ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAgEAwrr66r8n6B8Y0zMF3dOpXEapIQD9DiYQ6D6/zwor9o39jSkHNiMMER/GETBbzP83LOcekm02aRjo55ArO7gPPVvCXbrirJu9pkm4AC4BBre5xSLS= user@constoso-DSH",
                            path="home/user/.ssh/authorized_keys",
                        )],
                    },
                },
            },
            "roleName": "test",
            "roleType": "VirtualMachine",
            "storageProfile": {
                "dataDisks": [azure_native.hybridnetwork.DataDiskArgs(
                    create_option="Empty",
                    disk_size_gb=10,
                    name="DataDisk1",
                )],
                "imageReference": azure_native.hybridnetwork.ImageReferenceArgs(
                    offer="UbuntuServer",
                    publisher="Canonical",
                    sku="18.04-LTS",
                    version="18.04.201804262",
                ),
                "osDisk": {
                    "diskSizeGB": 30,
                    "name": "vhdName",
                    "osType": "Linux",
                    "vhd": azure_native.hybridnetwork.VirtualHardDiskArgs(
                        uri="https://contoso.net/link/vnd.vhd?sp=rl&st=2020-10-08T20:38:19Z&se=2020-12-09T19:38:00Z&sv=2019-12-12&sr=b&sig=7BM2f4yOw%3D",
                    ),
                },
            },
            "virtualMachineSize": "Standard_D3_v2",
        }],
    ),
    preview=True,
    sku_name="TestSku",
    vendor_name="TestVendor")

```

```yaml
resources:
  vendorSkus:
    type: azure-native:hybridnetwork:VendorSkus
    properties:
      deploymentMode: PrivateEdgeZone
      managedApplicationTemplate: {}
      networkFunctionTemplate:
        networkFunctionRoleConfigurations:
          - customProfile:
              metadataConfigurationPath: /var/logs/network.cfg
            networkInterfaces:
              - ipConfigurations:
                  - gateway:
                    ipAddress:
                    ipAllocationMethod: Dynamic
                    ipVersion: IPv4
                    subnet:
                macAddress:
                networkInterfaceName: nic1
                vmSwitchType: Wan
              - ipConfigurations:
                  - gateway:
                    ipAddress:
                    ipAllocationMethod: Dynamic
                    ipVersion: IPv4
                    subnet:
                macAddress:
                networkInterfaceName: nic2
                vmSwitchType: Management
            osProfile:
              adminUsername: dummyuser
              customData: base-64 encoded string of custom data
              linuxConfiguration:
                ssh:
                  publicKeys:
                    - keyData: ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAgEAwrr66r8n6B8Y0zMF3dOpXEapIQD9DiYQ6D6/zwor9o39jSkHNiMMER/GETBbzP83LOcekm02aRjo55ArO7gPPVvCXbrirJu9pkm4AC4BBre5xSLS= user@constoso-DSH
                      path: home/user/.ssh/authorized_keys
            roleName: test
            roleType: VirtualMachine
            storageProfile:
              dataDisks:
                - createOption: Empty
                  diskSizeGB: 10
                  name: DataDisk1
              imageReference:
                offer: UbuntuServer
                publisher: Canonical
                sku: 18.04-LTS
                version: 18.04.201804262
              osDisk:
                diskSizeGB: 30
                name: vhdName
                osType: Linux
                vhd:
                  uri: https://contoso.net/link/vnd.vhd?sp=rl&st=2020-10-08T20:38:19Z&se=2020-12-09T19:38:00Z&sv=2019-12-12&sr=b&sig=7BM2f4yOw%3D
            virtualMachineSize: Standard_D3_v2
      preview: true
      skuName: TestSku
      vendorName: TestVendor

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:hybridnetwork:VendorSkus TestSku /subscriptions/subid/providers/Microsoft.HybridNetwork/vendors/TestVendor/vendorskus/TestSku 
```
