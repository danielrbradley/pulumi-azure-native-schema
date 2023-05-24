Single item in a List or Get AuthorizationRule operation
API Version: 2021-11-01.
Previous API Version: 2017-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### EventHubAuthorizationRuleCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var eventHubAuthorizationRule = new AzureNative.EventHub.EventHubAuthorizationRule("eventHubAuthorizationRule", new()
    {
        AuthorizationRuleName = "sdk-Authrules-2513",
        EventHubName = "sdk-EventHub-532",
        NamespaceName = "sdk-Namespace-960",
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
		_, err := eventhub.NewEventHubAuthorizationRule(ctx, "eventHubAuthorizationRule", &eventhub.EventHubAuthorizationRuleArgs{
			AuthorizationRuleName: pulumi.String("sdk-Authrules-2513"),
			EventHubName:          pulumi.String("sdk-EventHub-532"),
			NamespaceName:         pulumi.String("sdk-Namespace-960"),
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
import com.pulumi.azurenative.eventhub.EventHubAuthorizationRule;
import com.pulumi.azurenative.eventhub.EventHubAuthorizationRuleArgs;
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
        var eventHubAuthorizationRule = new EventHubAuthorizationRule("eventHubAuthorizationRule", EventHubAuthorizationRuleArgs.builder()        
            .authorizationRuleName("sdk-Authrules-2513")
            .eventHubName("sdk-EventHub-532")
            .namespaceName("sdk-Namespace-960")
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

const eventHubAuthorizationRule = new azure_native.eventhub.EventHubAuthorizationRule("eventHubAuthorizationRule", {
    authorizationRuleName: "sdk-Authrules-2513",
    eventHubName: "sdk-EventHub-532",
    namespaceName: "sdk-Namespace-960",
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

event_hub_authorization_rule = azure_native.eventhub.EventHubAuthorizationRule("eventHubAuthorizationRule",
    authorization_rule_name="sdk-Authrules-2513",
    event_hub_name="sdk-EventHub-532",
    namespace_name="sdk-Namespace-960",
    resource_group_name="ArunMonocle",
    rights=[
        "Listen",
        "Send",
    ])

```

```yaml
resources:
  eventHubAuthorizationRule:
    type: azure-native:eventhub:EventHubAuthorizationRule
    properties:
      authorizationRuleName: sdk-Authrules-2513
      eventHubName: sdk-EventHub-532
      namespaceName: sdk-Namespace-960
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
$ pulumi import azure-native:eventhub:EventHubAuthorizationRule sdk-Authrules-2513 /subscriptions/5f750a97-50d9-4e36-8081-c9ee4c0210d4/resourceGroups/ArunMonocle/providers/Microsoft.EventHub/namespaces/sdk-Namespace-960/eventhubs/sdk-EventHub-532/authorizationRules/sdk-Authrules-2513 
```
