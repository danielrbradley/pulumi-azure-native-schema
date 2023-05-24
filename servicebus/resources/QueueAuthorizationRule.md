Description of a namespace authorization rule.
API Version: 2021-11-01.
Previous API Version: 2017-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### QueueAuthorizationRuleCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var queueAuthorizationRule = new AzureNative.ServiceBus.QueueAuthorizationRule("queueAuthorizationRule", new()
    {
        AuthorizationRuleName = "sdk-AuthRules-5800",
        NamespaceName = "sdk-Namespace-7982",
        QueueName = "sdk-Queues-2317",
        ResourceGroupName = "ArunMonocle",
        Rights = new[]
        {
            AzureNative.ServiceBus.AccessRights.Listen,
            AzureNative.ServiceBus.AccessRights.Send,
        },
    });

});


```

```go
package main

import (
	servicebus "github.com/pulumi/pulumi-azure-native-sdk/servicebus"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := servicebus.NewQueueAuthorizationRule(ctx, "queueAuthorizationRule", &servicebus.QueueAuthorizationRuleArgs{
			AuthorizationRuleName: pulumi.String("sdk-AuthRules-5800"),
			NamespaceName:         pulumi.String("sdk-Namespace-7982"),
			QueueName:             pulumi.String("sdk-Queues-2317"),
			ResourceGroupName:     pulumi.String("ArunMonocle"),
			Rights: []servicebus.AccessRights{
				servicebus.AccessRightsListen,
				servicebus.AccessRightsSend,
			},
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
import com.pulumi.azurenative.servicebus.QueueAuthorizationRule;
import com.pulumi.azurenative.servicebus.QueueAuthorizationRuleArgs;
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
        var queueAuthorizationRule = new QueueAuthorizationRule("queueAuthorizationRule", QueueAuthorizationRuleArgs.builder()        
            .authorizationRuleName("sdk-AuthRules-5800")
            .namespaceName("sdk-Namespace-7982")
            .queueName("sdk-Queues-2317")
            .resourceGroupName("ArunMonocle")
            .rights(            
                "Listen",
                "Send")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const queueAuthorizationRule = new azure_native.servicebus.QueueAuthorizationRule("queueAuthorizationRule", {
    authorizationRuleName: "sdk-AuthRules-5800",
    namespaceName: "sdk-Namespace-7982",
    queueName: "sdk-Queues-2317",
    resourceGroupName: "ArunMonocle",
    rights: [
        azure_native.servicebus.AccessRights.Listen,
        azure_native.servicebus.AccessRights.Send,
    ],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

queue_authorization_rule = azure_native.servicebus.QueueAuthorizationRule("queueAuthorizationRule",
    authorization_rule_name="sdk-AuthRules-5800",
    namespace_name="sdk-Namespace-7982",
    queue_name="sdk-Queues-2317",
    resource_group_name="ArunMonocle",
    rights=[
        azure_native.servicebus.AccessRights.LISTEN,
        azure_native.servicebus.AccessRights.SEND,
    ])

```

```yaml
resources:
  queueAuthorizationRule:
    type: azure-native:servicebus:QueueAuthorizationRule
    properties:
      authorizationRuleName: sdk-AuthRules-5800
      namespaceName: sdk-Namespace-7982
      queueName: sdk-Queues-2317
      resourceGroupName: ArunMonocle
      rights:
        - Listen
        - Send

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:servicebus:QueueAuthorizationRule sdk-AuthRules-5800 /subscriptions/5f750a97-50d9-4e36-8081-c9ee4c0210d4/resourceGroups/ArunMonocle/providers/Microsoft.ServiceBus/namespaces/sdk-Namespace-7982/queues/sdk-Queues-2317/authorizationRules/sdk-AuthRules-5800 
```
