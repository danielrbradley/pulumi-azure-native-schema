Define the Virtual Instance for SAP solutions resource.
API Version: 2023-04-01.
Previous API Version: 2021-12-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create Infrastructure (with OS configuration) with custom resource names for Distributed System
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sapVirtualInstance = new AzureNative.Workloads.SAPVirtualInstance("sapVirtualInstance", new()
    {
        Configuration = new AzureNative.Workloads.Inputs.DeploymentWithOSConfigurationArgs
        {
            AppLocation = "eastus",
            ConfigurationType = "DeploymentWithOSConfig",
            InfrastructureConfiguration = new AzureNative.Workloads.Inputs.ThreeTierConfigurationArgs
            {
                AppResourceGroup = "X00-RG",
                ApplicationServer = new AzureNative.Workloads.Inputs.ApplicationServerConfigurationArgs
                {
                    InstanceCount = 6,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_E32ds_v4",
                    },
                },
                CentralServer = new AzureNative.Workloads.Inputs.CentralServerConfigurationArgs
                {
                    InstanceCount = 1,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_E16ds_v4",
                    },
                },
                CustomResourceNames = new AzureNative.Workloads.Inputs.ThreeTierFullResourceNamesArgs
                {
                    ApplicationServer = new AzureNative.Workloads.Inputs.ApplicationServerFullResourceNamesArgs
                    {
                        AvailabilitySetName = "appAvSet",
                        VirtualMachines = new[]
                        {
                            new AzureNative.Workloads.Inputs.VirtualMachineResourceNamesArgs
                            {
                                DataDiskNames = 
                                {
                                    { "default", new[]
                                    {
                                        "app0disk0",
                                    } },
                                },
                                HostName = "apphostName0",
                                NetworkInterfaces = new[]
                                {
                                    new AzureNative.Workloads.Inputs.NetworkInterfaceResourceNamesArgs
                                    {
                                        NetworkInterfaceName = "appnic0",
                                    },
                                },
                                OsDiskName = "app0osdisk",
                                VmName = "appvm0",
                            },
                            new AzureNative.Workloads.Inputs.VirtualMachineResourceNamesArgs
                            {
                                DataDiskNames = 
                                {
                                    { "default", new[]
                                    {
                                        "app1disk0",
                                    } },
                                },
                                HostName = "apphostName1",
                                NetworkInterfaces = new[]
                                {
                                    new AzureNative.Workloads.Inputs.NetworkInterfaceResourceNamesArgs
                                    {
                                        NetworkInterfaceName = "appnic1",
                                    },
                                },
                                OsDiskName = "app1osdisk",
                                VmName = "appvm1",
                            },
                        },
                    },
                    CentralServer = new AzureNative.Workloads.Inputs.CentralServerFullResourceNamesArgs
                    {
                        VirtualMachines = new[]
                        {
                            new AzureNative.Workloads.Inputs.VirtualMachineResourceNamesArgs
                            {
                                DataDiskNames = 
                                {
                                    { "default", new[]
                                    {
                                        "ascsdisk0",
                                    } },
                                },
                                HostName = "ascshostName",
                                NetworkInterfaces = new[]
                                {
                                    new AzureNative.Workloads.Inputs.NetworkInterfaceResourceNamesArgs
                                    {
                                        NetworkInterfaceName = "ascsnic",
                                    },
                                },
                                OsDiskName = "ascsosdisk",
                                VmName = "ascsvm",
                            },
                        },
                    },
                    DatabaseServer = new AzureNative.Workloads.Inputs.DatabaseServerFullResourceNamesArgs
                    {
                        VirtualMachines = new[]
                        {
                            new AzureNative.Workloads.Inputs.VirtualMachineResourceNamesArgs
                            {
                                DataDiskNames = 
                                {
                                    { "hanaData", new[]
                                    {
                                        "hanadata0",
                                        "hanadata1",
                                    } },
                                    { "hanaLog", new[]
                                    {
                                        "hanalog0",
                                        "hanalog1",
                                        "hanalog2",
                                    } },
                                    { "hanaShared", new[]
                                    {
                                        "hanashared0",
                                        "hanashared1",
                                    } },
                                    { "usrSap", new[]
                                    {
                                        "usrsap0",
                                    } },
                                },
                                HostName = "dbhostName",
                                NetworkInterfaces = new[]
                                {
                                    new AzureNative.Workloads.Inputs.NetworkInterfaceResourceNamesArgs
                                    {
                                        NetworkInterfaceName = "dbnic",
                                    },
                                },
                                OsDiskName = "dbosdisk",
                                VmName = "dbvm",
                            },
                        },
                    },
                    NamingPatternType = "FullResourceName",
                    SharedStorage = new AzureNative.Workloads.Inputs.SharedStorageResourceNamesArgs
                    {
                        SharedStorageAccountName = "storageacc",
                        SharedStorageAccountPrivateEndPointName = "peForxNFS",
                    },
                },
                DatabaseServer = new AzureNative.Workloads.Inputs.DatabaseConfigurationArgs
                {
                    DatabaseType = "HANA",
                    InstanceCount = 1,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_M32ts",
                    },
                },
                DeploymentType = "ThreeTier",
            },
            OsSapConfiguration = new AzureNative.Workloads.Inputs.OsSapConfigurationArgs
            {
                SapFqdn = "xyz.test.com",
            },
        },
        Environment = "Prod",
        Location = "westcentralus",
        ResourceGroupName = "test-rg",
        SapProduct = "S4HANA",
        SapVirtualInstanceName = "X00",
        Tags = null,
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewSAPVirtualInstance(ctx, "sapVirtualInstance", &workloads.SAPVirtualInstanceArgs{
			Configuration: workloads.DeploymentWithOSConfiguration{
				AppLocation:       "eastus",
				ConfigurationType: "DeploymentWithOSConfig",
				InfrastructureConfiguration: workloads.ThreeTierConfiguration{
					AppResourceGroup: "X00-RG",
					ApplicationServer: workloads.ApplicationServerConfiguration{
						InstanceCount: 6,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "xyz",
										PublicKey:  "abc",
									},
								},
							},
							VmSize: "Standard_E32ds_v4",
						},
					},
					CentralServer: workloads.CentralServerConfiguration{
						InstanceCount: 1,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "xyz",
										PublicKey:  "abc",
									},
								},
							},
							VmSize: "Standard_E16ds_v4",
						},
					},
					CustomResourceNames: workloads.ThreeTierFullResourceNames{
						ApplicationServer: workloads.ApplicationServerFullResourceNames{
							AvailabilitySetName: "appAvSet",
							VirtualMachines: []workloads.VirtualMachineResourceNames{
								{
									DataDiskNames: {
										"default": []string{
											"app0disk0",
										},
									},
									HostName: "apphostName0",
									NetworkInterfaces: []workloads.NetworkInterfaceResourceNames{
										{
											NetworkInterfaceName: "appnic0",
										},
									},
									OsDiskName: "app0osdisk",
									VmName:     "appvm0",
								},
								{
									DataDiskNames: {
										"default": []string{
											"app1disk0",
										},
									},
									HostName: "apphostName1",
									NetworkInterfaces: []workloads.NetworkInterfaceResourceNames{
										{
											NetworkInterfaceName: "appnic1",
										},
									},
									OsDiskName: "app1osdisk",
									VmName:     "appvm1",
								},
							},
						},
						CentralServer: workloads.CentralServerFullResourceNames{
							VirtualMachines: []workloads.VirtualMachineResourceNames{
								{
									DataDiskNames: {
										"default": []string{
											"ascsdisk0",
										},
									},
									HostName: "ascshostName",
									NetworkInterfaces: []workloads.NetworkInterfaceResourceNames{
										{
											NetworkInterfaceName: "ascsnic",
										},
									},
									OsDiskName: "ascsosdisk",
									VmName:     "ascsvm",
								},
							},
						},
						DatabaseServer: workloads.DatabaseServerFullResourceNames{
							VirtualMachines: []workloads.VirtualMachineResourceNames{
								{
									DataDiskNames: {
										"hanaData": []string{
											"hanadata0",
											"hanadata1",
										},
										"hanaLog": []string{
											"hanalog0",
											"hanalog1",
											"hanalog2",
										},
										"hanaShared": []string{
											"hanashared0",
											"hanashared1",
										},
										"usrSap": []string{
											"usrsap0",
										},
									},
									HostName: "dbhostName",
									NetworkInterfaces: []workloads.NetworkInterfaceResourceNames{
										{
											NetworkInterfaceName: "dbnic",
										},
									},
									OsDiskName: "dbosdisk",
									VmName:     "dbvm",
								},
							},
						},
						NamingPatternType: "FullResourceName",
						SharedStorage: workloads.SharedStorageResourceNames{
							SharedStorageAccountName:                "storageacc",
							SharedStorageAccountPrivateEndPointName: "peForxNFS",
						},
					},
					DatabaseServer: workloads.DatabaseConfiguration{
						DatabaseType:  "HANA",
						InstanceCount: 1,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "xyz",
										PublicKey:  "abc",
									},
								},
							},
							VmSize: "Standard_M32ts",
						},
					},
					DeploymentType: "ThreeTier",
				},
				OsSapConfiguration: workloads.OsSapConfiguration{
					SapFqdn: "xyz.test.com",
				},
			},
			Environment:            pulumi.String("Prod"),
			Location:               pulumi.String("westcentralus"),
			ResourceGroupName:      pulumi.String("test-rg"),
			SapProduct:             pulumi.String("S4HANA"),
			SapVirtualInstanceName: pulumi.String("X00"),
			Tags:                   nil,
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
import com.pulumi.azurenative.workloads.SAPVirtualInstance;
import com.pulumi.azurenative.workloads.SAPVirtualInstanceArgs;
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
        var sapVirtualInstance = new SAPVirtualInstance("sapVirtualInstance", SAPVirtualInstanceArgs.builder()        
            .configuration(Map.ofEntries(
                Map.entry("appLocation", "eastus"),
                Map.entry("configurationType", "DeploymentWithOSConfig"),
                Map.entry("infrastructureConfiguration", Map.ofEntries(
                    Map.entry("appResourceGroup", "X00-RG"),
                    Map.entry("applicationServer", Map.ofEntries(
                        Map.entry("instanceCount", 6),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E32ds_v4")
                        ))
                    )),
                    Map.entry("centralServer", Map.ofEntries(
                        Map.entry("instanceCount", 1),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E16ds_v4")
                        ))
                    )),
                    Map.entry("customResourceNames", Map.ofEntries(
                        Map.entry("applicationServer", Map.ofEntries(
                            Map.entry("availabilitySetName", "appAvSet"),
                            Map.entry("virtualMachines",                             
                                Map.ofEntries(
                                    Map.entry("dataDiskNames", DeploymentConfigurationArgs.builder()
                                        .default_("app0disk0")
                                        .build()),
                                    Map.entry("hostName", "apphostName0"),
                                    Map.entry("networkInterfaces", Map.of("networkInterfaceName", "appnic0")),
                                    Map.entry("osDiskName", "app0osdisk"),
                                    Map.entry("vmName", "appvm0")
                                ),
                                Map.ofEntries(
                                    Map.entry("dataDiskNames", DeploymentConfigurationArgs.builder()
                                        .default_("app1disk0")
                                        .build()),
                                    Map.entry("hostName", "apphostName1"),
                                    Map.entry("networkInterfaces", Map.of("networkInterfaceName", "appnic1")),
                                    Map.entry("osDiskName", "app1osdisk"),
                                    Map.entry("vmName", "appvm1")
                                ))
                        )),
                        Map.entry("centralServer", Map.of("virtualMachines", Map.ofEntries(
                            Map.entry("dataDiskNames", DeploymentConfigurationArgs.builder()
                                .default_("ascsdisk0")
                                .build()),
                            Map.entry("hostName", "ascshostName"),
                            Map.entry("networkInterfaces", Map.of("networkInterfaceName", "ascsnic")),
                            Map.entry("osDiskName", "ascsosdisk"),
                            Map.entry("vmName", "ascsvm")
                        ))),
                        Map.entry("databaseServer", Map.of("virtualMachines", Map.ofEntries(
                            Map.entry("dataDiskNames", DeploymentConfigurationArgs.builder()
                                .hanaData(                                
                                    "hanadata0",
                                    "hanadata1")
                                .hanaLog(                                
                                    "hanalog0",
                                    "hanalog1",
                                    "hanalog2")
                                .hanaShared(                                
                                    "hanashared0",
                                    "hanashared1")
                                .usrSap("usrsap0")
                                .build()),
                            Map.entry("hostName", "dbhostName"),
                            Map.entry("networkInterfaces", Map.of("networkInterfaceName", "dbnic")),
                            Map.entry("osDiskName", "dbosdisk"),
                            Map.entry("vmName", "dbvm")
                        ))),
                        Map.entry("namingPatternType", "FullResourceName"),
                        Map.entry("sharedStorage", Map.ofEntries(
                            Map.entry("sharedStorageAccountName", "storageacc"),
                            Map.entry("sharedStorageAccountPrivateEndPointName", "peForxNFS")
                        ))
                    )),
                    Map.entry("databaseServer", Map.ofEntries(
                        Map.entry("databaseType", "HANA"),
                        Map.entry("instanceCount", 1),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_M32ts")
                        ))
                    )),
                    Map.entry("deploymentType", "ThreeTier")
                )),
                Map.entry("osSapConfiguration", Map.of("sapFqdn", "xyz.test.com"))
            ))
            .environment("Prod")
            .location("westcentralus")
            .resourceGroupName("test-rg")
            .sapProduct("S4HANA")
            .sapVirtualInstanceName("X00")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sapVirtualInstance = new azure_native.workloads.SAPVirtualInstance("sapVirtualInstance", {
    configuration: {
        appLocation: "eastus",
        configurationType: "DeploymentWithOSConfig",
        infrastructureConfiguration: {
            appResourceGroup: "X00-RG",
            applicationServer: {
                instanceCount: 6,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_E32ds_v4",
                },
            },
            centralServer: {
                instanceCount: 1,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_E16ds_v4",
                },
            },
            customResourceNames: {
                applicationServer: {
                    availabilitySetName: "appAvSet",
                    virtualMachines: [
                        {
                            dataDiskNames: {
                                "default": ["app0disk0"],
                            },
                            hostName: "apphostName0",
                            networkInterfaces: [{
                                networkInterfaceName: "appnic0",
                            }],
                            osDiskName: "app0osdisk",
                            vmName: "appvm0",
                        },
                        {
                            dataDiskNames: {
                                "default": ["app1disk0"],
                            },
                            hostName: "apphostName1",
                            networkInterfaces: [{
                                networkInterfaceName: "appnic1",
                            }],
                            osDiskName: "app1osdisk",
                            vmName: "appvm1",
                        },
                    ],
                },
                centralServer: {
                    virtualMachines: [{
                        dataDiskNames: {
                            "default": ["ascsdisk0"],
                        },
                        hostName: "ascshostName",
                        networkInterfaces: [{
                            networkInterfaceName: "ascsnic",
                        }],
                        osDiskName: "ascsosdisk",
                        vmName: "ascsvm",
                    }],
                },
                databaseServer: {
                    virtualMachines: [{
                        dataDiskNames: {
                            hanaData: [
                                "hanadata0",
                                "hanadata1",
                            ],
                            hanaLog: [
                                "hanalog0",
                                "hanalog1",
                                "hanalog2",
                            ],
                            hanaShared: [
                                "hanashared0",
                                "hanashared1",
                            ],
                            usrSap: ["usrsap0"],
                        },
                        hostName: "dbhostName",
                        networkInterfaces: [{
                            networkInterfaceName: "dbnic",
                        }],
                        osDiskName: "dbosdisk",
                        vmName: "dbvm",
                    }],
                },
                namingPatternType: "FullResourceName",
                sharedStorage: {
                    sharedStorageAccountName: "storageacc",
                    sharedStorageAccountPrivateEndPointName: "peForxNFS",
                },
            },
            databaseServer: {
                databaseType: "HANA",
                instanceCount: 1,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_M32ts",
                },
            },
            deploymentType: "ThreeTier",
        },
        osSapConfiguration: {
            sapFqdn: "xyz.test.com",
        },
    },
    environment: "Prod",
    location: "westcentralus",
    resourceGroupName: "test-rg",
    sapProduct: "S4HANA",
    sapVirtualInstanceName: "X00",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sap_virtual_instance = azure_native.workloads.SAPVirtualInstance("sapVirtualInstance",
    configuration=azure_native.workloads.DeploymentWithOSConfigurationArgs(
        app_location="eastus",
        configuration_type="DeploymentWithOSConfig",
        infrastructure_configuration=azure_native.workloads.ThreeTierConfigurationArgs(
            app_resource_group="X00-RG",
            application_server=azure_native.workloads.ApplicationServerConfigurationArgs(
                instance_count=6,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_E32ds_v4",
                ),
            ),
            central_server=azure_native.workloads.CentralServerConfigurationArgs(
                instance_count=1,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_E16ds_v4",
                ),
            ),
            custom_resource_names=azure_native.workloads.ThreeTierFullResourceNamesArgs(
                application_server=azure_native.workloads.ApplicationServerFullResourceNamesArgs(
                    availability_set_name="appAvSet",
                    virtual_machines=[
                        azure_native.workloads.VirtualMachineResourceNamesArgs(
                            data_disk_names={
                                "default": ["app0disk0"],
                            },
                            host_name="apphostName0",
                            network_interfaces=[azure_native.workloads.NetworkInterfaceResourceNamesArgs(
                                network_interface_name="appnic0",
                            )],
                            os_disk_name="app0osdisk",
                            vm_name="appvm0",
                        ),
                        azure_native.workloads.VirtualMachineResourceNamesArgs(
                            data_disk_names={
                                "default": ["app1disk0"],
                            },
                            host_name="apphostName1",
                            network_interfaces=[azure_native.workloads.NetworkInterfaceResourceNamesArgs(
                                network_interface_name="appnic1",
                            )],
                            os_disk_name="app1osdisk",
                            vm_name="appvm1",
                        ),
                    ],
                ),
                central_server=azure_native.workloads.CentralServerFullResourceNamesArgs(
                    virtual_machines=[azure_native.workloads.VirtualMachineResourceNamesArgs(
                        data_disk_names={
                            "default": ["ascsdisk0"],
                        },
                        host_name="ascshostName",
                        network_interfaces=[azure_native.workloads.NetworkInterfaceResourceNamesArgs(
                            network_interface_name="ascsnic",
                        )],
                        os_disk_name="ascsosdisk",
                        vm_name="ascsvm",
                    )],
                ),
                database_server=azure_native.workloads.DatabaseServerFullResourceNamesArgs(
                    virtual_machines=[azure_native.workloads.VirtualMachineResourceNamesArgs(
                        data_disk_names={
                            "hanaData": [
                                "hanadata0",
                                "hanadata1",
                            ],
                            "hanaLog": [
                                "hanalog0",
                                "hanalog1",
                                "hanalog2",
                            ],
                            "hanaShared": [
                                "hanashared0",
                                "hanashared1",
                            ],
                            "usrSap": ["usrsap0"],
                        },
                        host_name="dbhostName",
                        network_interfaces=[azure_native.workloads.NetworkInterfaceResourceNamesArgs(
                            network_interface_name="dbnic",
                        )],
                        os_disk_name="dbosdisk",
                        vm_name="dbvm",
                    )],
                ),
                naming_pattern_type="FullResourceName",
                shared_storage=azure_native.workloads.SharedStorageResourceNamesArgs(
                    shared_storage_account_name="storageacc",
                    shared_storage_account_private_end_point_name="peForxNFS",
                ),
            ),
            database_server=azure_native.workloads.DatabaseConfigurationArgs(
                database_type="HANA",
                instance_count=1,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_M32ts",
                ),
            ),
            deployment_type="ThreeTier",
        ),
        os_sap_configuration=azure_native.workloads.OsSapConfigurationArgs(
            sap_fqdn="xyz.test.com",
        ),
    ),
    environment="Prod",
    location="westcentralus",
    resource_group_name="test-rg",
    sap_product="S4HANA",
    sap_virtual_instance_name="X00",
    tags={})

```

```yaml
resources:
  sapVirtualInstance:
    type: azure-native:workloads:SAPVirtualInstance
    properties:
      configuration:
        appLocation: eastus
        configurationType: DeploymentWithOSConfig
        infrastructureConfiguration:
          appResourceGroup: X00-RG
          applicationServer:
            instanceCount: 6
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_E32ds_v4
          centralServer:
            instanceCount: 1
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_E16ds_v4
          customResourceNames:
            applicationServer:
              availabilitySetName: appAvSet
              virtualMachines:
                - dataDiskNames:
                    default:
                      - app0disk0
                  hostName: apphostName0
                  networkInterfaces:
                    - networkInterfaceName: appnic0
                  osDiskName: app0osdisk
                  vmName: appvm0
                - dataDiskNames:
                    default:
                      - app1disk0
                  hostName: apphostName1
                  networkInterfaces:
                    - networkInterfaceName: appnic1
                  osDiskName: app1osdisk
                  vmName: appvm1
            centralServer:
              virtualMachines:
                - dataDiskNames:
                    default:
                      - ascsdisk0
                  hostName: ascshostName
                  networkInterfaces:
                    - networkInterfaceName: ascsnic
                  osDiskName: ascsosdisk
                  vmName: ascsvm
            databaseServer:
              virtualMachines:
                - dataDiskNames:
                    hanaData:
                      - hanadata0
                      - hanadata1
                    hanaLog:
                      - hanalog0
                      - hanalog1
                      - hanalog2
                    hanaShared:
                      - hanashared0
                      - hanashared1
                    usrSap:
                      - usrsap0
                  hostName: dbhostName
                  networkInterfaces:
                    - networkInterfaceName: dbnic
                  osDiskName: dbosdisk
                  vmName: dbvm
            namingPatternType: FullResourceName
            sharedStorage:
              sharedStorageAccountName: storageacc
              sharedStorageAccountPrivateEndPointName: peForxNFS
          databaseServer:
            databaseType: HANA
            instanceCount: 1
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_M32ts
          deploymentType: ThreeTier
        osSapConfiguration:
          sapFqdn: xyz.test.com
      environment: Prod
      location: westcentralus
      resourceGroupName: test-rg
      sapProduct: S4HANA
      sapVirtualInstanceName: X00
      tags: {}

```

{{% /example %}}
{{% example %}}
### Create Infrastructure (with OS configuration) with custom resource names for HA System with Availability Set
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sapVirtualInstance = new AzureNative.Workloads.SAPVirtualInstance("sapVirtualInstance", new()
    {
        Configuration = new AzureNative.Workloads.Inputs.DeploymentWithOSConfigurationArgs
        {
            AppLocation = "eastus",
            ConfigurationType = "DeploymentWithOSConfig",
            InfrastructureConfiguration = new AzureNative.Workloads.Inputs.ThreeTierConfigurationArgs
            {
                AppResourceGroup = "X00-RG",
                ApplicationServer = new AzureNative.Workloads.Inputs.ApplicationServerConfigurationArgs
                {
                    InstanceCount = 6,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_E32ds_v4",
                    },
                },
                CentralServer = new AzureNative.Workloads.Inputs.CentralServerConfigurationArgs
                {
                    InstanceCount = 2,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_E16ds_v4",
                    },
                },
                CustomResourceNames = new AzureNative.Workloads.Inputs.ThreeTierFullResourceNamesArgs
                {
                    ApplicationServer = new AzureNative.Workloads.Inputs.ApplicationServerFullResourceNamesArgs
                    {
                        AvailabilitySetName = "appAvSet",
                        VirtualMachines = new[]
                        {
                            new AzureNative.Workloads.Inputs.VirtualMachineResourceNamesArgs
                            {
                                DataDiskNames = 
                                {
                                    { "default", new[]
                                    {
                                        "app0disk0",
                                    } },
                                },
                                HostName = "apphostName0",
                                NetworkInterfaces = new[]
                                {
                                    new AzureNative.Workloads.Inputs.NetworkInterfaceResourceNamesArgs
                                    {
                                        NetworkInterfaceName = "appnic0",
                                    },
                                },
                                OsDiskName = "app0osdisk",
                                VmName = "appvm0",
                            },
                            new AzureNative.Workloads.Inputs.VirtualMachineResourceNamesArgs
                            {
                                DataDiskNames = 
                                {
                                    { "default", new[]
                                    {
                                        "app1disk0",
                                    } },
                                },
                                HostName = "apphostName1",
                                NetworkInterfaces = new[]
                                {
                                    new AzureNative.Workloads.Inputs.NetworkInterfaceResourceNamesArgs
                                    {
                                        NetworkInterfaceName = "appnic1",
                                    },
                                },
                                OsDiskName = "app1osdisk",
                                VmName = "appvm1",
                            },
                        },
                    },
                    CentralServer = new AzureNative.Workloads.Inputs.CentralServerFullResourceNamesArgs
                    {
                        AvailabilitySetName = "csAvSet",
                        LoadBalancer = new AzureNative.Workloads.Inputs.LoadBalancerResourceNamesArgs
                        {
                            BackendPoolNames = new[]
                            {
                                "ascsBackendPool",
                            },
                            FrontendIpConfigurationNames = new[]
                            {
                                "ascsip0",
                                "ersip0",
                            },
                            HealthProbeNames = new[]
                            {
                                "ascsHealthProbe",
                                "ersHealthProbe",
                            },
                            LoadBalancerName = "ascslb",
                        },
                        VirtualMachines = new[]
                        {
                            new AzureNative.Workloads.Inputs.VirtualMachineResourceNamesArgs
                            {
                                HostName = "ascshostName",
                                NetworkInterfaces = new[]
                                {
                                    new AzureNative.Workloads.Inputs.NetworkInterfaceResourceNamesArgs
                                    {
                                        NetworkInterfaceName = "ascsnic",
                                    },
                                },
                                OsDiskName = "ascsosdisk",
                                VmName = "ascsvm",
                            },
                            new AzureNative.Workloads.Inputs.VirtualMachineResourceNamesArgs
                            {
                                HostName = "ershostName",
                                NetworkInterfaces = new[]
                                {
                                    new AzureNative.Workloads.Inputs.NetworkInterfaceResourceNamesArgs
                                    {
                                        NetworkInterfaceName = "ersnic",
                                    },
                                },
                                OsDiskName = "ersosdisk",
                                VmName = "ersvm",
                            },
                        },
                    },
                    DatabaseServer = new AzureNative.Workloads.Inputs.DatabaseServerFullResourceNamesArgs
                    {
                        AvailabilitySetName = "dbAvSet",
                        LoadBalancer = new AzureNative.Workloads.Inputs.LoadBalancerResourceNamesArgs
                        {
                            BackendPoolNames = new[]
                            {
                                "dbBackendPool",
                            },
                            FrontendIpConfigurationNames = new[]
                            {
                                "dbip",
                            },
                            HealthProbeNames = new[]
                            {
                                "dbHealthProbe",
                            },
                            LoadBalancerName = "dblb",
                        },
                        VirtualMachines = new[]
                        {
                            new AzureNative.Workloads.Inputs.VirtualMachineResourceNamesArgs
                            {
                                DataDiskNames = 
                                {
                                    { "hanaData", new[]
                                    {
                                        "hanadatapr0",
                                        "hanadatapr1",
                                    } },
                                    { "hanaLog", new[]
                                    {
                                        "hanalogpr0",
                                        "hanalogpr1",
                                        "hanalogpr2",
                                    } },
                                    { "hanaShared", new[]
                                    {
                                        "hanasharedpr0",
                                        "hanasharedpr1",
                                    } },
                                    { "usrSap", new[]
                                    {
                                        "usrsappr0",
                                    } },
                                },
                                HostName = "dbprhostName",
                                NetworkInterfaces = new[]
                                {
                                    new AzureNative.Workloads.Inputs.NetworkInterfaceResourceNamesArgs
                                    {
                                        NetworkInterfaceName = "dbprnic",
                                    },
                                },
                                OsDiskName = "dbprosdisk",
                                VmName = "dbvmpr",
                            },
                            new AzureNative.Workloads.Inputs.VirtualMachineResourceNamesArgs
                            {
                                DataDiskNames = 
                                {
                                    { "hanaData", new[]
                                    {
                                        "hanadatasr0",
                                        "hanadatasr1",
                                    } },
                                    { "hanaLog", new[]
                                    {
                                        "hanalogsr0",
                                        "hanalogsr1",
                                        "hanalogsr2",
                                    } },
                                    { "hanaShared", new[]
                                    {
                                        "hanasharedsr0",
                                        "hanasharedsr1",
                                    } },
                                    { "usrSap", new[]
                                    {
                                        "usrsapsr0",
                                    } },
                                },
                                HostName = "dbsrhostName",
                                NetworkInterfaces = new[]
                                {
                                    new AzureNative.Workloads.Inputs.NetworkInterfaceResourceNamesArgs
                                    {
                                        NetworkInterfaceName = "dbsrnic",
                                    },
                                },
                                OsDiskName = "dbsrosdisk",
                                VmName = "dbvmsr",
                            },
                        },
                    },
                    NamingPatternType = "FullResourceName",
                    SharedStorage = new AzureNative.Workloads.Inputs.SharedStorageResourceNamesArgs
                    {
                        SharedStorageAccountName = "storageacc",
                        SharedStorageAccountPrivateEndPointName = "peForxNFS",
                    },
                },
                DatabaseServer = new AzureNative.Workloads.Inputs.DatabaseConfigurationArgs
                {
                    DatabaseType = "HANA",
                    InstanceCount = 2,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_M32ts",
                    },
                },
                DeploymentType = "ThreeTier",
                HighAvailabilityConfig = new AzureNative.Workloads.Inputs.HighAvailabilityConfigurationArgs
                {
                    HighAvailabilityType = "AvailabilitySet",
                },
            },
            OsSapConfiguration = new AzureNative.Workloads.Inputs.OsSapConfigurationArgs
            {
                SapFqdn = "xyz.test.com",
            },
        },
        Environment = "Prod",
        Location = "westcentralus",
        ResourceGroupName = "test-rg",
        SapProduct = "S4HANA",
        SapVirtualInstanceName = "X00",
        Tags = null,
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewSAPVirtualInstance(ctx, "sapVirtualInstance", &workloads.SAPVirtualInstanceArgs{
			Configuration: workloads.DeploymentWithOSConfiguration{
				AppLocation:       "eastus",
				ConfigurationType: "DeploymentWithOSConfig",
				InfrastructureConfiguration: workloads.ThreeTierConfiguration{
					AppResourceGroup: "X00-RG",
					ApplicationServer: workloads.ApplicationServerConfiguration{
						InstanceCount: 6,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "xyz",
										PublicKey:  "abc",
									},
								},
							},
							VmSize: "Standard_E32ds_v4",
						},
					},
					CentralServer: workloads.CentralServerConfiguration{
						InstanceCount: 2,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "xyz",
										PublicKey:  "abc",
									},
								},
							},
							VmSize: "Standard_E16ds_v4",
						},
					},
					CustomResourceNames: workloads.ThreeTierFullResourceNames{
						ApplicationServer: workloads.ApplicationServerFullResourceNames{
							AvailabilitySetName: "appAvSet",
							VirtualMachines: []workloads.VirtualMachineResourceNames{
								{
									DataDiskNames: {
										"default": []string{
											"app0disk0",
										},
									},
									HostName: "apphostName0",
									NetworkInterfaces: []workloads.NetworkInterfaceResourceNames{
										{
											NetworkInterfaceName: "appnic0",
										},
									},
									OsDiskName: "app0osdisk",
									VmName:     "appvm0",
								},
								{
									DataDiskNames: {
										"default": []string{
											"app1disk0",
										},
									},
									HostName: "apphostName1",
									NetworkInterfaces: []workloads.NetworkInterfaceResourceNames{
										{
											NetworkInterfaceName: "appnic1",
										},
									},
									OsDiskName: "app1osdisk",
									VmName:     "appvm1",
								},
							},
						},
						CentralServer: workloads.CentralServerFullResourceNames{
							AvailabilitySetName: "csAvSet",
							LoadBalancer: workloads.LoadBalancerResourceNames{
								BackendPoolNames: []string{
									"ascsBackendPool",
								},
								FrontendIpConfigurationNames: []string{
									"ascsip0",
									"ersip0",
								},
								HealthProbeNames: []string{
									"ascsHealthProbe",
									"ersHealthProbe",
								},
								LoadBalancerName: "ascslb",
							},
							VirtualMachines: []workloads.VirtualMachineResourceNames{
								{
									HostName: "ascshostName",
									NetworkInterfaces: []workloads.NetworkInterfaceResourceNames{
										{
											NetworkInterfaceName: "ascsnic",
										},
									},
									OsDiskName: "ascsosdisk",
									VmName:     "ascsvm",
								},
								{
									HostName: "ershostName",
									NetworkInterfaces: []workloads.NetworkInterfaceResourceNames{
										{
											NetworkInterfaceName: "ersnic",
										},
									},
									OsDiskName: "ersosdisk",
									VmName:     "ersvm",
								},
							},
						},
						DatabaseServer: workloads.DatabaseServerFullResourceNames{
							AvailabilitySetName: "dbAvSet",
							LoadBalancer: workloads.LoadBalancerResourceNames{
								BackendPoolNames: []string{
									"dbBackendPool",
								},
								FrontendIpConfigurationNames: []string{
									"dbip",
								},
								HealthProbeNames: []string{
									"dbHealthProbe",
								},
								LoadBalancerName: "dblb",
							},
							VirtualMachines: []workloads.VirtualMachineResourceNames{
								{
									DataDiskNames: {
										"hanaData": []string{
											"hanadatapr0",
											"hanadatapr1",
										},
										"hanaLog": []string{
											"hanalogpr0",
											"hanalogpr1",
											"hanalogpr2",
										},
										"hanaShared": []string{
											"hanasharedpr0",
											"hanasharedpr1",
										},
										"usrSap": []string{
											"usrsappr0",
										},
									},
									HostName: "dbprhostName",
									NetworkInterfaces: []workloads.NetworkInterfaceResourceNames{
										{
											NetworkInterfaceName: "dbprnic",
										},
									},
									OsDiskName: "dbprosdisk",
									VmName:     "dbvmpr",
								},
								{
									DataDiskNames: {
										"hanaData": []string{
											"hanadatasr0",
											"hanadatasr1",
										},
										"hanaLog": []string{
											"hanalogsr0",
											"hanalogsr1",
											"hanalogsr2",
										},
										"hanaShared": []string{
											"hanasharedsr0",
											"hanasharedsr1",
										},
										"usrSap": []string{
											"usrsapsr0",
										},
									},
									HostName: "dbsrhostName",
									NetworkInterfaces: []workloads.NetworkInterfaceResourceNames{
										{
											NetworkInterfaceName: "dbsrnic",
										},
									},
									OsDiskName: "dbsrosdisk",
									VmName:     "dbvmsr",
								},
							},
						},
						NamingPatternType: "FullResourceName",
						SharedStorage: workloads.SharedStorageResourceNames{
							SharedStorageAccountName:                "storageacc",
							SharedStorageAccountPrivateEndPointName: "peForxNFS",
						},
					},
					DatabaseServer: workloads.DatabaseConfiguration{
						DatabaseType:  "HANA",
						InstanceCount: 2,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "xyz",
										PublicKey:  "abc",
									},
								},
							},
							VmSize: "Standard_M32ts",
						},
					},
					DeploymentType: "ThreeTier",
					HighAvailabilityConfig: workloads.HighAvailabilityConfiguration{
						HighAvailabilityType: "AvailabilitySet",
					},
				},
				OsSapConfiguration: workloads.OsSapConfiguration{
					SapFqdn: "xyz.test.com",
				},
			},
			Environment:            pulumi.String("Prod"),
			Location:               pulumi.String("westcentralus"),
			ResourceGroupName:      pulumi.String("test-rg"),
			SapProduct:             pulumi.String("S4HANA"),
			SapVirtualInstanceName: pulumi.String("X00"),
			Tags:                   nil,
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
import com.pulumi.azurenative.workloads.SAPVirtualInstance;
import com.pulumi.azurenative.workloads.SAPVirtualInstanceArgs;
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
        var sapVirtualInstance = new SAPVirtualInstance("sapVirtualInstance", SAPVirtualInstanceArgs.builder()        
            .configuration(Map.ofEntries(
                Map.entry("appLocation", "eastus"),
                Map.entry("configurationType", "DeploymentWithOSConfig"),
                Map.entry("infrastructureConfiguration", Map.ofEntries(
                    Map.entry("appResourceGroup", "X00-RG"),
                    Map.entry("applicationServer", Map.ofEntries(
                        Map.entry("instanceCount", 6),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E32ds_v4")
                        ))
                    )),
                    Map.entry("centralServer", Map.ofEntries(
                        Map.entry("instanceCount", 2),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E16ds_v4")
                        ))
                    )),
                    Map.entry("customResourceNames", Map.ofEntries(
                        Map.entry("applicationServer", Map.ofEntries(
                            Map.entry("availabilitySetName", "appAvSet"),
                            Map.entry("virtualMachines",                             
                                Map.ofEntries(
                                    Map.entry("dataDiskNames", DeploymentConfigurationArgs.builder()
                                        .default_("app0disk0")
                                        .build()),
                                    Map.entry("hostName", "apphostName0"),
                                    Map.entry("networkInterfaces", Map.of("networkInterfaceName", "appnic0")),
                                    Map.entry("osDiskName", "app0osdisk"),
                                    Map.entry("vmName", "appvm0")
                                ),
                                Map.ofEntries(
                                    Map.entry("dataDiskNames", DeploymentConfigurationArgs.builder()
                                        .default_("app1disk0")
                                        .build()),
                                    Map.entry("hostName", "apphostName1"),
                                    Map.entry("networkInterfaces", Map.of("networkInterfaceName", "appnic1")),
                                    Map.entry("osDiskName", "app1osdisk"),
                                    Map.entry("vmName", "appvm1")
                                ))
                        )),
                        Map.entry("centralServer", Map.ofEntries(
                            Map.entry("availabilitySetName", "csAvSet"),
                            Map.entry("loadBalancer", Map.ofEntries(
                                Map.entry("backendPoolNames", "ascsBackendPool"),
                                Map.entry("frontendIpConfigurationNames",                                 
                                    "ascsip0",
                                    "ersip0"),
                                Map.entry("healthProbeNames",                                 
                                    "ascsHealthProbe",
                                    "ersHealthProbe"),
                                Map.entry("loadBalancerName", "ascslb")
                            )),
                            Map.entry("virtualMachines",                             
                                Map.ofEntries(
                                    Map.entry("hostName", "ascshostName"),
                                    Map.entry("networkInterfaces", Map.of("networkInterfaceName", "ascsnic")),
                                    Map.entry("osDiskName", "ascsosdisk"),
                                    Map.entry("vmName", "ascsvm")
                                ),
                                Map.ofEntries(
                                    Map.entry("hostName", "ershostName"),
                                    Map.entry("networkInterfaces", Map.of("networkInterfaceName", "ersnic")),
                                    Map.entry("osDiskName", "ersosdisk"),
                                    Map.entry("vmName", "ersvm")
                                ))
                        )),
                        Map.entry("databaseServer", Map.ofEntries(
                            Map.entry("availabilitySetName", "dbAvSet"),
                            Map.entry("loadBalancer", Map.ofEntries(
                                Map.entry("backendPoolNames", "dbBackendPool"),
                                Map.entry("frontendIpConfigurationNames", "dbip"),
                                Map.entry("healthProbeNames", "dbHealthProbe"),
                                Map.entry("loadBalancerName", "dblb")
                            )),
                            Map.entry("virtualMachines",                             
                                Map.ofEntries(
                                    Map.entry("dataDiskNames", DeploymentConfigurationArgs.builder()
                                        .hanaData(                                        
                                            "hanadatapr0",
                                            "hanadatapr1")
                                        .hanaLog(                                        
                                            "hanalogpr0",
                                            "hanalogpr1",
                                            "hanalogpr2")
                                        .hanaShared(                                        
                                            "hanasharedpr0",
                                            "hanasharedpr1")
                                        .usrSap("usrsappr0")
                                        .build()),
                                    Map.entry("hostName", "dbprhostName"),
                                    Map.entry("networkInterfaces", Map.of("networkInterfaceName", "dbprnic")),
                                    Map.entry("osDiskName", "dbprosdisk"),
                                    Map.entry("vmName", "dbvmpr")
                                ),
                                Map.ofEntries(
                                    Map.entry("dataDiskNames", DeploymentConfigurationArgs.builder()
                                        .hanaData(                                        
                                            "hanadatasr0",
                                            "hanadatasr1")
                                        .hanaLog(                                        
                                            "hanalogsr0",
                                            "hanalogsr1",
                                            "hanalogsr2")
                                        .hanaShared(                                        
                                            "hanasharedsr0",
                                            "hanasharedsr1")
                                        .usrSap("usrsapsr0")
                                        .build()),
                                    Map.entry("hostName", "dbsrhostName"),
                                    Map.entry("networkInterfaces", Map.of("networkInterfaceName", "dbsrnic")),
                                    Map.entry("osDiskName", "dbsrosdisk"),
                                    Map.entry("vmName", "dbvmsr")
                                ))
                        )),
                        Map.entry("namingPatternType", "FullResourceName"),
                        Map.entry("sharedStorage", Map.ofEntries(
                            Map.entry("sharedStorageAccountName", "storageacc"),
                            Map.entry("sharedStorageAccountPrivateEndPointName", "peForxNFS")
                        ))
                    )),
                    Map.entry("databaseServer", Map.ofEntries(
                        Map.entry("databaseType", "HANA"),
                        Map.entry("instanceCount", 2),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_M32ts")
                        ))
                    )),
                    Map.entry("deploymentType", "ThreeTier"),
                    Map.entry("highAvailabilityConfig", Map.of("highAvailabilityType", "AvailabilitySet"))
                )),
                Map.entry("osSapConfiguration", Map.of("sapFqdn", "xyz.test.com"))
            ))
            .environment("Prod")
            .location("westcentralus")
            .resourceGroupName("test-rg")
            .sapProduct("S4HANA")
            .sapVirtualInstanceName("X00")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sapVirtualInstance = new azure_native.workloads.SAPVirtualInstance("sapVirtualInstance", {
    configuration: {
        appLocation: "eastus",
        configurationType: "DeploymentWithOSConfig",
        infrastructureConfiguration: {
            appResourceGroup: "X00-RG",
            applicationServer: {
                instanceCount: 6,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_E32ds_v4",
                },
            },
            centralServer: {
                instanceCount: 2,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_E16ds_v4",
                },
            },
            customResourceNames: {
                applicationServer: {
                    availabilitySetName: "appAvSet",
                    virtualMachines: [
                        {
                            dataDiskNames: {
                                "default": ["app0disk0"],
                            },
                            hostName: "apphostName0",
                            networkInterfaces: [{
                                networkInterfaceName: "appnic0",
                            }],
                            osDiskName: "app0osdisk",
                            vmName: "appvm0",
                        },
                        {
                            dataDiskNames: {
                                "default": ["app1disk0"],
                            },
                            hostName: "apphostName1",
                            networkInterfaces: [{
                                networkInterfaceName: "appnic1",
                            }],
                            osDiskName: "app1osdisk",
                            vmName: "appvm1",
                        },
                    ],
                },
                centralServer: {
                    availabilitySetName: "csAvSet",
                    loadBalancer: {
                        backendPoolNames: ["ascsBackendPool"],
                        frontendIpConfigurationNames: [
                            "ascsip0",
                            "ersip0",
                        ],
                        healthProbeNames: [
                            "ascsHealthProbe",
                            "ersHealthProbe",
                        ],
                        loadBalancerName: "ascslb",
                    },
                    virtualMachines: [
                        {
                            hostName: "ascshostName",
                            networkInterfaces: [{
                                networkInterfaceName: "ascsnic",
                            }],
                            osDiskName: "ascsosdisk",
                            vmName: "ascsvm",
                        },
                        {
                            hostName: "ershostName",
                            networkInterfaces: [{
                                networkInterfaceName: "ersnic",
                            }],
                            osDiskName: "ersosdisk",
                            vmName: "ersvm",
                        },
                    ],
                },
                databaseServer: {
                    availabilitySetName: "dbAvSet",
                    loadBalancer: {
                        backendPoolNames: ["dbBackendPool"],
                        frontendIpConfigurationNames: ["dbip"],
                        healthProbeNames: ["dbHealthProbe"],
                        loadBalancerName: "dblb",
                    },
                    virtualMachines: [
                        {
                            dataDiskNames: {
                                hanaData: [
                                    "hanadatapr0",
                                    "hanadatapr1",
                                ],
                                hanaLog: [
                                    "hanalogpr0",
                                    "hanalogpr1",
                                    "hanalogpr2",
                                ],
                                hanaShared: [
                                    "hanasharedpr0",
                                    "hanasharedpr1",
                                ],
                                usrSap: ["usrsappr0"],
                            },
                            hostName: "dbprhostName",
                            networkInterfaces: [{
                                networkInterfaceName: "dbprnic",
                            }],
                            osDiskName: "dbprosdisk",
                            vmName: "dbvmpr",
                        },
                        {
                            dataDiskNames: {
                                hanaData: [
                                    "hanadatasr0",
                                    "hanadatasr1",
                                ],
                                hanaLog: [
                                    "hanalogsr0",
                                    "hanalogsr1",
                                    "hanalogsr2",
                                ],
                                hanaShared: [
                                    "hanasharedsr0",
                                    "hanasharedsr1",
                                ],
                                usrSap: ["usrsapsr0"],
                            },
                            hostName: "dbsrhostName",
                            networkInterfaces: [{
                                networkInterfaceName: "dbsrnic",
                            }],
                            osDiskName: "dbsrosdisk",
                            vmName: "dbvmsr",
                        },
                    ],
                },
                namingPatternType: "FullResourceName",
                sharedStorage: {
                    sharedStorageAccountName: "storageacc",
                    sharedStorageAccountPrivateEndPointName: "peForxNFS",
                },
            },
            databaseServer: {
                databaseType: "HANA",
                instanceCount: 2,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_M32ts",
                },
            },
            deploymentType: "ThreeTier",
            highAvailabilityConfig: {
                highAvailabilityType: "AvailabilitySet",
            },
        },
        osSapConfiguration: {
            sapFqdn: "xyz.test.com",
        },
    },
    environment: "Prod",
    location: "westcentralus",
    resourceGroupName: "test-rg",
    sapProduct: "S4HANA",
    sapVirtualInstanceName: "X00",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sap_virtual_instance = azure_native.workloads.SAPVirtualInstance("sapVirtualInstance",
    configuration=azure_native.workloads.DeploymentWithOSConfigurationArgs(
        app_location="eastus",
        configuration_type="DeploymentWithOSConfig",
        infrastructure_configuration=azure_native.workloads.ThreeTierConfigurationArgs(
            app_resource_group="X00-RG",
            application_server=azure_native.workloads.ApplicationServerConfigurationArgs(
                instance_count=6,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_E32ds_v4",
                ),
            ),
            central_server=azure_native.workloads.CentralServerConfigurationArgs(
                instance_count=2,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_E16ds_v4",
                ),
            ),
            custom_resource_names=azure_native.workloads.ThreeTierFullResourceNamesArgs(
                application_server=azure_native.workloads.ApplicationServerFullResourceNamesArgs(
                    availability_set_name="appAvSet",
                    virtual_machines=[
                        azure_native.workloads.VirtualMachineResourceNamesArgs(
                            data_disk_names={
                                "default": ["app0disk0"],
                            },
                            host_name="apphostName0",
                            network_interfaces=[azure_native.workloads.NetworkInterfaceResourceNamesArgs(
                                network_interface_name="appnic0",
                            )],
                            os_disk_name="app0osdisk",
                            vm_name="appvm0",
                        ),
                        azure_native.workloads.VirtualMachineResourceNamesArgs(
                            data_disk_names={
                                "default": ["app1disk0"],
                            },
                            host_name="apphostName1",
                            network_interfaces=[azure_native.workloads.NetworkInterfaceResourceNamesArgs(
                                network_interface_name="appnic1",
                            )],
                            os_disk_name="app1osdisk",
                            vm_name="appvm1",
                        ),
                    ],
                ),
                central_server=azure_native.workloads.CentralServerFullResourceNamesArgs(
                    availability_set_name="csAvSet",
                    load_balancer=azure_native.workloads.LoadBalancerResourceNamesArgs(
                        backend_pool_names=["ascsBackendPool"],
                        frontend_ip_configuration_names=[
                            "ascsip0",
                            "ersip0",
                        ],
                        health_probe_names=[
                            "ascsHealthProbe",
                            "ersHealthProbe",
                        ],
                        load_balancer_name="ascslb",
                    ),
                    virtual_machines=[
                        azure_native.workloads.VirtualMachineResourceNamesArgs(
                            host_name="ascshostName",
                            network_interfaces=[azure_native.workloads.NetworkInterfaceResourceNamesArgs(
                                network_interface_name="ascsnic",
                            )],
                            os_disk_name="ascsosdisk",
                            vm_name="ascsvm",
                        ),
                        azure_native.workloads.VirtualMachineResourceNamesArgs(
                            host_name="ershostName",
                            network_interfaces=[azure_native.workloads.NetworkInterfaceResourceNamesArgs(
                                network_interface_name="ersnic",
                            )],
                            os_disk_name="ersosdisk",
                            vm_name="ersvm",
                        ),
                    ],
                ),
                database_server=azure_native.workloads.DatabaseServerFullResourceNamesArgs(
                    availability_set_name="dbAvSet",
                    load_balancer=azure_native.workloads.LoadBalancerResourceNamesArgs(
                        backend_pool_names=["dbBackendPool"],
                        frontend_ip_configuration_names=["dbip"],
                        health_probe_names=["dbHealthProbe"],
                        load_balancer_name="dblb",
                    ),
                    virtual_machines=[
                        azure_native.workloads.VirtualMachineResourceNamesArgs(
                            data_disk_names={
                                "hanaData": [
                                    "hanadatapr0",
                                    "hanadatapr1",
                                ],
                                "hanaLog": [
                                    "hanalogpr0",
                                    "hanalogpr1",
                                    "hanalogpr2",
                                ],
                                "hanaShared": [
                                    "hanasharedpr0",
                                    "hanasharedpr1",
                                ],
                                "usrSap": ["usrsappr0"],
                            },
                            host_name="dbprhostName",
                            network_interfaces=[azure_native.workloads.NetworkInterfaceResourceNamesArgs(
                                network_interface_name="dbprnic",
                            )],
                            os_disk_name="dbprosdisk",
                            vm_name="dbvmpr",
                        ),
                        azure_native.workloads.VirtualMachineResourceNamesArgs(
                            data_disk_names={
                                "hanaData": [
                                    "hanadatasr0",
                                    "hanadatasr1",
                                ],
                                "hanaLog": [
                                    "hanalogsr0",
                                    "hanalogsr1",
                                    "hanalogsr2",
                                ],
                                "hanaShared": [
                                    "hanasharedsr0",
                                    "hanasharedsr1",
                                ],
                                "usrSap": ["usrsapsr0"],
                            },
                            host_name="dbsrhostName",
                            network_interfaces=[azure_native.workloads.NetworkInterfaceResourceNamesArgs(
                                network_interface_name="dbsrnic",
                            )],
                            os_disk_name="dbsrosdisk",
                            vm_name="dbvmsr",
                        ),
                    ],
                ),
                naming_pattern_type="FullResourceName",
                shared_storage=azure_native.workloads.SharedStorageResourceNamesArgs(
                    shared_storage_account_name="storageacc",
                    shared_storage_account_private_end_point_name="peForxNFS",
                ),
            ),
            database_server=azure_native.workloads.DatabaseConfigurationArgs(
                database_type="HANA",
                instance_count=2,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_M32ts",
                ),
            ),
            deployment_type="ThreeTier",
            high_availability_config=azure_native.workloads.HighAvailabilityConfigurationArgs(
                high_availability_type="AvailabilitySet",
            ),
        ),
        os_sap_configuration=azure_native.workloads.OsSapConfigurationArgs(
            sap_fqdn="xyz.test.com",
        ),
    ),
    environment="Prod",
    location="westcentralus",
    resource_group_name="test-rg",
    sap_product="S4HANA",
    sap_virtual_instance_name="X00",
    tags={})

```

```yaml
resources:
  sapVirtualInstance:
    type: azure-native:workloads:SAPVirtualInstance
    properties:
      configuration:
        appLocation: eastus
        configurationType: DeploymentWithOSConfig
        infrastructureConfiguration:
          appResourceGroup: X00-RG
          applicationServer:
            instanceCount: 6
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_E32ds_v4
          centralServer:
            instanceCount: 2
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_E16ds_v4
          customResourceNames:
            applicationServer:
              availabilitySetName: appAvSet
              virtualMachines:
                - dataDiskNames:
                    default:
                      - app0disk0
                  hostName: apphostName0
                  networkInterfaces:
                    - networkInterfaceName: appnic0
                  osDiskName: app0osdisk
                  vmName: appvm0
                - dataDiskNames:
                    default:
                      - app1disk0
                  hostName: apphostName1
                  networkInterfaces:
                    - networkInterfaceName: appnic1
                  osDiskName: app1osdisk
                  vmName: appvm1
            centralServer:
              availabilitySetName: csAvSet
              loadBalancer:
                backendPoolNames:
                  - ascsBackendPool
                frontendIpConfigurationNames:
                  - ascsip0
                  - ersip0
                healthProbeNames:
                  - ascsHealthProbe
                  - ersHealthProbe
                loadBalancerName: ascslb
              virtualMachines:
                - hostName: ascshostName
                  networkInterfaces:
                    - networkInterfaceName: ascsnic
                  osDiskName: ascsosdisk
                  vmName: ascsvm
                - hostName: ershostName
                  networkInterfaces:
                    - networkInterfaceName: ersnic
                  osDiskName: ersosdisk
                  vmName: ersvm
            databaseServer:
              availabilitySetName: dbAvSet
              loadBalancer:
                backendPoolNames:
                  - dbBackendPool
                frontendIpConfigurationNames:
                  - dbip
                healthProbeNames:
                  - dbHealthProbe
                loadBalancerName: dblb
              virtualMachines:
                - dataDiskNames:
                    hanaData:
                      - hanadatapr0
                      - hanadatapr1
                    hanaLog:
                      - hanalogpr0
                      - hanalogpr1
                      - hanalogpr2
                    hanaShared:
                      - hanasharedpr0
                      - hanasharedpr1
                    usrSap:
                      - usrsappr0
                  hostName: dbprhostName
                  networkInterfaces:
                    - networkInterfaceName: dbprnic
                  osDiskName: dbprosdisk
                  vmName: dbvmpr
                - dataDiskNames:
                    hanaData:
                      - hanadatasr0
                      - hanadatasr1
                    hanaLog:
                      - hanalogsr0
                      - hanalogsr1
                      - hanalogsr2
                    hanaShared:
                      - hanasharedsr0
                      - hanasharedsr1
                    usrSap:
                      - usrsapsr0
                  hostName: dbsrhostName
                  networkInterfaces:
                    - networkInterfaceName: dbsrnic
                  osDiskName: dbsrosdisk
                  vmName: dbvmsr
            namingPatternType: FullResourceName
            sharedStorage:
              sharedStorageAccountName: storageacc
              sharedStorageAccountPrivateEndPointName: peForxNFS
          databaseServer:
            databaseType: HANA
            instanceCount: 2
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_M32ts
          deploymentType: ThreeTier
          highAvailabilityConfig:
            highAvailabilityType: AvailabilitySet
        osSapConfiguration:
          sapFqdn: xyz.test.com
      environment: Prod
      location: westcentralus
      resourceGroupName: test-rg
      sapProduct: S4HANA
      sapVirtualInstanceName: X00
      tags: {}

```

{{% /example %}}
{{% example %}}
### Create Infrastructure (with OS configuration) with custom resource names for HA system with Availability Zone
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sapVirtualInstance = new AzureNative.Workloads.SAPVirtualInstance("sapVirtualInstance", new()
    {
        Configuration = new AzureNative.Workloads.Inputs.DeploymentWithOSConfigurationArgs
        {
            AppLocation = "eastus",
            ConfigurationType = "DeploymentWithOSConfig",
            InfrastructureConfiguration = new AzureNative.Workloads.Inputs.ThreeTierConfigurationArgs
            {
                AppResourceGroup = "X00-RG",
                ApplicationServer = new AzureNative.Workloads.Inputs.ApplicationServerConfigurationArgs
                {
                    InstanceCount = 6,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_E32ds_v4",
                    },
                },
                CentralServer = new AzureNative.Workloads.Inputs.CentralServerConfigurationArgs
                {
                    InstanceCount = 2,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_E16ds_v4",
                    },
                },
                CustomResourceNames = new AzureNative.Workloads.Inputs.ThreeTierFullResourceNamesArgs
                {
                    ApplicationServer = new AzureNative.Workloads.Inputs.ApplicationServerFullResourceNamesArgs
                    {
                        VirtualMachines = new[]
                        {
                            new AzureNative.Workloads.Inputs.VirtualMachineResourceNamesArgs
                            {
                                DataDiskNames = 
                                {
                                    { "default", new[]
                                    {
                                        "app0disk0",
                                    } },
                                },
                                HostName = "apphostName0",
                                NetworkInterfaces = new[]
                                {
                                    new AzureNative.Workloads.Inputs.NetworkInterfaceResourceNamesArgs
                                    {
                                        NetworkInterfaceName = "appnic0",
                                    },
                                },
                                OsDiskName = "app0osdisk",
                                VmName = "appvm0",
                            },
                            new AzureNative.Workloads.Inputs.VirtualMachineResourceNamesArgs
                            {
                                DataDiskNames = 
                                {
                                    { "default", new[]
                                    {
                                        "app1disk0",
                                    } },
                                },
                                HostName = "apphostName1",
                                NetworkInterfaces = new[]
                                {
                                    new AzureNative.Workloads.Inputs.NetworkInterfaceResourceNamesArgs
                                    {
                                        NetworkInterfaceName = "appnic1",
                                    },
                                },
                                OsDiskName = "app1osdisk",
                                VmName = "appvm1",
                            },
                        },
                    },
                    CentralServer = new AzureNative.Workloads.Inputs.CentralServerFullResourceNamesArgs
                    {
                        LoadBalancer = new AzureNative.Workloads.Inputs.LoadBalancerResourceNamesArgs
                        {
                            BackendPoolNames = new[]
                            {
                                "ascsBackendPool",
                            },
                            FrontendIpConfigurationNames = new[]
                            {
                                "ascsip0",
                                "ersip0",
                            },
                            HealthProbeNames = new[]
                            {
                                "ascsHealthProbe",
                                "ersHealthProbe",
                            },
                            LoadBalancerName = "ascslb",
                        },
                        VirtualMachines = new[]
                        {
                            new AzureNative.Workloads.Inputs.VirtualMachineResourceNamesArgs
                            {
                                HostName = "ascshostName",
                                NetworkInterfaces = new[]
                                {
                                    new AzureNative.Workloads.Inputs.NetworkInterfaceResourceNamesArgs
                                    {
                                        NetworkInterfaceName = "ascsnic",
                                    },
                                },
                                OsDiskName = "ascsosdisk",
                                VmName = "ascsvm",
                            },
                            new AzureNative.Workloads.Inputs.VirtualMachineResourceNamesArgs
                            {
                                HostName = "ershostName",
                                NetworkInterfaces = new[]
                                {
                                    new AzureNative.Workloads.Inputs.NetworkInterfaceResourceNamesArgs
                                    {
                                        NetworkInterfaceName = "ersnic",
                                    },
                                },
                                OsDiskName = "ersosdisk",
                                VmName = "ersvm",
                            },
                        },
                    },
                    DatabaseServer = new AzureNative.Workloads.Inputs.DatabaseServerFullResourceNamesArgs
                    {
                        LoadBalancer = new AzureNative.Workloads.Inputs.LoadBalancerResourceNamesArgs
                        {
                            BackendPoolNames = new[]
                            {
                                "dbBackendPool",
                            },
                            FrontendIpConfigurationNames = new[]
                            {
                                "dbip",
                            },
                            HealthProbeNames = new[]
                            {
                                "dbHealthProbe",
                            },
                            LoadBalancerName = "dblb",
                        },
                        VirtualMachines = new[]
                        {
                            new AzureNative.Workloads.Inputs.VirtualMachineResourceNamesArgs
                            {
                                DataDiskNames = 
                                {
                                    { "hanaData", new[]
                                    {
                                        "hanadatapr0",
                                        "hanadatapr1",
                                    } },
                                    { "hanaLog", new[]
                                    {
                                        "hanalogpr0",
                                        "hanalogpr1",
                                        "hanalogpr2",
                                    } },
                                    { "hanaShared", new[]
                                    {
                                        "hanasharedpr0",
                                        "hanasharedpr1",
                                    } },
                                    { "usrSap", new[]
                                    {
                                        "usrsappr0",
                                    } },
                                },
                                HostName = "dbprhostName",
                                NetworkInterfaces = new[]
                                {
                                    new AzureNative.Workloads.Inputs.NetworkInterfaceResourceNamesArgs
                                    {
                                        NetworkInterfaceName = "dbprnic",
                                    },
                                },
                                OsDiskName = "dbprosdisk",
                                VmName = "dbvmpr",
                            },
                            new AzureNative.Workloads.Inputs.VirtualMachineResourceNamesArgs
                            {
                                DataDiskNames = 
                                {
                                    { "hanaData", new[]
                                    {
                                        "hanadatasr0",
                                        "hanadatasr1",
                                    } },
                                    { "hanaLog", new[]
                                    {
                                        "hanalogsr0",
                                        "hanalogsr1",
                                        "hanalogsr2",
                                    } },
                                    { "hanaShared", new[]
                                    {
                                        "hanasharedsr0",
                                        "hanasharedsr1",
                                    } },
                                    { "usrSap", new[]
                                    {
                                        "usrsapsr0",
                                    } },
                                },
                                HostName = "dbsrhostName",
                                NetworkInterfaces = new[]
                                {
                                    new AzureNative.Workloads.Inputs.NetworkInterfaceResourceNamesArgs
                                    {
                                        NetworkInterfaceName = "dbsrnic",
                                    },
                                },
                                OsDiskName = "dbsrosdisk",
                                VmName = "dbvmsr",
                            },
                        },
                    },
                    NamingPatternType = "FullResourceName",
                    SharedStorage = new AzureNative.Workloads.Inputs.SharedStorageResourceNamesArgs
                    {
                        SharedStorageAccountName = "storageacc",
                        SharedStorageAccountPrivateEndPointName = "peForxNFS",
                    },
                },
                DatabaseServer = new AzureNative.Workloads.Inputs.DatabaseConfigurationArgs
                {
                    DatabaseType = "HANA",
                    InstanceCount = 2,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_M32ts",
                    },
                },
                DeploymentType = "ThreeTier",
                HighAvailabilityConfig = new AzureNative.Workloads.Inputs.HighAvailabilityConfigurationArgs
                {
                    HighAvailabilityType = "AvailabilityZone",
                },
            },
            OsSapConfiguration = new AzureNative.Workloads.Inputs.OsSapConfigurationArgs
            {
                SapFqdn = "xyz.test.com",
            },
        },
        Environment = "Prod",
        Location = "westcentralus",
        ResourceGroupName = "test-rg",
        SapProduct = "S4HANA",
        SapVirtualInstanceName = "X00",
        Tags = null,
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewSAPVirtualInstance(ctx, "sapVirtualInstance", &workloads.SAPVirtualInstanceArgs{
			Configuration: workloads.DeploymentWithOSConfiguration{
				AppLocation:       "eastus",
				ConfigurationType: "DeploymentWithOSConfig",
				InfrastructureConfiguration: workloads.ThreeTierConfiguration{
					AppResourceGroup: "X00-RG",
					ApplicationServer: workloads.ApplicationServerConfiguration{
						InstanceCount: 6,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "xyz",
										PublicKey:  "abc",
									},
								},
							},
							VmSize: "Standard_E32ds_v4",
						},
					},
					CentralServer: workloads.CentralServerConfiguration{
						InstanceCount: 2,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "xyz",
										PublicKey:  "abc",
									},
								},
							},
							VmSize: "Standard_E16ds_v4",
						},
					},
					CustomResourceNames: workloads.ThreeTierFullResourceNames{
						ApplicationServer: workloads.ApplicationServerFullResourceNames{
							VirtualMachines: []workloads.VirtualMachineResourceNames{
								{
									DataDiskNames: {
										"default": []string{
											"app0disk0",
										},
									},
									HostName: "apphostName0",
									NetworkInterfaces: []workloads.NetworkInterfaceResourceNames{
										{
											NetworkInterfaceName: "appnic0",
										},
									},
									OsDiskName: "app0osdisk",
									VmName:     "appvm0",
								},
								{
									DataDiskNames: {
										"default": []string{
											"app1disk0",
										},
									},
									HostName: "apphostName1",
									NetworkInterfaces: []workloads.NetworkInterfaceResourceNames{
										{
											NetworkInterfaceName: "appnic1",
										},
									},
									OsDiskName: "app1osdisk",
									VmName:     "appvm1",
								},
							},
						},
						CentralServer: workloads.CentralServerFullResourceNames{
							LoadBalancer: workloads.LoadBalancerResourceNames{
								BackendPoolNames: []string{
									"ascsBackendPool",
								},
								FrontendIpConfigurationNames: []string{
									"ascsip0",
									"ersip0",
								},
								HealthProbeNames: []string{
									"ascsHealthProbe",
									"ersHealthProbe",
								},
								LoadBalancerName: "ascslb",
							},
							VirtualMachines: []workloads.VirtualMachineResourceNames{
								{
									HostName: "ascshostName",
									NetworkInterfaces: []workloads.NetworkInterfaceResourceNames{
										{
											NetworkInterfaceName: "ascsnic",
										},
									},
									OsDiskName: "ascsosdisk",
									VmName:     "ascsvm",
								},
								{
									HostName: "ershostName",
									NetworkInterfaces: []workloads.NetworkInterfaceResourceNames{
										{
											NetworkInterfaceName: "ersnic",
										},
									},
									OsDiskName: "ersosdisk",
									VmName:     "ersvm",
								},
							},
						},
						DatabaseServer: workloads.DatabaseServerFullResourceNames{
							LoadBalancer: workloads.LoadBalancerResourceNames{
								BackendPoolNames: []string{
									"dbBackendPool",
								},
								FrontendIpConfigurationNames: []string{
									"dbip",
								},
								HealthProbeNames: []string{
									"dbHealthProbe",
								},
								LoadBalancerName: "dblb",
							},
							VirtualMachines: []workloads.VirtualMachineResourceNames{
								{
									DataDiskNames: {
										"hanaData": []string{
											"hanadatapr0",
											"hanadatapr1",
										},
										"hanaLog": []string{
											"hanalogpr0",
											"hanalogpr1",
											"hanalogpr2",
										},
										"hanaShared": []string{
											"hanasharedpr0",
											"hanasharedpr1",
										},
										"usrSap": []string{
											"usrsappr0",
										},
									},
									HostName: "dbprhostName",
									NetworkInterfaces: []workloads.NetworkInterfaceResourceNames{
										{
											NetworkInterfaceName: "dbprnic",
										},
									},
									OsDiskName: "dbprosdisk",
									VmName:     "dbvmpr",
								},
								{
									DataDiskNames: {
										"hanaData": []string{
											"hanadatasr0",
											"hanadatasr1",
										},
										"hanaLog": []string{
											"hanalogsr0",
											"hanalogsr1",
											"hanalogsr2",
										},
										"hanaShared": []string{
											"hanasharedsr0",
											"hanasharedsr1",
										},
										"usrSap": []string{
											"usrsapsr0",
										},
									},
									HostName: "dbsrhostName",
									NetworkInterfaces: []workloads.NetworkInterfaceResourceNames{
										{
											NetworkInterfaceName: "dbsrnic",
										},
									},
									OsDiskName: "dbsrosdisk",
									VmName:     "dbvmsr",
								},
							},
						},
						NamingPatternType: "FullResourceName",
						SharedStorage: workloads.SharedStorageResourceNames{
							SharedStorageAccountName:                "storageacc",
							SharedStorageAccountPrivateEndPointName: "peForxNFS",
						},
					},
					DatabaseServer: workloads.DatabaseConfiguration{
						DatabaseType:  "HANA",
						InstanceCount: 2,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "xyz",
										PublicKey:  "abc",
									},
								},
							},
							VmSize: "Standard_M32ts",
						},
					},
					DeploymentType: "ThreeTier",
					HighAvailabilityConfig: workloads.HighAvailabilityConfiguration{
						HighAvailabilityType: "AvailabilityZone",
					},
				},
				OsSapConfiguration: workloads.OsSapConfiguration{
					SapFqdn: "xyz.test.com",
				},
			},
			Environment:            pulumi.String("Prod"),
			Location:               pulumi.String("westcentralus"),
			ResourceGroupName:      pulumi.String("test-rg"),
			SapProduct:             pulumi.String("S4HANA"),
			SapVirtualInstanceName: pulumi.String("X00"),
			Tags:                   nil,
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
import com.pulumi.azurenative.workloads.SAPVirtualInstance;
import com.pulumi.azurenative.workloads.SAPVirtualInstanceArgs;
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
        var sapVirtualInstance = new SAPVirtualInstance("sapVirtualInstance", SAPVirtualInstanceArgs.builder()        
            .configuration(Map.ofEntries(
                Map.entry("appLocation", "eastus"),
                Map.entry("configurationType", "DeploymentWithOSConfig"),
                Map.entry("infrastructureConfiguration", Map.ofEntries(
                    Map.entry("appResourceGroup", "X00-RG"),
                    Map.entry("applicationServer", Map.ofEntries(
                        Map.entry("instanceCount", 6),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E32ds_v4")
                        ))
                    )),
                    Map.entry("centralServer", Map.ofEntries(
                        Map.entry("instanceCount", 2),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E16ds_v4")
                        ))
                    )),
                    Map.entry("customResourceNames", Map.ofEntries(
                        Map.entry("applicationServer", Map.of("virtualMachines",                         
                            Map.ofEntries(
                                Map.entry("dataDiskNames", DeploymentConfigurationArgs.builder()
                                    .default_("app0disk0")
                                    .build()),
                                Map.entry("hostName", "apphostName0"),
                                Map.entry("networkInterfaces", Map.of("networkInterfaceName", "appnic0")),
                                Map.entry("osDiskName", "app0osdisk"),
                                Map.entry("vmName", "appvm0")
                            ),
                            Map.ofEntries(
                                Map.entry("dataDiskNames", DeploymentConfigurationArgs.builder()
                                    .default_("app1disk0")
                                    .build()),
                                Map.entry("hostName", "apphostName1"),
                                Map.entry("networkInterfaces", Map.of("networkInterfaceName", "appnic1")),
                                Map.entry("osDiskName", "app1osdisk"),
                                Map.entry("vmName", "appvm1")
                            ))),
                        Map.entry("centralServer", Map.ofEntries(
                            Map.entry("loadBalancer", Map.ofEntries(
                                Map.entry("backendPoolNames", "ascsBackendPool"),
                                Map.entry("frontendIpConfigurationNames",                                 
                                    "ascsip0",
                                    "ersip0"),
                                Map.entry("healthProbeNames",                                 
                                    "ascsHealthProbe",
                                    "ersHealthProbe"),
                                Map.entry("loadBalancerName", "ascslb")
                            )),
                            Map.entry("virtualMachines",                             
                                Map.ofEntries(
                                    Map.entry("hostName", "ascshostName"),
                                    Map.entry("networkInterfaces", Map.of("networkInterfaceName", "ascsnic")),
                                    Map.entry("osDiskName", "ascsosdisk"),
                                    Map.entry("vmName", "ascsvm")
                                ),
                                Map.ofEntries(
                                    Map.entry("hostName", "ershostName"),
                                    Map.entry("networkInterfaces", Map.of("networkInterfaceName", "ersnic")),
                                    Map.entry("osDiskName", "ersosdisk"),
                                    Map.entry("vmName", "ersvm")
                                ))
                        )),
                        Map.entry("databaseServer", Map.ofEntries(
                            Map.entry("loadBalancer", Map.ofEntries(
                                Map.entry("backendPoolNames", "dbBackendPool"),
                                Map.entry("frontendIpConfigurationNames", "dbip"),
                                Map.entry("healthProbeNames", "dbHealthProbe"),
                                Map.entry("loadBalancerName", "dblb")
                            )),
                            Map.entry("virtualMachines",                             
                                Map.ofEntries(
                                    Map.entry("dataDiskNames", DeploymentConfigurationArgs.builder()
                                        .hanaData(                                        
                                            "hanadatapr0",
                                            "hanadatapr1")
                                        .hanaLog(                                        
                                            "hanalogpr0",
                                            "hanalogpr1",
                                            "hanalogpr2")
                                        .hanaShared(                                        
                                            "hanasharedpr0",
                                            "hanasharedpr1")
                                        .usrSap("usrsappr0")
                                        .build()),
                                    Map.entry("hostName", "dbprhostName"),
                                    Map.entry("networkInterfaces", Map.of("networkInterfaceName", "dbprnic")),
                                    Map.entry("osDiskName", "dbprosdisk"),
                                    Map.entry("vmName", "dbvmpr")
                                ),
                                Map.ofEntries(
                                    Map.entry("dataDiskNames", DeploymentConfigurationArgs.builder()
                                        .hanaData(                                        
                                            "hanadatasr0",
                                            "hanadatasr1")
                                        .hanaLog(                                        
                                            "hanalogsr0",
                                            "hanalogsr1",
                                            "hanalogsr2")
                                        .hanaShared(                                        
                                            "hanasharedsr0",
                                            "hanasharedsr1")
                                        .usrSap("usrsapsr0")
                                        .build()),
                                    Map.entry("hostName", "dbsrhostName"),
                                    Map.entry("networkInterfaces", Map.of("networkInterfaceName", "dbsrnic")),
                                    Map.entry("osDiskName", "dbsrosdisk"),
                                    Map.entry("vmName", "dbvmsr")
                                ))
                        )),
                        Map.entry("namingPatternType", "FullResourceName"),
                        Map.entry("sharedStorage", Map.ofEntries(
                            Map.entry("sharedStorageAccountName", "storageacc"),
                            Map.entry("sharedStorageAccountPrivateEndPointName", "peForxNFS")
                        ))
                    )),
                    Map.entry("databaseServer", Map.ofEntries(
                        Map.entry("databaseType", "HANA"),
                        Map.entry("instanceCount", 2),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_M32ts")
                        ))
                    )),
                    Map.entry("deploymentType", "ThreeTier"),
                    Map.entry("highAvailabilityConfig", Map.of("highAvailabilityType", "AvailabilityZone"))
                )),
                Map.entry("osSapConfiguration", Map.of("sapFqdn", "xyz.test.com"))
            ))
            .environment("Prod")
            .location("westcentralus")
            .resourceGroupName("test-rg")
            .sapProduct("S4HANA")
            .sapVirtualInstanceName("X00")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sapVirtualInstance = new azure_native.workloads.SAPVirtualInstance("sapVirtualInstance", {
    configuration: {
        appLocation: "eastus",
        configurationType: "DeploymentWithOSConfig",
        infrastructureConfiguration: {
            appResourceGroup: "X00-RG",
            applicationServer: {
                instanceCount: 6,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_E32ds_v4",
                },
            },
            centralServer: {
                instanceCount: 2,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_E16ds_v4",
                },
            },
            customResourceNames: {
                applicationServer: {
                    virtualMachines: [
                        {
                            dataDiskNames: {
                                "default": ["app0disk0"],
                            },
                            hostName: "apphostName0",
                            networkInterfaces: [{
                                networkInterfaceName: "appnic0",
                            }],
                            osDiskName: "app0osdisk",
                            vmName: "appvm0",
                        },
                        {
                            dataDiskNames: {
                                "default": ["app1disk0"],
                            },
                            hostName: "apphostName1",
                            networkInterfaces: [{
                                networkInterfaceName: "appnic1",
                            }],
                            osDiskName: "app1osdisk",
                            vmName: "appvm1",
                        },
                    ],
                },
                centralServer: {
                    loadBalancer: {
                        backendPoolNames: ["ascsBackendPool"],
                        frontendIpConfigurationNames: [
                            "ascsip0",
                            "ersip0",
                        ],
                        healthProbeNames: [
                            "ascsHealthProbe",
                            "ersHealthProbe",
                        ],
                        loadBalancerName: "ascslb",
                    },
                    virtualMachines: [
                        {
                            hostName: "ascshostName",
                            networkInterfaces: [{
                                networkInterfaceName: "ascsnic",
                            }],
                            osDiskName: "ascsosdisk",
                            vmName: "ascsvm",
                        },
                        {
                            hostName: "ershostName",
                            networkInterfaces: [{
                                networkInterfaceName: "ersnic",
                            }],
                            osDiskName: "ersosdisk",
                            vmName: "ersvm",
                        },
                    ],
                },
                databaseServer: {
                    loadBalancer: {
                        backendPoolNames: ["dbBackendPool"],
                        frontendIpConfigurationNames: ["dbip"],
                        healthProbeNames: ["dbHealthProbe"],
                        loadBalancerName: "dblb",
                    },
                    virtualMachines: [
                        {
                            dataDiskNames: {
                                hanaData: [
                                    "hanadatapr0",
                                    "hanadatapr1",
                                ],
                                hanaLog: [
                                    "hanalogpr0",
                                    "hanalogpr1",
                                    "hanalogpr2",
                                ],
                                hanaShared: [
                                    "hanasharedpr0",
                                    "hanasharedpr1",
                                ],
                                usrSap: ["usrsappr0"],
                            },
                            hostName: "dbprhostName",
                            networkInterfaces: [{
                                networkInterfaceName: "dbprnic",
                            }],
                            osDiskName: "dbprosdisk",
                            vmName: "dbvmpr",
                        },
                        {
                            dataDiskNames: {
                                hanaData: [
                                    "hanadatasr0",
                                    "hanadatasr1",
                                ],
                                hanaLog: [
                                    "hanalogsr0",
                                    "hanalogsr1",
                                    "hanalogsr2",
                                ],
                                hanaShared: [
                                    "hanasharedsr0",
                                    "hanasharedsr1",
                                ],
                                usrSap: ["usrsapsr0"],
                            },
                            hostName: "dbsrhostName",
                            networkInterfaces: [{
                                networkInterfaceName: "dbsrnic",
                            }],
                            osDiskName: "dbsrosdisk",
                            vmName: "dbvmsr",
                        },
                    ],
                },
                namingPatternType: "FullResourceName",
                sharedStorage: {
                    sharedStorageAccountName: "storageacc",
                    sharedStorageAccountPrivateEndPointName: "peForxNFS",
                },
            },
            databaseServer: {
                databaseType: "HANA",
                instanceCount: 2,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_M32ts",
                },
            },
            deploymentType: "ThreeTier",
            highAvailabilityConfig: {
                highAvailabilityType: "AvailabilityZone",
            },
        },
        osSapConfiguration: {
            sapFqdn: "xyz.test.com",
        },
    },
    environment: "Prod",
    location: "westcentralus",
    resourceGroupName: "test-rg",
    sapProduct: "S4HANA",
    sapVirtualInstanceName: "X00",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sap_virtual_instance = azure_native.workloads.SAPVirtualInstance("sapVirtualInstance",
    configuration=azure_native.workloads.DeploymentWithOSConfigurationArgs(
        app_location="eastus",
        configuration_type="DeploymentWithOSConfig",
        infrastructure_configuration=azure_native.workloads.ThreeTierConfigurationArgs(
            app_resource_group="X00-RG",
            application_server=azure_native.workloads.ApplicationServerConfigurationArgs(
                instance_count=6,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_E32ds_v4",
                ),
            ),
            central_server=azure_native.workloads.CentralServerConfigurationArgs(
                instance_count=2,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_E16ds_v4",
                ),
            ),
            custom_resource_names=azure_native.workloads.ThreeTierFullResourceNamesArgs(
                application_server=azure_native.workloads.ApplicationServerFullResourceNamesArgs(
                    virtual_machines=[
                        azure_native.workloads.VirtualMachineResourceNamesArgs(
                            data_disk_names={
                                "default": ["app0disk0"],
                            },
                            host_name="apphostName0",
                            network_interfaces=[azure_native.workloads.NetworkInterfaceResourceNamesArgs(
                                network_interface_name="appnic0",
                            )],
                            os_disk_name="app0osdisk",
                            vm_name="appvm0",
                        ),
                        azure_native.workloads.VirtualMachineResourceNamesArgs(
                            data_disk_names={
                                "default": ["app1disk0"],
                            },
                            host_name="apphostName1",
                            network_interfaces=[azure_native.workloads.NetworkInterfaceResourceNamesArgs(
                                network_interface_name="appnic1",
                            )],
                            os_disk_name="app1osdisk",
                            vm_name="appvm1",
                        ),
                    ],
                ),
                central_server=azure_native.workloads.CentralServerFullResourceNamesArgs(
                    load_balancer=azure_native.workloads.LoadBalancerResourceNamesArgs(
                        backend_pool_names=["ascsBackendPool"],
                        frontend_ip_configuration_names=[
                            "ascsip0",
                            "ersip0",
                        ],
                        health_probe_names=[
                            "ascsHealthProbe",
                            "ersHealthProbe",
                        ],
                        load_balancer_name="ascslb",
                    ),
                    virtual_machines=[
                        azure_native.workloads.VirtualMachineResourceNamesArgs(
                            host_name="ascshostName",
                            network_interfaces=[azure_native.workloads.NetworkInterfaceResourceNamesArgs(
                                network_interface_name="ascsnic",
                            )],
                            os_disk_name="ascsosdisk",
                            vm_name="ascsvm",
                        ),
                        azure_native.workloads.VirtualMachineResourceNamesArgs(
                            host_name="ershostName",
                            network_interfaces=[azure_native.workloads.NetworkInterfaceResourceNamesArgs(
                                network_interface_name="ersnic",
                            )],
                            os_disk_name="ersosdisk",
                            vm_name="ersvm",
                        ),
                    ],
                ),
                database_server=azure_native.workloads.DatabaseServerFullResourceNamesArgs(
                    load_balancer=azure_native.workloads.LoadBalancerResourceNamesArgs(
                        backend_pool_names=["dbBackendPool"],
                        frontend_ip_configuration_names=["dbip"],
                        health_probe_names=["dbHealthProbe"],
                        load_balancer_name="dblb",
                    ),
                    virtual_machines=[
                        azure_native.workloads.VirtualMachineResourceNamesArgs(
                            data_disk_names={
                                "hanaData": [
                                    "hanadatapr0",
                                    "hanadatapr1",
                                ],
                                "hanaLog": [
                                    "hanalogpr0",
                                    "hanalogpr1",
                                    "hanalogpr2",
                                ],
                                "hanaShared": [
                                    "hanasharedpr0",
                                    "hanasharedpr1",
                                ],
                                "usrSap": ["usrsappr0"],
                            },
                            host_name="dbprhostName",
                            network_interfaces=[azure_native.workloads.NetworkInterfaceResourceNamesArgs(
                                network_interface_name="dbprnic",
                            )],
                            os_disk_name="dbprosdisk",
                            vm_name="dbvmpr",
                        ),
                        azure_native.workloads.VirtualMachineResourceNamesArgs(
                            data_disk_names={
                                "hanaData": [
                                    "hanadatasr0",
                                    "hanadatasr1",
                                ],
                                "hanaLog": [
                                    "hanalogsr0",
                                    "hanalogsr1",
                                    "hanalogsr2",
                                ],
                                "hanaShared": [
                                    "hanasharedsr0",
                                    "hanasharedsr1",
                                ],
                                "usrSap": ["usrsapsr0"],
                            },
                            host_name="dbsrhostName",
                            network_interfaces=[azure_native.workloads.NetworkInterfaceResourceNamesArgs(
                                network_interface_name="dbsrnic",
                            )],
                            os_disk_name="dbsrosdisk",
                            vm_name="dbvmsr",
                        ),
                    ],
                ),
                naming_pattern_type="FullResourceName",
                shared_storage=azure_native.workloads.SharedStorageResourceNamesArgs(
                    shared_storage_account_name="storageacc",
                    shared_storage_account_private_end_point_name="peForxNFS",
                ),
            ),
            database_server=azure_native.workloads.DatabaseConfigurationArgs(
                database_type="HANA",
                instance_count=2,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_M32ts",
                ),
            ),
            deployment_type="ThreeTier",
            high_availability_config=azure_native.workloads.HighAvailabilityConfigurationArgs(
                high_availability_type="AvailabilityZone",
            ),
        ),
        os_sap_configuration=azure_native.workloads.OsSapConfigurationArgs(
            sap_fqdn="xyz.test.com",
        ),
    ),
    environment="Prod",
    location="westcentralus",
    resource_group_name="test-rg",
    sap_product="S4HANA",
    sap_virtual_instance_name="X00",
    tags={})

```

```yaml
resources:
  sapVirtualInstance:
    type: azure-native:workloads:SAPVirtualInstance
    properties:
      configuration:
        appLocation: eastus
        configurationType: DeploymentWithOSConfig
        infrastructureConfiguration:
          appResourceGroup: X00-RG
          applicationServer:
            instanceCount: 6
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_E32ds_v4
          centralServer:
            instanceCount: 2
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_E16ds_v4
          customResourceNames:
            applicationServer:
              virtualMachines:
                - dataDiskNames:
                    default:
                      - app0disk0
                  hostName: apphostName0
                  networkInterfaces:
                    - networkInterfaceName: appnic0
                  osDiskName: app0osdisk
                  vmName: appvm0
                - dataDiskNames:
                    default:
                      - app1disk0
                  hostName: apphostName1
                  networkInterfaces:
                    - networkInterfaceName: appnic1
                  osDiskName: app1osdisk
                  vmName: appvm1
            centralServer:
              loadBalancer:
                backendPoolNames:
                  - ascsBackendPool
                frontendIpConfigurationNames:
                  - ascsip0
                  - ersip0
                healthProbeNames:
                  - ascsHealthProbe
                  - ersHealthProbe
                loadBalancerName: ascslb
              virtualMachines:
                - hostName: ascshostName
                  networkInterfaces:
                    - networkInterfaceName: ascsnic
                  osDiskName: ascsosdisk
                  vmName: ascsvm
                - hostName: ershostName
                  networkInterfaces:
                    - networkInterfaceName: ersnic
                  osDiskName: ersosdisk
                  vmName: ersvm
            databaseServer:
              loadBalancer:
                backendPoolNames:
                  - dbBackendPool
                frontendIpConfigurationNames:
                  - dbip
                healthProbeNames:
                  - dbHealthProbe
                loadBalancerName: dblb
              virtualMachines:
                - dataDiskNames:
                    hanaData:
                      - hanadatapr0
                      - hanadatapr1
                    hanaLog:
                      - hanalogpr0
                      - hanalogpr1
                      - hanalogpr2
                    hanaShared:
                      - hanasharedpr0
                      - hanasharedpr1
                    usrSap:
                      - usrsappr0
                  hostName: dbprhostName
                  networkInterfaces:
                    - networkInterfaceName: dbprnic
                  osDiskName: dbprosdisk
                  vmName: dbvmpr
                - dataDiskNames:
                    hanaData:
                      - hanadatasr0
                      - hanadatasr1
                    hanaLog:
                      - hanalogsr0
                      - hanalogsr1
                      - hanalogsr2
                    hanaShared:
                      - hanasharedsr0
                      - hanasharedsr1
                    usrSap:
                      - usrsapsr0
                  hostName: dbsrhostName
                  networkInterfaces:
                    - networkInterfaceName: dbsrnic
                  osDiskName: dbsrosdisk
                  vmName: dbvmsr
            namingPatternType: FullResourceName
            sharedStorage:
              sharedStorageAccountName: storageacc
              sharedStorageAccountPrivateEndPointName: peForxNFS
          databaseServer:
            databaseType: HANA
            instanceCount: 2
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_M32ts
          deploymentType: ThreeTier
          highAvailabilityConfig:
            highAvailabilityType: AvailabilityZone
        osSapConfiguration:
          sapFqdn: xyz.test.com
      environment: Prod
      location: westcentralus
      resourceGroupName: test-rg
      sapProduct: S4HANA
      sapVirtualInstanceName: X00
      tags: {}

```

{{% /example %}}
{{% example %}}
### Create Infrastructure (with OS configuration) with custom resource names for Single Server System
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sapVirtualInstance = new AzureNative.Workloads.SAPVirtualInstance("sapVirtualInstance", new()
    {
        Configuration = new AzureNative.Workloads.Inputs.DeploymentWithOSConfigurationArgs
        {
            AppLocation = "eastus",
            ConfigurationType = "DeploymentWithOSConfig",
            InfrastructureConfiguration = new AzureNative.Workloads.Inputs.SingleServerConfigurationArgs
            {
                AppResourceGroup = "X00-RG",
                DatabaseType = "HANA",
                DeploymentType = "SingleServer",
                NetworkConfiguration = new AzureNative.Workloads.Inputs.NetworkConfigurationArgs
                {
                    IsSecondaryIpEnabled = true,
                },
                SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                {
                    ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                    {
                        Offer = "RHEL-SAP",
                        Publisher = "RedHat",
                        Sku = "84sapha-gen2",
                        Version = "latest",
                    },
                    OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                    {
                        AdminUsername = "{your-username}",
                        OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                        {
                            DisablePasswordAuthentication = true,
                            OsType = "Linux",
                            SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                            {
                                PrivateKey = "xyz",
                                PublicKey = "abc",
                            },
                        },
                    },
                    VmSize = "Standard_E32ds_v4",
                },
            },
            OsSapConfiguration = new AzureNative.Workloads.Inputs.OsSapConfigurationArgs
            {
                SapFqdn = "xyz.test.com",
            },
        },
        Environment = "NonProd",
        Location = "westcentralus",
        ResourceGroupName = "test-rg",
        SapProduct = "S4HANA",
        SapVirtualInstanceName = "X00",
        Tags = null,
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewSAPVirtualInstance(ctx, "sapVirtualInstance", &workloads.SAPVirtualInstanceArgs{
			Configuration: workloads.DeploymentWithOSConfiguration{
				AppLocation:       "eastus",
				ConfigurationType: "DeploymentWithOSConfig",
				InfrastructureConfiguration: workloads.SingleServerConfiguration{
					AppResourceGroup: "X00-RG",
					DatabaseType:     "HANA",
					DeploymentType:   "SingleServer",
					NetworkConfiguration: workloads.NetworkConfiguration{
						IsSecondaryIpEnabled: true,
					},
					SubnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
					VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
						ImageReference: workloads.ImageReference{
							Offer:     "RHEL-SAP",
							Publisher: "RedHat",
							Sku:       "84sapha-gen2",
							Version:   "latest",
						},
						OsProfile: workloads.OSProfile{
							AdminUsername: "{your-username}",
							OsConfiguration: workloads.LinuxConfiguration{
								DisablePasswordAuthentication: true,
								OsType:                        "Linux",
								SshKeyPair: workloads.SshKeyPair{
									PrivateKey: "xyz",
									PublicKey:  "abc",
								},
							},
						},
						VmSize: "Standard_E32ds_v4",
					},
				},
				OsSapConfiguration: workloads.OsSapConfiguration{
					SapFqdn: "xyz.test.com",
				},
			},
			Environment:            pulumi.String("NonProd"),
			Location:               pulumi.String("westcentralus"),
			ResourceGroupName:      pulumi.String("test-rg"),
			SapProduct:             pulumi.String("S4HANA"),
			SapVirtualInstanceName: pulumi.String("X00"),
			Tags:                   nil,
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
import com.pulumi.azurenative.workloads.SAPVirtualInstance;
import com.pulumi.azurenative.workloads.SAPVirtualInstanceArgs;
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
        var sapVirtualInstance = new SAPVirtualInstance("sapVirtualInstance", SAPVirtualInstanceArgs.builder()        
            .configuration(Map.ofEntries(
                Map.entry("appLocation", "eastus"),
                Map.entry("configurationType", "DeploymentWithOSConfig"),
                Map.entry("infrastructureConfiguration", Map.ofEntries(
                    Map.entry("appResourceGroup", "X00-RG"),
                    Map.entry("databaseType", "HANA"),
                    Map.entry("deploymentType", "SingleServer"),
                    Map.entry("networkConfiguration", Map.of("isSecondaryIpEnabled", true)),
                    Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                    Map.entry("virtualMachineConfiguration", Map.ofEntries(
                        Map.entry("imageReference", Map.ofEntries(
                            Map.entry("offer", "RHEL-SAP"),
                            Map.entry("publisher", "RedHat"),
                            Map.entry("sku", "84sapha-gen2"),
                            Map.entry("version", "latest")
                        )),
                        Map.entry("osProfile", Map.ofEntries(
                            Map.entry("adminUsername", "{your-username}"),
                            Map.entry("osConfiguration", Map.ofEntries(
                                Map.entry("disablePasswordAuthentication", true),
                                Map.entry("osType", "Linux"),
                                Map.entry("sshKeyPair", Map.ofEntries(
                                    Map.entry("privateKey", "xyz"),
                                    Map.entry("publicKey", "abc")
                                ))
                            ))
                        )),
                        Map.entry("vmSize", "Standard_E32ds_v4")
                    ))
                )),
                Map.entry("osSapConfiguration", Map.of("sapFqdn", "xyz.test.com"))
            ))
            .environment("NonProd")
            .location("westcentralus")
            .resourceGroupName("test-rg")
            .sapProduct("S4HANA")
            .sapVirtualInstanceName("X00")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sapVirtualInstance = new azure_native.workloads.SAPVirtualInstance("sapVirtualInstance", {
    configuration: {
        appLocation: "eastus",
        configurationType: "DeploymentWithOSConfig",
        infrastructureConfiguration: {
            appResourceGroup: "X00-RG",
            databaseType: "HANA",
            deploymentType: "SingleServer",
            networkConfiguration: {
                isSecondaryIpEnabled: true,
            },
            subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
            virtualMachineConfiguration: {
                imageReference: {
                    offer: "RHEL-SAP",
                    publisher: "RedHat",
                    sku: "84sapha-gen2",
                    version: "latest",
                },
                osProfile: {
                    adminUsername: "{your-username}",
                    osConfiguration: {
                        disablePasswordAuthentication: true,
                        osType: "Linux",
                        sshKeyPair: {
                            privateKey: "xyz",
                            publicKey: "abc",
                        },
                    },
                },
                vmSize: "Standard_E32ds_v4",
            },
        },
        osSapConfiguration: {
            sapFqdn: "xyz.test.com",
        },
    },
    environment: "NonProd",
    location: "westcentralus",
    resourceGroupName: "test-rg",
    sapProduct: "S4HANA",
    sapVirtualInstanceName: "X00",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sap_virtual_instance = azure_native.workloads.SAPVirtualInstance("sapVirtualInstance",
    configuration=azure_native.workloads.DeploymentWithOSConfigurationArgs(
        app_location="eastus",
        configuration_type="DeploymentWithOSConfig",
        infrastructure_configuration=azure_native.workloads.SingleServerConfigurationArgs(
            app_resource_group="X00-RG",
            database_type="HANA",
            deployment_type="SingleServer",
            network_configuration=azure_native.workloads.NetworkConfigurationArgs(
                is_secondary_ip_enabled=True,
            ),
            subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
            virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                image_reference=azure_native.workloads.ImageReferenceArgs(
                    offer="RHEL-SAP",
                    publisher="RedHat",
                    sku="84sapha-gen2",
                    version="latest",
                ),
                os_profile=azure_native.workloads.OSProfileArgs(
                    admin_username="{your-username}",
                    os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                        disable_password_authentication=True,
                        os_type="Linux",
                        ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                            private_key="xyz",
                            public_key="abc",
                        ),
                    ),
                ),
                vm_size="Standard_E32ds_v4",
            ),
        ),
        os_sap_configuration=azure_native.workloads.OsSapConfigurationArgs(
            sap_fqdn="xyz.test.com",
        ),
    ),
    environment="NonProd",
    location="westcentralus",
    resource_group_name="test-rg",
    sap_product="S4HANA",
    sap_virtual_instance_name="X00",
    tags={})

```

```yaml
resources:
  sapVirtualInstance:
    type: azure-native:workloads:SAPVirtualInstance
    properties:
      configuration:
        appLocation: eastus
        configurationType: DeploymentWithOSConfig
        infrastructureConfiguration:
          appResourceGroup: X00-RG
          databaseType: HANA
          deploymentType: SingleServer
          networkConfiguration:
            isSecondaryIpEnabled: true
          subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
          virtualMachineConfiguration:
            imageReference:
              offer: RHEL-SAP
              publisher: RedHat
              sku: 84sapha-gen2
              version: latest
            osProfile:
              adminUsername: '{your-username}'
              osConfiguration:
                disablePasswordAuthentication: true
                osType: Linux
                sshKeyPair:
                  privateKey: xyz
                  publicKey: abc
            vmSize: Standard_E32ds_v4
        osSapConfiguration:
          sapFqdn: xyz.test.com
      environment: NonProd
      location: westcentralus
      resourceGroupName: test-rg
      sapProduct: S4HANA
      sapVirtualInstanceName: X00
      tags: {}

```

{{% /example %}}
{{% example %}}
### Create Infrastructure only for Distributed System
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sapVirtualInstance = new AzureNative.Workloads.SAPVirtualInstance("sapVirtualInstance", new()
    {
        Configuration = new AzureNative.Workloads.Inputs.DeploymentConfigurationArgs
        {
            AppLocation = "eastus",
            ConfigurationType = "Deployment",
            InfrastructureConfiguration = new AzureNative.Workloads.Inputs.ThreeTierConfigurationArgs
            {
                AppResourceGroup = "X00-RG",
                ApplicationServer = new AzureNative.Workloads.Inputs.ApplicationServerConfigurationArgs
                {
                    InstanceCount = 6,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                Ssh = new AzureNative.Workloads.Inputs.SshConfigurationArgs
                                {
                                    PublicKeys = new[]
                                    {
                                        new AzureNative.Workloads.Inputs.SshPublicKeyArgs
                                        {
                                            KeyData = "ssh-rsa public key",
                                        },
                                    },
                                },
                            },
                        },
                        VmSize = "Standard_E32ds_v4",
                    },
                },
                CentralServer = new AzureNative.Workloads.Inputs.CentralServerConfigurationArgs
                {
                    InstanceCount = 1,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                Ssh = new AzureNative.Workloads.Inputs.SshConfigurationArgs
                                {
                                    PublicKeys = new[]
                                    {
                                        new AzureNative.Workloads.Inputs.SshPublicKeyArgs
                                        {
                                            KeyData = "ssh-rsa public key",
                                        },
                                    },
                                },
                            },
                        },
                        VmSize = "Standard_E16ds_v4",
                    },
                },
                DatabaseServer = new AzureNative.Workloads.Inputs.DatabaseConfigurationArgs
                {
                    DatabaseType = "HANA",
                    InstanceCount = 1,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                Ssh = new AzureNative.Workloads.Inputs.SshConfigurationArgs
                                {
                                    PublicKeys = new[]
                                    {
                                        new AzureNative.Workloads.Inputs.SshPublicKeyArgs
                                        {
                                            KeyData = "ssh-rsa public key",
                                        },
                                    },
                                },
                            },
                        },
                        VmSize = "Standard_M32ts",
                    },
                },
                DeploymentType = "ThreeTier",
            },
        },
        Environment = "Prod",
        Location = "westcentralus",
        ResourceGroupName = "test-rg",
        SapProduct = "S4HANA",
        SapVirtualInstanceName = "X00",
        Tags = null,
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewSAPVirtualInstance(ctx, "sapVirtualInstance", &workloads.SAPVirtualInstanceArgs{
			Configuration: workloads.DeploymentConfiguration{
				AppLocation:       "eastus",
				ConfigurationType: "Deployment",
				InfrastructureConfiguration: workloads.ThreeTierConfiguration{
					AppResourceGroup: "X00-RG",
					ApplicationServer: workloads.ApplicationServerConfiguration{
						InstanceCount: 6,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									Ssh: workloads.SshConfiguration{
										PublicKeys: []workloads.SshPublicKey{
											{
												KeyData: "ssh-rsa public key",
											},
										},
									},
								},
							},
							VmSize: "Standard_E32ds_v4",
						},
					},
					CentralServer: workloads.CentralServerConfiguration{
						InstanceCount: 1,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									Ssh: workloads.SshConfiguration{
										PublicKeys: []workloads.SshPublicKey{
											{
												KeyData: "ssh-rsa public key",
											},
										},
									},
								},
							},
							VmSize: "Standard_E16ds_v4",
						},
					},
					DatabaseServer: workloads.DatabaseConfiguration{
						DatabaseType:  "HANA",
						InstanceCount: 1,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									Ssh: workloads.SshConfiguration{
										PublicKeys: []workloads.SshPublicKey{
											{
												KeyData: "ssh-rsa public key",
											},
										},
									},
								},
							},
							VmSize: "Standard_M32ts",
						},
					},
					DeploymentType: "ThreeTier",
				},
			},
			Environment:            pulumi.String("Prod"),
			Location:               pulumi.String("westcentralus"),
			ResourceGroupName:      pulumi.String("test-rg"),
			SapProduct:             pulumi.String("S4HANA"),
			SapVirtualInstanceName: pulumi.String("X00"),
			Tags:                   nil,
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
import com.pulumi.azurenative.workloads.SAPVirtualInstance;
import com.pulumi.azurenative.workloads.SAPVirtualInstanceArgs;
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
        var sapVirtualInstance = new SAPVirtualInstance("sapVirtualInstance", SAPVirtualInstanceArgs.builder()        
            .configuration(Map.ofEntries(
                Map.entry("appLocation", "eastus"),
                Map.entry("configurationType", "Deployment"),
                Map.entry("infrastructureConfiguration", Map.ofEntries(
                    Map.entry("appResourceGroup", "X00-RG"),
                    Map.entry("applicationServer", Map.ofEntries(
                        Map.entry("instanceCount", 6),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("ssh", Map.of("publicKeys", Map.of("keyData", "ssh-rsa public key")))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E32ds_v4")
                        ))
                    )),
                    Map.entry("centralServer", Map.ofEntries(
                        Map.entry("instanceCount", 1),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("ssh", Map.of("publicKeys", Map.of("keyData", "ssh-rsa public key")))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E16ds_v4")
                        ))
                    )),
                    Map.entry("databaseServer", Map.ofEntries(
                        Map.entry("databaseType", "HANA"),
                        Map.entry("instanceCount", 1),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("ssh", Map.of("publicKeys", Map.of("keyData", "ssh-rsa public key")))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_M32ts")
                        ))
                    )),
                    Map.entry("deploymentType", "ThreeTier")
                ))
            ))
            .environment("Prod")
            .location("westcentralus")
            .resourceGroupName("test-rg")
            .sapProduct("S4HANA")
            .sapVirtualInstanceName("X00")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sapVirtualInstance = new azure_native.workloads.SAPVirtualInstance("sapVirtualInstance", {
    configuration: {
        appLocation: "eastus",
        configurationType: "Deployment",
        infrastructureConfiguration: {
            appResourceGroup: "X00-RG",
            applicationServer: {
                instanceCount: 6,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            ssh: {
                                publicKeys: [{
                                    keyData: "ssh-rsa public key",
                                }],
                            },
                        },
                    },
                    vmSize: "Standard_E32ds_v4",
                },
            },
            centralServer: {
                instanceCount: 1,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            ssh: {
                                publicKeys: [{
                                    keyData: "ssh-rsa public key",
                                }],
                            },
                        },
                    },
                    vmSize: "Standard_E16ds_v4",
                },
            },
            databaseServer: {
                databaseType: "HANA",
                instanceCount: 1,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            ssh: {
                                publicKeys: [{
                                    keyData: "ssh-rsa public key",
                                }],
                            },
                        },
                    },
                    vmSize: "Standard_M32ts",
                },
            },
            deploymentType: "ThreeTier",
        },
    },
    environment: "Prod",
    location: "westcentralus",
    resourceGroupName: "test-rg",
    sapProduct: "S4HANA",
    sapVirtualInstanceName: "X00",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sap_virtual_instance = azure_native.workloads.SAPVirtualInstance("sapVirtualInstance",
    configuration=azure_native.workloads.DeploymentConfigurationArgs(
        app_location="eastus",
        configuration_type="Deployment",
        infrastructure_configuration=azure_native.workloads.ThreeTierConfigurationArgs(
            app_resource_group="X00-RG",
            application_server=azure_native.workloads.ApplicationServerConfigurationArgs(
                instance_count=6,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh=azure_native.workloads.SshConfigurationArgs(
                                public_keys=[azure_native.workloads.SshPublicKeyArgs(
                                    key_data="ssh-rsa public key",
                                )],
                            ),
                        ),
                    ),
                    vm_size="Standard_E32ds_v4",
                ),
            ),
            central_server=azure_native.workloads.CentralServerConfigurationArgs(
                instance_count=1,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh=azure_native.workloads.SshConfigurationArgs(
                                public_keys=[azure_native.workloads.SshPublicKeyArgs(
                                    key_data="ssh-rsa public key",
                                )],
                            ),
                        ),
                    ),
                    vm_size="Standard_E16ds_v4",
                ),
            ),
            database_server=azure_native.workloads.DatabaseConfigurationArgs(
                database_type="HANA",
                instance_count=1,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh=azure_native.workloads.SshConfigurationArgs(
                                public_keys=[azure_native.workloads.SshPublicKeyArgs(
                                    key_data="ssh-rsa public key",
                                )],
                            ),
                        ),
                    ),
                    vm_size="Standard_M32ts",
                ),
            ),
            deployment_type="ThreeTier",
        ),
    ),
    environment="Prod",
    location="westcentralus",
    resource_group_name="test-rg",
    sap_product="S4HANA",
    sap_virtual_instance_name="X00",
    tags={})

```

```yaml
resources:
  sapVirtualInstance:
    type: azure-native:workloads:SAPVirtualInstance
    properties:
      configuration:
        appLocation: eastus
        configurationType: Deployment
        infrastructureConfiguration:
          appResourceGroup: X00-RG
          applicationServer:
            instanceCount: 6
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  ssh:
                    publicKeys:
                      - keyData: ssh-rsa public key
              vmSize: Standard_E32ds_v4
          centralServer:
            instanceCount: 1
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  ssh:
                    publicKeys:
                      - keyData: ssh-rsa public key
              vmSize: Standard_E16ds_v4
          databaseServer:
            databaseType: HANA
            instanceCount: 1
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  ssh:
                    publicKeys:
                      - keyData: ssh-rsa public key
              vmSize: Standard_M32ts
          deploymentType: ThreeTier
      environment: Prod
      location: westcentralus
      resourceGroupName: test-rg
      sapProduct: S4HANA
      sapVirtualInstanceName: X00
      tags: {}

```

{{% /example %}}
{{% example %}}
### Create Infrastructure only for HA System with Availability Set
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sapVirtualInstance = new AzureNative.Workloads.SAPVirtualInstance("sapVirtualInstance", new()
    {
        Configuration = new AzureNative.Workloads.Inputs.DeploymentConfigurationArgs
        {
            AppLocation = "eastus",
            ConfigurationType = "Deployment",
            InfrastructureConfiguration = new AzureNative.Workloads.Inputs.ThreeTierConfigurationArgs
            {
                AppResourceGroup = "X00-RG",
                ApplicationServer = new AzureNative.Workloads.Inputs.ApplicationServerConfigurationArgs
                {
                    InstanceCount = 5,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                Ssh = new AzureNative.Workloads.Inputs.SshConfigurationArgs
                                {
                                    PublicKeys = new[]
                                    {
                                        new AzureNative.Workloads.Inputs.SshPublicKeyArgs
                                        {
                                            KeyData = "ssh-rsa public key",
                                        },
                                    },
                                },
                            },
                        },
                        VmSize = "Standard_E32ds_v4",
                    },
                },
                CentralServer = new AzureNative.Workloads.Inputs.CentralServerConfigurationArgs
                {
                    InstanceCount = 2,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                Ssh = new AzureNative.Workloads.Inputs.SshConfigurationArgs
                                {
                                    PublicKeys = new[]
                                    {
                                        new AzureNative.Workloads.Inputs.SshPublicKeyArgs
                                        {
                                            KeyData = "ssh-rsa public key",
                                        },
                                    },
                                },
                            },
                        },
                        VmSize = "Standard_E16ds_v4",
                    },
                },
                DatabaseServer = new AzureNative.Workloads.Inputs.DatabaseConfigurationArgs
                {
                    DatabaseType = "HANA",
                    InstanceCount = 2,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                Ssh = new AzureNative.Workloads.Inputs.SshConfigurationArgs
                                {
                                    PublicKeys = new[]
                                    {
                                        new AzureNative.Workloads.Inputs.SshPublicKeyArgs
                                        {
                                            KeyData = "ssh-rsa public key",
                                        },
                                    },
                                },
                            },
                        },
                        VmSize = "Standard_M32ts",
                    },
                },
                DeploymentType = "ThreeTier",
                HighAvailabilityConfig = new AzureNative.Workloads.Inputs.HighAvailabilityConfigurationArgs
                {
                    HighAvailabilityType = "AvailabilitySet",
                },
            },
        },
        Environment = "Prod",
        Location = "westcentralus",
        ResourceGroupName = "test-rg",
        SapProduct = "S4HANA",
        SapVirtualInstanceName = "X00",
        Tags = null,
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewSAPVirtualInstance(ctx, "sapVirtualInstance", &workloads.SAPVirtualInstanceArgs{
			Configuration: workloads.DeploymentConfiguration{
				AppLocation:       "eastus",
				ConfigurationType: "Deployment",
				InfrastructureConfiguration: workloads.ThreeTierConfiguration{
					AppResourceGroup: "X00-RG",
					ApplicationServer: workloads.ApplicationServerConfiguration{
						InstanceCount: 5,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									Ssh: workloads.SshConfiguration{
										PublicKeys: []workloads.SshPublicKey{
											{
												KeyData: "ssh-rsa public key",
											},
										},
									},
								},
							},
							VmSize: "Standard_E32ds_v4",
						},
					},
					CentralServer: workloads.CentralServerConfiguration{
						InstanceCount: 2,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									Ssh: workloads.SshConfiguration{
										PublicKeys: []workloads.SshPublicKey{
											{
												KeyData: "ssh-rsa public key",
											},
										},
									},
								},
							},
							VmSize: "Standard_E16ds_v4",
						},
					},
					DatabaseServer: workloads.DatabaseConfiguration{
						DatabaseType:  "HANA",
						InstanceCount: 2,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									Ssh: workloads.SshConfiguration{
										PublicKeys: []workloads.SshPublicKey{
											{
												KeyData: "ssh-rsa public key",
											},
										},
									},
								},
							},
							VmSize: "Standard_M32ts",
						},
					},
					DeploymentType: "ThreeTier",
					HighAvailabilityConfig: workloads.HighAvailabilityConfiguration{
						HighAvailabilityType: "AvailabilitySet",
					},
				},
			},
			Environment:            pulumi.String("Prod"),
			Location:               pulumi.String("westcentralus"),
			ResourceGroupName:      pulumi.String("test-rg"),
			SapProduct:             pulumi.String("S4HANA"),
			SapVirtualInstanceName: pulumi.String("X00"),
			Tags:                   nil,
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
import com.pulumi.azurenative.workloads.SAPVirtualInstance;
import com.pulumi.azurenative.workloads.SAPVirtualInstanceArgs;
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
        var sapVirtualInstance = new SAPVirtualInstance("sapVirtualInstance", SAPVirtualInstanceArgs.builder()        
            .configuration(Map.ofEntries(
                Map.entry("appLocation", "eastus"),
                Map.entry("configurationType", "Deployment"),
                Map.entry("infrastructureConfiguration", Map.ofEntries(
                    Map.entry("appResourceGroup", "X00-RG"),
                    Map.entry("applicationServer", Map.ofEntries(
                        Map.entry("instanceCount", 5),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("ssh", Map.of("publicKeys", Map.of("keyData", "ssh-rsa public key")))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E32ds_v4")
                        ))
                    )),
                    Map.entry("centralServer", Map.ofEntries(
                        Map.entry("instanceCount", 2),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("ssh", Map.of("publicKeys", Map.of("keyData", "ssh-rsa public key")))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E16ds_v4")
                        ))
                    )),
                    Map.entry("databaseServer", Map.ofEntries(
                        Map.entry("databaseType", "HANA"),
                        Map.entry("instanceCount", 2),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("ssh", Map.of("publicKeys", Map.of("keyData", "ssh-rsa public key")))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_M32ts")
                        ))
                    )),
                    Map.entry("deploymentType", "ThreeTier"),
                    Map.entry("highAvailabilityConfig", Map.of("highAvailabilityType", "AvailabilitySet"))
                ))
            ))
            .environment("Prod")
            .location("westcentralus")
            .resourceGroupName("test-rg")
            .sapProduct("S4HANA")
            .sapVirtualInstanceName("X00")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sapVirtualInstance = new azure_native.workloads.SAPVirtualInstance("sapVirtualInstance", {
    configuration: {
        appLocation: "eastus",
        configurationType: "Deployment",
        infrastructureConfiguration: {
            appResourceGroup: "X00-RG",
            applicationServer: {
                instanceCount: 5,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            ssh: {
                                publicKeys: [{
                                    keyData: "ssh-rsa public key",
                                }],
                            },
                        },
                    },
                    vmSize: "Standard_E32ds_v4",
                },
            },
            centralServer: {
                instanceCount: 2,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            ssh: {
                                publicKeys: [{
                                    keyData: "ssh-rsa public key",
                                }],
                            },
                        },
                    },
                    vmSize: "Standard_E16ds_v4",
                },
            },
            databaseServer: {
                databaseType: "HANA",
                instanceCount: 2,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            ssh: {
                                publicKeys: [{
                                    keyData: "ssh-rsa public key",
                                }],
                            },
                        },
                    },
                    vmSize: "Standard_M32ts",
                },
            },
            deploymentType: "ThreeTier",
            highAvailabilityConfig: {
                highAvailabilityType: "AvailabilitySet",
            },
        },
    },
    environment: "Prod",
    location: "westcentralus",
    resourceGroupName: "test-rg",
    sapProduct: "S4HANA",
    sapVirtualInstanceName: "X00",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sap_virtual_instance = azure_native.workloads.SAPVirtualInstance("sapVirtualInstance",
    configuration=azure_native.workloads.DeploymentConfigurationArgs(
        app_location="eastus",
        configuration_type="Deployment",
        infrastructure_configuration=azure_native.workloads.ThreeTierConfigurationArgs(
            app_resource_group="X00-RG",
            application_server=azure_native.workloads.ApplicationServerConfigurationArgs(
                instance_count=5,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh=azure_native.workloads.SshConfigurationArgs(
                                public_keys=[azure_native.workloads.SshPublicKeyArgs(
                                    key_data="ssh-rsa public key",
                                )],
                            ),
                        ),
                    ),
                    vm_size="Standard_E32ds_v4",
                ),
            ),
            central_server=azure_native.workloads.CentralServerConfigurationArgs(
                instance_count=2,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh=azure_native.workloads.SshConfigurationArgs(
                                public_keys=[azure_native.workloads.SshPublicKeyArgs(
                                    key_data="ssh-rsa public key",
                                )],
                            ),
                        ),
                    ),
                    vm_size="Standard_E16ds_v4",
                ),
            ),
            database_server=azure_native.workloads.DatabaseConfigurationArgs(
                database_type="HANA",
                instance_count=2,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh=azure_native.workloads.SshConfigurationArgs(
                                public_keys=[azure_native.workloads.SshPublicKeyArgs(
                                    key_data="ssh-rsa public key",
                                )],
                            ),
                        ),
                    ),
                    vm_size="Standard_M32ts",
                ),
            ),
            deployment_type="ThreeTier",
            high_availability_config=azure_native.workloads.HighAvailabilityConfigurationArgs(
                high_availability_type="AvailabilitySet",
            ),
        ),
    ),
    environment="Prod",
    location="westcentralus",
    resource_group_name="test-rg",
    sap_product="S4HANA",
    sap_virtual_instance_name="X00",
    tags={})

```

```yaml
resources:
  sapVirtualInstance:
    type: azure-native:workloads:SAPVirtualInstance
    properties:
      configuration:
        appLocation: eastus
        configurationType: Deployment
        infrastructureConfiguration:
          appResourceGroup: X00-RG
          applicationServer:
            instanceCount: 5
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  ssh:
                    publicKeys:
                      - keyData: ssh-rsa public key
              vmSize: Standard_E32ds_v4
          centralServer:
            instanceCount: 2
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  ssh:
                    publicKeys:
                      - keyData: ssh-rsa public key
              vmSize: Standard_E16ds_v4
          databaseServer:
            databaseType: HANA
            instanceCount: 2
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  ssh:
                    publicKeys:
                      - keyData: ssh-rsa public key
              vmSize: Standard_M32ts
          deploymentType: ThreeTier
          highAvailabilityConfig:
            highAvailabilityType: AvailabilitySet
      environment: Prod
      location: westcentralus
      resourceGroupName: test-rg
      sapProduct: S4HANA
      sapVirtualInstanceName: X00
      tags: {}

```

{{% /example %}}
{{% example %}}
### Create Infrastructure only for HA System with Availability Zone
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sapVirtualInstance = new AzureNative.Workloads.SAPVirtualInstance("sapVirtualInstance", new()
    {
        Configuration = new AzureNative.Workloads.Inputs.DeploymentConfigurationArgs
        {
            AppLocation = "eastus",
            ConfigurationType = "Deployment",
            InfrastructureConfiguration = new AzureNative.Workloads.Inputs.ThreeTierConfigurationArgs
            {
                AppResourceGroup = "X00-RG",
                ApplicationServer = new AzureNative.Workloads.Inputs.ApplicationServerConfigurationArgs
                {
                    InstanceCount = 6,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                Ssh = new AzureNative.Workloads.Inputs.SshConfigurationArgs
                                {
                                    PublicKeys = new[]
                                    {
                                        new AzureNative.Workloads.Inputs.SshPublicKeyArgs
                                        {
                                            KeyData = "ssh-rsa public key",
                                        },
                                    },
                                },
                            },
                        },
                        VmSize = "Standard_E32ds_v4",
                    },
                },
                CentralServer = new AzureNative.Workloads.Inputs.CentralServerConfigurationArgs
                {
                    InstanceCount = 2,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                Ssh = new AzureNative.Workloads.Inputs.SshConfigurationArgs
                                {
                                    PublicKeys = new[]
                                    {
                                        new AzureNative.Workloads.Inputs.SshPublicKeyArgs
                                        {
                                            KeyData = "ssh-rsa public key",
                                        },
                                    },
                                },
                            },
                        },
                        VmSize = "Standard_E16ds_v4",
                    },
                },
                DatabaseServer = new AzureNative.Workloads.Inputs.DatabaseConfigurationArgs
                {
                    DatabaseType = "HANA",
                    InstanceCount = 2,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                Ssh = new AzureNative.Workloads.Inputs.SshConfigurationArgs
                                {
                                    PublicKeys = new[]
                                    {
                                        new AzureNative.Workloads.Inputs.SshPublicKeyArgs
                                        {
                                            KeyData = "ssh-rsa public key",
                                        },
                                    },
                                },
                            },
                        },
                        VmSize = "Standard_M32ts",
                    },
                },
                DeploymentType = "ThreeTier",
                HighAvailabilityConfig = new AzureNative.Workloads.Inputs.HighAvailabilityConfigurationArgs
                {
                    HighAvailabilityType = "AvailabilityZone",
                },
            },
        },
        Environment = "Prod",
        Location = "westcentralus",
        ResourceGroupName = "test-rg",
        SapProduct = "S4HANA",
        SapVirtualInstanceName = "X00",
        Tags = null,
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewSAPVirtualInstance(ctx, "sapVirtualInstance", &workloads.SAPVirtualInstanceArgs{
			Configuration: workloads.DeploymentConfiguration{
				AppLocation:       "eastus",
				ConfigurationType: "Deployment",
				InfrastructureConfiguration: workloads.ThreeTierConfiguration{
					AppResourceGroup: "X00-RG",
					ApplicationServer: workloads.ApplicationServerConfiguration{
						InstanceCount: 6,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									Ssh: workloads.SshConfiguration{
										PublicKeys: []workloads.SshPublicKey{
											{
												KeyData: "ssh-rsa public key",
											},
										},
									},
								},
							},
							VmSize: "Standard_E32ds_v4",
						},
					},
					CentralServer: workloads.CentralServerConfiguration{
						InstanceCount: 2,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									Ssh: workloads.SshConfiguration{
										PublicKeys: []workloads.SshPublicKey{
											{
												KeyData: "ssh-rsa public key",
											},
										},
									},
								},
							},
							VmSize: "Standard_E16ds_v4",
						},
					},
					DatabaseServer: workloads.DatabaseConfiguration{
						DatabaseType:  "HANA",
						InstanceCount: 2,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									Ssh: workloads.SshConfiguration{
										PublicKeys: []workloads.SshPublicKey{
											{
												KeyData: "ssh-rsa public key",
											},
										},
									},
								},
							},
							VmSize: "Standard_M32ts",
						},
					},
					DeploymentType: "ThreeTier",
					HighAvailabilityConfig: workloads.HighAvailabilityConfiguration{
						HighAvailabilityType: "AvailabilityZone",
					},
				},
			},
			Environment:            pulumi.String("Prod"),
			Location:               pulumi.String("westcentralus"),
			ResourceGroupName:      pulumi.String("test-rg"),
			SapProduct:             pulumi.String("S4HANA"),
			SapVirtualInstanceName: pulumi.String("X00"),
			Tags:                   nil,
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
import com.pulumi.azurenative.workloads.SAPVirtualInstance;
import com.pulumi.azurenative.workloads.SAPVirtualInstanceArgs;
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
        var sapVirtualInstance = new SAPVirtualInstance("sapVirtualInstance", SAPVirtualInstanceArgs.builder()        
            .configuration(Map.ofEntries(
                Map.entry("appLocation", "eastus"),
                Map.entry("configurationType", "Deployment"),
                Map.entry("infrastructureConfiguration", Map.ofEntries(
                    Map.entry("appResourceGroup", "X00-RG"),
                    Map.entry("applicationServer", Map.ofEntries(
                        Map.entry("instanceCount", 6),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("ssh", Map.of("publicKeys", Map.of("keyData", "ssh-rsa public key")))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E32ds_v4")
                        ))
                    )),
                    Map.entry("centralServer", Map.ofEntries(
                        Map.entry("instanceCount", 2),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("ssh", Map.of("publicKeys", Map.of("keyData", "ssh-rsa public key")))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E16ds_v4")
                        ))
                    )),
                    Map.entry("databaseServer", Map.ofEntries(
                        Map.entry("databaseType", "HANA"),
                        Map.entry("instanceCount", 2),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("ssh", Map.of("publicKeys", Map.of("keyData", "ssh-rsa public key")))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_M32ts")
                        ))
                    )),
                    Map.entry("deploymentType", "ThreeTier"),
                    Map.entry("highAvailabilityConfig", Map.of("highAvailabilityType", "AvailabilityZone"))
                ))
            ))
            .environment("Prod")
            .location("westcentralus")
            .resourceGroupName("test-rg")
            .sapProduct("S4HANA")
            .sapVirtualInstanceName("X00")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sapVirtualInstance = new azure_native.workloads.SAPVirtualInstance("sapVirtualInstance", {
    configuration: {
        appLocation: "eastus",
        configurationType: "Deployment",
        infrastructureConfiguration: {
            appResourceGroup: "X00-RG",
            applicationServer: {
                instanceCount: 6,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            ssh: {
                                publicKeys: [{
                                    keyData: "ssh-rsa public key",
                                }],
                            },
                        },
                    },
                    vmSize: "Standard_E32ds_v4",
                },
            },
            centralServer: {
                instanceCount: 2,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            ssh: {
                                publicKeys: [{
                                    keyData: "ssh-rsa public key",
                                }],
                            },
                        },
                    },
                    vmSize: "Standard_E16ds_v4",
                },
            },
            databaseServer: {
                databaseType: "HANA",
                instanceCount: 2,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            ssh: {
                                publicKeys: [{
                                    keyData: "ssh-rsa public key",
                                }],
                            },
                        },
                    },
                    vmSize: "Standard_M32ts",
                },
            },
            deploymentType: "ThreeTier",
            highAvailabilityConfig: {
                highAvailabilityType: "AvailabilityZone",
            },
        },
    },
    environment: "Prod",
    location: "westcentralus",
    resourceGroupName: "test-rg",
    sapProduct: "S4HANA",
    sapVirtualInstanceName: "X00",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sap_virtual_instance = azure_native.workloads.SAPVirtualInstance("sapVirtualInstance",
    configuration=azure_native.workloads.DeploymentConfigurationArgs(
        app_location="eastus",
        configuration_type="Deployment",
        infrastructure_configuration=azure_native.workloads.ThreeTierConfigurationArgs(
            app_resource_group="X00-RG",
            application_server=azure_native.workloads.ApplicationServerConfigurationArgs(
                instance_count=6,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh=azure_native.workloads.SshConfigurationArgs(
                                public_keys=[azure_native.workloads.SshPublicKeyArgs(
                                    key_data="ssh-rsa public key",
                                )],
                            ),
                        ),
                    ),
                    vm_size="Standard_E32ds_v4",
                ),
            ),
            central_server=azure_native.workloads.CentralServerConfigurationArgs(
                instance_count=2,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh=azure_native.workloads.SshConfigurationArgs(
                                public_keys=[azure_native.workloads.SshPublicKeyArgs(
                                    key_data="ssh-rsa public key",
                                )],
                            ),
                        ),
                    ),
                    vm_size="Standard_E16ds_v4",
                ),
            ),
            database_server=azure_native.workloads.DatabaseConfigurationArgs(
                database_type="HANA",
                instance_count=2,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh=azure_native.workloads.SshConfigurationArgs(
                                public_keys=[azure_native.workloads.SshPublicKeyArgs(
                                    key_data="ssh-rsa public key",
                                )],
                            ),
                        ),
                    ),
                    vm_size="Standard_M32ts",
                ),
            ),
            deployment_type="ThreeTier",
            high_availability_config=azure_native.workloads.HighAvailabilityConfigurationArgs(
                high_availability_type="AvailabilityZone",
            ),
        ),
    ),
    environment="Prod",
    location="westcentralus",
    resource_group_name="test-rg",
    sap_product="S4HANA",
    sap_virtual_instance_name="X00",
    tags={})

```

```yaml
resources:
  sapVirtualInstance:
    type: azure-native:workloads:SAPVirtualInstance
    properties:
      configuration:
        appLocation: eastus
        configurationType: Deployment
        infrastructureConfiguration:
          appResourceGroup: X00-RG
          applicationServer:
            instanceCount: 6
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  ssh:
                    publicKeys:
                      - keyData: ssh-rsa public key
              vmSize: Standard_E32ds_v4
          centralServer:
            instanceCount: 2
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  ssh:
                    publicKeys:
                      - keyData: ssh-rsa public key
              vmSize: Standard_E16ds_v4
          databaseServer:
            databaseType: HANA
            instanceCount: 2
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  ssh:
                    publicKeys:
                      - keyData: ssh-rsa public key
              vmSize: Standard_M32ts
          deploymentType: ThreeTier
          highAvailabilityConfig:
            highAvailabilityType: AvailabilityZone
      environment: Prod
      location: westcentralus
      resourceGroupName: test-rg
      sapProduct: S4HANA
      sapVirtualInstanceName: X00
      tags: {}

```

{{% /example %}}
{{% example %}}
### Create Infrastructure only for Single Server System
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sapVirtualInstance = new AzureNative.Workloads.SAPVirtualInstance("sapVirtualInstance", new()
    {
        Configuration = new AzureNative.Workloads.Inputs.DeploymentConfigurationArgs
        {
            AppLocation = "eastus",
            ConfigurationType = "Deployment",
            InfrastructureConfiguration = new AzureNative.Workloads.Inputs.SingleServerConfigurationArgs
            {
                AppResourceGroup = "X00-RG",
                DatabaseType = "HANA",
                DeploymentType = "SingleServer",
                NetworkConfiguration = new AzureNative.Workloads.Inputs.NetworkConfigurationArgs
                {
                    IsSecondaryIpEnabled = true,
                },
                SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                {
                    ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                    {
                        Offer = "RHEL-SAP",
                        Publisher = "RedHat",
                        Sku = "84sapha-gen2",
                        Version = "latest",
                    },
                    OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                    {
                        AdminUsername = "{your-username}",
                        OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                        {
                            DisablePasswordAuthentication = true,
                            OsType = "Linux",
                            Ssh = new AzureNative.Workloads.Inputs.SshConfigurationArgs
                            {
                                PublicKeys = new[]
                                {
                                    new AzureNative.Workloads.Inputs.SshPublicKeyArgs
                                    {
                                        KeyData = "ssh-rsa public key",
                                    },
                                },
                            },
                        },
                    },
                    VmSize = "Standard_E32ds_v4",
                },
            },
        },
        Environment = "NonProd",
        Location = "westcentralus",
        ResourceGroupName = "test-rg",
        SapProduct = "S4HANA",
        SapVirtualInstanceName = "X00",
        Tags = null,
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewSAPVirtualInstance(ctx, "sapVirtualInstance", &workloads.SAPVirtualInstanceArgs{
			Configuration: workloads.DeploymentConfiguration{
				AppLocation:       "eastus",
				ConfigurationType: "Deployment",
				InfrastructureConfiguration: workloads.SingleServerConfiguration{
					AppResourceGroup: "X00-RG",
					DatabaseType:     "HANA",
					DeploymentType:   "SingleServer",
					NetworkConfiguration: workloads.NetworkConfiguration{
						IsSecondaryIpEnabled: true,
					},
					SubnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
					VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
						ImageReference: workloads.ImageReference{
							Offer:     "RHEL-SAP",
							Publisher: "RedHat",
							Sku:       "84sapha-gen2",
							Version:   "latest",
						},
						OsProfile: workloads.OSProfile{
							AdminUsername: "{your-username}",
							OsConfiguration: workloads.LinuxConfiguration{
								DisablePasswordAuthentication: true,
								OsType:                        "Linux",
								Ssh: workloads.SshConfiguration{
									PublicKeys: []workloads.SshPublicKey{
										{
											KeyData: "ssh-rsa public key",
										},
									},
								},
							},
						},
						VmSize: "Standard_E32ds_v4",
					},
				},
			},
			Environment:            pulumi.String("NonProd"),
			Location:               pulumi.String("westcentralus"),
			ResourceGroupName:      pulumi.String("test-rg"),
			SapProduct:             pulumi.String("S4HANA"),
			SapVirtualInstanceName: pulumi.String("X00"),
			Tags:                   nil,
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
import com.pulumi.azurenative.workloads.SAPVirtualInstance;
import com.pulumi.azurenative.workloads.SAPVirtualInstanceArgs;
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
        var sapVirtualInstance = new SAPVirtualInstance("sapVirtualInstance", SAPVirtualInstanceArgs.builder()        
            .configuration(Map.ofEntries(
                Map.entry("appLocation", "eastus"),
                Map.entry("configurationType", "Deployment"),
                Map.entry("infrastructureConfiguration", Map.ofEntries(
                    Map.entry("appResourceGroup", "X00-RG"),
                    Map.entry("databaseType", "HANA"),
                    Map.entry("deploymentType", "SingleServer"),
                    Map.entry("networkConfiguration", Map.of("isSecondaryIpEnabled", true)),
                    Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                    Map.entry("virtualMachineConfiguration", Map.ofEntries(
                        Map.entry("imageReference", Map.ofEntries(
                            Map.entry("offer", "RHEL-SAP"),
                            Map.entry("publisher", "RedHat"),
                            Map.entry("sku", "84sapha-gen2"),
                            Map.entry("version", "latest")
                        )),
                        Map.entry("osProfile", Map.ofEntries(
                            Map.entry("adminUsername", "{your-username}"),
                            Map.entry("osConfiguration", Map.ofEntries(
                                Map.entry("disablePasswordAuthentication", true),
                                Map.entry("osType", "Linux"),
                                Map.entry("ssh", Map.of("publicKeys", Map.of("keyData", "ssh-rsa public key")))
                            ))
                        )),
                        Map.entry("vmSize", "Standard_E32ds_v4")
                    ))
                ))
            ))
            .environment("NonProd")
            .location("westcentralus")
            .resourceGroupName("test-rg")
            .sapProduct("S4HANA")
            .sapVirtualInstanceName("X00")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sapVirtualInstance = new azure_native.workloads.SAPVirtualInstance("sapVirtualInstance", {
    configuration: {
        appLocation: "eastus",
        configurationType: "Deployment",
        infrastructureConfiguration: {
            appResourceGroup: "X00-RG",
            databaseType: "HANA",
            deploymentType: "SingleServer",
            networkConfiguration: {
                isSecondaryIpEnabled: true,
            },
            subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
            virtualMachineConfiguration: {
                imageReference: {
                    offer: "RHEL-SAP",
                    publisher: "RedHat",
                    sku: "84sapha-gen2",
                    version: "latest",
                },
                osProfile: {
                    adminUsername: "{your-username}",
                    osConfiguration: {
                        disablePasswordAuthentication: true,
                        osType: "Linux",
                        ssh: {
                            publicKeys: [{
                                keyData: "ssh-rsa public key",
                            }],
                        },
                    },
                },
                vmSize: "Standard_E32ds_v4",
            },
        },
    },
    environment: "NonProd",
    location: "westcentralus",
    resourceGroupName: "test-rg",
    sapProduct: "S4HANA",
    sapVirtualInstanceName: "X00",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sap_virtual_instance = azure_native.workloads.SAPVirtualInstance("sapVirtualInstance",
    configuration=azure_native.workloads.DeploymentConfigurationArgs(
        app_location="eastus",
        configuration_type="Deployment",
        infrastructure_configuration=azure_native.workloads.SingleServerConfigurationArgs(
            app_resource_group="X00-RG",
            database_type="HANA",
            deployment_type="SingleServer",
            network_configuration=azure_native.workloads.NetworkConfigurationArgs(
                is_secondary_ip_enabled=True,
            ),
            subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
            virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                image_reference=azure_native.workloads.ImageReferenceArgs(
                    offer="RHEL-SAP",
                    publisher="RedHat",
                    sku="84sapha-gen2",
                    version="latest",
                ),
                os_profile=azure_native.workloads.OSProfileArgs(
                    admin_username="{your-username}",
                    os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                        disable_password_authentication=True,
                        os_type="Linux",
                        ssh=azure_native.workloads.SshConfigurationArgs(
                            public_keys=[azure_native.workloads.SshPublicKeyArgs(
                                key_data="ssh-rsa public key",
                            )],
                        ),
                    ),
                ),
                vm_size="Standard_E32ds_v4",
            ),
        ),
    ),
    environment="NonProd",
    location="westcentralus",
    resource_group_name="test-rg",
    sap_product="S4HANA",
    sap_virtual_instance_name="X00",
    tags={})

```

```yaml
resources:
  sapVirtualInstance:
    type: azure-native:workloads:SAPVirtualInstance
    properties:
      configuration:
        appLocation: eastus
        configurationType: Deployment
        infrastructureConfiguration:
          appResourceGroup: X00-RG
          databaseType: HANA
          deploymentType: SingleServer
          networkConfiguration:
            isSecondaryIpEnabled: true
          subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
          virtualMachineConfiguration:
            imageReference:
              offer: RHEL-SAP
              publisher: RedHat
              sku: 84sapha-gen2
              version: latest
            osProfile:
              adminUsername: '{your-username}'
              osConfiguration:
                disablePasswordAuthentication: true
                osType: Linux
                ssh:
                  publicKeys:
                    - keyData: ssh-rsa public key
            vmSize: Standard_E32ds_v4
      environment: NonProd
      location: westcentralus
      resourceGroupName: test-rg
      sapProduct: S4HANA
      sapVirtualInstanceName: X00
      tags: {}

```

{{% /example %}}
{{% example %}}
### Create Infrastructure with Disk and OS configuration for Distributed System (Recommended)
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sapVirtualInstance = new AzureNative.Workloads.SAPVirtualInstance("sapVirtualInstance", new()
    {
        Configuration = new AzureNative.Workloads.Inputs.DeploymentWithOSConfigurationArgs
        {
            AppLocation = "eastus",
            ConfigurationType = "DeploymentWithOSConfig",
            InfrastructureConfiguration = new AzureNative.Workloads.Inputs.ThreeTierConfigurationArgs
            {
                AppResourceGroup = "X00-RG",
                ApplicationServer = new AzureNative.Workloads.Inputs.ApplicationServerConfigurationArgs
                {
                    InstanceCount = 6,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_E32ds_v4",
                    },
                },
                CentralServer = new AzureNative.Workloads.Inputs.CentralServerConfigurationArgs
                {
                    InstanceCount = 1,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_E16ds_v4",
                    },
                },
                DatabaseServer = new AzureNative.Workloads.Inputs.DatabaseConfigurationArgs
                {
                    DatabaseType = "HANA",
                    DiskConfiguration = new AzureNative.Workloads.Inputs.DiskConfigurationArgs
                    {
                        DiskVolumeConfigurations = 
                        {
                            { "backup", new AzureNative.Workloads.Inputs.DiskVolumeConfigurationArgs
                            {
                                Count = 2,
                                SizeGB = 256,
                                Sku = new AzureNative.Workloads.Inputs.DiskSkuArgs
                                {
                                    Name = "StandardSSD_LRS",
                                },
                            } },
                            { "hana/data", new AzureNative.Workloads.Inputs.DiskVolumeConfigurationArgs
                            {
                                Count = 4,
                                SizeGB = 128,
                                Sku = new AzureNative.Workloads.Inputs.DiskSkuArgs
                                {
                                    Name = "Premium_LRS",
                                },
                            } },
                            { "hana/log", new AzureNative.Workloads.Inputs.DiskVolumeConfigurationArgs
                            {
                                Count = 3,
                                SizeGB = 128,
                                Sku = new AzureNative.Workloads.Inputs.DiskSkuArgs
                                {
                                    Name = "Premium_LRS",
                                },
                            } },
                            { "hana/shared", new AzureNative.Workloads.Inputs.DiskVolumeConfigurationArgs
                            {
                                Count = 1,
                                SizeGB = 256,
                                Sku = new AzureNative.Workloads.Inputs.DiskSkuArgs
                                {
                                    Name = "StandardSSD_LRS",
                                },
                            } },
                            { "os", new AzureNative.Workloads.Inputs.DiskVolumeConfigurationArgs
                            {
                                Count = 1,
                                SizeGB = 64,
                                Sku = new AzureNative.Workloads.Inputs.DiskSkuArgs
                                {
                                    Name = "StandardSSD_LRS",
                                },
                            } },
                            { "usr/sap", new AzureNative.Workloads.Inputs.DiskVolumeConfigurationArgs
                            {
                                Count = 1,
                                SizeGB = 128,
                                Sku = new AzureNative.Workloads.Inputs.DiskSkuArgs
                                {
                                    Name = "Premium_LRS",
                                },
                            } },
                        },
                    },
                    InstanceCount = 1,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_M32ts",
                    },
                },
                DeploymentType = "ThreeTier",
            },
            OsSapConfiguration = new AzureNative.Workloads.Inputs.OsSapConfigurationArgs
            {
                SapFqdn = "xyz.test.com",
            },
        },
        Environment = "Prod",
        Location = "westcentralus",
        ResourceGroupName = "test-rg",
        SapProduct = "S4HANA",
        SapVirtualInstanceName = "X00",
        Tags = null,
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.workloads.SAPVirtualInstance;
import com.pulumi.azurenative.workloads.SAPVirtualInstanceArgs;
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
        var sapVirtualInstance = new SAPVirtualInstance("sapVirtualInstance", SAPVirtualInstanceArgs.builder()        
            .configuration(Map.ofEntries(
                Map.entry("appLocation", "eastus"),
                Map.entry("configurationType", "DeploymentWithOSConfig"),
                Map.entry("infrastructureConfiguration", Map.ofEntries(
                    Map.entry("appResourceGroup", "X00-RG"),
                    Map.entry("applicationServer", Map.ofEntries(
                        Map.entry("instanceCount", 6),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E32ds_v4")
                        ))
                    )),
                    Map.entry("centralServer", Map.ofEntries(
                        Map.entry("instanceCount", 1),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E16ds_v4")
                        ))
                    )),
                    Map.entry("databaseServer", Map.ofEntries(
                        Map.entry("databaseType", "HANA"),
                        Map.entry("diskConfiguration", Map.of("diskVolumeConfigurations", Map.ofEntries(
                            Map.entry("backup", Map.ofEntries(
                                Map.entry("count", 2),
                                Map.entry("sizeGB", 256),
                                Map.entry("sku", Map.of("name", "StandardSSD_LRS"))
                            )),
                            Map.entry("hana/data", Map.ofEntries(
                                Map.entry("count", 4),
                                Map.entry("sizeGB", 128),
                                Map.entry("sku", Map.of("name", "Premium_LRS"))
                            )),
                            Map.entry("hana/log", Map.ofEntries(
                                Map.entry("count", 3),
                                Map.entry("sizeGB", 128),
                                Map.entry("sku", Map.of("name", "Premium_LRS"))
                            )),
                            Map.entry("hana/shared", Map.ofEntries(
                                Map.entry("count", 1),
                                Map.entry("sizeGB", 256),
                                Map.entry("sku", Map.of("name", "StandardSSD_LRS"))
                            )),
                            Map.entry("os", Map.ofEntries(
                                Map.entry("count", 1),
                                Map.entry("sizeGB", 64),
                                Map.entry("sku", Map.of("name", "StandardSSD_LRS"))
                            )),
                            Map.entry("usr/sap", Map.ofEntries(
                                Map.entry("count", 1),
                                Map.entry("sizeGB", 128),
                                Map.entry("sku", Map.of("name", "Premium_LRS"))
                            ))
                        ))),
                        Map.entry("instanceCount", 1),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_M32ts")
                        ))
                    )),
                    Map.entry("deploymentType", "ThreeTier")
                )),
                Map.entry("osSapConfiguration", Map.of("sapFqdn", "xyz.test.com"))
            ))
            .environment("Prod")
            .location("westcentralus")
            .resourceGroupName("test-rg")
            .sapProduct("S4HANA")
            .sapVirtualInstanceName("X00")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sapVirtualInstance = new azure_native.workloads.SAPVirtualInstance("sapVirtualInstance", {
    configuration: {
        appLocation: "eastus",
        configurationType: "DeploymentWithOSConfig",
        infrastructureConfiguration: {
            appResourceGroup: "X00-RG",
            applicationServer: {
                instanceCount: 6,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_E32ds_v4",
                },
            },
            centralServer: {
                instanceCount: 1,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_E16ds_v4",
                },
            },
            databaseServer: {
                databaseType: "HANA",
                diskConfiguration: {
                    diskVolumeConfigurations: {
                        backup: {
                            count: 2,
                            sizeGB: 256,
                            sku: {
                                name: "StandardSSD_LRS",
                            },
                        },
                        "hana/data": {
                            count: 4,
                            sizeGB: 128,
                            sku: {
                                name: "Premium_LRS",
                            },
                        },
                        "hana/log": {
                            count: 3,
                            sizeGB: 128,
                            sku: {
                                name: "Premium_LRS",
                            },
                        },
                        "hana/shared": {
                            count: 1,
                            sizeGB: 256,
                            sku: {
                                name: "StandardSSD_LRS",
                            },
                        },
                        os: {
                            count: 1,
                            sizeGB: 64,
                            sku: {
                                name: "StandardSSD_LRS",
                            },
                        },
                        "usr/sap": {
                            count: 1,
                            sizeGB: 128,
                            sku: {
                                name: "Premium_LRS",
                            },
                        },
                    },
                },
                instanceCount: 1,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_M32ts",
                },
            },
            deploymentType: "ThreeTier",
        },
        osSapConfiguration: {
            sapFqdn: "xyz.test.com",
        },
    },
    environment: "Prod",
    location: "westcentralus",
    resourceGroupName: "test-rg",
    sapProduct: "S4HANA",
    sapVirtualInstanceName: "X00",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sap_virtual_instance = azure_native.workloads.SAPVirtualInstance("sapVirtualInstance",
    configuration=azure_native.workloads.DeploymentWithOSConfigurationArgs(
        app_location="eastus",
        configuration_type="DeploymentWithOSConfig",
        infrastructure_configuration=azure_native.workloads.ThreeTierConfigurationArgs(
            app_resource_group="X00-RG",
            application_server=azure_native.workloads.ApplicationServerConfigurationArgs(
                instance_count=6,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_E32ds_v4",
                ),
            ),
            central_server=azure_native.workloads.CentralServerConfigurationArgs(
                instance_count=1,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_E16ds_v4",
                ),
            ),
            database_server=azure_native.workloads.DatabaseConfigurationArgs(
                database_type="HANA",
                disk_configuration=azure_native.workloads.DiskConfigurationArgs(
                    disk_volume_configurations={
                        "backup": azure_native.workloads.DiskVolumeConfigurationArgs(
                            count=2,
                            size_gb=256,
                            sku=azure_native.workloads.DiskSkuArgs(
                                name="StandardSSD_LRS",
                            ),
                        ),
                        "hana/data": azure_native.workloads.DiskVolumeConfigurationArgs(
                            count=4,
                            size_gb=128,
                            sku=azure_native.workloads.DiskSkuArgs(
                                name="Premium_LRS",
                            ),
                        ),
                        "hana/log": azure_native.workloads.DiskVolumeConfigurationArgs(
                            count=3,
                            size_gb=128,
                            sku=azure_native.workloads.DiskSkuArgs(
                                name="Premium_LRS",
                            ),
                        ),
                        "hana/shared": azure_native.workloads.DiskVolumeConfigurationArgs(
                            count=1,
                            size_gb=256,
                            sku=azure_native.workloads.DiskSkuArgs(
                                name="StandardSSD_LRS",
                            ),
                        ),
                        "os": azure_native.workloads.DiskVolumeConfigurationArgs(
                            count=1,
                            size_gb=64,
                            sku=azure_native.workloads.DiskSkuArgs(
                                name="StandardSSD_LRS",
                            ),
                        ),
                        "usr/sap": azure_native.workloads.DiskVolumeConfigurationArgs(
                            count=1,
                            size_gb=128,
                            sku=azure_native.workloads.DiskSkuArgs(
                                name="Premium_LRS",
                            ),
                        ),
                    },
                ),
                instance_count=1,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_M32ts",
                ),
            ),
            deployment_type="ThreeTier",
        ),
        os_sap_configuration=azure_native.workloads.OsSapConfigurationArgs(
            sap_fqdn="xyz.test.com",
        ),
    ),
    environment="Prod",
    location="westcentralus",
    resource_group_name="test-rg",
    sap_product="S4HANA",
    sap_virtual_instance_name="X00",
    tags={})

```

```yaml
resources:
  sapVirtualInstance:
    type: azure-native:workloads:SAPVirtualInstance
    properties:
      configuration:
        appLocation: eastus
        configurationType: DeploymentWithOSConfig
        infrastructureConfiguration:
          appResourceGroup: X00-RG
          applicationServer:
            instanceCount: 6
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_E32ds_v4
          centralServer:
            instanceCount: 1
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_E16ds_v4
          databaseServer:
            databaseType: HANA
            diskConfiguration:
              diskVolumeConfigurations:
                backup:
                  count: 2
                  sizeGB: 256
                  sku:
                    name: StandardSSD_LRS
                hana/data:
                  count: 4
                  sizeGB: 128
                  sku:
                    name: Premium_LRS
                hana/log:
                  count: 3
                  sizeGB: 128
                  sku:
                    name: Premium_LRS
                hana/shared:
                  count: 1
                  sizeGB: 256
                  sku:
                    name: StandardSSD_LRS
                os:
                  count: 1
                  sizeGB: 64
                  sku:
                    name: StandardSSD_LRS
                usr/sap:
                  count: 1
                  sizeGB: 128
                  sku:
                    name: Premium_LRS
            instanceCount: 1
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_M32ts
          deploymentType: ThreeTier
        osSapConfiguration:
          sapFqdn: xyz.test.com
      environment: Prod
      location: westcentralus
      resourceGroupName: test-rg
      sapProduct: S4HANA
      sapVirtualInstanceName: X00
      tags: {}

```

{{% /example %}}
{{% example %}}
### Create Infrastructure with Disk and OS configuration for HA System with Availability Set (Recommended)
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sapVirtualInstance = new AzureNative.Workloads.SAPVirtualInstance("sapVirtualInstance", new()
    {
        Configuration = new AzureNative.Workloads.Inputs.DeploymentWithOSConfigurationArgs
        {
            AppLocation = "eastus",
            ConfigurationType = "DeploymentWithOSConfig",
            InfrastructureConfiguration = new AzureNative.Workloads.Inputs.ThreeTierConfigurationArgs
            {
                AppResourceGroup = "X00-RG",
                ApplicationServer = new AzureNative.Workloads.Inputs.ApplicationServerConfigurationArgs
                {
                    InstanceCount = 6,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_E32ds_v4",
                    },
                },
                CentralServer = new AzureNative.Workloads.Inputs.CentralServerConfigurationArgs
                {
                    InstanceCount = 2,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_E16ds_v4",
                    },
                },
                DatabaseServer = new AzureNative.Workloads.Inputs.DatabaseConfigurationArgs
                {
                    DatabaseType = "HANA",
                    DiskConfiguration = new AzureNative.Workloads.Inputs.DiskConfigurationArgs
                    {
                        DiskVolumeConfigurations = 
                        {
                            { "backup", new AzureNative.Workloads.Inputs.DiskVolumeConfigurationArgs
                            {
                                Count = 2,
                                SizeGB = 256,
                                Sku = new AzureNative.Workloads.Inputs.DiskSkuArgs
                                {
                                    Name = "StandardSSD_LRS",
                                },
                            } },
                            { "hana/data", new AzureNative.Workloads.Inputs.DiskVolumeConfigurationArgs
                            {
                                Count = 4,
                                SizeGB = 128,
                                Sku = new AzureNative.Workloads.Inputs.DiskSkuArgs
                                {
                                    Name = "Premium_LRS",
                                },
                            } },
                            { "hana/log", new AzureNative.Workloads.Inputs.DiskVolumeConfigurationArgs
                            {
                                Count = 3,
                                SizeGB = 128,
                                Sku = new AzureNative.Workloads.Inputs.DiskSkuArgs
                                {
                                    Name = "Premium_LRS",
                                },
                            } },
                            { "hana/shared", new AzureNative.Workloads.Inputs.DiskVolumeConfigurationArgs
                            {
                                Count = 1,
                                SizeGB = 256,
                                Sku = new AzureNative.Workloads.Inputs.DiskSkuArgs
                                {
                                    Name = "StandardSSD_LRS",
                                },
                            } },
                            { "os", new AzureNative.Workloads.Inputs.DiskVolumeConfigurationArgs
                            {
                                Count = 1,
                                SizeGB = 64,
                                Sku = new AzureNative.Workloads.Inputs.DiskSkuArgs
                                {
                                    Name = "StandardSSD_LRS",
                                },
                            } },
                            { "usr/sap", new AzureNative.Workloads.Inputs.DiskVolumeConfigurationArgs
                            {
                                Count = 1,
                                SizeGB = 128,
                                Sku = new AzureNative.Workloads.Inputs.DiskSkuArgs
                                {
                                    Name = "Premium_LRS",
                                },
                            } },
                        },
                    },
                    InstanceCount = 2,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_M32ts",
                    },
                },
                DeploymentType = "ThreeTier",
                HighAvailabilityConfig = new AzureNative.Workloads.Inputs.HighAvailabilityConfigurationArgs
                {
                    HighAvailabilityType = "AvailabilitySet",
                },
            },
            OsSapConfiguration = new AzureNative.Workloads.Inputs.OsSapConfigurationArgs
            {
                SapFqdn = "xyz.test.com",
            },
        },
        Environment = "Prod",
        Location = "westcentralus",
        ResourceGroupName = "test-rg",
        SapProduct = "S4HANA",
        SapVirtualInstanceName = "X00",
        Tags = null,
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.workloads.SAPVirtualInstance;
import com.pulumi.azurenative.workloads.SAPVirtualInstanceArgs;
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
        var sapVirtualInstance = new SAPVirtualInstance("sapVirtualInstance", SAPVirtualInstanceArgs.builder()        
            .configuration(Map.ofEntries(
                Map.entry("appLocation", "eastus"),
                Map.entry("configurationType", "DeploymentWithOSConfig"),
                Map.entry("infrastructureConfiguration", Map.ofEntries(
                    Map.entry("appResourceGroup", "X00-RG"),
                    Map.entry("applicationServer", Map.ofEntries(
                        Map.entry("instanceCount", 6),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E32ds_v4")
                        ))
                    )),
                    Map.entry("centralServer", Map.ofEntries(
                        Map.entry("instanceCount", 2),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E16ds_v4")
                        ))
                    )),
                    Map.entry("databaseServer", Map.ofEntries(
                        Map.entry("databaseType", "HANA"),
                        Map.entry("diskConfiguration", Map.of("diskVolumeConfigurations", Map.ofEntries(
                            Map.entry("backup", Map.ofEntries(
                                Map.entry("count", 2),
                                Map.entry("sizeGB", 256),
                                Map.entry("sku", Map.of("name", "StandardSSD_LRS"))
                            )),
                            Map.entry("hana/data", Map.ofEntries(
                                Map.entry("count", 4),
                                Map.entry("sizeGB", 128),
                                Map.entry("sku", Map.of("name", "Premium_LRS"))
                            )),
                            Map.entry("hana/log", Map.ofEntries(
                                Map.entry("count", 3),
                                Map.entry("sizeGB", 128),
                                Map.entry("sku", Map.of("name", "Premium_LRS"))
                            )),
                            Map.entry("hana/shared", Map.ofEntries(
                                Map.entry("count", 1),
                                Map.entry("sizeGB", 256),
                                Map.entry("sku", Map.of("name", "StandardSSD_LRS"))
                            )),
                            Map.entry("os", Map.ofEntries(
                                Map.entry("count", 1),
                                Map.entry("sizeGB", 64),
                                Map.entry("sku", Map.of("name", "StandardSSD_LRS"))
                            )),
                            Map.entry("usr/sap", Map.ofEntries(
                                Map.entry("count", 1),
                                Map.entry("sizeGB", 128),
                                Map.entry("sku", Map.of("name", "Premium_LRS"))
                            ))
                        ))),
                        Map.entry("instanceCount", 2),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_M32ts")
                        ))
                    )),
                    Map.entry("deploymentType", "ThreeTier"),
                    Map.entry("highAvailabilityConfig", Map.of("highAvailabilityType", "AvailabilitySet"))
                )),
                Map.entry("osSapConfiguration", Map.of("sapFqdn", "xyz.test.com"))
            ))
            .environment("Prod")
            .location("westcentralus")
            .resourceGroupName("test-rg")
            .sapProduct("S4HANA")
            .sapVirtualInstanceName("X00")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sapVirtualInstance = new azure_native.workloads.SAPVirtualInstance("sapVirtualInstance", {
    configuration: {
        appLocation: "eastus",
        configurationType: "DeploymentWithOSConfig",
        infrastructureConfiguration: {
            appResourceGroup: "X00-RG",
            applicationServer: {
                instanceCount: 6,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_E32ds_v4",
                },
            },
            centralServer: {
                instanceCount: 2,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_E16ds_v4",
                },
            },
            databaseServer: {
                databaseType: "HANA",
                diskConfiguration: {
                    diskVolumeConfigurations: {
                        backup: {
                            count: 2,
                            sizeGB: 256,
                            sku: {
                                name: "StandardSSD_LRS",
                            },
                        },
                        "hana/data": {
                            count: 4,
                            sizeGB: 128,
                            sku: {
                                name: "Premium_LRS",
                            },
                        },
                        "hana/log": {
                            count: 3,
                            sizeGB: 128,
                            sku: {
                                name: "Premium_LRS",
                            },
                        },
                        "hana/shared": {
                            count: 1,
                            sizeGB: 256,
                            sku: {
                                name: "StandardSSD_LRS",
                            },
                        },
                        os: {
                            count: 1,
                            sizeGB: 64,
                            sku: {
                                name: "StandardSSD_LRS",
                            },
                        },
                        "usr/sap": {
                            count: 1,
                            sizeGB: 128,
                            sku: {
                                name: "Premium_LRS",
                            },
                        },
                    },
                },
                instanceCount: 2,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_M32ts",
                },
            },
            deploymentType: "ThreeTier",
            highAvailabilityConfig: {
                highAvailabilityType: "AvailabilitySet",
            },
        },
        osSapConfiguration: {
            sapFqdn: "xyz.test.com",
        },
    },
    environment: "Prod",
    location: "westcentralus",
    resourceGroupName: "test-rg",
    sapProduct: "S4HANA",
    sapVirtualInstanceName: "X00",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sap_virtual_instance = azure_native.workloads.SAPVirtualInstance("sapVirtualInstance",
    configuration=azure_native.workloads.DeploymentWithOSConfigurationArgs(
        app_location="eastus",
        configuration_type="DeploymentWithOSConfig",
        infrastructure_configuration=azure_native.workloads.ThreeTierConfigurationArgs(
            app_resource_group="X00-RG",
            application_server=azure_native.workloads.ApplicationServerConfigurationArgs(
                instance_count=6,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_E32ds_v4",
                ),
            ),
            central_server=azure_native.workloads.CentralServerConfigurationArgs(
                instance_count=2,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_E16ds_v4",
                ),
            ),
            database_server=azure_native.workloads.DatabaseConfigurationArgs(
                database_type="HANA",
                disk_configuration=azure_native.workloads.DiskConfigurationArgs(
                    disk_volume_configurations={
                        "backup": azure_native.workloads.DiskVolumeConfigurationArgs(
                            count=2,
                            size_gb=256,
                            sku=azure_native.workloads.DiskSkuArgs(
                                name="StandardSSD_LRS",
                            ),
                        ),
                        "hana/data": azure_native.workloads.DiskVolumeConfigurationArgs(
                            count=4,
                            size_gb=128,
                            sku=azure_native.workloads.DiskSkuArgs(
                                name="Premium_LRS",
                            ),
                        ),
                        "hana/log": azure_native.workloads.DiskVolumeConfigurationArgs(
                            count=3,
                            size_gb=128,
                            sku=azure_native.workloads.DiskSkuArgs(
                                name="Premium_LRS",
                            ),
                        ),
                        "hana/shared": azure_native.workloads.DiskVolumeConfigurationArgs(
                            count=1,
                            size_gb=256,
                            sku=azure_native.workloads.DiskSkuArgs(
                                name="StandardSSD_LRS",
                            ),
                        ),
                        "os": azure_native.workloads.DiskVolumeConfigurationArgs(
                            count=1,
                            size_gb=64,
                            sku=azure_native.workloads.DiskSkuArgs(
                                name="StandardSSD_LRS",
                            ),
                        ),
                        "usr/sap": azure_native.workloads.DiskVolumeConfigurationArgs(
                            count=1,
                            size_gb=128,
                            sku=azure_native.workloads.DiskSkuArgs(
                                name="Premium_LRS",
                            ),
                        ),
                    },
                ),
                instance_count=2,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_M32ts",
                ),
            ),
            deployment_type="ThreeTier",
            high_availability_config=azure_native.workloads.HighAvailabilityConfigurationArgs(
                high_availability_type="AvailabilitySet",
            ),
        ),
        os_sap_configuration=azure_native.workloads.OsSapConfigurationArgs(
            sap_fqdn="xyz.test.com",
        ),
    ),
    environment="Prod",
    location="westcentralus",
    resource_group_name="test-rg",
    sap_product="S4HANA",
    sap_virtual_instance_name="X00",
    tags={})

```

```yaml
resources:
  sapVirtualInstance:
    type: azure-native:workloads:SAPVirtualInstance
    properties:
      configuration:
        appLocation: eastus
        configurationType: DeploymentWithOSConfig
        infrastructureConfiguration:
          appResourceGroup: X00-RG
          applicationServer:
            instanceCount: 6
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_E32ds_v4
          centralServer:
            instanceCount: 2
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_E16ds_v4
          databaseServer:
            databaseType: HANA
            diskConfiguration:
              diskVolumeConfigurations:
                backup:
                  count: 2
                  sizeGB: 256
                  sku:
                    name: StandardSSD_LRS
                hana/data:
                  count: 4
                  sizeGB: 128
                  sku:
                    name: Premium_LRS
                hana/log:
                  count: 3
                  sizeGB: 128
                  sku:
                    name: Premium_LRS
                hana/shared:
                  count: 1
                  sizeGB: 256
                  sku:
                    name: StandardSSD_LRS
                os:
                  count: 1
                  sizeGB: 64
                  sku:
                    name: StandardSSD_LRS
                usr/sap:
                  count: 1
                  sizeGB: 128
                  sku:
                    name: Premium_LRS
            instanceCount: 2
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_M32ts
          deploymentType: ThreeTier
          highAvailabilityConfig:
            highAvailabilityType: AvailabilitySet
        osSapConfiguration:
          sapFqdn: xyz.test.com
      environment: Prod
      location: westcentralus
      resourceGroupName: test-rg
      sapProduct: S4HANA
      sapVirtualInstanceName: X00
      tags: {}

```

{{% /example %}}
{{% example %}}
### Create Infrastructure with Disk and OS configuration for HA System with Availability Zone (Recommended)
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sapVirtualInstance = new AzureNative.Workloads.SAPVirtualInstance("sapVirtualInstance", new()
    {
        Configuration = new AzureNative.Workloads.Inputs.DeploymentWithOSConfigurationArgs
        {
            AppLocation = "eastus",
            ConfigurationType = "DeploymentWithOSConfig",
            InfrastructureConfiguration = new AzureNative.Workloads.Inputs.ThreeTierConfigurationArgs
            {
                AppResourceGroup = "X00-RG",
                ApplicationServer = new AzureNative.Workloads.Inputs.ApplicationServerConfigurationArgs
                {
                    InstanceCount = 6,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_E32ds_v4",
                    },
                },
                CentralServer = new AzureNative.Workloads.Inputs.CentralServerConfigurationArgs
                {
                    InstanceCount = 2,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_E16ds_v4",
                    },
                },
                DatabaseServer = new AzureNative.Workloads.Inputs.DatabaseConfigurationArgs
                {
                    DatabaseType = "HANA",
                    DiskConfiguration = new AzureNative.Workloads.Inputs.DiskConfigurationArgs
                    {
                        DiskVolumeConfigurations = 
                        {
                            { "backup", new AzureNative.Workloads.Inputs.DiskVolumeConfigurationArgs
                            {
                                Count = 2,
                                SizeGB = 256,
                                Sku = new AzureNative.Workloads.Inputs.DiskSkuArgs
                                {
                                    Name = "StandardSSD_LRS",
                                },
                            } },
                            { "hana/data", new AzureNative.Workloads.Inputs.DiskVolumeConfigurationArgs
                            {
                                Count = 4,
                                SizeGB = 128,
                                Sku = new AzureNative.Workloads.Inputs.DiskSkuArgs
                                {
                                    Name = "Premium_LRS",
                                },
                            } },
                            { "hana/log", new AzureNative.Workloads.Inputs.DiskVolumeConfigurationArgs
                            {
                                Count = 3,
                                SizeGB = 128,
                                Sku = new AzureNative.Workloads.Inputs.DiskSkuArgs
                                {
                                    Name = "Premium_LRS",
                                },
                            } },
                            { "hana/shared", new AzureNative.Workloads.Inputs.DiskVolumeConfigurationArgs
                            {
                                Count = 1,
                                SizeGB = 256,
                                Sku = new AzureNative.Workloads.Inputs.DiskSkuArgs
                                {
                                    Name = "StandardSSD_LRS",
                                },
                            } },
                            { "os", new AzureNative.Workloads.Inputs.DiskVolumeConfigurationArgs
                            {
                                Count = 1,
                                SizeGB = 64,
                                Sku = new AzureNative.Workloads.Inputs.DiskSkuArgs
                                {
                                    Name = "StandardSSD_LRS",
                                },
                            } },
                            { "usr/sap", new AzureNative.Workloads.Inputs.DiskVolumeConfigurationArgs
                            {
                                Count = 1,
                                SizeGB = 128,
                                Sku = new AzureNative.Workloads.Inputs.DiskSkuArgs
                                {
                                    Name = "Premium_LRS",
                                },
                            } },
                        },
                    },
                    InstanceCount = 2,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_M32ts",
                    },
                },
                DeploymentType = "ThreeTier",
                HighAvailabilityConfig = new AzureNative.Workloads.Inputs.HighAvailabilityConfigurationArgs
                {
                    HighAvailabilityType = "AvailabilityZone",
                },
            },
            OsSapConfiguration = new AzureNative.Workloads.Inputs.OsSapConfigurationArgs
            {
                SapFqdn = "xyz.test.com",
            },
        },
        Environment = "Prod",
        Location = "westcentralus",
        ResourceGroupName = "test-rg",
        SapProduct = "S4HANA",
        SapVirtualInstanceName = "X00",
        Tags = null,
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.workloads.SAPVirtualInstance;
import com.pulumi.azurenative.workloads.SAPVirtualInstanceArgs;
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
        var sapVirtualInstance = new SAPVirtualInstance("sapVirtualInstance", SAPVirtualInstanceArgs.builder()        
            .configuration(Map.ofEntries(
                Map.entry("appLocation", "eastus"),
                Map.entry("configurationType", "DeploymentWithOSConfig"),
                Map.entry("infrastructureConfiguration", Map.ofEntries(
                    Map.entry("appResourceGroup", "X00-RG"),
                    Map.entry("applicationServer", Map.ofEntries(
                        Map.entry("instanceCount", 6),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E32ds_v4")
                        ))
                    )),
                    Map.entry("centralServer", Map.ofEntries(
                        Map.entry("instanceCount", 2),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E16ds_v4")
                        ))
                    )),
                    Map.entry("databaseServer", Map.ofEntries(
                        Map.entry("databaseType", "HANA"),
                        Map.entry("diskConfiguration", Map.of("diskVolumeConfigurations", Map.ofEntries(
                            Map.entry("backup", Map.ofEntries(
                                Map.entry("count", 2),
                                Map.entry("sizeGB", 256),
                                Map.entry("sku", Map.of("name", "StandardSSD_LRS"))
                            )),
                            Map.entry("hana/data", Map.ofEntries(
                                Map.entry("count", 4),
                                Map.entry("sizeGB", 128),
                                Map.entry("sku", Map.of("name", "Premium_LRS"))
                            )),
                            Map.entry("hana/log", Map.ofEntries(
                                Map.entry("count", 3),
                                Map.entry("sizeGB", 128),
                                Map.entry("sku", Map.of("name", "Premium_LRS"))
                            )),
                            Map.entry("hana/shared", Map.ofEntries(
                                Map.entry("count", 1),
                                Map.entry("sizeGB", 256),
                                Map.entry("sku", Map.of("name", "StandardSSD_LRS"))
                            )),
                            Map.entry("os", Map.ofEntries(
                                Map.entry("count", 1),
                                Map.entry("sizeGB", 64),
                                Map.entry("sku", Map.of("name", "StandardSSD_LRS"))
                            )),
                            Map.entry("usr/sap", Map.ofEntries(
                                Map.entry("count", 1),
                                Map.entry("sizeGB", 128),
                                Map.entry("sku", Map.of("name", "Premium_LRS"))
                            ))
                        ))),
                        Map.entry("instanceCount", 2),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_M32ts")
                        ))
                    )),
                    Map.entry("deploymentType", "ThreeTier"),
                    Map.entry("highAvailabilityConfig", Map.of("highAvailabilityType", "AvailabilityZone"))
                )),
                Map.entry("osSapConfiguration", Map.of("sapFqdn", "xyz.test.com"))
            ))
            .environment("Prod")
            .location("westcentralus")
            .resourceGroupName("test-rg")
            .sapProduct("S4HANA")
            .sapVirtualInstanceName("X00")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sapVirtualInstance = new azure_native.workloads.SAPVirtualInstance("sapVirtualInstance", {
    configuration: {
        appLocation: "eastus",
        configurationType: "DeploymentWithOSConfig",
        infrastructureConfiguration: {
            appResourceGroup: "X00-RG",
            applicationServer: {
                instanceCount: 6,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_E32ds_v4",
                },
            },
            centralServer: {
                instanceCount: 2,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_E16ds_v4",
                },
            },
            databaseServer: {
                databaseType: "HANA",
                diskConfiguration: {
                    diskVolumeConfigurations: {
                        backup: {
                            count: 2,
                            sizeGB: 256,
                            sku: {
                                name: "StandardSSD_LRS",
                            },
                        },
                        "hana/data": {
                            count: 4,
                            sizeGB: 128,
                            sku: {
                                name: "Premium_LRS",
                            },
                        },
                        "hana/log": {
                            count: 3,
                            sizeGB: 128,
                            sku: {
                                name: "Premium_LRS",
                            },
                        },
                        "hana/shared": {
                            count: 1,
                            sizeGB: 256,
                            sku: {
                                name: "StandardSSD_LRS",
                            },
                        },
                        os: {
                            count: 1,
                            sizeGB: 64,
                            sku: {
                                name: "StandardSSD_LRS",
                            },
                        },
                        "usr/sap": {
                            count: 1,
                            sizeGB: 128,
                            sku: {
                                name: "Premium_LRS",
                            },
                        },
                    },
                },
                instanceCount: 2,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_M32ts",
                },
            },
            deploymentType: "ThreeTier",
            highAvailabilityConfig: {
                highAvailabilityType: "AvailabilityZone",
            },
        },
        osSapConfiguration: {
            sapFqdn: "xyz.test.com",
        },
    },
    environment: "Prod",
    location: "westcentralus",
    resourceGroupName: "test-rg",
    sapProduct: "S4HANA",
    sapVirtualInstanceName: "X00",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sap_virtual_instance = azure_native.workloads.SAPVirtualInstance("sapVirtualInstance",
    configuration=azure_native.workloads.DeploymentWithOSConfigurationArgs(
        app_location="eastus",
        configuration_type="DeploymentWithOSConfig",
        infrastructure_configuration=azure_native.workloads.ThreeTierConfigurationArgs(
            app_resource_group="X00-RG",
            application_server=azure_native.workloads.ApplicationServerConfigurationArgs(
                instance_count=6,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_E32ds_v4",
                ),
            ),
            central_server=azure_native.workloads.CentralServerConfigurationArgs(
                instance_count=2,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_E16ds_v4",
                ),
            ),
            database_server=azure_native.workloads.DatabaseConfigurationArgs(
                database_type="HANA",
                disk_configuration=azure_native.workloads.DiskConfigurationArgs(
                    disk_volume_configurations={
                        "backup": azure_native.workloads.DiskVolumeConfigurationArgs(
                            count=2,
                            size_gb=256,
                            sku=azure_native.workloads.DiskSkuArgs(
                                name="StandardSSD_LRS",
                            ),
                        ),
                        "hana/data": azure_native.workloads.DiskVolumeConfigurationArgs(
                            count=4,
                            size_gb=128,
                            sku=azure_native.workloads.DiskSkuArgs(
                                name="Premium_LRS",
                            ),
                        ),
                        "hana/log": azure_native.workloads.DiskVolumeConfigurationArgs(
                            count=3,
                            size_gb=128,
                            sku=azure_native.workloads.DiskSkuArgs(
                                name="Premium_LRS",
                            ),
                        ),
                        "hana/shared": azure_native.workloads.DiskVolumeConfigurationArgs(
                            count=1,
                            size_gb=256,
                            sku=azure_native.workloads.DiskSkuArgs(
                                name="StandardSSD_LRS",
                            ),
                        ),
                        "os": azure_native.workloads.DiskVolumeConfigurationArgs(
                            count=1,
                            size_gb=64,
                            sku=azure_native.workloads.DiskSkuArgs(
                                name="StandardSSD_LRS",
                            ),
                        ),
                        "usr/sap": azure_native.workloads.DiskVolumeConfigurationArgs(
                            count=1,
                            size_gb=128,
                            sku=azure_native.workloads.DiskSkuArgs(
                                name="Premium_LRS",
                            ),
                        ),
                    },
                ),
                instance_count=2,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_M32ts",
                ),
            ),
            deployment_type="ThreeTier",
            high_availability_config=azure_native.workloads.HighAvailabilityConfigurationArgs(
                high_availability_type="AvailabilityZone",
            ),
        ),
        os_sap_configuration=azure_native.workloads.OsSapConfigurationArgs(
            sap_fqdn="xyz.test.com",
        ),
    ),
    environment="Prod",
    location="westcentralus",
    resource_group_name="test-rg",
    sap_product="S4HANA",
    sap_virtual_instance_name="X00",
    tags={})

```

```yaml
resources:
  sapVirtualInstance:
    type: azure-native:workloads:SAPVirtualInstance
    properties:
      configuration:
        appLocation: eastus
        configurationType: DeploymentWithOSConfig
        infrastructureConfiguration:
          appResourceGroup: X00-RG
          applicationServer:
            instanceCount: 6
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_E32ds_v4
          centralServer:
            instanceCount: 2
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_E16ds_v4
          databaseServer:
            databaseType: HANA
            diskConfiguration:
              diskVolumeConfigurations:
                backup:
                  count: 2
                  sizeGB: 256
                  sku:
                    name: StandardSSD_LRS
                hana/data:
                  count: 4
                  sizeGB: 128
                  sku:
                    name: Premium_LRS
                hana/log:
                  count: 3
                  sizeGB: 128
                  sku:
                    name: Premium_LRS
                hana/shared:
                  count: 1
                  sizeGB: 256
                  sku:
                    name: StandardSSD_LRS
                os:
                  count: 1
                  sizeGB: 64
                  sku:
                    name: StandardSSD_LRS
                usr/sap:
                  count: 1
                  sizeGB: 128
                  sku:
                    name: Premium_LRS
            instanceCount: 2
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_M32ts
          deploymentType: ThreeTier
          highAvailabilityConfig:
            highAvailabilityType: AvailabilityZone
        osSapConfiguration:
          sapFqdn: xyz.test.com
      environment: Prod
      location: westcentralus
      resourceGroupName: test-rg
      sapProduct: S4HANA
      sapVirtualInstanceName: X00
      tags: {}

```

{{% /example %}}
{{% example %}}
### Create Infrastructure with Disk and OS configurations for Single Server System (Recommended)
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sapVirtualInstance = new AzureNative.Workloads.SAPVirtualInstance("sapVirtualInstance", new()
    {
        Configuration = new AzureNative.Workloads.Inputs.DeploymentWithOSConfigurationArgs
        {
            AppLocation = "eastus",
            ConfigurationType = "DeploymentWithOSConfig",
            InfrastructureConfiguration = new AzureNative.Workloads.Inputs.SingleServerConfigurationArgs
            {
                AppResourceGroup = "X00-RG",
                DatabaseType = "HANA",
                DbDiskConfiguration = new AzureNative.Workloads.Inputs.DiskConfigurationArgs
                {
                    DiskVolumeConfigurations = 
                    {
                        { "backup", new AzureNative.Workloads.Inputs.DiskVolumeConfigurationArgs
                        {
                            Count = 2,
                            SizeGB = 256,
                            Sku = new AzureNative.Workloads.Inputs.DiskSkuArgs
                            {
                                Name = "StandardSSD_LRS",
                            },
                        } },
                        { "hana/data", new AzureNative.Workloads.Inputs.DiskVolumeConfigurationArgs
                        {
                            Count = 4,
                            SizeGB = 128,
                            Sku = new AzureNative.Workloads.Inputs.DiskSkuArgs
                            {
                                Name = "Premium_LRS",
                            },
                        } },
                        { "hana/log", new AzureNative.Workloads.Inputs.DiskVolumeConfigurationArgs
                        {
                            Count = 3,
                            SizeGB = 128,
                            Sku = new AzureNative.Workloads.Inputs.DiskSkuArgs
                            {
                                Name = "Premium_LRS",
                            },
                        } },
                        { "hana/shared", new AzureNative.Workloads.Inputs.DiskVolumeConfigurationArgs
                        {
                            Count = 1,
                            SizeGB = 256,
                            Sku = new AzureNative.Workloads.Inputs.DiskSkuArgs
                            {
                                Name = "StandardSSD_LRS",
                            },
                        } },
                        { "os", new AzureNative.Workloads.Inputs.DiskVolumeConfigurationArgs
                        {
                            Count = 1,
                            SizeGB = 64,
                            Sku = new AzureNative.Workloads.Inputs.DiskSkuArgs
                            {
                                Name = "StandardSSD_LRS",
                            },
                        } },
                        { "usr/sap", new AzureNative.Workloads.Inputs.DiskVolumeConfigurationArgs
                        {
                            Count = 1,
                            SizeGB = 128,
                            Sku = new AzureNative.Workloads.Inputs.DiskSkuArgs
                            {
                                Name = "Premium_LRS",
                            },
                        } },
                    },
                },
                DeploymentType = "SingleServer",
                NetworkConfiguration = new AzureNative.Workloads.Inputs.NetworkConfigurationArgs
                {
                    IsSecondaryIpEnabled = true,
                },
                SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                {
                    ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                    {
                        Offer = "RHEL-SAP",
                        Publisher = "RedHat",
                        Sku = "84sapha-gen2",
                        Version = "latest",
                    },
                    OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                    {
                        AdminUsername = "{your-username}",
                        OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                        {
                            DisablePasswordAuthentication = true,
                            OsType = "Linux",
                            SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                            {
                                PrivateKey = "xyz",
                                PublicKey = "abc",
                            },
                        },
                    },
                    VmSize = "Standard_E32ds_v4",
                },
            },
            OsSapConfiguration = new AzureNative.Workloads.Inputs.OsSapConfigurationArgs
            {
                SapFqdn = "xyz.test.com",
            },
        },
        Environment = "NonProd",
        Location = "westcentralus",
        ResourceGroupName = "test-rg",
        SapProduct = "S4HANA",
        SapVirtualInstanceName = "X00",
        Tags = null,
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.workloads.SAPVirtualInstance;
import com.pulumi.azurenative.workloads.SAPVirtualInstanceArgs;
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
        var sapVirtualInstance = new SAPVirtualInstance("sapVirtualInstance", SAPVirtualInstanceArgs.builder()        
            .configuration(Map.ofEntries(
                Map.entry("appLocation", "eastus"),
                Map.entry("configurationType", "DeploymentWithOSConfig"),
                Map.entry("infrastructureConfiguration", Map.ofEntries(
                    Map.entry("appResourceGroup", "X00-RG"),
                    Map.entry("databaseType", "HANA"),
                    Map.entry("dbDiskConfiguration", Map.of("diskVolumeConfigurations", Map.ofEntries(
                        Map.entry("backup", Map.ofEntries(
                            Map.entry("count", 2),
                            Map.entry("sizeGB", 256),
                            Map.entry("sku", Map.of("name", "StandardSSD_LRS"))
                        )),
                        Map.entry("hana/data", Map.ofEntries(
                            Map.entry("count", 4),
                            Map.entry("sizeGB", 128),
                            Map.entry("sku", Map.of("name", "Premium_LRS"))
                        )),
                        Map.entry("hana/log", Map.ofEntries(
                            Map.entry("count", 3),
                            Map.entry("sizeGB", 128),
                            Map.entry("sku", Map.of("name", "Premium_LRS"))
                        )),
                        Map.entry("hana/shared", Map.ofEntries(
                            Map.entry("count", 1),
                            Map.entry("sizeGB", 256),
                            Map.entry("sku", Map.of("name", "StandardSSD_LRS"))
                        )),
                        Map.entry("os", Map.ofEntries(
                            Map.entry("count", 1),
                            Map.entry("sizeGB", 64),
                            Map.entry("sku", Map.of("name", "StandardSSD_LRS"))
                        )),
                        Map.entry("usr/sap", Map.ofEntries(
                            Map.entry("count", 1),
                            Map.entry("sizeGB", 128),
                            Map.entry("sku", Map.of("name", "Premium_LRS"))
                        ))
                    ))),
                    Map.entry("deploymentType", "SingleServer"),
                    Map.entry("networkConfiguration", Map.of("isSecondaryIpEnabled", true)),
                    Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                    Map.entry("virtualMachineConfiguration", Map.ofEntries(
                        Map.entry("imageReference", Map.ofEntries(
                            Map.entry("offer", "RHEL-SAP"),
                            Map.entry("publisher", "RedHat"),
                            Map.entry("sku", "84sapha-gen2"),
                            Map.entry("version", "latest")
                        )),
                        Map.entry("osProfile", Map.ofEntries(
                            Map.entry("adminUsername", "{your-username}"),
                            Map.entry("osConfiguration", Map.ofEntries(
                                Map.entry("disablePasswordAuthentication", true),
                                Map.entry("osType", "Linux"),
                                Map.entry("sshKeyPair", Map.ofEntries(
                                    Map.entry("privateKey", "xyz"),
                                    Map.entry("publicKey", "abc")
                                ))
                            ))
                        )),
                        Map.entry("vmSize", "Standard_E32ds_v4")
                    ))
                )),
                Map.entry("osSapConfiguration", Map.of("sapFqdn", "xyz.test.com"))
            ))
            .environment("NonProd")
            .location("westcentralus")
            .resourceGroupName("test-rg")
            .sapProduct("S4HANA")
            .sapVirtualInstanceName("X00")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sapVirtualInstance = new azure_native.workloads.SAPVirtualInstance("sapVirtualInstance", {
    configuration: {
        appLocation: "eastus",
        configurationType: "DeploymentWithOSConfig",
        infrastructureConfiguration: {
            appResourceGroup: "X00-RG",
            databaseType: "HANA",
            dbDiskConfiguration: {
                diskVolumeConfigurations: {
                    backup: {
                        count: 2,
                        sizeGB: 256,
                        sku: {
                            name: "StandardSSD_LRS",
                        },
                    },
                    "hana/data": {
                        count: 4,
                        sizeGB: 128,
                        sku: {
                            name: "Premium_LRS",
                        },
                    },
                    "hana/log": {
                        count: 3,
                        sizeGB: 128,
                        sku: {
                            name: "Premium_LRS",
                        },
                    },
                    "hana/shared": {
                        count: 1,
                        sizeGB: 256,
                        sku: {
                            name: "StandardSSD_LRS",
                        },
                    },
                    os: {
                        count: 1,
                        sizeGB: 64,
                        sku: {
                            name: "StandardSSD_LRS",
                        },
                    },
                    "usr/sap": {
                        count: 1,
                        sizeGB: 128,
                        sku: {
                            name: "Premium_LRS",
                        },
                    },
                },
            },
            deploymentType: "SingleServer",
            networkConfiguration: {
                isSecondaryIpEnabled: true,
            },
            subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
            virtualMachineConfiguration: {
                imageReference: {
                    offer: "RHEL-SAP",
                    publisher: "RedHat",
                    sku: "84sapha-gen2",
                    version: "latest",
                },
                osProfile: {
                    adminUsername: "{your-username}",
                    osConfiguration: {
                        disablePasswordAuthentication: true,
                        osType: "Linux",
                        sshKeyPair: {
                            privateKey: "xyz",
                            publicKey: "abc",
                        },
                    },
                },
                vmSize: "Standard_E32ds_v4",
            },
        },
        osSapConfiguration: {
            sapFqdn: "xyz.test.com",
        },
    },
    environment: "NonProd",
    location: "westcentralus",
    resourceGroupName: "test-rg",
    sapProduct: "S4HANA",
    sapVirtualInstanceName: "X00",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sap_virtual_instance = azure_native.workloads.SAPVirtualInstance("sapVirtualInstance",
    configuration=azure_native.workloads.DeploymentWithOSConfigurationArgs(
        app_location="eastus",
        configuration_type="DeploymentWithOSConfig",
        infrastructure_configuration=azure_native.workloads.SingleServerConfigurationArgs(
            app_resource_group="X00-RG",
            database_type="HANA",
            db_disk_configuration=azure_native.workloads.DiskConfigurationArgs(
                disk_volume_configurations={
                    "backup": azure_native.workloads.DiskVolumeConfigurationArgs(
                        count=2,
                        size_gb=256,
                        sku=azure_native.workloads.DiskSkuArgs(
                            name="StandardSSD_LRS",
                        ),
                    ),
                    "hana/data": azure_native.workloads.DiskVolumeConfigurationArgs(
                        count=4,
                        size_gb=128,
                        sku=azure_native.workloads.DiskSkuArgs(
                            name="Premium_LRS",
                        ),
                    ),
                    "hana/log": azure_native.workloads.DiskVolumeConfigurationArgs(
                        count=3,
                        size_gb=128,
                        sku=azure_native.workloads.DiskSkuArgs(
                            name="Premium_LRS",
                        ),
                    ),
                    "hana/shared": azure_native.workloads.DiskVolumeConfigurationArgs(
                        count=1,
                        size_gb=256,
                        sku=azure_native.workloads.DiskSkuArgs(
                            name="StandardSSD_LRS",
                        ),
                    ),
                    "os": azure_native.workloads.DiskVolumeConfigurationArgs(
                        count=1,
                        size_gb=64,
                        sku=azure_native.workloads.DiskSkuArgs(
                            name="StandardSSD_LRS",
                        ),
                    ),
                    "usr/sap": azure_native.workloads.DiskVolumeConfigurationArgs(
                        count=1,
                        size_gb=128,
                        sku=azure_native.workloads.DiskSkuArgs(
                            name="Premium_LRS",
                        ),
                    ),
                },
            ),
            deployment_type="SingleServer",
            network_configuration=azure_native.workloads.NetworkConfigurationArgs(
                is_secondary_ip_enabled=True,
            ),
            subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
            virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                image_reference=azure_native.workloads.ImageReferenceArgs(
                    offer="RHEL-SAP",
                    publisher="RedHat",
                    sku="84sapha-gen2",
                    version="latest",
                ),
                os_profile=azure_native.workloads.OSProfileArgs(
                    admin_username="{your-username}",
                    os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                        disable_password_authentication=True,
                        os_type="Linux",
                        ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                            private_key="xyz",
                            public_key="abc",
                        ),
                    ),
                ),
                vm_size="Standard_E32ds_v4",
            ),
        ),
        os_sap_configuration=azure_native.workloads.OsSapConfigurationArgs(
            sap_fqdn="xyz.test.com",
        ),
    ),
    environment="NonProd",
    location="westcentralus",
    resource_group_name="test-rg",
    sap_product="S4HANA",
    sap_virtual_instance_name="X00",
    tags={})

```

```yaml
resources:
  sapVirtualInstance:
    type: azure-native:workloads:SAPVirtualInstance
    properties:
      configuration:
        appLocation: eastus
        configurationType: DeploymentWithOSConfig
        infrastructureConfiguration:
          appResourceGroup: X00-RG
          databaseType: HANA
          dbDiskConfiguration:
            diskVolumeConfigurations:
              backup:
                count: 2
                sizeGB: 256
                sku:
                  name: StandardSSD_LRS
              hana/data:
                count: 4
                sizeGB: 128
                sku:
                  name: Premium_LRS
              hana/log:
                count: 3
                sizeGB: 128
                sku:
                  name: Premium_LRS
              hana/shared:
                count: 1
                sizeGB: 256
                sku:
                  name: StandardSSD_LRS
              os:
                count: 1
                sizeGB: 64
                sku:
                  name: StandardSSD_LRS
              usr/sap:
                count: 1
                sizeGB: 128
                sku:
                  name: Premium_LRS
          deploymentType: SingleServer
          networkConfiguration:
            isSecondaryIpEnabled: true
          subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/dindurkhya-e2etesting/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
          virtualMachineConfiguration:
            imageReference:
              offer: RHEL-SAP
              publisher: RedHat
              sku: 84sapha-gen2
              version: latest
            osProfile:
              adminUsername: '{your-username}'
              osConfiguration:
                disablePasswordAuthentication: true
                osType: Linux
                sshKeyPair:
                  privateKey: xyz
                  publicKey: abc
            vmSize: Standard_E32ds_v4
        osSapConfiguration:
          sapFqdn: xyz.test.com
      environment: NonProd
      location: westcentralus
      resourceGroupName: test-rg
      sapProduct: S4HANA
      sapVirtualInstanceName: X00
      tags: {}

```

{{% /example %}}
{{% example %}}
### Create Infrastructure with OS configuration for Distributed System (Recommended)
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sapVirtualInstance = new AzureNative.Workloads.SAPVirtualInstance("sapVirtualInstance", new()
    {
        Configuration = new AzureNative.Workloads.Inputs.DeploymentWithOSConfigurationArgs
        {
            AppLocation = "eastus",
            ConfigurationType = "DeploymentWithOSConfig",
            InfrastructureConfiguration = new AzureNative.Workloads.Inputs.ThreeTierConfigurationArgs
            {
                AppResourceGroup = "X00-RG",
                ApplicationServer = new AzureNative.Workloads.Inputs.ApplicationServerConfigurationArgs
                {
                    InstanceCount = 6,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_E32ds_v4",
                    },
                },
                CentralServer = new AzureNative.Workloads.Inputs.CentralServerConfigurationArgs
                {
                    InstanceCount = 1,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_E16ds_v4",
                    },
                },
                DatabaseServer = new AzureNative.Workloads.Inputs.DatabaseConfigurationArgs
                {
                    DatabaseType = "HANA",
                    InstanceCount = 1,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_M32ts",
                    },
                },
                DeploymentType = "ThreeTier",
            },
            OsSapConfiguration = new AzureNative.Workloads.Inputs.OsSapConfigurationArgs
            {
                SapFqdn = "xyz.test.com",
            },
        },
        Environment = "Prod",
        Location = "westcentralus",
        ResourceGroupName = "test-rg",
        SapProduct = "S4HANA",
        SapVirtualInstanceName = "X00",
        Tags = null,
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewSAPVirtualInstance(ctx, "sapVirtualInstance", &workloads.SAPVirtualInstanceArgs{
			Configuration: workloads.DeploymentWithOSConfiguration{
				AppLocation:       "eastus",
				ConfigurationType: "DeploymentWithOSConfig",
				InfrastructureConfiguration: workloads.ThreeTierConfiguration{
					AppResourceGroup: "X00-RG",
					ApplicationServer: workloads.ApplicationServerConfiguration{
						InstanceCount: 6,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "xyz",
										PublicKey:  "abc",
									},
								},
							},
							VmSize: "Standard_E32ds_v4",
						},
					},
					CentralServer: workloads.CentralServerConfiguration{
						InstanceCount: 1,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "xyz",
										PublicKey:  "abc",
									},
								},
							},
							VmSize: "Standard_E16ds_v4",
						},
					},
					DatabaseServer: workloads.DatabaseConfiguration{
						DatabaseType:  "HANA",
						InstanceCount: 1,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "xyz",
										PublicKey:  "abc",
									},
								},
							},
							VmSize: "Standard_M32ts",
						},
					},
					DeploymentType: "ThreeTier",
				},
				OsSapConfiguration: workloads.OsSapConfiguration{
					SapFqdn: "xyz.test.com",
				},
			},
			Environment:            pulumi.String("Prod"),
			Location:               pulumi.String("westcentralus"),
			ResourceGroupName:      pulumi.String("test-rg"),
			SapProduct:             pulumi.String("S4HANA"),
			SapVirtualInstanceName: pulumi.String("X00"),
			Tags:                   nil,
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
import com.pulumi.azurenative.workloads.SAPVirtualInstance;
import com.pulumi.azurenative.workloads.SAPVirtualInstanceArgs;
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
        var sapVirtualInstance = new SAPVirtualInstance("sapVirtualInstance", SAPVirtualInstanceArgs.builder()        
            .configuration(Map.ofEntries(
                Map.entry("appLocation", "eastus"),
                Map.entry("configurationType", "DeploymentWithOSConfig"),
                Map.entry("infrastructureConfiguration", Map.ofEntries(
                    Map.entry("appResourceGroup", "X00-RG"),
                    Map.entry("applicationServer", Map.ofEntries(
                        Map.entry("instanceCount", 6),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E32ds_v4")
                        ))
                    )),
                    Map.entry("centralServer", Map.ofEntries(
                        Map.entry("instanceCount", 1),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E16ds_v4")
                        ))
                    )),
                    Map.entry("databaseServer", Map.ofEntries(
                        Map.entry("databaseType", "HANA"),
                        Map.entry("instanceCount", 1),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_M32ts")
                        ))
                    )),
                    Map.entry("deploymentType", "ThreeTier")
                )),
                Map.entry("osSapConfiguration", Map.of("sapFqdn", "xyz.test.com"))
            ))
            .environment("Prod")
            .location("westcentralus")
            .resourceGroupName("test-rg")
            .sapProduct("S4HANA")
            .sapVirtualInstanceName("X00")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sapVirtualInstance = new azure_native.workloads.SAPVirtualInstance("sapVirtualInstance", {
    configuration: {
        appLocation: "eastus",
        configurationType: "DeploymentWithOSConfig",
        infrastructureConfiguration: {
            appResourceGroup: "X00-RG",
            applicationServer: {
                instanceCount: 6,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_E32ds_v4",
                },
            },
            centralServer: {
                instanceCount: 1,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_E16ds_v4",
                },
            },
            databaseServer: {
                databaseType: "HANA",
                instanceCount: 1,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_M32ts",
                },
            },
            deploymentType: "ThreeTier",
        },
        osSapConfiguration: {
            sapFqdn: "xyz.test.com",
        },
    },
    environment: "Prod",
    location: "westcentralus",
    resourceGroupName: "test-rg",
    sapProduct: "S4HANA",
    sapVirtualInstanceName: "X00",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sap_virtual_instance = azure_native.workloads.SAPVirtualInstance("sapVirtualInstance",
    configuration=azure_native.workloads.DeploymentWithOSConfigurationArgs(
        app_location="eastus",
        configuration_type="DeploymentWithOSConfig",
        infrastructure_configuration=azure_native.workloads.ThreeTierConfigurationArgs(
            app_resource_group="X00-RG",
            application_server=azure_native.workloads.ApplicationServerConfigurationArgs(
                instance_count=6,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_E32ds_v4",
                ),
            ),
            central_server=azure_native.workloads.CentralServerConfigurationArgs(
                instance_count=1,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_E16ds_v4",
                ),
            ),
            database_server=azure_native.workloads.DatabaseConfigurationArgs(
                database_type="HANA",
                instance_count=1,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_M32ts",
                ),
            ),
            deployment_type="ThreeTier",
        ),
        os_sap_configuration=azure_native.workloads.OsSapConfigurationArgs(
            sap_fqdn="xyz.test.com",
        ),
    ),
    environment="Prod",
    location="westcentralus",
    resource_group_name="test-rg",
    sap_product="S4HANA",
    sap_virtual_instance_name="X00",
    tags={})

```

```yaml
resources:
  sapVirtualInstance:
    type: azure-native:workloads:SAPVirtualInstance
    properties:
      configuration:
        appLocation: eastus
        configurationType: DeploymentWithOSConfig
        infrastructureConfiguration:
          appResourceGroup: X00-RG
          applicationServer:
            instanceCount: 6
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_E32ds_v4
          centralServer:
            instanceCount: 1
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_E16ds_v4
          databaseServer:
            databaseType: HANA
            instanceCount: 1
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_M32ts
          deploymentType: ThreeTier
        osSapConfiguration:
          sapFqdn: xyz.test.com
      environment: Prod
      location: westcentralus
      resourceGroupName: test-rg
      sapProduct: S4HANA
      sapVirtualInstanceName: X00
      tags: {}

```

{{% /example %}}
{{% example %}}
### Create Infrastructure with OS configuration for HA System with Availability Set (Recommended)
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sapVirtualInstance = new AzureNative.Workloads.SAPVirtualInstance("sapVirtualInstance", new()
    {
        Configuration = new AzureNative.Workloads.Inputs.DeploymentWithOSConfigurationArgs
        {
            AppLocation = "eastus",
            ConfigurationType = "DeploymentWithOSConfig",
            InfrastructureConfiguration = new AzureNative.Workloads.Inputs.ThreeTierConfigurationArgs
            {
                AppResourceGroup = "X00-RG",
                ApplicationServer = new AzureNative.Workloads.Inputs.ApplicationServerConfigurationArgs
                {
                    InstanceCount = 6,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_E32ds_v4",
                    },
                },
                CentralServer = new AzureNative.Workloads.Inputs.CentralServerConfigurationArgs
                {
                    InstanceCount = 2,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_E16ds_v4",
                    },
                },
                DatabaseServer = new AzureNative.Workloads.Inputs.DatabaseConfigurationArgs
                {
                    DatabaseType = "HANA",
                    InstanceCount = 2,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_M32ts",
                    },
                },
                DeploymentType = "ThreeTier",
                HighAvailabilityConfig = new AzureNative.Workloads.Inputs.HighAvailabilityConfigurationArgs
                {
                    HighAvailabilityType = "AvailabilitySet",
                },
            },
            OsSapConfiguration = new AzureNative.Workloads.Inputs.OsSapConfigurationArgs
            {
                SapFqdn = "xyz.test.com",
            },
        },
        Environment = "Prod",
        Location = "westcentralus",
        ResourceGroupName = "test-rg",
        SapProduct = "S4HANA",
        SapVirtualInstanceName = "X00",
        Tags = null,
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewSAPVirtualInstance(ctx, "sapVirtualInstance", &workloads.SAPVirtualInstanceArgs{
			Configuration: workloads.DeploymentWithOSConfiguration{
				AppLocation:       "eastus",
				ConfigurationType: "DeploymentWithOSConfig",
				InfrastructureConfiguration: workloads.ThreeTierConfiguration{
					AppResourceGroup: "X00-RG",
					ApplicationServer: workloads.ApplicationServerConfiguration{
						InstanceCount: 6,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "xyz",
										PublicKey:  "abc",
									},
								},
							},
							VmSize: "Standard_E32ds_v4",
						},
					},
					CentralServer: workloads.CentralServerConfiguration{
						InstanceCount: 2,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "xyz",
										PublicKey:  "abc",
									},
								},
							},
							VmSize: "Standard_E16ds_v4",
						},
					},
					DatabaseServer: workloads.DatabaseConfiguration{
						DatabaseType:  "HANA",
						InstanceCount: 2,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "xyz",
										PublicKey:  "abc",
									},
								},
							},
							VmSize: "Standard_M32ts",
						},
					},
					DeploymentType: "ThreeTier",
					HighAvailabilityConfig: workloads.HighAvailabilityConfiguration{
						HighAvailabilityType: "AvailabilitySet",
					},
				},
				OsSapConfiguration: workloads.OsSapConfiguration{
					SapFqdn: "xyz.test.com",
				},
			},
			Environment:            pulumi.String("Prod"),
			Location:               pulumi.String("westcentralus"),
			ResourceGroupName:      pulumi.String("test-rg"),
			SapProduct:             pulumi.String("S4HANA"),
			SapVirtualInstanceName: pulumi.String("X00"),
			Tags:                   nil,
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
import com.pulumi.azurenative.workloads.SAPVirtualInstance;
import com.pulumi.azurenative.workloads.SAPVirtualInstanceArgs;
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
        var sapVirtualInstance = new SAPVirtualInstance("sapVirtualInstance", SAPVirtualInstanceArgs.builder()        
            .configuration(Map.ofEntries(
                Map.entry("appLocation", "eastus"),
                Map.entry("configurationType", "DeploymentWithOSConfig"),
                Map.entry("infrastructureConfiguration", Map.ofEntries(
                    Map.entry("appResourceGroup", "X00-RG"),
                    Map.entry("applicationServer", Map.ofEntries(
                        Map.entry("instanceCount", 6),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E32ds_v4")
                        ))
                    )),
                    Map.entry("centralServer", Map.ofEntries(
                        Map.entry("instanceCount", 2),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E16ds_v4")
                        ))
                    )),
                    Map.entry("databaseServer", Map.ofEntries(
                        Map.entry("databaseType", "HANA"),
                        Map.entry("instanceCount", 2),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_M32ts")
                        ))
                    )),
                    Map.entry("deploymentType", "ThreeTier"),
                    Map.entry("highAvailabilityConfig", Map.of("highAvailabilityType", "AvailabilitySet"))
                )),
                Map.entry("osSapConfiguration", Map.of("sapFqdn", "xyz.test.com"))
            ))
            .environment("Prod")
            .location("westcentralus")
            .resourceGroupName("test-rg")
            .sapProduct("S4HANA")
            .sapVirtualInstanceName("X00")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sapVirtualInstance = new azure_native.workloads.SAPVirtualInstance("sapVirtualInstance", {
    configuration: {
        appLocation: "eastus",
        configurationType: "DeploymentWithOSConfig",
        infrastructureConfiguration: {
            appResourceGroup: "X00-RG",
            applicationServer: {
                instanceCount: 6,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_E32ds_v4",
                },
            },
            centralServer: {
                instanceCount: 2,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_E16ds_v4",
                },
            },
            databaseServer: {
                databaseType: "HANA",
                instanceCount: 2,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_M32ts",
                },
            },
            deploymentType: "ThreeTier",
            highAvailabilityConfig: {
                highAvailabilityType: "AvailabilitySet",
            },
        },
        osSapConfiguration: {
            sapFqdn: "xyz.test.com",
        },
    },
    environment: "Prod",
    location: "westcentralus",
    resourceGroupName: "test-rg",
    sapProduct: "S4HANA",
    sapVirtualInstanceName: "X00",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sap_virtual_instance = azure_native.workloads.SAPVirtualInstance("sapVirtualInstance",
    configuration=azure_native.workloads.DeploymentWithOSConfigurationArgs(
        app_location="eastus",
        configuration_type="DeploymentWithOSConfig",
        infrastructure_configuration=azure_native.workloads.ThreeTierConfigurationArgs(
            app_resource_group="X00-RG",
            application_server=azure_native.workloads.ApplicationServerConfigurationArgs(
                instance_count=6,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_E32ds_v4",
                ),
            ),
            central_server=azure_native.workloads.CentralServerConfigurationArgs(
                instance_count=2,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_E16ds_v4",
                ),
            ),
            database_server=azure_native.workloads.DatabaseConfigurationArgs(
                database_type="HANA",
                instance_count=2,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_M32ts",
                ),
            ),
            deployment_type="ThreeTier",
            high_availability_config=azure_native.workloads.HighAvailabilityConfigurationArgs(
                high_availability_type="AvailabilitySet",
            ),
        ),
        os_sap_configuration=azure_native.workloads.OsSapConfigurationArgs(
            sap_fqdn="xyz.test.com",
        ),
    ),
    environment="Prod",
    location="westcentralus",
    resource_group_name="test-rg",
    sap_product="S4HANA",
    sap_virtual_instance_name="X00",
    tags={})

```

```yaml
resources:
  sapVirtualInstance:
    type: azure-native:workloads:SAPVirtualInstance
    properties:
      configuration:
        appLocation: eastus
        configurationType: DeploymentWithOSConfig
        infrastructureConfiguration:
          appResourceGroup: X00-RG
          applicationServer:
            instanceCount: 6
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_E32ds_v4
          centralServer:
            instanceCount: 2
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_E16ds_v4
          databaseServer:
            databaseType: HANA
            instanceCount: 2
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_M32ts
          deploymentType: ThreeTier
          highAvailabilityConfig:
            highAvailabilityType: AvailabilitySet
        osSapConfiguration:
          sapFqdn: xyz.test.com
      environment: Prod
      location: westcentralus
      resourceGroupName: test-rg
      sapProduct: S4HANA
      sapVirtualInstanceName: X00
      tags: {}

```

{{% /example %}}
{{% example %}}
### Create Infrastructure with OS configuration for HA System with Availability Zone (Recommended)
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sapVirtualInstance = new AzureNative.Workloads.SAPVirtualInstance("sapVirtualInstance", new()
    {
        Configuration = new AzureNative.Workloads.Inputs.DeploymentWithOSConfigurationArgs
        {
            AppLocation = "eastus",
            ConfigurationType = "DeploymentWithOSConfig",
            InfrastructureConfiguration = new AzureNative.Workloads.Inputs.ThreeTierConfigurationArgs
            {
                AppResourceGroup = "X00-RG",
                ApplicationServer = new AzureNative.Workloads.Inputs.ApplicationServerConfigurationArgs
                {
                    InstanceCount = 6,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_E32ds_v4",
                    },
                },
                CentralServer = new AzureNative.Workloads.Inputs.CentralServerConfigurationArgs
                {
                    InstanceCount = 2,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_E16ds_v4",
                    },
                },
                DatabaseServer = new AzureNative.Workloads.Inputs.DatabaseConfigurationArgs
                {
                    DatabaseType = "HANA",
                    InstanceCount = 2,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_M32ts",
                    },
                },
                DeploymentType = "ThreeTier",
                HighAvailabilityConfig = new AzureNative.Workloads.Inputs.HighAvailabilityConfigurationArgs
                {
                    HighAvailabilityType = "AvailabilityZone",
                },
            },
            OsSapConfiguration = new AzureNative.Workloads.Inputs.OsSapConfigurationArgs
            {
                SapFqdn = "xyz.test.com",
            },
        },
        Environment = "Prod",
        Location = "westcentralus",
        ResourceGroupName = "test-rg",
        SapProduct = "S4HANA",
        SapVirtualInstanceName = "X00",
        Tags = null,
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewSAPVirtualInstance(ctx, "sapVirtualInstance", &workloads.SAPVirtualInstanceArgs{
			Configuration: workloads.DeploymentWithOSConfiguration{
				AppLocation:       "eastus",
				ConfigurationType: "DeploymentWithOSConfig",
				InfrastructureConfiguration: workloads.ThreeTierConfiguration{
					AppResourceGroup: "X00-RG",
					ApplicationServer: workloads.ApplicationServerConfiguration{
						InstanceCount: 6,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "xyz",
										PublicKey:  "abc",
									},
								},
							},
							VmSize: "Standard_E32ds_v4",
						},
					},
					CentralServer: workloads.CentralServerConfiguration{
						InstanceCount: 2,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "xyz",
										PublicKey:  "abc",
									},
								},
							},
							VmSize: "Standard_E16ds_v4",
						},
					},
					DatabaseServer: workloads.DatabaseConfiguration{
						DatabaseType:  "HANA",
						InstanceCount: 2,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "xyz",
										PublicKey:  "abc",
									},
								},
							},
							VmSize: "Standard_M32ts",
						},
					},
					DeploymentType: "ThreeTier",
					HighAvailabilityConfig: workloads.HighAvailabilityConfiguration{
						HighAvailabilityType: "AvailabilityZone",
					},
				},
				OsSapConfiguration: workloads.OsSapConfiguration{
					SapFqdn: "xyz.test.com",
				},
			},
			Environment:            pulumi.String("Prod"),
			Location:               pulumi.String("westcentralus"),
			ResourceGroupName:      pulumi.String("test-rg"),
			SapProduct:             pulumi.String("S4HANA"),
			SapVirtualInstanceName: pulumi.String("X00"),
			Tags:                   nil,
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
import com.pulumi.azurenative.workloads.SAPVirtualInstance;
import com.pulumi.azurenative.workloads.SAPVirtualInstanceArgs;
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
        var sapVirtualInstance = new SAPVirtualInstance("sapVirtualInstance", SAPVirtualInstanceArgs.builder()        
            .configuration(Map.ofEntries(
                Map.entry("appLocation", "eastus"),
                Map.entry("configurationType", "DeploymentWithOSConfig"),
                Map.entry("infrastructureConfiguration", Map.ofEntries(
                    Map.entry("appResourceGroup", "X00-RG"),
                    Map.entry("applicationServer", Map.ofEntries(
                        Map.entry("instanceCount", 6),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E32ds_v4")
                        ))
                    )),
                    Map.entry("centralServer", Map.ofEntries(
                        Map.entry("instanceCount", 2),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E16ds_v4")
                        ))
                    )),
                    Map.entry("databaseServer", Map.ofEntries(
                        Map.entry("databaseType", "HANA"),
                        Map.entry("instanceCount", 2),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_M32ts")
                        ))
                    )),
                    Map.entry("deploymentType", "ThreeTier"),
                    Map.entry("highAvailabilityConfig", Map.of("highAvailabilityType", "AvailabilityZone"))
                )),
                Map.entry("osSapConfiguration", Map.of("sapFqdn", "xyz.test.com"))
            ))
            .environment("Prod")
            .location("westcentralus")
            .resourceGroupName("test-rg")
            .sapProduct("S4HANA")
            .sapVirtualInstanceName("X00")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sapVirtualInstance = new azure_native.workloads.SAPVirtualInstance("sapVirtualInstance", {
    configuration: {
        appLocation: "eastus",
        configurationType: "DeploymentWithOSConfig",
        infrastructureConfiguration: {
            appResourceGroup: "X00-RG",
            applicationServer: {
                instanceCount: 6,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_E32ds_v4",
                },
            },
            centralServer: {
                instanceCount: 2,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_E16ds_v4",
                },
            },
            databaseServer: {
                databaseType: "HANA",
                instanceCount: 2,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_M32ts",
                },
            },
            deploymentType: "ThreeTier",
            highAvailabilityConfig: {
                highAvailabilityType: "AvailabilityZone",
            },
        },
        osSapConfiguration: {
            sapFqdn: "xyz.test.com",
        },
    },
    environment: "Prod",
    location: "westcentralus",
    resourceGroupName: "test-rg",
    sapProduct: "S4HANA",
    sapVirtualInstanceName: "X00",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sap_virtual_instance = azure_native.workloads.SAPVirtualInstance("sapVirtualInstance",
    configuration=azure_native.workloads.DeploymentWithOSConfigurationArgs(
        app_location="eastus",
        configuration_type="DeploymentWithOSConfig",
        infrastructure_configuration=azure_native.workloads.ThreeTierConfigurationArgs(
            app_resource_group="X00-RG",
            application_server=azure_native.workloads.ApplicationServerConfigurationArgs(
                instance_count=6,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_E32ds_v4",
                ),
            ),
            central_server=azure_native.workloads.CentralServerConfigurationArgs(
                instance_count=2,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_E16ds_v4",
                ),
            ),
            database_server=azure_native.workloads.DatabaseConfigurationArgs(
                database_type="HANA",
                instance_count=2,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_M32ts",
                ),
            ),
            deployment_type="ThreeTier",
            high_availability_config=azure_native.workloads.HighAvailabilityConfigurationArgs(
                high_availability_type="AvailabilityZone",
            ),
        ),
        os_sap_configuration=azure_native.workloads.OsSapConfigurationArgs(
            sap_fqdn="xyz.test.com",
        ),
    ),
    environment="Prod",
    location="westcentralus",
    resource_group_name="test-rg",
    sap_product="S4HANA",
    sap_virtual_instance_name="X00",
    tags={})

```

```yaml
resources:
  sapVirtualInstance:
    type: azure-native:workloads:SAPVirtualInstance
    properties:
      configuration:
        appLocation: eastus
        configurationType: DeploymentWithOSConfig
        infrastructureConfiguration:
          appResourceGroup: X00-RG
          applicationServer:
            instanceCount: 6
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_E32ds_v4
          centralServer:
            instanceCount: 2
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_E16ds_v4
          databaseServer:
            databaseType: HANA
            instanceCount: 2
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_M32ts
          deploymentType: ThreeTier
          highAvailabilityConfig:
            highAvailabilityType: AvailabilityZone
        osSapConfiguration:
          sapFqdn: xyz.test.com
      environment: Prod
      location: westcentralus
      resourceGroupName: test-rg
      sapProduct: S4HANA
      sapVirtualInstanceName: X00
      tags: {}

```

{{% /example %}}
{{% example %}}
### Create Infrastructure with OS configuration for Single Server System (Recommended)
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sapVirtualInstance = new AzureNative.Workloads.SAPVirtualInstance("sapVirtualInstance", new()
    {
        Configuration = new AzureNative.Workloads.Inputs.DeploymentWithOSConfigurationArgs
        {
            AppLocation = "eastus",
            ConfigurationType = "DeploymentWithOSConfig",
            InfrastructureConfiguration = new AzureNative.Workloads.Inputs.SingleServerConfigurationArgs
            {
                AppResourceGroup = "X00-RG",
                DatabaseType = "HANA",
                DeploymentType = "SingleServer",
                NetworkConfiguration = new AzureNative.Workloads.Inputs.NetworkConfigurationArgs
                {
                    IsSecondaryIpEnabled = true,
                },
                SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                {
                    ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                    {
                        Offer = "RHEL-SAP",
                        Publisher = "RedHat",
                        Sku = "84sapha-gen2",
                        Version = "latest",
                    },
                    OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                    {
                        AdminUsername = "{your-username}",
                        OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                        {
                            DisablePasswordAuthentication = true,
                            OsType = "Linux",
                            SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                            {
                                PrivateKey = "xyz",
                                PublicKey = "abc",
                            },
                        },
                    },
                    VmSize = "Standard_E32ds_v4",
                },
            },
            OsSapConfiguration = new AzureNative.Workloads.Inputs.OsSapConfigurationArgs
            {
                SapFqdn = "xyz.test.com",
            },
        },
        Environment = "NonProd",
        Location = "westcentralus",
        ResourceGroupName = "test-rg",
        SapProduct = "S4HANA",
        SapVirtualInstanceName = "X00",
        Tags = null,
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewSAPVirtualInstance(ctx, "sapVirtualInstance", &workloads.SAPVirtualInstanceArgs{
			Configuration: workloads.DeploymentWithOSConfiguration{
				AppLocation:       "eastus",
				ConfigurationType: "DeploymentWithOSConfig",
				InfrastructureConfiguration: workloads.SingleServerConfiguration{
					AppResourceGroup: "X00-RG",
					DatabaseType:     "HANA",
					DeploymentType:   "SingleServer",
					NetworkConfiguration: workloads.NetworkConfiguration{
						IsSecondaryIpEnabled: true,
					},
					SubnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
					VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
						ImageReference: workloads.ImageReference{
							Offer:     "RHEL-SAP",
							Publisher: "RedHat",
							Sku:       "84sapha-gen2",
							Version:   "latest",
						},
						OsProfile: workloads.OSProfile{
							AdminUsername: "{your-username}",
							OsConfiguration: workloads.LinuxConfiguration{
								DisablePasswordAuthentication: true,
								OsType:                        "Linux",
								SshKeyPair: workloads.SshKeyPair{
									PrivateKey: "xyz",
									PublicKey:  "abc",
								},
							},
						},
						VmSize: "Standard_E32ds_v4",
					},
				},
				OsSapConfiguration: workloads.OsSapConfiguration{
					SapFqdn: "xyz.test.com",
				},
			},
			Environment:            pulumi.String("NonProd"),
			Location:               pulumi.String("westcentralus"),
			ResourceGroupName:      pulumi.String("test-rg"),
			SapProduct:             pulumi.String("S4HANA"),
			SapVirtualInstanceName: pulumi.String("X00"),
			Tags:                   nil,
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
import com.pulumi.azurenative.workloads.SAPVirtualInstance;
import com.pulumi.azurenative.workloads.SAPVirtualInstanceArgs;
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
        var sapVirtualInstance = new SAPVirtualInstance("sapVirtualInstance", SAPVirtualInstanceArgs.builder()        
            .configuration(Map.ofEntries(
                Map.entry("appLocation", "eastus"),
                Map.entry("configurationType", "DeploymentWithOSConfig"),
                Map.entry("infrastructureConfiguration", Map.ofEntries(
                    Map.entry("appResourceGroup", "X00-RG"),
                    Map.entry("databaseType", "HANA"),
                    Map.entry("deploymentType", "SingleServer"),
                    Map.entry("networkConfiguration", Map.of("isSecondaryIpEnabled", true)),
                    Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                    Map.entry("virtualMachineConfiguration", Map.ofEntries(
                        Map.entry("imageReference", Map.ofEntries(
                            Map.entry("offer", "RHEL-SAP"),
                            Map.entry("publisher", "RedHat"),
                            Map.entry("sku", "84sapha-gen2"),
                            Map.entry("version", "latest")
                        )),
                        Map.entry("osProfile", Map.ofEntries(
                            Map.entry("adminUsername", "{your-username}"),
                            Map.entry("osConfiguration", Map.ofEntries(
                                Map.entry("disablePasswordAuthentication", true),
                                Map.entry("osType", "Linux"),
                                Map.entry("sshKeyPair", Map.ofEntries(
                                    Map.entry("privateKey", "xyz"),
                                    Map.entry("publicKey", "abc")
                                ))
                            ))
                        )),
                        Map.entry("vmSize", "Standard_E32ds_v4")
                    ))
                )),
                Map.entry("osSapConfiguration", Map.of("sapFqdn", "xyz.test.com"))
            ))
            .environment("NonProd")
            .location("westcentralus")
            .resourceGroupName("test-rg")
            .sapProduct("S4HANA")
            .sapVirtualInstanceName("X00")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sapVirtualInstance = new azure_native.workloads.SAPVirtualInstance("sapVirtualInstance", {
    configuration: {
        appLocation: "eastus",
        configurationType: "DeploymentWithOSConfig",
        infrastructureConfiguration: {
            appResourceGroup: "X00-RG",
            databaseType: "HANA",
            deploymentType: "SingleServer",
            networkConfiguration: {
                isSecondaryIpEnabled: true,
            },
            subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
            virtualMachineConfiguration: {
                imageReference: {
                    offer: "RHEL-SAP",
                    publisher: "RedHat",
                    sku: "84sapha-gen2",
                    version: "latest",
                },
                osProfile: {
                    adminUsername: "{your-username}",
                    osConfiguration: {
                        disablePasswordAuthentication: true,
                        osType: "Linux",
                        sshKeyPair: {
                            privateKey: "xyz",
                            publicKey: "abc",
                        },
                    },
                },
                vmSize: "Standard_E32ds_v4",
            },
        },
        osSapConfiguration: {
            sapFqdn: "xyz.test.com",
        },
    },
    environment: "NonProd",
    location: "westcentralus",
    resourceGroupName: "test-rg",
    sapProduct: "S4HANA",
    sapVirtualInstanceName: "X00",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sap_virtual_instance = azure_native.workloads.SAPVirtualInstance("sapVirtualInstance",
    configuration=azure_native.workloads.DeploymentWithOSConfigurationArgs(
        app_location="eastus",
        configuration_type="DeploymentWithOSConfig",
        infrastructure_configuration=azure_native.workloads.SingleServerConfigurationArgs(
            app_resource_group="X00-RG",
            database_type="HANA",
            deployment_type="SingleServer",
            network_configuration=azure_native.workloads.NetworkConfigurationArgs(
                is_secondary_ip_enabled=True,
            ),
            subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
            virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                image_reference=azure_native.workloads.ImageReferenceArgs(
                    offer="RHEL-SAP",
                    publisher="RedHat",
                    sku="84sapha-gen2",
                    version="latest",
                ),
                os_profile=azure_native.workloads.OSProfileArgs(
                    admin_username="{your-username}",
                    os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                        disable_password_authentication=True,
                        os_type="Linux",
                        ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                            private_key="xyz",
                            public_key="abc",
                        ),
                    ),
                ),
                vm_size="Standard_E32ds_v4",
            ),
        ),
        os_sap_configuration=azure_native.workloads.OsSapConfigurationArgs(
            sap_fqdn="xyz.test.com",
        ),
    ),
    environment="NonProd",
    location="westcentralus",
    resource_group_name="test-rg",
    sap_product="S4HANA",
    sap_virtual_instance_name="X00",
    tags={})

```

```yaml
resources:
  sapVirtualInstance:
    type: azure-native:workloads:SAPVirtualInstance
    properties:
      configuration:
        appLocation: eastus
        configurationType: DeploymentWithOSConfig
        infrastructureConfiguration:
          appResourceGroup: X00-RG
          databaseType: HANA
          deploymentType: SingleServer
          networkConfiguration:
            isSecondaryIpEnabled: true
          subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
          virtualMachineConfiguration:
            imageReference:
              offer: RHEL-SAP
              publisher: RedHat
              sku: 84sapha-gen2
              version: latest
            osProfile:
              adminUsername: '{your-username}'
              osConfiguration:
                disablePasswordAuthentication: true
                osType: Linux
                sshKeyPair:
                  privateKey: xyz
                  publicKey: abc
            vmSize: Standard_E32ds_v4
        osSapConfiguration:
          sapFqdn: xyz.test.com
      environment: NonProd
      location: westcentralus
      resourceGroupName: test-rg
      sapProduct: S4HANA
      sapVirtualInstanceName: X00
      tags: {}

```

{{% /example %}}
{{% example %}}
### Create Infrastructure with a new SAP Transport Directory Fileshare
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sapVirtualInstance = new AzureNative.Workloads.SAPVirtualInstance("sapVirtualInstance", new()
    {
        Configuration = new AzureNative.Workloads.Inputs.DeploymentWithOSConfigurationArgs
        {
            AppLocation = "eastus",
            ConfigurationType = "DeploymentWithOSConfig",
            InfrastructureConfiguration = new AzureNative.Workloads.Inputs.ThreeTierConfigurationArgs
            {
                AppResourceGroup = "X00-RG",
                ApplicationServer = new AzureNative.Workloads.Inputs.ApplicationServerConfigurationArgs
                {
                    InstanceCount = 6,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_E32ds_v4",
                    },
                },
                CentralServer = new AzureNative.Workloads.Inputs.CentralServerConfigurationArgs
                {
                    InstanceCount = 1,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_E16ds_v4",
                    },
                },
                DatabaseServer = new AzureNative.Workloads.Inputs.DatabaseConfigurationArgs
                {
                    DatabaseType = "HANA",
                    InstanceCount = 1,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_M32ts",
                    },
                },
                DeploymentType = "ThreeTier",
                StorageConfiguration = new AzureNative.Workloads.Inputs.StorageConfigurationArgs
                {
                    TransportFileShareConfiguration = new AzureNative.Workloads.Inputs.CreateAndMountFileShareConfigurationArgs
                    {
                        ConfigurationType = "CreateAndMount",
                        ResourceGroup = "rgName",
                        StorageAccountName = "storageName",
                    },
                },
            },
            OsSapConfiguration = new AzureNative.Workloads.Inputs.OsSapConfigurationArgs
            {
                SapFqdn = "xyz.test.com",
            },
        },
        Environment = "Prod",
        Location = "westcentralus",
        ResourceGroupName = "test-rg",
        SapProduct = "S4HANA",
        SapVirtualInstanceName = "X00",
        Tags = null,
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewSAPVirtualInstance(ctx, "sapVirtualInstance", &workloads.SAPVirtualInstanceArgs{
			Configuration: workloads.DeploymentWithOSConfiguration{
				AppLocation:       "eastus",
				ConfigurationType: "DeploymentWithOSConfig",
				InfrastructureConfiguration: workloads.ThreeTierConfiguration{
					AppResourceGroup: "X00-RG",
					ApplicationServer: workloads.ApplicationServerConfiguration{
						InstanceCount: 6,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "xyz",
										PublicKey:  "abc",
									},
								},
							},
							VmSize: "Standard_E32ds_v4",
						},
					},
					CentralServer: workloads.CentralServerConfiguration{
						InstanceCount: 1,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "xyz",
										PublicKey:  "abc",
									},
								},
							},
							VmSize: "Standard_E16ds_v4",
						},
					},
					DatabaseServer: workloads.DatabaseConfiguration{
						DatabaseType:  "HANA",
						InstanceCount: 1,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "xyz",
										PublicKey:  "abc",
									},
								},
							},
							VmSize: "Standard_M32ts",
						},
					},
					DeploymentType: "ThreeTier",
					StorageConfiguration: workloads.StorageConfiguration{
						TransportFileShareConfiguration: workloads.CreateAndMountFileShareConfiguration{
							ConfigurationType:  "CreateAndMount",
							ResourceGroup:      "rgName",
							StorageAccountName: "storageName",
						},
					},
				},
				OsSapConfiguration: workloads.OsSapConfiguration{
					SapFqdn: "xyz.test.com",
				},
			},
			Environment:            pulumi.String("Prod"),
			Location:               pulumi.String("westcentralus"),
			ResourceGroupName:      pulumi.String("test-rg"),
			SapProduct:             pulumi.String("S4HANA"),
			SapVirtualInstanceName: pulumi.String("X00"),
			Tags:                   nil,
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
import com.pulumi.azurenative.workloads.SAPVirtualInstance;
import com.pulumi.azurenative.workloads.SAPVirtualInstanceArgs;
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
        var sapVirtualInstance = new SAPVirtualInstance("sapVirtualInstance", SAPVirtualInstanceArgs.builder()        
            .configuration(Map.ofEntries(
                Map.entry("appLocation", "eastus"),
                Map.entry("configurationType", "DeploymentWithOSConfig"),
                Map.entry("infrastructureConfiguration", Map.ofEntries(
                    Map.entry("appResourceGroup", "X00-RG"),
                    Map.entry("applicationServer", Map.ofEntries(
                        Map.entry("instanceCount", 6),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E32ds_v4")
                        ))
                    )),
                    Map.entry("centralServer", Map.ofEntries(
                        Map.entry("instanceCount", 1),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E16ds_v4")
                        ))
                    )),
                    Map.entry("databaseServer", Map.ofEntries(
                        Map.entry("databaseType", "HANA"),
                        Map.entry("instanceCount", 1),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_M32ts")
                        ))
                    )),
                    Map.entry("deploymentType", "ThreeTier"),
                    Map.entry("storageConfiguration", Map.of("transportFileShareConfiguration", Map.ofEntries(
                        Map.entry("configurationType", "CreateAndMount"),
                        Map.entry("resourceGroup", "rgName"),
                        Map.entry("storageAccountName", "storageName")
                    )))
                )),
                Map.entry("osSapConfiguration", Map.of("sapFqdn", "xyz.test.com"))
            ))
            .environment("Prod")
            .location("westcentralus")
            .resourceGroupName("test-rg")
            .sapProduct("S4HANA")
            .sapVirtualInstanceName("X00")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sapVirtualInstance = new azure_native.workloads.SAPVirtualInstance("sapVirtualInstance", {
    configuration: {
        appLocation: "eastus",
        configurationType: "DeploymentWithOSConfig",
        infrastructureConfiguration: {
            appResourceGroup: "X00-RG",
            applicationServer: {
                instanceCount: 6,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_E32ds_v4",
                },
            },
            centralServer: {
                instanceCount: 1,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_E16ds_v4",
                },
            },
            databaseServer: {
                databaseType: "HANA",
                instanceCount: 1,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_M32ts",
                },
            },
            deploymentType: "ThreeTier",
            storageConfiguration: {
                transportFileShareConfiguration: {
                    configurationType: "CreateAndMount",
                    resourceGroup: "rgName",
                    storageAccountName: "storageName",
                },
            },
        },
        osSapConfiguration: {
            sapFqdn: "xyz.test.com",
        },
    },
    environment: "Prod",
    location: "westcentralus",
    resourceGroupName: "test-rg",
    sapProduct: "S4HANA",
    sapVirtualInstanceName: "X00",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sap_virtual_instance = azure_native.workloads.SAPVirtualInstance("sapVirtualInstance",
    configuration=azure_native.workloads.DeploymentWithOSConfigurationArgs(
        app_location="eastus",
        configuration_type="DeploymentWithOSConfig",
        infrastructure_configuration=azure_native.workloads.ThreeTierConfigurationArgs(
            app_resource_group="X00-RG",
            application_server=azure_native.workloads.ApplicationServerConfigurationArgs(
                instance_count=6,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_E32ds_v4",
                ),
            ),
            central_server=azure_native.workloads.CentralServerConfigurationArgs(
                instance_count=1,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_E16ds_v4",
                ),
            ),
            database_server=azure_native.workloads.DatabaseConfigurationArgs(
                database_type="HANA",
                instance_count=1,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_M32ts",
                ),
            ),
            deployment_type="ThreeTier",
            storage_configuration=azure_native.workloads.StorageConfigurationArgs(
                transport_file_share_configuration=azure_native.workloads.CreateAndMountFileShareConfigurationArgs(
                    configuration_type="CreateAndMount",
                    resource_group="rgName",
                    storage_account_name="storageName",
                ),
            ),
        ),
        os_sap_configuration=azure_native.workloads.OsSapConfigurationArgs(
            sap_fqdn="xyz.test.com",
        ),
    ),
    environment="Prod",
    location="westcentralus",
    resource_group_name="test-rg",
    sap_product="S4HANA",
    sap_virtual_instance_name="X00",
    tags={})

```

```yaml
resources:
  sapVirtualInstance:
    type: azure-native:workloads:SAPVirtualInstance
    properties:
      configuration:
        appLocation: eastus
        configurationType: DeploymentWithOSConfig
        infrastructureConfiguration:
          appResourceGroup: X00-RG
          applicationServer:
            instanceCount: 6
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_E32ds_v4
          centralServer:
            instanceCount: 1
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_E16ds_v4
          databaseServer:
            databaseType: HANA
            instanceCount: 1
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_M32ts
          deploymentType: ThreeTier
          storageConfiguration:
            transportFileShareConfiguration:
              configurationType: CreateAndMount
              resourceGroup: rgName
              storageAccountName: storageName
        osSapConfiguration:
          sapFqdn: xyz.test.com
      environment: Prod
      location: westcentralus
      resourceGroupName: test-rg
      sapProduct: S4HANA
      sapVirtualInstanceName: X00
      tags: {}

```

{{% /example %}}
{{% example %}}
### Create Infrastructure with an existing SAP Transport Directory Fileshare
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sapVirtualInstance = new AzureNative.Workloads.SAPVirtualInstance("sapVirtualInstance", new()
    {
        Configuration = new AzureNative.Workloads.Inputs.DeploymentWithOSConfigurationArgs
        {
            AppLocation = "eastus",
            ConfigurationType = "DeploymentWithOSConfig",
            InfrastructureConfiguration = new AzureNative.Workloads.Inputs.ThreeTierConfigurationArgs
            {
                AppResourceGroup = "X00-RG",
                ApplicationServer = new AzureNative.Workloads.Inputs.ApplicationServerConfigurationArgs
                {
                    InstanceCount = 6,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_E32ds_v4",
                    },
                },
                CentralServer = new AzureNative.Workloads.Inputs.CentralServerConfigurationArgs
                {
                    InstanceCount = 1,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_E16ds_v4",
                    },
                },
                DatabaseServer = new AzureNative.Workloads.Inputs.DatabaseConfigurationArgs
                {
                    DatabaseType = "HANA",
                    InstanceCount = 1,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_M32ts",
                    },
                },
                DeploymentType = "ThreeTier",
                StorageConfiguration = new AzureNative.Workloads.Inputs.StorageConfigurationArgs
                {
                    TransportFileShareConfiguration = new AzureNative.Workloads.Inputs.MountFileShareConfigurationArgs
                    {
                        ConfigurationType = "Mount",
                        Id = "/subscriptions/49d64d54-e888-4c46-a868-1936802b762c/resourceGroups/testrg/providers/Microsoft.Network/privateEndpoints/endpoint",
                        PrivateEndpointId = "/subscriptions/49d64d54-e888-4c46-a868-1936802b762c/resourceGroups/testrg/providers/Microsoft.Network/privateEndpoints/endpoint",
                    },
                },
            },
            OsSapConfiguration = new AzureNative.Workloads.Inputs.OsSapConfigurationArgs
            {
                SapFqdn = "xyz.test.com",
            },
        },
        Environment = "Prod",
        Location = "westcentralus",
        ResourceGroupName = "test-rg",
        SapProduct = "S4HANA",
        SapVirtualInstanceName = "X00",
        Tags = null,
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewSAPVirtualInstance(ctx, "sapVirtualInstance", &workloads.SAPVirtualInstanceArgs{
			Configuration: workloads.DeploymentWithOSConfiguration{
				AppLocation:       "eastus",
				ConfigurationType: "DeploymentWithOSConfig",
				InfrastructureConfiguration: workloads.ThreeTierConfiguration{
					AppResourceGroup: "X00-RG",
					ApplicationServer: workloads.ApplicationServerConfiguration{
						InstanceCount: 6,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "xyz",
										PublicKey:  "abc",
									},
								},
							},
							VmSize: "Standard_E32ds_v4",
						},
					},
					CentralServer: workloads.CentralServerConfiguration{
						InstanceCount: 1,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "xyz",
										PublicKey:  "abc",
									},
								},
							},
							VmSize: "Standard_E16ds_v4",
						},
					},
					DatabaseServer: workloads.DatabaseConfiguration{
						DatabaseType:  "HANA",
						InstanceCount: 1,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "xyz",
										PublicKey:  "abc",
									},
								},
							},
							VmSize: "Standard_M32ts",
						},
					},
					DeploymentType: "ThreeTier",
					StorageConfiguration: workloads.StorageConfiguration{
						TransportFileShareConfiguration: workloads.MountFileShareConfiguration{
							ConfigurationType: "Mount",
							Id:                "/subscriptions/49d64d54-e888-4c46-a868-1936802b762c/resourceGroups/testrg/providers/Microsoft.Network/privateEndpoints/endpoint",
							PrivateEndpointId: "/subscriptions/49d64d54-e888-4c46-a868-1936802b762c/resourceGroups/testrg/providers/Microsoft.Network/privateEndpoints/endpoint",
						},
					},
				},
				OsSapConfiguration: workloads.OsSapConfiguration{
					SapFqdn: "xyz.test.com",
				},
			},
			Environment:            pulumi.String("Prod"),
			Location:               pulumi.String("westcentralus"),
			ResourceGroupName:      pulumi.String("test-rg"),
			SapProduct:             pulumi.String("S4HANA"),
			SapVirtualInstanceName: pulumi.String("X00"),
			Tags:                   nil,
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
import com.pulumi.azurenative.workloads.SAPVirtualInstance;
import com.pulumi.azurenative.workloads.SAPVirtualInstanceArgs;
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
        var sapVirtualInstance = new SAPVirtualInstance("sapVirtualInstance", SAPVirtualInstanceArgs.builder()        
            .configuration(Map.ofEntries(
                Map.entry("appLocation", "eastus"),
                Map.entry("configurationType", "DeploymentWithOSConfig"),
                Map.entry("infrastructureConfiguration", Map.ofEntries(
                    Map.entry("appResourceGroup", "X00-RG"),
                    Map.entry("applicationServer", Map.ofEntries(
                        Map.entry("instanceCount", 6),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E32ds_v4")
                        ))
                    )),
                    Map.entry("centralServer", Map.ofEntries(
                        Map.entry("instanceCount", 1),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E16ds_v4")
                        ))
                    )),
                    Map.entry("databaseServer", Map.ofEntries(
                        Map.entry("databaseType", "HANA"),
                        Map.entry("instanceCount", 1),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_M32ts")
                        ))
                    )),
                    Map.entry("deploymentType", "ThreeTier"),
                    Map.entry("storageConfiguration", Map.of("transportFileShareConfiguration", Map.ofEntries(
                        Map.entry("configurationType", "Mount"),
                        Map.entry("id", "/subscriptions/49d64d54-e888-4c46-a868-1936802b762c/resourceGroups/testrg/providers/Microsoft.Network/privateEndpoints/endpoint"),
                        Map.entry("privateEndpointId", "/subscriptions/49d64d54-e888-4c46-a868-1936802b762c/resourceGroups/testrg/providers/Microsoft.Network/privateEndpoints/endpoint")
                    )))
                )),
                Map.entry("osSapConfiguration", Map.of("sapFqdn", "xyz.test.com"))
            ))
            .environment("Prod")
            .location("westcentralus")
            .resourceGroupName("test-rg")
            .sapProduct("S4HANA")
            .sapVirtualInstanceName("X00")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sapVirtualInstance = new azure_native.workloads.SAPVirtualInstance("sapVirtualInstance", {
    configuration: {
        appLocation: "eastus",
        configurationType: "DeploymentWithOSConfig",
        infrastructureConfiguration: {
            appResourceGroup: "X00-RG",
            applicationServer: {
                instanceCount: 6,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_E32ds_v4",
                },
            },
            centralServer: {
                instanceCount: 1,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_E16ds_v4",
                },
            },
            databaseServer: {
                databaseType: "HANA",
                instanceCount: 1,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_M32ts",
                },
            },
            deploymentType: "ThreeTier",
            storageConfiguration: {
                transportFileShareConfiguration: {
                    configurationType: "Mount",
                    id: "/subscriptions/49d64d54-e888-4c46-a868-1936802b762c/resourceGroups/testrg/providers/Microsoft.Network/privateEndpoints/endpoint",
                    privateEndpointId: "/subscriptions/49d64d54-e888-4c46-a868-1936802b762c/resourceGroups/testrg/providers/Microsoft.Network/privateEndpoints/endpoint",
                },
            },
        },
        osSapConfiguration: {
            sapFqdn: "xyz.test.com",
        },
    },
    environment: "Prod",
    location: "westcentralus",
    resourceGroupName: "test-rg",
    sapProduct: "S4HANA",
    sapVirtualInstanceName: "X00",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sap_virtual_instance = azure_native.workloads.SAPVirtualInstance("sapVirtualInstance",
    configuration=azure_native.workloads.DeploymentWithOSConfigurationArgs(
        app_location="eastus",
        configuration_type="DeploymentWithOSConfig",
        infrastructure_configuration=azure_native.workloads.ThreeTierConfigurationArgs(
            app_resource_group="X00-RG",
            application_server=azure_native.workloads.ApplicationServerConfigurationArgs(
                instance_count=6,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_E32ds_v4",
                ),
            ),
            central_server=azure_native.workloads.CentralServerConfigurationArgs(
                instance_count=1,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_E16ds_v4",
                ),
            ),
            database_server=azure_native.workloads.DatabaseConfigurationArgs(
                database_type="HANA",
                instance_count=1,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_M32ts",
                ),
            ),
            deployment_type="ThreeTier",
            storage_configuration=azure_native.workloads.StorageConfigurationArgs(
                transport_file_share_configuration=azure_native.workloads.MountFileShareConfigurationArgs(
                    configuration_type="Mount",
                    id="/subscriptions/49d64d54-e888-4c46-a868-1936802b762c/resourceGroups/testrg/providers/Microsoft.Network/privateEndpoints/endpoint",
                    private_endpoint_id="/subscriptions/49d64d54-e888-4c46-a868-1936802b762c/resourceGroups/testrg/providers/Microsoft.Network/privateEndpoints/endpoint",
                ),
            ),
        ),
        os_sap_configuration=azure_native.workloads.OsSapConfigurationArgs(
            sap_fqdn="xyz.test.com",
        ),
    ),
    environment="Prod",
    location="westcentralus",
    resource_group_name="test-rg",
    sap_product="S4HANA",
    sap_virtual_instance_name="X00",
    tags={})

```

```yaml
resources:
  sapVirtualInstance:
    type: azure-native:workloads:SAPVirtualInstance
    properties:
      configuration:
        appLocation: eastus
        configurationType: DeploymentWithOSConfig
        infrastructureConfiguration:
          appResourceGroup: X00-RG
          applicationServer:
            instanceCount: 6
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_E32ds_v4
          centralServer:
            instanceCount: 1
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_E16ds_v4
          databaseServer:
            databaseType: HANA
            instanceCount: 1
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_M32ts
          deploymentType: ThreeTier
          storageConfiguration:
            transportFileShareConfiguration:
              configurationType: Mount
              id: /subscriptions/49d64d54-e888-4c46-a868-1936802b762c/resourceGroups/testrg/providers/Microsoft.Network/privateEndpoints/endpoint
              privateEndpointId: /subscriptions/49d64d54-e888-4c46-a868-1936802b762c/resourceGroups/testrg/providers/Microsoft.Network/privateEndpoints/endpoint
        osSapConfiguration:
          sapFqdn: xyz.test.com
      environment: Prod
      location: westcentralus
      resourceGroupName: test-rg
      sapProduct: S4HANA
      sapVirtualInstanceName: X00
      tags: {}

```

{{% /example %}}
{{% example %}}
### Create Infrastructure without a SAP Transport Directory Fileshare
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sapVirtualInstance = new AzureNative.Workloads.SAPVirtualInstance("sapVirtualInstance", new()
    {
        Configuration = new AzureNative.Workloads.Inputs.DeploymentWithOSConfigurationArgs
        {
            AppLocation = "eastus",
            ConfigurationType = "DeploymentWithOSConfig",
            InfrastructureConfiguration = new AzureNative.Workloads.Inputs.ThreeTierConfigurationArgs
            {
                AppResourceGroup = "X00-RG",
                ApplicationServer = new AzureNative.Workloads.Inputs.ApplicationServerConfigurationArgs
                {
                    InstanceCount = 6,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_E32ds_v4",
                    },
                },
                CentralServer = new AzureNative.Workloads.Inputs.CentralServerConfigurationArgs
                {
                    InstanceCount = 1,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_E16ds_v4",
                    },
                },
                DatabaseServer = new AzureNative.Workloads.Inputs.DatabaseConfigurationArgs
                {
                    DatabaseType = "HANA",
                    InstanceCount = 1,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_M32ts",
                    },
                },
                DeploymentType = "ThreeTier",
                StorageConfiguration = new AzureNative.Workloads.Inputs.StorageConfigurationArgs
                {
                    TransportFileShareConfiguration = new AzureNative.Workloads.Inputs.SkipFileShareConfigurationArgs
                    {
                        ConfigurationType = "Skip",
                    },
                },
            },
            OsSapConfiguration = new AzureNative.Workloads.Inputs.OsSapConfigurationArgs
            {
                SapFqdn = "xyz.test.com",
            },
        },
        Environment = "Prod",
        Location = "westcentralus",
        ResourceGroupName = "test-rg",
        SapProduct = "S4HANA",
        SapVirtualInstanceName = "X00",
        Tags = null,
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewSAPVirtualInstance(ctx, "sapVirtualInstance", &workloads.SAPVirtualInstanceArgs{
			Configuration: workloads.DeploymentWithOSConfiguration{
				AppLocation:       "eastus",
				ConfigurationType: "DeploymentWithOSConfig",
				InfrastructureConfiguration: workloads.ThreeTierConfiguration{
					AppResourceGroup: "X00-RG",
					ApplicationServer: workloads.ApplicationServerConfiguration{
						InstanceCount: 6,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "xyz",
										PublicKey:  "abc",
									},
								},
							},
							VmSize: "Standard_E32ds_v4",
						},
					},
					CentralServer: workloads.CentralServerConfiguration{
						InstanceCount: 1,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "xyz",
										PublicKey:  "abc",
									},
								},
							},
							VmSize: "Standard_E16ds_v4",
						},
					},
					DatabaseServer: workloads.DatabaseConfiguration{
						DatabaseType:  "HANA",
						InstanceCount: 1,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "xyz",
										PublicKey:  "abc",
									},
								},
							},
							VmSize: "Standard_M32ts",
						},
					},
					DeploymentType: "ThreeTier",
					StorageConfiguration: workloads.StorageConfiguration{
						TransportFileShareConfiguration: workloads.SkipFileShareConfiguration{
							ConfigurationType: "Skip",
						},
					},
				},
				OsSapConfiguration: workloads.OsSapConfiguration{
					SapFqdn: "xyz.test.com",
				},
			},
			Environment:            pulumi.String("Prod"),
			Location:               pulumi.String("westcentralus"),
			ResourceGroupName:      pulumi.String("test-rg"),
			SapProduct:             pulumi.String("S4HANA"),
			SapVirtualInstanceName: pulumi.String("X00"),
			Tags:                   nil,
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
import com.pulumi.azurenative.workloads.SAPVirtualInstance;
import com.pulumi.azurenative.workloads.SAPVirtualInstanceArgs;
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
        var sapVirtualInstance = new SAPVirtualInstance("sapVirtualInstance", SAPVirtualInstanceArgs.builder()        
            .configuration(Map.ofEntries(
                Map.entry("appLocation", "eastus"),
                Map.entry("configurationType", "DeploymentWithOSConfig"),
                Map.entry("infrastructureConfiguration", Map.ofEntries(
                    Map.entry("appResourceGroup", "X00-RG"),
                    Map.entry("applicationServer", Map.ofEntries(
                        Map.entry("instanceCount", 6),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E32ds_v4")
                        ))
                    )),
                    Map.entry("centralServer", Map.ofEntries(
                        Map.entry("instanceCount", 1),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E16ds_v4")
                        ))
                    )),
                    Map.entry("databaseServer", Map.ofEntries(
                        Map.entry("databaseType", "HANA"),
                        Map.entry("instanceCount", 1),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_M32ts")
                        ))
                    )),
                    Map.entry("deploymentType", "ThreeTier"),
                    Map.entry("storageConfiguration", Map.of("transportFileShareConfiguration", Map.of("configurationType", "Skip")))
                )),
                Map.entry("osSapConfiguration", Map.of("sapFqdn", "xyz.test.com"))
            ))
            .environment("Prod")
            .location("westcentralus")
            .resourceGroupName("test-rg")
            .sapProduct("S4HANA")
            .sapVirtualInstanceName("X00")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sapVirtualInstance = new azure_native.workloads.SAPVirtualInstance("sapVirtualInstance", {
    configuration: {
        appLocation: "eastus",
        configurationType: "DeploymentWithOSConfig",
        infrastructureConfiguration: {
            appResourceGroup: "X00-RG",
            applicationServer: {
                instanceCount: 6,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_E32ds_v4",
                },
            },
            centralServer: {
                instanceCount: 1,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_E16ds_v4",
                },
            },
            databaseServer: {
                databaseType: "HANA",
                instanceCount: 1,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_M32ts",
                },
            },
            deploymentType: "ThreeTier",
            storageConfiguration: {
                transportFileShareConfiguration: {
                    configurationType: "Skip",
                },
            },
        },
        osSapConfiguration: {
            sapFqdn: "xyz.test.com",
        },
    },
    environment: "Prod",
    location: "westcentralus",
    resourceGroupName: "test-rg",
    sapProduct: "S4HANA",
    sapVirtualInstanceName: "X00",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sap_virtual_instance = azure_native.workloads.SAPVirtualInstance("sapVirtualInstance",
    configuration=azure_native.workloads.DeploymentWithOSConfigurationArgs(
        app_location="eastus",
        configuration_type="DeploymentWithOSConfig",
        infrastructure_configuration=azure_native.workloads.ThreeTierConfigurationArgs(
            app_resource_group="X00-RG",
            application_server=azure_native.workloads.ApplicationServerConfigurationArgs(
                instance_count=6,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_E32ds_v4",
                ),
            ),
            central_server=azure_native.workloads.CentralServerConfigurationArgs(
                instance_count=1,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_E16ds_v4",
                ),
            ),
            database_server=azure_native.workloads.DatabaseConfigurationArgs(
                database_type="HANA",
                instance_count=1,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_M32ts",
                ),
            ),
            deployment_type="ThreeTier",
            storage_configuration=azure_native.workloads.StorageConfigurationArgs(
                transport_file_share_configuration=azure_native.workloads.SkipFileShareConfigurationArgs(
                    configuration_type="Skip",
                ),
            ),
        ),
        os_sap_configuration=azure_native.workloads.OsSapConfigurationArgs(
            sap_fqdn="xyz.test.com",
        ),
    ),
    environment="Prod",
    location="westcentralus",
    resource_group_name="test-rg",
    sap_product="S4HANA",
    sap_virtual_instance_name="X00",
    tags={})

```

```yaml
resources:
  sapVirtualInstance:
    type: azure-native:workloads:SAPVirtualInstance
    properties:
      configuration:
        appLocation: eastus
        configurationType: DeploymentWithOSConfig
        infrastructureConfiguration:
          appResourceGroup: X00-RG
          applicationServer:
            instanceCount: 6
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_E32ds_v4
          centralServer:
            instanceCount: 1
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_E16ds_v4
          databaseServer:
            databaseType: HANA
            instanceCount: 1
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_M32ts
          deploymentType: ThreeTier
          storageConfiguration:
            transportFileShareConfiguration:
              configurationType: Skip
        osSapConfiguration:
          sapFqdn: xyz.test.com
      environment: Prod
      location: westcentralus
      resourceGroupName: test-rg
      sapProduct: S4HANA
      sapVirtualInstanceName: X00
      tags: {}

```

{{% /example %}}
{{% example %}}
### Detect SAP Software Installation on a Distributed System
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sapVirtualInstance = new AzureNative.Workloads.SAPVirtualInstance("sapVirtualInstance", new()
    {
        Configuration = new AzureNative.Workloads.Inputs.DeploymentWithOSConfigurationArgs
        {
            AppLocation = "eastus",
            ConfigurationType = "DeploymentWithOSConfig",
            InfrastructureConfiguration = new AzureNative.Workloads.Inputs.ThreeTierConfigurationArgs
            {
                AppResourceGroup = "{{resourcegrp}}",
                ApplicationServer = new AzureNative.Workloads.Inputs.ApplicationServerConfigurationArgs
                {
                    InstanceCount = 2,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP-HA",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "azureuser",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "{{privateKey}}",
                                    PublicKey = "{{sshkey}}",
                                },
                            },
                        },
                        VmSize = "Standard_E4ds_v4",
                    },
                },
                CentralServer = new AzureNative.Workloads.Inputs.CentralServerConfigurationArgs
                {
                    InstanceCount = 1,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP-HA",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "azureuser",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "{{privateKey}}",
                                    PublicKey = "{{sshkey}}",
                                },
                            },
                        },
                        VmSize = "Standard_E4ds_v4",
                    },
                },
                DatabaseServer = new AzureNative.Workloads.Inputs.DatabaseConfigurationArgs
                {
                    InstanceCount = 1,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP-HA",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "azureuser",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "{{privateKey}}",
                                    PublicKey = "{{sshkey}}",
                                },
                            },
                        },
                        VmSize = "Standard_M32ts",
                    },
                },
                DeploymentType = "ThreeTier",
                NetworkConfiguration = new AzureNative.Workloads.Inputs.NetworkConfigurationArgs
                {
                    IsSecondaryIpEnabled = true,
                },
            },
            OsSapConfiguration = new AzureNative.Workloads.Inputs.OsSapConfigurationArgs
            {
                SapFqdn = "sap.bpaas.com",
            },
            SoftwareConfiguration = new AzureNative.Workloads.Inputs.ExternalInstallationSoftwareConfigurationArgs
            {
                CentralServerVmId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0",
                SoftwareInstallationType = "External",
            },
        },
        Environment = "Prod",
        Location = "eastus2",
        ResourceGroupName = "test-rg",
        SapProduct = "S4HANA",
        SapVirtualInstanceName = "X00",
        Tags = 
        {
            { "created by", "azureuser" },
        },
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewSAPVirtualInstance(ctx, "sapVirtualInstance", &workloads.SAPVirtualInstanceArgs{
			Configuration: workloads.DeploymentWithOSConfiguration{
				AppLocation:       "eastus",
				ConfigurationType: "DeploymentWithOSConfig",
				InfrastructureConfiguration: workloads.ThreeTierConfiguration{
					AppResourceGroup: "{{resourcegrp}}",
					ApplicationServer: workloads.ApplicationServerConfiguration{
						InstanceCount: 2,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP-HA",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "azureuser",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "{{privateKey}}",
										PublicKey:  "{{sshkey}}",
									},
								},
							},
							VmSize: "Standard_E4ds_v4",
						},
					},
					CentralServer: workloads.CentralServerConfiguration{
						InstanceCount: 1,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP-HA",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "azureuser",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "{{privateKey}}",
										PublicKey:  "{{sshkey}}",
									},
								},
							},
							VmSize: "Standard_E4ds_v4",
						},
					},
					DatabaseServer: workloads.DatabaseConfiguration{
						InstanceCount: 1,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP-HA",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "azureuser",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "{{privateKey}}",
										PublicKey:  "{{sshkey}}",
									},
								},
							},
							VmSize: "Standard_M32ts",
						},
					},
					DeploymentType: "ThreeTier",
					NetworkConfiguration: workloads.NetworkConfiguration{
						IsSecondaryIpEnabled: true,
					},
				},
				OsSapConfiguration: workloads.OsSapConfiguration{
					SapFqdn: "sap.bpaas.com",
				},
				SoftwareConfiguration: workloads.ExternalInstallationSoftwareConfiguration{
					CentralServerVmId:        "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0",
					SoftwareInstallationType: "External",
				},
			},
			Environment:            pulumi.String("Prod"),
			Location:               pulumi.String("eastus2"),
			ResourceGroupName:      pulumi.String("test-rg"),
			SapProduct:             pulumi.String("S4HANA"),
			SapVirtualInstanceName: pulumi.String("X00"),
			Tags: pulumi.StringMap{
				"created by": pulumi.String("azureuser"),
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
import com.pulumi.azurenative.workloads.SAPVirtualInstance;
import com.pulumi.azurenative.workloads.SAPVirtualInstanceArgs;
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
        var sapVirtualInstance = new SAPVirtualInstance("sapVirtualInstance", SAPVirtualInstanceArgs.builder()        
            .configuration(Map.ofEntries(
                Map.entry("appLocation", "eastus"),
                Map.entry("configurationType", "DeploymentWithOSConfig"),
                Map.entry("infrastructureConfiguration", Map.ofEntries(
                    Map.entry("appResourceGroup", "{{resourcegrp}}"),
                    Map.entry("applicationServer", Map.ofEntries(
                        Map.entry("instanceCount", 2),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP-HA"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "azureuser"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "{{privateKey}}"),
                                        Map.entry("publicKey", "{{sshkey}}")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E4ds_v4")
                        ))
                    )),
                    Map.entry("centralServer", Map.ofEntries(
                        Map.entry("instanceCount", 1),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP-HA"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "azureuser"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "{{privateKey}}"),
                                        Map.entry("publicKey", "{{sshkey}}")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E4ds_v4")
                        ))
                    )),
                    Map.entry("databaseServer", Map.ofEntries(
                        Map.entry("instanceCount", 1),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP-HA"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "azureuser"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "{{privateKey}}"),
                                        Map.entry("publicKey", "{{sshkey}}")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_M32ts")
                        ))
                    )),
                    Map.entry("deploymentType", "ThreeTier"),
                    Map.entry("networkConfiguration", Map.of("isSecondaryIpEnabled", true))
                )),
                Map.entry("osSapConfiguration", Map.of("sapFqdn", "sap.bpaas.com")),
                Map.entry("softwareConfiguration", Map.ofEntries(
                    Map.entry("centralServerVmId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0"),
                    Map.entry("softwareInstallationType", "External")
                ))
            ))
            .environment("Prod")
            .location("eastus2")
            .resourceGroupName("test-rg")
            .sapProduct("S4HANA")
            .sapVirtualInstanceName("X00")
            .tags(Map.of("created by", "azureuser"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sapVirtualInstance = new azure_native.workloads.SAPVirtualInstance("sapVirtualInstance", {
    configuration: {
        appLocation: "eastus",
        configurationType: "DeploymentWithOSConfig",
        infrastructureConfiguration: {
            appResourceGroup: "{{resourcegrp}}",
            applicationServer: {
                instanceCount: 2,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP-HA",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "azureuser",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "{{privateKey}}",
                                publicKey: "{{sshkey}}",
                            },
                        },
                    },
                    vmSize: "Standard_E4ds_v4",
                },
            },
            centralServer: {
                instanceCount: 1,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP-HA",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "azureuser",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "{{privateKey}}",
                                publicKey: "{{sshkey}}",
                            },
                        },
                    },
                    vmSize: "Standard_E4ds_v4",
                },
            },
            databaseServer: {
                instanceCount: 1,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP-HA",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "azureuser",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "{{privateKey}}",
                                publicKey: "{{sshkey}}",
                            },
                        },
                    },
                    vmSize: "Standard_M32ts",
                },
            },
            deploymentType: "ThreeTier",
            networkConfiguration: {
                isSecondaryIpEnabled: true,
            },
        },
        osSapConfiguration: {
            sapFqdn: "sap.bpaas.com",
        },
        softwareConfiguration: {
            centralServerVmId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0",
            softwareInstallationType: "External",
        },
    },
    environment: "Prod",
    location: "eastus2",
    resourceGroupName: "test-rg",
    sapProduct: "S4HANA",
    sapVirtualInstanceName: "X00",
    tags: {
        "created by": "azureuser",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sap_virtual_instance = azure_native.workloads.SAPVirtualInstance("sapVirtualInstance",
    configuration=azure_native.workloads.DeploymentWithOSConfigurationArgs(
        app_location="eastus",
        configuration_type="DeploymentWithOSConfig",
        infrastructure_configuration=azure_native.workloads.ThreeTierConfigurationArgs(
            app_resource_group="{{resourcegrp}}",
            application_server=azure_native.workloads.ApplicationServerConfigurationArgs(
                instance_count=2,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP-HA",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="azureuser",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="{{privateKey}}",
                                public_key="{{sshkey}}",
                            ),
                        ),
                    ),
                    vm_size="Standard_E4ds_v4",
                ),
            ),
            central_server=azure_native.workloads.CentralServerConfigurationArgs(
                instance_count=1,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP-HA",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="azureuser",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="{{privateKey}}",
                                public_key="{{sshkey}}",
                            ),
                        ),
                    ),
                    vm_size="Standard_E4ds_v4",
                ),
            ),
            database_server=azure_native.workloads.DatabaseConfigurationArgs(
                instance_count=1,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP-HA",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="azureuser",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="{{privateKey}}",
                                public_key="{{sshkey}}",
                            ),
                        ),
                    ),
                    vm_size="Standard_M32ts",
                ),
            ),
            deployment_type="ThreeTier",
            network_configuration=azure_native.workloads.NetworkConfigurationArgs(
                is_secondary_ip_enabled=True,
            ),
        ),
        os_sap_configuration=azure_native.workloads.OsSapConfigurationArgs(
            sap_fqdn="sap.bpaas.com",
        ),
        software_configuration=azure_native.workloads.ExternalInstallationSoftwareConfigurationArgs(
            central_server_vm_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0",
            software_installation_type="External",
        ),
    ),
    environment="Prod",
    location="eastus2",
    resource_group_name="test-rg",
    sap_product="S4HANA",
    sap_virtual_instance_name="X00",
    tags={
        "created by": "azureuser",
    })

```

```yaml
resources:
  sapVirtualInstance:
    type: azure-native:workloads:SAPVirtualInstance
    properties:
      configuration:
        appLocation: eastus
        configurationType: DeploymentWithOSConfig
        infrastructureConfiguration:
          appResourceGroup: '{{resourcegrp}}'
          applicationServer:
            instanceCount: 2
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP-HA
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: azureuser
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: '{{privateKey}}'
                    publicKey: '{{sshkey}}'
              vmSize: Standard_E4ds_v4
          centralServer:
            instanceCount: 1
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP-HA
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: azureuser
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: '{{privateKey}}'
                    publicKey: '{{sshkey}}'
              vmSize: Standard_E4ds_v4
          databaseServer:
            instanceCount: 1
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP-HA
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: azureuser
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: '{{privateKey}}'
                    publicKey: '{{sshkey}}'
              vmSize: Standard_M32ts
          deploymentType: ThreeTier
          networkConfiguration:
            isSecondaryIpEnabled: true
        osSapConfiguration:
          sapFqdn: sap.bpaas.com
        softwareConfiguration:
          centralServerVmId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0
          softwareInstallationType: External
      environment: Prod
      location: eastus2
      resourceGroupName: test-rg
      sapProduct: S4HANA
      sapVirtualInstanceName: X00
      tags:
        created by: azureuser

```

{{% /example %}}
{{% example %}}
### Detect SAP Software Installation on a Single Server System
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sapVirtualInstance = new AzureNative.Workloads.SAPVirtualInstance("sapVirtualInstance", new()
    {
        Configuration = new AzureNative.Workloads.Inputs.DeploymentWithOSConfigurationArgs
        {
            AppLocation = "eastus",
            ConfigurationType = "DeploymentWithOSConfig",
            InfrastructureConfiguration = new AzureNative.Workloads.Inputs.SingleServerConfigurationArgs
            {
                AppResourceGroup = "X00-RG",
                DatabaseType = "HANA",
                DeploymentType = "SingleServer",
                NetworkConfiguration = new AzureNative.Workloads.Inputs.NetworkConfigurationArgs
                {
                    IsSecondaryIpEnabled = true,
                },
                SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                {
                    ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                    {
                        Offer = "RHEL-SAP-HA",
                        Publisher = "RedHat",
                        Sku = "84sapha-gen2",
                        Version = "latest",
                    },
                    OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                    {
                        AdminUsername = "{your-username}",
                        OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                        {
                            DisablePasswordAuthentication = true,
                            OsType = "Linux",
                            SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                            {
                                PrivateKey = "xyz",
                                PublicKey = "abc",
                            },
                        },
                    },
                    VmSize = "Standard_E32ds_v4",
                },
            },
            OsSapConfiguration = new AzureNative.Workloads.Inputs.OsSapConfigurationArgs
            {
                SapFqdn = "xyz.test.com",
            },
            SoftwareConfiguration = new AzureNative.Workloads.Inputs.ExternalInstallationSoftwareConfigurationArgs
            {
                CentralServerVmId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0",
                SoftwareInstallationType = "External",
            },
        },
        Environment = "NonProd",
        Location = "westcentralus",
        ResourceGroupName = "test-rg",
        SapProduct = "S4HANA",
        SapVirtualInstanceName = "X00",
        Tags = null,
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewSAPVirtualInstance(ctx, "sapVirtualInstance", &workloads.SAPVirtualInstanceArgs{
			Configuration: workloads.DeploymentWithOSConfiguration{
				AppLocation:       "eastus",
				ConfigurationType: "DeploymentWithOSConfig",
				InfrastructureConfiguration: workloads.SingleServerConfiguration{
					AppResourceGroup: "X00-RG",
					DatabaseType:     "HANA",
					DeploymentType:   "SingleServer",
					NetworkConfiguration: workloads.NetworkConfiguration{
						IsSecondaryIpEnabled: true,
					},
					SubnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
					VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
						ImageReference: workloads.ImageReference{
							Offer:     "RHEL-SAP-HA",
							Publisher: "RedHat",
							Sku:       "84sapha-gen2",
							Version:   "latest",
						},
						OsProfile: workloads.OSProfile{
							AdminUsername: "{your-username}",
							OsConfiguration: workloads.LinuxConfiguration{
								DisablePasswordAuthentication: true,
								OsType:                        "Linux",
								SshKeyPair: workloads.SshKeyPair{
									PrivateKey: "xyz",
									PublicKey:  "abc",
								},
							},
						},
						VmSize: "Standard_E32ds_v4",
					},
				},
				OsSapConfiguration: workloads.OsSapConfiguration{
					SapFqdn: "xyz.test.com",
				},
				SoftwareConfiguration: workloads.ExternalInstallationSoftwareConfiguration{
					CentralServerVmId:        "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0",
					SoftwareInstallationType: "External",
				},
			},
			Environment:            pulumi.String("NonProd"),
			Location:               pulumi.String("westcentralus"),
			ResourceGroupName:      pulumi.String("test-rg"),
			SapProduct:             pulumi.String("S4HANA"),
			SapVirtualInstanceName: pulumi.String("X00"),
			Tags:                   nil,
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
import com.pulumi.azurenative.workloads.SAPVirtualInstance;
import com.pulumi.azurenative.workloads.SAPVirtualInstanceArgs;
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
        var sapVirtualInstance = new SAPVirtualInstance("sapVirtualInstance", SAPVirtualInstanceArgs.builder()        
            .configuration(Map.ofEntries(
                Map.entry("appLocation", "eastus"),
                Map.entry("configurationType", "DeploymentWithOSConfig"),
                Map.entry("infrastructureConfiguration", Map.ofEntries(
                    Map.entry("appResourceGroup", "X00-RG"),
                    Map.entry("databaseType", "HANA"),
                    Map.entry("deploymentType", "SingleServer"),
                    Map.entry("networkConfiguration", Map.of("isSecondaryIpEnabled", true)),
                    Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                    Map.entry("virtualMachineConfiguration", Map.ofEntries(
                        Map.entry("imageReference", Map.ofEntries(
                            Map.entry("offer", "RHEL-SAP-HA"),
                            Map.entry("publisher", "RedHat"),
                            Map.entry("sku", "84sapha-gen2"),
                            Map.entry("version", "latest")
                        )),
                        Map.entry("osProfile", Map.ofEntries(
                            Map.entry("adminUsername", "{your-username}"),
                            Map.entry("osConfiguration", Map.ofEntries(
                                Map.entry("disablePasswordAuthentication", true),
                                Map.entry("osType", "Linux"),
                                Map.entry("sshKeyPair", Map.ofEntries(
                                    Map.entry("privateKey", "xyz"),
                                    Map.entry("publicKey", "abc")
                                ))
                            ))
                        )),
                        Map.entry("vmSize", "Standard_E32ds_v4")
                    ))
                )),
                Map.entry("osSapConfiguration", Map.of("sapFqdn", "xyz.test.com")),
                Map.entry("softwareConfiguration", Map.ofEntries(
                    Map.entry("centralServerVmId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0"),
                    Map.entry("softwareInstallationType", "External")
                ))
            ))
            .environment("NonProd")
            .location("westcentralus")
            .resourceGroupName("test-rg")
            .sapProduct("S4HANA")
            .sapVirtualInstanceName("X00")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sapVirtualInstance = new azure_native.workloads.SAPVirtualInstance("sapVirtualInstance", {
    configuration: {
        appLocation: "eastus",
        configurationType: "DeploymentWithOSConfig",
        infrastructureConfiguration: {
            appResourceGroup: "X00-RG",
            databaseType: "HANA",
            deploymentType: "SingleServer",
            networkConfiguration: {
                isSecondaryIpEnabled: true,
            },
            subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
            virtualMachineConfiguration: {
                imageReference: {
                    offer: "RHEL-SAP-HA",
                    publisher: "RedHat",
                    sku: "84sapha-gen2",
                    version: "latest",
                },
                osProfile: {
                    adminUsername: "{your-username}",
                    osConfiguration: {
                        disablePasswordAuthentication: true,
                        osType: "Linux",
                        sshKeyPair: {
                            privateKey: "xyz",
                            publicKey: "abc",
                        },
                    },
                },
                vmSize: "Standard_E32ds_v4",
            },
        },
        osSapConfiguration: {
            sapFqdn: "xyz.test.com",
        },
        softwareConfiguration: {
            centralServerVmId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0",
            softwareInstallationType: "External",
        },
    },
    environment: "NonProd",
    location: "westcentralus",
    resourceGroupName: "test-rg",
    sapProduct: "S4HANA",
    sapVirtualInstanceName: "X00",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sap_virtual_instance = azure_native.workloads.SAPVirtualInstance("sapVirtualInstance",
    configuration=azure_native.workloads.DeploymentWithOSConfigurationArgs(
        app_location="eastus",
        configuration_type="DeploymentWithOSConfig",
        infrastructure_configuration=azure_native.workloads.SingleServerConfigurationArgs(
            app_resource_group="X00-RG",
            database_type="HANA",
            deployment_type="SingleServer",
            network_configuration=azure_native.workloads.NetworkConfigurationArgs(
                is_secondary_ip_enabled=True,
            ),
            subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
            virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                image_reference=azure_native.workloads.ImageReferenceArgs(
                    offer="RHEL-SAP-HA",
                    publisher="RedHat",
                    sku="84sapha-gen2",
                    version="latest",
                ),
                os_profile=azure_native.workloads.OSProfileArgs(
                    admin_username="{your-username}",
                    os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                        disable_password_authentication=True,
                        os_type="Linux",
                        ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                            private_key="xyz",
                            public_key="abc",
                        ),
                    ),
                ),
                vm_size="Standard_E32ds_v4",
            ),
        ),
        os_sap_configuration=azure_native.workloads.OsSapConfigurationArgs(
            sap_fqdn="xyz.test.com",
        ),
        software_configuration=azure_native.workloads.ExternalInstallationSoftwareConfigurationArgs(
            central_server_vm_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0",
            software_installation_type="External",
        ),
    ),
    environment="NonProd",
    location="westcentralus",
    resource_group_name="test-rg",
    sap_product="S4HANA",
    sap_virtual_instance_name="X00",
    tags={})

```

```yaml
resources:
  sapVirtualInstance:
    type: azure-native:workloads:SAPVirtualInstance
    properties:
      configuration:
        appLocation: eastus
        configurationType: DeploymentWithOSConfig
        infrastructureConfiguration:
          appResourceGroup: X00-RG
          databaseType: HANA
          deploymentType: SingleServer
          networkConfiguration:
            isSecondaryIpEnabled: true
          subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
          virtualMachineConfiguration:
            imageReference:
              offer: RHEL-SAP-HA
              publisher: RedHat
              sku: 84sapha-gen2
              version: latest
            osProfile:
              adminUsername: '{your-username}'
              osConfiguration:
                disablePasswordAuthentication: true
                osType: Linux
                sshKeyPair:
                  privateKey: xyz
                  publicKey: abc
            vmSize: Standard_E32ds_v4
        osSapConfiguration:
          sapFqdn: xyz.test.com
        softwareConfiguration:
          centralServerVmId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0
          softwareInstallationType: External
      environment: NonProd
      location: westcentralus
      resourceGroupName: test-rg
      sapProduct: S4HANA
      sapVirtualInstanceName: X00
      tags: {}

```

{{% /example %}}
{{% example %}}
### Detect SAP Software Installation on an HA System with Availability Set
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sapVirtualInstance = new AzureNative.Workloads.SAPVirtualInstance("sapVirtualInstance", new()
    {
        Configuration = new AzureNative.Workloads.Inputs.DeploymentWithOSConfigurationArgs
        {
            AppLocation = "eastus",
            ConfigurationType = "DeploymentWithOSConfig",
            InfrastructureConfiguration = new AzureNative.Workloads.Inputs.ThreeTierConfigurationArgs
            {
                AppResourceGroup = "X00-RG",
                ApplicationServer = new AzureNative.Workloads.Inputs.ApplicationServerConfigurationArgs
                {
                    InstanceCount = 6,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP-HA",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_E32ds_v4",
                    },
                },
                CentralServer = new AzureNative.Workloads.Inputs.CentralServerConfigurationArgs
                {
                    InstanceCount = 2,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP-HA",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_E16ds_v4",
                    },
                },
                DatabaseServer = new AzureNative.Workloads.Inputs.DatabaseConfigurationArgs
                {
                    DatabaseType = "HANA",
                    InstanceCount = 2,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP-HA",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_M32ts",
                    },
                },
                DeploymentType = "ThreeTier",
                HighAvailabilityConfig = new AzureNative.Workloads.Inputs.HighAvailabilityConfigurationArgs
                {
                    HighAvailabilityType = "AvailabilitySet",
                },
            },
            OsSapConfiguration = new AzureNative.Workloads.Inputs.OsSapConfigurationArgs
            {
                SapFqdn = "xyz.test.com",
            },
            SoftwareConfiguration = new AzureNative.Workloads.Inputs.ExternalInstallationSoftwareConfigurationArgs
            {
                CentralServerVmId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0",
                SoftwareInstallationType = "External",
            },
        },
        Environment = "Prod",
        Location = "westcentralus",
        ResourceGroupName = "test-rg",
        SapProduct = "S4HANA",
        SapVirtualInstanceName = "X00",
        Tags = null,
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewSAPVirtualInstance(ctx, "sapVirtualInstance", &workloads.SAPVirtualInstanceArgs{
			Configuration: workloads.DeploymentWithOSConfiguration{
				AppLocation:       "eastus",
				ConfigurationType: "DeploymentWithOSConfig",
				InfrastructureConfiguration: workloads.ThreeTierConfiguration{
					AppResourceGroup: "X00-RG",
					ApplicationServer: workloads.ApplicationServerConfiguration{
						InstanceCount: 6,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP-HA",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "xyz",
										PublicKey:  "abc",
									},
								},
							},
							VmSize: "Standard_E32ds_v4",
						},
					},
					CentralServer: workloads.CentralServerConfiguration{
						InstanceCount: 2,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP-HA",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "xyz",
										PublicKey:  "abc",
									},
								},
							},
							VmSize: "Standard_E16ds_v4",
						},
					},
					DatabaseServer: workloads.DatabaseConfiguration{
						DatabaseType:  "HANA",
						InstanceCount: 2,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP-HA",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "xyz",
										PublicKey:  "abc",
									},
								},
							},
							VmSize: "Standard_M32ts",
						},
					},
					DeploymentType: "ThreeTier",
					HighAvailabilityConfig: workloads.HighAvailabilityConfiguration{
						HighAvailabilityType: "AvailabilitySet",
					},
				},
				OsSapConfiguration: workloads.OsSapConfiguration{
					SapFqdn: "xyz.test.com",
				},
				SoftwareConfiguration: workloads.ExternalInstallationSoftwareConfiguration{
					CentralServerVmId:        "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0",
					SoftwareInstallationType: "External",
				},
			},
			Environment:            pulumi.String("Prod"),
			Location:               pulumi.String("westcentralus"),
			ResourceGroupName:      pulumi.String("test-rg"),
			SapProduct:             pulumi.String("S4HANA"),
			SapVirtualInstanceName: pulumi.String("X00"),
			Tags:                   nil,
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
import com.pulumi.azurenative.workloads.SAPVirtualInstance;
import com.pulumi.azurenative.workloads.SAPVirtualInstanceArgs;
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
        var sapVirtualInstance = new SAPVirtualInstance("sapVirtualInstance", SAPVirtualInstanceArgs.builder()        
            .configuration(Map.ofEntries(
                Map.entry("appLocation", "eastus"),
                Map.entry("configurationType", "DeploymentWithOSConfig"),
                Map.entry("infrastructureConfiguration", Map.ofEntries(
                    Map.entry("appResourceGroup", "X00-RG"),
                    Map.entry("applicationServer", Map.ofEntries(
                        Map.entry("instanceCount", 6),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP-HA"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E32ds_v4")
                        ))
                    )),
                    Map.entry("centralServer", Map.ofEntries(
                        Map.entry("instanceCount", 2),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP-HA"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E16ds_v4")
                        ))
                    )),
                    Map.entry("databaseServer", Map.ofEntries(
                        Map.entry("databaseType", "HANA"),
                        Map.entry("instanceCount", 2),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP-HA"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_M32ts")
                        ))
                    )),
                    Map.entry("deploymentType", "ThreeTier"),
                    Map.entry("highAvailabilityConfig", Map.of("highAvailabilityType", "AvailabilitySet"))
                )),
                Map.entry("osSapConfiguration", Map.of("sapFqdn", "xyz.test.com")),
                Map.entry("softwareConfiguration", Map.ofEntries(
                    Map.entry("centralServerVmId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0"),
                    Map.entry("softwareInstallationType", "External")
                ))
            ))
            .environment("Prod")
            .location("westcentralus")
            .resourceGroupName("test-rg")
            .sapProduct("S4HANA")
            .sapVirtualInstanceName("X00")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sapVirtualInstance = new azure_native.workloads.SAPVirtualInstance("sapVirtualInstance", {
    configuration: {
        appLocation: "eastus",
        configurationType: "DeploymentWithOSConfig",
        infrastructureConfiguration: {
            appResourceGroup: "X00-RG",
            applicationServer: {
                instanceCount: 6,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP-HA",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_E32ds_v4",
                },
            },
            centralServer: {
                instanceCount: 2,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP-HA",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_E16ds_v4",
                },
            },
            databaseServer: {
                databaseType: "HANA",
                instanceCount: 2,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP-HA",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_M32ts",
                },
            },
            deploymentType: "ThreeTier",
            highAvailabilityConfig: {
                highAvailabilityType: "AvailabilitySet",
            },
        },
        osSapConfiguration: {
            sapFqdn: "xyz.test.com",
        },
        softwareConfiguration: {
            centralServerVmId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0",
            softwareInstallationType: "External",
        },
    },
    environment: "Prod",
    location: "westcentralus",
    resourceGroupName: "test-rg",
    sapProduct: "S4HANA",
    sapVirtualInstanceName: "X00",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sap_virtual_instance = azure_native.workloads.SAPVirtualInstance("sapVirtualInstance",
    configuration=azure_native.workloads.DeploymentWithOSConfigurationArgs(
        app_location="eastus",
        configuration_type="DeploymentWithOSConfig",
        infrastructure_configuration=azure_native.workloads.ThreeTierConfigurationArgs(
            app_resource_group="X00-RG",
            application_server=azure_native.workloads.ApplicationServerConfigurationArgs(
                instance_count=6,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP-HA",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_E32ds_v4",
                ),
            ),
            central_server=azure_native.workloads.CentralServerConfigurationArgs(
                instance_count=2,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP-HA",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_E16ds_v4",
                ),
            ),
            database_server=azure_native.workloads.DatabaseConfigurationArgs(
                database_type="HANA",
                instance_count=2,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP-HA",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_M32ts",
                ),
            ),
            deployment_type="ThreeTier",
            high_availability_config=azure_native.workloads.HighAvailabilityConfigurationArgs(
                high_availability_type="AvailabilitySet",
            ),
        ),
        os_sap_configuration=azure_native.workloads.OsSapConfigurationArgs(
            sap_fqdn="xyz.test.com",
        ),
        software_configuration=azure_native.workloads.ExternalInstallationSoftwareConfigurationArgs(
            central_server_vm_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0",
            software_installation_type="External",
        ),
    ),
    environment="Prod",
    location="westcentralus",
    resource_group_name="test-rg",
    sap_product="S4HANA",
    sap_virtual_instance_name="X00",
    tags={})

```

```yaml
resources:
  sapVirtualInstance:
    type: azure-native:workloads:SAPVirtualInstance
    properties:
      configuration:
        appLocation: eastus
        configurationType: DeploymentWithOSConfig
        infrastructureConfiguration:
          appResourceGroup: X00-RG
          applicationServer:
            instanceCount: 6
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP-HA
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_E32ds_v4
          centralServer:
            instanceCount: 2
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP-HA
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_E16ds_v4
          databaseServer:
            databaseType: HANA
            instanceCount: 2
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP-HA
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_M32ts
          deploymentType: ThreeTier
          highAvailabilityConfig:
            highAvailabilityType: AvailabilitySet
        osSapConfiguration:
          sapFqdn: xyz.test.com
        softwareConfiguration:
          centralServerVmId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0
          softwareInstallationType: External
      environment: Prod
      location: westcentralus
      resourceGroupName: test-rg
      sapProduct: S4HANA
      sapVirtualInstanceName: X00
      tags: {}

```

{{% /example %}}
{{% example %}}
### Detect SAP Software Installation on an HA System with Availability Zone
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sapVirtualInstance = new AzureNative.Workloads.SAPVirtualInstance("sapVirtualInstance", new()
    {
        Configuration = new AzureNative.Workloads.Inputs.DeploymentWithOSConfigurationArgs
        {
            AppLocation = "eastus",
            ConfigurationType = "DeploymentWithOSConfig",
            InfrastructureConfiguration = new AzureNative.Workloads.Inputs.ThreeTierConfigurationArgs
            {
                AppResourceGroup = "X00-RG",
                ApplicationServer = new AzureNative.Workloads.Inputs.ApplicationServerConfigurationArgs
                {
                    InstanceCount = 6,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP-HA",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_E32ds_v4",
                    },
                },
                CentralServer = new AzureNative.Workloads.Inputs.CentralServerConfigurationArgs
                {
                    InstanceCount = 2,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP-HA",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_E16ds_v4",
                    },
                },
                DatabaseServer = new AzureNative.Workloads.Inputs.DatabaseConfigurationArgs
                {
                    DatabaseType = "HANA",
                    InstanceCount = 2,
                    SubnetId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP-HA",
                            Publisher = "RedHat",
                            Sku = "84sapha-gen2",
                            Version = "latest",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "{your-username}",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "xyz",
                                    PublicKey = "abc",
                                },
                            },
                        },
                        VmSize = "Standard_M32ts",
                    },
                },
                DeploymentType = "ThreeTier",
                HighAvailabilityConfig = new AzureNative.Workloads.Inputs.HighAvailabilityConfigurationArgs
                {
                    HighAvailabilityType = "AvailabilityZone",
                },
            },
            OsSapConfiguration = new AzureNative.Workloads.Inputs.OsSapConfigurationArgs
            {
                SapFqdn = "xyz.test.com",
            },
            SoftwareConfiguration = new AzureNative.Workloads.Inputs.ExternalInstallationSoftwareConfigurationArgs
            {
                CentralServerVmId = "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0",
                SoftwareInstallationType = "External",
            },
        },
        Environment = "Prod",
        Location = "westcentralus",
        ResourceGroupName = "test-rg",
        SapProduct = "S4HANA",
        SapVirtualInstanceName = "X00",
        Tags = null,
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewSAPVirtualInstance(ctx, "sapVirtualInstance", &workloads.SAPVirtualInstanceArgs{
			Configuration: workloads.DeploymentWithOSConfiguration{
				AppLocation:       "eastus",
				ConfigurationType: "DeploymentWithOSConfig",
				InfrastructureConfiguration: workloads.ThreeTierConfiguration{
					AppResourceGroup: "X00-RG",
					ApplicationServer: workloads.ApplicationServerConfiguration{
						InstanceCount: 6,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP-HA",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "xyz",
										PublicKey:  "abc",
									},
								},
							},
							VmSize: "Standard_E32ds_v4",
						},
					},
					CentralServer: workloads.CentralServerConfiguration{
						InstanceCount: 2,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP-HA",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "xyz",
										PublicKey:  "abc",
									},
								},
							},
							VmSize: "Standard_E16ds_v4",
						},
					},
					DatabaseServer: workloads.DatabaseConfiguration{
						DatabaseType:  "HANA",
						InstanceCount: 2,
						SubnetId:      "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP-HA",
								Publisher: "RedHat",
								Sku:       "84sapha-gen2",
								Version:   "latest",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "{your-username}",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "xyz",
										PublicKey:  "abc",
									},
								},
							},
							VmSize: "Standard_M32ts",
						},
					},
					DeploymentType: "ThreeTier",
					HighAvailabilityConfig: workloads.HighAvailabilityConfiguration{
						HighAvailabilityType: "AvailabilityZone",
					},
				},
				OsSapConfiguration: workloads.OsSapConfiguration{
					SapFqdn: "xyz.test.com",
				},
				SoftwareConfiguration: workloads.ExternalInstallationSoftwareConfiguration{
					CentralServerVmId:        "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0",
					SoftwareInstallationType: "External",
				},
			},
			Environment:            pulumi.String("Prod"),
			Location:               pulumi.String("westcentralus"),
			ResourceGroupName:      pulumi.String("test-rg"),
			SapProduct:             pulumi.String("S4HANA"),
			SapVirtualInstanceName: pulumi.String("X00"),
			Tags:                   nil,
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
import com.pulumi.azurenative.workloads.SAPVirtualInstance;
import com.pulumi.azurenative.workloads.SAPVirtualInstanceArgs;
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
        var sapVirtualInstance = new SAPVirtualInstance("sapVirtualInstance", SAPVirtualInstanceArgs.builder()        
            .configuration(Map.ofEntries(
                Map.entry("appLocation", "eastus"),
                Map.entry("configurationType", "DeploymentWithOSConfig"),
                Map.entry("infrastructureConfiguration", Map.ofEntries(
                    Map.entry("appResourceGroup", "X00-RG"),
                    Map.entry("applicationServer", Map.ofEntries(
                        Map.entry("instanceCount", 6),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP-HA"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E32ds_v4")
                        ))
                    )),
                    Map.entry("centralServer", Map.ofEntries(
                        Map.entry("instanceCount", 2),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP-HA"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E16ds_v4")
                        ))
                    )),
                    Map.entry("databaseServer", Map.ofEntries(
                        Map.entry("databaseType", "HANA"),
                        Map.entry("instanceCount", 2),
                        Map.entry("subnetId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP-HA"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "84sapha-gen2"),
                                Map.entry("version", "latest")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "{your-username}"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "xyz"),
                                        Map.entry("publicKey", "abc")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_M32ts")
                        ))
                    )),
                    Map.entry("deploymentType", "ThreeTier"),
                    Map.entry("highAvailabilityConfig", Map.of("highAvailabilityType", "AvailabilityZone"))
                )),
                Map.entry("osSapConfiguration", Map.of("sapFqdn", "xyz.test.com")),
                Map.entry("softwareConfiguration", Map.ofEntries(
                    Map.entry("centralServerVmId", "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0"),
                    Map.entry("softwareInstallationType", "External")
                ))
            ))
            .environment("Prod")
            .location("westcentralus")
            .resourceGroupName("test-rg")
            .sapProduct("S4HANA")
            .sapVirtualInstanceName("X00")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sapVirtualInstance = new azure_native.workloads.SAPVirtualInstance("sapVirtualInstance", {
    configuration: {
        appLocation: "eastus",
        configurationType: "DeploymentWithOSConfig",
        infrastructureConfiguration: {
            appResourceGroup: "X00-RG",
            applicationServer: {
                instanceCount: 6,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP-HA",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_E32ds_v4",
                },
            },
            centralServer: {
                instanceCount: 2,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP-HA",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_E16ds_v4",
                },
            },
            databaseServer: {
                databaseType: "HANA",
                instanceCount: 2,
                subnetId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP-HA",
                        publisher: "RedHat",
                        sku: "84sapha-gen2",
                        version: "latest",
                    },
                    osProfile: {
                        adminUsername: "{your-username}",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "xyz",
                                publicKey: "abc",
                            },
                        },
                    },
                    vmSize: "Standard_M32ts",
                },
            },
            deploymentType: "ThreeTier",
            highAvailabilityConfig: {
                highAvailabilityType: "AvailabilityZone",
            },
        },
        osSapConfiguration: {
            sapFqdn: "xyz.test.com",
        },
        softwareConfiguration: {
            centralServerVmId: "/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0",
            softwareInstallationType: "External",
        },
    },
    environment: "Prod",
    location: "westcentralus",
    resourceGroupName: "test-rg",
    sapProduct: "S4HANA",
    sapVirtualInstanceName: "X00",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sap_virtual_instance = azure_native.workloads.SAPVirtualInstance("sapVirtualInstance",
    configuration=azure_native.workloads.DeploymentWithOSConfigurationArgs(
        app_location="eastus",
        configuration_type="DeploymentWithOSConfig",
        infrastructure_configuration=azure_native.workloads.ThreeTierConfigurationArgs(
            app_resource_group="X00-RG",
            application_server=azure_native.workloads.ApplicationServerConfigurationArgs(
                instance_count=6,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP-HA",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_E32ds_v4",
                ),
            ),
            central_server=azure_native.workloads.CentralServerConfigurationArgs(
                instance_count=2,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP-HA",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_E16ds_v4",
                ),
            ),
            database_server=azure_native.workloads.DatabaseConfigurationArgs(
                database_type="HANA",
                instance_count=2,
                subnet_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP-HA",
                        publisher="RedHat",
                        sku="84sapha-gen2",
                        version="latest",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="{your-username}",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="xyz",
                                public_key="abc",
                            ),
                        ),
                    ),
                    vm_size="Standard_M32ts",
                ),
            ),
            deployment_type="ThreeTier",
            high_availability_config=azure_native.workloads.HighAvailabilityConfigurationArgs(
                high_availability_type="AvailabilityZone",
            ),
        ),
        os_sap_configuration=azure_native.workloads.OsSapConfigurationArgs(
            sap_fqdn="xyz.test.com",
        ),
        software_configuration=azure_native.workloads.ExternalInstallationSoftwareConfigurationArgs(
            central_server_vm_id="/subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0",
            software_installation_type="External",
        ),
    ),
    environment="Prod",
    location="westcentralus",
    resource_group_name="test-rg",
    sap_product="S4HANA",
    sap_virtual_instance_name="X00",
    tags={})

```

```yaml
resources:
  sapVirtualInstance:
    type: azure-native:workloads:SAPVirtualInstance
    properties:
      configuration:
        appLocation: eastus
        configurationType: DeploymentWithOSConfig
        infrastructureConfiguration:
          appResourceGroup: X00-RG
          applicationServer:
            instanceCount: 6
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP-HA
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_E32ds_v4
          centralServer:
            instanceCount: 2
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/appsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP-HA
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_E16ds_v4
          databaseServer:
            databaseType: HANA
            instanceCount: 2
            subnetId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Networks/virtualNetworks/test-vnet/subnets/dbsubnet
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP-HA
                publisher: RedHat
                sku: 84sapha-gen2
                version: latest
              osProfile:
                adminUsername: '{your-username}'
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: xyz
                    publicKey: abc
              vmSize: Standard_M32ts
          deploymentType: ThreeTier
          highAvailabilityConfig:
            highAvailabilityType: AvailabilityZone
        osSapConfiguration:
          sapFqdn: xyz.test.com
        softwareConfiguration:
          centralServerVmId: /subscriptions/49d64d54-e966-4c46-a868-1999802b762c/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0
          softwareInstallationType: External
      environment: Prod
      location: westcentralus
      resourceGroupName: test-rg
      sapProduct: S4HANA
      sapVirtualInstanceName: X00
      tags: {}

```

{{% /example %}}
{{% example %}}
### Install SAP Software on Distributed System
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sapVirtualInstance = new AzureNative.Workloads.SAPVirtualInstance("sapVirtualInstance", new()
    {
        Configuration = new AzureNative.Workloads.Inputs.DeploymentWithOSConfigurationArgs
        {
            AppLocation = "eastus",
            ConfigurationType = "DeploymentWithOSConfig",
            InfrastructureConfiguration = new AzureNative.Workloads.Inputs.ThreeTierConfigurationArgs
            {
                AppResourceGroup = "{{resourcegrp}}",
                ApplicationServer = new AzureNative.Workloads.Inputs.ApplicationServerConfigurationArgs
                {
                    InstanceCount = 2,
                    SubnetId = "/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP-HA",
                            Publisher = "RedHat",
                            Sku = "8.2",
                            Version = "8.2.2021091201",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "azureuser",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "{{privateKey}}",
                                    PublicKey = "{{sshkey}}",
                                },
                            },
                        },
                        VmSize = "Standard_E4ds_v4",
                    },
                },
                CentralServer = new AzureNative.Workloads.Inputs.CentralServerConfigurationArgs
                {
                    InstanceCount = 1,
                    SubnetId = "/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP-HA",
                            Publisher = "RedHat",
                            Sku = "8.2",
                            Version = "8.2.2021091201",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "azureuser",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "{{privateKey}}",
                                    PublicKey = "{{sshkey}}",
                                },
                            },
                        },
                        VmSize = "Standard_E4ds_v4",
                    },
                },
                DatabaseServer = new AzureNative.Workloads.Inputs.DatabaseConfigurationArgs
                {
                    InstanceCount = 1,
                    SubnetId = "/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app",
                    VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                    {
                        ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                        {
                            Offer = "RHEL-SAP-HA",
                            Publisher = "RedHat",
                            Sku = "8.2",
                            Version = "8.2.2021091201",
                        },
                        OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                        {
                            AdminUsername = "azureuser",
                            OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                            {
                                DisablePasswordAuthentication = true,
                                OsType = "Linux",
                                SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                                {
                                    PrivateKey = "{{privateKey}}",
                                    PublicKey = "{{sshkey}}",
                                },
                            },
                        },
                        VmSize = "Standard_M32ts",
                    },
                },
                DeploymentType = "ThreeTier",
                NetworkConfiguration = new AzureNative.Workloads.Inputs.NetworkConfigurationArgs
                {
                    IsSecondaryIpEnabled = true,
                },
            },
            OsSapConfiguration = new AzureNative.Workloads.Inputs.OsSapConfigurationArgs
            {
                SapFqdn = "sap.bpaas.com",
            },
            SoftwareConfiguration = new AzureNative.Workloads.Inputs.SAPInstallWithoutOSConfigSoftwareConfigurationArgs
            {
                BomUrl = "https://teststorageaccount.blob.core.windows.net/sapbits/sapfiles/boms/S41909SPS03_v0011ms/S41909SPS03_v0011ms.yaml",
                SapBitsStorageAccountId = "/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Storage/storageAccounts/teststorageaccount",
                SoftwareInstallationType = "SAPInstallWithoutOSConfig",
                SoftwareVersion = "SAP S/4HANA 1909 SPS 03",
            },
        },
        Environment = "Prod",
        Location = "eastus2",
        ResourceGroupName = "test-rg",
        SapProduct = "S4HANA",
        SapVirtualInstanceName = "X00",
        Tags = 
        {
            { "created by", "azureuser" },
        },
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewSAPVirtualInstance(ctx, "sapVirtualInstance", &workloads.SAPVirtualInstanceArgs{
			Configuration: workloads.DeploymentWithOSConfiguration{
				AppLocation:       "eastus",
				ConfigurationType: "DeploymentWithOSConfig",
				InfrastructureConfiguration: workloads.ThreeTierConfiguration{
					AppResourceGroup: "{{resourcegrp}}",
					ApplicationServer: workloads.ApplicationServerConfiguration{
						InstanceCount: 2,
						SubnetId:      "/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP-HA",
								Publisher: "RedHat",
								Sku:       "8.2",
								Version:   "8.2.2021091201",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "azureuser",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "{{privateKey}}",
										PublicKey:  "{{sshkey}}",
									},
								},
							},
							VmSize: "Standard_E4ds_v4",
						},
					},
					CentralServer: workloads.CentralServerConfiguration{
						InstanceCount: 1,
						SubnetId:      "/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP-HA",
								Publisher: "RedHat",
								Sku:       "8.2",
								Version:   "8.2.2021091201",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "azureuser",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "{{privateKey}}",
										PublicKey:  "{{sshkey}}",
									},
								},
							},
							VmSize: "Standard_E4ds_v4",
						},
					},
					DatabaseServer: workloads.DatabaseConfiguration{
						InstanceCount: 1,
						SubnetId:      "/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app",
						VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
							ImageReference: workloads.ImageReference{
								Offer:     "RHEL-SAP-HA",
								Publisher: "RedHat",
								Sku:       "8.2",
								Version:   "8.2.2021091201",
							},
							OsProfile: workloads.OSProfile{
								AdminUsername: "azureuser",
								OsConfiguration: workloads.LinuxConfiguration{
									DisablePasswordAuthentication: true,
									OsType:                        "Linux",
									SshKeyPair: workloads.SshKeyPair{
										PrivateKey: "{{privateKey}}",
										PublicKey:  "{{sshkey}}",
									},
								},
							},
							VmSize: "Standard_M32ts",
						},
					},
					DeploymentType: "ThreeTier",
					NetworkConfiguration: workloads.NetworkConfiguration{
						IsSecondaryIpEnabled: true,
					},
				},
				OsSapConfiguration: workloads.OsSapConfiguration{
					SapFqdn: "sap.bpaas.com",
				},
				SoftwareConfiguration: workloads.SAPInstallWithoutOSConfigSoftwareConfiguration{
					BomUrl:                   "https://teststorageaccount.blob.core.windows.net/sapbits/sapfiles/boms/S41909SPS03_v0011ms/S41909SPS03_v0011ms.yaml",
					SapBitsStorageAccountId:  "/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Storage/storageAccounts/teststorageaccount",
					SoftwareInstallationType: "SAPInstallWithoutOSConfig",
					SoftwareVersion:          "SAP S/4HANA 1909 SPS 03",
				},
			},
			Environment:            pulumi.String("Prod"),
			Location:               pulumi.String("eastus2"),
			ResourceGroupName:      pulumi.String("test-rg"),
			SapProduct:             pulumi.String("S4HANA"),
			SapVirtualInstanceName: pulumi.String("X00"),
			Tags: pulumi.StringMap{
				"created by": pulumi.String("azureuser"),
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
import com.pulumi.azurenative.workloads.SAPVirtualInstance;
import com.pulumi.azurenative.workloads.SAPVirtualInstanceArgs;
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
        var sapVirtualInstance = new SAPVirtualInstance("sapVirtualInstance", SAPVirtualInstanceArgs.builder()        
            .configuration(Map.ofEntries(
                Map.entry("appLocation", "eastus"),
                Map.entry("configurationType", "DeploymentWithOSConfig"),
                Map.entry("infrastructureConfiguration", Map.ofEntries(
                    Map.entry("appResourceGroup", "{{resourcegrp}}"),
                    Map.entry("applicationServer", Map.ofEntries(
                        Map.entry("instanceCount", 2),
                        Map.entry("subnetId", "/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP-HA"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "8.2"),
                                Map.entry("version", "8.2.2021091201")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "azureuser"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "{{privateKey}}"),
                                        Map.entry("publicKey", "{{sshkey}}")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E4ds_v4")
                        ))
                    )),
                    Map.entry("centralServer", Map.ofEntries(
                        Map.entry("instanceCount", 1),
                        Map.entry("subnetId", "/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP-HA"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "8.2"),
                                Map.entry("version", "8.2.2021091201")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "azureuser"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "{{privateKey}}"),
                                        Map.entry("publicKey", "{{sshkey}}")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_E4ds_v4")
                        ))
                    )),
                    Map.entry("databaseServer", Map.ofEntries(
                        Map.entry("instanceCount", 1),
                        Map.entry("subnetId", "/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app"),
                        Map.entry("virtualMachineConfiguration", Map.ofEntries(
                            Map.entry("imageReference", Map.ofEntries(
                                Map.entry("offer", "RHEL-SAP-HA"),
                                Map.entry("publisher", "RedHat"),
                                Map.entry("sku", "8.2"),
                                Map.entry("version", "8.2.2021091201")
                            )),
                            Map.entry("osProfile", Map.ofEntries(
                                Map.entry("adminUsername", "azureuser"),
                                Map.entry("osConfiguration", Map.ofEntries(
                                    Map.entry("disablePasswordAuthentication", true),
                                    Map.entry("osType", "Linux"),
                                    Map.entry("sshKeyPair", Map.ofEntries(
                                        Map.entry("privateKey", "{{privateKey}}"),
                                        Map.entry("publicKey", "{{sshkey}}")
                                    ))
                                ))
                            )),
                            Map.entry("vmSize", "Standard_M32ts")
                        ))
                    )),
                    Map.entry("deploymentType", "ThreeTier"),
                    Map.entry("networkConfiguration", Map.of("isSecondaryIpEnabled", true))
                )),
                Map.entry("osSapConfiguration", Map.of("sapFqdn", "sap.bpaas.com")),
                Map.entry("softwareConfiguration", Map.ofEntries(
                    Map.entry("bomUrl", "https://teststorageaccount.blob.core.windows.net/sapbits/sapfiles/boms/S41909SPS03_v0011ms/S41909SPS03_v0011ms.yaml"),
                    Map.entry("sapBitsStorageAccountId", "/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Storage/storageAccounts/teststorageaccount"),
                    Map.entry("softwareInstallationType", "SAPInstallWithoutOSConfig"),
                    Map.entry("softwareVersion", "SAP S/4HANA 1909 SPS 03")
                ))
            ))
            .environment("Prod")
            .location("eastus2")
            .resourceGroupName("test-rg")
            .sapProduct("S4HANA")
            .sapVirtualInstanceName("X00")
            .tags(Map.of("created by", "azureuser"))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sapVirtualInstance = new azure_native.workloads.SAPVirtualInstance("sapVirtualInstance", {
    configuration: {
        appLocation: "eastus",
        configurationType: "DeploymentWithOSConfig",
        infrastructureConfiguration: {
            appResourceGroup: "{{resourcegrp}}",
            applicationServer: {
                instanceCount: 2,
                subnetId: "/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP-HA",
                        publisher: "RedHat",
                        sku: "8.2",
                        version: "8.2.2021091201",
                    },
                    osProfile: {
                        adminUsername: "azureuser",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "{{privateKey}}",
                                publicKey: "{{sshkey}}",
                            },
                        },
                    },
                    vmSize: "Standard_E4ds_v4",
                },
            },
            centralServer: {
                instanceCount: 1,
                subnetId: "/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP-HA",
                        publisher: "RedHat",
                        sku: "8.2",
                        version: "8.2.2021091201",
                    },
                    osProfile: {
                        adminUsername: "azureuser",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "{{privateKey}}",
                                publicKey: "{{sshkey}}",
                            },
                        },
                    },
                    vmSize: "Standard_E4ds_v4",
                },
            },
            databaseServer: {
                instanceCount: 1,
                subnetId: "/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app",
                virtualMachineConfiguration: {
                    imageReference: {
                        offer: "RHEL-SAP-HA",
                        publisher: "RedHat",
                        sku: "8.2",
                        version: "8.2.2021091201",
                    },
                    osProfile: {
                        adminUsername: "azureuser",
                        osConfiguration: {
                            disablePasswordAuthentication: true,
                            osType: "Linux",
                            sshKeyPair: {
                                privateKey: "{{privateKey}}",
                                publicKey: "{{sshkey}}",
                            },
                        },
                    },
                    vmSize: "Standard_M32ts",
                },
            },
            deploymentType: "ThreeTier",
            networkConfiguration: {
                isSecondaryIpEnabled: true,
            },
        },
        osSapConfiguration: {
            sapFqdn: "sap.bpaas.com",
        },
        softwareConfiguration: {
            bomUrl: "https://teststorageaccount.blob.core.windows.net/sapbits/sapfiles/boms/S41909SPS03_v0011ms/S41909SPS03_v0011ms.yaml",
            sapBitsStorageAccountId: "/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Storage/storageAccounts/teststorageaccount",
            softwareInstallationType: "SAPInstallWithoutOSConfig",
            softwareVersion: "SAP S/4HANA 1909 SPS 03",
        },
    },
    environment: "Prod",
    location: "eastus2",
    resourceGroupName: "test-rg",
    sapProduct: "S4HANA",
    sapVirtualInstanceName: "X00",
    tags: {
        "created by": "azureuser",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sap_virtual_instance = azure_native.workloads.SAPVirtualInstance("sapVirtualInstance",
    configuration=azure_native.workloads.DeploymentWithOSConfigurationArgs(
        app_location="eastus",
        configuration_type="DeploymentWithOSConfig",
        infrastructure_configuration=azure_native.workloads.ThreeTierConfigurationArgs(
            app_resource_group="{{resourcegrp}}",
            application_server=azure_native.workloads.ApplicationServerConfigurationArgs(
                instance_count=2,
                subnet_id="/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP-HA",
                        publisher="RedHat",
                        sku="8.2",
                        version="8.2.2021091201",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="azureuser",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="{{privateKey}}",
                                public_key="{{sshkey}}",
                            ),
                        ),
                    ),
                    vm_size="Standard_E4ds_v4",
                ),
            ),
            central_server=azure_native.workloads.CentralServerConfigurationArgs(
                instance_count=1,
                subnet_id="/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP-HA",
                        publisher="RedHat",
                        sku="8.2",
                        version="8.2.2021091201",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="azureuser",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="{{privateKey}}",
                                public_key="{{sshkey}}",
                            ),
                        ),
                    ),
                    vm_size="Standard_E4ds_v4",
                ),
            ),
            database_server=azure_native.workloads.DatabaseConfigurationArgs(
                instance_count=1,
                subnet_id="/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app",
                virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                    image_reference=azure_native.workloads.ImageReferenceArgs(
                        offer="RHEL-SAP-HA",
                        publisher="RedHat",
                        sku="8.2",
                        version="8.2.2021091201",
                    ),
                    os_profile=azure_native.workloads.OSProfileArgs(
                        admin_username="azureuser",
                        os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                            disable_password_authentication=True,
                            os_type="Linux",
                            ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                                private_key="{{privateKey}}",
                                public_key="{{sshkey}}",
                            ),
                        ),
                    ),
                    vm_size="Standard_M32ts",
                ),
            ),
            deployment_type="ThreeTier",
            network_configuration=azure_native.workloads.NetworkConfigurationArgs(
                is_secondary_ip_enabled=True,
            ),
        ),
        os_sap_configuration=azure_native.workloads.OsSapConfigurationArgs(
            sap_fqdn="sap.bpaas.com",
        ),
        software_configuration=azure_native.workloads.SAPInstallWithoutOSConfigSoftwareConfigurationArgs(
            bom_url="https://teststorageaccount.blob.core.windows.net/sapbits/sapfiles/boms/S41909SPS03_v0011ms/S41909SPS03_v0011ms.yaml",
            sap_bits_storage_account_id="/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Storage/storageAccounts/teststorageaccount",
            software_installation_type="SAPInstallWithoutOSConfig",
            software_version="SAP S/4HANA 1909 SPS 03",
        ),
    ),
    environment="Prod",
    location="eastus2",
    resource_group_name="test-rg",
    sap_product="S4HANA",
    sap_virtual_instance_name="X00",
    tags={
        "created by": "azureuser",
    })

```

```yaml
resources:
  sapVirtualInstance:
    type: azure-native:workloads:SAPVirtualInstance
    properties:
      configuration:
        appLocation: eastus
        configurationType: DeploymentWithOSConfig
        infrastructureConfiguration:
          appResourceGroup: '{{resourcegrp}}'
          applicationServer:
            instanceCount: 2
            subnetId: /subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP-HA
                publisher: RedHat
                sku: '8.2'
                version: 8.2.2021091201
              osProfile:
                adminUsername: azureuser
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: '{{privateKey}}'
                    publicKey: '{{sshkey}}'
              vmSize: Standard_E4ds_v4
          centralServer:
            instanceCount: 1
            subnetId: /subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP-HA
                publisher: RedHat
                sku: '8.2'
                version: 8.2.2021091201
              osProfile:
                adminUsername: azureuser
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: '{{privateKey}}'
                    publicKey: '{{sshkey}}'
              vmSize: Standard_E4ds_v4
          databaseServer:
            instanceCount: 1
            subnetId: /subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/app
            virtualMachineConfiguration:
              imageReference:
                offer: RHEL-SAP-HA
                publisher: RedHat
                sku: '8.2'
                version: 8.2.2021091201
              osProfile:
                adminUsername: azureuser
                osConfiguration:
                  disablePasswordAuthentication: true
                  osType: Linux
                  sshKeyPair:
                    privateKey: '{{privateKey}}'
                    publicKey: '{{sshkey}}'
              vmSize: Standard_M32ts
          deploymentType: ThreeTier
          networkConfiguration:
            isSecondaryIpEnabled: true
        osSapConfiguration:
          sapFqdn: sap.bpaas.com
        softwareConfiguration:
          bomUrl: https://teststorageaccount.blob.core.windows.net/sapbits/sapfiles/boms/S41909SPS03_v0011ms/S41909SPS03_v0011ms.yaml
          sapBitsStorageAccountId: /subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Storage/storageAccounts/teststorageaccount
          softwareInstallationType: SAPInstallWithoutOSConfig
          softwareVersion: SAP S/4HANA 1909 SPS 03
      environment: Prod
      location: eastus2
      resourceGroupName: test-rg
      sapProduct: S4HANA
      sapVirtualInstanceName: X00
      tags:
        created by: azureuser

```

{{% /example %}}
{{% example %}}
### Install SAP Software on Single Server System
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sapVirtualInstance = new AzureNative.Workloads.SAPVirtualInstance("sapVirtualInstance", new()
    {
        Configuration = new AzureNative.Workloads.Inputs.DeploymentWithOSConfigurationArgs
        {
            AppLocation = "eastus",
            ConfigurationType = "DeploymentWithOSConfig",
            InfrastructureConfiguration = new AzureNative.Workloads.Inputs.SingleServerConfigurationArgs
            {
                AppResourceGroup = "test-rg",
                DeploymentType = "SingleServer",
                SubnetId = "/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/testsubnet",
                VirtualMachineConfiguration = new AzureNative.Workloads.Inputs.VirtualMachineConfigurationArgs
                {
                    ImageReference = new AzureNative.Workloads.Inputs.ImageReferenceArgs
                    {
                        Offer = "SLES-SAP",
                        Publisher = "SUSE",
                        Sku = "12-sp4-gen2",
                        Version = "2022.02.01",
                    },
                    OsProfile = new AzureNative.Workloads.Inputs.OSProfileArgs
                    {
                        AdminUsername = "azureappadmin",
                        OsConfiguration = new AzureNative.Workloads.Inputs.LinuxConfigurationArgs
                        {
                            DisablePasswordAuthentication = true,
                            OsType = "Linux",
                            SshKeyPair = new AzureNative.Workloads.Inputs.SshKeyPairArgs
                            {
                                PrivateKey = "{{privateKey}}",
                                PublicKey = "{{sshkey}}",
                            },
                        },
                    },
                    VmSize = "Standard_E32ds_v4",
                },
            },
            OsSapConfiguration = new AzureNative.Workloads.Inputs.OsSapConfigurationArgs
            {
                SapFqdn = "sap.bpaas.com",
            },
            SoftwareConfiguration = new AzureNative.Workloads.Inputs.SAPInstallWithoutOSConfigSoftwareConfigurationArgs
            {
                BomUrl = "https://teststorageaccount.blob.core.windows.net/sapbits/sapfiles/boms/S41909SPS03_v0011ms/S41909SPS03_v0011ms.yaml",
                SapBitsStorageAccountId = "/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Storage/storageAccounts/teststorageaccount",
                SoftwareInstallationType = "SAPInstallWithoutOSConfig",
                SoftwareVersion = "SAP S/4HANA 1909 SPS 03",
            },
        },
        Environment = "NonProd",
        Location = "eastus2",
        ResourceGroupName = "test-rg",
        SapProduct = "S4HANA",
        SapVirtualInstanceName = "X00",
        Tags = null,
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewSAPVirtualInstance(ctx, "sapVirtualInstance", &workloads.SAPVirtualInstanceArgs{
			Configuration: workloads.DeploymentWithOSConfiguration{
				AppLocation:       "eastus",
				ConfigurationType: "DeploymentWithOSConfig",
				InfrastructureConfiguration: workloads.SingleServerConfiguration{
					AppResourceGroup: "test-rg",
					DeploymentType:   "SingleServer",
					SubnetId:         "/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/testsubnet",
					VirtualMachineConfiguration: workloads.VirtualMachineConfiguration{
						ImageReference: workloads.ImageReference{
							Offer:     "SLES-SAP",
							Publisher: "SUSE",
							Sku:       "12-sp4-gen2",
							Version:   "2022.02.01",
						},
						OsProfile: workloads.OSProfile{
							AdminUsername: "azureappadmin",
							OsConfiguration: workloads.LinuxConfiguration{
								DisablePasswordAuthentication: true,
								OsType:                        "Linux",
								SshKeyPair: workloads.SshKeyPair{
									PrivateKey: "{{privateKey}}",
									PublicKey:  "{{sshkey}}",
								},
							},
						},
						VmSize: "Standard_E32ds_v4",
					},
				},
				OsSapConfiguration: workloads.OsSapConfiguration{
					SapFqdn: "sap.bpaas.com",
				},
				SoftwareConfiguration: workloads.SAPInstallWithoutOSConfigSoftwareConfiguration{
					BomUrl:                   "https://teststorageaccount.blob.core.windows.net/sapbits/sapfiles/boms/S41909SPS03_v0011ms/S41909SPS03_v0011ms.yaml",
					SapBitsStorageAccountId:  "/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Storage/storageAccounts/teststorageaccount",
					SoftwareInstallationType: "SAPInstallWithoutOSConfig",
					SoftwareVersion:          "SAP S/4HANA 1909 SPS 03",
				},
			},
			Environment:            pulumi.String("NonProd"),
			Location:               pulumi.String("eastus2"),
			ResourceGroupName:      pulumi.String("test-rg"),
			SapProduct:             pulumi.String("S4HANA"),
			SapVirtualInstanceName: pulumi.String("X00"),
			Tags:                   nil,
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
import com.pulumi.azurenative.workloads.SAPVirtualInstance;
import com.pulumi.azurenative.workloads.SAPVirtualInstanceArgs;
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
        var sapVirtualInstance = new SAPVirtualInstance("sapVirtualInstance", SAPVirtualInstanceArgs.builder()        
            .configuration(Map.ofEntries(
                Map.entry("appLocation", "eastus"),
                Map.entry("configurationType", "DeploymentWithOSConfig"),
                Map.entry("infrastructureConfiguration", Map.ofEntries(
                    Map.entry("appResourceGroup", "test-rg"),
                    Map.entry("deploymentType", "SingleServer"),
                    Map.entry("subnetId", "/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/testsubnet"),
                    Map.entry("virtualMachineConfiguration", Map.ofEntries(
                        Map.entry("imageReference", Map.ofEntries(
                            Map.entry("offer", "SLES-SAP"),
                            Map.entry("publisher", "SUSE"),
                            Map.entry("sku", "12-sp4-gen2"),
                            Map.entry("version", "2022.02.01")
                        )),
                        Map.entry("osProfile", Map.ofEntries(
                            Map.entry("adminUsername", "azureappadmin"),
                            Map.entry("osConfiguration", Map.ofEntries(
                                Map.entry("disablePasswordAuthentication", true),
                                Map.entry("osType", "Linux"),
                                Map.entry("sshKeyPair", Map.ofEntries(
                                    Map.entry("privateKey", "{{privateKey}}"),
                                    Map.entry("publicKey", "{{sshkey}}")
                                ))
                            ))
                        )),
                        Map.entry("vmSize", "Standard_E32ds_v4")
                    ))
                )),
                Map.entry("osSapConfiguration", Map.of("sapFqdn", "sap.bpaas.com")),
                Map.entry("softwareConfiguration", Map.ofEntries(
                    Map.entry("bomUrl", "https://teststorageaccount.blob.core.windows.net/sapbits/sapfiles/boms/S41909SPS03_v0011ms/S41909SPS03_v0011ms.yaml"),
                    Map.entry("sapBitsStorageAccountId", "/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Storage/storageAccounts/teststorageaccount"),
                    Map.entry("softwareInstallationType", "SAPInstallWithoutOSConfig"),
                    Map.entry("softwareVersion", "SAP S/4HANA 1909 SPS 03")
                ))
            ))
            .environment("NonProd")
            .location("eastus2")
            .resourceGroupName("test-rg")
            .sapProduct("S4HANA")
            .sapVirtualInstanceName("X00")
            .tags()
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sapVirtualInstance = new azure_native.workloads.SAPVirtualInstance("sapVirtualInstance", {
    configuration: {
        appLocation: "eastus",
        configurationType: "DeploymentWithOSConfig",
        infrastructureConfiguration: {
            appResourceGroup: "test-rg",
            deploymentType: "SingleServer",
            subnetId: "/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/testsubnet",
            virtualMachineConfiguration: {
                imageReference: {
                    offer: "SLES-SAP",
                    publisher: "SUSE",
                    sku: "12-sp4-gen2",
                    version: "2022.02.01",
                },
                osProfile: {
                    adminUsername: "azureappadmin",
                    osConfiguration: {
                        disablePasswordAuthentication: true,
                        osType: "Linux",
                        sshKeyPair: {
                            privateKey: "{{privateKey}}",
                            publicKey: "{{sshkey}}",
                        },
                    },
                },
                vmSize: "Standard_E32ds_v4",
            },
        },
        osSapConfiguration: {
            sapFqdn: "sap.bpaas.com",
        },
        softwareConfiguration: {
            bomUrl: "https://teststorageaccount.blob.core.windows.net/sapbits/sapfiles/boms/S41909SPS03_v0011ms/S41909SPS03_v0011ms.yaml",
            sapBitsStorageAccountId: "/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Storage/storageAccounts/teststorageaccount",
            softwareInstallationType: "SAPInstallWithoutOSConfig",
            softwareVersion: "SAP S/4HANA 1909 SPS 03",
        },
    },
    environment: "NonProd",
    location: "eastus2",
    resourceGroupName: "test-rg",
    sapProduct: "S4HANA",
    sapVirtualInstanceName: "X00",
    tags: {},
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sap_virtual_instance = azure_native.workloads.SAPVirtualInstance("sapVirtualInstance",
    configuration=azure_native.workloads.DeploymentWithOSConfigurationArgs(
        app_location="eastus",
        configuration_type="DeploymentWithOSConfig",
        infrastructure_configuration=azure_native.workloads.SingleServerConfigurationArgs(
            app_resource_group="test-rg",
            deployment_type="SingleServer",
            subnet_id="/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/testsubnet",
            virtual_machine_configuration=azure_native.workloads.VirtualMachineConfigurationArgs(
                image_reference=azure_native.workloads.ImageReferenceArgs(
                    offer="SLES-SAP",
                    publisher="SUSE",
                    sku="12-sp4-gen2",
                    version="2022.02.01",
                ),
                os_profile=azure_native.workloads.OSProfileArgs(
                    admin_username="azureappadmin",
                    os_configuration=azure_native.workloads.LinuxConfigurationArgs(
                        disable_password_authentication=True,
                        os_type="Linux",
                        ssh_key_pair=azure_native.workloads.SshKeyPairArgs(
                            private_key="{{privateKey}}",
                            public_key="{{sshkey}}",
                        ),
                    ),
                ),
                vm_size="Standard_E32ds_v4",
            ),
        ),
        os_sap_configuration=azure_native.workloads.OsSapConfigurationArgs(
            sap_fqdn="sap.bpaas.com",
        ),
        software_configuration=azure_native.workloads.SAPInstallWithoutOSConfigSoftwareConfigurationArgs(
            bom_url="https://teststorageaccount.blob.core.windows.net/sapbits/sapfiles/boms/S41909SPS03_v0011ms/S41909SPS03_v0011ms.yaml",
            sap_bits_storage_account_id="/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Storage/storageAccounts/teststorageaccount",
            software_installation_type="SAPInstallWithoutOSConfig",
            software_version="SAP S/4HANA 1909 SPS 03",
        ),
    ),
    environment="NonProd",
    location="eastus2",
    resource_group_name="test-rg",
    sap_product="S4HANA",
    sap_virtual_instance_name="X00",
    tags={})

```

```yaml
resources:
  sapVirtualInstance:
    type: azure-native:workloads:SAPVirtualInstance
    properties:
      configuration:
        appLocation: eastus
        configurationType: DeploymentWithOSConfig
        infrastructureConfiguration:
          appResourceGroup: test-rg
          deploymentType: SingleServer
          subnetId: /subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Network/virtualNetworks/test-vnet/subnets/testsubnet
          virtualMachineConfiguration:
            imageReference:
              offer: SLES-SAP
              publisher: SUSE
              sku: 12-sp4-gen2
              version: 2022.02.01
            osProfile:
              adminUsername: azureappadmin
              osConfiguration:
                disablePasswordAuthentication: true
                osType: Linux
                sshKeyPair:
                  privateKey: '{{privateKey}}'
                  publicKey: '{{sshkey}}'
            vmSize: Standard_E32ds_v4
        osSapConfiguration:
          sapFqdn: sap.bpaas.com
        softwareConfiguration:
          bomUrl: https://teststorageaccount.blob.core.windows.net/sapbits/sapfiles/boms/S41909SPS03_v0011ms/S41909SPS03_v0011ms.yaml
          sapBitsStorageAccountId: /subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Storage/storageAccounts/teststorageaccount
          softwareInstallationType: SAPInstallWithoutOSConfig
          softwareVersion: SAP S/4HANA 1909 SPS 03
      environment: NonProd
      location: eastus2
      resourceGroupName: test-rg
      sapProduct: S4HANA
      sapVirtualInstanceName: X00
      tags: {}

```

{{% /example %}}
{{% example %}}
### Register existing SAP system as Virtual Instance for SAP solutions with optional customizations.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sapVirtualInstance = new AzureNative.Workloads.SAPVirtualInstance("sapVirtualInstance", new()
    {
        Configuration = new AzureNative.Workloads.Inputs.DiscoveryConfigurationArgs
        {
            CentralServerVmId = "/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0",
            ConfigurationType = "Discovery",
            ManagedRgStorageAccountName = "q20saacssgrs",
        },
        Environment = "NonProd",
        Location = "northeurope",
        ResourceGroupName = "test-rg",
        SapProduct = "S4HANA",
        SapVirtualInstanceName = "X00",
        Tags = 
        {
            { "createdby", "abc@microsoft.com" },
            { "test", "abc" },
        },
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewSAPVirtualInstance(ctx, "sapVirtualInstance", &workloads.SAPVirtualInstanceArgs{
			Configuration: workloads.DiscoveryConfiguration{
				CentralServerVmId:           "/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0",
				ConfigurationType:           "Discovery",
				ManagedRgStorageAccountName: "q20saacssgrs",
			},
			Environment:            pulumi.String("NonProd"),
			Location:               pulumi.String("northeurope"),
			ResourceGroupName:      pulumi.String("test-rg"),
			SapProduct:             pulumi.String("S4HANA"),
			SapVirtualInstanceName: pulumi.String("X00"),
			Tags: pulumi.StringMap{
				"createdby": pulumi.String("abc@microsoft.com"),
				"test":      pulumi.String("abc"),
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
import com.pulumi.azurenative.workloads.SAPVirtualInstance;
import com.pulumi.azurenative.workloads.SAPVirtualInstanceArgs;
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
        var sapVirtualInstance = new SAPVirtualInstance("sapVirtualInstance", SAPVirtualInstanceArgs.builder()        
            .configuration(Map.ofEntries(
                Map.entry("centralServerVmId", "/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0"),
                Map.entry("configurationType", "Discovery"),
                Map.entry("managedRgStorageAccountName", "q20saacssgrs")
            ))
            .environment("NonProd")
            .location("northeurope")
            .resourceGroupName("test-rg")
            .sapProduct("S4HANA")
            .sapVirtualInstanceName("X00")
            .tags(Map.ofEntries(
                Map.entry("createdby", "abc@microsoft.com"),
                Map.entry("test", "abc")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sapVirtualInstance = new azure_native.workloads.SAPVirtualInstance("sapVirtualInstance", {
    configuration: {
        centralServerVmId: "/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0",
        configurationType: "Discovery",
        managedRgStorageAccountName: "q20saacssgrs",
    },
    environment: "NonProd",
    location: "northeurope",
    resourceGroupName: "test-rg",
    sapProduct: "S4HANA",
    sapVirtualInstanceName: "X00",
    tags: {
        createdby: "abc@microsoft.com",
        test: "abc",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sap_virtual_instance = azure_native.workloads.SAPVirtualInstance("sapVirtualInstance",
    configuration=azure_native.workloads.DiscoveryConfigurationArgs(
        central_server_vm_id="/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0",
        configuration_type="Discovery",
        managed_rg_storage_account_name="q20saacssgrs",
    ),
    environment="NonProd",
    location="northeurope",
    resource_group_name="test-rg",
    sap_product="S4HANA",
    sap_virtual_instance_name="X00",
    tags={
        "createdby": "abc@microsoft.com",
        "test": "abc",
    })

```

```yaml
resources:
  sapVirtualInstance:
    type: azure-native:workloads:SAPVirtualInstance
    properties:
      configuration:
        centralServerVmId: /subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0
        configurationType: Discovery
        managedRgStorageAccountName: q20saacssgrs
      environment: NonProd
      location: northeurope
      resourceGroupName: test-rg
      sapProduct: S4HANA
      sapVirtualInstanceName: X00
      tags:
        createdby: abc@microsoft.com
        test: abc

```

{{% /example %}}
{{% example %}}
### Register existing SAP system as Virtual Instance for SAP solutions.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var sapVirtualInstance = new AzureNative.Workloads.SAPVirtualInstance("sapVirtualInstance", new()
    {
        Configuration = new AzureNative.Workloads.Inputs.DiscoveryConfigurationArgs
        {
            CentralServerVmId = "/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0",
            ConfigurationType = "Discovery",
        },
        Environment = "NonProd",
        Location = "northeurope",
        ResourceGroupName = "test-rg",
        SapProduct = "S4HANA",
        SapVirtualInstanceName = "X00",
        Tags = 
        {
            { "createdby", "abc@microsoft.com" },
            { "test", "abc" },
        },
    });

});


```

```go
package main

import (
	workloads "github.com/pulumi/pulumi-azure-native-sdk/workloads"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := workloads.NewSAPVirtualInstance(ctx, "sapVirtualInstance", &workloads.SAPVirtualInstanceArgs{
			Configuration: workloads.DiscoveryConfiguration{
				CentralServerVmId: "/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0",
				ConfigurationType: "Discovery",
			},
			Environment:            pulumi.String("NonProd"),
			Location:               pulumi.String("northeurope"),
			ResourceGroupName:      pulumi.String("test-rg"),
			SapProduct:             pulumi.String("S4HANA"),
			SapVirtualInstanceName: pulumi.String("X00"),
			Tags: pulumi.StringMap{
				"createdby": pulumi.String("abc@microsoft.com"),
				"test":      pulumi.String("abc"),
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
import com.pulumi.azurenative.workloads.SAPVirtualInstance;
import com.pulumi.azurenative.workloads.SAPVirtualInstanceArgs;
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
        var sapVirtualInstance = new SAPVirtualInstance("sapVirtualInstance", SAPVirtualInstanceArgs.builder()        
            .configuration(Map.ofEntries(
                Map.entry("centralServerVmId", "/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0"),
                Map.entry("configurationType", "Discovery")
            ))
            .environment("NonProd")
            .location("northeurope")
            .resourceGroupName("test-rg")
            .sapProduct("S4HANA")
            .sapVirtualInstanceName("X00")
            .tags(Map.ofEntries(
                Map.entry("createdby", "abc@microsoft.com"),
                Map.entry("test", "abc")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const sapVirtualInstance = new azure_native.workloads.SAPVirtualInstance("sapVirtualInstance", {
    configuration: {
        centralServerVmId: "/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0",
        configurationType: "Discovery",
    },
    environment: "NonProd",
    location: "northeurope",
    resourceGroupName: "test-rg",
    sapProduct: "S4HANA",
    sapVirtualInstanceName: "X00",
    tags: {
        createdby: "abc@microsoft.com",
        test: "abc",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

sap_virtual_instance = azure_native.workloads.SAPVirtualInstance("sapVirtualInstance",
    configuration=azure_native.workloads.DiscoveryConfigurationArgs(
        central_server_vm_id="/subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0",
        configuration_type="Discovery",
    ),
    environment="NonProd",
    location="northeurope",
    resource_group_name="test-rg",
    sap_product="S4HANA",
    sap_virtual_instance_name="X00",
    tags={
        "createdby": "abc@microsoft.com",
        "test": "abc",
    })

```

```yaml
resources:
  sapVirtualInstance:
    type: azure-native:workloads:SAPVirtualInstance
    properties:
      configuration:
        centralServerVmId: /subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Compute/virtualMachines/sapq20scsvm0
        configurationType: Discovery
      environment: NonProd
      location: northeurope
      resourceGroupName: test-rg
      sapProduct: S4HANA
      sapVirtualInstanceName: X00
      tags:
        createdby: abc@microsoft.com
        test: abc

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:workloads:SAPVirtualInstance Q20 /subscriptions/8e17e36c-42e9-4cd5-a078-7b44883414e0/resourceGroups/test-rg/providers/Microsoft.Workloads/sapVirtualInstances/Q20 
```
