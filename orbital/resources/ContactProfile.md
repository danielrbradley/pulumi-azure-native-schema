Customer creates a Contact Profile Resource, which will contain all of the configurations required for scheduling a contact.
API Version: 2022-11-01.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a contact profile
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var contactProfile = new AzureNative.Orbital.ContactProfile("contactProfile", new()
    {
        AutoTrackingConfiguration = AzureNative.Orbital.AutoTrackingConfiguration.Disabled,
        ContactProfileName = "CONTOSO-CP",
        EventHubUri = "/subscriptions/c1be1141-a7c9-4aac-9608-3c2e2f1152c3/resourceGroups/contoso-Rgp/providers/Microsoft.EventHub/namespaces/contosoHub/eventhubs/contosoHub",
        Links = new[]
        {
            new AzureNative.Orbital.Inputs.ContactProfileLinkArgs
            {
                Channels = new[]
                {
                    new AzureNative.Orbital.Inputs.ContactProfileLinkChannelArgs
                    {
                        BandwidthMHz = 2,
                        CenterFrequencyMHz = 2250,
                        EndPoint = new AzureNative.Orbital.Inputs.EndPointArgs
                        {
                            EndPointName = "ContosoTest_Uplink",
                            IpAddress = "10.1.0.4",
                            Port = "50000",
                            Protocol = "TCP",
                        },
                        Name = "contoso-uplink-channel",
                    },
                },
                Direction = "Uplink",
                EirpdBW = 45,
                GainOverTemperature = 0,
                Name = "contoso-uplink",
                Polarization = "LHCP",
            },
            new AzureNative.Orbital.Inputs.ContactProfileLinkArgs
            {
                Channels = new[]
                {
                    new AzureNative.Orbital.Inputs.ContactProfileLinkChannelArgs
                    {
                        BandwidthMHz = 15,
                        CenterFrequencyMHz = 8160,
                        EndPoint = new AzureNative.Orbital.Inputs.EndPointArgs
                        {
                            EndPointName = "ContosoTest_Downlink",
                            IpAddress = "10.1.0.5",
                            Port = "50001",
                            Protocol = "UDP",
                        },
                        Name = "contoso-downlink-channel",
                    },
                },
                Direction = "Downlink",
                EirpdBW = 0,
                GainOverTemperature = 25,
                Name = "contoso-downlink",
                Polarization = "RHCP",
            },
        },
        Location = "eastus2",
        MinimumElevationDegrees = 5,
        MinimumViableContactDuration = "PT1M",
        NetworkConfiguration = new AzureNative.Orbital.Inputs.ContactProfilesPropertiesNetworkConfigurationArgs
        {
            SubnetId = "/subscriptions/c1be1141-a7c9-4aac-9608-3c2e2f1152c3/resourceGroups/contoso-Rgp/providers/Microsoft.Network/virtualNetworks/contoso-vnet/subnets/orbital-delegated-subnet",
        },
        ResourceGroupName = "contoso-Rgp",
        ThirdPartyConfigurations = new[]
        {
            new AzureNative.Orbital.Inputs.ContactProfileThirdPartyConfigurationArgs
            {
                MissionConfiguration = "Ksat_MissionConfiguration",
                ProviderName = "KSAT",
            },
            new AzureNative.Orbital.Inputs.ContactProfileThirdPartyConfigurationArgs
            {
                MissionConfiguration = "Viasat_Configuration",
                ProviderName = "VIASAT",
            },
        },
    });

});


```

```go
package main

import (
	orbital "github.com/pulumi/pulumi-azure-native-sdk/orbital"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := orbital.NewContactProfile(ctx, "contactProfile", &orbital.ContactProfileArgs{
			AutoTrackingConfiguration: orbital.AutoTrackingConfigurationDisabled,
			ContactProfileName:        pulumi.String("CONTOSO-CP"),
			EventHubUri:               pulumi.String("/subscriptions/c1be1141-a7c9-4aac-9608-3c2e2f1152c3/resourceGroups/contoso-Rgp/providers/Microsoft.EventHub/namespaces/contosoHub/eventhubs/contosoHub"),
			Links: []orbital.ContactProfileLinkArgs{
				{
					Channels: orbital.ContactProfileLinkChannelArray{
						{
							BandwidthMHz:       pulumi.Float64(2),
							CenterFrequencyMHz: pulumi.Float64(2250),
							EndPoint: {
								EndPointName: pulumi.String("ContosoTest_Uplink"),
								IpAddress:    pulumi.String("10.1.0.4"),
								Port:         pulumi.String("50000"),
								Protocol:     pulumi.String("TCP"),
							},
							Name: pulumi.String("contoso-uplink-channel"),
						},
					},
					Direction:           pulumi.String("Uplink"),
					EirpdBW:             pulumi.Float64(45),
					GainOverTemperature: pulumi.Float64(0),
					Name:                pulumi.String("contoso-uplink"),
					Polarization:        pulumi.String("LHCP"),
				},
				{
					Channels: orbital.ContactProfileLinkChannelArray{
						{
							BandwidthMHz:       pulumi.Float64(15),
							CenterFrequencyMHz: pulumi.Float64(8160),
							EndPoint: {
								EndPointName: pulumi.String("ContosoTest_Downlink"),
								IpAddress:    pulumi.String("10.1.0.5"),
								Port:         pulumi.String("50001"),
								Protocol:     pulumi.String("UDP"),
							},
							Name: pulumi.String("contoso-downlink-channel"),
						},
					},
					Direction:           pulumi.String("Downlink"),
					EirpdBW:             pulumi.Float64(0),
					GainOverTemperature: pulumi.Float64(25),
					Name:                pulumi.String("contoso-downlink"),
					Polarization:        pulumi.String("RHCP"),
				},
			},
			Location:                     pulumi.String("eastus2"),
			MinimumElevationDegrees:      pulumi.Float64(5),
			MinimumViableContactDuration: pulumi.String("PT1M"),
			NetworkConfiguration: &orbital.ContactProfilesPropertiesNetworkConfigurationArgs{
				SubnetId: pulumi.String("/subscriptions/c1be1141-a7c9-4aac-9608-3c2e2f1152c3/resourceGroups/contoso-Rgp/providers/Microsoft.Network/virtualNetworks/contoso-vnet/subnets/orbital-delegated-subnet"),
			},
			ResourceGroupName: pulumi.String("contoso-Rgp"),
			ThirdPartyConfigurations: []orbital.ContactProfileThirdPartyConfigurationArgs{
				{
					MissionConfiguration: pulumi.String("Ksat_MissionConfiguration"),
					ProviderName:         pulumi.String("KSAT"),
				},
				{
					MissionConfiguration: pulumi.String("Viasat_Configuration"),
					ProviderName:         pulumi.String("VIASAT"),
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
import com.pulumi.azurenative.orbital.ContactProfile;
import com.pulumi.azurenative.orbital.ContactProfileArgs;
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
        var contactProfile = new ContactProfile("contactProfile", ContactProfileArgs.builder()        
            .autoTrackingConfiguration("disabled")
            .contactProfileName("CONTOSO-CP")
            .eventHubUri("/subscriptions/c1be1141-a7c9-4aac-9608-3c2e2f1152c3/resourceGroups/contoso-Rgp/providers/Microsoft.EventHub/namespaces/contosoHub/eventhubs/contosoHub")
            .links(            
                Map.ofEntries(
                    Map.entry("channels", Map.ofEntries(
                        Map.entry("bandwidthMHz", 2),
                        Map.entry("centerFrequencyMHz", 2250),
                        Map.entry("endPoint", Map.ofEntries(
                            Map.entry("endPointName", "ContosoTest_Uplink"),
                            Map.entry("ipAddress", "10.1.0.4"),
                            Map.entry("port", "50000"),
                            Map.entry("protocol", "TCP")
                        )),
                        Map.entry("name", "contoso-uplink-channel")
                    )),
                    Map.entry("direction", "Uplink"),
                    Map.entry("eirpdBW", 45),
                    Map.entry("gainOverTemperature", 0),
                    Map.entry("name", "contoso-uplink"),
                    Map.entry("polarization", "LHCP")
                ),
                Map.ofEntries(
                    Map.entry("channels", Map.ofEntries(
                        Map.entry("bandwidthMHz", 15),
                        Map.entry("centerFrequencyMHz", 8160),
                        Map.entry("endPoint", Map.ofEntries(
                            Map.entry("endPointName", "ContosoTest_Downlink"),
                            Map.entry("ipAddress", "10.1.0.5"),
                            Map.entry("port", "50001"),
                            Map.entry("protocol", "UDP")
                        )),
                        Map.entry("name", "contoso-downlink-channel")
                    )),
                    Map.entry("direction", "Downlink"),
                    Map.entry("eirpdBW", 0),
                    Map.entry("gainOverTemperature", 25),
                    Map.entry("name", "contoso-downlink"),
                    Map.entry("polarization", "RHCP")
                ))
            .location("eastus2")
            .minimumElevationDegrees(5)
            .minimumViableContactDuration("PT1M")
            .networkConfiguration(Map.of("subnetId", "/subscriptions/c1be1141-a7c9-4aac-9608-3c2e2f1152c3/resourceGroups/contoso-Rgp/providers/Microsoft.Network/virtualNetworks/contoso-vnet/subnets/orbital-delegated-subnet"))
            .resourceGroupName("contoso-Rgp")
            .thirdPartyConfigurations(            
                Map.ofEntries(
                    Map.entry("missionConfiguration", "Ksat_MissionConfiguration"),
                    Map.entry("providerName", "KSAT")
                ),
                Map.ofEntries(
                    Map.entry("missionConfiguration", "Viasat_Configuration"),
                    Map.entry("providerName", "VIASAT")
                ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const contactProfile = new azure_native.orbital.ContactProfile("contactProfile", {
    autoTrackingConfiguration: azure_native.orbital.AutoTrackingConfiguration.Disabled,
    contactProfileName: "CONTOSO-CP",
    eventHubUri: "/subscriptions/c1be1141-a7c9-4aac-9608-3c2e2f1152c3/resourceGroups/contoso-Rgp/providers/Microsoft.EventHub/namespaces/contosoHub/eventhubs/contosoHub",
    links: [
        {
            channels: [{
                bandwidthMHz: 2,
                centerFrequencyMHz: 2250,
                endPoint: {
                    endPointName: "ContosoTest_Uplink",
                    ipAddress: "10.1.0.4",
                    port: "50000",
                    protocol: "TCP",
                },
                name: "contoso-uplink-channel",
            }],
            direction: "Uplink",
            eirpdBW: 45,
            gainOverTemperature: 0,
            name: "contoso-uplink",
            polarization: "LHCP",
        },
        {
            channels: [{
                bandwidthMHz: 15,
                centerFrequencyMHz: 8160,
                endPoint: {
                    endPointName: "ContosoTest_Downlink",
                    ipAddress: "10.1.0.5",
                    port: "50001",
                    protocol: "UDP",
                },
                name: "contoso-downlink-channel",
            }],
            direction: "Downlink",
            eirpdBW: 0,
            gainOverTemperature: 25,
            name: "contoso-downlink",
            polarization: "RHCP",
        },
    ],
    location: "eastus2",
    minimumElevationDegrees: 5,
    minimumViableContactDuration: "PT1M",
    networkConfiguration: {
        subnetId: "/subscriptions/c1be1141-a7c9-4aac-9608-3c2e2f1152c3/resourceGroups/contoso-Rgp/providers/Microsoft.Network/virtualNetworks/contoso-vnet/subnets/orbital-delegated-subnet",
    },
    resourceGroupName: "contoso-Rgp",
    thirdPartyConfigurations: [
        {
            missionConfiguration: "Ksat_MissionConfiguration",
            providerName: "KSAT",
        },
        {
            missionConfiguration: "Viasat_Configuration",
            providerName: "VIASAT",
        },
    ],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

contact_profile = azure_native.orbital.ContactProfile("contactProfile",
    auto_tracking_configuration=azure_native.orbital.AutoTrackingConfiguration.DISABLED,
    contact_profile_name="CONTOSO-CP",
    event_hub_uri="/subscriptions/c1be1141-a7c9-4aac-9608-3c2e2f1152c3/resourceGroups/contoso-Rgp/providers/Microsoft.EventHub/namespaces/contosoHub/eventhubs/contosoHub",
    links=[
        {
            "channels": [{
                "bandwidthMHz": 2,
                "centerFrequencyMHz": 2250,
                "endPoint": azure_native.orbital.EndPointArgs(
                    end_point_name="ContosoTest_Uplink",
                    ip_address="10.1.0.4",
                    port="50000",
                    protocol="TCP",
                ),
                "name": "contoso-uplink-channel",
            }],
            "direction": "Uplink",
            "eirpdBW": 45,
            "gainOverTemperature": 0,
            "name": "contoso-uplink",
            "polarization": "LHCP",
        },
        {
            "channels": [{
                "bandwidthMHz": 15,
                "centerFrequencyMHz": 8160,
                "endPoint": azure_native.orbital.EndPointArgs(
                    end_point_name="ContosoTest_Downlink",
                    ip_address="10.1.0.5",
                    port="50001",
                    protocol="UDP",
                ),
                "name": "contoso-downlink-channel",
            }],
            "direction": "Downlink",
            "eirpdBW": 0,
            "gainOverTemperature": 25,
            "name": "contoso-downlink",
            "polarization": "RHCP",
        },
    ],
    location="eastus2",
    minimum_elevation_degrees=5,
    minimum_viable_contact_duration="PT1M",
    network_configuration=azure_native.orbital.ContactProfilesPropertiesNetworkConfigurationArgs(
        subnet_id="/subscriptions/c1be1141-a7c9-4aac-9608-3c2e2f1152c3/resourceGroups/contoso-Rgp/providers/Microsoft.Network/virtualNetworks/contoso-vnet/subnets/orbital-delegated-subnet",
    ),
    resource_group_name="contoso-Rgp",
    third_party_configurations=[
        azure_native.orbital.ContactProfileThirdPartyConfigurationArgs(
            mission_configuration="Ksat_MissionConfiguration",
            provider_name="KSAT",
        ),
        azure_native.orbital.ContactProfileThirdPartyConfigurationArgs(
            mission_configuration="Viasat_Configuration",
            provider_name="VIASAT",
        ),
    ])

```

```yaml
resources:
  contactProfile:
    type: azure-native:orbital:ContactProfile
    properties:
      autoTrackingConfiguration: disabled
      contactProfileName: CONTOSO-CP
      eventHubUri: /subscriptions/c1be1141-a7c9-4aac-9608-3c2e2f1152c3/resourceGroups/contoso-Rgp/providers/Microsoft.EventHub/namespaces/contosoHub/eventhubs/contosoHub
      links:
        - channels:
            - bandwidthMHz: 2
              centerFrequencyMHz: 2250
              endPoint:
                endPointName: ContosoTest_Uplink
                ipAddress: 10.1.0.4
                port: '50000'
                protocol: TCP
              name: contoso-uplink-channel
          direction: Uplink
          eirpdBW: 45
          gainOverTemperature: 0
          name: contoso-uplink
          polarization: LHCP
        - channels:
            - bandwidthMHz: 15
              centerFrequencyMHz: 8160
              endPoint:
                endPointName: ContosoTest_Downlink
                ipAddress: 10.1.0.5
                port: '50001'
                protocol: UDP
              name: contoso-downlink-channel
          direction: Downlink
          eirpdBW: 0
          gainOverTemperature: 25
          name: contoso-downlink
          polarization: RHCP
      location: eastus2
      minimumElevationDegrees: 5
      minimumViableContactDuration: PT1M
      networkConfiguration:
        subnetId: /subscriptions/c1be1141-a7c9-4aac-9608-3c2e2f1152c3/resourceGroups/contoso-Rgp/providers/Microsoft.Network/virtualNetworks/contoso-vnet/subnets/orbital-delegated-subnet
      resourceGroupName: contoso-Rgp
      thirdPartyConfigurations:
        - missionConfiguration: Ksat_MissionConfiguration
          providerName: KSAT
        - missionConfiguration: Viasat_Configuration
          providerName: VIASAT

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:orbital:ContactProfile CONTOSO-CP /subscriptions/c1be1141-a7c9-4aac-9608-3c2e2f1152c3/resourceGroups/contoso-Rgp/providers/Microsoft.Orbital/contactProfiles/CONTOSO-CP 
```
