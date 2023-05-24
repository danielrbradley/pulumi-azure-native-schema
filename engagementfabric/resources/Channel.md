The EngagementFabric channel
API Version: 2018-09-01-preview.
Previous API Version: 2018-09-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ChannelsCreateOrUpdateExample
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var channel = new AzureNative.EngagementFabric.Channel("channel", new()
    {
        AccountName = "ExampleAccount",
        ChannelFunctions = new[]
        {
            "MockFunction1",
            "MockFunction2",
        },
        ChannelName = "ExampleChannel",
        ChannelType = "MockChannel",
        Credentials = 
        {
            { "AppId", "exampleApp" },
            { "AppKey", "exampleAppKey" },
        },
        ResourceGroupName = "ExampleRg",
    });

});


```

```go
package main

import (
	engagementfabric "github.com/pulumi/pulumi-azure-native-sdk/engagementfabric"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := engagementfabric.NewChannel(ctx, "channel", &engagementfabric.ChannelArgs{
			AccountName: pulumi.String("ExampleAccount"),
			ChannelFunctions: pulumi.StringArray{
				pulumi.String("MockFunction1"),
				pulumi.String("MockFunction2"),
			},
			ChannelName: pulumi.String("ExampleChannel"),
			ChannelType: pulumi.String("MockChannel"),
			Credentials: pulumi.StringMap{
				"AppId":  pulumi.String("exampleApp"),
				"AppKey": pulumi.String("exampleAppKey"),
			},
			ResourceGroupName: pulumi.String("ExampleRg"),
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
import com.pulumi.azurenative.engagementfabric.Channel;
import com.pulumi.azurenative.engagementfabric.ChannelArgs;
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
        var channel = new Channel("channel", ChannelArgs.builder()        
            .accountName("ExampleAccount")
            .channelFunctions(            
                "MockFunction1",
                "MockFunction2")
            .channelName("ExampleChannel")
            .channelType("MockChannel")
            .credentials(Map.ofEntries(
                Map.entry("AppId", "exampleApp"),
                Map.entry("AppKey", "exampleAppKey")
            ))
            .resourceGroupName("ExampleRg")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const channel = new azure_native.engagementfabric.Channel("channel", {
    accountName: "ExampleAccount",
    channelFunctions: [
        "MockFunction1",
        "MockFunction2",
    ],
    channelName: "ExampleChannel",
    channelType: "MockChannel",
    credentials: {
        AppId: "exampleApp",
        AppKey: "exampleAppKey",
    },
    resourceGroupName: "ExampleRg",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

channel = azure_native.engagementfabric.Channel("channel",
    account_name="ExampleAccount",
    channel_functions=[
        "MockFunction1",
        "MockFunction2",
    ],
    channel_name="ExampleChannel",
    channel_type="MockChannel",
    credentials={
        "AppId": "exampleApp",
        "AppKey": "exampleAppKey",
    },
    resource_group_name="ExampleRg")

```

```yaml
resources:
  channel:
    type: azure-native:engagementfabric:Channel
    properties:
      accountName: ExampleAccount
      channelFunctions:
        - MockFunction1
        - MockFunction2
      channelName: ExampleChannel
      channelType: MockChannel
      credentials:
        AppId: exampleApp
        AppKey: exampleAppKey
      resourceGroupName: ExampleRg

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:engagementfabric:Channel ExampleChannel subscriptions/EDBF0095-A524-4A84-95FB-F72DA41AA6A1/resourceGroups/ExampleRg/providers/Microsoft.EngagementFabric/Accounts/ExampleAccount/Channels/ExampleChannel 
```
