Event Grid Partner Topic.
API Version: 2022-06-15.
Previous API Version: 2021-10-15-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### PartnerTopics_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var partnerTopic = new AzureNative.EventGrid.PartnerTopic("partnerTopic", new()
    {
        ExpirationTimeIfNotActivatedUtc = "2022-03-23T23:06:13.109Z",
        Location = "westus2",
        MessageForActivation = "Example message for activation",
        PartnerRegistrationImmutableId = "6f541064-031d-4cc8-9ec3-a3b4fc0f7185",
        PartnerTopicFriendlyDescription = "Example description",
        PartnerTopicName = "examplePartnerTopicName1",
        ResourceGroupName = "examplerg",
        Source = "ContosoCorp.Accounts.User1",
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
		_, err := eventgrid.NewPartnerTopic(ctx, "partnerTopic", &eventgrid.PartnerTopicArgs{
			ExpirationTimeIfNotActivatedUtc: pulumi.String("2022-03-23T23:06:13.109Z"),
			Location:                        pulumi.String("westus2"),
			MessageForActivation:            pulumi.String("Example message for activation"),
			PartnerRegistrationImmutableId:  pulumi.String("6f541064-031d-4cc8-9ec3-a3b4fc0f7185"),
			PartnerTopicFriendlyDescription: pulumi.String("Example description"),
			PartnerTopicName:                pulumi.String("examplePartnerTopicName1"),
			ResourceGroupName:               pulumi.String("examplerg"),
			Source:                          pulumi.String("ContosoCorp.Accounts.User1"),
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
import com.pulumi.azurenative.eventgrid.PartnerTopic;
import com.pulumi.azurenative.eventgrid.PartnerTopicArgs;
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
        var partnerTopic = new PartnerTopic("partnerTopic", PartnerTopicArgs.builder()        
            .expirationTimeIfNotActivatedUtc("2022-03-23T23:06:13.109Z")
            .location("westus2")
            .messageForActivation("Example message for activation")
            .partnerRegistrationImmutableId("6f541064-031d-4cc8-9ec3-a3b4fc0f7185")
            .partnerTopicFriendlyDescription("Example description")
            .partnerTopicName("examplePartnerTopicName1")
            .resourceGroupName("examplerg")
            .source("ContosoCorp.Accounts.User1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const partnerTopic = new azure_native.eventgrid.PartnerTopic("partnerTopic", {
    expirationTimeIfNotActivatedUtc: "2022-03-23T23:06:13.109Z",
    location: "westus2",
    messageForActivation: "Example message for activation",
    partnerRegistrationImmutableId: "6f541064-031d-4cc8-9ec3-a3b4fc0f7185",
    partnerTopicFriendlyDescription: "Example description",
    partnerTopicName: "examplePartnerTopicName1",
    resourceGroupName: "examplerg",
    source: "ContosoCorp.Accounts.User1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

partner_topic = azure_native.eventgrid.PartnerTopic("partnerTopic",
    expiration_time_if_not_activated_utc="2022-03-23T23:06:13.109Z",
    location="westus2",
    message_for_activation="Example message for activation",
    partner_registration_immutable_id="6f541064-031d-4cc8-9ec3-a3b4fc0f7185",
    partner_topic_friendly_description="Example description",
    partner_topic_name="examplePartnerTopicName1",
    resource_group_name="examplerg",
    source="ContosoCorp.Accounts.User1")

```

```yaml
resources:
  partnerTopic:
    type: azure-native:eventgrid:PartnerTopic
    properties:
      expirationTimeIfNotActivatedUtc: 2022-03-23T23:06:13.109Z
      location: westus2
      messageForActivation: Example message for activation
      partnerRegistrationImmutableId: 6f541064-031d-4cc8-9ec3-a3b4fc0f7185
      partnerTopicFriendlyDescription: Example description
      partnerTopicName: examplePartnerTopicName1
      resourceGroupName: examplerg
      source: ContosoCorp.Accounts.User1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:eventgrid:PartnerTopic examplePartnerTopicName1 /subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/partnerTopics/examplePartnerTopicName1 
```
