Channel info.
API Version: 2022-06-15.
Previous API Version: 2021-10-15-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Channels_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var channel = new AzureNative.EventGrid.Channel("channel", new()
    {
        ChannelName = "exampleChannelName1",
        ChannelType = "PartnerTopic",
        ExpirationTimeIfNotActivatedUtc = "2021-10-21T22:50:25.410433Z",
        MessageForActivation = "Example message to approver",
        PartnerNamespaceName = "examplePartnerNamespaceName1",
        PartnerTopicInfo = new AzureNative.EventGrid.Inputs.PartnerTopicInfoArgs
        {
            AzureSubscriptionId = "5b4b650e-28b9-4790-b3ab-ddbd88d727c4",
            Name = "examplePartnerTopic1",
            ResourceGroupName = "examplerg2",
            Source = "ContosoCorp.Accounts.User1",
        },
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
		_, err := eventgrid.NewChannel(ctx, "channel", &eventgrid.ChannelArgs{
			ChannelName:                     pulumi.String("exampleChannelName1"),
			ChannelType:                     pulumi.String("PartnerTopic"),
			ExpirationTimeIfNotActivatedUtc: pulumi.String("2021-10-21T22:50:25.410433Z"),
			MessageForActivation:            pulumi.String("Example message to approver"),
			PartnerNamespaceName:            pulumi.String("examplePartnerNamespaceName1"),
			PartnerTopicInfo: &eventgrid.PartnerTopicInfoArgs{
				AzureSubscriptionId: pulumi.String("5b4b650e-28b9-4790-b3ab-ddbd88d727c4"),
				Name:                pulumi.String("examplePartnerTopic1"),
				ResourceGroupName:   pulumi.String("examplerg2"),
				Source:              pulumi.String("ContosoCorp.Accounts.User1"),
			},
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
import com.pulumi.azurenative.eventgrid.Channel;
import com.pulumi.azurenative.eventgrid.ChannelArgs;
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
        var channel = new Channel("channel", ChannelArgs.builder()        
            .channelName("exampleChannelName1")
            .channelType("PartnerTopic")
            .expirationTimeIfNotActivatedUtc("2021-10-21T22:50:25.410433Z")
            .messageForActivation("Example message to approver")
            .partnerNamespaceName("examplePartnerNamespaceName1")
            .partnerTopicInfo(Map.ofEntries(
                Map.entry("azureSubscriptionId", "5b4b650e-28b9-4790-b3ab-ddbd88d727c4"),
                Map.entry("name", "examplePartnerTopic1"),
                Map.entry("resourceGroupName", "examplerg2"),
                Map.entry("source", "ContosoCorp.Accounts.User1")
            ))
            .resourceGroupName("examplerg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const channel = new azure_native.eventgrid.Channel("channel", {
    channelName: "exampleChannelName1",
    channelType: "PartnerTopic",
    expirationTimeIfNotActivatedUtc: "2021-10-21T22:50:25.410433Z",
    messageForActivation: "Example message to approver",
    partnerNamespaceName: "examplePartnerNamespaceName1",
    partnerTopicInfo: {
        azureSubscriptionId: "5b4b650e-28b9-4790-b3ab-ddbd88d727c4",
        name: "examplePartnerTopic1",
        resourceGroupName: "examplerg2",
        source: "ContosoCorp.Accounts.User1",
    },
    resourceGroupName: "examplerg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

channel = azure_native.eventgrid.Channel("channel",
    channel_name="exampleChannelName1",
    channel_type="PartnerTopic",
    expiration_time_if_not_activated_utc="2021-10-21T22:50:25.410433Z",
    message_for_activation="Example message to approver",
    partner_namespace_name="examplePartnerNamespaceName1",
    partner_topic_info=azure_native.eventgrid.PartnerTopicInfoArgs(
        azure_subscription_id="5b4b650e-28b9-4790-b3ab-ddbd88d727c4",
        name="examplePartnerTopic1",
        resource_group_name="examplerg2",
        source="ContosoCorp.Accounts.User1",
    ),
    resource_group_name="examplerg")

```

```yaml
resources:
  channel:
    type: azure-native:eventgrid:Channel
    properties:
      channelName: exampleChannelName1
      channelType: PartnerTopic
      expirationTimeIfNotActivatedUtc: 2021-10-21T22:50:25.410433Z
      messageForActivation: Example message to approver
      partnerNamespaceName: examplePartnerNamespaceName1
      partnerTopicInfo:
        azureSubscriptionId: 5b4b650e-28b9-4790-b3ab-ddbd88d727c4
        name: examplePartnerTopic1
        resourceGroupName: examplerg2
        source: ContosoCorp.Accounts.User1
      resourceGroupName: examplerg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:eventgrid:Channel exampleChannelName1 /subscriptions/5b4b650e-28b9-4790-b3ab-ddbd88d727c4/resourceGroups/examplerg/providers/Microsoft.EventGrid/partnerNamespaces/examplePartnerNamespaceName1/changes/exampleChannelName1 
```
