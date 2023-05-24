Represents a video resource within Azure Video Analyzer. Videos can be ingested from RTSP cameras through live pipelines or can be created by exporting sequences from existing captured video through a pipeline job. Videos ingested through live pipelines can be streamed through Azure Video Analyzer Player Widget or compatible players. Exported videos can be downloaded as MP4 files.
API Version: 2021-11-01-preview.
Previous API Version: 2021-05-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Register video entity.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var video = new AzureNative.VideoAnalyzer.Video("video", new()
    {
        AccountName = "testaccount2",
        Description = "Sample Description 1",
        ResourceGroupName = "testrg",
        Title = "Sample Title 1",
        VideoName = "video1",
    });

});


```

```go
package main

import (
	videoanalyzer "github.com/pulumi/pulumi-azure-native-sdk/videoanalyzer"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := videoanalyzer.NewVideo(ctx, "video", &videoanalyzer.VideoArgs{
			AccountName:       pulumi.String("testaccount2"),
			Description:       pulumi.String("Sample Description 1"),
			ResourceGroupName: pulumi.String("testrg"),
			Title:             pulumi.String("Sample Title 1"),
			VideoName:         pulumi.String("video1"),
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
import com.pulumi.azurenative.videoanalyzer.Video;
import com.pulumi.azurenative.videoanalyzer.VideoArgs;
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
        var video = new Video("video", VideoArgs.builder()        
            .accountName("testaccount2")
            .description("Sample Description 1")
            .resourceGroupName("testrg")
            .title("Sample Title 1")
            .videoName("video1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const video = new azure_native.videoanalyzer.Video("video", {
    accountName: "testaccount2",
    description: "Sample Description 1",
    resourceGroupName: "testrg",
    title: "Sample Title 1",
    videoName: "video1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

video = azure_native.videoanalyzer.Video("video",
    account_name="testaccount2",
    description="Sample Description 1",
    resource_group_name="testrg",
    title="Sample Title 1",
    video_name="video1")

```

```yaml
resources:
  video:
    type: azure-native:videoanalyzer:Video
    properties:
      accountName: testaccount2
      description: Sample Description 1
      resourceGroupName: testrg
      title: Sample Title 1
      videoName: video1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:videoanalyzer:Video video1 /subscriptions/591e76c3-3e97-44db-879c-3e2b12961b62/resourceGroups/testrg/providers/Microsoft.Media/videoAnalyzers/testaccount2/videos/video1 
```
