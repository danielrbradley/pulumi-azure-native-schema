Volume group resource for create
API Version: 2022-09-01.
Previous API Version: 2021-10-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### VolumeGroups_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var volumeGroup = new AzureNative.NetApp.VolumeGroup("volumeGroup", new()
    {
        AccountName = "account1",
        GroupMetaData = new AzureNative.NetApp.Inputs.VolumeGroupMetaDataArgs
        {
            ApplicationIdentifier = "DEV",
            ApplicationType = "SAP-HANA",
            DeploymentSpecId = "20542149-bfca-5618-1879-9863dc6767f1",
            GroupDescription = "Volume group",
        },
        Location = "westus",
        ResourceGroupName = "myRG",
        VolumeGroupName = "group1",
        Volumes = new[]
        {
            new AzureNative.NetApp.Inputs.VolumeGroupVolumePropertiesArgs
            {
                CapacityPoolResourceId = "/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRG/providers/Microsoft.NetApp/netAppAccounts/account1/capacityPools/pool1",
                CreationToken = "test-data-mnt00001",
                Name = "test-data-mnt00001",
                ProximityPlacementGroup = "/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/cys_sjain_fcp_rg/providers/Microsoft.Compute/proximityPlacementGroups/svlqa_sjain_multivolume_ppg",
                ServiceLevel = "Premium",
                SubnetId = "/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRP/providers/Microsoft.Network/virtualNetworks/testvnet3/subnets/testsubnet3",
                ThroughputMibps = 10,
                UsageThreshold = 107374182400,
                VolumeSpecName = "data",
            },
            new AzureNative.NetApp.Inputs.VolumeGroupVolumePropertiesArgs
            {
                CapacityPoolResourceId = "/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRG/providers/Microsoft.NetApp/netAppAccounts/account1/capacityPools/pool1",
                CreationToken = "test-log-mnt00001",
                Name = "test-log-mnt00001",
                ProximityPlacementGroup = "/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/cys_sjain_fcp_rg/providers/Microsoft.Compute/proximityPlacementGroups/svlqa_sjain_multivolume_ppg",
                ServiceLevel = "Premium",
                SubnetId = "/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRP/providers/Microsoft.Network/virtualNetworks/testvnet3/subnets/testsubnet3",
                ThroughputMibps = 10,
                UsageThreshold = 107374182400,
                VolumeSpecName = "log",
            },
            new AzureNative.NetApp.Inputs.VolumeGroupVolumePropertiesArgs
            {
                CapacityPoolResourceId = "/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRG/providers/Microsoft.NetApp/netAppAccounts/account1/capacityPools/pool1",
                CreationToken = "test-shared",
                Name = "test-shared",
                ProximityPlacementGroup = "/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/cys_sjain_fcp_rg/providers/Microsoft.Compute/proximityPlacementGroups/svlqa_sjain_multivolume_ppg",
                ServiceLevel = "Premium",
                SubnetId = "/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRP/providers/Microsoft.Network/virtualNetworks/testvnet3/subnets/testsubnet3",
                ThroughputMibps = 10,
                UsageThreshold = 107374182400,
                VolumeSpecName = "shared",
            },
        },
    });

});


```

```go
package main

import (
	netapp "github.com/pulumi/pulumi-azure-native-sdk/netapp"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := netapp.NewVolumeGroup(ctx, "volumeGroup", &netapp.VolumeGroupArgs{
			AccountName: pulumi.String("account1"),
			GroupMetaData: &netapp.VolumeGroupMetaDataArgs{
				ApplicationIdentifier: pulumi.String("DEV"),
				ApplicationType:       pulumi.String("SAP-HANA"),
				DeploymentSpecId:      pulumi.String("20542149-bfca-5618-1879-9863dc6767f1"),
				GroupDescription:      pulumi.String("Volume group"),
			},
			Location:          pulumi.String("westus"),
			ResourceGroupName: pulumi.String("myRG"),
			VolumeGroupName:   pulumi.String("group1"),
			Volumes: []netapp.VolumeGroupVolumePropertiesArgs{
				{
					CapacityPoolResourceId:  pulumi.String("/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRG/providers/Microsoft.NetApp/netAppAccounts/account1/capacityPools/pool1"),
					CreationToken:           pulumi.String("test-data-mnt00001"),
					Name:                    pulumi.String("test-data-mnt00001"),
					ProximityPlacementGroup: pulumi.String("/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/cys_sjain_fcp_rg/providers/Microsoft.Compute/proximityPlacementGroups/svlqa_sjain_multivolume_ppg"),
					ServiceLevel:            pulumi.String("Premium"),
					SubnetId:                pulumi.String("/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRP/providers/Microsoft.Network/virtualNetworks/testvnet3/subnets/testsubnet3"),
					ThroughputMibps:         pulumi.Float64(10),
					UsageThreshold:          pulumi.Float64(107374182400),
					VolumeSpecName:          pulumi.String("data"),
				},
				{
					CapacityPoolResourceId:  pulumi.String("/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRG/providers/Microsoft.NetApp/netAppAccounts/account1/capacityPools/pool1"),
					CreationToken:           pulumi.String("test-log-mnt00001"),
					Name:                    pulumi.String("test-log-mnt00001"),
					ProximityPlacementGroup: pulumi.String("/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/cys_sjain_fcp_rg/providers/Microsoft.Compute/proximityPlacementGroups/svlqa_sjain_multivolume_ppg"),
					ServiceLevel:            pulumi.String("Premium"),
					SubnetId:                pulumi.String("/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRP/providers/Microsoft.Network/virtualNetworks/testvnet3/subnets/testsubnet3"),
					ThroughputMibps:         pulumi.Float64(10),
					UsageThreshold:          pulumi.Float64(107374182400),
					VolumeSpecName:          pulumi.String("log"),
				},
				{
					CapacityPoolResourceId:  pulumi.String("/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRG/providers/Microsoft.NetApp/netAppAccounts/account1/capacityPools/pool1"),
					CreationToken:           pulumi.String("test-shared"),
					Name:                    pulumi.String("test-shared"),
					ProximityPlacementGroup: pulumi.String("/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/cys_sjain_fcp_rg/providers/Microsoft.Compute/proximityPlacementGroups/svlqa_sjain_multivolume_ppg"),
					ServiceLevel:            pulumi.String("Premium"),
					SubnetId:                pulumi.String("/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRP/providers/Microsoft.Network/virtualNetworks/testvnet3/subnets/testsubnet3"),
					ThroughputMibps:         pulumi.Float64(10),
					UsageThreshold:          pulumi.Float64(107374182400),
					VolumeSpecName:          pulumi.String("shared"),
				},
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
import com.pulumi.azurenative.netapp.VolumeGroup;
import com.pulumi.azurenative.netapp.VolumeGroupArgs;
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
        var volumeGroup = new VolumeGroup("volumeGroup", VolumeGroupArgs.builder()        
            .accountName("account1")
            .groupMetaData(Map.ofEntries(
                Map.entry("applicationIdentifier", "DEV"),
                Map.entry("applicationType", "SAP-HANA"),
                Map.entry("deploymentSpecId", "20542149-bfca-5618-1879-9863dc6767f1"),
                Map.entry("groupDescription", "Volume group")
            ))
            .location("westus")
            .resourceGroupName("myRG")
            .volumeGroupName("group1")
            .volumes(            
                Map.ofEntries(
                    Map.entry("capacityPoolResourceId", "/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRG/providers/Microsoft.NetApp/netAppAccounts/account1/capacityPools/pool1"),
                    Map.entry("creationToken", "test-data-mnt00001"),
                    Map.entry("name", "test-data-mnt00001"),
                    Map.entry("proximityPlacementGroup", "/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/cys_sjain_fcp_rg/providers/Microsoft.Compute/proximityPlacementGroups/svlqa_sjain_multivolume_ppg"),
                    Map.entry("serviceLevel", "Premium"),
                    Map.entry("subnetId", "/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRP/providers/Microsoft.Network/virtualNetworks/testvnet3/subnets/testsubnet3"),
                    Map.entry("throughputMibps", 10),
                    Map.entry("usageThreshold", 107374182400),
                    Map.entry("volumeSpecName", "data")
                ),
                Map.ofEntries(
                    Map.entry("capacityPoolResourceId", "/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRG/providers/Microsoft.NetApp/netAppAccounts/account1/capacityPools/pool1"),
                    Map.entry("creationToken", "test-log-mnt00001"),
                    Map.entry("name", "test-log-mnt00001"),
                    Map.entry("proximityPlacementGroup", "/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/cys_sjain_fcp_rg/providers/Microsoft.Compute/proximityPlacementGroups/svlqa_sjain_multivolume_ppg"),
                    Map.entry("serviceLevel", "Premium"),
                    Map.entry("subnetId", "/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRP/providers/Microsoft.Network/virtualNetworks/testvnet3/subnets/testsubnet3"),
                    Map.entry("throughputMibps", 10),
                    Map.entry("usageThreshold", 107374182400),
                    Map.entry("volumeSpecName", "log")
                ),
                Map.ofEntries(
                    Map.entry("capacityPoolResourceId", "/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRG/providers/Microsoft.NetApp/netAppAccounts/account1/capacityPools/pool1"),
                    Map.entry("creationToken", "test-shared"),
                    Map.entry("name", "test-shared"),
                    Map.entry("proximityPlacementGroup", "/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/cys_sjain_fcp_rg/providers/Microsoft.Compute/proximityPlacementGroups/svlqa_sjain_multivolume_ppg"),
                    Map.entry("serviceLevel", "Premium"),
                    Map.entry("subnetId", "/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRP/providers/Microsoft.Network/virtualNetworks/testvnet3/subnets/testsubnet3"),
                    Map.entry("throughputMibps", 10),
                    Map.entry("usageThreshold", 107374182400),
                    Map.entry("volumeSpecName", "shared")
                ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const volumeGroup = new azure_native.netapp.VolumeGroup("volumeGroup", {
    accountName: "account1",
    groupMetaData: {
        applicationIdentifier: "DEV",
        applicationType: "SAP-HANA",
        deploymentSpecId: "20542149-bfca-5618-1879-9863dc6767f1",
        groupDescription: "Volume group",
    },
    location: "westus",
    resourceGroupName: "myRG",
    volumeGroupName: "group1",
    volumes: [
        {
            capacityPoolResourceId: "/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRG/providers/Microsoft.NetApp/netAppAccounts/account1/capacityPools/pool1",
            creationToken: "test-data-mnt00001",
            name: "test-data-mnt00001",
            proximityPlacementGroup: "/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/cys_sjain_fcp_rg/providers/Microsoft.Compute/proximityPlacementGroups/svlqa_sjain_multivolume_ppg",
            serviceLevel: "Premium",
            subnetId: "/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRP/providers/Microsoft.Network/virtualNetworks/testvnet3/subnets/testsubnet3",
            throughputMibps: 10,
            usageThreshold: 107374182400,
            volumeSpecName: "data",
        },
        {
            capacityPoolResourceId: "/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRG/providers/Microsoft.NetApp/netAppAccounts/account1/capacityPools/pool1",
            creationToken: "test-log-mnt00001",
            name: "test-log-mnt00001",
            proximityPlacementGroup: "/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/cys_sjain_fcp_rg/providers/Microsoft.Compute/proximityPlacementGroups/svlqa_sjain_multivolume_ppg",
            serviceLevel: "Premium",
            subnetId: "/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRP/providers/Microsoft.Network/virtualNetworks/testvnet3/subnets/testsubnet3",
            throughputMibps: 10,
            usageThreshold: 107374182400,
            volumeSpecName: "log",
        },
        {
            capacityPoolResourceId: "/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRG/providers/Microsoft.NetApp/netAppAccounts/account1/capacityPools/pool1",
            creationToken: "test-shared",
            name: "test-shared",
            proximityPlacementGroup: "/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/cys_sjain_fcp_rg/providers/Microsoft.Compute/proximityPlacementGroups/svlqa_sjain_multivolume_ppg",
            serviceLevel: "Premium",
            subnetId: "/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRP/providers/Microsoft.Network/virtualNetworks/testvnet3/subnets/testsubnet3",
            throughputMibps: 10,
            usageThreshold: 107374182400,
            volumeSpecName: "shared",
        },
    ],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

volume_group = azure_native.netapp.VolumeGroup("volumeGroup",
    account_name="account1",
    group_meta_data=azure_native.netapp.VolumeGroupMetaDataArgs(
        application_identifier="DEV",
        application_type="SAP-HANA",
        deployment_spec_id="20542149-bfca-5618-1879-9863dc6767f1",
        group_description="Volume group",
    ),
    location="westus",
    resource_group_name="myRG",
    volume_group_name="group1",
    volumes=[
        azure_native.netapp.VolumeGroupVolumePropertiesArgs(
            capacity_pool_resource_id="/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRG/providers/Microsoft.NetApp/netAppAccounts/account1/capacityPools/pool1",
            creation_token="test-data-mnt00001",
            name="test-data-mnt00001",
            proximity_placement_group="/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/cys_sjain_fcp_rg/providers/Microsoft.Compute/proximityPlacementGroups/svlqa_sjain_multivolume_ppg",
            service_level="Premium",
            subnet_id="/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRP/providers/Microsoft.Network/virtualNetworks/testvnet3/subnets/testsubnet3",
            throughput_mibps=10,
            usage_threshold=107374182400,
            volume_spec_name="data",
        ),
        azure_native.netapp.VolumeGroupVolumePropertiesArgs(
            capacity_pool_resource_id="/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRG/providers/Microsoft.NetApp/netAppAccounts/account1/capacityPools/pool1",
            creation_token="test-log-mnt00001",
            name="test-log-mnt00001",
            proximity_placement_group="/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/cys_sjain_fcp_rg/providers/Microsoft.Compute/proximityPlacementGroups/svlqa_sjain_multivolume_ppg",
            service_level="Premium",
            subnet_id="/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRP/providers/Microsoft.Network/virtualNetworks/testvnet3/subnets/testsubnet3",
            throughput_mibps=10,
            usage_threshold=107374182400,
            volume_spec_name="log",
        ),
        azure_native.netapp.VolumeGroupVolumePropertiesArgs(
            capacity_pool_resource_id="/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRG/providers/Microsoft.NetApp/netAppAccounts/account1/capacityPools/pool1",
            creation_token="test-shared",
            name="test-shared",
            proximity_placement_group="/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/cys_sjain_fcp_rg/providers/Microsoft.Compute/proximityPlacementGroups/svlqa_sjain_multivolume_ppg",
            service_level="Premium",
            subnet_id="/subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRP/providers/Microsoft.Network/virtualNetworks/testvnet3/subnets/testsubnet3",
            throughput_mibps=10,
            usage_threshold=107374182400,
            volume_spec_name="shared",
        ),
    ])

```

```yaml
resources:
  volumeGroup:
    type: azure-native:netapp:VolumeGroup
    properties:
      accountName: account1
      groupMetaData:
        applicationIdentifier: DEV
        applicationType: SAP-HANA
        deploymentSpecId: 20542149-bfca-5618-1879-9863dc6767f1
        groupDescription: Volume group
      location: westus
      resourceGroupName: myRG
      volumeGroupName: group1
      volumes:
        - capacityPoolResourceId: /subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRG/providers/Microsoft.NetApp/netAppAccounts/account1/capacityPools/pool1
          creationToken: test-data-mnt00001
          name: test-data-mnt00001
          proximityPlacementGroup: /subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/cys_sjain_fcp_rg/providers/Microsoft.Compute/proximityPlacementGroups/svlqa_sjain_multivolume_ppg
          serviceLevel: Premium
          subnetId: /subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRP/providers/Microsoft.Network/virtualNetworks/testvnet3/subnets/testsubnet3
          throughputMibps: 10
          usageThreshold: 1.073741824e+11
          volumeSpecName: data
        - capacityPoolResourceId: /subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRG/providers/Microsoft.NetApp/netAppAccounts/account1/capacityPools/pool1
          creationToken: test-log-mnt00001
          name: test-log-mnt00001
          proximityPlacementGroup: /subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/cys_sjain_fcp_rg/providers/Microsoft.Compute/proximityPlacementGroups/svlqa_sjain_multivolume_ppg
          serviceLevel: Premium
          subnetId: /subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRP/providers/Microsoft.Network/virtualNetworks/testvnet3/subnets/testsubnet3
          throughputMibps: 10
          usageThreshold: 1.073741824e+11
          volumeSpecName: log
        - capacityPoolResourceId: /subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRG/providers/Microsoft.NetApp/netAppAccounts/account1/capacityPools/pool1
          creationToken: test-shared
          name: test-shared
          proximityPlacementGroup: /subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/cys_sjain_fcp_rg/providers/Microsoft.Compute/proximityPlacementGroups/svlqa_sjain_multivolume_ppg
          serviceLevel: Premium
          subnetId: /subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRP/providers/Microsoft.Network/virtualNetworks/testvnet3/subnets/testsubnet3
          throughputMibps: 10
          usageThreshold: 1.073741824e+11
          volumeSpecName: shared

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:netapp:VolumeGroup group1 /subscriptions/d633cc2e-722b-4ae1-b636-bbd9e4c60ed9/resourceGroups/myRG/providers/Microsoft.NetApp/netAppAccounts/account1/volumeGroups/group1 
```
