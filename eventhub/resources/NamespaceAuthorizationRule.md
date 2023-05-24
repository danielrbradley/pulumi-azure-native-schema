Single item in a List or Get AuthorizationRule operation
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
    var namespaceAuthorizationRule = new AzureNative.EventHub.NamespaceAuthorizationRule("namespaceAuthorizationRule", new()
    {
        AuthorizationRuleName = "sdk-Authrules-1746",
        NamespaceName = "sdk-Namespace-2702",
        ResourceGroupName = "ArunMonocle",
        Rights = new[]
        {
            "Listen",
            "Send",
        },
    });

});


```

```go
package main

import (
	eventhub "github.com/pulumi/pulumi-azure-native-sdk/eventhub"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := eventhub.NewNamespaceAuthorizationRule(ctx, "namespaceAuthorizationRule", &eventhub.NamespaceAuthorizationRuleArgs{
			AuthorizationRuleName: pulumi.String("sdk-Authrules-1746"),
			NamespaceName:         pulumi.String("sdk-Namespace-2702"),
			ResourceGroupName:     pulumi.String("ArunMonocle"),
			Rights: pulumi.StringArray{
				pulumi.String("Listen"),
				pulumi.String("Send"),
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
import com.pulumi.azurenative.eventhub.NamespaceAuthorizationRule;
import com.pulumi.azurenative.eventhub.NamespaceAuthorizationRuleArgs;
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
            .authorizationRuleName("sdk-Authrules-1746")
            .namespaceName("sdk-Namespace-2702")
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

const namespaceAuthorizationRule = new azure_native.eventhub.NamespaceAuthorizationRule("namespaceAuthorizationRule", {
    authorizationRuleName: "sdk-Authrules-1746",
    namespaceName: "sdk-Namespace-2702",
    resourceGroupName: "ArunMonocle",
    rights: [
        "Listen",
        "Send",
    ],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

namespace_authorization_rule = azure_native.eventhub.NamespaceAuthorizationRule("namespaceAuthorizationRule",
    authorization_rule_name="sdk-Authrules-1746",
    namespace_name="sdk-Namespace-2702",
    resource_group_name="ArunMonocle",
    rights=[
        "Listen",
        "Send",
    ])

```

```yaml
resources:
  namespaceAuthorizationRule:
    type: azure-native:eventhub:NamespaceAuthorizationRule
    properties:
      authorizationRuleName: sdk-Authrules-1746
      namespaceName: sdk-Namespace-2702
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
$ pulumi import azure-native:eventhub:NamespaceAuthorizationRule sdk-Authrules-1746 /subscriptions/5f750a97-50d9-4e36-8081-c9ee4c0210d4/resourceGroups/ArunMonocle/providers/Microsoft.EventHub/namespaces/sdk-Namespace-2702/AuthorizationRules/sdk-Authrules-1746 
```
