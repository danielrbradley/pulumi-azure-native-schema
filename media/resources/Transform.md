A Transform encapsulates the rules or instructions for generating desired outputs from input media, such as by transcoding or by extracting insights. After the Transform is created, it can be applied to input media by creating Jobs.
API Version: 2022-07-01.
Previous API Version: 2020-05-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update a Transform
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var transform = new AzureNative.Media.Transform("transform", new()
    {
        AccountName = "contosomedia",
        Description = "Example Transform to illustrate create and update.",
        Outputs = new[]
        {
            new AzureNative.Media.Inputs.TransformOutputArgs
            {
                Preset = new AzureNative.Media.Inputs.BuiltInStandardEncoderPresetArgs
                {
                    OdataType = "#Microsoft.Media.BuiltInStandardEncoderPreset",
                    PresetName = "AdaptiveStreaming",
                },
            },
        },
        ResourceGroupName = "contosoresources",
        TransformName = "createdTransform",
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
		_, err := media.NewTransform(ctx, "transform", &media.TransformArgs{
			AccountName: pulumi.String("contosomedia"),
			Description: pulumi.String("Example Transform to illustrate create and update."),
			Outputs: []media.TransformOutputTypeArgs{
				{
					Preset: {
						OdataType:  "#Microsoft.Media.BuiltInStandardEncoderPreset",
						PresetName: "AdaptiveStreaming",
					},
				},
			},
			ResourceGroupName: pulumi.String("contosoresources"),
			TransformName:     pulumi.String("createdTransform"),
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
import com.pulumi.azurenative.media.Transform;
import com.pulumi.azurenative.media.TransformArgs;
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
        var transform = new Transform("transform", TransformArgs.builder()        
            .accountName("contosomedia")
            .description("Example Transform to illustrate create and update.")
            .outputs(Map.of("preset", Map.ofEntries(
                Map.entry("odataType", "#Microsoft.Media.BuiltInStandardEncoderPreset"),
                Map.entry("presetName", "AdaptiveStreaming")
            )))
            .resourceGroupName("contosoresources")
            .transformName("createdTransform")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const transform = new azure_native.media.Transform("transform", {
    accountName: "contosomedia",
    description: "Example Transform to illustrate create and update.",
    outputs: [{
        preset: {
            odataType: "#Microsoft.Media.BuiltInStandardEncoderPreset",
            presetName: "AdaptiveStreaming",
        },
    }],
    resourceGroupName: "contosoresources",
    transformName: "createdTransform",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

transform = azure_native.media.Transform("transform",
    account_name="contosomedia",
    description="Example Transform to illustrate create and update.",
    outputs=[azure_native.media.TransformOutputArgs(
        preset=azure_native.media.BuiltInStandardEncoderPresetArgs(
            odata_type="#Microsoft.Media.BuiltInStandardEncoderPreset",
            preset_name="AdaptiveStreaming",
        ),
    )],
    resource_group_name="contosoresources",
    transform_name="createdTransform")

```

```yaml
resources:
  transform:
    type: azure-native:media:Transform
    properties:
      accountName: contosomedia
      description: Example Transform to illustrate create and update.
      outputs:
        - preset:
            odataType: '#Microsoft.Media.BuiltInStandardEncoderPreset'
            presetName: AdaptiveStreaming
      resourceGroupName: contosoresources
      transformName: createdTransform

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:media:Transform createdTransform /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/contosoresources/providers/Microsoft.Media/mediaservices/contosomedia/transforms/createdTransform 
```
