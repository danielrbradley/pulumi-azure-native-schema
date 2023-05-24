A Job resource type. The progress and state can be obtained by polling a Job or subscribing to events using EventGrid.
API Version: 2022-07-01.
Previous API Version: 2020-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create a Job
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var job = new AzureNative.Media.Job("job", new()
    {
        AccountName = "contosomedia",
        CorrelationData = 
        {
            { "Key 2", "Value 2" },
            { "key1", "value1" },
        },
        Input = new AzureNative.Media.Inputs.JobInputAssetArgs
        {
            AssetName = "job1-InputAsset",
            OdataType = "#Microsoft.Media.JobInputAsset",
        },
        JobName = "job1",
        Outputs = new[]
        {
            
            {
                { "assetName", "job1-OutputAsset" },
                { "odataType", "#Microsoft.Media.JobOutputAsset" },
            },
        },
        ResourceGroupName = "contosoresources",
        TransformName = "exampleTransform",
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
		_, err := media.NewJob(ctx, "job", &media.JobArgs{
			AccountName: pulumi.String("contosomedia"),
			CorrelationData: pulumi.StringMap{
				"Key 2": pulumi.String("Value 2"),
				"key1":  pulumi.String("value1"),
			},
			Input: media.JobInputAsset{
				AssetName: "job1-InputAsset",
				OdataType: "#Microsoft.Media.JobInputAsset",
			},
			JobName: pulumi.String("job1"),
			Outputs: []media.JobOutputAssetArgs{
				{
					AssetName: pulumi.String("job1-OutputAsset"),
					OdataType: pulumi.String("#Microsoft.Media.JobOutputAsset"),
				},
			},
			ResourceGroupName: pulumi.String("contosoresources"),
			TransformName:     pulumi.String("exampleTransform"),
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
import com.pulumi.azurenative.media.Job;
import com.pulumi.azurenative.media.JobArgs;
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
        var job = new Job("job", JobArgs.builder()        
            .accountName("contosomedia")
            .correlationData(Map.ofEntries(
                Map.entry("Key 2", "Value 2"),
                Map.entry("key1", "value1")
            ))
            .input(Map.ofEntries(
                Map.entry("assetName", "job1-InputAsset"),
                Map.entry("odataType", "#Microsoft.Media.JobInputAsset")
            ))
            .jobName("job1")
            .outputs(Map.ofEntries(
                Map.entry("assetName", "job1-OutputAsset"),
                Map.entry("odataType", "#Microsoft.Media.JobOutputAsset")
            ))
            .resourceGroupName("contosoresources")
            .transformName("exampleTransform")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const job = new azure_native.media.Job("job", {
    accountName: "contosomedia",
    correlationData: {
        "Key 2": "Value 2",
        key1: "value1",
    },
    input: {
        assetName: "job1-InputAsset",
        odataType: "#Microsoft.Media.JobInputAsset",
    },
    jobName: "job1",
    outputs: [{
        assetName: "job1-OutputAsset",
        odataType: "#Microsoft.Media.JobOutputAsset",
    }],
    resourceGroupName: "contosoresources",
    transformName: "exampleTransform",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

job = azure_native.media.Job("job",
    account_name="contosomedia",
    correlation_data={
        "Key 2": "Value 2",
        "key1": "value1",
    },
    input=azure_native.media.JobInputAssetArgs(
        asset_name="job1-InputAsset",
        odata_type="#Microsoft.Media.JobInputAsset",
    ),
    job_name="job1",
    outputs=[azure_native.media.JobOutputAssetResponseArgs(
        asset_name="job1-OutputAsset",
        odata_type="#Microsoft.Media.JobOutputAsset",
    )],
    resource_group_name="contosoresources",
    transform_name="exampleTransform")

```

```yaml
resources:
  job:
    type: azure-native:media:Job
    properties:
      accountName: contosomedia
      correlationData:
        Key 2: Value 2
        key1: value1
      input:
        assetName: job1-InputAsset
        odataType: '#Microsoft.Media.JobInputAsset'
      jobName: job1
      outputs:
        - assetName: job1-OutputAsset
          odataType: '#Microsoft.Media.JobOutputAsset'
      resourceGroupName: contosoresources
      transformName: exampleTransform

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:media:Job job1 /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/contosoresources/providers/Microsoft.Media/mediaservices/contosomedia/transforms/exampleTransform/jobs/job1 
```
