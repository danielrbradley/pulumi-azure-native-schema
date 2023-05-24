Pipeline job represents a unique instance of a batch topology, used for offline processing of selected portions of archived content.
API Version: 2021-11-01-preview.
Previous API Version: 2021-11-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a pipeline job
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var pipelineJob = new AzureNative.VideoAnalyzer.PipelineJob("pipelineJob", new()
    {
        AccountName = "testaccount2",
        Description = "Pipeline Job 1 Dsecription",
        Parameters = new[]
        {
            new AzureNative.VideoAnalyzer.Inputs.ParameterDefinitionArgs
            {
                Name = "timesequences",
                Value = "[[\"2020-10-05T03:30:00Z\", \"2020-10-05T04:30:00Z\"]]",
            },
            new AzureNative.VideoAnalyzer.Inputs.ParameterDefinitionArgs
            {
                Name = "videoSourceName",
                Value = "camera001",
            },
        },
        PipelineJobName = "pipelineJob1",
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
		_, err := videoanalyzer.NewPipelineJob(ctx, "pipelineJob", &videoanalyzer.PipelineJobArgs{
			AccountName: pulumi.String("testaccount2"),
			Description: pulumi.String("Pipeline Job 1 Dsecription"),
			Parameters: []videoanalyzer.ParameterDefinitionArgs{
				{
					Name:  pulumi.String("timesequences"),
					Value: pulumi.String("[[\"2020-10-05T03:30:00Z\", \"2020-10-05T04:30:00Z\"]]"),
				},
				{
					Name:  pulumi.String("videoSourceName"),
					Value: pulumi.String("camera001"),
				},
			},
			PipelineJobName:   pulumi.String("pipelineJob1"),
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
import com.pulumi.azurenative.videoanalyzer.PipelineJob;
import com.pulumi.azurenative.videoanalyzer.PipelineJobArgs;
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
        var pipelineJob = new PipelineJob("pipelineJob", PipelineJobArgs.builder()        
            .accountName("testaccount2")
            .description("Pipeline Job 1 Dsecription")
            .parameters(            
                Map.ofEntries(
                    Map.entry("name", "timesequences"),
                    Map.entry("value", "[[\"2020-10-05T03:30:00Z\", \"2020-10-05T04:30:00Z\"]]")
                ),
                Map.ofEntries(
                    Map.entry("name", "videoSourceName"),
                    Map.entry("value", "camera001")
                ))
            .pipelineJobName("pipelineJob1")
            .resourceGroupName("testrg")
            .topologyName("pipelinetopology1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const pipelineJob = new azure_native.videoanalyzer.PipelineJob("pipelineJob", {
    accountName: "testaccount2",
    description: "Pipeline Job 1 Dsecription",
    parameters: [
        {
            name: "timesequences",
            value: "[[\"2020-10-05T03:30:00Z\", \"2020-10-05T04:30:00Z\"]]",
        },
        {
            name: "videoSourceName",
            value: "camera001",
        },
    ],
    pipelineJobName: "pipelineJob1",
    resourceGroupName: "testrg",
    topologyName: "pipelinetopology1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

pipeline_job = azure_native.videoanalyzer.PipelineJob("pipelineJob",
    account_name="testaccount2",
    description="Pipeline Job 1 Dsecription",
    parameters=[
        azure_native.videoanalyzer.ParameterDefinitionArgs(
            name="timesequences",
            value="[[\"2020-10-05T03:30:00Z\", \"2020-10-05T04:30:00Z\"]]",
        ),
        azure_native.videoanalyzer.ParameterDefinitionArgs(
            name="videoSourceName",
            value="camera001",
        ),
    ],
    pipeline_job_name="pipelineJob1",
    resource_group_name="testrg",
    topology_name="pipelinetopology1")

```

```yaml
resources:
  pipelineJob:
    type: azure-native:videoanalyzer:PipelineJob
    properties:
      accountName: testaccount2
      description: Pipeline Job 1 Dsecription
      parameters:
        - name: timesequences
          value: '[["2020-10-05T03:30:00Z", "2020-10-05T04:30:00Z"]]'
        - name: videoSourceName
          value: camera001
      pipelineJobName: pipelineJob1
      resourceGroupName: testrg
      topologyName: pipelinetopology1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:videoanalyzer:PipelineJob pipelineJob1 /subscriptions/591e76c3-3e97-44db-879c-3e2b12961b62/resourceGroups/testrg/providers/Microsoft.Media/videoAnalyzers/testaccount2/pipelineJobs/pipelineJob1 
```
