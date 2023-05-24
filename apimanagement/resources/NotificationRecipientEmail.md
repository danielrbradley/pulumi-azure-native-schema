Recipient Email details.
API Version: 2022-08-01.
Previous API Version: 2020-12-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### ApiManagementCreateNotificationRecipientEmail
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var notificationRecipientEmail = new AzureNative.ApiManagement.NotificationRecipientEmail("notificationRecipientEmail", new()
    {
        Email = "foobar@live.com",
        NotificationName = "RequestPublisherNotificationMessage",
        ResourceGroupName = "rg1",
        ServiceName = "apimService1",
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
		_, err := apimanagement.NewNotificationRecipientEmail(ctx, "notificationRecipientEmail", &apimanagement.NotificationRecipientEmailArgs{
			Email:             pulumi.String("foobar@live.com"),
			NotificationName:  pulumi.String("RequestPublisherNotificationMessage"),
			ResourceGroupName: pulumi.String("rg1"),
			ServiceName:       pulumi.String("apimService1"),
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
import com.pulumi.azurenative.apimanagement.NotificationRecipientEmail;
import com.pulumi.azurenative.apimanagement.NotificationRecipientEmailArgs;
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
        var notificationRecipientEmail = new NotificationRecipientEmail("notificationRecipientEmail", NotificationRecipientEmailArgs.builder()        
            .email("foobar@live.com")
            .notificationName("RequestPublisherNotificationMessage")
            .resourceGroupName("rg1")
            .serviceName("apimService1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const notificationRecipientEmail = new azure_native.apimanagement.NotificationRecipientEmail("notificationRecipientEmail", {
    email: "foobar@live.com",
    notificationName: "RequestPublisherNotificationMessage",
    resourceGroupName: "rg1",
    serviceName: "apimService1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

notification_recipient_email = azure_native.apimanagement.NotificationRecipientEmail("notificationRecipientEmail",
    email="foobar@live.com",
    notification_name="RequestPublisherNotificationMessage",
    resource_group_name="rg1",
    service_name="apimService1")

```

```yaml
resources:
  notificationRecipientEmail:
    type: azure-native:apimanagement:NotificationRecipientEmail
    properties:
      email: foobar@live.com
      notificationName: RequestPublisherNotificationMessage
      resourceGroupName: rg1
      serviceName: apimService1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:apimanagement:NotificationRecipientEmail foobar@live.com /subscriptions/subid/resourceGroups/rg1/providers/Microsoft.ApiManagement/service/apimService1/notifications/RequestPublisherNotificationMessage/recipientEmails/foobar@live.com 
```
