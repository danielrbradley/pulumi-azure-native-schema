Description of a Namespace AuthorizationRules.
API Version: 2017-04-01.
Previous API Version: 2017-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### NotificationHubAuthorizationRuleCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var notificationHubAuthorizationRule = new AzureNative.NotificationHubs.NotificationHubAuthorizationRule("notificationHubAuthorizationRule", new()
    {
        AuthorizationRuleName = "DefaultListenSharedAccessSignature",
        NamespaceName = "nh-sdk-ns",
        NotificationHubName = "nh-sdk-hub",
        Properties = new AzureNative.NotificationHubs.Inputs.SharedAccessAuthorizationRulePropertiesArgs
        {
            Rights = new[]
            {
                AzureNative.NotificationHubs.AccessRights.Listen,
                AzureNative.NotificationHubs.AccessRights.Send,
            },
        },
        ResourceGroupName = "5ktrial",
    });

});


```

```go
package main

import (
	notificationhubs "github.com/pulumi/pulumi-azure-native-sdk/notificationhubs"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := notificationhubs.NewNotificationHubAuthorizationRule(ctx, "notificationHubAuthorizationRule", &notificationhubs.NotificationHubAuthorizationRuleArgs{
			AuthorizationRuleName: pulumi.String("DefaultListenSharedAccessSignature"),
			NamespaceName:         pulumi.String("nh-sdk-ns"),
			NotificationHubName:   pulumi.String("nh-sdk-hub"),
			Properties: &notificationhubs.SharedAccessAuthorizationRulePropertiesArgs{
				Rights: notificationhubs.AccessRightsArray{
					notificationhubs.AccessRightsListen,
					notificationhubs.AccessRightsSend,
				},
			},
			ResourceGroupName: pulumi.String("5ktrial"),
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
import com.pulumi.azurenative.notificationhubs.NotificationHubAuthorizationRule;
import com.pulumi.azurenative.notificationhubs.NotificationHubAuthorizationRuleArgs;
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
        var notificationHubAuthorizationRule = new NotificationHubAuthorizationRule("notificationHubAuthorizationRule", NotificationHubAuthorizationRuleArgs.builder()        
            .authorizationRuleName("DefaultListenSharedAccessSignature")
            .namespaceName("nh-sdk-ns")
            .notificationHubName("nh-sdk-hub")
            .properties(Map.of("rights",             
                "Listen",
                "Send"))
            .resourceGroupName("5ktrial")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const notificationHubAuthorizationRule = new azure_native.notificationhubs.NotificationHubAuthorizationRule("notificationHubAuthorizationRule", {
    authorizationRuleName: "DefaultListenSharedAccessSignature",
    namespaceName: "nh-sdk-ns",
    notificationHubName: "nh-sdk-hub",
    properties: {
        rights: [
            azure_native.notificationhubs.AccessRights.Listen,
            azure_native.notificationhubs.AccessRights.Send,
        ],
    },
    resourceGroupName: "5ktrial",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

notification_hub_authorization_rule = azure_native.notificationhubs.NotificationHubAuthorizationRule("notificationHubAuthorizationRule",
    authorization_rule_name="DefaultListenSharedAccessSignature",
    namespace_name="nh-sdk-ns",
    notification_hub_name="nh-sdk-hub",
    properties=azure_native.notificationhubs.SharedAccessAuthorizationRulePropertiesArgs(
        rights=[
            azure_native.notificationhubs.AccessRights.LISTEN,
            azure_native.notificationhubs.AccessRights.SEND,
        ],
    ),
    resource_group_name="5ktrial")

```

```yaml
resources:
  notificationHubAuthorizationRule:
    type: azure-native:notificationhubs:NotificationHubAuthorizationRule
    properties:
      authorizationRuleName: DefaultListenSharedAccessSignature
      namespaceName: nh-sdk-ns
      notificationHubName: nh-sdk-hub
      properties:
        rights:
          - Listen
          - Send
      resourceGroupName: 5ktrial

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:notificationhubs:NotificationHubAuthorizationRule DefaultListenSharedAccessSignature /subscriptions/29cfa613-cbbc-4512-b1d6-1b3a92c7fa40/resourceGroups/5ktrial/providers/Microsoft.NotificationHubs/namespaces/nh-sdk-ns/NotificationHubs/nh-sdk-hub/AuthorizationRules/DefaultListenSharedAccessSignature 
```
