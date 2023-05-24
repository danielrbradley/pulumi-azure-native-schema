The Live Output.
API Version: 2022-11-01.
Previous API Version: 2020-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a LiveOutput
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var liveOutput = new AzureNative.Media.LiveOutput("liveOutput", new()
    {
        AccountName = "slitestmedia10",
        ArchiveWindowLength = "PT5M",
        AssetName = "6f3264f5-a189-48b4-a29a-a40f22575212",
        Description = "test live output 1",
        Hls = new AzureNative.Media.Inputs.HlsArgs
        {
            FragmentsPerTsSegment = 5,
        },
        LiveEventName = "myLiveEvent1",
        LiveOutputName = "myLiveOutput1",
        ManifestName = "testmanifest",
        ResourceGroupName = "mediaresources",
        RewindWindowLength = "PT4M",
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
		_, err := media.NewLiveOutput(ctx, "liveOutput", &media.LiveOutputArgs{
			AccountName:         pulumi.String("slitestmedia10"),
			ArchiveWindowLength: pulumi.String("PT5M"),
			AssetName:           pulumi.String("6f3264f5-a189-48b4-a29a-a40f22575212"),
			Description:         pulumi.String("test live output 1"),
			Hls: &media.HlsArgs{
				FragmentsPerTsSegment: pulumi.Int(5),
			},
			LiveEventName:      pulumi.String("myLiveEvent1"),
			LiveOutputName:     pulumi.String("myLiveOutput1"),
			ManifestName:       pulumi.String("testmanifest"),
			ResourceGroupName:  pulumi.String("mediaresources"),
			RewindWindowLength: pulumi.String("PT4M"),
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
import com.pulumi.azurenative.media.LiveOutput;
import com.pulumi.azurenative.media.LiveOutputArgs;
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
        var liveOutput = new LiveOutput("liveOutput", LiveOutputArgs.builder()        
            .accountName("slitestmedia10")
            .archiveWindowLength("PT5M")
            .assetName("6f3264f5-a189-48b4-a29a-a40f22575212")
            .description("test live output 1")
            .hls(Map.of("fragmentsPerTsSegment", 5))
            .liveEventName("myLiveEvent1")
            .liveOutputName("myLiveOutput1")
            .manifestName("testmanifest")
            .resourceGroupName("mediaresources")
            .rewindWindowLength("PT4M")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const liveOutput = new azure_native.media.LiveOutput("liveOutput", {
    accountName: "slitestmedia10",
    archiveWindowLength: "PT5M",
    assetName: "6f3264f5-a189-48b4-a29a-a40f22575212",
    description: "test live output 1",
    hls: {
        fragmentsPerTsSegment: 5,
    },
    liveEventName: "myLiveEvent1",
    liveOutputName: "myLiveOutput1",
    manifestName: "testmanifest",
    resourceGroupName: "mediaresources",
    rewindWindowLength: "PT4M",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

live_output = azure_native.media.LiveOutput("liveOutput",
    account_name="slitestmedia10",
    archive_window_length="PT5M",
    asset_name="6f3264f5-a189-48b4-a29a-a40f22575212",
    description="test live output 1",
    hls=azure_native.media.HlsArgs(
        fragments_per_ts_segment=5,
    ),
    live_event_name="myLiveEvent1",
    live_output_name="myLiveOutput1",
    manifest_name="testmanifest",
    resource_group_name="mediaresources",
    rewind_window_length="PT4M")

```

```yaml
resources:
  liveOutput:
    type: azure-native:media:LiveOutput
    properties:
      accountName: slitestmedia10
      archiveWindowLength: PT5M
      assetName: 6f3264f5-a189-48b4-a29a-a40f22575212
      description: test live output 1
      hls:
        fragmentsPerTsSegment: 5
      liveEventName: myLiveEvent1
      liveOutputName: myLiveOutput1
      manifestName: testmanifest
      resourceGroupName: mediaresources
      rewindWindowLength: PT4M

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:media:LiveOutput myLiveOutput1 /subscriptions/0a6ec948-5a62-437d-b9df-934dc7c1b722/resourceGroups/mediaresources/providers/Microsoft.Media/mediaservices/slitestmedia10/liveevents/myLiveEvent1/liveoutputs/myLiveOutput1 
```
