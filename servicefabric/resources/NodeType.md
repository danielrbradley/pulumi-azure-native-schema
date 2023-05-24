Describes a node type in the cluster, each node type represents sub set of nodes in the cluster.
API Version: 2023-02-01-preview.
Previous API Version: 2020-01-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Put a node type with auto-scale parameters
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var nodeType = new AzureNative.ServiceFabric.NodeType("nodeType", new()
    {
        Capacities = 
        {
            { "ClientConnections", "65536" },
        },
        ClusterName = "myCluster",
        DataDiskSizeGB = 200,
        DataDiskType = "Premium_LRS",
        IsPrimary = false,
        IsStateless = true,
        MultiplePlacementGroups = true,
        NodeTypeName = "BE",
        PlacementProperties = 
        {
            { "HasSSD", "true" },
            { "NodeColor", "green" },
            { "SomeProperty", "5" },
        },
        ResourceGroupName = "resRg",
        VmExtensions = new[]
        {
            new AzureNative.ServiceFabric.Inputs.VMSSExtensionArgs
            {
                AutoUpgradeMinorVersion = true,
                Name = "Microsoft.Azure.Geneva.GenevaMonitoring",
                Publisher = "Microsoft.Azure.Geneva",
                Settings = null,
                Type = "GenevaMonitoring",
                TypeHandlerVersion = "2.0",
            },
        },
        VmImageOffer = "WindowsServer",
        VmImagePublisher = "MicrosoftWindowsServer",
        VmImageSku = "2016-Datacenter-Server-Core",
        VmImageVersion = "latest",
        VmInstanceCount = -1,
        VmManagedIdentity = new AzureNative.ServiceFabric.Inputs.VmManagedIdentityArgs
        {
            UserAssignedIdentities = new[]
            {
                "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/myIdentity",
                "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/myIdentity2",
            },
        },
        VmSecrets = new[]
        {
            new AzureNative.ServiceFabric.Inputs.VaultSecretGroupArgs
            {
                SourceVault = new AzureNative.ServiceFabric.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.KeyVault/vaults/myVault",
                },
                VaultCertificates = new[]
                {
                    new AzureNative.ServiceFabric.Inputs.VaultCertificateArgs
                    {
                        CertificateStore = "My",
                        CertificateUrl = "https://myVault.vault.azure.net:443/secrets/myCert/ef1a31d39e1f46bca33def54b6cda54c",
                    },
                },
            },
        },
        VmSize = "Standard_DS3",
    });

});


```

```go
package main

import (
	servicefabric "github.com/pulumi/pulumi-azure-native-sdk/servicefabric"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := servicefabric.NewNodeType(ctx, "nodeType", &servicefabric.NodeTypeArgs{
			Capacities: pulumi.StringMap{
				"ClientConnections": pulumi.String("65536"),
			},
			ClusterName:             pulumi.String("myCluster"),
			DataDiskSizeGB:          pulumi.Int(200),
			DataDiskType:            pulumi.String("Premium_LRS"),
			IsPrimary:               pulumi.Bool(false),
			IsStateless:             pulumi.Bool(true),
			MultiplePlacementGroups: pulumi.Bool(true),
			NodeTypeName:            pulumi.String("BE"),
			PlacementProperties: pulumi.StringMap{
				"HasSSD":       pulumi.String("true"),
				"NodeColor":    pulumi.String("green"),
				"SomeProperty": pulumi.String("5"),
			},
			ResourceGroupName: pulumi.String("resRg"),
			VmExtensions: []servicefabric.VMSSExtensionArgs{
				{
					AutoUpgradeMinorVersion: pulumi.Bool(true),
					Name:                    pulumi.String("Microsoft.Azure.Geneva.GenevaMonitoring"),
					Publisher:               pulumi.String("Microsoft.Azure.Geneva"),
					Settings:                nil,
					Type:                    pulumi.String("GenevaMonitoring"),
					TypeHandlerVersion:      pulumi.String("2.0"),
				},
			},
			VmImageOffer:     pulumi.String("WindowsServer"),
			VmImagePublisher: pulumi.String("MicrosoftWindowsServer"),
			VmImageSku:       pulumi.String("2016-Datacenter-Server-Core"),
			VmImageVersion:   pulumi.String("latest"),
			VmInstanceCount:  -1,
			VmManagedIdentity: &servicefabric.VmManagedIdentityArgs{
				UserAssignedIdentities: pulumi.StringArray{
					pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/myIdentity"),
					pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/myIdentity2"),
				},
			},
			VmSecrets: []servicefabric.VaultSecretGroupArgs{
				{
					SourceVault: {
						Id: pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.KeyVault/vaults/myVault"),
					},
					VaultCertificates: servicefabric.VaultCertificateArray{
						{
							CertificateStore: pulumi.String("My"),
							CertificateUrl:   pulumi.String("https://myVault.vault.azure.net:443/secrets/myCert/ef1a31d39e1f46bca33def54b6cda54c"),
						},
					},
				},
			},
			VmSize: pulumi.String("Standard_DS3"),
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
import com.pulumi.azurenative.servicefabric.NodeType;
import com.pulumi.azurenative.servicefabric.NodeTypeArgs;
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
        var nodeType = new NodeType("nodeType", NodeTypeArgs.builder()        
            .capacities(Map.of("ClientConnections", "65536"))
            .clusterName("myCluster")
            .dataDiskSizeGB(200)
            .dataDiskType("Premium_LRS")
            .isPrimary(false)
            .isStateless(true)
            .multiplePlacementGroups(true)
            .nodeTypeName("BE")
            .placementProperties(Map.ofEntries(
                Map.entry("HasSSD", "true"),
                Map.entry("NodeColor", "green"),
                Map.entry("SomeProperty", "5")
            ))
            .resourceGroupName("resRg")
            .vmExtensions(Map.ofEntries(
                Map.entry("autoUpgradeMinorVersion", true),
                Map.entry("name", "Microsoft.Azure.Geneva.GenevaMonitoring"),
                Map.entry("publisher", "Microsoft.Azure.Geneva"),
                Map.entry("settings", ),
                Map.entry("type", "GenevaMonitoring"),
                Map.entry("typeHandlerVersion", "2.0")
            ))
            .vmImageOffer("WindowsServer")
            .vmImagePublisher("MicrosoftWindowsServer")
            .vmImageSku("2016-Datacenter-Server-Core")
            .vmImageVersion("latest")
            .vmInstanceCount("TODO: GenUnaryOpExpression")
            .vmManagedIdentity(Map.of("userAssignedIdentities",             
                "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/myIdentity",
                "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/myIdentity2"))
            .vmSecrets(Map.ofEntries(
                Map.entry("sourceVault", Map.of("id", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.KeyVault/vaults/myVault")),
                Map.entry("vaultCertificates", Map.ofEntries(
                    Map.entry("certificateStore", "My"),
                    Map.entry("certificateUrl", "https://myVault.vault.azure.net:443/secrets/myCert/ef1a31d39e1f46bca33def54b6cda54c")
                ))
            ))
            .vmSize("Standard_DS3")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const nodeType = new azure_native.servicefabric.NodeType("nodeType", {
    capacities: {
        ClientConnections: "65536",
    },
    clusterName: "myCluster",
    dataDiskSizeGB: 200,
    dataDiskType: "Premium_LRS",
    isPrimary: false,
    isStateless: true,
    multiplePlacementGroups: true,
    nodeTypeName: "BE",
    placementProperties: {
        HasSSD: "true",
        NodeColor: "green",
        SomeProperty: "5",
    },
    resourceGroupName: "resRg",
    vmExtensions: [{
        autoUpgradeMinorVersion: true,
        name: "Microsoft.Azure.Geneva.GenevaMonitoring",
        publisher: "Microsoft.Azure.Geneva",
        settings: {},
        type: "GenevaMonitoring",
        typeHandlerVersion: "2.0",
    }],
    vmImageOffer: "WindowsServer",
    vmImagePublisher: "MicrosoftWindowsServer",
    vmImageSku: "2016-Datacenter-Server-Core",
    vmImageVersion: "latest",
    vmInstanceCount: -1,
    vmManagedIdentity: {
        userAssignedIdentities: [
            "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/myIdentity",
            "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/myIdentity2",
        ],
    },
    vmSecrets: [{
        sourceVault: {
            id: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.KeyVault/vaults/myVault",
        },
        vaultCertificates: [{
            certificateStore: "My",
            certificateUrl: "https://myVault.vault.azure.net:443/secrets/myCert/ef1a31d39e1f46bca33def54b6cda54c",
        }],
    }],
    vmSize: "Standard_DS3",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

node_type = azure_native.servicefabric.NodeType("nodeType",
    capacities={
        "ClientConnections": "65536",
    },
    cluster_name="myCluster",
    data_disk_size_gb=200,
    data_disk_type="Premium_LRS",
    is_primary=False,
    is_stateless=True,
    multiple_placement_groups=True,
    node_type_name="BE",
    placement_properties={
        "HasSSD": "true",
        "NodeColor": "green",
        "SomeProperty": "5",
    },
    resource_group_name="resRg",
    vm_extensions=[azure_native.servicefabric.VMSSExtensionArgs(
        auto_upgrade_minor_version=True,
        name="Microsoft.Azure.Geneva.GenevaMonitoring",
        publisher="Microsoft.Azure.Geneva",
        settings={},
        type="GenevaMonitoring",
        type_handler_version="2.0",
    )],
    vm_image_offer="WindowsServer",
    vm_image_publisher="MicrosoftWindowsServer",
    vm_image_sku="2016-Datacenter-Server-Core",
    vm_image_version="latest",
    vm_instance_count=-1,
    vm_managed_identity=azure_native.servicefabric.VmManagedIdentityArgs(
        user_assigned_identities=[
            "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/myIdentity",
            "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/myIdentity2",
        ],
    ),
    vm_secrets=[{
        "sourceVault": azure_native.servicefabric.SubResourceArgs(
            id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.KeyVault/vaults/myVault",
        ),
        "vaultCertificates": [azure_native.servicefabric.VaultCertificateArgs(
            certificate_store="My",
            certificate_url="https://myVault.vault.azure.net:443/secrets/myCert/ef1a31d39e1f46bca33def54b6cda54c",
        )],
    }],
    vm_size="Standard_DS3")

```

```yaml

```

{{% /example %}}
{{% example %}}
### Put a node type with maximum parameters
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var nodeType = new AzureNative.ServiceFabric.NodeType("nodeType", new()
    {
        AdditionalDataDisks = new[]
        {
            new AzureNative.ServiceFabric.Inputs.VmssDataDiskArgs
            {
                DiskLetter = "F",
                DiskSizeGB = 256,
                DiskType = "StandardSSD_LRS",
                Lun = 1,
            },
            new AzureNative.ServiceFabric.Inputs.VmssDataDiskArgs
            {
                DiskLetter = "G",
                DiskSizeGB = 150,
                DiskType = "Premium_LRS",
                Lun = 2,
            },
        },
        Capacities = 
        {
            { "ClientConnections", "65536" },
        },
        ClusterName = "myCluster",
        DataDiskLetter = "S",
        DataDiskSizeGB = 200,
        DataDiskType = "Premium_LRS",
        EnableAcceleratedNetworking = true,
        EnableEncryptionAtHost = true,
        EnableNodePublicIP = true,
        EnableOverProvisioning = false,
        EvictionPolicy = "Deallocate",
        FrontendConfigurations = new[]
        {
            new AzureNative.ServiceFabric.Inputs.FrontendConfigurationArgs
            {
                ApplicationGatewayBackendAddressPoolId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.Network/applicationGateways/appgw-test/backendAddressPools/appgwBepoolTest",
                LoadBalancerBackendAddressPoolId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.Network/loadBalancers/test-LB/backendAddressPools/LoadBalancerBEAddressPool",
                LoadBalancerInboundNatPoolId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.Network/loadBalancers/test-LB/inboundNatPools/LoadBalancerNATPool",
            },
        },
        IsPrimary = false,
        IsSpotVM = true,
        IsStateless = true,
        MultiplePlacementGroups = true,
        NodeTypeName = "BE",
        PlacementProperties = 
        {
            { "HasSSD", "true" },
            { "NodeColor", "green" },
            { "SomeProperty", "5" },
        },
        ResourceGroupName = "resRg",
        SecureBootEnabled = true,
        SecurityType = "TrustedLaunch",
        SpotRestoreTimeout = "PT30M",
        SubnetId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.Network/virtualNetworks/vnet1/subnets/subnet1",
        UseDefaultPublicLoadBalancer = true,
        UseEphemeralOSDisk = true,
        VmExtensions = new[]
        {
            new AzureNative.ServiceFabric.Inputs.VMSSExtensionArgs
            {
                AutoUpgradeMinorVersion = true,
                EnableAutomaticUpgrade = true,
                ForceUpdateTag = "v.1.0",
                Name = "Microsoft.Azure.Geneva.GenevaMonitoring",
                Publisher = "Microsoft.Azure.Geneva",
                Settings = null,
                Type = "GenevaMonitoring",
                TypeHandlerVersion = "2.0",
            },
        },
        VmImageOffer = "WindowsServer",
        VmImagePublisher = "MicrosoftWindowsServer",
        VmImageSku = "2016-Datacenter-Server-Core",
        VmImageVersion = "latest",
        VmInstanceCount = 10,
        VmManagedIdentity = new AzureNative.ServiceFabric.Inputs.VmManagedIdentityArgs
        {
            UserAssignedIdentities = new[]
            {
                "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/myIdentity",
                "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/myIdentity2",
            },
        },
        VmSecrets = new[]
        {
            new AzureNative.ServiceFabric.Inputs.VaultSecretGroupArgs
            {
                SourceVault = new AzureNative.ServiceFabric.Inputs.SubResourceArgs
                {
                    Id = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.KeyVault/vaults/myVault",
                },
                VaultCertificates = new[]
                {
                    new AzureNative.ServiceFabric.Inputs.VaultCertificateArgs
                    {
                        CertificateStore = "My",
                        CertificateUrl = "https://myVault.vault.azure.net:443/secrets/myCert/ef1a31d39e1f46bca33def54b6cda54c",
                    },
                },
            },
        },
        VmSetupActions = new[]
        {
            "EnableContainers",
            "EnableHyperV",
        },
        VmSize = "Standard_DS3",
    });

});


```

```go
package main

import (
	servicefabric "github.com/pulumi/pulumi-azure-native-sdk/servicefabric"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := servicefabric.NewNodeType(ctx, "nodeType", &servicefabric.NodeTypeArgs{
			AdditionalDataDisks: []servicefabric.VmssDataDiskArgs{
				{
					DiskLetter: pulumi.String("F"),
					DiskSizeGB: pulumi.Int(256),
					DiskType:   pulumi.String("StandardSSD_LRS"),
					Lun:        pulumi.Int(1),
				},
				{
					DiskLetter: pulumi.String("G"),
					DiskSizeGB: pulumi.Int(150),
					DiskType:   pulumi.String("Premium_LRS"),
					Lun:        pulumi.Int(2),
				},
			},
			Capacities: pulumi.StringMap{
				"ClientConnections": pulumi.String("65536"),
			},
			ClusterName:                 pulumi.String("myCluster"),
			DataDiskLetter:              pulumi.String("S"),
			DataDiskSizeGB:              pulumi.Int(200),
			DataDiskType:                pulumi.String("Premium_LRS"),
			EnableAcceleratedNetworking: pulumi.Bool(true),
			EnableEncryptionAtHost:      pulumi.Bool(true),
			EnableNodePublicIP:          pulumi.Bool(true),
			EnableOverProvisioning:      pulumi.Bool(false),
			EvictionPolicy:              pulumi.String("Deallocate"),
			FrontendConfigurations: []servicefabric.FrontendConfigurationArgs{
				{
					ApplicationGatewayBackendAddressPoolId: pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.Network/applicationGateways/appgw-test/backendAddressPools/appgwBepoolTest"),
					LoadBalancerBackendAddressPoolId:       pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.Network/loadBalancers/test-LB/backendAddressPools/LoadBalancerBEAddressPool"),
					LoadBalancerInboundNatPoolId:           pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.Network/loadBalancers/test-LB/inboundNatPools/LoadBalancerNATPool"),
				},
			},
			IsPrimary:               pulumi.Bool(false),
			IsSpotVM:                pulumi.Bool(true),
			IsStateless:             pulumi.Bool(true),
			MultiplePlacementGroups: pulumi.Bool(true),
			NodeTypeName:            pulumi.String("BE"),
			PlacementProperties: pulumi.StringMap{
				"HasSSD":       pulumi.String("true"),
				"NodeColor":    pulumi.String("green"),
				"SomeProperty": pulumi.String("5"),
			},
			ResourceGroupName:            pulumi.String("resRg"),
			SecureBootEnabled:            pulumi.Bool(true),
			SecurityType:                 pulumi.String("TrustedLaunch"),
			SpotRestoreTimeout:           pulumi.String("PT30M"),
			SubnetId:                     pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.Network/virtualNetworks/vnet1/subnets/subnet1"),
			UseDefaultPublicLoadBalancer: pulumi.Bool(true),
			UseEphemeralOSDisk:           pulumi.Bool(true),
			VmExtensions: []servicefabric.VMSSExtensionArgs{
				{
					AutoUpgradeMinorVersion: pulumi.Bool(true),
					EnableAutomaticUpgrade:  pulumi.Bool(true),
					ForceUpdateTag:          pulumi.String("v.1.0"),
					Name:                    pulumi.String("Microsoft.Azure.Geneva.GenevaMonitoring"),
					Publisher:               pulumi.String("Microsoft.Azure.Geneva"),
					Settings:                nil,
					Type:                    pulumi.String("GenevaMonitoring"),
					TypeHandlerVersion:      pulumi.String("2.0"),
				},
			},
			VmImageOffer:     pulumi.String("WindowsServer"),
			VmImagePublisher: pulumi.String("MicrosoftWindowsServer"),
			VmImageSku:       pulumi.String("2016-Datacenter-Server-Core"),
			VmImageVersion:   pulumi.String("latest"),
			VmInstanceCount:  pulumi.Int(10),
			VmManagedIdentity: &servicefabric.VmManagedIdentityArgs{
				UserAssignedIdentities: pulumi.StringArray{
					pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/myIdentity"),
					pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/myIdentity2"),
				},
			},
			VmSecrets: []servicefabric.VaultSecretGroupArgs{
				{
					SourceVault: {
						Id: pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.KeyVault/vaults/myVault"),
					},
					VaultCertificates: servicefabric.VaultCertificateArray{
						{
							CertificateStore: pulumi.String("My"),
							CertificateUrl:   pulumi.String("https://myVault.vault.azure.net:443/secrets/myCert/ef1a31d39e1f46bca33def54b6cda54c"),
						},
					},
				},
			},
			VmSetupActions: pulumi.StringArray{
				pulumi.String("EnableContainers"),
				pulumi.String("EnableHyperV"),
			},
			VmSize: pulumi.String("Standard_DS3"),
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
import com.pulumi.azurenative.servicefabric.NodeType;
import com.pulumi.azurenative.servicefabric.NodeTypeArgs;
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
        var nodeType = new NodeType("nodeType", NodeTypeArgs.builder()        
            .additionalDataDisks(            
                Map.ofEntries(
                    Map.entry("diskLetter", "F"),
                    Map.entry("diskSizeGB", 256),
                    Map.entry("diskType", "StandardSSD_LRS"),
                    Map.entry("lun", 1)
                ),
                Map.ofEntries(
                    Map.entry("diskLetter", "G"),
                    Map.entry("diskSizeGB", 150),
                    Map.entry("diskType", "Premium_LRS"),
                    Map.entry("lun", 2)
                ))
            .capacities(Map.of("ClientConnections", "65536"))
            .clusterName("myCluster")
            .dataDiskLetter("S")
            .dataDiskSizeGB(200)
            .dataDiskType("Premium_LRS")
            .enableAcceleratedNetworking(true)
            .enableEncryptionAtHost(true)
            .enableNodePublicIP(true)
            .enableOverProvisioning(false)
            .evictionPolicy("Deallocate")
            .frontendConfigurations(Map.ofEntries(
                Map.entry("applicationGatewayBackendAddressPoolId", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.Network/applicationGateways/appgw-test/backendAddressPools/appgwBepoolTest"),
                Map.entry("loadBalancerBackendAddressPoolId", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.Network/loadBalancers/test-LB/backendAddressPools/LoadBalancerBEAddressPool"),
                Map.entry("loadBalancerInboundNatPoolId", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.Network/loadBalancers/test-LB/inboundNatPools/LoadBalancerNATPool")
            ))
            .isPrimary(false)
            .isSpotVM(true)
            .isStateless(true)
            .multiplePlacementGroups(true)
            .nodeTypeName("BE")
            .placementProperties(Map.ofEntries(
                Map.entry("HasSSD", "true"),
                Map.entry("NodeColor", "green"),
                Map.entry("SomeProperty", "5")
            ))
            .resourceGroupName("resRg")
            .secureBootEnabled(true)
            .securityType("TrustedLaunch")
            .spotRestoreTimeout("PT30M")
            .subnetId("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.Network/virtualNetworks/vnet1/subnets/subnet1")
            .useDefaultPublicLoadBalancer(true)
            .useEphemeralOSDisk(true)
            .vmExtensions(Map.ofEntries(
                Map.entry("autoUpgradeMinorVersion", true),
                Map.entry("enableAutomaticUpgrade", true),
                Map.entry("forceUpdateTag", "v.1.0"),
                Map.entry("name", "Microsoft.Azure.Geneva.GenevaMonitoring"),
                Map.entry("publisher", "Microsoft.Azure.Geneva"),
                Map.entry("settings", ),
                Map.entry("type", "GenevaMonitoring"),
                Map.entry("typeHandlerVersion", "2.0")
            ))
            .vmImageOffer("WindowsServer")
            .vmImagePublisher("MicrosoftWindowsServer")
            .vmImageSku("2016-Datacenter-Server-Core")
            .vmImageVersion("latest")
            .vmInstanceCount(10)
            .vmManagedIdentity(Map.of("userAssignedIdentities",             
                "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/myIdentity",
                "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/myIdentity2"))
            .vmSecrets(Map.ofEntries(
                Map.entry("sourceVault", Map.of("id", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.KeyVault/vaults/myVault")),
                Map.entry("vaultCertificates", Map.ofEntries(
                    Map.entry("certificateStore", "My"),
                    Map.entry("certificateUrl", "https://myVault.vault.azure.net:443/secrets/myCert/ef1a31d39e1f46bca33def54b6cda54c")
                ))
            ))
            .vmSetupActions(            
                "EnableContainers",
                "EnableHyperV")
            .vmSize("Standard_DS3")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const nodeType = new azure_native.servicefabric.NodeType("nodeType", {
    additionalDataDisks: [
        {
            diskLetter: "F",
            diskSizeGB: 256,
            diskType: "StandardSSD_LRS",
            lun: 1,
        },
        {
            diskLetter: "G",
            diskSizeGB: 150,
            diskType: "Premium_LRS",
            lun: 2,
        },
    ],
    capacities: {
        ClientConnections: "65536",
    },
    clusterName: "myCluster",
    dataDiskLetter: "S",
    dataDiskSizeGB: 200,
    dataDiskType: "Premium_LRS",
    enableAcceleratedNetworking: true,
    enableEncryptionAtHost: true,
    enableNodePublicIP: true,
    enableOverProvisioning: false,
    evictionPolicy: "Deallocate",
    frontendConfigurations: [{
        applicationGatewayBackendAddressPoolId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.Network/applicationGateways/appgw-test/backendAddressPools/appgwBepoolTest",
        loadBalancerBackendAddressPoolId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.Network/loadBalancers/test-LB/backendAddressPools/LoadBalancerBEAddressPool",
        loadBalancerInboundNatPoolId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.Network/loadBalancers/test-LB/inboundNatPools/LoadBalancerNATPool",
    }],
    isPrimary: false,
    isSpotVM: true,
    isStateless: true,
    multiplePlacementGroups: true,
    nodeTypeName: "BE",
    placementProperties: {
        HasSSD: "true",
        NodeColor: "green",
        SomeProperty: "5",
    },
    resourceGroupName: "resRg",
    secureBootEnabled: true,
    securityType: "TrustedLaunch",
    spotRestoreTimeout: "PT30M",
    subnetId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.Network/virtualNetworks/vnet1/subnets/subnet1",
    useDefaultPublicLoadBalancer: true,
    useEphemeralOSDisk: true,
    vmExtensions: [{
        autoUpgradeMinorVersion: true,
        enableAutomaticUpgrade: true,
        forceUpdateTag: "v.1.0",
        name: "Microsoft.Azure.Geneva.GenevaMonitoring",
        publisher: "Microsoft.Azure.Geneva",
        settings: {},
        type: "GenevaMonitoring",
        typeHandlerVersion: "2.0",
    }],
    vmImageOffer: "WindowsServer",
    vmImagePublisher: "MicrosoftWindowsServer",
    vmImageSku: "2016-Datacenter-Server-Core",
    vmImageVersion: "latest",
    vmInstanceCount: 10,
    vmManagedIdentity: {
        userAssignedIdentities: [
            "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/myIdentity",
            "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/myIdentity2",
        ],
    },
    vmSecrets: [{
        sourceVault: {
            id: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.KeyVault/vaults/myVault",
        },
        vaultCertificates: [{
            certificateStore: "My",
            certificateUrl: "https://myVault.vault.azure.net:443/secrets/myCert/ef1a31d39e1f46bca33def54b6cda54c",
        }],
    }],
    vmSetupActions: [
        "EnableContainers",
        "EnableHyperV",
    ],
    vmSize: "Standard_DS3",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

node_type = azure_native.servicefabric.NodeType("nodeType",
    additional_data_disks=[
        azure_native.servicefabric.VmssDataDiskArgs(
            disk_letter="F",
            disk_size_gb=256,
            disk_type="StandardSSD_LRS",
            lun=1,
        ),
        azure_native.servicefabric.VmssDataDiskArgs(
            disk_letter="G",
            disk_size_gb=150,
            disk_type="Premium_LRS",
            lun=2,
        ),
    ],
    capacities={
        "ClientConnections": "65536",
    },
    cluster_name="myCluster",
    data_disk_letter="S",
    data_disk_size_gb=200,
    data_disk_type="Premium_LRS",
    enable_accelerated_networking=True,
    enable_encryption_at_host=True,
    enable_node_public_ip=True,
    enable_over_provisioning=False,
    eviction_policy="Deallocate",
    frontend_configurations=[azure_native.servicefabric.FrontendConfigurationArgs(
        application_gateway_backend_address_pool_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.Network/applicationGateways/appgw-test/backendAddressPools/appgwBepoolTest",
        load_balancer_backend_address_pool_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.Network/loadBalancers/test-LB/backendAddressPools/LoadBalancerBEAddressPool",
        load_balancer_inbound_nat_pool_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.Network/loadBalancers/test-LB/inboundNatPools/LoadBalancerNATPool",
    )],
    is_primary=False,
    is_spot_vm=True,
    is_stateless=True,
    multiple_placement_groups=True,
    node_type_name="BE",
    placement_properties={
        "HasSSD": "true",
        "NodeColor": "green",
        "SomeProperty": "5",
    },
    resource_group_name="resRg",
    secure_boot_enabled=True,
    security_type="TrustedLaunch",
    spot_restore_timeout="PT30M",
    subnet_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.Network/virtualNetworks/vnet1/subnets/subnet1",
    use_default_public_load_balancer=True,
    use_ephemeral_os_disk=True,
    vm_extensions=[azure_native.servicefabric.VMSSExtensionArgs(
        auto_upgrade_minor_version=True,
        enable_automatic_upgrade=True,
        force_update_tag="v.1.0",
        name="Microsoft.Azure.Geneva.GenevaMonitoring",
        publisher="Microsoft.Azure.Geneva",
        settings={},
        type="GenevaMonitoring",
        type_handler_version="2.0",
    )],
    vm_image_offer="WindowsServer",
    vm_image_publisher="MicrosoftWindowsServer",
    vm_image_sku="2016-Datacenter-Server-Core",
    vm_image_version="latest",
    vm_instance_count=10,
    vm_managed_identity=azure_native.servicefabric.VmManagedIdentityArgs(
        user_assigned_identities=[
            "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/myIdentity",
            "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/myIdentity2",
        ],
    ),
    vm_secrets=[{
        "sourceVault": azure_native.servicefabric.SubResourceArgs(
            id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.KeyVault/vaults/myVault",
        ),
        "vaultCertificates": [azure_native.servicefabric.VaultCertificateArgs(
            certificate_store="My",
            certificate_url="https://myVault.vault.azure.net:443/secrets/myCert/ef1a31d39e1f46bca33def54b6cda54c",
        )],
    }],
    vm_setup_actions=[
        "EnableContainers",
        "EnableHyperV",
    ],
    vm_size="Standard_DS3")

```

```yaml
resources:
  nodeType:
    type: azure-native:servicefabric:NodeType
    properties:
      additionalDataDisks:
        - diskLetter: F
          diskSizeGB: 256
          diskType: StandardSSD_LRS
          lun: 1
        - diskLetter: G
          diskSizeGB: 150
          diskType: Premium_LRS
          lun: 2
      capacities:
        ClientConnections: '65536'
      clusterName: myCluster
      dataDiskLetter: S
      dataDiskSizeGB: 200
      dataDiskType: Premium_LRS
      enableAcceleratedNetworking: true
      enableEncryptionAtHost: true
      enableNodePublicIP: true
      enableOverProvisioning: false
      evictionPolicy: Deallocate
      frontendConfigurations:
        - applicationGatewayBackendAddressPoolId: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.Network/applicationGateways/appgw-test/backendAddressPools/appgwBepoolTest
          loadBalancerBackendAddressPoolId: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.Network/loadBalancers/test-LB/backendAddressPools/LoadBalancerBEAddressPool
          loadBalancerInboundNatPoolId: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.Network/loadBalancers/test-LB/inboundNatPools/LoadBalancerNATPool
      isPrimary: false
      isSpotVM: true
      isStateless: true
      multiplePlacementGroups: true
      nodeTypeName: BE
      placementProperties:
        HasSSD: 'true'
        NodeColor: green
        SomeProperty: '5'
      resourceGroupName: resRg
      secureBootEnabled: true
      securityType: TrustedLaunch
      spotRestoreTimeout: PT30M
      subnetId: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.Network/virtualNetworks/vnet1/subnets/subnet1
      useDefaultPublicLoadBalancer: true
      useEphemeralOSDisk: true
      vmExtensions:
        - autoUpgradeMinorVersion: true
          enableAutomaticUpgrade: true
          forceUpdateTag: v.1.0
          name: Microsoft.Azure.Geneva.GenevaMonitoring
          publisher: Microsoft.Azure.Geneva
          settings: {}
          type: GenevaMonitoring
          typeHandlerVersion: '2.0'
      vmImageOffer: WindowsServer
      vmImagePublisher: MicrosoftWindowsServer
      vmImageSku: 2016-Datacenter-Server-Core
      vmImageVersion: latest
      vmInstanceCount: 10
      vmManagedIdentity:
        userAssignedIdentities:
          - /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/myIdentity
          - /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.ManagedIdentity/userAssignedIdentities/myIdentity2
      vmSecrets:
        - sourceVault:
            id: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.KeyVault/vaults/myVault
          vaultCertificates:
            - certificateStore: My
              certificateUrl: https://myVault.vault.azure.net:443/secrets/myCert/ef1a31d39e1f46bca33def54b6cda54c
      vmSetupActions:
        - EnableContainers
        - EnableHyperV
      vmSize: Standard_DS3

```

{{% /example %}}
{{% example %}}
### Put a node type with minimum parameters
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var nodeType = new AzureNative.ServiceFabric.NodeType("nodeType", new()
    {
        ClusterName = "myCluster",
        DataDiskSizeGB = 200,
        IsPrimary = false,
        NodeTypeName = "BE",
        ResourceGroupName = "resRg",
        VmImageOffer = "WindowsServer",
        VmImagePublisher = "MicrosoftWindowsServer",
        VmImageSku = "2016-Datacenter-Server-Core",
        VmImageVersion = "latest",
        VmInstanceCount = 10,
        VmSize = "Standard_D3",
    });

});


```

```go
package main

import (
	servicefabric "github.com/pulumi/pulumi-azure-native-sdk/servicefabric"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := servicefabric.NewNodeType(ctx, "nodeType", &servicefabric.NodeTypeArgs{
			ClusterName:       pulumi.String("myCluster"),
			DataDiskSizeGB:    pulumi.Int(200),
			IsPrimary:         pulumi.Bool(false),
			NodeTypeName:      pulumi.String("BE"),
			ResourceGroupName: pulumi.String("resRg"),
			VmImageOffer:      pulumi.String("WindowsServer"),
			VmImagePublisher:  pulumi.String("MicrosoftWindowsServer"),
			VmImageSku:        pulumi.String("2016-Datacenter-Server-Core"),
			VmImageVersion:    pulumi.String("latest"),
			VmInstanceCount:   pulumi.Int(10),
			VmSize:            pulumi.String("Standard_D3"),
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
import com.pulumi.azurenative.servicefabric.NodeType;
import com.pulumi.azurenative.servicefabric.NodeTypeArgs;
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
        var nodeType = new NodeType("nodeType", NodeTypeArgs.builder()        
            .clusterName("myCluster")
            .dataDiskSizeGB(200)
            .isPrimary(false)
            .nodeTypeName("BE")
            .resourceGroupName("resRg")
            .vmImageOffer("WindowsServer")
            .vmImagePublisher("MicrosoftWindowsServer")
            .vmImageSku("2016-Datacenter-Server-Core")
            .vmImageVersion("latest")
            .vmInstanceCount(10)
            .vmSize("Standard_D3")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const nodeType = new azure_native.servicefabric.NodeType("nodeType", {
    clusterName: "myCluster",
    dataDiskSizeGB: 200,
    isPrimary: false,
    nodeTypeName: "BE",
    resourceGroupName: "resRg",
    vmImageOffer: "WindowsServer",
    vmImagePublisher: "MicrosoftWindowsServer",
    vmImageSku: "2016-Datacenter-Server-Core",
    vmImageVersion: "latest",
    vmInstanceCount: 10,
    vmSize: "Standard_D3",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

node_type = azure_native.servicefabric.NodeType("nodeType",
    cluster_name="myCluster",
    data_disk_size_gb=200,
    is_primary=False,
    node_type_name="BE",
    resource_group_name="resRg",
    vm_image_offer="WindowsServer",
    vm_image_publisher="MicrosoftWindowsServer",
    vm_image_sku="2016-Datacenter-Server-Core",
    vm_image_version="latest",
    vm_instance_count=10,
    vm_size="Standard_D3")

```

```yaml
resources:
  nodeType:
    type: azure-native:servicefabric:NodeType
    properties:
      clusterName: myCluster
      dataDiskSizeGB: 200
      isPrimary: false
      nodeTypeName: BE
      resourceGroupName: resRg
      vmImageOffer: WindowsServer
      vmImagePublisher: MicrosoftWindowsServer
      vmImageSku: 2016-Datacenter-Server-Core
      vmImageVersion: latest
      vmInstanceCount: 10
      vmSize: Standard_D3

```

{{% /example %}}
{{% example %}}
### Put an stateless node type with temporary disk for service fabric
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var nodeType = new AzureNative.ServiceFabric.NodeType("nodeType", new()
    {
        ClusterName = "myCluster",
        EnableEncryptionAtHost = true,
        IsPrimary = false,
        IsStateless = true,
        MultiplePlacementGroups = true,
        NodeTypeName = "BE",
        ResourceGroupName = "resRg",
        UseTempDataDisk = true,
        VmExtensions = new[]
        {
            new AzureNative.ServiceFabric.Inputs.VMSSExtensionArgs
            {
                AutoUpgradeMinorVersion = true,
                Name = "Microsoft.Azure.Geneva.GenevaMonitoring",
                Publisher = "Microsoft.Azure.Geneva",
                Settings = null,
                Type = "GenevaMonitoring",
                TypeHandlerVersion = "2.0",
            },
        },
        VmImageOffer = "WindowsServer",
        VmImagePublisher = "MicrosoftWindowsServer",
        VmImageSku = "2016-Datacenter-Server-Core",
        VmImageVersion = "latest",
        VmInstanceCount = 10,
        VmSize = "Standard_DS3",
    });

});


```

```go
package main

import (
	servicefabric "github.com/pulumi/pulumi-azure-native-sdk/servicefabric"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := servicefabric.NewNodeType(ctx, "nodeType", &servicefabric.NodeTypeArgs{
			ClusterName:             pulumi.String("myCluster"),
			EnableEncryptionAtHost:  pulumi.Bool(true),
			IsPrimary:               pulumi.Bool(false),
			IsStateless:             pulumi.Bool(true),
			MultiplePlacementGroups: pulumi.Bool(true),
			NodeTypeName:            pulumi.String("BE"),
			ResourceGroupName:       pulumi.String("resRg"),
			UseTempDataDisk:         pulumi.Bool(true),
			VmExtensions: []servicefabric.VMSSExtensionArgs{
				{
					AutoUpgradeMinorVersion: pulumi.Bool(true),
					Name:                    pulumi.String("Microsoft.Azure.Geneva.GenevaMonitoring"),
					Publisher:               pulumi.String("Microsoft.Azure.Geneva"),
					Settings:                nil,
					Type:                    pulumi.String("GenevaMonitoring"),
					TypeHandlerVersion:      pulumi.String("2.0"),
				},
			},
			VmImageOffer:     pulumi.String("WindowsServer"),
			VmImagePublisher: pulumi.String("MicrosoftWindowsServer"),
			VmImageSku:       pulumi.String("2016-Datacenter-Server-Core"),
			VmImageVersion:   pulumi.String("latest"),
			VmInstanceCount:  pulumi.Int(10),
			VmSize:           pulumi.String("Standard_DS3"),
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
import com.pulumi.azurenative.servicefabric.NodeType;
import com.pulumi.azurenative.servicefabric.NodeTypeArgs;
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
        var nodeType = new NodeType("nodeType", NodeTypeArgs.builder()        
            .clusterName("myCluster")
            .enableEncryptionAtHost(true)
            .isPrimary(false)
            .isStateless(true)
            .multiplePlacementGroups(true)
            .nodeTypeName("BE")
            .resourceGroupName("resRg")
            .useTempDataDisk(true)
            .vmExtensions(Map.ofEntries(
                Map.entry("autoUpgradeMinorVersion", true),
                Map.entry("name", "Microsoft.Azure.Geneva.GenevaMonitoring"),
                Map.entry("publisher", "Microsoft.Azure.Geneva"),
                Map.entry("settings", ),
                Map.entry("type", "GenevaMonitoring"),
                Map.entry("typeHandlerVersion", "2.0")
            ))
            .vmImageOffer("WindowsServer")
            .vmImagePublisher("MicrosoftWindowsServer")
            .vmImageSku("2016-Datacenter-Server-Core")
            .vmImageVersion("latest")
            .vmInstanceCount(10)
            .vmSize("Standard_DS3")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const nodeType = new azure_native.servicefabric.NodeType("nodeType", {
    clusterName: "myCluster",
    enableEncryptionAtHost: true,
    isPrimary: false,
    isStateless: true,
    multiplePlacementGroups: true,
    nodeTypeName: "BE",
    resourceGroupName: "resRg",
    useTempDataDisk: true,
    vmExtensions: [{
        autoUpgradeMinorVersion: true,
        name: "Microsoft.Azure.Geneva.GenevaMonitoring",
        publisher: "Microsoft.Azure.Geneva",
        settings: {},
        type: "GenevaMonitoring",
        typeHandlerVersion: "2.0",
    }],
    vmImageOffer: "WindowsServer",
    vmImagePublisher: "MicrosoftWindowsServer",
    vmImageSku: "2016-Datacenter-Server-Core",
    vmImageVersion: "latest",
    vmInstanceCount: 10,
    vmSize: "Standard_DS3",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

node_type = azure_native.servicefabric.NodeType("nodeType",
    cluster_name="myCluster",
    enable_encryption_at_host=True,
    is_primary=False,
    is_stateless=True,
    multiple_placement_groups=True,
    node_type_name="BE",
    resource_group_name="resRg",
    use_temp_data_disk=True,
    vm_extensions=[azure_native.servicefabric.VMSSExtensionArgs(
        auto_upgrade_minor_version=True,
        name="Microsoft.Azure.Geneva.GenevaMonitoring",
        publisher="Microsoft.Azure.Geneva",
        settings={},
        type="GenevaMonitoring",
        type_handler_version="2.0",
    )],
    vm_image_offer="WindowsServer",
    vm_image_publisher="MicrosoftWindowsServer",
    vm_image_sku="2016-Datacenter-Server-Core",
    vm_image_version="latest",
    vm_instance_count=10,
    vm_size="Standard_DS3")

```

```yaml
resources:
  nodeType:
    type: azure-native:servicefabric:NodeType
    properties:
      clusterName: myCluster
      enableEncryptionAtHost: true
      isPrimary: false
      isStateless: true
      multiplePlacementGroups: true
      nodeTypeName: BE
      resourceGroupName: resRg
      useTempDataDisk: true
      vmExtensions:
        - autoUpgradeMinorVersion: true
          name: Microsoft.Azure.Geneva.GenevaMonitoring
          publisher: Microsoft.Azure.Geneva
          settings: {}
          type: GenevaMonitoring
          typeHandlerVersion: '2.0'
      vmImageOffer: WindowsServer
      vmImagePublisher: MicrosoftWindowsServer
      vmImageSku: 2016-Datacenter-Server-Core
      vmImageVersion: latest
      vmInstanceCount: 10
      vmSize: Standard_DS3

```

{{% /example %}}
{{% example %}}
### Put node type with custom vm image
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var nodeType = new AzureNative.ServiceFabric.NodeType("nodeType", new()
    {
        ClusterName = "myCluster",
        DataDiskSizeGB = 200,
        IsPrimary = false,
        NodeTypeName = "BE",
        ResourceGroupName = "resRg",
        VmImageResourceId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-custom-image/providers/Microsoft.Compute/galleries/myCustomImages/images/Win2019DC",
        VmInstanceCount = 10,
        VmSize = "Standard_D3",
    });

});


```

```go
package main

import (
	servicefabric "github.com/pulumi/pulumi-azure-native-sdk/servicefabric"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := servicefabric.NewNodeType(ctx, "nodeType", &servicefabric.NodeTypeArgs{
			ClusterName:       pulumi.String("myCluster"),
			DataDiskSizeGB:    pulumi.Int(200),
			IsPrimary:         pulumi.Bool(false),
			NodeTypeName:      pulumi.String("BE"),
			ResourceGroupName: pulumi.String("resRg"),
			VmImageResourceId: pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-custom-image/providers/Microsoft.Compute/galleries/myCustomImages/images/Win2019DC"),
			VmInstanceCount:   pulumi.Int(10),
			VmSize:            pulumi.String("Standard_D3"),
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
import com.pulumi.azurenative.servicefabric.NodeType;
import com.pulumi.azurenative.servicefabric.NodeTypeArgs;
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
        var nodeType = new NodeType("nodeType", NodeTypeArgs.builder()        
            .clusterName("myCluster")
            .dataDiskSizeGB(200)
            .isPrimary(false)
            .nodeTypeName("BE")
            .resourceGroupName("resRg")
            .vmImageResourceId("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-custom-image/providers/Microsoft.Compute/galleries/myCustomImages/images/Win2019DC")
            .vmInstanceCount(10)
            .vmSize("Standard_D3")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const nodeType = new azure_native.servicefabric.NodeType("nodeType", {
    clusterName: "myCluster",
    dataDiskSizeGB: 200,
    isPrimary: false,
    nodeTypeName: "BE",
    resourceGroupName: "resRg",
    vmImageResourceId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-custom-image/providers/Microsoft.Compute/galleries/myCustomImages/images/Win2019DC",
    vmInstanceCount: 10,
    vmSize: "Standard_D3",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

node_type = azure_native.servicefabric.NodeType("nodeType",
    cluster_name="myCluster",
    data_disk_size_gb=200,
    is_primary=False,
    node_type_name="BE",
    resource_group_name="resRg",
    vm_image_resource_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-custom-image/providers/Microsoft.Compute/galleries/myCustomImages/images/Win2019DC",
    vm_instance_count=10,
    vm_size="Standard_D3")

```

```yaml
resources:
  nodeType:
    type: azure-native:servicefabric:NodeType
    properties:
      clusterName: myCluster
      dataDiskSizeGB: 200
      isPrimary: false
      nodeTypeName: BE
      resourceGroupName: resRg
      vmImageResourceId: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-custom-image/providers/Microsoft.Compute/galleries/myCustomImages/images/Win2019DC
      vmInstanceCount: 10
      vmSize: Standard_D3

```

{{% /example %}}
{{% example %}}
### Put node type with dedicated hosts
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var nodeType = new AzureNative.ServiceFabric.NodeType("nodeType", new()
    {
        Capacities = null,
        ClusterName = "myCluster",
        DataDiskSizeGB = 200,
        DataDiskType = "StandardSSD_LRS",
        HostGroupId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/testhostgroupRG/providers/Microsoft.Compute/hostGroups/testHostGroup",
        IsPrimary = false,
        NodeTypeName = "BE",
        PlacementProperties = null,
        ResourceGroupName = "resRg",
        VmImageOffer = "WindowsServer",
        VmImagePublisher = "MicrosoftWindowsServer",
        VmImageSku = "2019-Datacenter",
        VmImageVersion = "latest",
        VmInstanceCount = 10,
        VmSize = "Standard_D8s_v3",
        Zones = new[]
        {
            "1",
        },
    });

});


```

```go
package main

import (
	servicefabric "github.com/pulumi/pulumi-azure-native-sdk/servicefabric"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := servicefabric.NewNodeType(ctx, "nodeType", &servicefabric.NodeTypeArgs{
			Capacities:          nil,
			ClusterName:         pulumi.String("myCluster"),
			DataDiskSizeGB:      pulumi.Int(200),
			DataDiskType:        pulumi.String("StandardSSD_LRS"),
			HostGroupId:         pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/testhostgroupRG/providers/Microsoft.Compute/hostGroups/testHostGroup"),
			IsPrimary:           pulumi.Bool(false),
			NodeTypeName:        pulumi.String("BE"),
			PlacementProperties: nil,
			ResourceGroupName:   pulumi.String("resRg"),
			VmImageOffer:        pulumi.String("WindowsServer"),
			VmImagePublisher:    pulumi.String("MicrosoftWindowsServer"),
			VmImageSku:          pulumi.String("2019-Datacenter"),
			VmImageVersion:      pulumi.String("latest"),
			VmInstanceCount:     pulumi.Int(10),
			VmSize:              pulumi.String("Standard_D8s_v3"),
			Zones: pulumi.StringArray{
				pulumi.String("1"),
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
import com.pulumi.azurenative.servicefabric.NodeType;
import com.pulumi.azurenative.servicefabric.NodeTypeArgs;
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
        var nodeType = new NodeType("nodeType", NodeTypeArgs.builder()        
            .capacities()
            .clusterName("myCluster")
            .dataDiskSizeGB(200)
            .dataDiskType("StandardSSD_LRS")
            .hostGroupId("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/testhostgroupRG/providers/Microsoft.Compute/hostGroups/testHostGroup")
            .isPrimary(false)
            .nodeTypeName("BE")
            .placementProperties()
            .resourceGroupName("resRg")
            .vmImageOffer("WindowsServer")
            .vmImagePublisher("MicrosoftWindowsServer")
            .vmImageSku("2019-Datacenter")
            .vmImageVersion("latest")
            .vmInstanceCount(10)
            .vmSize("Standard_D8s_v3")
            .zones("1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const nodeType = new azure_native.servicefabric.NodeType("nodeType", {
    capacities: {},
    clusterName: "myCluster",
    dataDiskSizeGB: 200,
    dataDiskType: "StandardSSD_LRS",
    hostGroupId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/testhostgroupRG/providers/Microsoft.Compute/hostGroups/testHostGroup",
    isPrimary: false,
    nodeTypeName: "BE",
    placementProperties: {},
    resourceGroupName: "resRg",
    vmImageOffer: "WindowsServer",
    vmImagePublisher: "MicrosoftWindowsServer",
    vmImageSku: "2019-Datacenter",
    vmImageVersion: "latest",
    vmInstanceCount: 10,
    vmSize: "Standard_D8s_v3",
    zones: ["1"],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

node_type = azure_native.servicefabric.NodeType("nodeType",
    capacities={},
    cluster_name="myCluster",
    data_disk_size_gb=200,
    data_disk_type="StandardSSD_LRS",
    host_group_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/testhostgroupRG/providers/Microsoft.Compute/hostGroups/testHostGroup",
    is_primary=False,
    node_type_name="BE",
    placement_properties={},
    resource_group_name="resRg",
    vm_image_offer="WindowsServer",
    vm_image_publisher="MicrosoftWindowsServer",
    vm_image_sku="2019-Datacenter",
    vm_image_version="latest",
    vm_instance_count=10,
    vm_size="Standard_D8s_v3",
    zones=["1"])

```

```yaml
resources:
  nodeType:
    type: azure-native:servicefabric:NodeType
    properties:
      capacities: {}
      clusterName: myCluster
      dataDiskSizeGB: 200
      dataDiskType: StandardSSD_LRS
      hostGroupId: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/testhostgroupRG/providers/Microsoft.Compute/hostGroups/testHostGroup
      isPrimary: false
      nodeTypeName: BE
      placementProperties: {}
      resourceGroupName: resRg
      vmImageOffer: WindowsServer
      vmImagePublisher: MicrosoftWindowsServer
      vmImageSku: 2019-Datacenter
      vmImageVersion: latest
      vmInstanceCount: 10
      vmSize: Standard_D8s_v3
      zones:
        - '1'

```

{{% /example %}}
{{% example %}}
### Put node type with shared galleries custom vm image
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var nodeType = new AzureNative.ServiceFabric.NodeType("nodeType", new()
    {
        ClusterName = "myCluster",
        DataDiskSizeGB = 200,
        IsPrimary = false,
        NodeTypeName = "BE",
        ResourceGroupName = "resRg",
        VmInstanceCount = 10,
        VmSharedGalleryImageId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-custom-image/providers/Microsoft.Compute/sharedGalleries/35349201-a0b3-405e-8a23-9f1450984307-SFSHAREDGALLERY/images/TestNoProdContainerDImage/versions/latest",
        VmSize = "Standard_D3",
    });

});


```

```go
package main

import (
	servicefabric "github.com/pulumi/pulumi-azure-native-sdk/servicefabric"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := servicefabric.NewNodeType(ctx, "nodeType", &servicefabric.NodeTypeArgs{
			ClusterName:            pulumi.String("myCluster"),
			DataDiskSizeGB:         pulumi.Int(200),
			IsPrimary:              pulumi.Bool(false),
			NodeTypeName:           pulumi.String("BE"),
			ResourceGroupName:      pulumi.String("resRg"),
			VmInstanceCount:        pulumi.Int(10),
			VmSharedGalleryImageId: pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-custom-image/providers/Microsoft.Compute/sharedGalleries/35349201-a0b3-405e-8a23-9f1450984307-SFSHAREDGALLERY/images/TestNoProdContainerDImage/versions/latest"),
			VmSize:                 pulumi.String("Standard_D3"),
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
import com.pulumi.azurenative.servicefabric.NodeType;
import com.pulumi.azurenative.servicefabric.NodeTypeArgs;
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
        var nodeType = new NodeType("nodeType", NodeTypeArgs.builder()        
            .clusterName("myCluster")
            .dataDiskSizeGB(200)
            .isPrimary(false)
            .nodeTypeName("BE")
            .resourceGroupName("resRg")
            .vmInstanceCount(10)
            .vmSharedGalleryImageId("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-custom-image/providers/Microsoft.Compute/sharedGalleries/35349201-a0b3-405e-8a23-9f1450984307-SFSHAREDGALLERY/images/TestNoProdContainerDImage/versions/latest")
            .vmSize("Standard_D3")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const nodeType = new azure_native.servicefabric.NodeType("nodeType", {
    clusterName: "myCluster",
    dataDiskSizeGB: 200,
    isPrimary: false,
    nodeTypeName: "BE",
    resourceGroupName: "resRg",
    vmInstanceCount: 10,
    vmSharedGalleryImageId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-custom-image/providers/Microsoft.Compute/sharedGalleries/35349201-a0b3-405e-8a23-9f1450984307-SFSHAREDGALLERY/images/TestNoProdContainerDImage/versions/latest",
    vmSize: "Standard_D3",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

node_type = azure_native.servicefabric.NodeType("nodeType",
    cluster_name="myCluster",
    data_disk_size_gb=200,
    is_primary=False,
    node_type_name="BE",
    resource_group_name="resRg",
    vm_instance_count=10,
    vm_shared_gallery_image_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-custom-image/providers/Microsoft.Compute/sharedGalleries/35349201-a0b3-405e-8a23-9f1450984307-SFSHAREDGALLERY/images/TestNoProdContainerDImage/versions/latest",
    vm_size="Standard_D3")

```

```yaml
resources:
  nodeType:
    type: azure-native:servicefabric:NodeType
    properties:
      clusterName: myCluster
      dataDiskSizeGB: 200
      isPrimary: false
      nodeTypeName: BE
      resourceGroupName: resRg
      vmInstanceCount: 10
      vmSharedGalleryImageId: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/test-custom-image/providers/Microsoft.Compute/sharedGalleries/35349201-a0b3-405e-8a23-9f1450984307-SFSHAREDGALLERY/images/TestNoProdContainerDImage/versions/latest
      vmSize: Standard_D3

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:servicefabric:NodeType BE /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/resRg/providers/Microsoft.ServiceFabric/managedClusters/myCluster/nodeTypes/BE 
```
