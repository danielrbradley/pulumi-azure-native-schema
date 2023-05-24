The properties of the EventHubConsumerGroupInfo object.
API Version: 2021-07-02.
Previous API Version: 2020-08-31. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### IotHubResource_CreateEventHubConsumerGroup
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var iotHubResourceEventHubConsumerGroup = new AzureNative.Devices.IotHubResourceEventHubConsumerGroup("iotHubResourceEventHubConsumerGroup", new()
    {
        EventHubEndpointName = "events",
        Name = "test",
        Properties = new AzureNative.Devices.Inputs.EventHubConsumerGroupNameArgs
        {
            Name = "test",
        },
        ResourceGroupName = "myResourceGroup",
        ResourceName = "testHub",
    });

});


```

```go
package main

import (
	devices "github.com/pulumi/pulumi-azure-native-sdk/devices"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := devices.NewIotHubResourceEventHubConsumerGroup(ctx, "iotHubResourceEventHubConsumerGroup", &devices.IotHubResourceEventHubConsumerGroupArgs{
			EventHubEndpointName: pulumi.String("events"),
			Name:                 pulumi.String("test"),
			Properties: &devices.EventHubConsumerGroupNameArgs{
				Name: pulumi.String("test"),
			},
			ResourceGroupName: pulumi.String("myResourceGroup"),
			ResourceName:      pulumi.String("testHub"),
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
import com.pulumi.azurenative.devices.IotHubResourceEventHubConsumerGroup;
import com.pulumi.azurenative.devices.IotHubResourceEventHubConsumerGroupArgs;
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
        var iotHubResourceEventHubConsumerGroup = new IotHubResourceEventHubConsumerGroup("iotHubResourceEventHubConsumerGroup", IotHubResourceEventHubConsumerGroupArgs.builder()        
            .eventHubEndpointName("events")
            .name("test")
            .properties(Map.of("name", "test"))
            .resourceGroupName("myResourceGroup")
            .resourceName("testHub")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const iotHubResourceEventHubConsumerGroup = new azure_native.devices.IotHubResourceEventHubConsumerGroup("iotHubResourceEventHubConsumerGroup", {
    eventHubEndpointName: "events",
    name: "test",
    properties: {
        name: "test",
    },
    resourceGroupName: "myResourceGroup",
    resourceName: "testHub",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

iot_hub_resource_event_hub_consumer_group = azure_native.devices.IotHubResourceEventHubConsumerGroup("iotHubResourceEventHubConsumerGroup",
    event_hub_endpoint_name="events",
    name="test",
    properties=azure_native.devices.EventHubConsumerGroupNameArgs(
        name="test",
    ),
    resource_group_name="myResourceGroup",
    resource_name_="testHub")

```

```yaml
resources:
  iotHubResourceEventHubConsumerGroup:
    type: azure-native:devices:IotHubResourceEventHubConsumerGroup
    properties:
      eventHubEndpointName: events
      name: test
      properties:
        name: test
      resourceGroupName: myResourceGroup
      resourceName: testHub

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:devices:IotHubResourceEventHubConsumerGroup test /subscriptions/cmd-sub-1/resourceGroups/cmd-rg-1/providers/Microsoft.Devices/IotHubs/test-hub-2/eventHubEndpoints/events/ConsumerGroups/%24Default 
```
