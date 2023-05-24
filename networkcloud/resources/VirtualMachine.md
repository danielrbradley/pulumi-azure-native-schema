
API Version: 2022-12-12-preview.
Previous API Version: 2022-12-12-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update virtual machine
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var virtualMachine = new AzureNative.NetworkCloud.VirtualMachine("virtualMachine", new()
    {
        AdminUsername = "username",
        BootMethod = "UEFI",
        CloudServicesNetworkAttachment = new AzureNative.NetworkCloud.Inputs.NetworkAttachmentArgs
        {
            AttachedNetworkId = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/cloudServicesNetworks/cloudServicesNetworkName",
            IpAllocationMethod = "Dynamic",
        },
        CpuCores = 2,
        ExtendedLocation = new AzureNative.NetworkCloud.Inputs.ExtendedLocationArgs
        {
            Name = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName",
            Type = "CustomLocation",
        },
        Location = "location",
        MemorySizeGB = 8,
        NetworkAttachments = new[]
        {
            new AzureNative.NetworkCloud.Inputs.NetworkAttachmentArgs
            {
                AttachedNetworkId = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/l3Networks/l3NetworkName",
                DefaultGateway = "True",
                IpAllocationMethod = "Dynamic",
                Ipv4Address = "198.51.100.1",
                Ipv6Address = "2001:0db8:0000:0000:0000:0000:0000:0000",
                NetworkAttachmentName = "netAttachName01",
            },
        },
        NetworkData = "bmV0d29ya0RhdGVTYW1wbGU=",
        PlacementHints = new[]
        {
            new AzureNative.NetworkCloud.Inputs.VirtualMachinePlacementHintArgs
            {
                HintType = "Affinity",
                ResourceId = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/racks/rackName",
                SchedulingExecution = "Hard",
                Scope = "",
            },
        },
        ResourceGroupName = "resourceGroupName",
        SshPublicKeys = new[]
        {
            new AzureNative.NetworkCloud.Inputs.SshPublicKeyArgs
            {
                KeyData = "ssh-rsa AAtsE3njSONzDYRIZv/WLjVuMfrUSByHp+jfaaOLHTIIB4fJvo6dQUZxE20w2iDHV3tEkmnTo84eba97VMueQD6OzJPEyWZMRpz8UYWOd0IXeRqiFu1lawNblZhwNT/ojNZfpB3af/YDzwQCZgTcTRyNNhL4o/blKUmug0daSsSXISTRnIDpcf5qytjs1Xo+yYyJMvzLL59mhAyb3p/cD+Y3/s3WhAx+l0XOKpzXnblrv9d3q4c2tWmm/SyFqthaqd0= admin@vm",
            },
        },
        StorageProfile = new AzureNative.NetworkCloud.Inputs.StorageProfileArgs
        {
            OsDisk = new AzureNative.NetworkCloud.Inputs.OsDiskArgs
            {
                CreateOption = "Ephemeral",
                DeleteOption = "Delete",
                DiskSizeGB = 120,
            },
            VolumeAttachments = new[]
            {
                "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/volumes/volumeName",
            },
        },
        Tags = 
        {
            { "key1", "myvalue1" },
            { "key2", "myvalue2" },
        },
        UserData = "dXNlckRhdGVTYW1wbGU=",
        VirtualMachineName = "virtualMachineName",
        VmDeviceModel = "T2",
        VmImage = "myacr.azurecr.io/foobar:latest",
        VmImageRepositoryCredentials = new AzureNative.NetworkCloud.Inputs.ImageRepositoryCredentialsArgs
        {
            Password = "{password}",
            RegistryUrl = "myacr.azurecr.io",
            Username = "myuser",
        },
    });

});


```

```go
package main

import (
	networkcloud "github.com/pulumi/pulumi-azure-native-sdk/networkcloud"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := networkcloud.NewVirtualMachine(ctx, "virtualMachine", &networkcloud.VirtualMachineArgs{
			AdminUsername: pulumi.String("username"),
			BootMethod:    pulumi.String("UEFI"),
			CloudServicesNetworkAttachment: &networkcloud.NetworkAttachmentArgs{
				AttachedNetworkId:  pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/cloudServicesNetworks/cloudServicesNetworkName"),
				IpAllocationMethod: pulumi.String("Dynamic"),
			},
			CpuCores: pulumi.Float64(2),
			ExtendedLocation: &networkcloud.ExtendedLocationArgs{
				Name: pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName"),
				Type: pulumi.String("CustomLocation"),
			},
			Location:     pulumi.String("location"),
			MemorySizeGB: pulumi.Float64(8),
			NetworkAttachments: []networkcloud.NetworkAttachmentArgs{
				{
					AttachedNetworkId:     pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/l3Networks/l3NetworkName"),
					DefaultGateway:        pulumi.String("True"),
					IpAllocationMethod:    pulumi.String("Dynamic"),
					Ipv4Address:           pulumi.String("198.51.100.1"),
					Ipv6Address:           pulumi.String("2001:0db8:0000:0000:0000:0000:0000:0000"),
					NetworkAttachmentName: pulumi.String("netAttachName01"),
				},
			},
			NetworkData: pulumi.String("bmV0d29ya0RhdGVTYW1wbGU="),
			PlacementHints: []networkcloud.VirtualMachinePlacementHintArgs{
				{
					HintType:            pulumi.String("Affinity"),
					ResourceId:          pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/racks/rackName"),
					SchedulingExecution: pulumi.String("Hard"),
					Scope:               pulumi.String(""),
				},
			},
			ResourceGroupName: pulumi.String("resourceGroupName"),
			SshPublicKeys: []networkcloud.SshPublicKeyArgs{
				{
					KeyData: pulumi.String("ssh-rsa AAtsE3njSONzDYRIZv/WLjVuMfrUSByHp+jfaaOLHTIIB4fJvo6dQUZxE20w2iDHV3tEkmnTo84eba97VMueQD6OzJPEyWZMRpz8UYWOd0IXeRqiFu1lawNblZhwNT/ojNZfpB3af/YDzwQCZgTcTRyNNhL4o/blKUmug0daSsSXISTRnIDpcf5qytjs1Xo+yYyJMvzLL59mhAyb3p/cD+Y3/s3WhAx+l0XOKpzXnblrv9d3q4c2tWmm/SyFqthaqd0= admin@vm"),
				},
			},
			StorageProfile: networkcloud.StorageProfileResponse{
				OsDisk: &networkcloud.OsDiskArgs{
					CreateOption: pulumi.String("Ephemeral"),
					DeleteOption: pulumi.String("Delete"),
					DiskSizeGB:   pulumi.Float64(120),
				},
				VolumeAttachments: pulumi.StringArray{
					pulumi.String("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/volumes/volumeName"),
				},
			},
			Tags: pulumi.StringMap{
				"key1": pulumi.String("myvalue1"),
				"key2": pulumi.String("myvalue2"),
			},
			UserData:           pulumi.String("dXNlckRhdGVTYW1wbGU="),
			VirtualMachineName: pulumi.String("virtualMachineName"),
			VmDeviceModel:      pulumi.String("T2"),
			VmImage:            pulumi.String("myacr.azurecr.io/foobar:latest"),
			VmImageRepositoryCredentials: &networkcloud.ImageRepositoryCredentialsArgs{
				Password:    pulumi.String("{password}"),
				RegistryUrl: pulumi.String("myacr.azurecr.io"),
				Username:    pulumi.String("myuser"),
			},
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
import com.pulumi.azurenative.networkcloud.VirtualMachine;
import com.pulumi.azurenative.networkcloud.VirtualMachineArgs;
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
            .adminUsername("username")
            .bootMethod("UEFI")
            .cloudServicesNetworkAttachment(Map.ofEntries(
                Map.entry("attachedNetworkId", "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/cloudServicesNetworks/cloudServicesNetworkName"),
                Map.entry("ipAllocationMethod", "Dynamic")
            ))
            .cpuCores(2)
            .extendedLocation(Map.ofEntries(
                Map.entry("name", "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName"),
                Map.entry("type", "CustomLocation")
            ))
            .location("location")
            .memorySizeGB(8)
            .networkAttachments(Map.ofEntries(
                Map.entry("attachedNetworkId", "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/l3Networks/l3NetworkName"),
                Map.entry("defaultGateway", "True"),
                Map.entry("ipAllocationMethod", "Dynamic"),
                Map.entry("ipv4Address", "198.51.100.1"),
                Map.entry("ipv6Address", "2001:0db8:0000:0000:0000:0000:0000:0000"),
                Map.entry("networkAttachmentName", "netAttachName01")
            ))
            .networkData("bmV0d29ya0RhdGVTYW1wbGU=")
            .placementHints(Map.ofEntries(
                Map.entry("hintType", "Affinity"),
                Map.entry("resourceId", "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/racks/rackName"),
                Map.entry("schedulingExecution", "Hard"),
                Map.entry("scope", "")
            ))
            .resourceGroupName("resourceGroupName")
            .sshPublicKeys(Map.of("keyData", "ssh-rsa AAtsE3njSONzDYRIZv/WLjVuMfrUSByHp+jfaaOLHTIIB4fJvo6dQUZxE20w2iDHV3tEkmnTo84eba97VMueQD6OzJPEyWZMRpz8UYWOd0IXeRqiFu1lawNblZhwNT/ojNZfpB3af/YDzwQCZgTcTRyNNhL4o/blKUmug0daSsSXISTRnIDpcf5qytjs1Xo+yYyJMvzLL59mhAyb3p/cD+Y3/s3WhAx+l0XOKpzXnblrv9d3q4c2tWmm/SyFqthaqd0= admin@vm"))
            .storageProfile(Map.ofEntries(
                Map.entry("osDisk", Map.ofEntries(
                    Map.entry("createOption", "Ephemeral"),
                    Map.entry("deleteOption", "Delete"),
                    Map.entry("diskSizeGB", 120)
                )),
                Map.entry("volumeAttachments", "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/volumes/volumeName")
            ))
            .tags(Map.ofEntries(
                Map.entry("key1", "myvalue1"),
                Map.entry("key2", "myvalue2")
            ))
            .userData("dXNlckRhdGVTYW1wbGU=")
            .virtualMachineName("virtualMachineName")
            .vmDeviceModel("T2")
            .vmImage("myacr.azurecr.io/foobar:latest")
            .vmImageRepositoryCredentials(Map.ofEntries(
                Map.entry("password", "{password}"),
                Map.entry("registryUrl", "myacr.azurecr.io"),
                Map.entry("username", "myuser")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const virtualMachine = new azure_native.networkcloud.VirtualMachine("virtualMachine", {
    adminUsername: "username",
    bootMethod: "UEFI",
    cloudServicesNetworkAttachment: {
        attachedNetworkId: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/cloudServicesNetworks/cloudServicesNetworkName",
        ipAllocationMethod: "Dynamic",
    },
    cpuCores: 2,
    extendedLocation: {
        name: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName",
        type: "CustomLocation",
    },
    location: "location",
    memorySizeGB: 8,
    networkAttachments: [{
        attachedNetworkId: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/l3Networks/l3NetworkName",
        defaultGateway: "True",
        ipAllocationMethod: "Dynamic",
        ipv4Address: "198.51.100.1",
        ipv6Address: "2001:0db8:0000:0000:0000:0000:0000:0000",
        networkAttachmentName: "netAttachName01",
    }],
    networkData: "bmV0d29ya0RhdGVTYW1wbGU=",
    placementHints: [{
        hintType: "Affinity",
        resourceId: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/racks/rackName",
        schedulingExecution: "Hard",
        scope: "",
    }],
    resourceGroupName: "resourceGroupName",
    sshPublicKeys: [{
        keyData: "ssh-rsa AAtsE3njSONzDYRIZv/WLjVuMfrUSByHp+jfaaOLHTIIB4fJvo6dQUZxE20w2iDHV3tEkmnTo84eba97VMueQD6OzJPEyWZMRpz8UYWOd0IXeRqiFu1lawNblZhwNT/ojNZfpB3af/YDzwQCZgTcTRyNNhL4o/blKUmug0daSsSXISTRnIDpcf5qytjs1Xo+yYyJMvzLL59mhAyb3p/cD+Y3/s3WhAx+l0XOKpzXnblrv9d3q4c2tWmm/SyFqthaqd0= admin@vm",
    }],
    storageProfile: {
        osDisk: {
            createOption: "Ephemeral",
            deleteOption: "Delete",
            diskSizeGB: 120,
        },
        volumeAttachments: ["/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/volumes/volumeName"],
    },
    tags: {
        key1: "myvalue1",
        key2: "myvalue2",
    },
    userData: "dXNlckRhdGVTYW1wbGU=",
    virtualMachineName: "virtualMachineName",
    vmDeviceModel: "T2",
    vmImage: "myacr.azurecr.io/foobar:latest",
    vmImageRepositoryCredentials: {
        password: "{password}",
        registryUrl: "myacr.azurecr.io",
        username: "myuser",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

virtual_machine = azure_native.networkcloud.VirtualMachine("virtualMachine",
    admin_username="username",
    boot_method="UEFI",
    cloud_services_network_attachment=azure_native.networkcloud.NetworkAttachmentArgs(
        attached_network_id="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/cloudServicesNetworks/cloudServicesNetworkName",
        ip_allocation_method="Dynamic",
    ),
    cpu_cores=2,
    extended_location=azure_native.networkcloud.ExtendedLocationArgs(
        name="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName",
        type="CustomLocation",
    ),
    location="location",
    memory_size_gb=8,
    network_attachments=[azure_native.networkcloud.NetworkAttachmentArgs(
        attached_network_id="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/l3Networks/l3NetworkName",
        default_gateway="True",
        ip_allocation_method="Dynamic",
        ipv4_address="198.51.100.1",
        ipv6_address="2001:0db8:0000:0000:0000:0000:0000:0000",
        network_attachment_name="netAttachName01",
    )],
    network_data="bmV0d29ya0RhdGVTYW1wbGU=",
    placement_hints=[azure_native.networkcloud.VirtualMachinePlacementHintArgs(
        hint_type="Affinity",
        resource_id="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/racks/rackName",
        scheduling_execution="Hard",
        scope="",
    )],
    resource_group_name="resourceGroupName",
    ssh_public_keys=[azure_native.networkcloud.SshPublicKeyArgs(
        key_data="ssh-rsa AAtsE3njSONzDYRIZv/WLjVuMfrUSByHp+jfaaOLHTIIB4fJvo6dQUZxE20w2iDHV3tEkmnTo84eba97VMueQD6OzJPEyWZMRpz8UYWOd0IXeRqiFu1lawNblZhwNT/ojNZfpB3af/YDzwQCZgTcTRyNNhL4o/blKUmug0daSsSXISTRnIDpcf5qytjs1Xo+yYyJMvzLL59mhAyb3p/cD+Y3/s3WhAx+l0XOKpzXnblrv9d3q4c2tWmm/SyFqthaqd0= admin@vm",
    )],
    storage_profile=azure_native.networkcloud.StorageProfileResponseArgs(
        os_disk=azure_native.networkcloud.OsDiskArgs(
            create_option="Ephemeral",
            delete_option="Delete",
            disk_size_gb=120,
        ),
        volume_attachments=["/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/volumes/volumeName"],
    ),
    tags={
        "key1": "myvalue1",
        "key2": "myvalue2",
    },
    user_data="dXNlckRhdGVTYW1wbGU=",
    virtual_machine_name="virtualMachineName",
    vm_device_model="T2",
    vm_image="myacr.azurecr.io/foobar:latest",
    vm_image_repository_credentials=azure_native.networkcloud.ImageRepositoryCredentialsArgs(
        password="{password}",
        registry_url="myacr.azurecr.io",
        username="myuser",
    ))

```

```yaml
resources:
  virtualMachine:
    type: azure-native:networkcloud:VirtualMachine
    properties:
      adminUsername: username
      bootMethod: UEFI
      cloudServicesNetworkAttachment:
        attachedNetworkId: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/cloudServicesNetworks/cloudServicesNetworkName
        ipAllocationMethod: Dynamic
      cpuCores: 2
      extendedLocation:
        name: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterExtendedLocationName
        type: CustomLocation
      location: location
      memorySizeGB: 8
      networkAttachments:
        - attachedNetworkId: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/l3Networks/l3NetworkName
          defaultGateway: True
          ipAllocationMethod: Dynamic
          ipv4Address: 198.51.100.1
          ipv6Address: 2001:0db8:0000:0000:0000:0000:0000:0000
          networkAttachmentName: netAttachName01
      networkData: bmV0d29ya0RhdGVTYW1wbGU=
      placementHints:
        - hintType: Affinity
          resourceId: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/racks/rackName
          schedulingExecution: Hard
          scope:
      resourceGroupName: resourceGroupName
      sshPublicKeys:
        - keyData: ssh-rsa AAtsE3njSONzDYRIZv/WLjVuMfrUSByHp+jfaaOLHTIIB4fJvo6dQUZxE20w2iDHV3tEkmnTo84eba97VMueQD6OzJPEyWZMRpz8UYWOd0IXeRqiFu1lawNblZhwNT/ojNZfpB3af/YDzwQCZgTcTRyNNhL4o/blKUmug0daSsSXISTRnIDpcf5qytjs1Xo+yYyJMvzLL59mhAyb3p/cD+Y3/s3WhAx+l0XOKpzXnblrv9d3q4c2tWmm/SyFqthaqd0= admin@vm
      storageProfile:
        osDisk:
          createOption: Ephemeral
          deleteOption: Delete
          diskSizeGB: 120
        volumeAttachments:
          - /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/volumes/volumeName
      tags:
        key1: myvalue1
        key2: myvalue2
      userData: dXNlckRhdGVTYW1wbGU=
      virtualMachineName: virtualMachineName
      vmDeviceModel: T2
      vmImage: myacr.azurecr.io/foobar:latest
      vmImageRepositoryCredentials:
        password: '{password}'
        registryUrl: myacr.azurecr.io
        username: myuser

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:networkcloud:VirtualMachine virtualMachineName /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/virtualMachines/virtualMachineName 
```
