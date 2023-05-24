Description of a namespace authorization rule.
API Version: 2021-11-01.
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
    var namespaceAuthorizationRule = new AzureNative.ServiceBus.NamespaceAuthorizationRule("namespaceAuthorizationRule", new()
    {
        AuthorizationRuleName = "sdk-AuthRules-1788",
        NamespaceName = "sdk-Namespace-6914",
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
		_, err := servicebus.NewNamespaceAuthorizationRule(ctx, "namespaceAuthorizationRule", &servicebus.NamespaceAuthorizationRuleArgs{
			AuthorizationRuleName: pulumi.String("sdk-AuthRules-1788"),
			NamespaceName:         pulumi.String("sdk-Namespace-6914"),
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
import com.pulumi.azurenative.servicebus.NamespaceAuthorizationRule;
import com.pulumi.azurenative.servicebus.NamespaceAuthorizationRuleArgs;
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
            .namespaceName("sdk-Namespace-6914")
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

const namespaceAuthorizationRule = new azure_native.servicebus.NamespaceAuthorizationRule("namespaceAuthorizationRule", {
    authorizationRuleName: "sdk-AuthRules-1788",
    namespaceName: "sdk-Namespace-6914",
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

namespace_authorization_rule = azure_native.servicebus.NamespaceAuthorizationRule("namespaceAuthorizationRule",
    authorization_rule_name="sdk-AuthRules-1788",
    namespace_name="sdk-Namespace-6914",
    resource_group_name="ArunMonocle",
    rights=[
        azure_native.servicebus.AccessRights.LISTEN,
        azure_native.servicebus.AccessRights.SEND,
    ])

```

```yaml
resources:
  namespaceAuthorizationRule:
    type: azure-native:servicebus:NamespaceAuthorizationRule
    properties:
      authorizationRuleName: sdk-AuthRules-1788
      namespaceName: sdk-Namespace-6914
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
$ pulumi import azure-native:servicebus:NamespaceAuthorizationRule sdk-AuthRules-1788 /subscriptions/5f750a97-50d9-4e36-8081-c9ee4c0210d4/resourceGroups/ArunMonocle/providers/Microsoft.ServiceBus/namespaces/sdk-Namespace-6914/AuthorizationRules/sdk-AuthRules-1788 
```
