An Asset Track resource.
API Version: 2022-08-01.
Previous API Version: 2021-11-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates a Track
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var track = new AzureNative.Media.Track("track", new()
    {
        AccountName = "contosomedia",
        AssetName = "ClimbingMountRainer",
        ResourceGroupName = "contosorg",
        Track = new AzureNative.Media.Inputs.TextTrackArgs
        {
            DisplayName = "A new track",
            FileName = "text3.ttml",
            OdataType = "#Microsoft.Media.TextTrack",
            PlayerVisibility = "Visible",
        },
        TrackName = "text3",
    });

});


```

```go
package main

import (
	media "github.com/pulumi/pulumi-azure-native-sdk/media"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := media.NewTrack(ctx, "track", &media.TrackArgs{
			AccountName:       pulumi.String("contosomedia"),
			AssetName:         pulumi.String("ClimbingMountRainer"),
			ResourceGroupName: pulumi.String("contosorg"),
			Track: media.TextTrack{
				DisplayName:      "A new track",
				FileName:         "text3.ttml",
				OdataType:        "#Microsoft.Media.TextTrack",
				PlayerVisibility: "Visible",
			},
			TrackName: pulumi.String("text3"),
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
import com.pulumi.azurenative.media.Track;
import com.pulumi.azurenative.media.TrackArgs;
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
        var track = new Track("track", TrackArgs.builder()        
            .accountName("contosomedia")
            .assetName("ClimbingMountRainer")
            .resourceGroupName("contosorg")
            .track(Map.ofEntries(
                Map.entry("displayName", "A new track"),
                Map.entry("fileName", "text3.ttml"),
                Map.entry("odataType", "#Microsoft.Media.TextTrack"),
                Map.entry("playerVisibility", "Visible")
            ))
            .trackName("text3")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const track = new azure_native.media.Track("track", {
    accountName: "contosomedia",
    assetName: "ClimbingMountRainer",
    resourceGroupName: "contosorg",
    track: {
        displayName: "A new track",
        fileName: "text3.ttml",
        odataType: "#Microsoft.Media.TextTrack",
        playerVisibility: "Visible",
    },
    trackName: "text3",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

track = azure_native.media.Track("track",
    account_name="contosomedia",
    asset_name="ClimbingMountRainer",
    resource_group_name="contosorg",
    track=azure_native.media.TextTrackArgs(
        display_name="A new track",
        file_name="text3.ttml",
        odata_type="#Microsoft.Media.TextTrack",
        player_visibility="Visible",
    ),
    track_name="text3")

```

```yaml
resources:
  track:
    type: azure-native:media:Track
    properties:
      accountName: contosomedia
      assetName: ClimbingMountRainer
      resourceGroupName: contosorg
      track:
        displayName: A new track
        fileName: text3.ttml
        odataType: '#Microsoft.Media.TextTrack'
        playerVisibility: Visible
      trackName: text3

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:media:Track text3 /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/contosorg/providers/Microsoft.Media/mediaservices/contosomedia/assets/ClimbingMountRainer/tracks/text3 
```
