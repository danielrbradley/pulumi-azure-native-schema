Event Subscription
API Version: 2022-06-15.
Previous API Version: 2021-10-15-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### DomainTopicEventSubscriptions_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var domainTopicEventSubscription = new AzureNative.EventGrid.DomainTopicEventSubscription("domainTopicEventSubscription", new()
    {
        Destination = new AzureNative.EventGrid.Inputs.WebHookEventSubscriptionDestinationArgs
        {
            EndpointType = "WebHook",
            EndpointUrl = "https://requestb.in/15ksip71",
        },
        DomainName = "exampleDomain1",
        EventSubscriptionName = "exampleEventSubscriptionName1",
        Filter = new AzureNative.EventGrid.Inputs.EventSubscriptionFilterArgs
        {
            IsSubjectCaseSensitive = false,
            SubjectBeginsWith = "ExamplePrefix",
            SubjectEndsWith = "ExampleSuffix",
        },
        ResourceGroupName = "examplerg",
        TopicName = "exampleDomainTopic1",
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
		_, err := eventgrid.NewDomainTopicEventSubscription(ctx, "domainTopicEventSubscription", &eventgrid.DomainTopicEventSubscriptionArgs{
			Destination: eventgrid.WebHookEventSubscriptionDestination{
				EndpointType: "WebHook",
				EndpointUrl:  "https://requestb.in/15ksip71",
			},
			DomainName:            pulumi.String("exampleDomain1"),
			EventSubscriptionName: pulumi.String("exampleEventSubscriptionName1"),
			Filter: &eventgrid.EventSubscriptionFilterArgs{
				IsSubjectCaseSensitive: pulumi.Bool(false),
				SubjectBeginsWith:      pulumi.String("ExamplePrefix"),
				SubjectEndsWith:        pulumi.String("ExampleSuffix"),
			},
			ResourceGroupName: pulumi.String("examplerg"),
			TopicName:         pulumi.String("exampleDomainTopic1"),
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
import com.pulumi.azurenative.eventgrid.DomainTopicEventSubscription;
import com.pulumi.azurenative.eventgrid.DomainTopicEventSubscriptionArgs;
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
        var domainTopicEventSubscription = new DomainTopicEventSubscription("domainTopicEventSubscription", DomainTopicEventSubscriptionArgs.builder()        
            .destination(Map.ofEntries(
                Map.entry("endpointType", "WebHook"),
                Map.entry("endpointUrl", "https://requestb.in/15ksip71")
            ))
            .domainName("exampleDomain1")
            .eventSubscriptionName("exampleEventSubscriptionName1")
            .filter(Map.ofEntries(
                Map.entry("isSubjectCaseSensitive", false),
                Map.entry("subjectBeginsWith", "ExamplePrefix"),
                Map.entry("subjectEndsWith", "ExampleSuffix")
            ))
            .resourceGroupName("examplerg")
            .topicName("exampleDomainTopic1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const domainTopicEventSubscription = new azure_native.eventgrid.DomainTopicEventSubscription("domainTopicEventSubscription", {
    destination: {
        endpointType: "WebHook",
        endpointUrl: "https://requestb.in/15ksip71",
    },
    domainName: "exampleDomain1",
    eventSubscriptionName: "exampleEventSubscriptionName1",
    filter: {
        isSubjectCaseSensitive: false,
        subjectBeginsWith: "ExamplePrefix",
        subjectEndsWith: "ExampleSuffix",
    },
    resourceGroupName: "examplerg",
    topicName: "exampleDomainTopic1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

domain_topic_event_subscription = azure_native.eventgrid.DomainTopicEventSubscription("domainTopicEventSubscription",
    destination=azure_native.eventgrid.WebHookEventSubscriptionDestinationArgs(
        endpoint_type="WebHook",
        endpoint_url="https://requestb.in/15ksip71",
    ),
    domain_name="exampleDomain1",
    event_subscription_name="exampleEventSubscriptionName1",
    filter=azure_native.eventgrid.EventSubscriptionFilterArgs(
        is_subject_case_sensitive=False,
        subject_begins_with="ExamplePrefix",
        subject_ends_with="ExampleSuffix",
    ),
    resource_group_name="examplerg",
    topic_name="exampleDomainTopic1")

```

```yaml
resources:
  domainTopicEventSubscription:
    type: azure-native:eventgrid:DomainTopicEventSubscription
    properties:
      destination:
        endpointType: WebHook
        endpointUrl: https://requestb.in/15ksip71
      domainName: exampleDomain1
      eventSubscriptionName: exampleEventSubscriptionName1
      filter:
        isSubjectCaseSensitive: false
        subjectBeginsWith: ExamplePrefix
        subjectEndsWith: ExampleSuffix
      resourceGroupName: examplerg
      topicName: exampleDomainTopic1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:eventgrid:DomainTopicEventSubscription exampleEventSubscriptionName1 /subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/domains/exampleDomain1/domainTopics/exampleDomainTopic1/eventSubscriptions/exampleEventSubscriptionName1 
```
