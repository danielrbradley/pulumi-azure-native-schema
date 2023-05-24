Live pipeline represents a unique instance of a live topology, used for real-time ingestion, archiving and publishing of content for a unique RTSP camera.
API Version: 2021-11-01-preview.
Previous API Version: 2021-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a live pipeline
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var livePipeline = new AzureNative.VideoAnalyzer.LivePipeline("livePipeline", new()
    {
        AccountName = "testaccount2",
        BitrateKbps = 500,
        Description = "Live Pipeline 1 Description",
        LivePipelineName = "livePipeline1",
        Parameters = new[]
        {
            new AzureNative.VideoAnalyzer.Inputs.ParameterDefinitionArgs
            {
                Name = "rtspUrlParameter",
                Value = "rtsp://contoso.com/stream",
            },
        },
        ResourceGroupName = "testrg",
        TopologyName = "pipelinetopology1",
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
		_, err := videoanalyzer.NewLivePipeline(ctx, "livePipeline", &videoanalyzer.LivePipelineArgs{
			AccountName:      pulumi.String("testaccount2"),
			BitrateKbps:      pulumi.Int(500),
			Description:      pulumi.String("Live Pipeline 1 Description"),
			LivePipelineName: pulumi.String("livePipeline1"),
			Parameters: []videoanalyzer.ParameterDefinitionArgs{
				{
					Name:  pulumi.String("rtspUrlParameter"),
					Value: pulumi.String("rtsp://contoso.com/stream"),
				},
			},
			ResourceGroupName: pulumi.String("testrg"),
			TopologyName:      pulumi.String("pipelinetopology1"),
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
import com.pulumi.azurenative.videoanalyzer.LivePipeline;
import com.pulumi.azurenative.videoanalyzer.LivePipelineArgs;
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
        var livePipeline = new LivePipeline("livePipeline", LivePipelineArgs.builder()        
            .accountName("testaccount2")
            .bitrateKbps(500)
            .description("Live Pipeline 1 Description")
            .livePipelineName("livePipeline1")
            .parameters(Map.ofEntries(
                Map.entry("name", "rtspUrlParameter"),
                Map.entry("value", "rtsp://contoso.com/stream")
            ))
            .resourceGroupName("testrg")
            .topologyName("pipelinetopology1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const livePipeline = new azure_native.videoanalyzer.LivePipeline("livePipeline", {
    accountName: "testaccount2",
    bitrateKbps: 500,
    description: "Live Pipeline 1 Description",
    livePipelineName: "livePipeline1",
    parameters: [{
        name: "rtspUrlParameter",
        value: "rtsp://contoso.com/stream",
    }],
    resourceGroupName: "testrg",
    topologyName: "pipelinetopology1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

live_pipeline = azure_native.videoanalyzer.LivePipeline("livePipeline",
    account_name="testaccount2",
    bitrate_kbps=500,
    description="Live Pipeline 1 Description",
    live_pipeline_name="livePipeline1",
    parameters=[azure_native.videoanalyzer.ParameterDefinitionArgs(
        name="rtspUrlParameter",
        value="rtsp://contoso.com/stream",
    )],
    resource_group_name="testrg",
    topology_name="pipelinetopology1")

```

```yaml
resources:
  livePipeline:
    type: azure-native:videoanalyzer:LivePipeline
    properties:
      accountName: testaccount2
      bitrateKbps: 500
      description: Live Pipeline 1 Description
      livePipelineName: livePipeline1
      parameters:
        - name: rtspUrlParameter
          value: rtsp://contoso.com/stream
      resourceGroupName: testrg
      topologyName: pipelinetopology1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:videoanalyzer:LivePipeline livePipeline1 /subscriptions/591e76c3-3e97-44db-879c-3e2b12961b62/resourceGroups/testrg/providers/Microsoft.Media/videoAnalyzers/testaccount2/livePipelines/livePipeline1 
```
