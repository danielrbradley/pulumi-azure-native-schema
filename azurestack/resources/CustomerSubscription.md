Customer subscription.
API Version: 2022-06-01.
Previous API Version: 2017-06-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Creates a new customer subscription under a registration.
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var customerSubscription = new AzureNative.AzureStack.CustomerSubscription("customerSubscription", new()
    {
        CustomerSubscriptionName = "E09A4E93-29A7-4EBA-A6D4-76202383F07F",
        RegistrationName = "testregistration",
        ResourceGroup = "azurestack",
        TenantId = "dbab3982-796f-4d03-9908-044c08aef8a2",
    });

});


```

```go
package main

import (
	azurestack "github.com/pulumi/pulumi-azure-native-sdk/azurestack"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := azurestack.NewCustomerSubscription(ctx, "customerSubscription", &azurestack.CustomerSubscriptionArgs{
			CustomerSubscriptionName: pulumi.String("E09A4E93-29A7-4EBA-A6D4-76202383F07F"),
			RegistrationName:         pulumi.String("testregistration"),
			ResourceGroup:            pulumi.String("azurestack"),
			TenantId:                 pulumi.String("dbab3982-796f-4d03-9908-044c08aef8a2"),
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
import com.pulumi.azurenative.azurestack.CustomerSubscription;
import com.pulumi.azurenative.azurestack.CustomerSubscriptionArgs;
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
        var customerSubscription = new CustomerSubscription("customerSubscription", CustomerSubscriptionArgs.builder()        
            .customerSubscriptionName("E09A4E93-29A7-4EBA-A6D4-76202383F07F")
            .registrationName("testregistration")
            .resourceGroup("azurestack")
            .tenantId("dbab3982-796f-4d03-9908-044c08aef8a2")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const customerSubscription = new azure_native.azurestack.CustomerSubscription("customerSubscription", {
    customerSubscriptionName: "E09A4E93-29A7-4EBA-A6D4-76202383F07F",
    registrationName: "testregistration",
    resourceGroup: "azurestack",
    tenantId: "dbab3982-796f-4d03-9908-044c08aef8a2",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

customer_subscription = azure_native.azurestack.CustomerSubscription("customerSubscription",
    customer_subscription_name="E09A4E93-29A7-4EBA-A6D4-76202383F07F",
    registration_name="testregistration",
    resource_group="azurestack",
    tenant_id="dbab3982-796f-4d03-9908-044c08aef8a2")

```

```yaml
resources:
  customerSubscription:
    type: azure-native:azurestack:CustomerSubscription
    properties:
      customerSubscriptionName: E09A4E93-29A7-4EBA-A6D4-76202383F07F
      registrationName: testregistration
      resourceGroup: azurestack
      tenantId: dbab3982-796f-4d03-9908-044c08aef8a2

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:azurestack:CustomerSubscription myresource1 /subscriptions/{subscriptionId}/resourceGroups/{resourceGroup}/providers/Microsoft.AzureStack/registrations/{registrationName}/customerSubscriptions/{customerSubscriptionName} 
```
