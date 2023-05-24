Description of topic resource.
API Version: 2021-11-01.
Previous API Version: 2017-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### TopicCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var topic = new AzureNative.ServiceBus.Topic("topic", new()
    {
        EnableExpress = true,
        NamespaceName = "sdk-Namespace-1617",
        ResourceGroupName = "ArunMonocle",
        TopicName = "sdk-Topics-5488",
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
		_, err := servicebus.NewTopic(ctx, "topic", &servicebus.TopicArgs{
			EnableExpress:     pulumi.Bool(true),
			NamespaceName:     pulumi.String("sdk-Namespace-1617"),
			ResourceGroupName: pulumi.String("ArunMonocle"),
			TopicName:         pulumi.String("sdk-Topics-5488"),
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
import com.pulumi.azurenative.servicebus.Topic;
import com.pulumi.azurenative.servicebus.TopicArgs;
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
        var topic = new Topic("topic", TopicArgs.builder()        
            .enableExpress(true)
            .namespaceName("sdk-Namespace-1617")
            .resourceGroupName("ArunMonocle")
            .topicName("sdk-Topics-5488")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const topic = new azure_native.servicebus.Topic("topic", {
    enableExpress: true,
    namespaceName: "sdk-Namespace-1617",
    resourceGroupName: "ArunMonocle",
    topicName: "sdk-Topics-5488",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

topic = azure_native.servicebus.Topic("topic",
    enable_express=True,
    namespace_name="sdk-Namespace-1617",
    resource_group_name="ArunMonocle",
    topic_name="sdk-Topics-5488")

```

```yaml
resources:
  topic:
    type: azure-native:servicebus:Topic
    properties:
      enableExpress: true
      namespaceName: sdk-Namespace-1617
      resourceGroupName: ArunMonocle
      topicName: sdk-Topics-5488

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:servicebus:Topic sdk-Topics-5488 /subscriptions/5f750a97-50d9-4e36-8081-c9ee4c0210d4/resourceGroups/ArunMonocle/providers/Microsoft.ServiceBus/namespaces/sdk-Namespace-1617/topics/sdk-Topics-5488 
```
