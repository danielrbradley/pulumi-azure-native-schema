EventGrid Topic
API Version: 2022-06-15.
Previous API Version: 2020-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Topics_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var topic = new AzureNative.EventGrid.Topic("topic", new()
    {
        InboundIpRules = new[]
        {
            new AzureNative.EventGrid.Inputs.InboundIpRuleArgs
            {
                Action = "Allow",
                IpMask = "12.18.30.15",
            },
            new AzureNative.EventGrid.Inputs.InboundIpRuleArgs
            {
                Action = "Allow",
                IpMask = "12.18.176.1",
            },
        },
        Location = "westus2",
        PublicNetworkAccess = "Enabled",
        ResourceGroupName = "examplerg",
        Tags = 
        {
            { "tag1", "value1" },
            { "tag2", "value2" },
        },
        TopicName = "exampletopic1",
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
		_, err := eventgrid.NewTopic(ctx, "topic", &eventgrid.TopicArgs{
			InboundIpRules: []eventgrid.InboundIpRuleArgs{
				{
					Action: pulumi.String("Allow"),
					IpMask: pulumi.String("12.18.30.15"),
				},
				{
					Action: pulumi.String("Allow"),
					IpMask: pulumi.String("12.18.176.1"),
				},
			},
			Location:            pulumi.String("westus2"),
			PublicNetworkAccess: pulumi.String("Enabled"),
			ResourceGroupName:   pulumi.String("examplerg"),
			Tags: pulumi.StringMap{
				"tag1": pulumi.String("value1"),
				"tag2": pulumi.String("value2"),
			},
			TopicName: pulumi.String("exampletopic1"),
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
import com.pulumi.azurenative.eventgrid.Topic;
import com.pulumi.azurenative.eventgrid.TopicArgs;
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
        var topic = new Topic("topic", TopicArgs.builder()        
            .inboundIpRules(            
                Map.ofEntries(
                    Map.entry("action", "Allow"),
                    Map.entry("ipMask", "12.18.30.15")
                ),
                Map.ofEntries(
                    Map.entry("action", "Allow"),
                    Map.entry("ipMask", "12.18.176.1")
                ))
            .location("westus2")
            .publicNetworkAccess("Enabled")
            .resourceGroupName("examplerg")
            .tags(Map.ofEntries(
                Map.entry("tag1", "value1"),
                Map.entry("tag2", "value2")
            ))
            .topicName("exampletopic1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const topic = new azure_native.eventgrid.Topic("topic", {
    inboundIpRules: [
        {
            action: "Allow",
            ipMask: "12.18.30.15",
        },
        {
            action: "Allow",
            ipMask: "12.18.176.1",
        },
    ],
    location: "westus2",
    publicNetworkAccess: "Enabled",
    resourceGroupName: "examplerg",
    tags: {
        tag1: "value1",
        tag2: "value2",
    },
    topicName: "exampletopic1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

topic = azure_native.eventgrid.Topic("topic",
    inbound_ip_rules=[
        azure_native.eventgrid.InboundIpRuleArgs(
            action="Allow",
            ip_mask="12.18.30.15",
        ),
        azure_native.eventgrid.InboundIpRuleArgs(
            action="Allow",
            ip_mask="12.18.176.1",
        ),
    ],
    location="westus2",
    public_network_access="Enabled",
    resource_group_name="examplerg",
    tags={
        "tag1": "value1",
        "tag2": "value2",
    },
    topic_name="exampletopic1")

```

```yaml
resources:
  topic:
    type: azure-native:eventgrid:Topic
    properties:
      inboundIpRules:
        - action: Allow
          ipMask: 12.18.30.15
        - action: Allow
          ipMask: 12.18.176.1
      location: westus2
      publicNetworkAccess: Enabled
      resourceGroupName: examplerg
      tags:
        tag1: value1
        tag2: value2
      topicName: exampletopic1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:eventgrid:Topic exampletopic1 /subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1 
```
