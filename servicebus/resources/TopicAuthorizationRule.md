Description of a namespace authorization rule.
API Version: 2021-11-01.
Previous API Version: 2017-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### TopicAuthorizationRuleCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var topicAuthorizationRule = new AzureNative.ServiceBus.TopicAuthorizationRule("topicAuthorizationRule", new()
    {
        AuthorizationRuleName = "sdk-AuthRules-4310",
        NamespaceName = "sdk-Namespace-6261",
        ResourceGroupName = "ArunMonocle",
        Rights = new[]
        {
            AzureNative.ServiceBus.AccessRights.Listen,
            AzureNative.ServiceBus.AccessRights.Send,
        },
        TopicName = "sdk-Topics-1984",
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
		_, err := servicebus.NewTopicAuthorizationRule(ctx, "topicAuthorizationRule", &servicebus.TopicAuthorizationRuleArgs{
			AuthorizationRuleName: pulumi.String("sdk-AuthRules-4310"),
			NamespaceName:         pulumi.String("sdk-Namespace-6261"),
			ResourceGroupName:     pulumi.String("ArunMonocle"),
			Rights: []servicebus.AccessRights{
				servicebus.AccessRightsListen,
				servicebus.AccessRightsSend,
			},
			TopicName: pulumi.String("sdk-Topics-1984"),
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
import com.pulumi.azurenative.servicebus.TopicAuthorizationRule;
import com.pulumi.azurenative.servicebus.TopicAuthorizationRuleArgs;
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
        var topicAuthorizationRule = new TopicAuthorizationRule("topicAuthorizationRule", TopicAuthorizationRuleArgs.builder()        
            .authorizationRuleName("sdk-AuthRules-4310")
            .namespaceName("sdk-Namespace-6261")
            .resourceGroupName("ArunMonocle")
            .rights(            
                "Listen",
                "Send")
            .topicName("sdk-Topics-1984")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const topicAuthorizationRule = new azure_native.servicebus.TopicAuthorizationRule("topicAuthorizationRule", {
    authorizationRuleName: "sdk-AuthRules-4310",
    namespaceName: "sdk-Namespace-6261",
    resourceGroupName: "ArunMonocle",
    rights: [
        azure_native.servicebus.AccessRights.Listen,
        azure_native.servicebus.AccessRights.Send,
    ],
    topicName: "sdk-Topics-1984",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

topic_authorization_rule = azure_native.servicebus.TopicAuthorizationRule("topicAuthorizationRule",
    authorization_rule_name="sdk-AuthRules-4310",
    namespace_name="sdk-Namespace-6261",
    resource_group_name="ArunMonocle",
    rights=[
        azure_native.servicebus.AccessRights.LISTEN,
        azure_native.servicebus.AccessRights.SEND,
    ],
    topic_name="sdk-Topics-1984")

```

```yaml
resources:
  topicAuthorizationRule:
    type: azure-native:servicebus:TopicAuthorizationRule
    properties:
      authorizationRuleName: sdk-AuthRules-4310
      namespaceName: sdk-Namespace-6261
      resourceGroupName: ArunMonocle
      rights:
        - Listen
        - Send
      topicName: sdk-Topics-1984

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:servicebus:TopicAuthorizationRule sdk-AuthRules-4310 /subscriptions/5f750a97-50d9-4e36-8081-c9ee4c0210d4/resourceGroups/ArunMonocle/providers/Microsoft.ServiceBus/namespaces/sdk-Namespace-6261/topics/sdk-Topics-1984/authorizationRules/sdk-AuthRules-4310 
```
