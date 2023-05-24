The managed cluster resource

API Version: 2023-02-01-preview.
Previous API Version: 2020-01-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Put a cluster with maximum parameters
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedCluster = new AzureNative.ServiceFabric.ManagedCluster("managedCluster", new()
    {
        AddonFeatures = new[]
        {
            "DnsService",
            "BackupRestoreService",
            "ResourceMonitorService",
        },
        AdminPassword = "{vm-password}",
        AdminUserName = "vmadmin",
        AllowRdpAccess = true,
        ApplicationTypeVersionsCleanupPolicy = new AzureNative.ServiceFabric.Inputs.ApplicationTypeVersionsCleanupPolicyArgs
        {
            MaxUnusedVersionsToKeep = 3,
        },
        AuxiliarySubnets = new[]
        {
            new AzureNative.ServiceFabric.Inputs.SubnetArgs
            {
                EnableIpv6 = true,
                Name = "testSubnet1",
                NetworkSecurityGroupId = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.Network/networkSecurityGroups/sn1",
                PrivateEndpointNetworkPolicies = "enabled",
                PrivateLinkServiceNetworkPolicies = "enabled",
            },
        },
        ClientConnectionPort = 19000,
        ClusterCodeVersion = "7.1.168.9494",
        ClusterName = "myCluster",
        ClusterUpgradeMode = "Manual",
        DnsName = "myCluster",
        EnableAutoOSUpgrade = true,
        EnableIpv6 = true,
        FabricSettings = new[]
        {
            new AzureNative.ServiceFabric.Inputs.SettingsSectionDescriptionArgs
            {
                Name = "ManagedIdentityTokenService",
                Parameters = new[]
                {
                    new AzureNative.ServiceFabric.Inputs.SettingsParameterDescriptionArgs
                    {
                        Name = "IsEnabled",
                        Value = "true",
                    },
                },
            },
        },
        HttpGatewayConnectionPort = 19080,
        IpTags = new[]
        {
            new AzureNative.ServiceFabric.Inputs.IPTagArgs
            {
                IpTagType = "FirstPartyUsage",
                Tag = "SQL",
            },
        },
        LoadBalancingRules = new[]
        {
            new AzureNative.ServiceFabric.Inputs.LoadBalancingRuleArgs
            {
                BackendPort = 80,
                FrontendPort = 80,
                ProbePort = 80,
                ProbeProtocol = "http",
                Protocol = "http",
            },
            new AzureNative.ServiceFabric.Inputs.LoadBalancingRuleArgs
            {
                BackendPort = 443,
                FrontendPort = 443,
                ProbePort = 443,
                ProbeProtocol = "http",
                Protocol = "http",
            },
            new AzureNative.ServiceFabric.Inputs.LoadBalancingRuleArgs
            {
                BackendPort = 10000,
                FrontendPort = 10000,
                LoadDistribution = "Default",
                ProbePort = 10000,
                ProbeProtocol = "http",
                Protocol = "tcp",
            },
        },
        Location = "eastus",
        NetworkSecurityRules = new[]
        {
            new AzureNative.ServiceFabric.Inputs.NetworkSecurityRuleArgs
            {
                Access = "allow",
                Description = "Test description",
                DestinationAddressPrefixes = new[]
                {
                    "*",
                },
                DestinationPortRanges = new[]
                {
                    "*",
                },
                Direction = "inbound",
                Name = "TestName",
                Priority = 1010,
                Protocol = "tcp",
                SourceAddressPrefixes = new[]
                {
                    "*",
                },
                SourcePortRanges = new[]
                {
                    "*",
                },
            },
            new AzureNative.ServiceFabric.Inputs.NetworkSecurityRuleArgs
            {
                Access = "allow",
                DestinationAddressPrefix = "*",
                DestinationPortRange = "33500-33699",
                Direction = "inbound",
                Name = "AllowARM",
                Priority = 2002,
                Protocol = "*",
                SourceAddressPrefix = "AzureResourceManager",
                SourcePortRange = "*",
            },
        },
        ResourceGroupName = "resRg",
        ServiceEndpoints = new[]
        {
            new AzureNative.ServiceFabric.Inputs.ServiceEndpointArgs
            {
                Locations = new[]
                {
                    "eastus2",
                    "usnorth",
                },
                Service = "Microsoft.Storage",
            },
        },
        Sku = new AzureNative.ServiceFabric.Inputs.SkuArgs
        {
            Name = "Basic",
        },
        Tags = null,
        UseCustomVnet = true,
        ZonalResiliency = true,
        ZonalUpdateMode = "Fast",
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
		_, err := servicefabric.NewManagedCluster(ctx, "managedCluster", &servicefabric.ManagedClusterArgs{
			AddonFeatures: pulumi.StringArray{
				pulumi.String("DnsService"),
				pulumi.String("BackupRestoreService"),
				pulumi.String("ResourceMonitorService"),
			},
			AdminPassword:  pulumi.String("{vm-password}"),
			AdminUserName:  pulumi.String("vmadmin"),
			AllowRdpAccess: pulumi.Bool(true),
			ApplicationTypeVersionsCleanupPolicy: &servicefabric.ApplicationTypeVersionsCleanupPolicyArgs{
				MaxUnusedVersionsToKeep: pulumi.Int(3),
			},
			AuxiliarySubnets: []servicefabric.SubnetArgs{
				{
					EnableIpv6:                        pulumi.Bool(true),
					Name:                              pulumi.String("testSubnet1"),
					NetworkSecurityGroupId:            pulumi.String("/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.Network/networkSecurityGroups/sn1"),
					PrivateEndpointNetworkPolicies:    pulumi.String("enabled"),
					PrivateLinkServiceNetworkPolicies: pulumi.String("enabled"),
				},
			},
			ClientConnectionPort: pulumi.Int(19000),
			ClusterCodeVersion:   pulumi.String("7.1.168.9494"),
			ClusterName:          pulumi.String("myCluster"),
			ClusterUpgradeMode:   pulumi.String("Manual"),
			DnsName:              pulumi.String("myCluster"),
			EnableAutoOSUpgrade:  pulumi.Bool(true),
			EnableIpv6:           pulumi.Bool(true),
			FabricSettings: []servicefabric.SettingsSectionDescriptionArgs{
				{
					Name: pulumi.String("ManagedIdentityTokenService"),
					Parameters: servicefabric.SettingsParameterDescriptionArray{
						{
							Name:  pulumi.String("IsEnabled"),
							Value: pulumi.String("true"),
						},
					},
				},
			},
			HttpGatewayConnectionPort: pulumi.Int(19080),
			IpTags: []servicefabric.IPTagArgs{
				{
					IpTagType: pulumi.String("FirstPartyUsage"),
					Tag:       pulumi.String("SQL"),
				},
			},
			LoadBalancingRules: []servicefabric.LoadBalancingRuleArgs{
				{
					BackendPort:   pulumi.Int(80),
					FrontendPort:  pulumi.Int(80),
					ProbePort:     pulumi.Int(80),
					ProbeProtocol: pulumi.String("http"),
					Protocol:      pulumi.String("http"),
				},
				{
					BackendPort:   pulumi.Int(443),
					FrontendPort:  pulumi.Int(443),
					ProbePort:     pulumi.Int(443),
					ProbeProtocol: pulumi.String("http"),
					Protocol:      pulumi.String("http"),
				},
				{
					BackendPort:      pulumi.Int(10000),
					FrontendPort:     pulumi.Int(10000),
					LoadDistribution: pulumi.String("Default"),
					ProbePort:        pulumi.Int(10000),
					ProbeProtocol:    pulumi.String("http"),
					Protocol:         pulumi.String("tcp"),
				},
			},
			Location: pulumi.String("eastus"),
			NetworkSecurityRules: []servicefabric.NetworkSecurityRuleArgs{
				{
					Access:      pulumi.String("allow"),
					Description: pulumi.String("Test description"),
					DestinationAddressPrefixes: pulumi.StringArray{
						pulumi.String("*"),
					},
					DestinationPortRanges: pulumi.StringArray{
						pulumi.String("*"),
					},
					Direction: pulumi.String("inbound"),
					Name:      pulumi.String("TestName"),
					Priority:  pulumi.Int(1010),
					Protocol:  pulumi.String("tcp"),
					SourceAddressPrefixes: pulumi.StringArray{
						pulumi.String("*"),
					},
					SourcePortRanges: pulumi.StringArray{
						pulumi.String("*"),
					},
				},
				{
					Access:                   pulumi.String("allow"),
					DestinationAddressPrefix: pulumi.String("*"),
					DestinationPortRange:     pulumi.String("33500-33699"),
					Direction:                pulumi.String("inbound"),
					Name:                     pulumi.String("AllowARM"),
					Priority:                 pulumi.Int(2002),
					Protocol:                 pulumi.String("*"),
					SourceAddressPrefix:      pulumi.String("AzureResourceManager"),
					SourcePortRange:          pulumi.String("*"),
				},
			},
			ResourceGroupName: pulumi.String("resRg"),
			ServiceEndpoints: []servicefabric.ServiceEndpointArgs{
				{
					Locations: pulumi.StringArray{
						pulumi.String("eastus2"),
						pulumi.String("usnorth"),
					},
					Service: pulumi.String("Microsoft.Storage"),
				},
			},
			Sku: &servicefabric.SkuArgs{
				Name: pulumi.String("Basic"),
			},
			Tags:            nil,
			UseCustomVnet:   pulumi.Bool(true),
			ZonalResiliency: pulumi.Bool(true),
			ZonalUpdateMode: pulumi.String("Fast"),
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
import com.pulumi.azurenative.servicefabric.ManagedCluster;
import com.pulumi.azurenative.servicefabric.ManagedClusterArgs;
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
            .addonFeatures(            
                "DnsService",
                "BackupRestoreService",
                "ResourceMonitorService")
            .adminPassword("{vm-password}")
            .adminUserName("vmadmin")
            .allowRdpAccess(true)
            .applicationTypeVersionsCleanupPolicy(Map.of("maxUnusedVersionsToKeep", 3))
            .auxiliarySubnets(Map.ofEntries(
                Map.entry("enableIpv6", true),
                Map.entry("name", "testSubnet1"),
                Map.entry("networkSecurityGroupId", "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.Network/networkSecurityGroups/sn1"),
                Map.entry("privateEndpointNetworkPolicies", "enabled"),
                Map.entry("privateLinkServiceNetworkPolicies", "enabled")
            ))
            .clientConnectionPort(19000)
            .clusterCodeVersion("7.1.168.9494")
            .clusterName("myCluster")
            .clusterUpgradeMode("Manual")
            .dnsName("myCluster")
            .enableAutoOSUpgrade(true)
            .enableIpv6(true)
            .fabricSettings(Map.ofEntries(
                Map.entry("name", "ManagedIdentityTokenService"),
                Map.entry("parameters", Map.ofEntries(
                    Map.entry("name", "IsEnabled"),
                    Map.entry("value", "true")
                ))
            ))
            .httpGatewayConnectionPort(19080)
            .ipTags(Map.ofEntries(
                Map.entry("ipTagType", "FirstPartyUsage"),
                Map.entry("tag", "SQL")
            ))
            .loadBalancingRules(            
                Map.ofEntries(
                    Map.entry("backendPort", 80),
                    Map.entry("frontendPort", 80),
                    Map.entry("probePort", 80),
                    Map.entry("probeProtocol", "http"),
                    Map.entry("protocol", "http")
                ),
                Map.ofEntries(
                    Map.entry("backendPort", 443),
                    Map.entry("frontendPort", 443),
                    Map.entry("probePort", 443),
                    Map.entry("probeProtocol", "http"),
                    Map.entry("protocol", "http")
                ),
                Map.ofEntries(
                    Map.entry("backendPort", 10000),
                    Map.entry("frontendPort", 10000),
                    Map.entry("loadDistribution", "Default"),
                    Map.entry("probePort", 10000),
                    Map.entry("probeProtocol", "http"),
                    Map.entry("protocol", "tcp")
                ))
            .location("eastus")
            .networkSecurityRules(            
                Map.ofEntries(
                    Map.entry("access", "allow"),
                    Map.entry("description", "Test description"),
                    Map.entry("destinationAddressPrefixes", "*"),
                    Map.entry("destinationPortRanges", "*"),
                    Map.entry("direction", "inbound"),
                    Map.entry("name", "TestName"),
                    Map.entry("priority", 1010),
                    Map.entry("protocol", "tcp"),
                    Map.entry("sourceAddressPrefixes", "*"),
                    Map.entry("sourcePortRanges", "*")
                ),
                Map.ofEntries(
                    Map.entry("access", "allow"),
                    Map.entry("destinationAddressPrefix", "*"),
                    Map.entry("destinationPortRange", "33500-33699"),
                    Map.entry("direction", "inbound"),
                    Map.entry("name", "AllowARM"),
                    Map.entry("priority", 2002),
                    Map.entry("protocol", "*"),
                    Map.entry("sourceAddressPrefix", "AzureResourceManager"),
                    Map.entry("sourcePortRange", "*")
                ))
            .resourceGroupName("resRg")
            .serviceEndpoints(Map.ofEntries(
                Map.entry("locations",                 
                    "eastus2",
                    "usnorth"),
                Map.entry("service", "Microsoft.Storage")
            ))
            .sku(Map.of("name", "Basic"))
            .tags()
            .useCustomVnet(true)
            .zonalResiliency(true)
            .zonalUpdateMode("Fast")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedCluster = new azure_native.servicefabric.ManagedCluster("managedCluster", {
    addonFeatures: [
        "DnsService",
        "BackupRestoreService",
        "ResourceMonitorService",
    ],
    adminPassword: "{vm-password}",
    adminUserName: "vmadmin",
    allowRdpAccess: true,
    applicationTypeVersionsCleanupPolicy: {
        maxUnusedVersionsToKeep: 3,
    },
    auxiliarySubnets: [{
        enableIpv6: true,
        name: "testSubnet1",
        networkSecurityGroupId: "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.Network/networkSecurityGroups/sn1",
        privateEndpointNetworkPolicies: "enabled",
        privateLinkServiceNetworkPolicies: "enabled",
    }],
    clientConnectionPort: 19000,
    clusterCodeVersion: "7.1.168.9494",
    clusterName: "myCluster",
    clusterUpgradeMode: "Manual",
    dnsName: "myCluster",
    enableAutoOSUpgrade: true,
    enableIpv6: true,
    fabricSettings: [{
        name: "ManagedIdentityTokenService",
        parameters: [{
            name: "IsEnabled",
            value: "true",
        }],
    }],
    httpGatewayConnectionPort: 19080,
    ipTags: [{
        ipTagType: "FirstPartyUsage",
        tag: "SQL",
    }],
    loadBalancingRules: [
        {
            backendPort: 80,
            frontendPort: 80,
            probePort: 80,
            probeProtocol: "http",
            protocol: "http",
        },
        {
            backendPort: 443,
            frontendPort: 443,
            probePort: 443,
            probeProtocol: "http",
            protocol: "http",
        },
        {
            backendPort: 10000,
            frontendPort: 10000,
            loadDistribution: "Default",
            probePort: 10000,
            probeProtocol: "http",
            protocol: "tcp",
        },
    ],
    location: "eastus",
    networkSecurityRules: [
        {
            access: "allow",
            description: "Test description",
            destinationAddressPrefixes: ["*"],
            destinationPortRanges: ["*"],
            direction: "inbound",
            name: "TestName",
            priority: 1010,
            protocol: "tcp",
            sourceAddressPrefixes: ["*"],
            sourcePortRanges: ["*"],
        },
        {
            access: "allow",
            destinationAddressPrefix: "*",
            destinationPortRange: "33500-33699",
            direction: "inbound",
            name: "AllowARM",
            priority: 2002,
            protocol: "*",
            sourceAddressPrefix: "AzureResourceManager",
            sourcePortRange: "*",
        },
    ],
    resourceGroupName: "resRg",
    serviceEndpoints: [{
        locations: [
            "eastus2",
            "usnorth",
        ],
        service: "Microsoft.Storage",
    }],
    sku: {
        name: "Basic",
    },
    tags: {},
    useCustomVnet: true,
    zonalResiliency: true,
    zonalUpdateMode: "Fast",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_cluster = azure_native.servicefabric.ManagedCluster("managedCluster",
    addon_features=[
        "DnsService",
        "BackupRestoreService",
        "ResourceMonitorService",
    ],
    admin_password="{vm-password}",
    admin_user_name="vmadmin",
    allow_rdp_access=True,
    application_type_versions_cleanup_policy=azure_native.servicefabric.ApplicationTypeVersionsCleanupPolicyArgs(
        max_unused_versions_to_keep=3,
    ),
    auxiliary_subnets=[azure_native.servicefabric.SubnetArgs(
        enable_ipv6=True,
        name="testSubnet1",
        network_security_group_id="/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.Network/networkSecurityGroups/sn1",
        private_endpoint_network_policies="enabled",
        private_link_service_network_policies="enabled",
    )],
    client_connection_port=19000,
    cluster_code_version="7.1.168.9494",
    cluster_name="myCluster",
    cluster_upgrade_mode="Manual",
    dns_name="myCluster",
    enable_auto_os_upgrade=True,
    enable_ipv6=True,
    fabric_settings=[{
        "name": "ManagedIdentityTokenService",
        "parameters": [azure_native.servicefabric.SettingsParameterDescriptionArgs(
            name="IsEnabled",
            value="true",
        )],
    }],
    http_gateway_connection_port=19080,
    ip_tags=[azure_native.servicefabric.IPTagArgs(
        ip_tag_type="FirstPartyUsage",
        tag="SQL",
    )],
    load_balancing_rules=[
        azure_native.servicefabric.LoadBalancingRuleArgs(
            backend_port=80,
            frontend_port=80,
            probe_port=80,
            probe_protocol="http",
            protocol="http",
        ),
        azure_native.servicefabric.LoadBalancingRuleArgs(
            backend_port=443,
            frontend_port=443,
            probe_port=443,
            probe_protocol="http",
            protocol="http",
        ),
        azure_native.servicefabric.LoadBalancingRuleArgs(
            backend_port=10000,
            frontend_port=10000,
            load_distribution="Default",
            probe_port=10000,
            probe_protocol="http",
            protocol="tcp",
        ),
    ],
    location="eastus",
    network_security_rules=[
        azure_native.servicefabric.NetworkSecurityRuleArgs(
            access="allow",
            description="Test description",
            destination_address_prefixes=["*"],
            destination_port_ranges=["*"],
            direction="inbound",
            name="TestName",
            priority=1010,
            protocol="tcp",
            source_address_prefixes=["*"],
            source_port_ranges=["*"],
        ),
        azure_native.servicefabric.NetworkSecurityRuleArgs(
            access="allow",
            destination_address_prefix="*",
            destination_port_range="33500-33699",
            direction="inbound",
            name="AllowARM",
            priority=2002,
            protocol="*",
            source_address_prefix="AzureResourceManager",
            source_port_range="*",
        ),
    ],
    resource_group_name="resRg",
    service_endpoints=[azure_native.servicefabric.ServiceEndpointArgs(
        locations=[
            "eastus2",
            "usnorth",
        ],
        service="Microsoft.Storage",
    )],
    sku=azure_native.servicefabric.SkuArgs(
        name="Basic",
    ),
    tags={},
    use_custom_vnet=True,
    zonal_resiliency=True,
    zonal_update_mode="Fast")

```

```yaml
resources:
  managedCluster:
    type: azure-native:servicefabric:ManagedCluster
    properties:
      addonFeatures:
        - DnsService
        - BackupRestoreService
        - ResourceMonitorService
      adminPassword: '{vm-password}'
      adminUserName: vmadmin
      allowRdpAccess: true
      applicationTypeVersionsCleanupPolicy:
        maxUnusedVersionsToKeep: 3
      auxiliarySubnets:
        - enableIpv6: true
          name: testSubnet1
          networkSecurityGroupId: /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/resRg/providers/Microsoft.Network/networkSecurityGroups/sn1
          privateEndpointNetworkPolicies: enabled
          privateLinkServiceNetworkPolicies: enabled
      clientConnectionPort: 19000
      clusterCodeVersion: 7.1.168.9494
      clusterName: myCluster
      clusterUpgradeMode: Manual
      dnsName: myCluster
      enableAutoOSUpgrade: true
      enableIpv6: true
      fabricSettings:
        - name: ManagedIdentityTokenService
          parameters:
            - name: IsEnabled
              value: 'true'
      httpGatewayConnectionPort: 19080
      ipTags:
        - ipTagType: FirstPartyUsage
          tag: SQL
      loadBalancingRules:
        - backendPort: 80
          frontendPort: 80
          probePort: 80
          probeProtocol: http
          protocol: http
        - backendPort: 443
          frontendPort: 443
          probePort: 443
          probeProtocol: http
          protocol: http
        - backendPort: 10000
          frontendPort: 10000
          loadDistribution: Default
          probePort: 10000
          probeProtocol: http
          protocol: tcp
      location: eastus
      networkSecurityRules:
        - access: allow
          description: Test description
          destinationAddressPrefixes:
            - '*'
          destinationPortRanges:
            - '*'
          direction: inbound
          name: TestName
          priority: 1010
          protocol: tcp
          sourceAddressPrefixes:
            - '*'
          sourcePortRanges:
            - '*'
        - access: allow
          destinationAddressPrefix: '*'
          destinationPortRange: 33500-33699
          direction: inbound
          name: AllowARM
          priority: 2002
          protocol: '*'
          sourceAddressPrefix: AzureResourceManager
          sourcePortRange: '*'
      resourceGroupName: resRg
      serviceEndpoints:
        - locations:
            - eastus2
            - usnorth
          service: Microsoft.Storage
      sku:
        name: Basic
      tags: {}
      useCustomVnet: true
      zonalResiliency: true
      zonalUpdateMode: Fast

```

{{% /example %}}
{{% example %}}
### Put a cluster with minimum parameters
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var managedCluster = new AzureNative.ServiceFabric.ManagedCluster("managedCluster", new()
    {
        AdminPassword = "{vm-password}",
        AdminUserName = "vmadmin",
        ClusterName = "myCluster",
        ClusterUpgradeCadence = "Wave1",
        ClusterUpgradeMode = "Automatic",
        DnsName = "myCluster",
        FabricSettings = new[]
        {
            new AzureNative.ServiceFabric.Inputs.SettingsSectionDescriptionArgs
            {
                Name = "ManagedIdentityTokenService",
                Parameters = new[]
                {
                    new AzureNative.ServiceFabric.Inputs.SettingsParameterDescriptionArgs
                    {
                        Name = "IsEnabled",
                        Value = "true",
                    },
                },
            },
        },
        Location = "eastus",
        ResourceGroupName = "resRg",
        Sku = new AzureNative.ServiceFabric.Inputs.SkuArgs
        {
            Name = "Basic",
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
		_, err := servicefabric.NewManagedCluster(ctx, "managedCluster", &servicefabric.ManagedClusterArgs{
			AdminPassword:         pulumi.String("{vm-password}"),
			AdminUserName:         pulumi.String("vmadmin"),
			ClusterName:           pulumi.String("myCluster"),
			ClusterUpgradeCadence: pulumi.String("Wave1"),
			ClusterUpgradeMode:    pulumi.String("Automatic"),
			DnsName:               pulumi.String("myCluster"),
			FabricSettings: []servicefabric.SettingsSectionDescriptionArgs{
				{
					Name: pulumi.String("ManagedIdentityTokenService"),
					Parameters: servicefabric.SettingsParameterDescriptionArray{
						{
							Name:  pulumi.String("IsEnabled"),
							Value: pulumi.String("true"),
						},
					},
				},
			},
			Location:          pulumi.String("eastus"),
			ResourceGroupName: pulumi.String("resRg"),
			Sku: &servicefabric.SkuArgs{
				Name: pulumi.String("Basic"),
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
import com.pulumi.azurenative.servicefabric.ManagedCluster;
import com.pulumi.azurenative.servicefabric.ManagedClusterArgs;
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
            .adminPassword("{vm-password}")
            .adminUserName("vmadmin")
            .clusterName("myCluster")
            .clusterUpgradeCadence("Wave1")
            .clusterUpgradeMode("Automatic")
            .dnsName("myCluster")
            .fabricSettings(Map.ofEntries(
                Map.entry("name", "ManagedIdentityTokenService"),
                Map.entry("parameters", Map.ofEntries(
                    Map.entry("name", "IsEnabled"),
                    Map.entry("value", "true")
                ))
            ))
            .location("eastus")
            .resourceGroupName("resRg")
            .sku(Map.of("name", "Basic"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const managedCluster = new azure_native.servicefabric.ManagedCluster("managedCluster", {
    adminPassword: "{vm-password}",
    adminUserName: "vmadmin",
    clusterName: "myCluster",
    clusterUpgradeCadence: "Wave1",
    clusterUpgradeMode: "Automatic",
    dnsName: "myCluster",
    fabricSettings: [{
        name: "ManagedIdentityTokenService",
        parameters: [{
            name: "IsEnabled",
            value: "true",
        }],
    }],
    location: "eastus",
    resourceGroupName: "resRg",
    sku: {
        name: "Basic",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

managed_cluster = azure_native.servicefabric.ManagedCluster("managedCluster",
    admin_password="{vm-password}",
    admin_user_name="vmadmin",
    cluster_name="myCluster",
    cluster_upgrade_cadence="Wave1",
    cluster_upgrade_mode="Automatic",
    dns_name="myCluster",
    fabric_settings=[{
        "name": "ManagedIdentityTokenService",
        "parameters": [azure_native.servicefabric.SettingsParameterDescriptionArgs(
            name="IsEnabled",
            value="true",
        )],
    }],
    location="eastus",
    resource_group_name="resRg",
    sku=azure_native.servicefabric.SkuArgs(
        name="Basic",
    ))

```

```yaml
resources:
  managedCluster:
    type: azure-native:servicefabric:ManagedCluster
    properties:
      adminPassword: '{vm-password}'
      adminUserName: vmadmin
      clusterName: myCluster
      clusterUpgradeCadence: Wave1
      clusterUpgradeMode: Automatic
      dnsName: myCluster
      fabricSettings:
        - name: ManagedIdentityTokenService
          parameters:
            - name: IsEnabled
              value: 'true'
      location: eastus
      resourceGroupName: resRg
      sku:
        name: Basic

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:servicefabric:ManagedCluster myCluster /subscriptions/00000000-0000-0000-0000-000000000000/resourcegroups/resRg/providers/Microsoft.ServiceFabric/managedClusters/myCluster 
```
