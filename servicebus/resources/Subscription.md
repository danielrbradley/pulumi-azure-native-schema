Description of subscription resource.
API Version: 2021-11-01.
Previous API Version: 2017-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### SubscriptionCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var subscription = new AzureNative.ServiceBus.Subscription("subscription", new()
    {
        EnableBatchedOperations = true,
        NamespaceName = "sdk-Namespace-1349",
        ResourceGroupName = "ResourceGroup",
        SubscriptionName = "sdk-Subscriptions-2178",
        TopicName = "sdk-Topics-8740",
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
		_, err := servicebus.NewSubscription(ctx, "subscription", &servicebus.SubscriptionArgs{
			EnableBatchedOperations: pulumi.Bool(true),
			NamespaceName:           pulumi.String("sdk-Namespace-1349"),
			ResourceGroupName:       pulumi.String("ResourceGroup"),
			SubscriptionName:        pulumi.String("sdk-Subscriptions-2178"),
			TopicName:               pulumi.String("sdk-Topics-8740"),
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
import com.pulumi.azurenative.servicebus.Subscription;
import com.pulumi.azurenative.servicebus.SubscriptionArgs;
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
        var subscription = new Subscription("subscription", SubscriptionArgs.builder()        
            .enableBatchedOperations(true)
            .namespaceName("sdk-Namespace-1349")
            .resourceGroupName("ResourceGroup")
            .subscriptionName("sdk-Subscriptions-2178")
            .topicName("sdk-Topics-8740")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const subscription = new azure_native.servicebus.Subscription("subscription", {
    enableBatchedOperations: true,
    namespaceName: "sdk-Namespace-1349",
    resourceGroupName: "ResourceGroup",
    subscriptionName: "sdk-Subscriptions-2178",
    topicName: "sdk-Topics-8740",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

subscription = azure_native.servicebus.Subscription("subscription",
    enable_batched_operations=True,
    namespace_name="sdk-Namespace-1349",
    resource_group_name="ResourceGroup",
    subscription_name="sdk-Subscriptions-2178",
    topic_name="sdk-Topics-8740")

```

```yaml
resources:
  subscription:
    type: azure-native:servicebus:Subscription
    properties:
      enableBatchedOperations: true
      namespaceName: sdk-Namespace-1349
      resourceGroupName: ResourceGroup
      subscriptionName: sdk-Subscriptions-2178
      topicName: sdk-Topics-8740

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:servicebus:Subscription sdk-Subscriptions-2178 /subscriptions/Subscriptionid/resourceGroups/ResourceGroup/providers/Microsoft.ServiceBus/namespaces/sdk-Namespace-1349/topics/sdk-Topics-8740/subscriptions/sdk-Subscriptions-2178 
```
