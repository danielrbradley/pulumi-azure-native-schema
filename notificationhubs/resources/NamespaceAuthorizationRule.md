Description of a Namespace AuthorizationRules.
API Version: 2017-04-01.
Previous API Version: 2017-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### NameSpaceAuthorizationRuleCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var namespaceAuthorizationRule = new AzureNative.NotificationHubs.NamespaceAuthorizationRule("namespaceAuthorizationRule", new()
    {
        AuthorizationRuleName = "sdk-AuthRules-1788",
        NamespaceName = "nh-sdk-ns",
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
		_, err := notificationhubs.NewNamespaceAuthorizationRule(ctx, "namespaceAuthorizationRule", &notificationhubs.NamespaceAuthorizationRuleArgs{
			AuthorizationRuleName: pulumi.String("sdk-AuthRules-1788"),
			NamespaceName:         pulumi.String("nh-sdk-ns"),
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
import com.pulumi.azurenative.notificationhubs.NamespaceAuthorizationRule;
import com.pulumi.azurenative.notificationhubs.NamespaceAuthorizationRuleArgs;
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
        var namespaceAuthorizationRule = new NamespaceAuthorizationRule("namespaceAuthorizationRule", NamespaceAuthorizationRuleArgs.builder()        
            .authorizationRuleName("sdk-AuthRules-1788")
            .namespaceName("nh-sdk-ns")
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

const namespaceAuthorizationRule = new azure_native.notificationhubs.NamespaceAuthorizationRule("namespaceAuthorizationRule", {
    authorizationRuleName: "sdk-AuthRules-1788",
    namespaceName: "nh-sdk-ns",
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

namespace_authorization_rule = azure_native.notificationhubs.NamespaceAuthorizationRule("namespaceAuthorizationRule",
    authorization_rule_name="sdk-AuthRules-1788",
    namespace_name="nh-sdk-ns",
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
  namespaceAuthorizationRule:
    type: azure-native:notificationhubs:NamespaceAuthorizationRule
    properties:
      authorizationRuleName: sdk-AuthRules-1788
      namespaceName: nh-sdk-ns
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
$ pulumi import azure-native:notificationhubs:NamespaceAuthorizationRule sdk-AuthRules-1788 /subscriptions/29cfa613-cbbc-4512-b1d6-1b3a92c7fa40/resourceGroups/ArunMonocle/providers/Microsoft.NotificationHubs/namespaces/sdk-Namespace-6914/AuthorizationRules/sdk-AuthRules-1788 
```
