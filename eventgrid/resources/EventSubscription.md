Event Subscription
API Version: 2022-06-15.
Previous API Version: 2020-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### EventSubscriptions_CreateOrUpdateForCustomTopic
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var eventSubscription = new AzureNative.EventGrid.EventSubscription("eventSubscription", new()
    {
        Destination = new AzureNative.EventGrid.Inputs.EventHubEventSubscriptionDestinationArgs
        {
            EndpointType = "EventHub",
            ResourceId = "/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.EventHub/namespaces/ContosoNamespace/eventhubs/EH1",
        },
        EventSubscriptionName = "examplesubscription1",
        Filter = new AzureNative.EventGrid.Inputs.EventSubscriptionFilterArgs
        {
            IsSubjectCaseSensitive = false,
            SubjectBeginsWith = "ExamplePrefix",
            SubjectEndsWith = "ExampleSuffix",
        },
        Scope = "subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1",
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
		_, err := eventgrid.NewEventSubscription(ctx, "eventSubscription", &eventgrid.EventSubscriptionArgs{
			Destination: eventgrid.EventHubEventSubscriptionDestination{
				EndpointType: "EventHub",
				ResourceId:   "/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.EventHub/namespaces/ContosoNamespace/eventhubs/EH1",
			},
			EventSubscriptionName: pulumi.String("examplesubscription1"),
			Filter: &eventgrid.EventSubscriptionFilterArgs{
				IsSubjectCaseSensitive: pulumi.Bool(false),
				SubjectBeginsWith:      pulumi.String("ExamplePrefix"),
				SubjectEndsWith:        pulumi.String("ExampleSuffix"),
			},
			Scope: pulumi.String("subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1"),
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
import com.pulumi.azurenative.eventgrid.EventSubscription;
import com.pulumi.azurenative.eventgrid.EventSubscriptionArgs;
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
        var eventSubscription = new EventSubscription("eventSubscription", EventSubscriptionArgs.builder()        
            .destination(Map.ofEntries(
                Map.entry("endpointType", "EventHub"),
                Map.entry("resourceId", "/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.EventHub/namespaces/ContosoNamespace/eventhubs/EH1")
            ))
            .eventSubscriptionName("examplesubscription1")
            .filter(Map.ofEntries(
                Map.entry("isSubjectCaseSensitive", false),
                Map.entry("subjectBeginsWith", "ExamplePrefix"),
                Map.entry("subjectEndsWith", "ExampleSuffix")
            ))
            .scope("subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const eventSubscription = new azure_native.eventgrid.EventSubscription("eventSubscription", {
    destination: {
        endpointType: "EventHub",
        resourceId: "/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.EventHub/namespaces/ContosoNamespace/eventhubs/EH1",
    },
    eventSubscriptionName: "examplesubscription1",
    filter: {
        isSubjectCaseSensitive: false,
        subjectBeginsWith: "ExamplePrefix",
        subjectEndsWith: "ExampleSuffix",
    },
    scope: "subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

event_subscription = azure_native.eventgrid.EventSubscription("eventSubscription",
    destination=azure_native.eventgrid.EventHubEventSubscriptionDestinationArgs(
        endpoint_type="EventHub",
        resource_id="/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.EventHub/namespaces/ContosoNamespace/eventhubs/EH1",
    ),
    event_subscription_name="examplesubscription1",
    filter=azure_native.eventgrid.EventSubscriptionFilterArgs(
        is_subject_case_sensitive=False,
        subject_begins_with="ExamplePrefix",
        subject_ends_with="ExampleSuffix",
    ),
    scope="subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1")

```

```yaml
resources:
  eventSubscription:
    type: azure-native:eventgrid:EventSubscription
    properties:
      destination:
        endpointType: EventHub
        resourceId: /subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.EventHub/namespaces/ContosoNamespace/eventhubs/EH1
      eventSubscriptionName: examplesubscription1
      filter:
        isSubjectCaseSensitive: false
        subjectBeginsWith: ExamplePrefix
        subjectEndsWith: ExampleSuffix
      scope: subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1

```

{{% /example %}}
{{% example %}}
### EventSubscriptions_CreateOrUpdateForCustomTopic_AzureFunctionDestination
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var eventSubscription = new AzureNative.EventGrid.EventSubscription("eventSubscription", new()
    {
        DeadLetterDestination = new AzureNative.EventGrid.Inputs.StorageBlobDeadLetterDestinationArgs
        {
            BlobContainerName = "contosocontainer",
            EndpointType = "StorageBlob",
            ResourceId = "/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.Storage/storageAccounts/contosostg",
        },
        Destination = new AzureNative.EventGrid.Inputs.AzureFunctionEventSubscriptionDestinationArgs
        {
            EndpointType = "AzureFunction",
            ResourceId = "/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.Web/sites/ContosoSite/funtions/ContosoFunc",
        },
        EventSubscriptionName = "examplesubscription1",
        Filter = new AzureNative.EventGrid.Inputs.EventSubscriptionFilterArgs
        {
            IsSubjectCaseSensitive = false,
            SubjectBeginsWith = "ExamplePrefix",
            SubjectEndsWith = "ExampleSuffix",
        },
        Scope = "subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.eventgrid.EventSubscription;
import com.pulumi.azurenative.eventgrid.EventSubscriptionArgs;
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
        var eventSubscription = new EventSubscription("eventSubscription", EventSubscriptionArgs.builder()        
            .deadLetterDestination(Map.ofEntries(
                Map.entry("blobContainerName", "contosocontainer"),
                Map.entry("endpointType", "StorageBlob"),
                Map.entry("resourceId", "/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.Storage/storageAccounts/contosostg")
            ))
            .destination(Map.ofEntries(
                Map.entry("endpointType", "AzureFunction"),
                Map.entry("resourceId", "/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.Web/sites/ContosoSite/funtions/ContosoFunc")
            ))
            .eventSubscriptionName("examplesubscription1")
            .filter(Map.ofEntries(
                Map.entry("isSubjectCaseSensitive", false),
                Map.entry("subjectBeginsWith", "ExamplePrefix"),
                Map.entry("subjectEndsWith", "ExampleSuffix")
            ))
            .scope("subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const eventSubscription = new azure_native.eventgrid.EventSubscription("eventSubscription", {
    deadLetterDestination: {
        blobContainerName: "contosocontainer",
        endpointType: "StorageBlob",
        resourceId: "/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.Storage/storageAccounts/contosostg",
    },
    destination: {
        endpointType: "AzureFunction",
        resourceId: "/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.Web/sites/ContosoSite/funtions/ContosoFunc",
    },
    eventSubscriptionName: "examplesubscription1",
    filter: {
        isSubjectCaseSensitive: false,
        subjectBeginsWith: "ExamplePrefix",
        subjectEndsWith: "ExampleSuffix",
    },
    scope: "subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

event_subscription = azure_native.eventgrid.EventSubscription("eventSubscription",
    dead_letter_destination=azure_native.eventgrid.StorageBlobDeadLetterDestinationResponseArgs(
        blob_container_name="contosocontainer",
        endpoint_type="StorageBlob",
        resource_id="/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.Storage/storageAccounts/contosostg",
    ),
    destination=azure_native.eventgrid.AzureFunctionEventSubscriptionDestinationArgs(
        endpoint_type="AzureFunction",
        resource_id="/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.Web/sites/ContosoSite/funtions/ContosoFunc",
    ),
    event_subscription_name="examplesubscription1",
    filter=azure_native.eventgrid.EventSubscriptionFilterArgs(
        is_subject_case_sensitive=False,
        subject_begins_with="ExamplePrefix",
        subject_ends_with="ExampleSuffix",
    ),
    scope="subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1")

```

```yaml
resources:
  eventSubscription:
    type: azure-native:eventgrid:EventSubscription
    properties:
      deadLetterDestination:
        blobContainerName: contosocontainer
        endpointType: StorageBlob
        resourceId: /subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.Storage/storageAccounts/contosostg
      destination:
        endpointType: AzureFunction
        resourceId: /subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.Web/sites/ContosoSite/funtions/ContosoFunc
      eventSubscriptionName: examplesubscription1
      filter:
        isSubjectCaseSensitive: false
        subjectBeginsWith: ExamplePrefix
        subjectEndsWith: ExampleSuffix
      scope: subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1

```

{{% /example %}}
{{% example %}}
### EventSubscriptions_CreateOrUpdateForCustomTopic_EventHubDestination
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var eventSubscription = new AzureNative.EventGrid.EventSubscription("eventSubscription", new()
    {
        DeadLetterDestination = new AzureNative.EventGrid.Inputs.StorageBlobDeadLetterDestinationArgs
        {
            BlobContainerName = "contosocontainer",
            EndpointType = "StorageBlob",
            ResourceId = "/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.Storage/storageAccounts/contosostg",
        },
        Destination = new AzureNative.EventGrid.Inputs.EventHubEventSubscriptionDestinationArgs
        {
            EndpointType = "EventHub",
            ResourceId = "/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.EventHub/namespaces/ContosoNamespace/eventhubs/EH1",
        },
        EventSubscriptionName = "examplesubscription1",
        Filter = new AzureNative.EventGrid.Inputs.EventSubscriptionFilterArgs
        {
            IsSubjectCaseSensitive = false,
            SubjectBeginsWith = "ExamplePrefix",
            SubjectEndsWith = "ExampleSuffix",
        },
        Scope = "subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.eventgrid.EventSubscription;
import com.pulumi.azurenative.eventgrid.EventSubscriptionArgs;
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
        var eventSubscription = new EventSubscription("eventSubscription", EventSubscriptionArgs.builder()        
            .deadLetterDestination(Map.ofEntries(
                Map.entry("blobContainerName", "contosocontainer"),
                Map.entry("endpointType", "StorageBlob"),
                Map.entry("resourceId", "/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.Storage/storageAccounts/contosostg")
            ))
            .destination(Map.ofEntries(
                Map.entry("endpointType", "EventHub"),
                Map.entry("resourceId", "/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.EventHub/namespaces/ContosoNamespace/eventhubs/EH1")
            ))
            .eventSubscriptionName("examplesubscription1")
            .filter(Map.ofEntries(
                Map.entry("isSubjectCaseSensitive", false),
                Map.entry("subjectBeginsWith", "ExamplePrefix"),
                Map.entry("subjectEndsWith", "ExampleSuffix")
            ))
            .scope("subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const eventSubscription = new azure_native.eventgrid.EventSubscription("eventSubscription", {
    deadLetterDestination: {
        blobContainerName: "contosocontainer",
        endpointType: "StorageBlob",
        resourceId: "/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.Storage/storageAccounts/contosostg",
    },
    destination: {
        endpointType: "EventHub",
        resourceId: "/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.EventHub/namespaces/ContosoNamespace/eventhubs/EH1",
    },
    eventSubscriptionName: "examplesubscription1",
    filter: {
        isSubjectCaseSensitive: false,
        subjectBeginsWith: "ExamplePrefix",
        subjectEndsWith: "ExampleSuffix",
    },
    scope: "subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

event_subscription = azure_native.eventgrid.EventSubscription("eventSubscription",
    dead_letter_destination=azure_native.eventgrid.StorageBlobDeadLetterDestinationResponseArgs(
        blob_container_name="contosocontainer",
        endpoint_type="StorageBlob",
        resource_id="/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.Storage/storageAccounts/contosostg",
    ),
    destination=azure_native.eventgrid.EventHubEventSubscriptionDestinationArgs(
        endpoint_type="EventHub",
        resource_id="/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.EventHub/namespaces/ContosoNamespace/eventhubs/EH1",
    ),
    event_subscription_name="examplesubscription1",
    filter=azure_native.eventgrid.EventSubscriptionFilterArgs(
        is_subject_case_sensitive=False,
        subject_begins_with="ExamplePrefix",
        subject_ends_with="ExampleSuffix",
    ),
    scope="subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1")

```

```yaml
resources:
  eventSubscription:
    type: azure-native:eventgrid:EventSubscription
    properties:
      deadLetterDestination:
        blobContainerName: contosocontainer
        endpointType: StorageBlob
        resourceId: /subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.Storage/storageAccounts/contosostg
      destination:
        endpointType: EventHub
        resourceId: /subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.EventHub/namespaces/ContosoNamespace/eventhubs/EH1
      eventSubscriptionName: examplesubscription1
      filter:
        isSubjectCaseSensitive: false
        subjectBeginsWith: ExamplePrefix
        subjectEndsWith: ExampleSuffix
      scope: subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1

```

{{% /example %}}
{{% example %}}
### EventSubscriptions_CreateOrUpdateForCustomTopic_HybridConnectionDestination
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var eventSubscription = new AzureNative.EventGrid.EventSubscription("eventSubscription", new()
    {
        DeadLetterDestination = new AzureNative.EventGrid.Inputs.StorageBlobDeadLetterDestinationArgs
        {
            BlobContainerName = "contosocontainer",
            EndpointType = "StorageBlob",
            ResourceId = "/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.Storage/storageAccounts/contosostg",
        },
        Destination = new AzureNative.EventGrid.Inputs.HybridConnectionEventSubscriptionDestinationArgs
        {
            EndpointType = "HybridConnection",
            ResourceId = "/subscriptions/d33c5f7a-02ea-40f4-bf52-07f17e84d6a8/resourceGroups/TestRG/providers/Microsoft.Relay/namespaces/ContosoNamespace/hybridConnections/HC1",
        },
        EventSubscriptionName = "examplesubscription1",
        Filter = new AzureNative.EventGrid.Inputs.EventSubscriptionFilterArgs
        {
            IsSubjectCaseSensitive = false,
            SubjectBeginsWith = "ExamplePrefix",
            SubjectEndsWith = "ExampleSuffix",
        },
        Scope = "subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.eventgrid.EventSubscription;
import com.pulumi.azurenative.eventgrid.EventSubscriptionArgs;
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
        var eventSubscription = new EventSubscription("eventSubscription", EventSubscriptionArgs.builder()        
            .deadLetterDestination(Map.ofEntries(
                Map.entry("blobContainerName", "contosocontainer"),
                Map.entry("endpointType", "StorageBlob"),
                Map.entry("resourceId", "/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.Storage/storageAccounts/contosostg")
            ))
            .destination(Map.ofEntries(
                Map.entry("endpointType", "HybridConnection"),
                Map.entry("resourceId", "/subscriptions/d33c5f7a-02ea-40f4-bf52-07f17e84d6a8/resourceGroups/TestRG/providers/Microsoft.Relay/namespaces/ContosoNamespace/hybridConnections/HC1")
            ))
            .eventSubscriptionName("examplesubscription1")
            .filter(Map.ofEntries(
                Map.entry("isSubjectCaseSensitive", false),
                Map.entry("subjectBeginsWith", "ExamplePrefix"),
                Map.entry("subjectEndsWith", "ExampleSuffix")
            ))
            .scope("subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const eventSubscription = new azure_native.eventgrid.EventSubscription("eventSubscription", {
    deadLetterDestination: {
        blobContainerName: "contosocontainer",
        endpointType: "StorageBlob",
        resourceId: "/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.Storage/storageAccounts/contosostg",
    },
    destination: {
        endpointType: "HybridConnection",
        resourceId: "/subscriptions/d33c5f7a-02ea-40f4-bf52-07f17e84d6a8/resourceGroups/TestRG/providers/Microsoft.Relay/namespaces/ContosoNamespace/hybridConnections/HC1",
    },
    eventSubscriptionName: "examplesubscription1",
    filter: {
        isSubjectCaseSensitive: false,
        subjectBeginsWith: "ExamplePrefix",
        subjectEndsWith: "ExampleSuffix",
    },
    scope: "subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

event_subscription = azure_native.eventgrid.EventSubscription("eventSubscription",
    dead_letter_destination=azure_native.eventgrid.StorageBlobDeadLetterDestinationResponseArgs(
        blob_container_name="contosocontainer",
        endpoint_type="StorageBlob",
        resource_id="/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.Storage/storageAccounts/contosostg",
    ),
    destination=azure_native.eventgrid.HybridConnectionEventSubscriptionDestinationArgs(
        endpoint_type="HybridConnection",
        resource_id="/subscriptions/d33c5f7a-02ea-40f4-bf52-07f17e84d6a8/resourceGroups/TestRG/providers/Microsoft.Relay/namespaces/ContosoNamespace/hybridConnections/HC1",
    ),
    event_subscription_name="examplesubscription1",
    filter=azure_native.eventgrid.EventSubscriptionFilterArgs(
        is_subject_case_sensitive=False,
        subject_begins_with="ExamplePrefix",
        subject_ends_with="ExampleSuffix",
    ),
    scope="subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1")

```

```yaml
resources:
  eventSubscription:
    type: azure-native:eventgrid:EventSubscription
    properties:
      deadLetterDestination:
        blobContainerName: contosocontainer
        endpointType: StorageBlob
        resourceId: /subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.Storage/storageAccounts/contosostg
      destination:
        endpointType: HybridConnection
        resourceId: /subscriptions/d33c5f7a-02ea-40f4-bf52-07f17e84d6a8/resourceGroups/TestRG/providers/Microsoft.Relay/namespaces/ContosoNamespace/hybridConnections/HC1
      eventSubscriptionName: examplesubscription1
      filter:
        isSubjectCaseSensitive: false
        subjectBeginsWith: ExamplePrefix
        subjectEndsWith: ExampleSuffix
      scope: subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1

```

{{% /example %}}
{{% example %}}
### EventSubscriptions_CreateOrUpdateForCustomTopic_ServiceBusQueueDestination
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var eventSubscription = new AzureNative.EventGrid.EventSubscription("eventSubscription", new()
    {
        DeadLetterDestination = new AzureNative.EventGrid.Inputs.StorageBlobDeadLetterDestinationArgs
        {
            BlobContainerName = "contosocontainer",
            EndpointType = "StorageBlob",
            ResourceId = "/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.Storage/storageAccounts/contosostg",
        },
        Destination = new AzureNative.EventGrid.Inputs.ServiceBusQueueEventSubscriptionDestinationArgs
        {
            EndpointType = "ServiceBusQueue",
            ResourceId = "/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.ServiceBus/namespaces/ContosoNamespace/queues/SBQ",
        },
        EventSubscriptionName = "examplesubscription1",
        Filter = new AzureNative.EventGrid.Inputs.EventSubscriptionFilterArgs
        {
            IsSubjectCaseSensitive = false,
            SubjectBeginsWith = "ExamplePrefix",
            SubjectEndsWith = "ExampleSuffix",
        },
        Scope = "subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.eventgrid.EventSubscription;
import com.pulumi.azurenative.eventgrid.EventSubscriptionArgs;
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
        var eventSubscription = new EventSubscription("eventSubscription", EventSubscriptionArgs.builder()        
            .deadLetterDestination(Map.ofEntries(
                Map.entry("blobContainerName", "contosocontainer"),
                Map.entry("endpointType", "StorageBlob"),
                Map.entry("resourceId", "/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.Storage/storageAccounts/contosostg")
            ))
            .destination(Map.ofEntries(
                Map.entry("endpointType", "ServiceBusQueue"),
                Map.entry("resourceId", "/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.ServiceBus/namespaces/ContosoNamespace/queues/SBQ")
            ))
            .eventSubscriptionName("examplesubscription1")
            .filter(Map.ofEntries(
                Map.entry("isSubjectCaseSensitive", false),
                Map.entry("subjectBeginsWith", "ExamplePrefix"),
                Map.entry("subjectEndsWith", "ExampleSuffix")
            ))
            .scope("subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const eventSubscription = new azure_native.eventgrid.EventSubscription("eventSubscription", {
    deadLetterDestination: {
        blobContainerName: "contosocontainer",
        endpointType: "StorageBlob",
        resourceId: "/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.Storage/storageAccounts/contosostg",
    },
    destination: {
        endpointType: "ServiceBusQueue",
        resourceId: "/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.ServiceBus/namespaces/ContosoNamespace/queues/SBQ",
    },
    eventSubscriptionName: "examplesubscription1",
    filter: {
        isSubjectCaseSensitive: false,
        subjectBeginsWith: "ExamplePrefix",
        subjectEndsWith: "ExampleSuffix",
    },
    scope: "subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

event_subscription = azure_native.eventgrid.EventSubscription("eventSubscription",
    dead_letter_destination=azure_native.eventgrid.StorageBlobDeadLetterDestinationResponseArgs(
        blob_container_name="contosocontainer",
        endpoint_type="StorageBlob",
        resource_id="/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.Storage/storageAccounts/contosostg",
    ),
    destination=azure_native.eventgrid.ServiceBusQueueEventSubscriptionDestinationArgs(
        endpoint_type="ServiceBusQueue",
        resource_id="/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.ServiceBus/namespaces/ContosoNamespace/queues/SBQ",
    ),
    event_subscription_name="examplesubscription1",
    filter=azure_native.eventgrid.EventSubscriptionFilterArgs(
        is_subject_case_sensitive=False,
        subject_begins_with="ExamplePrefix",
        subject_ends_with="ExampleSuffix",
    ),
    scope="subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1")

```

```yaml
resources:
  eventSubscription:
    type: azure-native:eventgrid:EventSubscription
    properties:
      deadLetterDestination:
        blobContainerName: contosocontainer
        endpointType: StorageBlob
        resourceId: /subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.Storage/storageAccounts/contosostg
      destination:
        endpointType: ServiceBusQueue
        resourceId: /subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.ServiceBus/namespaces/ContosoNamespace/queues/SBQ
      eventSubscriptionName: examplesubscription1
      filter:
        isSubjectCaseSensitive: false
        subjectBeginsWith: ExamplePrefix
        subjectEndsWith: ExampleSuffix
      scope: subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1

```

{{% /example %}}
{{% example %}}
### EventSubscriptions_CreateOrUpdateForCustomTopic_ServiceBusTopicDestination
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var eventSubscription = new AzureNative.EventGrid.EventSubscription("eventSubscription", new()
    {
        DeadLetterDestination = new AzureNative.EventGrid.Inputs.StorageBlobDeadLetterDestinationArgs
        {
            BlobContainerName = "contosocontainer",
            EndpointType = "StorageBlob",
            ResourceId = "/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.Storage/storageAccounts/contosostg",
        },
        Destination = new AzureNative.EventGrid.Inputs.ServiceBusTopicEventSubscriptionDestinationArgs
        {
            EndpointType = "ServiceBusTopic",
            ResourceId = "/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.ServiceBus/namespaces/ContosoNamespace/topics/SBT",
        },
        EventSubscriptionName = "examplesubscription1",
        Filter = new AzureNative.EventGrid.Inputs.EventSubscriptionFilterArgs
        {
            IsSubjectCaseSensitive = false,
            SubjectBeginsWith = "ExamplePrefix",
            SubjectEndsWith = "ExampleSuffix",
        },
        Scope = "subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.eventgrid.EventSubscription;
import com.pulumi.azurenative.eventgrid.EventSubscriptionArgs;
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
        var eventSubscription = new EventSubscription("eventSubscription", EventSubscriptionArgs.builder()        
            .deadLetterDestination(Map.ofEntries(
                Map.entry("blobContainerName", "contosocontainer"),
                Map.entry("endpointType", "StorageBlob"),
                Map.entry("resourceId", "/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.Storage/storageAccounts/contosostg")
            ))
            .destination(Map.ofEntries(
                Map.entry("endpointType", "ServiceBusTopic"),
                Map.entry("resourceId", "/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.ServiceBus/namespaces/ContosoNamespace/topics/SBT")
            ))
            .eventSubscriptionName("examplesubscription1")
            .filter(Map.ofEntries(
                Map.entry("isSubjectCaseSensitive", false),
                Map.entry("subjectBeginsWith", "ExamplePrefix"),
                Map.entry("subjectEndsWith", "ExampleSuffix")
            ))
            .scope("subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const eventSubscription = new azure_native.eventgrid.EventSubscription("eventSubscription", {
    deadLetterDestination: {
        blobContainerName: "contosocontainer",
        endpointType: "StorageBlob",
        resourceId: "/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.Storage/storageAccounts/contosostg",
    },
    destination: {
        endpointType: "ServiceBusTopic",
        resourceId: "/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.ServiceBus/namespaces/ContosoNamespace/topics/SBT",
    },
    eventSubscriptionName: "examplesubscription1",
    filter: {
        isSubjectCaseSensitive: false,
        subjectBeginsWith: "ExamplePrefix",
        subjectEndsWith: "ExampleSuffix",
    },
    scope: "subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

event_subscription = azure_native.eventgrid.EventSubscription("eventSubscription",
    dead_letter_destination=azure_native.eventgrid.StorageBlobDeadLetterDestinationResponseArgs(
        blob_container_name="contosocontainer",
        endpoint_type="StorageBlob",
        resource_id="/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.Storage/storageAccounts/contosostg",
    ),
    destination=azure_native.eventgrid.ServiceBusTopicEventSubscriptionDestinationArgs(
        endpoint_type="ServiceBusTopic",
        resource_id="/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.ServiceBus/namespaces/ContosoNamespace/topics/SBT",
    ),
    event_subscription_name="examplesubscription1",
    filter=azure_native.eventgrid.EventSubscriptionFilterArgs(
        is_subject_case_sensitive=False,
        subject_begins_with="ExamplePrefix",
        subject_ends_with="ExampleSuffix",
    ),
    scope="subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1")

```

```yaml
resources:
  eventSubscription:
    type: azure-native:eventgrid:EventSubscription
    properties:
      deadLetterDestination:
        blobContainerName: contosocontainer
        endpointType: StorageBlob
        resourceId: /subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.Storage/storageAccounts/contosostg
      destination:
        endpointType: ServiceBusTopic
        resourceId: /subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.ServiceBus/namespaces/ContosoNamespace/topics/SBT
      eventSubscriptionName: examplesubscription1
      filter:
        isSubjectCaseSensitive: false
        subjectBeginsWith: ExamplePrefix
        subjectEndsWith: ExampleSuffix
      scope: subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1

```

{{% /example %}}
{{% example %}}
### EventSubscriptions_CreateOrUpdateForCustomTopic_StorageQueueDestination
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var eventSubscription = new AzureNative.EventGrid.EventSubscription("eventSubscription", new()
    {
        DeadLetterDestination = new AzureNative.EventGrid.Inputs.StorageBlobDeadLetterDestinationArgs
        {
            BlobContainerName = "contosocontainer",
            EndpointType = "StorageBlob",
            ResourceId = "/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.Storage/storageAccounts/contosostg",
        },
        Destination = new AzureNative.EventGrid.Inputs.StorageQueueEventSubscriptionDestinationArgs
        {
            EndpointType = "StorageQueue",
            QueueName = "queue1",
            ResourceId = "/subscriptions/d33c5f7a-02ea-40f4-bf52-07f17e84d6a8/resourceGroups/TestRG/providers/Microsoft.Storage/storageAccounts/contosostg",
        },
        EventSubscriptionName = "examplesubscription1",
        Filter = new AzureNative.EventGrid.Inputs.EventSubscriptionFilterArgs
        {
            IsSubjectCaseSensitive = false,
            SubjectBeginsWith = "ExamplePrefix",
            SubjectEndsWith = "ExampleSuffix",
        },
        Scope = "subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1",
    });

});


```

```java
package generated_program;

import com.pulumi.Context;
import com.pulumi.Pulumi;
import com.pulumi.core.Output;
import com.pulumi.azurenative.eventgrid.EventSubscription;
import com.pulumi.azurenative.eventgrid.EventSubscriptionArgs;
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
        var eventSubscription = new EventSubscription("eventSubscription", EventSubscriptionArgs.builder()        
            .deadLetterDestination(Map.ofEntries(
                Map.entry("blobContainerName", "contosocontainer"),
                Map.entry("endpointType", "StorageBlob"),
                Map.entry("resourceId", "/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.Storage/storageAccounts/contosostg")
            ))
            .destination(Map.ofEntries(
                Map.entry("endpointType", "StorageQueue"),
                Map.entry("queueName", "queue1"),
                Map.entry("resourceId", "/subscriptions/d33c5f7a-02ea-40f4-bf52-07f17e84d6a8/resourceGroups/TestRG/providers/Microsoft.Storage/storageAccounts/contosostg")
            ))
            .eventSubscriptionName("examplesubscription1")
            .filter(Map.ofEntries(
                Map.entry("isSubjectCaseSensitive", false),
                Map.entry("subjectBeginsWith", "ExamplePrefix"),
                Map.entry("subjectEndsWith", "ExampleSuffix")
            ))
            .scope("subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const eventSubscription = new azure_native.eventgrid.EventSubscription("eventSubscription", {
    deadLetterDestination: {
        blobContainerName: "contosocontainer",
        endpointType: "StorageBlob",
        resourceId: "/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.Storage/storageAccounts/contosostg",
    },
    destination: {
        endpointType: "StorageQueue",
        queueName: "queue1",
        resourceId: "/subscriptions/d33c5f7a-02ea-40f4-bf52-07f17e84d6a8/resourceGroups/TestRG/providers/Microsoft.Storage/storageAccounts/contosostg",
    },
    eventSubscriptionName: "examplesubscription1",
    filter: {
        isSubjectCaseSensitive: false,
        subjectBeginsWith: "ExamplePrefix",
        subjectEndsWith: "ExampleSuffix",
    },
    scope: "subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

event_subscription = azure_native.eventgrid.EventSubscription("eventSubscription",
    dead_letter_destination=azure_native.eventgrid.StorageBlobDeadLetterDestinationResponseArgs(
        blob_container_name="contosocontainer",
        endpoint_type="StorageBlob",
        resource_id="/subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.Storage/storageAccounts/contosostg",
    ),
    destination=azure_native.eventgrid.StorageQueueEventSubscriptionDestinationArgs(
        endpoint_type="StorageQueue",
        queue_name="queue1",
        resource_id="/subscriptions/d33c5f7a-02ea-40f4-bf52-07f17e84d6a8/resourceGroups/TestRG/providers/Microsoft.Storage/storageAccounts/contosostg",
    ),
    event_subscription_name="examplesubscription1",
    filter=azure_native.eventgrid.EventSubscriptionFilterArgs(
        is_subject_case_sensitive=False,
        subject_begins_with="ExamplePrefix",
        subject_ends_with="ExampleSuffix",
    ),
    scope="subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1")

```

```yaml
resources:
  eventSubscription:
    type: azure-native:eventgrid:EventSubscription
    properties:
      deadLetterDestination:
        blobContainerName: contosocontainer
        endpointType: StorageBlob
        resourceId: /subscriptions/55f3dcd4-cac7-43b4-990b-a139d62a1eb2/resourceGroups/TestRG/providers/Microsoft.Storage/storageAccounts/contosostg
      destination:
        endpointType: StorageQueue
        queueName: queue1
        resourceId: /subscriptions/d33c5f7a-02ea-40f4-bf52-07f17e84d6a8/resourceGroups/TestRG/providers/Microsoft.Storage/storageAccounts/contosostg
      eventSubscriptionName: examplesubscription1
      filter:
        isSubjectCaseSensitive: false
        subjectBeginsWith: ExamplePrefix
        subjectEndsWith: ExampleSuffix
      scope: subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1

```

{{% /example %}}
{{% example %}}
### EventSubscriptions_CreateOrUpdateForCustomTopic_WebhookDestination
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var eventSubscription = new AzureNative.EventGrid.EventSubscription("eventSubscription", new()
    {
        Destination = new AzureNative.EventGrid.Inputs.WebHookEventSubscriptionDestinationArgs
        {
            EndpointType = "WebHook",
            EndpointUrl = "https://azurefunctionexample.azurewebsites.net/runtime/webhooks/EventGrid?functionName=EventGridTrigger1&code=PASSWORDCODE",
        },
        EventSubscriptionName = "examplesubscription1",
        Filter = new AzureNative.EventGrid.Inputs.EventSubscriptionFilterArgs
        {
            IsSubjectCaseSensitive = false,
            SubjectBeginsWith = "ExamplePrefix",
            SubjectEndsWith = "ExampleSuffix",
        },
        Scope = "subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1",
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
		_, err := eventgrid.NewEventSubscription(ctx, "eventSubscription", &eventgrid.EventSubscriptionArgs{
			Destination: eventgrid.WebHookEventSubscriptionDestination{
				EndpointType: "WebHook",
				EndpointUrl:  "https://azurefunctionexample.azurewebsites.net/runtime/webhooks/EventGrid?functionName=EventGridTrigger1&code=PASSWORDCODE",
			},
			EventSubscriptionName: pulumi.String("examplesubscription1"),
			Filter: &eventgrid.EventSubscriptionFilterArgs{
				IsSubjectCaseSensitive: pulumi.Bool(false),
				SubjectBeginsWith:      pulumi.String("ExamplePrefix"),
				SubjectEndsWith:        pulumi.String("ExampleSuffix"),
			},
			Scope: pulumi.String("subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1"),
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
import com.pulumi.azurenative.eventgrid.EventSubscription;
import com.pulumi.azurenative.eventgrid.EventSubscriptionArgs;
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
        var eventSubscription = new EventSubscription("eventSubscription", EventSubscriptionArgs.builder()        
            .destination(Map.ofEntries(
                Map.entry("endpointType", "WebHook"),
                Map.entry("endpointUrl", "https://azurefunctionexample.azurewebsites.net/runtime/webhooks/EventGrid?functionName=EventGridTrigger1&code=PASSWORDCODE")
            ))
            .eventSubscriptionName("examplesubscription1")
            .filter(Map.ofEntries(
                Map.entry("isSubjectCaseSensitive", false),
                Map.entry("subjectBeginsWith", "ExamplePrefix"),
                Map.entry("subjectEndsWith", "ExampleSuffix")
            ))
            .scope("subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const eventSubscription = new azure_native.eventgrid.EventSubscription("eventSubscription", {
    destination: {
        endpointType: "WebHook",
        endpointUrl: "https://azurefunctionexample.azurewebsites.net/runtime/webhooks/EventGrid?functionName=EventGridTrigger1&code=PASSWORDCODE",
    },
    eventSubscriptionName: "examplesubscription1",
    filter: {
        isSubjectCaseSensitive: false,
        subjectBeginsWith: "ExamplePrefix",
        subjectEndsWith: "ExampleSuffix",
    },
    scope: "subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

event_subscription = azure_native.eventgrid.EventSubscription("eventSubscription",
    destination=azure_native.eventgrid.WebHookEventSubscriptionDestinationArgs(
        endpoint_type="WebHook",
        endpoint_url="https://azurefunctionexample.azurewebsites.net/runtime/webhooks/EventGrid?functionName=EventGridTrigger1&code=PASSWORDCODE",
    ),
    event_subscription_name="examplesubscription1",
    filter=azure_native.eventgrid.EventSubscriptionFilterArgs(
        is_subject_case_sensitive=False,
        subject_begins_with="ExamplePrefix",
        subject_ends_with="ExampleSuffix",
    ),
    scope="subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1")

```

```yaml
resources:
  eventSubscription:
    type: azure-native:eventgrid:EventSubscription
    properties:
      destination:
        endpointType: WebHook
        endpointUrl: https://azurefunctionexample.azurewebsites.net/runtime/webhooks/EventGrid?functionName=EventGridTrigger1&code=PASSWORDCODE
      eventSubscriptionName: examplesubscription1
      filter:
        isSubjectCaseSensitive: false
        subjectBeginsWith: ExamplePrefix
        subjectEndsWith: ExampleSuffix
      scope: subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/topics/exampletopic1

```

{{% /example %}}
{{% example %}}
### EventSubscriptions_CreateOrUpdateForResource
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var eventSubscription = new AzureNative.EventGrid.EventSubscription("eventSubscription", new()
    {
        Destination = new AzureNative.EventGrid.Inputs.WebHookEventSubscriptionDestinationArgs
        {
            EndpointType = "WebHook",
            EndpointUrl = "https://requestb.in/15ksip71",
        },
        EventSubscriptionName = "examplesubscription10",
        Filter = new AzureNative.EventGrid.Inputs.EventSubscriptionFilterArgs
        {
            IsSubjectCaseSensitive = false,
            SubjectBeginsWith = "ExamplePrefix",
            SubjectEndsWith = "ExampleSuffix",
        },
        Scope = "subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventHub/namespaces/examplenamespace1",
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
		_, err := eventgrid.NewEventSubscription(ctx, "eventSubscription", &eventgrid.EventSubscriptionArgs{
			Destination: eventgrid.WebHookEventSubscriptionDestination{
				EndpointType: "WebHook",
				EndpointUrl:  "https://requestb.in/15ksip71",
			},
			EventSubscriptionName: pulumi.String("examplesubscription10"),
			Filter: &eventgrid.EventSubscriptionFilterArgs{
				IsSubjectCaseSensitive: pulumi.Bool(false),
				SubjectBeginsWith:      pulumi.String("ExamplePrefix"),
				SubjectEndsWith:        pulumi.String("ExampleSuffix"),
			},
			Scope: pulumi.String("subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventHub/namespaces/examplenamespace1"),
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
import com.pulumi.azurenative.eventgrid.EventSubscription;
import com.pulumi.azurenative.eventgrid.EventSubscriptionArgs;
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
        var eventSubscription = new EventSubscription("eventSubscription", EventSubscriptionArgs.builder()        
            .destination(Map.ofEntries(
                Map.entry("endpointType", "WebHook"),
                Map.entry("endpointUrl", "https://requestb.in/15ksip71")
            ))
            .eventSubscriptionName("examplesubscription10")
            .filter(Map.ofEntries(
                Map.entry("isSubjectCaseSensitive", false),
                Map.entry("subjectBeginsWith", "ExamplePrefix"),
                Map.entry("subjectEndsWith", "ExampleSuffix")
            ))
            .scope("subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventHub/namespaces/examplenamespace1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const eventSubscription = new azure_native.eventgrid.EventSubscription("eventSubscription", {
    destination: {
        endpointType: "WebHook",
        endpointUrl: "https://requestb.in/15ksip71",
    },
    eventSubscriptionName: "examplesubscription10",
    filter: {
        isSubjectCaseSensitive: false,
        subjectBeginsWith: "ExamplePrefix",
        subjectEndsWith: "ExampleSuffix",
    },
    scope: "subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventHub/namespaces/examplenamespace1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

event_subscription = azure_native.eventgrid.EventSubscription("eventSubscription",
    destination=azure_native.eventgrid.WebHookEventSubscriptionDestinationArgs(
        endpoint_type="WebHook",
        endpoint_url="https://requestb.in/15ksip71",
    ),
    event_subscription_name="examplesubscription10",
    filter=azure_native.eventgrid.EventSubscriptionFilterArgs(
        is_subject_case_sensitive=False,
        subject_begins_with="ExamplePrefix",
        subject_ends_with="ExampleSuffix",
    ),
    scope="subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventHub/namespaces/examplenamespace1")

```

```yaml
resources:
  eventSubscription:
    type: azure-native:eventgrid:EventSubscription
    properties:
      destination:
        endpointType: WebHook
        endpointUrl: https://requestb.in/15ksip71
      eventSubscriptionName: examplesubscription10
      filter:
        isSubjectCaseSensitive: false
        subjectBeginsWith: ExamplePrefix
        subjectEndsWith: ExampleSuffix
      scope: subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventHub/namespaces/examplenamespace1

```

{{% /example %}}
{{% example %}}
### EventSubscriptions_CreateOrUpdateForResourceGroup
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var eventSubscription = new AzureNative.EventGrid.EventSubscription("eventSubscription", new()
    {
        Destination = new AzureNative.EventGrid.Inputs.WebHookEventSubscriptionDestinationArgs
        {
            EndpointType = "WebHook",
            EndpointUrl = "https://requestb.in/15ksip71",
        },
        EventSubscriptionName = "examplesubscription2",
        Filter = new AzureNative.EventGrid.Inputs.EventSubscriptionFilterArgs
        {
            IsSubjectCaseSensitive = false,
            SubjectBeginsWith = "ExamplePrefix",
            SubjectEndsWith = "ExampleSuffix",
        },
        Scope = "subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg",
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
		_, err := eventgrid.NewEventSubscription(ctx, "eventSubscription", &eventgrid.EventSubscriptionArgs{
			Destination: eventgrid.WebHookEventSubscriptionDestination{
				EndpointType: "WebHook",
				EndpointUrl:  "https://requestb.in/15ksip71",
			},
			EventSubscriptionName: pulumi.String("examplesubscription2"),
			Filter: &eventgrid.EventSubscriptionFilterArgs{
				IsSubjectCaseSensitive: pulumi.Bool(false),
				SubjectBeginsWith:      pulumi.String("ExamplePrefix"),
				SubjectEndsWith:        pulumi.String("ExampleSuffix"),
			},
			Scope: pulumi.String("subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg"),
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
import com.pulumi.azurenative.eventgrid.EventSubscription;
import com.pulumi.azurenative.eventgrid.EventSubscriptionArgs;
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
        var eventSubscription = new EventSubscription("eventSubscription", EventSubscriptionArgs.builder()        
            .destination(Map.ofEntries(
                Map.entry("endpointType", "WebHook"),
                Map.entry("endpointUrl", "https://requestb.in/15ksip71")
            ))
            .eventSubscriptionName("examplesubscription2")
            .filter(Map.ofEntries(
                Map.entry("isSubjectCaseSensitive", false),
                Map.entry("subjectBeginsWith", "ExamplePrefix"),
                Map.entry("subjectEndsWith", "ExampleSuffix")
            ))
            .scope("subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const eventSubscription = new azure_native.eventgrid.EventSubscription("eventSubscription", {
    destination: {
        endpointType: "WebHook",
        endpointUrl: "https://requestb.in/15ksip71",
    },
    eventSubscriptionName: "examplesubscription2",
    filter: {
        isSubjectCaseSensitive: false,
        subjectBeginsWith: "ExamplePrefix",
        subjectEndsWith: "ExampleSuffix",
    },
    scope: "subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

event_subscription = azure_native.eventgrid.EventSubscription("eventSubscription",
    destination=azure_native.eventgrid.WebHookEventSubscriptionDestinationArgs(
        endpoint_type="WebHook",
        endpoint_url="https://requestb.in/15ksip71",
    ),
    event_subscription_name="examplesubscription2",
    filter=azure_native.eventgrid.EventSubscriptionFilterArgs(
        is_subject_case_sensitive=False,
        subject_begins_with="ExamplePrefix",
        subject_ends_with="ExampleSuffix",
    ),
    scope="subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg")

```

```yaml
resources:
  eventSubscription:
    type: azure-native:eventgrid:EventSubscription
    properties:
      destination:
        endpointType: WebHook
        endpointUrl: https://requestb.in/15ksip71
      eventSubscriptionName: examplesubscription2
      filter:
        isSubjectCaseSensitive: false
        subjectBeginsWith: ExamplePrefix
        subjectEndsWith: ExampleSuffix
      scope: subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg

```

{{% /example %}}
{{% example %}}
### EventSubscriptions_CreateOrUpdateForSubscription
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var eventSubscription = new AzureNative.EventGrid.EventSubscription("eventSubscription", new()
    {
        Destination = new AzureNative.EventGrid.Inputs.WebHookEventSubscriptionDestinationArgs
        {
            EndpointType = "WebHook",
            EndpointUrl = "https://requestb.in/15ksip71",
        },
        EventSubscriptionName = "examplesubscription3",
        Filter = new AzureNative.EventGrid.Inputs.EventSubscriptionFilterArgs
        {
            IsSubjectCaseSensitive = false,
        },
        Scope = "subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4",
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
		_, err := eventgrid.NewEventSubscription(ctx, "eventSubscription", &eventgrid.EventSubscriptionArgs{
			Destination: eventgrid.WebHookEventSubscriptionDestination{
				EndpointType: "WebHook",
				EndpointUrl:  "https://requestb.in/15ksip71",
			},
			EventSubscriptionName: pulumi.String("examplesubscription3"),
			Filter: &eventgrid.EventSubscriptionFilterArgs{
				IsSubjectCaseSensitive: pulumi.Bool(false),
			},
			Scope: pulumi.String("subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4"),
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
import com.pulumi.azurenative.eventgrid.EventSubscription;
import com.pulumi.azurenative.eventgrid.EventSubscriptionArgs;
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
        var eventSubscription = new EventSubscription("eventSubscription", EventSubscriptionArgs.builder()        
            .destination(Map.ofEntries(
                Map.entry("endpointType", "WebHook"),
                Map.entry("endpointUrl", "https://requestb.in/15ksip71")
            ))
            .eventSubscriptionName("examplesubscription3")
            .filter(Map.of("isSubjectCaseSensitive", false))
            .scope("subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const eventSubscription = new azure_native.eventgrid.EventSubscription("eventSubscription", {
    destination: {
        endpointType: "WebHook",
        endpointUrl: "https://requestb.in/15ksip71",
    },
    eventSubscriptionName: "examplesubscription3",
    filter: {
        isSubjectCaseSensitive: false,
    },
    scope: "subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

event_subscription = azure_native.eventgrid.EventSubscription("eventSubscription",
    destination=azure_native.eventgrid.WebHookEventSubscriptionDestinationArgs(
        endpoint_type="WebHook",
        endpoint_url="https://requestb.in/15ksip71",
    ),
    event_subscription_name="examplesubscription3",
    filter=azure_native.eventgrid.EventSubscriptionFilterArgs(
        is_subject_case_sensitive=False,
    ),
    scope="subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4")

```

```yaml
resources:
  eventSubscription:
    type: azure-native:eventgrid:EventSubscription
    properties:
      destination:
        endpointType: WebHook
        endpointUrl: https://requestb.in/15ksip71
      eventSubscriptionName: examplesubscription3
      filter:
        isSubjectCaseSensitive: false
      scope: subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:eventgrid:EventSubscription examplesubscription3 /subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/providers/Microsoft.EventGrid/eventSubscriptions/examplesubscription3 
```
