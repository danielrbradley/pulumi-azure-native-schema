Customer creates a spacecraft resource to schedule a contact.
API Version: 2022-11-01.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a spacecraft
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var spacecraft = new AzureNative.Orbital.Spacecraft("spacecraft", new()
    {
        Links = new[]
        {
            new AzureNative.Orbital.Inputs.SpacecraftLinkArgs
            {
                BandwidthMHz = 2,
                CenterFrequencyMHz = 2250,
                Direction = "Uplink",
                Name = "uplink_lhcp1",
                Polarization = "LHCP",
            },
            new AzureNative.Orbital.Inputs.SpacecraftLinkArgs
            {
                BandwidthMHz = 15,
                CenterFrequencyMHz = 8160,
                Direction = "Downlink",
                Name = "downlink_rhcp1",
                Polarization = "RHCP",
            },
        },
        Location = "eastus2",
        NoradId = "36411",
        ResourceGroupName = "contoso-Rgp",
        SpacecraftName = "CONTOSO_SAT",
        TitleLine = "CONTOSO_SAT",
        TleLine1 = "1 27424U 02022A   22167.05119303  .00000638  00000+0  15103-3 0  9994",
        TleLine2 = "2 27424  98.2477 108.9546 0000928  92.9194 327.0802 14.57300770 69982",
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
		_, err := orbital.NewSpacecraft(ctx, "spacecraft", &orbital.SpacecraftArgs{
			Links: []orbital.SpacecraftLinkArgs{
				{
					BandwidthMHz:       pulumi.Float64(2),
					CenterFrequencyMHz: pulumi.Float64(2250),
					Direction:          pulumi.String("Uplink"),
					Name:               pulumi.String("uplink_lhcp1"),
					Polarization:       pulumi.String("LHCP"),
				},
				{
					BandwidthMHz:       pulumi.Float64(15),
					CenterFrequencyMHz: pulumi.Float64(8160),
					Direction:          pulumi.String("Downlink"),
					Name:               pulumi.String("downlink_rhcp1"),
					Polarization:       pulumi.String("RHCP"),
				},
			},
			Location:          pulumi.String("eastus2"),
			NoradId:           pulumi.String("36411"),
			ResourceGroupName: pulumi.String("contoso-Rgp"),
			SpacecraftName:    pulumi.String("CONTOSO_SAT"),
			TitleLine:         pulumi.String("CONTOSO_SAT"),
			TleLine1:          pulumi.String("1 27424U 02022A   22167.05119303  .00000638  00000+0  15103-3 0  9994"),
			TleLine2:          pulumi.String("2 27424  98.2477 108.9546 0000928  92.9194 327.0802 14.57300770 69982"),
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
import com.pulumi.azurenative.orbital.Spacecraft;
import com.pulumi.azurenative.orbital.SpacecraftArgs;
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
        var spacecraft = new Spacecraft("spacecraft", SpacecraftArgs.builder()        
            .links(            
                Map.ofEntries(
                    Map.entry("bandwidthMHz", 2),
                    Map.entry("centerFrequencyMHz", 2250),
                    Map.entry("direction", "Uplink"),
                    Map.entry("name", "uplink_lhcp1"),
                    Map.entry("polarization", "LHCP")
                ),
                Map.ofEntries(
                    Map.entry("bandwidthMHz", 15),
                    Map.entry("centerFrequencyMHz", 8160),
                    Map.entry("direction", "Downlink"),
                    Map.entry("name", "downlink_rhcp1"),
                    Map.entry("polarization", "RHCP")
                ))
            .location("eastus2")
            .noradId("36411")
            .resourceGroupName("contoso-Rgp")
            .spacecraftName("CONTOSO_SAT")
            .titleLine("CONTOSO_SAT")
            .tleLine1("1 27424U 02022A   22167.05119303  .00000638  00000+0  15103-3 0  9994")
            .tleLine2("2 27424  98.2477 108.9546 0000928  92.9194 327.0802 14.57300770 69982")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const spacecraft = new azure_native.orbital.Spacecraft("spacecraft", {
    links: [
        {
            bandwidthMHz: 2,
            centerFrequencyMHz: 2250,
            direction: "Uplink",
            name: "uplink_lhcp1",
            polarization: "LHCP",
        },
        {
            bandwidthMHz: 15,
            centerFrequencyMHz: 8160,
            direction: "Downlink",
            name: "downlink_rhcp1",
            polarization: "RHCP",
        },
    ],
    location: "eastus2",
    noradId: "36411",
    resourceGroupName: "contoso-Rgp",
    spacecraftName: "CONTOSO_SAT",
    titleLine: "CONTOSO_SAT",
    tleLine1: "1 27424U 02022A   22167.05119303  .00000638  00000+0  15103-3 0  9994",
    tleLine2: "2 27424  98.2477 108.9546 0000928  92.9194 327.0802 14.57300770 69982",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

spacecraft = azure_native.orbital.Spacecraft("spacecraft",
    links=[
        azure_native.orbital.SpacecraftLinkArgs(
            bandwidth_m_hz=2,
            center_frequency_m_hz=2250,
            direction="Uplink",
            name="uplink_lhcp1",
            polarization="LHCP",
        ),
        azure_native.orbital.SpacecraftLinkArgs(
            bandwidth_m_hz=15,
            center_frequency_m_hz=8160,
            direction="Downlink",
            name="downlink_rhcp1",
            polarization="RHCP",
        ),
    ],
    location="eastus2",
    norad_id="36411",
    resource_group_name="contoso-Rgp",
    spacecraft_name="CONTOSO_SAT",
    title_line="CONTOSO_SAT",
    tle_line1="1 27424U 02022A   22167.05119303  .00000638  00000+0  15103-3 0  9994",
    tle_line2="2 27424  98.2477 108.9546 0000928  92.9194 327.0802 14.57300770 69982")

```

```yaml
resources:
  spacecraft:
    type: azure-native:orbital:Spacecraft
    properties:
      links:
        - bandwidthMHz: 2
          centerFrequencyMHz: 2250
          direction: Uplink
          name: uplink_lhcp1
          polarization: LHCP
        - bandwidthMHz: 15
          centerFrequencyMHz: 8160
          direction: Downlink
          name: downlink_rhcp1
          polarization: RHCP
      location: eastus2
      noradId: '36411'
      resourceGroupName: contoso-Rgp
      spacecraftName: CONTOSO_SAT
      titleLine: CONTOSO_SAT
      tleLine1: 1 27424U 02022A   22167.05119303  .00000638  00000+0  15103-3 0  9994
      tleLine2: 2 27424  98.2477 108.9546 0000928  92.9194 327.0802 14.57300770 69982

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:orbital:Spacecraft CONTOSO_SAT /subscriptions/c1be1141-a7c9-4aac-9608-3c2e2f1152c3/resourceGroups/contoso-Rgp/providers/Microsoft.Orbital/spacecrafts/CONTOSO_SAT 
```
