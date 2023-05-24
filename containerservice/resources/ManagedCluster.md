Managed cluster.
API Version: 2023-01-01.
Previous API Version: 2021-03-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Managed Cluster using an agent pool snapshot
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedCluster = new AzureNative.ContainerService.ManagedCluster("managedCluster", new()
    {
        AddonProfiles = null,
        AgentPoolProfiles = new[]
        {
            new AzureNative.ContainerService.Inputs.ManagedClusterAgentPoolProfileArgs
            {
                Count = 3,
                CreationData = new AzureNative.ContainerService.Inputs.CreationDataArgs
                {
                    SourceResourceId = "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.ContainerService/snapshots/snapshot1",
                },
                EnableFIPS = true,
                EnableNodePublicIP = true,
                Mode = "System",
                Name = "nodepool1",
                OsType = "Linux",
                Type = "VirtualMachineScaleSets",
                VmSize = "Standard_DS2_v2",
            },
        },
        AutoScalerProfile = new AzureNative.ContainerService.Inputs.ManagedClusterPropertiesAutoScalerProfileArgs
        {
            ScaleDownDelayAfterAdd = "15m",
            ScanInterval = "20s",
        },
        DiskEncryptionSetID = "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
        DnsPrefix = "dnsprefix1",
        EnablePodSecurityPolicy = false,
        EnableRBAC = true,
        KubernetesVersion = "",
        LinuxProfile = new AzureNative.ContainerService.Inputs.ContainerServiceLinuxProfileArgs
        {
            AdminUsername = "azureuser",
            Ssh = new AzureNative.ContainerService.Inputs.ContainerServiceSshConfigurationArgs
            {
                PublicKeys = new[]
                {
                    new AzureNative.ContainerService.Inputs.ContainerServiceSshPublicKeyArgs
                    {
                        KeyData = "keydata",
                    },
                },
            },
        },
        Location = "location1",
        NetworkProfile = new AzureNative.ContainerService.Inputs.ContainerServiceNetworkProfileArgs
        {
            LoadBalancerProfile = new AzureNative.ContainerService.Inputs.ManagedClusterLoadBalancerProfileArgs
            {
                ManagedOutboundIPs = new AzureNative.ContainerService.Inputs.ManagedClusterLoadBalancerProfileManagedOutboundIPsArgs
                {
                    Count = 2,
                },
            },
            LoadBalancerSku = "standard",
            OutboundType = "loadBalancer",
        },
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        ServicePrincipalProfile = new AzureNative.ContainerService.Inputs.ManagedClusterServicePrincipalProfileArgs
        {
            ClientId = "clientid",
            Secret = "secret",
        },
        Sku = new AzureNative.ContainerService.Inputs.ManagedClusterSKUArgs
        {
            Name = "Basic",
            Tier = "Free",
        },
        Tags = 
        {
            { "archv2", "" },
            { "tier", "production" },
        },
        WindowsProfile = new AzureNative.ContainerService.Inputs.ManagedClusterWindowsProfileArgs
        {
            AdminPassword = "replacePassword1234$",
            AdminUsername = "azureuser",
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.containerservice.ManagedCluster;
import com.pulumi.azurenative.containerservice.ManagedClusterArgs;
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
        var managedCluster = new ManagedCluster("managedCluster", ManagedClusterArgs.builder()        
            .addonProfiles()
            .agentPoolProfiles(Map.ofEntries(
                Map.entry("count", 3),
                Map.entry("creationData", Map.of("sourceResourceId", "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.ContainerService/snapshots/snapshot1")),
                Map.entry("enableFIPS", true),
                Map.entry("enableNodePublicIP", true),
                Map.entry("mode", "System"),
                Map.entry("name", "nodepool1"),
                Map.entry("osType", "Linux"),
                Map.entry("type", "VirtualMachineScaleSets"),
                Map.entry("vmSize", "Standard_DS2_v2")
            ))
            .autoScalerProfile(Map.ofEntries(
                Map.entry("scaleDownDelayAfterAdd", "15m"),
                Map.entry("scanInterval", "20s")
            ))
            .diskEncryptionSetID("/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des")
            .dnsPrefix("dnsprefix1")
            .enablePodSecurityPolicy(false)
            .enableRBAC(true)
            .kubernetesVersion("")
            .linuxProfile(Map.ofEntries(
                Map.entry("adminUsername", "azureuser"),
                Map.entry("ssh", Map.of("publicKeys", Map.of("keyData", "keydata")))
            ))
            .location("location1")
            .networkProfile(Map.ofEntries(
                Map.entry("loadBalancerProfile", Map.of("managedOutboundIPs", Map.of("count", 2))),
                Map.entry("loadBalancerSku", "standard"),
                Map.entry("outboundType", "loadBalancer")
            ))
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .servicePrincipalProfile(Map.ofEntries(
                Map.entry("clientId", "clientid"),
                Map.entry("secret", "secret")
            ))
            .sku(Map.ofEntries(
                Map.entry("name", "Basic"),
                Map.entry("tier", "Free")
            ))
            .tags(Map.ofEntries(
                Map.entry("archv2", ""),
                Map.entry("tier", "production")
            ))
            .windowsProfile(Map.ofEntries(
                Map.entry("adminPassword", "replacePassword1234$"),
                Map.entry("adminUsername", "azureuser")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedCluster = new azure_native.containerservice.ManagedCluster("managedCluster", {
    addonProfiles: {},
    agentPoolProfiles: [{
        count: 3,
        creationData: {
            sourceResourceId: "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.ContainerService/snapshots/snapshot1",
        },
        enableFIPS: true,
        enableNodePublicIP: true,
        mode: "System",
        name: "nodepool1",
        osType: "Linux",
        type: "VirtualMachineScaleSets",
        vmSize: "Standard_DS2_v2",
    }],
    autoScalerProfile: {
        scaleDownDelayAfterAdd: "15m",
        scanInterval: "20s",
    },
    diskEncryptionSetID: "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
    dnsPrefix: "dnsprefix1",
    enablePodSecurityPolicy: false,
    enableRBAC: true,
    kubernetesVersion: "",
    linuxProfile: {
        adminUsername: "azureuser",
        ssh: {
            publicKeys: [{
                keyData: "keydata",
            }],
        },
    },
    location: "location1",
    networkProfile: {
        loadBalancerProfile: {
            managedOutboundIPs: {
                count: 2,
            },
        },
        loadBalancerSku: "standard",
        outboundType: "loadBalancer",
    },
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    servicePrincipalProfile: {
        clientId: "clientid",
        secret: "secret",
    },
    sku: {
        name: "Basic",
        tier: "Free",
    },
    tags: {
        archv2: "",
        tier: "production",
    },
    windowsProfile: {
        adminPassword: "replacePassword1234$",
        adminUsername: "azureuser",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_cluster = azure_native.containerservice.ManagedCluster("managedCluster",
    addon_profiles={},
    agent_pool_profiles=[{
        "count": 3,
        "creationData": azure_native.containerservice.CreationDataArgs(
            source_resource_id="/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.ContainerService/snapshots/snapshot1",
        ),
        "enableFIPS": True,
        "enableNodePublicIP": True,
        "mode": "System",
        "name": "nodepool1",
        "osType": "Linux",
        "type": "VirtualMachineScaleSets",
        "vmSize": "Standard_DS2_v2",
    }],
    auto_scaler_profile=azure_native.containerservice.ManagedClusterPropertiesAutoScalerProfileArgs(
        scale_down_delay_after_add="15m",
        scan_interval="20s",
    ),
    disk_encryption_set_id="/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
    dns_prefix="dnsprefix1",
    enable_pod_security_policy=False,
    enable_rbac=True,
    kubernetes_version="",
    linux_profile=azure_native.containerservice.ContainerServiceLinuxProfileResponseArgs(
        admin_username="azureuser",
        ssh={
            "publicKeys": [azure_native.containerservice.ContainerServiceSshPublicKeyArgs(
                key_data="keydata",
            )],
        },
    ),
    location="location1",
    network_profile=azure_native.containerservice.ContainerServiceNetworkProfileResponseArgs(
        load_balancer_profile={
            "managedOutboundIPs": azure_native.containerservice.ManagedClusterLoadBalancerProfileManagedOutboundIPsArgs(
                count=2,
            ),
        },
        load_balancer_sku="standard",
        outbound_type="loadBalancer",
    ),
    resource_group_name="rg1",
    resource_name_="clustername1",
    service_principal_profile=azure_native.containerservice.ManagedClusterServicePrincipalProfileArgs(
        client_id="clientid",
        secret="secret",
    ),
    sku=azure_native.containerservice.ManagedClusterSKUArgs(
        name="Basic",
        tier="Free",
    ),
    tags={
        "archv2": "",
        "tier": "production",
    },
    windows_profile=azure_native.containerservice.ManagedClusterWindowsProfileArgs(
        admin_password="replacePassword1234$",
        admin_username="azureuser",
    ))

```

```yaml
resources:
  managedCluster:
    type: azure-native:containerservice:ManagedCluster
    properties:
      addonProfiles: {}
      agentPoolProfiles:
        - count: 3
          creationData:
            sourceResourceId: /subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.ContainerService/snapshots/snapshot1
          enableFIPS: true
          enableNodePublicIP: true
          mode: System
          name: nodepool1
          osType: Linux
          type: VirtualMachineScaleSets
          vmSize: Standard_DS2_v2
      autoScalerProfile:
        scaleDownDelayAfterAdd: 15m
        scanInterval: 20s
      diskEncryptionSetID: /subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des
      dnsPrefix: dnsprefix1
      enablePodSecurityPolicy: false
      enableRBAC: true
      kubernetesVersion:
      linuxProfile:
        adminUsername: azureuser
        ssh:
          publicKeys:
            - keyData: keydata
      location: location1
      networkProfile:
        loadBalancerProfile:
          managedOutboundIPs:
            count: 2
        loadBalancerSku: standard
        outboundType: loadBalancer
      resourceGroupName: rg1
      resourceName: clustername1
      servicePrincipalProfile:
        clientId: clientid
        secret: secret
      sku:
        name: Basic
        tier: Free
      tags:
        archv2:
        tier: production
      windowsProfile:
        adminPassword: replacePassword1234$
        adminUsername: azureuser

```

{{% /example %}}
{{% example %}}
### Create Managed Cluster with AKS-managed NAT gateway as outbound type
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedCluster = new AzureNative.ContainerService.ManagedCluster("managedCluster", new()
    {
        AddonProfiles = null,
        AgentPoolProfiles = new[]
        {
            new AzureNative.ContainerService.Inputs.ManagedClusterAgentPoolProfileArgs
            {
                Count = 3,
                EnableNodePublicIP = false,
                Mode = "System",
                Name = "nodepool1",
                OsType = "Linux",
                Type = "VirtualMachineScaleSets",
                VmSize = "Standard_DS2_v2",
            },
        },
        AutoScalerProfile = new AzureNative.ContainerService.Inputs.ManagedClusterPropertiesAutoScalerProfileArgs
        {
            ScaleDownDelayAfterAdd = "15m",
            ScanInterval = "20s",
        },
        DiskEncryptionSetID = "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
        DnsPrefix = "dnsprefix1",
        EnablePodSecurityPolicy = true,
        EnableRBAC = true,
        KubernetesVersion = "",
        LinuxProfile = new AzureNative.ContainerService.Inputs.ContainerServiceLinuxProfileArgs
        {
            AdminUsername = "azureuser",
            Ssh = new AzureNative.ContainerService.Inputs.ContainerServiceSshConfigurationArgs
            {
                PublicKeys = new[]
                {
                    new AzureNative.ContainerService.Inputs.ContainerServiceSshPublicKeyArgs
                    {
                        KeyData = "keydata",
                    },
                },
            },
        },
        Location = "location1",
        NetworkProfile = new AzureNative.ContainerService.Inputs.ContainerServiceNetworkProfileArgs
        {
            LoadBalancerSku = "standard",
            NatGatewayProfile = new AzureNative.ContainerService.Inputs.ManagedClusterNATGatewayProfileArgs
            {
                ManagedOutboundIPProfile = new AzureNative.ContainerService.Inputs.ManagedClusterManagedOutboundIPProfileArgs
                {
                    Count = 2,
                },
            },
            OutboundType = "managedNATGateway",
        },
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        ServicePrincipalProfile = new AzureNative.ContainerService.Inputs.ManagedClusterServicePrincipalProfileArgs
        {
            ClientId = "clientid",
            Secret = "secret",
        },
        Sku = new AzureNative.ContainerService.Inputs.ManagedClusterSKUArgs
        {
            Name = "Basic",
            Tier = "Free",
        },
        Tags = 
        {
            { "archv2", "" },
            { "tier", "production" },
        },
        WindowsProfile = new AzureNative.ContainerService.Inputs.ManagedClusterWindowsProfileArgs
        {
            AdminPassword = "replacePassword1234$",
            AdminUsername = "azureuser",
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.containerservice.ManagedCluster;
import com.pulumi.azurenative.containerservice.ManagedClusterArgs;
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
        var managedCluster = new ManagedCluster("managedCluster", ManagedClusterArgs.builder()        
            .addonProfiles()
            .agentPoolProfiles(Map.ofEntries(
                Map.entry("count", 3),
                Map.entry("enableNodePublicIP", false),
                Map.entry("mode", "System"),
                Map.entry("name", "nodepool1"),
                Map.entry("osType", "Linux"),
                Map.entry("type", "VirtualMachineScaleSets"),
                Map.entry("vmSize", "Standard_DS2_v2")
            ))
            .autoScalerProfile(Map.ofEntries(
                Map.entry("scaleDownDelayAfterAdd", "15m"),
                Map.entry("scanInterval", "20s")
            ))
            .diskEncryptionSetID("/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des")
            .dnsPrefix("dnsprefix1")
            .enablePodSecurityPolicy(true)
            .enableRBAC(true)
            .kubernetesVersion("")
            .linuxProfile(Map.ofEntries(
                Map.entry("adminUsername", "azureuser"),
                Map.entry("ssh", Map.of("publicKeys", Map.of("keyData", "keydata")))
            ))
            .location("location1")
            .networkProfile(Map.ofEntries(
                Map.entry("loadBalancerSku", "standard"),
                Map.entry("natGatewayProfile", Map.of("managedOutboundIPProfile", Map.of("count", 2))),
                Map.entry("outboundType", "managedNATGateway")
            ))
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .servicePrincipalProfile(Map.ofEntries(
                Map.entry("clientId", "clientid"),
                Map.entry("secret", "secret")
            ))
            .sku(Map.ofEntries(
                Map.entry("name", "Basic"),
                Map.entry("tier", "Free")
            ))
            .tags(Map.ofEntries(
                Map.entry("archv2", ""),
                Map.entry("tier", "production")
            ))
            .windowsProfile(Map.ofEntries(
                Map.entry("adminPassword", "replacePassword1234$"),
                Map.entry("adminUsername", "azureuser")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedCluster = new azure_native.containerservice.ManagedCluster("managedCluster", {
    addonProfiles: {},
    agentPoolProfiles: [{
        count: 3,
        enableNodePublicIP: false,
        mode: "System",
        name: "nodepool1",
        osType: "Linux",
        type: "VirtualMachineScaleSets",
        vmSize: "Standard_DS2_v2",
    }],
    autoScalerProfile: {
        scaleDownDelayAfterAdd: "15m",
        scanInterval: "20s",
    },
    diskEncryptionSetID: "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
    dnsPrefix: "dnsprefix1",
    enablePodSecurityPolicy: true,
    enableRBAC: true,
    kubernetesVersion: "",
    linuxProfile: {
        adminUsername: "azureuser",
        ssh: {
            publicKeys: [{
                keyData: "keydata",
            }],
        },
    },
    location: "location1",
    networkProfile: {
        loadBalancerSku: "standard",
        natGatewayProfile: {
            managedOutboundIPProfile: {
                count: 2,
            },
        },
        outboundType: "managedNATGateway",
    },
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    servicePrincipalProfile: {
        clientId: "clientid",
        secret: "secret",
    },
    sku: {
        name: "Basic",
        tier: "Free",
    },
    tags: {
        archv2: "",
        tier: "production",
    },
    windowsProfile: {
        adminPassword: "replacePassword1234$",
        adminUsername: "azureuser",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_cluster = azure_native.containerservice.ManagedCluster("managedCluster",
    addon_profiles={},
    agent_pool_profiles=[azure_native.containerservice.ManagedClusterAgentPoolProfileArgs(
        count=3,
        enable_node_public_ip=False,
        mode="System",
        name="nodepool1",
        os_type="Linux",
        type="VirtualMachineScaleSets",
        vm_size="Standard_DS2_v2",
    )],
    auto_scaler_profile=azure_native.containerservice.ManagedClusterPropertiesAutoScalerProfileArgs(
        scale_down_delay_after_add="15m",
        scan_interval="20s",
    ),
    disk_encryption_set_id="/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
    dns_prefix="dnsprefix1",
    enable_pod_security_policy=True,
    enable_rbac=True,
    kubernetes_version="",
    linux_profile=azure_native.containerservice.ContainerServiceLinuxProfileResponseArgs(
        admin_username="azureuser",
        ssh={
            "publicKeys": [azure_native.containerservice.ContainerServiceSshPublicKeyArgs(
                key_data="keydata",
            )],
        },
    ),
    location="location1",
    network_profile=azure_native.containerservice.ContainerServiceNetworkProfileResponseArgs(
        load_balancer_sku="standard",
        nat_gateway_profile={
            "managedOutboundIPProfile": azure_native.containerservice.ManagedClusterManagedOutboundIPProfileArgs(
                count=2,
            ),
        },
        outbound_type="managedNATGateway",
    ),
    resource_group_name="rg1",
    resource_name_="clustername1",
    service_principal_profile=azure_native.containerservice.ManagedClusterServicePrincipalProfileArgs(
        client_id="clientid",
        secret="secret",
    ),
    sku=azure_native.containerservice.ManagedClusterSKUArgs(
        name="Basic",
        tier="Free",
    ),
    tags={
        "archv2": "",
        "tier": "production",
    },
    windows_profile=azure_native.containerservice.ManagedClusterWindowsProfileArgs(
        admin_password="replacePassword1234$",
        admin_username="azureuser",
    ))

```

```yaml
resources:
  managedCluster:
    type: azure-native:containerservice:ManagedCluster
    properties:
      addonProfiles: {}
      agentPoolProfiles:
        - count: 3
          enableNodePublicIP: false
          mode: System
          name: nodepool1
          osType: Linux
          type: VirtualMachineScaleSets
          vmSize: Standard_DS2_v2
      autoScalerProfile:
        scaleDownDelayAfterAdd: 15m
        scanInterval: 20s
      diskEncryptionSetID: /subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des
      dnsPrefix: dnsprefix1
      enablePodSecurityPolicy: true
      enableRBAC: true
      kubernetesVersion:
      linuxProfile:
        adminUsername: azureuser
        ssh:
          publicKeys:
            - keyData: keydata
      location: location1
      networkProfile:
        loadBalancerSku: standard
        natGatewayProfile:
          managedOutboundIPProfile:
            count: 2
        outboundType: managedNATGateway
      resourceGroupName: rg1
      resourceName: clustername1
      servicePrincipalProfile:
        clientId: clientid
        secret: secret
      sku:
        name: Basic
        tier: Free
      tags:
        archv2:
        tier: production
      windowsProfile:
        adminPassword: replacePassword1234$
        adminUsername: azureuser

```

{{% /example %}}
{{% example %}}
### Create Managed Cluster with Azure KeyVault Secrets Provider Addon
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedCluster = new AzureNative.ContainerService.ManagedCluster("managedCluster", new()
    {
        AddonProfiles = 
        {
            { "azureKeyvaultSecretsProvider", new AzureNative.ContainerService.Inputs.ManagedClusterAddonProfileArgs
            {
                Config = 
                {
                    { "enableSecretRotation", "true" },
                    { "rotationPollInterval", "2m" },
                },
                Enabled = true,
            } },
        },
        AgentPoolProfiles = new[]
        {
            new AzureNative.ContainerService.Inputs.ManagedClusterAgentPoolProfileArgs
            {
                Count = 3,
                EnableNodePublicIP = true,
                Mode = "System",
                Name = "nodepool1",
                OsType = "Linux",
                Type = "VirtualMachineScaleSets",
                VmSize = "Standard_DS2_v2",
            },
        },
        AutoScalerProfile = new AzureNative.ContainerService.Inputs.ManagedClusterPropertiesAutoScalerProfileArgs
        {
            ScaleDownDelayAfterAdd = "15m",
            ScanInterval = "20s",
        },
        DiskEncryptionSetID = "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
        DnsPrefix = "dnsprefix1",
        EnablePodSecurityPolicy = true,
        EnableRBAC = true,
        KubernetesVersion = "",
        LinuxProfile = new AzureNative.ContainerService.Inputs.ContainerServiceLinuxProfileArgs
        {
            AdminUsername = "azureuser",
            Ssh = new AzureNative.ContainerService.Inputs.ContainerServiceSshConfigurationArgs
            {
                PublicKeys = new[]
                {
                    new AzureNative.ContainerService.Inputs.ContainerServiceSshPublicKeyArgs
                    {
                        KeyData = "keydata",
                    },
                },
            },
        },
        Location = "location1",
        NetworkProfile = new AzureNative.ContainerService.Inputs.ContainerServiceNetworkProfileArgs
        {
            LoadBalancerProfile = new AzureNative.ContainerService.Inputs.ManagedClusterLoadBalancerProfileArgs
            {
                ManagedOutboundIPs = new AzureNative.ContainerService.Inputs.ManagedClusterLoadBalancerProfileManagedOutboundIPsArgs
                {
                    Count = 2,
                },
            },
            LoadBalancerSku = "standard",
            OutboundType = "loadBalancer",
        },
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        ServicePrincipalProfile = new AzureNative.ContainerService.Inputs.ManagedClusterServicePrincipalProfileArgs
        {
            ClientId = "clientid",
            Secret = "secret",
        },
        Sku = new AzureNative.ContainerService.Inputs.ManagedClusterSKUArgs
        {
            Name = "Basic",
            Tier = "Free",
        },
        Tags = 
        {
            { "archv2", "" },
            { "tier", "production" },
        },
        WindowsProfile = new AzureNative.ContainerService.Inputs.ManagedClusterWindowsProfileArgs
        {
            AdminPassword = "replacePassword1234$",
            AdminUsername = "azureuser",
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.containerservice.ManagedCluster;
import com.pulumi.azurenative.containerservice.ManagedClusterArgs;
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
        var managedCluster = new ManagedCluster("managedCluster", ManagedClusterArgs.builder()        
            .addonProfiles(Map.of("azureKeyvaultSecretsProvider", Map.ofEntries(
                Map.entry("config", Map.ofEntries(
                    Map.entry("enableSecretRotation", "true"),
                    Map.entry("rotationPollInterval", "2m")
                )),
                Map.entry("enabled", true)
            )))
            .agentPoolProfiles(Map.ofEntries(
                Map.entry("count", 3),
                Map.entry("enableNodePublicIP", true),
                Map.entry("mode", "System"),
                Map.entry("name", "nodepool1"),
                Map.entry("osType", "Linux"),
                Map.entry("type", "VirtualMachineScaleSets"),
                Map.entry("vmSize", "Standard_DS2_v2")
            ))
            .autoScalerProfile(Map.ofEntries(
                Map.entry("scaleDownDelayAfterAdd", "15m"),
                Map.entry("scanInterval", "20s")
            ))
            .diskEncryptionSetID("/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des")
            .dnsPrefix("dnsprefix1")
            .enablePodSecurityPolicy(true)
            .enableRBAC(true)
            .kubernetesVersion("")
            .linuxProfile(Map.ofEntries(
                Map.entry("adminUsername", "azureuser"),
                Map.entry("ssh", Map.of("publicKeys", Map.of("keyData", "keydata")))
            ))
            .location("location1")
            .networkProfile(Map.ofEntries(
                Map.entry("loadBalancerProfile", Map.of("managedOutboundIPs", Map.of("count", 2))),
                Map.entry("loadBalancerSku", "standard"),
                Map.entry("outboundType", "loadBalancer")
            ))
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .servicePrincipalProfile(Map.ofEntries(
                Map.entry("clientId", "clientid"),
                Map.entry("secret", "secret")
            ))
            .sku(Map.ofEntries(
                Map.entry("name", "Basic"),
                Map.entry("tier", "Free")
            ))
            .tags(Map.ofEntries(
                Map.entry("archv2", ""),
                Map.entry("tier", "production")
            ))
            .windowsProfile(Map.ofEntries(
                Map.entry("adminPassword", "replacePassword1234$"),
                Map.entry("adminUsername", "azureuser")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedCluster = new azure_native.containerservice.ManagedCluster("managedCluster", {
    addonProfiles: {
        azureKeyvaultSecretsProvider: {
            config: {
                enableSecretRotation: "true",
                rotationPollInterval: "2m",
            },
            enabled: true,
        },
    },
    agentPoolProfiles: [{
        count: 3,
        enableNodePublicIP: true,
        mode: "System",
        name: "nodepool1",
        osType: "Linux",
        type: "VirtualMachineScaleSets",
        vmSize: "Standard_DS2_v2",
    }],
    autoScalerProfile: {
        scaleDownDelayAfterAdd: "15m",
        scanInterval: "20s",
    },
    diskEncryptionSetID: "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
    dnsPrefix: "dnsprefix1",
    enablePodSecurityPolicy: true,
    enableRBAC: true,
    kubernetesVersion: "",
    linuxProfile: {
        adminUsername: "azureuser",
        ssh: {
            publicKeys: [{
                keyData: "keydata",
            }],
        },
    },
    location: "location1",
    networkProfile: {
        loadBalancerProfile: {
            managedOutboundIPs: {
                count: 2,
            },
        },
        loadBalancerSku: "standard",
        outboundType: "loadBalancer",
    },
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    servicePrincipalProfile: {
        clientId: "clientid",
        secret: "secret",
    },
    sku: {
        name: "Basic",
        tier: "Free",
    },
    tags: {
        archv2: "",
        tier: "production",
    },
    windowsProfile: {
        adminPassword: "replacePassword1234$",
        adminUsername: "azureuser",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_cluster = azure_native.containerservice.ManagedCluster("managedCluster",
    addon_profiles={
        "azureKeyvaultSecretsProvider": azure_native.containerservice.ManagedClusterAddonProfileArgs(
            config={
                "enableSecretRotation": "true",
                "rotationPollInterval": "2m",
            },
            enabled=True,
        ),
    },
    agent_pool_profiles=[azure_native.containerservice.ManagedClusterAgentPoolProfileArgs(
        count=3,
        enable_node_public_ip=True,
        mode="System",
        name="nodepool1",
        os_type="Linux",
        type="VirtualMachineScaleSets",
        vm_size="Standard_DS2_v2",
    )],
    auto_scaler_profile=azure_native.containerservice.ManagedClusterPropertiesAutoScalerProfileArgs(
        scale_down_delay_after_add="15m",
        scan_interval="20s",
    ),
    disk_encryption_set_id="/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
    dns_prefix="dnsprefix1",
    enable_pod_security_policy=True,
    enable_rbac=True,
    kubernetes_version="",
    linux_profile=azure_native.containerservice.ContainerServiceLinuxProfileResponseArgs(
        admin_username="azureuser",
        ssh={
            "publicKeys": [azure_native.containerservice.ContainerServiceSshPublicKeyArgs(
                key_data="keydata",
            )],
        },
    ),
    location="location1",
    network_profile=azure_native.containerservice.ContainerServiceNetworkProfileResponseArgs(
        load_balancer_profile={
            "managedOutboundIPs": azure_native.containerservice.ManagedClusterLoadBalancerProfileManagedOutboundIPsArgs(
                count=2,
            ),
        },
        load_balancer_sku="standard",
        outbound_type="loadBalancer",
    ),
    resource_group_name="rg1",
    resource_name_="clustername1",
    service_principal_profile=azure_native.containerservice.ManagedClusterServicePrincipalProfileArgs(
        client_id="clientid",
        secret="secret",
    ),
    sku=azure_native.containerservice.ManagedClusterSKUArgs(
        name="Basic",
        tier="Free",
    ),
    tags={
        "archv2": "",
        "tier": "production",
    },
    windows_profile=azure_native.containerservice.ManagedClusterWindowsProfileArgs(
        admin_password="replacePassword1234$",
        admin_username="azureuser",
    ))

```

```yaml
resources:
  managedCluster:
    type: azure-native:containerservice:ManagedCluster
    properties:
      addonProfiles:
        azureKeyvaultSecretsProvider:
          config:
            enableSecretRotation: 'true'
            rotationPollInterval: 2m
          enabled: true
      agentPoolProfiles:
        - count: 3
          enableNodePublicIP: true
          mode: System
          name: nodepool1
          osType: Linux
          type: VirtualMachineScaleSets
          vmSize: Standard_DS2_v2
      autoScalerProfile:
        scaleDownDelayAfterAdd: 15m
        scanInterval: 20s
      diskEncryptionSetID: /subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des
      dnsPrefix: dnsprefix1
      enablePodSecurityPolicy: true
      enableRBAC: true
      kubernetesVersion:
      linuxProfile:
        adminUsername: azureuser
        ssh:
          publicKeys:
            - keyData: keydata
      location: location1
      networkProfile:
        loadBalancerProfile:
          managedOutboundIPs:
            count: 2
        loadBalancerSku: standard
        outboundType: loadBalancer
      resourceGroupName: rg1
      resourceName: clustername1
      servicePrincipalProfile:
        clientId: clientid
        secret: secret
      sku:
        name: Basic
        tier: Free
      tags:
        archv2:
        tier: production
      windowsProfile:
        adminPassword: replacePassword1234$
        adminUsername: azureuser

```

{{% /example %}}
{{% example %}}
### Create Managed Cluster with Dedicated Host Group
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedCluster = new AzureNative.ContainerService.ManagedCluster("managedCluster", new()
    {
        AddonProfiles = null,
        AgentPoolProfiles = new[]
        {
            new AzureNative.ContainerService.Inputs.ManagedClusterAgentPoolProfileArgs
            {
                Count = 3,
                EnableNodePublicIP = true,
                HostGroupID = "/subscriptions/subid1/resourcegroups/rg/providers/Microsoft.Compute/hostGroups/hostgroup1",
                Name = "nodepool1",
                OsType = "Linux",
                Type = "VirtualMachineScaleSets",
                VmSize = "Standard_DS2_v2",
            },
        },
        AutoScalerProfile = new AzureNative.ContainerService.Inputs.ManagedClusterPropertiesAutoScalerProfileArgs
        {
            ScaleDownDelayAfterAdd = "15m",
            ScanInterval = "20s",
        },
        DiskEncryptionSetID = "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
        DnsPrefix = "dnsprefix1",
        EnablePodSecurityPolicy = false,
        EnableRBAC = true,
        KubernetesVersion = "",
        LinuxProfile = new AzureNative.ContainerService.Inputs.ContainerServiceLinuxProfileArgs
        {
            AdminUsername = "azureuser",
            Ssh = new AzureNative.ContainerService.Inputs.ContainerServiceSshConfigurationArgs
            {
                PublicKeys = new[]
                {
                    new AzureNative.ContainerService.Inputs.ContainerServiceSshPublicKeyArgs
                    {
                        KeyData = "keydata",
                    },
                },
            },
        },
        Location = "location1",
        NetworkProfile = new AzureNative.ContainerService.Inputs.ContainerServiceNetworkProfileArgs
        {
            LoadBalancerProfile = new AzureNative.ContainerService.Inputs.ManagedClusterLoadBalancerProfileArgs
            {
                ManagedOutboundIPs = new AzureNative.ContainerService.Inputs.ManagedClusterLoadBalancerProfileManagedOutboundIPsArgs
                {
                    Count = 2,
                },
            },
            LoadBalancerSku = "standard",
            OutboundType = "loadBalancer",
        },
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        ServicePrincipalProfile = new AzureNative.ContainerService.Inputs.ManagedClusterServicePrincipalProfileArgs
        {
            ClientId = "clientid",
            Secret = "secret",
        },
        Sku = new AzureNative.ContainerService.Inputs.ManagedClusterSKUArgs
        {
            Name = "Basic",
            Tier = "Free",
        },
        Tags = 
        {
            { "archv2", "" },
            { "tier", "production" },
        },
        WindowsProfile = new AzureNative.ContainerService.Inputs.ManagedClusterWindowsProfileArgs
        {
            AdminPassword = "replacePassword1234$",
            AdminUsername = "azureuser",
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.containerservice.ManagedCluster;
import com.pulumi.azurenative.containerservice.ManagedClusterArgs;
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
        var managedCluster = new ManagedCluster("managedCluster", ManagedClusterArgs.builder()        
            .addonProfiles()
            .agentPoolProfiles(Map.ofEntries(
                Map.entry("count", 3),
                Map.entry("enableNodePublicIP", true),
                Map.entry("hostGroupID", "/subscriptions/subid1/resourcegroups/rg/providers/Microsoft.Compute/hostGroups/hostgroup1"),
                Map.entry("name", "nodepool1"),
                Map.entry("osType", "Linux"),
                Map.entry("type", "VirtualMachineScaleSets"),
                Map.entry("vmSize", "Standard_DS2_v2")
            ))
            .autoScalerProfile(Map.ofEntries(
                Map.entry("scaleDownDelayAfterAdd", "15m"),
                Map.entry("scanInterval", "20s")
            ))
            .diskEncryptionSetID("/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des")
            .dnsPrefix("dnsprefix1")
            .enablePodSecurityPolicy(false)
            .enableRBAC(true)
            .kubernetesVersion("")
            .linuxProfile(Map.ofEntries(
                Map.entry("adminUsername", "azureuser"),
                Map.entry("ssh", Map.of("publicKeys", Map.of("keyData", "keydata")))
            ))
            .location("location1")
            .networkProfile(Map.ofEntries(
                Map.entry("loadBalancerProfile", Map.of("managedOutboundIPs", Map.of("count", 2))),
                Map.entry("loadBalancerSku", "standard"),
                Map.entry("outboundType", "loadBalancer")
            ))
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .servicePrincipalProfile(Map.ofEntries(
                Map.entry("clientId", "clientid"),
                Map.entry("secret", "secret")
            ))
            .sku(Map.ofEntries(
                Map.entry("name", "Basic"),
                Map.entry("tier", "Free")
            ))
            .tags(Map.ofEntries(
                Map.entry("archv2", ""),
                Map.entry("tier", "production")
            ))
            .windowsProfile(Map.ofEntries(
                Map.entry("adminPassword", "replacePassword1234$"),
                Map.entry("adminUsername", "azureuser")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedCluster = new azure_native.containerservice.ManagedCluster("managedCluster", {
    addonProfiles: {},
    agentPoolProfiles: [{
        count: 3,
        enableNodePublicIP: true,
        hostGroupID: "/subscriptions/subid1/resourcegroups/rg/providers/Microsoft.Compute/hostGroups/hostgroup1",
        name: "nodepool1",
        osType: "Linux",
        type: "VirtualMachineScaleSets",
        vmSize: "Standard_DS2_v2",
    }],
    autoScalerProfile: {
        scaleDownDelayAfterAdd: "15m",
        scanInterval: "20s",
    },
    diskEncryptionSetID: "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
    dnsPrefix: "dnsprefix1",
    enablePodSecurityPolicy: false,
    enableRBAC: true,
    kubernetesVersion: "",
    linuxProfile: {
        adminUsername: "azureuser",
        ssh: {
            publicKeys: [{
                keyData: "keydata",
            }],
        },
    },
    location: "location1",
    networkProfile: {
        loadBalancerProfile: {
            managedOutboundIPs: {
                count: 2,
            },
        },
        loadBalancerSku: "standard",
        outboundType: "loadBalancer",
    },
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    servicePrincipalProfile: {
        clientId: "clientid",
        secret: "secret",
    },
    sku: {
        name: "Basic",
        tier: "Free",
    },
    tags: {
        archv2: "",
        tier: "production",
    },
    windowsProfile: {
        adminPassword: "replacePassword1234$",
        adminUsername: "azureuser",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_cluster = azure_native.containerservice.ManagedCluster("managedCluster",
    addon_profiles={},
    agent_pool_profiles=[azure_native.containerservice.ManagedClusterAgentPoolProfileArgs(
        count=3,
        enable_node_public_ip=True,
        host_group_id="/subscriptions/subid1/resourcegroups/rg/providers/Microsoft.Compute/hostGroups/hostgroup1",
        name="nodepool1",
        os_type="Linux",
        type="VirtualMachineScaleSets",
        vm_size="Standard_DS2_v2",
    )],
    auto_scaler_profile=azure_native.containerservice.ManagedClusterPropertiesAutoScalerProfileArgs(
        scale_down_delay_after_add="15m",
        scan_interval="20s",
    ),
    disk_encryption_set_id="/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
    dns_prefix="dnsprefix1",
    enable_pod_security_policy=False,
    enable_rbac=True,
    kubernetes_version="",
    linux_profile=azure_native.containerservice.ContainerServiceLinuxProfileResponseArgs(
        admin_username="azureuser",
        ssh={
            "publicKeys": [azure_native.containerservice.ContainerServiceSshPublicKeyArgs(
                key_data="keydata",
            )],
        },
    ),
    location="location1",
    network_profile=azure_native.containerservice.ContainerServiceNetworkProfileResponseArgs(
        load_balancer_profile={
            "managedOutboundIPs": azure_native.containerservice.ManagedClusterLoadBalancerProfileManagedOutboundIPsArgs(
                count=2,
            ),
        },
        load_balancer_sku="standard",
        outbound_type="loadBalancer",
    ),
    resource_group_name="rg1",
    resource_name_="clustername1",
    service_principal_profile=azure_native.containerservice.ManagedClusterServicePrincipalProfileArgs(
        client_id="clientid",
        secret="secret",
    ),
    sku=azure_native.containerservice.ManagedClusterSKUArgs(
        name="Basic",
        tier="Free",
    ),
    tags={
        "archv2": "",
        "tier": "production",
    },
    windows_profile=azure_native.containerservice.ManagedClusterWindowsProfileArgs(
        admin_password="replacePassword1234$",
        admin_username="azureuser",
    ))

```

```yaml
resources:
  managedCluster:
    type: azure-native:containerservice:ManagedCluster
    properties:
      addonProfiles: {}
      agentPoolProfiles:
        - count: 3
          enableNodePublicIP: true
          hostGroupID: /subscriptions/subid1/resourcegroups/rg/providers/Microsoft.Compute/hostGroups/hostgroup1
          name: nodepool1
          osType: Linux
          type: VirtualMachineScaleSets
          vmSize: Standard_DS2_v2
      autoScalerProfile:
        scaleDownDelayAfterAdd: 15m
        scanInterval: 20s
      diskEncryptionSetID: /subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des
      dnsPrefix: dnsprefix1
      enablePodSecurityPolicy: false
      enableRBAC: true
      kubernetesVersion:
      linuxProfile:
        adminUsername: azureuser
        ssh:
          publicKeys:
            - keyData: keydata
      location: location1
      networkProfile:
        loadBalancerProfile:
          managedOutboundIPs:
            count: 2
        loadBalancerSku: standard
        outboundType: loadBalancer
      resourceGroupName: rg1
      resourceName: clustername1
      servicePrincipalProfile:
        clientId: clientid
        secret: secret
      sku:
        name: Basic
        tier: Free
      tags:
        archv2:
        tier: production
      windowsProfile:
        adminPassword: replacePassword1234$
        adminUsername: azureuser

```

{{% /example %}}
{{% example %}}
### Create Managed Cluster with EncryptionAtHost enabled
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedCluster = new AzureNative.ContainerService.ManagedCluster("managedCluster", new()
    {
        AddonProfiles = null,
        AgentPoolProfiles = new[]
        {
            new AzureNative.ContainerService.Inputs.ManagedClusterAgentPoolProfileArgs
            {
                Count = 3,
                EnableEncryptionAtHost = true,
                EnableNodePublicIP = true,
                Mode = "System",
                Name = "nodepool1",
                OsType = "Linux",
                Type = "VirtualMachineScaleSets",
                VmSize = "Standard_DS2_v2",
            },
        },
        AutoScalerProfile = new AzureNative.ContainerService.Inputs.ManagedClusterPropertiesAutoScalerProfileArgs
        {
            ScaleDownDelayAfterAdd = "15m",
            ScanInterval = "20s",
        },
        DiskEncryptionSetID = "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
        DnsPrefix = "dnsprefix1",
        EnablePodSecurityPolicy = true,
        EnableRBAC = true,
        KubernetesVersion = "",
        LinuxProfile = new AzureNative.ContainerService.Inputs.ContainerServiceLinuxProfileArgs
        {
            AdminUsername = "azureuser",
            Ssh = new AzureNative.ContainerService.Inputs.ContainerServiceSshConfigurationArgs
            {
                PublicKeys = new[]
                {
                    new AzureNative.ContainerService.Inputs.ContainerServiceSshPublicKeyArgs
                    {
                        KeyData = "keydata",
                    },
                },
            },
        },
        Location = "location1",
        NetworkProfile = new AzureNative.ContainerService.Inputs.ContainerServiceNetworkProfileArgs
        {
            LoadBalancerProfile = new AzureNative.ContainerService.Inputs.ManagedClusterLoadBalancerProfileArgs
            {
                ManagedOutboundIPs = new AzureNative.ContainerService.Inputs.ManagedClusterLoadBalancerProfileManagedOutboundIPsArgs
                {
                    Count = 2,
                },
            },
            LoadBalancerSku = "standard",
            OutboundType = "loadBalancer",
        },
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        ServicePrincipalProfile = new AzureNative.ContainerService.Inputs.ManagedClusterServicePrincipalProfileArgs
        {
            ClientId = "clientid",
            Secret = "secret",
        },
        Sku = new AzureNative.ContainerService.Inputs.ManagedClusterSKUArgs
        {
            Name = "Basic",
            Tier = "Free",
        },
        Tags = 
        {
            { "archv2", "" },
            { "tier", "production" },
        },
        WindowsProfile = new AzureNative.ContainerService.Inputs.ManagedClusterWindowsProfileArgs
        {
            AdminPassword = "replacePassword1234$",
            AdminUsername = "azureuser",
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.containerservice.ManagedCluster;
import com.pulumi.azurenative.containerservice.ManagedClusterArgs;
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
        var managedCluster = new ManagedCluster("managedCluster", ManagedClusterArgs.builder()        
            .addonProfiles()
            .agentPoolProfiles(Map.ofEntries(
                Map.entry("count", 3),
                Map.entry("enableEncryptionAtHost", true),
                Map.entry("enableNodePublicIP", true),
                Map.entry("mode", "System"),
                Map.entry("name", "nodepool1"),
                Map.entry("osType", "Linux"),
                Map.entry("type", "VirtualMachineScaleSets"),
                Map.entry("vmSize", "Standard_DS2_v2")
            ))
            .autoScalerProfile(Map.ofEntries(
                Map.entry("scaleDownDelayAfterAdd", "15m"),
                Map.entry("scanInterval", "20s")
            ))
            .diskEncryptionSetID("/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des")
            .dnsPrefix("dnsprefix1")
            .enablePodSecurityPolicy(true)
            .enableRBAC(true)
            .kubernetesVersion("")
            .linuxProfile(Map.ofEntries(
                Map.entry("adminUsername", "azureuser"),
                Map.entry("ssh", Map.of("publicKeys", Map.of("keyData", "keydata")))
            ))
            .location("location1")
            .networkProfile(Map.ofEntries(
                Map.entry("loadBalancerProfile", Map.of("managedOutboundIPs", Map.of("count", 2))),
                Map.entry("loadBalancerSku", "standard"),
                Map.entry("outboundType", "loadBalancer")
            ))
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .servicePrincipalProfile(Map.ofEntries(
                Map.entry("clientId", "clientid"),
                Map.entry("secret", "secret")
            ))
            .sku(Map.ofEntries(
                Map.entry("name", "Basic"),
                Map.entry("tier", "Free")
            ))
            .tags(Map.ofEntries(
                Map.entry("archv2", ""),
                Map.entry("tier", "production")
            ))
            .windowsProfile(Map.ofEntries(
                Map.entry("adminPassword", "replacePassword1234$"),
                Map.entry("adminUsername", "azureuser")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedCluster = new azure_native.containerservice.ManagedCluster("managedCluster", {
    addonProfiles: {},
    agentPoolProfiles: [{
        count: 3,
        enableEncryptionAtHost: true,
        enableNodePublicIP: true,
        mode: "System",
        name: "nodepool1",
        osType: "Linux",
        type: "VirtualMachineScaleSets",
        vmSize: "Standard_DS2_v2",
    }],
    autoScalerProfile: {
        scaleDownDelayAfterAdd: "15m",
        scanInterval: "20s",
    },
    diskEncryptionSetID: "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
    dnsPrefix: "dnsprefix1",
    enablePodSecurityPolicy: true,
    enableRBAC: true,
    kubernetesVersion: "",
    linuxProfile: {
        adminUsername: "azureuser",
        ssh: {
            publicKeys: [{
                keyData: "keydata",
            }],
        },
    },
    location: "location1",
    networkProfile: {
        loadBalancerProfile: {
            managedOutboundIPs: {
                count: 2,
            },
        },
        loadBalancerSku: "standard",
        outboundType: "loadBalancer",
    },
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    servicePrincipalProfile: {
        clientId: "clientid",
        secret: "secret",
    },
    sku: {
        name: "Basic",
        tier: "Free",
    },
    tags: {
        archv2: "",
        tier: "production",
    },
    windowsProfile: {
        adminPassword: "replacePassword1234$",
        adminUsername: "azureuser",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_cluster = azure_native.containerservice.ManagedCluster("managedCluster",
    addon_profiles={},
    agent_pool_profiles=[azure_native.containerservice.ManagedClusterAgentPoolProfileArgs(
        count=3,
        enable_encryption_at_host=True,
        enable_node_public_ip=True,
        mode="System",
        name="nodepool1",
        os_type="Linux",
        type="VirtualMachineScaleSets",
        vm_size="Standard_DS2_v2",
    )],
    auto_scaler_profile=azure_native.containerservice.ManagedClusterPropertiesAutoScalerProfileArgs(
        scale_down_delay_after_add="15m",
        scan_interval="20s",
    ),
    disk_encryption_set_id="/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
    dns_prefix="dnsprefix1",
    enable_pod_security_policy=True,
    enable_rbac=True,
    kubernetes_version="",
    linux_profile=azure_native.containerservice.ContainerServiceLinuxProfileResponseArgs(
        admin_username="azureuser",
        ssh={
            "publicKeys": [azure_native.containerservice.ContainerServiceSshPublicKeyArgs(
                key_data="keydata",
            )],
        },
    ),
    location="location1",
    network_profile=azure_native.containerservice.ContainerServiceNetworkProfileResponseArgs(
        load_balancer_profile={
            "managedOutboundIPs": azure_native.containerservice.ManagedClusterLoadBalancerProfileManagedOutboundIPsArgs(
                count=2,
            ),
        },
        load_balancer_sku="standard",
        outbound_type="loadBalancer",
    ),
    resource_group_name="rg1",
    resource_name_="clustername1",
    service_principal_profile=azure_native.containerservice.ManagedClusterServicePrincipalProfileArgs(
        client_id="clientid",
        secret="secret",
    ),
    sku=azure_native.containerservice.ManagedClusterSKUArgs(
        name="Basic",
        tier="Free",
    ),
    tags={
        "archv2": "",
        "tier": "production",
    },
    windows_profile=azure_native.containerservice.ManagedClusterWindowsProfileArgs(
        admin_password="replacePassword1234$",
        admin_username="azureuser",
    ))

```

```yaml
resources:
  managedCluster:
    type: azure-native:containerservice:ManagedCluster
    properties:
      addonProfiles: {}
      agentPoolProfiles:
        - count: 3
          enableEncryptionAtHost: true
          enableNodePublicIP: true
          mode: System
          name: nodepool1
          osType: Linux
          type: VirtualMachineScaleSets
          vmSize: Standard_DS2_v2
      autoScalerProfile:
        scaleDownDelayAfterAdd: 15m
        scanInterval: 20s
      diskEncryptionSetID: /subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des
      dnsPrefix: dnsprefix1
      enablePodSecurityPolicy: true
      enableRBAC: true
      kubernetesVersion:
      linuxProfile:
        adminUsername: azureuser
        ssh:
          publicKeys:
            - keyData: keydata
      location: location1
      networkProfile:
        loadBalancerProfile:
          managedOutboundIPs:
            count: 2
        loadBalancerSku: standard
        outboundType: loadBalancer
      resourceGroupName: rg1
      resourceName: clustername1
      servicePrincipalProfile:
        clientId: clientid
        secret: secret
      sku:
        name: Basic
        tier: Free
      tags:
        archv2:
        tier: production
      windowsProfile:
        adminPassword: replacePassword1234$
        adminUsername: azureuser

```

{{% /example %}}
{{% example %}}
### Create Managed Cluster with FIPS enabled OS
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedCluster = new AzureNative.ContainerService.ManagedCluster("managedCluster", new()
    {
        AddonProfiles = null,
        AgentPoolProfiles = new[]
        {
            new AzureNative.ContainerService.Inputs.ManagedClusterAgentPoolProfileArgs
            {
                Count = 3,
                EnableFIPS = true,
                EnableNodePublicIP = true,
                Mode = "System",
                Name = "nodepool1",
                OsType = "Linux",
                Type = "VirtualMachineScaleSets",
                VmSize = "Standard_DS2_v2",
            },
        },
        AutoScalerProfile = new AzureNative.ContainerService.Inputs.ManagedClusterPropertiesAutoScalerProfileArgs
        {
            ScaleDownDelayAfterAdd = "15m",
            ScanInterval = "20s",
        },
        DiskEncryptionSetID = "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
        DnsPrefix = "dnsprefix1",
        EnablePodSecurityPolicy = false,
        EnableRBAC = true,
        KubernetesVersion = "",
        LinuxProfile = new AzureNative.ContainerService.Inputs.ContainerServiceLinuxProfileArgs
        {
            AdminUsername = "azureuser",
            Ssh = new AzureNative.ContainerService.Inputs.ContainerServiceSshConfigurationArgs
            {
                PublicKeys = new[]
                {
                    new AzureNative.ContainerService.Inputs.ContainerServiceSshPublicKeyArgs
                    {
                        KeyData = "keydata",
                    },
                },
            },
        },
        Location = "location1",
        NetworkProfile = new AzureNative.ContainerService.Inputs.ContainerServiceNetworkProfileArgs
        {
            LoadBalancerProfile = new AzureNative.ContainerService.Inputs.ManagedClusterLoadBalancerProfileArgs
            {
                ManagedOutboundIPs = new AzureNative.ContainerService.Inputs.ManagedClusterLoadBalancerProfileManagedOutboundIPsArgs
                {
                    Count = 2,
                },
            },
            LoadBalancerSku = "standard",
            OutboundType = "loadBalancer",
        },
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        ServicePrincipalProfile = new AzureNative.ContainerService.Inputs.ManagedClusterServicePrincipalProfileArgs
        {
            ClientId = "clientid",
            Secret = "secret",
        },
        Sku = new AzureNative.ContainerService.Inputs.ManagedClusterSKUArgs
        {
            Name = "Basic",
            Tier = "Free",
        },
        Tags = 
        {
            { "archv2", "" },
            { "tier", "production" },
        },
        WindowsProfile = new AzureNative.ContainerService.Inputs.ManagedClusterWindowsProfileArgs
        {
            AdminPassword = "replacePassword1234$",
            AdminUsername = "azureuser",
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.containerservice.ManagedCluster;
import com.pulumi.azurenative.containerservice.ManagedClusterArgs;
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
        var managedCluster = new ManagedCluster("managedCluster", ManagedClusterArgs.builder()        
            .addonProfiles()
            .agentPoolProfiles(Map.ofEntries(
                Map.entry("count", 3),
                Map.entry("enableFIPS", true),
                Map.entry("enableNodePublicIP", true),
                Map.entry("mode", "System"),
                Map.entry("name", "nodepool1"),
                Map.entry("osType", "Linux"),
                Map.entry("type", "VirtualMachineScaleSets"),
                Map.entry("vmSize", "Standard_DS2_v2")
            ))
            .autoScalerProfile(Map.ofEntries(
                Map.entry("scaleDownDelayAfterAdd", "15m"),
                Map.entry("scanInterval", "20s")
            ))
            .diskEncryptionSetID("/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des")
            .dnsPrefix("dnsprefix1")
            .enablePodSecurityPolicy(false)
            .enableRBAC(true)
            .kubernetesVersion("")
            .linuxProfile(Map.ofEntries(
                Map.entry("adminUsername", "azureuser"),
                Map.entry("ssh", Map.of("publicKeys", Map.of("keyData", "keydata")))
            ))
            .location("location1")
            .networkProfile(Map.ofEntries(
                Map.entry("loadBalancerProfile", Map.of("managedOutboundIPs", Map.of("count", 2))),
                Map.entry("loadBalancerSku", "standard"),
                Map.entry("outboundType", "loadBalancer")
            ))
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .servicePrincipalProfile(Map.ofEntries(
                Map.entry("clientId", "clientid"),
                Map.entry("secret", "secret")
            ))
            .sku(Map.ofEntries(
                Map.entry("name", "Basic"),
                Map.entry("tier", "Free")
            ))
            .tags(Map.ofEntries(
                Map.entry("archv2", ""),
                Map.entry("tier", "production")
            ))
            .windowsProfile(Map.ofEntries(
                Map.entry("adminPassword", "replacePassword1234$"),
                Map.entry("adminUsername", "azureuser")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedCluster = new azure_native.containerservice.ManagedCluster("managedCluster", {
    addonProfiles: {},
    agentPoolProfiles: [{
        count: 3,
        enableFIPS: true,
        enableNodePublicIP: true,
        mode: "System",
        name: "nodepool1",
        osType: "Linux",
        type: "VirtualMachineScaleSets",
        vmSize: "Standard_DS2_v2",
    }],
    autoScalerProfile: {
        scaleDownDelayAfterAdd: "15m",
        scanInterval: "20s",
    },
    diskEncryptionSetID: "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
    dnsPrefix: "dnsprefix1",
    enablePodSecurityPolicy: false,
    enableRBAC: true,
    kubernetesVersion: "",
    linuxProfile: {
        adminUsername: "azureuser",
        ssh: {
            publicKeys: [{
                keyData: "keydata",
            }],
        },
    },
    location: "location1",
    networkProfile: {
        loadBalancerProfile: {
            managedOutboundIPs: {
                count: 2,
            },
        },
        loadBalancerSku: "standard",
        outboundType: "loadBalancer",
    },
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    servicePrincipalProfile: {
        clientId: "clientid",
        secret: "secret",
    },
    sku: {
        name: "Basic",
        tier: "Free",
    },
    tags: {
        archv2: "",
        tier: "production",
    },
    windowsProfile: {
        adminPassword: "replacePassword1234$",
        adminUsername: "azureuser",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_cluster = azure_native.containerservice.ManagedCluster("managedCluster",
    addon_profiles={},
    agent_pool_profiles=[azure_native.containerservice.ManagedClusterAgentPoolProfileArgs(
        count=3,
        enable_fips=True,
        enable_node_public_ip=True,
        mode="System",
        name="nodepool1",
        os_type="Linux",
        type="VirtualMachineScaleSets",
        vm_size="Standard_DS2_v2",
    )],
    auto_scaler_profile=azure_native.containerservice.ManagedClusterPropertiesAutoScalerProfileArgs(
        scale_down_delay_after_add="15m",
        scan_interval="20s",
    ),
    disk_encryption_set_id="/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
    dns_prefix="dnsprefix1",
    enable_pod_security_policy=False,
    enable_rbac=True,
    kubernetes_version="",
    linux_profile=azure_native.containerservice.ContainerServiceLinuxProfileResponseArgs(
        admin_username="azureuser",
        ssh={
            "publicKeys": [azure_native.containerservice.ContainerServiceSshPublicKeyArgs(
                key_data="keydata",
            )],
        },
    ),
    location="location1",
    network_profile=azure_native.containerservice.ContainerServiceNetworkProfileResponseArgs(
        load_balancer_profile={
            "managedOutboundIPs": azure_native.containerservice.ManagedClusterLoadBalancerProfileManagedOutboundIPsArgs(
                count=2,
            ),
        },
        load_balancer_sku="standard",
        outbound_type="loadBalancer",
    ),
    resource_group_name="rg1",
    resource_name_="clustername1",
    service_principal_profile=azure_native.containerservice.ManagedClusterServicePrincipalProfileArgs(
        client_id="clientid",
        secret="secret",
    ),
    sku=azure_native.containerservice.ManagedClusterSKUArgs(
        name="Basic",
        tier="Free",
    ),
    tags={
        "archv2": "",
        "tier": "production",
    },
    windows_profile=azure_native.containerservice.ManagedClusterWindowsProfileArgs(
        admin_password="replacePassword1234$",
        admin_username="azureuser",
    ))

```

```yaml
resources:
  managedCluster:
    type: azure-native:containerservice:ManagedCluster
    properties:
      addonProfiles: {}
      agentPoolProfiles:
        - count: 3
          enableFIPS: true
          enableNodePublicIP: true
          mode: System
          name: nodepool1
          osType: Linux
          type: VirtualMachineScaleSets
          vmSize: Standard_DS2_v2
      autoScalerProfile:
        scaleDownDelayAfterAdd: 15m
        scanInterval: 20s
      diskEncryptionSetID: /subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des
      dnsPrefix: dnsprefix1
      enablePodSecurityPolicy: false
      enableRBAC: true
      kubernetesVersion:
      linuxProfile:
        adminUsername: azureuser
        ssh:
          publicKeys:
            - keyData: keydata
      location: location1
      networkProfile:
        loadBalancerProfile:
          managedOutboundIPs:
            count: 2
        loadBalancerSku: standard
        outboundType: loadBalancer
      resourceGroupName: rg1
      resourceName: clustername1
      servicePrincipalProfile:
        clientId: clientid
        secret: secret
      sku:
        name: Basic
        tier: Free
      tags:
        archv2:
        tier: production
      windowsProfile:
        adminPassword: replacePassword1234$
        adminUsername: azureuser

```

{{% /example %}}
{{% example %}}
### Create Managed Cluster with GPUMIG
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedCluster = new AzureNative.ContainerService.ManagedCluster("managedCluster", new()
    {
        AddonProfiles = null,
        AgentPoolProfiles = new[]
        {
            new AzureNative.ContainerService.Inputs.ManagedClusterAgentPoolProfileArgs
            {
                Count = 3,
                EnableNodePublicIP = true,
                GpuInstanceProfile = "MIG3g",
                Mode = "System",
                Name = "nodepool1",
                OsType = "Linux",
                Type = "VirtualMachineScaleSets",
                VmSize = "Standard_ND96asr_v4",
            },
        },
        AutoScalerProfile = new AzureNative.ContainerService.Inputs.ManagedClusterPropertiesAutoScalerProfileArgs
        {
            ScaleDownDelayAfterAdd = "15m",
            ScanInterval = "20s",
        },
        DiskEncryptionSetID = "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
        DnsPrefix = "dnsprefix1",
        EnablePodSecurityPolicy = true,
        EnableRBAC = true,
        HttpProxyConfig = new AzureNative.ContainerService.Inputs.ManagedClusterHTTPProxyConfigArgs
        {
            HttpProxy = "http://myproxy.server.com:8080",
            HttpsProxy = "https://myproxy.server.com:8080",
            NoProxy = new[]
            {
                "localhost",
                "127.0.0.1",
            },
            TrustedCa = "Q29uZ3JhdHMhIFlvdSBoYXZlIGZvdW5kIGEgaGlkZGVuIG1lc3NhZ2U=",
        },
        KubernetesVersion = "",
        LinuxProfile = new AzureNative.ContainerService.Inputs.ContainerServiceLinuxProfileArgs
        {
            AdminUsername = "azureuser",
            Ssh = new AzureNative.ContainerService.Inputs.ContainerServiceSshConfigurationArgs
            {
                PublicKeys = new[]
                {
                    new AzureNative.ContainerService.Inputs.ContainerServiceSshPublicKeyArgs
                    {
                        KeyData = "keydata",
                    },
                },
            },
        },
        Location = "location1",
        NetworkProfile = new AzureNative.ContainerService.Inputs.ContainerServiceNetworkProfileArgs
        {
            LoadBalancerProfile = new AzureNative.ContainerService.Inputs.ManagedClusterLoadBalancerProfileArgs
            {
                ManagedOutboundIPs = new AzureNative.ContainerService.Inputs.ManagedClusterLoadBalancerProfileManagedOutboundIPsArgs
                {
                    Count = 2,
                },
            },
            LoadBalancerSku = "standard",
            OutboundType = "loadBalancer",
        },
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        ServicePrincipalProfile = new AzureNative.ContainerService.Inputs.ManagedClusterServicePrincipalProfileArgs
        {
            ClientId = "clientid",
            Secret = "secret",
        },
        Sku = new AzureNative.ContainerService.Inputs.ManagedClusterSKUArgs
        {
            Name = "Basic",
            Tier = "Free",
        },
        Tags = 
        {
            { "archv2", "" },
            { "tier", "production" },
        },
        WindowsProfile = new AzureNative.ContainerService.Inputs.ManagedClusterWindowsProfileArgs
        {
            AdminPassword = "replacePassword1234$",
            AdminUsername = "azureuser",
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.containerservice.ManagedCluster;
import com.pulumi.azurenative.containerservice.ManagedClusterArgs;
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
        var managedCluster = new ManagedCluster("managedCluster", ManagedClusterArgs.builder()        
            .addonProfiles()
            .agentPoolProfiles(Map.ofEntries(
                Map.entry("count", 3),
                Map.entry("enableNodePublicIP", true),
                Map.entry("gpuInstanceProfile", "MIG3g"),
                Map.entry("mode", "System"),
                Map.entry("name", "nodepool1"),
                Map.entry("osType", "Linux"),
                Map.entry("type", "VirtualMachineScaleSets"),
                Map.entry("vmSize", "Standard_ND96asr_v4")
            ))
            .autoScalerProfile(Map.ofEntries(
                Map.entry("scaleDownDelayAfterAdd", "15m"),
                Map.entry("scanInterval", "20s")
            ))
            .diskEncryptionSetID("/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des")
            .dnsPrefix("dnsprefix1")
            .enablePodSecurityPolicy(true)
            .enableRBAC(true)
            .httpProxyConfig(Map.ofEntries(
                Map.entry("httpProxy", "http://myproxy.server.com:8080"),
                Map.entry("httpsProxy", "https://myproxy.server.com:8080"),
                Map.entry("noProxy",                 
                    "localhost",
                    "127.0.0.1"),
                Map.entry("trustedCa", "Q29uZ3JhdHMhIFlvdSBoYXZlIGZvdW5kIGEgaGlkZGVuIG1lc3NhZ2U=")
            ))
            .kubernetesVersion("")
            .linuxProfile(Map.ofEntries(
                Map.entry("adminUsername", "azureuser"),
                Map.entry("ssh", Map.of("publicKeys", Map.of("keyData", "keydata")))
            ))
            .location("location1")
            .networkProfile(Map.ofEntries(
                Map.entry("loadBalancerProfile", Map.of("managedOutboundIPs", Map.of("count", 2))),
                Map.entry("loadBalancerSku", "standard"),
                Map.entry("outboundType", "loadBalancer")
            ))
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .servicePrincipalProfile(Map.ofEntries(
                Map.entry("clientId", "clientid"),
                Map.entry("secret", "secret")
            ))
            .sku(Map.ofEntries(
                Map.entry("name", "Basic"),
                Map.entry("tier", "Free")
            ))
            .tags(Map.ofEntries(
                Map.entry("archv2", ""),
                Map.entry("tier", "production")
            ))
            .windowsProfile(Map.ofEntries(
                Map.entry("adminPassword", "replacePassword1234$"),
                Map.entry("adminUsername", "azureuser")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedCluster = new azure_native.containerservice.ManagedCluster("managedCluster", {
    addonProfiles: {},
    agentPoolProfiles: [{
        count: 3,
        enableNodePublicIP: true,
        gpuInstanceProfile: "MIG3g",
        mode: "System",
        name: "nodepool1",
        osType: "Linux",
        type: "VirtualMachineScaleSets",
        vmSize: "Standard_ND96asr_v4",
    }],
    autoScalerProfile: {
        scaleDownDelayAfterAdd: "15m",
        scanInterval: "20s",
    },
    diskEncryptionSetID: "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
    dnsPrefix: "dnsprefix1",
    enablePodSecurityPolicy: true,
    enableRBAC: true,
    httpProxyConfig: {
        httpProxy: "http://myproxy.server.com:8080",
        httpsProxy: "https://myproxy.server.com:8080",
        noProxy: [
            "localhost",
            "127.0.0.1",
        ],
        trustedCa: "Q29uZ3JhdHMhIFlvdSBoYXZlIGZvdW5kIGEgaGlkZGVuIG1lc3NhZ2U=",
    },
    kubernetesVersion: "",
    linuxProfile: {
        adminUsername: "azureuser",
        ssh: {
            publicKeys: [{
                keyData: "keydata",
            }],
        },
    },
    location: "location1",
    networkProfile: {
        loadBalancerProfile: {
            managedOutboundIPs: {
                count: 2,
            },
        },
        loadBalancerSku: "standard",
        outboundType: "loadBalancer",
    },
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    servicePrincipalProfile: {
        clientId: "clientid",
        secret: "secret",
    },
    sku: {
        name: "Basic",
        tier: "Free",
    },
    tags: {
        archv2: "",
        tier: "production",
    },
    windowsProfile: {
        adminPassword: "replacePassword1234$",
        adminUsername: "azureuser",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_cluster = azure_native.containerservice.ManagedCluster("managedCluster",
    addon_profiles={},
    agent_pool_profiles=[azure_native.containerservice.ManagedClusterAgentPoolProfileArgs(
        count=3,
        enable_node_public_ip=True,
        gpu_instance_profile="MIG3g",
        mode="System",
        name="nodepool1",
        os_type="Linux",
        type="VirtualMachineScaleSets",
        vm_size="Standard_ND96asr_v4",
    )],
    auto_scaler_profile=azure_native.containerservice.ManagedClusterPropertiesAutoScalerProfileArgs(
        scale_down_delay_after_add="15m",
        scan_interval="20s",
    ),
    disk_encryption_set_id="/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
    dns_prefix="dnsprefix1",
    enable_pod_security_policy=True,
    enable_rbac=True,
    http_proxy_config=azure_native.containerservice.ManagedClusterHTTPProxyConfigArgs(
        http_proxy="http://myproxy.server.com:8080",
        https_proxy="https://myproxy.server.com:8080",
        no_proxy=[
            "localhost",
            "127.0.0.1",
        ],
        trusted_ca="Q29uZ3JhdHMhIFlvdSBoYXZlIGZvdW5kIGEgaGlkZGVuIG1lc3NhZ2U=",
    ),
    kubernetes_version="",
    linux_profile=azure_native.containerservice.ContainerServiceLinuxProfileResponseArgs(
        admin_username="azureuser",
        ssh={
            "publicKeys": [azure_native.containerservice.ContainerServiceSshPublicKeyArgs(
                key_data="keydata",
            )],
        },
    ),
    location="location1",
    network_profile=azure_native.containerservice.ContainerServiceNetworkProfileResponseArgs(
        load_balancer_profile={
            "managedOutboundIPs": azure_native.containerservice.ManagedClusterLoadBalancerProfileManagedOutboundIPsArgs(
                count=2,
            ),
        },
        load_balancer_sku="standard",
        outbound_type="loadBalancer",
    ),
    resource_group_name="rg1",
    resource_name_="clustername1",
    service_principal_profile=azure_native.containerservice.ManagedClusterServicePrincipalProfileArgs(
        client_id="clientid",
        secret="secret",
    ),
    sku=azure_native.containerservice.ManagedClusterSKUArgs(
        name="Basic",
        tier="Free",
    ),
    tags={
        "archv2": "",
        "tier": "production",
    },
    windows_profile=azure_native.containerservice.ManagedClusterWindowsProfileArgs(
        admin_password="replacePassword1234$",
        admin_username="azureuser",
    ))

```

```yaml
resources:
  managedCluster:
    type: azure-native:containerservice:ManagedCluster
    properties:
      addonProfiles: {}
      agentPoolProfiles:
        - count: 3
          enableNodePublicIP: true
          gpuInstanceProfile: MIG3g
          mode: System
          name: nodepool1
          osType: Linux
          type: VirtualMachineScaleSets
          vmSize: Standard_ND96asr_v4
      autoScalerProfile:
        scaleDownDelayAfterAdd: 15m
        scanInterval: 20s
      diskEncryptionSetID: /subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des
      dnsPrefix: dnsprefix1
      enablePodSecurityPolicy: true
      enableRBAC: true
      httpProxyConfig:
        httpProxy: http://myproxy.server.com:8080
        httpsProxy: https://myproxy.server.com:8080
        noProxy:
          - localhost
          - 127.0.0.1
        trustedCa: Q29uZ3JhdHMhIFlvdSBoYXZlIGZvdW5kIGEgaGlkZGVuIG1lc3NhZ2U=
      kubernetesVersion:
      linuxProfile:
        adminUsername: azureuser
        ssh:
          publicKeys:
            - keyData: keydata
      location: location1
      networkProfile:
        loadBalancerProfile:
          managedOutboundIPs:
            count: 2
        loadBalancerSku: standard
        outboundType: loadBalancer
      resourceGroupName: rg1
      resourceName: clustername1
      servicePrincipalProfile:
        clientId: clientid
        secret: secret
      sku:
        name: Basic
        tier: Free
      tags:
        archv2:
        tier: production
      windowsProfile:
        adminPassword: replacePassword1234$
        adminUsername: azureuser

```

{{% /example %}}
{{% example %}}
### Create Managed Cluster with HTTP proxy configured
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedCluster = new AzureNative.ContainerService.ManagedCluster("managedCluster", new()
    {
        AddonProfiles = null,
        AgentPoolProfiles = new[]
        {
            new AzureNative.ContainerService.Inputs.ManagedClusterAgentPoolProfileArgs
            {
                Count = 3,
                EnableNodePublicIP = true,
                Mode = "System",
                Name = "nodepool1",
                OsType = "Linux",
                Type = "VirtualMachineScaleSets",
                VmSize = "Standard_DS2_v2",
            },
        },
        AutoScalerProfile = new AzureNative.ContainerService.Inputs.ManagedClusterPropertiesAutoScalerProfileArgs
        {
            ScaleDownDelayAfterAdd = "15m",
            ScanInterval = "20s",
        },
        DiskEncryptionSetID = "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
        DnsPrefix = "dnsprefix1",
        EnablePodSecurityPolicy = true,
        EnableRBAC = true,
        HttpProxyConfig = new AzureNative.ContainerService.Inputs.ManagedClusterHTTPProxyConfigArgs
        {
            HttpProxy = "http://myproxy.server.com:8080",
            HttpsProxy = "https://myproxy.server.com:8080",
            NoProxy = new[]
            {
                "localhost",
                "127.0.0.1",
            },
            TrustedCa = "Q29uZ3JhdHMhIFlvdSBoYXZlIGZvdW5kIGEgaGlkZGVuIG1lc3NhZ2U=",
        },
        KubernetesVersion = "",
        LinuxProfile = new AzureNative.ContainerService.Inputs.ContainerServiceLinuxProfileArgs
        {
            AdminUsername = "azureuser",
            Ssh = new AzureNative.ContainerService.Inputs.ContainerServiceSshConfigurationArgs
            {
                PublicKeys = new[]
                {
                    new AzureNative.ContainerService.Inputs.ContainerServiceSshPublicKeyArgs
                    {
                        KeyData = "keydata",
                    },
                },
            },
        },
        Location = "location1",
        NetworkProfile = new AzureNative.ContainerService.Inputs.ContainerServiceNetworkProfileArgs
        {
            LoadBalancerProfile = new AzureNative.ContainerService.Inputs.ManagedClusterLoadBalancerProfileArgs
            {
                ManagedOutboundIPs = new AzureNative.ContainerService.Inputs.ManagedClusterLoadBalancerProfileManagedOutboundIPsArgs
                {
                    Count = 2,
                },
            },
            LoadBalancerSku = "standard",
            OutboundType = "loadBalancer",
        },
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        ServicePrincipalProfile = new AzureNative.ContainerService.Inputs.ManagedClusterServicePrincipalProfileArgs
        {
            ClientId = "clientid",
            Secret = "secret",
        },
        Sku = new AzureNative.ContainerService.Inputs.ManagedClusterSKUArgs
        {
            Name = "Basic",
            Tier = "Free",
        },
        Tags = 
        {
            { "archv2", "" },
            { "tier", "production" },
        },
        WindowsProfile = new AzureNative.ContainerService.Inputs.ManagedClusterWindowsProfileArgs
        {
            AdminPassword = "replacePassword1234$",
            AdminUsername = "azureuser",
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.containerservice.ManagedCluster;
import com.pulumi.azurenative.containerservice.ManagedClusterArgs;
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
        var managedCluster = new ManagedCluster("managedCluster", ManagedClusterArgs.builder()        
            .addonProfiles()
            .agentPoolProfiles(Map.ofEntries(
                Map.entry("count", 3),
                Map.entry("enableNodePublicIP", true),
                Map.entry("mode", "System"),
                Map.entry("name", "nodepool1"),
                Map.entry("osType", "Linux"),
                Map.entry("type", "VirtualMachineScaleSets"),
                Map.entry("vmSize", "Standard_DS2_v2")
            ))
            .autoScalerProfile(Map.ofEntries(
                Map.entry("scaleDownDelayAfterAdd", "15m"),
                Map.entry("scanInterval", "20s")
            ))
            .diskEncryptionSetID("/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des")
            .dnsPrefix("dnsprefix1")
            .enablePodSecurityPolicy(true)
            .enableRBAC(true)
            .httpProxyConfig(Map.ofEntries(
                Map.entry("httpProxy", "http://myproxy.server.com:8080"),
                Map.entry("httpsProxy", "https://myproxy.server.com:8080"),
                Map.entry("noProxy",                 
                    "localhost",
                    "127.0.0.1"),
                Map.entry("trustedCa", "Q29uZ3JhdHMhIFlvdSBoYXZlIGZvdW5kIGEgaGlkZGVuIG1lc3NhZ2U=")
            ))
            .kubernetesVersion("")
            .linuxProfile(Map.ofEntries(
                Map.entry("adminUsername", "azureuser"),
                Map.entry("ssh", Map.of("publicKeys", Map.of("keyData", "keydata")))
            ))
            .location("location1")
            .networkProfile(Map.ofEntries(
                Map.entry("loadBalancerProfile", Map.of("managedOutboundIPs", Map.of("count", 2))),
                Map.entry("loadBalancerSku", "standard"),
                Map.entry("outboundType", "loadBalancer")
            ))
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .servicePrincipalProfile(Map.ofEntries(
                Map.entry("clientId", "clientid"),
                Map.entry("secret", "secret")
            ))
            .sku(Map.ofEntries(
                Map.entry("name", "Basic"),
                Map.entry("tier", "Free")
            ))
            .tags(Map.ofEntries(
                Map.entry("archv2", ""),
                Map.entry("tier", "production")
            ))
            .windowsProfile(Map.ofEntries(
                Map.entry("adminPassword", "replacePassword1234$"),
                Map.entry("adminUsername", "azureuser")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedCluster = new azure_native.containerservice.ManagedCluster("managedCluster", {
    addonProfiles: {},
    agentPoolProfiles: [{
        count: 3,
        enableNodePublicIP: true,
        mode: "System",
        name: "nodepool1",
        osType: "Linux",
        type: "VirtualMachineScaleSets",
        vmSize: "Standard_DS2_v2",
    }],
    autoScalerProfile: {
        scaleDownDelayAfterAdd: "15m",
        scanInterval: "20s",
    },
    diskEncryptionSetID: "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
    dnsPrefix: "dnsprefix1",
    enablePodSecurityPolicy: true,
    enableRBAC: true,
    httpProxyConfig: {
        httpProxy: "http://myproxy.server.com:8080",
        httpsProxy: "https://myproxy.server.com:8080",
        noProxy: [
            "localhost",
            "127.0.0.1",
        ],
        trustedCa: "Q29uZ3JhdHMhIFlvdSBoYXZlIGZvdW5kIGEgaGlkZGVuIG1lc3NhZ2U=",
    },
    kubernetesVersion: "",
    linuxProfile: {
        adminUsername: "azureuser",
        ssh: {
            publicKeys: [{
                keyData: "keydata",
            }],
        },
    },
    location: "location1",
    networkProfile: {
        loadBalancerProfile: {
            managedOutboundIPs: {
                count: 2,
            },
        },
        loadBalancerSku: "standard",
        outboundType: "loadBalancer",
    },
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    servicePrincipalProfile: {
        clientId: "clientid",
        secret: "secret",
    },
    sku: {
        name: "Basic",
        tier: "Free",
    },
    tags: {
        archv2: "",
        tier: "production",
    },
    windowsProfile: {
        adminPassword: "replacePassword1234$",
        adminUsername: "azureuser",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_cluster = azure_native.containerservice.ManagedCluster("managedCluster",
    addon_profiles={},
    agent_pool_profiles=[azure_native.containerservice.ManagedClusterAgentPoolProfileArgs(
        count=3,
        enable_node_public_ip=True,
        mode="System",
        name="nodepool1",
        os_type="Linux",
        type="VirtualMachineScaleSets",
        vm_size="Standard_DS2_v2",
    )],
    auto_scaler_profile=azure_native.containerservice.ManagedClusterPropertiesAutoScalerProfileArgs(
        scale_down_delay_after_add="15m",
        scan_interval="20s",
    ),
    disk_encryption_set_id="/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
    dns_prefix="dnsprefix1",
    enable_pod_security_policy=True,
    enable_rbac=True,
    http_proxy_config=azure_native.containerservice.ManagedClusterHTTPProxyConfigArgs(
        http_proxy="http://myproxy.server.com:8080",
        https_proxy="https://myproxy.server.com:8080",
        no_proxy=[
            "localhost",
            "127.0.0.1",
        ],
        trusted_ca="Q29uZ3JhdHMhIFlvdSBoYXZlIGZvdW5kIGEgaGlkZGVuIG1lc3NhZ2U=",
    ),
    kubernetes_version="",
    linux_profile=azure_native.containerservice.ContainerServiceLinuxProfileResponseArgs(
        admin_username="azureuser",
        ssh={
            "publicKeys": [azure_native.containerservice.ContainerServiceSshPublicKeyArgs(
                key_data="keydata",
            )],
        },
    ),
    location="location1",
    network_profile=azure_native.containerservice.ContainerServiceNetworkProfileResponseArgs(
        load_balancer_profile={
            "managedOutboundIPs": azure_native.containerservice.ManagedClusterLoadBalancerProfileManagedOutboundIPsArgs(
                count=2,
            ),
        },
        load_balancer_sku="standard",
        outbound_type="loadBalancer",
    ),
    resource_group_name="rg1",
    resource_name_="clustername1",
    service_principal_profile=azure_native.containerservice.ManagedClusterServicePrincipalProfileArgs(
        client_id="clientid",
        secret="secret",
    ),
    sku=azure_native.containerservice.ManagedClusterSKUArgs(
        name="Basic",
        tier="Free",
    ),
    tags={
        "archv2": "",
        "tier": "production",
    },
    windows_profile=azure_native.containerservice.ManagedClusterWindowsProfileArgs(
        admin_password="replacePassword1234$",
        admin_username="azureuser",
    ))

```

```yaml
resources:
  managedCluster:
    type: azure-native:containerservice:ManagedCluster
    properties:
      addonProfiles: {}
      agentPoolProfiles:
        - count: 3
          enableNodePublicIP: true
          mode: System
          name: nodepool1
          osType: Linux
          type: VirtualMachineScaleSets
          vmSize: Standard_DS2_v2
      autoScalerProfile:
        scaleDownDelayAfterAdd: 15m
        scanInterval: 20s
      diskEncryptionSetID: /subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des
      dnsPrefix: dnsprefix1
      enablePodSecurityPolicy: true
      enableRBAC: true
      httpProxyConfig:
        httpProxy: http://myproxy.server.com:8080
        httpsProxy: https://myproxy.server.com:8080
        noProxy:
          - localhost
          - 127.0.0.1
        trustedCa: Q29uZ3JhdHMhIFlvdSBoYXZlIGZvdW5kIGEgaGlkZGVuIG1lc3NhZ2U=
      kubernetesVersion:
      linuxProfile:
        adminUsername: azureuser
        ssh:
          publicKeys:
            - keyData: keydata
      location: location1
      networkProfile:
        loadBalancerProfile:
          managedOutboundIPs:
            count: 2
        loadBalancerSku: standard
        outboundType: loadBalancer
      resourceGroupName: rg1
      resourceName: clustername1
      servicePrincipalProfile:
        clientId: clientid
        secret: secret
      sku:
        name: Basic
        tier: Free
      tags:
        archv2:
        tier: production
      windowsProfile:
        adminPassword: replacePassword1234$
        adminUsername: azureuser

```

{{% /example %}}
{{% example %}}
### Create Managed Cluster with Node Public IP Prefix
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedCluster = new AzureNative.ContainerService.ManagedCluster("managedCluster", new()
    {
        AddonProfiles = null,
        AgentPoolProfiles = new[]
        {
            new AzureNative.ContainerService.Inputs.ManagedClusterAgentPoolProfileArgs
            {
                Count = 3,
                EnableNodePublicIP = true,
                Mode = "System",
                Name = "nodepool1",
                NodePublicIPPrefixID = "/subscriptions/subid1/resourcegroups/rg1/providers/Microsoft.Network/publicIPPrefixes/public-ip-prefix",
                OsType = "Linux",
                Type = "VirtualMachineScaleSets",
                VmSize = "Standard_DS2_v2",
            },
        },
        AutoScalerProfile = new AzureNative.ContainerService.Inputs.ManagedClusterPropertiesAutoScalerProfileArgs
        {
            ScaleDownDelayAfterAdd = "15m",
            ScanInterval = "20s",
        },
        DiskEncryptionSetID = "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
        DnsPrefix = "dnsprefix1",
        EnablePodSecurityPolicy = true,
        EnableRBAC = true,
        KubernetesVersion = "",
        LinuxProfile = new AzureNative.ContainerService.Inputs.ContainerServiceLinuxProfileArgs
        {
            AdminUsername = "azureuser",
            Ssh = new AzureNative.ContainerService.Inputs.ContainerServiceSshConfigurationArgs
            {
                PublicKeys = new[]
                {
                    new AzureNative.ContainerService.Inputs.ContainerServiceSshPublicKeyArgs
                    {
                        KeyData = "keydata",
                    },
                },
            },
        },
        Location = "location1",
        NetworkProfile = new AzureNative.ContainerService.Inputs.ContainerServiceNetworkProfileArgs
        {
            LoadBalancerProfile = new AzureNative.ContainerService.Inputs.ManagedClusterLoadBalancerProfileArgs
            {
                ManagedOutboundIPs = new AzureNative.ContainerService.Inputs.ManagedClusterLoadBalancerProfileManagedOutboundIPsArgs
                {
                    Count = 2,
                },
            },
            LoadBalancerSku = "standard",
            OutboundType = "loadBalancer",
        },
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        ServicePrincipalProfile = new AzureNative.ContainerService.Inputs.ManagedClusterServicePrincipalProfileArgs
        {
            ClientId = "clientid",
            Secret = "secret",
        },
        Sku = new AzureNative.ContainerService.Inputs.ManagedClusterSKUArgs
        {
            Name = "Basic",
            Tier = "Free",
        },
        Tags = 
        {
            { "archv2", "" },
            { "tier", "production" },
        },
        WindowsProfile = new AzureNative.ContainerService.Inputs.ManagedClusterWindowsProfileArgs
        {
            AdminPassword = "replacePassword1234$",
            AdminUsername = "azureuser",
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.containerservice.ManagedCluster;
import com.pulumi.azurenative.containerservice.ManagedClusterArgs;
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
        var managedCluster = new ManagedCluster("managedCluster", ManagedClusterArgs.builder()        
            .addonProfiles()
            .agentPoolProfiles(Map.ofEntries(
                Map.entry("count", 3),
                Map.entry("enableNodePublicIP", true),
                Map.entry("mode", "System"),
                Map.entry("name", "nodepool1"),
                Map.entry("nodePublicIPPrefixID", "/subscriptions/subid1/resourcegroups/rg1/providers/Microsoft.Network/publicIPPrefixes/public-ip-prefix"),
                Map.entry("osType", "Linux"),
                Map.entry("type", "VirtualMachineScaleSets"),
                Map.entry("vmSize", "Standard_DS2_v2")
            ))
            .autoScalerProfile(Map.ofEntries(
                Map.entry("scaleDownDelayAfterAdd", "15m"),
                Map.entry("scanInterval", "20s")
            ))
            .diskEncryptionSetID("/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des")
            .dnsPrefix("dnsprefix1")
            .enablePodSecurityPolicy(true)
            .enableRBAC(true)
            .kubernetesVersion("")
            .linuxProfile(Map.ofEntries(
                Map.entry("adminUsername", "azureuser"),
                Map.entry("ssh", Map.of("publicKeys", Map.of("keyData", "keydata")))
            ))
            .location("location1")
            .networkProfile(Map.ofEntries(
                Map.entry("loadBalancerProfile", Map.of("managedOutboundIPs", Map.of("count", 2))),
                Map.entry("loadBalancerSku", "standard"),
                Map.entry("outboundType", "loadBalancer")
            ))
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .servicePrincipalProfile(Map.ofEntries(
                Map.entry("clientId", "clientid"),
                Map.entry("secret", "secret")
            ))
            .sku(Map.ofEntries(
                Map.entry("name", "Basic"),
                Map.entry("tier", "Free")
            ))
            .tags(Map.ofEntries(
                Map.entry("archv2", ""),
                Map.entry("tier", "production")
            ))
            .windowsProfile(Map.ofEntries(
                Map.entry("adminPassword", "replacePassword1234$"),
                Map.entry("adminUsername", "azureuser")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedCluster = new azure_native.containerservice.ManagedCluster("managedCluster", {
    addonProfiles: {},
    agentPoolProfiles: [{
        count: 3,
        enableNodePublicIP: true,
        mode: "System",
        name: "nodepool1",
        nodePublicIPPrefixID: "/subscriptions/subid1/resourcegroups/rg1/providers/Microsoft.Network/publicIPPrefixes/public-ip-prefix",
        osType: "Linux",
        type: "VirtualMachineScaleSets",
        vmSize: "Standard_DS2_v2",
    }],
    autoScalerProfile: {
        scaleDownDelayAfterAdd: "15m",
        scanInterval: "20s",
    },
    diskEncryptionSetID: "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
    dnsPrefix: "dnsprefix1",
    enablePodSecurityPolicy: true,
    enableRBAC: true,
    kubernetesVersion: "",
    linuxProfile: {
        adminUsername: "azureuser",
        ssh: {
            publicKeys: [{
                keyData: "keydata",
            }],
        },
    },
    location: "location1",
    networkProfile: {
        loadBalancerProfile: {
            managedOutboundIPs: {
                count: 2,
            },
        },
        loadBalancerSku: "standard",
        outboundType: "loadBalancer",
    },
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    servicePrincipalProfile: {
        clientId: "clientid",
        secret: "secret",
    },
    sku: {
        name: "Basic",
        tier: "Free",
    },
    tags: {
        archv2: "",
        tier: "production",
    },
    windowsProfile: {
        adminPassword: "replacePassword1234$",
        adminUsername: "azureuser",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_cluster = azure_native.containerservice.ManagedCluster("managedCluster",
    addon_profiles={},
    agent_pool_profiles=[azure_native.containerservice.ManagedClusterAgentPoolProfileArgs(
        count=3,
        enable_node_public_ip=True,
        mode="System",
        name="nodepool1",
        node_public_ip_prefix_id="/subscriptions/subid1/resourcegroups/rg1/providers/Microsoft.Network/publicIPPrefixes/public-ip-prefix",
        os_type="Linux",
        type="VirtualMachineScaleSets",
        vm_size="Standard_DS2_v2",
    )],
    auto_scaler_profile=azure_native.containerservice.ManagedClusterPropertiesAutoScalerProfileArgs(
        scale_down_delay_after_add="15m",
        scan_interval="20s",
    ),
    disk_encryption_set_id="/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
    dns_prefix="dnsprefix1",
    enable_pod_security_policy=True,
    enable_rbac=True,
    kubernetes_version="",
    linux_profile=azure_native.containerservice.ContainerServiceLinuxProfileResponseArgs(
        admin_username="azureuser",
        ssh={
            "publicKeys": [azure_native.containerservice.ContainerServiceSshPublicKeyArgs(
                key_data="keydata",
            )],
        },
    ),
    location="location1",
    network_profile=azure_native.containerservice.ContainerServiceNetworkProfileResponseArgs(
        load_balancer_profile={
            "managedOutboundIPs": azure_native.containerservice.ManagedClusterLoadBalancerProfileManagedOutboundIPsArgs(
                count=2,
            ),
        },
        load_balancer_sku="standard",
        outbound_type="loadBalancer",
    ),
    resource_group_name="rg1",
    resource_name_="clustername1",
    service_principal_profile=azure_native.containerservice.ManagedClusterServicePrincipalProfileArgs(
        client_id="clientid",
        secret="secret",
    ),
    sku=azure_native.containerservice.ManagedClusterSKUArgs(
        name="Basic",
        tier="Free",
    ),
    tags={
        "archv2": "",
        "tier": "production",
    },
    windows_profile=azure_native.containerservice.ManagedClusterWindowsProfileArgs(
        admin_password="replacePassword1234$",
        admin_username="azureuser",
    ))

```

```yaml
resources:
  managedCluster:
    type: azure-native:containerservice:ManagedCluster
    properties:
      addonProfiles: {}
      agentPoolProfiles:
        - count: 3
          enableNodePublicIP: true
          mode: System
          name: nodepool1
          nodePublicIPPrefixID: /subscriptions/subid1/resourcegroups/rg1/providers/Microsoft.Network/publicIPPrefixes/public-ip-prefix
          osType: Linux
          type: VirtualMachineScaleSets
          vmSize: Standard_DS2_v2
      autoScalerProfile:
        scaleDownDelayAfterAdd: 15m
        scanInterval: 20s
      diskEncryptionSetID: /subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des
      dnsPrefix: dnsprefix1
      enablePodSecurityPolicy: true
      enableRBAC: true
      kubernetesVersion:
      linuxProfile:
        adminUsername: azureuser
        ssh:
          publicKeys:
            - keyData: keydata
      location: location1
      networkProfile:
        loadBalancerProfile:
          managedOutboundIPs:
            count: 2
        loadBalancerSku: standard
        outboundType: loadBalancer
      resourceGroupName: rg1
      resourceName: clustername1
      servicePrincipalProfile:
        clientId: clientid
        secret: secret
      sku:
        name: Basic
        tier: Free
      tags:
        archv2:
        tier: production
      windowsProfile:
        adminPassword: replacePassword1234$
        adminUsername: azureuser

```

{{% /example %}}
{{% example %}}
### Create Managed Cluster with OSSKU
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedCluster = new AzureNative.ContainerService.ManagedCluster("managedCluster", new()
    {
        AddonProfiles = null,
        AgentPoolProfiles = new[]
        {
            new AzureNative.ContainerService.Inputs.ManagedClusterAgentPoolProfileArgs
            {
                Count = 3,
                EnableNodePublicIP = true,
                Mode = "System",
                Name = "nodepool1",
                OsSKU = "CBLMariner",
                OsType = "Linux",
                Type = "VirtualMachineScaleSets",
                VmSize = "Standard_DS2_v2",
            },
        },
        AutoScalerProfile = new AzureNative.ContainerService.Inputs.ManagedClusterPropertiesAutoScalerProfileArgs
        {
            ScaleDownDelayAfterAdd = "15m",
            ScanInterval = "20s",
        },
        DiskEncryptionSetID = "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
        DnsPrefix = "dnsprefix1",
        EnablePodSecurityPolicy = true,
        EnableRBAC = true,
        HttpProxyConfig = new AzureNative.ContainerService.Inputs.ManagedClusterHTTPProxyConfigArgs
        {
            HttpProxy = "http://myproxy.server.com:8080",
            HttpsProxy = "https://myproxy.server.com:8080",
            NoProxy = new[]
            {
                "localhost",
                "127.0.0.1",
            },
            TrustedCa = "Q29uZ3JhdHMhIFlvdSBoYXZlIGZvdW5kIGEgaGlkZGVuIG1lc3NhZ2U=",
        },
        KubernetesVersion = "",
        LinuxProfile = new AzureNative.ContainerService.Inputs.ContainerServiceLinuxProfileArgs
        {
            AdminUsername = "azureuser",
            Ssh = new AzureNative.ContainerService.Inputs.ContainerServiceSshConfigurationArgs
            {
                PublicKeys = new[]
                {
                    new AzureNative.ContainerService.Inputs.ContainerServiceSshPublicKeyArgs
                    {
                        KeyData = "keydata",
                    },
                },
            },
        },
        Location = "location1",
        NetworkProfile = new AzureNative.ContainerService.Inputs.ContainerServiceNetworkProfileArgs
        {
            LoadBalancerProfile = new AzureNative.ContainerService.Inputs.ManagedClusterLoadBalancerProfileArgs
            {
                ManagedOutboundIPs = new AzureNative.ContainerService.Inputs.ManagedClusterLoadBalancerProfileManagedOutboundIPsArgs
                {
                    Count = 2,
                },
            },
            LoadBalancerSku = "standard",
            OutboundType = "loadBalancer",
        },
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        ServicePrincipalProfile = new AzureNative.ContainerService.Inputs.ManagedClusterServicePrincipalProfileArgs
        {
            ClientId = "clientid",
            Secret = "secret",
        },
        Sku = new AzureNative.ContainerService.Inputs.ManagedClusterSKUArgs
        {
            Name = "Basic",
            Tier = "Free",
        },
        Tags = 
        {
            { "archv2", "" },
            { "tier", "production" },
        },
        WindowsProfile = new AzureNative.ContainerService.Inputs.ManagedClusterWindowsProfileArgs
        {
            AdminPassword = "replacePassword1234$",
            AdminUsername = "azureuser",
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.containerservice.ManagedCluster;
import com.pulumi.azurenative.containerservice.ManagedClusterArgs;
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
        var managedCluster = new ManagedCluster("managedCluster", ManagedClusterArgs.builder()        
            .addonProfiles()
            .agentPoolProfiles(Map.ofEntries(
                Map.entry("count", 3),
                Map.entry("enableNodePublicIP", true),
                Map.entry("mode", "System"),
                Map.entry("name", "nodepool1"),
                Map.entry("osSKU", "CBLMariner"),
                Map.entry("osType", "Linux"),
                Map.entry("type", "VirtualMachineScaleSets"),
                Map.entry("vmSize", "Standard_DS2_v2")
            ))
            .autoScalerProfile(Map.ofEntries(
                Map.entry("scaleDownDelayAfterAdd", "15m"),
                Map.entry("scanInterval", "20s")
            ))
            .diskEncryptionSetID("/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des")
            .dnsPrefix("dnsprefix1")
            .enablePodSecurityPolicy(true)
            .enableRBAC(true)
            .httpProxyConfig(Map.ofEntries(
                Map.entry("httpProxy", "http://myproxy.server.com:8080"),
                Map.entry("httpsProxy", "https://myproxy.server.com:8080"),
                Map.entry("noProxy",                 
                    "localhost",
                    "127.0.0.1"),
                Map.entry("trustedCa", "Q29uZ3JhdHMhIFlvdSBoYXZlIGZvdW5kIGEgaGlkZGVuIG1lc3NhZ2U=")
            ))
            .kubernetesVersion("")
            .linuxProfile(Map.ofEntries(
                Map.entry("adminUsername", "azureuser"),
                Map.entry("ssh", Map.of("publicKeys", Map.of("keyData", "keydata")))
            ))
            .location("location1")
            .networkProfile(Map.ofEntries(
                Map.entry("loadBalancerProfile", Map.of("managedOutboundIPs", Map.of("count", 2))),
                Map.entry("loadBalancerSku", "standard"),
                Map.entry("outboundType", "loadBalancer")
            ))
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .servicePrincipalProfile(Map.ofEntries(
                Map.entry("clientId", "clientid"),
                Map.entry("secret", "secret")
            ))
            .sku(Map.ofEntries(
                Map.entry("name", "Basic"),
                Map.entry("tier", "Free")
            ))
            .tags(Map.ofEntries(
                Map.entry("archv2", ""),
                Map.entry("tier", "production")
            ))
            .windowsProfile(Map.ofEntries(
                Map.entry("adminPassword", "replacePassword1234$"),
                Map.entry("adminUsername", "azureuser")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedCluster = new azure_native.containerservice.ManagedCluster("managedCluster", {
    addonProfiles: {},
    agentPoolProfiles: [{
        count: 3,
        enableNodePublicIP: true,
        mode: "System",
        name: "nodepool1",
        osSKU: "CBLMariner",
        osType: "Linux",
        type: "VirtualMachineScaleSets",
        vmSize: "Standard_DS2_v2",
    }],
    autoScalerProfile: {
        scaleDownDelayAfterAdd: "15m",
        scanInterval: "20s",
    },
    diskEncryptionSetID: "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
    dnsPrefix: "dnsprefix1",
    enablePodSecurityPolicy: true,
    enableRBAC: true,
    httpProxyConfig: {
        httpProxy: "http://myproxy.server.com:8080",
        httpsProxy: "https://myproxy.server.com:8080",
        noProxy: [
            "localhost",
            "127.0.0.1",
        ],
        trustedCa: "Q29uZ3JhdHMhIFlvdSBoYXZlIGZvdW5kIGEgaGlkZGVuIG1lc3NhZ2U=",
    },
    kubernetesVersion: "",
    linuxProfile: {
        adminUsername: "azureuser",
        ssh: {
            publicKeys: [{
                keyData: "keydata",
            }],
        },
    },
    location: "location1",
    networkProfile: {
        loadBalancerProfile: {
            managedOutboundIPs: {
                count: 2,
            },
        },
        loadBalancerSku: "standard",
        outboundType: "loadBalancer",
    },
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    servicePrincipalProfile: {
        clientId: "clientid",
        secret: "secret",
    },
    sku: {
        name: "Basic",
        tier: "Free",
    },
    tags: {
        archv2: "",
        tier: "production",
    },
    windowsProfile: {
        adminPassword: "replacePassword1234$",
        adminUsername: "azureuser",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_cluster = azure_native.containerservice.ManagedCluster("managedCluster",
    addon_profiles={},
    agent_pool_profiles=[azure_native.containerservice.ManagedClusterAgentPoolProfileArgs(
        count=3,
        enable_node_public_ip=True,
        mode="System",
        name="nodepool1",
        os_sku="CBLMariner",
        os_type="Linux",
        type="VirtualMachineScaleSets",
        vm_size="Standard_DS2_v2",
    )],
    auto_scaler_profile=azure_native.containerservice.ManagedClusterPropertiesAutoScalerProfileArgs(
        scale_down_delay_after_add="15m",
        scan_interval="20s",
    ),
    disk_encryption_set_id="/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
    dns_prefix="dnsprefix1",
    enable_pod_security_policy=True,
    enable_rbac=True,
    http_proxy_config=azure_native.containerservice.ManagedClusterHTTPProxyConfigArgs(
        http_proxy="http://myproxy.server.com:8080",
        https_proxy="https://myproxy.server.com:8080",
        no_proxy=[
            "localhost",
            "127.0.0.1",
        ],
        trusted_ca="Q29uZ3JhdHMhIFlvdSBoYXZlIGZvdW5kIGEgaGlkZGVuIG1lc3NhZ2U=",
    ),
    kubernetes_version="",
    linux_profile=azure_native.containerservice.ContainerServiceLinuxProfileResponseArgs(
        admin_username="azureuser",
        ssh={
            "publicKeys": [azure_native.containerservice.ContainerServiceSshPublicKeyArgs(
                key_data="keydata",
            )],
        },
    ),
    location="location1",
    network_profile=azure_native.containerservice.ContainerServiceNetworkProfileResponseArgs(
        load_balancer_profile={
            "managedOutboundIPs": azure_native.containerservice.ManagedClusterLoadBalancerProfileManagedOutboundIPsArgs(
                count=2,
            ),
        },
        load_balancer_sku="standard",
        outbound_type="loadBalancer",
    ),
    resource_group_name="rg1",
    resource_name_="clustername1",
    service_principal_profile=azure_native.containerservice.ManagedClusterServicePrincipalProfileArgs(
        client_id="clientid",
        secret="secret",
    ),
    sku=azure_native.containerservice.ManagedClusterSKUArgs(
        name="Basic",
        tier="Free",
    ),
    tags={
        "archv2": "",
        "tier": "production",
    },
    windows_profile=azure_native.containerservice.ManagedClusterWindowsProfileArgs(
        admin_password="replacePassword1234$",
        admin_username="azureuser",
    ))

```

```yaml
resources:
  managedCluster:
    type: azure-native:containerservice:ManagedCluster
    properties:
      addonProfiles: {}
      agentPoolProfiles:
        - count: 3
          enableNodePublicIP: true
          mode: System
          name: nodepool1
          osSKU: CBLMariner
          osType: Linux
          type: VirtualMachineScaleSets
          vmSize: Standard_DS2_v2
      autoScalerProfile:
        scaleDownDelayAfterAdd: 15m
        scanInterval: 20s
      diskEncryptionSetID: /subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des
      dnsPrefix: dnsprefix1
      enablePodSecurityPolicy: true
      enableRBAC: true
      httpProxyConfig:
        httpProxy: http://myproxy.server.com:8080
        httpsProxy: https://myproxy.server.com:8080
        noProxy:
          - localhost
          - 127.0.0.1
        trustedCa: Q29uZ3JhdHMhIFlvdSBoYXZlIGZvdW5kIGEgaGlkZGVuIG1lc3NhZ2U=
      kubernetesVersion:
      linuxProfile:
        adminUsername: azureuser
        ssh:
          publicKeys:
            - keyData: keydata
      location: location1
      networkProfile:
        loadBalancerProfile:
          managedOutboundIPs:
            count: 2
        loadBalancerSku: standard
        outboundType: loadBalancer
      resourceGroupName: rg1
      resourceName: clustername1
      servicePrincipalProfile:
        clientId: clientid
        secret: secret
      sku:
        name: Basic
        tier: Free
      tags:
        archv2:
        tier: production
      windowsProfile:
        adminPassword: replacePassword1234$
        adminUsername: azureuser

```

{{% /example %}}
{{% example %}}
### Create Managed Cluster with PPG
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedCluster = new AzureNative.ContainerService.ManagedCluster("managedCluster", new()
    {
        AddonProfiles = null,
        AgentPoolProfiles = new[]
        {
            new AzureNative.ContainerService.Inputs.ManagedClusterAgentPoolProfileArgs
            {
                Count = 3,
                EnableNodePublicIP = true,
                Mode = "System",
                Name = "nodepool1",
                OsType = "Linux",
                ProximityPlacementGroupID = "/subscriptions/subid1/resourcegroups/rg1/providers/Microsoft.Compute/proximityPlacementGroups/ppg1",
                Type = "VirtualMachineScaleSets",
                VmSize = "Standard_DS2_v2",
            },
        },
        AutoScalerProfile = new AzureNative.ContainerService.Inputs.ManagedClusterPropertiesAutoScalerProfileArgs
        {
            ScaleDownDelayAfterAdd = "15m",
            ScanInterval = "20s",
        },
        DiskEncryptionSetID = "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
        DnsPrefix = "dnsprefix1",
        EnablePodSecurityPolicy = true,
        EnableRBAC = true,
        KubernetesVersion = "",
        LinuxProfile = new AzureNative.ContainerService.Inputs.ContainerServiceLinuxProfileArgs
        {
            AdminUsername = "azureuser",
            Ssh = new AzureNative.ContainerService.Inputs.ContainerServiceSshConfigurationArgs
            {
                PublicKeys = new[]
                {
                    new AzureNative.ContainerService.Inputs.ContainerServiceSshPublicKeyArgs
                    {
                        KeyData = "keydata",
                    },
                },
            },
        },
        Location = "location1",
        NetworkProfile = new AzureNative.ContainerService.Inputs.ContainerServiceNetworkProfileArgs
        {
            LoadBalancerProfile = new AzureNative.ContainerService.Inputs.ManagedClusterLoadBalancerProfileArgs
            {
                ManagedOutboundIPs = new AzureNative.ContainerService.Inputs.ManagedClusterLoadBalancerProfileManagedOutboundIPsArgs
                {
                    Count = 2,
                },
            },
            LoadBalancerSku = "standard",
            OutboundType = "loadBalancer",
        },
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        ServicePrincipalProfile = new AzureNative.ContainerService.Inputs.ManagedClusterServicePrincipalProfileArgs
        {
            ClientId = "clientid",
            Secret = "secret",
        },
        Sku = new AzureNative.ContainerService.Inputs.ManagedClusterSKUArgs
        {
            Name = "Basic",
            Tier = "Free",
        },
        Tags = 
        {
            { "archv2", "" },
            { "tier", "production" },
        },
        WindowsProfile = new AzureNative.ContainerService.Inputs.ManagedClusterWindowsProfileArgs
        {
            AdminPassword = "replacePassword1234$",
            AdminUsername = "azureuser",
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.containerservice.ManagedCluster;
import com.pulumi.azurenative.containerservice.ManagedClusterArgs;
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
        var managedCluster = new ManagedCluster("managedCluster", ManagedClusterArgs.builder()        
            .addonProfiles()
            .agentPoolProfiles(Map.ofEntries(
                Map.entry("count", 3),
                Map.entry("enableNodePublicIP", true),
                Map.entry("mode", "System"),
                Map.entry("name", "nodepool1"),
                Map.entry("osType", "Linux"),
                Map.entry("proximityPlacementGroupID", "/subscriptions/subid1/resourcegroups/rg1/providers/Microsoft.Compute/proximityPlacementGroups/ppg1"),
                Map.entry("type", "VirtualMachineScaleSets"),
                Map.entry("vmSize", "Standard_DS2_v2")
            ))
            .autoScalerProfile(Map.ofEntries(
                Map.entry("scaleDownDelayAfterAdd", "15m"),
                Map.entry("scanInterval", "20s")
            ))
            .diskEncryptionSetID("/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des")
            .dnsPrefix("dnsprefix1")
            .enablePodSecurityPolicy(true)
            .enableRBAC(true)
            .kubernetesVersion("")
            .linuxProfile(Map.ofEntries(
                Map.entry("adminUsername", "azureuser"),
                Map.entry("ssh", Map.of("publicKeys", Map.of("keyData", "keydata")))
            ))
            .location("location1")
            .networkProfile(Map.ofEntries(
                Map.entry("loadBalancerProfile", Map.of("managedOutboundIPs", Map.of("count", 2))),
                Map.entry("loadBalancerSku", "standard"),
                Map.entry("outboundType", "loadBalancer")
            ))
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .servicePrincipalProfile(Map.ofEntries(
                Map.entry("clientId", "clientid"),
                Map.entry("secret", "secret")
            ))
            .sku(Map.ofEntries(
                Map.entry("name", "Basic"),
                Map.entry("tier", "Free")
            ))
            .tags(Map.ofEntries(
                Map.entry("archv2", ""),
                Map.entry("tier", "production")
            ))
            .windowsProfile(Map.ofEntries(
                Map.entry("adminPassword", "replacePassword1234$"),
                Map.entry("adminUsername", "azureuser")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedCluster = new azure_native.containerservice.ManagedCluster("managedCluster", {
    addonProfiles: {},
    agentPoolProfiles: [{
        count: 3,
        enableNodePublicIP: true,
        mode: "System",
        name: "nodepool1",
        osType: "Linux",
        proximityPlacementGroupID: "/subscriptions/subid1/resourcegroups/rg1/providers/Microsoft.Compute/proximityPlacementGroups/ppg1",
        type: "VirtualMachineScaleSets",
        vmSize: "Standard_DS2_v2",
    }],
    autoScalerProfile: {
        scaleDownDelayAfterAdd: "15m",
        scanInterval: "20s",
    },
    diskEncryptionSetID: "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
    dnsPrefix: "dnsprefix1",
    enablePodSecurityPolicy: true,
    enableRBAC: true,
    kubernetesVersion: "",
    linuxProfile: {
        adminUsername: "azureuser",
        ssh: {
            publicKeys: [{
                keyData: "keydata",
            }],
        },
    },
    location: "location1",
    networkProfile: {
        loadBalancerProfile: {
            managedOutboundIPs: {
                count: 2,
            },
        },
        loadBalancerSku: "standard",
        outboundType: "loadBalancer",
    },
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    servicePrincipalProfile: {
        clientId: "clientid",
        secret: "secret",
    },
    sku: {
        name: "Basic",
        tier: "Free",
    },
    tags: {
        archv2: "",
        tier: "production",
    },
    windowsProfile: {
        adminPassword: "replacePassword1234$",
        adminUsername: "azureuser",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_cluster = azure_native.containerservice.ManagedCluster("managedCluster",
    addon_profiles={},
    agent_pool_profiles=[azure_native.containerservice.ManagedClusterAgentPoolProfileArgs(
        count=3,
        enable_node_public_ip=True,
        mode="System",
        name="nodepool1",
        os_type="Linux",
        proximity_placement_group_id="/subscriptions/subid1/resourcegroups/rg1/providers/Microsoft.Compute/proximityPlacementGroups/ppg1",
        type="VirtualMachineScaleSets",
        vm_size="Standard_DS2_v2",
    )],
    auto_scaler_profile=azure_native.containerservice.ManagedClusterPropertiesAutoScalerProfileArgs(
        scale_down_delay_after_add="15m",
        scan_interval="20s",
    ),
    disk_encryption_set_id="/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
    dns_prefix="dnsprefix1",
    enable_pod_security_policy=True,
    enable_rbac=True,
    kubernetes_version="",
    linux_profile=azure_native.containerservice.ContainerServiceLinuxProfileResponseArgs(
        admin_username="azureuser",
        ssh={
            "publicKeys": [azure_native.containerservice.ContainerServiceSshPublicKeyArgs(
                key_data="keydata",
            )],
        },
    ),
    location="location1",
    network_profile=azure_native.containerservice.ContainerServiceNetworkProfileResponseArgs(
        load_balancer_profile={
            "managedOutboundIPs": azure_native.containerservice.ManagedClusterLoadBalancerProfileManagedOutboundIPsArgs(
                count=2,
            ),
        },
        load_balancer_sku="standard",
        outbound_type="loadBalancer",
    ),
    resource_group_name="rg1",
    resource_name_="clustername1",
    service_principal_profile=azure_native.containerservice.ManagedClusterServicePrincipalProfileArgs(
        client_id="clientid",
        secret="secret",
    ),
    sku=azure_native.containerservice.ManagedClusterSKUArgs(
        name="Basic",
        tier="Free",
    ),
    tags={
        "archv2": "",
        "tier": "production",
    },
    windows_profile=azure_native.containerservice.ManagedClusterWindowsProfileArgs(
        admin_password="replacePassword1234$",
        admin_username="azureuser",
    ))

```

```yaml
resources:
  managedCluster:
    type: azure-native:containerservice:ManagedCluster
    properties:
      addonProfiles: {}
      agentPoolProfiles:
        - count: 3
          enableNodePublicIP: true
          mode: System
          name: nodepool1
          osType: Linux
          proximityPlacementGroupID: /subscriptions/subid1/resourcegroups/rg1/providers/Microsoft.Compute/proximityPlacementGroups/ppg1
          type: VirtualMachineScaleSets
          vmSize: Standard_DS2_v2
      autoScalerProfile:
        scaleDownDelayAfterAdd: 15m
        scanInterval: 20s
      diskEncryptionSetID: /subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des
      dnsPrefix: dnsprefix1
      enablePodSecurityPolicy: true
      enableRBAC: true
      kubernetesVersion:
      linuxProfile:
        adminUsername: azureuser
        ssh:
          publicKeys:
            - keyData: keydata
      location: location1
      networkProfile:
        loadBalancerProfile:
          managedOutboundIPs:
            count: 2
        loadBalancerSku: standard
        outboundType: loadBalancer
      resourceGroupName: rg1
      resourceName: clustername1
      servicePrincipalProfile:
        clientId: clientid
        secret: secret
      sku:
        name: Basic
        tier: Free
      tags:
        archv2:
        tier: production
      windowsProfile:
        adminPassword: replacePassword1234$
        adminUsername: azureuser

```

{{% /example %}}
{{% example %}}
### Create Managed Cluster with PodIdentity enabled
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedCluster = new AzureNative.ContainerService.ManagedCluster("managedCluster", new()
    {
        AddonProfiles = null,
        AgentPoolProfiles = new[]
        {
            new AzureNative.ContainerService.Inputs.ManagedClusterAgentPoolProfileArgs
            {
                Count = 3,
                EnableNodePublicIP = true,
                Mode = "System",
                Name = "nodepool1",
                OsType = "Linux",
                Type = "VirtualMachineScaleSets",
                VmSize = "Standard_DS2_v2",
            },
        },
        AutoScalerProfile = new AzureNative.ContainerService.Inputs.ManagedClusterPropertiesAutoScalerProfileArgs
        {
            ScaleDownDelayAfterAdd = "15m",
            ScanInterval = "20s",
        },
        DiskEncryptionSetID = "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
        DnsPrefix = "dnsprefix1",
        EnablePodSecurityPolicy = true,
        EnableRBAC = true,
        KubernetesVersion = "",
        LinuxProfile = new AzureNative.ContainerService.Inputs.ContainerServiceLinuxProfileArgs
        {
            AdminUsername = "azureuser",
            Ssh = new AzureNative.ContainerService.Inputs.ContainerServiceSshConfigurationArgs
            {
                PublicKeys = new[]
                {
                    new AzureNative.ContainerService.Inputs.ContainerServiceSshPublicKeyArgs
                    {
                        KeyData = "keydata",
                    },
                },
            },
        },
        Location = "location1",
        NetworkProfile = new AzureNative.ContainerService.Inputs.ContainerServiceNetworkProfileArgs
        {
            LoadBalancerProfile = new AzureNative.ContainerService.Inputs.ManagedClusterLoadBalancerProfileArgs
            {
                ManagedOutboundIPs = new AzureNative.ContainerService.Inputs.ManagedClusterLoadBalancerProfileManagedOutboundIPsArgs
                {
                    Count = 2,
                },
            },
            LoadBalancerSku = "standard",
            OutboundType = "loadBalancer",
        },
        PodIdentityProfile = new AzureNative.ContainerService.Inputs.ManagedClusterPodIdentityProfileArgs
        {
            AllowNetworkPluginKubenet = true,
            Enabled = true,
        },
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        ServicePrincipalProfile = new AzureNative.ContainerService.Inputs.ManagedClusterServicePrincipalProfileArgs
        {
            ClientId = "clientid",
            Secret = "secret",
        },
        Sku = new AzureNative.ContainerService.Inputs.ManagedClusterSKUArgs
        {
            Name = "Basic",
            Tier = "Free",
        },
        Tags = 
        {
            { "archv2", "" },
            { "tier", "production" },
        },
        WindowsProfile = new AzureNative.ContainerService.Inputs.ManagedClusterWindowsProfileArgs
        {
            AdminPassword = "replacePassword1234$",
            AdminUsername = "azureuser",
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.containerservice.ManagedCluster;
import com.pulumi.azurenative.containerservice.ManagedClusterArgs;
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
        var managedCluster = new ManagedCluster("managedCluster", ManagedClusterArgs.builder()        
            .addonProfiles()
            .agentPoolProfiles(Map.ofEntries(
                Map.entry("count", 3),
                Map.entry("enableNodePublicIP", true),
                Map.entry("mode", "System"),
                Map.entry("name", "nodepool1"),
                Map.entry("osType", "Linux"),
                Map.entry("type", "VirtualMachineScaleSets"),
                Map.entry("vmSize", "Standard_DS2_v2")
            ))
            .autoScalerProfile(Map.ofEntries(
                Map.entry("scaleDownDelayAfterAdd", "15m"),
                Map.entry("scanInterval", "20s")
            ))
            .diskEncryptionSetID("/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des")
            .dnsPrefix("dnsprefix1")
            .enablePodSecurityPolicy(true)
            .enableRBAC(true)
            .kubernetesVersion("")
            .linuxProfile(Map.ofEntries(
                Map.entry("adminUsername", "azureuser"),
                Map.entry("ssh", Map.of("publicKeys", Map.of("keyData", "keydata")))
            ))
            .location("location1")
            .networkProfile(Map.ofEntries(
                Map.entry("loadBalancerProfile", Map.of("managedOutboundIPs", Map.of("count", 2))),
                Map.entry("loadBalancerSku", "standard"),
                Map.entry("outboundType", "loadBalancer")
            ))
            .podIdentityProfile(Map.ofEntries(
                Map.entry("allowNetworkPluginKubenet", true),
                Map.entry("enabled", true)
            ))
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .servicePrincipalProfile(Map.ofEntries(
                Map.entry("clientId", "clientid"),
                Map.entry("secret", "secret")
            ))
            .sku(Map.ofEntries(
                Map.entry("name", "Basic"),
                Map.entry("tier", "Free")
            ))
            .tags(Map.ofEntries(
                Map.entry("archv2", ""),
                Map.entry("tier", "production")
            ))
            .windowsProfile(Map.ofEntries(
                Map.entry("adminPassword", "replacePassword1234$"),
                Map.entry("adminUsername", "azureuser")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedCluster = new azure_native.containerservice.ManagedCluster("managedCluster", {
    addonProfiles: {},
    agentPoolProfiles: [{
        count: 3,
        enableNodePublicIP: true,
        mode: "System",
        name: "nodepool1",
        osType: "Linux",
        type: "VirtualMachineScaleSets",
        vmSize: "Standard_DS2_v2",
    }],
    autoScalerProfile: {
        scaleDownDelayAfterAdd: "15m",
        scanInterval: "20s",
    },
    diskEncryptionSetID: "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
    dnsPrefix: "dnsprefix1",
    enablePodSecurityPolicy: true,
    enableRBAC: true,
    kubernetesVersion: "",
    linuxProfile: {
        adminUsername: "azureuser",
        ssh: {
            publicKeys: [{
                keyData: "keydata",
            }],
        },
    },
    location: "location1",
    networkProfile: {
        loadBalancerProfile: {
            managedOutboundIPs: {
                count: 2,
            },
        },
        loadBalancerSku: "standard",
        outboundType: "loadBalancer",
    },
    podIdentityProfile: {
        allowNetworkPluginKubenet: true,
        enabled: true,
    },
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    servicePrincipalProfile: {
        clientId: "clientid",
        secret: "secret",
    },
    sku: {
        name: "Basic",
        tier: "Free",
    },
    tags: {
        archv2: "",
        tier: "production",
    },
    windowsProfile: {
        adminPassword: "replacePassword1234$",
        adminUsername: "azureuser",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_cluster = azure_native.containerservice.ManagedCluster("managedCluster",
    addon_profiles={},
    agent_pool_profiles=[azure_native.containerservice.ManagedClusterAgentPoolProfileArgs(
        count=3,
        enable_node_public_ip=True,
        mode="System",
        name="nodepool1",
        os_type="Linux",
        type="VirtualMachineScaleSets",
        vm_size="Standard_DS2_v2",
    )],
    auto_scaler_profile=azure_native.containerservice.ManagedClusterPropertiesAutoScalerProfileArgs(
        scale_down_delay_after_add="15m",
        scan_interval="20s",
    ),
    disk_encryption_set_id="/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
    dns_prefix="dnsprefix1",
    enable_pod_security_policy=True,
    enable_rbac=True,
    kubernetes_version="",
    linux_profile=azure_native.containerservice.ContainerServiceLinuxProfileResponseArgs(
        admin_username="azureuser",
        ssh={
            "publicKeys": [azure_native.containerservice.ContainerServiceSshPublicKeyArgs(
                key_data="keydata",
            )],
        },
    ),
    location="location1",
    network_profile=azure_native.containerservice.ContainerServiceNetworkProfileResponseArgs(
        load_balancer_profile={
            "managedOutboundIPs": azure_native.containerservice.ManagedClusterLoadBalancerProfileManagedOutboundIPsArgs(
                count=2,
            ),
        },
        load_balancer_sku="standard",
        outbound_type="loadBalancer",
    ),
    pod_identity_profile=azure_native.containerservice.ManagedClusterPodIdentityProfileArgs(
        allow_network_plugin_kubenet=True,
        enabled=True,
    ),
    resource_group_name="rg1",
    resource_name_="clustername1",
    service_principal_profile=azure_native.containerservice.ManagedClusterServicePrincipalProfileArgs(
        client_id="clientid",
        secret="secret",
    ),
    sku=azure_native.containerservice.ManagedClusterSKUArgs(
        name="Basic",
        tier="Free",
    ),
    tags={
        "archv2": "",
        "tier": "production",
    },
    windows_profile=azure_native.containerservice.ManagedClusterWindowsProfileArgs(
        admin_password="replacePassword1234$",
        admin_username="azureuser",
    ))

```

```yaml
resources:
  managedCluster:
    type: azure-native:containerservice:ManagedCluster
    properties:
      addonProfiles: {}
      agentPoolProfiles:
        - count: 3
          enableNodePublicIP: true
          mode: System
          name: nodepool1
          osType: Linux
          type: VirtualMachineScaleSets
          vmSize: Standard_DS2_v2
      autoScalerProfile:
        scaleDownDelayAfterAdd: 15m
        scanInterval: 20s
      diskEncryptionSetID: /subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des
      dnsPrefix: dnsprefix1
      enablePodSecurityPolicy: true
      enableRBAC: true
      kubernetesVersion:
      linuxProfile:
        adminUsername: azureuser
        ssh:
          publicKeys:
            - keyData: keydata
      location: location1
      networkProfile:
        loadBalancerProfile:
          managedOutboundIPs:
            count: 2
        loadBalancerSku: standard
        outboundType: loadBalancer
      podIdentityProfile:
        allowNetworkPluginKubenet: true
        enabled: true
      resourceGroupName: rg1
      resourceName: clustername1
      servicePrincipalProfile:
        clientId: clientid
        secret: secret
      sku:
        name: Basic
        tier: Free
      tags:
        archv2:
        tier: production
      windowsProfile:
        adminPassword: replacePassword1234$
        adminUsername: azureuser

```

{{% /example %}}
{{% example %}}
### Create Managed Cluster with RunCommand disabled
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedCluster = new AzureNative.ContainerService.ManagedCluster("managedCluster", new()
    {
        AddonProfiles = null,
        AgentPoolProfiles = new[]
        {
            new AzureNative.ContainerService.Inputs.ManagedClusterAgentPoolProfileArgs
            {
                Count = 3,
                EnableEncryptionAtHost = true,
                EnableNodePublicIP = true,
                Mode = "System",
                Name = "nodepool1",
                OsType = "Linux",
                Type = "VirtualMachineScaleSets",
                VmSize = "Standard_DS2_v2",
            },
        },
        ApiServerAccessProfile = new AzureNative.ContainerService.Inputs.ManagedClusterAPIServerAccessProfileArgs
        {
            DisableRunCommand = true,
        },
        AutoScalerProfile = new AzureNative.ContainerService.Inputs.ManagedClusterPropertiesAutoScalerProfileArgs
        {
            ScaleDownDelayAfterAdd = "15m",
            ScanInterval = "20s",
        },
        DnsPrefix = "dnsprefix1",
        EnablePodSecurityPolicy = true,
        EnableRBAC = true,
        KubernetesVersion = "",
        LinuxProfile = new AzureNative.ContainerService.Inputs.ContainerServiceLinuxProfileArgs
        {
            AdminUsername = "azureuser",
            Ssh = new AzureNative.ContainerService.Inputs.ContainerServiceSshConfigurationArgs
            {
                PublicKeys = new[]
                {
                    new AzureNative.ContainerService.Inputs.ContainerServiceSshPublicKeyArgs
                    {
                        KeyData = "keydata",
                    },
                },
            },
        },
        Location = "location1",
        NetworkProfile = new AzureNative.ContainerService.Inputs.ContainerServiceNetworkProfileArgs
        {
            LoadBalancerProfile = new AzureNative.ContainerService.Inputs.ManagedClusterLoadBalancerProfileArgs
            {
                ManagedOutboundIPs = new AzureNative.ContainerService.Inputs.ManagedClusterLoadBalancerProfileManagedOutboundIPsArgs
                {
                    Count = 2,
                },
            },
            LoadBalancerSku = "standard",
            OutboundType = "loadBalancer",
        },
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        ServicePrincipalProfile = new AzureNative.ContainerService.Inputs.ManagedClusterServicePrincipalProfileArgs
        {
            ClientId = "clientid",
            Secret = "secret",
        },
        Sku = new AzureNative.ContainerService.Inputs.ManagedClusterSKUArgs
        {
            Name = "Basic",
            Tier = "Free",
        },
        Tags = 
        {
            { "archv2", "" },
            { "tier", "production" },
        },
        WindowsProfile = new AzureNative.ContainerService.Inputs.ManagedClusterWindowsProfileArgs
        {
            AdminPassword = "replacePassword1234$",
            AdminUsername = "azureuser",
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.containerservice.ManagedCluster;
import com.pulumi.azurenative.containerservice.ManagedClusterArgs;
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
        var managedCluster = new ManagedCluster("managedCluster", ManagedClusterArgs.builder()        
            .addonProfiles()
            .agentPoolProfiles(Map.ofEntries(
                Map.entry("count", 3),
                Map.entry("enableEncryptionAtHost", true),
                Map.entry("enableNodePublicIP", true),
                Map.entry("mode", "System"),
                Map.entry("name", "nodepool1"),
                Map.entry("osType", "Linux"),
                Map.entry("type", "VirtualMachineScaleSets"),
                Map.entry("vmSize", "Standard_DS2_v2")
            ))
            .apiServerAccessProfile(Map.of("disableRunCommand", true))
            .autoScalerProfile(Map.ofEntries(
                Map.entry("scaleDownDelayAfterAdd", "15m"),
                Map.entry("scanInterval", "20s")
            ))
            .dnsPrefix("dnsprefix1")
            .enablePodSecurityPolicy(true)
            .enableRBAC(true)
            .kubernetesVersion("")
            .linuxProfile(Map.ofEntries(
                Map.entry("adminUsername", "azureuser"),
                Map.entry("ssh", Map.of("publicKeys", Map.of("keyData", "keydata")))
            ))
            .location("location1")
            .networkProfile(Map.ofEntries(
                Map.entry("loadBalancerProfile", Map.of("managedOutboundIPs", Map.of("count", 2))),
                Map.entry("loadBalancerSku", "standard"),
                Map.entry("outboundType", "loadBalancer")
            ))
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .servicePrincipalProfile(Map.ofEntries(
                Map.entry("clientId", "clientid"),
                Map.entry("secret", "secret")
            ))
            .sku(Map.ofEntries(
                Map.entry("name", "Basic"),
                Map.entry("tier", "Free")
            ))
            .tags(Map.ofEntries(
                Map.entry("archv2", ""),
                Map.entry("tier", "production")
            ))
            .windowsProfile(Map.ofEntries(
                Map.entry("adminPassword", "replacePassword1234$"),
                Map.entry("adminUsername", "azureuser")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedCluster = new azure_native.containerservice.ManagedCluster("managedCluster", {
    addonProfiles: {},
    agentPoolProfiles: [{
        count: 3,
        enableEncryptionAtHost: true,
        enableNodePublicIP: true,
        mode: "System",
        name: "nodepool1",
        osType: "Linux",
        type: "VirtualMachineScaleSets",
        vmSize: "Standard_DS2_v2",
    }],
    apiServerAccessProfile: {
        disableRunCommand: true,
    },
    autoScalerProfile: {
        scaleDownDelayAfterAdd: "15m",
        scanInterval: "20s",
    },
    dnsPrefix: "dnsprefix1",
    enablePodSecurityPolicy: true,
    enableRBAC: true,
    kubernetesVersion: "",
    linuxProfile: {
        adminUsername: "azureuser",
        ssh: {
            publicKeys: [{
                keyData: "keydata",
            }],
        },
    },
    location: "location1",
    networkProfile: {
        loadBalancerProfile: {
            managedOutboundIPs: {
                count: 2,
            },
        },
        loadBalancerSku: "standard",
        outboundType: "loadBalancer",
    },
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    servicePrincipalProfile: {
        clientId: "clientid",
        secret: "secret",
    },
    sku: {
        name: "Basic",
        tier: "Free",
    },
    tags: {
        archv2: "",
        tier: "production",
    },
    windowsProfile: {
        adminPassword: "replacePassword1234$",
        adminUsername: "azureuser",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_cluster = azure_native.containerservice.ManagedCluster("managedCluster",
    addon_profiles={},
    agent_pool_profiles=[azure_native.containerservice.ManagedClusterAgentPoolProfileArgs(
        count=3,
        enable_encryption_at_host=True,
        enable_node_public_ip=True,
        mode="System",
        name="nodepool1",
        os_type="Linux",
        type="VirtualMachineScaleSets",
        vm_size="Standard_DS2_v2",
    )],
    api_server_access_profile=azure_native.containerservice.ManagedClusterAPIServerAccessProfileArgs(
        disable_run_command=True,
    ),
    auto_scaler_profile=azure_native.containerservice.ManagedClusterPropertiesAutoScalerProfileArgs(
        scale_down_delay_after_add="15m",
        scan_interval="20s",
    ),
    dns_prefix="dnsprefix1",
    enable_pod_security_policy=True,
    enable_rbac=True,
    kubernetes_version="",
    linux_profile=azure_native.containerservice.ContainerServiceLinuxProfileResponseArgs(
        admin_username="azureuser",
        ssh={
            "publicKeys": [azure_native.containerservice.ContainerServiceSshPublicKeyArgs(
                key_data="keydata",
            )],
        },
    ),
    location="location1",
    network_profile=azure_native.containerservice.ContainerServiceNetworkProfileResponseArgs(
        load_balancer_profile={
            "managedOutboundIPs": azure_native.containerservice.ManagedClusterLoadBalancerProfileManagedOutboundIPsArgs(
                count=2,
            ),
        },
        load_balancer_sku="standard",
        outbound_type="loadBalancer",
    ),
    resource_group_name="rg1",
    resource_name_="clustername1",
    service_principal_profile=azure_native.containerservice.ManagedClusterServicePrincipalProfileArgs(
        client_id="clientid",
        secret="secret",
    ),
    sku=azure_native.containerservice.ManagedClusterSKUArgs(
        name="Basic",
        tier="Free",
    ),
    tags={
        "archv2": "",
        "tier": "production",
    },
    windows_profile=azure_native.containerservice.ManagedClusterWindowsProfileArgs(
        admin_password="replacePassword1234$",
        admin_username="azureuser",
    ))

```

```yaml
resources:
  managedCluster:
    type: azure-native:containerservice:ManagedCluster
    properties:
      addonProfiles: {}
      agentPoolProfiles:
        - count: 3
          enableEncryptionAtHost: true
          enableNodePublicIP: true
          mode: System
          name: nodepool1
          osType: Linux
          type: VirtualMachineScaleSets
          vmSize: Standard_DS2_v2
      apiServerAccessProfile:
        disableRunCommand: true
      autoScalerProfile:
        scaleDownDelayAfterAdd: 15m
        scanInterval: 20s
      dnsPrefix: dnsprefix1
      enablePodSecurityPolicy: true
      enableRBAC: true
      kubernetesVersion:
      linuxProfile:
        adminUsername: azureuser
        ssh:
          publicKeys:
            - keyData: keydata
      location: location1
      networkProfile:
        loadBalancerProfile:
          managedOutboundIPs:
            count: 2
        loadBalancerSku: standard
        outboundType: loadBalancer
      resourceGroupName: rg1
      resourceName: clustername1
      servicePrincipalProfile:
        clientId: clientid
        secret: secret
      sku:
        name: Basic
        tier: Free
      tags:
        archv2:
        tier: production
      windowsProfile:
        adminPassword: replacePassword1234$
        adminUsername: azureuser

```

{{% /example %}}
{{% example %}}
### Create Managed Cluster with Security Profile configured
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedCluster = new AzureNative.ContainerService.ManagedCluster("managedCluster", new()
    {
        AgentPoolProfiles = new[]
        {
            new AzureNative.ContainerService.Inputs.ManagedClusterAgentPoolProfileArgs
            {
                Count = 3,
                EnableNodePublicIP = true,
                Mode = "System",
                Name = "nodepool1",
                OsType = "Linux",
                Type = "VirtualMachineScaleSets",
                VmSize = "Standard_DS2_v2",
            },
        },
        DnsPrefix = "dnsprefix1",
        KubernetesVersion = "",
        LinuxProfile = new AzureNative.ContainerService.Inputs.ContainerServiceLinuxProfileArgs
        {
            AdminUsername = "azureuser",
            Ssh = new AzureNative.ContainerService.Inputs.ContainerServiceSshConfigurationArgs
            {
                PublicKeys = new[]
                {
                    new AzureNative.ContainerService.Inputs.ContainerServiceSshPublicKeyArgs
                    {
                        KeyData = "keydata",
                    },
                },
            },
        },
        Location = "location1",
        NetworkProfile = new AzureNative.ContainerService.Inputs.ContainerServiceNetworkProfileArgs
        {
            LoadBalancerProfile = new AzureNative.ContainerService.Inputs.ManagedClusterLoadBalancerProfileArgs
            {
                ManagedOutboundIPs = new AzureNative.ContainerService.Inputs.ManagedClusterLoadBalancerProfileManagedOutboundIPsArgs
                {
                    Count = 2,
                },
            },
            LoadBalancerSku = "standard",
            OutboundType = "loadBalancer",
        },
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        SecurityProfile = new AzureNative.ContainerService.Inputs.ManagedClusterSecurityProfileArgs
        {
            Defender = new AzureNative.ContainerService.Inputs.ManagedClusterSecurityProfileDefenderArgs
            {
                LogAnalyticsWorkspaceResourceId = "/subscriptions/SUB_ID/resourcegroups/RG_NAME/providers/microsoft.operationalinsights/workspaces/WORKSPACE_NAME",
                SecurityMonitoring = new AzureNative.ContainerService.Inputs.ManagedClusterSecurityProfileDefenderSecurityMonitoringArgs
                {
                    Enabled = true,
                },
            },
        },
        Sku = new AzureNative.ContainerService.Inputs.ManagedClusterSKUArgs
        {
            Name = "Basic",
            Tier = "Free",
        },
        Tags = 
        {
            { "archv2", "" },
            { "tier", "production" },
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.containerservice.ManagedCluster;
import com.pulumi.azurenative.containerservice.ManagedClusterArgs;
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
        var managedCluster = new ManagedCluster("managedCluster", ManagedClusterArgs.builder()        
            .agentPoolProfiles(Map.ofEntries(
                Map.entry("count", 3),
                Map.entry("enableNodePublicIP", true),
                Map.entry("mode", "System"),
                Map.entry("name", "nodepool1"),
                Map.entry("osType", "Linux"),
                Map.entry("type", "VirtualMachineScaleSets"),
                Map.entry("vmSize", "Standard_DS2_v2")
            ))
            .dnsPrefix("dnsprefix1")
            .kubernetesVersion("")
            .linuxProfile(Map.ofEntries(
                Map.entry("adminUsername", "azureuser"),
                Map.entry("ssh", Map.of("publicKeys", Map.of("keyData", "keydata")))
            ))
            .location("location1")
            .networkProfile(Map.ofEntries(
                Map.entry("loadBalancerProfile", Map.of("managedOutboundIPs", Map.of("count", 2))),
                Map.entry("loadBalancerSku", "standard"),
                Map.entry("outboundType", "loadBalancer")
            ))
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .securityProfile(Map.of("defender", Map.ofEntries(
                Map.entry("logAnalyticsWorkspaceResourceId", "/subscriptions/SUB_ID/resourcegroups/RG_NAME/providers/microsoft.operationalinsights/workspaces/WORKSPACE_NAME"),
                Map.entry("securityMonitoring", Map.of("enabled", true))
            )))
            .sku(Map.ofEntries(
                Map.entry("name", "Basic"),
                Map.entry("tier", "Free")
            ))
            .tags(Map.ofEntries(
                Map.entry("archv2", ""),
                Map.entry("tier", "production")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedCluster = new azure_native.containerservice.ManagedCluster("managedCluster", {
    agentPoolProfiles: [{
        count: 3,
        enableNodePublicIP: true,
        mode: "System",
        name: "nodepool1",
        osType: "Linux",
        type: "VirtualMachineScaleSets",
        vmSize: "Standard_DS2_v2",
    }],
    dnsPrefix: "dnsprefix1",
    kubernetesVersion: "",
    linuxProfile: {
        adminUsername: "azureuser",
        ssh: {
            publicKeys: [{
                keyData: "keydata",
            }],
        },
    },
    location: "location1",
    networkProfile: {
        loadBalancerProfile: {
            managedOutboundIPs: {
                count: 2,
            },
        },
        loadBalancerSku: "standard",
        outboundType: "loadBalancer",
    },
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    securityProfile: {
        defender: {
            logAnalyticsWorkspaceResourceId: "/subscriptions/SUB_ID/resourcegroups/RG_NAME/providers/microsoft.operationalinsights/workspaces/WORKSPACE_NAME",
            securityMonitoring: {
                enabled: true,
            },
        },
    },
    sku: {
        name: "Basic",
        tier: "Free",
    },
    tags: {
        archv2: "",
        tier: "production",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_cluster = azure_native.containerservice.ManagedCluster("managedCluster",
    agent_pool_profiles=[azure_native.containerservice.ManagedClusterAgentPoolProfileArgs(
        count=3,
        enable_node_public_ip=True,
        mode="System",
        name="nodepool1",
        os_type="Linux",
        type="VirtualMachineScaleSets",
        vm_size="Standard_DS2_v2",
    )],
    dns_prefix="dnsprefix1",
    kubernetes_version="",
    linux_profile=azure_native.containerservice.ContainerServiceLinuxProfileResponseArgs(
        admin_username="azureuser",
        ssh={
            "publicKeys": [azure_native.containerservice.ContainerServiceSshPublicKeyArgs(
                key_data="keydata",
            )],
        },
    ),
    location="location1",
    network_profile=azure_native.containerservice.ContainerServiceNetworkProfileResponseArgs(
        load_balancer_profile={
            "managedOutboundIPs": azure_native.containerservice.ManagedClusterLoadBalancerProfileManagedOutboundIPsArgs(
                count=2,
            ),
        },
        load_balancer_sku="standard",
        outbound_type="loadBalancer",
    ),
    resource_group_name="rg1",
    resource_name_="clustername1",
    security_profile=azure_native.containerservice.ManagedClusterSecurityProfileResponseArgs(
        defender={
            "logAnalyticsWorkspaceResourceId": "/subscriptions/SUB_ID/resourcegroups/RG_NAME/providers/microsoft.operationalinsights/workspaces/WORKSPACE_NAME",
            "securityMonitoring": azure_native.containerservice.ManagedClusterSecurityProfileDefenderSecurityMonitoringArgs(
                enabled=True,
            ),
        },
    ),
    sku=azure_native.containerservice.ManagedClusterSKUArgs(
        name="Basic",
        tier="Free",
    ),
    tags={
        "archv2": "",
        "tier": "production",
    })

```

```yaml
resources:
  managedCluster:
    type: azure-native:containerservice:ManagedCluster
    properties:
      agentPoolProfiles:
        - count: 3
          enableNodePublicIP: true
          mode: System
          name: nodepool1
          osType: Linux
          type: VirtualMachineScaleSets
          vmSize: Standard_DS2_v2
      dnsPrefix: dnsprefix1
      kubernetesVersion:
      linuxProfile:
        adminUsername: azureuser
        ssh:
          publicKeys:
            - keyData: keydata
      location: location1
      networkProfile:
        loadBalancerProfile:
          managedOutboundIPs:
            count: 2
        loadBalancerSku: standard
        outboundType: loadBalancer
      resourceGroupName: rg1
      resourceName: clustername1
      securityProfile:
        defender:
          logAnalyticsWorkspaceResourceId: /subscriptions/SUB_ID/resourcegroups/RG_NAME/providers/microsoft.operationalinsights/workspaces/WORKSPACE_NAME
          securityMonitoring:
            enabled: true
      sku:
        name: Basic
        tier: Free
      tags:
        archv2:
        tier: production

```

{{% /example %}}
{{% example %}}
### Create Managed Cluster with UltraSSD enabled
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedCluster = new AzureNative.ContainerService.ManagedCluster("managedCluster", new()
    {
        AddonProfiles = null,
        AgentPoolProfiles = new[]
        {
            new AzureNative.ContainerService.Inputs.ManagedClusterAgentPoolProfileArgs
            {
                Count = 3,
                EnableNodePublicIP = true,
                EnableUltraSSD = true,
                Mode = "System",
                Name = "nodepool1",
                OsType = "Linux",
                Type = "VirtualMachineScaleSets",
                VmSize = "Standard_DS2_v2",
            },
        },
        AutoScalerProfile = new AzureNative.ContainerService.Inputs.ManagedClusterPropertiesAutoScalerProfileArgs
        {
            ScaleDownDelayAfterAdd = "15m",
            ScanInterval = "20s",
        },
        DiskEncryptionSetID = "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
        DnsPrefix = "dnsprefix1",
        EnablePodSecurityPolicy = true,
        EnableRBAC = true,
        KubernetesVersion = "",
        LinuxProfile = new AzureNative.ContainerService.Inputs.ContainerServiceLinuxProfileArgs
        {
            AdminUsername = "azureuser",
            Ssh = new AzureNative.ContainerService.Inputs.ContainerServiceSshConfigurationArgs
            {
                PublicKeys = new[]
                {
                    new AzureNative.ContainerService.Inputs.ContainerServiceSshPublicKeyArgs
                    {
                        KeyData = "keydata",
                    },
                },
            },
        },
        Location = "location1",
        NetworkProfile = new AzureNative.ContainerService.Inputs.ContainerServiceNetworkProfileArgs
        {
            LoadBalancerProfile = new AzureNative.ContainerService.Inputs.ManagedClusterLoadBalancerProfileArgs
            {
                ManagedOutboundIPs = new AzureNative.ContainerService.Inputs.ManagedClusterLoadBalancerProfileManagedOutboundIPsArgs
                {
                    Count = 2,
                },
            },
            LoadBalancerSku = "standard",
            OutboundType = "loadBalancer",
        },
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        ServicePrincipalProfile = new AzureNative.ContainerService.Inputs.ManagedClusterServicePrincipalProfileArgs
        {
            ClientId = "clientid",
            Secret = "secret",
        },
        Sku = new AzureNative.ContainerService.Inputs.ManagedClusterSKUArgs
        {
            Name = "Basic",
            Tier = "Free",
        },
        Tags = 
        {
            { "archv2", "" },
            { "tier", "production" },
        },
        WindowsProfile = new AzureNative.ContainerService.Inputs.ManagedClusterWindowsProfileArgs
        {
            AdminPassword = "replacePassword1234$",
            AdminUsername = "azureuser",
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.containerservice.ManagedCluster;
import com.pulumi.azurenative.containerservice.ManagedClusterArgs;
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
        var managedCluster = new ManagedCluster("managedCluster", ManagedClusterArgs.builder()        
            .addonProfiles()
            .agentPoolProfiles(Map.ofEntries(
                Map.entry("count", 3),
                Map.entry("enableNodePublicIP", true),
                Map.entry("enableUltraSSD", true),
                Map.entry("mode", "System"),
                Map.entry("name", "nodepool1"),
                Map.entry("osType", "Linux"),
                Map.entry("type", "VirtualMachineScaleSets"),
                Map.entry("vmSize", "Standard_DS2_v2")
            ))
            .autoScalerProfile(Map.ofEntries(
                Map.entry("scaleDownDelayAfterAdd", "15m"),
                Map.entry("scanInterval", "20s")
            ))
            .diskEncryptionSetID("/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des")
            .dnsPrefix("dnsprefix1")
            .enablePodSecurityPolicy(true)
            .enableRBAC(true)
            .kubernetesVersion("")
            .linuxProfile(Map.ofEntries(
                Map.entry("adminUsername", "azureuser"),
                Map.entry("ssh", Map.of("publicKeys", Map.of("keyData", "keydata")))
            ))
            .location("location1")
            .networkProfile(Map.ofEntries(
                Map.entry("loadBalancerProfile", Map.of("managedOutboundIPs", Map.of("count", 2))),
                Map.entry("loadBalancerSku", "standard"),
                Map.entry("outboundType", "loadBalancer")
            ))
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .servicePrincipalProfile(Map.ofEntries(
                Map.entry("clientId", "clientid"),
                Map.entry("secret", "secret")
            ))
            .sku(Map.ofEntries(
                Map.entry("name", "Basic"),
                Map.entry("tier", "Free")
            ))
            .tags(Map.ofEntries(
                Map.entry("archv2", ""),
                Map.entry("tier", "production")
            ))
            .windowsProfile(Map.ofEntries(
                Map.entry("adminPassword", "replacePassword1234$"),
                Map.entry("adminUsername", "azureuser")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedCluster = new azure_native.containerservice.ManagedCluster("managedCluster", {
    addonProfiles: {},
    agentPoolProfiles: [{
        count: 3,
        enableNodePublicIP: true,
        enableUltraSSD: true,
        mode: "System",
        name: "nodepool1",
        osType: "Linux",
        type: "VirtualMachineScaleSets",
        vmSize: "Standard_DS2_v2",
    }],
    autoScalerProfile: {
        scaleDownDelayAfterAdd: "15m",
        scanInterval: "20s",
    },
    diskEncryptionSetID: "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
    dnsPrefix: "dnsprefix1",
    enablePodSecurityPolicy: true,
    enableRBAC: true,
    kubernetesVersion: "",
    linuxProfile: {
        adminUsername: "azureuser",
        ssh: {
            publicKeys: [{
                keyData: "keydata",
            }],
        },
    },
    location: "location1",
    networkProfile: {
        loadBalancerProfile: {
            managedOutboundIPs: {
                count: 2,
            },
        },
        loadBalancerSku: "standard",
        outboundType: "loadBalancer",
    },
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    servicePrincipalProfile: {
        clientId: "clientid",
        secret: "secret",
    },
    sku: {
        name: "Basic",
        tier: "Free",
    },
    tags: {
        archv2: "",
        tier: "production",
    },
    windowsProfile: {
        adminPassword: "replacePassword1234$",
        adminUsername: "azureuser",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_cluster = azure_native.containerservice.ManagedCluster("managedCluster",
    addon_profiles={},
    agent_pool_profiles=[azure_native.containerservice.ManagedClusterAgentPoolProfileArgs(
        count=3,
        enable_node_public_ip=True,
        enable_ultra_ssd=True,
        mode="System",
        name="nodepool1",
        os_type="Linux",
        type="VirtualMachineScaleSets",
        vm_size="Standard_DS2_v2",
    )],
    auto_scaler_profile=azure_native.containerservice.ManagedClusterPropertiesAutoScalerProfileArgs(
        scale_down_delay_after_add="15m",
        scan_interval="20s",
    ),
    disk_encryption_set_id="/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
    dns_prefix="dnsprefix1",
    enable_pod_security_policy=True,
    enable_rbac=True,
    kubernetes_version="",
    linux_profile=azure_native.containerservice.ContainerServiceLinuxProfileResponseArgs(
        admin_username="azureuser",
        ssh={
            "publicKeys": [azure_native.containerservice.ContainerServiceSshPublicKeyArgs(
                key_data="keydata",
            )],
        },
    ),
    location="location1",
    network_profile=azure_native.containerservice.ContainerServiceNetworkProfileResponseArgs(
        load_balancer_profile={
            "managedOutboundIPs": azure_native.containerservice.ManagedClusterLoadBalancerProfileManagedOutboundIPsArgs(
                count=2,
            ),
        },
        load_balancer_sku="standard",
        outbound_type="loadBalancer",
    ),
    resource_group_name="rg1",
    resource_name_="clustername1",
    service_principal_profile=azure_native.containerservice.ManagedClusterServicePrincipalProfileArgs(
        client_id="clientid",
        secret="secret",
    ),
    sku=azure_native.containerservice.ManagedClusterSKUArgs(
        name="Basic",
        tier="Free",
    ),
    tags={
        "archv2": "",
        "tier": "production",
    },
    windows_profile=azure_native.containerservice.ManagedClusterWindowsProfileArgs(
        admin_password="replacePassword1234$",
        admin_username="azureuser",
    ))

```

```yaml
resources:
  managedCluster:
    type: azure-native:containerservice:ManagedCluster
    properties:
      addonProfiles: {}
      agentPoolProfiles:
        - count: 3
          enableNodePublicIP: true
          enableUltraSSD: true
          mode: System
          name: nodepool1
          osType: Linux
          type: VirtualMachineScaleSets
          vmSize: Standard_DS2_v2
      autoScalerProfile:
        scaleDownDelayAfterAdd: 15m
        scanInterval: 20s
      diskEncryptionSetID: /subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des
      dnsPrefix: dnsprefix1
      enablePodSecurityPolicy: true
      enableRBAC: true
      kubernetesVersion:
      linuxProfile:
        adminUsername: azureuser
        ssh:
          publicKeys:
            - keyData: keydata
      location: location1
      networkProfile:
        loadBalancerProfile:
          managedOutboundIPs:
            count: 2
        loadBalancerSku: standard
        outboundType: loadBalancer
      resourceGroupName: rg1
      resourceName: clustername1
      servicePrincipalProfile:
        clientId: clientid
        secret: secret
      sku:
        name: Basic
        tier: Free
      tags:
        archv2:
        tier: production
      windowsProfile:
        adminPassword: replacePassword1234$
        adminUsername: azureuser

```

{{% /example %}}
{{% example %}}
### Create Managed Cluster with user-assigned NAT gateway as outbound type
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedCluster = new AzureNative.ContainerService.ManagedCluster("managedCluster", new()
    {
        AddonProfiles = null,
        AgentPoolProfiles = new[]
        {
            new AzureNative.ContainerService.Inputs.ManagedClusterAgentPoolProfileArgs
            {
                Count = 3,
                EnableNodePublicIP = false,
                Mode = "System",
                Name = "nodepool1",
                OsType = "Linux",
                Type = "VirtualMachineScaleSets",
                VmSize = "Standard_DS2_v2",
            },
        },
        AutoScalerProfile = new AzureNative.ContainerService.Inputs.ManagedClusterPropertiesAutoScalerProfileArgs
        {
            ScaleDownDelayAfterAdd = "15m",
            ScanInterval = "20s",
        },
        DiskEncryptionSetID = "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
        DnsPrefix = "dnsprefix1",
        EnablePodSecurityPolicy = true,
        EnableRBAC = true,
        KubernetesVersion = "",
        LinuxProfile = new AzureNative.ContainerService.Inputs.ContainerServiceLinuxProfileArgs
        {
            AdminUsername = "azureuser",
            Ssh = new AzureNative.ContainerService.Inputs.ContainerServiceSshConfigurationArgs
            {
                PublicKeys = new[]
                {
                    new AzureNative.ContainerService.Inputs.ContainerServiceSshPublicKeyArgs
                    {
                        KeyData = "keydata",
                    },
                },
            },
        },
        Location = "location1",
        NetworkProfile = new AzureNative.ContainerService.Inputs.ContainerServiceNetworkProfileArgs
        {
            LoadBalancerSku = "standard",
            OutboundType = "userAssignedNATGateway",
        },
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        ServicePrincipalProfile = new AzureNative.ContainerService.Inputs.ManagedClusterServicePrincipalProfileArgs
        {
            ClientId = "clientid",
            Secret = "secret",
        },
        Sku = new AzureNative.ContainerService.Inputs.ManagedClusterSKUArgs
        {
            Name = "Basic",
            Tier = "Free",
        },
        Tags = 
        {
            { "archv2", "" },
            { "tier", "production" },
        },
        WindowsProfile = new AzureNative.ContainerService.Inputs.ManagedClusterWindowsProfileArgs
        {
            AdminPassword = "replacePassword1234$",
            AdminUsername = "azureuser",
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.containerservice.ManagedCluster;
import com.pulumi.azurenative.containerservice.ManagedClusterArgs;
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
        var managedCluster = new ManagedCluster("managedCluster", ManagedClusterArgs.builder()        
            .addonProfiles()
            .agentPoolProfiles(Map.ofEntries(
                Map.entry("count", 3),
                Map.entry("enableNodePublicIP", false),
                Map.entry("mode", "System"),
                Map.entry("name", "nodepool1"),
                Map.entry("osType", "Linux"),
                Map.entry("type", "VirtualMachineScaleSets"),
                Map.entry("vmSize", "Standard_DS2_v2")
            ))
            .autoScalerProfile(Map.ofEntries(
                Map.entry("scaleDownDelayAfterAdd", "15m"),
                Map.entry("scanInterval", "20s")
            ))
            .diskEncryptionSetID("/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des")
            .dnsPrefix("dnsprefix1")
            .enablePodSecurityPolicy(true)
            .enableRBAC(true)
            .kubernetesVersion("")
            .linuxProfile(Map.ofEntries(
                Map.entry("adminUsername", "azureuser"),
                Map.entry("ssh", Map.of("publicKeys", Map.of("keyData", "keydata")))
            ))
            .location("location1")
            .networkProfile(Map.ofEntries(
                Map.entry("loadBalancerSku", "standard"),
                Map.entry("outboundType", "userAssignedNATGateway")
            ))
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .servicePrincipalProfile(Map.ofEntries(
                Map.entry("clientId", "clientid"),
                Map.entry("secret", "secret")
            ))
            .sku(Map.ofEntries(
                Map.entry("name", "Basic"),
                Map.entry("tier", "Free")
            ))
            .tags(Map.ofEntries(
                Map.entry("archv2", ""),
                Map.entry("tier", "production")
            ))
            .windowsProfile(Map.ofEntries(
                Map.entry("adminPassword", "replacePassword1234$"),
                Map.entry("adminUsername", "azureuser")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedCluster = new azure_native.containerservice.ManagedCluster("managedCluster", {
    addonProfiles: {},
    agentPoolProfiles: [{
        count: 3,
        enableNodePublicIP: false,
        mode: "System",
        name: "nodepool1",
        osType: "Linux",
        type: "VirtualMachineScaleSets",
        vmSize: "Standard_DS2_v2",
    }],
    autoScalerProfile: {
        scaleDownDelayAfterAdd: "15m",
        scanInterval: "20s",
    },
    diskEncryptionSetID: "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
    dnsPrefix: "dnsprefix1",
    enablePodSecurityPolicy: true,
    enableRBAC: true,
    kubernetesVersion: "",
    linuxProfile: {
        adminUsername: "azureuser",
        ssh: {
            publicKeys: [{
                keyData: "keydata",
            }],
        },
    },
    location: "location1",
    networkProfile: {
        loadBalancerSku: "standard",
        outboundType: "userAssignedNATGateway",
    },
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    servicePrincipalProfile: {
        clientId: "clientid",
        secret: "secret",
    },
    sku: {
        name: "Basic",
        tier: "Free",
    },
    tags: {
        archv2: "",
        tier: "production",
    },
    windowsProfile: {
        adminPassword: "replacePassword1234$",
        adminUsername: "azureuser",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_cluster = azure_native.containerservice.ManagedCluster("managedCluster",
    addon_profiles={},
    agent_pool_profiles=[azure_native.containerservice.ManagedClusterAgentPoolProfileArgs(
        count=3,
        enable_node_public_ip=False,
        mode="System",
        name="nodepool1",
        os_type="Linux",
        type="VirtualMachineScaleSets",
        vm_size="Standard_DS2_v2",
    )],
    auto_scaler_profile=azure_native.containerservice.ManagedClusterPropertiesAutoScalerProfileArgs(
        scale_down_delay_after_add="15m",
        scan_interval="20s",
    ),
    disk_encryption_set_id="/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
    dns_prefix="dnsprefix1",
    enable_pod_security_policy=True,
    enable_rbac=True,
    kubernetes_version="",
    linux_profile=azure_native.containerservice.ContainerServiceLinuxProfileResponseArgs(
        admin_username="azureuser",
        ssh={
            "publicKeys": [azure_native.containerservice.ContainerServiceSshPublicKeyArgs(
                key_data="keydata",
            )],
        },
    ),
    location="location1",
    network_profile=azure_native.containerservice.ContainerServiceNetworkProfileArgs(
        load_balancer_sku="standard",
        outbound_type="userAssignedNATGateway",
    ),
    resource_group_name="rg1",
    resource_name_="clustername1",
    service_principal_profile=azure_native.containerservice.ManagedClusterServicePrincipalProfileArgs(
        client_id="clientid",
        secret="secret",
    ),
    sku=azure_native.containerservice.ManagedClusterSKUArgs(
        name="Basic",
        tier="Free",
    ),
    tags={
        "archv2": "",
        "tier": "production",
    },
    windows_profile=azure_native.containerservice.ManagedClusterWindowsProfileArgs(
        admin_password="replacePassword1234$",
        admin_username="azureuser",
    ))

```

```yaml
resources:
  managedCluster:
    type: azure-native:containerservice:ManagedCluster
    properties:
      addonProfiles: {}
      agentPoolProfiles:
        - count: 3
          enableNodePublicIP: false
          mode: System
          name: nodepool1
          osType: Linux
          type: VirtualMachineScaleSets
          vmSize: Standard_DS2_v2
      autoScalerProfile:
        scaleDownDelayAfterAdd: 15m
        scanInterval: 20s
      diskEncryptionSetID: /subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des
      dnsPrefix: dnsprefix1
      enablePodSecurityPolicy: true
      enableRBAC: true
      kubernetesVersion:
      linuxProfile:
        adminUsername: azureuser
        ssh:
          publicKeys:
            - keyData: keydata
      location: location1
      networkProfile:
        loadBalancerSku: standard
        outboundType: userAssignedNATGateway
      resourceGroupName: rg1
      resourceName: clustername1
      servicePrincipalProfile:
        clientId: clientid
        secret: secret
      sku:
        name: Basic
        tier: Free
      tags:
        archv2:
        tier: production
      windowsProfile:
        adminPassword: replacePassword1234$
        adminUsername: azureuser

```

{{% /example %}}
{{% example %}}
### Create Managed Private Cluster with Public FQDN specified
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedCluster = new AzureNative.ContainerService.ManagedCluster("managedCluster", new()
    {
        AddonProfiles = null,
        AgentPoolProfiles = new[]
        {
            new AzureNative.ContainerService.Inputs.ManagedClusterAgentPoolProfileArgs
            {
                Count = 3,
                EnableEncryptionAtHost = true,
                EnableNodePublicIP = true,
                Mode = "System",
                Name = "nodepool1",
                OsType = "Linux",
                Type = "VirtualMachineScaleSets",
                VmSize = "Standard_DS2_v2",
            },
        },
        ApiServerAccessProfile = new AzureNative.ContainerService.Inputs.ManagedClusterAPIServerAccessProfileArgs
        {
            EnablePrivateCluster = true,
            EnablePrivateClusterPublicFQDN = true,
        },
        AutoScalerProfile = new AzureNative.ContainerService.Inputs.ManagedClusterPropertiesAutoScalerProfileArgs
        {
            ScaleDownDelayAfterAdd = "15m",
            ScanInterval = "20s",
        },
        DnsPrefix = "dnsprefix1",
        EnablePodSecurityPolicy = true,
        EnableRBAC = true,
        KubernetesVersion = "",
        LinuxProfile = new AzureNative.ContainerService.Inputs.ContainerServiceLinuxProfileArgs
        {
            AdminUsername = "azureuser",
            Ssh = new AzureNative.ContainerService.Inputs.ContainerServiceSshConfigurationArgs
            {
                PublicKeys = new[]
                {
                    new AzureNative.ContainerService.Inputs.ContainerServiceSshPublicKeyArgs
                    {
                        KeyData = "keydata",
                    },
                },
            },
        },
        Location = "location1",
        NetworkProfile = new AzureNative.ContainerService.Inputs.ContainerServiceNetworkProfileArgs
        {
            LoadBalancerProfile = new AzureNative.ContainerService.Inputs.ManagedClusterLoadBalancerProfileArgs
            {
                ManagedOutboundIPs = new AzureNative.ContainerService.Inputs.ManagedClusterLoadBalancerProfileManagedOutboundIPsArgs
                {
                    Count = 2,
                },
            },
            LoadBalancerSku = "standard",
            OutboundType = "loadBalancer",
        },
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        ServicePrincipalProfile = new AzureNative.ContainerService.Inputs.ManagedClusterServicePrincipalProfileArgs
        {
            ClientId = "clientid",
            Secret = "secret",
        },
        Sku = new AzureNative.ContainerService.Inputs.ManagedClusterSKUArgs
        {
            Name = "Basic",
            Tier = "Free",
        },
        Tags = 
        {
            { "archv2", "" },
            { "tier", "production" },
        },
        WindowsProfile = new AzureNative.ContainerService.Inputs.ManagedClusterWindowsProfileArgs
        {
            AdminPassword = "replacePassword1234$",
            AdminUsername = "azureuser",
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.containerservice.ManagedCluster;
import com.pulumi.azurenative.containerservice.ManagedClusterArgs;
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
        var managedCluster = new ManagedCluster("managedCluster", ManagedClusterArgs.builder()        
            .addonProfiles()
            .agentPoolProfiles(Map.ofEntries(
                Map.entry("count", 3),
                Map.entry("enableEncryptionAtHost", true),
                Map.entry("enableNodePublicIP", true),
                Map.entry("mode", "System"),
                Map.entry("name", "nodepool1"),
                Map.entry("osType", "Linux"),
                Map.entry("type", "VirtualMachineScaleSets"),
                Map.entry("vmSize", "Standard_DS2_v2")
            ))
            .apiServerAccessProfile(Map.ofEntries(
                Map.entry("enablePrivateCluster", true),
                Map.entry("enablePrivateClusterPublicFQDN", true)
            ))
            .autoScalerProfile(Map.ofEntries(
                Map.entry("scaleDownDelayAfterAdd", "15m"),
                Map.entry("scanInterval", "20s")
            ))
            .dnsPrefix("dnsprefix1")
            .enablePodSecurityPolicy(true)
            .enableRBAC(true)
            .kubernetesVersion("")
            .linuxProfile(Map.ofEntries(
                Map.entry("adminUsername", "azureuser"),
                Map.entry("ssh", Map.of("publicKeys", Map.of("keyData", "keydata")))
            ))
            .location("location1")
            .networkProfile(Map.ofEntries(
                Map.entry("loadBalancerProfile", Map.of("managedOutboundIPs", Map.of("count", 2))),
                Map.entry("loadBalancerSku", "standard"),
                Map.entry("outboundType", "loadBalancer")
            ))
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .servicePrincipalProfile(Map.ofEntries(
                Map.entry("clientId", "clientid"),
                Map.entry("secret", "secret")
            ))
            .sku(Map.ofEntries(
                Map.entry("name", "Basic"),
                Map.entry("tier", "Free")
            ))
            .tags(Map.ofEntries(
                Map.entry("archv2", ""),
                Map.entry("tier", "production")
            ))
            .windowsProfile(Map.ofEntries(
                Map.entry("adminPassword", "replacePassword1234$"),
                Map.entry("adminUsername", "azureuser")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedCluster = new azure_native.containerservice.ManagedCluster("managedCluster", {
    addonProfiles: {},
    agentPoolProfiles: [{
        count: 3,
        enableEncryptionAtHost: true,
        enableNodePublicIP: true,
        mode: "System",
        name: "nodepool1",
        osType: "Linux",
        type: "VirtualMachineScaleSets",
        vmSize: "Standard_DS2_v2",
    }],
    apiServerAccessProfile: {
        enablePrivateCluster: true,
        enablePrivateClusterPublicFQDN: true,
    },
    autoScalerProfile: {
        scaleDownDelayAfterAdd: "15m",
        scanInterval: "20s",
    },
    dnsPrefix: "dnsprefix1",
    enablePodSecurityPolicy: true,
    enableRBAC: true,
    kubernetesVersion: "",
    linuxProfile: {
        adminUsername: "azureuser",
        ssh: {
            publicKeys: [{
                keyData: "keydata",
            }],
        },
    },
    location: "location1",
    networkProfile: {
        loadBalancerProfile: {
            managedOutboundIPs: {
                count: 2,
            },
        },
        loadBalancerSku: "standard",
        outboundType: "loadBalancer",
    },
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    servicePrincipalProfile: {
        clientId: "clientid",
        secret: "secret",
    },
    sku: {
        name: "Basic",
        tier: "Free",
    },
    tags: {
        archv2: "",
        tier: "production",
    },
    windowsProfile: {
        adminPassword: "replacePassword1234$",
        adminUsername: "azureuser",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_cluster = azure_native.containerservice.ManagedCluster("managedCluster",
    addon_profiles={},
    agent_pool_profiles=[azure_native.containerservice.ManagedClusterAgentPoolProfileArgs(
        count=3,
        enable_encryption_at_host=True,
        enable_node_public_ip=True,
        mode="System",
        name="nodepool1",
        os_type="Linux",
        type="VirtualMachineScaleSets",
        vm_size="Standard_DS2_v2",
    )],
    api_server_access_profile=azure_native.containerservice.ManagedClusterAPIServerAccessProfileArgs(
        enable_private_cluster=True,
        enable_private_cluster_public_fqdn=True,
    ),
    auto_scaler_profile=azure_native.containerservice.ManagedClusterPropertiesAutoScalerProfileArgs(
        scale_down_delay_after_add="15m",
        scan_interval="20s",
    ),
    dns_prefix="dnsprefix1",
    enable_pod_security_policy=True,
    enable_rbac=True,
    kubernetes_version="",
    linux_profile=azure_native.containerservice.ContainerServiceLinuxProfileResponseArgs(
        admin_username="azureuser",
        ssh={
            "publicKeys": [azure_native.containerservice.ContainerServiceSshPublicKeyArgs(
                key_data="keydata",
            )],
        },
    ),
    location="location1",
    network_profile=azure_native.containerservice.ContainerServiceNetworkProfileResponseArgs(
        load_balancer_profile={
            "managedOutboundIPs": azure_native.containerservice.ManagedClusterLoadBalancerProfileManagedOutboundIPsArgs(
                count=2,
            ),
        },
        load_balancer_sku="standard",
        outbound_type="loadBalancer",
    ),
    resource_group_name="rg1",
    resource_name_="clustername1",
    service_principal_profile=azure_native.containerservice.ManagedClusterServicePrincipalProfileArgs(
        client_id="clientid",
        secret="secret",
    ),
    sku=azure_native.containerservice.ManagedClusterSKUArgs(
        name="Basic",
        tier="Free",
    ),
    tags={
        "archv2": "",
        "tier": "production",
    },
    windows_profile=azure_native.containerservice.ManagedClusterWindowsProfileArgs(
        admin_password="replacePassword1234$",
        admin_username="azureuser",
    ))

```

```yaml
resources:
  managedCluster:
    type: azure-native:containerservice:ManagedCluster
    properties:
      addonProfiles: {}
      agentPoolProfiles:
        - count: 3
          enableEncryptionAtHost: true
          enableNodePublicIP: true
          mode: System
          name: nodepool1
          osType: Linux
          type: VirtualMachineScaleSets
          vmSize: Standard_DS2_v2
      apiServerAccessProfile:
        enablePrivateCluster: true
        enablePrivateClusterPublicFQDN: true
      autoScalerProfile:
        scaleDownDelayAfterAdd: 15m
        scanInterval: 20s
      dnsPrefix: dnsprefix1
      enablePodSecurityPolicy: true
      enableRBAC: true
      kubernetesVersion:
      linuxProfile:
        adminUsername: azureuser
        ssh:
          publicKeys:
            - keyData: keydata
      location: location1
      networkProfile:
        loadBalancerProfile:
          managedOutboundIPs:
            count: 2
        loadBalancerSku: standard
        outboundType: loadBalancer
      resourceGroupName: rg1
      resourceName: clustername1
      servicePrincipalProfile:
        clientId: clientid
        secret: secret
      sku:
        name: Basic
        tier: Free
      tags:
        archv2:
        tier: production
      windowsProfile:
        adminPassword: replacePassword1234$
        adminUsername: azureuser

```

{{% /example %}}
{{% example %}}
### Create Managed Private Cluster with fqdn subdomain specified
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedCluster = new AzureNative.ContainerService.ManagedCluster("managedCluster", new()
    {
        AddonProfiles = null,
        AgentPoolProfiles = new[]
        {
            new AzureNative.ContainerService.Inputs.ManagedClusterAgentPoolProfileArgs
            {
                Count = 3,
                EnableEncryptionAtHost = true,
                EnableNodePublicIP = true,
                Mode = "System",
                Name = "nodepool1",
                OsType = "Linux",
                Type = "VirtualMachineScaleSets",
                VmSize = "Standard_DS2_v2",
            },
        },
        ApiServerAccessProfile = new AzureNative.ContainerService.Inputs.ManagedClusterAPIServerAccessProfileArgs
        {
            EnablePrivateCluster = true,
            PrivateDNSZone = "/subscriptions/subid1/resourcegroups/rg1/providers/Microsoft.Network/privateDnsZones/privatelink.location1.azmk8s.io",
        },
        AutoScalerProfile = new AzureNative.ContainerService.Inputs.ManagedClusterPropertiesAutoScalerProfileArgs
        {
            ScaleDownDelayAfterAdd = "15m",
            ScanInterval = "20s",
        },
        EnablePodSecurityPolicy = true,
        EnableRBAC = true,
        FqdnSubdomain = "domain1",
        KubernetesVersion = "",
        LinuxProfile = new AzureNative.ContainerService.Inputs.ContainerServiceLinuxProfileArgs
        {
            AdminUsername = "azureuser",
            Ssh = new AzureNative.ContainerService.Inputs.ContainerServiceSshConfigurationArgs
            {
                PublicKeys = new[]
                {
                    new AzureNative.ContainerService.Inputs.ContainerServiceSshPublicKeyArgs
                    {
                        KeyData = "keydata",
                    },
                },
            },
        },
        Location = "location1",
        NetworkProfile = new AzureNative.ContainerService.Inputs.ContainerServiceNetworkProfileArgs
        {
            LoadBalancerProfile = new AzureNative.ContainerService.Inputs.ManagedClusterLoadBalancerProfileArgs
            {
                ManagedOutboundIPs = new AzureNative.ContainerService.Inputs.ManagedClusterLoadBalancerProfileManagedOutboundIPsArgs
                {
                    Count = 2,
                },
            },
            LoadBalancerSku = "standard",
            OutboundType = "loadBalancer",
        },
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        ServicePrincipalProfile = new AzureNative.ContainerService.Inputs.ManagedClusterServicePrincipalProfileArgs
        {
            ClientId = "clientid",
            Secret = "secret",
        },
        Sku = new AzureNative.ContainerService.Inputs.ManagedClusterSKUArgs
        {
            Name = "Basic",
            Tier = "Free",
        },
        Tags = 
        {
            { "archv2", "" },
            { "tier", "production" },
        },
        WindowsProfile = new AzureNative.ContainerService.Inputs.ManagedClusterWindowsProfileArgs
        {
            AdminPassword = "replacePassword1234$",
            AdminUsername = "azureuser",
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.containerservice.ManagedCluster;
import com.pulumi.azurenative.containerservice.ManagedClusterArgs;
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
        var managedCluster = new ManagedCluster("managedCluster", ManagedClusterArgs.builder()        
            .addonProfiles()
            .agentPoolProfiles(Map.ofEntries(
                Map.entry("count", 3),
                Map.entry("enableEncryptionAtHost", true),
                Map.entry("enableNodePublicIP", true),
                Map.entry("mode", "System"),
                Map.entry("name", "nodepool1"),
                Map.entry("osType", "Linux"),
                Map.entry("type", "VirtualMachineScaleSets"),
                Map.entry("vmSize", "Standard_DS2_v2")
            ))
            .apiServerAccessProfile(Map.ofEntries(
                Map.entry("enablePrivateCluster", true),
                Map.entry("privateDNSZone", "/subscriptions/subid1/resourcegroups/rg1/providers/Microsoft.Network/privateDnsZones/privatelink.location1.azmk8s.io")
            ))
            .autoScalerProfile(Map.ofEntries(
                Map.entry("scaleDownDelayAfterAdd", "15m"),
                Map.entry("scanInterval", "20s")
            ))
            .enablePodSecurityPolicy(true)
            .enableRBAC(true)
            .fqdnSubdomain("domain1")
            .kubernetesVersion("")
            .linuxProfile(Map.ofEntries(
                Map.entry("adminUsername", "azureuser"),
                Map.entry("ssh", Map.of("publicKeys", Map.of("keyData", "keydata")))
            ))
            .location("location1")
            .networkProfile(Map.ofEntries(
                Map.entry("loadBalancerProfile", Map.of("managedOutboundIPs", Map.of("count", 2))),
                Map.entry("loadBalancerSku", "standard"),
                Map.entry("outboundType", "loadBalancer")
            ))
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .servicePrincipalProfile(Map.ofEntries(
                Map.entry("clientId", "clientid"),
                Map.entry("secret", "secret")
            ))
            .sku(Map.ofEntries(
                Map.entry("name", "Basic"),
                Map.entry("tier", "Free")
            ))
            .tags(Map.ofEntries(
                Map.entry("archv2", ""),
                Map.entry("tier", "production")
            ))
            .windowsProfile(Map.ofEntries(
                Map.entry("adminPassword", "replacePassword1234$"),
                Map.entry("adminUsername", "azureuser")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedCluster = new azure_native.containerservice.ManagedCluster("managedCluster", {
    addonProfiles: {},
    agentPoolProfiles: [{
        count: 3,
        enableEncryptionAtHost: true,
        enableNodePublicIP: true,
        mode: "System",
        name: "nodepool1",
        osType: "Linux",
        type: "VirtualMachineScaleSets",
        vmSize: "Standard_DS2_v2",
    }],
    apiServerAccessProfile: {
        enablePrivateCluster: true,
        privateDNSZone: "/subscriptions/subid1/resourcegroups/rg1/providers/Microsoft.Network/privateDnsZones/privatelink.location1.azmk8s.io",
    },
    autoScalerProfile: {
        scaleDownDelayAfterAdd: "15m",
        scanInterval: "20s",
    },
    enablePodSecurityPolicy: true,
    enableRBAC: true,
    fqdnSubdomain: "domain1",
    kubernetesVersion: "",
    linuxProfile: {
        adminUsername: "azureuser",
        ssh: {
            publicKeys: [{
                keyData: "keydata",
            }],
        },
    },
    location: "location1",
    networkProfile: {
        loadBalancerProfile: {
            managedOutboundIPs: {
                count: 2,
            },
        },
        loadBalancerSku: "standard",
        outboundType: "loadBalancer",
    },
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    servicePrincipalProfile: {
        clientId: "clientid",
        secret: "secret",
    },
    sku: {
        name: "Basic",
        tier: "Free",
    },
    tags: {
        archv2: "",
        tier: "production",
    },
    windowsProfile: {
        adminPassword: "replacePassword1234$",
        adminUsername: "azureuser",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_cluster = azure_native.containerservice.ManagedCluster("managedCluster",
    addon_profiles={},
    agent_pool_profiles=[azure_native.containerservice.ManagedClusterAgentPoolProfileArgs(
        count=3,
        enable_encryption_at_host=True,
        enable_node_public_ip=True,
        mode="System",
        name="nodepool1",
        os_type="Linux",
        type="VirtualMachineScaleSets",
        vm_size="Standard_DS2_v2",
    )],
    api_server_access_profile=azure_native.containerservice.ManagedClusterAPIServerAccessProfileArgs(
        enable_private_cluster=True,
        private_dns_zone="/subscriptions/subid1/resourcegroups/rg1/providers/Microsoft.Network/privateDnsZones/privatelink.location1.azmk8s.io",
    ),
    auto_scaler_profile=azure_native.containerservice.ManagedClusterPropertiesAutoScalerProfileArgs(
        scale_down_delay_after_add="15m",
        scan_interval="20s",
    ),
    enable_pod_security_policy=True,
    enable_rbac=True,
    fqdn_subdomain="domain1",
    kubernetes_version="",
    linux_profile=azure_native.containerservice.ContainerServiceLinuxProfileResponseArgs(
        admin_username="azureuser",
        ssh={
            "publicKeys": [azure_native.containerservice.ContainerServiceSshPublicKeyArgs(
                key_data="keydata",
            )],
        },
    ),
    location="location1",
    network_profile=azure_native.containerservice.ContainerServiceNetworkProfileResponseArgs(
        load_balancer_profile={
            "managedOutboundIPs": azure_native.containerservice.ManagedClusterLoadBalancerProfileManagedOutboundIPsArgs(
                count=2,
            ),
        },
        load_balancer_sku="standard",
        outbound_type="loadBalancer",
    ),
    resource_group_name="rg1",
    resource_name_="clustername1",
    service_principal_profile=azure_native.containerservice.ManagedClusterServicePrincipalProfileArgs(
        client_id="clientid",
        secret="secret",
    ),
    sku=azure_native.containerservice.ManagedClusterSKUArgs(
        name="Basic",
        tier="Free",
    ),
    tags={
        "archv2": "",
        "tier": "production",
    },
    windows_profile=azure_native.containerservice.ManagedClusterWindowsProfileArgs(
        admin_password="replacePassword1234$",
        admin_username="azureuser",
    ))

```

```yaml
resources:
  managedCluster:
    type: azure-native:containerservice:ManagedCluster
    properties:
      addonProfiles: {}
      agentPoolProfiles:
        - count: 3
          enableEncryptionAtHost: true
          enableNodePublicIP: true
          mode: System
          name: nodepool1
          osType: Linux
          type: VirtualMachineScaleSets
          vmSize: Standard_DS2_v2
      apiServerAccessProfile:
        enablePrivateCluster: true
        privateDNSZone: /subscriptions/subid1/resourcegroups/rg1/providers/Microsoft.Network/privateDnsZones/privatelink.location1.azmk8s.io
      autoScalerProfile:
        scaleDownDelayAfterAdd: 15m
        scanInterval: 20s
      enablePodSecurityPolicy: true
      enableRBAC: true
      fqdnSubdomain: domain1
      kubernetesVersion:
      linuxProfile:
        adminUsername: azureuser
        ssh:
          publicKeys:
            - keyData: keydata
      location: location1
      networkProfile:
        loadBalancerProfile:
          managedOutboundIPs:
            count: 2
        loadBalancerSku: standard
        outboundType: loadBalancer
      resourceGroupName: rg1
      resourceName: clustername1
      servicePrincipalProfile:
        clientId: clientid
        secret: secret
      sku:
        name: Basic
        tier: Free
      tags:
        archv2:
        tier: production
      windowsProfile:
        adminPassword: replacePassword1234$
        adminUsername: azureuser

```

{{% /example %}}
{{% example %}}
### Create/Update AAD Managed Cluster with EnableAzureRBAC
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedCluster = new AzureNative.ContainerService.ManagedCluster("managedCluster", new()
    {
        AadProfile = new AzureNative.ContainerService.Inputs.ManagedClusterAADProfileArgs
        {
            EnableAzureRBAC = true,
            Managed = true,
        },
        AddonProfiles = null,
        AgentPoolProfiles = new[]
        {
            new AzureNative.ContainerService.Inputs.ManagedClusterAgentPoolProfileArgs
            {
                AvailabilityZones = new[]
                {
                    "1",
                    "2",
                    "3",
                },
                Count = 3,
                EnableNodePublicIP = true,
                Mode = "System",
                Name = "nodepool1",
                OsType = "Linux",
                Type = "VirtualMachineScaleSets",
                VmSize = "Standard_DS1_v2",
            },
        },
        AutoScalerProfile = new AzureNative.ContainerService.Inputs.ManagedClusterPropertiesAutoScalerProfileArgs
        {
            ScaleDownDelayAfterAdd = "15m",
            ScanInterval = "20s",
        },
        DiskEncryptionSetID = "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
        DnsPrefix = "dnsprefix1",
        EnablePodSecurityPolicy = true,
        EnableRBAC = true,
        KubernetesVersion = "",
        LinuxProfile = new AzureNative.ContainerService.Inputs.ContainerServiceLinuxProfileArgs
        {
            AdminUsername = "azureuser",
            Ssh = new AzureNative.ContainerService.Inputs.ContainerServiceSshConfigurationArgs
            {
                PublicKeys = new[]
                {
                    new AzureNative.ContainerService.Inputs.ContainerServiceSshPublicKeyArgs
                    {
                        KeyData = "keydata",
                    },
                },
            },
        },
        Location = "location1",
        NetworkProfile = new AzureNative.ContainerService.Inputs.ContainerServiceNetworkProfileArgs
        {
            LoadBalancerProfile = new AzureNative.ContainerService.Inputs.ManagedClusterLoadBalancerProfileArgs
            {
                ManagedOutboundIPs = new AzureNative.ContainerService.Inputs.ManagedClusterLoadBalancerProfileManagedOutboundIPsArgs
                {
                    Count = 2,
                },
            },
            LoadBalancerSku = "standard",
            OutboundType = "loadBalancer",
        },
        ResourceGroupName = "rg1",
        ResourceName = "clustername1",
        ServicePrincipalProfile = new AzureNative.ContainerService.Inputs.ManagedClusterServicePrincipalProfileArgs
        {
            ClientId = "clientid",
            Secret = "secret",
        },
        Sku = new AzureNative.ContainerService.Inputs.ManagedClusterSKUArgs
        {
            Name = "Basic",
            Tier = "Free",
        },
        Tags = 
        {
            { "archv2", "" },
            { "tier", "production" },
        },
        WindowsProfile = new AzureNative.ContainerService.Inputs.ManagedClusterWindowsProfileArgs
        {
            AdminPassword = "replacePassword1234$",
            AdminUsername = "azureuser",
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.containerservice.ManagedCluster;
import com.pulumi.azurenative.containerservice.ManagedClusterArgs;
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
        var managedCluster = new ManagedCluster("managedCluster", ManagedClusterArgs.builder()        
            .aadProfile(Map.ofEntries(
                Map.entry("enableAzureRBAC", true),
                Map.entry("managed", true)
            ))
            .addonProfiles()
            .agentPoolProfiles(Map.ofEntries(
                Map.entry("availabilityZones",                 
                    "1",
                    "2",
                    "3"),
                Map.entry("count", 3),
                Map.entry("enableNodePublicIP", true),
                Map.entry("mode", "System"),
                Map.entry("name", "nodepool1"),
                Map.entry("osType", "Linux"),
                Map.entry("type", "VirtualMachineScaleSets"),
                Map.entry("vmSize", "Standard_DS1_v2")
            ))
            .autoScalerProfile(Map.ofEntries(
                Map.entry("scaleDownDelayAfterAdd", "15m"),
                Map.entry("scanInterval", "20s")
            ))
            .diskEncryptionSetID("/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des")
            .dnsPrefix("dnsprefix1")
            .enablePodSecurityPolicy(true)
            .enableRBAC(true)
            .kubernetesVersion("")
            .linuxProfile(Map.ofEntries(
                Map.entry("adminUsername", "azureuser"),
                Map.entry("ssh", Map.of("publicKeys", Map.of("keyData", "keydata")))
            ))
            .location("location1")
            .networkProfile(Map.ofEntries(
                Map.entry("loadBalancerProfile", Map.of("managedOutboundIPs", Map.of("count", 2))),
                Map.entry("loadBalancerSku", "standard"),
                Map.entry("outboundType", "loadBalancer")
            ))
            .resourceGroupName("rg1")
            .resourceName("clustername1")
            .servicePrincipalProfile(Map.ofEntries(
                Map.entry("clientId", "clientid"),
                Map.entry("secret", "secret")
            ))
            .sku(Map.ofEntries(
                Map.entry("name", "Basic"),
                Map.entry("tier", "Free")
            ))
            .tags(Map.ofEntries(
                Map.entry("archv2", ""),
                Map.entry("tier", "production")
            ))
            .windowsProfile(Map.ofEntries(
                Map.entry("adminPassword", "replacePassword1234$"),
                Map.entry("adminUsername", "azureuser")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedCluster = new azure_native.containerservice.ManagedCluster("managedCluster", {
    aadProfile: {
        enableAzureRBAC: true,
        managed: true,
    },
    addonProfiles: {},
    agentPoolProfiles: [{
        availabilityZones: [
            "1",
            "2",
            "3",
        ],
        count: 3,
        enableNodePublicIP: true,
        mode: "System",
        name: "nodepool1",
        osType: "Linux",
        type: "VirtualMachineScaleSets",
        vmSize: "Standard_DS1_v2",
    }],
    autoScalerProfile: {
        scaleDownDelayAfterAdd: "15m",
        scanInterval: "20s",
    },
    diskEncryptionSetID: "/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
    dnsPrefix: "dnsprefix1",
    enablePodSecurityPolicy: true,
    enableRBAC: true,
    kubernetesVersion: "",
    linuxProfile: {
        adminUsername: "azureuser",
        ssh: {
            publicKeys: [{
                keyData: "keydata",
            }],
        },
    },
    location: "location1",
    networkProfile: {
        loadBalancerProfile: {
            managedOutboundIPs: {
                count: 2,
            },
        },
        loadBalancerSku: "standard",
        outboundType: "loadBalancer",
    },
    resourceGroupName: "rg1",
    resourceName: "clustername1",
    servicePrincipalProfile: {
        clientId: "clientid",
        secret: "secret",
    },
    sku: {
        name: "Basic",
        tier: "Free",
    },
    tags: {
        archv2: "",
        tier: "production",
    },
    windowsProfile: {
        adminPassword: "replacePassword1234$",
        adminUsername: "azureuser",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_cluster = azure_native.containerservice.ManagedCluster("managedCluster",
    aad_profile=azure_native.containerservice.ManagedClusterAADProfileArgs(
        enable_azure_rbac=True,
        managed=True,
    ),
    addon_profiles={},
    agent_pool_profiles=[azure_native.containerservice.ManagedClusterAgentPoolProfileArgs(
        availability_zones=[
            "1",
            "2",
            "3",
        ],
        count=3,
        enable_node_public_ip=True,
        mode="System",
        name="nodepool1",
        os_type="Linux",
        type="VirtualMachineScaleSets",
        vm_size="Standard_DS1_v2",
    )],
    auto_scaler_profile=azure_native.containerservice.ManagedClusterPropertiesAutoScalerProfileArgs(
        scale_down_delay_after_add="15m",
        scan_interval="20s",
    ),
    disk_encryption_set_id="/subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des",
    dns_prefix="dnsprefix1",
    enable_pod_security_policy=True,
    enable_rbac=True,
    kubernetes_version="",
    linux_profile=azure_native.containerservice.ContainerServiceLinuxProfileResponseArgs(
        admin_username="azureuser",
        ssh={
            "publicKeys": [azure_native.containerservice.ContainerServiceSshPublicKeyArgs(
                key_data="keydata",
            )],
        },
    ),
    location="location1",
    network_profile=azure_native.containerservice.ContainerServiceNetworkProfileResponseArgs(
        load_balancer_profile={
            "managedOutboundIPs": azure_native.containerservice.ManagedClusterLoadBalancerProfileManagedOutboundIPsArgs(
                count=2,
            ),
        },
        load_balancer_sku="standard",
        outbound_type="loadBalancer",
    ),
    resource_group_name="rg1",
    resource_name_="clustername1",
    service_principal_profile=azure_native.containerservice.ManagedClusterServicePrincipalProfileArgs(
        client_id="clientid",
        secret="secret",
    ),
    sku=azure_native.containerservice.ManagedClusterSKUArgs(
        name="Basic",
        tier="Free",
    ),
    tags={
        "archv2": "",
        "tier": "production",
    },
    windows_profile=azure_native.containerservice.ManagedClusterWindowsProfileArgs(
        admin_password="replacePassword1234$",
        admin_username="azureuser",
    ))

```

```yaml
resources:
  managedCluster:
    type: azure-native:containerservice:ManagedCluster
    properties:
      aadProfile:
        enableAzureRBAC: true
        managed: true
      addonProfiles: {}
      agentPoolProfiles:
        - availabilityZones:
            - '1'
            - '2'
            - '3'
          count: 3
          enableNodePublicIP: true
          mode: System
          name: nodepool1
          osType: Linux
          type: VirtualMachineScaleSets
          vmSize: Standard_DS1_v2
      autoScalerProfile:
        scaleDownDelayAfterAdd: 15m
        scanInterval: 20s
      diskEncryptionSetID: /subscriptions/subid1/resourceGroups/rg1/providers/Microsoft.Compute/diskEncryptionSets/des
      dnsPrefix: dnsprefix1
      enablePodSecurityPolicy: true
      enableRBAC: true
      kubernetesVersion:
      linuxProfile:
        adminUsername: azureuser
        ssh:
          publicKeys:
            - keyData: keydata
      location: location1
      networkProfile:
        loadBalancerProfile:
          managedOutboundIPs:
            count: 2
        loadBalancerSku: standard
        outboundType: loadBalancer
      resourceGroupName: rg1
      resourceName: clustername1
      servicePrincipalProfile:
        clientId: clientid
        secret: secret
      sku:
        name: Basic
        tier: Free
      tags:
        archv2:
        tier: production
      windowsProfile:
        adminPassword: replacePassword1234$
        adminUsername: azureuser

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:containerservice:ManagedCluster clustername1 /subscriptions/subid1/resourcegroups/rg1/providers/Microsoft.ContainerService/managedClusters/clustername1 
```
