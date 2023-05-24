Description of a NotificationHub Resource.
API Version: 2017-04-01.
Previous API Version: 2017-04-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### NotificationHubCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var notificationHub = new AzureNative.NotificationHubs.NotificationHub("notificationHub", new()
    {
        Location = "eastus",
        NamespaceName = "nh-sdk-ns",
        NotificationHubName = "nh-sdk-hub",
        ResourceGroupName = "5ktrial",
    });

});


```

```go
package main

import (
	notificationhubs "github.com/pulumi/pulumi-azure-native-sdk/notificationhubs"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := notificationhubs.NewNotificationHub(ctx, "notificationHub", &notificationhubs.NotificationHubArgs{
			Location:            pulumi.String("eastus"),
			NamespaceName:       pulumi.String("nh-sdk-ns"),
			NotificationHubName: pulumi.String("nh-sdk-hub"),
			ResourceGroupName:   pulumi.String("5ktrial"),
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
import com.pulumi.azurenative.notificationhubs.NotificationHub;
import com.pulumi.azurenative.notificationhubs.NotificationHubArgs;
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
        var notificationHub = new NotificationHub("notificationHub", NotificationHubArgs.builder()        
            .location("eastus")
            .namespaceName("nh-sdk-ns")
            .notificationHubName("nh-sdk-hub")
            .resourceGroupName("5ktrial")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const notificationHub = new azure_native.notificationhubs.NotificationHub("notificationHub", {
    location: "eastus",
    namespaceName: "nh-sdk-ns",
    notificationHubName: "nh-sdk-hub",
    resourceGroupName: "5ktrial",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

notification_hub = azure_native.notificationhubs.NotificationHub("notificationHub",
    location="eastus",
    namespace_name="nh-sdk-ns",
    notification_hub_name="nh-sdk-hub",
    resource_group_name="5ktrial")

```

```yaml
resources:
  notificationHub:
    type: azure-native:notificationhubs:NotificationHub
    properties:
      location: eastus
      namespaceName: nh-sdk-ns
      notificationHubName: nh-sdk-hub
      resourceGroupName: 5ktrial

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:notificationhubs:NotificationHub nh-sdk-hub /subscriptions/29cfa613-cbbc-4512-b1d6-1b3a92c7fa40/resourceGroups/sdkresourceGroup/providers/Microsoft.NotificationHubs/namespaces/nh-sdk-ns/notificationHubs/nh-sdk-hub 
```
