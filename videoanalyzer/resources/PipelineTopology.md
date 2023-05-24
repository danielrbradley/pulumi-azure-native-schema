Pipeline topology describes the processing steps to be applied when processing content for a particular outcome. The topology should be defined according to the scenario to be achieved and can be reused across many pipeline instances which share the same processing characteristics. For instance, a pipeline topology which captures content from a RTSP camera and archives the content can be reused across many different cameras, as long as the same processing is to be applied across all the cameras. Individual instance properties can be defined through the use of user-defined parameters, which allow for a topology to be parameterized. This allows  individual pipelines refer to different values, such as individual cameras' RTSP endpoints and credentials. Overall a topology is composed of the following:

  - Parameters: list of user defined parameters that can be references across the topology nodes.
  - Sources: list of one or more data sources nodes such as an RTSP source which allows for content to be ingested from cameras.
  - Processors: list of nodes which perform data analysis or transformations.
  - Sinks: list of one or more data sinks which allow for data to be stored or exported to other destinations.
API Version: 2021-11-01-preview.
Previous API Version: 2021-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a pipeline topology with an Rtsp source and video sink.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var pipelineTopology = new AzureNative.VideoAnalyzer.PipelineTopology("pipelineTopology", new()
    {
        AccountName = "testaccount2",
        Description = "Pipeline Topology 1 Description",
        Kind = "Live",
        Parameters = new[]
        {
            new AzureNative.VideoAnalyzer.Inputs.ParameterDeclarationArgs
            {
                Default = "rtsp://microsoft.com/video.mp4",
                Description = "rtsp source url parameter",
                Name = "rtspUrlParameter",
                Type = "String",
            },
            new AzureNative.VideoAnalyzer.Inputs.ParameterDeclarationArgs
            {
                Default = "password",
                Description = "rtsp source password parameter",
                Name = "rtspPasswordParameter",
                Type = "SecretString",
            },
        },
        PipelineTopologyName = "pipelineTopology1",
        ResourceGroupName = "testrg",
        Sinks = new[]
        {
            
            {
                { "inputs", new[]
                {
                    new AzureNative.VideoAnalyzer.Inputs.NodeInputArgs
                    {
                        NodeName = "rtspSource",
                    },
                } },
                { "name", "videoSink" },
                { "type", "#Microsoft.VideoAnalyzer.VideoSink" },
                { "videoCreationProperties", new AzureNative.VideoAnalyzer.Inputs.VideoCreationPropertiesArgs
                {
                    Description = "Parking lot south entrance",
                    SegmentLength = "PT30S",
                    Title = "Parking Lot (Camera 1)",
                } },
                { "videoName", "camera001" },
                { "videoPublishingOptions", new AzureNative.VideoAnalyzer.Inputs.VideoPublishingOptionsArgs
                {
                    DisableArchive = "false",
                    DisableRtspPublishing = "true",
                } },
            },
        },
        Sku = new AzureNative.VideoAnalyzer.Inputs.SkuArgs
        {
            Name = "Live_S1",
        },
        Sources = new[]
        {
            new AzureNative.VideoAnalyzer.Inputs.RtspSourceArgs
            {
                Endpoint = new AzureNative.VideoAnalyzer.Inputs.UnsecuredEndpointArgs
                {
                    Credentials = new AzureNative.VideoAnalyzer.Inputs.UsernamePasswordCredentialsArgs
                    {
                        Password = "${rtspPasswordParameter}",
                        Type = "#Microsoft.VideoAnalyzer.UsernamePasswordCredentials",
                        Username = "username",
                    },
                    Type = "#Microsoft.VideoAnalyzer.UnsecuredEndpoint",
                    Url = "${rtspUrlParameter}",
                },
                Name = "rtspSource",
                Transport = "Http",
                Type = "#Microsoft.VideoAnalyzer.RtspSource",
            },
        },
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
		_, err := videoanalyzer.NewPipelineTopology(ctx, "pipelineTopology", &videoanalyzer.PipelineTopologyArgs{
			AccountName: pulumi.String("testaccount2"),
			Description: pulumi.String("Pipeline Topology 1 Description"),
			Kind:        pulumi.String("Live"),
			Parameters: []videoanalyzer.ParameterDeclarationArgs{
				{
					Default:     pulumi.String("rtsp://microsoft.com/video.mp4"),
					Description: pulumi.String("rtsp source url parameter"),
					Name:        pulumi.String("rtspUrlParameter"),
					Type:        pulumi.String("String"),
				},
				{
					Default:     pulumi.String("password"),
					Description: pulumi.String("rtsp source password parameter"),
					Name:        pulumi.String("rtspPasswordParameter"),
					Type:        pulumi.String("SecretString"),
				},
			},
			PipelineTopologyName: pulumi.String("pipelineTopology1"),
			ResourceGroupName:    pulumi.String("testrg"),
			Sinks: []videoanalyzer.VideoSinkArgs{
				{
					Inputs: videoanalyzer.NodeInputArray{
						{
							NodeName: pulumi.String("rtspSource"),
						},
					},
					Name: pulumi.String("videoSink"),
					Type: pulumi.String("#Microsoft.VideoAnalyzer.VideoSink"),
					VideoCreationProperties: {
						Description:   pulumi.String("Parking lot south entrance"),
						SegmentLength: pulumi.String("PT30S"),
						Title:         pulumi.String("Parking Lot (Camera 1)"),
					},
					VideoName: pulumi.String("camera001"),
					VideoPublishingOptions: {
						DisableArchive:        pulumi.String("false"),
						DisableRtspPublishing: pulumi.String("true"),
					},
				},
			},
			Sku: &videoanalyzer.SkuArgs{
				Name: pulumi.String("Live_S1"),
			},
			Sources: pulumi.AnyArray{
				videoanalyzer.RtspSource{
					Endpoint: videoanalyzer.UnsecuredEndpoint{
						Credentials: videoanalyzer.UsernamePasswordCredentials{
							Password: "${rtspPasswordParameter}",
							Type:     "#Microsoft.VideoAnalyzer.UsernamePasswordCredentials",
							Username: "username",
						},
						Type: "#Microsoft.VideoAnalyzer.UnsecuredEndpoint",
						Url:  "${rtspUrlParameter}",
					},
					Name:      "rtspSource",
					Transport: "Http",
					Type:      "#Microsoft.VideoAnalyzer.RtspSource",
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
import com.pulumi.azurenative.videoanalyzer.PipelineTopology;
import com.pulumi.azurenative.videoanalyzer.PipelineTopologyArgs;
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
        var pipelineTopology = new PipelineTopology("pipelineTopology", PipelineTopologyArgs.builder()        
            .accountName("testaccount2")
            .description("Pipeline Topology 1 Description")
            .kind("Live")
            .parameters(            
                Map.ofEntries(
                    Map.entry("default", "rtsp://microsoft.com/video.mp4"),
                    Map.entry("description", "rtsp source url parameter"),
                    Map.entry("name", "rtspUrlParameter"),
                    Map.entry("type", "String")
                ),
                Map.ofEntries(
                    Map.entry("default", "password"),
                    Map.entry("description", "rtsp source password parameter"),
                    Map.entry("name", "rtspPasswordParameter"),
                    Map.entry("type", "SecretString")
                ))
            .pipelineTopologyName("pipelineTopology1")
            .resourceGroupName("testrg")
            .sinks(Map.ofEntries(
                Map.entry("inputs", Map.of("nodeName", "rtspSource")),
                Map.entry("name", "videoSink"),
                Map.entry("type", "#Microsoft.VideoAnalyzer.VideoSink"),
                Map.entry("videoCreationProperties", Map.ofEntries(
                    Map.entry("description", "Parking lot south entrance"),
                    Map.entry("segmentLength", "PT30S"),
                    Map.entry("title", "Parking Lot (Camera 1)")
                )),
                Map.entry("videoName", "camera001"),
                Map.entry("videoPublishingOptions", Map.ofEntries(
                    Map.entry("disableArchive", "false"),
                    Map.entry("disableRtspPublishing", "true")
                ))
            ))
            .sku(Map.of("name", "Live_S1"))
            .sources(Map.ofEntries(
                Map.entry("endpoint", Map.ofEntries(
                    Map.entry("credentials", Map.ofEntries(
                        Map.entry("password", "${rtspPasswordParameter}"),
                        Map.entry("type", "#Microsoft.VideoAnalyzer.UsernamePasswordCredentials"),
                        Map.entry("username", "username")
                    )),
                    Map.entry("type", "#Microsoft.VideoAnalyzer.UnsecuredEndpoint"),
                    Map.entry("url", "${rtspUrlParameter}")
                )),
                Map.entry("name", "rtspSource"),
                Map.entry("transport", "Http"),
                Map.entry("type", "#Microsoft.VideoAnalyzer.RtspSource")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const pipelineTopology = new azure_native.videoanalyzer.PipelineTopology("pipelineTopology", {
    accountName: "testaccount2",
    description: "Pipeline Topology 1 Description",
    kind: "Live",
    parameters: [
        {
            "default": "rtsp://microsoft.com/video.mp4",
            description: "rtsp source url parameter",
            name: "rtspUrlParameter",
            type: "String",
        },
        {
            "default": "password",
            description: "rtsp source password parameter",
            name: "rtspPasswordParameter",
            type: "SecretString",
        },
    ],
    pipelineTopologyName: "pipelineTopology1",
    resourceGroupName: "testrg",
    sinks: [{
        inputs: [{
            nodeName: "rtspSource",
        }],
        name: "videoSink",
        type: "#Microsoft.VideoAnalyzer.VideoSink",
        videoCreationProperties: {
            description: "Parking lot south entrance",
            segmentLength: "PT30S",
            title: "Parking Lot (Camera 1)",
        },
        videoName: "camera001",
        videoPublishingOptions: {
            disableArchive: "false",
            disableRtspPublishing: "true",
        },
    }],
    sku: {
        name: "Live_S1",
    },
    sources: [{
        endpoint: {
            credentials: {
                password: "${rtspPasswordParameter}",
                type: "#Microsoft.VideoAnalyzer.UsernamePasswordCredentials",
                username: "username",
            },
            type: "#Microsoft.VideoAnalyzer.UnsecuredEndpoint",
            url: "${rtspUrlParameter}",
        },
        name: "rtspSource",
        transport: "Http",
        type: "#Microsoft.VideoAnalyzer.RtspSource",
    }],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

pipeline_topology = azure_native.videoanalyzer.PipelineTopology("pipelineTopology",
    account_name="testaccount2",
    description="Pipeline Topology 1 Description",
    kind="Live",
    parameters=[
        azure_native.videoanalyzer.ParameterDeclarationArgs(
            default="rtsp://microsoft.com/video.mp4",
            description="rtsp source url parameter",
            name="rtspUrlParameter",
            type="String",
        ),
        azure_native.videoanalyzer.ParameterDeclarationArgs(
            default="password",
            description="rtsp source password parameter",
            name="rtspPasswordParameter",
            type="SecretString",
        ),
    ],
    pipeline_topology_name="pipelineTopology1",
    resource_group_name="testrg",
    sinks=[azure_native.videoanalyzer.VideoSinkResponseArgs(
        inputs=[azure_native.videoanalyzer.NodeInputArgs(
            node_name="rtspSource",
        )],
        name="videoSink",
        type="#Microsoft.VideoAnalyzer.VideoSink",
        video_creation_properties=azure_native.videoanalyzer.VideoCreationPropertiesArgs(
            description="Parking lot south entrance",
            segment_length="PT30S",
            title="Parking Lot (Camera 1)",
        ),
        video_name="camera001",
        video_publishing_options=azure_native.videoanalyzer.VideoPublishingOptionsArgs(
            disable_archive="false",
            disable_rtsp_publishing="true",
        ),
    )],
    sku=azure_native.videoanalyzer.SkuArgs(
        name="Live_S1",
    ),
    sources=[azure_native.videoanalyzer.RtspSourceArgs(
        endpoint=azure_native.videoanalyzer.UnsecuredEndpointArgs(
            credentials=azure_native.videoanalyzer.UsernamePasswordCredentialsArgs(
                password="${rtspPasswordParameter}",
                type="#Microsoft.VideoAnalyzer.UsernamePasswordCredentials",
                username="username",
            ),
            type="#Microsoft.VideoAnalyzer.UnsecuredEndpoint",
            url="${rtspUrlParameter}",
        ),
        name="rtspSource",
        transport="Http",
        type="#Microsoft.VideoAnalyzer.RtspSource",
    )])

```

```yaml
resources:
  pipelineTopology:
    type: azure-native:videoanalyzer:PipelineTopology
    properties:
      accountName: testaccount2
      description: Pipeline Topology 1 Description
      kind: Live
      parameters:
        - default: rtsp://microsoft.com/video.mp4
          description: rtsp source url parameter
          name: rtspUrlParameter
          type: String
        - default: password
          description: rtsp source password parameter
          name: rtspPasswordParameter
          type: SecretString
      pipelineTopologyName: pipelineTopology1
      resourceGroupName: testrg
      sinks:
        - inputs:
            - nodeName: rtspSource
          name: videoSink
          type: '#Microsoft.VideoAnalyzer.VideoSink'
          videoCreationProperties:
            description: Parking lot south entrance
            segmentLength: PT30S
            title: Parking Lot (Camera 1)
          videoName: camera001
          videoPublishingOptions:
            disableArchive: 'false'
            disableRtspPublishing: 'true'
      sku:
        name: Live_S1
      sources:
        - endpoint:
            credentials:
              password: ${rtspPasswordParameter}
              type: '#Microsoft.VideoAnalyzer.UsernamePasswordCredentials'
              username: username
            type: '#Microsoft.VideoAnalyzer.UnsecuredEndpoint'
            url: ${rtspUrlParameter}
          name: rtspSource
          transport: Http
          type: '#Microsoft.VideoAnalyzer.RtspSource'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:videoanalyzer:PipelineTopology pipelineTopology1 /subscriptions/591e76c3-3e97-44db-879c-3e2b12961b62/resourceGroups/testrg/providers/Microsoft.Media/videoAnalyzers/testaccount2/pipelineTopologies/pipelineTopology1 
```
