Event Subscription
API Version: 2022-06-15.
Previous API Version: 2020-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PartnerTopicEventSubscriptions_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var partnerTopicEventSubscription = new AzureNative.EventGrid.PartnerTopicEventSubscription("partnerTopicEventSubscription", new()
    {
        Destination = new AzureNative.EventGrid.Inputs.WebHookEventSubscriptionDestinationArgs
        {
            EndpointType = "WebHook",
            EndpointUrl = "https://requestb.in/15ksip71",
        },
        EventSubscriptionName = "exampleEventSubscriptionName1",
        Filter = new AzureNative.EventGrid.Inputs.EventSubscriptionFilterArgs
        {
            IsSubjectCaseSensitive = false,
            SubjectBeginsWith = "ExamplePrefix",
            SubjectEndsWith = "ExampleSuffix",
        },
        PartnerTopicName = "examplePartnerTopic1",
        ResourceGroupName = "examplerg",
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
		_, err := eventgrid.NewPartnerTopicEventSubscription(ctx, "partnerTopicEventSubscription", &eventgrid.PartnerTopicEventSubscriptionArgs{
			Destination: eventgrid.WebHookEventSubscriptionDestination{
				EndpointType: "WebHook",
				EndpointUrl:  "https://requestb.in/15ksip71",
			},
			EventSubscriptionName: pulumi.String("exampleEventSubscriptionName1"),
			Filter: &eventgrid.EventSubscriptionFilterArgs{
				IsSubjectCaseSensitive: pulumi.Bool(false),
				SubjectBeginsWith:      pulumi.String("ExamplePrefix"),
				SubjectEndsWith:        pulumi.String("ExampleSuffix"),
			},
			PartnerTopicName:  pulumi.String("examplePartnerTopic1"),
			ResourceGroupName: pulumi.String("examplerg"),
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
import com.pulumi.azurenative.eventgrid.PartnerTopicEventSubscription;
import com.pulumi.azurenative.eventgrid.PartnerTopicEventSubscriptionArgs;
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
        var partnerTopicEventSubscription = new PartnerTopicEventSubscription("partnerTopicEventSubscription", PartnerTopicEventSubscriptionArgs.builder()        
            .destination(Map.ofEntries(
                Map.entry("endpointType", "WebHook"),
                Map.entry("endpointUrl", "https://requestb.in/15ksip71")
            ))
            .eventSubscriptionName("exampleEventSubscriptionName1")
            .filter(Map.ofEntries(
                Map.entry("isSubjectCaseSensitive", false),
                Map.entry("subjectBeginsWith", "ExamplePrefix"),
                Map.entry("subjectEndsWith", "ExampleSuffix")
            ))
            .partnerTopicName("examplePartnerTopic1")
            .resourceGroupName("examplerg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const partnerTopicEventSubscription = new azure_native.eventgrid.PartnerTopicEventSubscription("partnerTopicEventSubscription", {
    destination: {
        endpointType: "WebHook",
        endpointUrl: "https://requestb.in/15ksip71",
    },
    eventSubscriptionName: "exampleEventSubscriptionName1",
    filter: {
        isSubjectCaseSensitive: false,
        subjectBeginsWith: "ExamplePrefix",
        subjectEndsWith: "ExampleSuffix",
    },
    partnerTopicName: "examplePartnerTopic1",
    resourceGroupName: "examplerg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

partner_topic_event_subscription = azure_native.eventgrid.PartnerTopicEventSubscription("partnerTopicEventSubscription",
    destination=azure_native.eventgrid.WebHookEventSubscriptionDestinationArgs(
        endpoint_type="WebHook",
        endpoint_url="https://requestb.in/15ksip71",
    ),
    event_subscription_name="exampleEventSubscriptionName1",
    filter=azure_native.eventgrid.EventSubscriptionFilterArgs(
        is_subject_case_sensitive=False,
        subject_begins_with="ExamplePrefix",
        subject_ends_with="ExampleSuffix",
    ),
    partner_topic_name="examplePartnerTopic1",
    resource_group_name="examplerg")

```

```yaml
resources:
  partnerTopicEventSubscription:
    type: azure-native:eventgrid:PartnerTopicEventSubscription
    properties:
      destination:
        endpointType: WebHook
        endpointUrl: https://requestb.in/15ksip71
      eventSubscriptionName: exampleEventSubscriptionName1
      filter:
        isSubjectCaseSensitive: false
        subjectBeginsWith: ExamplePrefix
        subjectEndsWith: ExampleSuffix
      partnerTopicName: examplePartnerTopic1
      resourceGroupName: examplerg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:eventgrid:PartnerTopicEventSubscription exampleEventSubscriptionName1 /subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/partnerTopics/examplePartnerTopic1/eventSubscriptions/exampleEventSubscriptionName1 
```
