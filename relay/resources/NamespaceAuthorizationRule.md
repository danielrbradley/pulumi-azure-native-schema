Single item in a List or Get AuthorizationRule operation
API Version: 2021-11-01.
Previous API Version: 2017-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### RelayNameSpaceAuthorizationRuleCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var namespaceAuthorizationRule = new AzureNative.Relay.NamespaceAuthorizationRule("namespaceAuthorizationRule", new()
    {
        AuthorizationRuleName = "example-RelayAuthRules-01",
        NamespaceName = "example-RelayNamespace-01",
        ResourceGroupName = "resourcegroup",
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
	relay "github.com/pulumi/pulumi-azure-native-sdk/relay"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := relay.NewNamespaceAuthorizationRule(ctx, "namespaceAuthorizationRule", &relay.NamespaceAuthorizationRuleArgs{
			AuthorizationRuleName: pulumi.String("example-RelayAuthRules-01"),
			NamespaceName:         pulumi.String("example-RelayNamespace-01"),
			ResourceGroupName:     pulumi.String("resourcegroup"),
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
import com.pulumi.azurenative.relay.NamespaceAuthorizationRule;
import com.pulumi.azurenative.relay.NamespaceAuthorizationRuleArgs;
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
            .authorizationRuleName("example-RelayAuthRules-01")
            .namespaceName("example-RelayNamespace-01")
            .resourceGroupName("resourcegroup")
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

const namespaceAuthorizationRule = new azure_native.relay.NamespaceAuthorizationRule("namespaceAuthorizationRule", {
    authorizationRuleName: "example-RelayAuthRules-01",
    namespaceName: "example-RelayNamespace-01",
    resourceGroupName: "resourcegroup",
    rights: [
        "Listen",
        "Send",
    ],
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

namespace_authorization_rule = azure_native.relay.NamespaceAuthorizationRule("namespaceAuthorizationRule",
    authorization_rule_name="example-RelayAuthRules-01",
    namespace_name="example-RelayNamespace-01",
    resource_group_name="resourcegroup",
    rights=[
        "Listen",
        "Send",
    ])

```

```yaml
resources:
  namespaceAuthorizationRule:
    type: azure-native:relay:NamespaceAuthorizationRule
    properties:
      authorizationRuleName: example-RelayAuthRules-01
      namespaceName: example-RelayNamespace-01
      resourceGroupName: resourcegroup
      rights:
        - Listen
        - Send

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:relay:NamespaceAuthorizationRule example-RelayAuthRules-01 /subscriptions/ffffffff-ffff-ffff-ffff-ffffffffffff/resourceGroups/resourcegroup/providers/Microsoft.Relay/namespaces/example-RelayNamespace-01/AuthorizationRules/example-RelayAuthRules-01 
```
