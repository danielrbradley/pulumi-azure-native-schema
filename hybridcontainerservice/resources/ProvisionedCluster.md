The provisionedClusters resource definition.
API Version: 2022-09-01-preview.
Previous API Version: 2022-05-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PutProvisionedCluster
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var provisionedCluster = new AzureNative.HybridContainerService.ProvisionedCluster("provisionedCluster", new()
    {
        ExtendedLocation = new AzureNative.HybridContainerService.Inputs.ProvisionedClustersExtendedLocationArgs
        {
            Name = "/subscriptions/a3e42606-29b1-4d7d-b1d9-9ff6b9d3c71b/resourcegroups/test-arcappliance-resgrp/providers/microsoft.extendedlocation/customlocations/testcustomlocation",
            Type = "CustomLocation",
        },
        Location = "westus",
        Properties = new AzureNative.HybridContainerService.Inputs.ProvisionedClustersAllPropertiesArgs
        {
            AgentPoolProfiles = new[]
            {
                new AzureNative.HybridContainerService.Inputs.NamedAgentPoolProfileArgs
                {
                    Count = 1,
                    Name = "default-nodepool-1",
                    OsType = "Linux",
                    VmSize = "Standard_A4_v2",
                },
            },
            CloudProviderProfile = new AzureNative.HybridContainerService.Inputs.CloudProviderProfileArgs
            {
                InfraNetworkProfile = new AzureNative.HybridContainerService.Inputs.CloudProviderProfileInfraNetworkProfileArgs
                {
                    VnetSubnetIds = new[]
                    {
                        "/subscriptions/a3e42606-29b1-4d7d-b1d9-9ff6b9d3c71b/resourceGroups/test-arcappliance-resgrp/providers/Microsoft.HybridContainerService/virtualNetworks/test-vnet-static",
                    },
                },
                InfraStorageProfile = new AzureNative.HybridContainerService.Inputs.CloudProviderProfileInfraStorageProfileArgs
                {
                    StorageSpaceIds = new[]
                    {
                        "/subscriptions/a3e42606-29b1-4d7d-b1d9-9ff6b9d3c71b/resourceGroups/test-arcappliance-resgrp/providers/Microsoft.HybridContainerService/storageSpaces/test-storage",
                    },
                },
            },
            ControlPlane = new AzureNative.HybridContainerService.Inputs.ControlPlaneProfileArgs
            {
                Count = 1,
                LinuxProfile = new AzureNative.HybridContainerService.Inputs.LinuxProfilePropertiesArgs
                {
                    Ssh = new AzureNative.HybridContainerService.Inputs.LinuxProfilePropertiesSshArgs
                    {
                        PublicKeys = new[]
                        {
                            new AzureNative.HybridContainerService.Inputs.LinuxProfilePropertiesPublicKeysArgs
                            {
                                KeyData = "ssh-rsa AAAAB1NzaC1yc2EAAAADAQABAAACAQCY......",
                            },
                        },
                    },
                },
                OsType = "Linux",
                VmSize = "Standard_A4_v2",
            },
            KubernetesVersion = "v1.20.5",
            LinuxProfile = new AzureNative.HybridContainerService.Inputs.LinuxProfilePropertiesArgs
            {
                Ssh = new AzureNative.HybridContainerService.Inputs.LinuxProfilePropertiesSshArgs
                {
                    PublicKeys = new[]
                    {
                        new AzureNative.HybridContainerService.Inputs.LinuxProfilePropertiesPublicKeysArgs
                        {
                            KeyData = "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQCY.......",
                        },
                    },
                },
            },
            NetworkProfile = new AzureNative.HybridContainerService.Inputs.NetworkProfileArgs
            {
                LoadBalancerProfile = new AzureNative.HybridContainerService.Inputs.LoadBalancerProfileArgs
                {
                    Count = 1,
                    LinuxProfile = new AzureNative.HybridContainerService.Inputs.LinuxProfilePropertiesArgs
                    {
                        Ssh = new AzureNative.HybridContainerService.Inputs.LinuxProfilePropertiesSshArgs
                        {
                            PublicKeys = new[]
                            {
                                new AzureNative.HybridContainerService.Inputs.LinuxProfilePropertiesPublicKeysArgs
                                {
                                    KeyData = "ssh-rsa AAAAB2NzaC1yc2EAAAADAQABAAACAQCY......",
                                },
                            },
                        },
                    },
                    OsType = "Linux",
                    VmSize = "Standard_K8S3_v1",
                },
                LoadBalancerSku = "unstacked-haproxy",
                NetworkPolicy = "calico",
                PodCidr = "10.244.0.0/16",
            },
        },
        ResourceGroupName = "test-arcappliance-resgrp",
        ResourceName = "test-hybridakscluster",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.hybridcontainerservice.ProvisionedCluster;
import com.pulumi.azurenative.hybridcontainerservice.ProvisionedClusterArgs;
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
        var provisionedCluster = new ProvisionedCluster("provisionedCluster", ProvisionedClusterArgs.builder()        
            .extendedLocation(Map.ofEntries(
                Map.entry("name", "/subscriptions/a3e42606-29b1-4d7d-b1d9-9ff6b9d3c71b/resourcegroups/test-arcappliance-resgrp/providers/microsoft.extendedlocation/customlocations/testcustomlocation"),
                Map.entry("type", "CustomLocation")
            ))
            .location("westus")
            .properties(Map.ofEntries(
                Map.entry("agentPoolProfiles", Map.ofEntries(
                    Map.entry("count", 1),
                    Map.entry("name", "default-nodepool-1"),
                    Map.entry("osType", "Linux"),
                    Map.entry("vmSize", "Standard_A4_v2")
                )),
                Map.entry("cloudProviderProfile", Map.ofEntries(
                    Map.entry("infraNetworkProfile", Map.of("vnetSubnetIds", "/subscriptions/a3e42606-29b1-4d7d-b1d9-9ff6b9d3c71b/resourceGroups/test-arcappliance-resgrp/providers/Microsoft.HybridContainerService/virtualNetworks/test-vnet-static")),
                    Map.entry("infraStorageProfile", Map.of("storageSpaceIds", "/subscriptions/a3e42606-29b1-4d7d-b1d9-9ff6b9d3c71b/resourceGroups/test-arcappliance-resgrp/providers/Microsoft.HybridContainerService/storageSpaces/test-storage"))
                )),
                Map.entry("controlPlane", Map.ofEntries(
                    Map.entry("count", 1),
                    Map.entry("linuxProfile", Map.of("ssh", Map.of("publicKeys", Map.of("keyData", "ssh-rsa AAAAB1NzaC1yc2EAAAADAQABAAACAQCY......")))),
                    Map.entry("osType", "Linux"),
                    Map.entry("vmSize", "Standard_A4_v2")
                )),
                Map.entry("kubernetesVersion", "v1.20.5"),
                Map.entry("linuxProfile", Map.of("ssh", Map.of("publicKeys", Map.of("keyData", "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQCY.......")))),
                Map.entry("networkProfile", Map.ofEntries(
                    Map.entry("loadBalancerProfile", Map.ofEntries(
                        Map.entry("count", 1),
                        Map.entry("linuxProfile", Map.of("ssh", Map.of("publicKeys", Map.of("keyData", "ssh-rsa AAAAB2NzaC1yc2EAAAADAQABAAACAQCY......")))),
                        Map.entry("osType", "Linux"),
                        Map.entry("vmSize", "Standard_K8S3_v1")
                    )),
                    Map.entry("loadBalancerSku", "unstacked-haproxy"),
                    Map.entry("networkPolicy", "calico"),
                    Map.entry("podCidr", "10.244.0.0/16")
                ))
            ))
            .resourceGroupName("test-arcappliance-resgrp")
            .resourceName("test-hybridakscluster")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const provisionedCluster = new azure_native.hybridcontainerservice.ProvisionedCluster("provisionedCluster", {
    extendedLocation: {
        name: "/subscriptions/a3e42606-29b1-4d7d-b1d9-9ff6b9d3c71b/resourcegroups/test-arcappliance-resgrp/providers/microsoft.extendedlocation/customlocations/testcustomlocation",
        type: "CustomLocation",
    },
    location: "westus",
    properties: {
        agentPoolProfiles: [{
            count: 1,
            name: "default-nodepool-1",
            osType: "Linux",
            vmSize: "Standard_A4_v2",
        }],
        cloudProviderProfile: {
            infraNetworkProfile: {
                vnetSubnetIds: ["/subscriptions/a3e42606-29b1-4d7d-b1d9-9ff6b9d3c71b/resourceGroups/test-arcappliance-resgrp/providers/Microsoft.HybridContainerService/virtualNetworks/test-vnet-static"],
            },
            infraStorageProfile: {
                storageSpaceIds: ["/subscriptions/a3e42606-29b1-4d7d-b1d9-9ff6b9d3c71b/resourceGroups/test-arcappliance-resgrp/providers/Microsoft.HybridContainerService/storageSpaces/test-storage"],
            },
        },
        controlPlane: {
            count: 1,
            linuxProfile: {
                ssh: {
                    publicKeys: [{
                        keyData: "ssh-rsa AAAAB1NzaC1yc2EAAAADAQABAAACAQCY......",
                    }],
                },
            },
            osType: "Linux",
            vmSize: "Standard_A4_v2",
        },
        kubernetesVersion: "v1.20.5",
        linuxProfile: {
            ssh: {
                publicKeys: [{
                    keyData: "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQCY.......",
                }],
            },
        },
        networkProfile: {
            loadBalancerProfile: {
                count: 1,
                linuxProfile: {
                    ssh: {
                        publicKeys: [{
                            keyData: "ssh-rsa AAAAB2NzaC1yc2EAAAADAQABAAACAQCY......",
                        }],
                    },
                },
                osType: "Linux",
                vmSize: "Standard_K8S3_v1",
            },
            loadBalancerSku: "unstacked-haproxy",
            networkPolicy: "calico",
            podCidr: "10.244.0.0/16",
        },
    },
    resourceGroupName: "test-arcappliance-resgrp",
    resourceName: "test-hybridakscluster",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

provisioned_cluster = azure_native.hybridcontainerservice.ProvisionedCluster("provisionedCluster",
    extended_location=azure_native.hybridcontainerservice.ProvisionedClustersExtendedLocationArgs(
        name="/subscriptions/a3e42606-29b1-4d7d-b1d9-9ff6b9d3c71b/resourcegroups/test-arcappliance-resgrp/providers/microsoft.extendedlocation/customlocations/testcustomlocation",
        type="CustomLocation",
    ),
    location="westus",
    properties=azure_native.hybridcontainerservice.ProvisionedClustersResponsePropertiesResponseArgs(
        agent_pool_profiles=[azure_native.hybridcontainerservice.NamedAgentPoolProfileArgs(
            count=1,
            name="default-nodepool-1",
            os_type="Linux",
            vm_size="Standard_A4_v2",
        )],
        cloud_provider_profile={
            "infraNetworkProfile": azure_native.hybridcontainerservice.CloudProviderProfileInfraNetworkProfileArgs(
                vnet_subnet_ids=["/subscriptions/a3e42606-29b1-4d7d-b1d9-9ff6b9d3c71b/resourceGroups/test-arcappliance-resgrp/providers/Microsoft.HybridContainerService/virtualNetworks/test-vnet-static"],
            ),
            "infraStorageProfile": azure_native.hybridcontainerservice.CloudProviderProfileInfraStorageProfileArgs(
                storage_space_ids=["/subscriptions/a3e42606-29b1-4d7d-b1d9-9ff6b9d3c71b/resourceGroups/test-arcappliance-resgrp/providers/Microsoft.HybridContainerService/storageSpaces/test-storage"],
            ),
        },
        control_plane={
            "count": 1,
            "linuxProfile": {
                "ssh": {
                    "publicKeys": [azure_native.hybridcontainerservice.LinuxProfilePropertiesPublicKeysArgs(
                        key_data="ssh-rsa AAAAB1NzaC1yc2EAAAADAQABAAACAQCY......",
                    )],
                },
            },
            "osType": "Linux",
            "vmSize": "Standard_A4_v2",
        },
        kubernetes_version="v1.20.5",
        linux_profile={
            "ssh": {
                "publicKeys": [azure_native.hybridcontainerservice.LinuxProfilePropertiesPublicKeysArgs(
                    key_data="ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQCY.......",
                )],
            },
        },
        network_profile={
            "loadBalancerProfile": {
                "count": 1,
                "linuxProfile": {
                    "ssh": {
                        "publicKeys": [azure_native.hybridcontainerservice.LinuxProfilePropertiesPublicKeysArgs(
                            key_data="ssh-rsa AAAAB2NzaC1yc2EAAAADAQABAAACAQCY......",
                        )],
                    },
                },
                "osType": "Linux",
                "vmSize": "Standard_K8S3_v1",
            },
            "loadBalancerSku": "unstacked-haproxy",
            "networkPolicy": "calico",
            "podCidr": "10.244.0.0/16",
        },
    ),
    resource_group_name="test-arcappliance-resgrp",
    resource_name_="test-hybridakscluster")

```

```yaml
resources:
  provisionedCluster:
    type: azure-native:hybridcontainerservice:ProvisionedCluster
    properties:
      extendedLocation:
        name: /subscriptions/a3e42606-29b1-4d7d-b1d9-9ff6b9d3c71b/resourcegroups/test-arcappliance-resgrp/providers/microsoft.extendedlocation/customlocations/testcustomlocation
        type: CustomLocation
      location: westus
      properties:
        agentPoolProfiles:
          - count: 1
            name: default-nodepool-1
            osType: Linux
            vmSize: Standard_A4_v2
        cloudProviderProfile:
          infraNetworkProfile:
            vnetSubnetIds:
              - /subscriptions/a3e42606-29b1-4d7d-b1d9-9ff6b9d3c71b/resourceGroups/test-arcappliance-resgrp/providers/Microsoft.HybridContainerService/virtualNetworks/test-vnet-static
          infraStorageProfile:
            storageSpaceIds:
              - /subscriptions/a3e42606-29b1-4d7d-b1d9-9ff6b9d3c71b/resourceGroups/test-arcappliance-resgrp/providers/Microsoft.HybridContainerService/storageSpaces/test-storage
        controlPlane:
          count: 1
          linuxProfile:
            ssh:
              publicKeys:
                - keyData: ssh-rsa AAAAB1NzaC1yc2EAAAADAQABAAACAQCY......
          osType: Linux
          vmSize: Standard_A4_v2
        kubernetesVersion: v1.20.5
        linuxProfile:
          ssh:
            publicKeys:
              - keyData: ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQCY.......
        networkProfile:
          loadBalancerProfile:
            count: 1
            linuxProfile:
              ssh:
                publicKeys:
                  - keyData: ssh-rsa AAAAB2NzaC1yc2EAAAADAQABAAACAQCY......
            osType: Linux
            vmSize: Standard_K8S3_v1
          loadBalancerSku: unstacked-haproxy
          networkPolicy: calico
          podCidr: 10.244.0.0/16
      resourceGroupName: test-arcappliance-resgrp
      resourceName: test-hybridakscluster

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:hybridcontainerservice:ProvisionedCluster test-hybridakscluster /subscriptions/a3e42606-29b1-4d7d-b1d9-9ff6b9d3c71b/resourceGroups/test-arcappliance-resgrp/providers/Microsoft.HybridContainerService/provisionedClusters/test-hybridakscluster 
```
