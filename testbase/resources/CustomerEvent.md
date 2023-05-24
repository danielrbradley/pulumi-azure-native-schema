The Customer Notification Event resource.
API Version: 2022-04-01-preview.
Previous API Version: 2022-04-01-preview. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### CustomerEventCreate
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var customerEvent = new AzureNative.TestBase.CustomerEvent("customerEvent", new()
    {
        CustomerEventName = "WeeklySummary",
        EventName = "WeeklySummary",
        Receivers = new[]
        {
            new AzureNative.TestBase.Inputs.NotificationEventReceiverArgs
            {
                ReceiverType = "UserObjects",
                ReceiverValue = new AzureNative.TestBase.Inputs.NotificationReceiverValueArgs
                {
                    UserObjectReceiverValue = new AzureNative.TestBase.Inputs.UserObjectReceiverValueArgs
                    {
                        UserObjectIds = new[]
                        {
                            "245245245245325",
                            "365365365363565",
                        },
                    },
                },
            },
            new AzureNative.TestBase.Inputs.NotificationEventReceiverArgs
            {
                ReceiverType = "DistributionGroup",
                ReceiverValue = new AzureNative.TestBase.Inputs.NotificationReceiverValueArgs
                {
                    DistributionGroupListReceiverValue = new AzureNative.TestBase.Inputs.DistributionGroupListReceiverValueArgs
                    {
                        DistributionGroups = new[]
                        {
                            "test@microsoft.com",
                        },
                    },
                },
            },
        },
        ResourceGroupName = "contoso-rg1",
        TestBaseAccountName = "contoso-testBaseAccount1",
    });

});


```

```go
package main

import (
	testbase "github.com/pulumi/pulumi-azure-native-sdk/testbase"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := testbase.NewCustomerEvent(ctx, "customerEvent", &testbase.CustomerEventArgs{
			CustomerEventName: pulumi.String("WeeklySummary"),
			EventName:         pulumi.String("WeeklySummary"),
			Receivers: []testbase.NotificationEventReceiverArgs{
				{
					ReceiverType: pulumi.String("UserObjects"),
					ReceiverValue: {
						UserObjectReceiverValue: {
							UserObjectIds: pulumi.StringArray{
								pulumi.String("245245245245325"),
								pulumi.String("365365365363565"),
							},
						},
					},
				},
				{
					ReceiverType: pulumi.String("DistributionGroup"),
					ReceiverValue: {
						DistributionGroupListReceiverValue: {
							DistributionGroups: pulumi.StringArray{
								pulumi.String("test@microsoft.com"),
							},
						},
					},
				},
			},
			ResourceGroupName:   pulumi.String("contoso-rg1"),
			TestBaseAccountName: pulumi.String("contoso-testBaseAccount1"),
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
import com.pulumi.azurenative.testbase.CustomerEvent;
import com.pulumi.azurenative.testbase.CustomerEventArgs;
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
        var customerEvent = new CustomerEvent("customerEvent", CustomerEventArgs.builder()        
            .customerEventName("WeeklySummary")
            .eventName("WeeklySummary")
            .receivers(            
                Map.ofEntries(
                    Map.entry("receiverType", "UserObjects"),
                    Map.entry("receiverValue", Map.of("userObjectReceiverValue", Map.of("userObjectIds",                     
                        "245245245245325",
                        "365365365363565")))
                ),
                Map.ofEntries(
                    Map.entry("receiverType", "DistributionGroup"),
                    Map.entry("receiverValue", Map.of("distributionGroupListReceiverValue", Map.of("distributionGroups", "test@microsoft.com")))
                ))
            .resourceGroupName("contoso-rg1")
            .testBaseAccountName("contoso-testBaseAccount1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const customerEvent = new azure_native.testbase.CustomerEvent("customerEvent", {
    customerEventName: "WeeklySummary",
    eventName: "WeeklySummary",
    receivers: [
        {
            receiverType: "UserObjects",
            receiverValue: {
                userObjectReceiverValue: {
                    userObjectIds: [
                        "245245245245325",
                        "365365365363565",
                    ],
                },
            },
        },
        {
            receiverType: "DistributionGroup",
            receiverValue: {
                distributionGroupListReceiverValue: {
                    distributionGroups: ["test@microsoft.com"],
                },
            },
        },
    ],
    resourceGroupName: "contoso-rg1",
    testBaseAccountName: "contoso-testBaseAccount1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

customer_event = azure_native.testbase.CustomerEvent("customerEvent",
    customer_event_name="WeeklySummary",
    event_name="WeeklySummary",
    receivers=[
        {
            "receiverType": "UserObjects",
            "receiverValue": {
                "userObjectReceiverValue": azure_native.testbase.UserObjectReceiverValueArgs(
                    user_object_ids=[
                        "245245245245325",
                        "365365365363565",
                    ],
                ),
            },
        },
        {
            "receiverType": "DistributionGroup",
            "receiverValue": {
                "distributionGroupListReceiverValue": azure_native.testbase.DistributionGroupListReceiverValueArgs(
                    distribution_groups=["test@microsoft.com"],
                ),
            },
        },
    ],
    resource_group_name="contoso-rg1",
    test_base_account_name="contoso-testBaseAccount1")

```

```yaml
resources:
  customerEvent:
    type: azure-native:testbase:CustomerEvent
    properties:
      customerEventName: WeeklySummary
      eventName: WeeklySummary
      receivers:
        - receiverType: UserObjects
          receiverValue:
            userObjectReceiverValue:
              userObjectIds:
                - '245245245245325'
                - '365365365363565'
        - receiverType: DistributionGroup
          receiverValue:
            distributionGroupListReceiverValue:
              distributionGroups:
                - test@microsoft.com
      resourceGroupName: contoso-rg1
      testBaseAccountName: contoso-testBaseAccount1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:testbase:CustomerEvent WeeklySummary /subscriptions/subscription-id/resourceGroups/contoso-rg1/providers/Microsoft.TestBase/testBaseAccounts/contoso-testBaseAccount1/customerEvents/WeeklySummary 
```
