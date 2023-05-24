Packet core control plane resource.
API Version: 2022-11-01.
Previous API Version: 2022-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create packet core control plane
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var packetCoreControlPlane = new AzureNative.MobileNetwork.PacketCoreControlPlane("packetCoreControlPlane", new()
    {
        ControlPlaneAccessInterface = new AzureNative.MobileNetwork.Inputs.InterfacePropertiesArgs
        {
            Name = "N2",
        },
        CoreNetworkTechnology = "5GC",
        LocalDiagnosticsAccess = new AzureNative.MobileNetwork.Inputs.LocalDiagnosticsAccessConfigurationArgs
        {
            AuthenticationType = "AAD",
            HttpsServerCertificate = new AzureNative.MobileNetwork.Inputs.HttpsServerCertificateArgs
            {
                CertificateUrl = "https://contosovault.vault.azure.net/certificates/ingress",
            },
        },
        Location = "eastus",
        PacketCoreControlPlaneName = "TestPacketCoreCP",
        Platform = new AzureNative.MobileNetwork.Inputs.PlatformConfigurationArgs
        {
            AzureStackEdgeDevice = new AzureNative.MobileNetwork.Inputs.AzureStackEdgeDeviceResourceIdArgs
            {
                Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/TestAzureStackEdgeDevice",
            },
            ConnectedCluster = new AzureNative.MobileNetwork.Inputs.ConnectedClusterResourceIdArgs
            {
                Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Kubernetes/connectedClusters/TestConnectedCluster",
            },
            CustomLocation = new AzureNative.MobileNetwork.Inputs.CustomLocationResourceIdArgs
            {
                Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ExtendedLocation/customLocations/TestCustomLocation",
            },
            Type = "AKS-HCI",
        },
        ResourceGroupName = "rg1",
        Sites = new[]
        {
            new AzureNative.MobileNetwork.Inputs.SiteResourceIdArgs
            {
                Id = "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/sites/testSite",
            },
        },
        Sku = "G0",
        UeMtu = 1600,
        Version = "0.2.0",
    });

});


```

```go
package main

import (
	mobilenetwork "github.com/pulumi/pulumi-azure-native-sdk/mobilenetwork"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := mobilenetwork.NewPacketCoreControlPlane(ctx, "packetCoreControlPlane", &mobilenetwork.PacketCoreControlPlaneArgs{
			ControlPlaneAccessInterface: &mobilenetwork.InterfacePropertiesArgs{
				Name: pulumi.String("N2"),
			},
			CoreNetworkTechnology: pulumi.String("5GC"),
			LocalDiagnosticsAccess: mobilenetwork.LocalDiagnosticsAccessConfigurationResponse{
				AuthenticationType: pulumi.String("AAD"),
				HttpsServerCertificate: &mobilenetwork.HttpsServerCertificateArgs{
					CertificateUrl: pulumi.String("https://contosovault.vault.azure.net/certificates/ingress"),
				},
			},
			Location:                   pulumi.String("eastus"),
			PacketCoreControlPlaneName: pulumi.String("TestPacketCoreCP"),
			Platform: mobilenetwork.PlatformConfigurationResponse{
				AzureStackEdgeDevice: &mobilenetwork.AzureStackEdgeDeviceResourceIdArgs{
					Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/TestAzureStackEdgeDevice"),
				},
				ConnectedCluster: &mobilenetwork.ConnectedClusterResourceIdArgs{
					Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Kubernetes/connectedClusters/TestConnectedCluster"),
				},
				CustomLocation: &mobilenetwork.CustomLocationResourceIdArgs{
					Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ExtendedLocation/customLocations/TestCustomLocation"),
				},
				Type: pulumi.String("AKS-HCI"),
			},
			ResourceGroupName: pulumi.String("rg1"),
			Sites: []mobilenetwork.SiteResourceIdArgs{
				{
					Id: pulumi.String("/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/sites/testSite"),
				},
			},
			Sku:     pulumi.String("G0"),
			UeMtu:   pulumi.Int(1600),
			Version: pulumi.String("0.2.0"),
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
import com.pulumi.azurenative.mobilenetwork.PacketCoreControlPlane;
import com.pulumi.azurenative.mobilenetwork.PacketCoreControlPlaneArgs;
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
        var packetCoreControlPlane = new PacketCoreControlPlane("packetCoreControlPlane", PacketCoreControlPlaneArgs.builder()        
            .controlPlaneAccessInterface(Map.of("name", "N2"))
            .coreNetworkTechnology("5GC")
            .localDiagnosticsAccess(Map.ofEntries(
                Map.entry("authenticationType", "AAD"),
                Map.entry("httpsServerCertificate", Map.of("certificateUrl", "https://contosovault.vault.azure.net/certificates/ingress"))
            ))
            .location("eastus")
            .packetCoreControlPlaneName("TestPacketCoreCP")
            .platform(Map.ofEntries(
                Map.entry("azureStackEdgeDevice", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/TestAzureStackEdgeDevice")),
                Map.entry("connectedCluster", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Kubernetes/connectedClusters/TestConnectedCluster")),
                Map.entry("customLocation", Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ExtendedLocation/customLocations/TestCustomLocation")),
                Map.entry("type", "AKS-HCI")
            ))
            .resourceGroupName("rg1")
            .sites(Map.of("id", "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/sites/testSite"))
            .sku("G0")
            .ueMtu(1600)
            .version("0.2.0")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const packetCoreControlPlane = new azure_native.mobilenetwork.PacketCoreControlPlane("packetCoreControlPlane", {
    controlPlaneAccessInterface: {
        name: "N2",
    },
    coreNetworkTechnology: "5GC",
    localDiagnosticsAccess: {
        authenticationType: "AAD",
        httpsServerCertificate: {
            certificateUrl: "https://contosovault.vault.azure.net/certificates/ingress",
        },
    },
    location: "eastus",
    packetCoreControlPlaneName: "TestPacketCoreCP",
    platform: {
        azureStackEdgeDevice: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/TestAzureStackEdgeDevice",
        },
        connectedCluster: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Kubernetes/connectedClusters/TestConnectedCluster",
        },
        customLocation: {
            id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ExtendedLocation/customLocations/TestCustomLocation",
        },
        type: "AKS-HCI",
    },
    resourceGroupName: "rg1",
    sites: [{
        id: "/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/sites/testSite",
    }],
    sku: "G0",
    ueMtu: 1600,
    version: "0.2.0",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

packet_core_control_plane = azure_native.mobilenetwork.PacketCoreControlPlane("packetCoreControlPlane",
    control_plane_access_interface=azure_native.mobilenetwork.InterfacePropertiesArgs(
        name="N2",
    ),
    core_network_technology="5GC",
    local_diagnostics_access=azure_native.mobilenetwork.LocalDiagnosticsAccessConfigurationResponseArgs(
        authentication_type="AAD",
        https_server_certificate=azure_native.mobilenetwork.HttpsServerCertificateArgs(
            certificate_url="https://contosovault.vault.azure.net/certificates/ingress",
        ),
    ),
    location="eastus",
    packet_core_control_plane_name="TestPacketCoreCP",
    platform=azure_native.mobilenetwork.PlatformConfigurationResponseArgs(
        azure_stack_edge_device=azure_native.mobilenetwork.AzureStackEdgeDeviceResourceIdArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/TestAzureStackEdgeDevice",
        ),
        connected_cluster=azure_native.mobilenetwork.ConnectedClusterResourceIdArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Kubernetes/connectedClusters/TestConnectedCluster",
        ),
        custom_location=azure_native.mobilenetwork.CustomLocationResourceIdArgs(
            id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ExtendedLocation/customLocations/TestCustomLocation",
        ),
        type="AKS-HCI",
    ),
    resource_group_name="rg1",
    sites=[azure_native.mobilenetwork.SiteResourceIdArgs(
        id="/subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/sites/testSite",
    )],
    sku="G0",
    ue_mtu=1600,
    version="0.2.0")

```

```yaml
resources:
  packetCoreControlPlane:
    type: azure-native:mobilenetwork:PacketCoreControlPlane
    properties:
      controlPlaneAccessInterface:
        name: N2
      coreNetworkTechnology: 5GC
      localDiagnosticsAccess:
        authenticationType: AAD
        httpsServerCertificate:
          certificateUrl: https://contosovault.vault.azure.net/certificates/ingress
      location: eastus
      packetCoreControlPlaneName: TestPacketCoreCP
      platform:
        azureStackEdgeDevice:
          id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.DataBoxEdge/dataBoxEdgeDevices/TestAzureStackEdgeDevice
        connectedCluster:
          id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.Kubernetes/connectedClusters/TestConnectedCluster
        customLocation:
          id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ExtendedLocation/customLocations/TestCustomLocation
        type: AKS-HCI
      resourceGroupName: rg1
      sites:
        - id: /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/mobileNetworks/testMobileNetwork/sites/testSite
      sku: G0
      ueMtu: 1600
      version: 0.2.0

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:mobilenetwork:PacketCoreControlPlane TestPacketCoreCP /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.MobileNetwork/packetCoreControlPlanes/TestPacketCoreCP 
```
