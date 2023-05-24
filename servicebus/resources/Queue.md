Description of queue Resource.
API Version: 2021-11-01.
Previous API Version: 2017-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### QueueCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var queue = new AzureNative.ServiceBus.Queue("queue", new()
    {
        EnablePartitioning = true,
        NamespaceName = "sdk-Namespace-3174",
        QueueName = "sdk-Queues-5647",
        ResourceGroupName = "ArunMonocle",
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
		_, err := servicebus.NewQueue(ctx, "queue", &servicebus.QueueArgs{
			EnablePartitioning: pulumi.Bool(true),
			NamespaceName:      pulumi.String("sdk-Namespace-3174"),
			QueueName:          pulumi.String("sdk-Queues-5647"),
			ResourceGroupName:  pulumi.String("ArunMonocle"),
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
import com.pulumi.azurenative.servicebus.Queue;
import com.pulumi.azurenative.servicebus.QueueArgs;
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
        var queue = new Queue("queue", QueueArgs.builder()        
            .enablePartitioning(true)
            .namespaceName("sdk-Namespace-3174")
            .queueName("sdk-Queues-5647")
            .resourceGroupName("ArunMonocle")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const queue = new azure_native.servicebus.Queue("queue", {
    enablePartitioning: true,
    namespaceName: "sdk-Namespace-3174",
    queueName: "sdk-Queues-5647",
    resourceGroupName: "ArunMonocle",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

queue = azure_native.servicebus.Queue("queue",
    enable_partitioning=True,
    namespace_name="sdk-Namespace-3174",
    queue_name="sdk-Queues-5647",
    resource_group_name="ArunMonocle")

```

```yaml
resources:
  queue:
    type: azure-native:servicebus:Queue
    properties:
      enablePartitioning: true
      namespaceName: sdk-Namespace-3174
      queueName: sdk-Queues-5647
      resourceGroupName: ArunMonocle

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:servicebus:Queue sdk-Queues-5647 /subscriptions/5f750a97-50d9-4e36-8081-c9ee4c0210d4/resourceGroups/ArunMonocle/providers/Microsoft.ServiceBus/namespaces/sdk-Namespace-3174/queues/sdk-Queues-5647 
```
