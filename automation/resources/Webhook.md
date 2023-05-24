Definition of the webhook type.
API Version: 2015-10-31.
Previous API Version: 2015-10-31. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Create or update webhook
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var webhook = new AzureNative.Automation.Webhook("webhook", new()
    {
        AutomationAccountName = "myAutomationAccount33",
        ExpiryTime = "2018-03-29T22:18:13.7002872Z",
        IsEnabled = true,
        Name = "TestWebhook",
        ResourceGroupName = "rg",
        Runbook = new AzureNative.Automation.Inputs.RunbookAssociationPropertyArgs
        {
            Name = "TestRunbook",
        },
        Uri = "<uri>",
        WebhookName = "TestWebhook",
    });

});


```

```go
package main

import (
	automation "github.com/pulumi/pulumi-azure-native-sdk/automation"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := automation.NewWebhook(ctx, "webhook", &automation.WebhookArgs{
			AutomationAccountName: pulumi.String("myAutomationAccount33"),
			ExpiryTime:            pulumi.String("2018-03-29T22:18:13.7002872Z"),
			IsEnabled:             pulumi.Bool(true),
			Name:                  pulumi.String("TestWebhook"),
			ResourceGroupName:     pulumi.String("rg"),
			Runbook: &automation.RunbookAssociationPropertyArgs{
				Name: pulumi.String("TestRunbook"),
			},
			Uri:         pulumi.String("<uri>"),
			WebhookName: pulumi.String("TestWebhook"),
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
import com.pulumi.azurenative.automation.Webhook;
import com.pulumi.azurenative.automation.WebhookArgs;
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
        var webhook = new Webhook("webhook", WebhookArgs.builder()        
            .automationAccountName("myAutomationAccount33")
            .expiryTime("2018-03-29T22:18:13.7002872Z")
            .isEnabled(true)
            .name("TestWebhook")
            .resourceGroupName("rg")
            .runbook(Map.of("name", "TestRunbook"))
            .uri("<uri>")
            .webhookName("TestWebhook")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const webhook = new azure_native.automation.Webhook("webhook", {
    automationAccountName: "myAutomationAccount33",
    expiryTime: "2018-03-29T22:18:13.7002872Z",
    isEnabled: true,
    name: "TestWebhook",
    resourceGroupName: "rg",
    runbook: {
        name: "TestRunbook",
    },
    uri: "<uri>",
    webhookName: "TestWebhook",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

webhook = azure_native.automation.Webhook("webhook",
    automation_account_name="myAutomationAccount33",
    expiry_time="2018-03-29T22:18:13.7002872Z",
    is_enabled=True,
    name="TestWebhook",
    resource_group_name="rg",
    runbook=azure_native.automation.RunbookAssociationPropertyArgs(
        name="TestRunbook",
    ),
    uri="<uri>",
    webhook_name="TestWebhook")

```

```yaml
resources:
  webhook:
    type: azure-native:automation:Webhook
    properties:
      automationAccountName: myAutomationAccount33
      expiryTime: 2018-03-29T22:18:13.7002872Z
      isEnabled: true
      name: TestWebhook
      resourceGroupName: rg
      runbook:
        name: TestRunbook
      uri: <uri>
      webhookName: TestWebhook

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:automation:Webhook TestWebhook /subscriptions/subid/resourceGroups/rg/providers/Microsoft.Automation/automationAccounts/myAutomationAccount33/webhooks/TestWebhook 
```
