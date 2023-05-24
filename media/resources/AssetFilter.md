An Asset Filter.
API Version: 2022-08-01.
Previous API Version: 2020-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create an Asset Filter
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var assetFilter = new AzureNative.Media.AssetFilter("assetFilter", new()
    {
        AccountName = "contosomedia",
        AssetName = "ClimbingMountRainer",
        FilterName = "newAssetFilter",
        FirstQuality = new AzureNative.Media.Inputs.FirstQualityArgs
        {
            Bitrate = 128000,
        },
        PresentationTimeRange = new AzureNative.Media.Inputs.PresentationTimeRangeArgs
        {
            EndTimestamp = 170000000,
            ForceEndTimestamp = false,
            LiveBackoffDuration = 0,
            PresentationWindowDuration = 9223372036854774784,
            StartTimestamp = 0,
            Timescale = 10000000,
        },
        ResourceGroupName = "contosorg",
        Tracks = new[]
        {
            new AzureNative.Media.Inputs.FilterTrackSelectionArgs
            {
                TrackSelections = new[]
                {
                    new AzureNative.Media.Inputs.FilterTrackPropertyConditionArgs
                    {
                        Operation = "Equal",
                        Property = "Type",
                        Value = "Audio",
                    },
                    new AzureNative.Media.Inputs.FilterTrackPropertyConditionArgs
                    {
                        Operation = "NotEqual",
                        Property = "Language",
                        Value = "en",
                    },
                    new AzureNative.Media.Inputs.FilterTrackPropertyConditionArgs
                    {
                        Operation = "NotEqual",
                        Property = "FourCC",
                        Value = "EC-3",
                    },
                },
            },
            new AzureNative.Media.Inputs.FilterTrackSelectionArgs
            {
                TrackSelections = new[]
                {
                    new AzureNative.Media.Inputs.FilterTrackPropertyConditionArgs
                    {
                        Operation = "Equal",
                        Property = "Type",
                        Value = "Video",
                    },
                    new AzureNative.Media.Inputs.FilterTrackPropertyConditionArgs
                    {
                        Operation = "Equal",
                        Property = "Bitrate",
                        Value = "3000000-5000000",
                    },
                },
            },
        },
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
		_, err := media.NewAssetFilter(ctx, "assetFilter", &media.AssetFilterArgs{
			AccountName: pulumi.String("contosomedia"),
			AssetName:   pulumi.String("ClimbingMountRainer"),
			FilterName:  pulumi.String("newAssetFilter"),
			FirstQuality: &media.FirstQualityArgs{
				Bitrate: pulumi.Int(128000),
			},
			PresentationTimeRange: &media.PresentationTimeRangeArgs{
				EndTimestamp:               pulumi.Float64(170000000),
				ForceEndTimestamp:          pulumi.Bool(false),
				LiveBackoffDuration:        pulumi.Float64(0),
				PresentationWindowDuration: pulumi.Float64(9223372036854774784),
				StartTimestamp:             pulumi.Float64(0),
				Timescale:                  pulumi.Float64(10000000),
			},
			ResourceGroupName: pulumi.String("contosorg"),
			Tracks: []media.FilterTrackSelectionArgs{
				{
					TrackSelections: media.FilterTrackPropertyConditionArray{
						{
							Operation: pulumi.String("Equal"),
							Property:  pulumi.String("Type"),
							Value:     pulumi.String("Audio"),
						},
						{
							Operation: pulumi.String("NotEqual"),
							Property:  pulumi.String("Language"),
							Value:     pulumi.String("en"),
						},
						{
							Operation: pulumi.String("NotEqual"),
							Property:  pulumi.String("FourCC"),
							Value:     pulumi.String("EC-3"),
						},
					},
				},
				{
					TrackSelections: media.FilterTrackPropertyConditionArray{
						{
							Operation: pulumi.String("Equal"),
							Property:  pulumi.String("Type"),
							Value:     pulumi.String("Video"),
						},
						{
							Operation: pulumi.String("Equal"),
							Property:  pulumi.String("Bitrate"),
							Value:     pulumi.String("3000000-5000000"),
						},
					},
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
import com.pulumi.azurenative.media.AssetFilter;
import com.pulumi.azurenative.media.AssetFilterArgs;
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
        var assetFilter = new AssetFilter("assetFilter", AssetFilterArgs.builder()        
            .accountName("contosomedia")
            .assetName("ClimbingMountRainer")
            .filterName("newAssetFilter")
            .firstQuality(Map.of("bitrate", 128000))
            .presentationTimeRange(Map.ofEntries(
                Map.entry("endTimestamp", 170000000),
                Map.entry("forceEndTimestamp", false),
                Map.entry("liveBackoffDuration", 0),
                Map.entry("presentationWindowDuration", 9223372036854774784),
                Map.entry("startTimestamp", 0),
                Map.entry("timescale", 10000000)
            ))
            .resourceGroupName("contosorg")
            .tracks(            
                Map.of("trackSelections",                 
                    Map.ofEntries(
                        Map.entry("operation", "Equal"),
                        Map.entry("property", "Type"),
                        Map.entry("value", "Audio")
                    ),
                    Map.ofEntries(
                        Map.entry("operation", "NotEqual"),
                        Map.entry("property", "Language"),
                        Map.entry("value", "en")
                    ),
                    Map.ofEntries(
                        Map.entry("operation", "NotEqual"),
                        Map.entry("property", "FourCC"),
                        Map.entry("value", "EC-3")
                    )),
                Map.of("trackSelections",                 
                    Map.ofEntries(
                        Map.entry("operation", "Equal"),
                        Map.entry("property", "Type"),
                        Map.entry("value", "Video")
                    ),
                    Map.ofEntries(
                        Map.entry("operation", "Equal"),
                        Map.entry("property", "Bitrate"),
                        Map.entry("value", "3000000-5000000")
                    )))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const assetFilter = new azure_native.media.AssetFilter("assetFilter", {
    accountName: "contosomedia",
    assetName: "ClimbingMountRainer",
    filterName: "newAssetFilter",
    firstQuality: {
        bitrate: 128000,
    },
    presentationTimeRange: {
        endTimestamp: 170000000,
        forceEndTimestamp: false,
        liveBackoffDuration: 0,
        presentationWindowDuration: 9223372036854774784,
        startTimestamp: 0,
        timescale: 10000000,
    },
    resourceGroupName: "contosorg",
    tracks: [
        {
            trackSelections: [
                {
                    operation: "Equal",
                    property: "Type",
                    value: "Audio",
                },
                {
                    operation: "NotEqual",
                    property: "Language",
                    value: "en",
                },
                {
                    operation: "NotEqual",
                    property: "FourCC",
                    value: "EC-3",
                },
            ],
        },
        {
            trackSelections: [
                {
                    operation: "Equal",
                    property: "Type",
                    value: "Video",
                },
                {
                    operation: "Equal",
                    property: "Bitrate",
                    value: "3000000-5000000",
                },
            ],
        },
    ],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

asset_filter = azure_native.media.AssetFilter("assetFilter",
    account_name="contosomedia",
    asset_name="ClimbingMountRainer",
    filter_name="newAssetFilter",
    first_quality=azure_native.media.FirstQualityArgs(
        bitrate=128000,
    ),
    presentation_time_range=azure_native.media.PresentationTimeRangeArgs(
        end_timestamp=170000000,
        force_end_timestamp=False,
        live_backoff_duration=0,
        presentation_window_duration=9223372036854774784,
        start_timestamp=0,
        timescale=10000000,
    ),
    resource_group_name="contosorg",
    tracks=[
        {
            "trackSelections": [
                azure_native.media.FilterTrackPropertyConditionArgs(
                    operation="Equal",
                    property="Type",
                    value="Audio",
                ),
                azure_native.media.FilterTrackPropertyConditionArgs(
                    operation="NotEqual",
                    property="Language",
                    value="en",
                ),
                azure_native.media.FilterTrackPropertyConditionArgs(
                    operation="NotEqual",
                    property="FourCC",
                    value="EC-3",
                ),
            ],
        },
        {
            "trackSelections": [
                azure_native.media.FilterTrackPropertyConditionArgs(
                    operation="Equal",
                    property="Type",
                    value="Video",
                ),
                azure_native.media.FilterTrackPropertyConditionArgs(
                    operation="Equal",
                    property="Bitrate",
                    value="3000000-5000000",
                ),
            ],
        },
    ])

```

```yaml
resources:
  assetFilter:
    type: azure-native:media:AssetFilter
    properties:
      accountName: contosomedia
      assetName: ClimbingMountRainer
      filterName: newAssetFilter
      firstQuality:
        bitrate: 128000
      presentationTimeRange:
        endTimestamp: 1.7e+08
        forceEndTimestamp: false
        liveBackoffDuration: 0
        presentationWindowDuration: 9.223372036854775e+18
        startTimestamp: 0
        timescale: 1e+07
      resourceGroupName: contosorg
      tracks:
        - trackSelections:
            - operation: Equal
              property: Type
              value: Audio
            - operation: NotEqual
              property: Language
              value: en
            - operation: NotEqual
              property: FourCC
              value: EC-3
        - trackSelections:
            - operation: Equal
              property: Type
              value: Video
            - operation: Equal
              property: Bitrate
              value: 3000000-5000000

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:media:AssetFilter newAssetFilter /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/contosorg/providers/Microsoft.Media/mediaservices/contosomedia/assets/ClimbingMountRainer/assetFilters/newAssetFilter 
```
