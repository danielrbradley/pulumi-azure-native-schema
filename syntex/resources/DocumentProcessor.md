Document processor details
API Version: 2022-09-15-preview.
Previous API Version: 2022-09-15-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### DocumentProcessor_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var documentProcessor = new AzureNative.Syntex.DocumentProcessor("documentProcessor", new()
    {
        Location = "westus",
        ProcessorName = "myprocessor",
        Properties = new AzureNative.Syntex.Inputs.DocumentProcessorPropertiesArgs
        {
            SpoTenantId = "e9bb744b-9558-4dc6-9e50-a3297e3332fa",
            SpoTenantUrl = "https://test123.sharepoint.com",
        },
        ResourceGroupName = "mygroup",
        Tags = 
        {
            { "additionalProp1", "string1" },
            { "additionalProp2", "string2" },
            { "additionalProp3", "string3" },
        },
    });

});


```

```go
package main

import (
	syntex "github.com/pulumi/pulumi-azure-native-sdk/syntex"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := syntex.NewDocumentProcessor(ctx, "documentProcessor", &syntex.DocumentProcessorArgs{
			Location:      pulumi.String("westus"),
			ProcessorName: pulumi.String("myprocessor"),
			Properties: &syntex.DocumentProcessorPropertiesArgs{
				SpoTenantId:  pulumi.String("e9bb744b-9558-4dc6-9e50-a3297e3332fa"),
				SpoTenantUrl: pulumi.String("https://test123.sharepoint.com"),
			},
			ResourceGroupName: pulumi.String("mygroup"),
			Tags: pulumi.StringMap{
				"additionalProp1": pulumi.String("string1"),
				"additionalProp2": pulumi.String("string2"),
				"additionalProp3": pulumi.String("string3"),
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
import com.pulumi.azurenative.syntex.DocumentProcessor;
import com.pulumi.azurenative.syntex.DocumentProcessorArgs;
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
        var documentProcessor = new DocumentProcessor("documentProcessor", DocumentProcessorArgs.builder()        
            .location("westus")
            .processorName("myprocessor")
            .properties(Map.ofEntries(
                Map.entry("spoTenantId", "e9bb744b-9558-4dc6-9e50-a3297e3332fa"),
                Map.entry("spoTenantUrl", "https://test123.sharepoint.com")
            ))
            .resourceGroupName("mygroup")
            .tags(Map.ofEntries(
                Map.entry("additionalProp1", "string1"),
                Map.entry("additionalProp2", "string2"),
                Map.entry("additionalProp3", "string3")
            ))
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const documentProcessor = new azure_native.syntex.DocumentProcessor("documentProcessor", {
    location: "westus",
    processorName: "myprocessor",
    properties: {
        spoTenantId: "e9bb744b-9558-4dc6-9e50-a3297e3332fa",
        spoTenantUrl: "https://test123.sharepoint.com",
    },
    resourceGroupName: "mygroup",
    tags: {
        additionalProp1: "string1",
        additionalProp2: "string2",
        additionalProp3: "string3",
    },
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

document_processor = azure_native.syntex.DocumentProcessor("documentProcessor",
    location="westus",
    processor_name="myprocessor",
    properties=azure_native.syntex.DocumentProcessorPropertiesArgs(
        spo_tenant_id="e9bb744b-9558-4dc6-9e50-a3297e3332fa",
        spo_tenant_url="https://test123.sharepoint.com",
    ),
    resource_group_name="mygroup",
    tags={
        "additionalProp1": "string1",
        "additionalProp2": "string2",
        "additionalProp3": "string3",
    })

```

```yaml
resources:
  documentProcessor:
    type: azure-native:syntex:DocumentProcessor
    properties:
      location: westus
      processorName: myprocessor
      properties:
        spoTenantId: e9bb744b-9558-4dc6-9e50-a3297e3332fa
        spoTenantUrl: https://test123.sharepoint.com
      resourceGroupName: mygroup
      tags:
        additionalProp1: string1
        additionalProp2: string2
        additionalProp3: string3

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:syntex:DocumentProcessor myprocessor /subscriptions/cd0d3cc8-cae2-4559-b882-cd707170799b/resourceGroups/mygroup/providers/Microsoft.Syntex/documentProcessors/myprocessor 
```
