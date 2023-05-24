A notification.
API Version: 2018-09-15.
Previous API Version: 2018-09-15. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### NotificationChannels_CreateOrUpdate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var notificationChannel = new AzureNative.DevTestLab.NotificationChannel("notificationChannel", new()
    {
        Description = "Integration configured for auto-shutdown",
        EmailRecipient = "{email}",
        Events = new[]
        {
            new AzureNative.DevTestLab.Inputs.EventArgs
            {
                EventName = "AutoShutdown",
            },
        },
        LabName = "{labName}",
        Name = "{notificationChannelName}",
        NotificationLocale = "en",
        ResourceGroupName = "resourceGroupName",
        WebHookUrl = "{webhookUrl}",
    });

});


```

```go
package main

import (
	devtestlab "github.com/pulumi/pulumi-azure-native-sdk/devtestlab"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := devtestlab.NewNotificationChannel(ctx, "notificationChannel", &devtestlab.NotificationChannelArgs{
			Description:    pulumi.String("Integration configured for auto-shutdown"),
			EmailRecipient: pulumi.String("{email}"),
			Events: []devtestlab.EventArgs{
				{
					EventName: pulumi.String("AutoShutdown"),
				},
			},
			LabName:            pulumi.String("{labName}"),
			Name:               pulumi.String("{notificationChannelName}"),
			NotificationLocale: pulumi.String("en"),
			ResourceGroupName:  pulumi.String("resourceGroupName"),
			WebHookUrl:         pulumi.String("{webhookUrl}"),
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
import com.pulumi.azurenative.devtestlab.NotificationChannel;
import com.pulumi.azurenative.devtestlab.NotificationChannelArgs;
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
        var notificationChannel = new NotificationChannel("notificationChannel", NotificationChannelArgs.builder()        
            .description("Integration configured for auto-shutdown")
            .emailRecipient("{email}")
            .events(Map.of("eventName", "AutoShutdown"))
            .labName("{labName}")
            .name("{notificationChannelName}")
            .notificationLocale("en")
            .resourceGroupName("resourceGroupName")
            .webHookUrl("{webhookUrl}")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const notificationChannel = new azure_native.devtestlab.NotificationChannel("notificationChannel", {
    description: "Integration configured for auto-shutdown",
    emailRecipient: "{email}",
    events: [{
        eventName: "AutoShutdown",
    }],
    labName: "{labName}",
    name: "{notificationChannelName}",
    notificationLocale: "en",
    resourceGroupName: "resourceGroupName",
    webHookUrl: "{webhookUrl}",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

notification_channel = azure_native.devtestlab.NotificationChannel("notificationChannel",
    description="Integration configured for auto-shutdown",
    email_recipient="{email}",
    events=[azure_native.devtestlab.EventArgs(
        event_name="AutoShutdown",
    )],
    lab_name="{labName}",
    name="{notificationChannelName}",
    notification_locale="en",
    resource_group_name="resourceGroupName",
    web_hook_url="{webhookUrl}")

```

```yaml
resources:
  notificationChannel:
    type: azure-native:devtestlab:NotificationChannel
    properties:
      description: Integration configured for auto-shutdown
      emailRecipient: '{email}'
      events:
        - eventName: AutoShutdown
      labName: '{labName}'
      name: '{notificationChannelName}'
      notificationLocale: en
      resourceGroupName: resourceGroupName
      webHookUrl: '{webhookUrl}'

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devtestlab:NotificationChannel {notificationChannelName} /subscriptions/{subscriptionId}/resourceGroups/resourceGroupName/providers/Microsoft.DevTestLab/labs/{labName}/notificationChannels/{notificationChannelName} 
```
