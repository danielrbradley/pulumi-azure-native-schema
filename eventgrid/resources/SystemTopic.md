EventGrid System Topic.
API Version: 2022-06-15.
Previous API Version: 2021-06-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### SystemTopics_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var systemTopic = new AzureNative.EventGrid.SystemTopic("systemTopic", new()
    {
        Location = "westus2",
        ResourceGroupName = "examplerg",
        Source = "/subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/azureeventgridrunnerrgcentraluseuap/providers/microsoft.storage/storageaccounts/pubstgrunnerb71cd29e",
        SystemTopicName = "exampleSystemTopic1",
        Tags = 
        {
            { "tag1", "value1" },
            { "tag2", "value2" },
        },
        TopicType = "microsoft.storage.storageaccounts",
    });

});


```

```go
package main

import (
	eventgrid "github.com/pulumi/pulumi-azure-native-sdk/eventgrid"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := eventgrid.NewSystemTopic(ctx, "systemTopic", &eventgrid.SystemTopicArgs{
			Location:          pulumi.String("westus2"),
			ResourceGroupName: pulumi.String("examplerg"),
			Source:            pulumi.String("/subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/azureeventgridrunnerrgcentraluseuap/providers/microsoft.storage/storageaccounts/pubstgrunnerb71cd29e"),
			SystemTopicName:   pulumi.String("exampleSystemTopic1"),
			Tags: pulumi.StringMap{
				"tag1": pulumi.String("value1"),
				"tag2": pulumi.String("value2"),
			},
			TopicType: pulumi.String("microsoft.storage.storageaccounts"),
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
import com.pulumi.azurenative.eventgrid.SystemTopic;
import com.pulumi.azurenative.eventgrid.SystemTopicArgs;
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
        var systemTopic = new SystemTopic("systemTopic", SystemTopicArgs.builder()        
            .location("westus2")
            .resourceGroupName("examplerg")
            .source("/subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/azureeventgridrunnerrgcentraluseuap/providers/microsoft.storage/storageaccounts/pubstgrunnerb71cd29e")
            .systemTopicName("exampleSystemTopic1")
            .tags(Map.ofEntries(
                Map.entry("tag1", "value1"),
                Map.entry("tag2", "value2")
            ))
            .topicType("microsoft.storage.storageaccounts")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const systemTopic = new azure_native.eventgrid.SystemTopic("systemTopic", {
    location: "westus2",
    resourceGroupName: "examplerg",
    source: "/subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/azureeventgridrunnerrgcentraluseuap/providers/microsoft.storage/storageaccounts/pubstgrunnerb71cd29e",
    systemTopicName: "exampleSystemTopic1",
    tags: {
        tag1: "value1",
        tag2: "value2",
    },
    topicType: "microsoft.storage.storageaccounts",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

system_topic = azure_native.eventgrid.SystemTopic("systemTopic",
    location="westus2",
    resource_group_name="examplerg",
    source="/subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/azureeventgridrunnerrgcentraluseuap/providers/microsoft.storage/storageaccounts/pubstgrunnerb71cd29e",
    system_topic_name="exampleSystemTopic1",
    tags={
        "tag1": "value1",
        "tag2": "value2",
    },
    topic_type="microsoft.storage.storageaccounts")

```

```yaml
resources:
  systemTopic:
    type: azure-native:eventgrid:SystemTopic
    properties:
      location: westus2
      resourceGroupName: examplerg
      source: /subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/azureeventgridrunnerrgcentraluseuap/providers/microsoft.storage/storageaccounts/pubstgrunnerb71cd29e
      systemTopicName: exampleSystemTopic1
      tags:
        tag1: value1
        tag2: value2
      topicType: microsoft.storage.storageaccounts

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:eventgrid:SystemTopic exampleSystemTopic2 /subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/systemTopics/exampleSystemTopic2 
```
