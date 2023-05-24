Contains information about a pool.
API Version: 2022-10-01.
Previous API Version: 2021-01-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CreatePool - Custom Image
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var pool = new AzureNative.Batch.Pool("pool", new()
    {
        AccountName = "sampleacct",
        DeploymentConfiguration = new AzureNative.Batch.Inputs.DeploymentConfigurationArgs
        {
            VirtualMachineConfiguration = new AzureNative.Batch.Inputs.VirtualMachineConfigurationArgs
            {
                ImageReference = new AzureNative.Batch.Inputs.ImageReferenceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/networking-group/providers/Microsoft.Compute/galleries/testgallery/images/testimagedef/versions/0.0.1",
                },
                NodeAgentSkuId = "batch.node.ubuntu 18.04",
            },
        },
        PoolName = "testpool",
        ResourceGroupName = "default-azurebatch-japaneast",
        VmSize = "STANDARD_D4",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.batch.Pool;
import com.pulumi.azurenative.batch.PoolArgs;
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
        var pool = new Pool("pool", PoolArgs.builder()        
            .accountName("sampleacct")
            .deploymentConfiguration(Map.of("virtualMachineConfiguration", Map.ofEntries(
                Map.entry("imageReference", Map.of("id", "/subscriptions/subid/resourceGroups/networking-group/providers/Microsoft.Compute/galleries/testgallery/images/testimagedef/versions/0.0.1")),
                Map.entry("nodeAgentSkuId", "batch.node.ubuntu 18.04")
            )))
            .poolName("testpool")
            .resourceGroupName("default-azurebatch-japaneast")
            .vmSize("STANDARD_D4")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const pool = new azure_native.batch.Pool("pool", {
    accountName: "sampleacct",
    deploymentConfiguration: {
        virtualMachineConfiguration: {
            imageReference: {
                id: "/subscriptions/subid/resourceGroups/networking-group/providers/Microsoft.Compute/galleries/testgallery/images/testimagedef/versions/0.0.1",
            },
            nodeAgentSkuId: "batch.node.ubuntu 18.04",
        },
    },
    poolName: "testpool",
    resourceGroupName: "default-azurebatch-japaneast",
    vmSize: "STANDARD_D4",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

pool = azure_native.batch.Pool("pool",
    account_name="sampleacct",
    deployment_configuration=azure_native.batch.DeploymentConfigurationResponseArgs(
        virtual_machine_configuration={
            "imageReference": azure_native.batch.ImageReferenceArgs(
                id="/subscriptions/subid/resourceGroups/networking-group/providers/Microsoft.Compute/galleries/testgallery/images/testimagedef/versions/0.0.1",
            ),
            "nodeAgentSkuId": "batch.node.ubuntu 18.04",
        },
    ),
    pool_name="testpool",
    resource_group_name="default-azurebatch-japaneast",
    vm_size="STANDARD_D4")

```

```yaml
resources:
  pool:
    type: azure-native:batch:Pool
    properties:
      accountName: sampleacct
      deploymentConfiguration:
        virtualMachineConfiguration:
          imageReference:
            id: /subscriptions/subid/resourceGroups/networking-group/providers/Microsoft.Compute/galleries/testgallery/images/testimagedef/versions/0.0.1
          nodeAgentSkuId: batch.node.ubuntu 18.04
      poolName: testpool
      resourceGroupName: default-azurebatch-japaneast
      vmSize: STANDARD_D4

```

{{% /example %}}
{{% example %}}
### CreatePool - Full CloudServiceConfiguration
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var pool = new AzureNative.Batch.Pool("pool", new()
    {
        AccountName = "sampleacct",
        ApplicationLicenses = new[]
        {
            "app-license0",
            "app-license1",
        },
        ApplicationPackages = new[]
        {
            new AzureNative.Batch.Inputs.ApplicationPackageReferenceArgs
            {
                Id = "/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Batch/batchAccounts/sampleacct/pools/testpool/applications/app_1234",
                Version = "asdf",
            },
        },
        Certificates = new[]
        {
            new AzureNative.Batch.Inputs.CertificateReferenceArgs
            {
                Id = "/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Batch/batchAccounts/sampleacct/pools/testpool/certificates/sha1-1234567",
                StoreLocation = AzureNative.Batch.CertificateStoreLocation.LocalMachine,
                StoreName = "MY",
                Visibility = new[]
                {
                    AzureNative.Batch.CertificateVisibility.RemoteUser,
                },
            },
        },
        DeploymentConfiguration = new AzureNative.Batch.Inputs.DeploymentConfigurationArgs
        {
            CloudServiceConfiguration = new AzureNative.Batch.Inputs.CloudServiceConfigurationArgs
            {
                OsFamily = "4",
                OsVersion = "WA-GUEST-OS-4.45_201708-01",
            },
        },
        DisplayName = "my-pool-name",
        InterNodeCommunication = AzureNative.Batch.InterNodeCommunicationState.Enabled,
        Metadata = new[]
        {
            new AzureNative.Batch.Inputs.MetadataItemArgs
            {
                Name = "metadata-1",
                Value = "value-1",
            },
            new AzureNative.Batch.Inputs.MetadataItemArgs
            {
                Name = "metadata-2",
                Value = "value-2",
            },
        },
        NetworkConfiguration = new AzureNative.Batch.Inputs.NetworkConfigurationArgs
        {
            PublicIPAddressConfiguration = new AzureNative.Batch.Inputs.PublicIPAddressConfigurationArgs
            {
                IpAddressIds = new[]
                {
                    "/subscriptions/subid1/resourceGroups/rg13/providers/Microsoft.Network/publicIPAddresses/ip135",
                    "/subscriptions/subid2/resourceGroups/rg24/providers/Microsoft.Network/publicIPAddresses/ip268",
                },
                Provision = AzureNative.Batch.IPAddressProvisioningType.UserManaged,
            },
            SubnetId = "/subscriptions/subid/resourceGroups/rg1234/providers/Microsoft.Network/virtualNetworks/network1234/subnets/subnet123",
        },
        PoolName = "testpool",
        ResourceGroupName = "default-azurebatch-japaneast",
        ScaleSettings = new AzureNative.Batch.Inputs.ScaleSettingsArgs
        {
            FixedScale = new AzureNative.Batch.Inputs.FixedScaleSettingsArgs
            {
                NodeDeallocationOption = AzureNative.Batch.ComputeNodeDeallocationOption.TaskCompletion,
                ResizeTimeout = "PT8M",
                TargetDedicatedNodes = 6,
                TargetLowPriorityNodes = 28,
            },
        },
        StartTask = new AzureNative.Batch.Inputs.StartTaskArgs
        {
            CommandLine = "cmd /c SET",
            EnvironmentSettings = new[]
            {
                new AzureNative.Batch.Inputs.EnvironmentSettingArgs
                {
                    Name = "MYSET",
                    Value = "1234",
                },
            },
            MaxTaskRetryCount = 6,
            ResourceFiles = new[]
            {
                new AzureNative.Batch.Inputs.ResourceFileArgs
                {
                    FileMode = "777",
                    FilePath = "c:\\temp\\gohere",
                    HttpUrl = "https://testaccount.blob.core.windows.net/example-blob-file",
                },
            },
            UserIdentity = new AzureNative.Batch.Inputs.UserIdentityArgs
            {
                AutoUser = new AzureNative.Batch.Inputs.AutoUserSpecificationArgs
                {
                    ElevationLevel = AzureNative.Batch.ElevationLevel.Admin,
                    Scope = AzureNative.Batch.AutoUserScope.Pool,
                },
            },
            WaitForSuccess = true,
        },
        TaskSchedulingPolicy = new AzureNative.Batch.Inputs.TaskSchedulingPolicyArgs
        {
            NodeFillType = AzureNative.Batch.ComputeNodeFillType.Pack,
        },
        TaskSlotsPerNode = 13,
        UserAccounts = new[]
        {
            new AzureNative.Batch.Inputs.UserAccountArgs
            {
                ElevationLevel = AzureNative.Batch.ElevationLevel.Admin,
                LinuxUserConfiguration = new AzureNative.Batch.Inputs.LinuxUserConfigurationArgs
                {
                    Gid = 4567,
                    SshPrivateKey = "sshprivatekeyvalue",
                    Uid = 1234,
                },
                Name = "username1",
                Password = "<ExamplePassword>",
            },
        },
        VmSize = "STANDARD_D4",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.batch.Pool;
import com.pulumi.azurenative.batch.PoolArgs;
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
        var pool = new Pool("pool", PoolArgs.builder()        
            .accountName("sampleacct")
            .applicationLicenses(            
                "app-license0",
                "app-license1")
            .applicationPackages(Map.ofEntries(
                Map.entry("id", "/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Batch/batchAccounts/sampleacct/pools/testpool/applications/app_1234"),
                Map.entry("version", "asdf")
            ))
            .certificates(Map.ofEntries(
                Map.entry("id", "/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Batch/batchAccounts/sampleacct/pools/testpool/certificates/sha1-1234567"),
                Map.entry("storeLocation", "LocalMachine"),
                Map.entry("storeName", "MY"),
                Map.entry("visibility", "RemoteUser")
            ))
            .deploymentConfiguration(Map.of("cloudServiceConfiguration", Map.ofEntries(
                Map.entry("osFamily", "4"),
                Map.entry("osVersion", "WA-GUEST-OS-4.45_201708-01")
            )))
            .displayName("my-pool-name")
            .interNodeCommunication("Enabled")
            .metadata(            
                Map.ofEntries(
                    Map.entry("name", "metadata-1"),
                    Map.entry("value", "value-1")
                ),
                Map.ofEntries(
                    Map.entry("name", "metadata-2"),
                    Map.entry("value", "value-2")
                ))
            .networkConfiguration(Map.ofEntries(
                Map.entry("publicIPAddressConfiguration", Map.ofEntries(
                    Map.entry("ipAddressIds",                     
                        "/subscriptions/subid1/resourceGroups/rg13/providers/Microsoft.Network/publicIPAddresses/ip135",
                        "/subscriptions/subid2/resourceGroups/rg24/providers/Microsoft.Network/publicIPAddresses/ip268"),
                    Map.entry("provision", "UserManaged")
                )),
                Map.entry("subnetId", "/subscriptions/subid/resourceGroups/rg1234/providers/Microsoft.Network/virtualNetworks/network1234/subnets/subnet123")
            ))
            .poolName("testpool")
            .resourceGroupName("default-azurebatch-japaneast")
            .scaleSettings(Map.of("fixedScale", Map.ofEntries(
                Map.entry("nodeDeallocationOption", "TaskCompletion"),
                Map.entry("resizeTimeout", "PT8M"),
                Map.entry("targetDedicatedNodes", 6),
                Map.entry("targetLowPriorityNodes", 28)
            )))
            .startTask(Map.ofEntries(
                Map.entry("commandLine", "cmd /c SET"),
                Map.entry("environmentSettings", Map.ofEntries(
                    Map.entry("name", "MYSET"),
                    Map.entry("value", "1234")
                )),
                Map.entry("maxTaskRetryCount", 6),
                Map.entry("resourceFiles", Map.ofEntries(
                    Map.entry("fileMode", "777"),
                    Map.entry("filePath", "c:\\temp\\gohere"),
                    Map.entry("httpUrl", "https://testaccount.blob.core.windows.net/example-blob-file")
                )),
                Map.entry("userIdentity", Map.of("autoUser", Map.ofEntries(
                    Map.entry("elevationLevel", "Admin"),
                    Map.entry("scope", "Pool")
                ))),
                Map.entry("waitForSuccess", true)
            ))
            .taskSchedulingPolicy(Map.of("nodeFillType", "Pack"))
            .taskSlotsPerNode(13)
            .userAccounts(Map.ofEntries(
                Map.entry("elevationLevel", "Admin"),
                Map.entry("linuxUserConfiguration", Map.ofEntries(
                    Map.entry("gid", 4567),
                    Map.entry("sshPrivateKey", "sshprivatekeyvalue"),
                    Map.entry("uid", 1234)
                )),
                Map.entry("name", "username1"),
                Map.entry("password", "<ExamplePassword>")
            ))
            .vmSize("STANDARD_D4")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const pool = new azure_native.batch.Pool("pool", {
    accountName: "sampleacct",
    applicationLicenses: [
        "app-license0",
        "app-license1",
    ],
    applicationPackages: [{
        id: "/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Batch/batchAccounts/sampleacct/pools/testpool/applications/app_1234",
        version: "asdf",
    }],
    certificates: [{
        id: "/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Batch/batchAccounts/sampleacct/pools/testpool/certificates/sha1-1234567",
        storeLocation: azure_native.batch.CertificateStoreLocation.LocalMachine,
        storeName: "MY",
        visibility: [azure_native.batch.CertificateVisibility.RemoteUser],
    }],
    deploymentConfiguration: {
        cloudServiceConfiguration: {
            osFamily: "4",
            osVersion: "WA-GUEST-OS-4.45_201708-01",
        },
    },
    displayName: "my-pool-name",
    interNodeCommunication: azure_native.batch.InterNodeCommunicationState.Enabled,
    metadata: [
        {
            name: "metadata-1",
            value: "value-1",
        },
        {
            name: "metadata-2",
            value: "value-2",
        },
    ],
    networkConfiguration: {
        publicIPAddressConfiguration: {
            ipAddressIds: [
                "/subscriptions/subid1/resourceGroups/rg13/providers/Microsoft.Network/publicIPAddresses/ip135",
                "/subscriptions/subid2/resourceGroups/rg24/providers/Microsoft.Network/publicIPAddresses/ip268",
            ],
            provision: azure_native.batch.IPAddressProvisioningType.UserManaged,
        },
        subnetId: "/subscriptions/subid/resourceGroups/rg1234/providers/Microsoft.Network/virtualNetworks/network1234/subnets/subnet123",
    },
    poolName: "testpool",
    resourceGroupName: "default-azurebatch-japaneast",
    scaleSettings: {
        fixedScale: {
            nodeDeallocationOption: azure_native.batch.ComputeNodeDeallocationOption.TaskCompletion,
            resizeTimeout: "PT8M",
            targetDedicatedNodes: 6,
            targetLowPriorityNodes: 28,
        },
    },
    startTask: {
        commandLine: "cmd /c SET",
        environmentSettings: [{
            name: "MYSET",
            value: "1234",
        }],
        maxTaskRetryCount: 6,
        resourceFiles: [{
            fileMode: "777",
            filePath: "c:\\temp\\gohere",
            httpUrl: "https://testaccount.blob.core.windows.net/example-blob-file",
        }],
        userIdentity: {
            autoUser: {
                elevationLevel: azure_native.batch.ElevationLevel.Admin,
                scope: azure_native.batch.AutoUserScope.Pool,
            },
        },
        waitForSuccess: true,
    },
    taskSchedulingPolicy: {
        nodeFillType: azure_native.batch.ComputeNodeFillType.Pack,
    },
    taskSlotsPerNode: 13,
    userAccounts: [{
        elevationLevel: azure_native.batch.ElevationLevel.Admin,
        linuxUserConfiguration: {
            gid: 4567,
            sshPrivateKey: "sshprivatekeyvalue",
            uid: 1234,
        },
        name: "username1",
        password: "<ExamplePassword>",
    }],
    vmSize: "STANDARD_D4",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

pool = azure_native.batch.Pool("pool",
    account_name="sampleacct",
    application_licenses=[
        "app-license0",
        "app-license1",
    ],
    application_packages=[azure_native.batch.ApplicationPackageReferenceArgs(
        id="/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Batch/batchAccounts/sampleacct/pools/testpool/applications/app_1234",
        version="asdf",
    )],
    certificates=[azure_native.batch.CertificateReferenceArgs(
        id="/subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Batch/batchAccounts/sampleacct/pools/testpool/certificates/sha1-1234567",
        store_location=azure_native.batch.CertificateStoreLocation.LOCAL_MACHINE,
        store_name="MY",
        visibility=[azure_native.batch.CertificateVisibility.REMOTE_USER],
    )],
    deployment_configuration=azure_native.batch.DeploymentConfigurationResponseArgs(
        cloud_service_configuration=azure_native.batch.CloudServiceConfigurationArgs(
            os_family="4",
            os_version="WA-GUEST-OS-4.45_201708-01",
        ),
    ),
    display_name="my-pool-name",
    inter_node_communication=azure_native.batch.InterNodeCommunicationState.ENABLED,
    metadata=[
        azure_native.batch.MetadataItemArgs(
            name="metadata-1",
            value="value-1",
        ),
        azure_native.batch.MetadataItemArgs(
            name="metadata-2",
            value="value-2",
        ),
    ],
    network_configuration=azure_native.batch.NetworkConfigurationResponseArgs(
        public_ip_address_configuration=azure_native.batch.PublicIPAddressConfigurationArgs(
            ip_address_ids=[
                "/subscriptions/subid1/resourceGroups/rg13/providers/Microsoft.Network/publicIPAddresses/ip135",
                "/subscriptions/subid2/resourceGroups/rg24/providers/Microsoft.Network/publicIPAddresses/ip268",
            ],
            provision=azure_native.batch.IPAddressProvisioningType.USER_MANAGED,
        ),
        subnet_id="/subscriptions/subid/resourceGroups/rg1234/providers/Microsoft.Network/virtualNetworks/network1234/subnets/subnet123",
    ),
    pool_name="testpool",
    resource_group_name="default-azurebatch-japaneast",
    scale_settings=azure_native.batch.ScaleSettingsResponseArgs(
        fixed_scale=azure_native.batch.FixedScaleSettingsArgs(
            node_deallocation_option=azure_native.batch.ComputeNodeDeallocationOption.TASK_COMPLETION,
            resize_timeout="PT8M",
            target_dedicated_nodes=6,
            target_low_priority_nodes=28,
        ),
    ),
    start_task=azure_native.batch.StartTaskResponseArgs(
        command_line="cmd /c SET",
        environment_settings=[azure_native.batch.EnvironmentSettingArgs(
            name="MYSET",
            value="1234",
        )],
        max_task_retry_count=6,
        resource_files=[azure_native.batch.ResourceFileArgs(
            file_mode="777",
            file_path="c:\\temp\\gohere",
            http_url="https://testaccount.blob.core.windows.net/example-blob-file",
        )],
        user_identity={
            "autoUser": azure_native.batch.AutoUserSpecificationArgs(
                elevation_level=azure_native.batch.ElevationLevel.ADMIN,
                scope=azure_native.batch.AutoUserScope.POOL,
            ),
        },
        wait_for_success=True,
    ),
    task_scheduling_policy=azure_native.batch.TaskSchedulingPolicyArgs(
        node_fill_type=azure_native.batch.ComputeNodeFillType.PACK,
    ),
    task_slots_per_node=13,
    user_accounts=[{
        "elevationLevel": azure_native.batch.ElevationLevel.ADMIN,
        "linuxUserConfiguration": azure_native.batch.LinuxUserConfigurationArgs(
            gid=4567,
            ssh_private_key="sshprivatekeyvalue",
            uid=1234,
        ),
        "name": "username1",
        "password": "<ExamplePassword>",
    }],
    vm_size="STANDARD_D4")

```

```yaml
resources:
  pool:
    type: azure-native:batch:Pool
    properties:
      accountName: sampleacct
      applicationLicenses:
        - app-license0
        - app-license1
      applicationPackages:
        - id: /subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Batch/batchAccounts/sampleacct/pools/testpool/applications/app_1234
          version: asdf
      certificates:
        - id: /subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Batch/batchAccounts/sampleacct/pools/testpool/certificates/sha1-1234567
          storeLocation: LocalMachine
          storeName: MY
          visibility:
            - RemoteUser
      deploymentConfiguration:
        cloudServiceConfiguration:
          osFamily: '4'
          osVersion: WA-GUEST-OS-4.45_201708-01
      displayName: my-pool-name
      interNodeCommunication: Enabled
      metadata:
        - name: metadata-1
          value: value-1
        - name: metadata-2
          value: value-2
      networkConfiguration:
        publicIPAddressConfiguration:
          ipAddressIds:
            - /subscriptions/subid1/resourceGroups/rg13/providers/Microsoft.Network/publicIPAddresses/ip135
            - /subscriptions/subid2/resourceGroups/rg24/providers/Microsoft.Network/publicIPAddresses/ip268
          provision: UserManaged
        subnetId: /subscriptions/subid/resourceGroups/rg1234/providers/Microsoft.Network/virtualNetworks/network1234/subnets/subnet123
      poolName: testpool
      resourceGroupName: default-azurebatch-japaneast
      scaleSettings:
        fixedScale:
          nodeDeallocationOption: TaskCompletion
          resizeTimeout: PT8M
          targetDedicatedNodes: 6
          targetLowPriorityNodes: 28
      startTask:
        commandLine: cmd /c SET
        environmentSettings:
          - name: MYSET
            value: '1234'
        maxTaskRetryCount: 6
        resourceFiles:
          - fileMode: '777'
            filePath: c:\temp\gohere
            httpUrl: https://testaccount.blob.core.windows.net/example-blob-file
        userIdentity:
          autoUser:
            elevationLevel: Admin
            scope: Pool
        waitForSuccess: true
      taskSchedulingPolicy:
        nodeFillType: Pack
      taskSlotsPerNode: 13
      userAccounts:
        - elevationLevel: Admin
          linuxUserConfiguration:
            gid: 4567
            sshPrivateKey: sshprivatekeyvalue
            uid: 1234
          name: username1
          password: <ExamplePassword>
      vmSize: STANDARD_D4

```

{{% /example %}}
{{% example %}}
### CreatePool - Full VirtualMachineConfiguration
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var pool = new AzureNative.Batch.Pool("pool", new()
    {
        AccountName = "sampleacct",
        DeploymentConfiguration = new AzureNative.Batch.Inputs.DeploymentConfigurationArgs
        {
            VirtualMachineConfiguration = new AzureNative.Batch.Inputs.VirtualMachineConfigurationArgs
            {
                DataDisks = new[]
                {
                    new AzureNative.Batch.Inputs.DataDiskArgs
                    {
                        Caching = AzureNative.Batch.CachingType.ReadWrite,
                        DiskSizeGB = 30,
                        Lun = 0,
                        StorageAccountType = AzureNative.Batch.StorageAccountType.Premium_LRS,
                    },
                    new AzureNative.Batch.Inputs.DataDiskArgs
                    {
                        Caching = AzureNative.Batch.CachingType.None,
                        DiskSizeGB = 200,
                        Lun = 1,
                        StorageAccountType = AzureNative.Batch.StorageAccountType.Standard_LRS,
                    },
                },
                DiskEncryptionConfiguration = new AzureNative.Batch.Inputs.DiskEncryptionConfigurationArgs
                {
                    Targets = new[]
                    {
                        AzureNative.Batch.DiskEncryptionTarget.OsDisk,
                        AzureNative.Batch.DiskEncryptionTarget.TemporaryDisk,
                    },
                },
                ImageReference = new AzureNative.Batch.Inputs.ImageReferenceArgs
                {
                    Offer = "WindowsServer",
                    Publisher = "MicrosoftWindowsServer",
                    Sku = "2016-Datacenter-SmallDisk",
                    Version = "latest",
                },
                LicenseType = "Windows_Server",
                NodeAgentSkuId = "batch.node.windows amd64",
                NodePlacementConfiguration = new AzureNative.Batch.Inputs.NodePlacementConfigurationArgs
                {
                    Policy = AzureNative.Batch.NodePlacementPolicyType.Zonal,
                },
                OsDisk = new AzureNative.Batch.Inputs.OSDiskArgs
                {
                    EphemeralOSDiskSettings = new AzureNative.Batch.Inputs.DiffDiskSettingsArgs
                    {
                        Placement = AzureNative.Batch.DiffDiskPlacement.CacheDisk,
                    },
                },
                WindowsConfiguration = new AzureNative.Batch.Inputs.WindowsConfigurationArgs
                {
                    EnableAutomaticUpdates = false,
                },
            },
        },
        NetworkConfiguration = new AzureNative.Batch.Inputs.NetworkConfigurationArgs
        {
            EndpointConfiguration = new AzureNative.Batch.Inputs.PoolEndpointConfigurationArgs
            {
                InboundNatPools = new[]
                {
                    new AzureNative.Batch.Inputs.InboundNatPoolArgs
                    {
                        BackendPort = 12001,
                        FrontendPortRangeEnd = 15100,
                        FrontendPortRangeStart = 15000,
                        Name = "testnat",
                        NetworkSecurityGroupRules = new[]
                        {
                            new AzureNative.Batch.Inputs.NetworkSecurityGroupRuleArgs
                            {
                                Access = AzureNative.Batch.NetworkSecurityGroupRuleAccess.Allow,
                                Priority = 150,
                                SourceAddressPrefix = "192.100.12.45",
                                SourcePortRanges = new[]
                                {
                                    "1",
                                    "2",
                                },
                            },
                            new AzureNative.Batch.Inputs.NetworkSecurityGroupRuleArgs
                            {
                                Access = AzureNative.Batch.NetworkSecurityGroupRuleAccess.Deny,
                                Priority = 3500,
                                SourceAddressPrefix = "*",
                                SourcePortRanges = new[]
                                {
                                    "*",
                                },
                            },
                        },
                        Protocol = AzureNative.Batch.InboundEndpointProtocol.TCP,
                    },
                },
            },
        },
        PoolName = "testpool",
        ResourceGroupName = "default-azurebatch-japaneast",
        ScaleSettings = new AzureNative.Batch.Inputs.ScaleSettingsArgs
        {
            AutoScale = new AzureNative.Batch.Inputs.AutoScaleSettingsArgs
            {
                EvaluationInterval = "PT5M",
                Formula = "$TargetDedicatedNodes=1",
            },
        },
        VmSize = "STANDARD_D4",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.batch.Pool;
import com.pulumi.azurenative.batch.PoolArgs;
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
        var pool = new Pool("pool", PoolArgs.builder()        
            .accountName("sampleacct")
            .deploymentConfiguration(Map.of("virtualMachineConfiguration", Map.ofEntries(
                Map.entry("dataDisks",                 
                    Map.ofEntries(
                        Map.entry("caching", "ReadWrite"),
                        Map.entry("diskSizeGB", 30),
                        Map.entry("lun", 0),
                        Map.entry("storageAccountType", "Premium_LRS")
                    ),
                    Map.ofEntries(
                        Map.entry("caching", "None"),
                        Map.entry("diskSizeGB", 200),
                        Map.entry("lun", 1),
                        Map.entry("storageAccountType", "Standard_LRS")
                    )),
                Map.entry("diskEncryptionConfiguration", Map.of("targets",                 
                    "OsDisk",
                    "TemporaryDisk")),
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "WindowsServer"),
                    Map.entry("publisher", "MicrosoftWindowsServer"),
                    Map.entry("sku", "2016-Datacenter-SmallDisk"),
                    Map.entry("version", "latest")
                )),
                Map.entry("licenseType", "Windows_Server"),
                Map.entry("nodeAgentSkuId", "batch.node.windows amd64"),
                Map.entry("nodePlacementConfiguration", Map.of("policy", "Zonal")),
                Map.entry("osDisk", Map.of("ephemeralOSDiskSettings", Map.of("placement", "CacheDisk"))),
                Map.entry("windowsConfiguration", Map.of("enableAutomaticUpdates", false))
            )))
            .networkConfiguration(Map.of("endpointConfiguration", Map.of("inboundNatPools", Map.ofEntries(
                Map.entry("backendPort", 12001),
                Map.entry("frontendPortRangeEnd", 15100),
                Map.entry("frontendPortRangeStart", 15000),
                Map.entry("name", "testnat"),
                Map.entry("networkSecurityGroupRules",                 
                    Map.ofEntries(
                        Map.entry("access", "Allow"),
                        Map.entry("priority", 150),
                        Map.entry("sourceAddressPrefix", "192.100.12.45"),
                        Map.entry("sourcePortRanges",                         
                            "1",
                            "2")
                    ),
                    Map.ofEntries(
                        Map.entry("access", "Deny"),
                        Map.entry("priority", 3500),
                        Map.entry("sourceAddressPrefix", "*"),
                        Map.entry("sourcePortRanges", "*")
                    )),
                Map.entry("protocol", "TCP")
            ))))
            .poolName("testpool")
            .resourceGroupName("default-azurebatch-japaneast")
            .scaleSettings(Map.of("autoScale", Map.ofEntries(
                Map.entry("evaluationInterval", "PT5M"),
                Map.entry("formula", "$TargetDedicatedNodes=1")
            )))
            .vmSize("STANDARD_D4")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const pool = new azure_native.batch.Pool("pool", {
    accountName: "sampleacct",
    deploymentConfiguration: {
        virtualMachineConfiguration: {
            dataDisks: [
                {
                    caching: azure_native.batch.CachingType.ReadWrite,
                    diskSizeGB: 30,
                    lun: 0,
                    storageAccountType: azure_native.batch.StorageAccountType.Premium_LRS,
                },
                {
                    caching: azure_native.batch.CachingType.None,
                    diskSizeGB: 200,
                    lun: 1,
                    storageAccountType: azure_native.batch.StorageAccountType.Standard_LRS,
                },
            ],
            diskEncryptionConfiguration: {
                targets: [
                    azure_native.batch.DiskEncryptionTarget.OsDisk,
                    azure_native.batch.DiskEncryptionTarget.TemporaryDisk,
                ],
            },
            imageReference: {
                offer: "WindowsServer",
                publisher: "MicrosoftWindowsServer",
                sku: "2016-Datacenter-SmallDisk",
                version: "latest",
            },
            licenseType: "Windows_Server",
            nodeAgentSkuId: "batch.node.windows amd64",
            nodePlacementConfiguration: {
                policy: azure_native.batch.NodePlacementPolicyType.Zonal,
            },
            osDisk: {
                ephemeralOSDiskSettings: {
                    placement: azure_native.batch.DiffDiskPlacement.CacheDisk,
                },
            },
            windowsConfiguration: {
                enableAutomaticUpdates: false,
            },
        },
    },
    networkConfiguration: {
        endpointConfiguration: {
            inboundNatPools: [{
                backendPort: 12001,
                frontendPortRangeEnd: 15100,
                frontendPortRangeStart: 15000,
                name: "testnat",
                networkSecurityGroupRules: [
                    {
                        access: azure_native.batch.NetworkSecurityGroupRuleAccess.Allow,
                        priority: 150,
                        sourceAddressPrefix: "192.100.12.45",
                        sourcePortRanges: [
                            "1",
                            "2",
                        ],
                    },
                    {
                        access: azure_native.batch.NetworkSecurityGroupRuleAccess.Deny,
                        priority: 3500,
                        sourceAddressPrefix: "*",
                        sourcePortRanges: ["*"],
                    },
                ],
                protocol: azure_native.batch.InboundEndpointProtocol.TCP,
            }],
        },
    },
    poolName: "testpool",
    resourceGroupName: "default-azurebatch-japaneast",
    scaleSettings: {
        autoScale: {
            evaluationInterval: "PT5M",
            formula: "$TargetDedicatedNodes=1",
        },
    },
    vmSize: "STANDARD_D4",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

pool = azure_native.batch.Pool("pool",
    account_name="sampleacct",
    deployment_configuration=azure_native.batch.DeploymentConfigurationResponseArgs(
        virtual_machine_configuration={
            "dataDisks": [
                azure_native.batch.DataDiskArgs(
                    caching=azure_native.batch.CachingType.READ_WRITE,
                    disk_size_gb=30,
                    lun=0,
                    storage_account_type=azure_native.batch.StorageAccountType.PREMIUM_LRS,
                ),
                azure_native.batch.DataDiskArgs(
                    caching=azure_native.batch.CachingType.NONE,
                    disk_size_gb=200,
                    lun=1,
                    storage_account_type=azure_native.batch.StorageAccountType.STANDARD_LRS,
                ),
            ],
            "diskEncryptionConfiguration": azure_native.batch.DiskEncryptionConfigurationArgs(
                targets=[
                    azure_native.batch.DiskEncryptionTarget.OS_DISK,
                    azure_native.batch.DiskEncryptionTarget.TEMPORARY_DISK,
                ],
            ),
            "imageReference": azure_native.batch.ImageReferenceArgs(
                offer="WindowsServer",
                publisher="MicrosoftWindowsServer",
                sku="2016-Datacenter-SmallDisk",
                version="latest",
            ),
            "licenseType": "Windows_Server",
            "nodeAgentSkuId": "batch.node.windows amd64",
            "nodePlacementConfiguration": azure_native.batch.NodePlacementConfigurationArgs(
                policy=azure_native.batch.NodePlacementPolicyType.ZONAL,
            ),
            "osDisk": {
                "ephemeralOSDiskSettings": azure_native.batch.DiffDiskSettingsArgs(
                    placement=azure_native.batch.DiffDiskPlacement.CACHE_DISK,
                ),
            },
            "windowsConfiguration": azure_native.batch.WindowsConfigurationArgs(
                enable_automatic_updates=False,
            ),
        },
    ),
    network_configuration=azure_native.batch.NetworkConfigurationResponseArgs(
        endpoint_configuration={
            "inboundNatPools": [{
                "backendPort": 12001,
                "frontendPortRangeEnd": 15100,
                "frontendPortRangeStart": 15000,
                "name": "testnat",
                "networkSecurityGroupRules": [
                    azure_native.batch.NetworkSecurityGroupRuleArgs(
                        access=azure_native.batch.NetworkSecurityGroupRuleAccess.ALLOW,
                        priority=150,
                        source_address_prefix="192.100.12.45",
                        source_port_ranges=[
                            "1",
                            "2",
                        ],
                    ),
                    azure_native.batch.NetworkSecurityGroupRuleArgs(
                        access=azure_native.batch.NetworkSecurityGroupRuleAccess.DENY,
                        priority=3500,
                        source_address_prefix="*",
                        source_port_ranges=["*"],
                    ),
                ],
                "protocol": azure_native.batch.InboundEndpointProtocol.TCP,
            }],
        },
    ),
    pool_name="testpool",
    resource_group_name="default-azurebatch-japaneast",
    scale_settings=azure_native.batch.ScaleSettingsResponseArgs(
        auto_scale=azure_native.batch.AutoScaleSettingsArgs(
            evaluation_interval="PT5M",
            formula="$TargetDedicatedNodes=1",
        ),
    ),
    vm_size="STANDARD_D4")

```

```yaml
resources:
  pool:
    type: azure-native:batch:Pool
    properties:
      accountName: sampleacct
      deploymentConfiguration:
        virtualMachineConfiguration:
          dataDisks:
            - caching: ReadWrite
              diskSizeGB: 30
              lun: 0
              storageAccountType: Premium_LRS
            - caching: None
              diskSizeGB: 200
              lun: 1
              storageAccountType: Standard_LRS
          diskEncryptionConfiguration:
            targets:
              - OsDisk
              - TemporaryDisk
          imageReference:
            offer: WindowsServer
            publisher: MicrosoftWindowsServer
            sku: 2016-Datacenter-SmallDisk
            version: latest
          licenseType: Windows_Server
          nodeAgentSkuId: batch.node.windows amd64
          nodePlacementConfiguration:
            policy: Zonal
          osDisk:
            ephemeralOSDiskSettings:
              placement: CacheDisk
          windowsConfiguration:
            enableAutomaticUpdates: false
      networkConfiguration:
        endpointConfiguration:
          inboundNatPools:
            - backendPort: 12001
              frontendPortRangeEnd: 15100
              frontendPortRangeStart: 15000
              name: testnat
              networkSecurityGroupRules:
                - access: Allow
                  priority: 150
                  sourceAddressPrefix: 192.100.12.45
                  sourcePortRanges:
                    - '1'
                    - '2'
                - access: Deny
                  priority: 3500
                  sourceAddressPrefix: '*'
                  sourcePortRanges:
                    - '*'
              protocol: TCP
      poolName: testpool
      resourceGroupName: default-azurebatch-japaneast
      scaleSettings:
        autoScale:
          evaluationInterval: PT5M
          formula: $TargetDedicatedNodes=1
      vmSize: STANDARD_D4

```

{{% /example %}}
{{% example %}}
### CreatePool - Minimal CloudServiceConfiguration
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var pool = new AzureNative.Batch.Pool("pool", new()
    {
        AccountName = "sampleacct",
        DeploymentConfiguration = new AzureNative.Batch.Inputs.DeploymentConfigurationArgs
        {
            CloudServiceConfiguration = new AzureNative.Batch.Inputs.CloudServiceConfigurationArgs
            {
                OsFamily = "5",
            },
        },
        PoolName = "testpool",
        ResourceGroupName = "default-azurebatch-japaneast",
        ScaleSettings = new AzureNative.Batch.Inputs.ScaleSettingsArgs
        {
            FixedScale = new AzureNative.Batch.Inputs.FixedScaleSettingsArgs
            {
                TargetDedicatedNodes = 3,
            },
        },
        VmSize = "STANDARD_D4",
    });

});


```

```go
package main

import (
	batch "github.com/pulumi/pulumi-azure-native-sdk/batch"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := batch.NewPool(ctx, "pool", &batch.PoolArgs{
			AccountName: pulumi.String("sampleacct"),
			DeploymentConfiguration: batch.DeploymentConfigurationResponse{
				CloudServiceConfiguration: &batch.CloudServiceConfigurationArgs{
					OsFamily: pulumi.String("5"),
				},
			},
			PoolName:          pulumi.String("testpool"),
			ResourceGroupName: pulumi.String("default-azurebatch-japaneast"),
			ScaleSettings: batch.ScaleSettingsResponse{
				FixedScale: &batch.FixedScaleSettingsArgs{
					TargetDedicatedNodes: pulumi.Int(3),
				},
			},
			VmSize: pulumi.String("STANDARD_D4"),
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
import com.pulumi.azurenative.batch.Pool;
import com.pulumi.azurenative.batch.PoolArgs;
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
        var pool = new Pool("pool", PoolArgs.builder()        
            .accountName("sampleacct")
            .deploymentConfiguration(Map.of("cloudServiceConfiguration", Map.of("osFamily", "5")))
            .poolName("testpool")
            .resourceGroupName("default-azurebatch-japaneast")
            .scaleSettings(Map.of("fixedScale", Map.of("targetDedicatedNodes", 3)))
            .vmSize("STANDARD_D4")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const pool = new azure_native.batch.Pool("pool", {
    accountName: "sampleacct",
    deploymentConfiguration: {
        cloudServiceConfiguration: {
            osFamily: "5",
        },
    },
    poolName: "testpool",
    resourceGroupName: "default-azurebatch-japaneast",
    scaleSettings: {
        fixedScale: {
            targetDedicatedNodes: 3,
        },
    },
    vmSize: "STANDARD_D4",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

pool = azure_native.batch.Pool("pool",
    account_name="sampleacct",
    deployment_configuration=azure_native.batch.DeploymentConfigurationResponseArgs(
        cloud_service_configuration=azure_native.batch.CloudServiceConfigurationArgs(
            os_family="5",
        ),
    ),
    pool_name="testpool",
    resource_group_name="default-azurebatch-japaneast",
    scale_settings=azure_native.batch.ScaleSettingsResponseArgs(
        fixed_scale=azure_native.batch.FixedScaleSettingsArgs(
            target_dedicated_nodes=3,
        ),
    ),
    vm_size="STANDARD_D4")

```

```yaml
resources:
  pool:
    type: azure-native:batch:Pool
    properties:
      accountName: sampleacct
      deploymentConfiguration:
        cloudServiceConfiguration:
          osFamily: '5'
      poolName: testpool
      resourceGroupName: default-azurebatch-japaneast
      scaleSettings:
        fixedScale:
          targetDedicatedNodes: 3
      vmSize: STANDARD_D4

```

{{% /example %}}
{{% example %}}
### CreatePool - Minimal VirtualMachineConfiguration
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var pool = new AzureNative.Batch.Pool("pool", new()
    {
        AccountName = "sampleacct",
        DeploymentConfiguration = new AzureNative.Batch.Inputs.DeploymentConfigurationArgs
        {
            VirtualMachineConfiguration = new AzureNative.Batch.Inputs.VirtualMachineConfigurationArgs
            {
                ImageReference = new AzureNative.Batch.Inputs.ImageReferenceArgs
                {
                    Offer = "UbuntuServer",
                    Publisher = "Canonical",
                    Sku = "18.04-LTS",
                    Version = "latest",
                },
                NodeAgentSkuId = "batch.node.ubuntu 18.04",
            },
        },
        PoolName = "testpool",
        ResourceGroupName = "default-azurebatch-japaneast",
        ScaleSettings = new AzureNative.Batch.Inputs.ScaleSettingsArgs
        {
            AutoScale = new AzureNative.Batch.Inputs.AutoScaleSettingsArgs
            {
                EvaluationInterval = "PT5M",
                Formula = "$TargetDedicatedNodes=1",
            },
        },
        VmSize = "STANDARD_D4",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.batch.Pool;
import com.pulumi.azurenative.batch.PoolArgs;
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
        var pool = new Pool("pool", PoolArgs.builder()        
            .accountName("sampleacct")
            .deploymentConfiguration(Map.of("virtualMachineConfiguration", Map.ofEntries(
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "UbuntuServer"),
                    Map.entry("publisher", "Canonical"),
                    Map.entry("sku", "18.04-LTS"),
                    Map.entry("version", "latest")
                )),
                Map.entry("nodeAgentSkuId", "batch.node.ubuntu 18.04")
            )))
            .poolName("testpool")
            .resourceGroupName("default-azurebatch-japaneast")
            .scaleSettings(Map.of("autoScale", Map.ofEntries(
                Map.entry("evaluationInterval", "PT5M"),
                Map.entry("formula", "$TargetDedicatedNodes=1")
            )))
            .vmSize("STANDARD_D4")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const pool = new azure_native.batch.Pool("pool", {
    accountName: "sampleacct",
    deploymentConfiguration: {
        virtualMachineConfiguration: {
            imageReference: {
                offer: "UbuntuServer",
                publisher: "Canonical",
                sku: "18.04-LTS",
                version: "latest",
            },
            nodeAgentSkuId: "batch.node.ubuntu 18.04",
        },
    },
    poolName: "testpool",
    resourceGroupName: "default-azurebatch-japaneast",
    scaleSettings: {
        autoScale: {
            evaluationInterval: "PT5M",
            formula: "$TargetDedicatedNodes=1",
        },
    },
    vmSize: "STANDARD_D4",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

pool = azure_native.batch.Pool("pool",
    account_name="sampleacct",
    deployment_configuration=azure_native.batch.DeploymentConfigurationResponseArgs(
        virtual_machine_configuration={
            "imageReference": azure_native.batch.ImageReferenceArgs(
                offer="UbuntuServer",
                publisher="Canonical",
                sku="18.04-LTS",
                version="latest",
            ),
            "nodeAgentSkuId": "batch.node.ubuntu 18.04",
        },
    ),
    pool_name="testpool",
    resource_group_name="default-azurebatch-japaneast",
    scale_settings=azure_native.batch.ScaleSettingsResponseArgs(
        auto_scale=azure_native.batch.AutoScaleSettingsArgs(
            evaluation_interval="PT5M",
            formula="$TargetDedicatedNodes=1",
        ),
    ),
    vm_size="STANDARD_D4")

```

```yaml
resources:
  pool:
    type: azure-native:batch:Pool
    properties:
      accountName: sampleacct
      deploymentConfiguration:
        virtualMachineConfiguration:
          imageReference:
            offer: UbuntuServer
            publisher: Canonical
            sku: 18.04-LTS
            version: latest
          nodeAgentSkuId: batch.node.ubuntu 18.04
      poolName: testpool
      resourceGroupName: default-azurebatch-japaneast
      scaleSettings:
        autoScale:
          evaluationInterval: PT5M
          formula: $TargetDedicatedNodes=1
      vmSize: STANDARD_D4

```

{{% /example %}}
{{% example %}}
### CreatePool - No public IP
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var pool = new AzureNative.Batch.Pool("pool", new()
    {
        AccountName = "sampleacct",
        DeploymentConfiguration = new AzureNative.Batch.Inputs.DeploymentConfigurationArgs
        {
            VirtualMachineConfiguration = new AzureNative.Batch.Inputs.VirtualMachineConfigurationArgs
            {
                ImageReference = new AzureNative.Batch.Inputs.ImageReferenceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/networking-group/providers/Microsoft.Compute/galleries/testgallery/images/testimagedef/versions/0.0.1",
                },
                NodeAgentSkuId = "batch.node.ubuntu 18.04",
            },
        },
        NetworkConfiguration = new AzureNative.Batch.Inputs.NetworkConfigurationArgs
        {
            PublicIPAddressConfiguration = new AzureNative.Batch.Inputs.PublicIPAddressConfigurationArgs
            {
                Provision = AzureNative.Batch.IPAddressProvisioningType.NoPublicIPAddresses,
            },
            SubnetId = "/subscriptions/subid/resourceGroups/rg1234/providers/Microsoft.Network/virtualNetworks/network1234/subnets/subnet123",
        },
        PoolName = "testpool",
        ResourceGroupName = "default-azurebatch-japaneast",
        VmSize = "STANDARD_D4",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.batch.Pool;
import com.pulumi.azurenative.batch.PoolArgs;
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
        var pool = new Pool("pool", PoolArgs.builder()        
            .accountName("sampleacct")
            .deploymentConfiguration(Map.of("virtualMachineConfiguration", Map.ofEntries(
                Map.entry("imageReference", Map.of("id", "/subscriptions/subid/resourceGroups/networking-group/providers/Microsoft.Compute/galleries/testgallery/images/testimagedef/versions/0.0.1")),
                Map.entry("nodeAgentSkuId", "batch.node.ubuntu 18.04")
            )))
            .networkConfiguration(Map.ofEntries(
                Map.entry("publicIPAddressConfiguration", Map.of("provision", "NoPublicIPAddresses")),
                Map.entry("subnetId", "/subscriptions/subid/resourceGroups/rg1234/providers/Microsoft.Network/virtualNetworks/network1234/subnets/subnet123")
            ))
            .poolName("testpool")
            .resourceGroupName("default-azurebatch-japaneast")
            .vmSize("STANDARD_D4")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const pool = new azure_native.batch.Pool("pool", {
    accountName: "sampleacct",
    deploymentConfiguration: {
        virtualMachineConfiguration: {
            imageReference: {
                id: "/subscriptions/subid/resourceGroups/networking-group/providers/Microsoft.Compute/galleries/testgallery/images/testimagedef/versions/0.0.1",
            },
            nodeAgentSkuId: "batch.node.ubuntu 18.04",
        },
    },
    networkConfiguration: {
        publicIPAddressConfiguration: {
            provision: azure_native.batch.IPAddressProvisioningType.NoPublicIPAddresses,
        },
        subnetId: "/subscriptions/subid/resourceGroups/rg1234/providers/Microsoft.Network/virtualNetworks/network1234/subnets/subnet123",
    },
    poolName: "testpool",
    resourceGroupName: "default-azurebatch-japaneast",
    vmSize: "STANDARD_D4",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

pool = azure_native.batch.Pool("pool",
    account_name="sampleacct",
    deployment_configuration=azure_native.batch.DeploymentConfigurationResponseArgs(
        virtual_machine_configuration={
            "imageReference": azure_native.batch.ImageReferenceArgs(
                id="/subscriptions/subid/resourceGroups/networking-group/providers/Microsoft.Compute/galleries/testgallery/images/testimagedef/versions/0.0.1",
            ),
            "nodeAgentSkuId": "batch.node.ubuntu 18.04",
        },
    ),
    network_configuration=azure_native.batch.NetworkConfigurationResponseArgs(
        public_ip_address_configuration=azure_native.batch.PublicIPAddressConfigurationArgs(
            provision=azure_native.batch.IPAddressProvisioningType.NO_PUBLIC_IP_ADDRESSES,
        ),
        subnet_id="/subscriptions/subid/resourceGroups/rg1234/providers/Microsoft.Network/virtualNetworks/network1234/subnets/subnet123",
    ),
    pool_name="testpool",
    resource_group_name="default-azurebatch-japaneast",
    vm_size="STANDARD_D4")

```

```yaml
resources:
  pool:
    type: azure-native:batch:Pool
    properties:
      accountName: sampleacct
      deploymentConfiguration:
        virtualMachineConfiguration:
          imageReference:
            id: /subscriptions/subid/resourceGroups/networking-group/providers/Microsoft.Compute/galleries/testgallery/images/testimagedef/versions/0.0.1
          nodeAgentSkuId: batch.node.ubuntu 18.04
      networkConfiguration:
        publicIPAddressConfiguration:
          provision: NoPublicIPAddresses
        subnetId: /subscriptions/subid/resourceGroups/rg1234/providers/Microsoft.Network/virtualNetworks/network1234/subnets/subnet123
      poolName: testpool
      resourceGroupName: default-azurebatch-japaneast
      vmSize: STANDARD_D4

```

{{% /example %}}
{{% example %}}
### CreatePool - Public IPs
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var pool = new AzureNative.Batch.Pool("pool", new()
    {
        AccountName = "sampleacct",
        DeploymentConfiguration = new AzureNative.Batch.Inputs.DeploymentConfigurationArgs
        {
            VirtualMachineConfiguration = new AzureNative.Batch.Inputs.VirtualMachineConfigurationArgs
            {
                ImageReference = new AzureNative.Batch.Inputs.ImageReferenceArgs
                {
                    Id = "/subscriptions/subid/resourceGroups/networking-group/providers/Microsoft.Compute/galleries/testgallery/images/testimagedef/versions/0.0.1",
                },
                NodeAgentSkuId = "batch.node.ubuntu 18.04",
            },
        },
        NetworkConfiguration = new AzureNative.Batch.Inputs.NetworkConfigurationArgs
        {
            PublicIPAddressConfiguration = new AzureNative.Batch.Inputs.PublicIPAddressConfigurationArgs
            {
                IpAddressIds = new[]
                {
                    "/subscriptions/subid1/resourceGroups/rg13/providers/Microsoft.Network/publicIPAddresses/ip135",
                },
                Provision = AzureNative.Batch.IPAddressProvisioningType.UserManaged,
            },
            SubnetId = "/subscriptions/subid/resourceGroups/rg1234/providers/Microsoft.Network/virtualNetworks/network1234/subnets/subnet123",
        },
        PoolName = "testpool",
        ResourceGroupName = "default-azurebatch-japaneast",
        VmSize = "STANDARD_D4",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.batch.Pool;
import com.pulumi.azurenative.batch.PoolArgs;
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
        var pool = new Pool("pool", PoolArgs.builder()        
            .accountName("sampleacct")
            .deploymentConfiguration(Map.of("virtualMachineConfiguration", Map.ofEntries(
                Map.entry("imageReference", Map.of("id", "/subscriptions/subid/resourceGroups/networking-group/providers/Microsoft.Compute/galleries/testgallery/images/testimagedef/versions/0.0.1")),
                Map.entry("nodeAgentSkuId", "batch.node.ubuntu 18.04")
            )))
            .networkConfiguration(Map.ofEntries(
                Map.entry("publicIPAddressConfiguration", Map.ofEntries(
                    Map.entry("ipAddressIds", "/subscriptions/subid1/resourceGroups/rg13/providers/Microsoft.Network/publicIPAddresses/ip135"),
                    Map.entry("provision", "UserManaged")
                )),
                Map.entry("subnetId", "/subscriptions/subid/resourceGroups/rg1234/providers/Microsoft.Network/virtualNetworks/network1234/subnets/subnet123")
            ))
            .poolName("testpool")
            .resourceGroupName("default-azurebatch-japaneast")
            .vmSize("STANDARD_D4")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const pool = new azure_native.batch.Pool("pool", {
    accountName: "sampleacct",
    deploymentConfiguration: {
        virtualMachineConfiguration: {
            imageReference: {
                id: "/subscriptions/subid/resourceGroups/networking-group/providers/Microsoft.Compute/galleries/testgallery/images/testimagedef/versions/0.0.1",
            },
            nodeAgentSkuId: "batch.node.ubuntu 18.04",
        },
    },
    networkConfiguration: {
        publicIPAddressConfiguration: {
            ipAddressIds: ["/subscriptions/subid1/resourceGroups/rg13/providers/Microsoft.Network/publicIPAddresses/ip135"],
            provision: azure_native.batch.IPAddressProvisioningType.UserManaged,
        },
        subnetId: "/subscriptions/subid/resourceGroups/rg1234/providers/Microsoft.Network/virtualNetworks/network1234/subnets/subnet123",
    },
    poolName: "testpool",
    resourceGroupName: "default-azurebatch-japaneast",
    vmSize: "STANDARD_D4",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

pool = azure_native.batch.Pool("pool",
    account_name="sampleacct",
    deployment_configuration=azure_native.batch.DeploymentConfigurationResponseArgs(
        virtual_machine_configuration={
            "imageReference": azure_native.batch.ImageReferenceArgs(
                id="/subscriptions/subid/resourceGroups/networking-group/providers/Microsoft.Compute/galleries/testgallery/images/testimagedef/versions/0.0.1",
            ),
            "nodeAgentSkuId": "batch.node.ubuntu 18.04",
        },
    ),
    network_configuration=azure_native.batch.NetworkConfigurationResponseArgs(
        public_ip_address_configuration=azure_native.batch.PublicIPAddressConfigurationArgs(
            ip_address_ids=["/subscriptions/subid1/resourceGroups/rg13/providers/Microsoft.Network/publicIPAddresses/ip135"],
            provision=azure_native.batch.IPAddressProvisioningType.USER_MANAGED,
        ),
        subnet_id="/subscriptions/subid/resourceGroups/rg1234/providers/Microsoft.Network/virtualNetworks/network1234/subnets/subnet123",
    ),
    pool_name="testpool",
    resource_group_name="default-azurebatch-japaneast",
    vm_size="STANDARD_D4")

```

```yaml
resources:
  pool:
    type: azure-native:batch:Pool
    properties:
      accountName: sampleacct
      deploymentConfiguration:
        virtualMachineConfiguration:
          imageReference:
            id: /subscriptions/subid/resourceGroups/networking-group/providers/Microsoft.Compute/galleries/testgallery/images/testimagedef/versions/0.0.1
          nodeAgentSkuId: batch.node.ubuntu 18.04
      networkConfiguration:
        publicIPAddressConfiguration:
          ipAddressIds:
            - /subscriptions/subid1/resourceGroups/rg13/providers/Microsoft.Network/publicIPAddresses/ip135
          provision: UserManaged
        subnetId: /subscriptions/subid/resourceGroups/rg1234/providers/Microsoft.Network/virtualNetworks/network1234/subnets/subnet123
      poolName: testpool
      resourceGroupName: default-azurebatch-japaneast
      vmSize: STANDARD_D4

```

{{% /example %}}
{{% example %}}
### CreatePool - VirtualMachineConfiguration Extensions
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var pool = new AzureNative.Batch.Pool("pool", new()
    {
        AccountName = "sampleacct",
        DeploymentConfiguration = new AzureNative.Batch.Inputs.DeploymentConfigurationArgs
        {
            VirtualMachineConfiguration = new AzureNative.Batch.Inputs.VirtualMachineConfigurationArgs
            {
                Extensions = new[]
                {
                    new AzureNative.Batch.Inputs.VMExtensionArgs
                    {
                        AutoUpgradeMinorVersion = true,
                        Name = "batchextension1",
                        ProtectedSettings = 
                        {
                            { "protectedSettingsKey", "protectedSettingsValue" },
                        },
                        Publisher = "Microsoft.Azure.Security.Monitoring",
                        Settings = 
                        {
                            { "settingsKey", "settingsValue" },
                        },
                        Type = "SecurityMonitoringForLinux",
                        TypeHandlerVersion = "1.0",
                    },
                },
                ImageReference = new AzureNative.Batch.Inputs.ImageReferenceArgs
                {
                    Offer = "0001-com-ubuntu-server-focal",
                    Publisher = "Canonical",
                    Sku = "20_04-lts",
                },
                NodeAgentSkuId = "batch.node.ubuntu 20.04",
            },
        },
        PoolName = "testpool",
        ResourceGroupName = "default-azurebatch-japaneast",
        ScaleSettings = new AzureNative.Batch.Inputs.ScaleSettingsArgs
        {
            AutoScale = new AzureNative.Batch.Inputs.AutoScaleSettingsArgs
            {
                EvaluationInterval = "PT5M",
                Formula = "$TargetDedicatedNodes=1",
            },
        },
        TargetNodeCommunicationMode = AzureNative.Batch.NodeCommunicationMode.Default,
        VmSize = "STANDARD_D4",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.batch.Pool;
import com.pulumi.azurenative.batch.PoolArgs;
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
        var pool = new Pool("pool", PoolArgs.builder()        
            .accountName("sampleacct")
            .deploymentConfiguration(Map.of("virtualMachineConfiguration", Map.ofEntries(
                Map.entry("extensions", Map.ofEntries(
                    Map.entry("autoUpgradeMinorVersion", true),
                    Map.entry("name", "batchextension1"),
                    Map.entry("protectedSettings", Map.of("protectedSettingsKey", "protectedSettingsValue")),
                    Map.entry("publisher", "Microsoft.Azure.Security.Monitoring"),
                    Map.entry("settings", Map.of("settingsKey", "settingsValue")),
                    Map.entry("type", "SecurityMonitoringForLinux"),
                    Map.entry("typeHandlerVersion", "1.0")
                )),
                Map.entry("imageReference", Map.ofEntries(
                    Map.entry("offer", "0001-com-ubuntu-server-focal"),
                    Map.entry("publisher", "Canonical"),
                    Map.entry("sku", "20_04-lts")
                )),
                Map.entry("nodeAgentSkuId", "batch.node.ubuntu 20.04")
            )))
            .poolName("testpool")
            .resourceGroupName("default-azurebatch-japaneast")
            .scaleSettings(Map.of("autoScale", Map.ofEntries(
                Map.entry("evaluationInterval", "PT5M"),
                Map.entry("formula", "$TargetDedicatedNodes=1")
            )))
            .targetNodeCommunicationMode("Default")
            .vmSize("STANDARD_D4")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const pool = new azure_native.batch.Pool("pool", {
    accountName: "sampleacct",
    deploymentConfiguration: {
        virtualMachineConfiguration: {
            extensions: [{
                autoUpgradeMinorVersion: true,
                name: "batchextension1",
                protectedSettings: {
                    protectedSettingsKey: "protectedSettingsValue",
                },
                publisher: "Microsoft.Azure.Security.Monitoring",
                settings: {
                    settingsKey: "settingsValue",
                },
                type: "SecurityMonitoringForLinux",
                typeHandlerVersion: "1.0",
            }],
            imageReference: {
                offer: "0001-com-ubuntu-server-focal",
                publisher: "Canonical",
                sku: "20_04-lts",
            },
            nodeAgentSkuId: "batch.node.ubuntu 20.04",
        },
    },
    poolName: "testpool",
    resourceGroupName: "default-azurebatch-japaneast",
    scaleSettings: {
        autoScale: {
            evaluationInterval: "PT5M",
            formula: "$TargetDedicatedNodes=1",
        },
    },
    targetNodeCommunicationMode: azure_native.batch.NodeCommunicationMode.Default,
    vmSize: "STANDARD_D4",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

pool = azure_native.batch.Pool("pool",
    account_name="sampleacct",
    deployment_configuration=azure_native.batch.DeploymentConfigurationResponseArgs(
        virtual_machine_configuration={
            "extensions": [azure_native.batch.VMExtensionArgs(
                auto_upgrade_minor_version=True,
                name="batchextension1",
                protected_settings={
                    "protectedSettingsKey": "protectedSettingsValue",
                },
                publisher="Microsoft.Azure.Security.Monitoring",
                settings={
                    "settingsKey": "settingsValue",
                },
                type="SecurityMonitoringForLinux",
                type_handler_version="1.0",
            )],
            "imageReference": azure_native.batch.ImageReferenceArgs(
                offer="0001-com-ubuntu-server-focal",
                publisher="Canonical",
                sku="20_04-lts",
            ),
            "nodeAgentSkuId": "batch.node.ubuntu 20.04",
        },
    ),
    pool_name="testpool",
    resource_group_name="default-azurebatch-japaneast",
    scale_settings=azure_native.batch.ScaleSettingsResponseArgs(
        auto_scale=azure_native.batch.AutoScaleSettingsArgs(
            evaluation_interval="PT5M",
            formula="$TargetDedicatedNodes=1",
        ),
    ),
    target_node_communication_mode=azure_native.batch.NodeCommunicationMode.DEFAULT,
    vm_size="STANDARD_D4")

```

```yaml
resources:
  pool:
    type: azure-native:batch:Pool
    properties:
      accountName: sampleacct
      deploymentConfiguration:
        virtualMachineConfiguration:
          extensions:
            - autoUpgradeMinorVersion: true
              name: batchextension1
              protectedSettings:
                protectedSettingsKey: protectedSettingsValue
              publisher: Microsoft.Azure.Security.Monitoring
              settings:
                settingsKey: settingsValue
              type: SecurityMonitoringForLinux
              typeHandlerVersion: '1.0'
          imageReference:
            offer: 0001-com-ubuntu-server-focal
            publisher: Canonical
            sku: 20_04-lts
          nodeAgentSkuId: batch.node.ubuntu 20.04
      poolName: testpool
      resourceGroupName: default-azurebatch-japaneast
      scaleSettings:
        autoScale:
          evaluationInterval: PT5M
          formula: $TargetDedicatedNodes=1
      targetNodeCommunicationMode: Default
      vmSize: STANDARD_D4

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:batch:Pool testpool /subscriptions/subid/resourceGroups/default-azurebatch-japaneast/providers/Microsoft.Batch/batchAccounts/sampleacct/pools/testpool 
```
