
API Version: 2022-12-12-preview.
Previous API Version: 2022-12-12-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update cluster
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var cluster = new AzureNative.NetworkCloud.Cluster("cluster", new()
    {
        AggregatorOrSingleRackDefinition = new AzureNative.NetworkCloud.Inputs.RackDefinitionArgs
        {
            BareMetalMachineConfigurationData = new[]
            {
                new AzureNative.NetworkCloud.Inputs.BareMetalMachineConfigurationDataArgs
                {
                    BmcCredentials = new AzureNative.NetworkCloud.Inputs.AdministrativeCredentialsArgs
                    {
                        Password = "{password}",
                        Username = "username",
                    },
                    BmcMacAddress = "AA:BB:CC:DD:EE:FF",
                    BootMacAddress = "00:BB:CC:DD:EE:FF",
                    MachineDetails = "extraDetails",
                    MachineName = "bmmName1",
                    RackSlot = 1,
                    SerialNumber = "BM1219XXX",
                },
                new AzureNative.NetworkCloud.Inputs.BareMetalMachineConfigurationDataArgs
                {
                    BmcCredentials = new AzureNative.NetworkCloud.Inputs.AdministrativeCredentialsArgs
                    {
                        Password = "{password}",
                        Username = "username",
                    },
                    BmcMacAddress = "AA:BB:CC:DD:EE:00",
                    BootMacAddress = "00:BB:CC:DD:EE:00",
                    MachineDetails = "extraDetails",
                    MachineName = "bmmName2",
                    RackSlot = 2,
                    SerialNumber = "BM1219YYY",
                },
            },
            NetworkRackId = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkRacks/networkRackName",
            RackLocation = "Foo Datacenter, Floor 3, Aisle 9, Rack 2",
            RackSerialNumber = "AA1234",
            RackSkuId = "/subscriptions/subscriptionId/providers/Microsoft.NetworkCloud/rackSkus/rackSkuName",
            StorageApplianceConfigurationData = new[]
            {
                new AzureNative.NetworkCloud.Inputs.StorageApplianceConfigurationDataArgs
                {
                    AdminCredentials = new AzureNative.NetworkCloud.Inputs.AdministrativeCredentialsArgs
                    {
                        Password = "{password}",
                        Username = "username",
                    },
                    RackSlot = 1,
                    SerialNumber = "BM1219XXX",
                    StorageApplianceName = "vmName",
                },
            },
        },
        AnalyticsWorkspaceId = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/microsoft.operationalInsights/workspaces/logAnalyticsWorkspaceName",
        ClusterLocation = "Foo Street, 3rd Floor, row 9",
        ClusterName = "clusterName",
        ClusterServicePrincipal = new AzureNative.NetworkCloud.Inputs.ServicePrincipalInformationArgs
        {
            ApplicationId = "12345678-1234-1234-1234-123456789012",
            Password = "{password}",
            PrincipalId = "00000008-0004-0004-0004-000000000012",
            TenantId = "80000000-4000-4000-4000-120000000000",
        },
        ClusterType = "SingleRack",
        ClusterVersion = "1.0.0",
        ComputeDeploymentThreshold = new AzureNative.NetworkCloud.Inputs.ValidationThresholdArgs
        {
            Grouping = "PerCluster",
            Type = "PercentSuccess",
            Value = 90,
        },
        ComputeRackDefinitions = new[]
        {
            new AzureNative.NetworkCloud.Inputs.RackDefinitionArgs
            {
                BareMetalMachineConfigurationData = new[]
                {
                    new AzureNative.NetworkCloud.Inputs.BareMetalMachineConfigurationDataArgs
                    {
                        BmcCredentials = new AzureNative.NetworkCloud.Inputs.AdministrativeCredentialsArgs
                        {
                            Password = "{password}",
                            Username = "username",
                        },
                        BmcMacAddress = "AA:BB:CC:DD:EE:FF",
                        BootMacAddress = "00:BB:CC:DD:EE:FF",
                        MachineDetails = "extraDetails",
                        MachineName = "bmmName1",
                        RackSlot = 1,
                        SerialNumber = "BM1219XXX",
                    },
                    new AzureNative.NetworkCloud.Inputs.BareMetalMachineConfigurationDataArgs
                    {
                        BmcCredentials = new AzureNative.NetworkCloud.Inputs.AdministrativeCredentialsArgs
                        {
                            Password = "{password}",
                            Username = "username",
                        },
                        BmcMacAddress = "AA:BB:CC:DD:EE:00",
                        BootMacAddress = "00:BB:CC:DD:EE:00",
                        MachineDetails = "extraDetails",
                        MachineName = "bmmName2",
                        RackSlot = 2,
                        SerialNumber = "BM1219YYY",
                    },
                },
                NetworkRackId = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkRacks/networkRackName",
                RackLocation = "Foo Datacenter, Floor 3, Aisle 9, Rack 2",
                RackSerialNumber = "AA1234",
                RackSkuId = "/subscriptions/subscriptionId/providers/Microsoft.NetworkCloud/rackSkus/rackSkuName",
                StorageApplianceConfigurationData = new[]
                {
                    new AzureNative.NetworkCloud.Inputs.StorageApplianceConfigurationDataArgs
                    {
                        AdminCredentials = new AzureNative.NetworkCloud.Inputs.AdministrativeCredentialsArgs
                        {
                            Password = "{password}",
                            Username = "username",
                        },
                        RackSlot = 1,
                        SerialNumber = "BM1219XXX",
                        StorageApplianceName = "vmName",
                    },
                },
            },
        },
        ExtendedLocation = new AzureNative.NetworkCloud.Inputs.ExtendedLocationArgs
        {
            Name = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterManagerExtendedLocationName",
            Type = "CustomLocation",
        },
        Location = "location",
        ManagedResourceGroupConfiguration = new AzureNative.NetworkCloud.Inputs.ManagedResourceGroupConfigurationArgs
        {
            Location = "East US",
            Name = "my-managed-rg",
        },
        NetworkFabricId = "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkFabrics/fabricName",
        ResourceGroupName = "resourceGroupName",
        Tags = 
        {
            { "key1", "myvalue1" },
            { "key2", "myvalue2" },
        },
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.networkcloud.Cluster;
import com.pulumi.azurenative.networkcloud.ClusterArgs;
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
        var cluster = new Cluster("cluster", ClusterArgs.builder()        
            .aggregatorOrSingleRackDefinition(Map.ofEntries(
                Map.entry("bareMetalMachineConfigurationData",                 
                    Map.ofEntries(
                        Map.entry("bmcCredentials", Map.ofEntries(
                            Map.entry("password", "{password}"),
                            Map.entry("username", "username")
                        )),
                        Map.entry("bmcMacAddress", "AA:BB:CC:DD:EE:FF"),
                        Map.entry("bootMacAddress", "00:BB:CC:DD:EE:FF"),
                        Map.entry("machineDetails", "extraDetails"),
                        Map.entry("machineName", "bmmName1"),
                        Map.entry("rackSlot", 1),
                        Map.entry("serialNumber", "BM1219XXX")
                    ),
                    Map.ofEntries(
                        Map.entry("bmcCredentials", Map.ofEntries(
                            Map.entry("password", "{password}"),
                            Map.entry("username", "username")
                        )),
                        Map.entry("bmcMacAddress", "AA:BB:CC:DD:EE:00"),
                        Map.entry("bootMacAddress", "00:BB:CC:DD:EE:00"),
                        Map.entry("machineDetails", "extraDetails"),
                        Map.entry("machineName", "bmmName2"),
                        Map.entry("rackSlot", 2),
                        Map.entry("serialNumber", "BM1219YYY")
                    )),
                Map.entry("networkRackId", "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkRacks/networkRackName"),
                Map.entry("rackLocation", "Foo Datacenter, Floor 3, Aisle 9, Rack 2"),
                Map.entry("rackSerialNumber", "AA1234"),
                Map.entry("rackSkuId", "/subscriptions/subscriptionId/providers/Microsoft.NetworkCloud/rackSkus/rackSkuName"),
                Map.entry("storageApplianceConfigurationData", Map.ofEntries(
                    Map.entry("adminCredentials", Map.ofEntries(
                        Map.entry("password", "{password}"),
                        Map.entry("username", "username")
                    )),
                    Map.entry("rackSlot", 1),
                    Map.entry("serialNumber", "BM1219XXX"),
                    Map.entry("storageApplianceName", "vmName")
                ))
            ))
            .analyticsWorkspaceId("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/microsoft.operationalInsights/workspaces/logAnalyticsWorkspaceName")
            .clusterLocation("Foo Street, 3rd Floor, row 9")
            .clusterName("clusterName")
            .clusterServicePrincipal(Map.ofEntries(
                Map.entry("applicationId", "12345678-1234-1234-1234-123456789012"),
                Map.entry("password", "{password}"),
                Map.entry("principalId", "00000008-0004-0004-0004-000000000012"),
                Map.entry("tenantId", "80000000-4000-4000-4000-120000000000")
            ))
            .clusterType("SingleRack")
            .clusterVersion("1.0.0")
            .computeDeploymentThreshold(Map.ofEntries(
                Map.entry("grouping", "PerCluster"),
                Map.entry("type", "PercentSuccess"),
                Map.entry("value", 90)
            ))
            .computeRackDefinitions(Map.ofEntries(
                Map.entry("bareMetalMachineConfigurationData",                 
                    Map.ofEntries(
                        Map.entry("bmcCredentials", Map.ofEntries(
                            Map.entry("password", "{password}"),
                            Map.entry("username", "username")
                        )),
                        Map.entry("bmcMacAddress", "AA:BB:CC:DD:EE:FF"),
                        Map.entry("bootMacAddress", "00:BB:CC:DD:EE:FF"),
                        Map.entry("machineDetails", "extraDetails"),
                        Map.entry("machineName", "bmmName1"),
                        Map.entry("rackSlot", 1),
                        Map.entry("serialNumber", "BM1219XXX")
                    ),
                    Map.ofEntries(
                        Map.entry("bmcCredentials", Map.ofEntries(
                            Map.entry("password", "{password}"),
                            Map.entry("username", "username")
                        )),
                        Map.entry("bmcMacAddress", "AA:BB:CC:DD:EE:00"),
                        Map.entry("bootMacAddress", "00:BB:CC:DD:EE:00"),
                        Map.entry("machineDetails", "extraDetails"),
                        Map.entry("machineName", "bmmName2"),
                        Map.entry("rackSlot", 2),
                        Map.entry("serialNumber", "BM1219YYY")
                    )),
                Map.entry("networkRackId", "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkRacks/networkRackName"),
                Map.entry("rackLocation", "Foo Datacenter, Floor 3, Aisle 9, Rack 2"),
                Map.entry("rackSerialNumber", "AA1234"),
                Map.entry("rackSkuId", "/subscriptions/subscriptionId/providers/Microsoft.NetworkCloud/rackSkus/rackSkuName"),
                Map.entry("storageApplianceConfigurationData", Map.ofEntries(
                    Map.entry("adminCredentials", Map.ofEntries(
                        Map.entry("password", "{password}"),
                        Map.entry("username", "username")
                    )),
                    Map.entry("rackSlot", 1),
                    Map.entry("serialNumber", "BM1219XXX"),
                    Map.entry("storageApplianceName", "vmName")
                ))
            ))
            .extendedLocation(Map.ofEntries(
                Map.entry("name", "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterManagerExtendedLocationName"),
                Map.entry("type", "CustomLocation")
            ))
            .location("location")
            .managedResourceGroupConfiguration(Map.ofEntries(
                Map.entry("location", "East US"),
                Map.entry("name", "my-managed-rg")
            ))
            .networkFabricId("/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkFabrics/fabricName")
            .resourceGroupName("resourceGroupName")
            .tags(Map.ofEntries(
                Map.entry("key1", "myvalue1"),
                Map.entry("key2", "myvalue2")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const cluster = new azure_native.networkcloud.Cluster("cluster", {
    aggregatorOrSingleRackDefinition: {
        bareMetalMachineConfigurationData: [
            {
                bmcCredentials: {
                    password: "{password}",
                    username: "username",
                },
                bmcMacAddress: "AA:BB:CC:DD:EE:FF",
                bootMacAddress: "00:BB:CC:DD:EE:FF",
                machineDetails: "extraDetails",
                machineName: "bmmName1",
                rackSlot: 1,
                serialNumber: "BM1219XXX",
            },
            {
                bmcCredentials: {
                    password: "{password}",
                    username: "username",
                },
                bmcMacAddress: "AA:BB:CC:DD:EE:00",
                bootMacAddress: "00:BB:CC:DD:EE:00",
                machineDetails: "extraDetails",
                machineName: "bmmName2",
                rackSlot: 2,
                serialNumber: "BM1219YYY",
            },
        ],
        networkRackId: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkRacks/networkRackName",
        rackLocation: "Foo Datacenter, Floor 3, Aisle 9, Rack 2",
        rackSerialNumber: "AA1234",
        rackSkuId: "/subscriptions/subscriptionId/providers/Microsoft.NetworkCloud/rackSkus/rackSkuName",
        storageApplianceConfigurationData: [{
            adminCredentials: {
                password: "{password}",
                username: "username",
            },
            rackSlot: 1,
            serialNumber: "BM1219XXX",
            storageApplianceName: "vmName",
        }],
    },
    analyticsWorkspaceId: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/microsoft.operationalInsights/workspaces/logAnalyticsWorkspaceName",
    clusterLocation: "Foo Street, 3rd Floor, row 9",
    clusterName: "clusterName",
    clusterServicePrincipal: {
        applicationId: "12345678-1234-1234-1234-123456789012",
        password: "{password}",
        principalId: "00000008-0004-0004-0004-000000000012",
        tenantId: "80000000-4000-4000-4000-120000000000",
    },
    clusterType: "SingleRack",
    clusterVersion: "1.0.0",
    computeDeploymentThreshold: {
        grouping: "PerCluster",
        type: "PercentSuccess",
        value: 90,
    },
    computeRackDefinitions: [{
        bareMetalMachineConfigurationData: [
            {
                bmcCredentials: {
                    password: "{password}",
                    username: "username",
                },
                bmcMacAddress: "AA:BB:CC:DD:EE:FF",
                bootMacAddress: "00:BB:CC:DD:EE:FF",
                machineDetails: "extraDetails",
                machineName: "bmmName1",
                rackSlot: 1,
                serialNumber: "BM1219XXX",
            },
            {
                bmcCredentials: {
                    password: "{password}",
                    username: "username",
                },
                bmcMacAddress: "AA:BB:CC:DD:EE:00",
                bootMacAddress: "00:BB:CC:DD:EE:00",
                machineDetails: "extraDetails",
                machineName: "bmmName2",
                rackSlot: 2,
                serialNumber: "BM1219YYY",
            },
        ],
        networkRackId: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkRacks/networkRackName",
        rackLocation: "Foo Datacenter, Floor 3, Aisle 9, Rack 2",
        rackSerialNumber: "AA1234",
        rackSkuId: "/subscriptions/subscriptionId/providers/Microsoft.NetworkCloud/rackSkus/rackSkuName",
        storageApplianceConfigurationData: [{
            adminCredentials: {
                password: "{password}",
                username: "username",
            },
            rackSlot: 1,
            serialNumber: "BM1219XXX",
            storageApplianceName: "vmName",
        }],
    }],
    extendedLocation: {
        name: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterManagerExtendedLocationName",
        type: "CustomLocation",
    },
    location: "location",
    managedResourceGroupConfiguration: {
        location: "East US",
        name: "my-managed-rg",
    },
    networkFabricId: "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkFabrics/fabricName",
    resourceGroupName: "resourceGroupName",
    tags: {
        key1: "myvalue1",
        key2: "myvalue2",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

cluster = azure_native.networkcloud.Cluster("cluster",
    aggregator_or_single_rack_definition=azure_native.networkcloud.RackDefinitionResponseArgs(
        bare_metal_machine_configuration_data=[
            {
                "bmcCredentials": azure_native.networkcloud.AdministrativeCredentialsArgs(
                    password="{password}",
                    username="username",
                ),
                "bmcMacAddress": "AA:BB:CC:DD:EE:FF",
                "bootMacAddress": "00:BB:CC:DD:EE:FF",
                "machineDetails": "extraDetails",
                "machineName": "bmmName1",
                "rackSlot": 1,
                "serialNumber": "BM1219XXX",
            },
            {
                "bmcCredentials": azure_native.networkcloud.AdministrativeCredentialsArgs(
                    password="{password}",
                    username="username",
                ),
                "bmcMacAddress": "AA:BB:CC:DD:EE:00",
                "bootMacAddress": "00:BB:CC:DD:EE:00",
                "machineDetails": "extraDetails",
                "machineName": "bmmName2",
                "rackSlot": 2,
                "serialNumber": "BM1219YYY",
            },
        ],
        network_rack_id="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkRacks/networkRackName",
        rack_location="Foo Datacenter, Floor 3, Aisle 9, Rack 2",
        rack_serial_number="AA1234",
        rack_sku_id="/subscriptions/subscriptionId/providers/Microsoft.NetworkCloud/rackSkus/rackSkuName",
        storage_appliance_configuration_data=[{
            "adminCredentials": azure_native.networkcloud.AdministrativeCredentialsArgs(
                password="{password}",
                username="username",
            ),
            "rackSlot": 1,
            "serialNumber": "BM1219XXX",
            "storageApplianceName": "vmName",
        }],
    ),
    analytics_workspace_id="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/microsoft.operationalInsights/workspaces/logAnalyticsWorkspaceName",
    cluster_location="Foo Street, 3rd Floor, row 9",
    cluster_name="clusterName",
    cluster_service_principal=azure_native.networkcloud.ServicePrincipalInformationArgs(
        application_id="12345678-1234-1234-1234-123456789012",
        password="{password}",
        principal_id="00000008-0004-0004-0004-000000000012",
        tenant_id="80000000-4000-4000-4000-120000000000",
    ),
    cluster_type="SingleRack",
    cluster_version="1.0.0",
    compute_deployment_threshold=azure_native.networkcloud.ValidationThresholdArgs(
        grouping="PerCluster",
        type="PercentSuccess",
        value=90,
    ),
    compute_rack_definitions=[{
        "bareMetalMachineConfigurationData": [
            {
                "bmcCredentials": azure_native.networkcloud.AdministrativeCredentialsArgs(
                    password="{password}",
                    username="username",
                ),
                "bmcMacAddress": "AA:BB:CC:DD:EE:FF",
                "bootMacAddress": "00:BB:CC:DD:EE:FF",
                "machineDetails": "extraDetails",
                "machineName": "bmmName1",
                "rackSlot": 1,
                "serialNumber": "BM1219XXX",
            },
            {
                "bmcCredentials": azure_native.networkcloud.AdministrativeCredentialsArgs(
                    password="{password}",
                    username="username",
                ),
                "bmcMacAddress": "AA:BB:CC:DD:EE:00",
                "bootMacAddress": "00:BB:CC:DD:EE:00",
                "machineDetails": "extraDetails",
                "machineName": "bmmName2",
                "rackSlot": 2,
                "serialNumber": "BM1219YYY",
            },
        ],
        "networkRackId": "/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkRacks/networkRackName",
        "rackLocation": "Foo Datacenter, Floor 3, Aisle 9, Rack 2",
        "rackSerialNumber": "AA1234",
        "rackSkuId": "/subscriptions/subscriptionId/providers/Microsoft.NetworkCloud/rackSkus/rackSkuName",
        "storageApplianceConfigurationData": [{
            "adminCredentials": azure_native.networkcloud.AdministrativeCredentialsArgs(
                password="{password}",
                username="username",
            ),
            "rackSlot": 1,
            "serialNumber": "BM1219XXX",
            "storageApplianceName": "vmName",
        }],
    }],
    extended_location=azure_native.networkcloud.ExtendedLocationArgs(
        name="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterManagerExtendedLocationName",
        type="CustomLocation",
    ),
    location="location",
    managed_resource_group_configuration=azure_native.networkcloud.ManagedResourceGroupConfigurationArgs(
        location="East US",
        name="my-managed-rg",
    ),
    network_fabric_id="/subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkFabrics/fabricName",
    resource_group_name="resourceGroupName",
    tags={
        "key1": "myvalue1",
        "key2": "myvalue2",
    })

```

```yaml
resources:
  cluster:
    type: azure-native:networkcloud:Cluster
    properties:
      aggregatorOrSingleRackDefinition:
        bareMetalMachineConfigurationData:
          - bmcCredentials:
              password: '{password}'
              username: username
            bmcMacAddress: AA:BB:CC:DD:EE:FF
            bootMacAddress: 00:BB:CC:DD:EE:FF
            machineDetails: extraDetails
            machineName: bmmName1
            rackSlot: 1
            serialNumber: BM1219XXX
          - bmcCredentials:
              password: '{password}'
              username: username
            bmcMacAddress: AA:BB:CC:DD:EE:00
            bootMacAddress: 00:BB:CC:DD:EE:00
            machineDetails: extraDetails
            machineName: bmmName2
            rackSlot: 2
            serialNumber: BM1219YYY
        networkRackId: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkRacks/networkRackName
        rackLocation: Foo Datacenter, Floor 3, Aisle 9, Rack 2
        rackSerialNumber: AA1234
        rackSkuId: /subscriptions/subscriptionId/providers/Microsoft.NetworkCloud/rackSkus/rackSkuName
        storageApplianceConfigurationData:
          - adminCredentials:
              password: '{password}'
              username: username
            rackSlot: 1
            serialNumber: BM1219XXX
            storageApplianceName: vmName
      analyticsWorkspaceId: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/microsoft.operationalInsights/workspaces/logAnalyticsWorkspaceName
      clusterLocation: Foo Street, 3rd Floor, row 9
      clusterName: clusterName
      clusterServicePrincipal:
        applicationId: 12345678-1234-1234-1234-123456789012
        password: '{password}'
        principalId: 00000008-0004-0004-0004-000000000012
        tenantId: 80000000-4000-4000-4000-120000000000
      clusterType: SingleRack
      clusterVersion: 1.0.0
      computeDeploymentThreshold:
        grouping: PerCluster
        type: PercentSuccess
        value: 90
      computeRackDefinitions:
        - bareMetalMachineConfigurationData:
            - bmcCredentials:
                password: '{password}'
                username: username
              bmcMacAddress: AA:BB:CC:DD:EE:FF
              bootMacAddress: 00:BB:CC:DD:EE:FF
              machineDetails: extraDetails
              machineName: bmmName1
              rackSlot: 1
              serialNumber: BM1219XXX
            - bmcCredentials:
                password: '{password}'
                username: username
              bmcMacAddress: AA:BB:CC:DD:EE:00
              bootMacAddress: 00:BB:CC:DD:EE:00
              machineDetails: extraDetails
              machineName: bmmName2
              rackSlot: 2
              serialNumber: BM1219YYY
          networkRackId: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkRacks/networkRackName
          rackLocation: Foo Datacenter, Floor 3, Aisle 9, Rack 2
          rackSerialNumber: AA1234
          rackSkuId: /subscriptions/subscriptionId/providers/Microsoft.NetworkCloud/rackSkus/rackSkuName
          storageApplianceConfigurationData:
            - adminCredentials:
                password: '{password}'
                username: username
              rackSlot: 1
              serialNumber: BM1219XXX
              storageApplianceName: vmName
      extendedLocation:
        name: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ExtendedLocation/customLocations/clusterManagerExtendedLocationName
        type: CustomLocation
      location: location
      managedResourceGroupConfiguration:
        location: East US
        name: my-managed-rg
      networkFabricId: /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.ManagedNetworkFabric/networkFabrics/fabricName
      resourceGroupName: resourceGroupName
      tags:
        key1: myvalue1
        key2: myvalue2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:networkcloud:Cluster clusterName /subscriptions/subscriptionId/resourceGroups/resourceGroupName/providers/Microsoft.NetworkCloud/clusters/clusterName 
```
