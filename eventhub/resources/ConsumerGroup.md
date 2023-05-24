Single item in List or Get Consumer group operation
API Version: 2021-11-01.
Previous API Version: 2017-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ConsumerGroupCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var consumerGroup = new AzureNative.EventHub.ConsumerGroup("consumerGroup", new()
    {
        ConsumerGroupName = "sdk-ConsumerGroup-5563",
        EventHubName = "sdk-EventHub-6681",
        NamespaceName = "sdk-Namespace-2661",
        ResourceGroupName = "ArunMonocle",
        UserMetadata = "New consumergroup",
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
		_, err := eventhub.NewConsumerGroup(ctx, "consumerGroup", &eventhub.ConsumerGroupArgs{
			ConsumerGroupName: pulumi.String("sdk-ConsumerGroup-5563"),
			EventHubName:      pulumi.String("sdk-EventHub-6681"),
			NamespaceName:     pulumi.String("sdk-Namespace-2661"),
			ResourceGroupName: pulumi.String("ArunMonocle"),
			UserMetadata:      pulumi.String("New consumergroup"),
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
import com.pulumi.azurenative.eventhub.ConsumerGroup;
import com.pulumi.azurenative.eventhub.ConsumerGroupArgs;
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
        var consumerGroup = new ConsumerGroup("consumerGroup", ConsumerGroupArgs.builder()        
            .consumerGroupName("sdk-ConsumerGroup-5563")
            .eventHubName("sdk-EventHub-6681")
            .namespaceName("sdk-Namespace-2661")
            .resourceGroupName("ArunMonocle")
            .userMetadata("New consumergroup")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const consumerGroup = new azure_native.eventhub.ConsumerGroup("consumerGroup", {
    consumerGroupName: "sdk-ConsumerGroup-5563",
    eventHubName: "sdk-EventHub-6681",
    namespaceName: "sdk-Namespace-2661",
    resourceGroupName: "ArunMonocle",
    userMetadata: "New consumergroup",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

consumer_group = azure_native.eventhub.ConsumerGroup("consumerGroup",
    consumer_group_name="sdk-ConsumerGroup-5563",
    event_hub_name="sdk-EventHub-6681",
    namespace_name="sdk-Namespace-2661",
    resource_group_name="ArunMonocle",
    user_metadata="New consumergroup")

```

```yaml
resources:
  consumerGroup:
    type: azure-native:eventhub:ConsumerGroup
    properties:
      consumerGroupName: sdk-ConsumerGroup-5563
      eventHubName: sdk-EventHub-6681
      namespaceName: sdk-Namespace-2661
      resourceGroupName: ArunMonocle
      userMetadata: New consumergroup

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:eventhub:ConsumerGroup sdk-ConsumerGroup-5563 /subscriptions/5f750a97-50d9-4e36-8081-c9ee4c0210d4/resourceGroups/ArunMonocle/providers/Microsoft.EventHub/namespaces/sdk-Namespace-2661/eventhubs/sdk-EventHub-6681/consumergroups/sdk-ConsumerGroup-5563 
```
