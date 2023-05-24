A type of trigger based on schedule
API Version: 2021-08-01.
Previous API Version: 2020-09-01. See https://github.com/pulumi/pulumi-azure-native/discussions/TODO for information on migrating from v1 to v2 of the provider.

{{% examples %}}
## Example Usage
{{% example %}}
### Triggers_Create
```csharp
using System.Collections.Generic;
using System.Linq;
using Pulumi;
using AzureNative = Pulumi.AzureNative;

return await Deployment.RunAsync(() => 
{
    var scheduledTrigger = new AzureNative.DataShare.ScheduledTrigger("scheduledTrigger", new()
    {
        AccountName = "Account1",
        Kind = "ScheduleBased",
        RecurrenceInterval = "Day",
        ResourceGroupName = "SampleResourceGroup",
        ShareSubscriptionName = "ShareSubscription1",
        SynchronizationMode = "Incremental",
        SynchronizationTime = "2018-11-14T04:47:52.9614956Z",
        TriggerName = "Trigger1",
    });

});


```

```go
package main

import (
	datashare "github.com/pulumi/pulumi-azure-native-sdk/datashare"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {
		_, err := datashare.NewScheduledTrigger(ctx, "scheduledTrigger", &datashare.ScheduledTriggerArgs{
			AccountName:           pulumi.String("Account1"),
			Kind:                  pulumi.String("ScheduleBased"),
			RecurrenceInterval:    pulumi.String("Day"),
			ResourceGroupName:     pulumi.String("SampleResourceGroup"),
			ShareSubscriptionName: pulumi.String("ShareSubscription1"),
			SynchronizationMode:   pulumi.String("Incremental"),
			SynchronizationTime:   pulumi.String("2018-11-14T04:47:52.9614956Z"),
			TriggerName:           pulumi.String("Trigger1"),
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
import com.pulumi.azurenative.datashare.ScheduledTrigger;
import com.pulumi.azurenative.datashare.ScheduledTriggerArgs;
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
        var scheduledTrigger = new ScheduledTrigger("scheduledTrigger", ScheduledTriggerArgs.builder()        
            .accountName("Account1")
            .kind("ScheduleBased")
            .recurrenceInterval("Day")
            .resourceGroupName("SampleResourceGroup")
            .shareSubscriptionName("ShareSubscription1")
            .synchronizationMode("Incremental")
            .synchronizationTime("2018-11-14T04:47:52.9614956Z")
            .triggerName("Trigger1")
            .build());

    }
}

```

```typescript
import * as pulumi from "@pulumi/pulumi";
import * as azure_native from "@pulumi/azure-native";

const scheduledTrigger = new azure_native.datashare.ScheduledTrigger("scheduledTrigger", {
    accountName: "Account1",
    kind: "ScheduleBased",
    recurrenceInterval: "Day",
    resourceGroupName: "SampleResourceGroup",
    shareSubscriptionName: "ShareSubscription1",
    synchronizationMode: "Incremental",
    synchronizationTime: "2018-11-14T04:47:52.9614956Z",
    triggerName: "Trigger1",
});

```

```python
import pulumi
import pulumi_azure_native as azure_native

scheduled_trigger = azure_native.datashare.ScheduledTrigger("scheduledTrigger",
    account_name="Account1",
    kind="ScheduleBased",
    recurrence_interval="Day",
    resource_group_name="SampleResourceGroup",
    share_subscription_name="ShareSubscription1",
    synchronization_mode="Incremental",
    synchronization_time="2018-11-14T04:47:52.9614956Z",
    trigger_name="Trigger1")

```

```yaml
resources:
  scheduledTrigger:
    type: azure-native:datashare:ScheduledTrigger
    properties:
      accountName: Account1
      kind: ScheduleBased
      recurrenceInterval: Day
      resourceGroupName: SampleResourceGroup
      shareSubscriptionName: ShareSubscription1
      synchronizationMode: Incremental
      synchronizationTime: 2018-11-14T04:47:52.9614956Z
      triggerName: Trigger1

```

{{% /example %}}
{{% /examples %}}

## Import

An existing resource can be imported using its type token, name, and identifier, e.g.

```sh
$ pulumi import azure-native:datashare:ScheduledTrigger Trigger1 /subscriptions/433a8dfd-e5d5-4e77-ad86-90acdc75eb1a/resourceGroups/SampleResourceGroup/providers/Microsoft.DataShare/accounts/Account1/shareSubscriptions/ShareSubscription1/triggers/Trigger1 
```
