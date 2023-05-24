Recipient User details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateNotificationRecipientUser
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var notificationRecipientUser = new AzureNative.ApiManagement.NotificationRecipientUser("notificationRecipientUser", new()
    {
        NotificationName = "RequestPublisherNotificationMessage",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
        UserId = "576823d0a40f7e74ec07d642",
    });

});


```

```go
package main

import (
	apimanagement "github.com/pulumi/pulumi-azure-native-sdk/apimanagement"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := apimanagement.NewNotificationRecipientUser(ctx, "notificationRecipientUser", &apimanagement.NotificationRecipientUserArgs{
			NotificationName:  pulumi.String("RequestPublisherNotificationMessage"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
			UserId:            pulumi.String("576823d0a40f7e74ec07d642"),
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
import com.pulumi.azurenative.apimanagement.NotificationRecipientUser;
import com.pulumi.azurenative.apimanagement.NotificationRecipientUserArgs;
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
        var notificationRecipientUser = new NotificationRecipientUser("notificationRecipientUser", NotificationRecipientUserArgs.builder()        
            .notificationName("RequestPublisherNotificationMessage")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .userId("576823d0a40f7e74ec07d642")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const notificationRecipientUser = new azure_native.apimanagement.NotificationRecipientUser("notificationRecipientUser", {
    notificationName: "RequestPublisherNotificationMessage",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
    userId: "576823d0a40f7e74ec07d642",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

notification_recipient_user = azure_native.apimanagement.NotificationRecipientUser("notificationRecipientUser",
    notification_name="RequestPublisherNotificationMessage",
    resource_group_name="rg1",
    service_name="apimService1",
    user_id="576823d0a40f7e74ec07d642")

```

```yaml
resources:
  notificationRecipientUser:
    type: azure-native:apimanagement:NotificationRecipientUser
    properties:
      notificationName: RequestPublisherNotificationMessage
      resourceGroupName: rg1
      serviceName: apimService1
      userId: 576823d0a40f7e74ec07d642

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:NotificationRecipientUser 576823d0a40f7e74ec07d642 /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/notifications/RequestPublisherNotificationMessage/recipientUsers/576823d0a40f7e74ec07d642 
```
